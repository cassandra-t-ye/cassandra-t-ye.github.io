---
layout: page
title: Learned, Uncertainty-driven Adaptive Acquisition
for Photon-Efficient Multiphoton Microscopy
# author: 
# - [Cassandra Tong Ye](https://cassandra-t-ye.github.io) 
# - Jiashu Han
# - Kunzan Liu 
# - [Anastasios Angelopoulos](https://people.eecs.berkeley.edu/~angelopoulos/) 
# - [Linda Griffith](https://lgglab.mit.edu/) 
# - [Kristina Monakhova](http://kristinamonakhova.com/)
# - [Sixian You](https://sixianyou.mit.edu/)  
img: assets/img/proj_1/cover_img.png
importance: 1
category: 
related_publications: ye2023learned
---

**Abstract**

Multiphoton microscopy (MPM) is a powerful imaging tool that has been a critical enabler for live tissue imaging. However, since most multiphoton microscopy platforms rely on point scanning, there is an inherent trade-off between acquisition time, field of view (FOV), phototoxicity, and image quality, often resulting in noisy measurements when fast, large FOV, and/or gentle imaging is needed. Deep learning could be used to denoise multiphoton microscopy measurements, but these algorithms can be prone to hallucination, which can be disastrous for medical and scientific applications. We propose a method to simultaneously denoise and predict pixel-wise uncertainty for multiphoton imaging measurements, improving algorithm trustworthiness and providing statistical guarantees for the deep learning predictions. Furthermore, we propose to leverage this learned, pixel-wise uncertainty to drive an adaptive acquisition technique that rescans only the most uncertain regions of a sample. We demonstrate our method on experimental noisy MPM measurements of human endometrium tissues, showing that we can maintain fine features and outperform other denoising methods while predicting uncertainty at each pixel. Finally, with our adaptive acquisition technique, we demonstrate a 120X reduction in acquisition time and total light dose while successfully recovering fine features in the sample. We are the first to demonstrate distribution-free uncertainty quantification for a denoising task with real experimental data and the first to propose adaptive acquisition based on reconstruction uncertainty.


**Multiphoton Microscopy**

Multiphoton microscopy (MPM) is a form of laser-scanning microscopy based on nonlinear
interactions between ultrafast laser pulses and biological tissues. Since its first demonstration
decades ago, MPM has become the imaging technique of choice for non-invasive imaging of
thick or living samples.

<div class="row">
    <div class="col-sm mt-1 mt-md-0">
        {% include figure.html path="assets/img/proj_1/img1.png" title="Multiphoton Microscopy" class="img-fluid rounded z-depth-1"%}
    </div>
</div>
<div class="caption">
    Multiphoton microscopy (MPM) is a powerful imaging tool that has been a critical enabler for live
    tissue imaging.
</div>

### Uncertainty Quantification




<!-- You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal its glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %} -->