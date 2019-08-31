# OBSliveTally

This small website connects to any OBS instance on the network and displays either the stream status (live/offline) or tally information for different scenes(on air/in preview/nothing).

## This is how the tally part could be used

![Image](https://cdn.lebaston100.de/git/obslivetally/animation_small.gif)

## Setup
There is not that much to set up:
- Install the awesome [obs-websocket plugin](https://github.com/Palakis/obs-websocket/releases) by Palakis (Version >= 4.3.3)
- Open the "Tools" menu and select "websocket server settings"
- Make sure that "Enable Websocket server" is checked, "Server Port" is 4444 and "Enable authentification" is unchecked

- [Download this repository](https://github.com/lebaston100/OBSliveTally/archive/master.zip) and unpack or clone it
- The only file you need is the OBSliveTally.html

By default it is setup to connect to the IP of the machine you run it on. You can change that by editing the IP address in line 8.
You can open the file directly with a webbrowser or use a webserver somewhere on the network to serv it.
The newest version is always [hosted here](https://lebaston100.github.io/OBSliveTally/OBSliveTally.html).
This tool does NOT need an internet connection to work.

## Important Note
If you use Studio Mode and have disabled "Swap Preview/Output Scenes After Transitioning", please set "swapScencesIsEnabled" in line 9 to 0. This is because this script currently has to work around [bug #259](https://github.com/Palakis/obs-websocket/issues/259) in the websocket plugin. As soon as that is fixed there, i can fix this here.
If you do not have that set right, the scene will stay "red" even after transitioning away.

## General Usage
- Open the OBSliveTally.html in a web browser (On a pc, laptop, tablet, smartphone)
- You can change the ip here to the address of your obs machine. If you edited it in the file as mentioned above it will show up here already filled in.
- Click on the "Connect to Server" button
- If the connection to the obs machine was successful, a list of buttons will show up with all your scenes you created in obs and another button on top called "Stream Status"

### Show Stream Status
- Click the "Stream Status" button
- That's it. It will show OFFLINE and a white background if you're not streaming and LIVE with a red background when the stream is live

### Show Scene Tally
- Click on the scene name you want
- It will show the name of the scene on top of the page.
- If the scene is neither in preview or program, the background will be black
- If the scene is in preview, the background will be green
- If the scene is in program, the background will be red
- If studio mode is disabled there will be only a red and black display, no green

If you find any bugs, please report them as a Github Issue

## Tested on/with:
- Win 10 1809
- obs-studio 23.0.1
- obs-websocket 4.5.0