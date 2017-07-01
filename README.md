# EmoRecon

Real-Time Facial Emotion Recognition with Convolutional Neural Nets
About:
	takes pictures or webcam video as input. It detects all faces in each frame, and then
	classifies which emotion each face is expressing.Then replaces each face with an emoji corresponding to that emotion.
	Recognized emotions:
		Neutral
		Happy
		Sad
		Angry
		Surprise

	Training accuracy was 91% and test accuracy was 57%, with the following requirements:
		- User's facial expression must be strong / exaggerated
		- Adequate Lighting (no shadows on face)
		- Camera is at eye level or slightly above eye level
    
Credits:

	This was built using the Caffe and OpenCV libraries
	used the Emotions in the Wild (EitW) Caffe model as the starting point
		- This model is available on Caffe Model Zoo
		- EitW is itself based on VGG_S Net

	Retrained EitW on new data:
		Cohn-Kanade Plus (CK+) dataset (available for online download)
		Japanese Female Facial Expressions (JAFFE) dataset (also available online)
		Custom dataset, generated using our 'gather_training_data' script

Requirements:
	Caffe and OpenCV installed
	Webcam

Main scripts: 
	gather_training_data.py - Use this to generate a custom training set
	process_dataset.py - Read in an entire training set and calculate accuracy over the set
	process_image.py   - Read in a single image, add the correct emoji, and write to file
	video_test.py      - Run in real-time.

Utility functions:
	caffe_functions.py  - Helper Functions dealing with caffe
	opencv_functions.py - Helper Functions dealing with opencv
	utility_functions.py - General functions mostly related to file I/O

Datasets:
	Cohn-Kanade Plus (CK+) and Japanese Female Facial Expressions (JAFFE) can be downloaded online.

Caffe Files:
	deploy.prototxt - Architecture of The CNN model 
	solver.prototxt - This configures the retraining process.
	train.prototxt - This configures the architecture during training. 
					 Mainly used to add layer-specific learning rates.
	loss_history.txt - Log file from our last retraining on our dataset

  
