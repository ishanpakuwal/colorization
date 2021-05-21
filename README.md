# Augmenting Colorization With Seam Carving

<img src="https://github.com/ishanpakuwal/colorization/blob/main/updated_enhanced_colorizer.gif" width="900">

### GIF explanation:
We first start with a greyscale image which we colorize using Instance Colorization. Next, we take the colorized image and we use seam carving implementation to resize the image upto a particular size. For the demonstration purposes, we resized the image upto 60% of it's original size. Each of these white lines or curves represents a seam that gets removed at each step until we get to the targeted size selected by the user. In the end, we also perform object removal technique as seen in the above gif, person in the image at the start of the gif disappears towards the end.

## Getting Started
1. Clone this repo:
```sh
git clone https://github.com/ericsujw/InstColorization
cd InstColorization
```
2. Install [conda](https://www.anaconda.com/).
3. Install all the dependencies
```sh
conda env create --file env.yml
```
4. Switch to the conda environment
```sh
conda activate instacolorization
```
5. Install other dependencies
```sh
sh scripts/install.sh
```

## Seam Carving:
### Instructions:
1. Open seam_carving.ipynb found in the root of this repo
2. Run the cells sequentially making sure to correctly install and import necessary libraries
3. Make sure to run all the implemented functions by running all the cells sequentially
4. The last cell contains commented out tests on the seam carving functions
5. Enjoy!

### Key functions in seam_carving.ipynb:
- computeEnergy: For each pixel location, returns the sum of gradients in x and y direction for that location
- findSeam: Returns an array where each index represents the row in the image, and the index's value represents the column
where 
- drawSeam: Given an image and a seam array, returns the original image with the seam locations colored.
- removeColumn: Given an image and a seam, returns an image with one less column where the seam is removed
- reduceImageRows: Given an image, reduces the rows in the image through seams
- reduceImageRows: Given an image, reduces the columns in the image through seams
- enlarge2D: Given an image, desired scale along Y, and desired scale along X, returns a 2D scaled image fitting the specifications
- addSeam: Given an image and a seam array, adds new pixels along the columns specified in the seam
- seamCarve2D: Given an image, combines reduceImageColumns and reduceImageRows to reduce image in 2D

## Colorization:
The instructions below, starting from 'Prerequisites' to 'Training the Model' were adopted from the original project's repo
cited in the footer of this document.

## Prerequisites
* Python3
* Pytorch >= 1.5
* Detectron2
* OpenCV-Python
* Pillow/scikit-image
* Please refer to the [env.yml](env.yml) for detail dependencies.

## Pretrained Model
1. Download it from [google drive](https://drive.google.com/open?id=1Xb-DKAA9ibCVLqm8teKd1MWk6imjwTBh).
```sh
sh scripts/download_model.sh
```
2. Now the pretrained models would place in [checkpoints](checkpoints).

## Instance Prediction
Please follow the command below to predict all the bounding boxes fo the images in `example` folder.
```
python inference_bbox.py --test_img_dir example
```
All the prediction results would save in `example_bbox` folder.

## Colorize Images
Please follow the command below to colorize all the images in `example` foler.
```
python test_fusion.py --name test_fusion --sample_p 1.0 --model fusion --fineSize 256 --test_img_dir example --results_img_dir results
```
All the colorized results would save in `results` folder.

* Note: all the images would convert into L channel to colorize in [test_fusion.py's L51](test_fusion.py#L51)

## Training the Model
Please follow this [tutorial](README_TRAIN.md) to train the colorization model.



## Combined Colorization & Seam Carving
- In the file colorization_and_seamcarving.ipynb, we have the 2 modules: the instance-aware colorizer and the implementations of different applications of seam carving.
- To get started, open the notebook (found in the root of this repo), and run the cells sequentially
- As you get used to it, notice how the images we display are loaded and feel free to experiment with your own images as well
- Enjoy!

```

## Acknowledgments
Our code borrows heavily from the https://github.com/ericsujw/InstColorization repository.

**Instance-aware Image Colorization**
<br/>
[Jheng-Wei Su](https://github.com/ericsujw), 
[Hung-Kuo Chu](https://cgv.cs.nthu.edu.tw/hkchu/), and 
[Jia-Bin Huang](https://filebox.ece.vt.edu/~jbhuang/)
<br/>
In IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2020.

```
