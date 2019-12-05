# MammogramGist-CNN

## Installation
All code is in Python 3.6.6 64-bit.
First clone the directory. From a terminal inside the directory, run:

```python -m pip install --upgrade pip```


### Using GPU

Note that this uses tensorflow-gpu, which requires cuDNN, NVidia drivers, and CUDA toolkit. These are available at https://www.tensorflow.org/install/gpu along with the instructions to download/install. PyTorch is also utilizing the GPU, and instructions for specific installations are at https://pytorch.org/get-started/locally/. We use CUDA v10.1 with tensorflow-gpu and gpu accelerated torch.

```python -m pip install -r requirementsGPU.txt --user```

```python -m pip install torch==1.3.1 torchvision==0.4.2 -f https://download.pytorch.org/whl/torch_stable.html --user```

### Not using GPU


```python -m pip install -r requirements.txt --user```

```python -m pip install torch==1.3.1+cpu torchvision==0.4.2+cpu -f https://download.pytorch.org/whl/torch_stable.html --user```

## Running the code
From within the /Code directory, run

```python End_to_end_model.py```


This will run the current settings within the code, and print desired results.

## Settings
Within End_to_end_model.py are a number of options to choose from. 

Critically, ```use_GPU``` should match what you followed during installation. Set to ```True``` or ```False``` if you plan to use the GPU (CUDA) or not. Note that if you installed CUDA, you may also opt to set this to False without any issue, though it takes ~66% longer on our test machine(33 seconds vs 56 seconds):

CPU: i5-6600k
GPU: NVIDIA 2080Ti
Memory: 32GB 2333Hz

The following four choices are the core variables to change in the experiment.
model_name: 
Either ```"inceptionv4"``` or ```"vgg19"```. Chooses which deep network to generate features from.

classifier_name:
Either ```"LGBM"``` or ```"SVM"```. Chooses which classification method to use.

preprocessingType:
Either ```1```, ```2```, ```3```, or ```4```. 
Preprocessing 1: No changes to original images.
Preprocessing 2: Mirror left breast images vertically.
Preprocessing 3: Crop muscle fibers from the images.
Preprocessing 4: Crop muscle fibers from the images and mirror left breast images vertically.

use_radiologist_gist:
Whether or not to include the radiologist gist response in the input vector for the classifier. Either ```True``` or ```False```.

The following variables were helpful with testing and reporting data. Default is False.

use_rotations:
Augments the data with rotations of the original images. Either ```True``` or ```False```.

use_PCA:
Uses PCA to downscale the original feature vector to a smaller space. Either ```True``` or ```False```.

show_charts:
Prints charts of AUC curves and a histogram of the bootstrapping using matplotlib. Either ```True``` or ```False```.

print_statements_debug:
Prints additional debugging information. Either ```True``` or ```False```.

save_AUC_chart:
Automatically saves AUC charts from the run with the name "ROC Curve - " + model_name + " features into " + classifier_name + " with radiologist gist".png in the current directory. If radiologist gist isn't used, remove " with radiologist gist" from the title. Either ```True``` or ```False```.

print_TPRandFPR:
Reports True Positive Rate and False Positive Rate to console. Either ```True``` or ```False```.

save_results_and_do_post_hoc_tests:
Saves the bootstrapping results to a text file in a /Results folder and prints the results of a Levene test for equal variances and a one-way F test(ANOVA) to the console. Either ```True``` or ```False```.

do_TSNE:
Creates a t-SNE chart from the feature vector using matplotlib. Either ```True``` or ```False```.
