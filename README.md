# American Sign Language Alphabet Detector

This project uses Python's OpenCV library to detect American Sign Language Alphabet gestures in real time. The data for this model is over 100 images of each letter in the alphabet, as well as an additional gesture for 'space'. 
The data was collected by recording myself making all of the individual gestures and then saving the framed images, compiling a 100 frames per class. I then used Python's mediapipe hand landmark detection capability to draw hand landmarks and track their coordinates for each image in each class. This created a set of 42 pairs of (x,y) data points for 100 images across the 27 classes. The model was then run through a RandomForestClassifier and was able to generate a 99.2% accuracy score on the testing data.

After this, the RandomForest model was saved and then uploaded to another python file, that opens up the camera and detects for the gestures in real time. The model works very well, but there are some discrepancies when classifying gestures that are very similar in appearance, like "I" and "J", "R" and "U", and "M" and "N".

In order to improve the model, I would suggest using something other than a RandomForest algorithm, as it works fine for static images but for motion-based gestures like "J" and "Z", there are issues when classifying, and I found that during the real-time gesture capture it worked best on the ends of the motion gestures, and not their beginnings. 
