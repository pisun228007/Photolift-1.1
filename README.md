PhotoLift

A simple desktop app for clean, high-quality photo upscaling. PhotoLift runs Real-ESRGAN (via the ready-made realesrgan-ncnn-vulkan build) on your GPU and gives you a 2× or 4× bigger image with no extra filters, sharpening or smoothing on top.

Features
Pure upscaling. Only the neural network result, no post-processing.
2× and 4× scale. 4× is the native network output; 2× is the 4× result downscaled with Lanczos to keep the detail sharp.
Before / After / Compare views with a draggable split slider.
Smooth viewer. Mouse-wheel zoom, drag to pan, "Fit" and 1:1 buttons.
Many ways to open a photo. Drag & drop, Ctrl+V (image or file from the clipboard), Ctrl+O, or the load button.
Save as PNG, JPG, WEBP, TIFF or BMP (Ctrl+S).
Built-in examples. Before/after samples in the side panel; click one to open it larger.
Dark, modern interface built with CustomTkinter.
Requirements
Windows (the project is developed and tested on Windows)
Python 3.9+
A GPU with Vulkan support
The realesrgan-ncnn-vulkan release with its models folder
Run from source
bash
pip install customtkinter pillow tkinterdnd2
python photolift.py

tkinterdnd2 is optional: without it drag & drop is disabled, but everything else works.

Put the engine folder next to the script:

photolift.py
examples_data.py
realesrgan/
    realesrgan-ncnn-vulkan.exe
    models/
examples/            (optional, see below)

If the engine is not found, the app asks you to point to realesrgan-ncnn-vulkan once and remembers the path.

Usage
Open a photo (drag it into the window, paste it, or use the load button).
Pick 2× or 4× and the output format.
Press Enhance image and wait. Large photos can take a couple of minutes.
Drag the slider to compare, then press Download.
Custom examples

Drop these files into an examples folder next to the app and they replace the built-in previews. They are shown 1:1 when you click an example:

examples/2x_wide.png    examples/2x_close.png
examples/4x_wide.png    examples/4x_close.png

PNG, JPG and WEBP are supported. Without the folder the app uses the embedded copies from examples_data.py.

Build a standalone app

Run build_photolift.bat (or the commands below). It builds the exe with PyInstaller, copies realesrgan and examples next to it and packs everything into PhotoLift.zip.

bash
pip install pyinstaller
pyinstaller --noconsole --onedir --name PhotoLift --collect-all customtkinter --collect-all tkinterdnd2 photolift.py

Then copy the realesrgan and examples folders into dist/PhotoLift/.

Troubleshooting
Drag & drop does nothing: don't run the app as administrator while Explorer runs as a normal user, Windows blocks drops in that case. Dragging straight from a browser or messenger often doesn't carry a real file, so save the image to disk first.
Engine error: make sure your GPU supports Vulkan and that the models folder sits next to realesrgan-ncnn-vulkan.exe.
Credits
