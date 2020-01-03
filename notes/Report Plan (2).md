---
attachments: [Clipboard_2019-12-19-10-43-31.png, Clipboard_2019-12-19-10-44-30.png]
tags: [CS3330-Coursework]
title: Report Plan
created: '2019-12-18T18:21:36.768Z'
modified: '2019-12-19T11:47:37.806Z'
---

# Report Plan

## background - words 260
*	What is the aim of foreground segmentation?
*	Why is segmenting an image useful? Hint: segmentation is a mid-level image processing technique, and the output of mid-level techniques is often fed into high-level techniques.
*	What are the existing approaches to foreground segmentation? Briefly outline THREE different algorithms for foreground segmentation found through your research and discuss the way in which the aims and performances of these algorithms differ in academic literature.

foreground segmentation is mid-level process that aims to extract the 'foregorund' for each image in a sequence of images. It does so by segmenting the pixels into foreground and background categories based on change in pixel values over time. Often the background pixels are static for majority of images in the sequence while foreground pixels are more variable in value. Many algorithms work under that assumption, to build background models of an image, so that the subtraction of the next image from the model leads to obtaining the foreground. 

Foreground subtraction has many applications, in majority of cases it acts as input in high level processes such as object tracking, object identification, 2D-3D mapping, movement observation. These processes can be seen in self-driving cars, surveillance, traffic monitoring, AR and other major industries. Foreground subtraction is a popular topic in computer vision due to to the usefullness it can provide. Much like AI if, we can encapsulate processes that are natural to use humans, inside the machines, we can automate many processes that rely on us manually determining what's the foreground and what's the background.


