---
layout: post
title:  Multiplayer Game Server, Part 1
date:   2020-08-03 12:00:00 -0700
categories: games
tags:
- intro
---
Game Engine
----
There are two popular game frameworks right now: [Unity][unity] and [Unreal Engine][ue]. They both have the ability to export games to all major platforms, and they handle 3D games well. Unity uses C# and Unreal Engine uses C++. Epic Games has been pushing their Unreal Engine framework aggressively and has been getting attention due to the popularity of Fortnite and their new store which only takes a 12% cut. Unity seems to have wider overall adoption and can also do 2D games well.<br><br>

Having said that, I am developing my game in [Godot][godot]. It is an open-source framework that uses a python-esque scripting language for development called gdscript. The project's pace of development is very fast and it has a solid feature set. I love the tiny binary size, the fast launch time and the excellent [tutorials][tutorials].<br><br>

Networked Games
---
In networked gaming, each player interacts with the game through a game client installed on their local machine. Something needs to coordinate changes in game state between the game clients. So if player 1 moves forward, player 2 needs to be connected to some system of authority that will inform it that player 1 has moved forward.<br><br>

It is possible to make one player's game client the authority and have all other players connect to it. This is a peer-to-peer networked game. This avoids the cost of hosting a separate game server and theoretically you could connect clients in the same room together locally without needing internet access.<br><br>

Assuming you are not in the same room, however, you will still need a matchmaking service to help clients find the system of authority. Also, using a peer as the authority is risky in case they have a bad internet connection or they want to cheat. This is still a common pattern, though, because Unity and Steam (and even Apple) offer matchmaking services so you can avoid hosting costs this way.<br><br>

For the setup I will discuss here, there will be a dedicated game server for each game and a dedicated matchmaking service.

[unity]: https://unity.com
[ue]: https://www.unrealengine.com
[godot]: https://godotengine.org
[tutorials]: https://docs.godotengine.org/en/stable/getting_started/step_by_step/your_first_game.html
