<p align="center">
  <a href="https://amethyst.rs">
    <img
        alt="Amethyst"
        src="https://amethyst.rs/brand/logo-standard.svg"
        width="60"
    />
  </a>
  <a href="https://www.codeandweb.com/texturepacker">
    <img
        alt="TexturePacker"
        src="https://www.codeandweb.com/o/img/texturepacker512-512.png"
        width="60"
    />
  </a>
</p>
<h1 align="center">
  Amethyst spritesheet example
</h1>

This project demonstrates how you can use sprite sheets packed with [TexturePacker](https://www.codeandweb.com/texturepacker) in your Amethyst application.

## Quickstart

- Clone the repository

```bash
git clone https://github.com/CodeAndWeb/amethyst-spritesheet-example.git
cd amethyst-spritesheet-example
```

- Build and run the project

```bash
cargo run
```

## Features

This project contains the minimum amount of code needed to draw sprites to the screen. Here's a small summary of what you'll find in the source files:

- `resources/sprites/fruits/*.png`
  The individual sprites which will be packed on a sprite sheet.

- `resources/sprites/fruits.tps`
  The TexturePacker project file. Can be opened by TexturePacker UI oder command line client
  to (re)pack the sprite sheet.

- `resources/sprites/fruits.png`, `resources/sprites/fruits.ron`
  The sprite sheet and its corresponding data file, both generated with TexturePacker.
  The data file contains the coordinates of the sprites on the sheet.

- `src/state/sprites.rs`
  A file containing constants for all sprites, these constants can be used to access sprites by
  name instead of by index position. This file can be generated with TexturePacker, too.

- `src/main.rs`  
  Creates the render graph, adds the required bundles, builds the game data with our own state and finally, starts the game's main event loop.

- `src/state.rs`  
  Implements the main game state. In the `on_start` hook, the camera is initialized, and the sprites that will be drawn are loaded and their entities created.  
   In the `handle_event` hook, we print any keys that were pressed and close the window if the user presses escape or the OS requests that we quit.


#### For Mac Users

This starter uses vulkan as a renderer by default. You'll want to change the backend to use `metal`, which can be done by opening the `Cargo.toml` file and changing

```toml
[features]
default = ["vulkan"]
```

to

```toml
[features]
default = ["metal"]
```

If using OSX and Metal you will require full XCode installed from the Appstore in order to compile metal shaders.
After install you may be required to run this command `sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer` [reference gfx-rs issue](https://github.com/gfx-rs/gfx/issues/2472)

#### For Linux Users

You might need to install some dependencies. Please refer to [this section](https://github.com/amethyst/amethyst#dependencies) of the README for more details.
