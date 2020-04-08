# CarKeypoints

This repository contains inference code for using a modified [stacked-hourglass](https://github.com/krrish94/stacked-hourglass) to detect semantic keypoints on cars. 

The network outputs a likelihood of keypoint presence over every pixel of an input image (the input image is a 64 x 64 car bounding box).

Here is a 3D wireframe with reference keypoints.
<p align="center">
	<img src="assets/carkeypoints.png" />
</p>

## Setup

This code assumes you have the following packages installed.
* [Torch7](https://github.com/torch/torch7)
* Torch packages: `nn`, `cunn`, `cudnn`, `image`, `nngraph`


## Downloading the pre-trained model

Download the pre-trained model [here](https://www.dropbox.com/s/qezt3e02j4uawov/model.t7?dl=0).


## Running the inference code

To perform inference on a set of images, first edit `valid.txt` and add paths to the images you need to run inference on. **These images must only contain cropped car bounding boxes** (i.e., from any image that contains a car, pick only one car bounding box and crop the region of the image contained within that bounding box). These are the only kind of images the model has been trained on.

Then, run the inference script.
```
inference.lua
```

This will write a `results.txt` file (you can edit the name and path of this output file in `inference.lua`).
### Running with arguments
You must have a `valid.txt` file and a `model.t7` following the instructions above. All arguments must be used.
If you do not you must create a absolute path dir `/abosolute/path/to/` with a `valid.txt` file and a `model.t7`.
The generated `results.txt` will also be located there
#### Torch 7
```bash
th inference.lua ./valid.txt ./model.t7 ./results.txt
```
#### Lua
```bash
lua inference.lua ./valid.txt ./model.t7 ./results.txt
```
