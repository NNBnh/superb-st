<h1 align="center"><i>SuperB ST</i></h1>
<p align="center">ST-base terminal with enough patches</p>
<p align="center"><img src="https://user-images.githubusercontent.com/43980777/121320376-4ef51180-c937-11eb-9cd8-f06dafab918e.png"></p>
<p align="center"><a href="https://github.com/NNBnh/superbst/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-mit--1.1-%233978A8.svg?labelColor=39314B&style=for-the-badge&logoColor=FFFFFF" alt="License: MIT"></a> <a href="https://st.suckless.org"><img src="https://img.shields.io/badge/st_version-0.8.4-%233978A8.svg?labelColor=39314B&style=for-the-badge&logoColor=FFFFFF" alt="ST version: 0.8.4"></a></p>

## 💡 About
**SuperB ST** is a *SuperB* [ST-base](https://st.suckless.org) terminal using [ST-flexipatch](https://github.com/bakkeby/st-flexipatch) to add enough patches so it can be compared with other modern terminal like [Alacritty](https://github.com/alacritty/alacritty) and [Kitty](https://sw.kovidgoyal.net/kitty):
- **Goal**:
  - Patch features that only the terminal can do
- **Non goal**:
  - Patch features that conflict with the terminal multiplexer or some windows manager's features
  - Patch features that can be integrate using other tools/programs

### ✨ Features
- Resize to any pixel size and centers the content
- Configurable background's opacity
- Wide-character support
- Fonts ligatures support
- [True colors](https://gist.github.com/XVilka/8346728) support
- [Color emoji](https://gitlab.freedesktop.org/xorg/lib/libxft/-/merge_requests/1) support
- Graphics rendering support ([SIXEL](https://en.wikipedia.org/wiki/Sixel) and [W3M](http://w3m.sourceforge.net))
- Even more escape sequences support
- XIM support
- Beginner friendly features:
  - Scrollback support and clipboard handling:
    > Although these basic and important features can be achieved using other programs, there aren't many programs that just only these features.<br>
    > Currently they are only be supported properly by some terminal multiplexer (like [Tmux](https://github.com/tmux/tmux/wiki) which come with many bloated features conflict with the windows manager).<br>
    > Looking forward to [scroll](https://tools.suckless.org/scroll).
  - [Xresources](https://wiki.archlinux.org/title/X_resources) support:
    > Although terminal configuration can be approached using escape sequences with tool like [`bui-terminal`](https://github.com/NNBnh/bui-terminal), some aspect of the terminal can't be change using escape sequences (e.g: font, background's opacity...).<br>
    > Font and bg's opacity can be config with startup flags using [`bt`](https://github.com/NNBnh/bt), still it isn't cover every options.

### 🩹 Patches
- Window:
  - [`anysize`](https://st.suckless.org/patches/anysize): allows the terminal to resize to any pixel size and centers the content of the terminal.
  - [`relativeborder`](https://st.suckless.org/patches/relativeborder): allows users to specify a border that is relative in size to the width of a cell in the terminal.
  - [`themed_cursor`](https://st.suckless.org/patches/themed_cursor): use the xterm cursor from your cursor theme.
  - [`alpha`](https://st.suckless.org/patches/alpha): allows users to only change the opacity of the background (unlike using the composite manager to change the opacity of the whole windows).
- Font:
  - [`wide_glyphs`](https://www.reddit.com/r/suckless/comments/jt90ai/update_support_for_proper_glyph_rendering_in_st): support proper glyph rendering.
  - [`ligatures`](https://st.suckless.org/patches/ligatures): support ligatures rendering.
  - [`boxdraw`](https://st.suckless.org/patches/boxdraw): custom rendering of lines and blocks (but not braille e.g: `⠞⠓⠊⠎`) characters for gapless alignment.
- Drawing:
  - [`bold-is-not-bright`](https://st.suckless.org/patches/bold-is-not-bright): makes bold text rendered simply as bold, leaving the color unaffected.
  - [`sync`](https://st.suckless.org/patches/sync): better draw timing to reduce flicker/tearing and improve animation smoothness.
  - [`sixel`](https://gist.github.com/saitoha/70e0fdf22e3e8f63ce937c7f7da71809): support [SIXEL](https://en.wikipedia.org/wiki/Sixel) graphics.
  - [`w3m`](https://st.suckless.org/patches/w3m): support [W3M](http://w3m.sourceforge.net) graphics.
- Escape sequences:
  - [`osc_10_11_12_2`](https://st.suckless.org/patches/osc_10_11_12_2): to modify the background, foreground and cursor colors.
  - [`blinking_cursor`](https://st.suckless.org/patches/blinking_cursor): to modify cursor style.
  - [`undercurl`](https://st.suckless.org/patches/undercurl): to render special underlines.
  - [`csi_22_23`](https://st.suckless.org/patches/csi_22_23): to save and restore window title.
- Beginner friendly:
  - [`scrollback`](https://st.suckless.org/patches/scrollback): scroll back through terminal output using mouse wheel.
  - [`clipboard`](https://st.suckless.org/patches/clipboard): support clipboard copy and paste.
  - [`xresources`](https://st.suckless.org/patches/xresources): adds the ability to configure ST via [Xresources](https://wiki.archlinux.org/title/X_resources)

> *The Xresources config will reload when a `SIGUSR1` signal is received:*
>
> `killall -USR1 st`

## 🚀 Setup
### 🧾 Dependencies
- [`fontconfig`](https://archlinux.org/packages/extra/x86_64/fontconfig) and [`libx11`](https://archlinux.org/packages/extra/x86_64/libx11) are make dependencies
- [`libxft-bgra`](https://aur.archlinux.org/packages/libxft-bgra) is make dependencies for color emoji support

> *Make dependencies only needed when compile.*

### 📥 Installation
#### 🔧 Manually
Option 1: download

<p align="center"><a href="https://github.com/NNBnh/superb-st/releases"><img src="https://img.shields.io/github/downloads/NNBnh/superb-st/total?color=3978A8&labelColor=39314B&style=for-the-badge" alt="Downloads"></a></p>

and move it to `~/.local/bin/`. Or using `curl`:

```sh
curl -L https://github.com/NNBnh/superb-st/releases/download/1.0.0/st > ~/.local/bin/st
```

make sure to make the file executable:

```sh
chmod +x ~/.local/bin/st
```

Option 2: compile
```sh
git clone https://github.com/NNBnh/superb-st
git clone https://github.com/bakkeby/st-flexipatch

cd superb-st
cp -f patches.h config.h config.mk ../st-flexipatch/

cd ../st-flexipatch/
sudo make install
```

#### 📦 Package manager
For [`nix`](https://nixos.org) user:
```sh
#TODO
```

For [`arch`](https://archlinux.org) user:
```sh
#TODO
```

> *If you can and want to port SuperB ST to other package managers, feel free to do so.*

## ⌨️ Keybinds
- Font size:
  - <kbd>Ctrl</kbd> + <kbd>MouseWheel up</kbd> : increase font size
  - <kbd>Ctrl</kbd> + <kbd>MouseWheel down</kbd> : decrease font size
  - <kbd>Ctrl</kbd> + <kbd>MouseWheel button</kbd> : reset font size
  - <kbd>Ctrl</kbd> + <kbd>=</kbd> : increase font size
  - <kbd>Ctrl</kbd> + <kbd>-</kbd> : decrease font size
  - <kbd>Ctrl</kbd> + <kbd>'</kbd> : reset font size
- Scrollback:
  - <kbd>MouseWheel up</kbd> : scroll up
  - <kbd>MouseWheel down</kbd> : scroll down
- Clipboard handling:
  - <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>c</kbd> : copy selected texts to clipboard
  - <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>v</kbd> : paste texts from clipboard to ther terminal

## ⚙️ Configuration
You can config SuperB ST with outside tools like [`bui-terminal`](https://github.com/NNBnh/bui-terminal) + [`bt`](https://github.com/NNBnh/bt) (recommended) or with [Xresources](https://wiki.archlinux.org/title/X_resources):
```Xresources
*.font:         <STRING>:pixelsize=<FLOAT>:antialias=<BOOLEAN>:autohint=<BOOLEAN>
*.color0:       #<HEX>
*.color1:       #<HEX>
*.color2:       #<HEX>
*.color3:       #<HEX>
*.color4:       #<HEX>
*.color5:       #<HEX>
*.color6:       #<HEX>
*.color7:       #<HEX>
*.color8:       #<HEX>
*.color9:       #<HEX>
*.color10:      #<HEX>
*.color11:      #<HEX>
*.color12:      #<HEX>
*.color13:      #<HEX>
*.color14:      #<HEX>
*.color15:      #<HEX>
*.background:   #<HEX>
*.foreground:   #<HEX>
*.cursorColor:  #<HEX>
*.alpha:        <FLOAT>
*.borderperc:   <INTEGER>
*.termname:     <STRING>
*.shell:        <STRING>
*.minlatency:   <INTEGER>
*.maxlatency:   <INTEGER>
*.blinktimeout: <INTEGER>
*.bellvolume:   <INTEGER>
*.tabspaces:    <INTEGER>
```

## 💌 Credits
Special thanks to:
- [**ST**](https://st.suckless.org) by [`suckless.org`](https://suckless.org)
- [ST-flexipatch](https://github.com/bakkeby/st-flexipatch) by [Stein Gunnar Bakkeby](https://github.com/bakkeby)

<br><br><br><br>

---

> <h1 align="center">Made with ❤️ by <a href="https://github.com/NNBnh"><i>NNB</i></a></h1>
>
> <p align="center"><a href="https://www.buymeacoffee.com/nnbnh"><img src="https://img.shields.io/badge/buy_me_a_coffee%20-%23F7CA88.svg?logo=buy-me-a-coffee&logoColor=333333&style=for-the-badge" alt="Buy Me a Coffee"></a></p>
