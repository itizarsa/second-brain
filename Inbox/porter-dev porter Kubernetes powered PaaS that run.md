# porter-dev/porter: Kubernetes powered PaaS that runs in your own cloud.

Source: Website
Status: Unprocessed
URL: https://github.com/porter-dev/porter

[https://opengraph.githubassets.com/a5f15578f5f48eb406ca071a743e0c727c69e99fe8c4e168c38ce2b13bf72424/porter-dev/porter](https://opengraph.githubassets.com/a5f15578f5f48eb406ca071a743e0c727c69e99fe8c4e168c38ce2b13bf72424/porter-dev/porter)

---

# Porter

[porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f696d672e736869656c64732e696f2f61706d2f6c2f61746f6d69632d64657369676e2d75692e7376673f](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f696d672e736869656c64732e696f2f61706d2f6c2f61746f6d69632d64657369676e2d75692e7376673f)

[porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f676f6a702f676f7265706f727463617264](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f676f6a702f676f7265706f727463617264)

[porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3534323838383834363237313138343839363f636f6c6f723d373338394438266c6162656c3d636f6d6d756e697479266c6f676f3d646973636f7264266c6f676f436f6c6f723d666666666666](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f696d672e736869656c64732e696f2f646973636f72642f3534323838383834363237313138343839363f636f6c6f723d373338394438266c6162656c3d636f6d6d756e697479266c6f676f3d646973636f7264266c6f676f436f6c6f723d666666666666)

[porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f75726c2f68747470732f747769747465722e636f6d2f636c6f7564706f7373652e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f75726c2f68747470732f747769747465722e636f6d2f636c6f7564706f7373652e7376673f7374796c653d736f6369616c266c6162656c3d466f6c6c6f77)

**Porter is a Kubernetes-powered PaaS that runs in your own cloud provider.** Porter brings the Heroku experience to your own AWS/GCP account, while upgrading your infrastructure to Kubernetes. Get started on Porter without the overhead of DevOps and customize your infrastructure later when you need to.

![porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/104234811-fe2dcb00-5421-11eb-9ce3-c0ebefc37476.png](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/104234811-fe2dcb00-5421-11eb-9ce3-c0ebefc37476.png)

## Community and Updates

For help, questions, or if you just want a place to hang out, [join our Discord community.](https://discord.gg/mmGAw5nNjr)

To keep updated on our progress, please watch the repo for new releases (**Watch > Custom > Releases**) and [follow us on Twitter](https://twitter.com/getporterdev)!

## Why Porter?

### A PaaS that grows with your applications

A traditional PaaS like Heroku is great for minimizing unnecessary DevOps work but doesn't offer enough flexibility as your applications grow. Custom network rules, resource constraints, and cost are common reasons developers move their applications off Heroku beyond a certain scale.

Porter brings the simplicity of a traditional PaaS to your own cloud provider while preserving the configurability of Kubernetes. Porter is built on top of a popular Kubernetes package manager `helm` and is compatible with standard Kubernetes management tools like `kubectl`, preparing your infra for mature DevOps work from day one.

![porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/103713478-71e75800-4f8a-11eb-915f-adee9d4f5bf7.png](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/103713478-71e75800-4f8a-11eb-915f-adee9d4f5bf7.png)

## Features

### Basics

- One-click provisioning of a Kubernetes cluster in your own cloud console
    - AWS
        
        ![porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/2705.png](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/2705.png)
        
    - GCP
    - Digital Ocean
- Simple deploy of any public or private Docker image
- Auto CI/CD with [buildpacks](https://buildpacks.io/) for non-Dockerized apps
- Heroku-like GUI to monitor application status, logs, and history
- Application rollback to previously deployed versions
- Zero-downtime deploy and health checks
- Monitor CPU, RAM, and Network usage per deployment
- Marketplace for one click add-ons (e.g. MongoDB, Redis, PostgreSQL)

### DevOps Mode

For those who are familiar with Kubernetes and Helm:

- Connect to existing Kubernetes clusters that are not provisioned by Porter
- Visualize, deploy, and configure Helm charts via the GUI
- User-generated [form overlays](https://github.com/porter-dev/porter-charts/blob/master/docs/form-yaml-reference.md) for managing `values.yaml`
- In-depth view of releases, including revision histories and component graphs
- Rollback/update of existing releases, including editing of raw `values.yaml`

![porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/101073320-43322800-356d-11eb-9b69-a68bd951992e.png](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/101073320-43322800-356d-11eb-9b69-a68bd951992e.png)

## Docs

Below are instructions for a quickstart. For full documentation, please visit our [official Docs.](https://docs.getporter.dev/)

## Getting Started

1. 
    
    Sign up and log into [Porter Dashboard](https://dashboard.getporter.dev/).
    
2. 
    
    Create a Project and [put in your cloud provider credentials](https://docs.getporter.dev/docs/getting-started-with-porter-on-aws). Porter will automatically provision a Kubernetes cluster in your own cloud. It is also possible to [link up an existing Kubernetes cluster.](https://docs.getporter.dev/docs/cli-documentation#connecting-to-an-existing-cluster)
    
3.  Deploy your applications from a [git repository](https://docs.getporter.dev/docs/applications) or [Docker image registry](https://docs.getporter.dev/docs/cli-documentation#porter-docker-configure).
    
    ![porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/1f680.png](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/1f680.png)
    

## Running Porter Locally

While it requires a few additional steps, it is possible to run Porter locally. Follow [this guide](https://docs.getporter.dev/docs/running-porter-locally) to run the local version of Porter.

## Want to Help?

We welcome all contributions. If you're interested in contributing, please read our [contributing guide](https://github.com/porter-dev/porter/blob/master/CONTRIBUTING.md) and [join our Discord community](https://discord.gg/GJynMR3KXK).

![porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/103712859-def9ee00-4f88-11eb-804c-4b775d697ec4.jpeg](porter-dev%20porter%20Kubernetes%20powered%20PaaS%20that%20run%2025f5e75bea504818927bb23b8d61da78/103712859-def9ee00-4f88-11eb-804c-4b775d697ec4.jpeg)