---
layout: post
title: "Devlog #5: Project 'Kinetic Foundation' – System Overhaul"
date: 2026-02-17 23:50:00
categories: [polytoria, updates, engineering, combat]
---

## 🚀 Transitioning from Prototype to Production

It has been a productive 48 hours. I’ve successfully moved the project away from 'placeholder' mechanics into a robust, scalable framework. The focus was on two pillars: **Authoritative Security** and **Kinetic Game Feel**.

Here's a funnny bug when implementing recoil logic
<p align="center">
  <img src="{{ site.baseurl }}/assets/images/recoil_bug.jpg" alt="Upside down recoil bug screen" width="800" />
  <br>
  <em>I'm hella concussed</em>
</p>

### 🛠️ Key Technical Milestones

* **Ballistic Evolution (Raycasting):** Migrated the entire weapon system from physical projectile instances to a high-performance Raycasting system. This eliminates 'bullet ghosting' at high velocities and provides pixel-perfect hit detection.
    
* **State & Data Management:** Implemented a centralized ModuleScript for data management. This move standardizes how weapon stats (Damage, Magazine size, etc.) are handled, paving the way for easier balancing and future inventory expansion.

* **UI & Ammo Authority:** Refactored the ammo tracking system. The UI now dynamically mirrors the server's authoritative ammo count, and I've successfully closed the 'Infinite Ammo' exploit by gating firing logic behind server-side magazine checks.

* **Engagement Loops (Zombie Waves):** Refined the core loop with a wave countdown and reward system. Fixed a critical bug where zombies would fail to spawn or double-spawn, ensuring the challenge scaling remains consistent.

* **Procedural Kineticism (Recoil):** Added a layered recoil system using Camera Rotation Offsets. Weapons now feel 'heavy' and reactive, requiring active aim compensation and skill-based recovery.

### 🎮 Quality of Life Improvements
* Added **Hotkeys**: 'M' for Menu and 'Ctrl' for localized cursor toggling.
* Implemented a **Ready System** for multiplayer lobby flow.
* Refined the environment maps for better sightlines during zombie waves.

**Aschente! The foundation is set. Now, we build the war.**