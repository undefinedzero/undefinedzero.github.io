---
title: "ROB 535 Self-driving Car Kaggle Competition"
excerpt: "TOP 1 out of 19 Teams in image classication task and TOP 3 out of 13 Teams in vehicle localization task<br/><img src='/images/rob535/kaggle-out.png' width='600'>"
collection: projects
---

- Author: LIN JIANING (Leader of Team 15 🚗)

- Date: 2019.10 - 2019.12

- Environment: Google colab

- Language: Python

## Abtract
A number of successful object detection systems based on convolutional neural networks (CNN) have been proposed in recent years. The autonomous vehicle is rely on the object detection system using the data from Lidar, Radar, and camera sensors. Mask R-CNN, which extends Faster R-CNN by adding a branch for predicting segmentation masks on each Region of Interest (ROI), is one of the best architecture that can achieve the state of the art performance for object detection. Mask R-CNN is a two-stage detector, images are processed by a feature extractor (e.g., ResNet, ResNeXt) at the first stage. claims that replacing ResNet-101-FPN feature extractor with ResNeXt-101-FPN in Mask R-CNN framework can significantly improve the detection accuracy. Based on this, we propose that deeper feature extractors, which can extract more representative features, could improve the performance of Mask R-CNN detection system. In this project, we start with a Mask R-CNN with ResNeXt-152 model trained on COCO dataset, and fine-tune the model with the given training dataset. Our final test result can achieve 84.102\% detection accuracy in Kaggle task 1.

## Kaggle Leaderboard
<img src='/images/rob535/kaggle.png' width='600'>

