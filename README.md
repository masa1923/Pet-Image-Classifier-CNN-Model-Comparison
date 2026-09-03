# Pet-Image-Classifier-CNN-Model-Comparison
Python/PyTorch program that uses three pretrained CNN architectures (ResNet, AlexNet, VGG) to classify pet images and compares which one best identifies dogs and dog breeds.
Overview

A command-line program that classifies a folder of pet images using pretrained CNN models, then evaluates and compares the performance of three different architectures — ResNet, AlexNet, and VGG — to determine which best identifies whether an image contains a dog, and (if so) the correct breed. Built as part of Udacity's Intro to Python for AI Programmers coursework, on top of a provided project structure.

What I implemented

The project runs a pipeline of several stages; I wrote the core logic for:

classify_images.py — runs each image through the selected CNN model, formats the predicted label, and compares it against the true label (parsed from the filename) to record a match/no-match result.
adjust_results4_isadog.py — cross-references both the true label and the model's predicted label against a reference list of dog breed names, to determine whether each one is a dog — separately from whether the breed matched exactly.
calculates_results_stats.py — aggregates the per-image results into summary statistics: number of images, number of dog vs. non-dog images, number of label matches, and the percentage of dogs correctly identified as dogs, non-dogs correctly identified as non-dogs, and breeds correctly identified.
How it works end-to-end
check_images.py parses command-line arguments (image directory, model architecture, dog-names file) and drives the pipeline.
Pet image labels are extracted from filenames.
classifier.py (provided) runs each image through the chosen pretrained model (resnet18, alexnet, or vgg16 from torchvision.models) and returns its predicted ImageNet class.
Predicted labels are compared to true labels, then checked against a dog-names reference list.
Results are aggregated into summary statistics so that all three architectures can be compared side by side.
Tech

Python, PyTorch, torchvision (pretrained resnet18, alexnet, vgg16 models), PIL.

Usage
bash
python check_images.py --dir pet_images/ --arch vgg --dogfile dognames.txt

--arch can be resnet, alexnet, or vgg — run it once per architecture to compare results.

Context

Completed as part of Udacity's Intro to Python for AI Programmers coursework (part of the AI Programming with Python Nanodegree), building on a provided project skeleton.
