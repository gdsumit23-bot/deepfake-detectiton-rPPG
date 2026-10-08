# Remote Photoplethysmography (rPPG) Deepfake Detection Under Video DegradationCourse Project: IT204 - Signals & Systems

## Stage1 Implementation — ROI Extraction & Signal Pipeline Setup📌 

## Project Overview
This project explores the application of Remote Photoplethysmography (rPPG)—a contact-free method for extracting blood volume pulse (BVP) signals from facial video—to distinguish real human faces from deepfakes.While state-of-the-art rPPG detectors perform well on high-quality video, video-conferencing platforms (Zoom, Teams, Google Meet) apply lossy compression (e.g., H.264/VP8 chroma subsampling) that degrades delicate skin color fluctuations. Our project evaluates baseline rPPG robustness under simulated codec degradation and introduces an adaptive Signal-to-Noise Ratio (SNR) gating mechanism to filter corrupted video segments prior to classification.📡 Signals & Systems (S&S) MappingThe physiological signal extraction pipeline directly applies foundational S&S principles:ConceptImplementation in ProjectSampling & Discrete SignalSequential video frames sample continuous skin color variations into a discrete signal $x[n]$.Band-Pass FilteringButterworth filter isolating heart rate frequencies between 0.7 Hz and 4.0 Hz (42–240 BPM).Frequency Analysis (FFT)Fast Fourier Transform converts filtered time-domain $x[n]$ into $X(e^{j\omega})$ to identify pulse energy peaks.Noise & Artifact SuppressionFiltering out low-frequency motion artifacts and high-frequency sensor noise.


## 🛠️ Stage 1
Implementation HighlightsIn Stage 1, we established the core video decoding and facial region-of-interest (ROI) isolation pipeline:Facial Landmark Detection: Integrated MediaPipe FaceMesh to dynamically track 468 3D facial landmarks frame-by-frame.ROI Selection: Extracted landmarks specifically corresponding to the forehead and cheek regions due to high micro-vascular density and lower susceptibility to rigid motion artifacts.Pipeline Configuration Parameters:MAX_SECONDS = 10: Limits processing to the first 10 seconds per video.MIN_FRAMES = 90: Rejects videos too short for reliable spectral density estimation.LOW_HZ = 0.7, HIGH_HZ = 4.0: Bounds frequency range to realistic physiological pulse limits (42–240 BPM).


🚀 Getting StartedPrerequisitesPython 3.9+OpenCVMediaPipeNumPy & SciPyMatplotlibInstallation 


## Install required dependencies
pip install opencv-python mediapipe numpy scipy matplotlib

## Run Stage 1 extraction test
python main.py
📅 Project Roadmap[x] Stage 1: Environment setup, MediaPipe ROI tracking, frame-level color signal extraction.[ ] Stage 2: Implement temporal band-pass filter and FFT spectral analysis.[ ] Stage 3: Reproduce baseline rPPG extraction on test videos.[ ] Stage 4: Introduce ffmpeg video compression degradation experiments.[ ] Stage 5: Implement SNR quality gating and evaluate real vs. fake classification metrics.
