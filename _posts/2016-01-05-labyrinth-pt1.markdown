---
layout: post
title:  "Phoenix Labyrinth - Building the Game"
date:   2016-01-05 14:22:06
categories: ElixirConf 2015
banner_image: "/media/labyrinth/labyrinth.jpg"
featured: true
comments: true
---

Labyrinth is a game where the goal is to navigate a steel ball through a maze without falling through any of the holes in the game board.  The desktop version of the game consists of a box with a tilting game board which is controlled by two knobs.

<!--more-->

Some labyrinth games offer the ability to swap out game boards allowing the user to select the level of difficulty.  The game I purchased, as illustrated above, did not offer this ability.  It shipped with a 60 hole board and playing it manually was quite challenging.  

The original idea for this experiment was to demonstrate the use of the ObjC PhoenixClient.  This client library facilitates streaming connections between iOS devices and PhoenixFramework based applications using the Phoenix Channel abstraction.  At a simple level, the project maps the pitch and roll axis data of the iPhone gyro to a servo connected to the corresponding axis on the game board.  The entire system is powered by a BeagleBone Black which boots directly to our Phoenix App using the [Nerves Framework][nerves-home]. The source for both the Phoenix app and the iPhone app are available on [github][labyrinth_src]



## Parts

To create this project you will need a few things.

- A BeagleBone Black
- 2 Standard [Servo motors][amazon-servos]
- 5 VDC Power Adapter
- Breadboard and jumpers

It is highly recommended to get an AC -> 5V DC power adapter that has a high amperage rating. Do no attempt to run the BeagleBone off USB power or even through the URB port powered by an iPhone charger or something. With two servo motors the current draw is too high and will either brown out the BeagleBone or damage your power supply / computer. Additionally, If you would like to have the ability to connect directly to the BeagleBone to see whats going on and maybe type commands directly into IEX, purchase an [FTDI Cable](https://www.sparkfun.com/products/9718).  You can connect this cable to the serial debug interface pins. Make sure to connect the cable to the header in the correct orientation, Notice the ground pin side.

![Image of BeagleBone Serial](/media/labyrinth/beaglebone-black-serial.jpg)

## Connecting Servos

Wiring the system is fairly basic. We can derrive power from the 5VDC adapter to power both our servo motors and our BeagleBone Black. Follow the layout below for information on how to wire the power and signal pins.

![Image Breadboard](/media/labyrinth/labyrinth_wiring.jpg)

You can edit and open the breadboard and schematic in fritzig direcly.
[labyrinth-fritzig](https://github.com/mobileoverlord/labyrinth/blob/master/labyrinth_sketch.fzz)

In the next article we will Deploy the nerves app onto the board, and control the servos.

[amazon-servos]: http://www.amazon.com/Hitec-31311S-HS-311-Standard-Universal/dp/B0006O3WVE/ref=sr_1_1?s=toys-and-games&ie=UTF8&qid=1444139671&sr=1-1&keywords=servo
[nerves-home]: http://nerves-project.org
[labyrinth_src]: https://github.com/mobileoverlord/labyrinth
