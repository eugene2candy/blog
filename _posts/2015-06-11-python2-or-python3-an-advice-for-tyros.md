---
layout: post
title: Python2 or Python3? An advice for tyros
date: 2015-06-11 11:30
author: CHENGJIE XU
comments: true
categories: []
tags: []
---

Original writer is me: **[sonjasper.com](https://blog.sonjasper.com/2015/06/11/python2-or-python3-an-advice-for-tyros.html)**

Every beginner will be confused when he decided to learn Python. In some respects, there are a huge changes from Python2 to Python3. As the most developers use Python2, so you thought you should choose it. But when you noticed that Python3 is more standard, then you thought maybe Python3 is better.

So what's the difference between them? :P

Here are some visible comparisons of them:

# First, the syntax.

The same function code between Python2 and Python3.

Python 3.4:

    import urllib.request
    import webbrowser as web
    url = "http://www.google.de"
    content = urllib.request.urlopen(url).read()
    open("google.html","wb").write(content)
    web.open_new_tab('google.html')

Python 2.7:

    import urllib
    import webbrowser as web
    url = "http://www.google.de"
    content = urllib.urlopen(url).read()
    open("google.html","wb").write(content)
    web.open_new_tab('google.html')

They are all used to get the code of google homepage and save as a file named google.html.

The only difference is the first sentence. You can consider that the syntax in Python3 is more standard and detailed.

Such as input function,

Python 3.4:

    input

Python 2.7:

    raw_input

# Second, encode.

Python3 uses UTF-8 so it will be legal when you input some special characters such as Chinese.

# Finally,

This article is not about the comparison of different python versions. As you can see, the examples above are some small differences between Python2 and Python3. But when you meet more of them you should be confused and it will be difficult for you to solve the issue you meet due to the number of developers who use Python3 is less.

It's good for you to try the newest staff but it will not be smart. It's a nice try but not a good choice.

**1st reason**: There are more online courses based on Python2 and you should choose them. I was stupid when I first started to learn Python3 and I found it difficult to find the solutions when I met some issues.

**2nd reason**: It will be easy for us to graduate from Python2 to Python3 when the latter is more popular due to the syntax is so similar.

And now, the most important task is to fully learn Python as quickly as possible. As a result, from my standpoint, choosing Python2 should be a smart choice when you are just beginning.

If you like my article, click the [DONATE](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ZK2HJKF2RFMWA) button and support me :D
