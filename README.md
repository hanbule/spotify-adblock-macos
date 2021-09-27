# spotify-adblock-macos
This was tested on an Apple Silicon device. May not work on x86.

## Re-signing Spotify
For this to work, you have to re-sign Spotify with your own code signing certificate:
```
$ codesign --deep --force --sign "Your Certificate" /Applications/Spotify.app
```

## Compiling and signing the shared library
Compile the library with `make` and sign it:
```
$ make
$ codesign --sign "Your Certificate" "Chromium Embedded Framework"
```

## Rename the original one
Rename the old library to `Chromium Embedded Framework.orig`:
```
$ cd "/Applications/Spotify.app/Contents/Frameworks/Chromium Embedded Framework.framework"
$ mv "Chromium Embedded Framework" "Chromium Embedded Framework.orig"
```

## Place the new one with Finder (!)
Use Finder to drag the compiled library to where the old one is located.
