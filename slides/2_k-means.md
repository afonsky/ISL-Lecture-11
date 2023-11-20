# Clustering intuition
<br>
<br>
<div class="grid grid-cols-[5fr,4fr] gap-10">
<div>
<br>
<br>

* Each cluster is represented by its
center
* All objects are assigned to the
closest center
* The goal is to find such centers that
form the most compact clusters
</div>
<div>
  <figure>
    <img src="/basics K-Means clustering algorithm.png" style="width: 500px !important;">
    <figcaption style="color:#b3b3b3ff; font-size: 11px; float: right;">Image source: <a href="https://medium.com/@msdasila90/basics-k-means-clustering-algorithm-a77c539c9e00">https://medium.com/@msdasila90/basics-k-means-clustering-algorithm-a77c539c9e00</a>
    </figcaption>
  </figure>
</div>
</div>

---

# Notation

* Consider a sample with $N$ objects $\{x_n\}_{n=1}^N$
* We will search for $K$ clusters with centers $\{\mu_1,\mu_2, ..., \mu_K\}$
* Criterion to find the best centers is minimum of **within-cluster distance**:
$$Q = \sum\limits_{n=1}^N \min\limits_k \rho (x_n, \mu_k) \rightarrow \min\limits_{\mu_1, ..., \mu_K}$$
* Each object $x_n$ is assigned to a cluster $z_n \in \{1, 2, ..., K\}$ as:
$$z_n = \argmin\limits_k \rho (x_n, \mu_k)$$

---

# General K-Means / K-Medians algorithm

<div class="bg-orange-100">

* ### Algorithm
   1. Initialize $\mu_1, ..., \mu_K$ from random training objects
   2. While not converged:
      1. For $n = 1, 2, ..., N$:<br>
         $z_n = \argmin\limits_k \rho (x_n, \mu_k)$ $~~~~~~~~~~~~~~~~~\leftarrow$ assign each object to the nearest center
      2. For $k = 1, 2, ..., K$:<br>
         $z_n = \argmin\limits_\mu \sum\limits_{n: z_n = k} \rho (x_n, \mu)$ $~~~~~~~~~\leftarrow$ update the centers
   3. Return $z_1, ..., z_N$
</div>

---

# Algorithm variations

* Distance $\rho (x_n, \mu_k)$ can be defined in different ways:
   * If $\rho (x_n, \mu_k) = \lVert x_n - \mu_k \rVert_2^2$
      * we get **K-Means algorithm**
   * If $\rho (x_n, \mu_k) = \lVert x_n - \mu_k \rVert_1$
      * we get **K-Medians algorithm**

---

# K-Means algorithm

<div class="bg-orange-100">

* ### Algorithm
   1. Initialize $\mu_j, j = 1, 2, ..., K$.
   2. While not converged:
      1. For $i = 1, 2, ..., N$:<br>
         find cluster number of $x_i$:<br>
         $z_i = \argmin\limits_{j \in \{1,2, ..., K\}} \lVert x_n - \mu_k \rVert_2^2$
      2. For $j = 1, 2, ..., K$:<br>
         $\mu_j = \frac{\sum\limits_{n=1}^N \mathbb{I} [z_n = j] x_i}{\sum\limits_{n=1}^N \mathbb{I} [z_n = j]}$
   3. Return $z_i, \mu_j$
</div>

---
layout: section
---

# K-Means demo

[https://cartography-playground.gitlab.io/playgrounds/clustering-comparison/](https://cartography-playground.gitlab.io/playgrounds/clustering-comparison/)

---
layout: iframe

# K-Means demo
url: https://cartography-playground.gitlab.io/playgrounds/clustering-comparison/
---

---

# Properties of K-Means

* Initialization:
   * Centers $\{\mu_k\}_{k=1}^K$ are usually initialized randomly from training objects
   * Number of clusters (and centers) $K$ is fixed. They act as a hyperparameters.
* Convergence criteria:
   * Iterations limit is reached
   * Centers stop changing significantly
   * Cluster assignments $\{z_n\}_{n=1}^N$ stop changing
* Solution:
   * Depends on starting positions of centers
   * Sensitive to outliers, may create single-object clusters
   * It is recommended to run the algorithm with several different initializations and select solution with the minimal within-cluster distance $Q$


---

# Elbow method

* How to estimate optimal number of clusters $K$?
* Consider within-cluster distances $Q^{(K)}$ for all possible $K$:
$$Q^{(K)} = \sum\limits_{n=1}^N \lVert x_n - \mu_{z_n} \rVert_2^2 \rightarrow \min\limits_{z_1, ..., z_N, \mu_1, ..., \mu_K}$$

<div>
<figure>
 <img src="/elbow_1.png" style="width: 1000px !important;">
</figure>
</div>

---

# Elbow method

<br>
<br>
<div class="grid grid-cols-[4fr,5fr] gap-10">
<div>

* Within-cluster distances $Q^{(K)}$ decreases with increasing $K$
* The dependence has elbow at the
optimal number of clusters ($K = 5$)
* Let’s try to formalize it
</div>
<div>
  <figure>
    <img src="/elbow_2.png" style="width: 500px !important;">
  </figure>
</div>
</div>

---

# Elbow method

<br>
<br>
<div class="grid grid-cols-[4fr,5fr] gap-10">
<div>

* Let's define relative change of within-cluster distance:
$$D(K) = \frac{\lvert Q^{(K+1)} - Q^{(K)} \rvert}{\lvert Q^{(K)} - Q^{(K-1)} \rvert}$$
   * This function takes small value for the optimal number of clusters

</div>
<div>
  <figure>
    <img src="/elbow_3.png" style="width: 500px !important;">
  </figure>
</div>
</div>