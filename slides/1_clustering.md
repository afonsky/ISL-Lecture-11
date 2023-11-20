# Clustering vs classification

<br>
<br>
<div class="grid grid-cols-[5fr,4fr] gap-10">
<div>

* In **classification**, we have object
features $X$ and class labels $y \in \{0, 1\}$
* A classifier learns decision rule $f$,<br> so
that $f(X) \approx y$
* The trained classifier predicts class
labels for new objects
</div>
<div>
  <figure>
    <img src="/classification_example.png" style="width: 500px !important;">
    <figcaption style="color:#b3b3b3ff; font-size: 11px; float: right;"><span>Classification example</span>
    </figcaption>
  </figure>
</div>
</div>

---

# Clustering vs classification

<br>
<br>
<div class="grid grid-cols-[5fr,4fr] gap-10">
<div>

* In **clustering**, we don’t have class
labels $y$
* The goal is to divide all objects into
separate groups using only object
features $X$
* Objects inside groups are similar
* Objects from different groups are
dissimilar
</div>
<div>
  <figure>
    <img src="/clustering_example.png" style="width: 500px !important;">
    <figcaption style="color:#b3b3b3ff; font-size: 11px; float: right;"><span>Clustering example</span>
    </figcaption>
  </figure>
</div>
</div>

---

# Clustering example

<div>
  <figure>
    <img src="/em_clusters_example.png" style="width: 400px !important;">
<!--     <figcaption style="color:#b3b3b3ff; font-size: 11px; float: center;"><span>
    Clusters in electromagnetic calorimeter of KTeV experiment for $K \rightarrow \pi^0 \pi^0$ decay
  </span>
    </figcaption> -->
  </figure>
</div>
<div style="color:#b3b3b3ff; font-size: 11px; float: center;">

Clusters in electromagnetic calorimeter of KTeV experiment for $\textcolor{#B3B3B3}{K \rightarrow \pi^0 \pi^0}$ decay
  </div>

---

# Clustering assumptions

#### Most of clustering algorithms are based on the following assumptions:

* Objects form dense clusters
* Objects from one cluster are similar
* Objects from different clusters are dissimilar
* Objects similarity is often based on distance between them
* Distances between neighbors within one cluster are smaller than between
objects from different clusters