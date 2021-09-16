+++
date = "2021-09-16T10:00:00-00:00"
title = "Two Spades"
slug = "two-spades"
author = "Alan Pope"
+++

What could possibly better than running an Ace of Spades / OpenSpades (piqueserver) instance?

Running **two**, obviously!

The existing "Good vs Evil" server is currently configured to rotate through a few maps. Each map runs until one team catches the flag ten times, or twenty-four hours elapses with no winner, whichever comes first.

This is a pretty common configuration on many⁺ of the servers online.

⁺ *I say 'many' but there's only ever about thirty servers online at any one time. This is an old game with few online players.*

Some servers have no configured timeout, though. They rely on an amount of points being reached by either team to trigger the map change alone.

When the map changes though, everything in the previous game is lost. That includes any beautiful construction or destruction. Unfinished tunnels, barracks or defensive positions are gone forever.

Not all servers, in the past, were configured that way though. A few had **much** longer times between map rotations. 

I quite like playing on long-lived instances in OpenSpades. It's a bit like playing on a Minecraft server. People come and go, build, destroy, and re-build again. With a server that rotates quickly, there's no chance for that to happen.

With longer-lived servers, people can drop in, and play the game as usual, but anything they build or deconstruct is kept for other players for a lengthier time. In addition, when those players return, there will (perhaps) be some familiarity from their older constructions, if they survive.

So I decided to spin up a longer living instance. The [Linode](https://www.linode.com/?r=49a71a9eddc09fbca846964312f36841f25e52a8) (affiliate link) server I'm using has some spare capacity. 

![Screenshot](/images/linode_usage_2021-09-16.png "Server stats") 

So I spun up a second instance of piqueserver with a slightly different configuration.

```toml
# server name - displayed on master server
name = "Good vs Evil. 99wins 1month"
# default time limit to set per map. When the time limit runs out, the map rotation is advanced
default_time_limit = "720hours"
# number of intel captures to win the game (default: 10)
cap_limit = 99
```

The rest of the configuration, scripts, and maps are all identical. The only difference is that this map will run for a month rather than twenty-four hours, and requires ninety-nine wins from one side to trigger a map change.

It shows up in the server list, along with my "main" server instance. You can right-click them to "favourite" the servers, which brings them to the top and highlights them, thus.

![Screenshot](/images/both-servers.png "Both servers") 

So it's day one, hour one, and we have a big, blank, hallway map canvas. Let's see how this works out.

![Screenshot](/images/longserver-ready.png "Long lived server, ready!") 
