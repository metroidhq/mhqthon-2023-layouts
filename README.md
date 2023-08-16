# MHQthon 2022 Layouts

## Getting Started
To get started, clone or download & unzip this repo onto your computer in a place that OBS Studio or your broadcasting software of choice can access local HTML files.

## OBS Studio Setup
### Prerequites
* This guide assumes that you know how to add and place your own game capture, camera, and audio sources. If you have trouble with any of this, contact Elias and he will walk you through it.
* In your Profile video settings, make sure that your canvas resolution is set to 1920x1080.

### Host View
1) Create a new scene. Call it `Host View`.

2) Add a new Browser source to your new scene. Name it `Global Overlay`.

3) Set the following properties:
* URL `file://C:/path/to/the/downloaded/files/global.html`
* Width `1920`
* Height `1080`
* FPS `30`
  * Make sure Custom CSS is empty.

3) Click the lock icon next to the source to ensure it is not accidentally moved.

4) Add a new Browser source below `Global Overlay`. Name it `Host Overlay`.

3) Set the following properties:
* URL `file://C:/path/to/the/downloaded/files/layout.html?layout=host`
* Width `1920`
* Height `1080`
* FPS `30`
* Custom CSS
```css
#game-title::after { content: 'MHQthon 2022'; }
#next-game::after { content: '<Next Game in Schedule>'; }
  ```

5) Add and position your camera and audio sources under the Overlays.

### Game Views
For each game your location is streaming, do the following steps:
1) Create a new scene. Call it `<Game Name> View`.

2) Add the `Global Overlay` to your scene. Click the lock icon next to the source to ensure it is not accidentally moved.

3) Add a new Browser source below `Global Overlay`. Name it `<Game Name> Overlay`.

4) Set the following properties:
* URL `file://C:/path/to/the/downloaded/files/layout.html?layout=<Layout Name>`
* Width `1920`
* Height `1080`
* FPS `30`
* Custom CSS
```css
#game-title::after { content: '<Game Name>'; }
#next-game::after { content: '<Next Game in Schedule>'; }
#host-one::after { content: '<Player Name>'; }
  ```

5) Add and position your game capture, camera, and audio sources under the Overlays.

### Stand By View
1) Create a new scene. Call it `Stand By View`.

2) Add the `Global Overlay` to your scene. Click the lock icon next to the source to ensure it is not accidentally moved.

3) Add a new Browser source below `Global Overlay`. Name it `Stand By Overlay`.

4) Set the following properties:
* URL `file://C:/path/to/the/downloaded/files/layout.html`
* Width `1920`
* Height `1080`
* FPS `30`
* Custom CSS
```css
#game-title::after { content: 'MHQthon 2022'; }
#next-game::after { content: '<Next Game in Schedule>'; }
#stand-by-title::after { content: 'Returning Shortly'; }
  ```

5) Add your desktop audio source and a source for Metroid music looping playback of your choice.

### Countdown View
1) Create a new scene. Call it `Countdown View`.

2) Add the `Global Overlay` to your scene. Click the lock icon next to the source to ensure it is not accidentally moved.

3) Add a new Browser source below `Global Overlay`. Name it `Stand By Overlay`.

4) Set the following properties:
* URL `file://C:/path/to/the/downloaded/files/layout.html?countdown&nocomms`
* Width `1920`
* Height `1080`
* FPS `30`
* Custom CSS
```css
#game-title::after { content: 'MHQthon 2022';}
#next-game::after { content: '<First Game of the Broadcast>';}
  ```

5) Add your desktop audio source and a source for Metroid music looping playback of your choice.

### Ending View
1) Create a new scene. Call it `Ending View`.

2) Add the `Global Overlay` to your scene. Click the lock icon next to the source to ensure it is not accidentally moved.

3) Add a new Browser source below `Global Overlay`. Name it `Ending Overlay`.

4) Set the following properties:
* URL `file://C:/path/to/the/downloaded/files/layout.html?nocomms&nonext`
* Width `1920`
* Height `1080`
* FPS `30`
* Custom CSS
```css
#game-title::after { content: 'MHQthon 2022'; }
#stand-by-title::after { content: 'See You Next Year!'; }
  ```

5) Add your desktop audio source and a source for Metroid music looping playback of your choice.

## Notes

* Valid Layout Names are `host`, `nes`, `nesrace2p`, `snes`, `snesrace2p`, `snesrando`, `fullscreen`, `fullscreenrace2p`, `fullscreenrando`, `fullscreenrandorace2p`, `fullscreenrandorace3p`, `fullscreenrandorace4p`, `widescreen`, `widescreenrace2p`, `widescreenrando`, `gb`, `gbrace2p`, `gba`, `gbarace2p`, `gbarando`, `gbarandorace2p`, `gbarandorace3p`, `ds`, `dsrace2p`, `dstall`, `dstallrace2p`, `3ds`, & `3dsrace2p`.
  * If you provide an invalid Layout Name, it should be immediately evident in the rendering of the layout.
* If you are the last game on the schedule, set the `#next-game` line of CSS to `Nothing` or the met incentive game goal.
* For some of the older consoles like NES or SNES, you may have to skew the game capture, as the fullscreen output of the game is not the native resolution of the console.
