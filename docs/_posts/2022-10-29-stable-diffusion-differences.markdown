---
layout: post
title:  "Visualizing Diffusion Model Evolution"
date:   2022-10-29 11:37:59 +0100
categories: jekyll update
---

Stable Diffusion is generative AI model for producing images from text. It is a form of diffusion model where a model is trained to gradually denoise an image conditioned on an input prompt over a number of iterations. Then with the trained model, we can start with pure gaussian noise and an input prompt and produce a brand new image. The results are impressive.

Prompt : '*an astronaut relaxing on a tropical island*'
![A stable diffusion render of a astronaut on a tropical island five gradual stages.](/assets/images/astronaut_top.png)

To reduce training time Stable Diffusion carries out the diffusion process in a latent space before converting to a 512x512 image through a variational autoencoder. This is why the noise at the start of the diffusion process looks somewhat denser and less grainy than a image composed of pure gaussian noise.

To visualise what the network was doing at each step I thought it would be interesting to visualise the difference between sequential iterations of the de-diffusion process. Looking at the example above, we can measure the absolute difference (in RGB space) between the the denoised step and the previous iteration at a number of timepoints.

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/astronaut0-15-30-40-47.png)

The differences are coloured so that the biggest difference in each image is yellow. To start with there is no obvious pattern to the changes but midway through the process the shape of final image becomes clearer and the changes are focussed on areas of high detail in the image. Looking at another example.


![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/panda0-15-30-40-47.png)

Here the panda face is obvious in the first iteration. Even though the change is impercetible in the noisy images themselves:

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

Another property worth noting is that towards the end of the process the black and white parts of the image are constant and its the background that it mostly changing. This is a phenomena that seems to be repeated with simple objects.

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/sphere0-15-30-40-47.png)

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/cake0-15-30-40-47.png)

Here the initial changes don't nearly as closely resemble the final image as before. It takes a few iterations before the shape becomes apparent. Maybe if I we try a few more images with very distinctive shapes?

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

