---
layout: post
title:  "Visualizing Diffusion Model Evolution"
date:   2022-10-29 11:37:59 +0100
categories: jekyll update
---

Stable Diffusion is generative AI model for producing images from text. It is a form of diffusion model where a model is trained to gradually denoise an image conditioned on an input prompt over a number of iterations. Then with the trained model, we can start with pure gaussian noise and an input prompt and produce a brand new image. The results are impressive.

Prompt : '*an astronaut relaxing on a tropical island*'
![A stable diffusion render of a astronaut on a tropical island over five gradual stages.](/assets/images/astronaut_top.png)

To reduce training time, Stable Diffusion carries out the diffusion process in a latent space before converting to a 512x512 image through a variational autoencoder. This is why the noise at the start of the diffusion process looks somewhat denser and less grainy than a image composed of pure gaussian noise.

To visualise what the network was doing at each step I thought it would be interesting to visualise the difference between sequential iterations of the de-diffusion process. Looking at the example above, we can measure the absolute difference (in RGB space) between the the denoised step and the previous iteration at a number of timepoints.

Prompt : '*an astronaut relaxing on a tropical island*'
![A stable diffusion render of a astronaut on a tropical island over five gradual stages. The bottom row is the differences between the denoised images at each iteration](/assets/images/astronaut0-15-30-40-47.png)

At the start there is no obvious pattern to the changes, however midway through the shape of the final image becomes clearer and the changes are focussed on areas of high detail in the image. Looking at another example.

Prompt : '*a portrait of a panda wearing a top hat, cartoon*'
![A stable diffusion render of a panda wearing a top hat over five gradual stages. The bottom row is the differences between the denoised images at each iteration](/assets/images/panda0-15-30-40-47.png)

Here the panda face is obvious in the first iteration even though the change is impercetible in the noisy images themselves:

![A stable diffusion render of a panda wearing a top hat over five gradual stages.](/assets/images/pandatop.png)

This is true for other pandas, but it seems the cartoon modifier is needed, perhaps as it encourages block colours.

Prompt : '*a panda portrait, cartoon*'
![A stable diffusion render of a sphere over five gradual stages.](/assets/images/pandacartoon0-15-30-40-47.png)
Prompt : '*a panda portrait*'
![A stable diffusion render of a sphere over five gradual stages.](/assets/images/pandaportrait0-15-30-40-47.png)

When visualising all of the changes it is clear that the model mostly works on the panda intially before focussing on the background towards the end.

![A stable diffusion render of a sphere over five gradual stages.](/assets/images/panda_evolution.gif)

I haven't managed to find any other image that seems to have a recognisable initial diffusion change as pandas. Even with objects with very distinctive shapes. I wonder what's so special about pandas?

Prompt : '*a snowman cartoon*'
![A stable diffusion render of a snowman photograph over five gradual stages.](/assets/images/snowmancartoon0-15-30-40-47.png)
Prompt : '*pyramids of giza, cartoon*'
![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pyramidsofgiza0-15-30-40-47.png)
Prompt : '*a zebra cartoon*'
![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/zebracartoon0-15-30-40-47.png)
Prompt : '*a pineapple, pop art*'
![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pineapple0-15-30-40-47.png)
