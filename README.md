# Status
* **v00.00.69**: Only Debug Mode, published
* **v01.01.00**: Found (dev build), fixing in progress, private for now
* **Game Graphics**: No info (Vbios , io_state needed)
* **GPU**: Partially Found
* **CPU**: Lost, no info

## Language
- [English](#english)
- [Русский](#русский)
  
<a id="english"></a>
# Pac-Man VR (1996), PC Port

 * Ported by ErrorDan
 * Developer: Virtuality (Virtuality Group / Virtuality Entertainment
 * ROM purchase & dump: chilistudios (aka PACNATIC)

#**PLEASE USE DOSBOX, NOT DOSBOX-X!!!!**

 This is a patched version of the rare Pac-Man VR arcade game (originally developed by Virtuality for Namco in 1996). The original game required a proprietary SU2000 VR headset and specific hardware cards to run. This port bypasses those hardware checks, allowing the game logic to run on standard pc emulators like DOSBox.

  Due to the hardware dependency of the 3d rendering library , the game currently runs in Debug Text Mode. The game logic, AI, and sound are fully functional, but the 3D graphics are replaced by a developer overlay showing coordinates and state because of the hardware. 

# How to Run

1.  **Download DOSBox-X**: [https://dosbox-x.com/](https://dosbox-x.com/)
2.  **Extract Files**: Unzip this archive into a folder.
3.  **Launch**:
    *   Drag and drop RUN_GAME.BAT onto the DOSBox-X executable.
      [PHOTO](https://github.com/ErrorDanOfficial/PacMan-VR-1996-WORKING-DEBUG/blob/main/HOWTOSTART.png)
    *   OR run via command line: `dosbox-x -conf dosbox_pacman.conf` (don't forget to change path name!) [PHOTO](https://github.com/ErrorDanOfficial/PacMan-VR-1996-WORKING-DEBUG/blob/main/SECONDWAY.png)
4.  **Controls**:
    won't even work

## Technical:

* Getting this game to run required overcoming/bypassing major obstacles:

* The game relies on PIX.DLL,  which is hardcoded to communicate with Virtuality's proprietary PCI cards. Over 332 calls to this library were intercepted and bypassed (NOP'd) to prevent the game from crashing when it couldn't find the files. the startup code contained infinite loops of waiting for hardware status registers to flip. These were patched to skip it. The PC port exceeded the original hardware's polygon limits, causing a hard crash (Too many vertices). It was patched the jump instruction (JGE to JMP) to ignore this limit, allowing full level geometry to load. The game was designed for an arcade and waited for a specific memory bit (Coin Insert and Start Button) to change via I/O. Thats was patched to bypass this check, enabling autostarting

### Easter Eggs :)
*   Debug Mode: The text mode you see is actually a built-in developer tool WHICH FINALLY SUPPORTS VGA. The original devs included (PIX_Open failure fallback) to debug game logic without the headset. It displays raw head tracking data and ghost AI.
*   VGA Mode: VGA mode was hardcoded and disabled by developers.

<a id="русский"></a>
# Pac-Man VR (1996), ПК порт

* Портировано: ErrorDan
* Разработчик: Virtuality (Virtuality Group / Virtuality Entertainment)
* Покупка и дамп ROM: chilistudios (aka PACNATIC)

#**ИСПОЛЬЗУЙТЕ DOSBOX, DOSBOX-X ТЯЖЕЛО НАСТРОИТЬ**

Это пропатченная версия редкой аркадной игры Pac-Man VR (первоначально разработанной Virtuality для Namco в 1996 году). Оригинальная игра требовала фирменный VR-шлем SU2000 и специфические аппаратные платы для запуска. Этот порт обходит проверки оборудования, позволяя игровой логике работать на обычных PC-эмуляторах, таких как DOSBox.

Из-за аппаратной зависимости библиотеки 3D-рендеринга игра сейчас работает в текстовом режиме Debug. Игровая логика, AI и звук полностью функциональны, но 3D-графика заменена разработческим оверлеем, показывающим координаты и состояние из-за оборудования.

# Как запустить

1. **Скачайте DOSBox-X**: [https://dosbox-x.com/](https://dosbox-x.com/)
2. **Распакуйте файлы**: распакуйте этот архив в папку.
3. **Запуск**:

   * Перетащите RUN_GAME.BAT на исполняемый файл DOSBox-X.
     [ФОТО](https://github.com/ErrorDanOfficial/PacMan-VR-1996-WORKING-DEBUG/blob/main/HOWTOSTART.png)
   * ИЛИ запустите через командную строку: `dosbox-x -conf dosbox_pacman.conf` (не забудьте изменить путь!)
     [ФОТО](https://github.com/ErrorDanOfficial/PacMan-VR-1996-WORKING-DEBUG/blob/main/SECONDWAY.png)
4. **Управление**:
   всё равно не работает

## Техническое:

* Чтобы заставить игру работать, потребовалось преодолеть/обойти серьёзные препятствия:

* Игра опирается на PIX.DLL, который жёстко прописан для связи с фирменными PCI-картами Virtuality. Более 332 вызовов к этой библиотеке были перехвачены и обойдены (заменены на NOP), чтобы предотвратить падение игры при отсутствии файлов. Стартовый код содержал бесконечные циклы ожидания изменения регистров состояния оборудования. Они были пропатчены, чтобы пропустить это. PC-порт превысил лимиты полигонов оригинального оборудования, что вызывало жёсткий краш (Too many vertices). Был пропатчен переход (JGE на JMP), чтобы игнорировать этот лимит и позволить загрузить полную геометрию уровней. Игра была рассчитана на аркадный автомат и ждала изменения определённого бита памяти (Coin Insert и Start Button) через I/O. Это было пропатчено для обхода проверки и включения автозапуска.

### Пасхалки :)

* **Debug Mode**: Текстовый режим, который вы видите, на самом деле встроенный инструмент разработчиков, КОТОРЫЙ НАКОНЕЦ-ТО ПОДДЕРЖИВАЕТ VGA. Оригинальные разработчики включили (PIX_Open failure fallback), чтобы отлаживать игровую логику без шлема. Он отображает сырые данные трекинга головы и AI призраков.
* **VGA Mode**: VGA-режим был жёстко прописан и отключён разработчиками.








