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

<style>
.clickable-spot:hover {
    transform: scale(1.2);
    box-shadow: 0 0 15px rgba(255,255,255,0.8);
}

.distribution-active {
    animation: fadeIn 0.5s ease-in;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 20px;
    background-color: #fff;
}

.main-container {
    max-width: 1200px;
    margin: 0 auto;
}

/* Clear section separation */
.section {
    margin-bottom: 30px;
    padding: 40px 0;
    border-bottom: 2px solid #e9ecef;
    clear: both;
}

.section:last-child {
    border-bottom: none;
    margin-bottom: 40px;
}

.section-title {
    font-weight: bold;
    font-size: 28px;
    margin-bottom: 30px;
    color: #333;
    text-align: center;
}
.pinball-container {
    background-color: #f8f9fa;
    padding: 30px;
    border-radius: 12px;
    margin: 20px 0;
    border: 1px solid #e9ecef;
}

.pinball-content {
    display: flex;
    align-items: center;
    gap: 40px;
    flex-wrap: wrap;
}

.equation-side {
    flex: 1;
    min-width: 300px;
    text-align: center;
}

.interactive-side {
    flex: 1;
    min-width: 350px;
    text-align: center;
}

.function-definition {
    font-family: 'Times New Roman', serif;
    font-size: 20px;
    line-height: 2.2;
    margin-bottom: 20px;
}

.piecewise-container {
    display: inline-block;
    vertical-align: middle;
}

.piecewise-brace {
    font-size: 70px;
    line-height: 1;
    vertical-align: middle;
    margin-right: 15px;
}

.piecewise-cases {
    display: inline-block;
    text-align: left;
    vertical-align: middle;
}

.case-line {
    margin: 12px 0;
    white-space: nowrap;
    font-size: 18px;
}

.simple-slider {
    margin: 10px 0 20px 0;
}

.quantile-slider {
    width: 80%;
    margin: 10px 0;
    -webkit-appearance: none;
    appearance: none;
    height: 6px;
    border-radius: 3px;
    background: #ddd;
    outline: none;
}

.quantile-slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background: #007bff;
    cursor: pointer;
}

.quantile-slider::-moz-range-thumb {
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background: #007bff;
    cursor: pointer;
    border: none;
}

.quantile-value {
    font-size: 16px;
    font-weight: bold;
    color: #007bff;
    margin: 5px 0;
}

.chart-container {
    width: 100%;
    height: 300px;
    border: 1px solid #ddd;
    border-radius: 8px;
    background-color: #fff;
    margin: 10px 0;
}

.equation-label {
    font-size: 16px;
    color: #555;
    margin-top: 15px;
    font-style: italic;
}

.text-content {
    text-align: justify;
}

/* Method section styles */
.method-container {
    background-color: #f8f9fa;
    padding: 30px;
    border-radius: 12px;
    margin: 20px 0;
    border: 1px solid #e9ecef;
}

