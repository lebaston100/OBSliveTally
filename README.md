# OBSliveTally

This small "webpage" connects to any OBS instance on the local network and displays either the stream status (live/offline) or tally information for different scenes or sources(on air/in preview/neither).

## This is how the tally part could be used

![Image](https://cdn.lebaston100.de/git/obslivetally/animation_small.gif)

## Setup
There is not that much to set up:
- Install the awesome [obs-websocket plugin](https://github.com/Palakis/obs-websocket/releases/tag/4.9.1) (only version 4.9.1)
- Open the "Tools" menu and select "websocket server settings"
- Make sure that "Enable Websocket server" is checked, "Server Port" is 4444 and "Enable authentification" is unchecked

- [Download this repository](https://github.com/lebaston100/OBSliveTally/archive/master.zip) and unpack or clone it
- The only file you need is the OBSliveTally.html

By default it is setup to connect to the IP of the machine you run it on(127.0.0.1). You can change that default start value by editing the IP address and/or the port in line 8.
You can open the file directly with a webbrowser or use a [simple webserver](https://github.com/maditnerd/WinSimpleHTTP) somewhere on the network to serv it to local clients.
This tool does NOT need an any internet connection to work.

The newest version is always [hosted here](https://lebaston100.github.io/OBSliveTally/OBSliveTally.html) thanks to github pages.

## General Usage
- Open the OBSliveTally.html in a web browser (On a pc, laptop, tablet, smartphone)
- You can change the ip here to the address of your obs machine. If you edited it in the file as mentioned above it will show up here already filled in.
- Click on the "Connect to OBS" button
- If the connection to the obs machine was successful, a list of buttons will show up with all your scenes and sources from obs and another button on top called "Stream Status"
- As soon as you click the "Connect to OBS" button, the IP address entered will be saved on the device with the localStorage API if available. If you then reload the page on the device it will auto-fill the IP field with the saved value so you don't have to re-enter it every time.

### Show Stream Status
- Click the "Stream Status" button
- That's it. It will show OFFLINE and a white background if you're not streaming and LIVE with a red background when the stream is live

### Show Scene Tally
- Click on the scene name you want that are listed under "Scenes"
- It will show the name of the scene on top of the page.
- If the scene is neither in preview or program, the background will be black
- If the scene is in preview, the background will be green
- If the scene is in program, the background will be red
- If a transition (like a fade) is started where the destination scene is the scene you selected, then it will light up red
- If studio mode is disabled there will be only a red and black display, no green

### Show Source Tally
You can also show the tally status for individual sources. Every scene that containes that source will be handled like described in Show Scene Tally above. The page will update the scenes every 30 seconds in case you add the source to a new scenes after starting the tally.

### Advanced options
- If you want the page to automatically connect to obs without making any default selection then edit the file with a text editor and set "autoConnect" in line 9 from false to true.
- If you want to automatically restore what you last selected in terms of Stream Status / Scene / Source then set "saveAndRestoreWatchDetails" to true in line 10. Combine this with autoConnect = true for the full auto-restore experience.
- If you want to delete all of the locally stored data to get the selection menu again after using "saveAndRestoreWatchDetails" then set "deleteSavedSettings" in line 11 to true, then reload the page to clear the saved data, then set it to false again

If you find any bugs, please report them as a Github Issue or join my [Discord Server](https://discord.gg/PCYQJwX)

## Tested on/with:
- Win 10 20H2
- obs-studio 26.1.0
- obs-websocket 4.8.0

## Thanks

Thanks to [alexdean](https://github.com/alexdean) for refactoring it and fixing a few state bug's that came up.