---
title: Let's do peek inside admin's dashboard - Abuse API endpoint
author:
  name: Bhavik Kanejiya
  link: https://linktr.ee/bhavikkanejiya
date: 2021-12-31 12:00:00 +0800
categories: [Write-up]
tags: [api]
render_with_liquid: false
#image:
#  src: /assets/api-blog/Header.png
#  width: 800
#  height: 500
---


There is broken access control in API which helps employee to become admin of workspace but with limited permissions

<br>

![Window shadow](/assets/api-blog/Header.png){: .shadow width="1548" height="864" style="max-width: 90%" }
_Let's do peek inside admin's dashboard: Abuse API endpoint Image_


## Introduction to application:

It's basically Productivity app which has over 2 million+ users which basically used by businesses to track employee project time and expense.


## Key Features:

There are many features but this are some important features.

- User can join multiple workspace
  ![Window shadow](/assets/api-blog/Workspace.png)
_Join multiple workspace image_

- User can create own workspace
  ![Window shadow](/assets/api-blog/Create.png)
_Create own workspace Image_

- Admin of workspace can invite other users by email
  ![Window shadow](/assets/api-blog/Invite.png)
_Invite other users by email image_


## How does Application works?

A User can join multiple workspace from one account but User ID will be same across all the work spaces. So, User created his/her personal workspace and joined company's workspace too.

The API pass the Workspace ID to interact with application.

***This is how request looks like:***
<br>
![Window shadow](/assets/api-blog/Request.png)
_Request Structure Image_


***And This is how Workspace ID look alike:***
<br>
![Window shadow](/assets/api-blog/Table.png)
_Workspace ID table image_

> While test for role based broken access control, Use Multi account containers Where Cookies are separated by container, allowing us to use the web with multiple accounts.

There are few sections which are only visible to admin. On User side we have limited functionalities. If We change the workspace ID directly, It will redirect me to it's homepage. We use ***Burp's match and replace*** feature to replace Workspace ID.


This is the final result when User successfully match and replace Personal Workspace ID with company's Workspace ID.
<br>
![Window shadow](/assets/api-blog/comp.png){: width="589" height="972" }
_Path Image_


## Step to Reproduce:

![Window shadow](/assets/api-blog/Steps.png)
_Step to reproduce Image_


## End Note
If you enjoyed this post, I'd be very grateful if you just give a 👏 and share. Thank you!
<br>
<https://linktr.ee/bhavikkanejiya>
  
## If you enjoyed this, you might also enjoy these References too:

- <https://www.youtube.com/watch?v=Mpw1Lo3GAK0>
- <https://blog.yeswehack.com/yeswerhackers/pimpmyburp-pwnfox-autorize-find-idor>
- <https://www.youtube.com/watch?v=3K1-a7dnA60>
- <https://blog.usamav.dev/two-account-takeover-bugs-worth-4300-dollar-bounty>