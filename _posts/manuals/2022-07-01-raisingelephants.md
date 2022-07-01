---
layout: "post"
title: "Linux Computer Recovery"
permalink: "/syscrash/"
use-math: "true"
---

If a linux computer freezes completely, you try to *Raise the Elephant* instead of using the power switch.

### **R**aising **E**lephants **I**s **S**o **U**niquely **B**eneficial

>   <kbd>Alt</kbd> + <kbd>SysRq</kbd> + <kbd>R</kbd> : switch keyboard to 'raw' mode.

>   <kbd>Alt</kbd> + <kbd>SysRq</kbd>+ <kbd>E</kbd> : send SIGTERM (termination) signal to all processes except init.

>   <kbd>Alt</kbd> + <kbd>SysRq</kbd>+ <kbd>I</kbd> : send SIGKILL signal to all processes.

>   <kbd>Alt</kbd> + <kbd>SysRq</kbd>+ <kbd>S</kbd> : sync all filesystems to prevent data loss

>   <kbd>Alt</kbd> + <kbd>SysRq</kbd>+ <kbd>U</kbd> : remount filesystems as read-only

>   <kbd>Alt</kbd> + <kbd>SysRq</kbd>+ <kbd>B</kbd> : forcefully reboot

If there is no <kbd>SysRq</kbd> try the <kbd>PrtScn</kbd> or <kbd>Pause/Break</kbd>.

You can read more about the magic keys on the [Wikipedia](https://en.wikipedia.org/wiki/Magic_SysRq_key) article.