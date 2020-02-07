---
path: octopi-spaghettidetective
date: 2020-02-06T22:01:28.927Z
title: '3D Printing Remote Monitoring: OctoPrint/OctoPi + The Spaghetti Detective'
description: A guide to watching your 3D prints anywhere in the world.
---
Today I'm setting up [The Spaghetti Detective](https://www.thespaghettidetective.com/) to work with my Monoprice Maker Select Plus which I recently set up with OctoPi. This has been an absolute game changer -- it's allowed me to remote control my printer from any device with a web browser.

OctoPi itself is not too bad to set up, but it's probably the more difficult of the two tools to setup. You'll need a Raspberry Pi and a computer to flash the OctoPi image onto an SD card. Luckily, the instructions from OctoPi are pretty [straight forward](https://octoprint.org/download/)

Once you've got OctoPi on your Raspberry Pi and you've physically connected the Pi to your printer, you'll be able to launch jobs through your web browser by navigating to the URL `octopi`. It's pretty awesome, no more copying GCODE onto and SD card and then walking over to your printer. You can pretty much do all the controlling from your browser, cause there's a nice little interface:

![octopi interface](/assets/octopi-interface.png "octopi interface")

The webcam part is really cool, and should be easy to set up too. I had some trouble with my specific webcam, a Logitech Quickcam Pro 9000, but I found [this](https://community.octoprint.org/t/usb-webcam-randomly-connects-and-not-connect-on-startup-to-octopi/11805/5) to be pretty helpful. Basically, I had to kill the mjpg_streamer process on the pi (`sudo pkill mjpg_streamer`), then I configured the pi to use YUVY instead of MJPEG by adding a `-y` option to the file `/boot/octopi.txt`:

```
camera_usb_options="-r 1280x960 -f 5 -y
```

Now OctoPi by itself only works on your local network, so you'll need to be doing all of this from a computer that's connected to the same wifi network as your Raspberry Pi. You will not be able to monitor your prints when your out and about with your phone using cellular data.

But this is where The Spaghetti Detective comes in. Its the successor to OctoPrint Anywhere, a popular OctoPrint plugin that you can find a lot of guides for setting up. However, at the time of this post, OctoPrint Anywhere was no long free, so I decided to give the Spaghetti Detective a chance despite being hesitant at first (there's not as much information about it, but I liked that it's made by the same person as OctoPrint Anywhere, and the github repo has more stars anyway).

I think the killer feature that it has over its predecessor is it's AI-enhanced failure detection. It promises to be able to catch failed prints -- which in my own experience results in a mess of plastic spaghetti on the print bed -- hence its name. Since I've only tested one print with it, I'll have to see how good this feature is.

Anyways, setting up the Spaghetti Detective was dead simple. Just sign up with your Google or Facebook account, and then connect it to your OctoPi via their plugin (you'll have to copy an access token essentially). Now you'll be able to login from any device in the world and have access to your webcam and printer!

![](/assets/spaghettidetectiveinterface.png)

Unfortunately, there's the issue of pricing tiers with The Spaghetti Detective. There's a free tier, but since I only started using it I'm not sure how limited it really is. All I really wanted was webcam monitoring, so it's probably good enough for that. I think the paid tiers give you more hours for the failure detection, but I probably won't be using the failure detection so much, as I don't really plan on using this setup as an excuse to leave my house and printer unattended for hours. I don't think this is a totally fool-proof setup, and should not be considered a safe way to ensure your house doesn't burn down. Remember folks, there's always a risk of fire when you're using 3D printers, especially cause the technology is still in its infancy.

In the end, this was really just an experiment to see if it was possible to 100% remotely monitor and control my printer. I would say it was successful, but I'd still planning on only printing when I'm at home. I'll give it 10 years or so before this technology is stable enough that you could just leave your printer unattended while your outside your house -- similar to the way you'd leave your washer and dryer unattended (who wants to wait around for their laundry to finish?). Until then, unattended 3D printing is a lot closer to leaving the oven on while your away, and most people aren't dumb enough to do that.
