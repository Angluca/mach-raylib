# mach-raylib ![Mach](https://img.shields.io/badge/language-Mach-orange)
Mach language bindings for Raylib

# How to use
<img width="200" height="178" alt="图片" src="https://github.com/user-attachments/assets/7bd46b95-4182-41b9-b9e1-3181182ba348" />

1. Create new project
```zsh
mach init mygame
```
2. write it to `mach.toml` and pull it
```toml
[dep.mach-raylib]
git = "https://github.com/angluca/mach-raylib"
ref = "branch/main"
```
```zsh
mach dep pull
```
3. modify `main.mach`
```rust
use std.runtime;
use ra: raylib.raylib;

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
# Examples
open examples/xxx dir
* use Makefile
```zsh
# set makefile LIBS_PATH
make
# or
make file_name
# or
make run file_name
# or
make run file_name ARGS="-L ../../libs" 
```
* use Mach
```zsh
mach build . -L lib_path
# or 
mach build . -L lib_path --bin file_name

mach run . --bin file_name
```
