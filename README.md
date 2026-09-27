# Starship-Genesis

A 2D arcade shooter built in Unity. Move freely, aim with the mouse, and clear
waves of enemies across a set of hand-built levels.

## Play

| Action | Control |
|---|---|
| Move | `W` `A` `S` `D` / arrow keys |
| Aim | Mouse |
| Fire | Left mouse button |
| Pause | Configured pause action (`UIManager.pauseAction`) |

Clear a level by defeating the required number of enemies before your health
runs out. Progress and high scores persist between sessions.

## Features

- Wave-based enemy spawning with per-level configuration
- Health and damage component system, shared by player and enemies
- Three enemy archetypes: chaser, straight shooter, and diagonal shooter
- Page-based UI manager (main menu, level select, instructions, pause, victory, game over)
- Title, victory, and defeat effects

## Technical

| | |
|---|---|
| Engine | Unity 6000.3.11f1 |
| Render pipeline | Universal Render Pipeline (2D) |
| Input | Input System |
| Text | TextMesh Pro |
| Audio | Built-in audio, music and SFX per scene |

### Project layout

```text
Assets/
  _Scenes/            MainMenu, Level1-3
  Scripts/
    Camera/           CameraController
    Enemies/          Enemy, EnemySpawner
    Health&Damage/    Health, Damage
    Player/           Controller
    ShootingProjectiles/  Projectile, ShootingController
    UI/               UIManager, UIPage, UIelement, displays and buttons
    Utility/          GameManager and helpers
```

Architecture notes:

- `GameManager` is a singleton owning score, high score, and win/lose state.
- `UIManager` drives a stack of `UIPage` panels and handles pause via
  `Time.timeScale`.
- `Health` and `Damage` are reusable components, so anything can take or deal
  damage without inheriting from a base class.
- `EnemySpawner` spawns on a timer within a configurable range and hands each
  instance its follow target and projectile holder.

## Running locally

1. Install Unity Hub and add Unity `6000.3.11f1`.
2. Clone this repository.
3. Open the project folder in the Unity Hub and let it import (first import
   takes a few minutes).
4. Press Play. The build scene list starts at `MainMenu`.

Large binaries (`.wav`, `.fbx`, `.psd`) are stored with Git LFS, so install it
before cloning: <https://git-lfs.github.com>

## Credits

Art and audio assets are bundled with the project. See the attribution files
alongside the assets for their sources and licenses.