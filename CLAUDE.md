# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Defold game engine tutorial project called "Walking Astronaut Tutorial". It demonstrates basic character movement, input handling, and sprite animation in the Defold 2D game engine.

## Commands

### Build and Run
- **Build and run the game**: Use the Defold editor menu: `Project ▸ Build` or open `defold://project.build` in the editor
- **Build output**: Compiled files are placed in the `build/default/` directory

### Development
- The project uses the Defold editor for development - there are no traditional command-line build tools
- Hot-reload is supported in the Defold engine for script changes during development

## Architecture

### Core Structure
- **Bootstrap Collection**: `/main/main.collection` - Entry point defined in `game.project`, contains the main game scene
- **Game Objects**: Container entities that hold components (e.g., `/main/astronaut.go`)
- **Components**: Functional parts like sprites, scripts, tilemaps that give game objects behavior
- **Scripts**: Lua files (`.script`) that define game object behavior with lifecycle functions

### Key Files
- `game.project` - Main project configuration (bootstrap collection, display settings)
- `/main/main.collection` - Bootstrap collection containing astronaut and level game objects
- `/main/astronaut.go` - Player character game object blueprint
- `/main/astronaut.script` - Player movement and animation logic
- `/main/astronaut.atlas` - Sprite atlas containing character animations (idle, left, right, front, back)
- `/main/level.tilemap` - Level geometry and collision detection
- `/input/game.input_binding` - Input mappings (arrow keys, mouse)

### Script Lifecycle Functions
Scripts use standard Defold lifecycle functions:
- `init(self)` - Component initialization
- `update(self, dt)` - Frame update loop
- `on_input(self, action_id, action)` - Input event handling
- `on_message(self, message_id, message, sender)` - Message passing
- `final(self)` - Component cleanup
- `on_reload(self)` - Hot-reload handling

### Input System
- Input actions defined in `/input/game.input_binding`
- Mapped actions: "left", "right", "up", "down", "touch"
- Input focus must be acquired with `msg.post(".", "acquire_input_focus")`

### Movement and Collision
- The astronaut script implements tile-based collision detection
- Uses AABB (Axis-Aligned Bounding Box) collision testing
- Separates X and Y axis movement for smooth wall sliding
- Collision layer named "collision" in the tilemap

### Animation System
- Sprite animations stored in atlas files as animation groups
- Direction-based animation switching (idle, left, right, front, back)
- Uses `sprite.play_flipbook()` to change animations
- Animation state tracking prevents unnecessary restarts