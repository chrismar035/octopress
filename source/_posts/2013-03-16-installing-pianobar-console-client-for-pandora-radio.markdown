---
layout: post
title: "Installing PianoBar - Console client for Pandora Radio"
date: 2010-01-26 00:03
comments: true
categories: [HowTo, Self-Reference]
---

PianoBar is a console client for Pandora Internet Radio. For me, this is a huge discovery. If you run Ubuntu, the flash player for Pandora can be a pain in the ass to install. Plus, on my netbook, the flash plugin for Chrome usually eats about 40-55% CPU constantly. A console client for Pandora will resolve all these issues. 
<!--more-->
However, the install instructions in the readme at the <a href="http://github.com/PromyLOPh/pianobar">PianoBar Github Repo</a> are very sparse and for someone pretty new to linux (like me) may be a little daunting. In the next few paragraphs, I will try to flesh out the installation instructions for PianoBar on Ubuntu linux.
<h2>1. Get the PianoBar source.</h2>
<p>I downloaded the .tar.gz from <a href="http://6xq.net/html/00/17.html">http://6xq.net/html/00/17.html</a> and extracted it with 
<code>tar -xzf PromyLOPh-pianobar-e079b45.tar.gz</code>
<h2>2.  Try to Make the PianoBar source.</h2>
<p>I say try because for me it didn't work. I was missing some of the required dependencies. But, you might not be missing the same ones as me. So, try to make it and then follow the instructions below for the dependencies you are missing.
<code>cd PromyLOPh-pianobar-e079b45/
cmake .</code>
<h2>3. Get and install libao</h2>
<p>Libao is a cross-platform audio library for playing audio. I followed <a href="http://www.linuxfromscratch.org/blfs/view/cvs/multimedia/libao.html">these instructions from Linux from Scratch</a> to install it. Download the source from that page. Extract the .tar.gz:
<code>tar -xzf libao-0.8.8</code>
Then, from withing the libao-0.8.8 directory, configure the library with:
<code>./configure --prefix=/usr && make</code>
Finally, install it as root:
<code>sudo make install && sudo install -v -m644 README /usr/share/doc/libao-0.8.8</code>
Then, I retried step 2 to see that I didn't need the LIBAO anymore.
<h2>4. Install FAAD2</h2>
<p>Download the bootstrapped .tar.gz from <a href="http://www.audiocoding.com/downloads.html">AudioCoding.com</a>. 
Extract the .tar.gz with:
<code>tar -xzf f@d2-2.7</code>
There are installation instructions in the INSTALL file in the extracted folder. I'll summarize what worked for me.
Configure it:
<code>./configure</code>
Make it:
<code>make</code>
Install it:
<code>sudo make install</code>
Then, I tried to make pianobar again. It still said it couldn't find libmad, but it turned out I didn't need it.
<h2>5. Install PianoBar.</h2>
<p>After running the cmake from the extracted PianoBar folder, you should see that the object files were made. Then, run make:
<code>make</code>
And install:
<code>sudo make install</code>
If all goes well, you will be able to run it:
<code>./src/pianobar</code>
Enter your pandora username/email address and password. 
Choose your station.
Hear music!
<HR>
<strong>UPDATE:</strong><BR>I recently used this post to install pianobar on another computer and was getting 
<code>pianobar: error while loading shared libraries: libf@d.so.2: cannot open shared object file: No such file or directory</code>
I needed to update the Shared Libraries (You can read more about Linux Shared Libraries from <a href="http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/shared-libraries.html">this page</a>, specifically 3.5).  I tried
<code>ldd /usr/local.bin/pianobar</code>
to see which shared libraries where being used by PianoBar and did see that libf@d/so/2 was not found.
<code>linux-gate.so.1 =>  (0x0044c000)
libf@d.so.2 => not found
libao.seeo.2 => /usr/lib/libao.so.2 (0x00edb000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00507000)
libm.so.6 => /lib/tls/i686/cmov/libibm.so.6 (0x00794000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00982000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00f20000)
/lib/0x00f20000ld-linux.so.2 (0x00f4e000)</code>
But I could find the libf@d.so.2 file in the <code>/usr/local/lib/</code>directory. Therefore, I needed to run ldconfig:
<code>sudo ldconfig</code>
Then I ran the ldd again and saw that libf@d.so.2 was now found in /usr/local/lib/ and PianoBar was now running again.
Also, I learned how to automatically sign in and change the keyboard short cuts.
<h2>6. PianoBar config</h2>
You can change the configuration of PianoBar to switch up the keyboard short cuts and automatically login on run. To do this, you need to create and edit a file named 'config' in the .config/pianobar/ within your home directory.
<code>vim ~/.config/pianobar/config</code>
To automatically login, add the following two lines
<code>user = pandoraUserName
password = pandoraPassword</code>
I also found that changing the "Loving Song" keyboard short cut from + to = worked out better, since I didn't have to press Shift+=.
<code>act_songlove = =</code>



