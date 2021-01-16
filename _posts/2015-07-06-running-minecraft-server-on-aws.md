---
layout: post
title: Running Minecraft Server On AWS
date: 2015-07-06 10:30
author: CHENGJIE XU
comments: true
categories: []
tags: []
---

You could try 1 year free AWS service before you pay it.
Log in your amazon aws account and create EC2 instance.

I created Ubuntu Server 14.04 LTS (HVM), SSD Volume Type.

Just keep all the default info and RUN it.

Create a new key for yourself and download the .pem file.

SSH to your ubuntu by using PUTTY.

Before you log in ubuntu.

Load your xxx.pem file and save as xxx.ppk file.

(The detailed information about how to use PUTTY you could google it.)

Here are the steps:

## STEP 1:

Log in Ubuntu as root by using PUTTY.

```bash
sudo -i
```

## STEP 2:

install JAVA(JDK)

```bash
sudo apt-get update  
sudo apt-get install default-jre  
sudo apt-get install default-jdk

sudo apt-get install python-software-properties  
sudo add-apt-repository ppa:webupd8team/java  
sudo apt-get update

sudo apt-get install oracle-java7-installer
```

And then, check the JAVA version to make sure you install sucessfully.

```bash
java -version
```

## STEP 3：

Download Minecraft to your Ubuntu.

```bash
cd /
mkdir Minecraft  
cd Minecraft  
wget https://s3.amazonaws.com/Minecraft.Download/versions/1.7.10/minecraft_server.1.7.10.jar
```

(You could download other version of MC and get the link: https://mcversions.net/)

## STEP 4:

Install Minecraft server.

```bash
java -Xmx1024M -Xms1024M -jar minecraft_server.1.7.10.jar nogui
```

(If you need to agree EULA, edit the eula.txt and **change false to true**, and install it again.)

After finished it. Press **CTRL+C** to quit it.

Check the files in the Minecraft folder.

```bash
ls
```

Edit the server.properties.

```bash
vim server.properties
```

Quit and save it.

Run 

```bash
java -Xmx1024M -Xms1024M -jar minecraft_server.1.7.10.jar nogui
```

again to load the MC server.

All done!

Have fun :D

If you like my article, click the <a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ZK2HJKF2RFMWA" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-blue.svg" height="22" /></a> button and support me :D
