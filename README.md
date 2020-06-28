# NMT (Neural Machine Translation)

This repo contains code for the final capstone project of the padhAI Deep Learning course.

Problem Statement : <br>
Given an image, locate 'Hindi' language texts if any and then translate all of them to English. <br>

Approach : <br>
This problem statement can be divided into 3 tasks. They are : <br>
1. Detecting texts in a given image (Object Detection).
2. Finding what is the exact text which present in the image.
3. Translating Hindi words to English.

Task-1 : <br>
I have used RCNN for detecting images in text. I have used openCV's 'Selective Search' algorithm for region proposals. Instead of doing a regression for finding dimensions of bounding boxes, I have used the 'Selective Search' algorithm on test images and generate proposals and then classified each region, This method would be too slow as the number of proposed regions would be high. However, training a regression model for a large dataset would also take considerable amount of time. So, I limited the number of regions proposed for each image and achieved fairly good results. <br>
Other better methods are using a faster-RCNN or mask-RCNN model or even YOLO algorithms.

Task-2 : <br>
After finding where the texts are present in the image, next we have to predict what is that text. I have modeled this as a classification problem. Taking an exhaustive list of Hindi words and classify each image into these classes. <br>
Other better method is to use an CNN-RNN encoder-decoder model. This would be a better choice as there would be very less datapoints for some words and the total number of words might be quite high.

Task-3 : <br>
After getting the text from the image, next we have to translate it to English. This task can be modeled as prediction of a sequence of English letters given a sequence of Hindi letters. We can use a Seq2Seq model for this task. For this I have used a simple Encoder-Decoder model using LSTM and achieved good results. <br>
We can try using a different representation for each Hindi letter (like 'word2vec'), to see if we can get better results.
