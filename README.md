# MTCNN


<img src="https://badge.fury.io/py/mtcnn.svg">
<img src="https://travis-ci.org/ipazc/mtcnn.svg?branch=master">
  

Implementation of the MTCNN face detector for Keras in Python3.4+. It is written from scratch, using as a reference the implementation of
MTCNN from David Sandberg (`FaceNet's MTCNN <https://github.com/davidsandberg/facenet/tree/master/src/align>`_) in Facenet. It is based on the paper *Zhang, K et al. (2016)* [ZHANG2016]_.

<img src="https://raw.githubusercontent.com/vaibhavhariaramani/mtcnn/master/result.jpg">


INSTALLATION
############

Currently it is only supported Python3.4 onwards. It can be installed through pip:

.. code:: bash

    $ pip install mtcnn

This implementation requires OpenCV>=4.1 and Keras>=2.0.0 (any Tensorflow supported by Keras will be supported by this MTCNN package).
If this is the first time you use tensorflow, you will probably need to install it in your system:

.. code:: bash

    $ pip install tensorflow

or with `conda`

.. code:: bash

    $ conda install tensorflow

Note that `tensorflow-gpu` version can be used instead if a GPU device is available on the system, which will speedup the results.

USAGE
#####

The following example illustrates the ease of use of this package:


.. code:: python

    >>> from mtcnn import MTCNN
    >>> import cv2
    >>>
    >>> img = cv2.cvtColor(cv2.imread("vaibhav.jpg"), cv2.COLOR_BGR2RGB)
    >>> detector = MTCNN()
    >>> detector.detect_faces(img)
    [
        {
            'box': [277, 90, 48, 63],
            'keypoints':
            {
                'nose': (303, 131),
                'mouth_right': (313, 141),
                'right_eye': (314, 114),
                'left_eye': (291, 117),
                'mouth_left': (296, 143)
            },
            'confidence': 0.99851983785629272
        }
    ]

The detector returns a list of JSON objects. Each JSON object contains three main keys: 'box', 'confidence' and 'keypoints':

- The bounding box is formatted as [x, y, width, height] under the key 'box'.
- The confidence is the probability for a bounding box to be matching a face.
- The keypoints are formatted into a JSON object with the keys 'left_eye', 'right_eye', 'nose', 'mouth_left', 'mouth_right'. Each keypoint is identified by a pixel position (x, y).

Another good example of usage can be found in the file "`example.py`_." located in the root of this repository.

BENCHMARK
=========

The following tables shows the benchmark of this mtcnn implementation running on an `Intel i7-3612QM CPU @ 2.10GHz <https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-3612QM+%40+2.10GHz>`_, with a **CPU-based** Tensorflow 1.4.1.

 - Pictures containing a single frontal face:

+------------+--------------+---------------+-----+
| Image size | Total pixels | Process time  | FPS |
+============+==============+===============+=====+
| 460x259    | 119,140      | 0.118 seconds | 8.5 |
+------------+--------------+---------------+-----+
| 561x561    | 314,721      | 0.227 seconds | 4.5 |
+------------+--------------+---------------+-----+
| 667x1000   | 667,000      | 0.456 seconds | 2.2 |
+------------+--------------+---------------+-----+
| 1920x1200  | 2,304,000    | 1.093 seconds | 0.9 |
+------------+--------------+---------------+-----+
| 4799x3599  | 17,271,601   | 8.798 seconds | 0.1 |
+------------+--------------+---------------+-----+

 - Pictures containing 10 frontal faces:

+------------+--------------+---------------+-----+
| Image size | Total pixels | Process time  | FPS |
+============+==============+===============+=====+
| 474x224    | 106,176      | 0.185 seconds | 5.4 |
+------------+--------------+---------------+-----+
| 736x348    | 256,128      | 0.290 seconds | 3.4 |
+------------+--------------+---------------+-----+
| 2100x994   | 2,087,400    | 1.286 seconds | 0.7 |
+------------+--------------+---------------+-----+

