# Jarvis Glasses – Vision

## Core Fantasy

You put on a pair of sleek glasses.  
Suddenly the world has an AI layer.

You can look at a block and ask “What is this useful for?”  
You can say “Find me the nearest diamonds” and get a direction.  
You can say “Build a 5x5 platform in front of me” and watch it happen.  
You can ask “Any threats nearby?” and get a real answer.

It should feel like having a personal AI assistant that lives in your vision, not like typing commands at a robot.

## Design Principles

1. **Wearable first** – Features only fully unlock while the glasses are equipped.
2. **Natural language** – Prefer “Jarvis, scan that” over rigid slash commands.
3. **Context aware** – The AI should know what you’re looking at, where you are, and roughly what you have.
4. **Helpful, not overpowered** – It assists. It doesn’t play the game for you.
5. **Hybrid intelligence** – Use real LLMs for understanding, Script API for execution.

## Feature Ideas

### Scanning
- Identify block / entity you’re looking at
- Show hardness, tool required, drops, rarity
- Detect structures or interesting features in view

### Finding
- Nearest resource (ore, tree type, specific block)
- Structures (village, stronghold, monument…)
- Player markers / last death / waypoints you set

### Building Assist
- Simple shapes (platform, wall, box, staircase)
- “Fill this area with X”
- Blueprint suggestions
- Scaffolding helper

### Awareness
- Time, weather, biome, dimension
- Nearby hostile mobs
- Inventory suggestions (“You’re low on food”)

### Memory
- Named locations
- Previous conversations / goals
- Preferred build style

## Technical Direction

- Bedrock Script API (JavaScript/TypeScript) for the in-game side
- Lightweight bridge (Cloudflare Worker, Northflank, or simple Node server) for the LLM calls
- Structured output from the AI so the game can reliably execute actions
