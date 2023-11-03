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
  <div style="display: inline-block;">
    <a href="https://github.com/cassandra-t-ye/Learned_Uncertainty_Quantification">
      <img src="/assets/img/proj_1/github.png" alt="Github Repo" style="width: 70px; height: auto; margin-right: 20px; text-align: center;">
    </a>
    <div class="caption" style="text-align: center;">Github Repo</div>
  </div>
  <div style="display: inline-block;">
    <a href="https://arxiv.org/abs/2310.16102">
      <img src="/assets/img/proj_1/paper_front_page.png" alt="Arxiv Paper" style="width: 70px; height: auto; margin-left: 20px; text-align: center;">
    </a>
    <div class="caption" style="text-align: center;">Arxiv Paper</div>
  </div>
</div>


<!-- **Authors:** [Cassandra Tong Ye <sup>1</sup>](https://cassandra-t-ye.gtihub.io), Jiashu Han, Kunzan Liu, [Anastasios Angelopoulos](https://people.eecs.berkeley.edu/~angelopoulos/), [Linda Griffith](https://lgglab.mit.edu/), [Kristina Monakhova](http://kristinamonakhova.com/), [Sixian You](https://sixianyou.mit.edu/) 
-->
<div class="section">
    <b style="font-size: 24px;">Abstract</b>
    
    <div class="row">
        <div class="col-md-12" style="text-align: center;"> 
            {% include figure.html path="assets/img/proj_1/teaser.gif" title="Multiphoton Microscopy" class="img-fluid " style="height: 230px;"%}
        </div>
        <div class="col-md-12"> <!-- This will make the text take up 6 columns (half the width) on medium-sized screens -->
            Multiphoton microscopy (MPM) is a powerful imaging tool that has been a critical enabler for live tissue imaging. However, since most multiphoton microscopy platforms rely on point scanning, there is an inherent trade-off between acquisition time, field of view (FOV), phototoxicity, and image quality, often resulting in noisy measurements when fast, large FOV, and/or gentle imaging is needed. Deep learning could be used to denoise multiphoton microscopy measurements, but these algorithms can be prone to hallucination, which can be disastrous for medical and scientific applications. We propose a method to simultaneously denoise and predict pixel-wise uncertainty for multiphoton imaging measurements, improving algorithm trustworthiness and providing statistical guarantees for the deep learning predictions. Furthermore, we propose to leverage this learned, pixel-wise uncertainty to drive an adaptive acquisition technique that rescans only the most uncertain regions of a sample. We demonstrate our method on experimental noisy MPM measurements of human endometrium tissues, showing that we can maintain fine features and outperform other denoising methods while predicting uncertainty at each pixel. Finally, with our adaptive acquisition technique, we demonstrate a 120X reduction in acquisition time and total light dose while successfully recovering fine features in the sample. We are the first to demonstrate distribution-free uncertainty quantification for a denoising task with real experimental data and the first to propose adaptive acquisition based on reconstruction uncertainty. 

        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Intro to Multiphoton Microscopy</b>
    <div class="row">
        <div class="col-md-6">
            Multiphoton microscopy (MPM) is a form of laser-scanning microscopy based on nonlinear interactions between ultrafast laser pulses and biological tissues. Since its first demonstration decades ago, MPM has become the imaging technique of choice for non-invasive imaging of thick or living samples. Owing to its unique advantage of imaging depth and subcellular resolution, MPM has been used extensively to measure calcium dynamics in deep scattering mouse brains in neuroscience and characterizing multicellular dynamics in immunology and cancer studies. Because of these unique advantages of MPM, it has made tremendous progress and become an increasingly popular tool for tissue and cell microscopy in neuroscience, immunology, and cancer research.

        </div>

        <div class="col-md-6">
            {% include figure.html path="assets/img/proj_1/mpm.png" title="Multiphoton Microscopy" class="img-fluid " style="width: 180px; height: auto;"%}
            <div class="caption" style="text-align: left;">
                Multiphoton microscopy (MPM) is a powerful imaging tool that has been a critical enabler for live tissue imaging.
            </div>
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Proposed Method</b>
    <div class="row">
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_1/fig_1_gif.gif" title="Fig. 1 Summary" class="img-fluid " width="700px" height="auto" %}        
        <div class="caption" style="text-align: left;">
            <b>Uncertainty-based Adaptive Imaging</b>: A noisy measurement is acquired with a scanning multiphoton microscope (MPM) and passed into a deep learning model that predicts a denoised image and its associated pixel-wise uncertainty. Subsequently, the top N uncertain pixels are selected for a rescan, obtaining more measurements at only the uncertain regions. As more adaptive measurements are taken, the deep learning model predicts a denoised image with lower uncertainty. Scan duration and power are minimized, limiting sample damage while maintaining high confidence in the model prediction.
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
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Denoising Results</b>
    <div class="row">
        <div class="col-md-12">
            We evaluated our fine-tuned NAFNet model with learned uncertainty against BM3D (classical method), Noise2Self (self-supervised DL method), and pre-trained NAFNet (supervised DL method) for single-image denoising. Our method, which is fine-tuned with our SHG dataset, outperforms the other methods in terms of MSE and SSIM. Our fine-tuned model can reconstruct features that BM3D and its pre-trained version cannot. In the region highlighted by the <span class="green-text">green box</span>, our model recovers fine structures present in the ground truth that the other methods cannot.

            Since leveraging multiple image measurements could enhance a model’s overall performance,
            next we compare denoising performance against several multi-frame denoisers. To measure
            performance, we chose VBM4D (classic method) and FastDVDNet (deep method) as reference
            benchmarks for denoising sequences of frames. When comparing denoised results, it is evident
            that all the multi-image techniques outperform their single-image counterparts as expected.     
        </div>
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_1/results_2.png" title="Fig. 2 Denoising Results" class="img-fluid "  %}        
        </div>
    </div>
</div>


<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Uncertainty Quantification</b>
    <div class="row">
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_1/results_3.png" title="Fig. 3 UQ" class="img-fluid"  %}        
        <div class="caption" style="text-align: left;">
            <b>Increasing measurements reduces uncertainty</b>: Results of single-image, three-image, and fiveimage denoising, showing the image prediction and predicted uncertainty. As the number of measurements increases, the predicted image more closely matches the ground truth, and the pixel-wise uncertainty
            decreases.
        </div>
    </div>
         <div class="col-md-12">
            With more measurements, the predicted uncertainty of the network decreases, demonstrating
            an increase in the confidence of the predicted image. We determined the display threshold
            for all three uncertainty predictions by choosing the uncertainty interval linked to the top 5%
            most uncertain pixels. <span class="red-text"> Red pixel regions </span>, indicate areas with larger uncertainty, whereas <span class="blue-text"> pixels appearing blue </span> represent lower uncertainty intervals. More importantly, as more fine structures are present, the uncertainty decreases.  This finding affirms that increasing measurements to our model not only improves denoising performance but also decreases the denoised prediction’s uncertainty. 
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Learned Adaptive Acquisition</b>
    
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Conclusion</b>
    We presented a method to utilize learned, distribution-free uncertainty quantification for multiimage denoising and proposed an adaptive acquisition technique based on the learned uncertainty.
    We demonstrated both methods on experimental MPM SHG measurements, showing a 120×
    decrease in total scanning time and a 120× decrease in total light dose while successfully
    recovering fine structures and outperforming existing denoising benchmarks. These speed and
    total light dose improvements are significant and demonstrate an important step towards faster
    and gentler MPM, which will enable the imaging of a new class of interesting samples and lead
    to new scientific insights and advances.
    Furthermore, we demonstrate how deep learning methods for microscopy can be designed to
    be trustworthy by building in uncertainty quantification to provide error bars for each prediction.
    To the best of our knowledge, we are the first to utilize distribution-free uncertainty quantification
    for a denoising task. Uncertainty quantification should become standard practice when using
    deep-learning techniques for scientific and medical imaging to reduce hallucinations and build
    confidence in image predictions. We believe that the distribution-free learned uncertainty
    quantification presented here is an attractive path toward this due to its ease of use, fast
    computational time, and statistical guarantees.
</div>


<div class="row" style="margin-top: 20px;">
    <div class="col-md-12">
        <b style="font-size: 24px;">Bibtex Citation</b>
        <div class="form-group col-md-12">
            <textarea id="bibtex" class="form-control" readonly>
            @article{ye2023learned,
                title       = {Learned, Uncertainty-driven Adaptive Acquisition for Photon-Efficient Multiphoton Microscopy},
                author      = {Ye, Cassandra Tong and Han, Jiashu and Liu, Kunzan and Angelopoulos, Anastasios and Griffith, Linda and Monakhova, Kristina and You, Sixian},
                journal     = {arXiv preprint arXiv:2310.16102},
                year        = {2023}
            }
            </textarea>
        </div>
    </div>
</div>





