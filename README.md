# Residual Convolutional Network with Bidirectional LSTM for Finger Movement Classification 
Overview: This project presents a deep learning approach for classifying individual finger movements using human ECoG (Electrocorticography) data. The model leverages a combination of Residual Convolutional Networks and Bidirectional LSTM layers to effectively capture both spatial and temporal features in the neural signals. By utilizing a filter bank approach and transforming the data into the frequency domain, the model aims to enhance feature extraction and improve classification accuracy. This work has potential applications in brain-computer interfaces, particularly in real-time control systems and neuroprosthetics.

Data: This project uses an open-source dataset from the Stanford Libraries, the link to the dataset is copied here. https://exhibits.stanford.edu/data/catalog/zk881ps0522

Ethics statement: All patients participated in a purely voluntary manner, after providing informed written consent, under experimental protocols approved by the Institutional Review Board of the University of Washington (#12193). All patient data was anonymized according to IRB protocol, in accordance with HIPAA mandate. These data originally appeared in the manuscript “Human Motor Cortical Activity Is Selectively Phase- Entrained on Underlying Rhythms” published in PLoS Computational Biology in 2012 [Reference].

Features

•	Neural Network Architecture: Combined Residual Convolutional layers with Bidirectional LSTM for capturing spatial-temporal features.

•	Filter Bank Approach: Utilized multiple frequency band filters (theta, alpha, beta, gamma) to enhance input data representation.

•	Frequency-Domain Data: Applied FFT for effective feature extraction from neural signals.

•	Benchmarking: Compared against baseline models (shallow CNN, simple LSTM, and SVM) to demonstrate superior performance.


Results

•	The model achieved 90% test accuracy in classifying finger movements.

Task: During the finger movement task, subjects were cued with a word displayed on a bedside monitor indicating which finger to move during 2- second movement trials. The subject performed self-paced movements in response to each of these cues, and they typically moved each finger 2–5 times during each trial, but some trials included many more movements. A 2-second rest trial (blank screen) followed each movement trial. There were 30 movement cues for each finger, and trials were interleaved randomly. Finger positions were recorded using a 5 degree-of-freedom dataglove sensor (5 dt, Irvine, CA). 

Data Files and Variables: The basic datafiles (in MATLAB format) are named “##_fingerflex.mat” in the folder data/##, where ## denotes the 2 letter patient code.

Each datafile has 7 variables, the ones used in this project are:

"elec_regions" (number of channels x 1): A numerical code for the anatomical location of the associated channel. The code is as follows:
1 – dorsal M1
3 – dorsal S1
4 – ventral sensorimotor (M1+ S1) 
6 – frontal (non-rolandic) 
7 – parietal (non-rolandic)
8 – temporal 
9 – occipital

 "data" (time x number of channels): These are the data.
-	sampled at 1000Hz
-	scale factor: 1 amplifier unit = .0298 microvolts
-	built-in band pass 0.15 to 200 Hz, 
		- but a 1 pole band pass, so there is no sharp corner at 200Hz. 
		-The amplitude roll-off function is in the file “ns_1k_1_300_filt.mat”

There is an additional file, are named “##_stim.mat” in the folder data/##, where ## denotes the 2 letter patient code. This file contains a variable “stim”, which are labeled epochs encasing the actual movement types. The code is as follows:
0 – Inter-stimulus interval
1 – thumb
2 – index finger
3 – middle finger 
4 – ring finger
5 – little finger

How to Use the Trained Model:
The trained model is saved as ‘finger_movement_classification_model.keras’. You can download it in the GitHub repository where this project is located. After downloading, place the file in the project directory and use the following code to load the model in your notebook: 

From tensorflow.keras.models import load_model 

model = load_model(‘finger_movement_classification_model.keras’)

Acknowledgements:
Special thanks to the researchers who collected the dataset.


