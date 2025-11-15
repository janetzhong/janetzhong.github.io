---
layout: post
title: "Machine Learning Kerr Combs"
date: 2025-11-14 12:00:00 +0000
categories: research
---

We will be presenting some [work](/assets/Machine_Learning_Kerr_Combs_v2_Nov14.pdf) on the inverse design of Kerr combs at the Machine Learning and the Physical Sciences Workshop @ NeurIPS. We train a generative neural network on Lugiato-Lefever equation simulations using variational autoencoders and flow-matching models.

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
  <img src="/assets/images/LLE.pdf" alt="LLE">
</p>

The above picture in (a) is the optical spectra vs detuning (∆) calculated using the LLE. Detuning is the mismatch between the input laser frequency and the natural frequency of resonator. The order of transitions (if they occur) as detuning is swept is CW → Turing rolls → instabilities → solitons → CW. (b) is the field intensity snapshot vs spatial coordinate in the ring 𝜑 and (c) is the optical spectra snapshot in mode (frequency) space.

# Kerr comb inverse design motivation

The nonlinearity of Kerr combs means that they are difficult to analytical solve or computationally simulate. The LLE does not perfectly match reality, and thus data-driven machine learning approaches on actual experimental data is very compelling. For some desired property of optical spectra in the picture above, it is difficult to predict the physical parameters that produce it since the problem is nonlinear, high dimensional, and may have many solutions. An example of an inverse design objective is broadband solitons (which is when the optical spectra spans a wide number of modes and is a steady-state - both properties are useful for applications such as in telecommunications or metrology). Generative neural networks offer a compelling alternative to traditional optimization methods because they naturally represent the multi-valued nature of the problem. Conditional models also have the benefit that they do not require an extra optimization step. We train such a model using VAEs and flow matching models and we show that multi-objective inverse design can work well for Kerr combs. For more details, see the paper link above.

# Acknowledgement

Thank you to my co-authors on this work, in particular to Eran who taught me about Kerr combs and Shiye who taught me about flow models.
