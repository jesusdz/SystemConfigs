# Fonts in Linux

## Font rendering protocol

First decide which protocol for font rendering you want to use

1. Core protocol: Better for fixed fonts.
2. Xft protocol: Better for TrueType fonts, for instance, where we will want antialiasing.

## Find out font names

For core protocol rendering, you can use the `xfontsel` tool to find out the name of a font.

To show all available font names (TrueType fonts and others included) we can use the command `fc-list`. E.g. `fc-list|grep courbd.ttf` shows you the font name is Courier New and style is Bold (append `:style=Bold` to select it).

Use `fc-match "Courier New"` to check which font is the best match for a given name from Xft's point of view.

Other applications may have their own conventions for X11 and Xft font names. E.g. the same `xft:` prefix is used by emacs; xterm uses `faceName` and `renderFont` resources to determine whether to use Xft and which font to request; `xedit` supports core protocol only. The mere fact that the application is configurable from X resources isn't enough to tell how the font names are interpreted.

## Powerline fonts

For have some font symbols in some applications such as *vim airline*, powerline fonts are required. We can install these fonts by first cloning the following repository:

```
git clone https://github.com/powerline/fonts.git
```

And then executing the installation script inside the `fonts` directory, `install.sh`, which copies the font files into a local directory and then updates the font cache:

```
cd fonts
./install.sh
```

## .XResources

Add the following line to specify that the `urxvt` terminal will use the default `fixed` font as the main font, and the *Terminess* font as a fallback whenever a symbol is not present in the `fixed` font.

```
urxvt*font: fixed,xft:xos4 Terminess Powerline
```

## Check if urxvt terminal supports Xft

```
urxvt --help 2>&1 | grep options
```

## Some good proportional (non-fixed) bitmap fonts

If we invoke the command *xfontsel* you can find some good bitmap proportional fonts such as:
```
-*-helvetica-medium-r-*-*-8-*-*-*-*-*-*-*                                                                 
-*-helvetica-bold-r-*-*-8-*-*-*-*-*-*-*                                                                                                                                                                             
-*-helvetica-medium-r-*-*-10-*-*-*-*-*-*-*                                                                
-*-helvetica-bold-r-*-*-10-*-*-*-*-*-*-*                                                                  
-*-helvetica-medium-r-*-*-12-*-*-*-*-*-*-*                                                                
-*-helvetica-bold-r-*-*-12-*-*-*-*-*-*-*                                                                  
-*-helvetica-medium-r-*-*-14-*-*-*-*-*-*-*                                                                
-*-helvetica-bold-r-*-*-14-*-*-*-*-*-*-*  
```

Specifically, these fonts are placed under the directory */usr/shared/fonts/75dpi*. They have the prefix *helv* and the extension *.pcf.gz*.

To convert them to TrueType fonts we can use an online font conversor.
