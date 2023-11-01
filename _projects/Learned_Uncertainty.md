---
layout: page
title: Learned, Uncertainty-driven Adaptive Acquisition for Photon-Efficient Multiphoton Microscopy
description: 
img: assets/img/proj_1/cover_img.png
importance: 1
related_publications: ye2023learned
---
[Cassandra Tong Ye](https://kristinamonakhova.com/), Jiashu Han, Kunzan Liu, [Anastasios Angelopoulos](https://people.eecs.berkeley.edu/~angelopoulos/), [Linda Griffith](https://lgglab.mit.edu/), [Kristina Monakhova](http://kristinamonakhova.com/), [Sixian You](https://sixianyou.mit.edu/)

<div style="text-align: center;">
  <a href="https://github.com/cassandra-t-ye/Learned_Uncertainty_Quantification">
    <img src="/assets/img/proj_1/github.png" alt="Github Repo" style="width: 70px; height: auto; margin-right: 20px;">
  </a>  
  <a href="https://arxiv.org/abs/2310.16102">
    <img src="/assets/img/proj_1/paper_front_page.png" alt="Arxiv Paper" style="width: 70px; height: auto; margin-left: 20px;">
  </a>
</div>

<!-- **Authors:** [Cassandra Tong Ye <sup>1</sup>](https://cassandra-t-ye.gtihub.io), Jiashu Han, Kunzan Liu, [Anastasios Angelopoulos](https://people.eecs.berkeley.edu/~angelopoulos/), [Linda Griffith](https://lgglab.mit.edu/), [Kristina Monakhova](http://kristinamonakhova.com/), [Sixian You](https://sixianyou.mit.edu/) 
-->
<div class="section">
    <b>Abstract</b>
    <div class="row">
        <div class="col-md-12" style="text-align: center;"> 
            {% include figure.html path="assets/img/proj_1/teaser.gif" title="Multiphoton Microscopy" class="img-fluid rounded z-depth-1" style="height: 230px;"%}
        </div>
        <div class="col-md-12"> <!-- This will make the text take up 6 columns (half the width) on medium-sized screens -->
            Multiphoton microscopy (MPM) is a powerful imaging tool that has been a critical enabler for live tissue imaging. However, since most multiphoton microscopy platforms rely on point scanning, there is an inherent trade-off between acquisition time, field of view (FOV), phototoxicity, and image quality, often resulting in noisy measurements when fast, large FOV, and/or gentle imaging is needed. Deep learning could be used to denoise multiphoton microscopy measurements, but these algorithms can be prone to hallucination, which can be disastrous for medical and scientific applications. We propose a method to simultaneously denoise and predict pixel-wise uncertainty for multiphoton imaging measurements, improving algorithm trustworthiness and providing statistical guarantees for the deep learning predictions. Furthermore, we propose to leverage this learned, pixel-wise uncertainty to drive an adaptive acquisition technique that rescans only the most uncertain regions of a sample. We demonstrate our method on experimental noisy MPM measurements of human endometrium tissues, showing that we can maintain fine features and outperform other denoising methods while predicting uncertainty at each pixel. Finally, with our adaptive acquisition technique, we demonstrate a 120X reduction in acquisition time and total light dose while successfully recovering fine features in the sample. We are the first to demonstrate distribution-free uncertainty quantification for a denoising task with real experimental data and the first to propose adaptive acquisition based on reconstruction uncertainty. 

        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b>Intro to Multiphoton Microscopy</b>
    <div class="row">
        <div class="col-md-6">
            Multiphoton microscopy (MPM) is a form of laser-scanning microscopy based on nonlinear interactions between ultrafast laser pulses and biological tissues. Since its first demonstration decades ago, MPM has become the imaging technique of choice for non-invasive imaging of thick or living samples. Owing to its unique advantage of imaging depth and subcellular resolution, MPM has been used extensively to measure calcium dynamics in deep scattering mouse brains in neuroscience and characterizing multicellular dynamics in immunology and cancer studies. Because of these unique advantages of MPM, it has made tremendous progress and become an increasingly popular tool for tissue and cell microscopy in neuroscience, immunology, and cancer research.

        </div>

        <div class="col-md-6">
            {% include figure.html path="assets/img/proj_1/mpm.png" title="Multiphoton Microscopy" class="img-fluid rounded z-depth-1" style="width: 180px; height: auto;"%}
            <div class="caption" style="text-align: left;">
                Multiphoton microscopy (MPM) is a powerful imaging tool that has been a critical enabler for live tissue imaging.
            </div>
        </div>
    </div>
</div>

<b>Uncertainty Quantification and Our Proposed Method</b>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/proj_1/fig_1_summary.png" title="Fig. 1 Summary" class="img-fluid rounded z-depth-1" %}
        <div class="caption" style="text-align: left;">
           <b>(a) Uncertainty-based Adaptive Imaging</b>: A noisy measurement is acquired with a scanning multiphoton microscope (MPM) and passed into a deep learning model that predicts a denoised image and its associated pixel-wise uncertainty. Subsequently, the top N uncertain pixels are selected for a rescan, obtaining more measurements at only the uncertain regions. As more adaptive measurements are taken, the deep learning model predicts a denoised image with lower uncertainty. Scan duration andpower are minimized, limiting sample damage while maintaining high confidence in the model prediction.<b>(b) Rescanning Process</b>: Given a pixel-wise uncertainty prediction, regions with high uncertainty can be selected for rescanning. Only this patch of pixels will be rescanned in the sample, and this patch, superimposed with the original, becomes an additional channel that is fed into the model.
        </div>
    </div>

    <div class="col-md-12">
        Deep learning (DL) based methods have shown exciting results for denoising extremely noisy
        images in microscopy, however, they still produce hallucinations. To counter this uncertainty quantification techniques can help catch model hallucinations and improve the
        robustness of deep learning methods.

        We demonstrate distribution-free uncertainty quantification for MPM denoising
        and <b>propose an adaptive microscopy imaging pipeline</b> informed by uncertainty quantification.   

        This pipeline leverages the learned uncertainty to drive adaptive
        acquisition: we capture more measurements of our sample only at the most uncertain regions
        rather than rescanning the whole sample.     
    </div>
</div>



