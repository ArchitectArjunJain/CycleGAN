# Style Transfer using CycleGAN

Misdiagnosis in the medical field is a very serious issue but it’s also uncomfortably common to occur. Imaging procedures in the medical field requires an expert radiologist’s opinion since interpreting them is not a simple binary process ( Normal or Abnormal). Even so, one radiologist may see something that another does not. This can lead to conflicting reports and make it difficult to effectively recommend treatment options to the patient.

One of the complicated tasks in medical imaging is to diagnose MRI(Magnetic Resonance Imaging). Sometimes to interpret the scan, the radiologist needs different variations of the imaging which can drastically enhance the accuracy of diagnosis by providing practitioners with a more comprehensive understanding.
 
But to have access to different imaging is difficult and expensive. With the help of deep learning, we can use style transfer to generate artificial MRI images of different contrast levels from existing MRI scans. This will help to provide a better diagnosis with the help of an additional image.

 
In this project, I have used CycleGAN to translate the style of one MRI image to another, which will help in a better understanding of the scanned image. Using GANs I have created T2 weighted images from T1 weighted MRI image and vice-versa.

#### Problem statement : To build a Generative adversarial model(modified U-Net) which can generate artificial MRI images of different contrast levels from existing MRI scans.
 
For the dataset refer to the zipped file attached (MRI+T1_T2+Dataset).


The project pipeline can be briefly summarized in the following four steps:

Data Understanding: Here, you need to load the data and create the dataset for it.
Image Processing: In this step, you will have to process the images using different steps.
Model-Building and Training: This is the final step at which you have to create your Generators and Discriminators using a modified U-Net architecture(similar to CycleGAN).

All the above project pipleline steps can be found in T12T2CycleGAN.zip

The Generator uses the U-net architecture which uses downsampling and upsampling(refer below screenshot), while the descriminnator uses basic Convolutions and acts an an Image classifier.

![image](https://user-images.githubusercontent.com/108930510/184673599-0e8a0a3c-6e60-4796-b694-eedc68adfc91.png)

 I have also defined a loss function and training step for model training. The loss functions are Binary Cross-Entropy loss, Cycle-consistency loss and the Identity loss.
 
 ###### Cycle-consistency Loss
 ![image](https://user-images.githubusercontent.com/108930510/184674361-8bf5bab9-dde3-47ed-8fd6-7abebfc8df83.png)

###### Identity Loss : 
![image](https://user-images.githubusercontent.com/108930510/184674396-3f3d248d-a4d5-49fe-afd6-e5a90ab0f7b3.png)

###### Binary Cross-Entropy Loss
![image](https://user-images.githubusercontent.com/108930510/184674637-79303112-584b-4451-bc2e-70f8561e9b72.png)

In the nascant stage before the model is actually trained, the network generates random sample of pixel values.
![image](https://user-images.githubusercontent.com/108930510/184675229-95eecc60-520c-47fc-9ab1-c2d7ecef118b.png)

But as the training progresses(weights are updated and model parameters are optimised), the model becomes mature in learning the underlying features. I've managed to train the model for aroung 300 epochs and I've noticed fantastic results.
![image](https://user-images.githubusercontent.com/108930510/184675596-87cb5393-3260-4a26-b0cd-ad595c0e8323.png)


