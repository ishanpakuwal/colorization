# Augmenting Colorization With Seam Carving

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

<img src="https://github.com/ishanpakuwal/colorization/blob/main/updated_enhanced_colorizer.gif" width="900">

### Instructions:
1. Open seam_carving.ipynb found in the root of this repo
2. Run the cells in order making to correct install and import necessary libraries
3. Make sure to run all the implemented functions by running all the cells sequentially
4. The last cell contains commented out tests on the seam carving functions
5. Enjoy!




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
- In the file colorization_and_seamcarving.ipynb, we append the 2 modules: the instance-aware colorizer and the seam carving applications.
- To get started, open the notebook (found in the root of this repo), and run the cells sequentially
- As you get used to it, notice how the images we display are loaded and feel free to experiment with your own
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
