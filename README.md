# Jarvis Glasses

**A wearable AI assistant for Minecraft Bedrock Edition.**

Inspired by Tony Stark’s glasses — not a mob that follows you, but a pair of glasses you wear. Talk to it, ask it to scan the world, find resources, help you build, and answer questions about what’s around you.

---

## Concept

You equip a special pair of **Jarvis Glasses**.  
While wearing them you can talk to the AI through chat (or a dedicated interaction).  
It can:

- **Scan** blocks, entities, and structures you’re looking at
- **Find** resources, biomes, structures, chests, your last death, etc.
- **Build** assist — place blocks, suggest designs, auto-build simple structures
- Answer questions about the world, inventory, threats, time, weather
- Remember places and goals you mark

---

## Approach: Middle Ground

This project is designed as a **layered system**:

1. **Offline Core (always works)**  
   Solid Script API features that work with no internet and no API key:
   - Raycast scanning
   - Basic find (nearest ore, structure, etc.)
   - Simple build assist (platforms, walls, shapes)
   - Local commands and responses

2. **Optional AI Layer**  
   When you want smarter natural language understanding, you can connect an external AI (Grok, Claude, Gemini, OpenAI, etc.) through a small bridge.  
   The offline core still works even if the AI is unavailable.

This way you get a usable glasses assistant right away, and the real “Jarvis” intelligence is an upgrade on top.

---

## Planned Architecture

```
Player (wearing glasses)
    ↓  chat / interact
Bedrock Script API (glasses item + systems)
    ↓
  ├─ Offline logic (scan / find / build)
  └─ Optional → AI Bridge → LLM → structured actions back into the game
```

### In-game components
- `jarvis_glasses` item (wearable)
- Script systems that:
  - Detect when the glasses are worn
  - Capture player chat directed at Jarvis
  - Read what the player is looking at (raycast)
  - Execute build/find/scan actions
  - Display responses (chat, title, actionbar, or custom UI)

### Optional AI Bridge
A lightweight backend that:
- Receives context (player position, looking-at block, inventory summary, recent chat)
- Sends a well-crafted prompt to the LLM
- Parses the response into structured actions the Script API can execute

---

## Goals (v0.1)

- [ ] Glasses item + basic wearable behavior
- [ ] Chat command / prefix to talk to Jarvis (`!j` or `jarvis, ...`)
- [ ] Raycast “what am I looking at?” scan (offline)
- [ ] Simple find commands (nearest diamond, village, etc.) (offline)
- [ ] Basic build assist (place platform, wall, simple shapes) (offline)
- [ ] Optional external AI bridge (can be added later)

---

## Status

Very early stage. This repo currently holds the vision and will grow into the actual Bedrock addon + optional bridge code.

---

## Credits / Inspiration

- Tony Stark’s glasses (Iron Man / MCU)
- Existing Bedrock AI companion experiments
- The Echo AI project (earlier companion work)
