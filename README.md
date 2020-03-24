# nima_gan
This is an attempt at designing and training a GAN to generate nice images. It is implemented in PyTorch.

The goal here is a bit different than for a usual GAN as we don't want to have realistic images but interesting images. This is achieved by three factors: A very simple pure DCGAN architecture is used, none of the usual GAN tricks to improve performance is used besides trying to balance the generator and discriminator, and the dataset chosen is very diverse in its image content.

The dataset base that is used is [AVA: "A large-scale database for aesthetic visual analysis"](https://doi.org/10.1109/CVPR.2012.6247954). However, only images with a mean score over 6 are used and the images have been rescaled to a square aspect ratio and a smaller resolution. Thus, the images have the abstract quality of being "good" in common, but the have very diverse visual content.

![GAN generated images](img/nima_gan.jpg?raw=true "GAN generated images")

A lot of the code is just a modified version of the basic PyTorch [DCGAN TUTORIAL](https://pytorch.org/tutorials/beginner/dcgan_faces_tutorial.html).

This project was inspired by the [NIMA: Neural Image Assessment](https://doi.org/10.1109/TIP.2018.2831899) paper.

Early versions didn't implement a traditional GAN architecture, but replaced the descriminator with a scorer network, that was trained via transfer learning on the whole AVA dataset to asses the score distribution of the image. For training, the scorer was put in sequence with the generator with clamped weights of the scorer, and the gradient was calculated from the whole network with a score distribution randomly drawn from a high scoring gaussian distribution as its target. This scorer network was working fine, but the generator wasn't converging. I don't really know what exactly went wrong, but one suspect are the batch normalization layers of keras when loading the pre-trained scorer model.