MODEL
#####

By default the MTCNN bundles a face detection weights model.

The model is adapted from the Facenet's MTCNN implementation, merged in a single file located inside the folder 'data' relative
to the module's path. It can be overriden by injecting it into the MTCNN() constructor during instantiation.

The model must be numpy-based containing the 3 main keys "pnet", "rnet" and "onet", having each of them the weights of each of the layers of the network.

For more reference about the network definition, take a close look at the paper from *Zhang et al. (2016)* [ZHANG2016]_.

LICENSE
#######

`MIT License`_.


REFERENCE
=========

.. [ZHANG2016] Zhang, K., Zhang, Z., Li, Z., and Qiao, Y. (2016). Joint face detection and alignment using multitask cascaded convolutional networks. IEEE Signal Processing Letters, 23(10):1499–1503.

.. _example.py: example.py
.. _MIT license: LICENSE
Resources 
#########

To learn more about these Resources you can Refer to some of these articles written by Me:-

[MTCNN](https://sites.google.com/view/geeky-traveller/computer-vision/face-detection-using-mtcnn)

# Resources 

To learn more about these Resources you can Refer to some of these articles written by Me:-

- [Medium](https://medium.com/geeky-bawa)
- [geeky Traveller](https://sites.google.com/view/geeky-traveller/)
- [Blogs](https://github.com/vaibhavhariaramani/blogs)
- [Youtube](https://www.youtube.com/channel/UCy7amUpLnsRLEMIaJGGBYog)[![Youtube Badge](https://img.shields.io/badge/-Geeky_Bawa-1ca0f1?style=flat-circle&labelColor=d54b3d&logo=youtube&logoColor=white&link=https://www.youtube.com/channel/UCy7amUpLnsRLEMIaJGGBYog)](https://www.youtube.com/channel/UCy7amUpLnsRLEMIaJGGBYog)

### Don't forget to tag us

if you use this repo in  your project don't forget to mention us as Contributer in it . And Don't forget to tag us [Linkedin](https://www.linkedin.com/in/vaibhav-hariramani-087488186/),[ instagram](https://www.instagram.com/geeky_baba_/?hl=en),[ facebook](https://www.facebook.com/jayesh.hariramani.3) ,[ twitter](https://www.linkedin.com/in/vaibhav-hariramani-087488186/), [ Github](https://github.com/vaibhavhariaramani) 

============================================================================
# Made with ❤️by Vaibhav Hariramani
#### About me

I’ve always been the kind of developer who learns by building.
What started with IoT, Android, machine learning, and computer vision gradually turned into a career around cloud infrastructure, DevOps, SRE, distributed systems, and AI.
Today I spend most of my time designing and automating cloud systems, working with Kubernetes, Terraform, AWS, Azure, CI/CD, observability, and Python — but I still make time for the kind of projects that started everything: building random ideas just to see if I can.
I’ve worked at Jaguar Land Rover, Avaya, 42Gears, and OneWorld, and completed my MSc in Computer Science at University College Dublin.
Some repositories here are polished projects. Others are experiments, old ideas, or things I built simply because I was curious.
That’s probably the best description of me as a developer: curious enough to build it, and stubborn enough to figure out how it works.

[My PortFolio](https://vaibhavhariaramani.github.io/)
You can find me at:-
[Linkedin](https://www.linkedin.com/in/vaibhav-hariramani-087488186/) or [Github](https://github.com/vaibhavhariaramani) .

Email: [vaibhav.hariramani01@gmail.com](mailto:vaibhav.hariramani01@gmail.com)


# Download [THE VAIBHAV HARIRAMANI APP](https://github.com/vaibhavhariaramani/The-Vaibhav-Hariramani-App/raw/master/vaibhav%20hariramani%20app.apk)

# [<img src="https://github.com/vaibhavhariaramani/vaibhavhariaramani/blob/master/icon/gh-bannner-light.png">](https://github.com/vaibhavhariaramani/The-Vaibhav-Hariramani-App/raw/master/vaibhav%20hariramani%20app.apk) 
<p align='center'>
<a href="https://www.linkedin.com/in/vaibhav-hariramani-087488186/"><img height="30" src="https://github.com/vaibhavhariaramani/vaibhavhariaramani/blob/master/icon/linkedin.png"></a>&nbsp;&nbsp;
<a href="https://twitter.com/vaibhavhariram2"><img height="30" src="https://github.com/vaibhavhariaramani/vaibhavhariaramani/blob/master/icon/twitter.png"></a>&nbsp;&nbsp;
<a href="https://www.instagram.com/vaibhav.hariramani/?hl=en"><img height="30" src="https://github.com/vaibhavhariaramani/vaibhavhariaramani/blob/master/icon/instagram.jpg"></a>&nbsp;&nbsp;
<a href="https://www.buymeacoffee.com/vaibhavJii"><img height="30" src="https://github.com/vaibhavhariaramani/vaibhavhariaramani/blob/master/icon/by-me-a-coffee.png"></a>
<a href="https://wa.me/+917790991077"><img height="30" src="https://github.com/vaibhavhariaramani/vaibhavhariaramani/blob/master/icon/whatsapp.png"></a>&nbsp;&nbsp;
<a href="mailto:vaibhav.hariramani01@gmail.com"><img height="30" src="https://github.com/vaibhavhariaramani/vaibhavhariaramani/blob/master/icon/email.png"></a>&nbsp;&nbsp;
</p>


[<img width="150" align='center' src="https://archive.org/download/download-button-png/download-button-png.png">The Vaibhav Hariramani App (Latest Version) ](https://github.com/vaibhavhariaramani/The-Vaibhav-Hariramani-App/raw/master/vaibhav%20hariramani%20app.apk)

Download [THE VAIBHAV HARIRAMANI APP](https://github.com/vaibhavhariaramani/The-Vaibhav-Hariramani-App/raw/master/vaibhav%20hariramani%20app.apk) consist of Tutorials,Projects,Blogs and Vlogs of our Site developed Using Android Studio with Web View try installing it in your android device.

Happy coding ❤️ .

### Follow me
  
[![Linkedin Badge](https://img.shields.io/badge/-VaibhavHariramani-blue?style=flat-circle&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/vaibhav-hariramani-087488186/)](https://www.linkedin.com/in/vaibhav-hariramani-087488186/) [![Instagram Badge](https://img.shields.io/badge/-VaibhavHariramani-e02c73?style=flat-circle&labelColor=e02c73&logo=Instagram&logoColor=white&link=https://www.instagram.com/vaibhav.hariramani/?hl=en)](https://www.instagram.com/vaibhav.hariramani/?hl=en) [![Twitter Badge](https://img.shields.io/badge/-VaibhavHariramani-1ca0f1?style=flat-circle&labelColor=1ca0f1&logo=twitter&logoColor=white&link=https://twitter.com/vaibhavhariram2)](https://twitter.com/vaibhavhariram2) [![GitHub Badge](https://img.shields.io/badge/-@Vaibhavhariaramani-24292e?style=flat-circle&labelColor=24292e&logo=github&logoColor=white&link=https://github.com/vaibhavhariaramani)](https://github.com/vaibhavhariaramani) [![Gmail Badge](https://img.shields.io/badge/-VaibhavHariramani-d54b3d?style=flat-circle&labelColor=d54b3d&logo=gmail&logoColor=white&link=mailto:vaibhav.hariramani01@gmail.com)](mailto:vaibhav.hariramani01@gmail.com) [![Medium Badge](https://img.shields.io/badge/-VaibhavHariramani-d54b3d?style=flat-circle&labelColor=d54b3d&logo=medium&logoColor=white&link=https://medium.com/geeky-bawa)](https://medium.com/geeky-bawa) 

