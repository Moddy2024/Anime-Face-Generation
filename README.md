# Anime-Face-Generation
Welcome to AnimeGAN, a generative adversarial network (GAN) designed to generate anime faces. With AnimeGAN, you can train your own model on a dataset of anime faces, or use a pre-trained model to generate new anime faces. The goal of this project is to generate realistic anime faces. The model used for this task is a deep convolutional generative adversarial network (DCGAN). The dataset used for training the model is a collection of over 100k anime face images. The dataset is preprocessed before training to ensure that the model is able to learn the features of the anime faces. In a GAN, the generator and discriminator are trained together in a two-player game. The generator generates fake samples, and the discriminator tries to distinguish between the real and fake samples. The generator is trained to fool the discriminator, while the discriminator is trained to accurately distinguish between the real and fake samples. To train the discriminator, MSE loss function is being used. First the loss is calculated on how well the discriminator is able to recognize the real images, after that the loss is calulated on how well the discriminator outputs for the images generated by the Generator. By minimizing these loss functions, the discriminator is trained to accurately distinguish between real and fake samples. By training the discriminator to better distinguish between real and fake samples, the overall quality of the GAN-generated samples is improved. This is because the generator learns from the feedback provided by the discriminator, and thus is able to generate more realistic-looking samples. 

In GANs, the discriminator is trained to distinguish between real and fake samples by assigning a label of 1 to real samples and 0 to fake samples. However, this can lead to overconfidence in the discriminator, where it can learn to rely too heavily on specific features of the training data and become less effective in distinguishing between real and fake samples from other distributions. To address this issue, label smoothing technique is being used to improve the generalization and robustness of the discriminator in the GAN training process. 

Label smoothing introduces a small amount of noise to the labels. The noise is generated using a beta distribution with parameters (1, 5) and added to the real and fake targets before calculating the mean squared error loss between the discriminator's predictions and the noisy labels. This helps to prevent the discriminator from becoming too confident in its predictions and encourages it to learn more robust features for distinguishing between real and fake samples. Overall, the label smoothing technique can improve the performance of GANs by making the discriminator more robust to variations in the training data and better able to distinguish between real and fake samples from different distributions.

The model has been trained for 100 epochs on a Kaggle Notebook with GPU (Nvidia Tesla P100) which took 2 hour 40 mins approximately.

# Dependencies
* [PyTorch](https://pytorch.org/)
* [Matplotlib](https://matplotlib.org/)
* [Numpy](https://numpy.org/)
* [OS](https://docs.python.org/3/library/os.html)
* [Torchvision](https://pytorch.org/vision/stable/index.html)
* [torchinfo](https://github.com/TylerYep/torchinfo)
* [imageio](https://pypi.org/project/imageio/)

Once you have these dependencies installed, you can clone the AdaIN Style Transfer repository from GitHub:
```bash
https://github.com/Moddy2024/Anime-Face-Generation.git
```
# Key Directories and Files
* [anime-gan.ipynb](https://github.com/Moddy2024/Anime-Face-Generation/blob/main/anime-gan.ipynb) - In this Jupyter Notebook, you can find a comprehensive walkthrough of the data pipeline for GANS, which includes steps for preprocessing the data, details on the various data transformations and data loader creation steps,  along with visualizations of the data after transformations and moving the preprocessed data to the GPU for model training. There's the architecture of the Discriminator and the Generator being used for training and the whole training process.
* [prediction.ipynb](https://github.com/Moddy2024/AdaIN-Style-Transfer/blob/main/prediction.ipynb) - The notebook includes code for loading the trained generator and using it to generate multiple anime face images.
* [trained-models](https://github.com/Moddy2024/Anime-Face-Generation/tree/main/trained-models) - This directory contains the trained model files for Generator and Discriminator which can be used for further training or inference.
# Dataset
The [Anime Faces dataset](https://www.kaggle.com/datasets/modassirafzal/anime-faces) is a collection of over 100,000 high-quality anime-style face images, spanning different years ranging from 2000-2021. The images feature a wide variety of colors, styles, and expressions, making it a valuable resource for training GANS for Anime Face Generation of new kinds and will help the model to generate diverse images. The script below can be used to download the dataset on COLAB or any other platform for training in Kaggle it can be directly used from the datset section of Kaggle. In order to download the dataset from Kaggle you need to extract [API Token](https://www.kaggle.com/discussions/general/371462#2060661) from the Kaggle account only then you will be able to download dataset from Kaggle to anywhere. The official instructions on how to use the [KAGGLE API](https://github.com/Kaggle/kaggle-api). The Anime Faces dataset in Kaggle can be found [here](https://www.kaggle.com/datasets/modassirafzal/anime-faces).
```bash
!ls -lha /content/kaggle.json
!pip install -q kaggle
!mkdir -p ~/.kaggle #Create the directory
!cp kaggle.json ~/.kaggle/
!chmod 600 /content/kaggle.json

!kaggle datasets download -d modassirafzal/anime-faces -p '/content/'
local_zip = '/content/anime-faces.zip'
zip_ref = zipfile.ZipFile(local_zip, 'r')
zip_ref.extractall('/content')
zip_ref.close()
os.remove(local_zip)
```

# Results
**From Noise to Art: A Journey through GAN Training**

 ![](https://github.com/Moddy2024/Anime-Face-Generation/blob/main/anime100.gif)
