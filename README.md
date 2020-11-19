# Onomatopoeic-Word-Converter
Convert a select few of sound types (crumpling, jingling, knocking, and rubbing)→ display as onomatopoeic words on a LCD screen. This is done by 
an arduino set up to pick up environmental sounds and feed through a pre-trained classifier.
We used Fast Hartley Transform to process the sound, feed the top ten frequencies into a python-trained multilayer classification model, and get the sound label from the model. 
Fast Hartley Transform, in FHT.h, is a Fast Fourier Transform equivalent for Arduino. 
Our multilayer classification model consists of 10 inputs, one hidden layer with 7 nodes, and 4 outputs. It classifies sounds by adjusting weights in the matrices in the direction that minimize the discrepancy between predicted labels and the labels we provided. 
After training, the accuracy achieved on training set is 83.2%.
310 clips of training data was taken by Arduino on two different days in the lab to ensure generality. We produce the sound, print it’s FHT result to Serial, and copy that to a txt file.
Then, a jupyter notebook reads in training data sets and generate true labels for training.
After 100000 epochs of training we achieved an accuracy of 83.2%.
We printed out the matrices in a python notebook 
and copied them to Arduino.
We also reproduced the exact same model on 
Arduino.
Although the experiment works as intended, the data from the results slightly deviates from complete accuracy. Possible errors and solutions may include:
Limited Arduino memory: Raspberry Pi may be able to classify more sounds.
Limited FHT sample rate and size: could not take into account temporal distribution. 
Background noise: Since the data from results 1 and 2 were taken in different locations, different background sounds may have skewed recorded values in some degree depending on the two different locations.
