# Size matters: Exploring the impact of model architecture and dataset size on semantic segmentation of abdominal wall muscles in CT scans

Computed Tomography(CT) scans are an excellent way of capturing the details of the abdominal muscles. Several abnormalities including hernia, tumour, and neuro-muscular diseases can be identified and estimated by CT scans, including the representation of muscle loss. Radiologists carefully segment and review every CT slice to monitor these abnormalities. This is a meticulous, painstaking, and time consuming process. This is especially true for the abdomen, which has a lot of variations and complexities in the wall and surrounding tissues.

To solve this, we annotated 451 image-mask pairs from DICOM files of the abdominal muscles of size 512 x 512 pixels. In this work, the trade-off between computation cost and image loss is estimated by splitting the imageries into two categories of size: 128 x 128 pixels and 512 x 512 pixels. To sustain the original image size, the authors create a resized version of the base U-Net and train it from scratch. Furthermore, two dataset categories are created to show the data-intensive quality of the models(One double in size compared to the other). To train the system using these datasets, two architectures U-Net and resized U-Net are used which are then compared through the introduction of a new loss function - “complete loss”. The resized U-Net performs better than the standard U-Net by displaying a mean complete loss of 3.52% and 10.79% for the validation and test sets respectively. The data dependency of models is clearly shown as well.


Example of CT slice and preprocessing done :
<img width="475" alt="Screenshot 2023-05-16 at 4 23 49 PM" src="https://github.com/AnveshSK/Size-matters-Exploring-the-impact-of-model-architecture-and-dataset-size-/assets/54216044/28b05536-1872-43ae-aaf4-c46bc0199c8c">

Architecture of Resized U-Net :

In this study, comparisons were made between two U-Net architectures, Standard U-Net(base U-Net and Resized U-Net, using two different datasets which differ in sizes and image dimensions(128 x 128 pixels and 512 x 512 pixels). The standard U-Net model’s main objective was to utilise the encoder and decoder architecture to create a complete and accurate mask for the given abdominal CT. It took an image of 128 x 128 pixels and consisted of a 5-layered architecture coupled with dice loss. (architecture similar to Base U-Net) Both datasets, global and local were tested on this model. It was time efficient and saved computational costs i.e the model only had around 2 million parameters. Though this model gave a reasonable accuracy, the reconstruction loss (resizing it back to 512 x 512 pixels) significantly increased the complete loss which made the image blurry and inaccurate. To overcome this, the authors built on this architecture through the addition of two intermediate layers each to the encoder and decoder, which resulted in an overall of 6 layers each(Refer Fig. 3). This was done to maintain the spatial resolution of the image, avoid image resizing, and reduced the reconstruction loss to 0. Each layer of the custom U-Net model also consists of two convolution layers, one max pool layer, and a dropout layer. To standardise values and make the network faster, batch normalisation wasvdone for each convolution layer. Long skip connections from the encoder to the
decoder were maintained [12,13]. Note that this model was trained from scratch. This model achieved an improved complete loss and generalised better across all datasets. But this came at a serious increase in computation cost(around 34 million parameters). Hyperparameter tuning was done to improve performance
and make the models a better fit for the dataset. The best parameters for each model and dataset combination were considered and compared to analyse the effects of image and dataset size.











<img width="451" alt="Screenshot 2023-05-16 at 4 24 29 PM" src="https://github.com/AnveshSK/Size-matters-Exploring-the-impact-of-model-architecture-and-dataset-size-/assets/54216044/059fabb4-53d5-407a-8df4-1c694b7824f2">














RESULTS:














<img width="480" alt="Screenshot 2023-05-16 at 4 26 30 PM" src="https://github.com/AnveshSK/Size-matters-Exploring-the-impact-of-model-architecture-and-dataset-size-/assets/54216044/07c6f4f6-5c7b-4408-b06b-49f04c5aa797">

<img width="490" alt="Screenshot 2023-05-16 at 4 26 46 PM" src="https://github.com/AnveshSK/Size-matters-Exploring-the-impact-of-model-architecture-and-dataset-size-/assets/54216044/dfd066ab-a871-46d8-8eeb-679a456ce94f">




If you use this code 
Citation :


