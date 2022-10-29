---
layout: post
title:  "Visualizing Diffusion Model Evolution"
date:   2022-10-29 11:37:59 +0100
categories: jekyll update
---

Stable Diffusion is generative AI model for producing images from text. It is a form of diffusion model where a model is trained to gradually denoise an image conditioned on an input prompt over a number of iterations. Then with the trained model, we can start with pure gaussian noise and an input prompt and produce a brand new image. The results are impressive.

Prompt : '*an astronaut relaxing on a tropical island*'
![A stable diffusion render of a astronaut on a tropical island five gradual stages.](/assets/images/astronauttop.png)

To reduce training time Stable Diffusion carries out the diffusion process in a latent space before converting to a 512x512 image through a variational autoencoder. This is why the noise at the start of the diffusion process looks somewhat denser and less grainy than a image composed of pure gaussian noise.

To visualise what the network was doing at each step I thought it would be interesting to visualise the difference between sequential iterations of the de-diffusion process. Looking at the example above, we can measure the absolute difference (in RGB space) between the initial gaussian noise and the first denoised iteration.

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

Although it can't be seen in the noisy images themselves, there's a clearly the start of the panda's face emerging in the difference. We can then look at differences at later stages in the diffusing process.

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

It seems that as diffusing process continues the parts of the image that are changing get more and more distinctive. The white and black areas of the image are almost untouched by the end with the majority of the changes occuring in the background and the edges in the image. Looking at a few more examples:

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

Here the initial changes don't nearly as closely resemble the final image as before. It takes a few iterations before the shape becomes apparent. Maybe if I we try a few more images with very distinctive shapes?

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

