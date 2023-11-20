---
theme: seriph
addons:
  - slidev-addon-ultracharger
addonsConfig:
  ultracharger:
    inlineSvg:
      markersWorkaround: false
    disable:
      - metaFooter
      - tocFooter
NObackground: >-
  https://images.unsplash.com/photo-1511149755252-35875b273fd6?ixlib=rb-4.0.3&dl=leon-contreras-qpdfU6vehgs-unsplash.jpg&w=1920&q=80&fm=jpg&crop=entropy&cs=tinysrgb
background: /ship2.jpg
highlighter: shiki
routerMode: hash
lineNumbers: false
info: >
  ## Slidev ultracharger demo

  A doc / demo presentation for the ultracharger set of
  [Sli.dev](https://sli.dev) addons.

  It also acts as an experimental area for some features I can imagine.


  NB: [Source code
  available](https://github.com/twitwi/slidev-addon-ultracharger)
css: windicss
title: Introduction to Statistical Learning
subtitle: Unsupervised Learning
date: 21/11/2023
venue: HSE
author: Alexey Boldyrev, Maksim Karpov, Oleg Melnikov
ghPrefix: https://github.com/twitwi/slidev-addon-ultracharger/blob/main/
ghSelf: https://github.com/twitwi/slidev-addon-ultracharger-demo/blob/main/
---

# <span style="font-size:28.0pt" v-html="$slidev.configs.title?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:32.0pt" v-html="$slidev.configs.subtitle?.replaceAll(' ', '<br/>')"></span>
# <span style="font-size:18.0pt" v-html="$slidev.configs.author?.replaceAll(' ', '<br/>')"></span>

<span style="font-size:18.0pt" v-html="$slidev.configs.date?.replaceAll(' ', '<br/>')"></span>

<div>
<br>
<span style="color:#b3b3b3ff; font-size: 11px; float: right;">Image credit: ‘The Mayﬂower at Sea’<br> by Granville Perkins, 1876<br>
Wallach Division Picture Collection<br> The New York Public Library.
</span>
</div>

<style>
  :deep(footer) { padding-bottom: 3em !important; }
</style>

<!--
NB: This demo uses a custom syntax (using preparser extensions), with all the @@@@.
-->

---
src: ./slides/0_attendance.md
---

---
src: ./slides/0_outline.md
---

---
src: ./slides/1_clustering.md
---

---
src: ./slides/2_k-means.md
---

---
src: ./slides/3_quality_metrics.md
---

---
src: ./slides/4_summary.md
---

---
src: ./slides/5_SVC.md
---

---
src: ./slides/6_SVM.md
---

---
src: ./slides/0_end.md
---