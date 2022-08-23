---
layout: "post"
title: "Logging Parameters of MAS in Asterix"
permalink: "/maslogging/"
use-math: "true"
---

# Logging of MAS freq and pressures #

1. Start Topspin
2. Double-click on the *MAS spin rate*. It will open a window with the title 'MAS Pneumatic Unit Control'.
3. Click on the tab 'Config'.
4. Enable GUI and CORBA log messages.
5. Close the window.
6. On the desktop click on the application called MASLogging.
7. It will ask you for how many hours you want to log and at what interval.
8. It will start running the script and at the end will write a file called *spin.log* on the desktop. 

The spin.log file is deleted once you start running the script. So save it in another name if you want to keep it.

``` sh
#!/bin/bash
rm -rf /home/$(whoami)/Desktop/spin.log
cd /opt/topspin3.2/prog/curdir/$(whoami)
echo -n "For how many hours > "
read var1
echo -n "Interval in seconds > "
read var2
var3=$(echo "scale=0; $var1*3600/$var2"|bc)
echo $var3
for (( i=1; i<=$var3; i++)) 
do
cat MasDebugServer.log | grep "freq=" >> temp.txt;
my_var=$(tail -n 1 temp.txt);
now=$(date +"%D %T")
echo "$now $my_var"
echo "$now $my_var" >> spin.log;
sleep $var2; 
echo $i;
done
cp spin.log /home/$(whoami)/Desktop/
cp -rf /home/$(whoami)/Desktop/spin.log /home/$(whoami)/Desktop/spin_lasttime.log
```