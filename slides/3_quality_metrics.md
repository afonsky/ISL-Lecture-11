# Quality metrics

#### There are two kinds of quality metrics for clustering:

* Supervised
  * Based on ground truth of object labels
  * Invariant to cluster naming
* Unsupervised
  * Based on intuition about “good” clusters:
    * Objects from the same cluster are similar / close to each other
    * Objects from different clusters are dissimilar / distant from each other

---

# Rand Index

#### Rand Index ($RI$) is supervised quality metric defined as:
$$RI = \frac{\textcolor{red}{TP} + \textcolor{blue}{TN}}{\textcolor{red}{TP} + \textcolor{blue}{TN} + \textcolor{orange}{FP} + \textcolor{green}{FN}}$$
where:
* $\textcolor{red}{TP}$ – number of pairs in the same cluster in predictions and the ground truth
* $\textcolor{blue}{TN}$ – number of pairs from different clusters in predictions and the ground truth
* $\textcolor{orange}{FP}$ – number of pairs in the same cluster in predictions, but from different clusters in the ground truth
* $\textcolor{green}{FN}$ – number of pairs in the same cluster in the ground truth, but from the different clusters in predictions

---

# Adjusted Rand Index

#### Adjusted Rand Index ($ARI$) is a modification of $RI$:
$$ARI = \frac{RI - RI_{\mathrm{expected}}}{RI_{\max} - RI_{\mathrm{expected}}}$$
<br>

* $ARI$ has values:
  * close to $0$ for random labeling independently of the number
of clusters and samples
  * exactly $1$ when the clustering is ideal

---

# Metrics for classification

* $\mathrm{Precision} = \dfrac{TP}{TP + FN}$

* $\mathrm{Recall} = \dfrac{TP}{TP + FP}$

* F1-score, $\mathrm{F1} = \dfrac{2 \times \mathrm{Precision} \times \mathrm{Recall}}{\mathrm{Precision} + \mathrm{Recall}}$

* Fowlkes-Mallows Index, $FMI = \dfrac{TP}{\sqrt{(TP + FP)(TP + FN)}}$

* etc.

---

# Silhouette

#### Silhouette is unsupervised quality metric defined as:
$$\mathrm{Silhouette} = \frac{1}{N}\sum\limits_{i=1}^N \frac{d_i - s_i}{\max\{d_i, s_i\}}$$
where:
* $s_i$ - mean distance between the $i$-th object and all objects in the same cluster
* $d_i$ - mean distance between the $i$-th object and all objects in the nearest
cluster

---

# Ex. of quality metrics for clustering

<br>
<br>
<div class="grid grid-cols-[1fr,1fr] gap-10">
<div>
  <figure>
    <img src="/clusters.png" style="width: 380px !important;">
  </figure>
</div>
<div>
  <figure>
    <img src="/quality_metrics.png" style="width: 500px !important;">
  </figure>
</div>
</div>

---

# K-Means Limitations

* K-Means looks for cluster centers
  * All objects are separated between these centers based on the closest distances
* In result, objects of a cluster concentrated around its center
* Real clusters may have more difficult forms, like circles or moons
* They are divided by K-Means between several centers