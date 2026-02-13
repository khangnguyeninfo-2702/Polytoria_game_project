---
layout: post
title: "Devlog #2: NavMesh Logic & Infinity Errors"
date: 2026-02-12 21:00:00
categories: [polytoria, ai, debugging]
---

## 🧭 The Path to Infinity

I've transitioned the Zombie AI to use the native `SetNavDestination` method. While more efficient than manual waypoints, it introduced a new logic bug: `NavDestinationDistance` returning infinity.

### Debugging the Navigation Proxy
* **The Infinity Issue:** This typically signifies a 'Unreachable Destination.' If the pathfinder cannot calculate a valid route on the NavMesh, the distance defaults to infinity.
* **Syntax Refinement:** I realized I was using dot notation instead of colon notation for the method call. In Lua, `npc:SetNavDestination()` is required to pass the `self` reference correctly.
* **Coordinate Mapping:** I'm now normalizing the Y-coordinate of the destination to match the NPC's floor level, ensuring the AI doesn't try to pathfind into the air.

### Current Status
The 'Blank' logic is being refined. Once the NavMesh is properly baked into the Hub environment, the infinity error should resolve, allowing the horde to finally close the gap.