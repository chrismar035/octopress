---
layout: post
title: "Notepad++ Color Configurator and styler.xml"
date: 2010-01-08 10:54
comments: true
categories: [HowTo, Self-Reference]
---

Before I start talking about colors, let's talk font. <a href='http://www.microsoft.com/downloads/details.aspx?familyid=22e69ae4-7e40-4807-8a86-b3d36fab68d3&displaylang=en'>Consolas</a> That's all you need to know. By far the best programming font. Get it. Use it. Love it. 

{% render_partial ads/ads1.html %}

<!--more-->

Recently I started learning Ruby on Rails and I found <a href='http://railscasts.com/'>RailsCasts</a> with a ton of Rails focused screencasts. I believe he (they?) use <a href='http://macromates.com/'>TextMate</a> for mac. I hadn't really thought much about color in my code before watching some of these screencasts. But, it actually helps, a lot! I use Notepad++ in Windows and they have a great styling system. You can use the in program Style Confirurator or you can directly modify the XML style sheet.
<br>
<h1>Style Configurator</h1>
The Style Configurator is a dialog within Notepad++ accessible through the Settings menu. The really great thing about the Configurator is that the styles you choose are updated live in your code. So, open up a file with a lot of code. Then open the Configurator and move it over to another screen. If you don't have more than one monitor, check the Transparency box in the lower right and you will be able to see through the Configurator. The slider there sets the Transparency level. Now you can see all of your code and pick styles for them. 
<p>Start with the very first 'language,' Global Styles. These not only include default styles of text but many of the stuff around your code, such as line number margin, inactive and active tab color, and the edge. The edge is great to keep your lines of code to a certain length for printing or displaying in a terminal. I also set the global font to Consolas. Also, be sure to set the current line color and selected text background color.
<p>Now you are ready to style for you language. I usu PHP mostly at work so I'll go though that one. Hopefully, I'll be familiar with Ruby soon enough to write a post about Ruby styles.
<ul>
<li>QUESTION MARK - This is the style of the opening and closing php tags ('<?php' and '?>')</li>
<li>DEFAULT - Text that doesn't match any of the other styles will be this.</li>
<li>STRING - Any string enclosed with double quotes</li>
<li>STRING VARIABLE - variables enclosed withing literal strings: "The Count is $count"</li>
<li>SIMPLESTRING - These are string enclosed with single quotes. (I used a very similar green to STRING)</li>
<li>WORD - These are the keywords of PHP. There are a bunch defined. You can also define some of your own in the blank box.</li>
<li>NUMBER - Number literals, including array indices</li>
<li>VARIABLE - Any word started with a $</li>
<li>COMMENT - Text between matching multi-line comments ('/*' and '*/')</li>
<li>COMMENTLINE - Text on a line after and including two forward slashes (//)</li>
<li>OPERATOR - Operators (+,=,-,etc.), matched parenthesis, brackets, curly brackets and logical operators</li>
<h1>Stylers.xml</h1>
<br><br>The stylers.xml file contains all the settings from the Configurator used by Notepad++. In addition to using the Configurator, you can manually edit this file. Or, download one from the web. The <a href='http://notepad-plus.sourceforge.net/uk/download.php'>Notepad++ site</a> has some under Theme Files. <a href='http://joyboner.com/60-free-textmate-notepad-styler-themes/'>Joy Boner</a> (read the <a href='http://joyboner.com/about/'>About page</a>) has 60 themes. I didn't check any of these out, but it might be worth a shot if you really don't want to set your own styles. 
<p>I also put <a href='http://gist.github.com/272115'>my personal stylers.xml</a> as a gist on github. Feel free to fork it. 
<p>If you have any other Notepad++ styling tips, comment below!
<p>--Chris

{% render_partial ads/ads2.html %}