.method-image-container {
    text-align: center;
    margin: 20px 0;
    min-height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.method-image {
    max-width: 100%;
    max-height: 350px;
    border-radius: 2px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    transition: opacity 0.3s ease;
}

.method-buttons {
    display: flex;
    justify-content: center;
    gap: 15px;
    margin: 20px 0;
    flex-wrap: wrap;
}

.method-btn {
    padding: 12px 24px;
    border: 2px solid #007bff;
    background-color: #fff;
    color: #007bff;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    transition: all 0.3s ease;
    min-width: 120px;
}

.method-btn:hover {
    background-color: #e3f2fd;
    transform: translateY(-2px);
}

.method-btn.active {
    background-color: #007bff;
    color: #fff;
    box-shadow: 0 4px 12px rgba(0,123,255,0.3);
}

.method-caption {
    margin-top: 15px;
    font-size: 16px;
    color: #555;
    line-height: 1.6;
    max-width: 800px;
    margin-left: auto;
    margin-right: auto;
    text-align: left;
    padding: 0 20px;
}

.stage-title {
    font-size: 18px;
    font-weight: bold;
    color: #007bff;
    margin-bottom: 10px;
}

/* Results section styles */
.under-construction {
    background: linear-gradient(45deg, #fff3cd, #ffeaa7);
    border: 2px dashed #e67e22;
    border-radius: 8px;
    padding: 20px;
    text-align: center;
    font-weight: bold;
    color: #d35400;
    margin: 20px 0;
}

.results-section {
    margin-top: 20px;
}

.results-title {
    font-weight: bold;
    font-size: 24px;
    margin-bottom: 30px;
    display: block;
}

.content-text {
    font-size: 16px;
    line-height: 1.6;
    margin: 20px 0;
}

.figure-container {
    max-width: 300px;
    margin-bottom: 20px;
}

.figure-container img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.caption {
    text-align: left;
    font-size: 14px;
    margin-top: 8px;
    color: #666;
    font-style: italic;
}

/* Mobile responsive styles */
@media (max-width: 768px) {
    .pinball-content {
        flex-direction: column;
        gap: 30px;
    }
    
    .equation-side,
    .interactive-side {
        min-width: 100%;
    }
    
    .piecewise-brace {
        font-size: 50px;
    }
    
    .function-definition {
        font-size: 18px;
    }
    
    .case-line {
        font-size: 16px;
    }

    .method-buttons {
        flex-direction: column;
        align-items: center;
    }

    .method-btn {
        width: 200px;
    }

    .figure-container {
        max-width: 100%;
        margin: 20px 0;
    }
}
</style>
<div class="section" style="margin-top: 60px;">
    <h2 style="font-weight: bold; font-size: 24px; margin-bottom: 20px;">Abstract</h2>
    
    <div class="row">
        <div class="col-md-12">
            Deep learning models often hallucinate, producing realistic artifacts that are not truly present in the sample. This can have dire consequences for scientific and medical inverse problems, such as MRI and microscopy denoising, where accuracy is more important than perceptual quality. Uncertainty quantification techniques, such as conformal prediction, can pinpoint outliers and provide guarantees for image regression tasks, improving reliability. However, existing methods utilize a linear constant scaling factor to calibrate uncertainty bounds, resulting in larger, less informative bounds. We propose <strong>QUTCC</strong>, a quantile uncertainty training and calibration technique that enables nonlinear, non-uniform scaling of quantile predictions to enable tighter uncertainty estimates. Using a U-Net architecture with a quantile embedding, QUTCC enables the prediction of the full conditional distribution of quantiles for the imaging task. During calibration, QUTCC generates uncertainty bounds by iteratively querying the network for upper and lower quantiles, progressively refining the bounds to obtain a tighter interval that captures the desired coverage. We evaluate our method on several denoising tasks as well as compressive MRI reconstruction. <strong>Our method successfully pinpoints hallucinations in image estimates and consistently achieves tighter uncertainty intervals than prior methods while maintaining the same statistical coverage</strong>. 
        </div>
    </div>
</div>

<div class="section" style="margin-top: 60px;">
    <h2 style="font-weight: bold; font-size: 24px; margin-bottom: 20px;">Quantile Regression: Pinball Loss</h2>
    
    <div class="text-content">
        <p>
            Quantile regression is a general approach to estimate the conditional quantiles of a target distribution rather than the mean of a response variable. This is often accomplished by leveraging an asymmetric loss function, called pinball loss, tailored to the specified quantile level.
        </p>
    </div>
    
    <div class="pinball-container">
        <div class="pinball-content">
            <div class="equation-side">
                <div class="function-definition">
                    L<sub>q</sub>(x, x̂) = 
                    <div class="piecewise-container">
                        <span class="piecewise-brace">{</span>
                        <div class="piecewise-cases">
                            <div class="case-line">q * |x - x̂|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if x - x̂ ≥ 0 </div>
                            <div class="case-line">(1 - q) * |x - x̂|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="interactive-side">
                <canvas id="pinball-chart" class="chart-container" width="400" height="300"></canvas>
                <div class="simple-slider">
                    <div class="quantile-value">q = <span id="quantile-display">0.35</span></div>
                    <input type="range" id="quantile-slider" class="quantile-slider" 
                           min="0.01" max="0.99" value="0.5" step="0.01">
                </div>
            </div>
        </div>
    </div>
    
    <div class="text-content">
        <p>
            where q ∈ (0,1) is the desired quantile level, x is the true value, and x̂ is the predicted value. This asymmetric penalty ensures that overestimation and underestimation are weighted differently according to the target quantile. For example, if q = 0.1, then overestimates will be penalized heavier than underestimates.
        </p>

        <p>
            Pinball loss has been used in the past 
            <a href="https://arxiv.org/abs/2202.05265" target="_blank" style="color: #0066cc; text-decoration: none;">to predict a fixed set of upper and lower confidence bounds</a> (Im2Im-UQ). 
            In contrast, our work investigates learning the full spectrum of quantiles, commonly referred to as 
            <a href="https://library.seg.org/doi/10.1190/tle44020133.1#:~:text=The%20simultaneous%20quantile%20regression%20method,method%20on%20synthetic%20Kimberlina%20data." target="_blank" style="color: #0066cc; text-decoration: none;">
                <strong>Simultaneous Quantile Regression (SQR)</strong>
            </a>, for inverse image tasks.
        </p>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <b style="font-weight: bold; font-size: 24px; margin-bottom: 20px;">Our Method: QUTCC</b>
    <div class="row">
        <div class="col-md-12">
            <p>
                We propose <strong>QUTCC</strong> (pronounced: CUTESY), short for <strong>Quantile Uncertainty Training and Conformal Calibration</strong>, a novel method for simultaneous quantile prediction and conformal calibration that enables efficient and accurate uncertainty quantification for imaging inverse problems. QUTCC uses a single neural network to estimate a distribution of quantiles. During the conformal calibration step, QUTCC applies a non-uniform, nonlinear scaling to the uncertainty bounds, compared to constant scaling used by prior methods. This results in smaller and potentially more informative uncertainty intervals. Additionally, because all quantiles are learned during training, QUTCC can query the full quantile range at inference time to construct a pixel-wise estimate of the underlying probability distribution.
            </p>
        </div>
    </div>
    
    <div class="method-container">
        <div class="method-image-container">
            <img id="method-image" class="method-image" src="https://raw.githubusercontent.com/cassandra-t-ye/cassandra-t-ye.github.io/master/assets/img/proj_2_qutcc/fig_1_training_gif.gif" alt="Training">
            
            <div class="method-caption">
                <div class="stage-title">Training</div>
                <div>During training, QUTCC uses a U-Net architecture with quantile embeddings to learn the full spectrum of quantiles simultaneously. The network is trained using the pinball loss function, which enables it to predict different quantile levels of the conditional distribution for each pixel in the image reconstruction task. This simultaneous quantile regression approach allows the model to capture the uncertainty inherent in the inverse problem.</div>
            </div>
        </div>

        <div class="method-buttons">
            <button class="method-btn active" data-stage="training">Training</button>
            <button class="method-btn" data-stage="calibration">Calibration</button>
            <button class="method-btn" data-stage="inference">Inference</button>
        </div>
    </div>
</div>


<!-- <div class="section results-section">
    <b class="results-title">Results</b> -->
<div class="section results-section" style="margin-top: 20px;">
    <b class="results-title">Results</b>
    <div class="row">
        <div class="col-md-12 mt-3">
            <div style="text-align: left; padding: 20px; background-color: #f8f9fa; border-radius: 8px;">
                SOMETHING ABOUT HALLUCINATIONS
            </div>
        </div>
        <div class="col-12 mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/hallucination_gif.gif" title="" class="img-fluid" width="700px" height="auto" %}        
            <div class="caption" style="text-align: left;">
                <b>FIG CAPTION</b>
            </div>
        </div>
        <div class="col-md-12 mt-3">
            <div style="text-align: left; padding: 20px; background-color: #f8f9fa; border-radius: 8px;">
                To evaluate QUTCC, we test our approach against Im2Im-UQ in four separate imaging tasks- <b>MRI</b>, <b>Gaussian</b>, <b>Poisson</b>, and <b>Real denoising</b>. We compare the predictive interval sizes of Im2Im-Deep and QUTCC across all four inverse tasks. QUTCC consistently produces narrower uncertainty intervals.  By achieving smaller interval lengths while exhibiting comparable risk, QUTCC demonstrates that its uncertainty quantification is both more precise and well-calibrated, effectively capturing predictive confidence without sacrificing coverage.
            </div>
        </div>
        <div class="col-12 mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/fig_2_violin_plot.png" title="" class="img-fluid" width="700px" height="auto" %}        
            <div class="caption" style="text-align: left;">
                <b>FIG CAPTION</b>
            </div>
        </div>
        
    </div>
</div>

<div class="section results-section" style="margin-top: 20px;">
    <b class="results-title">Pixel-wise Probability Density Functions</b>
    <div class="row">
        <div class="col-md-12 mt-3">
            <div style="text-align: left; padding: 20px; background-color: #f8f9fa; border-radius: 8px;">
                One of the key advantages of QUTCC is its ability to predict the full spectrum of quantiles, enabling the reconstruction of pixel-wise probability density functions. By querying the trained network across the entire quantile range q ∈ (0, 1), we can estimate the underlying conditional distribution for each pixel in the reconstructed image. This provides rich uncertainty information that goes beyond simple confidence intervals, revealing the shape and characteristics of the predictive distribution at each spatial location.
            </div>
        </div> 
        <!-- Interactive Visualization Container -->
        <div class="col-12 mt-3" style="text-align: center;">
            <div class="pdf-visualization-container" style="background-color: #fff; border: 1px solid #ddd; border-radius: 12px; padding: 20px; margin: 20px 0;">  
                <!-- Microscope image with clickable spots -->
                <div class="image-container" style="position: relative; display: inline-block; margin-bottom: 20px;">
                    {% include figure.html path="assets/img/proj_2_qutcc/pdf_microscope.png" class="img-fluid" style="width: 600px; height: 150px; object-fit: cover;" %} 
                    <div class="clickable-spot spot-blue" onclick="showDistribution('right-skewed')" 
                        style="position: absolute; top: 21.5%; left: 41%; width: 20px; height: 20px; border: 3px solid #4A90E2; border-radius: 50%; cursor: pointer; background: rgba(74, 144, 226, 0.4); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold; transition: all 0.3s ease; z-index: 10;"
                        title="Click to view right-skewed distribution">
                        1
                    </div>
                    <div class="clickable-spot spot-green" onclick="showDistribution('normal')" 
                        style="position: absolute; top: 36%; left: 18%; width: 20px; height: 20px; border: 3px solid #7ED321; border-radius: 50%; cursor: pointer; background: rgba(126, 211, 33, 0.4); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold; transition: all 0.3s ease; z-index: 10;"
                        title="Click to view normal distribution">
                        2
                    </div>
                    <div class="clickable-spot spot-red" onclick="showDistribution('left-skewed')" 
                        style="position: absolute; top: 42.5%; left: 40.5%; width: 20px; height: 20px; border: 3px solid #D0021B; border-radius: 50%; cursor: pointer; background: rgba(208, 2, 27, 0.4); display: flex; align-items: center; justify-content: center; color: white; font-weight: bold; transition: all 0.3s ease; z-index: 10;"
                        title="Click to view left-skewed distribution">
                        3
                    </div>
                </div>
                <!-- Instructions -->
                <div style="margin: 20px 0; padding: 15px; background: #e3f2fd; border-radius: 8px; color: #1976d2; text-align: left;">
                    <strong>Interactive Demo:</strong> Click on the different colored regions to see different QUTCC pixel-wise PDFs predictions
                </div>
                <!-- Distribution display area -->
                <div class="distribution-display" style="margin-top: 30px; min-height: 200px;">
                    <div id="distribution-info" style="display: none; text-align: center; padding: 20px;">
                        <h4 id="dist-title" style="color: #333; margin-bottom: 15px;"></h4>
                        <div id="dist-description" style="font-size: 14px; line-height: 1.6; color: #555; max-width: 600px; margin: 0 auto;"></div>
                        <!-- Distribution visualization -->
                        <div id="dist-visualization" style="margin: 20px 0; height: 150px; display: flex; align-items: left; justify-content: left; border-radius: 3px;">
                            <!-- Images will be loaded here by JavaScript -->
                        </div>
                        <div id="dist-stats" style="margin-top: 15px; font-size: 14px; color: #777;"></div>
                    </div>
                    <div id="default-message" style="text-align: center; padding: 40px; color: #888;">
                    </div>
                </div>
            </div>
        </div>
        <div class="col-md-12 mt-3">
            <div style="text-align: left; padding: 20px; background-color: #f8f9fa; border-radius: 8px;">
                The ability to visualize these pixel-wise distributions provides valuable insights into the reconstruction process. <strong>Right-skewed distributions</strong> often indicate regions where the model is more confident about lower intensity values but uncertain about potential high-intensity artifacts. <strong>Normal distributions</strong> suggest well-behaved, symmetric uncertainty around the predicted value. <strong>Left-skewed distributions</strong> may indicate areas where the model expects higher intensities but has some uncertainty about potential underestimation. This granular uncertainty information enables practitioners to identify not just <em>where</em> the model is uncertain, but <em>how</em> it is uncertain, facilitating more informed decision-making in critical applications.
            </div>
        </div>
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <h2 style="font-weight: bold; font-size: 24px; margin-bottom: 20px;">Conclusion</h2>  
    <div class="row">
        <div class="col-md-12">
            We propose QUTCC, a <b>new uncertainty quantification method for imaging inverse problems</b> that can achieve <b>tighter uncertainty estimates</b> than previous methods while maintaining the same statistical coverage.  QUTCC accomplishes this by training a U-Net with a quantile embedding simultaneously on q ∈ (0, 1) quantiles and then dynamically adjusting its quantile bound predictions during calibration until the desired risk is satisfied. Our method exhibited tighter uncertainty intervals, on average, while still pinpointing model hallucinations and regions of high error. This can be attributed to our model applying a nonlinear and asymmetrical scaling to its pixel-wise uncertainty predictions. While quantifying model uncertainty remains a significant open challenge in the field of deep learning, we believe that QUTCC offers a simple, yet robust method of uncertainty quantification for imaging inverse problems and image-to-image regression tasks.
        </div>
    </div>
</div>


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

<script>
function showDistribution(type) {
    const distributions = {
        'right-skewed': {
            title: 'Right-Skewed Distribution',
            description: 'This pixel exhibits a right-skewed probability distribution, indicating higher confidence in lower intensity values with a tail extending toward higher intensities. This pattern often occurs in regions where the model is certain about the baseline but uncertain about potential bright artifacts or noise.',
            // stats: 'Mean: 0.24 | Median: 0.19 | Skewness: +1.2',
            image: 'https://raw.githubusercontent.com/cassandra-t-ye/cassandra-t-ye.github.io/master/assets/img/proj_2_qutcc/right_skewed_pdf.png'
        },
        'normal': {
            title: 'Normal Distribution', 
            description: 'This pixel shows a symmetric, normal distribution centered around the predicted intensity value. This indicates well-calibrated uncertainty with equal probability of over- and under-estimation, typical of regions with good signal-to-noise ratio.',
            // stats: 'Mean: 0.51 | Median: 0.51 | Skewness: 0.0',
            image: 'https://raw.githubusercontent.com/cassandra-t-ye/cassandra-t-ye.github.io/master/assets/img/proj_2_qutcc/normal_pdf.png'
        },
        'left-skewed': {
            title: 'Left-Skewed Distribution',
            description: 'This pixel demonstrates a left-skewed distribution, suggesting the model expects higher intensity values but has some uncertainty about potential underestimation. This pattern may indicate regions where the reconstruction tends to be conservative.',
            // stats: 'Mean: 0.68 | Median: 0.72 | Skewness: -0.8',
            image: 'https://raw.githubusercontent.com/cassandra-t-ye/cassandra-t-ye.github.io/master/assets/img/proj_2_qutcc/left_skewed_pdf.png'
        }
    };
    
    const distInfo = distributions[type];
    
    // Hide default message
    document.getElementById('default-message').style.display = 'none';
    
    // Show and update distribution info
    const infoDiv = document.getElementById('distribution-info');
    infoDiv.style.display = 'block';
    infoDiv.className = 'distribution-active';
    
    document.getElementById('dist-title').textContent = distInfo.title;
    document.getElementById('dist-description').textContent = distInfo.description;
    document.getElementById('dist-stats').textContent = distInfo.stats;
    
    // Add visual feedback to clicked spot
    document.querySelectorAll('.clickable-spot').forEach(spot => {
        spot.style.transform = 'scale(1)';
        spot.style.boxShadow = 'none';
    });
    
    event.target.style.transform = 'scale(1.3)';
    event.target.style.boxShadow = '0 0 20px rgba(255,255,255,0.9)';
    
    setTimeout(() => {
        event.target.style.transform = 'scale(1)';
        event.target.style.boxShadow = 'none';
    }, 300);
}
</script>

<script type="text/javascript">
document.addEventListener('DOMContentLoaded', function() {
    var canvas = document.getElementById('pinball-chart');
    if (!canvas || !canvas.getContext) {
        return;
    }
    
    var slider = document.getElementById('quantile-slider');
    var display = document.getElementById('quantile-display');
    var ctx = canvas.getContext('2d');
    
    canvas.width = 400;
    canvas.height = 300;
    
    function drawPinballLoss(q) {
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        const margin = 40;
        const width = canvas.width - 2 * margin;
        const height = canvas.height - 2 * margin;

        // Draw axes
        ctx.strokeStyle = '#333';
        ctx.lineWidth = 2;
        ctx.beginPath();
        ctx.moveTo(margin, canvas.height - margin); // X-axis
        ctx.lineTo(canvas.width - margin, canvas.height - margin);
        ctx.moveTo(margin, margin); // Y-axis
        ctx.lineTo(margin, canvas.height - margin);
        ctx.stroke();

        // Axis labels
        ctx.fillStyle = '#333';
        ctx.font = '12px Arial';
        ctx.textAlign = 'center';
        ctx.fillText('Ground Truth - Predicted', canvas.width / 2, canvas.height - 10);
        ctx.save();
        ctx.translate(15, canvas.height / 2);
        ctx.rotate(-Math.PI / 2);
        ctx.fillText('Pinball Loss', 0, 0);
        ctx.restore();

        // Function scaling
        const uMin = -5, uMax = 5;
        const uToPx = (u) => margin + ((u - uMin) / (uMax - uMin)) * width;
        const maxLoss = Math.max(q * Math.abs(uMax), (1 - q) * Math.abs(uMin));
        const lossToPy = (loss) => (canvas.height - margin) - (loss / maxLoss) * (height * 0.9);

        // Pinball loss function from formula
        function pinballLoss(u, q) {
            const absU = Math.abs(u);
            if (u >= 0) {
                return q * absU;
            } else {
                return (1 - q) * absU;
            }
        }

        // Plot curve
        ctx.strokeStyle = '#007bff';
        ctx.lineWidth = 2;
        ctx.beginPath();
        const steps = 300;
        for (let i = 0; i <= steps; i++) {
            const u = uMin + i * (uMax - uMin) / steps;
            const loss = pinballLoss(u, q);
            const px = uToPx(u);
            const py = lossToPy(loss);
            
            if (i === 0) {
                ctx.moveTo(px, py);
            } else {
                ctx.lineTo(px, py);
            }
        }
        ctx.stroke();

        // Show q value
        ctx.fillStyle = '#007bff';
        ctx.font = 'bold 16px Arial';
        ctx.textAlign = 'left';
        ctx.fillText('q = ' + (1 - q).toFixed(2), margin + 10, margin + 20);
    }

    function updateVisualization() {
        var q = parseFloat(slider.value);
        display.textContent = (1-q).toFixed(2);
        drawPinballLoss(q);
    }

    updateVisualization();
    slider.addEventListener('input', updateVisualization);

    // Method stage switching functionality
    const methodButtons = document.querySelectorAll('.method-btn');
    const methodImage = document.getElementById('method-image');
    const methodCaption = document.querySelector('.method-caption');
    const stageData = {
        training: {
            image: "https://raw.githubusercontent.com/cassandra-t-ye/cassandra-t-ye.github.io/master/assets/img/proj_2_qutcc/fig_1_training_gif.gif",
            title: "Training",
            caption: "During training, a neural network with a quantile embedding predicts an image as a function of the measurement and quantile, q. The quantile embedding is randomly sampled (q ∈ (0, 1)) and the value of q determines the asymmetry of the pinball loss, enabling the model to learn a range of conditional quantiles."
        },
        calibration: {
            image: "https://raw.githubusercontent.com/cassandra-t-ye/cassandra-t-ye.github.io/master/assets/img/proj_2_qutcc/fig_1_calibration_gif.gif",
            title: "Calibration", 
            caption: "During calibration, the predictive bounds (q_lower, q_upper) are iteratively adjusted on a held-out dataset to satisfy the desired miscoverage level α."
        },
        inference: {
            image: "https://raw.githubusercontent.com/cassandra-t-ye/cassandra-t-ye.github.io/master/assets/img/proj_2_qutcc/fig_1_inference_gif.gif",
            title: "Inference",
            caption: "At test time, the model is queried with q_lower, q_0.5, and q_upper to produce the mean prediction and a corresponding pixel-wise uncertainty map. Querying the full range of quantile values enables the prediction of the pixel-wise distribution."
        }
    };

    methodButtons.forEach(button => {
        button.addEventListener('click', function() {
            // Remove active class from all buttons
            methodButtons.forEach(btn => btn.classList.remove('active'));
            
            // Add active class to clicked button
            this.classList.add('active');
            
            // Get stage data
            const stage = this.dataset.stage;
            const data = stageData[stage];
            
            // Update image and caption with fade effect
            methodImage.style.opacity = '0.3';
            setTimeout(() => {
                methodImage.src = data.image;
                methodImage.alt = data.title;


                methodCaption.innerHTML = `
                    <div class="stage-title">${data.title}</div>
                    <div>${data.caption}</div>
                `;
                
                methodImage.style.opacity = '1';
            }, 150);
        });
    });
});
</script>