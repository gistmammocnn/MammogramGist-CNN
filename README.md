# MammogramGist-CNN

## Installation
All code is in Python 3.6.6.
First clone the directory. From a terminal inside the directory, run:
'''pip install requirements.txt'''

## Running the code
From within the /Code directory, run
'''python End_to_end_model.py'''
This will run the current settings within the code, and print desired results.

## Settings
Within End_to_end_model.py are a number of options to choose from. The following four choices are the core variables to change in the experiment.
model_name: 
Either "inceptionv4" or "vgg19". Chooses which deep network to generate features from.

classifier_name:
Either "LGBM" or "SVM". Chooses which classification method to use.

preprocessingType:
Either 1, 2, 3, or 4. 
Preprocessing 1: No changes to original images.
Preprocessing 2: Mirror left breast images vertically.
Preprocessing 3: Crop muscle fibers from the images.
Preprocessing 4: Crop muscle fibers from the images and mirror left breast images vertically.

use_radiologist_gist:
Whether or not to include the radiologist gist response in the input vector for the classifier. Either True or False.

The following variables were helpful with testing and reporting data. Default is False.

use_rotations:
Augments the data with rotations of the original images. Options are True or False.

use_PCA:
Uses PCA to downscale the original feature vector to a smaller space. Options are True or False.

show_charts:
Prints charts of AUC curves and a histogram of the bootstrapping using matplotlib. Options are True or False.

print_statements_debug:
Prints additional debugging information. Options are True or False.

save_AUC_chart:
Automatically saves AUC charts from the run with the name "ROC Curve - " + model_name + " features into " + classifier_name + " with radiologist gist".png in the current directory. If radiologist gist isn't used, remove " with radiologist gist" from the title. Options are True or False.

print_TPRandFPR:
Reports True Positive Rate and False Positive Rate to console. Options are True or False.

save_results_and_do_post_hoc_tests:
Saves the bootstrapping results to a text file in a /Results folder and prints the results of a Levene test for equal variances and a one-way F test(ANOVA) to the console. Options are True or False.

do_TSNE:
Creates a t-SNE chart from the feature vector using matplotlib. Options are True or False.
