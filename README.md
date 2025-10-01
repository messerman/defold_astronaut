# Walking Astronaut Tutorial

A Defold game engine tutorial project demonstrating basic 2D character movement, tile-based collision detection, and sprite animation.

## Overview

This project showcases fundamental game development concepts using the Defold engine:
- **Character movement** with arrow key controls
- **Tile-based collision detection** using AABB (Axis-Aligned Bounding Box)
- **Directional sprite animations** (idle, left, right, front, back)
- **Smooth wall sliding** with separated X/Y axis collision resolution

## Getting Started

### Prerequisites
- [Defold Editor](https://defold.com/download/) installed

### Running the Project
1. Open the project in Defold Editor
2. Select `Project ▸ Build` from the menu or press `Ctrl+B` (Windows/Linux) / `Cmd+B` (macOS)
3. The game will launch in a separate window

### Controls
- **Arrow Keys**: Move the astronaut character
  - ↑ Up
  - ↓ Down
  - ← Left
  - → Right

## Project Structure

```
astronaut/
├── game.project              # Main project configuration
├── main/
│   ├── main.collection       # Bootstrap scene (entry point)
│   ├── astronaut.go          # Player character game object
│   ├── astronaut.script      # Movement and animation logic
│   ├── astronaut.atlas       # Sprite atlas with animations
│   └── level.tilemap         # Level layout and collision layer
├── input/
│   └── game.input_binding    # Input mappings
└── assets/                   # Sprites and visual assets
```

## Key Features

### Movement System
- Diagonal movement normalized to prevent faster diagonal speed
- Smooth collision response with wall sliding
- Tile-based collision detection (64x64 tile size)
- Hitbox offset for feet/bottom area collision

### Animation System
- Direction-based animation switching
- Animation state tracking to prevent unnecessary restarts
- Five animation states: idle, left, right, front (down), back (up)

### Collision Detection
- AABB collision using four corner samples
- Separate X and Y axis resolution for smooth movement
- Collision layer named "collision" in the tilemap
- World-to-tile coordinate conversion system

## Technical Details

- **Engine**: Defold 2D Game Engine
- **Language**: Lua
- **Display**: 1280x768
- **Tile Size**: 64x64 pixels
- **Movement Speed**: 250 pixels/second

## Learning Resources

- [Defold Documentation](https://defold.com/learn)
- [Defold Tutorials](https://defold.com/tutorials)
- [Defold Forum](https://forum.defold.com)

## License

This is a tutorial project for educational purposes.
