---
layout: post
title: "Devlog #8: Coming back with a new vision"
date: 2026-03-22
author: Solo Architect
categories: Game-Dev Journey
---

### The Return: Lessons from the "Flicker" Project
I come back to this project and continued where I left of 1 month ago. What did I do in the mean time? I was making another game which is a "Flicker" style kind of game that requires good state management. 

But I'm done making that game, now I'm back to this very first project of mine with experiences learnt from lots of lots of mistakes I made and it has changed how I look at a project quite a lot.

---

### The Discovery: The Hard-Coding Trap
First thing I do when coming back to the game, I intend on making a new type of weapon, gears. However, in the moment of making it, I realized that all of my purchase panels, stats display for guns/house's health and other stuffs are all **HARD CODED.**

I knew why I hard coded it in the first place, it's just to keep going, but now, I learnt, to keep going is to build a good foundation and my foundation was built like a baby stacking bricks.

---

### The Fix: From Static to Dynamic
I looked over, changed the game data, create mapping tables to match the stats display with the boost stats of the player that affects the display stats. 

I changed how stats are displayed, instead of hard coded, they are generated on a button click and now even if a gun have 100 stats to display or 100 upgrades possible, the game will still display all of that with the boosts the the players have right next to those weapon stats.

---

### The Architecture Shift: Server vs. Client
There was 1 really important thing before I fixed all of the hard coded stuffs, it was the fact that the client was giving info to the server, not the other way around. 

Now I know making it like that, if a player just change their gun to shoot out a rabbit then the whole server is fried. I had to spent 2 days fixing those logic. It was the longest 2 days of my life.

---

### Current Status: Under the Hood
I am writing this devblog by myself as I am finishing with making all the display panels/upgrade panels get generated flexibly and more scalable but still I'm not done yet. 

I literally have not had any progress on making the gear (well a little bit like stats and models and upgrades but it's literally not working at all) since I came back, it has already been like 4 days I think. And all I've done is just refactoring codes making sure they are flexible/scalable that's it. (the game's look has 0 difference, it's only the internal codes that's modified)

---

### Final Thought
> Very big lesson learn here, past self, please don't hard code stuffs, only pain awaits ahead if you do.