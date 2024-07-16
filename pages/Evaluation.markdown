---
layout: page
title: Evaluation and Ranking
menubar: home_menu
show_sidebar: false
hero_image: /images/BannerFETA.png
---

# 1. Evaluation metrics
## 1.1 Segmentation task

Four complementary evaluation metrics will be used to compute the rankings: 

- Dice similarity coefficient (DSC) to measure the spatial overlap [1] [2]. 
- The 95th percentile of Hausdorff distance (HD95) to quantify the contour distance.  
- Volume similarity to measure the volume difference [1].
- The Euler characteristic (EC), defined k-dimensional Betti numbers to quantify topological correctness [3] [4].
 
 
The implementations of DSC and VS can be found [**here**](https://github.com/Visceral-Project/EvaluateSegmentation
), HD95 can be found [**here**](https://github.com/google-deepmind/surface-distance), and Betti number and EC can be found [**here**](https://github.com/smilell/Topology-Evaluation).
 
## 1.2 Biometry task

The ranking will be based on the measurement error in percentage (ME) which is the difference between estimated measurement and the actual measurement in comparison to the actual measurement. 

In addition, we will compute the R2 coefficient between the predictions and the ground truth for each region to assess the spread of the prediction, but we will not use it in the ranking.  

**Note.** While the ranking will be based on the the biometric measurements, we encourage the participants to include the landmarks of the predictions if their method performs them.

# 2. Ranking


The two tasks will have independent rankings. 

For fetal tissue segmentation task, a final score incorporating the four metrics (DSC, HD95, VS, EC) will be determined. All metrics will be calculated for each label within each of the corresponding predicted label maps of the fetal brain volumes in the testing set. The mean and standard deviation of each label will be calculated, and the participating algorithms will be ranked from low to high (HD95, EC), where the lowest score receives the highest scoring rank (best), and from high to low (DSC, VS), where the highest value will receive highest scoring rank (best). For each label, the four rankings were added together, and the algorithm with the highest ranking was ranked first.  

Similarly, for biometry, a final score considering all cases using measurement error in percentage as a metric will be obtained for each team. For each case, each team will be ranked from low to high, where the lowest ME score receives the highest scoring rank (best). Hence, a ranking based on the sum of the ranking score across all cases can be calculated. 



### Reference
<small>
[1] C. Dong, C. C. Loy, and X. Tang, Accelerating the Super-Resolution Convolutional Neural Network, in Computer Vision ECCV 2016, vol. 9906, B. Leibe, J. Matas, N. Sebe, and M. Welling, Eds., in Lecture Notes in Computer Science, vol. 9906. , Cham: Springer International Publishing, 2016, doi: 10.1007/978-3-319-46475-6_25.   
[2] A. Gholipour et al., A normative spatiotemporal MRI atlas of the fetal brain for automatic segmentation and analysis of early brain growth, Sci. Rep., vol. 7, no. 476, 2017, doi: 10.1038/s41598-017-00525-w.   
[3] A. A. Taha and A. Hanbury, Metrics for evaluating 3D medical image segmentation: analysis, selection, and tool, BMC Med. Imaging, vol. 15, no. 1, p. 29, Dec. 2015, doi: 10.1186/s12880-015-0068-x.   
[4] L. Maier Hein et al., Metrics reloaded: Recommendations for image analysis validation. arXiv, Sep. 22, 2023. doi: 10.48550/arXiv.2206.01653.  
</small>

  