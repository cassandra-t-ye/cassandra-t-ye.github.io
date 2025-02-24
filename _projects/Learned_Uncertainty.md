---
layout: page
title: Learned, Uncertainty-driven Adaptive Acquisition for Photon-Efficient Multiphoton Microscopy
description: 
img: assets/img/proj_1/cover_img.png
importance: 1
related_publications: ye2023learned
---
[Cassandra Tong Ye](https://kristinamonakhova.com/), Jiashu Han, [Kunzan Liu](https://liukunzan.github.io/), [Anastasios Angelopoulos](https://people.eecs.berkeley.edu/~angelopoulos/), [Linda Griffith](https://lgglab.mit.edu/), [Kristina Monakhova](http://kristinamonakhova.com/), [Sixian You](https://sixianyou.mit.edu/)

<div style="text-align: center;">
  <div style="display: inline-block;">
    <a href="https://github.com/cassandra-t-ye/Learned_Uncertainty_Quantification" style="display: block; text-align: center;">
        <img src="/assets/img/proj_1/github.png" alt="Github Repo" style="width: 70px; height: auto; margin-right: 20px; margin: 0 auto;">
    </a>
    <div class="caption" style="text-align: center;">Github Repo</div>
  </div>
  <div style="display: inline-block;">
    <a href="https://arxiv.org/abs/2310.16102" style="display: block; text-align: center;">
        <img src="/assets/img/proj_1/paper_front_page.png" alt="Arxiv Paper" style="width: 70px; height: auto; margin-left: 20px; margin: 0 auto;">
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
            Scanning microscopy systems, such as confocal and multiphoton microscopy, are powerful imaging tools for probing deep into biological tissue. However, scanning systems have an inherent trade-off between acquisition time, field of view, phototoxicity, and image quality, often resulting in noisy measurements when fast, large field of view, and/or gentle imaging is needed. Deep learning could be used to denoise noisy microscopy measurements, but these algorithms can be prone to hallucination, which can be disastrous for medical and scientific applications. We propose a method to simultaneously denoise and predict pixel-wise uncertainty for scanning microscopy systems, improving algorithm trustworthiness and providing statistical guarantees for deep learning predictions. Furthermore, we propose to leverage this learned, pixel-wise uncertainty to drive an adaptive acquisition technique that rescans only the most uncertain regions of a sample, saving time and reducing the total light dose to the sample. We demonstrate our method on experimental confocal and multiphoton microscopy systems, showing that our uncertainty maps can pinpoint hallucinations in the deep learned predictions. Finally, with our adaptive acquisition technique, we demonstrate up to 16 times reduction in acquisition time and total light dose while successfully recovering fine features in the sample and reducing hallucinations. We are the first to demonstrate distribution-free uncertainty quantification for a denoising task with real experimental data and the first to propose adaptive acquisition based on reconstruction uncertainty. 
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Intro to Scanning</b>
    <div class="row">
        <div class="col-md-6">
            Many popular microscopy modalities leverage scanning to probe deep into biological tissues; they focus light
            to a small region of a sample and collect light only from that region. By scanning light to different regions
            of the sample, they build up three-dimensional images of the sample often one point at a time. Scanning
            confocal microscopes have been widely adopted for medical and scientific applications due to their ability
            to recover three-dimensional structures by optical sectioning. Two-photon and multiphoton microscopy
            leverage non-linear excitation to probe even deeper into thick, scattering tissue. These systems are often used
            by neuroscientists to measure calcium dynamics in deep scattering mouse brains, as well as to characterize
            multicellular dynamics in immunology and cancer studies. In addition, label-free multiphoton microscopy
            enables minimally invasive imaging of biological structures in living and unlabeled biosystems, such as collagen
            fibers, immune cells, endothelial cells, and extracellular vesicles, through second harmonic generation
            (SHG), third harmonic generation (THG), and two-photon and three-photon autofluorescence (2PAF,
            3PAF). This has become an increasingly popular tool for tissue and cell microscopy in neuroscience,
            immunology, and cancer research.
            To provide a minimally perturbative window into the tissue architecture and cell dynamics of intact biosystems,
            the next advances in scanning microscopy require deeper, faster, and gentler imaging of thick and living
            samples. For scanning microscopy systems, there is an inherent trade-off between acquisition time, field of
            view, phototoxicity, and image quality, often resulting in noisy measurements when fast, large field of view, deep,
            and/or gentle imaging is needed. Noisy images can be challenging to interpret, and fine structures within the images can be obscured by noise. 

        </div>

        <div class="col-md-6">
            {% include figure.html path="assets/img/proj_1/mpm.png" title="Multiphoton Microscopy" class="img-fluid " style="width: 180px; height: auto;"%}
            <div class="caption" style="text-align: left;">
                Multiphoton microscopy (MPM), a type of scanning microscopy, is a powerful imaging tool that has been a critical enabler for live tissue imaging.
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
    <b style="font-size: 24px;">Denoising Results</b>
    <div class="row">
        <div class="col-md-12">
            We evaluated our denoising and uncertainty prediction on an experimental dataset of confocal and two-photon
            measurements (FMD dataset) as well as a custom multiphoton dataset (MPM dataset). First, we test our denoiser’s performance as a function of the number of noisy measurements. To do this, we vary the input to the network, feeding in 1-20 unique, non-moving, noisy measurements. Each measurement has a different instance of noise, so intuitively, with more measurements, the denoising prediction should improve. In the image below, we show the predicted denoised images and uncertainty maps for samples from the FMD dataset. Here, we can see that as the number of measurements increases, the network’s predicted uncertainty
            decreases, and concurrently, the denoised predictions become sharper and closer to the ground truth. In the zoomed in portion of the image, we demonstrate a hallucination that was observed in the first denoised iteration (indicated by high uncertainty), which is resolved by the tenth denoised iteration. 
        </div>
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_1/results_2.png" title="Fig. 2 Denoising Results for FMD Samples" class="img-fluid "  %}        
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
    <div class="row">
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_1/results_4.png" title="Fig. 4 Rescan Percentages" class="img-fluid " %}        
        </div>

        <div class="col-md-12">
            To evaluate our uncertainty-informed adaptive acquisition, we compared the denoising and
            uncertainty performance for various different uncertainty thresholds. After a measurement is
            denoised, a new acquisition pattern is chosen based on a user-defined uncertainty threshold. This
            is repeated for four subsequent acquisitions, each time acquiring new measurements only in the
            areas of the sample that are too uncertain (i.e higher than the uncertainty threshold). Figure 5
            shows the results of this sweep for a representative sample from our test set. Here, we see that
            when the uncertainty threshold is lower (more pixels are rescanned), performance (based on
            MSE, SSIM, and average uncertainty) is better, but the total scanning duration is higher. When
            the threshold is higher and fewer than 40% of the pixels are rescanned, the performance drops
            and fewer features are successfully recovered. For this sample, we found that an uncertainty
            threshold corresponding to rescanning 57% of the sample minimizes total time and light dose
            while maintaining denoising performance and successfully recovering fine features within the
            sample.    
        </div>
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_1/results_5.png" title="Fig. 5 Visual UQ Rescan" class="img-fluid "  %}        
        </div>
    </div>
    
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-size: 24px;">Conclusion</b>
    <p>
        We presented a method to utilize learned, distribution-free uncertainty quantification for multiimage denoising and proposed an adaptive acquisition technique based on the learned uncertainty.
        We demonstrated both methods on experimental MPM SHG measurements, showing a 120×
        decrease in total scanning time and a 120× decrease in total light dose while successfully
        recovering fine structures and outperforming existing denoising benchmarks. These speed and
        total light dose improvements are significant and demonstrate an important step towards faster
        and gentler MPM, which will enable the imaging of a new class of interesting samples and lead
        to new scientific insights and advances.
    </p>
    <p>
        Furthermore, we demonstrate how deep learning methods for microscopy can be designed to
        be trustworthy by building in uncertainty quantification to provide error bars for each prediction.
        To the best of our knowledge, we are the first to utilize distribution-free uncertainty quantification
        for a denoising task. Uncertainty quantification should become standard practice when using
        deep-learning techniques for scientific and medical imaging to reduce hallucinations and build
        confidence in image predictions. <b>We believe that the distribution-free learned uncertainty
        quantification presented here is an attractive path toward this due to its ease of use, fast
        computational time, and statistical guarantees.</b>
    </p>
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





