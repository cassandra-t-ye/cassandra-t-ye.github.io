---
layout: page
title: "QUTCC🤗: Quantile Uncertainty Training and Conformal Calibration for Imaging Inverse Problems"
description: 
img: 
importance: 1
related_publications: ye2026qutcc
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

.fig5 { text-align: center; }
.fig5-img { width: 100%; max-width: 1000px; display: block; margin: 12px auto 0; }
.pdf-demo { margin-top: 0; }
.pdf-demo-grid { display: grid; grid-template-columns: minmax(0, 400px) minmax(0, 1fr); gap: 32px; align-items: start; }
.pdf-demo-left { text-align: center; }
.pdf-crop { position: relative; width: 100%; aspect-ratio: 1 / 1; }
.pdf-crop img { width: 100%; height: 100%; display: block; border-radius: 4px; }
/* Each spot is centered on its drawn circle and sized to match it (54 px of 640) */
.pdf-crop .clickable-spot { position: absolute; width: 8.5%; aspect-ratio: 1 / 1; transform: translate(-50%, -50%);
    border: 3px solid var(--spot); border-radius: 50%; background: transparent; padding: 0; cursor: pointer;
    color: transparent; font-size: 0; transition: box-shadow 0.2s ease; }
.pdf-crop .clickable-spot:hover { transform: translate(-50%, -50%) scale(1.25); }
.pdf-crop .clickable-spot.selected { box-shadow: 0 0 0 3px #fff, 0 0 12px 4px var(--spot); }
.pdf-demo-right #dist-title { color: #333; margin: 0 0 8px; text-align: center; font-size: 1.2rem; font-weight: bold; }
.pdf-demo-right .pdf-chart { width: 100%; height: auto; display: block; }
.pdf-demo-right #dist-description { font-size: 16px; line-height: 1.6; color: #555; margin-top: 8px; text-align: center; min-height: 4.8em; }
@media (max-width: 767px) { .pdf-demo-grid { grid-template-columns: 1fr; } .pdf-crop { max-width: 400px; margin: 0 auto; } }

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
    background: var(--q-color, #007bff);
    cursor: pointer;
}

.quantile-slider::-moz-range-thumb {
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background: var(--q-color, #007bff);
    cursor: pointer;
    border: none;
}

.quantile-value {
    font-size: 18px;
    font-weight: bold;
    color: var(--q-color, #007bff);
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
    font-size: 18px;
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
    font-size: 18px;
    color: #555;
    line-height: 1.6;
    max-width: 800px;
    margin-left: auto;
    margin-right: auto;
    text-align: left;
    padding: 0 20px;
}

.stage-title {
    font-size: 20px;
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
    font-size: 28px;
    margin-bottom: 15px;
    display: block;
}

.content-text {
    font-size: 18px;
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
    font-size: 16px;
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
/* Method figure: fixed-size area, all GIFs same width, caption as wide as the GIF */
.method-stage-area { margin: 10px 0; }
.method-stack { display: grid; }
.method-stack > * { grid-area: 1 / 1; visibility: hidden; opacity: 0; transition: opacity 0.25s ease; }
.method-stack > .active { visibility: visible; opacity: 1; }
.method-image-stack { align-items: start; justify-items: start; }
.method-stack .method-image { width: 100%; height: auto; max-height: none; display: block; }
.method-stack .method-caption { max-width: none; margin: 15px 0 0; padding: 0; }

/* Table 1 viewer */
.t1-buttons { display: flex; justify-content: center; flex-wrap: wrap; gap: 10px; margin-bottom: 14px; }
.t1-btn { padding: 8px 18px; border: 2px solid #007bff; background: #fff; color: #007bff; border-radius: 8px;
    cursor: pointer; font-size: 16px; font-weight: bold; transition: all 0.2s ease; }
.t1-btn:hover { background: #e3f2fd; }
.t1-btn.active { background: #007bff; color: #fff; }
.t1-caption { text-align: center; color: #52514e; font-size: 1rem; margin-bottom: 6px; }
.t1-legend { display: flex; flex-wrap: wrap; justify-content: center; gap: 4px 18px; font-size: 14px; color: #52514e; margin-bottom: 4px; }
.t1-legend-item { display: inline-flex; align-items: center; gap: 6px; cursor: default; }
.t1-legend-item.is-qutcc { color: #0b0b0b; font-weight: bold; }
.t1-legend-group { color: #8a8984; font-size: 13px; }
.t1-chart { position: relative; }
.t1-chart svg { width: 100%; height: auto; display: block; overflow: visible; }
.t1-tip { position: absolute; pointer-events: none; background: #fff; border: 1px solid #ddd; border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.12); padding: 8px 10px; font-size: 13px; color: #0b0b0b; white-space: nowrap; z-index: 5; }
.t1-tip .t1-tip-head { font-weight: bold; margin-bottom: 4px; }
.t1-tip .t1-tip-row { display: flex; justify-content: space-between; gap: 14px; color: #52514e; }
.t1-tip .t1-tip-row.is-qutcc { color: #1f3be8; font-weight: bold; }
.t1-dot { display: inline-block; width: 8px; height: 8px; border-radius: 50%; margin-right: 6px; }
.t1-groups { display: flex; justify-content: center; gap: 8px; margin-bottom: 12px; }
.t1-group-btn { padding: 4px 14px; border: 1.5px solid #000; background: #fff; color: #000; border-radius: 999px;
    cursor: pointer; font-size: 14px; transition: all 0.2s ease; }
.t1-group-btn:hover { background: #f0f0f0; }
.t1-group-btn.active { background: #000; border-color: #000; color: #fff; }
.t1-legend-item.is-off { opacity: 0.35; }
.t1-note { text-align: center; font-size: 0.85rem; color: #6b6a66; margin-top: 8px; }

/* Wider layout for this project page only */
.container { max-width: 1200px; }

/* Larger base text for the whole project page */
.post article { font-size: 1.15rem; }
.post article strong, .post article b { font-weight: 700; }

/* Quantile regression section */
.qr-lead { font-size: 1.2rem; line-height: 1.7; margin-bottom: 0.75rem; }
.qr-points { padding-left: 1.3rem; margin: 0.5rem 0 0; }
.qr-points li { margin-bottom: 0.55rem; line-height: 1.6; }
.qr-points a { color: #0066cc; }
.qr-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; margin: 20px 0; }
.qr-card { background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 12px; padding: 20px 24px; }
.qr-card h3 { font-size: 1.2rem; font-weight: bold; color: #333; margin: 0 0 0.6rem; }
.qr-contrast { border-left: 4px solid #007bff; }
.slider-hint { font-size: 15px; color: #777; font-style: italic; }
.qr-compact { padding: 18px 20px; }
.qr-equation { display: flex; align-items: center; justify-content: center;
    font-family: 'Times New Roman', serif; font-size: 20px; align-self: center; margin-bottom: 26px; }
.qr-brace { font-size: 44px; line-height: 1; margin-right: 10px; }
.qr-cases div { white-space: nowrap; margin: 2px 0; }
.qr-cond { margin-left: 18px; font-size: 17px; }
.qr-viz { display: grid; grid-template-columns: auto minmax(0, 320px) minmax(0, 320px); gap: 32px;
    align-items: start; justify-content: center; }
@media (max-width: 991px) {
    .qr-viz { grid-template-columns: minmax(0, 320px); }
    .qr-equation { margin-bottom: 0; }
}
.qr-panel { text-align: center; }
.qr-panel .chart-container { width: 100%; height: auto; aspect-ratio: 1 / 1; margin: 0; display: block; }
.q-image-slot { aspect-ratio: 1 / 1; border-radius: 8px; background: #000;
    border: 3px solid var(--q-color, #c13ce0); box-sizing: border-box; transition: border-color 0.1s;
    display: flex; align-items: center; justify-content: center; overflow: hidden; color: #999; font-size: 15px; }
.q-image-slot img { width: 100%; height: 100%; object-fit: cover; display: block; }
.qr-panel-label { font-size: 15px; color: #555; margin-top: 6px; }
.qr-compact .simple-slider { margin: 12px 0 0; text-align: center; }
.qr-compact .quantile-slider { width: 60%;
    background: linear-gradient(to right, #1f1bff, #7b2bf9, #c13ce0, #f05aa6, #f98c5c, #f6c24a); }
</style>
<div class="section" style="margin-top: 60px;">
    <h2 style="font-weight: bold; font-size: 28px; margin-bottom: 20px;">Abstract</h2>
    
    <div class="row">
        <div class="col-md-12">
            While deep learning offers tremendous promise for scientific and medical imaging, any failures and hallucinations (predictions that do not coincide with reality) are hard to pinpoint and can have serious downstream consequences. Uncertainty estimation techniques, such as conformal prediction, can help by predicting statistically valid error bars for a model's prediction. However, popular conformal prediction methods were not designed for high-dimensional image-valued problems and do not take into account spatial correlations within an image during conformal calibration, resulting in larger-than-necessary uncertainty intervals. We propose a practical simultaneous quantile regression method that enables non-linear, spatially-adaptive scaling during conformal calibration. Our method, <strong>QUTCC</strong> uses a U-Net architecture with a quantile embedding to learn a full conditional quantile distribution during training, and then leverages this non-linear, learned function for spatially-adaptive conformal calibration. At test time, our method can efficiently estimate uncertainty intervals with pixel-marginal coverage guarantees. In addition, QUTCC can also predict pixel-wise conditional probability density estimates without any built-in distributional assumptions. We evaluate our method on several denoising problems, accelerated magnetic resonance imaging, and quantitative phase microscopy. <strong>Our method consistently produces tighter uncertainty intervals than prior conformal methods at the same coverage level</strong>, can predict plausible conditional distributions for different tasks, and in some cases, high-uncertainty regions can help us locate hallucinations in a model's prediction.
        </div>
    </div>
</div>

<div class="section" style="margin-top: 60px;">
    <h2 style="font-weight: bold; font-size: 28px; margin-bottom: 20px;">Quantile Regression: Pinball Loss</h2>
    <div class="qr-card qr-contrast" style="margin-bottom: 20px;">
        <ul class="qr-points">
            <li><strong>Prior work (Im2Im-UQ)</strong> uses pinball loss
                <a href="https://arxiv.org/abs/2202.05265" target="_blank">to predict a fixed pair of upper and lower bounds</a>.</li>
            <li><strong>QUTCC</strong> learns the <em>full spectrum</em> of quantiles with a single network, known as
                <a href="https://library.seg.org/doi/10.1190/tle44020133.1#:~:text=The%20simultaneous%20quantile%20regression%20method,method%20on%20synthetic%20Kimberlina%20data." target="_blank"><strong>Simultaneous Quantile Regression (SQR)</strong></a>, applied to imaging inverse problems.</li>
        </ul>
    </div>
    <p class="qr-lead">
        Instead of predicting a single "best guess," <strong>quantile regression</strong> predicts a chosen quantile of the target distribution, for example a value the true answer falls below 10% or 90% of the time.
    </p>
    <ul class="qr-points">
        <li><em>q</em> ∈ (0, 1) is the target quantile level</li>
        <li><em>x</em> is the true value, <em>x̂</em> is the prediction</li>
        <li>Over- and under-estimates are <strong>penalized unequally</strong>, depending on <em>q</em></li>
    </ul>
    <div class="pinball-container qr-compact">
        <div class="qr-viz">
        <div class="qr-equation">
            <span style="margin-right: 12px; white-space: nowrap;">L<sub>q</sub>(x, x̂) =</span>
            <span class="qr-brace">{</span>
            <div class="qr-cases">
                <div><span>q · |x − x̂|</span><span class="qr-cond">if x − x̂ ≥ 0</span></div>
                <div><span>(1 − q) · |x − x̂|</span><span class="qr-cond">otherwise</span></div>
            </div>
        </div>
            <div class="qr-panel">
                <canvas id="pinball-chart" class="chart-container" width="320" height="320"></canvas>
                <div class="qr-panel-label">Pinball loss</div>
            </div>
            <div class="qr-panel">
                <!-- Image for the current q. Frames are listed in qImageFrames in the script below. -->
                <div id="q-image-slot" class="q-image-slot">
                    <img id="q-image" alt="QUTCC prediction at the selected quantile" hidden>
                    <span id="q-image-placeholder">Image at each q goes here</span>
                </div>
                <div class="qr-panel-label">QUTCC prediction of an MRI sample at q = <span id="q-image-label">0.50</span></div>
            </div>
        </div>
        <div class="simple-slider">
            <div class="quantile-value">q = <span id="quantile-display">0.50</span></div>
            <input type="range" id="quantile-slider" class="quantile-slider"
                   min="0.01" max="0.99" value="0.5" step="0.01">
            <div class="slider-hint">Drag the slider to change q</div>
        </div>
    </div>

</div>

<div class="section" style="margin-top: 20px;">
    <h2 style="font-weight: bold; font-size: 28px; margin-bottom: 20px;">Our Method: QUTCC</h2>
    <div class="row">
        <div class="col-md-12">
            <p class="qr-lead">
                We propose <strong>Quantile Uncertainty Training and Conformal Calibration</strong> (<strong>QUTCC🤗</strong>), an uncertainty quantification method for imaging inverse problems.
            </p>
            <ul class="qr-points">
                <li><strong>One learned network:</strong> a single network learns the full range of quantiles, instead of just a fixed upper and lower bound.</li>
                <li><strong>Spatially Adaptive Calibration:</strong> bounds are scaled <em>non-uniformly and nonlinearly</em> during conformal calibration, instead of by one constant factor like prior methods.</li>
                <li><strong>QUTCC predicts smaller UQ intervals:</strong> our method predicts tighter, more informative uncertainty intervals.</li>
                <li><strong>QUTCC can predict the full conditional distribution:</strong> since every quantile is learned, QUTCC can query them all at inference time to estimate each pixel's probability distribution.</li>
                <li><strong>Tested on 5 inverse problems:</strong> Gaussian noise, Poisson noise, real noise, MRI, and quantitative phase imaging (QPI).</li>
            </ul>
        </div>
    </div>
    
    <div class="method-container">
        <!-- All three stages sit in the same spot; only the active one is shown,
             so the box keeps the size of the largest stage. -->
        <div class="method-stage-area">
            <div class="method-stack method-image-stack">
                <img class="method-image active" data-stage="training" src="{{ '/assets/img/proj_2_qutcc/' | relative_url }}fig_1_training_gif.gif" alt="Training">
                <img class="method-image" data-stage="calibration" src="{{ '/assets/img/proj_2_qutcc/' | relative_url }}fig_1_calibration_gif.gif" alt="Calibration">
                <img class="method-image" data-stage="inference" src="{{ '/assets/img/proj_2_qutcc/' | relative_url }}fig_1_inference_gif.gif" alt="Inference">
            </div>
            <div class="method-stack method-caption-stack">
                <div class="method-caption active" data-stage="training">
                    <div class="stage-title">Training</div>
                    <div>During training, a neural network with a quantile embedding predicts an image as a function of the measurement and quantile, q. The quantile embedding is randomly sampled (q ∈ (0, 1)) and the value of q determines the asymmetry of the pinball loss, enabling the model to learn a range of conditional quantiles.</div>
                </div>
                <div class="method-caption" data-stage="calibration">
                    <div class="stage-title">Calibration</div>
                    <div>During calibration, the predictive bounds (q_lower, q_upper) are iteratively adjusted on a held-out dataset to satisfy the desired miscoverage level α.</div>
                </div>
                <div class="method-caption" data-stage="inference">
                    <div class="stage-title">Inference</div>
                    <div>At test time, the model is queried with q_lower, q_0.5, and q_upper to produce the mean prediction and a corresponding pixel-wise uncertainty map. Querying the full range of quantile values enables the prediction of the pixel-wise distribution.</div>
                </div>
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
    <h2 style="font-weight: bold; font-size: 28px; margin-bottom: 20px;">QUTCC Produces Smaller Uncertainty Intervals</h2>
    <div class="row">
        <div class="col-md-12 mt-3">
            <!-- Gray box around the bullets and chart -->
            <div class="method-container" style="margin-top: 0;">
            <!-- Bullets above the chart: edit the text below -->
            <ul class="qr-points" style="margin-bottom: 1.5rem;">
                <li>For evaluation, we compare MC-Dropout, Deep Ensembles, Im2Im, Im2Im-Asym., K-RCPS, and our method QUTCC on five imaging inverse problems: accelerated MRI, quantitative phase imaging (QPI), and denoising under real noise, synthetic Poisson noise, and Gaussian noise.</li>
                <li>We compare predicted uncertainty interval lengths stratified by pixel intensity for each task, and QUTCC achieves either the smallest or second-smallest interval lengths across the tasks.</li>
                <li>When QUTCC ranks second, it is usually behind MC-Dropout or Deep Ensembles, which are far more costly: 28×–47× slower inference and ~10× longer training, respectively.</li>
                <li>QUTCC achieves the smallest mean interval length on every task among conformal methods, and remains competitive with the posterior-sampling baselines despite using a single model and only two forward passes to construct each bound.</li>
            </ul>
            <!-- Table 1 of the paper: interval length by pixel intensity, one task at a time -->
            <div class="t1" id="table1">
                <div class="t1-buttons" role="tablist" aria-label="Task">
                    <button class="t1-btn active" data-task="0">Poisson</button>
                    <button class="t1-btn" data-task="1">Gaussian</button>
                    <button class="t1-btn" data-task="2">Real-Noise</button>
                    <button class="t1-btn" data-task="3">MRI</button>
                    <button class="t1-btn" data-task="4">QPI</button>
                </div>
                <div class="t1-groups" role="radiogroup" aria-label="Method type">
                    <button class="t1-group-btn" data-group="Posterior-based" role="radio" aria-checked="false">Posterior-based</button>
                    <button class="t1-group-btn active" data-group="Quantile-based" role="radio" aria-checked="true">Quantile-based</button>
                </div>
                <div class="t1-legend" id="t1-legend"></div>
                <div class="t1-chart" id="t1-chart">
                    <svg id="t1-svg" viewBox="0 0 760 330" role="img" aria-label="Line chart of uncertainty interval length by pixel intensity for each method"></svg>
                    <div class="t1-tip" id="t1-tip" hidden></div>
                </div>
                <p class="t1-note">Hover over the chart for mean ± std at each intensity. Data from Table 1 of the paper.</p>
            </div>
            </div>
        </div>
        <div class="col-md-12 mt-5">
             <div class="col-md-12">
                <!-- MRI bullets: edit the text below -->
                <ul class="qr-points">
                    <li>QUTCC's smaller uncertainty interval lengths mean it can be more precise about pinpointing areas of error and hallucination.</li>
                    <li>Below, we show predictions from QUTCC and Im2Im-UQ on an undersampled MRI task.</li>
                    <li>Both models highlight regions of high uncertainty that correspond to regions of high error, but QUTCC predicts precise regions.</li>
                </ul>
            </div>
        </div>
        <div class="col-12 mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/hallucination_gif.gif" title="" class="img-fluid" width="700px" height="auto" %}        
            <!-- <div class="caption" style="text-align: left;">
                <b>FIG CAPTION</b>
            </div> -->
        </div>
    </div>
</div>

<div class="section results-section" style="margin-top: 20px;">
    <h2 style="font-weight: bold; font-size: 28px; margin-bottom: 20px;">Pixel-wise Probability Density Functions</h2>
    <div class="row">
        <div class="col-md-12 mt-3">
            <p class="qr-lead">
                Because QUTCC learns every quantile, it can predict a full <strong>probability density function (PDF)</strong> at each pixel, not just an upper and lower bound.
            </p>
            <!-- PDF bullets: edit the text below -->
            <ul class="qr-points">
                <li>Prior quantile methods like Im2Im-UQ only predict discrete upper and lower bounds, so they can't describe the full distribution at a pixel.</li>
                <li>QUTCC queries many quantiles from a single network and calibrates them across a range of miscoverage levels α (e.g., 0.1 to 0.9).</li>
                <li>Together, these calibrated intervals approximate the cumulative distribution function (CDF) at each pixel. Differentiating it gives a <strong>conformalized pixel-wise PDF</strong> with coverage guarantees at each risk level.</li>
                <li>Below, we take a noisy Gaussian image (σ = 0.1) and compare the predicted PDFs at three pixels.</li>
            </ul>
        </div>
        <!-- Interactive demo: click a numbered spot to show that pixel's PDF on the right -->
        <div class="col-12 mt-3">
            <div class="method-container pdf-demo">
                <div class="pdf-demo-grid">
                    <div class="pdf-demo-left">
                        <!-- Square crop of pdf_microscope.png. Spot positions are the circle centers in the crop (640x640 px). -->
                        <div class="pdf-crop">
                            <img src="{{ '/assets/img/proj_2_qutcc/pdf_microscope_crop.png' | relative_url }}" alt="Noisy Gaussian measurement with three marked pixels">
                        <button class="clickable-spot spot-blue" onclick="showDistribution('right-skewed', this)" style="left: 84.53%; top: 27.03%; --spot: #0000ff;" title="Pixel 1: right-skewed">1</button>
                        <button class="clickable-spot spot-green" onclick="showDistribution('normal', this)" style="left: 14.84%; top: 44.84%; --spot: #008000;" title="Pixel 2: normal">2</button>
                        <button class="clickable-spot spot-red" onclick="showDistribution('left-skewed', this)" style="left: 84.53%; top: 52.50%; --spot: #ff0000;" title="Pixel 3: left-skewed">3</button>
                        </div>
                        <div class="slider-hint">Gaussian noise, σ = 0.1. Click a circled pixel.</div>
                    </div>
                    <div class="pdf-demo-right">
                        <div id="distribution-info">
                            <h4 id="dist-title"></h4>
                            <div id="dist-visualization"></div>
                            <div id="dist-description"></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- Figure 5 viewer: pick a noise type and level to show that panel -->
        <div class="col-12 mt-4">
            <!-- Fig. 5 bullets: edit the text below -->
            <ul class="qr-points" style="margin-bottom: 1.5rem;">
                <li>We compare the predicted conditional PDFs of 10 representative pixels, recovered from a measurement with different levels of Gaussian and Poisson noise, across QUTCC, Ensemble, and MC-Dropout.</li>
                <li>Consistent with a Gaussian distribution, as σ increases, the conditional PDF at each pixel becomes broader, reflecting the increased variance of the distribution.</li>
                <li>In contrast, in the Poisson setting, increasing λ shifts the distribution upward, while the spread increases in proportion to the mean.</li>
            </ul>
            <div class="method-container fig5" style="margin-top: 0;">
                <div class="t1-buttons" role="radiogroup" aria-label="Noise type">
                    <button class="t1-btn fig5-noise active" data-noise="gaussian" role="radio" aria-checked="true">Gaussian Noise</button>
                    <button class="t1-btn fig5-noise" data-noise="poisson" role="radio" aria-checked="false">Poisson Noise</button>
                </div>
                <div class="t1-groups" role="radiogroup" aria-label="Noise level">
                    <button class="t1-group-btn fig5-level active" data-level="less" role="radio" aria-checked="true">Less noise</button>
                    <button class="t1-group-btn fig5-level" data-level="more" role="radio" aria-checked="false">More noise</button>
                </div>
                <!-- Images are crops of Fig. 5 of the paper, in assets/img/proj_2_qutcc/fig5/ -->
                <img id="fig5-img" class="fig5-img" src="{{ '/assets/img/proj_2_qutcc/fig5/gaussian_less.png' | relative_url }}" alt="Fig. 5: predicted pixel PDFs, Gaussian noise, less noise">
                <p class="t1-note" id="fig5-note">Gaussian noise, σ = 0.1. Predicted PDFs at the 10 colored pixels for QUTCC, Deep Ensemble and MC-Dropout. From Fig. 5 of the paper.</p>
            </div>
        </div>
        <!-- <div class="col-md-12 mt-3">
            <div style="text-align: left; padding: 20px; background-color: #f8f9fa; border-radius: 8px;">
                The ability to visualize these pixel-wise distributions provides valuable insights into the reconstruction process. <strong>Right-skewed distributions</strong> often indicate regions where the model is more confident about lower intensity values but uncertain about potential high-intensity artifacts. <strong>Normal distributions</strong> suggest well-behaved, symmetric uncertainty around the predicted value. <strong>Left-skewed distributions</strong> may indicate areas where the model expects higher intensities but has some uncertainty about potential underestimation. This granular uncertainty information enables practitioners to identify not just <em>where</em> the model is uncertain, but <em>how</em> it is uncertain, facilitating more informed decision-making in critical applications.
            </div>
        </div> -->
    </div>
</div>

<div class="section" style="margin-top: 20px;">
    <h2 style="font-weight: bold; font-size: 28px; margin-bottom: 20px;">Conclusion</h2>  
    <div class="row">
        <div class="col-md-12">
            We propose QUTCC, a <b>new uncertainty quantification method for imaging inverse problems</b> that uses a learned, <b>nonlinear, and spatially-adaptive conformal calibration</b>. QUTCC trains a single U-Net with a quantile embedding on q ∈ (0, 1) quantiles through simultaneous quantile regression, then adjusts its quantile bound predictions during calibration until the desired risk is satisfied. Across five imaging inverse problems, QUTCC achieves <b>smaller uncertainty intervals than prior conformal methods</b> and is competitive with MC-Dropout and Deep Ensembles at a fraction of their compute cost, all while maintaining the same statistical coverage. QUTCC can also estimate a <b>conformalized pixel-wise conditional PDF</b>, something previous conformal methods for image-to-image regression could not do, and its high-uncertainty regions often coincide with reconstruction errors and hallucinations. While QUTCC requires paired data for training and calibration and offers pixel-wise marginal coverage guarantees, we hope it helps practitioners identify harmful mistakes in scientific and medical imaging.
        </div>
    </div>
</div>


<div class="row" style="margin-top: 20px;">
    <div class="col-md-12">
        <b style="font-size: 28px;">Bibtex Citation</b>
        <div class="form-group col-md-12">
            <textarea id="bibtex" class="form-control" readonly>
            @inproceedings{ye2026qutcc,
            title={QUTCC: Quantile Uncertainty Training and Conformal Calibration for Imaging Inverse Problems},
            author={Ye, Cassandra Tong and Li, Shamus and King, Tyler and Monakhova, Kristina},
            booktitle={Advances in Neural Information Processing Systems (NeurIPS)},
            year={2026},
            eprint={2507.14760},
            archivePrefix={arXiv}
            }
            </textarea>
        </div>
    </div>
</div>

<script>
// Curves traced from right_skewed_pdf.png, normal_pdf.png and left_skewed_pdf.png
var PDF_DATA = {"right_skewed":{"xDomain":[0.008,0.0409],"yMax":56.0,"xticks":[0.008,0.024,0.04],"yticks":[0,28,56],"curve":[[0.0098,37.31],[0.01007,37.37],[0.01033,37.38],[0.01059,37.37],[0.01086,37.28],[0.01112,37.15],[0.01138,37.07],[0.01165,36.93],[0.01191,36.81],[0.01218,36.68],[0.01244,36.56],[0.0127,36.53],[0.01297,36.53],[0.01323,36.59],[0.01349,36.75],[0.01376,36.96],[0.01402,37.24],[0.01429,37.56],[0.01455,37.93],[0.01481,38.35],[0.01508,38.8],[0.01534,39.3],[0.0156,39.83],[0.01587,40.39],[0.01613,40.97],[0.0164,41.56],[0.01666,42.18],[0.01692,42.79],[0.01719,43.41],[0.01745,44.05],[0.01771,44.69],[0.01798,45.33],[0.01824,45.97],[0.01851,46.58],[0.01877,47.17],[0.01903,47.74],[0.0193,48.29],[0.01956,48.8],[0.01982,49.32],[0.02009,49.78],[0.02035,50.21],[0.02062,50.59],[0.02088,50.91],[0.02114,51.2],[0.02193,51.68],[0.0222,51.72],[0.02246,51.65],[0.02273,51.53],[0.02299,51.31],[0.02325,50.98],[0.02352,50.53],[0.02378,50.02],[0.02404,49.36],[0.02431,48.57],[0.02457,47.62],[0.02484,46.58],[0.0251,45.33],[0.02536,43.97],[0.02563,42.51],[0.02589,40.84],[0.02615,39.22],[0.02642,37.57],[0.02668,35.86],[0.02695,34.25],[0.02721,32.65],[0.02747,31.08],[0.02774,29.64],[0.028,28.19],[0.02826,26.81],[0.02853,25.55],[0.02879,24.32],[0.02905,23.15],[0.02932,22.07],[0.02958,21.04],[0.02985,20.13],[0.03011,19.27],[0.03037,18.44],[0.03064,17.7],[0.0309,17.03],[0.03116,16.37],[0.03143,15.81],[0.03169,15.28],[0.03196,14.8],[0.03222,14.39],[0.03248,13.99],[0.03275,13.63],[0.03301,13.35],[0.03327,13.08],[0.03354,12.85],[0.0338,12.63],[0.03407,12.46],[0.03433,12.31],[0.03459,12.2],[0.03486,12.07],[0.03512,11.99],[0.03538,11.95],[0.03565,11.9],[0.03591,11.84],[0.03618,11.78],[0.03644,11.75],[0.0367,11.7],[0.03697,11.68],[0.03723,11.68],[0.03749,11.65],[0.03776,11.61],[0.03802,11.56],[0.03829,11.5],[0.03855,11.43],[0.03881,11.37],[0.03908,11.26],[0.03934,11.14],[0.03943,11.11]],"dot":[0.02143,51.249]},"normal":{"xDomain":[0.0059,0.0191],"yMax":108.79,"xticks":[0.008,0.013,0.018],"yticks":[0,50,100],"curve":[[0.00646,71.97],[0.00657,72.03],[0.00667,72.27],[0.00678,72.42],[0.00688,72.42],[0.00699,72.42],[0.00709,72.42],[0.0072,72.36],[0.00731,72.21],[0.00741,72.12],[0.00752,72.03],[0.00762,71.97],[0.00773,71.97],[0.00783,71.97],[0.00794,72.0],[0.00804,72.18],[0.00815,72.42],[0.00825,72.7],[0.00836,73.12],[0.00847,73.61],[0.00857,74.15],[0.00868,74.85],[0.00878,75.64],[0.00889,76.52],[0.00899,77.42],[0.0091,78.42],[0.0092,79.48],[0.00931,80.58],[0.00941,81.67],[0.00952,82.73],[0.00963,83.79],[0.00973,84.88],[0.00984,85.97],[0.00994,87.06],[0.01005,88.15],[0.01015,89.21],[0.01026,90.27],[0.01036,91.3],[0.01047,92.36],[0.01057,93.33],[0.01068,94.27],[0.01079,95.21],[0.01089,96.15],[0.011,97.0],[0.0111,97.85],[0.01121,98.64],[0.01131,99.36],[0.01142,100.09],[0.01152,100.79],[0.01163,101.42],[0.01173,101.94],[0.01184,102.42],[0.01195,102.82],[0.01205,103.21],[0.0124,103.76],[0.01251,104.06],[0.01261,104.06],[0.01272,103.97],[0.01282,103.85],[0.01293,103.58],[0.01304,103.3],[0.01314,102.88],[0.01325,102.39],[0.01335,101.82],[0.01346,101.12],[0.01356,100.3],[0.01367,99.48],[0.01377,98.52],[0.01388,97.45],[0.01398,96.24],[0.01409,95.0],[0.0142,93.64],[0.0143,92.18],[0.01441,90.64],[0.01451,89.0],[0.01462,87.27],[0.01472,85.45],[0.01483,83.64],[0.01493,81.7],[0.01504,79.73],[0.01514,77.79],[0.01525,75.82],[0.01536,73.85],[0.01546,71.94],[0.01557,70.0],[0.01567,68.06],[0.01578,66.15],[0.01588,64.36],[0.01599,62.67],[0.01609,61.0],[0.0162,59.39],[0.0163,57.94],[0.01641,56.45],[0.01651,55.03],[0.01662,53.79],[0.01673,52.55],[0.01683,51.33],[0.01694,50.24],[0.01704,49.24],[0.01715,48.36],[0.01725,47.58],[0.01736,46.85],[0.01746,46.21],[0.01757,45.7],[0.01767,45.21],[0.01778,44.88],[0.01789,44.67],[0.01799,44.45],[0.0181,44.39],[0.0182,44.55],[0.01831,44.82],[0.01841,45.04],[0.01845,45.1]],"dot":[0.01226,103.333]},"left_skewed":{"xDomain":[0.2,0.57],"yMax":6.0,"xticks":[0.2,0.385,0.57],"yticks":[0,3,6],"curve":[[0.22613,1.956],[0.22909,1.946],[0.23205,1.934],[0.235,1.923],[0.23796,1.917],[0.24092,1.913],[0.24388,1.911],[0.24684,1.907],[0.24979,1.909],[0.25275,1.911],[0.25571,1.913],[0.25867,1.917],[0.26163,1.921],[0.26458,1.928],[0.26754,1.939],[0.2705,1.948],[0.27346,1.958],[0.27642,1.971],[0.27937,1.981],[0.28233,1.994],[0.28529,2.008],[0.28825,2.021],[0.29121,2.036],[0.29416,2.048],[0.29712,2.065],[0.30008,2.08],[0.30304,2.095],[0.306,2.106],[0.30895,2.121],[0.31191,2.133],[0.31487,2.15],[0.31783,2.162],[0.32079,2.173],[0.32374,2.188],[0.3267,2.2],[0.32966,2.215],[0.33262,2.225],[0.33558,2.242],[0.33853,2.257],[0.34149,2.275],[0.34445,2.29],[0.34741,2.309],[0.35037,2.331],[0.35332,2.354],[0.35628,2.381],[0.35924,2.407],[0.3622,2.438],[0.36516,2.469],[0.36811,2.504],[0.37107,2.543],[0.37403,2.582],[0.37699,2.627],[0.37995,2.674],[0.3829,2.725],[0.38586,2.779],[0.38882,2.837],[0.39178,2.901],[0.39474,2.968],[0.39769,3.04],[0.40065,3.115],[0.40361,3.194],[0.40657,3.281],[0.40953,3.371],[0.41249,3.466],[0.41544,3.57],[0.4184,3.677],[0.42136,3.777],[0.42728,3.975],[0.43023,4.164],[0.43319,4.294],[0.43615,4.428],[0.43911,4.557],[0.44207,4.689],[0.44502,4.813],[0.44798,4.93],[0.45094,5.038],[0.4539,5.135],[0.45686,5.222],[0.45981,5.296],[0.46277,5.349],[0.46573,5.388],[0.46869,5.404],[0.47165,5.396],[0.4746,5.353],[0.47756,5.259],[0.48052,5.117],[0.48348,4.925],[0.48644,4.699],[0.48939,4.458],[0.49235,4.205],[0.49531,3.961],[0.49827,3.719],[0.50123,3.486],[0.50418,3.269],[0.50714,3.055],[0.5101,2.866],[0.51306,2.685],[0.51602,2.528],[0.51897,2.394],[0.52193,2.28],[0.52489,2.192],[0.52785,2.13],[0.53081,2.1],[0.53376,2.106],[0.53672,2.145],[0.53968,2.224],[0.54264,2.306],[0.54362,2.323]],"dot":[0.4258,3.909]}};

function showDistribution(type, el) {
    const distributions = {
        'right-skewed': {
            title: 'Right-Skewed Distribution',
            description: 'A right-skewed probability distribution indicates higher confidence in lower intensity values with a tail extending toward higher intensities',
            data: PDF_DATA.right_skewed, ticks: PDF_TICKS.right_skewed, color: '#0000ff'
        },
        'normal': {
            title: 'Normal Distribution', 
            description: 'A symmetric, normal distribution centered around the predicted intensity value indicates well-calibrated uncertainty with equal probability of over- and under-estimation.',
            data: PDF_DATA.normal, ticks: PDF_TICKS.normal, color: '#008000'
        },
        'left-skewed': {
            title: 'Left-Skewed Distribution',
            description: 'A left-skewed distribution indicates the model expects higher intensity values but has some uncertainty about potential underestimation. This pattern may indicate regions where the reconstruction tends to be conservative.',
            data: PDF_DATA.left_skewed, ticks: PDF_TICKS.left_skewed, color: '#ff0000'
        }
    };
    
    const distInfo = distributions[type];

    document.getElementById('dist-title').textContent = distInfo.title;
    document.getElementById('dist-description').textContent = distInfo.description;

    if (!pdfChart) pdfChart = buildPdfChart(document.getElementById('dist-visualization'));
    pdfChart.update(distInfo.data, distInfo.ticks, distInfo.color);

    // Outline the chosen spot
    document.querySelectorAll('.clickable-spot').forEach(spot => {
        spot.classList.toggle('selected', spot === el);
    });
}

// One PDF chart that is built once. Switching pixels only changes the axis
// numbers and the curve; the frame, grid, ticks and labels stay put.
// Every pixel uses 3 x-ticks and 3 y-ticks at the same positions:
// x-ticks sit 1/10, 1/2 and 9/10 of the way across, y-ticks at 0, 45% and 91%.
var PDF_TICKS = {
    right_skewed: { x: [0.010, 0.025, 0.040], y: [0, 28, 56] },
    normal:       { x: [0.006, 0.012, 0.018], y: [0, 50, 100] },
    left_skewed:  { x: [0.220, 0.385, 0.550], y: [0, 3, 6] }
};
var pdfChart = null;

function buildPdfChart(box) {
    const NS = 'http://www.w3.org/2000/svg';
    const W = 560, H = 300, M = { l: 62, r: 18, t: 14, b: 52 };
    const pw = W - M.l - M.r, ph = H - M.t - M.b;
    const el = (tag, attrs, parent) => {
        const n = document.createElementNS(NS, tag);
        for (const k in attrs) n.setAttribute(k, attrs[k]);
        (parent || svg).appendChild(n);
        return n;
    };
    box.innerHTML = '';
    const svg = el('svg', { viewBox: '0 0 ' + W + ' ' + H, class: 'pdf-chart', role: 'img', 'aria-label': 'Predicted pixel PDF' }, box);
    // fixed tick positions as fractions of the plot
    const fx = [0.1, 0.5, 0.9], fy = [0, 0.5 / 1.1, 1 / 1.1];
    const px = f => M.l + f * pw, py = f => M.t + ph - f * ph;
    const yLabels = fy.map(f => {
        el('line', { x1: M.l, x2: W - M.r, y1: py(f), y2: py(f), stroke: f === 0 ? '#999' : '#e6e6e6', 'stroke-width': 1 });
        return el('text', { x: M.l - 8, y: py(f) + 4, 'text-anchor': 'end', 'font-size': 13, fill: '#52514e' });
    });
    const xLabels = fx.map(f => {
        el('line', { x1: px(f), x2: px(f), y1: M.t + ph, y2: M.t + ph + 5, stroke: '#999' });
        return el('text', { x: px(f), y: M.t + ph + 21, 'text-anchor': 'middle', 'font-size': 13, fill: '#52514e' });
    });
    el('text', { x: M.l + pw / 2, y: H - 8, 'text-anchor': 'middle', 'font-size': 14, fill: '#333' }).textContent = 'Pixel intensity';
    el('text', { x: 16, y: M.t + ph / 2, 'text-anchor': 'middle', 'font-size': 14, fill: '#333', transform: 'rotate(-90 16 ' + (M.t + ph / 2) + ')' }).textContent = 'Density';
    const fill = el('path', { 'fill-opacity': 0.18 });
    const line = el('path', { fill: 'none', 'stroke-width': 2.5, 'stroke-linejoin': 'round' });
    const dot = el('circle', { r: 5, fill: '#111', stroke: '#fff', 'stroke-width': 2 });
    const guide = el('line', { y1: M.t, y2: M.t + ph, stroke: '#777', 'stroke-dasharray': '3 3', visibility: 'hidden' });
    const mark = el('circle', { r: 4.5, stroke: '#fff', 'stroke-width': 2, visibility: 'hidden' });
    const tip = el('text', { 'font-size': 13, fill: '#111', visibility: 'hidden' });
    const hit = el('rect', { x: M.l, y: M.t, width: pw, height: ph, fill: 'transparent' });

    const chart = { cur: null };
    chart.update = function (d, ticks, color) {
        const t = ticks.x, span = t[2] - t[0];
        const x0 = t[0] - span / 8, x1 = t[2] + span / 8; // ticks land at 1/10 and 9/10
        const yMax = ticks.y[2] * 1.1;
        const x = v => M.l + (v - x0) / (x1 - x0) * pw;
        const y = v => M.t + ph - v / yMax * ph;
        chart.cur = { d, x, y, color, yMax };
        ticks.y.forEach((v, i) => { yLabels[i].textContent = v; });
        ticks.x.forEach((v, i) => { xLabels[i].textContent = v.toFixed(3); });
        const c = d.curve;
        const path = c.map((p, i) => (i ? 'L' : 'M') + x(p[0]).toFixed(1) + ' ' + y(p[1]).toFixed(1)).join(' ');
        line.setAttribute('d', path);
        line.setAttribute('stroke', color);
        fill.setAttribute('d', path + ' L' + x(c[c.length - 1][0]).toFixed(1) + ' ' + y(0) + ' L' + x(c[0][0]).toFixed(1) + ' ' + y(0) + ' Z');
        fill.setAttribute('fill', color);
        dot.setAttribute('cx', x(d.dot[0])); dot.setAttribute('cy', y(d.dot[1]));
        mark.setAttribute('fill', color);
        [guide, mark, tip].forEach(n => n.setAttribute('visibility', 'hidden'));
    };
    hit.addEventListener('mousemove', ev => {
        const k = chart.cur; if (!k) return;
        const r = svg.getBoundingClientRect();
        const mx = (ev.clientX - r.left) * W / r.width;
        let best = k.d.curve[0];
        k.d.curve.forEach(p => { if (Math.abs(k.x(p[0]) - mx) < Math.abs(k.x(best[0]) - mx)) best = p; });
        const bx = k.x(best[0]), by = k.y(best[1]);
        [guide, mark, tip].forEach(n => n.setAttribute('visibility', 'visible'));
        guide.setAttribute('x1', bx); guide.setAttribute('x2', bx);
        mark.setAttribute('cx', bx); mark.setAttribute('cy', by);
        tip.textContent = 'intensity ' + best[0].toFixed(4) + ', density ' + best[1].toFixed(best[1] < 10 ? 2 : 1);
        const right = bx > M.l + pw * 0.6;
        tip.setAttribute('x', right ? bx - 8 : bx + 8);
        tip.setAttribute('text-anchor', right ? 'end' : 'start');
        tip.setAttribute('y', M.t + 14);
    });
    hit.addEventListener('mouseleave', () => [guide, mark, tip].forEach(n => n.setAttribute('visibility', 'hidden')));
    return chart;
}

// Figure 5 viewer: one image per noise type and level
(function () {
    var dir = "{{ '/assets/img/proj_2_qutcc/fig5/' | relative_url }}";
    var notes = {
        gaussian_less: 'Gaussian noise, σ = 0.1',
        gaussian_more: 'Gaussian noise, σ = 0.4',
        poisson_less: 'Poisson noise, λ = 90',
        poisson_more: 'Poisson noise, λ = 60'
    };
    var state = { noise: 'gaussian', level: 'less' };
    // preload so switching is instant
    Object.keys(notes).forEach(function (k) { new Image().src = dir + k + '.png'; });
    function update() {
        var key = state.noise + '_' + state.level;
        var img = document.getElementById('fig5-img');
        img.src = dir + key + '.png';
        img.alt = 'Fig. 5: predicted pixel PDFs, ' + notes[key];
        document.getElementById('fig5-note').textContent = notes[key] + '. Predicted PDFs at the 10 colored pixels for QUTCC, Deep Ensemble and MC-Dropout. From Fig. 5 of the paper.';
    }
    function wire(selector, attr, field) {
        var btns = document.querySelectorAll(selector);
        btns.forEach(function (b) {
            b.addEventListener('click', function () {
                state[field] = b.getAttribute(attr);
                btns.forEach(function (o) {
                    o.classList.toggle('active', o === b);
                    o.setAttribute('aria-checked', o === b ? 'true' : 'false');
                });
                update();
            });
        });
    }
    document.addEventListener('DOMContentLoaded', function () {
        if (!document.getElementById('fig5-img')) return;
        wire('.fig5-noise', 'data-noise', 'noise');
        wire('.fig5-level', 'data-level', 'level');
    });
})();

// Show the first pixel's PDF when the page loads
document.addEventListener('DOMContentLoaded', function () {
    showDistribution('right-skewed', document.querySelector('.spot-blue'));
});
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
    
    canvas.width = 320;
    canvas.height = 320;
    
// Color for a quantile q, from blue (low q) through purple and pink to orange (high q),
// matching the quantile-embedding colors in the paper's Fig. 1.
var qColorStops = [
    [0.00, [31, 27, 255]],
    [0.20, [123, 43, 249]],
    [0.40, [193, 60, 224]],
    [0.60, [240, 90, 166]],
    [0.80, [249, 140, 92]],
    [1.00, [246, 194, 74]]
];
function qColor(q) {
    for (var i = 1; i < qColorStops.length; i++) {
        if (q <= qColorStops[i][0]) {
            var a = qColorStops[i - 1], b = qColorStops[i];
            var t = (q - a[0]) / (b[0] - a[0]);
            var c = a[1].map(function (v, k) { return Math.round(v + t * (b[1][k] - v)); });
            return 'rgb(' + c.join(',') + ')';
        }
    }
    return 'rgb(' + qColorStops[qColorStops.length - 1][1].join(',') + ')';
}

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
    ctx.fillText('Predicted − Ground Truth', canvas.width / 2, canvas.height - 10);
    ctx.save();
    ctx.translate(15, canvas.height / 2);
    ctx.rotate(-Math.PI / 2);
    ctx.fillText('Pinball Loss', 0, 0);
    ctx.restore();
    
    // Function scaling - match Python code ranges
    const errorMin = -0.5, errorMax = 0.5;  // Match Python xlim
    const errorToPx = (error) => margin + ((error - errorMin) / (errorMax - errorMin)) * width;
    const maxLoss = 0.5;  // Match Python ylim
    const lossToPy = (loss) => (canvas.height - margin) - (loss / maxLoss) * height;
    
    // Pinball loss (paper Eq. 1), plotted against x̂ − x like Fig. 1a.
    // Over-estimates (x̂ > x) cost (1 − q); under-estimates cost q.
    function pinballLoss(error, quantile) {
        return Math.max((1 - quantile) * error, -quantile * error);
    }
    
    // Draw horizontal line at y=0
    ctx.strokeStyle = 'rgba(0, 0, 0, 0.3)';
    ctx.lineWidth = 1.5;
    ctx.beginPath();
    ctx.moveTo(margin, lossToPy(0));
    ctx.lineTo(canvas.width - margin, lossToPy(0));
    ctx.stroke();
    
    // Draw vertical line at x=0 (error=0)
    ctx.beginPath();
    ctx.moveTo(errorToPx(0), margin);
    ctx.lineTo(errorToPx(0), canvas.height - margin);
    ctx.stroke();
    
    // Plot curve
    ctx.strokeStyle = qColor(q);
    ctx.lineWidth = 5;
    ctx.beginPath();
    const steps = 1000;  // Match Python resolution
    for (let i = 0; i <= steps; i++) {
        const error = errorMin + i * (errorMax - errorMin) / steps;
        const loss = pinballLoss(error, q);
        const px = errorToPx(error);
        const py = lossToPy(loss);
        
        if (i === 0) {
            ctx.moveTo(px, py);
        } else {
            ctx.lineTo(px, py);
        }
    }
    ctx.stroke();
    
    // Show q value - match Python display logic
    ctx.fillStyle = qColor(q);
    ctx.font = 'bold 16px Arial';
    ctx.textAlign = 'left';
    let displayText;
    if (Math.abs(q - 0.5) < 0.01) {  // Close to 0.5
        displayText = 'q = 0.5';
    } else {
        displayText = `q = ${q.toFixed(2)}`;
    }
    ctx.fillText(displayText, margin + 10, margin + 20);
}

// Images of the QUTCC prediction at different q, listed in quantiles/manifest.json
// (made by the export script in the qutcc repo). Shows a placeholder until it exists.
var qImageFrames = [];
var qFramesDir = "{{ '/assets/img/proj_2_qutcc/quantiles/' | relative_url }}";
fetch(qFramesDir + 'manifest.json')
    .then(function (r) { return r.ok ? r.json() : null; })
    .then(function (m) {
        if (!m || !m.frames || !m.frames.length) return;
        qImageFrames = m.frames.map(function (f) {
            var img = new Image();
            img.src = qFramesDir + f.file; // preload so the slider swaps instantly
            return { q: f.q, src: img.src };
        });
        updateQImage(parseFloat(slider.value));
    })
    .catch(function () {});
var qImage = document.getElementById('q-image');
var qImagePlaceholder = document.getElementById('q-image-placeholder');
var qImageLabel = document.getElementById('q-image-label');

function updateQImage(q) {
    qImageLabel.textContent = q.toFixed(2);
    if (!qImageFrames.length) return;
    var best = qImageFrames.reduce(function (a, b) {
        return Math.abs(b.q - q) < Math.abs(a.q - q) ? b : a;
    });
    if (qImage.getAttribute('src') !== best.src) qImage.src = best.src;
    qImage.hidden = false;
    qImagePlaceholder.hidden = true;
}

function updateVisualization() {
    var q = parseFloat(slider.value);
    display.textContent = q.toFixed(2);
    document.querySelector('.qr-compact').style.setProperty('--q-color', qColor(q));
    drawPinballLoss(q);
    updateQImage(q);
}
    updateVisualization();
    slider.addEventListener('input', updateVisualization);

    // Method stage switching: show the chosen stage's GIF and caption
    const methodButtons = document.querySelectorAll('.method-btn');
    methodButtons.forEach(button => {
        button.addEventListener('click', function() {
            const stage = this.dataset.stage;
            methodButtons.forEach(btn => btn.classList.toggle('active', btn === this));
            document.querySelectorAll('.method-image, .method-caption').forEach(el => {
                const on = el.dataset.stage === stage;
                if (on && el.tagName === 'IMG' && !el.classList.contains('active')) {
                    el.src = el.src; // restart the GIF from the beginning
                }
                el.classList.toggle('active', on);
            });
        });
    });
});
</script>

<script>
// Table 1 viewer: chart + table for one task at a time
(function () {
    var DATA = [{"task": "Poisson", "rows": [{"bin": "0.00–0.20", "vals": [[0.123, 0.107, ""], [0.037, 0.036, "second"], [0.04, 0.013, ""], [0.039, 0.013, ""], [0.041, 0.011, ""], [0.035, 0.011, "best"]]}, {"bin": "0.20–0.40", "vals": [[0.371, 0.148, ""], [0.104, 0.097, ""], [0.112, 0.018, ""], [0.109, 0.018, ""], [0.1, 0.015, "second"], [0.09, 0.015, "best"]]}, {"bin": "0.40–0.60", "vals": [[0.643, 0.213, ""], [0.24, 0.309, ""], [0.211, 0.026, ""], [0.206, 0.026, ""], [0.181, 0.021, "second"], [0.16, 0.022, "best"]]}, {"bin": "0.60–0.80", "vals": [[0.663, 0.215, ""], [0.306, 0.438, ""], [0.244, 0.03, ""], [0.238, 0.03, ""], [0.207, 0.024, "second"], [0.158, 0.028, "best"]]}, {"bin": "0.80–1.00", "vals": [[0.771, 0.25, ""], [0.653, 0.933, ""], [0.302, 0.042, ""], [0.294, 0.042, ""], [0.225, 0.028, "second"], [0.187, 0.034, "best"]]}]}, {"task": "Gaussian", "rows": [{"bin": "0.00–0.20", "vals": [[0.073, 0.07, ""], [0.05, 0.019, "best"], [0.056, 0.02, ""], [0.055, 0.02, ""], [0.054, 0.019, "second"], [0.057, 0.022, ""]]}, {"bin": "0.20–0.40", "vals": [[0.198, 0.121, ""], [0.121, 0.027, "best"], [0.135, 0.027, ""], [0.132, 0.026, ""], [0.126, 0.025, "second"], [0.131, 0.03, ""]]}, {"bin": "0.40–0.60", "vals": [[0.318, 0.169, ""], [0.216, 0.043, ""], [0.227, 0.041, ""], [0.222, 0.04, ""], [0.211, 0.037, "second"], [0.206, 0.046, "best"]]}, {"bin": "0.60–0.80", "vals": [[0.318, 0.129, ""], [0.198, 0.05, "second"], [0.239, 0.04, ""], [0.234, 0.039, ""], [0.222, 0.036, ""], [0.19, 0.048, "best"]]}, {"bin": "0.80–1.00", "vals": [[0.355, 0.126, ""], [0.23, 0.061, "second"], [0.276, 0.045, ""], [0.27, 0.044, ""], [0.246, 0.038, ""], [0.205, 0.051, "best"]]}]}, {"task": "Real-Noise", "rows": [{"bin": "0.00–0.20", "vals": [[0.025, 0.015, "second"], [0.021, 0.006, "best"], [0.03, 0.013, ""], [0.03, 0.013, ""], [0.031, 0.012, ""], [0.033, 0.012, ""]]}, {"bin": "0.20–0.40", "vals": [[0.104, 0.035, "second"], [0.088, 0.013, "best"], [0.166, 0.017, ""], [0.165, 0.017, ""], [0.151, 0.015, ""], [0.14, 0.016, ""]]}, {"bin": "0.40–0.60", "vals": [[0.189, 0.047, "second"], [0.152, 0.021, "best"], [0.232, 0.018, ""], [0.23, 0.018, ""], [0.208, 0.016, ""], [0.202, 0.018, ""]]}, {"bin": "0.60–0.80", "vals": [[0.273, 0.058, ""], [0.233, 0.037, "best"], [0.266, 0.017, ""], [0.263, 0.017, ""], [0.236, 0.015, "second"], [0.248, 0.021, ""]]}, {"bin": "0.80–1.00", "vals": [[0.342, 0.055, ""], [0.318, 0.063, ""], [0.278, 0.014, ""], [0.274, 0.014, "second"], [0.197, 0.014, "best"], [0.286, 0.025, ""]]}]}, {"task": "MRI", "rows": [{"bin": "0.00–0.20", "vals": [[0.132, 0.051, ""], [0.088, 0.026, "best"], [0.092, 0.025, "second"], [0.092, 0.025, ""], [0.091, 0.025, ""], [0.092, 0.026, ""]]}, {"bin": "0.20–0.40", "vals": [[0.206, 0.073, ""], [0.127, 0.031, "best"], [0.132, 0.029, ""], [0.132, 0.029, ""], [0.13, 0.028, ""], [0.13, 0.031, "second"]]}, {"bin": "0.40–0.60", "vals": [[0.304, 0.093, ""], [0.132, 0.029, "second"], [0.135, 0.028, ""], [0.135, 0.028, ""], [0.133, 0.027, ""], [0.13, 0.03, "best"]]}, {"bin": "0.60–0.80", "vals": [[0.454, 0.131, ""], [0.138, 0.026, "second"], [0.141, 0.024, ""], [0.14, 0.024, ""], [0.139, 0.024, ""], [0.133, 0.027, "best"]]}, {"bin": "0.80–1.00", "vals": [[0.68, 0.223, ""], [0.14, 0.02, "second"], [0.14, 0.019, ""], [0.14, 0.019, ""], [0.138, 0.018, ""], [0.136, 0.022, "best"]]}]}, {"task": "QPI", "rows": [{"bin": "0.00–0.20", "vals": [[0.055, 0.012, ""], [0.037, 0.005, "best"], [0.059, 0.005, ""], [0.058, 0.004, ""], [0.061, 0.005, ""], [0.057, 0.005, "second"]]}, {"bin": "0.20–0.40", "vals": [[0.059, 0.144, ""], [0.042, 0.006, "best"], [0.067, 0.005, ""], [0.066, 0.005, ""], [0.067, 0.006, ""], [0.063, 0.006, "second"]]}, {"bin": "0.40–0.60", "vals": [[0.088, 0.018, ""], [0.054, 0.006, "best"], [0.085, 0.006, ""], [0.083, 0.006, ""], [0.088, 0.006, ""], [0.081, 0.006, "second"]]}, {"bin": "0.60–0.80", "vals": [[0.105, 0.017, ""], [0.059, 0.006, "best"], [0.093, 0.006, ""], [0.091, 0.006, ""], [0.096, 0.006, ""], [0.09, 0.006, "second"]]}, {"bin": "0.80–1.00", "vals": [[0.116, 0.016, ""], [0.054, 0.006, "best"], [0.087, 0.007, ""], [0.085, 0.007, "second"], [0.091, 0.006, ""], [0.087, 0.007, ""]]}]}];
    var METHODS = [
        // QUTCC blue and Im2Im red follow the paper (Fig. 4); the others use matplotlib colors
        { name: 'MC-Dropout',     short: 'MC-Drop.',    group: 'Posterior-based', dash: '6 4', shape: 'circle',   color: '#2ca02c' },
        { name: 'Deep Ensemble',  short: 'Deep Ens.',   group: 'Posterior-based', dash: '6 4', shape: 'square',   color: '#8c564b' },
        { name: 'Im2Im',          short: 'Im2Im',       group: 'Quantile-based',  dash: '',    shape: 'triangle', color: '#e8202a' },
        { name: 'Im2Im-Asym.',    short: 'Im2Im-Asym.', group: 'Quantile-based',  dash: '',    shape: 'diamond',  color: '#f28e2b' },
        { name: 'K-RCPS',         short: 'K-RCPS',      group: 'Quantile-based',  dash: '',    shape: 'tri-down', color: '#9b4dca' },
        { name: 'QUTCC',          short: 'QUTCC',       group: 'Quantile-based',  dash: '',    shape: 'dot',      color: '#1f3be8', focus: true }
    ];
    var BIN_COLORS = ['rgb(49,54,149)', 'rgb(116,173,209)', 'rgb(255,255,191)', 'rgb(253,174,97)', 'rgb(215,48,39)'];
    var BLUE = '#1f3be8';
    var W = 760, H = 330, M = { l: 58, r: 24, t: 14, b: 50 };
    var NS = 'http://www.w3.org/2000/svg';
    var svg = document.getElementById('t1-svg');
    var tip = document.getElementById('t1-tip');
    var chartBox = document.getElementById('t1-chart');
    var current = 0, highlight = null;
    // Show one method type at a time; QUTCC always stays in for comparison
    var mode = 'Quantile-based';
    function visible(i) { return METHODS[i].focus || METHODS[i].group === mode; }

    function el(tag, attrs, parent) {
        var e = document.createElementNS(NS, tag);
        for (var k in attrs) e.setAttribute(k, attrs[k]);
        if (parent) parent.appendChild(e);
        return e;
    }
    function marker(shape, x, y, color, parent, focus) {
        var r = focus ? 5 : 4.5, fill = focus ? color : '#fff', sw = focus ? 2 : 1.8;
        var common = { fill: fill, stroke: color, 'stroke-width': sw };
        if (focus) { common.stroke = '#fff'; common['stroke-width'] = 2; } // surface ring
        var a;
        if (shape === 'circle' || shape === 'dot') { a = Object.assign({ cx: x, cy: y, r: r }, common); return el('circle', a, parent); }
        if (shape === 'square') { a = Object.assign({ x: x - r, y: y - r, width: 2 * r, height: 2 * r, rx: 1 }, common); return el('rect', a, parent); }
        var pts;
        if (shape === 'triangle') pts = [[x, y - r - 1], [x + r + 0.5, y + r - 0.5], [x - r - 0.5, y + r - 0.5]];
        if (shape === 'tri-down') pts = [[x, y + r + 1], [x + r + 0.5, y - r + 0.5], [x - r - 0.5, y - r + 0.5]];
        if (shape === 'diamond') pts = [[x, y - r - 1], [x + r + 1, y], [x, y + r + 1], [x - r - 1, y]];
        a = Object.assign({ points: pts.map(function (p) { return p.join(','); }).join(' ') }, common);
        return el('polygon', a, parent);
    }
    function niceMax(v) {
        var step = Math.pow(10, Math.floor(Math.log10(v))) / 2;
        var steps = [1, 2, 2.5, 5, 10].map(function (m) { return m * step; });
        for (var i = 0; i < steps.length; i++) if (v / steps[i] <= 6) return { max: Math.ceil(v / steps[i]) * steps[i], step: steps[i] };
        return { max: v, step: v / 5 };
    }
    function colorFor(i) { return METHODS[i].color; }
    // When a legend item is hovered, fade the other lines
    function opacityFor(i) { return highlight === null || highlight === i ? 1 : 0.2; }

    // Legend (built once)
    var legend = document.getElementById('t1-legend');
    ['Posterior-based', 'Quantile-based'].forEach(function (g) {
        var label = document.createElement('span');
        label.className = 't1-legend-group';
        label.textContent = g + ':';
        legend.appendChild(label);
        METHODS.forEach(function (m, i) {
            if (m.group !== g) return;
            var item = document.createElement('span');
            item.className = 't1-legend-item' + (m.focus ? ' is-qutcc' : '');
            item.dataset.group = m.group;
            var sw = document.createElementNS(NS, 'svg');
            sw.setAttribute('width', 30); sw.setAttribute('height', 14);
            el('line', { x1: 1, y1: 7, x2: 29, y2: 7, stroke: m.color, 'stroke-width': m.focus ? 3 : 2, 'stroke-dasharray': m.dash }, sw);
            marker(m.shape, 15, 7, m.color, sw, m.focus);
            item.appendChild(sw);
            item.appendChild(document.createTextNode(m.short));
            item.addEventListener('mouseenter', function () { if (visible(i)) { highlight = i; draw(); } });
            item.addEventListener('mouseleave', function () { highlight = null; draw(); });
            legend.appendChild(item);
        });
    });

    function draw() {
        var task = DATA[current];
        while (svg.firstChild) svg.removeChild(svg.firstChild);
        var maxV = 0;
        task.rows.forEach(function (r) { r.vals.forEach(function (v, i) { if (visible(i)) maxV = Math.max(maxV, v[0] + v[1]); }); });
        var ny = niceMax(maxV * 1.05);
        var pw = W - M.l - M.r, ph = H - M.t - M.b;
        var x = function (j) { return M.l + pw * (j + 0.5) / task.rows.length; };
        var shown = METHODS.map(function (m, i) { return i; }).filter(visible);
        var xo = function (j, i) { return x(j) + (shown.indexOf(i) - (shown.length - 1) / 2) * 7; };
        var y = function (v) { return M.t + ph * (1 - v / ny.max); };

        // Grid + y axis
        for (var t = 0; t <= ny.max + 1e-9; t += ny.step) {
            el('line', { x1: M.l, x2: W - M.r, y1: y(t), y2: y(t), stroke: t === 0 ? '#bdbcb7' : '#ececea', 'stroke-width': 1 }, svg);
            var lab = el('text', { x: M.l - 8, y: y(t) + 4, 'text-anchor': 'end', 'font-size': 12, fill: '#52514e' }, svg);
            lab.textContent = (+t.toFixed(3)).toString();
        }
        var yl = el('text', { x: 14, y: M.t + ph / 2, 'text-anchor': 'middle', 'font-size': 13, fill: '#52514e', transform: 'rotate(-90 14 ' + (M.t + ph / 2) + ')' }, svg);
        yl.textContent = 'Interval length';
        // X axis labels
        task.rows.forEach(function (r, j) {
            var tx = el('text', { x: x(j), y: H - M.b + 20, 'text-anchor': 'middle', 'font-size': 12, fill: '#52514e' }, svg);
            tx.textContent = r.bin;
        });
        var xl = el('text', { x: M.l + pw / 2, y: H - 6, 'text-anchor': 'middle', 'font-size': 13, fill: '#52514e' }, svg);
        xl.textContent = 'Ground-truth pixel intensity';

        // Crosshair (behind lines)
        var cross = el('line', { y1: M.t, y2: M.t + ph, stroke: '#bdbcb7', 'stroke-width': 1, visibility: 'hidden' }, svg);

        // Lines: context first, focus (QUTCC) last so it sits on top
        var order = METHODS.map(function (m, i) { return i; }).filter(visible)
            .sort(function (a, b) { return (METHODS[a].focus ? 2 : a === highlight ? 1 : 0) - (METHODS[b].focus ? 2 : b === highlight ? 1 : 0); });
        order.forEach(function (i) {
            var m = METHODS[i], c = colorFor(i);
            var g = el('g', { opacity: opacityFor(i) }, svg);
            // Std bars (mean ± std, clipped at 0) with small caps
            task.rows.forEach(function (r, j) {
                var mu = r.vals[i][0], sd = r.vals[i][1], cx = xo(j, i);
                var y1 = y(Math.max(0, mu - sd)), y2 = y(mu + sd);
                el('line', { x1: cx, x2: cx, y1: y1, y2: y2, stroke: c, 'stroke-width': 1.5, opacity: 0.6 }, g);
                el('line', { x1: cx - 3, x2: cx + 3, y1: y2, y2: y2, stroke: c, 'stroke-width': 1.5, opacity: 0.6 }, g);
                if (mu - sd > 0) el('line', { x1: cx - 3, x2: cx + 3, y1: y1, y2: y1, stroke: c, 'stroke-width': 1.5, opacity: 0.6 }, g);
            });
            var d = task.rows.map(function (r, j) { return (j ? 'L' : 'M') + xo(j, i) + ' ' + y(r.vals[i][0]); }).join(' ');
            el('path', { d: d, fill: 'none', stroke: c, 'stroke-width': m.focus ? 3 : 2, 'stroke-dasharray': m.dash, 'stroke-linejoin': 'round', 'stroke-linecap': 'round' }, g);
            task.rows.forEach(function (r, j) { marker(m.shape, xo(j, i), y(r.vals[i][0]), c, g, m.focus); });
        });
        // Direct label for QUTCC at the right end
        var last = task.rows.length - 1;
        if (visible(5)) { var ql = el('text', { x: xo(last, 5) + 10, y: y(task.rows[last].vals[5][0]) + 4, 'font-size': 13, 'font-weight': 'bold', fill: BLUE }, svg);
        ql.textContent = 'QUTCC'; }

        // Hover targets: one column per intensity bin
        task.rows.forEach(function (r, j) {
            var colW = pw / task.rows.length;
            var hit = el('rect', { x: M.l + colW * j, y: M.t, width: colW, height: ph, fill: 'transparent' }, svg);
            hit.addEventListener('mousemove', function (ev) { showTip(j, ev); cross.setAttribute('x1', x(j)); cross.setAttribute('x2', x(j)); cross.setAttribute('visibility', 'visible'); });
            hit.addEventListener('mouseleave', function () { tip.hidden = true; cross.setAttribute('visibility', 'hidden'); });
        });
    }

    function showTip(j, ev) {
        var r = DATA[current].rows[j];
        var rows = METHODS.map(function (m, i) { return { m: m, v: r.vals[i], i: i }; })
            .filter(function (o) { return visible(o.i); })
            .sort(function (a, b) { return a.v[0] - b.v[0]; });
        tip.innerHTML = '<div class="t1-tip-head">Intensity ' + r.bin + '</div>' + rows.map(function (o) {
            return '<div class="t1-tip-row' + (o.m.focus ? ' is-qutcc' : '') + '"><span><span class="t1-dot" style="background:' + o.m.color + '"></span>' + o.m.short + '</span><span>' +
                o.v[0].toFixed(3) + ' ± ' + o.v[1].toFixed(3) + '</span></div>';
        }).join('');
        tip.hidden = false;
        var box = chartBox.getBoundingClientRect();
        var left = ev.clientX - box.left + 14, top = ev.clientY - box.top + 10;
        if (left + tip.offsetWidth > box.width) left = ev.clientX - box.left - tip.offsetWidth - 14;
        tip.style.left = Math.max(0, left) + 'px';
        tip.style.top = Math.max(0, Math.min(top, box.height - tip.offsetHeight)) + 'px';
    }

    var buttons = document.querySelectorAll('#table1 .t1-btn');
    buttons.forEach(function (b) {
        b.addEventListener('click', function () {
            current = +b.dataset.task;
            buttons.forEach(function (o) { o.classList.toggle('active', o === b); });
            tip.hidden = true;
            draw();
        });
    });
    // Posterior-based / Quantile-based: pick one
    function applyMode() {
        document.querySelectorAll('#table1 .t1-group-btn').forEach(function (o) {
            var on = o.dataset.group === mode;
            o.classList.toggle('active', on);
            o.setAttribute('aria-checked', on);
        });
        document.querySelectorAll('.t1-legend-item').forEach(function (it, k) {
            it.classList.toggle('is-off', !visible(k));
        });
    }
    document.querySelectorAll('#table1 .t1-group-btn').forEach(function (b) {
        b.addEventListener('click', function () {
            mode = b.dataset.group;
            highlight = null;
            tip.hidden = true;
            applyMode();
            draw();
        });
    });
    applyMode();
    draw();
})();
</script>
