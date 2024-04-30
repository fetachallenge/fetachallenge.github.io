---
layout: page
title: Fetal Tissue Annotation and Segmentation
subtitle: MICCAI 2024 Challenge
menubar: home_menu
hero_image: /images/BannerFETA.png
show_sidebar: false
---



Congenital disorders are one of the leading causes of infant mortality worldwide [1]. In-utero MRI of the fetal brain has started to emerge as a valuable tool for investigating the neurological development of fetuses with congenital disorders. Fetal MRI can aid in the future development of clinical risk stratification tools for early interventions, treatments, and clinical counseling. Moreover, fetal MRI is a powerful tool to portray the complex neurodevelopmental events during human gestation, which remain to be completely characterized. Acquisition and analysis of in-utero MRI of the fetal brain requires collaboration from specialized clinical centers because image cohorts of this vulnerable patient populations are small and heterogeneous (e.g. variability in image acquisition parameters between sites). In the majority of specialized clinical centers working with fetal MRI, assessments are performed using only 2D biometric measurements derived from thick 2D slice acquisitions, although recent work has demonstrated the ability to perform these measurements in 3D super-resolution reconstructed volumes [2], [3].  

Automated biometry, segmentation, and quantification of the highly complex and rapidly changing brain morphology prior to birth in MRI data would improve the diagnostic process, as manual annotations are both time consuming and subject to human error and inter-rater variability. It is clinically relevant to analyze information such as the shape or volume of the developing brain structures, as many congenital disorders cause subtle changes to these tissue compartments [4], [5], [6], [7]. Existing growth data is mainly based on normally developing brains [2], [8], [9], and growth data for many pathologies and congenital disorders is lacking. Thus, robust methods for automatic quantification of the developing human brain across different scanners and image acquisition protocols would be a first step in performing such an analysis. 

From a technical standpoint, there are many challenges that an automatic segmentation method of the fetal brain would need to overcome. During prenatal development, the physiology of the human brain changes while its structure undergoes developmental reorganization. In addition, the quality of the images is often poor due to fetal and maternal movement and imaging artefacts [10], [11], while partial volume effects frequently lead to blurring of boundary between tissues. Finally, compared to the healthy controls, structures of an abnormal fetal brain often have a different morphology. This can make it challenging for an automatic method to recognize what the structures are. The field of fetal MRI has so far been understudied due to challenges in imaging and due to the lack of public, curated, and annotated ground truth data. Site and MRI scanner harmonization, paired with automated and robust methods for MRI analyses are needed in order to increase sample size for adequate power of these studies.   

