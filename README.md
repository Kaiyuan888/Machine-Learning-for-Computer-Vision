# Machine-Learning-for-Computer-Vision
This project experiments various machine learning models on computer vision tasks such as image super resolution, style transferring, and object detection. 

## Introduction
Machine learning is now a fast developing research field with vast applications. The objective of this summary is to briefly explain how some neural network for processing image in some form of artistic ways and image classification and some thought on them. The main focus is to apply machine learning methods to computer vision tasks. Here, we experiment with various tasks such as style transferring, image super resolution, and image classification.

## Style transfer net
The style transfer model is trained to transfer pattern of a style image to another image. 	

### Algorithm:
Convolution neural network is used for the model. The style loss and content loss are measured by loss function. The loss function can be VGG, MSE. The basic idea that the model can extract image style from the style image match it on to the contour of the other image. 

Resize the input image and style images. 

Load vgg16 model 

From the latent layers, we seperate content and style 

Minimize loss: 

-Content loss 

-Style loss 

optimize with the L-BFGS algorithm. 


<img src="results/截屏2020-06-29 下午3.28.01.png" width = "500">

### Result:
The result is better when more suitable image is chosen. The result image will kind of look like filling the pattern of the style image into the unclear contour of the other image. 
Content image | Style image | Style transfer result
------------ | ------------- | -------------
<img src="results/未命名文件夹/IMG_1206.jpeg"  width = "250"> | <img src="results/未命名文件夹/IMG_1291.jpeg" width = "250"> | <img src="results/crazystyle1.png" width = "250">
<img src="results/未命名文件夹/IMG_1528.jpeg"  width = "250"> |<img src="results/未命名文件夹/IMG_0900.jpeg" width = "250">|<img src="results/crazystyle2.png" width = "250">
<img src="results/未命名文件夹/IMG_0900.jpeg"  width = "250"> |<img src="results/未命名文件夹/IMG_1430.jpeg" width = "250">|<img src="results/crazystyle3.png" width = "250">
<img src="results/未命名文件夹/IMG_0900.jpeg"  width = "250">|<img src="results/未命名文件夹/IMG_1206.jpeg" width = "250">|<img src="results/crazystyle4.png" width = "250">
<img src="results/未命名文件夹/IMG_0791.png"  width = "250">|<img src="results/未命名文件夹/IMG_0530.png" height = "250">|<img src="results/crazystyle6.png" width = "250">

### Thought:
Although this model is good to create some artistic image, the generated image probably will not truly reflect the style of the style image since the model cannot often properly match the pattern to the correct place. 

## Deep dream net:
The deep dream net makes the image look very wired by make some pattern in the image look like pattern of something else.

### Algorithm:
The algorithm is slightly similar to the style transfer. The convolution layers are used in the model. The basic idea is to make the detail in the original image that looks like feature in the style image more like the feature of the style image. 

<img src="results/inception.png" width = "500">

### Result:
This result image often looks very wired and sometimes horrifying. The generated image will have detail that resemble the feature of the style image, but the color is chaotic. 

Content image | Deep dream result | Iteratively Zoomed result
------------ | ------------- | -------------
<img src="results/未命名文件夹/IMG_0001_2.jpeg" height = "250" width = "250">|<img src="results/deepdream1.jpg" height = "250" width = "250">|<img src="results/deepdream.jpg" height = "250" width = "250">
<img src="results/未命名文件夹/IMG_1528.jpeg" height = "250" width = "250">|<img src="results/Unknown-11.jpg" height = "250" width = "250">|<img src="results/Unknown-21.jpg" height = "250" width = "250">
<img src="results/IMG_2513.jpg" height = "250" width = "250">|<img src="results/Unknown-31.jpg" height = "250" width = "250">|<img src="results/Unknown-32.jpg" height = "250" width = "250">
<img src="results/IMG_1624.jpeg" height = "250" width = "250">|<img src="results/Unknown-42.jpg" height = "250" width = "250">|<img src="results/Unknown-41.jpg" height = "250" width = "250">

