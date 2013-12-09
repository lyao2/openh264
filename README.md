OpenH264
=======
OpenH264 is a codec library which supports H.264 encoding and decoding. It is suitable for use in real time applications such as WebRTC. See http://www.openh264.org/ for more details.
 
Encoder Features
------------------------
- Constrained Baseline Profile up to Level 5.2 (4096x2304)
- Arbitrary resolution, not constrained to multiples of 16x16
- Rate control with adaptive quantization, or constant quantization
- Slice options: 1 slice per frame, N slices per frame, N macroblocks per slice, or N bytes per slice
- Multiple threads automatically used for multiple slices
- Temporal scalability up to 4 layers in a dyadic hierarchy
- Spatial simulcast up to 4 resolutions from a single input
- Long Term Reference (LTR) frames
- Memory Management Control Operation (MMCO)
- Reference picture list modification
- Single reference frame for inter prediction
- Multiple reference frames when using LTR and/or 3-4 temporal layers
- Periodic and on-demand Instantaneous Decoder Refresh (IDR) frame insertion
- Dynamic changes to bit rate, frame rate, and resolution 
- Annex B byte stream output
- YUV 4:2:0 planar input
 
Decoder Features
------------------------
- Constrained Baseline Profile up to Level 5.2 (4096x2304)
- Arbitrary resolution, not constrained to multiples of 16x16
- Single thread for all slices
- Long Term Reference (LTR) frames
- Memory Management Control Operation (MMCO)
- Reference picture list modification
- Multiple reference frames when specified in Sequence Parameter Set (SPS)
- Annex B byte stream input
- YUV 4:2:0 planar output
 
OS Support
----------------
- Windows 64-bit and 32-bit (initial release is only 32-bit, 64-bit will follow soon)
- Mac OS X 64-bit (initial release does not include this target, will follow soon)
- Linux 64-bit and 32-bit (initial release is only 32-bit, 64-bit will follow soon)
- Android 32-bit (initial release does not include this target, will follow soon)
- iOS 64-bit and 32-bit (not supported yet, may be added in the future)
 
Processor Support
-------------------------
- Intel x86 optionally with MMX/SSE (no AVX yet, help is welcome)
- ARMv7 optionally with NEON (initial release does not include this target, will follow later)
- Any architecture using C/C++ fallback functions

Build Prerequisites
-----------------------
- Python 2.6 or newer (www.python.org)
- gyp (https://code.google.com/p/gyp)
- nasm 2.07 or newer (www.nasm.us)


Build Instructions
-----------------------
- First run setup.sh to build the makefiles

>./setup.sh

- Then build:

>make -C build    (to build debug)
>make -C build BUILDTYPE=Release  (to build opt)

The binaries will end up in build/out/Default.
 
API details to be provided later.
 
Using the Test App
-------------------------
ENCODER (encode264)

To run:
encode264 <input> <output> -sw <width> -sh <height>
NOTE: The encoder always pads out to 1280x720. We are working
on fixing this.

DECODER (decode264):
To run:
decode264 <input> <output>
 
Usage information can be found in testbin/CmdLineReadMe
Command line options and details to be provided later.
 
Using the Source
-----------------------
codec - encoder, decoder, console (test app), build (makefile, vcproj)
processing - raw pixel processing (used by encoder)
testbin - autobuild scripts, test app config files, yuv test files
bin - binaries for library and test app
 
Known Issues
-------------------
See the issue tracker on https://github.com/cisco/openh264/issues
- Encoder errors when resolution exceeds 3840x2160
- Encoder errors when compressed frame size exceeds half uncompressed size
- Encoder console app only support multiple of 16 width/height for now
- Decoder errors when compressed frame size exceeds 1MB
 
License
----------
BSD, see LICENSE file for details.
