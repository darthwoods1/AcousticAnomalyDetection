# Methods to denoise

1) Iterative Wiener from pyroomacoustics in python
2) Spectral Subtraction from ""
3) Subspace Subtraction
4) Blind denoise
5) U-Net
6) SEGAN 



1) 
Iterative Wiener single channel noise reduction in frequency domain.[1]
Wiener filter uses a linear time-invarient filtering of a noisy signal, assumes known additive noise spectra and known stationary signal. 
The LTI filter produces an estimate of the random singal, statistical filter. 
peformance criterion is hte minimum mean-square error. 


2) Spectral Subtraction

One of the first and simplest methods for denoising a signal. Assumptions given in this method is that the noise additive, is stationary and does not change significantly between updating periods
Noise is estimated and power of noise is stimaated using averaging opeation. 
Subtraction of noise can lead to musical noise (zeroing of subtracted spectral components becomes negative) 
Musical noise can be reduced by using M Berouti Method (alpha and beta variable) 



The process for the spectral subtraciton involves: 
1) Windowing the signal
2) Peforming FFT
3) Get the Power spectrum of the noisy signal
4) Estimate the spectrum of the noise
5) Subtract the estimated noise from the signal
6) IFFT
7) Overlap and add 

class pyroomacoustics.denoise.spectral_subtraction.SpectralSub(nfft, db_reduc, lookback, beta, alpha=1)
"
# initialize STFT and SpectralSub objects
nfft = 512
stft = pra.transform.STFT(nfft, hop=nfft//2,
                          analysis_window=pra.hann(nfft))
scnr = pra.denoise.SpectralSub(nfft, db_reduc=10, lookback=5,
                               beta=20, alpha=3)

# apply block-by-block
for n in range(num_blocks):

    # go to frequency domain for noise reduction
    stft.analysis(mono_noisy)
    gain_filt = scnr.compute_gain_filter(stft.X)

    # estimating input convolved with unknown response
    mono_denoised = stft.synthesis(gain_filt*stft.X)
"
6)https://github.com/santi-pdp/segan



## "Frequency of Interest-based Noise Attenuation
Method to Improve Anomaly Detection
Performance"
Park, et al. maximises computation while extracting driving events for anomaly detection by identifying Frequency of Interest (FoI) and using filters to remove characterisitics not in the FoI.
On dataset improvement by 8.6%.

They mention that using a deep learning model for noise reduction is not feasible due to increased computation required, not a solution for and edge node device.

Noise reduction should only be on noise that interferes with the peformance of the anomaly detection.
if noise mitigatoin increases the generalisation abilities by using addition of random noise in training, then the reconstruction error difference between normal and abnormal sounds will be reduced. 

1st (21.5Hz) to 60th harmonic notch filters acting as a high pass filter, DC component also removed)

Noise reduction on audio before event extraction using peak finding (stationary mic and oncoming cars?)









##references:


  https://github.com/BA-HanseML/NF_Prj_MIMII_Dataset/blob/master/feature_extraction_diagrams/A04_DenoiseDesign_mono/librosa_NNFilter_BlindDenoise.ipynb
https://pyroomacoustics.readthedocs.io/en/pypi-release/pyroomacoustics.denoise.spectral_subtraction.html
[1] Lim, J.S. and Oppenheim, A.V. (1978) All-Pole Modeling of Degraded Speech. IEEE Trans. Acoust. Speech, Signal Processing, ASSP, 26, 197–210.
