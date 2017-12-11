# dereverberation
Single-Channel Dereverberation algorithm in Matlab called SPENDRED (SPeech ENhancement and DeREverberation by Doire)

Reference:

C. S. J. Doire, D. M. Brookes, P. A. Naylor, C. M. Hicks, D. Betts, M. A. Dmour, and S. H. Jensen.
          Single-channel online enhancement of speech corrupted by reverberation and noise.
          IEEE Trans. Audio, Speech, Language Processing, 25 (3): 572587, Mar. 2017. doi: 10.1109/TASLP.2016.2641904.
          
Usage : 
(1)       [enhanced_speech] = spendred(corrupted_speech,fs)   % Denoises and dereverberates the input speech file
(2)       [enhanced_speech] = spendred(corrupted_speech,fs,algo_params)  % performs enhancement using custom parameters in 'algo_params'


Inputs:
   input_speech     Noisy and reverberant input speech signal (single-channel)
   fs               Sample frequency in Hz
   algo_params      algorithm parameters [optional]


Outputs:
   enhanced_speech  Enhanced output speech file

Algorithm Parameters:
       The following parameters are defined in 'algo_params'. Default values are shown below.

        algo_params.of=6                % Overlap factor [6]
        algo_params.ti=0.005            % Desired frame increment in seconds [0.005]
        algo_params.ri=1                % Set to 1 to round ti to the nearest power of 2 samples [1]
        algo_params.sg=1                % Type of gain: 1=Wiener Gain, 2=Power Spectral Subtraction, 3=MMSE speech estimate [1]
        algo_params.sc=0.95             % Smoothing constant for computation of the spectral gain [0.95]
        algo_params.sf=1e-5;            % Floor for the spectral gain [1e-5]
        algo_params.os=2;               % Interference Over-subtraction factor [2]
        algo_params.cl=6;               % Number of HMM states to use (minimum is 2 - maximum is 6) [6]
        algo_params.ds=1;          	    % Way of computing posterior distributions : 1 = max track , 2 = weighted sum of tracks
        algo_params.mo=1;          	    % Mode : 'fast' = 1 or 'slow' = 0 [1]
        algo_params.ef=-60;          	  % Energy floor (dB) [-60]
