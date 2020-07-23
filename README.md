# [The Mathematics behind the Generative Adversarial Networks (GANs)](https://medium.com/analytics-vidhya/generative-adversarial-network-gan-b510d41df2cb?source=friends_link&sk=20e058cc47e6b9a749e8b0aa3c887c25)
* [**Here you can find the GAN for Generating MNIST Handwritten Digits.**](https://github.com/A2Amir/Generative-Adversarial-Network--GAN-/blob/master/GAN.ipynb)


## 1. Introduction

In **2014**, one of the most important new developments in deep learning was the [**Generative Adversarial Network (GAN)**](https://www.google.com/search?client=firefox-b-e&q=http%3A%2F%2FI.+Goodfellow+et+al.%2C+%E2%80%9CGenerative+adversarial+nets.%E2%80%9D+in+Advances+in+neural+information+processing+systems%2C+pp.+2672%E2%80%932680%2C+2014) , which was presented by Ian Goodfellow and other researchers at Montreal University. The great potential of GANs lies in the imitation of every data distribution, which leads immediately to a popular approach among data scientists. It should be noted that **GAN** has been used in many research projects in recent years, including in satellite imagery mapping and game development and has many [interesting applications](https://machinelearningmastery.com/impressive-applications-of-generative-adversarial-networks/) . This post covers the concept and architecture of the **GAN** networks.

Generating new plausible samples was the application described in the original paper by Ian Goodfellow, where GANs were used to generate new plausible examples for the MNIST handwritten digit dataset, the CIFAR-10 small object photograph dataset, and the Toronto Face Database.

<p align='center'>
<img src='images/1.PNG' width="500" height="350">
</p>  
  





## 2. The architecture of the GAN

**The basic idea of the GAN is to train two different networks( Generative and Discriminator Network) to compete with each other.** These networks have two different target functions to create fake images similar to real images (training data). For this purpose, these two networks were designed.

![The architecture of the GAN](https://cdn-images-1.medium.com/max/1434/1*xjjSDPcCOPFPTwmWQaBEBg.png)

**Generative Network:** attempts to generate data from some random uniform distribution so that the output generated is very similar and cannot be distinguished from real data. Also, the discriminator is not able to discern real and fake images (**the generator is trying to deceive the discriminator**).

> **_In other words, a generative network attempts to learn the probability of the input data (x) and target (y) simultaneously P(x, y)._**

**Discriminator Network:** takes data from the training data set and generative network and discerns real data from fake ones (**while the generator tries to deceive the discriminator, the discriminator tries to avoid by comparing generated data with real data**). During this task, the accuracy of the discriminator improves over time, making it harder for the generator to fool it.

> **_In other words, a discriminating network learns a function map from the input data (x) to the output (y) which is described in probabilistic terms as a conditional distribution P(y|x)._**

## 3. The training process of the GAN

**Based on figure above , the training phases of the GAN can be divided into six steps:**

**Step 1:** discriminator is trained by training data. Since the discriminator attempts to enhance the probability of correct labeling, the training data entering the outputs are labeled as real, and the generated data entering the discriminator’s outputs are labeled as fake.

**Step 2:** some noise is taken from random distribution to produce random noise data (called _z)._

**Step 3:** the noise (**z)** produced in the last step is fed into the generator\*\* \*\*to rebuild the fake x (label y=0) → (x, y) input-label pair.

· **Step 4:** the discriminator classifies the inputs taken from the training data (the real pair y =1) and the data generated by the generator (the fake pair y=0) as fake and real. For both fake x and real x, the error is calculated according to the loss function of the classification. The whole discriminator loss is obtained by combining them.

**Step 5:** since the discriminator’s goal is the classification error minimization, the discriminator is updated, and the parameters are adjusted by propagating the classification error back.

**Step 6:** since the Generator’s goal is the discriminator classification error maximization, the loss function is calculated and updated based on its noise by propagating the classification error back.

## 4. The GAN's loss function

In this section, the loss function of the GAN will be presented as **a mathematical equation** to show how the network works and how the error is calculated and propagated back to update the parameters to achieve different goals in the network.

**The definition of variables and functions are described in the following:**

![](https://cdn-images-1.medium.com/max/2232/1*idx9KpCn0IzLTsIRUqcZCQ.png)

![](https://cdn-images-1.medium.com/max/2290/1*pVv7Kos4Bh4QrxAE95nhoQ.png)

Where the output of D(x), D(G(z)), is a score between 0–1 and to create a loss function for the discriminator that maximizes the real data while minimizing the fake data and a loss function for the generator that maximizes the fake data. The final loss equation based of the **GAN** paper is described as follows.

![](https://cdn-images-1.medium.com/max/1936/1*jce_nz9vARTMp-EbexAQDg.png)

> **_As seen, before calculating the final discriminator loss, the loss function of the discriminator is performed twice (one for real inputs from the training dataset and one for fake inputs from the generator) whereas the generator loss function runs only once._**

Based on the value function **V ([G](http://Generator), [D](http://Discriminator))**, a **two-player minimax game** is played by **D **and **G**. Imagine a counterfeiter passes false notes by learning different methods and a policeman attempts to detect them. In this game, both players are dynamic and learn each other’s methods competitively.

**The equations of the discriminator (D) in terms of min-max game:**

![](https://cdn-images-1.medium.com/max/1678/1*4b2KdZB5Maha_pEyfPmADQ.png)

**As seen in the equations of the generator (G) in terms of min-max game, optimize G can fool the discriminator the most:**

![](https://cdn-images-1.medium.com/max/1160/1*irft8dH3_fyZds_ZZKmz_A.png)

**The final loss equation of the GAN in term of the min-max game:**

![](https://cdn-images-1.medium.com/max/1808/1*AbBssZZ3Xg9F_0gp3hQPYw.png)

There are many various problems that prevent successful **GAN** training due to the **GAN**s’ extremely diverse applications. Accordingly, improving the training of the **GAN**s is an open research field for researchers. in the next post I am going through the problems than can be happend by training a **GAN**.

