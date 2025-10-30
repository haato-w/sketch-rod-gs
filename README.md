# SketchRodGS: Sketch-based Extraction of Slender Geometries for Animating Gaussian Splatting Scenes

<!-- Authors -->
Haato Watanabe, Nobuyuki Umetani

<!-- Links -->
| [Project page](https://haato-w.github.io/sketch-rod-gs-project-page/) | [Paper](https://drive.google.com/file/d/1wGobqDku-FI_5NBXXg0IhNwWbq-0uBcf/view?usp=sharing) | [Video](https://youtu.be/eaK0p0nU47g?si=sTGmfLNSeCYiJELJ) | [Dataset (Google Drive)](https://drive.google.com/drive/folders/1QhOkshES3-ubzQtoMD1wOpd_6Vj45H0f?usp=sharing) |<br>

<!-- Teaser Image -->
![Teaser image](resources/teaser.jpg)

This repository contains the official authors implementation associated with the paper "SketchRodGS: Sketch-based Extraction of Slender Geometries for Animating Gaussian Splatting Scenes", which can be found [here](https://haato-w.github.io/sketch-rod-gs-project-page/). We further provide the real scene datasets that has skinny object as well as pre-trained models.

## Abstract
Physics simulation of slender elastic objects often requires discretization as a polyline. However, constructing a polyline from Gaussian splatting is challenging as Gaussian splatting lacks connectivity information and the configuration of Gaussian primitives contains much noise. This paper presents a method to extract a polyline representation of the slender part of the objects in a Gaussian splatting scene from the user’s sketching input. Our method robustly constructs a polyline mesh that represents the slender parts using the screen-space shortest path analysis that can be efficiently solved using dynamic programming. We demonstrate the effectiveness of our approach in several in-the-wild examples.

## BibTeX
```bibtex
@inproceedings{watanabe2025SketchRodGS,
author    = {Haato Watanabe and Nobuyuki Umetani},
title     = {SketchRodGS: Sketch-based Extraction of Slender Geometries for Animating Gaussian Splatting Scenes},
booktitle = {SIGGRAPH Asia 2025 Technical Communications (SA Technical Communications '25)},
year      = {2025},
month     = dec,
address   = {Hong Kong, Hong Kong},
publisher = {ACM},
isbn      = {979-8-4007-2136-6/2025/12},
doi       = {10.1145/3757376.3771403},
url       = {https://doi.org/10.1145/3757376.3771403}
}
```

## Installation
This repository is based on the original 3D Gaussian Splatting by INRIA.
Since our implementation extends it with PySide6 viewer, pybind11 C++/CUDA modules, and other utilities,
please also refer to the original 3DGS setup guide if you encounter environment-related issues.

Clone this repository with submodules:
```
# SSH
git clone git@github.com:haato-w/sketch-rod-gs.git --recursive
```
```
# HTTPS
git clone 
https://github.com/haato-w/sketch-rod-gs.git --recursive
```

### Software Requirements
- Conda (recommended for easy setup)
- C++ Compiler for PyTorch extensions (we used Visual Studio 2019 for Windows)
- CUDA SDK 11 for PyTorch extensions, install after Visual Studio (we used 11.8, known issues with 11.6)
- C++ Compiler and CUDA SDK must be compatible

## Setup
```
conda env create --file environment.yml
conda activate sketch-rod-gs
```

### Data Setup
Please set .ply 3DGS scene data into `gs_data` directory. While you can use arbitrary data, we release [our real scene datasets](https://drive.google.com/drive/folders/1QhOkshES3-ubzQtoMD1wOpd_6Vj45H0f?usp=sharing) that has skinny object.

Place your .ply 3DGS scene data under the gs_data directory.
You can use any 3DGS data, but we also provide [our real-scene datasets](https://drive.google.com/drive/folders/1QhOkshES3-ubzQtoMD1wOpd_6Vj45H0f?usp=sharing)

### Running the Viewer
```
python viewer.py gs_data/"file name".ply
```

### Usage

**Please click and watch the demo video.**<br>
[![Demo Video](resources/youtube_thumbnail_with_icon.jpg)](https://youtu.be/eaK0p0nU47g?si=54fC0_AL-OYZkHY3)

There are three modes available:

- **VIEWER:** Observe the scene from any viewpoint.  
- **GUIDE_EDITOR:** This mode is used for drawing a sketch guide.  
- **PLAY:** Interact with the generated polyline — pull and release to simulate motion.

Below is a brief overview of controls:

| Key / Mouse                 | Action                                    |
| --------------------------- | ----------------------------------------- |
| Mouse Drag                  | Orbit camera                              |
| Wheel                       | Zoom in/out                               |
| Arrow Key                   | Rotate camera                             |
| `W`,`A`,`S`,`D` Key         | Move camera (parallel)                    |
| `W`,`A`,`S`,`D` Key + Shift | Rotate camera                             |
| `M` Key                     | Switch mode (Viewer / Sketch / Animation) |
| `I` Key                     | Toggle information panel                  |

## TODO
- [ ] Improve stability of animation
- [ ] Improve rendering speed
- [ ] Enable multi-polyline simulation
- [ ] Fix animation artifacts 

## Contact
If you have any questions or find issues, feel free to:
- Open an Issue on GitHub, or
-  Contact me via email: heart.watanabe.research[at]gmail.com
