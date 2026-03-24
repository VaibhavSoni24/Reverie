# Reverie

A 3D third-person action-adventure game built with Unity 6, featuring smooth player movement, cinematic camera controls, and a detailed temple environment.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Controls](#controls)
- [Project Structure](#project-structure)
- [Scripts](#scripts)
- [Building](#building)
- [Recommended Project Settings](#recommended-project-settings)

---

## Overview

Reverie is an early-stage third-person action game set inside a richly detailed ancient temple environment. The player can explore the space, interact with objects, and perform combat actions — all driven by a Rigidbody-based character controller, Cinemachine cameras, and Unity's modern Input System.

---

## Features

- **Third-person player controller** — walk, run, jump, roll, and attack
- **Camera-relative movement** — character always moves in the direction the camera faces
- **Cinematic camera** — smooth pitch/yaw camera via Cinemachine
- **Interactive objects** — collectible/narrative letter with animated pop-out
- **High-quality environment** — Sun Temple asset pack with buildings, nature, props, and VFX
- **Mixamo character animations** — rigged humanoid characters with full animation sets

---

## Tech Stack

| Category | Technology |
|---|---|
| Engine | Unity 6000.0.61f1 |
| Language | C# |
| Camera | Cinemachine 3.1.5 |
| Input | Unity Input System 1.14.2 |
| Animation | Unity Animator + Mixamo |
| UI | Unity UGUI 2.0.0 |
| Physics | Unity 3D Physics (Rigidbody) |
| 3D Modeling | Blender 3.0 |

---

## Prerequisites

- [Unity Hub](https://unity.com/download)
- **Unity 6000.0.61f1** (exact version required)
- [Git LFS](https://git-lfs.github.com/) (required for large binary assets)

---

## Getting Started

1. **Install Git LFS** (if not already installed):
   ```bash
   git lfs install
   ```

2. **Clone the repository:**
   ```bash
   git clone https://github.com/VaibhavSoni24/Reverie.git
   cd Reverie
   ```

3. **Open in Unity Hub:**
   - Open Unity Hub
   - Click **Add** → **Add project from disk**
   - Select the cloned `Reverie` folder
   - Ensure **Unity 6000.0.61f1** is selected as the editor version
   - Click **Open**

4. **Wait for the initial import** — the project contains ~2.2 GB of assets and may take several minutes to import on first open.

5. **Open the main scene:**
   - In the Project window, navigate to `Assets/Scenes/`
   - Double-click `SampleScene.unity`

6. **Press Play** to run the game.

---

## Controls

| Action | Input |
|---|---|
| Move | `W` / `A` / `S` / `D` |
| Look / Rotate Camera | Mouse |
| Jump | `Space` |
| Roll | `Left Ctrl` |
| Light Attack | `Left Mouse Button` |
| Heavy Attack | `Right Mouse Button` |
| Interact | `E` (hold) |

---

## Project Structure

```
Reverie/
├── Assets/
│   ├── Scenes/             # Game scenes
│   ├── Scripts/            # Custom C# game scripts
│   ├── Prefabs/            # Pre-built game objects
│   ├── Mixamo/             # Rigged character models and animations
│   ├── Letter/             # Interactive letter model and animations
│   ├── Sun_Temple/         # Environment asset pack
│   └── InputSystem_Actions.inputactions
├── Packages/               # Unity package manifest and lock file
├── ProjectSettings/        # Unity project configuration
└── Letter.blend            # Blender source file for letter model
```

---

## Scripts

All custom scripts are located in `Assets/Scripts/`.

### `PlayerController.cs`
Main character controller handling:
- **Movement** — camera-relative walk (`2.0 m/s`) and run (`5.0 m/s`)
- **Jump** — with ground detection via Rigidbody physics
- **Roll** — dodge-roll action (`Left Ctrl`)
- **Attacks** — light (`LMB`) and heavy (`RMB`) attack triggers
- **Animation** — drives the Animator with movement state parameters

### `FollowTarget.cs`
Third-person camera controller:
- Pitch/yaw rotation driven by mouse input
- Vertical look clamped between **-40°** and **70°**
- Configurable rotation speed (default `200`)

### `PlayerMouseRotation.cs`
Handles horizontal rotation of the player to match camera facing direction using the Input System `Look` action.

### `LetterInteract.cs`
Single-use interaction for the collectible letter object:
- Triggers an Animator-driven pop-out animation on `E` (hold)
- Designed as a template for future collectible or narrative interactions

---

## Building

1. Open **File → Build Settings**
2. Select your target platform (PC, Mac, Linux, etc.)
3. Click **Add Open Scenes** to include the current scene
4. Click **Build** and choose an output directory

---

## Recommended Project Settings

For the best visual quality and performance (especially with the Sun Temple environment):

| Setting | Recommended Value |
|---|---|
| Color Space | **Linear** |
| Rendering Path | **Deferred** |

These can be configured in **Edit → Project Settings → Player** (Color Space) and the active **Render Pipeline Asset**.
