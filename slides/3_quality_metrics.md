
# Maximal Margin Classifier (MMC)
<div>

We further want to find the one that “**maximally**” separates the two classes
</div>
<div class="grid grid-cols-[9fr,4fr]">
<div>

* Pick the nearest points $\{z_i\}_i$<br> to the separating hyperplanes $\{H_\alpha\}_{\alpha \in \R}$
	* This fixes the points and forms a set of margins<br> (one for each $\alpha$)
* Then we compute MMC $\{\beta_j\}_j$ as the farthest $H_\alpha$ from $\{z_i\}$
	* The **support vectors** $\{z_i\}$ “support” the MMC

</div>
<div>
  <figure>
    <img src="/ESL_figure_12.1_L.png" style="width: 270px; position: relative">
    <figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
      <a href="https://hastie.su.domains/ElemStatLearn/printings/ESLII_print12.pdf#page=437">ESL Fig. 12.1 (left)</a>
    </figcaption>
  </figure>
</div>
</div>
<br>

* Need to solve:
$~~\underset{\beta_{0:p}}{\mathrm{argmax}} \big\{ M ~|~ y_i(\beta_0 + \beta_{p \times 1}^{\prime} x_i) \geq M, ~~~~i = 1:n, ~~~~||\beta|| = 1 \big\}$,
<br>where:
$M$ is the margin we want to maximize,<br>
$y_i(\beta_0 + \beta^{\prime} x_i)$ are shortest distances to hyperplane under $\sum \beta_j^2 = 1$
