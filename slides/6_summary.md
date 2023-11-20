# Overview of clustering methods

<div>
  <figure>
    <img src="/clustering_overview.png" style="width: 800px !important;">
  </figure>
</div>

---

# Summary of clustering methods

* K-Means limitations
	* Find clusters that concentrated only around one center
	* Can not find clusters with complex forms

* Hierarchical clustering
	* Agglomerative clustering
	* Dendrogram contains information about clusters structure

* DBSCAN
	* Density-Based Spatial Clustering of Applications with Noise
	* Able to find complex clusters and outliers

---

# Ex. Dimension reduction with PCA

<div>
  <figure>
    <img src="/ISLP_figure_12.2.png" style="width: 750px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; position: relative; top: 10px; left: 530px;">Based on <a href="https://hastie.su.domains/ISLP/ISLP_website.pdf#page=515">ISLP Fig. 12.2</a>
  </figcaption>
  </figure>
</div>
<br>
<br>

* Problem: Least squared regression fails for data matrix $X_{n \times p}$ with $p >> n$
* For **correlated** and redundant features, we can **reduce dimensionality** with PCA

---

# Ex. Microarray
<div class="grid grid-cols-[4fr,4fr] gap-10">
<div>
  <figure>
    <img src="/microarray.png" style="width: 370px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; position: relative; top: 10px; left: -30px;">Image source:<br> <a href="https://bioramble.wordpress.com/2015/08/03/heatmaps-part-3-how-to-create-a-microarray-heatmap-with-r/">https://bioramble.wordpress.com/2015/08/03/heatmaps-part-3-how-to-create-a-microarray-heatmap-with-r/</a>
  </figcaption>
  </figure>
</div>
<div>

* Wide dataset
* If we apply PCA, we compute 16k of **PCs ordered** by their decreasing variance
* We use **scree** (elbow) plot to identify (a few, say 10) PCs explaining most variance
</div>
</div>
<br>

* We **throw away** all other PCs
	* We can do this because all **PCs are additive**, i.e. they are **uncorrelated**
	* Note that we still need **all** 16k of original features
* The output is data matrix $Z_{144 \times 10}$ of 10 PCs (columns)
* Now, apply regression model

---

# Ex. PCA's eigenfaces (a.k.a. ghost faces)

#### We can represent a face image as a **linear combination** of weighted eigenfaces <br>
$\small \mathrm{Original~photo_1} = 1.35 \cdot \mathrm{Eigenface_1} - 2.20 \cdot \mathrm{Eigenface_2} + ... + 0.02 \cdot \mathrm{Eigenface_m}$
#### Ex: Assume "normalized" $m = 2429$ images of size $n = 19 \times 19 = 361$
<div class="grid grid-cols-[5fr,3fr] gap-1">
<div>

* Stack them vertically in matrix $X_{n \times m}$
* Apply PCA to build $2429$ PCs, $Z_{n \times m}$
	* Each PC is a $19 \times 19$ eigenvector (eigenface)
* Let's keep $1000$ PCs with greatest variance
	* This is our lower-dimensional set of basis vectors
</div>
<div>
<figure>
	<img src="/eigenfaces.png" style="width: 490px !important;">
	<figcaption style="color:#b3b3b3ff; font-size: 11px; position: relative; top: 10px; left: 10px;">Images sources: <a href="https://en.wikipedia.org/wiki/Eigenface">https://en.wikipedia.org/wiki/Eigenface</a>,<br> <a href="https://scikit-learn.org/stable/auto_examples/applications/plot_face_recognition.html">https://scikit-learn.org/stable/auto_examples/applications/plot_face_recognition.html</a>
	</figcaption>
</figure>
</div>
</div>

* Any face in $X$ is $\approx$ linear combination of a lower-dimensional space of $Z_{n \times 1000}$
* PCA here is expensive, but it allows significant storage savings
* More PCs implies better approximation

---

# Recap of Principal Component Analysis (PCA)

* Each PC $Z_k$ is a linear combination of **all** original features $\{X_{j, n \times 1}\}$<br>
$\small Z_k = \begin{bmatrix} Z_{1k} \\ \vdots \\ Z_{nk} \end{bmatrix} = X \phi_k = \sum\limits_{j=1}^p \phi_{jk}X_j~~~$ given $\lVert \phi_k \rVert_2^2 = \sum\limits_{j=1}^p \phi_{jk}^2 = 1$, $\forall k = 1:p$<br>
where $\phi_{k, p \times p}$ is a **loading vector** for $k$th PC; $z_{ik}$ is the $i$th **score of the** $k$**th PC**

