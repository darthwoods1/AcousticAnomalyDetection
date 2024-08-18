Definitions. 

Acoustic Anomaly Detection (AAD) makes a prediction about how normal or anomlous a sound is. Anomalous machine sounds are a deviation from standard operating. 
Machine faults would be indicated by an anomaly being detection in these systems. 
Practically there is a need for a robust system that has a low false positive rate, the misclassification of normal sounds to anomlalous would happen more often than reveresed. 
Using pAUC metrics, a robust system would need to increase its accuracy within low false positive rate of the peformanec of the system, 
ie the area for AUC (False Positive Rate vs True Positive Rate) above 0.1 FPR, if the system accuracy increases rapidly it would not matter as it is already preidciotn false anomalies.



Unsupervised learning, where there is no human intervention in the training is used. The data is not labelled and only training on normal samples is done. 

Autoencoder networks uses deep learning to train a model to minimise the reconstruction error from a network. 
The important layer is the bottleneck, where the dimensionality is reduced after an encoder, then a decoder reconstructs to match as close the original signal.
As the network is trained on normal samples, the reconstruction error should be minimised through training and validation loss. 
Assuming that the anomlaous samples have enough statistical deviation in the features extracted during preprocessing, an anomlay will increase the reconstruction error on the model.
When the reconstruction error is above a threshold (calculated by system), then the system will output a predicted anomaly. 


Audio data is converted to 16 kHz sampling rate, 
To input into machine learning models, the dimensionality of the data needs to be reduce, 
feature extraction to find the important information. 
Features used: 
  - Mel frequncy Cepstrum Coefficients
  - Mel frequncy Energy Coefficients
  - Spectrums
  - Raw Audio

log uses: 
  - small values near 0 -> -infinite, use small value, approximates human hearing (dB scale)
  - For convolution, conversion into frequncy domain and taking log will create addition of coefficint instead of convolution
  


MFCC uses DCT (Discrete Cosine Transform)
  - information about rate of change of frequncy in bands, spectral envelope, timbre (Subjective)
  - based on human hearing, 10-20 coefficients
  - Spectrum of a spectrum (Framing ->windowing->DFT or STFT -> Filter bands (triangular) ->log spectrum -> DCT
  - Power Cepstrum = |F-1(log(|F(x(t))^2)|^2
  - DCT finds coefficients to descibe spectrum in wavefroms ie c1,c2,...cN
  - The filtered bands are based on mel/frequency relationship, perceptual spacing,  with sum of weighted frames (triangular) adds correlation
  - 

MFEC does not use DCT, 
  - DCT in MFCC lose sphase information, decorrelates the data and converts back into a time domain (cepstrum, changing features of spectrum) (PCA is another dim reduction method)
  - 

ReLU: rectified Linear Unit, ie half wave rectifier.rdf
