# Frank Rosenblatt’s Perceptron (1958)
<div class="grid grid-cols-[3fr,2fr]">

* Developed by [Rosenblatt](https://en.wikipedia.org/wiki/Frank_Rosenblatt) 2 years after his PhD’56 at Cornell Aeronautical Laboratory
* Perceptron is a binary classifier<br> with a **hyperplane decision boundary**
* The algorithm minimizes the distance of misclassifications to the hyperplane
* **Goal**: minimize<br> $D(\beta, \beta_0) := -\sum_{i \in \cal{M}} y_i (\beta_0 + \beta^{\prime} x_i)$
	* where $\cal{M}$ is the set of misclassified points

<div>
  <figure>
    <img src="/Rosenblatt.png" style="width: 380px; position: relative">
    <figcaption style="color:#b3b3b3ff; font-size: 11px">Image source:
      <a href="https://news.cornell.edu/stories/2019/09/professors-perceptron-paved-way-ai-60-years-too-soon">https://news.cornell.edu/stories/2019/09/professors-perceptron-paved-way-ai-60-years-too-soon</a>
    </figcaption>
  </figure>
</div>
</div>