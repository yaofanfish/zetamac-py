# Introduction

This is really an ongoing project so although the core features should all work, there will be some ongoing dev. 

# zetamac-cxx

A terminal-first mental arithmetic trainer inspired by Zetamac, written in modern C++ with Lua scripting support.

Unlike most arithmetic trainers, **zetamac-cxx is highly scriptable**. Problem generation, presets, analytics, and custom practice modes can all be extended in Lua without recompiling the program.

## Features

* ➕ Addition, subtraction, multiplication and division
* ⏱️ Timed games
* 🧠 Flash Anzan mode
* 📈 Replay previous runs
* 📊 Per-question analytics
* 💾 SQLite-backed score history
* 📝 Embedded Lua console
* 🔧 Fully scriptable problem generation
* 🖥️ Terminal interface with an experimental Qt GUI

## Lua Scripting

One of the main goals of this project is making custom practice sessions easy.

For example:

```lua
tt({7}, {6,7,8})
```
in the lua shell

practises only the 7 times table against 6, 7 and 8.

Presets can also be defined entirely in Lua:

```lua
function pre1()
    settings.operations = {"*"}
    settings.multiplication_bounds = {2, 12, 13, 19}
end
```

The generator itself is implemented in Lua, allowing new question types or completely different game modes to be added without touching the C++ code.

## Replay & Analytics

Every standard run is stored in SQLite.

You can:

* replay previous sessions
* compare replay speed against the original
* view fastest and slowest questions
* inspect average and median solve times
* access run data directly from Lua

## Configuration

User configuration lives in:

```text
~/.config/zetamac-cxx/luarc.lua
```

This file is loaded automatically on startup and can define:

* presets
* helper functions
* custom generators
* practice commands
* overrides for operand generation

## Dependencies

* C++20 compiler
* Lua 5.4
* sol2
* SQLite3
* SQLiteCpp
* nlohmann/json
* Qt (optional GUI)

## Building

```bash
git clone https://github.com/<your-username>/zetamac-cxx.git
cd zetamac-cxx
make
```

(or use your preferred build system if different.)

## Roadmap

* Better Qt interface
* More statistics and visualisations
* Additional training modes
* Better scripting API
* Plugin ecosystem

## Example

```
37 * 18 =
666
correct!

29 + 64 =
93
correct!

Score: 72
```

## Motivation

I wanted an arithmetic trainer that was both fast and hackable.

Most existing trainers have fixed question generators and limited customisation. This project instead exposes almost everything through Lua, making it easy to create specialised drills, experiment with new ideas, and analyse performance afterwards.

## License

MIT License.

# Additional info




