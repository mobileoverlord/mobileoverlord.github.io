---
layout: post
title:  "Save room for more Pi"
date:   2016-03-27 10:00:00
categories: Nerves Development
banner_image: "/media/bakeware/home.jpg"
featured: true
comments: true
---
Nerves system 0.4.0 release is going to be jam packed with wonderful goodies like support for more Pi's. With the release of 0.4.0-rc3 brings Pi3 support with thanks to [fairbanksg](https://github.com/fairbanksg). All these new features are just begging to be enabled.
<!--more-->

## The Pi Collection

The Raspberry Pi is one fantastic collection of boards. There is one for almost every project. From the low power A+, to the Zero, Raspberry Pi makes embedded linux available to more developers.

I am very excited to see Nerves support for the Pi3. With built in bluetooth and wifi, its is an all inclusive environment for Nerves development. No more will we have to carry around a case full of boards, adapters, a display.... hum, well. I guess we can't ditch that display just yet. But we will be able to soon.

## Bluetooth and Wifi

First, thanks to the community for your patience with wifi, we have been working on adding support but it required us to tackle bigger underlying issues first. Now that the Pi 3 has on board wifi and bluetooth, it shouldn't be long before we bring that into your nerves apps. As of today, 0.4.0 images bring wpa supplicant and a handful of wifi drivers, but not bluetooth.

Bluetooth support will probably not be added directly to our minimal images due to the amount of dependancies required. This would make the system images a lot bigger and not everyone is going to require bluetooth . To handle this, we are working on a mechanism for aggregating defconfig and root filesystem additions down to the system config so a base system can be "extended" to contain additional packages, settings, and or files. Doing this will require the system to be rebuilt with the newly merged configuration and rootfs-additions which we have been "avoiding" due to complexities in enabling this on Mac OS. In the (near) future, this process will configured as an adapter to the Nerves system compiler. You will be able to create and specify providers who can carry out the job for you. By default, the Nerves system compiler will ship with two providers, Local and Bakeware. For Linux hosts, you can you either provider, Mac OS hosts will need to use the Bakeware provider.

## The Future

The way we develop Nerves applications is about to change, too much to get into the specifics in this article. When Bake was introduced, the community was opened up to fast approach to creating embedded Elixir firmware. This is only just scratching the surface. We have created a mechanism for exposing access to all levels letting developer choose where they want to display the console, hdmi / serial, how to layout the partition structure, and so much more. Keep posted for more information about how Nerves is integrating with `mix` and how developing Nerves applications will be as easy as `mix firmware`
