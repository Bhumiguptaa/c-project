# C++ Compression Project

This is a standalone C++ project capable of both **File Compression** (via LZW algorithm) and **Image Compression** (resaving images as lossy JPEG).

The project is structured efficiently with headers and source files, and does not require complex installations or external compilation tools since it relies on simple header-only libraries or natively written algorithms.

## Features
- **Generic File Compression:** Compresses and decompresses text or binary files using a natively implemented Lempel-Ziv-Welch (LZW) algorithm.
- **Image Compression:** Uses the popular `stb_image` and `stb_image_write` single-header public domain libraries to compress images (PNG, JPG, BMP) by re-encoding them into standard fast JPEG representation with adjustable quality.

## Project Structure
```text
.
├── external/                # External header-only libraries
│   ├── stb_image.h
│   └── stb_image_write.h
├── src/
│   ├── main.cpp             # CLI Entry Point
│   ├── FileCompressor.h     # File compression API (LZW)
│   ├── FileCompressor.cpp   # File compression implementation
│   ├── ImageCompressor.h    # Image compression API
│   └── ImageCompressor.cpp  # Image compression implementation (stb bindings)
├── CMakeLists.txt           # Build instructions for CMake
└── README.md                # You are here!
```

## How to Build

We provide two easy ways to compile the code depending on what tools you have available. Both build methods produce a Command-Line version (`compressor.exe`) and a Native Windows GUI version (`CompressionUI.exe`).

### Method 1: Direct Compilation via g++ (MinGW)
If you already have `g++` on your compiler path, simply run this in the terminal:
```powershell
# Compile the Command-Line tool
g++ -std=c++11 src/main.cpp src/FileCompressor.cpp src/ImageCompressor.cpp -o compressor.exe

# Compile the Native Windows GUI tool (no console window)
g++ -std=c++11 -mwindows src/gui_main.cpp src/FileCompressor.cpp src/ImageCompressor.cpp -o CompressionUI.exe -lcomdlg32 -static
```

### Method 2: Using CMake
If you prefer standard CMake build pipelines:
```powershell
mkdir build
cd build
cmake ..
cmake --build .
```

## How to Use

You now have THREE ways to use this tool!

### 1. The Web UI Front (NEW!)
We built a gorgeous, modern webpage interface featuring glassmorphism layout, powered by an Express backend proxy.
```powershell
cd web
npm install
node server.js
```
Then simply open your browser and navigate to **http://localhost:3000**. Upload files securely and smoothly through the web!

### 2. The Graphical User Interface (GUI) Desktop App
Simply double click `CompressionUI.exe` from your File Explorer! 
It features a native Windows desktop user interface where you can easily browse files visually and push buttons to compress text/binary files or transcode images without needing the command prompt!

### 3. The Command Line Interface (CLI)
After compiling you will get `compressor.exe`. The tool uses a simple command-line interface.

#### Running a File Compression (Text/Binary)
```powershell
# Compress a file
.\compressor.exe file compress input.txt output.bin

# Decompress a file back
.\compressor.exe file decompress output.bin decompressed.txt
```

#### Running an Image Compression
Resize or optimize the quality of an image significantly by rewriting it into JPEG output with a designated quality (0-100).
```powershell
# Compress an image into a JPEG (default quality is 50)
.\compressor.exe image input_image.png output_image.jpg

# Optionally, compress with a specific quality scale
.\compressor.exe image input_image.png output_image.jpg 30
```