### Thought:
The algorithm might be able to generate something more interesting than the weird image by slightly altering the model.

## Super resolution:
The model can make resize the image and recover some detail.

### Algorithm:
The model consists Gan and residual block. discriminator of the Gan is trained first to check whether the generated image is real enough. 

Downscale High resolution image to get training data

Upsample the low resolution using generator

The descrimator check the result and give the loss to train the generator


<img src="results/截屏2020-07-01 下午2.39.37.png" width = "500">

### Result: 
The generated image is almost indistinguishable to people who has few experiences in art. Blurry edges can often be wrongly generated and the color might changed slightly. Although it cannot recover full lost detail in some cases, the result is good enough.

Original image | Orignal image(downscale) | LR | SR(PRE) | SR(GAN)
------------ | ------------- | ------------- | ------------- | -------------
<img src="results/未命名文件夹/IMG_20160724_103423.jpeg" width = "250">|<img src="results/未命名文件夹/IMG_20160724_1034232.jpg" width = "250">|<img src="results/Unknown-3_副本.png" width = "250">|<img src="results/Unknown-3_副本2.png" width = "250">|<img src="results/Unknown-3_副本3.png" width = "250">
<img src="results/未命名文件夹/IMG_1403.jpeg" width = "250">|<img src="results/Webp.net-resizeimage.jpg" width = "250">|<img src="results/Unknown-54_副本.png" width = "250">|<img src="results/Unknown-54_副本2.png" width = "250">|<img src="results/Unknown-54_副本3.png" width = "250">
<img src="results/IMG_1624.jpeg" width = "250">|<img src="results/Webp.net-resizeimage-2.jpg" width = "250">|<img src="results/Unknown-64_副本.png" width = "250">|<img src="results/Unknown-64_副本2.png" width = "250">|<img src="results/Unknown-64_副本3.png" width = "250">

## Yolonet:
This algorithm detect object image and locate its position with a bounding box. It is trained with data with proper labels.
Costum data Result after trained for a short time:

### Algorithm: 
The image is diveded by neural network 

Probability of each region and bounding box is predicted

<img src="results/1*ZbmrsQJW-Lp72C5KoTnzUg.jpeg" width = "500">

### Result: 
<img src="results/Unknown.png" width = "500">
	
<img src="results/Unknown-2.png" width = "500">

<img src="results/Unknown-75.png" width = "500">
		
### Thought: 
The result is quite good for detecting those objects that is hardly distinguish from background after trained for a short time. 

### References:
Johnson, J., Alahi, A., & Fei-Fei, L. (2016, October). Perceptual losses for real-time style transfer and super-resolution. In European conference on computer vision (pp. 694-711). Springer, Cham.

Lacout, F. (2019, March 21). Deep Dream with tensorflow Keras. Retrieved July 01, 2020, from https://www.kaggle.com/flacout/deep-dream-with-tensorflow-keras

Ledig, C., Theis, L., Huszár, F., Caballero, J., Cunningham, A., Acosta, A., ... & Shi, W. (2017). Photo-realistic single image super-resolution using a generative adversarial network. In Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 4681-4690). 

Redmon, J., Divvala, S., Girshick, R., &amp; Farhadi, A. (n.d.). You Only Look Once: Uniﬁed, Real-Time Object Detection. Retrieved July 1, 2020, from https://pjreddie.com/media/files/papers/yolo.pdf

Redmon, Joseph, and Ali Farhadi. “YOLOv3: An Incremental Improvement.” YOLO: Real-Time Object Detection, ArXiv, 2018, pjreddie.com/darknet/yolo/.

### Code references:
Style transfer: https://github.com/lengstrom/fast-style-transfer 

Deep dream: https://colab.research.google.com/drive/1DWcrN9WXni58MbddvlShX0wF_oeo8W_0 

Super resolution: https://github.com/deepak112/Keras-SRGAN 

Yolonet: https://colab.research.google.com/drive/1Mh2HP_Mfxoao6qNFbhfV3u28tG8jAVGk 

