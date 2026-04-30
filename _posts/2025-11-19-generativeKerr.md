---
layout: post
title: "Machine Learning Kerr Combs"
date: 2025-11-19 12:00:00 +0000
categories: research
---

We will be presenting some [work](https://ml4physicalsciences.github.io/2025/files/NeurIPS_ML4PS_2025_33.pdf) on the inverse design of Kerr combs at the Machine Learning and the Physical Sciences Workshop @ NeurIPS. We train a generative neural network on Lugiato-Lefever equation simulations using variational autoencoders and flow-matching models.

# Summary

Light in integrated micro-resonators (ring-shaped optical media) can lead to highly nonlinear processes and complex
optical spectra including frequency combs, instabilities, solitons, and more. Due to
the inherent nonlinearity, bistability, and hysteresis in the system, the mapping of
desired optical spectral properties to input physical parameters can be very difficult.
Unlike previous approaches using traditional optimization or non-generative neural
networks, which struggle with multi-solution landscapes, we frame this inverse
design problem as a generative distribution-learning task for the first time. Using
conditional variational autoencoders and flow matching models, we generate input
parameters and their spectra for high-bandwidth steady-state solitons trained on
Lugiato-Lefever equation simulations. Our approach can be applied to experimental
data with little modification. Real experimental conditions for Kerr combs often
deviate from theoretical models, making data-driven machine learning approaches
particularly promising for applications in spectroscopy, optical communications,
and nonlinear optics research.

# Lugiato-Lefever equation and Kerr combs

The behaviour of continuous-wave laser light incident on an optical resonator can be studied with the Lugiato-Lefever equation (LLE).

<p align="center">
  <img src="/assets/kerr_images/LLE.png" alt="LLE">
</p>

The above picture shows what the LLE predicts as the laser is tuned across the resonance. In (a), the horizontal axis is detuning (∆), which is the mismatch between the input laser frequency and the natural frequency of the resonator. As detuning is swept, the system can move through several regimes: a continuous-wave state, Turing rolls, instabilities, solitons, and eventually back to a continuous-wave state. Panel (b) shows a snapshot of the field intensity around the ring coordinate 𝜑, while panel (c) shows the same state in frequency space as an optical spectrum. Note that the stability of the states (how they fluctuate in time) is also important, and is contained in the LLE solution but is not shown in these snapshots here.

# Generative neural network motivation

One useful target is a broadband steady-state soliton, where the optical spectrum spans many modes while remaining stable. These states are useful for applications such as telecommunications and metrology, but finding the parameters that generate them is a nonlinear, high-dimensional problem. In this system, many different physical settings can produce similar spectra, making the inverse problem very one-to-many.

Generative neural networks are an interesting approach because they can represent multiple valid solutions rather than returning a single optimized point. In this work, we use conditional VAEs and flow matching models to generate candidate Kerr-comb parameters and spectra, and show that multi-objective inverse design can work well in this setting. For more details, see the paper link above.

<p align="center">
  <img src="/assets/kerr_images/genv2.png" alt="Generative Kerr comb model">
</p>

In the picture above in (a, b), we show in the top row some generated samples and in the bottom row of (a, b) we show the nearest example in the test set, which are directly from the LLE. They match very well. In (c) and (d), we show one of the evaluation metrics, which is how close the generated distribution of parameters matches the test set parameter distribution (via a Wasserstein metric). In this metric, the flow model does better, but there are pros and cons of different models. The VAE is significantly cheaper to train.

# Acknowledgement

Thank you to my co-authors on this work, in particular to Eran who taught me about Kerr combs and Shiye who taught me about flow models.
