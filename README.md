﻿<!-- Heading -->
<br />
<p align="center">
  <a href="https://github.com/curlpipe/ox/">
    <img src="assets/logo.png" alt="Logo" width="150" height="150">
  </a>

  <h1 align="center" style="font-size: 50px;">Ox editor</h1>

  <p align="center" style="font-size: 20px;">
    Ox is a code editor that runs in your terminal.
    <br><br>
    <div align="center" style="display:inline;">
      <img src="https://i.postimg.cc/nrs9jksB/image.png" width="49%">
      <img src="https://i.postimg.cc/KcQ0nv1Y/image.png" width="49%">
    </div>
    <br>
</p>

![Build Status](https://img.shields.io/github/forks/curlpipe/ox.svg?style=for-the-badge)
![Build Status](https://img.shields.io/github/stars/curlpipe/ox.svg?style=for-the-badge)
![License](https://img.shields.io/github/license/curlpipe/ox.svg?style=for-the-badge)

## About

Ox is an independent text editor that can be used to write everything from text to code.

If you're looking for a text editor that...
1. :feather: Is lightweight and efficient
2. :wrench: Can be configured to your heart's content
3. :package: Has features out of the box,  including 
    - syntax highlighting
    - undo and redo
    - search and replace
    - line numbers
    - opening multiple files

...then Ox is right up your street

It runs in your terminal as a text-user-interface, just like vim, nano and micro, however, it is not based on any existing editors and has been built from the ground up.

It is mainly used on linux systems, but macOS and Windows users (via WSL) are free to give it a go.

## Selling Points

### Lightweight and Efficient

- :feather: Ox is lightweight, with the precompiled binary taking up roughly 3mb in storage space.
- :knot: It uses a `rope` data structure which allows incremental editing, file reading and file writing, which will speed up performance, particularly on huge files.
- :crab: It was built in Rust, which is a quick lower level language that has a strong reputation in the performance department.

### Strong configurability

- :electric_plug: Plug-In system where you can write your own plug-ins or integrate other people's
- :wrench: A wide number of options for configuration with everything from colours to the status line to syntax highlighting being open to customisation
- :moon: Ox uses Lua as a configuration language for familiarity when scripting and configuring

### Out of the box features

- :paintbrush: Syntax highlighting
- :arrow_right_hook: Undo and redo
- :mag: Search and replace text
- :file_folder: Opening multiple files at once
- :eye: UI that shows you the state of the editor and file

### Robustness

- :globe_with_meridians: Handles double-width unicode characters like a charm, including those of the Chinese, Korean and Japanese languages and emojis
- :boxing_glove: Backend has been thoroughly tested via automated unit tests

## Installation

> :warning: Huge Warning: A lot of these (except manual) are quite out of date, it is quite a huge task having to push to all these sources each time I update and I'd rather focus on creating high quality updates

### Prerequisites

Because Ox is written in Rust, you must have a modern and working version of `rustc` and `cargo`.

On Arch Linux, you can run this command:
```sh
sudo pacman -S rustup
rustup toolchain install stable
```

If you are not using Arch, you can easily set it up on other distros by running the distro-neutral command:
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
/usr/bin/rustup toolchain install stable
```
You must have `curl` installed in order to run this command.

### Installation Routes

#### Manual

The absolute best way to install Ox, it will ensure you always have the latest version

It should only really take at most 1 minute on most modern hardware.

```sh
cargo install --git https://github.com/curlpipe/ox
```

#### Arch Linux

Install `ox-bin` or `ox-git` from the Arch User Repository.

That's all there is to it!

#### Fedora/CentOS

Install `ox` from the [COPR Repository](https://copr.fedorainfracloud.org/coprs/atim/ox/): 

```
sudo dnf copr enable atim/ox -y
sudo dnf install ox
```

You can also find an rpm file in the releases page

#### Debian

You can find a deb file in the releases page, which can be installed via dpkg:

```sh
dpkg -i ox_version.deb
```

#### Homebrew

Install `ox` from Homebrew core tap.

```sh
brew install ox
```

#### MacPorts

On macOS, you can install `ox` via [MacPorts](https://www.macports.org)

```sh
sudo port selfupdate
sudo port install ox
```

## Quick Start Guide

This is just a quick guide to help get you up to speed quickly with how to use the editor. You dive into more details in the documentation section below, but this quick start guide is a good place to start.

### Opening Files

At the moment, you can open ox by using the command

```sh
ox
```

This will open up an empty document.

If you wish to open a file straight from the command line, you can run
```sh
ox /path/to/file
```

To open and edit a file. You can provide multiple arguments of files if you wish to open more than one, for example:

```sh
ox file1.txt file2.txt
```

You can also open a file from within Ox by using the <kbd>Ctrl</kbd>  + <kbd>O</kbd> key binding

If at any time, you wish to create a new file, you can use <kbd>Ctrl</kbd>  + <kbd>N</kbd> to do so.

You can find more command line options for Ox by typing:
```sh
ox --help
```

When you open multiple files, notice the tabs at the top.

You can close the file you're looking at using the <kbd>Ctrl</kbd>  + <kbd>Q</kbd> key binding. When no more documents are open, the editor will automatically close for you.

If you want to move tabs and look at other files that are open, you can use <kbd>Shift</kbd>  + <kbd>Left</kbd> and <kbd>Shift</kbd>  + <kbd>Right</kbd> to move back and forth respectively.

### Editing Files

There are no modes in Ox, so you can just type straight into an open file, just as you would nano, or windows notepad.

You can move the cursor around the file using the standard arrow keys. 

You can also use:
- <kbd>PageUp</kbd> - Move up a page in the viewport
- <kbd>PageDown</kbd> - Move down a page in the viewport
- <kbd>Home</kbd> - Go to the start of the current line
- <kbd>End</kbd> - Go to the end of the current line
- <kbd>Ctrl</kbd>  + <kbd>Left</kbd> - Go to the previous word
- <kbd>Ctrl</kbd>  + <kbd>Right</kbd> - Go to the next word
- <kbd>Ctrl</kbd>  + <kbd>Up</kbd> - Go to the top of the document
- <kbd>Ctrl</kbd>  + <kbd>Down</kbd> - Go to the bottom of the document

No surprises here, to insert characters, use the letters and numbers on your keyboard. <kbd>Enter</kbd> will put a new line in, <kbd>Tab</kbd> will create a tab (or indent) and <kbd>Backspace</kbd> / <kbd>Delete</kbd> to delete characters.

If you modify a file, you may notice a `[+]` symbol, this means the file has been modified without saving. You can save a document in many ways, including <kbd>Ctrl</kbd>  + <kbd>S</kbd> to save it to the file it was opened from. <kbd>Ctrl</kbd>  + <kbd>A</kbd> to save all files that are open and <kbd>Alt</kbd>  + <kbd>S</kbd> to save as, where a prompt for a new file name to write to will be shown.

We've covered most keyboard shortcuts, but there are some other features you might want to make use of, the following table shows the keyboard shortcuts we haven't covered yet.

| Keybinding  | What it does  |
| ------------ | ------------ |
| `Ctrl + F`  | Searches the document for a search query. Allows pressing of <kbd>←</kbd> to move the cursor to the previous occurance fof the query and <kbd>→</kbd> to move to the next occurance of the query. Press <kbd>Return</kbd> or <kbd>Esc</kbd> to leave the search. Note: you can use regular expressions for search queries. | 
| `Ctrl + Z`  | Undoes your last action. The changes are committed to the undo stack every time you press the space bar, create / destroy a new line and when there is no activity after a certain period of time which can be used to capture points where you pause for thought or grab a coffee etc... | 
| `Ctrl + Y`  | Redoes your last action. The changes are committed to the undo stack every time you press the space bar, create / destroy a new line and when there is no activity after a certain period of time which can be used to capture points where you pause for thought or grab a coffee etc... | 
| `Ctrl + R`  | Allows replacing of occurances in the document. Uses the same keybindings as the search feature: <kbd>←</kbd> to move the cursor to the previous occurance of the query and <kbd>→</kbd> to move to the next occurance of the query. You can also press <kbd>Return</kbd> to carry out the replace action. To exit replace mode once you're finished, you can press <kbd>Esc</kbd>. You can also use <kbd>Tab</kbd> to replace every instance in the document at once. Note: you can use regular expressions for search queries. | 
| `Ctrl + K`  | Opens the command line.  | 

### Configuration

Ox features a configuration system that allows modification and personalization of the editor.

By default, Ox will look for a file here: `$XDG_CONFIG_HOME/.oxrc` or `~/.oxrc`.

Ox's configuration language is [Lua](https://lua.org).

There is a default config in the `config` folder in the repository for you to refer to. You can either download it and place it in the default config directory or create your own using the example ones as a reference.

If you don't have a config file, or don't want to mess around with it, don't worry, Ox has default settings it will use.

## Documentation

If you've been through the quick start guide above, but are looking for more detail, you can find in-depth documentation in the [wiki page](https://github.com/curlpipe/ox/wiki/)

This will take you step-by-step in great detail through 5 different stages:

1. **Installation** - advice and how-tos on installation
2. **Starting** - using the command line interface
3. **Using** - editing a document and controlling the editor
4. **Configuring** - writing plug-ins, changing layout, adding to and changing the syntax highlighting
5. **Next Steps** - planned features and contributing

Hopefully it contains everything you need to take you from beginner to a power user.

## License

Distributed under the GNU GPLv2 License. See `LICENSE` for more information.

## Contact

You can contact me on Discord at my handle `curlpipe`. I'll be happy to answer any questions you may have!

## Acknowledgements

- [Luke (curlpipe)](https://github.com/curlpipe), principal developer
- [Spike (spikecodes)](https://github.com/spikecodes), for the logo
- The community, for the stars, ideas, suggestions and bug reports

The creators of the following technologies:

* [Rust language](https://rust-lang.org)
* [Kaolinite](https://github.com/curlpipe/kaolinite)
* [Synoptic](https://github.com/curlpipe/synoptic)
* [Crossterm](https://github.com/crossterm-rs/crossterm)
* [Mlua](https://github.com/mlua-rs/mlua)
* [Jargon-args](https://crates.io/crates/jargon-args)
* [Regex](https://docs.rs/regex/1.3.9/regex/)
* [Unicode-rs](https://unicode-rs.github.io/)
* [Quick-error](https://github.com/tailhook/quick-error)
* [Shellexpand](https://github.com/netvl/shellexpand)

