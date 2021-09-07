+++
date = "2020-04-17T11:00:00-00:00"
title = "Stress Testing"
slug = "2020/04/17/stress-testing"
author = "Alan Pope"
+++

Last night, myself and my friend [Martin](https://twitter.com/m_wimpress) decided to ‘stress test’ my popey spades server. I was keen to see if it could handle a bunch of people playing for an extended period, so put out a [call](https://twitter.com/popey/status/1250886876225048577) to see of people wanted to spank either of us with a spade.

Turns out, I needn’t have bothered, because by the time I joined just before 10pm UK time, there were already 20 + people playing! As the server is public, and has a few standard, but relatively popular maps, I shouldn’t be surprised by this. By about 30 mins later when Martin joined, the server was pretty much full, and stayed that way for the couple of hours playing, and beyond.

The server is just a modest [Digital Ocean](https://m.do.co/c/f9f96ea43bd3) droplet (affiliate link) with a single CPU core, 1GB RAM (and 1GB Swap, I added), 30GB disk and a single public IP. Here’s what the performance graphs look like from the Digital Ocean dashboard.

![CPU Usage](/images/cpuusage.png "CPU Usage")

![Bandwidth](/images/bandwidth.png "Bandwidth")

![Disk I/O](/images/diskio.png "Disk I/O")

As you can see, the server is pretty idle until around 9pm when everyone seemed to jump on together, got busy then goes back to nothing once everyone has had enough. During that time we peaked at the maximum 32 players online. Nobody reported any lag, and I felt the game server kept pace well. No complaints at all (other than cheaters and griefers, who were dealt with 🔨 ).

The game has server selection screen where users can browse and filter the server list, to pick their favourite map, find a new one, or just choose a random server which has slots available to play in. Often a server will sit with `0/32` players for hours, until one person joins, and that’s all it takes. Once a server has one player, depending on the day/time it will often get an influx of players, looking for a challenge.

![Screenshot](/images/serverlist.png "OpenSpades Server List")

I’m pretty happy with the way piqueserver is running on this small droplet. It needs very little maintenance and has plenty of scope for expansion. Perhaps I’ll add more maps soon, or add scripts to enhance gameplay. But for now, I quite enjoy having a relatively vanilla server to play on, with random friends online. Maybe I’ll see you on there soon.