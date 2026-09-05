# mach-raylib ![Mach](https://img.shields.io/badge/language-Mach-orange)
Mach language bindings for [Raylib](https://github.com/raysan5/raylib)

# How to use
1. Create new project
```zsh
mach init mygame
```
2. You can choose one of the two methods to add `mach-raylib` and run `mach dep pull`
   1. `mach dep add mach-raylib --git` https://github.com/Angluca/mach-raylib
      `mach dep add mach-std --git` https://github.com/briar-systems/mach-std
   2.  Or write it to `mach.toml`
```toml
[dep.mach-raylib]
git = "https://github.com/angluca/mach-raylib"
ref = "branch/main"

[dep.mach-std]
git = "https://github.com/briar-systems/mach-std"
ref = "branch/main"
```
3. write `main.mach`
<img width="200" height="178" alt="basic_window" src="https://github.com/user-attachments/assets/8b203cf6-30f0-42c8-bcdf-f31f70218850" />

```rust
use std.runtime;
use raylib.ra;  # ra is composed of raylib/raymath/rcamera

#[symbol("main")]
fun main(argc: i64, argv: **u8) i64 {
    val sw: i32 = 200;
    val sh: i32 = 150;
    ra.init_window(sw, sh, "^^v");
    ra.set_target_fps(60);

    val color: ra.Color = ra.Color{ r: 200, g: 100, b: 90, a: 255 };
    for (!ra.window_should_close()) {
        ra.begin_drawing();
            ra.clear_background(ra.LIGHTGRAY);
            ra.draw_text("Mach", 40, 76, 40, color);
            ra.draw_text("raylib", 72, 100, 40, ra.BLACK);
        ra.end_drawing();
    }

    ra.close_window();
    ret 0;
}
```
4. Download or build [Raylib Library](https://github.com/raysan5/raylib)
5. `build` and `run` it
```zsh
# mach build . -L lib_path --profile release
mach build . -L lib_path
# or
mach build . -L lib_path -l libname.a or .dylib or name
mach run .
```
## Examples
[mach-raylib examples](https://github.com/Angluca/mach-raylib_examples)
