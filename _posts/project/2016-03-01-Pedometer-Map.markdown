---
layout: project
title:  "Pedometer Map"
date:   2016-03-01 12:34:56
author: Steven Luo
categories:
- project
img: /pedomap/pedomap_icon.jpg
carousel:
- /pedomap/pedomap1.jpg
- /pedomap/pedomap2.jpg
tagged: Android, Java, Accelerometer, Low Bypass Filter
website: https://github.com/o00o00o/Pedometer-Map
---
**Learn:**

This was the first time that I have developed on the android system. It is extremely interesting how each embedded system worked with each other. There are a lot of platform specific things like onCreate, onResume, and permissions that I had to learn. Learning to read and understand the official documentation from Google was extremely helpful with solving issues. Furthermore, this was the first time working with team members so we used SVN as a version control system to collaborate efficiently. Learning how to use a version control efficiently while working with teammates was very rewarding.

**Features:**

* Detect footsteps
* Set start and end locations
* Find direct route to end location
* Update position on SVG map
* Record displayment
* Graph sensor data

**Discription:**

WWe needed to deliver code every 2 weeks to meet deliverables. This was akin to a sprint in an agile development cycle. At the end of our project the application was able to detect the number of steps the user took and update position on the SVG map with each step. We also implemented a way to drop a start and stop waypoint with a recursive path finding algorithm. This was able to find a direct route from anywhere on the map.

**Challange:**

The challenge was implementing the 2 algorithms we need for this project. I was responsible for the first algorithm which was step detection. Using a finite state machine, I was able to accurately detect a step using the onboard accelerometer with an low bypass filter. I also helped brainstorm and debug the recursive path finding algorithm. We first tired a wall following implementation but ended up using navigation waypoint in instead. The feeling when the app worked as intended was indescribable. We were able to meet the all the deliverable on time with a 95% project mark.