$\small Z = \color{grey}\underbrace{\color{#006}{[Z_1, ..., Z_p]}}_{\mathrm{PCs}}
\color{#006} =  {\scriptsize \begin{bmatrix} z_{11} & \ldots & z_{1p} \\ \vdots & \ddots & \vdots \\ z_{n1} & \ldots & z_{np}\end{bmatrix}} = {\scriptsize \begin{bmatrix} x_{11} & \ldots & x_{1p} \\ \vdots & \ddots & \vdots \\ x_{n1} & \ldots & x_{np}\end{bmatrix}} {\scriptsize \begin{bmatrix}\phi_{11} & \ldots & \phi_{1p} \\ \vdots & \ddots & \vdots \\ \phi_{p1} & \ldots & \phi_{pp}\end{bmatrix}} = X \color{grey}\underbrace{\color{#006}{[\phi_1, ..., \phi_p]}}_{\mathrm{loadings}}
\color{#006} = X \phi$
<br>
<br>

* The PCs are ordered by **decreasing variance**: $\mathbb{V}Z_1 \geq \mathbb{V}Z_2 \geq ... \geq \mathbb{V}Z_p$

---

# Recap of Principal Component Analysis (PCA)

* The PCs are ordered by **decreasing variance**: $\mathbb{V}Z_1 \geq \mathbb{V}Z_2 \geq ... \geq \mathbb{V}Z_p$
	* Use **scree plot** to identify "useless" PCs, which do not explain variability of $\{X_j\}$

* PCs and loadings are **orthogonal**, i.e. $\rho_{Z_i, Z_j} = I_{(i=j)}$
	* So, assuming centered $Z_i$, we have $Z_i^\prime Z_j = (n - 1) \mathbb{V} Z_i \cdot I_{(i=j)}$

* Also, $\sum \mathbb{V}Z_i =$ **total variability** of $X$ features,<br> where $\sum \mathbb{V}X_j$ ignores correlations b/w $X_j$
	* Total variance of PCs is sum of individual variances
		* which is not true about correlated $X_j$

---

# Scree plot: Proportion of Variance Explained (PVE)

<div>
  <figure>
    <img src="/ISLP_figure_12.3.png" style="width: 450px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; position: relative; top: 10px; left: 30px;">Image source: <a href="https://hastie.su.domains/ISLP/ISLP_website.pdf#page=518">ISLP Fig. 12.3</a>
  </figcaption>
  </figure>
</div>
<br>

* Since all $\mathbb{V}Z_j$ are **additive** ($Z_j$'s are uncorrelated)
	* Thus, we can meaningfully compare their variances individually or cumulatively
* **PVE** is $\frac{\mathbb{V}Z_j}{\sum_j\mathbb{V}Z_j}$, just a fraction of total variance
* Once plotted, we look for the "elbow" shape after which we can discard other PCs
	* Alternatively, we can threshold PCs after, say, 95% of cumulative variance is explained

---

# PCA training

* First, we find a loading vector, $\phi_1$, of PC1 by maximizing its variance:<br>
$\small \phi_1 := \argmax\limits_{\phi_1^\ast} \big\{\lVert z_{i1} \rVert_2 ~~|~~ \lVert \phi_1^\ast \rVert_2 = 1 \big\} = \argmax\limits_{\phi_1^\ast} \bigg\{\sum\limits_{i=1}^n \big(\sum\limits_{j=1}^p \phi_{j1}^\ast x_{ij} \big)^2 ~~|~~ \lVert \phi_1^\ast \rVert_2 = 1 \bigg\}$
	* Basically, this is a search for $\phi_1$ in the direction of largest variability of $\{X_j\}$

<div class="grid grid-cols-[5fr,3fr] gap-4">
<div>

* Then we look for $\phi_2$ with an additional constraint:<br>
$\argmax\limits_{\phi_1^\ast} \big\{\lVert z_{i2} \rVert_2 ~~|~~ \lVert \phi_2^\ast \rVert_2 = 1, ~\rho_{\phi_1, \phi_2^\ast} = 0 \big\}$
* Continue until $\phi_p$, which is orthogonal to $\phi_1, ..., \phi_{p-1}$
* It so happens that we will have all PCs<br> orthogonal as well
* Note: ranking PCs by decreasing variance is possible because of they are uncorrelated
</div>
<div>
<br>
<figure>
	<img src="/ESL_figure_3.9.png" style="width: 265px !important;">
	<figcaption style="color:#b3b3b3ff; font-size: 11px; position: relative; top: 10px; left: 140px;">Image source: <a href="https://hastie.su.domains/ElemStatLearn/printings/ESLII_print12.pdf#page=86">ESL Fig. 3.9</a>
	</figcaption>
</figure>
</div>
</div>