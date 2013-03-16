---
layout: post
title: "Keep ssh sessions from timing out"
date: 2010-05-20 15:18
comments: true
categories: [HowTo, Self-Reference]
---

<p>The <a href="http://embraceubuntu.com">Ubuntu Blog</a> has a nice lil' article about <a href='http://embraceubuntu.com/2006/02/03/keeping-ssh-sessions-alive/'>keeping SSH sessions alive</a>.</p>
<p>It basically boils down to editing your <code style='display:inline;'>/etc/ssh/ssh_config</code> file and adding the following:</p>
<p>
/etc/ssh/ssh_config
<code>ServerAliveInterval 5</code>
<p>The number is the number of seconds to send the small keep alive which keeps the connection open. Ubuntu Blog suggests changing it from 5 to 240 or 300 (4 or 5 minutes).</p>
