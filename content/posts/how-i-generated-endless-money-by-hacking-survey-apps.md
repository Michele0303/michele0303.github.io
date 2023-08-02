+++
title = "How I Generated Endless Money by Hacking Survey Apps"
date = "2023-07-31T08:02:44+02:00"
author = "Michele0303"
authorTwitter = "" #do not include @
cover = ""
tags = ["exploitation", "android", "app", "reversing", "api"]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = true
hideComments = false
color = "" #color from the theme settings
+++

# Michele0303
## _Generate Endless Money by Hacking Survey Apps_

### 1) Introduction
> Survey apps? Infinite money? What on earth are you talking about?

Survey apps allow users to earn rewards by answering surveys and participating in similar activities are well-known. These apps are designed to collect data and opinions from users on various topics, such as products, services, lifestyles, shopping experiences, and more. The information gathered through surveys is then used by companies and organizations to improve their products or services, develop new marketing strategies, or make informed business decisions.

The functioning of survey apps is quite simple. Each completed survey awards a certain number of points to the user, and typically, the longer it takes to complete a survey, the more points can be earned.

Once a user has accumulated a certain amount of points, they can redeem them for a reward. The rewards may vary depending on the app, but common rewards include:

- Gift cards
- PayPal transfers

### 2) Recon

From here, the challenge begins. I started by exploring the Play Store, in search of an app that could inspire me. After a long search, I finally found an app that sparked my interest... Here's the rewards page:

![Reward Page](https://i.imgur.com/yhKv8dh.png)

### 3) Attack

My first idea was to search for possible interesting APIs by decompiling and extracting links from the APK.

###### I decompiled the APK:
![Decompile](https://i.imgur.com/FK9skpx.png)

###### I searched for the smali files:
![Files smali](https://i.imgur.com/qmNgx56.png)

###### I extracted the links from the files:
![Extract links](https://i.imgur.com/Os9IZqV.png)

Noticing keywords like "getuserdata" and "adjustpoints" in the endpoints, I think that they might be the APIs I was looking for.

1. I tested the first API by inserting the "invitecode" parameter with a referral code to invite friends, and I noticed that the API worked, as it returned the number of points I had. ![First api](https://i.imgur.com/9Ko5af1.png)
2. Moving to the second endpoint, I inserted the "uniquecode" parameter with the referral code. ![Second api](https://i.imgur.com/z65Fe8Z.png)

Now, by checking through the first API or using the app, it's possible to notice an arbitrary increase in points, which allows me to redeem unlimited PayPal cash and Amazon gift cards.

![Final points api](https://i.imgur.com/pS2LRIi.png)


![Final points app](https://i.imgur.com/27RnzhQ.png)