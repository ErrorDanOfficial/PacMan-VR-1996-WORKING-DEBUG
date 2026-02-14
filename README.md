Pac-Man VR (1996), PC Port

 * Ported by ErrorDan
 * Developer: Virtuality (Virtuality Group / Virtuality Entertainment
 * ROM purchase & dump: chilistudios (aka PACNATIC)


 * This is a patched version of the rare Pac-Man VR arcade game (originally developed by Virtuality for Namco in 1996). The original game required a proprietary SU2000 VR headset and specific hardware cards to run. This port bypasses those hardware checks, allowing the game logic to run on standard pc emulators like DOSBox.

 * Due to the hardware dependency of the 3d rendering library , the game currently runs in Debug Text Mode. The game logic, AI, and sound are fully functional, but the 3D graphics are replaced by a developer overlay showing coordinates and state because of the hardware. 

# How to Run

1.  **Download DOSBox-X**: [https://dosbox-x.com/](https://dosbox-x.com/)
2.  **Extract Files**: Unzip this archive into a folder.
3.  **Launch**:
    *   Drag and drop RUN_GAME.BAT onto the DOSBox-X executable.
    *   *OR* run via command line: `dosbox-x -conf dosbox_pacman.conf` (don't forget to change path name!)
4.  **Controls**:
    won't even work

## Technical:

* Getting this game to run required overcoming/bypassing major obstacles:

* The game relies on PIX.DLL,  which is hardcoded to communicate with Virtuality's proprietary PCI cards. Over 332 calls to this library were intercepted and bypassed (NOP'd) to prevent the game from crashing when it couldn't find the files. the startup code contained infinite loops of waiting for hardware status registers to flip. These were patched to skip it. The PC port exceeded the original hardware's polygon limits, causing a hard crash (Too many vertices). It was patched the jump instruction (JGE to JMP) to ignore this limit, allowing full level geometry to load. The game was designed for an arcade and waited for a specific memory bit (Coin Insert and Start Button) to change via I/O. Thats was patched to bypass this check, enabling autostarting

### Easter Eggs :)
*   Debug Mode: The text mode you see is actually a built-in developer tool WHICH FINALLY SUPPORTS VGA. The original devs included (PIX_Open failure fallback) to debug game logic without the headset. It displays raw head tracking data and ghost AI.
*   VGA Mode: VGA mode was hardcoded and disabled by developers.

