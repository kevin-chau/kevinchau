---
path: digitone-update
date: 2020-02-21T14:00:00.000Z
title: Updating my Elektron Digitone to OS 1.21
description: Updating from OS 1.10A to OS 1.21, and a closer look at SysEx tools in the era of macOS
---
![digitone](https://media.sweetwater.com/api/i/q-82__ha-881632ee9fc14431__hmac-2d2a94fa1a40e745f631db12455dad50be90f42e/images/items/750/DigiTone-large.jpg)
So today I was following [this](https://www.youtube.com/watch?v=j7Y0DBsFtm4) tutorial for creating 303 acid bass sounds on the Elektron [Digitone](https://www.elektron.se/products/digitone/) when I noticed that my Digitone was missing the portamento feature. I've been updating all my music equipment lately so I figured that I was behind a few firmware versions. A quick power reset of my Digitone confirmed it was on OS 1.10A, "operating system" apparently being the term Elektron likes to use to mean firmware.

Heading over to the [Digitone support page](https://www.elektron.se/support/?connection=digitone#resources), I found their latest release is OS 1.21. I'm quite behind, so time for an update! I also reminded that I'm yet to try out the Overbridge 2.0 beta, but I'll get to that another time.

# Updating to OS 1.21 -- Sysex!?!
First thing I did was download the update. It comes as a zip, and I was hoping that once I extracted it there would be a nice updater bundled. Nope. It's just a sysex file. I'm not too familiar with sysex files but I knew it essentially meant that I had to transfer the file over manually to the digitone to update it. Luckily, the zip came with a nice "How-to" in html format so I opened that up for instructions on how to update.

Elektron gives you two options to upgrade:

- **A.** Upgrade from within the OS: This let's you update while the Digitone is on in it's normal operating mode. If you choose this option, you can send the sysex file over MIDI or USB.

- **B.** Upgrade from the "Early Startup Menu": You'll need to hold the `FUNC` button while turning on the Digitone, which puts you in a special update mode. This option only lets you transfer over MIDI and NOT USB.

Since option A is significantly easier and simpler, and most people are more likely to have an open USB port on their computer as opposed to having an audio interface with MIDI out capabilities, I'm not really sure why they give you two choices in the instructions. I don't really see an advantage to transferring the sysex file over MIDI, but I guess it's always better to have multiple options. Maybe some people don't have access to a computer and need to update their Digitone by sending the sysex file from another MIDI instrument like an MPC or something, I don't know.

## I'm going with USB. Now what?
Once I decided on option A, I busted out my USB-A to USB-B cable (I used the fancy braided cable made by Elektron) and connected the Digitone to my Macbook with it. In the Digitone, I navigated to `Settings > System > OS Upgrade`, and then my Digitone prompted "OS UPGRADE WAITING FOR SYSEX".

I was kind of hoping that the Digitone would pop up in Finder as an external drive and I could just drag over the sysex update to copy it, but of course it's not that simple. In reality, you usually need another software tool to send sysex over USB. The instructions from Elektron suggest using their own C6 tool. There wasn't a direct link to the tool, so I headed back over to the Digitone support page.

Luckily the support page has a direct download link for `C6 SysEx Manager + Manual`. Unfortunately, it says it was last updated on May 23, 2013, for version 1.51, and it's compatible with OSX. Uh-oh. 

At this point I'm praying to god C6 is compatible with macOS, but I'm doubtful because it's been a long time since Apple made the switch from OSX to macOS and even longer since Elektron updated C6. Opening up the `.dmg` file confirmed my suspicions, I was promptly notified by macOS that C6 was not compatible:

![c6update](/assets/c6update.png)

## Is Elektron C6 SysEx tool dead? Yup. Enter SysEx Librarian

A quick google search reveals that Elektron has effectively stopped development on C6 and they do not plan to update the software to 64-bit to maintain compatibility with macOS 10.15 Catalina. [Here is an Elektronauts post about it](https://www.elektronauts.com/t/c6-sysex-manager-not-getting-catalina-64-bit-update/106193). Great. Time to find a 3rd party tool not officially endorsed by Elektron. We're heading into murky waters now.

Another google search for specifically the term [`sysex`](https://www.google.com/search?q=sysex) shows a top result called "SysEx Librarian" by Snoize. Referencing the Elektronauts post, this seemed like a popular alternative so I was willing to give it a shot. A closer inspection of [Snoize.com](https://www.snoize.com/) reveals that the code for all their tools including SysEx Librarian is open-sourced, and it's even hosted on [GitHub](https://github.com/krevis/MIDIApps)! A huge win in my book. Let's download and install it.

It's currently at version 1.4 -- I don't know why I always have to mention the version number of everything but I just do. The download comes as a zip which contains the application, so I copied it over to my `Applications` folder. Super easy to install, you gotta love open source software, right?

## Sending the Digitone OS 1.21 SysEx update file via SysEx Librarian
Well this about as manual as it gets when it comes to firmware updating your kic music instruments. I'm going to preface this section by saying none of this is officially supported by Elektron and the following instructions could have the potential to totally brick your instrument if you don't follow them carefully. Proceed with caution and at your own risk.

There's an Elektronauts [post](https://www.elektronauts.com/t/how-do-i-update-digitone-os-on-a-mac-using-sysex-librarian-step-by-step-needed/107847/2) I found explaining how to use SysEx Librian to update the Digitone, so refer to that for more information. Here was my process:

#### 1. Connect the Digitone to your computer using the included USB cable.

#### 2. Open SysEx Librarian, and in the `Destination` menu, select `Digitone out 1` as the destination.

#### 3. Drag the file `Digitone_and_Digitone_Keys_OS1.21.syx` into SysEx Librarian under the `SysEx File` section. 

After this step, SysEx Librarian should now look like this:

![sysexlibrarian](/assets/sysexlibrarian.png)

#### 4. Press `Play` in SysEx Librarian

You should now see a progress bar, showing the number of messages and the amount of data sent to the Digitone, as well as a progress bar on the Digitone itself saying "OS UPGRADDE RECEIVING. Interesetingly, I noted that the update sysex file contained 11094 messages. At 400/11094 messages, it had sent rougly 50 KB of data. That's pretty darn slow. 

![sysexprogress](/assets/sysexprogress.png)

It goes without saying that you do not want to unplug your Digitone during this process, or you'll completely brick it. It's also a shame that the transfer is so slow, because even an unexpected power failure in your house or surge protector could kill your Digitone. Definitely take into consideration the stability of your power source while doing this update, and maybe even consider having some sort of backup power solution. I'm actually writing this post as the transfer is happening, and I'm estimating it takes no less than 20 minutes of uninterrupted power. Elektron, please come up with a better update solution on your next iteration of the Digitone, we will all greatly appreciate it.

## OS UPGRADE RECEIVING... SUCCESS!
After holding my breath for what seemed like forever, the update transfer was done! The Digitone let me know the transfer was successful and then proceeded to perform an additional boostrap upgrade. After that, it displayed "BOOSTRAP UPGRADE COMPETE PLEASE RESTART ME". A quick toggle of the power switch and BOOM, I now have Digitone OS 1.21! 

Finally equipped with Portamento, I went back to the youtube tutorial I was following and continued on my way to synthesizing some of that righteous 303 acid bass. Cheers, and see you in the next one!

### Epilogue: A note on Elektron Transfer
There is an official Elektron application with macOS compatibility called [Transfer](https://www.elektron.se/support/?connection=transfer#resources), but it looks like they haven't updated it to work with Digitone yet. When I tried using it, I got this error:

![elektrontransfererror](/assets/elektrontransfererror.png)

It works with a lot of their other instruments, but specifically not Digitone. Their last udpate was in March 2018, which was long enough ago that they should have added Digitone support by now. There really is no reason that I should have to use SysEx Librarian to manually update my Digitone. Elektron, please update your SysEx tools.

If you're curious, here are a few Elektronauts posts about Transfer and Digitone support:

https://www.elektronauts.com/t/elektron-transfer-cant-connect-to-digitone/60423

https://www.elektronauts.com/t/update-digitone/51756

https://www.elektronauts.com/t/unable-to-upgrade-digitone-os-using-elektron-transfer/53412/3