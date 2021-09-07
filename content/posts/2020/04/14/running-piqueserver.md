+++
date = "2020-04-14T11:00:00-00:00"
title = "Running Piqueserver"
slug = "running-piqueserver"
author = "Alan Pope"
+++

I mentioned in the [Welcome](/posts/2020/04/13/welcome) post that I’m running [piqueserver](hhttps://www.piqueserver.org/) to play on. Piqueserver is an awesome free software implementation of the [OpenSpades](https://openspades.yvt.jp/) / [Ace of Spades](https://store.steampowered.com/app/224540/Ace_of_Spades_Battle_Builder/) server.

It’s pretty configurable, so you can customise your server to have maps and game modes you prefer. It has server and team text chat, map voting and admin / moderation tools. It can also connect to an IRC channel to allow for server monitoring, and has an SSH remote access option.

I installed using the [piqueserver documentation](https://piqueserver.readthedocs.io/en/latest/) which worked out great on a [Digital Ocean](https://m.do.co/c/f9f96ea43bd3) droplet (affiliate link). I ran it just fine over the Easter holiday weekend. In the evenings the server got pretty busy, maxing out at 32 players, busy building & shooting with no problem.

However, I wanted to have something super easy to setup for others, be automatically updated, and be confined. So obviously I made a [snap of piqueserver](https://snapcraft.io/piqueserver)! I’ve replaced the previous install on the popey spades “Good vs Evil” server, and so far it’s working perfectly.

Initially I simply took the build of piqueserver which is available via `pip` and bundled that in the snap. This is great to prototype the package, to get up and running quickly, but it’s not great for the long term. One of the benefits of the snap build service is edge-channel builds of the upstream project master branch. So I’m working towards having builds of piqueserver built from source for each supported architecture, and published in the edge channel, for testing or adventurous server admins.

In the meantime, if you want to run a stable & confined piqueserver yourself, get the details on the Snap Store page:

[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/piqueserver)