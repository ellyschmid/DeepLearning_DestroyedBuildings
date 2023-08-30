# Final Project:
## Identifying Damaged Buildings in Ukraine through RCNN-based Detection
Authors: Elly Schmid, Agnes Zwick<br>
Lecturer: Jakob Schwalb-Willmann<br>
Course: Deep Learning and Earth Observation

## Description:

*This project aims to construct an RCNN model specifically designed to identify destroyed building within Ukraine. By harnessing the capabilities of the RCNN architecture, the intention is to achieve precise recognition of destroyed structures and subsequently generate bounding boxes to encapsulate these areas of interest.<br>
Input for this project comprises a RGB screenshot obtained from Google Earth along with corresponding ground truth data provided by UNOSAT.*

### Code 1: Generating Buffers Around Ground Truth Data

The ground truth dataset provides point information about damaged buildings. The first code creates buffers around these points in a square. (Mask for the training dataset)

### Code 2: Generating Clipped Images using Created Buffers

The code takes the screenshot of the specified area of interest and clips it using the previously generated buffers. These clipped images are then saved in both their original format and as RGB converted versions in JPEG files.
In summary, this code snippet utilizes geospatial data processing to extract smaller image segments focused on areas with destroyed buildings. These images are subsequently employed in training the model.

### Code 3: Interactive Annotation Tool for Detecting Destroyed Buildings in Images

This script serves as an interactive annotation tool designed specifically for identifying and annotating regions of interest containing destroyed buildings within images. It employs the matplotlib library to create an interactive environment that enables users to draw bounding boxes around the areas of images where destroyed buildings are present. These bounding boxes serve as annotations for machine learning tasks such as object detection. The script generates XML annotations for each bounding box, encapsulating essential information about the destroyed building's location and image attributes. This tool significantly streamlines the process of generating labeled data for training models to detect and analyze destroyed buildings within images.

### Code 4: XML to CSV Converter

Convert XML annotations to CSV format for improved data utilization


### Code 5: Building Damage Detection with Regional Based Convolutional Neural Networks (RCNNs)

This code demonstrates the process of building damage detection using Regional Based Convolutional Neural Networks (RCNNs). It involves preprocessing images and annotations, creating and training a CNN model (based on VGG16), performing data augmentation, and utilizing selective search to identify and visualize regions of interest (potential damaged areas) in test images. The code showcases model training, evaluation, and testing for identifying whether an image contains signs of building damage.

Sucessfull Detection       |  
:-------------------------:|
![grafik](https://github.com/ellyschmid/DeepLearning_DestroyedBuildings/assets/116875590/8cade0f6-1716-4b30-a9e4-542e14542c8b)|



## Result and Outlook

The performance of the model in the training runs always showed good accuracies around 0.9. However, the results in predicting the bounding boxes of destroyed buildings in the test images were different each time. Sometimes the predicted boxes detected the destroyed buildings, other times only parts of them, and sometimes the predicted box was outside the destroyed building. We assume that the main challenge for the model to distinguish between destroyed and intact buildings is mainly the similarity of the intensity of the pixels in all three dimensions of the RGB image, which makes it difficult for the selective search algorithm to suggest the correct regions. To improve the detection of destroyed buildings, it could be beneficial to use proxies that can better distinguish the building types, than RGB bands. Previous studies have shown good results using texture features such as Gray Level Co-occurance Matrix between pre- and postevent images. [1] Unfortunately, this is often only possible with commercial high resolution satellite data such as WorldView-2 or Quickbird.

Sucessfull Detection       |  Unsucessfull
:-------------------------:|:-------------------------:
![prediction_193](https://github.com/ellyschmid/DeepLearning_DestroyedBuildings/assets/116875590/e56a0063-fe1d-4a34-9bcc-c9c24ead6024) | ![grafik](https://github.com/ellyschmid/DeepLearning_DestroyedBuildings/assets/116875590/e32e9b5d-4d3d-4029-ae88-cd598ee77954)

### References

- code template for RCNN-Model based on https://github.com/Hulkido/RCNN
- [1] Ji, M.; Liu, L.; Du, R.; Buchroithner, M.F. A Comparative Study of Texture and Convolutional Neural Network Features for Detecting Collapsed Buildings After Earthquakes Using Pre- and Post-Event Satellite Imagery. Remote Sens. 2019, 11, 1202. https://doi.org/10.3390/rs11101202
