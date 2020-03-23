# nima_gan
This is an attempt at designing and training a GAN to generate nice images. It is implemented in PyTorch.

A lot of the code is just a modified version of the basic PyTorch [DCGAN TUTORIAL](https://pytorch.org/tutorials/beginner/dcgan_faces_tutorial.html).

The dataset base I am using is [AVA: "A large-scale database for aesthetic visual analysis"](https://doi.org/10.1109/CVPR.2012.6247954). However, I am only using images with a mean score over 6 and the images have been rescaled to a square aspect ration and a smaller resolution.
