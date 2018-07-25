### Fonts in Linux

## Font rendering protocol

First decide which protocol for font rendering you want to use

1. Core protocol: Better for fixed fonts.
2. Xft protocol: Better for TrueType fonts, for instance, where we will want antialiasing.

## Find out font names

For core protocol rendering, you can use the `xfontsel` tool to find out the name of a font.

To show all available font names (TrueType fonts and others included) we can use the command `fc-list`. E.g. `fc-list|grep courbd.ttf` shows you the font name is Courier New and style is Bold (append `:style=Bold` to select it).

Use `fc-match "Courier New"` to check which font is the best match for a given name from Xft's point of view.

Other applications may have their own conventions for X11 and Xft font names. E.g. the same `xft:` prefix is used by emacs; xterm uses `faceName` and `renderFont` resources to determine whether to use Xft and which font to request; `xedit` supports core protocol only. The mere fact that the application is configurable from X resources isn't enough to tell how the font names are interpreted.

## Check if urxvt terminal supports Xft

```
urxvt --help 2>&1 | grep options
```