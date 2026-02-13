---
layout: post
title: "Devlog #3: Polytoria Network API & Message Serialization"
date: 2026-02-13 23:55:00
categories: [polytoria, networking, api, technical]
---

## 📦 Mastering the NetMessage Protocol

I've refactored the economy system to strictly adhere to the Polytoria `NetworkEvent` and `NetMessage` documentation. Transitioning to a structured message-passing architecture has significantly improved the Hub's data integrity.

### Implementation Logic
* **Serialization:** Instead of raw global variables, I’m now using `NetMessage.New()` to serialize combat rewards into a key-value pair format (Integers).
* **InvokedServer Handling:** The server-side listener now utilizes the `sender` parameter provided by the engine to securely identify which Challenger is requesting a stat update.
* **Data Unpacking:** Using `message:GetInt("key")`, the server extracts the coin and EXP deltas before committing them to the `sessionData` hash map.

**Aschente! The data is packed, signed, and delivered.**