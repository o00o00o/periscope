---
layout: project
title:  "Extreme Pomodoro (SDL)"
date:   2016-09-01 12:34:56
author: Steven Luo
categories:
- project
img: /isolation/icon_edited.jpg
carousel:
- /isolation/screen2.png
- /isolation/screen1.png
- /isolation/screen3.png
tagged: C++, SDL, Makefile
website: https://github.com/stluo/isolation
---
**Currently going through the process of packaging this application for open source Debian distribution**

**Learn:**

This was my first time using a open source framework and joining the open source community. I learned how to use SDL to directly access I/O inputs and control graphics rendering. I used SDL to grab all raw keyboard input which would prevent the user from using system keys such as alt-tab. I learned how to alpha blend my text with my background texture and many other techniques with computer graphics. Learning a new framework of this size was extremely difficult but having gone through this project I am much more confident working with official documentation.  Lastly I learned how to make a build system and manage source files. This is my biggest projects to date with 11 different source files using MAKE was an indispensable tool. My MAKEFILE stills needs improving but I was able to automate my build process and manage all the dependency.  

**Description:**

The point of this application is to use the Pomodoro technique combined with the 20-foot rule in order to help the user concentrate. The Pomodoro technique is a balance of study periods and short breaks. The 20-foot rule is when a psychological effect that when an object is 20 foot away, it will not distract you. When the user has a computer in front of them, they will easily get distracted. This application implements the 20-foot rule on the computer thus removing the distraction. The application will not allow users to alt-tab or stop the study session until the full time elapses. There is also a built in alarm to get the user back to work once a break is over.

**Features:**

- Hardcore mode: will not allow user to close application at all under any circumstance
- Softcore mode: require a button to be held for 1 minute to close
- Random rotating nature backgrounds
- Adjustable study and break periods
- System independent
- Easy to use and effective


**Challenge:**

This was the first time working with computer textures. I had a lot to learn regarding how a texture is handled and how a texture is generated. The order you draw your frames is also extremely important which was something that I was not aware of before. Things that I found to be extremely cool was alpha blending and the many different type of ways to manipulate a texture. Furthermore, since this application is “hardcore,” I wanted a program that you cannot get out of. In order for this to happen, it required taking the raw inputs from the keyboard and processing them directly.

**Goal:**

I want to put this project up on the Ubuntu store and this is not an easy process. As this is also my first step into the open source development world. To get something into the Debian repository you need to follow a long process and work with many other open source developers. What better way to entering a community than contributing to it?

**Special thanks to Kevin Ding for the background photos and Minda Yang for the Icon creation.**
