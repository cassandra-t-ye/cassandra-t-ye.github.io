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
}
</style>

<div class="section">
    <b style="font-weight: bold; font-size: 24px;">Abstract</b>
    
    <div class="row">
        <div class="col-md-12">
            Deep learning models often hallucinate, producing realistic artifacts that are not truly present in the sample. This can have dire consequences for scientific and medical inverse problems, such as MRI and microscopy denoising, where accuracy is more important than perceptual quality. Uncertainty quantification techniques, such as conformal prediction, can pinpoint outliers and provide guarantees for image regression tasks, improving reliability. However, existing methods utilize a linear constant scaling factor to calibrate uncertainty bounds, resulting in larger, less informative bounds. We propose QUTCC, a quantile uncertainty training and calibration technique that enables nonlinear, non-uniform scaling of quantile predictions to enable tighter uncertainty estimates. Using a U-Net architecture with a quantile embedding, QUTCC enables the prediction of the full conditional distribution of quantiles for the imaging task. During calibration, QUTCC generates uncertainty bounds by iteratively querying the network for upper and lower quantiles, progressively refining the bounds to obtain a tighter interval that captures the desired coverage. We evaluate our method on several denoising tasks as well as compressive MRI reconstruction. Our method successfully pinpoints hallucinations in image estimates and consistently achieves tighter uncertainty intervals than prior methods while maintaining the same statistical coverage. 
        </div>
    </div>
</div>

<div class="section" style="margin-top: 60px;">
    <h2 style="font-weight: bold; font-size: 24px; margin-bottom: 20px;">Quantile Regression: Pinball Loss</h2>
    
    <div class="text-content">
        <p>
            Quantile regression is a general approach to estimate the conditional quantiles of a target distribution rather than the mean of a response variable. This is often accomplished by leveraging an asymmetric loss function, called pinball loss (Fig. 1), tailored to the specified quantile level.
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
            In contrast, our work investigates learning the full spectrum of quantiles, commonly referred to as <a href='https://library.seg.org/doi/10.1190/tle44020133.1#:~:text=The%20simultaneous%20quantile%20regression%20method,method%20on%20synthetic%20Kimberlina%20data.', target="_blank", style ="color: #0066cc; text-decoration: none;"><strong>Simultaneous Quantile Regression (SQR)</strong></a>, for inverse image tasks.
        </p>
    </div>
</div>

<div class="section" style="margin-top: 60px;">
    <b style="font-size: 24px;">Our Method: QUTCC</b>
    <div class="row">
        <div class="col-sm mt-3 mt-md-0" style="text-align: center;">
            {% include figure.html path="assets/img/proj_2_qutcc/fig_1_gif.gif" title="Fig. 1 Summary" class="img-fluid " width="700px" height="auto" %}        
            <div class="caption" style="text-align: left;">
                <!-- Caption content here if needed -->
            </div>
        </div>
        <div class="col-md-12">
            <p>
                We propose <strong>QUTCC</strong> (pronounced: CUTESY), short for <strong>Quantile Uncertainty Training and Conformal Calibration</strong>, a novel method for simultaneous quantile prediction and conformal calibration that enables efficient and accurate uncertainty quantification for imaging inverse problems. QUTCC uses a single neural network to estimate a distribution of quantiles. During the conformal calibration step, QUTCC applies a non-uniform, nonlinear scaling to the uncertainty bounds, compared to constant scaling used by prior methods. This results in smaller and potentially more informative uncertainty intervals. Additionally, because all quantiles are learned during training, QUTCC can query the full quantile range at inference time to construct a pixel-wise estimate of the underlying probability distribution.
            </p>
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
    function pinballLoss(u) {
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
        const px = uToPx(u);
        const py = lossToPy(pinballLoss(u));
        if (i === 0) ctx.moveTo(px, py);
        else ctx.lineTo(px, py);
    }
    ctx.stroke();

    // Show q value
    ctx.fillStyle = '#007bff';
    ctx.font = 'bold 16px Arial';
    ctx.textAlign = 'left';
    ctx.fillText('q = ' + q.toFixed(2), margin + 10, margin + 20);
}

    
    function updateVisualization() {
        var q = parseFloat(slider.value);
        display.textContent = q.toFixed(2);
        drawPinballLoss(q);
    }
    
    updateVisualization();
    slider.addEventListener('input', updateVisualization);
});
</script>