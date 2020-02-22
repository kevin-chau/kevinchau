---
path: digitakt-update
date: 2020-02-22T14:00:00.000Z
title: Updating my Elektron Digitakt to OS 1.11
description: Updating the Elektron Digitakt from OS 1.10A to OS 1.11
---

Hey everyone, this post is a follow-up to yesterday's post on updating my Digitone. I'm going to go through the same update process with my [Digitakt](https://www.elektron.se/products/digitakt/), but it should be a lot more straight forward now that I know what to do and because Elektron [Transfer](https://www.elektron.se/support/?connection=transfer#resources) actually supports sending SysEx to the Digitakt (but not the Digitone).

Here is a list of improvements taken from Elektron's official [release notes](https://www.elektron.se/wp-content/uploads/2018/07/Digitakt_OS1.11_readme.html) for OS 1.11:

```
Added support for Overbridge plugin.

Added scale per track functionality to the sequencer.

Added functionality to randomize page parameters. [PARAMETER] + [YES] to randomize. [PARAMETER] + [NO] to reset PARAMETER page to its last saved state.

Delay Time parameter values are now displayed as note values on relevant steps.

Added the possibility to revert changes made by using the Control all functionality.

Implemented reload track Sound functionality. ([TRK] + [TRIG 1-8] + [NO]) Several track Sounds can be reloaded at the same time by pressing multiple [TRIG] keys.

Added the option to select if audio over USB is Post or Pre track level.

The screen saver now turns off the screen after 60 minutes of inactivity.

Added option to mute internal output from main (USB CONFIG menu).

Added USB to main volume setting (USB CONFIG menu).

Added support for pattern mutes over CC/NRPN.
```

The most interesting one to note is most definitely the Overbridge support. This will be a necessary update for me before I'm able to try out Overbridge, which adds a VST / Audio Unit style plugin to Ableton, or any DAW for that matter.

## Updating the Digitakt
The first step is to grab the `Digitakt OS 1.11` download from Digitakt's [resources](https://www.elektron.se/support/?connection=digitakt#resources) page. Just like with the Digitone, it's a zip file that contains a SysEx file and a README. The README instructions are basically the same, letting you know that you can either update from within the OS or from the Early Startup Menu. Curiously, there is no mention of Elektron Transfer despite the fact that it is supported by the Digitakt.

The next step is putting the Digitakt in update mode. Navigate to `Settings > System > OS Upgrade`, and then you're ready to start the update process. Don't forget to connect the Digitakt to your computer with a USB cable.

Then I went ahead and fired up Transfer since I already had it installed from yesterday's experiments. In the `MIDI in` drop-down, I selected `Elektron Digitakt Digitakt in 1` and for `MIDI out` I selected `Elektron Digitakt Digitakt out 1`. Your configuration should look like this:

![transferconfiguration](/assets/transferconfiguration.png)

Then I clicked the `Connect` button, which brought me to the following interface:

![transferinterface](/assets/transferinterface.png)

I dragged the update file `Digitakt_OS1.11.syx` into Elektron Transfer which immediately sent it to the Digitakt, but to my surprise, the Digitakt ejected itself from update mode back to the System settings menu with the error "UPGRADE FAILED CHECKSUM ERROR". Huh. I thought maybe the sysex update file was corrupted, so I tried redownloading it again but kept getting the same failure. Googling this issue, I found [this](https://www.elektronauts.com/t/update-digitakt-from-1-11beta-to-1-11-fails/100402) Elektronauts post which seems to suggest that it's a bug with macOS 10.15 Catalina, and that updating with Transfer should be possible from a Windows computer, the alternative for Mac users being -- you guessed it -- SysEx Librarian. Since I'm too lazy to move my Digitakt over to my PC, I guess we're going with Sysex Librarian again.

So, it turns out this is the exact same update process as for the Digitone. Go ahead and refer to [that blog post](https://www.kevinchau.com/blog/digitone-update/) for the full detailed instructions. I'll sum it up by saying it does take a long time (~20 minutes), so have some patience and go make yourself a cup of coffee or something. 

After waiting for the transfer to complete, the Digitakt should now be on OS 1.11. Next stop, Overbridge 2.0 Beta!