---
layout: post
title: How to create a Paypal donate button[für Deutsch Benutzer]
date: 2015-06-12 12:00
author: CHENGJIE XU
comments: true
categories: []
tags: []
---

Original writer is me: **[sonjasper.com](https://blog.sonjasper.com/2015/06/12/how-to-create-a-paypal-donate-button.html)**

As an indie developer, I won't get a lot from my project for now but happiness. When a visitor could find something useful from here and support my achievements, no matter what it is, game or code staff. And he will support me. I will appreciate it. And donation from others should be a meaningful method.

Here are the steps how to create a Paypal donate button:

## Step1:

Log in your personal Paypal account and upgrade your personal account to business account. It's totally free.

Click Mein Profil-->Kontoeinstellungen

## Step2:

Select Verkäufer/Händler and enter PayPal-Buttons option.

## Step3:

Click Neuen Button erstellen

## Step4:

Select Button type: Spenden.

And you could select different language logo of the button.

## Step5:

Just click Button erstellen. All done! You got the HTML code and a web address.

    <form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
    <input type="hidden" name="cmd" value="_s-xclick">
    <input type="hidden" name="hosted_button_id" value="ZK2HJKF2RFMWA">
    <input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif" border="0" name="submit" alt="PayPal - The safer, easier way to pay online!">
    <img alt="" border="0" src="https://www.paypalobjects.com/de_DE/i/scr/pixel.gif" width="1" height="1">
    </form>

    https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ZK2HJKF2RFMWA

Then you could put the donate button in your website :P

If you like my article, click the [DONATE](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ZK2HJKF2RFMWA) button and support me :D
