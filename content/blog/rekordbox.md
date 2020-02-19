---
path: rekordbox
date: 2020-02-18T16:07:00.000Z
title: Restoring your Rekordbox Collection from a USB Drive
description: A quick tutorial on recovering your entire Rekordbox DJ music collection from a USB stick
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/eR1H-cZEP8c" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Hello fellow DJs! Today I want to go over how to restore your [rekordbox](https://rekordbox.com/en/) DJ collection from your USB drive. Check out the video above for a quick overview of the process!

This is really useful if you need to copy over your entire DJ music collection to a brand new computer or if you've completely screwed up your current collection and just want to start fresh. The latter was the case for me, as I had many duplicates and missing files in my collection after a while, especially after letting my friends borrow my laptop to analyze their own tracks. I was fed up with seeing so many lost tracks and tracks I didn't recognize, and knowing my USB was in tip-top shape in terms of organization, up-to-date playlists, and having my complete music collection without duplicates, I wanted to figure out how to import the entire contents of it to rekordbox. 

Essentially, after deleting the corrupted collection from rekordbox and starting from 0 tracks, I wanted to figure out how to import everything on my USB stick so that my laptop would once again mirror exactly what I had on the USB. This was not only critical for maintaining and backing up my collection -- I recently lost my secondary USB stick which I normally use as a backup for my music collection -- but also very useful for transferring my collection to a new Windows 10 desktop PC that I'm setting up for music production.

Rekordbox isn't exactly the easiest piece of music software to learn since there isn't a lot of documentation, and I'm still relatively new to it so I wanted to make a quick write-up for documenting my process, in hopes that other DJs might find this information useful if they're ever in a similar situation. For the *record*, I'm using rekordbox version 5.8.3 but this guide should pretty much work for any version since it's not using any new features.

## A bunch of tracks, fewer playlists
If every single track in your music collection is already in a playlist on your USB, then you can actually just follow [these](https://forums.pioneerdj.com/hc/en-us/articles/115005275326) official instructions from Pioneer DJ for importing all your music. You basically just need to import each playlist one at a time, making sure to select the "Copy" option when you do so. This will create a local copy of the tracks/playlist on your computer in the folder `/Users/<YOUR_USERNAME>/PioneerDJ/Imported From Device/Contents`, which is conveniently organized into subfolders by artist and exactly mirrors the `Contents` folder you'll find on your USB stick.  

However, in my case, I had a ton of tracks (442 to be precise) but most of them were not in playlists! They were analyzed by rekordbox, had DJ playcounts, custom meta-data, and saved cue-points, but I'd say only about 10% of them were actaully in a playlist at all! Sure I could import the playlists I had, but how would I get over all the other tracks?

## File > Import, right?

The first thing I tried was using rekordbox's built-in import feature, `File > Import > Import Folder`, and selecting the `Contents` folder directly off my USB drive. You would think this would make a copy of your tracks on your computer but it doesn't. Instead, it just adds the track data to rekordbox's collection and then says the location of each track is on your external USB drive. So once you eject your USB drive, you now have 500 missing tracks that can't be played at all. Even worse, if you do this in combination with the Playlist import and copy technique I linked above, you'll end up with duplicate tracks in your collection. I'm sorry Pioneer, but your implementation of this import feature is super shitty. Please add an extra option to copy the tracks locally.

## How about Backup and Restore?

I also tried using the above `Import Folder` feature + rekordbox's [Backup and Restore](https://rekord.cloud/blog/using-the-same-rekordbox-on-multiple-computers) feature in order to create a local copy of my music collection. The downfall here was that when I tried to import and copy the playlists over, I once again had duplicate tracks in the collection which I wasn't going to settle for.

# How to Import your entire DJ collection
*What ended up actually working for me was creating a playlist on my USB itself that contained all my tracks, importing that playlist first, and then importing all the other playlists WITHOUT COPYING*. Pretty simple huh? Not necessarily obvious, but it's definitely a straight forward process. I'll outline it below.

1. Create a playlist on your USB with every single track.

![alltracksplaylist](/assets/alltracksplaylist.jpg)

The name of the playlist actually doesn't matter. You can name it "All Songs", "Everything", "My Collection", whatever, but since I believe this should be an automatic playlist that rekordbox should maintain for you (or at least give us a way to import all the tracks damn it), I gave it the same exact name as the actual feature you'll see above the Playlists folder in the sidebar.

After you create the playlist, go to the actual "All Tracks" collection, select all the tracks (with `cmd/ctrl + A`), and then drag them over to the new playlist (or right click > Add to playlist).

2. Import the playlist containing all your tracks, making sure to select the "Copy" option

![importall](/assets/importall.png)

Right click on your new mega playlist, and import the thing into your collection. Definitely select the copy option, as in the Pioneer DJ article I linked above. Cool, you now have local copies of all your tracks, but none of the playlists!

3. Copy over your actual playlists, but skip copying the files!

![importplaylist](/assets/importplaylist.png)

Here's the last step, it's a little tricky so I'll explain exactly what's happening here. What we're going to do is copy over each playlist one at a time, similar to the advice given in the Pioneer DJ article, but we're NOT going to copy over all the tracks, just the playlist information.

When you right click your playlists and click `Import`, you'll actually see three different import options since rekordbox has detected that you've already imported the tracks (in step 2). Each option does something different so I'll break them down for you since only one of them works in our case.

The first option, "Import", will create duplicates track in your rekordbox collection. The first copy will point to your local copy that you imported in step 2, while the second copy will point to your external USB location. This is dumb.

The second option, "Update Collection", will not create a duplicate track but it will point your track in your rekordbox collection to the location on your external USB, while at the same time leaving your local copy on your laptop. It will however show as a missing file when you eject your USB, and you won't be able to play it. This is also really dumb.

The third option, "Skip (add to the palylist only)", is most definitely the correct option! What this will do is leave the track in your collection pointing to the location of the local copy created when you imported it in step 2, while transferring over all the playlist information only. So you'll have your playlist on your laptop, and your tracks will still play even after ejecting your USB! 

Make sure to select the "Apply to the rest of all" checkbox, since rekordbox is detecting a duplicoate import for each track you are importing from the playlist in question.

Now rinse and repeat for each of your playlists on your USB, and then you'll have your entire DJ music collection back onto your laptop. No duplicates, no missing files, and all the meta-data written from your live performances (ie DJ play count) synced to your collection. 

That's it! Congratulations, you now have the ability to import your DJ collection to any computer with rekordbox!

## Bonus points for new MacBook Pro users!
If you're using one of the newer MacBook Pro's with only USB-C slots, I highly recommend [this](https://www.amazon.com/SanDisk-256GB-Ultra-Drive-Type-C/dp/B06XC1WGQR) USB drive from SanDisk. It's a dual-sided stick, one side with USB type A and one side with USB type C, perfect for exporting music from rekordbox on your MacBook while still maintaining compatibility with CDJs. It completely removes the need for a USB-C to USB-A adapter and I can't recommend it enough to other USB type C disabled DJs. Before I got a couple of these bad boys, I was constantly looking for my adapter whenever I needed to use rekordbox, and it completely ruined the flow/mood for me and I'd even go as far as saying it inhibited my musical creativity. Thanks Apple. Maybe one day CDJs will have USB-C media input, but I highly doubt it. Don't get me wrong, I actually love USB-C, but we'll probably see bluetooth input from Pioneer DJ before that ever happens.
![USB-C Stick](https://images-na.ssl-images-amazon.com/images/I/61idhO32C0L._AC_SL1100_.jpg)