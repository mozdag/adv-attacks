# Adversarial Attacks on deep learning algorithms using naturally perturbed images

Our aim is to fool a state-of-the-art deep learning model with wrong predictions. This repository presents the experimental steps on this project. You may also want to check how to install Tensorflow and the model we use here.

OUR FOG GENERATOR

We generate fog on images as the natural perturbation. For the Cityscapes dataset, we generate our own foggy images using stereo pair (left and right) images and disparity map. Please refer to the file fog.m in order to reproduce those foggy Cityscapes images.

Values of the Parameters for the different Fog Densities:

Light fog														tFactor :  0.05														atmLight: 1.0

Medium fog														tFactor :  0.1														atmLight: 1.0

Light fog														tFactor :  0.15														atmLight: 1.0

In order to find the produced foggy images, I store those files in the same path where fog.m is:
Fog/stereoImages/disparity  		   --> disparity maps.
Fog/stereoImages/berlin_left_images        --> left images.
Fog/berlin_foggy_images	     	           --> foggy images.
The link for those files:
https://drive.google.com/open?id=1ae9i-BLKPuiPVTwgNvFbYDwBR2gVv9Wn


CLASSIFICATION
For the image classification task, we use the Inception model with Tensorflow.

Start by cloning the repository from the following link on GitHub:
https://github.com/tensorflow/models

Copy the following folders under the directory models-master/tutorials/image/imagenet:
berlin_foggy_images
berlin_left_images

Run the following commands:
cd models-master/tutorials/image/imagenet
python classify_image.py

The above command will classify a supplied image of a panda bear. If the model runs correctly, the script will produce the following output:
giant panda, panda, panda bear, coon bear, Ailuropoda melanoleuca (score = 0.88493)
indri, indris, Indri indri, Indri brevicaudatus (score = 0.00878)
lesser panda, red panda, panda, bear cat, cat bear, Ailurus fulgens (score = 0.00317)
custard apple (score = 0.00149)
earthstar (score = 0.00127)

In the line 192 of the code classify_image.py, we write the name of the foggy image with its path as follows:
'/Users/mesutozdag/Downloads/models-master/tutorials/image/imagenet/berlin_foggy_images/berlin216_foggy.png'

We use Cityscapes and Frida/Frida2 datasets.


INSTALLING TENSORFLOW WITH NATIVE PIP

Before starting the environmental setup, it would be helpful to mention the common problem you might face, which is "Too many levels of symbolic links".

This is because you have multiple Python versions installed in your system. Here is my solution:
-	Clean the system from all the Pythons using “find” utility.
	o	sudo find / -iname "python*" > python.log
-	Unlink all the links pointing to whatever Python version from everywhere.
-	Install a fresh Python using homebrew.
-	Install virtualenv or native pip.


Prerequisite: Python
In order to install TensorFlow, your system must contain one of the following Python versions:
•	Python 2.7
•	Python 3.3+

When installing Python, you might need to disable System Integrity Protection (SIP) to permit any entity other than Mac App Store to install software.

Prerequisite: pip
Pip installs and manages software packages written in Python. If you intend to install with native pip, then one of the following flavors of pip must be installed on your system:
•	pip, for Python 2.7
•	pip3, for Python 3.n.

pip or pip3 was probably installed on your system when you installed Python. To determine whether pip or pip3 is actually installed on your system, issue one of the following commands:
$ pip -V  # for Python 2.7
$ pip3 -V # for Python 3.n 

We recommend pip or pip3 version 8.1 or higher in order to install TensorFlow. If pip or pip3 8.1 or later is not installed, issue the following commands to install or upgrade:
$ sudo easy_install --upgrade pip
$ sudo easy_install --upgrade six 

Install TensorFlow
Assuming the prerequisite software is installed on your Mac, take the following steps:
1.	Install TensorFlow by invoking one of the following commands:
2.	$ pip install tensorflow      # Python 2.7; CPU support
 	$ pip3 install tensorflow     # Python 3.n; CPU support

Validate your installation
To validate your TensorFlow installation, do the following:
1.	Ensure that your environment is prepared to run TensorFlow programs.
2.	Run a short TensorFlow program.

Prepare your environment
If you installed on native pip, virtualenv, or Anaconda, then do the following:
1.	Start a terminal.
2.	If you installed with virtualenv or Anaconda, activate your container.
3.	If you installed TensorFlow source code, navigate to any directory except one containing TensorFlow source code.

If you installed through Docker, start a Docker container that runs bash. For example:
$ docker run -it gcr.io/tensorflow/tensorflow bash

Run a short TensorFlow program
Invoke python from your shell as follows:
$ python

Enter the following short program inside the python interactive shell:
# Python
import tensorflow as tf
hello = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
print(sess.run(hello))

If the system outputs the following, then you are ready to begin TensorFlow 
Hello, TensorFlow!
