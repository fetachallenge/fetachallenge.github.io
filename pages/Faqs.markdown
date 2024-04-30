---
layout: page
title: Frequently Asked Questions
menubar: home_menu
show_sidebar: false
hero_image: /images/Feta_2024_2.png
---
{% include notification.html
message="FAQs to be updated - currently contain info from FeTA 2021 "
icon="false"
status="is-success" %}
***

## General questions on the challenge and dataset

* What's new about FetA Challenge 2024 compared to previous editions?

In FeTA 2024 we aim to improve and extend the established FeTA Challenge in two ways: Firstly, we introduce a new task to automatically derive clinically relevant biometry typically used in practice for fetal evaluation. Secondly, following the recent rise in popularity of low-cost low-field MRI systems which aim at democratizing MRI access world-wide, we extend the generalizability assessment of segmentation methods by including low-field (0.55T) MRI data. FeTA 2024 challenge is an important step towards the development of effective, domain-generalizable and reproducible methods for analyzing high resolution reconstructed MR images of the developing fetal brain from gestational week 21-36.

* Where can I find the submitted FeTa challenge proposals for supplementary information?

All challenge proposals are available on Zenodo:

[FetA Challenge 2024](https://zenodo.org/records/10986046)

FetA Challenge 2022 (Not available)

[FetA Challenge 2021](https://zenodo.org/records/6362587)


* I found a link for a FeTA Dataset on Zenodo, is that related to the challenge?

There was a version of the FeTA dataset on Zenodo related to a paper that is currently in revision. However, the dataset to be used for the FeTA 2024 challenge is a larger version of the Zenodo dataset with a wider range of gestational ages, pathologies, and super-resolution reconstruction methods. This dataset can be downloaded from Synapse after registering to the challenge and for the Synapse website.

* Can I use my own data while creating my segmentation algorithm?

The participants can use publicly available data as desired, but they should document whatever is used in the description of their algorithm. Participants may modify the training data as they wish as long as everything is documented. Synthetic data should be able to be made available upon request. Non-public data may not be used, this is for fairness of comparison.

* What is the test dataset like?

The test dataset consists of 40 unique 3D fetal brain volumes (20 cases reconstructed with the mialSR reconstruction method, 20 cases reconstructed with the irtk reconstruction method). The resolution of the test dataset cases will be the same as in the training dataset (for the respective reconstruction method), and cover the same range and distribution of gestational ages and pathologies. The acquisition and preprocessing of the images in the test dataset is the same as those in the training  dataset. 

* The training data includes data generated with two different reconstructions methods. Is this going to be the case for the test data, and if yes, will we receive information on the reconstruction method used?

The test cases are representative of the training data. Both reconstruction methods (modalities) will be equally present in the test dataset. The file naming, meta data and folder structure will be the same for the test set as it was for the training set.

# Questions about submitting the model

* Are you going to release the test dataset so that we can evaluate our model locally?

No, the test dataset is not going to be made publicly available.

* Is there a limit on the number of submissions per team?

We allow one submission per team. The only exception is when a team submits models that are significantly different from each other.

* Are you going to give feedback to us regarding the accuracy of our model?

No, in the test stage, we will only return if your Docker submission is working or not. In case it is not working, we will contact the team.

* During the testing of our model, will the information on the gestational age be used as input?

Yes, this information can be used by the model. To make it easy to access, the information is stored as a JSON file in the same subject folder named 'sub-[ID]_meta.json'.

* During the testing phase, what will be the exact input and output of our model? 

The input is the path to the data of one subject and the output is the segmentation map of the testing subject. Your Docker container will be run multiple times till all the subjects in the test data are evaluated.

* Is there a limitation on the computation time?

There is no hard limit to the computation time. A reasonable time for evaluating your model on one case should not be longer than an hour.

* During the testing phase, will you run our submission on a computer with GPU? What GPUs are available? 

Yes, we will have access to a GPU.

We have **3090, Titan Xp, A5000, A6000, P100**. So please make sure the docker is tested on the similar GPU architectures listed above or let us know beforehand in case you use a very different one. 

* How can I share my Docker container with you?

You can use any safe and reliable cloud storage service you prefer. Please send us a link in your submission.

## Website and registration

* I have registered, but the 'Submission Instructions' on the Grand Challenge website is unaccessible (“Forbidden”).

Pages, such as the ‘Submission Instructions’ are only accessible once your registration has been confirmed by us.

* Do I need to register every member of our team separately?

No, only one registration per team is necessary. 