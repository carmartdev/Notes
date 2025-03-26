
<span class="tag">Tags</span>:   [[Zig]] [[Coding]] [[SDL Library]] 

Created at 2024-10-05 17:10
<span class="tag">Status</span>: <span class="danger">Not done yet</span>
<span class="danger">Sources</span>:

# Zig-SDL2

## Imports
At first we would import the libraries:
```c
const c = @cImport({
    @cInclude("SDL2/SDL.h");
});
const assert = @import("std").debug.assert;
```
We're importing the SDL2 C library and the assert from std.  
## Main function

```c
pub fn main() !void {
```

## SDL Initialization

```c
if (c.SDL_Init(c.SDL_INIT_VIDEO) != 0) {
        c.SDL_Log("Unable to initialize SDL: %s", c.SDL_GetError());
        return error.SDLInitializationFailed;
    }
    defer c.SDL_Quit();
```
Initializes the SDL and quits if there's any error.

## Creating the Window

```c
const screen = c.SDL_CreateWindow("My Game Window", c.SDL_WINDOWPOS_UNDEFINED, c.SDL_WINDOWPOS_UNDEFINED, 400, 140, c.SDL_WINDOW_OPENGL) orelse
        {
        c.SDL_Log("Unable to create window: %s", c.SDL_GetError());
        return error.SDLInitializationFailed;
    };
    defer c.SDL_DestroyWindow(screen);
```
This piece of code creates a window and if you run the program it will open for moment and it closes suddenly after the creation.

## Creating the renderer

```c
const renderer = c.SDL_CreateRenderer(screen, -1, 0) orelse {
        c.SDL_Log("Unable to create renderer: %s", c.SDL_GetError());
        return error.SDLInitializationFailed;
    };
    defer c.SDL_DestroyRenderer(renderer);
```

## Main loop and end of the main function

```c
var quit = false;
    while (!quit) {
        var event: c.SDL_Event = undefined;
        while (c.SDL_PollEvent(&event) != 0) {
            switch (event.type) {
                c.SDL_QUIT => {
                    quit = true;
                },
                else => {},
            }
        }

        _ = c.SDL_RenderClear(renderer);
        _ = c.SDL_RenderCopy(renderer, zig_texture, null, null);
        c.SDL_RenderPresent(renderer);

        c.SDL_Delay(17);
    }
}

```
# References
