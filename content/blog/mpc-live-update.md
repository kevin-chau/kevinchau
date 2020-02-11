---
path: mpc-live-update
date: 2020-02-10T22:14:00.000Z
title: How to Update your MPC Live to Firmware v2.7
description: Firmware update walkthrough for the MPC Live
---
![MPC Live Firmware 2.7](https://d1jtxvnvoxswj8.cloudfront.net/wysiwyg/akai-pro/news/Force_MPC_Ableton_Web_Banner.jpg)
Hey folks! Today I finally took my dusty old MPC Live off the shelf because I needed a controller for an Ableton drum synthesis tutorial I was following and it was the only instrument I had with velocity-sensitive pads -- perfect for finger drumming.

After plugging in the MPC to my macbook via a USB cable and powering it on (holy moly there's still charge in the built-in battery?), I was suprised to see that there was no MIDI input showing up in Ableton despite me hammering away at the pads. Well, turns on this isn't exactly a feature that is directly supported. There is a "MIDI CONTROL" mode built it, but this sends out MIDI information through the 5 pin DIN output, and me being too lazy to dig out my MIDI cable to connect to my audio interface, I decided to look for another solution.

A quick search on Google showed me that the latest [firmware update](https://www.akaipro.com/newsflash-ableton-live-integration) for the MPC just added Ableton Live Control integration. Perfect! 

As a side note, I've super glad that AKAI has continued to breath life into the MPC Live with continual free updates, and has absolutely added do the value of the instrument even after the original purchase date. I've basically been getting free features and content over the years, and with version 2.7 I'm getting the exact feature I needed. 

The latest update promises built-in control of Ableton's mixer and clip launching, all through Ableton's fancy new Link software, either over ethernet or wifi. Given my interest in Link (it's an open source project on [GitHub](https://github.com/Ableton/link)!), I figured this was the perfect opportunity to see how far they've gotten with expanded their software ecosystem.

# How to update the MPC Live
Updating the MPC should be pretty straight forward. Since version 2.6, it's been possible to update the MPC directly from your Windows or macOS computer. [Here's](https://www.akaipro.com/kb/akai-pro-mpc-x-and-mpc-live-firmware-update-2-6-walkthrough#COMPUTER) their official guide on updating to 2.6. But since there's no walkthrough specifically for version 2.7, and since the last time I had to do it with a USB stick (my MPC Live is currently on 2.4), I decided to walk you through the process myself. Here we go.

First I went over to the MPC Live support page and then navigating to their [downloads](https://www.akaipro.com/mpc-live) section. Since I'm a hardcore mac user, I selected the file called "MPC X/Live/One-2.7.2 Firmware Update (Mac)" to download. This gives you a nice little zip file that when extracted has the Application called "MPC Live 2.7.2 Updater". Double clicking on it gave my macOS's standard warning that says the developer can't be verified, but since I trust AKAI didn't put any malware in their updater, I went ahead and opened it "anyway" by going to the "Security & Privacy" page in macOS's System Preferences. Annoying, but whatever.

![updatempc](/assets/updatempc.png)

Cool. Super simple interface with one button. Let's click it:

![updatempc2](/assets/updatempc2.png)

My MPC Live was already connected via USB so I was hoping it would auto detect but it's pretty standard for you to have to put your instrument into some sort of special update mode whenever you update firmware. I assume it's for safety reasons so you don't accidentally update.

Following the instructions, I went to the settings > INFO > Shift + Update. The MPC Live asked me "Are you sure you want to restart your MPC in update mode?". ***Hell Yeah*** I'm sure. 

After restarting the MPC, I tried clicking the update button in the software on my computer again. No detect. A quick unplug-and-plug-back-in did the trick, but this time the software asked me to connect the MPC live to a power source (did I mention I was using the MPC in battery mode, and it still had 39% despite not being fully charged -- or used -- in several months?).

![updatempc3](/assets/updatempc3.png)

Again, this is pretty standard when updating any device. If your device runs out of power when updating, you'll probably brick it and have to send it in to get fixed.

After plugging in the power cable, the update was finally under way!

![updatempc4](/assets/updatempc4.png)

 Once the transfer was complete, the MPC restarted itself and then there was one more screen confirming the update. That's it folks, your MPC Live is now on the latest firmware! Right away I saw a fancy new interface, but I went ahead and nagivating to settings > INFO again to double check the firmware version number, cause you know, version numbers matter. 2.7.2 Baby!

# Testing out Live Control
Now for the fun part. I want to try testing out Ableton Link using WiFi since I don't have a USB-to-ethernet adapter that I could use for the MPC Live. Actually, I'd need two, since my macbook doesn't have any ethernet ports either, just USB-C. Obviously, wi-fi is going to introduce a ton of lag and make it not really useable as a real-time controller, which is why the official instructions in AKAI's [youtube video](https://www.youtube.com/watch?v=hY2PRqZLHos) recommend using an ethernet cable. But the idea of Link is that it doesn't matter how you're connected, it's all the same software interface.

The first step was to connect my MPC Live to my house's network. I didn't even know the MPC had a wifi chip or connection feature at all, but I did a quick check for it even before I updated the firmware, and indeed it was there. This leads me to believe it was supported from the beginning and Live integration has been in their plans for many years, even before releasing the product. Good on you AKAI. Anyways, you can connect the MPC to any wifi network in the Settings.

The next step is to turn on Link in Ableton via the button in the top left corner. The video is pretty clear on how to do this, so refer to that. It didn't work for me right away however, and it turns out I had forgotten to download the additional software "Akai Professional Network MIDI Driver", which you can also download from the MPC Live support page. After installing that, I was finally able to view the Ableton Session interface from inside my MPC Live! Woohoo!!!!! 

To my surprise, the input latency was not bad at all, so I decided to test it out with a drum rack. Unfortunately, instead of clean drum hits, I got a weird mess of garbled sound, almost as if the Link was sending a ton of sub-millisecond inputs to the sampler. It was however quite reactive and fast, and I'm assuming it would work just fine for clip launching, as is their intended/demonstrated use case in the video. The touch screen interface itself is just an exact copy of Ableton's session view, so I'm sure it's optimized and works well for that.

Well there you have it folks, a complete guide to firmware updating the MPC Live and a glimpse into the future of wireless Ableton instruments. Oh how far we've come. Hope you had fun!
