# Lung-Nodule-Segmentation-using-Squeeze-and-Excitation-Dense-UNet
In this project I have used LUNA-16 which consists of 888 CT scan images and this dataset is a subset of LIDC/IDRI dataset. 

## For the Pre-processing we have followed following steps:
1. Applying CLAHE
2. Binary Thresholding
3. Erosion amd Dilation
4. Filling Holes
5. Extracting lungs and nodule masks

Picture below shows the images obtained after some preprocessing steps. (a) is the original CT scan image from the dataset (b) image is obtained after applying CLAHE (c) image is obtained after binary thresholding (d) image is obtained after filling holes using contours and (e) is the final segmented lung ROI.

![image](https://github.com/yashika03/Lung-Nodule-Segmentation-using-Squeeze-and-Excitation-Dense-UNet/assets/76561509/6cff0d5f-ef36-4d7f-af00-2f9c549fab7e)

## Model:
We trained our pre-processed images on a Squeeze-and-Excitation Dense-UNet (SE Dense-UNet) model in which an SE block was added in the decoder layer. Model consists of encoder and decoder layer. 
## Encoder and Decoder Block:
Encoder layer consists of five blocks: 2D Convolutional Layer with Gelu Activation Function, Concatenation Layer, Dense Layer, Dropout Layer with 0.4 dropuout rate and 2D Max Pooling Layer.


Decoder Layer consists of: 2D Transpose Layer, Concatenation Layer, SE Block, 2D Convolutional Layer with Gelu Activation Function, Concatenation Layer connected to the corresponding convolutional layer in encoder
, Dropout Layer with rate 0.4.

![image](https://github.com/yashika03/Lung-Nodule-Segmentation-using-Squeeze-and-Excitation-Dense-UNet/assets/76561509/a3ea9e47-6347-46be-abbe-8c807868ed02)

In above image left image shows the shape and location of the nodule inside the lung observed by the radiologists whereas right image shows our models predicted nodule shape and location.

