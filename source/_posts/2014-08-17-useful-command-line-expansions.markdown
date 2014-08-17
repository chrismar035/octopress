---
layout: post
title: "Command Line Tips and Tricks"
date: 2014-08-17 10:05
comments: true
categories: Self-Reference
---

Often when dealing with the commmand line, there's a easier way to do what you
are doing. Pair programming and live coding sessions can be a great way to get
a peak behind the curtain at how others work and be able to steal some tricks
they've picked up along the way. Since we can't pair together today, here are
some of my favorite and most useful tricks to level up your command line fu.

# 

# Move to start and end

```
$ vm /really/long/path/with/more/dirs/file /another/deeply/nested/dir/structure
```

Whew, that's a doozy of a move command. However, in my haste, I've typoed `mv`
into `vm`. To get my cursor back there to fix it, I could hold the `left arrow`
and wait for a few days. But there's a better way! `Ctrl + a` will immediately
take you to the beginning of the prompt, while `Crtl + e` will take you to the
end.

# Repeat Last Command

```
$ mv /really/long/path/with/more/dirs/file /another/deeply/nested/dir/structure
mv: cannot move `...' to `...': Permission denied
```

Doh. Now that we've got the command correct, we see that we don't have
permissions to execute that move. If I had a nickel for ever time I've
run a command without sudo that needed sudo... Using the technique from the
last tip, I could press the `up arrow` and `Crtl+ a` then add `sudo`.

While that does work, we can do a bit better. The `!!` history expansion
shortcut will expand into the most previously run command in the subsequent
command. So, we can simply type:

```
$ sudo !!
```

And the `!!` will expand to the last command,
`mv /really/long/path/with/more/dirs/file /another/deeply/nested/dir/structure`,
and actually execute:

```
$ sudo mv /really/long/path/with/more/dirs/file /another/deeply/nested/dir/structure
```

# Reuse arguments

Ok, we've got that file in it's place now. But now I'd like to edit it. I could
type out `vim` and the long path to the new location of the file, but there's a
better way.

The `!$` history expansion expands to the last argument (or token) from the
previous command. So, all we need is:

```
$ vim !$
```

Quick and easy! There are many ways to use history expansion to get parts of the
previous (and others from history) command. `!$` is by far the one I use the
most. You'll do yourself a huge favor to commit that to muscle memory.

To get an argument other than the last, you can use `!:x` where `x` is the (0
based) index of the arguemnt, or a range, or `*` to get all the arguments.

```
$ git checkout -b features/laser-sharks

  !:2     => -b
  !:0     => git
  !:$     => features/laser-sharks
  !:^     => checkout
  !:1-2   => checkout -b
  !:-2    => git checkout -b
  !:2-$   => -b features/laser-sharks
  !:*     => checkout -b features/laser-sharks
```

> ZSH power tip: Tapping `tab` with any of these expansions in ZSH will expand
  them inline to preview before executing.

# 