Some know object segmentation techniques:
* frame differencing - He algorithm works by taking a difference between previous frame and the current frame and applying a set threshold to obtain a  foreground. It is very sensitive to Illumination chnages. Very cheap comutationally, but has low accuracy.[http://tmu.ac.in/college-of-computing-sciences-and-it/wp-content/uploads/sites/17/2016/10/T208.pdf] 

* Mixture of Gaussian - Mixture of Gaussian models the background with multiple normal ditributions to represent different modalieties of the background. The pixel values of incoming images are compared with different gaussians used to classify them into groups. The background pixels have weak variance as they are more present over time. In the end the classified background pixels are subtracted from the frame to find the foregorund. This algorithm is state of the art and in majority of background subtraction applications. It's robust against changes in environmnet such as: illumination changes, high speed foreground objects, ect and which makes it accurate. Overall all it's an algorithm is balanced in speed, accuracy and computation ability. [https://hal.archives-ouvertes.fr/hal-00338206/document]

* Median Approximation - This algorithm works by storing an N sized buffer of previously observed frames and calculates the median background value as the median of all observed frames. The median background is subtracted from the frame obtaining the foreground. The algorithm is quite accurate, however it is computationally expensive due to computing median for every pixel for N number of frames for each new images. It's also expensive on memory due to storage of the buffer frames.[https://s3.amazonaws.com/academia.edu.documents/39028408/A_Qualitative_and_Quantitative_Comparison_of_Real-time.pdf?response-content-disposition=inline%3B%20filename%3DA_Qualitative_and_Quantitative_Compariso.pdf&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWOWYYGZ2Y53UL3A%2F20191219%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20191219T113521Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=9be453e0fe68e775377dfbb34460ccaef554c95712dfcb0317820cb48b556355]

## the algorithm - 350

* Motivate why it would be suitable for foreground segmentation, making reference to the literature.
*	Discuss any drawbacks to the algorithm, again, making reference to the literature.
*	Describe how the algorithm works in your own words (e.g., using high-level pseudocode).



I built my foreground detection pipeline from several parts, sampling different algorithms but at the core, the algorithms is based on implemnetation of Temporal Median Filter as described here[reference]. Summary of my algorithm actions for each images:
1. Image is smoothed with a 3 x 3 box filter to get rid of noise
2. Temporal ''median'' process is use on the image to update the background model
4. The background model is subtracted from the image
3. The image is thresholded using Otsu's thersholding method to get the best segmentation of high and low intensity values
4. Image is dilated to join seperated neigbouring regions in the image.
final. the foreground mask for the image is obtained
This processes is repeated for every frame in the image sequence.

I modeled the temporal median process described this paper:[]. The algorithm works by slowly building up a background model that becomes more accurate over time:

The algorithm works pixel by pixel. I checks if the current frame's pixel value falls in region of tolerance around the background model pixel's value, then the background model pixel value is assigned the current frame pixel value with simple exponential smoothing filter(measure against noise) and a long term counter for that pixel is incremented. the tolerance level allows for slightly dynamic pixel values to be learned into background and the longterm counter is used as a level of confidence that the pixel is in the background

If the current frames pixel value is outside of tolerance level for the equivalent background model pixel but it's inside the tolerance level for previous frame's pixel, that means that the pixel was covered by a different value(different object) indicating change in background model. In such cases when previous to current values stay the same for longer than current background model value for that pixel, the new value is considered to be background an is integrated in the background model by condition (short term counter> long term counter). To make sure that long term counter doesn't grow too much, it's growth is restricted to u number of frames, allowing short term counter to learn new object into th ebackground after u + 1 number of frames. The background model is build frame by frame, and to obtain the foreground mask, it is taken away from the current frame.

In cases where frame to frame changes are too extreme for tolerance level to handle, the short term counter is reset to indicated that the pixel value changed significantly and should not yet be learned into background.

The algorithm is fast, able to provide real-time segmentation, has low memory requirement and is fairly easy in terms of computation and development effort. The algoitm is also fairly robust to change. Since it has low resource requriements which makes it perfect for low memory and fairly low performnace embedded system, such as self-driving cars.

However it does come with it's drawbacks. The algorithm isn't very good against camera movement, which can really distrubt it's performance. it doesn't deal well with quickly moving targets and has trouble filling the regions of objects it finds.

[get the drawback from research]


## the results - 500 words


## the results - 437
*	Describe how you will test the applicability of your method to your chosen problem application (your methodology). You may want to propose some subjective or objective analysis of your results.
*	At minimum, you should use Matlab to apply your method to a set of test image sequences and comment on the results.
*	You may gain extra marks for objective analysis (comparison to ground truth images is a good candidate). 
*	Visually demonstrate the results of applying your segmentation algorithm and discuss how well it has binarized each document image. As stated above, you should aim to binarize at least one of the test image sequences with reasonable accuracy.
*	Present and discuss any further evidence that you have gathered, as per your methodology.

I will analyse the perfomance of my algorithm alongisde the performance of frame-differencing with otsu thresholding for background subtraction for 5 different sets of image sequences. I will mesure psnr, recall, precision and f-measure as a way of evaluating the performance of each method against groundtruth images.
the results show: 

``` frame_differencing for sequence Board - 
psnr: 53.5263 recall: 0.343 precision: 0.98303 f_measure: 0.41146
preprocessed_temporal_weighted_gbst_metric for sequence Board - 
psnr: 60.4489 recall: 0.81339 precision: 0.97918 f_measure: 0.88387

frame_differencing for sequence HighwayI - 
psnr: 57.2624 recall: 0.33305 precision: 0.44177 f_measure: 0.37484
preprocessed_temporal_weighted_gbst_metric for sequence HighwayI - 
psnr: 57.2907 recall: 0.66907 precision: 0.47326 f_measure: 0.54617

frame_differencing for sequence HallAndMonitor - 
psnr: 60.1918 recall: NaN precision: 0.4675 f_measure: NaN
preprocessed_temporal_weighted_gbst_metric for sequence HallAndMonitor - 
psnr: 65.43 recall: NaN precision: 0.90314 f_measure: NaN

frame_differencing for sequence Snellen - 
psnr: 51.8947 recall: 0.26173 precision: 0.93213 f_measure: 0.38412
preprocessed_temporal_weighted_gbst_metric for sequence Snellen - 
psnr: 53.2749 recall: 0.50167 precision: 0.89989 f_measure: 0.63024

frame_differencing for sequence Foliage - 
psnr: 50.9004 recall: 0.18482 precision: 0.90076 f_measure: NaN
preprocessed_temporal_weighted_gbst_metric for sequence Foliage - 
psnr: 53.2578 recall: 0.5198 precision: 0.96265 f_measure: 0.66716
```
the result for the 3
[make pictures and tables]
both algorithms performed worse when dealing with a high speed targets as seen in Highway1 ``

frame differencing with Otsu's thresholding: 
![](@attachment/Clipboard_2019-12-19-10-43-31.png)
preprocessed temporal weighted gbst:
![](@attachment/Clipboard_2019-12-19-10-44-30.png)

In 3 out of five instances the precision of preprocessed temporal weighted gbst was higher than frame differencing and in all measurable cases the recall was better by on average by approcimatly twice. The same pattern exists for f_measure. therefore frame differencing can compete with preprocessed temporal weighted gbst on reporting less false postives on some image sequences. The preprocessed temporal weighted gbst however is overall better a reporting a higher number of true postives, which makes it better at determining whole objects. The average PSNR is higher for The preprocessed temporal weighted gbst in all cases, more significantly on some image sequences. However the preprocessed temporal weighted gbst is slower than frame differencing.

Both algorithms did worse in equences Sennel and Foliage. Most likely due to flames and foliage moving quickly with out huge change in color, however in those cases, the preprocessed temporal weighted gbst was more robust. Both algorithms performed similarly in terms of PSNR and precision when mapping highspeed foregorund objects from 'HighwayI' showing that in conditions of fast moving objects there's no significant difference in the algorithms, aside from recall.

## the conclusion - 90-100 words

To conclude. While computationally more expensive and slower, preprocessed temporal weighted gbst performs better in terms of PSNR, recall, and F_measure when compared to frame differencing. It was more robust algorithm, providing better results globally through the five image sequences that were used. Overall the algorithm is better at providing full objects than frame differencing hence the of the recall is always higher. Both algorithms perform similarly when extracting high speed objects such as cars, and in those cases, frame differencing is better suited due to it's faster computation time(unless higher recall is required).



