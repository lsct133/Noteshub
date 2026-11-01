Lightning image viewer

  Lightning Image Viewer is fast and lightweight desktop image viewer featuring
minimalistic &quot;transparent fullscreen overlay&quot; UI/UX with controls
similar to map apps. It is free (as in FOSS
[https://en.wikipedia.org/wiki/Free_and_open-source_software], licensed under
GPLv3) native (as in native code) cross-platform app (written in C with SDL3
[https://libsdl.org/], tested on Linux and Windows). Detailed description and
source code are available on GitHub
[https://github.com/shatsky/lightning-image-viewer]. This webpage is primarily
demo featuring actual app which is compiled to WebAssembly
[https://webassembly.org/] and runs in browser via Emscripten
[https://emscripten.org/]. It is launched after image file is selected and
renders to canvas, displaying image over webpage content just like native build
displays over desktop and handling input events same as native. It should work
in all mainstream browsers.


Controls:

 * mouse scroll up/down: zoom in/out, preserving image point currently under
   mouse cursor
 * keyboard =/-/0: zoom in/out/1:1, preserving image point currently in the
   centre of the screen
 * mouse move with left button pressed: pan
 * keyboard Up/Down/Left/Right: pan up/down/left/right
 * mouse middle button click || keyboard F, F11: toggle fullscreen
 * mouse left button click with no move nor zoom between button press and
   release || keyboard Esc, Q, Enter: close
 * keyboard R/L: rotate 90deg clockwise/counter clockwise
 * keyboard M: mirror horizontally
 * keyboard PgDn/PgUp: prev/next image app running in browser cannot access
   local filesystem, so this only resets view of opened image


Downloads: check GitHub releases
[https://github.com/shatsky/lightning-image-viewer/releases]


Known issues specific to this demo webpage:

 * image formats support is limited to formats internally supported by
   SDL3_image library (BMP, GIF, JPEG, LBM, PCX, PNG, PNM (PPM/PGM/PBM), QOI,
   TGA, XCF, XPM, and simple SVG format images) (because I didn&apos;t bother to
   build external dependencies needed for AVIF, JPEG-XL, TIFF, and WebP)