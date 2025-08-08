---
layout: page
title: "QUTCC🤗: Quantile Uncertainty Training and Conformal Calibration for Imaging Inverse Problems"
description: 
img: 
importance: 1
related_publications: ye2025qutcc
---
[Cassandra Tong Ye](https://https://cassandra-t-ye.github.io/), [Shamus Li](https://shamus.li/), [Tyler King](https://tylertking.com/), [Kristina Monakhova](http://kristinamonakhova.com/)

<div style="text-align: center; margin: 20px 0;">
  <a href="https://github.com/cassandra-t-ye/qutcc">
    <img src="https://img.shields.io/badge/Code-GitHub-black?style=for-the-badge&logo=github" alt="GitHub">
  </a>
  <a href="https://arxiv.org/abs/2507.14760" style="margin-left: 10px;">
    <img src="https://img.shields.io/badge/Paper-arXiv-red?style=for-the-badge&logo=arxiv" alt="arXiv">
  </a>
</div>


<!-- <!-- **Authors:** [Cassandra Tong Ye <sup>1</sup>](https://cassandra-t-ye.gtihub.io), Jiashu Han, Kunzan Liu, [Anastasios Angelopoulos](https://people.eecs.berkeley.edu/~angelopoulos/), [Linda Griffith](https://lgglab.mit.edu/), [Kristina Monakhova](http://kristinamonakhova.com/), [Sixian You](https://sixianyou.mit.edu/) 
-->
<div class="section">
    <b style="font-size: 24px;">Abstract</b>
    
    <div class="row">
        <div class="col-md-12" style="text-align: center;"> 
            {% include figure.html path="assets/img/proj_2_qutcc/teaser.gif" title="Multiphoton Microscopy" class="img-fluid " style="height: 230px;"%}
        </div>
        <div class="col-md-12"> <!-- This will make the text take up 6 columns (half the width) on medium-sized screens -->
            Deep learning models often hallucinate, producing realistic artifacts that are not truly present in the sample. This can have dire consequences for scientific and medical inverse problems, such as MRI and microscopy denoising, where accuracy is more important than perceptual quality. Uncertainty quantification techniques, such as conformal prediction, can pinpoint outliers and provide guarantees for image regression tasks, improving reliability. However, existing methods utilize a linear constant scaling factor to calibrate uncertainty bounds, resulting in larger, less informative bounds. We propose QUTCC, a quantile uncertainty training and calibration technique that enables nonlinear, non-uniform scaling of quantile predictions to enable tighter uncertainty estimates. Using a U-Net architecture with a quantile embedding, QUTCC enables the prediction of the full conditional distribution of quantiles for the imaging task. During calibration, QUTCC generates uncertainty bounds by iteratively querying the network for upper and lower quantiles, progressively refining the bounds to obtain a tighter interval that captures the desired coverage. We evaluate our method on several denoising tasks as well as compressive MRI reconstruction. Our method successfully pinpoints hallucinations in image estimates and consistently achieves tighter uncertainty intervals than prior methods while maintaining the same statistical coverage. 
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Quantile Regression: Pinball Loss</b>
    <div class="row">
        <div class="col-md-6">
            Quantile regression is a statistical technique that estimates conditional quantiles of a response variable distribution. Unlike traditional regression which estimates the mean, quantile regression provides a more complete picture of the relationship between variables by estimating different quantiles (e.g., 10th, 50th, 90th percentiles).
        </div>
        <div class="col-md-6">
            {% include figure.html path="assets/img/proj_2_qutcc/pinball_loss_animation.gif" title="Pinball Loss" class="img-fluid" style="width: 250px; height: auto;"%}
            <div class="caption" style="text-align: left;">
                Pinball loss is an asymmetric loss function used to estimate conditional quantiles of distribution in data. 
            </div>
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Our Method: QUTCC</b>
    <div class="row">
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/fig_1_gif.gif" title="Fig. 1 Summary" class="img-fluid " width="700px" height="auto" %}        
        <div class="caption" style="text-align: left;">
            <b>Uncertainty-based Adaptive Imaging</b>: A noisy measurement is acquired with a scanning microscopye and passed into a deep learning model that predicts a denoised image and its associated pixel-wise uncertainty. Subsequently, the top N uncertain pixels are selected for a rescan, obtaining more measurements at only the uncertain regions. As more adaptive measurements are taken, the deep learning model predicts a denoised image with lower uncertainty. Scan duration and power are minimized, limiting sample damage while maintaining high confidence in the model prediction.
        </div>
    </div>

        <div class="col-md-12">
            Deep learning (DL) based methods have shown exciting results for denoising extremely noisy
            images in microscopy, however, they still produce hallucinations. To counter this uncertainty quantification techniques can help catch model hallucinations and improve the
            robustness of deep learning methods.

            We demonstrate distribution-free uncertainty quantification for denoising
            and <b>propose an adaptive microscopy imaging pipeline</b> informed by uncertainty quantification.   

            This pipeline leverages the learned uncertainty to drive adaptive
            acquisition: we capture more measurements of our sample only at the most uncertain regions
            rather than rescanning the whole sample.     
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Multi-Image Denoising and Uncertainty Quantification Results</b>
    <div class="row">
        <div class="col-md-12">
            We evaluated our denoising and uncertainty prediction on an experimental dataset of confocal and two-photon
            measurements (FMD dataset) as well as a custom multiphoton dataset (MPM dataset). First, we test our denoiser’s performance as a function of the number of noisy measurements. To do this, we vary the input to the network, feeding in 1-20 unique, non-moving, noisy measurements. Each measurement has a different instance of noise, so intuitively, with more measurements, the denoising prediction should improve. In the image below, we show the predicted denoised images and uncertainty maps for samples from the FMD dataset. Here, we can see that as the number of measurements increases, the network’s predicted uncertainty
            decreases, and concurrently, the denoised predictions become sharper and closer to the ground truth. In the zoomed in portion of the image, we demonstrate a hallucination that was observed in the first denoised iteration (indicated by high uncertainty), which is resolved by the tenth denoised iteration. 
        </div>
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/results_2.png" title="Fig. 2 Denoising Results for FMD Samples" class="img-fluid "  %}        
        </div>
    </div>
</div>


<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Uncertainty informed Adaptive Acquisition</b>
    <div class="row">
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/results_3.png" title="Fig. 3 UQ" class="img-fluid"  %}        
        <div class="caption" style="text-align: left;">
            <b>Adaptive Acquisition of two-photon images:</b> We compare three different color channels from a two-photon sample
            from the FMD dataset. After single-image denoising, we threshold the uncertainty to obtain an adaptive mask (center).
            Each channel has a different percentage of rescanned pixels (red text), which leads to a total light dosage savings of x2.6,
            x2.7, x5.6, respectively. .
        </div>
    </div>
         <div class="col-md-12">
            Does uncertainty-guided adaptive acquisition retain image quality, while decreasing the total number of pixels
            needed and increasing the light-dosage savings? We investigated the effects of different adaptive percentages on
            different two-photon samples. In this experiment, we show the adaptive mask slowly changing through
            iterations- with earlier iterations needing more pixels and later iterations exclusively segmenting areas of high
            signal to adaptively acquire. After the 20th iteration, zoomed-in samples of the adaptively acquired and denoised
            image demonstrate that it maintains the same level of details for sample features, while providing a significant
            improvement in acquisition parameters. In the figure presented, we show an improvement between 2.6 and 5.6 times in light
            dosage while retaining image quality.
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Adaptive Acquisition of samples can catch hallucinations</b>
    <div class="row">
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/results_4.png" title="Fig. 4 Rescan Percentages" class="img-fluid " %}        
        </div>

        <div class="col-md-12">
            We also show that our adaptive method is still capable of locating and resolving model hallucination in
            scanning microscopy images. In the figure presented, we demonstrate that adaptively rescanning can resolve hallucinations
            in both confocal and experimental MPM samples at different rescanning percentages. In the MPM sample,
            rescanning at 80% allows for a 1.25 times savings in light-dose, while in the confocal sample, rescanning at 6%
            allows for a 16.7 savings in light-dose. It is important to note that optimal rescanning percentages are highly
            dependent on the sample itself. As shown, a sparse sample will need a lower percentage of pixels
            rescanned, while a dense sample will need a much higher rescanning percentage.    
        </div>
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/results_5.png" title="Fig. 5 Visual UQ Rescan" class="img-fluid "  %}        
        </div>
    </div>
    
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Conclusion</b>
    <p>
        We presented a method to utilize learned, distribution-free uncertainty quantification for multi-image denoising and proposed an adaptive acquisition technique based on the learned uncertainty. In this paper, we demonstrate that our method of uncertainty-driven adaptive acquisition works on experimental confocal, two-photon, and multiphoton microscopy systems, showing a potential 1-16 times decrease in total scanning time and light dose while successfully recovering fine structures. Our method can be adapted for different forms of scanning microscopy without explicit retraining or fine-tuning. Our network trained on FMD data can be used on different data after performing the conformal calibration step using a small calibration dataset. This is one of the advantages of conformal calibration - uncertainty predictions will still hold after calibrating for a different dataset without explicit retraining. All of the statistical guarantees will still hold; however, the size of the uncertainty bounds may increase since the network is not optimized for the data or imaging modality. We discuss this further in our supplement. 

        These speed and total light dose improvements are significant and demonstrate an important step towards faster and gentler scanning microscopy, which will enable the imaging of a new class of interesting samples and lead to new scientific insights and advances.  

    </p>
    <p>
       Furthermore, we demonstrate how deep learning methods for microscopy can be designed to be trustworthy by building in uncertainty quantification to provide error bars for each prediction. Our method successfully identified model hallucinations, which were reduced by taking more measurements or adaptively rescanning the most uncertain regions of the sample. Our method of quantifying uncertainty provides guarantees for the reliability of the prediction. Uncertainty quantification should become standard practice when using deep-learning techniques for scientific and medical imaging to reduce hallucinations and build confidence in image predictions. We believe that the distribution-free learned uncertainty quantification presented here is an attractive path toward this due to its ease of use, fast computational time, and statistical guarantees. 
    </p>
</div> -->


<div class="row" style="margin-top: 20px;">
    <div class="col-md-12">
        <b style="font-size: 24px;">Bibtex Citation</b>
        <div class="form-group col-md-12">
            <textarea id="bibtex" class="form-control" readonly>
            @article{ye2025qutcc,
            title={QUTCC: Quantile Uncertainty Training and Conformal Calibration for Imaging Inverse Problems},
            author={Ye, Cassandra Tong and Li, Shamus and King, Tyler and Monakhova, Kristina},
            journal={arXiv preprint arXiv:2507.14760},
            year={2025}
            }
            </textarea>
        </div>
    </div>
</div>





