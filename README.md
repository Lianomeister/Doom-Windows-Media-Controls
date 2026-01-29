# DOOM: Windows Media Controls Edition
**_"Have you ever wanted to play DOOM inside the Windows Media Controls overlay? Probably not, but now you can RIP AND TEAR!"_**

## What is This?
This is a fully functional DOOM-style FPS game that lives where it shouldn't: inside the Windows Media Controls Overlay (`Win + A`). It works by hijacking the browser's MediaSession API and HTML5 Canvas to stream a live 3D raycasted game feed as "Album Artwork" while a silent track plays in the background—tricking Windows into thinking a demon-slaying rampage is actually just a song with very aggressive metadata.

The game "screen" is displayed where the album art would normally go, kills and health are tracked in the song title, and ammo/gun status in the artist name. Keyboard media buttons (or the mouse) are used to control movement, turning, and shooting.

<table>
  <tr>
    <td valign="center">
      <br> 
        <div align="center">
          <img width="390" height="635" alt="website ui" src="/DoomSite.png" />
        <br>
        <p><sup><i>Figure 1: Screenshot of the webpage UI.</i></sup></p>
      </div>
    </td>
    <td width="400">
      <div align="center">
        <img width="390" src="/doommedia.png" alt="DOOM running" />
        <br>
        <p><sup><i>Figure 2: DOOM running in the Windows Media Controls Overlay.</i></sup></p>
      </div>
    </td>
  </tr>
</table>

## How to Play
1. Visit the site [HERE](https://[YOUR-USERNAME].github.io/doom-windows-media-controls/).

2. Initialize Hell Link: Choose your difficulty (optional) and then click the big red button to establish connection.

3. Open the "Game Screen": Press `Win + A` on your keyboard.

4. Press `Prev Track (⏮︎)` or `Next Track (⏭︎)` to start the carnage.


### The Controls*:

- `Prev Track (⏮︎)`: Turn LEFT
- `Next Track (⏭︎)`: Turn RIGHT
- `Play (⏵︎)`: Move FORWARD
- `Pause (⏸︎)`: SHOOT

**The Goal: Hunt demons. Survive. Get the high score. RIP AND TEAR!**

<sup>*Note: Some keyboards (like mine) will require holding down the `Fn` key in order to use the media buttons. Mouse controls also work - you can click the buttons directly in the overlay!</sup>

## Game Features

### 🎮 Core Mechanics
- **3D Raycasting Engine**: Real DOOM-style first-person perspective with textured walls
- **Enemy AI**: Demons that chase you and attack when close
- **Combat System**: Shoot enemies with your trusty gun (75 damage per shot)
- **Ammo Management**: Start with 50 rounds, enemies drop +2 ammo on death
- **Health System**: Start with 100 HP, demons deal 10 damage per attack
- **Dynamic Spawning**: Enemies continuously spawn based on difficulty

### 🔥 Visual Features
- **Raycasted 3D Rendering**: 80-ray system for smooth walls
- **Enemy Sprites**: Red demons with glowing yellow eyes
- **Health Bars**: Enemies show damage taken
- **Muzzle Flash**: Screen flash and gun animation when shooting
- **On-Screen HUD**: HP, Ammo, and Kill count
- **Low Health Warning**: Red pulsing screen when HP < 30
- **Low Ammo Warning**: Yellow warning when ammo < 5
- **Crosshair**: Green targeting reticle
- **Gun Sprite**: Visible weapon at bottom of screen

### ⚙️ Difficulty Levels

| Difficulty | Max Enemies | Spawn Rate |
|-----------|-------------|------------|
| **I'm Too Young To Die (Easy)** | 4 | 5 seconds |
| **Hurt Me Plenty (Normal)** | 6 | 3 seconds |
| **Ultra-Violence (Hard)** | 10 | 2 seconds |

## Technical Implementation

### The Raycasting Engine
This game uses a simplified version of the raycasting technique used in the original DOOM (1993). The engine:
- Casts 80 rays across the player's field of view
- Detects wall intersections to calculate distances
- Renders wall slices with distance-based shading
- Implements sprite rendering for enemies
- Uses different shading for horizontal vs vertical walls

### Enemy AI
Enemies feature simple but effective AI:
- **Chase Behavior**: Moves toward player at 0.02 units/frame
- **Collision Avoidance**: Won't walk through walls
- **Attack Range**: Attacks when within 2 units of player
- **Attack Cooldown**: 3 seconds between attacks
- **Ammo Drops**: Each killed enemy drops 2 rounds

### The Out-Of-Focus Paradox

The same problem from Snake applies here, but it's even more critical with DOOM's complex controls:
- To use traditional WASD keys, the browser tab needs focus
- To see the game, you must open the `Win + A` overlay
- Opening the overlay **removes focus** from the browser
- Clicking the browser to get focus back **closes the overlay**

The solution? **Media Keys**. They're the only inputs allowed to control a background webpage without closing the media overlay. While it's unconventional to use "Skip Track" to turn and "Pause" to shoot demons, it's what makes this technically possible.

## The Flickering Problem

Yes, the flickering exists. It's a limitation of how Windows refreshes the Media Controls overlay. The system wasn't exactly designed for real-time 3D gaming at 60fps.

The flickering is more noticeable in DOOM than in Snake due to:
- More complex graphics (3D raycasting vs 2D sprites)
- Constant movement and rotation
- Enemy animations and effects
- HUD updates

However, the gameplay is still surprisingly playable once you get used to it. Think of it as "retro screen tearing" for authentic 90s vibes. 😎

## Performance Notes

The game runs at approximately:
- **60 FPS** rendering
- **200ms** artwork update throttling (to reduce flickering)
- **100ms** metadata updates (for score/health display)

## Browser Compatibility

Tested and working on:
- ✅ Chrome/Edge (Windows 11)
- ✅ Firefox (Windows 11) 
- ❓ Other browsers with MediaSession API support

**Note**: This specifically targets Windows 11's Media Controls overlay. Other OS media overlays may display differently or not at all.

## Credits & Inspiration

- Original DOOM (1993) by id Software
- Raycasting tutorial inspiration from Lode Vandevenne
- "Snake: Windows Media Controls Edition" - the predecessor project that started this madness

## License
This project is licensed under the MIT License. You're free to fork it, break it, or turn it into the next big thing.

If this code helps you out (or makes you laugh), giving a little shout-out or a link back to this repo would be awesome. It's good for the soul—and my GitHub ego.

---

**WARNING**: Playing DOOM in your Windows Media Controls may cause:
- Confusion from coworkers
- Questions about your sanity
- An inexplicable urge to play more games in inappropriate places
- Carpal tunnel from holding the Fn key

**Play at your own risk. RIP AND TEAR! 💀🔥**