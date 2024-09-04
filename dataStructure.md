# ToyADMOS 2 
"Each sub-dataset contains over 27 k samples of normal machine-operating sounds and over 8 k samples of anomalous sounds recorded at a 48-kHz sampling rate"
"MPEG-4 ALS (MPEG-4 Audio Lossless Coding) with a suffix of '.mp4' "
-Designed to evaluate model performace under domain shifting conditions
-Difference in operating conditions: different machine model, parts, configuration, operating speeds, mic arrangments etc
- In each sheet exists infromation on recording patterns in columns A-I.
- Number of recordings in col I, the setup uses 5 mic setup, so 5x samples avaliable (will only use one channel)

- configuration requirements in columns named r#_xxx
- r#_pat = resutling pathname pattern
- ie "ToyCar/train/section_00_source_train_normal_?????.wav" will create files incrementing from 00001 in folder ToyCar/train
- -r0_mics IDs of mics to be used
- r0_nz ID of environmental noise to be mixed with: single number 1 - 4 to be used
- r0_qty = number of samples to create
- In benchmark r0_xxx used for source training, r1_xxx used for source testing, r2_xxx used for target training and r3_xxx used for target tesign
- 




Recipe file: 
- Ability to mix and create datasets from the machine sounds and environmental noises.
- Two machines: ToyCar and ToyTrain with Normal and anomalous sound.
- Normal sounds have 150 recording patterns and anomolous have 300 recording patterns



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




## DATASET
Using ToyCar and ToyTrain


