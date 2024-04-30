---
layout: page
title: Docker Submission
subtitle: Building Your Docker Container
menubar: home_menu
show_sidebar: false
hero_image: /images/BannerFETA.png
---

{% include notification.html
message="The updated guideline for FeTA 2024 will come out soon."
icon="false"
status="is-success" %}
***

## Introduction 
Since the test set will not be released, we require Docker submissions from all the participants for the evaluation.
In the next section, we will explain how to build a docker from scratch. We also provide a simple example of how to
 containerize python codes for the FeTA challenge datasets.  The source code can be found on GitHub: [hongweilibran
 /FeTA_challenge](https://github.com/hongweilibran/FeTA_challenge).  

Please upload the zipped docker container to cloud platforms such as [Mega](https://mega.io/zh-hans/), [Google Drive](https://www.google.com/drive/), [WeTransfer](https://wetransfer.com/), etc
., send the
 download link and the command to execute your container to us [feta-challenge@googlegroups.com](mailto:feta-challenge@googlegroups.com). 

For any questions, please contact us [feta-challenge@googlegroups.com](mailto:feta-challenge@googlegroups.com). 

Please remember to fill in the following form with your submission: [FeTA Challenge Algorithm Description Submission](https://www.synapse.org/Portal/filehandle?ownerId=syn25649159&ownerType=ENTITY&fileName=Algorithm_submission_instructions.docx&preview=false&wikiId=610007)



## How to containerize your model? 
First, here is a bag of tricks to build a Docker container including [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/) and [Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/). 

We further give instructions on two key components (FROM and RUN) of a **Dockerfile** to facilitate the building process. 



### FROM

Choose a suitable base image for the container on [Docker Hub](https://hub.docker.com/) for your preferred operating system, [CentOS](https://hub.docker.com/_/centos/) or
 [Ubuntu](https://hub.docker.com/_/ubuntu/)
. Please specify a version tag (e.g. centos:7), because the :latest tag (default when not specifying a tag) might be
 updated. In the [following example](https://github.com/hongweilibran/FeTA_challenge), we choose a [miniconda](https://hub.docker.com/r/continuumio/miniconda) environment as the base image. 

If you want to use a GPU, make sure to choose a [nvidia/cuda](https://hub.docker.com/r/nvidia/cuda/) base image. And take a look at all the available tags
 to find the matched environment.



### RUN

Please limit the number of RUN commands, by combining them into a single RUN. Each command in a Dockerfile creates a layer in your container, thus increases the container size. So instead of this: 


    RUN apt-get update
    
    RUN apt-get install -y build-essential  
    
    RUN apt-get install -y libsqlite3-dev  
    
    RUN rm -rf /var/lib/apt/lists/* 


Please do this: 

    RUN apt-get update && apt-get install -y \

    build-essential \ 

    libsqlite3-dev \ 

    && rm -rf /var/lib/apt/lists/* 


## Example of building a Docker container
This section is to show a simple example of how to containerize python codes for the FeTA challenge. The source code can be found on GitHub: [hongweilibran/FeTA_challenge](https://github.com/hongweilibran/FeTA_challenge). 

The following python script does simple thresholding of the T2-w image at gray value 100 by using the BinaryThreshold function from the SimpleITK package. 
***

    import os
    
    import glob
    
    import SimpleITK as sitk
    
    import ast
    
    
    import json


    inputDir = '/input_img'      # input path of the image data
    
    input_meta_dir = '/input_meta'  # input path of the meta information, including pathology and GA information 
    
    outputDir = '/output'   # output path
    
    T2wImagePath = glob.glob(os.path.join(inputDir, ‘anat’, ‘*_T2w.nii.gz’))[0]
    
    sub = os.path.split(T2wImagePath)[1].split(‘_’)[0]     # to split the input directory and to obtain the suject name

read JSON file

    jsonPath = os.path.join(input_meta_dir, 'meta.json')
    
    with open(jsonPath) as jsonFile:
    
            jsonData = json.dumps(json.load(jsonFile))
    
            jsonFile.close()
    
    jsonData = ast.literal_eval(jsonData)
    
    pathology = jsonData['Pathology']
    
    
    GA = jsonData['Gestational age']



    T2wImage = sitk.ReadImage(T2wImagePath)    # your logic here.  
    
    # using SimpleITK to do binary thresholding between 100 - 10000
    
    resultImage = sitk.BinaryThreshold(T2wImage, lowerThreshold=100, upperThreshold=10000) 
    
    print('pathological info:', pathology)
    
    
    print('GA:', GA)
    
    sitk.WriteImage(resultImage, os.path.join(outputDir, sub + '_seg_result.nii.gz'))

This code needs a basic Python installation with SimpleITK added. We therefore used miniconda, which has Docker
 container available that we can inherit from: [continuumio/miniconda](https://hub.docker.com/r/continuumio/miniconda). Please feel free to pick other suitable
  environments for your solutions from DockerHub. 



Our **Dockerfile** looks like this: 


    FROM continuumio/miniconda
    
    MAINTAINER [TEAM-NAME]
    
    RUN pip install numpy SimpleITK
    
    ADD python/src /feta_seg


Inside, it pulls the necessary environment from DockerHub, installs necessary packages, and maps the folders.  Our Python code is saved next to this Dockerfile in the folder python/src/example.py. With the following command, we build a Docker container from our Dockerfile and the Python source code:

    docker build -f Dockerfile -t feta_challenge/[TEAM-NAME] . 

Note: the . at the end specifies that everything is in the current folder. Hence, you run this build command from the folder that contains the Dockerfile and the source code. 



Once your container is ready, we can run it with the following command:


    docker run -dit -v [TEST-INPUT-IMG]:/input_img/:ro -v [TEST-INPUT-META]:/input_meta/:ro -v /output feta_challenge/[TEAM-NAME] 

The -v option maps the input image folder into the container at /input_img and the meta information folder at /input_meta , read-only. The last -v creates an output directory.

**Please note that the container will be run subject by subject.** 

**We provide information on pathology and gestational age in the test stage.**  The information for each subject is stored as a JSON file with a named 'meta.json'.  Here is one example to understand the JSON structure in case you need such information.  Also please check how to read the meta-information in the provided demo. 

This command outputs the Container ID, which you can also lookup with:

    docker ps



Next, we will execute the example Python script:

    docker exec [CONTAINER-ID] python /feta_seg/example.py

Since this script is quite tiny, it doesn’t take long to finish. Next, we copy the output from the container to our local machine:

    docker cp [CONTAINER-ID]:/output [RESULT-LOCATION]



Finally, we shut down the running container. This also removes the created /output folder and any other changes made to the container.

    docker stop [CONTAINER-ID]
    docker rm -v [CONTAINER-ID]

I hope now you understand how the container works. Enjoy! ;)

As the last step, please use [docker save](https://docs.docker.com/engine/reference/commandline/save/) to save your docker into a zipped file (e.g. tar.gz file), and send it to
 us. 