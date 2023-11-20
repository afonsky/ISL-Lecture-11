# Intuition

#### Density-Based Spatial Clustering of Applications with Noise (DBSCAN)
<br>
<div class="grid grid-cols-[5fr,4fr] gap-10">
<div>
<br>
<br>

* It supposed that clusters form dense groups of objects
* Areas between the clusters are sparse, with very low densities
* Let’s start from a random object and grow up a cluster by adding neighbor objects within some radius
</div>
<div>
  <figure>
    <img src="/dbscan_cluster.png" style="width: 500px !important;">
  </figure>
</div>
</div>

---

# DBSCAN idea \#1

<br>
<div class="grid grid-cols-[5fr,4fr] gap-10">
<div>
<br>
<br>

#### DBSCAN has two parameters:
* $\epsilon$ – radius of neighborhood of each object
* **MinPts** – minimal number of objects inside the neighborhood
</div>
<div>
  <figure>
    <img src="/dbscan_1.png" style="width: 500px !important;">
  </figure>
</div>
</div>

---

# DBSCAN idea \#2

<br>
<div class="grid grid-cols-[5fr,4fr] gap-10">
<div>
<br>
<br>

#### Three types of objects:
* <span style="color:#6E1B1A">**Core**</span>: has $\geq$ **MinPts** objects within $\epsilon$ neighborhood
* <span style="color:#9F8544">**Border**</span>: not <span style="color:#6E1B1A">**core**</span> object, has at least $1$ <span style="color:#6E1B1A">**core**</span> object within its $\epsilon$ neighborhood
* <span style="color:#07227C">**Noise**</span>: neither a <span style="color:#6E1B1A">**core**</span> nor a <span style="color:#9F8544">**border**</span> object

</div>
<div>
  <figure>
    <img src="/dbscan_1.png" style="width: 500px !important;">
  </figure>
</div>
</div>

---

# DBSCAN (short) algorithm

<div class="bg-orange-100">

* ### Algorithm
   1. Label all objects as <span style="color:#6E1B1A">**core**</span>, <span style="color:#9F8544">**border**</span>, or <span style="color:#07227C">**noise**</span> objects
   2. Eliminate noise objects
   3. Put an edge between all <span style="color:#6E1B1A">**core**</span> objects that are within $\epsilon$ of each other
   4. Make each group of connected <span style="color:#6E1B1A">**core**</span> objects into a separate cluster
   5. Assign each <span style="color:#9F8544">**border**</span> object to one of the clusters of its associated <span style="color:#6E1B1A">**core**</span> objects
</div>

---

# DBSCAN (detailed) algorithm

##### NB: pseudocode!
<div class="grid grid-cols-[5fr,4fr] gap-10">
<div>
```python
function dbscan(X, eps, min_pts):
    initialize NV = X # not visited objects 
    for x in NV:
        remove(NV, x) # mark as visited
        nbr = neighbours(x, eps) # set of neighbours
        if nbr.size < min_pts:
            mark_as_noise(x)
        else:
            C = new_cluster() 
            expand_cluster(x, nbr, C, eps, min_pts, NV)
            yield C
```
</div>
<div>
```python
function expand_cluster(x, nbr, C, eps, min_pts, NV):
	add(x, C)
	for x1 in nbr:
		if x1 in NV: # object not visited
			remove(NV, x1) # mark as visited
			nbr1 = neighbours(x1, eps)
			if nbr1.size >= min_pts:
				# join sets of neighbours
				merge(nbr, nbr_1) 
		if x1 not in any cluster:
			add(x1, C)
```
</div>
</div>
<br>

##### Source: [https://shestakoff.github.io/hse_se_ml/2020/l14-cluster/lecture-clust.slides#/4/5](https://shestakoff.github.io/hse_se_ml/2020/l14-cluster/lecture-clust.slides#/4/5)

---
layout: section
---

# DBSCAN demo

[https://www.naftaliharris.com/blog/visualizing-dbscan-clustering/](https://www.naftaliharris.com/blog/visualizing-dbscan-clustering/)

---
layout: iframe

url: https://www.naftaliharris.com/blog/visualizing-dbscan-clustering/
---

---

# DBSCAN key features

* Number of clusters is estimated automatically

* Robust to outliers
	* They are recognized as a noise

* Can find clusters with complex shapes

* Sensitive to objects density variations