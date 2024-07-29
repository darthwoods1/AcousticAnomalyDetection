# Acoustic Anomaly Detection (AAD) under changes in environmental noise 
How can potential faults in machinery be diagnosed without expert human intervention?
Using microphones as a sensor for this task would allow non-destructive sensing and early detection of faults in a machine.
Machine learning models that are trained on normal machinery sounds, which is an unsupervised approach, is most practical. 
In a real life application only small amounts of normal could be gathered to train a model. 
Exisiting datasets avaliable for this task include:
- MIMII (Malfunctioning Industrial Machinery Investigation and Inspection)[1]
- MIMII 2
- ToyAdmos
- ToyAdmos 2 [4]

In this thesis, experiments around the effects of environmental noise on these models are tested. 


# Data Gathering
Environmental noise was recorded at an industrial site in different locations using Zoom H1 handy recorder, with WAV files at 44.1 kHz and 16 bit rate.  
The procedure for the experinment was following:
1. Make long audio recording in different areas on site.
2. Listen back to recordings making notes ono the changes in noises over time.
3. Analyse the environemntal nosie over time using audio analysis in matlab and python.
4. Label the data
5. Collect environmental noises into structured databases
6. Perform noise reduction / denoising methods on the enviornmental noise
8. Mix with ToyAdmos 2 dataset
9. Perform training and testing using mixed acoustic data
10. Use exisitng models for Acosutic Anomlay detection: Baseline and Advanced.

# Anomaly Detection 
Acosutic Anomaly Detection uses acoustic data that is usually transformed before input into models to either identitdy that data as normal or anomolous. 
There is a one sided nature for data avaliable for this problem, given that it is difficult to find labelled anomoulous machinery noises because machinery faults are rare and creating data would require more work than collection of normal data sets.


# Statistical Measures
A receiver operating characterisitc (ROC) curve is used to plot the true positive agasint hte false positive rate. The area under the curve (AUC) for the whole ROC is the total number of true positives vs false positives. For an unbalanced problem, a partial under the curve (pAUC) is a better measure to establish the accuracy of the model for real life scenarios. 
A pAUC curve will find the probability of TP/FP below a certain FP rate. The region of interest would be below a certain FPR, as in real life, applications for AAD would assume a low false positive rate, as a high FPR would be impractical for a fault detection solution. 

A fault detection solution needs to consistently detect faults. The accuracy of True Postive would need to be high. Given the unbalanced nature, the probability of false positive would be higher, and if not reduced would decrease the seen reliability of these sensors. To restrict the ROC curve to a region below a false positive rate of 0.2 would give an estimate of how well the models performed under these conditions. 


# Environmental noise discussion
Under practical scenarios, AAD will need to be robust for use with different environmental nosie qualities. the MIMII and ToyADMOS data sets have premixed environmnetal noise to machinery sounds that were recorded under acoustic isolation. The datasets are labelled with different SNRs for these machine sounds and the environemtnal noise avaliable.

Mixing in the MIMII dataset:

Mixing in the ToyADMOS dataset:



Practical considerations for environmental noise in real life that would not have been evaluated using the method of analysing 10 second clips is the analysing that changes in performance over a continous stream of environmental noise. Is an environmental noise source that is less stationary, more difficult on the model?

It is unknown how the environemntal noise was mixed into the datasets, exisitng qualities that were given in the datasets are: 





# Noise reduction techniques
In preprocesssing stage for the data, denoising can be peformed to better isolate the target machine and environmental noises. 




1. https://arxiv.org/abs/1909.09347


4. https://arxiv.org/abs/2106.02369