In our first FeTA edition (FeTA 2021), we used the first publicly available dataset of fetal brain MRI images [12] to encourage participating teams to develop automatic brain tissue segmentation methods [13]. Based on its success, we extended the challenge in FeTA 2022 by studying the generalizability of segmentation algorithms across different sites, acquired from different image acquisition protocols and MRI scanners) (paper under review [**link**](https://arxiv.org/abs/2402.09463)). 

In FeTA 2024 we aim to improve and extend the established FeTA Challenge in two ways: Firstly, we introduce a new task to automatically derive clinically relevant biometry typically used in practice for fetal evaluation. Secondly, following the recent rise in popularity of low-cost low-field MRI systems [14] which aim at democratizing MRI access world-wide, we extend the generalizability assessment of segmentation methods by including low-field (0.55T) MRI data. FeTA 2024 challenge is an important step towards the development of effective, domain-generalizable and reproducible methods for analyzing high resolution reconstructed MR images of the developing fetal brain from gestational week 21-36. It will include a new clinically relevant task on automated biometry measurements and data from five different sites and magnetic fields including recent low-field systems. Such new algorithms will have the potential to support clinicians in the assessment of fetal brain MRI in-utero in many ways: to better understand the underlying causes of congenital disorders and ultimately to guide the development of antenatal/postnatal guidelines and clinical risk stratification tools for early interventions, treatments, and care management decisions across hospitals and research institutions worldwide.    


The accepted full proposal can be found [here](https://zenodo.org/records/10986046).


### References
<small>
[1] Child mortality and causes of death. Accessed: Jan. 10, 2024. [Online]. Available: https://www.who.int/data/gho/data/themes/topics/  
[2] V. Kyriakopoulou et al., Normative biometry of the fetal brain using magnetic resonance imaging, Brain Struct. Funct., vol. 222, no. 5, 2017, doi: 10.1007/s00429-016-1342-6.   
[3] M. Khawam et al., Fetal Brain Biometric Measurements on 3D Super-Resolution Reconstructed T2-Weighted MRI: An Intra- and Inter-observer Agreement Study, Front. Pediatr., vol. 9, p. 639746, Aug. 2021, doi: 10.3389/fped.2021.639746.  
[4] G. Egaña-Ugrinovic, M. Sanz-Cortes, F. Figueras, N. Bargalló, and E. Gratacós, Differences in cortical development assessed by fetal MRI in late-onset intrauterine growth restriction, Am. J. Obstet. Gynecol., vol. 209, no. 2, Aug. 2013, doi: 10.1016/j.ajog.2013.04.008.  
[5] A. Zugazaga Cortazar, C. Martín Martinez, C. Duran Feliubadalo, M. R. Bella Cueto, and L. Serra, Magnetic resonance imaging in the prenatal diagnosis of neural tube defects, Insights Imaging, vol. 4, no. 2, Apr. 2013, doi : 10.1007/s13244-013-0223-2.  
[6] C. Clouchoux et al., Delayed cortical development in fetuses with complex congenital heart disease, Cereb. Cortex, vol. 23, no. 12, Art. no. 12, 2013.  
[7] C. K. Rollins et al., Regional Brain Growth Trajectories in Fetuses with Congenital Heart Disease, Ann. Neurol., vol. 89, no. 1, Jan. 2021, doi: 10.1002/ana.25940.  
[8] D. Prayer et al., MRI of normal fetal brain development, Eur. J. Radiol., vol. 57, no. 2, Feb. 2006, doi: 10.1016/j.ejrad.2005.11.020.  
[9] D. A. Jarvis, C. R. Finney, and P. D. Griffiths, Normative volume measurements of the fetal intra-cranial compartments using 3D volume in utero MR imaging, Eur. Radiol., vol. 29, no. 7, Jul. 2019, doi: 10.1007/s00330-018-5938-5.  
[10] T. Sanchez, O. Esteban, Y. Gomez, E. Eixarch, and M. B. Cuadra, FetMRQC: Automated Quality Control for Fetal Brain MRI, in Perinatal, Preterm and Paediatric Image Analysis, vol. 14246, D. Link-Sourani, E. Abaci Turk, C. Macgowan, J. Hutter, A. Melbourne, and R. Licandro, Eds., in Lecture Notes in Computer Science, vol. 14246. , Cham: Springer Nature Switzerland, 2023, doi: 10.1007/978-3-031-45544-5_1.  
[11] T. Sanchez et al., FetMRQC: an open-source machine learning framework for multi-centric fetal brain MRI quality control. arXiv, Nov. 08, 2023. Accessed: Jan. 10, 2024. [Online]. Available: http://arxiv.org/abs/2311.04780  
[12] K. Payette et al., An automatic multi-tissue human fetal brain segmentation benchmark using the Fetal Tissue Annotation Dataset, Sci. Data, vol. 8, no. 1, Art. no. 1, Jul. 2021, doi: 10.1038/s41597-021-00946-3.  
[13] K. Payette et al., Fetal brain tissue annotation and segmentation challenge results, Med. Image Anal., vol. 88, p. 102833, Aug. 2023, doi: 10.1016/j.media.2023.102833.  
[14] J. Aviles Verdera et al., Reliability and Feasibility of Low-Field-Strength Fetal MRI at 0.55 T during Pregnancy, Radiology, vol. 309, no. 1, p. e223050, Oct. 2023, doi: 10.1148/radiol.223050. 
</small>
