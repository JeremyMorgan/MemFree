MemFree
=======

Application to chart the free memory available on a server at regular intervals. 


##How this works

A cron job is set up on your server like this: 

>00 06 * * * cd /home/web/memfree && sh memfree.sh

You can change the options to have it run however times you want of course. Your paths may differ as well. 

Memfree.sh is very simple:

```
#!/bin/bash
cat /proc/meminfo | grep MemFree > /home/web/memfree/perfprofile/$DATE-$TIME.txt
```
This simply dumps the current free memory info into a text file. 

The next cron job will call /jogs/checklog.php which will see if there are any new log files added, and if they are they'll be stuffed into a mysql database. 

When you bring up the index of the website you'll see a chart rendered by D3 that looks like this:

<img src="http://images.jeremymorgan.com/memfree.png">

I'll be adding some features to this such as realtime values as well. 


