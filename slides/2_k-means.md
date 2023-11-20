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
layout: iframe

# K-Means demo
url: https://cartography-playground.gitlab.io/playgrounds/clustering-comparison/
---

---

# Linear Algebra of a Hyperplane

* Affine set $L$ (a hyperplane) is defined as $L := \{x_{2 \times 1} ~|~\beta_0 + \beta_1 x_1 + \beta_2 x_2 = 0\}$

<div class="grid grid-cols-[3fr,2fr]">
<div>

* Properties of $L$:
   * $\forall x_1, x_2 \in L$ we have $\beta^{T}(x_1 - x_2) = 0$
      * i.e. $\vec\beta$ is **orthogonal** to $L$
         * So, $\vec{\beta}^{*} := \frac{\vec\beta}{||\vec\beta||}$ is a **normal** vector to $L$

      * $\forall x_0 \in L$, we have $\beta^{T}x_0 = -\beta_0$
      * $\forall x \in \R^p$, the **signed distance** is
<br> $d(L,x) = \beta^{*T} (x - x_0) \propto \beta^{T} (x - x_0)$

</div>
<div>
  <figure>
   <br>
   <br>
    <img src="/Hyperplane_ex.png" style="width: 500px">
    <figcaption style="color:#b3b3b3ff; font-size: 11px">Based on
      <a href="https://hastie.su.domains/ElemStatLearn/printings/ESLII_print12.pdf#page=149">ESL Fig. 4.15</a>
    </figcaption>
  </figure>
</div>
</div>

---

# Separating Hyperplanes

* We want to find a **separating hyperplane** (if possible), which perfectly separates the observations of two classes, $y = \pm 1$

$$
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x \lt 0\}}_{\text{\textcolor{grey}{y = -1}}}
\color{#006}\cup
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x = 0\}}_{\text{\textcolor{grey}{hyper-plane}}}
\color{#006}\cup
\color{grey}\underbrace{\color{#006}\{x ~|~\beta_0 + \beta^{T} x \gt 0\}}_{\text{\textcolor{grey}{y = 1}}}
$$

* **Training**: estimate $\beta_i$ parameters as $\hat{\beta}_i$
* **Inference**: classify new $x^{*}$ as $\mathrm{sign}(\beta_0 + \beta^{T} x^{*})$ 
   * Distance of $x_{p \times 1}^{*}$ to the hyperplane, $|\beta_0 + \beta^{T}x^{*}|$, indicates confidence of prediction
