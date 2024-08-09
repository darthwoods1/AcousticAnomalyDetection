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







  references:
  https://github.com/BA-HanseML/NF_Prj_MIMII_Dataset/blob/master/feature_extraction_diagrams/A04_DenoiseDesign_mono/librosa_NNFilter_BlindDenoise.ipynb
https://pyroomacoustics.readthedocs.io/en/pypi-release/pyroomacoustics.denoise.spectral_subtraction.html
[1] Lim, J.S. and Oppenheim, A.V. (1978) All-Pole Modeling of Degraded Speech. IEEE Trans. Acoust. Speech, Signal Processing, ASSP, 26, 197–210.
