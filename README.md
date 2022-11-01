# bevy_rapier_cam (Based on bevy_flycam)
See the original here: [sburris0's github](https://github.com/sburris0/bevy_flycam). Provided with no warranty under the ISC license.

A basic first-person camera for Bevy 0.8.1 providing physics through [Rapier3D](https://rapier.rs/).

## Controls
* WASD to move horizontally
* SPACE to ascend
* LSHIFT to descend
* ESC to grab/release cursor.

## Comparison
This is not a simple fly camera like it's foundation, it is a physically based first person camera.

## Usage `!! HEAVY CONSTRUCTION !!` 
1. Add to `Cargo.toml` or copy `lib.rs` to your own file
```toml
[dependencies]
bevy = "0.8.1"
bevy_rapier_cam = { git = "https://github.com/GRAYgoose124/bevy_flycam_rapier3d.git"}
```

2. Include the `PlayerPlugin`
```rust
use bevy_flycam::PlayerPlugin;
```
This will spawn a camera for you. 
Use `NoCameraPlayerPlugin` if you do not want this and make sure to use `.insert(FlyCam)` on your own camera or else this plugin won't know what to move.

3. Add the `PlayerPlugin`:
```rust
#[bevy_main]
fn main() {
    App::new()
        .add_plugins(DefaultPlugins)
        .add_plugin(PlayerPlugin)
        .run();
}
```

Alternatively you can see the example `basic.rs` or `scroll.rs` located in the examples folder.
You can run the example by cloning this repository and run the command: `cargo run --release --example basic`

## Customization
To modify player movement speed or mouse sensitivity, import `bevy_flycam::MovementSettings` and add it as a resource:
```Rust
#[bevy_main]
fn main() {
    App::new()
        .add_plugins(DefaultPlugins)
        .add_plugin(PlayerPlugin)
        .insert_resource(MovementSettings {
            sensitivity: 0.00015, // default: 0.00012
            speed: 12.0, // default: 12.0
        })
        .run();
}
```

