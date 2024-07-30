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
- 


1) Install essential modules from requirements.txt
2)  Make example dataset, compatible file-folder structure as DCASE 2021 challenge task 2 (1 hr)
3) Run Baseline autoencoder DCASE 2020 task2 baseline
4) 
