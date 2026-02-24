---
layout: post
title: "Devlog #7: Through the Fire and the Bricks"
date: 2026-02-24
author: Solo Architect
categories: Game-Dev Journey
---

## 200 Visits: The Cost of Creation

They say game development is a team sport. For the past two weeks, I’ve learned that’s a lie. 

I invited friends. I gave them tasks. I waited. What I got back was silence and "bricks." Unnamed, ungrouped, disorganized parts that I had to manually stitch together. I realized quickly that while others liked the *idea* of a game, I was the only one with the **compassion** to endure the process. 

I feel like I’ve aged two years in fourteen days. I’ve gone through development hell three times over, and every time, I came out with a more stable server and a sharper mind.

### What’s Under the Hood?
This isn't just a zombie game; it’s a living, breathing machine. Everything you see—and everything you don't—was forged alone:

* **The Global Heartbeat:** A full game loop where the house isn't just a model; it's a living entity with health. If the house falls, the dream ends.
* **The Combat Engine:** Custom weapon classes with `Auto` modes, varied stats, and a manual reload/refill system that respects magazines and ammo boxes.
* **Tactical Feedback:** Implemented a Headshot multiplier and randomized particle/decal systems so every bullet feels heavy.
* **The Intelligence:** A wave spawner that doesn't just spawn NPCs—it uses formulas to scale their strength, ensuring the challenge grows with the player.
* **The Economy:** A rock-solid DataSync system between Client and Server, handling end-of-wave rewards and a complex player stat upgrade tree.
* **The Atmosphere:** A dynamic Day/Night cycle that dictates the tension—safety in the light, survival in the dark.

### The Architecture of a Solo Dev
The hardest part wasn't the code; it was the **organization**. While my "team" left me with a mess of parts, I spent the late hours renaming, grouping, and optimizing. 



Every UI, every tweened arrow guiding new players, and every networked message was written by my hand. When the game hit 200 visits, it wasn't a "lucky break." it was the result of a modular framework that didn't break because I knew where every single bolt was tightened.

### The Verdict
I stepped in thinking this would be a piece of cake. I was wrong. It was a war. But standing here at 200 visits, looking at a game that *actually works*, I feel more confident than ever. I didn't just build a game; I built myself into a developer.

**Next Stop: 1,000 Visits.**
---