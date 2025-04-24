---
layout: default
title: Locally Hosted Wiki
---
*This is a guide I wrote a little while back, and I decided to post it here because why not.*

This guide will walk you through the process of creating a locally hosted wiki, using MediaWiki.

But first...

**Why even bother making a wiki?**  
Probably the best reason to follow this guide is if you're working on some creative project, and need a place to organize information about it. Wikis are great ways to compact information from across all instances of your project, and allow a centralized place to determine and confirm inconsistences. All in all, wikis are great for creative project organizing.  
**But why not use Fandom?**  
There's a great reason for that: Fandom wikis are public. Unless the project you're working on is already public, and you don't mind spoiling parts of it on the public wiki, a Fandom wiki wouldn't work well. Asides from that, there's also the issue of the excess bloat on Fandom (mainly ads*).  
**Alright, I'm sold. How do I start?**  
Setting up the wiki is relatively easy. First, make sure you meet these requirements:  

- A windows PC (always running and online if you want to access it on other devices).
- Half-decent technical know-how (I'll be explaining things as simple as possible, but I can only explain so much).
- Administrator access or access to an administrator.

**Part 1: Install WAMP.**  
WAMP stands for Windows Apache MySql PHP. To briefly summarize, it allows hosting of different files on your PC to be access through a web browser. It's very useful for many things, but I'll try and keep it simple for this blog.  
To install WAMP, go to this site: [https://www.wampserver.com/en](https://www.wampserver.com/en). From there, you want to scroll down, and press the download button for WampServer. It'll provide a window for you to sign up for something, but you can just press the download button somewhere in that top paragraph. After the download finishes, don't run the executable yet. Now go to [https://github.com/abbodi1406/vcredist/releases](https://github.com/abbodi1406/vcredist/releases). Download the VisualCppRedist\_AIO\_x86\_x64.exe file. Run this once it finishes downloading. This will install all the dependencies for the software. Now you can run the WampServer executable. Follow the steps to install (it's relatively straightforward). Once it's finished, run WampServer from the new shortcut on the desktop. You can move on to the next step once the tray icon (the little icons in the bottom right corner) is green.  
**Part 2: Setup WAMP for external access.**  
This step is only applicable if you want to be able to access the wiki on other devices on your network. Keep in mind that devices outside your network still won't be able to access the wiki even after this step.  

To make WampServer accessible from other devices, left click the tray icon. Hover over the Apache section. Click on httpd-vhosts.conf. It'll open a file with a few lines of code. We want to focus on the line that says `require local`. Change that to `require all granted`. Save the file. Now click on the tray icon for WampServer, and click Restart All Services. After a few seconds, the icon should turn green again, and your WampServer will be accessible from other devices on your network! Except, there's one last thing we need to do. Open the start menu, and search for firewall. Choose Windows Defender Firewall with Advanced Security. On the left sidebar, go to Inbound Rules. Now choose New Rule on the right sidebar. Choose port, then go to the next step. On Specific Local Ports, type in `80`. Click next. Leave the next 2 steps default. On the final step, you can name the rule whatever you want. I named it `Allow Port 80`. Click finish.  

Now your WampServer is accessible from other devices on your network!

**Part 3: Install MediaWiki.**  
Installing MediaWiki is incredibly simple. First, go to [https://www.mediawiki.org/wiki/Download](https://www.mediawiki.org/wiki/Download). Click the download button. After it finishes downloading, extract the files. Now for an important step: Depending on the way you extracted it, the first folder may or may not be the correct one. To figure that out, go into the newly extracted folder. If you see several folders and files, you are good. If you only see one folder, go inside of that one. It should have several folders and files inside of it. Regardless of the method, you want to copy the folder containing several files/folders into the www folder in your WAMP folder (usually c:/wamp64). If you have trouble on this step, please feel free to ask me via email. Finally, rename the newly copied folder to something. I'd recommend naming it `wiki`, but you may want to do something else, depending on your use case. When naming the folder, it's a good idea to name it like: `example_wiki`, as opposed to: `Example Wiki`.

**Part 4: Setup your wiki.**  
On the web browser of the computer you're using, type in `localhost/wiki`, and press enter. Make sure `wiki` is whatever you named that folder. If everything was set up properly, you should now see a boring page that says Set up the wiki. Go ahead and press that button. Now time to configure the wiki settings. Each new line below is a step.  

Configure the language, then press continue.  

It'll do an environment check. Provided it's good, press continue.  

On this step, you only need to change Database Name to the name of your wiki, using the same format as the wiki folder name. Press continue.  

Leave this step blank. Press continue.  

Name the wiki whatever you want. Keep in mind that something like Kraggle09's Wiki won't work, but Kraggle09s Wiki will. I usually change the project namespace to something shorter, so if you want to do that, press other (specify). Type in the namespace of your choosing. Now type in the details for your administrator account. You don't need to specify an email, so that can be skipped. You can also uncheck the "Share data about this installation with MediaWiki developers" button if you'd like. Press continue.  

This step is probably the most configured one. First, choose user settings. Assuming you trust your family/roommates, you can leave it on Open Wiki. Otherwise, you can choose one of the other options. I leave copyright and license as default. Since this isn't a public wiki, it doesn't really matter. Uncheck the Enable outbound email option. Choose a default skin (I usually choose Vector since some of the other ones don't seem to always work. Now time for extension. If you really want to take the time, you can hand go through each and every extension and decide whether you want to use it. Or, since I've already done that, you can use the ones I chose. Assuming you want to save the time, check the boxes for `Category Tree`, `Cite`, `Code Editor`, `Echo`, `Multimedia Viewer`, `PDF Handler`, `SyntaxHighlight_GeSHi`, `TemplateData`, `VisualEditor`, and `WikiEditor`. Also check the box for File Uploads. Press continue.  

Press continue one last time.  

After a few seconds, the database will have been setup. Press continue.  

A file will have been saved. Put that inside the wiki folder (in my case that's just wiki). Press the enter your wiki button.  

And like that, you're done! You now have a blank slate wiki! This guide won't be talking about how to edit this wiki, or even customize it beyond the initial setup, as that's a much more detailed thing that, luckily, has already been done! On your wiki's main page, you should see a link to the user guide. Press that, and you'll see the official documentation on how to edit your new wiki!  

To visit your new wiki, just type in `localhost/wiki`, like you did when you first set up the wiki.

**Part 5: One last change.**  
If you want to access your wiki from other devices in your network, you'll need to change one last thing. Open the LocalSettings.php file using any text editor. Change the line that says `$wgServer = 'http://localhost';` to say `$wgServer = 'http://hostname';` replacing `hostname` with the hostname of your PC. Usually, the hostname is just the name of your PC, which can easily be found in Settings > System > About.

To access your wiki on other devices, enter `hostname/wiki`, again replacing hostname with your actual hostname.  

And that's all there is to it! If you have any questions, please don't hesitate to reach out to me via email!  

**Footnotes:**  
*Yes, signed in users don't see ads, but they still see the other junk.