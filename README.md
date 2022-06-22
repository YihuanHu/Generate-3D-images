# Interpolation of StyleGan2

### Introduction
Thisn project is mainly focus on basic exploration of StyleGAN2. StyleGAN2 is the pre-traiend generative adversarial network where “Style” in the StyleGAN paper refers to major attributes of the data like pose, and identity. Combined with the feature of this arechitecture and I'm a fan of Pokemon, I'm wondering how StyleGAN2 can surpreise us with Pokemon Dataset.  With the limited computational resources and dataset, StyleGAN2 with adaptive discriminator augmentation (ADA) are adopted.

### Data
This dataset is downloaded from Kaggle (https://www.kaggle.com/datasets/vishalsubbiah/pokemon-images-and-types). It includes 809 unique images with 93x93 resolution. This is a very very small dataset and the expectation of this project is not as accurate as possible. This is more like an exploration to extract the most significant features among all the Pokemon.

### Implementation

Pretrained model can lead to quick convergence. Since StyleGAN2 only provides  pretrained model for 256x256 or 1024x1024, all the images have been properly resized to 256x256. Then, all the images are transformed into tfrecords.  Paramerts are tuned. After long waitting time on GPU,  the trained custom model is save as pickle file with only  runs for 410 kimgs(thousands of images).

Ref: https://colab.research.google.com/github/dvschultz/ml-art-colabs/blob/master/Stylegan2_ada_Custom_Training.ipynb


### Result

Even though this customed model doesn't run for at least 25000 kimgs, it did give us some prompt as it generate images:

![grid](/Users/huyihuan/GITHUB/Generate-3D-images/out/grid.png)

It is clearly to see this mode collapses for repeatly generating output that looks real. To some extent, this can be explained by the very small dataset which might have an effect on the latent space. And this also shows up in the latent space exploration:

<video src="/Users/huyihuan/GITHUB/Generate-3D-images/out/result.mp4"></video>

The weird Pokemon seems to show up everywhere, which might imply the feature of sharpe claws and ears might be an common characteristc even though nobody wants a Pokemon looks like this.

### Reflection

I have been thinking about how to solve the problem of mode collabpse of unable to learn a rich feature representation. One possible solution might be WGAN but it might face the same problem with such a limited dataset. Another improvement might be very straightforward: train for more kimgs. This is feasible as long as I have some budgets. In conclusion, GAN is such a charming and applicable architecture as long as it conveges and not collapse. 
