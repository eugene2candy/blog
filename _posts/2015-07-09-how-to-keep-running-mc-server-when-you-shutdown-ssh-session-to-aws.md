---
layout: post
title: How to keep running Minecraft server when you shutdown SSH session to AWS
date: 2015-07-09 19:30
author: CHENGJIE XU
comments: true
categories: []
tags: []
---

When you bulid MC server by the method: [Running Minecraft Server On AWS](https://blog.sonjasper.com/2015/07/06/running-minecraft-server-on-aws.html).

You'll find that when you close PUTTY session, the server should be closed at the same time. To avoid such a situation, you need to install a function named **screen** to your ubuntu server.

STEP1:

install screen:

```bash
sudo apt-get install screen
```

STEP2:

run Minecraft server by:

```bash
screen java -Xmx1024M -Xms1024M -jar cauldron-1.7.10-1.1388.1.0-server.jar nogui
```

After then, your MC server will be running in a screen.

You could press **Ctrl+A**, and then press **D** to detach your screen back to original shell status.

Then you could

```bash
screen -ls
```

to find your screen session.

And the 1286 is the my screen ID.

When you log in AWS next time, you could

```
screen -r [screen ID]
```

to back to your screen which is running MC server.
