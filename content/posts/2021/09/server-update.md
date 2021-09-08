+++
date = "2021-09-08T11:00:00-00:00"
title = "Server Update"
slug = "server-update"
author = "Alan Pope"
+++

tl;dr: Server was down, now it's back on line, running on [Linode](https://www.linode.com/?r=49a71a9eddc09fbca846964312f36841f25e52a8) (affiliate link), with new maps and a new, extra admin.

----

It's been a while!

You may recall I [sparked](/posts/2020/04/13/welcome/) up and [Stress Tested](/posts/2020/04/17/stress-testing/) [Piqueserver](/posts/2020/04/14/running-piqueserver/) on a [Digital Ocean](https://m.do.co/c/f9f96ea43bd3) droplet (affiliate link) in April last year. It lasted about six months, then I had to shut it down. I had other things going on, and decided paying for a DO droplet for a game I wasn't playing much didn't make sense.

Well, things have changed, and I decided to *reboot* this project, and get the server back online. You see, I really like playing OpenSpades, and as I said before, I like being able to choose my own map to play on. So, popey spades is back online. Here's what I did.

Unfortunately last year, when I nuked the DO droplet, I didn't have a backup. I do normally backup my systems, but for whatever reason that one never was. So I lost the configuration and map files I'd collected. Thankfully the maps are archived online in various [places](https://aos.party/), and the configuration isn't hard to get your head around.

I updated the [piqueserver snap](https://snapcraft.io/piqueserver) because the previous release contained some bugs which are fixed, but are as-yet unreleased upstream. So I changed the [snapcraft config](https://github.com/popey/piqueserver-snap) to pull the tip of upstream [piqueserver git](https://github.com/piqueserver/piqueserver), which is now built and published in the edge channel.

I have a "spare" HP MicroServer lurking in my loft which I sometimes use to test stuff out. I installed the piqueserver snap on it, and forwarded the necessary ports on my router to that machine. After iterating on the config a little, I had a decently running server that I and others could play on.

The server shows up in the lobby in [OpenSpades](https://snapcraft.io/openspades), so anyone can connect to it, and play on the selection of maps provided. 

After a week of successful "testing", I wasn't sure if many people would actually play on the server, so was it actually worthwhile running it. Well, I had logs, so could see this! Piqueserver has a feature where it can connect to an IRC server, and log activity in a channel. I configured this, then lurked in the channel so I can see when there's activity, and monitor the discussion without being online. Also, if someone mentions me by name, I get a ping.

My IRC client logs the chat, so I can see with a bit of grepping, how many people played over a given span of time. Here's what the chat looks like, with the IP addresses redacted:

```
[2021-09-06T15:55:53.343Z] <popeyserver> * Sniper Brian (IP 80.x.y.z, ID 3) entered the game!
[2021-09-06T15:57:40.019Z] <popeyserver> * Sniper Brian (IP 80.x.y.z) disconnected
[2021-09-06T18:06:33.213Z] <popeyserver> * Shoval (IP 37.a.b.c, ID 3) entered the game!
[2021-09-06T18:13:06.583Z] <popeyserver> * Shoval (IP 37.a.b.c) disconnected
```
If I grep for "entered the game!" and use a little bit of awk (badly) we can see how many unique IP addresses connected to my server. 

```
alan@robby:~$ grep "entered the game!" /var/snap/thelounge/current/home/logs/alan/libera.chat-7-41d9-ba73-9d8b71ed6474/\#popeyspades.log  | awk -F '*' '{print $2}' | awk -F '(' '{print $2}' | awk -F ',' '{print $1}' | sort |uniq | wc -l
422
```

*I appreciate that one IP does not equal one person, but it's a decent ball-park figure.*

So roughly 400 or so people connected to my Piqueserver over the course of a week it was running at my house. I then remembered I still had the logs from when the server was running last year, so ran the same against my freenode (RIP) log files. 

```
alan@robby:~$ grep "entered the game!" /var/snap/thelounge/current/home/logs/alan/freenode-8684-41b8-a008-4343729ed478/#popeyspades.log | awk -F '*' '{print $2}' | awk -F '(' '{print $2}' | awk -F ',' '{print $1}' | sort |uniq | wc -l
5380
```

Woah! Over a six month period around 5K people connected to my little server to play games. Some may have dropped in and out, others may have stayed a while - I could probably derive that data too. I think that's pretty amazing numbers for a ten-year old game. Good enough to keep it running, I think.

Rather than run it at home, I decided to move the server to a box outside my network. People connecting would sometimes find it laggy, and downloading map data at the start of a game can take a while, due to my slow upstream bandwidth.

I spun up a new machine, this time on [Linode](https://www.linode.com/?r=49a71a9eddc09fbca846964312f36841f25e52a8) (affiliate link - which will get you $100 60-day credit once a payment method is added to your account). I'm using the smallest "Linode" called a "Nanode". It has a single CPU core, 1GB RAM, 25GB storage, a public IP, ssh access and a funky dashboard. There's a choice of Linode DataCentres to launch in, and I chose East Coast USA.

Taking the work I'd done on my home server, I replicated that to the Linode, and started the server up. Unsurprisingly everything worked just fine. I was able to connect and play with others on my server just as I was at home.

Soon after I started the server, while I played on another one, someone DM'ed me asking if they could contact me via [Discord](/discord/) for further conversation. The chat system in OpenSpades is a bit basic, so we took the conversation to Discord. They introduced themselves as an admin on other servers, and offered to help admin mine. Clearly when I'm asleep there's nobody around to get rid of the cheaters and griefers.

My general rule of thumb is "*If someone asks for admin rights, they're instantly disqualified from being an admin*" which I picked up from IRC many years ago. Often people want the power but maybe bad actors themselves, or ineffectual admins. I explained this to them, and they took it well :). 

We continued chatting, and I gained confidence that they're actually a good person. Specifically they helped me with some additional scripts which can be loaded onto the server to aid adminstration and deal with cheaters. I set them a task to find one of the maps I've been having real trouble locating. Thankfully they found one which was similar enough to what I was looking for, and I added it to the map rotation. 

They're now also an admin on the server ;).

Maybe I'll see you on the server, it's easy to find - still called "Good vs Evil". Pick a side. 👼 or 👿