# Docker volumes vs. bind mounts - LogRocket Blog

Source: Article
Status: Unprocessed
URL: https://blog.logrocket.com/docker-volumes-vs-bind-mounts/

![https://blog.logrocket.com/wp-content/uploads/2021/06/docker-volumes-bind-mounts.png](https://blog.logrocket.com/wp-content/uploads/2021/06/docker-volumes-bind-mounts.png)

---

![Docker%20volumes%20vs%20bind%20mounts%20-%20LogRocket%20Blog%2062d2082cf6684f0a94f2aaaa250f31d1/docker-volumes-bind-mounts.png](Docker%20volumes%20vs%20bind%20mounts%20-%20LogRocket%20Blog%2062d2082cf6684f0a94f2aaaa250f31d1/docker-volumes-bind-mounts.png)

When a Docker container is destroyed, creating a new container off of the existing Docker image does so without making any changes to the original container. Therefore, you’ll lose data any time you destroy one container and create a new one.

To avoid losing data, Docker provides volumes and bind mounts, two mechanisms for persisting data in your Docker container. In this tutorial, we’ll examine volumes and bind mounts before looking at some examples and use cases for each.

Let’s get started!

## Bind mounts

[Bind mounts](https://docs.docker.com/storage/bind-mounts/) have been available in Docker since its earliest days for data persisting. Bind mounts will mount a file or directory on to your container from your host machine, which you can then reference via its absolute path.

To use bind mounts, the file or directory does not need to exist on your Docker host already. If it doesn’t exist, it will be created on demand. Bind mounts rely on the host machine’s filesystem having a specific directory structure available. You must explicitly create a path to the file or folder to place the storage.

Another important piece of information about bind mounts is that they give access to sensitive files. According to the Docker docs, you can change the host filesystem through processes running in a container. This includes creating, modifying, and deleting system files and directories, which can have pretty severe security implications. It could even impact non-Docker processes.

### Getting started using bind mounts

To use bind mounts on a container, you two flag options to use, `--mount` and `-v`. The most notable difference between the two options is that `--mount` is more verbose and explicit, whereas `-v` is more of a shorthand for `--mount`. It combines all the options you pass to `--mount` into one field.

On the surface, both commands create a PostgreSQL container and set a volume to persist data. However, there are some scenarios where the difference between using `--mount` and `-v` will be noticeably different. For example, it’s best practice to use `--mount` when you are working with [services](https://docs.docker.com/engine/reference/commandline/service/) because you’ll need to specify more options than are possible with `-v`.

Specify the bind mount using the `--mount` flag by running:

```
docker run --rm --name postgres-db -e POSTGRES_PASSWORD=password --mount type=bind,source="$pwd",target=/var/lib/postgresql/data -p 2000:5432 -d postgres
```

Use this code to specify it with the `-v` flag:

```
docker run --rm --name postgres-db -e POSTGRES_PASSWORD=password --v "$pwd":/var/lib/postgresql/data -p 2000:5432 -d postgres
```

Note that in both cases, we specify `$pwd`, the working directory, as the source. Basically, we’re telling Docker to create the bind mount in the directory we are currently in.

## Docker volumes

[Volumes](https://docs.docker.com/storage/volumes/) are a great mechanism for adding a data persisting layer in your Docker containers, especially for a situation where you need to persist data after shutting down your containers.

Docker volumes are completely handled by Docker itself and therefore independent of both your directory structure and the OS of the host machine. When you use a volume, a new directory is created within Docker’s storage directory on the host machine, and Docker manages that directory’s contents.

### Benefits of using volumes

In Docker volumes, storage is not coupled to the lifecycle of the container, but instead exists outside of it. This has many benefits. For one, you can kill your container as many times as you want and still have your data persisted. It’s also easy to reuse storage in multiple containers; for example, one container writes to the storage while another reads from it.

Since volumes are not tied to any container, you can easily attach them to multiple running containers at the same time. You’ll also find that volumes don’t increase the size of the Docker container using them. Lastly, you can use the Docker CLI to manage volumes, for example, retrieving the list of volumes or removing unused volumes.

### Getting started using volumes

Now, let’s see an example!

Let’s say you want to create a PostgreSQL container, and you are interested in persisting the data. Start with a folder called `postgres` in `$HOME/docker/volumes/postgres`.

Like bind mounts, we can add the following code to specify that volume using the `--mount` flag:

```
docker run --rm --name postgres-db -e POSTGRES_PASSWORD=password --mount type=volume,source=$HOME/docker/volumes/postgres,target=/var/lib/postgresql/data -p 2000:5432 -d postgres
```

Alternately, here is the same command using the shorthand flag `-v`:

```
docker run --rm --name postgres-db -e POSTGRES_PASSWORD=password --v $HOME/docker/volumes/postgres:/var/lib/postgresql/data -p 2000:5432 -d postgres
```

You must store the data under `$HOME/docker/volumes/` if you’re using Mac or Linux, and `C:\ProgramData\docker\volumes` if you’re on Windows. Otherwise, Docker won’t treat or manage your data as a volume.

## Use cases

When deciding when to use volumes or bind mounts, there are a few important factors to consider. If you want your storage or persisting layer to be fully managed by Docker and accessed only through Docker containers and the Docker CLI, you should choose to use volumes.

However, if you need full control of the storage and plan on allowing other processes besides Docker to access or modify the storage layer, then bind mounts is the right tool for the job.

## Comparing volumes and bind mounts

According to the Docker documentation, using volumes is the easiest way to begin persisting data in your Docker container. Overall, bind mounts are more limited in comparison.

This insight comes as no surprised based on what we’ve seen so far. A good rule of thumb is that if you’re ever in doubt of what route to take to persist data in your Docker containers, use volumes.

One of the key differentiators of a bind mount is that a bind mount can be accessed and modified by processes outside Docker. As previously mentioned, this can be a benefit when you want to integrate Docker with other processes, but it could also cause a headache if you’re concerned with security.

## Conclusion

Now that we’ve seen the core differences between volumes and bind mounts, let’s review some advantages that make volumes the recommended mechanism for persisting data in Docker.

For one, volumes are more safely shared among containers; they can only be specified in a single directory (`$HOME/docker/volumes`) and are fully managed by Docker itself. You can also store volumes outside your host machine on remote hosts or cloud providers.

You can manage volumes using both the Docker CLI and the Docker API, and you can pre-populate the content of a new volume from a container. Additionally, volumes work on both Linux and Windows, making it perfect for teams using both operating systems.

Having investigated both volumes and bind mounts, we’ve seen that volumes are the better option for persisting data more often than not. Be sure to let me know which method you prefer in the comments!

## [LogRocket](https://logrocket.com/signup/): Full visibility into your web apps

![Docker%20volumes%20vs%20bind%20mounts%20-%20LogRocket%20Blog%2062d2082cf6684f0a94f2aaaa250f31d1/1d0cd-1s_rmyo6nbrasp-xtvbaxfg.png](Docker%20volumes%20vs%20bind%20mounts%20-%20LogRocket%20Blog%2062d2082cf6684f0a94f2aaaa250f31d1/1d0cd-1s_rmyo6nbrasp-xtvbaxfg.png)

[LogRocket](https://logrocket.com/signup/) is a frontend application monitoring solution that lets you replay problems as if they happened in your own browser. Instead of guessing why errors happen, or asking users for screenshots and log dumps, LogRocket lets you replay the session to quickly understand what went wrong. It works perfectly with any app, regardless of framework, and has plugins to log additional context from Redux, Vuex, and @ngrx/store.

In addition to logging Redux actions and state, LogRocket records console logs, JavaScript errors, stacktraces, network requests/responses with headers + bodies, browser metadata, and custom logs. It also instruments the DOM to record the HTML and CSS on the page, recreating pixel-perfect videos of even the most complex single-page apps.

[Try it for free](https://logrocket.com/signup/).