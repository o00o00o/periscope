---
layout: post          
title: "Distributing Applications With Ubuntu Snapcraft"
date: 2017-02-23 12:34:56
author: Steven
categories:
- blog
- Code             
- Snapcraft
- Ubuntu
img: snapcraft2.jpg       
thumb: snapcraft_thumb.jpg    
---
Snapcraft is a set of tools that allows developers to craft packages for multiple Linux distributions. These packages (.snap) are completely self contained with built in security policies such as confinement protocols.
<!--more-->

This is a quick pedal to the metal guide for creating a snap and uploading it for distribution on the Ubuntu Software Center. I created this guide after trying to ship my [Extreme Prodomo](http://www.swluo.me/project/Extreme-Pomodoro). In the process, I even had to file some bug fixes with Canonical! I will say that they were extremely professional and have respect for the open-source community.

To start things off we need to make sure Snapcraft is installed.


```
$ sudo apt install snapcraft
$ sudo apt install build-essential
```

Now that Snapcraft is installed you can try installing a [demo](https://tutorials.ubuntu.com/tutorial/basic-snap-usage?utm_source=snapcraft.io&utm_medium=buildsnapsindex&utm_campaign=tutorials&_ga=1.11867060.1298965547.1473039303#0) or creating your own!



```
$ snapcraft init
```

Snapcraft init creates a snapcraft.yaml, which is the recipe of your snap. All the information needed to create a snap will be stored here. The default yaml will look like this:

```
name: my-snap-name # you probably want to 'snapcraft register <name>'
version: '0.1' # just for humans, typically '1.2+git' or '1.3.2'
summary: Single-line elevator pitch for your amazing snap # 79 char long summary
description: |
  This is my-snap's description. You have a paragraph or two to tell the
  most important story about your snap. Keep it under 100 words though,
  we live in tweetspace and your description wants to look good in the snap
  store.

grade: devel # must be 'stable' to release into candidate/stable channels
confinement: devmode # use 'strict' once you have the right plugs and slots

parts:
  my-part:
    # See 'snapcraft plugins'
    plugin: nil
```
<br/>
Important things to note, the name of the snap is not necessarily the command to start your application. This name needs to be registered with the Ubuntu Software Center when you decide to upload.

**version, Summary, and description:** Are self explanatory. <br/>
**grade:** Determines what channels your application can be released onto and is a nice way of having beta builds. <br/>
**confinement:** This is extremely important. Not only does it determine what channels your application can go, it also defines the security policies that your application is forced under. [Here](https://snapcraft.io/docs/reference/confinement) is a full description of each confinement level. Note, if you decide to use classic, there will be a manual review of your application before release. <br/>

**parts:** This keyword stands for the building blocks that will make up your snap. This is where the source code and the compile tools are used. Snapcraft supports tons of plugins that will make building easy and it can work with remote sources such as Git repos. Below is what my parts section looks like:

```parts:
    my-parts:
        source: .
        stage-packages:
                        - libsdl2-dev
                        - libsdl2-image-dev
                        - libsdl2-ttf-dev
                        - libsdl2-mixer-dev
        plugin: make
        install: |
                 mv run /home/swluo/code/isolation/prime/
                 mv img /home/swluo/code/isolation/prime/
                 mv font /home/swluo/code/isolation/prime/
                 mv sound /home/swluo/code/isolation/prime/
                 mv settings.txt /home/swluo/code/isolation/prime/
```

**source:** Defines the location of your source files, could be remote or local. In my case, they are local files. <br/>
**stage-packages:** This is where the magic of Snapcraft comes in. These are the necessary dependencies that my application requires. By listing them as stage-packages Snapcraft will automatically install them from apt if need! This allows the .snap to be completely self contained! <br/>
**plugin:** A huge list of [plugins](https://snapcraft.io/docs/reference/plugins/) are supported; my build uses make. <br/>
**install:** The install keyword denote commands that are executed after the plugin has finished. You can almost do anything you want! <br/> <br/>

An important part of the yaml that is not created by default is the apps section:

```
apps:
  concentration:
    command: run
    plugs: [ x11, mir ]           
```

The apps part of the yaml describes how to run the application. <br/>
**concentration:** This is the command that will launch your application from your terminal. You want to make sure that there are no conflicting names with commands such as “grep.” <br/>
**command:** This is the command that will be executed. To clarify, my make file will create the executable call "run”, located in my prime folder (more on this later). When the user types in "concentration" the system calls "./run" <br/>
**plugs:** Depending on your application you might need to use certain plugs. Plugs are also known as interfaces which define things such as access to the webcam. A list of plugs are available [here](https://snapcraft.io/docs/reference/interfaces) <br/>

<br/>
Now that your yaml is completed, we can go ahead and create our .snapcraft

```
$ snapcraft
```
The summary of what happens after you snap a package is: <br/>
1. **Pull:** snapcraft pulls the required code and dependencies from either apt, remote, or locally <br/>
2. **Build:** using the built-in plugins such as make <br/>
3. **Stage:** you will see that snapcraft will create a subfolder in your directory call stages. Here is where all the files that snapcraft needs to create your .snap <br/>
4. **Snap:** here is when everything is completed. You will result in a .snap which can be uploaded to the Software Center <br/>

**Prime:** If you applications needs assets such as images like mine does, you need to put these files into the prime folder that is also generated. Everything in the prime folder is what your application can have access to. When your application is installed, the prime folder is placed in /snap/"name_of_application." There are lots of ways of doing this. An easy way is to run commands during the build, you can do this by listing commands under the "install" keyword (above).

**Congratulations!** If everything worked properly, you should have created your first snap. There is a complete GUI for the upload process by going online to [myapps.developer.ubuntu.com](https://myapps.developer.ubuntu.com/dev/click-apps/). In the command line, upload and distribute your application simply by logging into your Ubuntu developer account.

```
$ snapcraft login
```
Reserve a name for your snap

```
$ snapcraft register concentration
```
Upload

```
$ snapcraft push concentration_stable_amd64.snap
```
And finally release!

```
snapcraft release concentration1 stable
```

Now your snap is available for users to install. <br/>
**Note:** It might be important to learn about the different [channels](https://snapcraft.io/docs/build-snaps/publish) that you can release your application in. Also dealing with [naming disputes](https://snapcraft.io/docs/build-snaps/publish). If you need any help, refer to the [official documentation](https://snapcraft.io/docs/) or reach out to me.

<br/>
My next step is learning about the auto build feature for Github. There is support for an automatic build-snap-release every time a specified branch is updated in Github. This will be a cool feature that will allow open-source developers access to the latest possible builds with ease.
