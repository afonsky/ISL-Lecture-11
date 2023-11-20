# Intuition

<br>
<br>
<div class="grid grid-cols-[4fr,5fr] gap-10">
<div>
<br>
<br>

* Let’s ask K-Means to find many clusters
* Each found cluster will be inside a real cluster
* Now, let’s unite neighbor found clusters into one
* As a result, we will get clusters with more complex shapes
</div>
<div>
  <figure>
    <img src="/clusters_2.png" style="width: 500px !important;">
  </figure>
</div>
</div>

---

# Agglomerative clustering

<figure>
  <img src="/agglomerative_clustering.png" style="width: 900px !important;">
  <figcaption style="color:#b3b3b3ff; font-size: 11px; float: right;">Image source: <a href="https://www.brandidea.com/hierarchicalclustering.html">https://www.brandidea.com/hierarchicalclustering.html</a>
  </figcaption>
</figure>

---

# Dendrogram

<br>
<br>
<div class="grid grid-cols-[4fr,5fr] gap-10">
<div>
<br>

* Agglomerative clustering algorithms build a dendrogram
* Dendrogram shows hierarchy of clusters in a data sample
* It contains information about objects inside each cluster and distances between these clusters
</div>
<div>
  <figure>
    <img src="/dendrogram_1.png" style="width: 500px !important;">
  </figure>
</div>
</div>

---

# Agglomerative clustering algorithm

<div class="bg-orange-100">

* ### Algorithm
   1. Initialize distance matrix $M \in \mathbb{R}^{N \times N}$ between singleton clusters $\{x_1\}, ..., \{x_N\}$
   2. Repeat until $1$ cluster is left:
      1. Pick closest pair of clusters $i$ and $j$
      2. Merge clusters $i$ and $j$
      3. Delete rows / columns from $M$ and add new column for merged cluster
      4. Recalculate distances between clusters
   3. Return hierarchical clustering of objects
</div>

---

# Linkage

#### In agglomerative clustering, **linkage** specifies how the distance between two clusters is calculated
<br>

* Nearest-neighbor (single link):
$$\rho(A, B) = \min\limits_{a \in A, b \in B} \rho(a, b)$$

* Furthest-neighbor (complete link):
$$\rho(A, B) = \max\limits_{a \in A, b \in B} \rho(a, b)$$

where $A = \{x_{i_1}, x_{i_2}, ...\}$ and $B = \{x_{j_1}, x_{j_2}, ...\}$ are two clusters

---

# Linkage

* Average (group average link):
$$\rho(A, B) = \frac{1}{N_A N_B} \sum\limits_{a \in A, b \in B} \rho(a, b)$$

* Closest centroid (centroid link):
$$\rho(A, B) = \rho(\mu_A, \mu_B)$$

where $\mu_A$ and $\mu_B$ are cluster centers

---

# Linkage comparison

<div>
  <figure>
    <img src="/linkage.png" style="width: 1000px !important;">
  </figure>
</div>

---

# Two approaches to hierarchical clustering

<div>
  <figure>
    <img src="/agglomerative_vs_divisive.png" style="width: 800px !important;">
      <figcaption style="color:#b3b3b3ff; font-size: 11px; float: right;">Image source: <a href="https://education.yandex.ru/handbook/ml/article/klasterizaciya/">https://education.yandex.ru/handbook/ml/article/klasterizaciya/</a>
    </figcaption>
  </figure>
</div>
