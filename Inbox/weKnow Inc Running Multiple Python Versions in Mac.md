# weKnow Inc | Running Multiple Python Versions in Mac OSX

Source: Article
Status: Unprocessed
URL: https://weknowinc.com/blog/running-multiple-python-versions-mac-osx

![https://weknowinc.com/static/a76639bf0723b6f77f510c86797dae7a/14b42/default-drupal-weknowinc.jpg](https://weknowinc.com/static/a76639bf0723b6f77f510c86797dae7a/14b42/default-drupal-weknowinc.jpg)

---

Last few months I have been delving into Data Science and Machine Learning.

Both fields are related. In fact, in my opinion [Data Science](https://en.wikipedia.org/wiki/Data_science) could be considered almost a prerequisite for [Machine Learning](https://en.wikipedia.org/wiki/Machine_learning).

These are not only related to data manipulation and statistic concepts, but they are also connected in terms of what program language is commonly used, which is [Python](https://www.python.org/).

One of the blockers I quickly faced related to my environment. Python has two versions actively used, Python 2.x and 3.x. Python 2.x is the legacy version, and Python 3.x is the present and future of Python, but some of the less disruptive improvements in 3.0 and 3.1 have been backported to 2.6 and 2.7, respectively.

Regarding the materials available to learn about Data Science and Machine Learning you need the ability to switch between those Python versions, and that is precisely what I want to cover in this blog post.

## Assumptions

For this article, I will use my environment as an example. I am running a macOS High Sierra 10.13.3, this specific version came with Python 2.7.10, which is a legacy version.

As an add-on, in this article, I will use a specific solution to setup an environment to run Python using [Fish Shell](https://fishshell.com/).

If you want to know more about how to setup Fish in your local environment, the article [Improve your shell using Fish and Oh My Fish](https://jmolivas.weknowinc.com/improve-your-shell-using-fish-and-oh-my-fish) is precisely what you need.

## Uninstall the previous Python

It is possible that before needing a different version of python you choose to update your Python version.

If you use [HomeBrew](https://brew.sh/) to install Python, you could uninstall running the following command.

```
$ brew uninstall --ignore-dependencies python
```

You may be familiar with the [Anaconda Distribution](https://www.anaconda.com/). Anaconda Inc is the creator of the Anaconda Distribution that includes hundreds of popular data science and machine learning packages and the Conda package manager.

If this is your case follow the next steps to remove that installation. Don't worry, nothing is going to break (at least not for now, I hope :P ).

Determine where your Python is located with the following command

In my case, it points me to the following path ***/Users/******enzo******/anaconda3/bin/python***

If you were using your Python from Anaconda, after removing Python remember to edit your ***~/.bash_profile*** to remove Anaconda path from your ***$PATH*** environment variable.

Since I was using Fish Shell, I did something similar to the following snippet of code in my ***~/.config/fish/config.fish*** file.

I had to remove the following lines:

The final step is to remove the Python files:

```
$ rm -rf ~/anaconda3/

$ rm -rf ~/.conda/
```

To be able to switch quickly between different versions of Python, we will use [Pyenv](https://github.com/pyenv/pyenv).

Installing Pyenv on Mac OS X is very simple with Homebrew:

Pyenv requires some extra instructions after installed that are documented for bash and sadly bash scripting is not compatible with Fish. Fortunately, there is a plugin that does the magic.

Before installing the plugin, we need to install [Fisherman](https://github.com/fisherman/fisherman), which is a plugin manager for Fish. You can search for Fisherman's complete list of plugins [here](https://fisherman.github.io/).

To install Fisherman, just execute the following command that runs the installer:

```
$ curl -Lo ~/.config/fish/functions/fisher.fish --create-dirs https://git.io/fisher
```

The installer doesn’t indicate anything, but don’t worry. In this case, "no news is good news."

Now we need to install the [pyenv](https://github.com/fisherman/pyenv) plugin to be able to use it in Fish

```
$ fisher add fisherman/pyenv
```

[weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/iFjSP7KFN_pXtEqc1McuO-brxOmxINo8HZOQ4_W0WgoYLN2w02irH-Qlgh7_i6NeOYfXBUxyf3weKFgbqDMYjmpMkfObZoXD8g1lHOO3T5NtbpkOxjemMS-I6LmkroshSzauynv2](weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/iFjSP7KFN_pXtEqc1McuO-brxOmxINo8HZOQ4_W0WgoYLN2w02irH-Qlgh7_i6NeOYfXBUxyf3weKFgbqDMYjmpMkfObZoXD8g1lHOO3T5NtbpkOxjemMS-I6LmkroshSzauynv2)

Install your different Pythons

With everything setup, you need to define what do you want to install on your machine, in my case I want to have Python 2.x and 3.x

To check all versions available execute this command

The list is long, but let's explore some of them. As you can see in the following image you could just choose the specific version required.

[weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/NQUyjBdBX-rVR9g-b7NEcwqbtAAjJBhFWTIhHJKvQe7pgW52TLCjEaDaHkHYZekwgEyJPMlZhcbped6sye_Z1omoCr1H9JF3uv0Eh8eycGROanxq8_Gm-aSIVGTBGq3Fw1-vWiBz](weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/NQUyjBdBX-rVR9g-b7NEcwqbtAAjJBhFWTIhHJKvQe7pgW52TLCjEaDaHkHYZekwgEyJPMlZhcbped6sye_Z1omoCr1H9JF3uv0Eh8eycGROanxq8_Gm-aSIVGTBGq3Fw1-vWiBz)

But there are also options that contain some extra programs, like Miniconda, which is a package manager that enables us to install python packages such as Numpy, Pandas, etc. At the end, each package will include a different version of Python depending on their own requirements.

[weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/0ck312uep_jQ42gYo7hkF96D1fcTgP6Yu4gO_eg8h-h9jUY2-D7bTtmT81bRTZ0sFLcfDdqnjl7868D_xHnsE2ULJitVBUKJoZpQXu4m0AKpfVl78UThEWweEq8tPlWrG6FwFhrw](weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/0ck312uep_jQ42gYo7hkF96D1fcTgP6Yu4gO_eg8h-h9jUY2-D7bTtmT81bRTZ0sFLcfDdqnjl7868D_xHnsE2ULJitVBUKJoZpQXu4m0AKpfVl78UThEWweEq8tPlWrG6FwFhrw)

First I want to install Python 3.6.4

```
$ pyenv install 3.6.4
```

This command will download the sources and build/compile Python in your system, so this could take several minutes.

But also, it is possible that the build fails with the following error.

**Error: can't decompress data; zlib not available**

There are two possible solutions for that.

```
$ brew install readline xz
```

After installing or updating, if the problem remains, check the next option.

Download [Xcode](https://developer.apple.com/xcode/) on your machine

To install your second version of Python only choose the version required

```
$ pyenv install  2.7.14
```

### Managing your version of Python

It is important to mention that you need to activate your Python, because downloading it is not enough to use it.

To get a list of all Python version available to be activated, execute the next command.

[weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/Pk_2uD73_OIDr0YuczJF7XbThJZxvlcbiSvA1le1HzwftmCqCI9165v9wiNH4a86nW9ur8FhA8GxR6CF7iAjEHWlEJdS1d21LcaCO_R9oiURSzfsfccqRaIbCgH_XqBOzeZkz5rk](weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/Pk_2uD73_OIDr0YuczJF7XbThJZxvlcbiSvA1le1HzwftmCqCI9165v9wiNH4a86nW9ur8FhA8GxR6CF7iAjEHWlEJdS1d21LcaCO_R9oiURSzfsfccqRaIbCgH_XqBOzeZkz5rk)

The star symbol marks the currently active version if there is one active.

To set our default version to be Python 3.6.4 just run the next instruction.

```
$ pyenv global 3.6.4
```

[weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/cczEb3mocXz8FKT6YV1zQIZSTz1ltmiEYLvYidujEqz2kU5X-er6pB5ilX6GbXvC9rlnmSQcsBKKNh5NwoTE0EbnxVfo4khNnXD47T8nZbkZ9ncg6EzYiuKz8D0Idrg3eWomWdCX](weKnow%20Inc%20Running%20Multiple%20Python%20Versions%20in%20Mac%205a6e0833b532408ab880ce3ce09d1ab7/cczEb3mocXz8FKT6YV1zQIZSTz1ltmiEYLvYidujEqz2kU5X-er6pB5ilX6GbXvC9rlnmSQcsBKKNh5NwoTE0EbnxVfo4khNnXD47T8nZbkZ9ncg6EzYiuKz8D0Idrg3eWomWdCX)

Setting a local version

If there is a project that requires a legacy version like Python 2.7.14, you need to go to the project’s folder and execute this command inside the folder:

This command will create the hidden file ***.python-version***, which contains the specific version of Python required to execute this project.

If you run any Python script outside this specific folder, the Python version to be used will be the global version.

If you have reached this section, it means that now you can setup your environment correctly, and there is no excuse to not continue rocking in Data Science or Machine Learning!

Hail Skynet, Hail Hydra

## Related articles