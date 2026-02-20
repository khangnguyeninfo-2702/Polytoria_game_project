---
layout: post
title: "Devlog #6: The Ghost in the Machine — Conquering Networking Authority"
date: 2026-02-20
categories: [polytoria, programming, networking, game-design]
---

## 🔫 The "Invisible Gun" Crisis

On February 20th, I finally overcame the most grueling technical hurdle of my project so far: **The Networking Authority Wall**. For an entire day, I was stuck in a loop where my shop system would "successfully" purchase a gun, print all the right messages, and deduct the coins—but the gun itself was a total ghost. It existed in the code, but it didn't exist in the world.

<p align="center">
<img src="{{ site.baseurl }}/assets/images/desperate_asking_for_help.jpg" alt="A screenshot of how I asked and got no reply to help" width="800" />
</p>

---

## 💡 The Technology: Server vs. Client Authority

This challenge forced me to dive deep into how game engines handle "The Source of Truth." I spent hours asking for help on Discord, but eventually, I had to roll up my sleeves and experiment. I learned that cloning an object isn't just about making a copy; it's about *who* makes the copy and *where* it lives.

### Lessons Learned
* **Server Authority:** The server is the only one who can truly "create" an item that everyone else can see. If a client clones something, it’s just a local hallucination.
* **LocalScript Execution:** I discovered that LocalScripts inside tools have very strict rules about when they "wake up." If the server clones them incorrectly, they stay dormant forever.
* **NetMessages:** Mastered the art of using `NetMessage` to bridge the gap between player input (Client) and game logic (Server).

---

## ⚙️ Development Challenges and Solutions

I went through a dozen iterations, including a 2-hour stint where I rewrote the entire system to be local-only just to test the logic, before realizing the architecture itself was the problem.

### Problem 1: The "Ghost" Item

Initially, I tried cloning the gun prefab directly in a `LocalScript`. 

* **The Unexpected Behavior:** My console would print `Purchase Successful`, and it even claimed the gun's parent was the `Backpack`. But when I looked at my character, my hands were empty.
* **The Core Issue:** The `Backpack` belongs to the Server's domain. When a `LocalScript` clones an instance, the Server literally doesn't "see" it. I was putting a "Client-only" object into a "Server-owned" container.
* **The Fix:** I moved the cloning logic to the **Server script**. By having the Server perform the `Clone()` and set the `Parent`, the item was replicated to the entire game world properly.

### Problem 2: The Silent Script

Once the gun finally appeared, a new nightmare began: the LocalScript inside the gun wouldn't run. No prints, no inputs, nothing.

* **The Difficulty:** I realized that when the Server parents a tool to the Backpack, the engine doesn't always automatically trigger the LocalScripts inside if the player is already spawned.
* **The Breakthrough:** I moved away from having 20 different scripts inside 20 different guns. 
* **The Fix:** The "Big Brain" play was creating a **Master Gun Controller**. Instead of relying on a script inside the gun to "wake up," I wrote a persistent LocalScript that stays on the player and "listens" for whenever a new item is added to the Backpack. The moment the Server gives the player a gun, the Master Script "hooks" it and handles the inputs.

---

## 🎬 Next Steps

With the weapon system finally optimized and the networking logic ironed out, I've laid the foundation for the entire combat loop. Now that players can actually *hold* and *fire* their purchases, I can move on to:
1.  **Zombie AI Polish:** Making the enemies react to the new functional weapons.
2.  **Visual Feedback:** Adding muzzle flashes and shell ejections to that beautifully working LocalScript!