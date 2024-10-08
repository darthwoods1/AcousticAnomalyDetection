<img width="689" alt="image" src="https://github.com/user-attachments/assets/11534c88-293a-4390-88f1-ee4624019850">Week 1: 
Researching into Acoustics and different potential research areas 
Week 2:
Reviewing papers for literature review 
Week 3 
reading comprehensive evaluation of time series anomaly detection algorithms  
reading the rest of the articles for the literature review 
ACTIVE NOISE CONTROL: Tutorial Review 
discovered by changing search terms and backward branching using 'active noise control' keywords in scopus  
Focusing direction on Acoustic Anomaly Detection 
Creating mind map with associated area in acoustics for industry, finding links between the papers 
Week 4: 
Writing research Proposal  
Limited computation for acoustic anomaly detection  
Week 5: 
Monday: Working on project timeline and reviewing DCASE competitions. 
Timeline to include tasks, dates and durations 
Looking at soltuois for whole systesm  
Exisiting solutions in early stages, amazon web services acoustic anomaly detection intergrates backend software and AAD models with big data approaches 
Look into multimodal uses. 
Week 6: 
Running google Colab baseline for 2023 DCASE competition 
Debugging errors due to libraries 
Mounting google drive into google Colab
Continuing with comparisons of available systems for acoustic anomaly detection.  
Break: 
DCASE 2024 Challenge Task 2 and DCASE 2023 Challenge Task 2 Baseline Auto Encoder: dcase2023_task2_baseline_ae 
uploaded this to a google colab and linked google drive into colab for saving files 
Ran the training files, automatic downloading of the training data set 
Week 8 
-Writing up data collection procedure specifying what data will be collected  
-Transferring all files into one drive for continuity 
-one note still linked to pc storage 
- Changning ADD test code for 2022 DCASE task 2 challenge, importing dev and eval data sets into directory  
- attempting to run other data sets for DCASE 2023 code (DCASE 2022 code had multiple errors when running, maybe due to different version of python being used or libraries out of order)  
 - running the evaluation scripts  
Week 9: 
Creating baseline models for DCASE 2023 (MIMII dataset) first shot problem 
Results from development can't be compared to any official DCASE results 
Running the training set for 2020, to get models to work for 2020 evaluation  
 - trained 8 models from DCASE 2020  
Week 10:  
Running autoencoder baseline model on DCASE  
Writing testing procedures to evaluate effects of environmental noise on the performance of acoustic anomaly detection baseline models 
Reading through ToyADMOS2 dataset, python mixing script  
Finding noise mitigation techniques used in papers, python scripts for google colab 
Semester break: 
Made two recordings on site using zoom h1 audio recorder.  
Feasibility of laptop recorder not as good as portable recorder. Areas in the industrial site are very noisy, dusty, hot and conditions unsuitable for laptop recording.  
First recording in packing shed, quieter environment, input gain set to 30 
Second recording in the flour mill, dusty and hot environment. Microphone was shaking ontop of outlet when I came back to retrive it, causing error to the acutal sound. Large vibrations in that room. Input gain was set to 10.  
Week 1:  
Starting GitHub repo to keep documentation and informal report, demonstration and explanation of experiments  


Week 2) 
MATLAB Signal Spectrogram Settings: 
window length: 1024 
window: periodic blackman
hop: window/4

Listened to packing shed 1,
Listen to 


Audio analysis:
detrend, normalise?
oscillogram, spectrum(spectral and t-f), cepstrogram, signal histogram, 
autocorrelation function, signal statistics

Python libraries to use:

NumPy: numerical computing (filtering, resampling and FFT)
SciPy: DSP, Fourier analysis and filter design
Librosa: feature extraction etc
Pydub: load, manipulate file formates
Pyaudio: realtime input and output

How much variance is there in the environmental noise samples,
Use clustering and methods to analyse how similar all the files are for the recorded environmental noise. 



Exporting audio into 10 second clips
3 hours of recording = 1000 10 second clips
Segmentised PackingShed.


Selecting window for spectrum to use: https://avisoft.com/tutorials/selecting-appropriate-spectrogram-parameters/
using blackmann, medium bandwidth, 

Creating excel document with segments from environmnetal noise and adding tags

-Sound Intensity Levels in the files?  DONE
-How to get noise into ToyADMOS2 Dataset? 
- stat.csv file?
- get rms and 	vol_adj for audio clips DONE
-import using mixer in python?
use made split noise files and combine with two folders and stat csv file. 


Week 3: 


**Mounting google drive using Zip folders** 
https://sharkovsky.github.io/2020/09/18/colab-io-bench.html
'''
images = os.listdir('/content/gdrive/path/to/training/data')
with open(path, 'r') as f:
  content = f.readlines()
Google Drive can be a bit clumsy and unstable when dealing with folders containing many files. An efficient approach to uploading large datasets to Drive is to upload a zipped folder, and unzip it directly on the Drive. Sometimes, reading the files would fail with an OSError exception or a timeout. I found that listing the directories containing the training data and catching the exceptions in that moment with the following code can help in later on making the training process more stable.
retry = True
while retry:
  retry=False
  try:
    next(os.walk('/content/gdrive/path/to/training/data'))
  except StopIteration:
    print('Exception Raised. Retry')
    retry = True
'''


- testing creating new env noise in dataset folder 
r0_nz -- ID of environmental noise to be mixed. A single number is accepted: 1 to 4.


- Make a flowcahrt of procedures


Wednesday: 

Found articles on noise mitigation with acoustic anomaly detection.
writing up method and description

- Look into https://neurodsp-tools.github.io/neurodsp/auto_tutorials/spectral/plot_SpectralVariance.html spectral variance as statistical mea
-make some more recordings on site



DCASE 2021 "Unsupervised Anomalous Sounds Detection for Machine Coniditon Monitioring under Domain Shifted Conditions", follow up from DCASE 2020 Task 2, the task is an unsupervised problem, where only normal samples are give as trainnig data combined with a domain shfit problem where the *Acoustic characterisitcs of the training data and the test data is differnt".
Problem solves issue of False Anomaly due to changes within the normal conditions. 
An example of changes in normal operating conditon is chagnes in motor speed due to changes in production over time due to changes in searosnal demands., environmental noise conditions (SNR, sound characterisitics)

KEYWORDS:
Anomalous Sound Detection System Sound(Input)->Anomaly Score(Output)

Audio datasets:
10 second audio clips
7 machine types (INCLUDING ToyCar and ToyTrain)
Each section has source and target domain for calculating peformace metrics.
 Different products may be in hte same section.
![image](https://github.com/user-attachments/assets/b7f4d0ad-b0ba-4afb-a70a-d5a64848b73c)
Development dataset: 
Sections 00,01,02
 - source domain (1000 clips (normal) Training,
200 clips (50% anomalous/normal split)
- Target domain (3 clips(normal) Training and 200 clips (50% anomalous/normal split)
Additional Training dataset
Sections 03,04,05
 - source domain (1000 clips (normal) Training)
 - Target Domain (3 clips (normal) Training)
Evaluation dataset
Sections 03,04,05

<img width="689" alt="image" src="https://github.com/user-attachments/assets/c45d189d-5088-403f-86ab-42b7109246ce">





plotted spectrogram and welch power density spectrums for segmetns fo interest in regions. 


https://repositorium.sdum.uminho.pt/bitstream/1822/73560/1/aiai2-dcase.pdf



TUESDAY:
listening to Flour Mill


2/9/24
 -Trying to cluster segments
 





