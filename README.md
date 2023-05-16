# MultiClass_SemanticSegmentation_AbdominalCT

Computed Tomography(CT) scans are an excellent way of capturing the details of the abdominal muscles. Several abnormalities including hernia, tumour, and neuro-muscular diseases can be identified and estimated by CT scans, including the representation of muscle loss. Radiologists carefully segment and review every CT slice to monitor these abnormalities. This is a meticulous, painstaking, and time consuming process. This is especially true for the abdomen, which has a lot of variations and complexities in the wall and surrounding tissues.

To solve this, we annotated 451 image-mask pairs from DICOM files of the abdominal muscles of size 512 x 512 pixels. In this work, the trade-off between computation cost and image loss is estimated by splitting the imageries into two categories of size: 128 x 128 pixels and 512 x 512 pixels. To sustain the original image size, the authors create a resized version of the base U-Net and train it from scratch. Furthermore, two dataset categories are created to show the data-intensive quality of the models(One double in size compared to the other). To train the system using these datasets, two architectures U-Net and resized U-Net are used which are then compared through the introduction of a new loss function - “complete loss”. The resized U-Net performs better than the standard U-Net by displaying a mean complete loss of 3.52% and 10.79% for the validation and test sets respectively. The data dependency of models is clearly shown as well.

If you use this code 
Citation :

