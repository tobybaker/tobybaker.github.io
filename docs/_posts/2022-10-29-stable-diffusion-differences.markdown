---
layout: post
title:  "Visualizing Diffusion Model Evolution"
date:   2022-10-29 11:37:59 +0100
categories: jekyll update
---

Stable Diffusion is generative AI model for producing images from text. It is a form of diffusion model where a model is trained to gradually denoise an image conditioned on an input prompt over a number of iterations. Then with the trained model, we can start with pure gaussian noise and an input prompt and produce a brand new image. The results are impressive.

![A stable diffusion render of a panda wearing a top hat five gradual stages.](/assets/images/pandatop.png)

To reduce training time Stable Diffusion carries out the diffusion process in a latent space before converting to a 512x512 image through a variational autoencoder.