
⸻

## Deepfake Face Swap 

Digital Image Processing Project

Authors: Hiten S (241EC217), Rihan Shajahan (241EC245)
Date: April 2026

⸻

## Overview

This project implements a deepfake face swap system using classical computer vision techniques without any deep learning or generative AI models.

Instead of using GANs or diffusion models, the pipeline relies on:
	•	Frequency analysis
	•	Edge detection
	•	Facial landmark detection
	•	Delaunay triangulation
	•	Affine warping
	•	Poisson-based seamless cloning

The goal is to demonstrate that convincing face swaps can be achieved using geometry and signal processing principles alone.

The pipeline is fully deterministic, interpretable, and GPU-free.  ￼

⸻

Project Pipeline

The implementation is divided into two main phases:

Phase 1 — Image Analysis
	•	Convert source image to grayscale
	•	Perform FFT-based frequency analysis
	•	Detect edges using Canny operator
	•	Evaluate image sharpness and texture density

Phase 2 — Face Swap Pipeline
	1.	Detect 68 facial landmarks using dlib
	2.	Perform Delaunay triangulation on landmark points
	3.	Warp each triangle using affine transformation
	4.	Blend warped face into target image using seamless cloning

⸻

Tools and Libraries
	•	OpenCV
	•	NumPy
	•	dlib
	•	SciPy
	•	Matplotlib

⸻

Algorithm Summary

Frequency Analysis
	•	Apply 2D FFT
	•	Shift low frequency components to center
	•	Suppress low frequency components
	•	Compute high frequency energy as sharpness metric

Edge Detection
	•	Apply Canny edge detection
	•	Compute edge density

Landmark Detection
	•	Detect face using dlib frontal face detector
	•	Extract 68 landmark points

Triangulation
	•	Perform Delaunay triangulation on facial landmarks

Warping
	•	Compute affine transform for each triangle
	•	Warp source face geometry to match target face

Seamless Cloning
	•	Create convex hull mask
	•	Blend warped face into target using Poisson image editing

⸻

Results

1. Grayscale Image


⸻

2. Frequency Spectrum


⸻

3. Edge Detection Output


⸻

4. Facial Landmarks Detection


⸻

5. Delaunay Triangulation


⸻

6. Warped Face


⸻

7. Final Face Swap Result


⸻

Example Output

Stage	Description
Grayscale	Confirms correct preprocessing
FFT Spectrum	Shows distribution of frequency components
Edge Map	Detects strong facial boundaries
Landmarks	Identifies key facial geometry
Triangulation	Creates mesh for transformation
Warped Face	Rearranges source face geometry
Final Output	Natural blended face swap

The quality of the final result depends on:
	•	similarity of pose
	•	lighting direction
	•	face size
	•	facial expression

⸻

Limitations
	•	Sensitive to large pose variations
	•	Lighting mismatch may cause artifacts
	•	Only swaps inner face region (not hair or ears)
	•	Works only on single images (not video)
	•	No anti-spoofing robustness

⸻


How to Run
	1.	Install dependencies

pip install opencv-python numpy dlib scipy matplotlib

	2.	Run notebook

jupyter notebook deepfake.ipynb

	3.	Provide source and target images

source.jpg
target.jpg


⸻

Conclusion

This project demonstrates that face swapping is fundamentally a geometric transformation problem. By decomposing the face into triangles defined by semantic landmarks, we can warp each triangle independently and blend the result smoothly into a new image.

Classical computer vision methods provide a transparent and educational baseline for understanding how deepfake systems operate internally.  ￼

⸻
