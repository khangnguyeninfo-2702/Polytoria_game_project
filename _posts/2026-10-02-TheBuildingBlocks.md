---
layout: post
title: "Devlog #1: UI Foundations, Input Sinking, and the Hub Architecture"
date: 2026-02-10 13:13:00
categories: [polytoria, programming, devblog, ui, architecture]
---

## 🎨 Phase 1: Building the Main Menu & HUD (Feb 10th)

I kicked off this project by establishing the basic flow of the game—moving from a title screen into the active game world. This was primarily a UI day, focusing on getting the presentation and "feel" of the menus right before diving into the zombie AI.

### The UI Toolkit: Visibility and Interaction

I started by building out the GameMenu and the Clock/Menu HUD. This introduced me to the specific way Polytoria handles UI layers and mouse input:

* **`UIView` and `UIButton` Nodes:** I set up these core elements to ensure the Main Menu overlays the game world properly.
* **Property Management:** I learned that just hiding a menu isn't enough; you have to manage the physical "hitbox" of the UI as well.

### Problem Breakdown: The Invisible Wall

My biggest battle was with "Input Sinking." Even when the menus were gone, I couldn't click on anything in the game world.

1.  **Ghost UI Blocks:** Setting `Visible = false` makes the element disappear, but the mouse still "hits" the invisible glass of the UI container.
    * **Solution:** I updated my toggle functions to always pair `Visible` with the `Interactable` property. If the menu is hidden, it is now also set to not interactable, allowing clicks to pass through to the 3D world.
2.  **Parent-Child Inheritance:** I have a lot of buttons (Play, Store, Settings, Votekick), and the parent containers didn't have a global "Interactable" switch.
    * **Solution:** I wrote a recursive function using `:GetChildren()`. Now, when I hide a menu, the script automatically loops through every button inside and disables them all at once.
3.  **The "Nil" Crash:** During a refactor, my script kept crashing with an `attempt to call a nil value` error.
    * **Solution:** This was a classic developer oversight—a naming mismatch. I had defined `SetHoverEffect` but was calling `SetupHoverEffect`. Fixing the typo restored the entire UI's functionality.

---

## 💥 Phase 2: Dynamic Systems and State (Feb 10th)

The next step was making the UI feel "alive" and responsive to the server's state, especially for the lobby phase.

### The Multi-Player Ready System

I implemented a "Ready Up" button that tracks how many players are prepared for the first wave.

* **State Toggling:** Instead of a one-way click, I used a boolean variable (`isReady`) to track the player's state. Clicking once adds 1 to the count; clicking again subtracts it.
* **Dynamic Player Count:** Using `#game.Players:GetPlayers()`, the button text automatically scales (e.g., "Ready 1/4"), so it always knows how many people are in the server without manual updates.

### Universal Hover Effects

To save time and keep the code "DRY" (Don't Repeat Yourself), I moved away from writing unique code for every button hover.

* **The Logic:** I created a single function that accepts a `button` as an input. Now, I can pass any button—from the "Tank" class selector to the "Settings" menu—into this function, and they all get the same polished random-color hover effect automatically.

---

## ⏱️ Phase 3: Hub Architecture and Teleportation

Finally, I focused on the "Big Picture" of the game's world. I decided to build this as a Multi-Place Universe rather than one giant file.

* **The Hub Model:** The main game file now serves as a high-performance lobby where players can choose their difficulty.
* **Teleportation:** I integrated `TeleportService` to send players to separate Place IDs for "Easy," "Normal," and "Hard" modes. This keeps the zombie logic and map assets from lagging the main menu.

## 🎬 Next Steps

With the fundamentals of the UI and world structure working, I'll be looking at enhancing the player classes. I'll be drawing up the specific stats for the **Tank** and **Artificer** and starting on the basic zombie pathfinding logic.