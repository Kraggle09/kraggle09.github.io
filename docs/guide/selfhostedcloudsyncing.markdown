---
layout: default
title: Self Hosted Cloud Storage/Syncing
---
# How to make your own self hosted cloud storage/syncing service

## Questions
**What is this?**  
This is a guide on how to make your own replacement for services like OneDrive and DropBox.

**Why use my own setup?**  
There are several reasons you might want to host your own setup, including finer control, cheaper hosting, and more storage per dollar.

**Is this free?**  
Mostly, yes. You'll need to already have a server (this can just be a low power computer that is on 24/7), and a hard drive to store stuff on. The software is completely free, so you really will just be paying for power usage (which is pretty low).

**Is there any reason I shouldn't use this?**  
If you need to be able to access files from outside of your network (i.e. at a store or work), you probably will want to stick with your current solution.

## Quick definitions:
Server: The device you plan on *hosting* the files on.  
Client: The device you plan on *accessing* the files on.

## Part one: Setting up storage
First, you'll want to log into your server, and configure a network share (this is assuming you're running Windows on the server, Linux will differ). 

To do that, right click the drive/folder (drive if you have a seperate hard drive for this, folder if you don't) you want to share. Go to properties, sharing, advanced sharing, and check "Share this folder". Name the folder, and click permissions. From there, you can either give full access to everyone (by selecting everyone and checking full control), or you can explicitly add permissions for you (add button). I usually just give everyone full control, since I trust the people in my house. Click ok, ok, and apply.

To test that this works, go to file explorer on a different computer (ideally the computer you want stuff to sync to), go to the network tab, and double click your computer. (you may need to turn on network discovery) In there, you should see the drive/folder you shared.

Technically, you've setup your cloud storage. You can just put files in there and access them from any computer.

But if you want this to be a cloud *syncing* service, you'll need to keep going.

## Part two: Setting up manual syncing
Go to [https://freefilesync.org](https://freefilesync.org/), click download, and download the latest version for your operating system. Install the app (it's a pretty simple process, so I won't cover it here), and launch it.

The app has 4 main sections: File syncing presets (upper left), syncing controls (top), folder configuration (middle), and files to be synced (bottom). 

First, you'll want to link the folders you want synced. In my case, I'll sync my documents folder. Add the path for your local folder (dragging and dropping works too), and add the path for the remote folder (in my case a documents folder inside my network share). You can add additional folders by clicking the green - icon.

Click compare, and wait. After this finishes, click synchronize.

It'll sync the files, and viola! You now have a cloud syncing service.

One thing that you'll encounter here is when you delete files locally, freefilesync errors out saying that there's no recycling bin. To fix this, click the blue gear, click synchronization, and click Permanent. Don't worry, locally deleted files will still go to your client's recycling bin, they just won't also go to a remote bin.

## Part three: Setting up automatic syncing
Once you've configured your syncing how you like, click "Save as batch job". Click "Run minimized", and save as. Save it to somewhere on your PC (it'll stay here). Close freefilesync, and open RealTimeSync. Click File, Open, and load the file you saved. Click start.

This will run in the background, and whenever you make changes, it'll sync them.

To make this run automatically at startup, press ⊞ + R. Type `shell:startup` and press enter. Right click, create a new shortcut, and enter the path of realtimesync (usually `C:\Program Files\FreeFileSync\RealTimeSync.exe`), as well as the path of your batch job file. It should look something like this in the end: `"C:\Program Files\FreeFileSync\RealTimeSync.exe" "C:\Users\redpi\Documents\FreeFileSync Batch Jobs\Documents.ffs_batch"`. Save the file, and restart your pc. If you did things right, you should see a little icon in your background apps. This will monitor the changes done to folders, and sync when their made.

If you want to add more files, just open freefilesync, add a new folder, and click save.


I hope this guide was useful. If anything here didn't work, feel free to email me using the link at the bottom of this page.