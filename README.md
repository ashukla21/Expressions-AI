# Expressions-AI
Generating Artificial Faces with Machine Learning

## Inspiration

The power of facial generators raise a lot of questions. On the one hand there are obvious creative applications for this technology. Programs like this could create endless virtual worlds, as well as help designers and illustrators. They’re already leading to new types of artwork.

Then there are the downsides. As we’ve seen in discussions about deepfakes, the ability to manipulate and generate realistic imagery at scale is going to have a huge effect on how modern societies think about evidence and trust. Such software could also be extremely useful for creating political propaganda and influence campaigns.

Having said this, I have been extremley intrigued by this phenemoa and wanted to delve into the world of AI facial generation myself. These amateur generators are just the polite introduction to this new technology. The rude awakening comes later.

## What it does

Expressions AI runs off of an algorithm which is trained on a huge dataset of real images, then uses a type of neural network known as a generative adversarial network (or GAN) to fabricate new examples. 

## How I built it

GANs learn a probability distribution of a dataset by pitting two neural networks against each other.

One neural network, called the Generator, generates new data instances, while the other, the Discriminator, evaluates them for authenticity; i.e. the discriminator decides whether each instance of data that it reviews belongs to the actual training dataset or not.

Meanwhile, the generator is creating new, synthetic/fake images that it passes to the discriminator. It does so in the hopes that they, too, will be deemed authentic, even though they are fake. The fake image is generated from a 100-dimensional noise (uniform distribution between -1.0 to 1.0) using the inverse of convolution, called transposed convolution.

The goal of the generator is to generate passable images: to lie without being caught. The goal of the discriminator is to identify images coming from the generator as fake. The generator goes the other way: It is the artist who is trying to fool the discriminator. This network consists of 8 convolutional layers, and each convolutional layer performs a convolution and then performs batch normalization

Using a dataset downloaded from Kaggle, my objective was to create a model capable of generating realistic human images that do not exist in reality. These were models for face detection, particularly for recognizing facial attributes such as finding people with brown hair, are smiling, or wearing glasses. Images cover large pose variations, background clutter, diverse people, supported by a large number of images and rich annotations.

A GAN model can be defined that combines both the generator model and the discriminator model into one larger model. This larger model will be used to train the model weights in the generator, using the output and error calculated by the discriminator model. The discriminator model is trained separately, and as such, the model weights are marked as not trainable in this larger GAN model to ensure that only the weights of the generator model are updated. This change to the trainability of the discriminator weights only affects when training the combined GAN model, not when training the discriminator standalone.

## Challenges I ran into

Because of the timeframe of this hackathon, and my lack of prior experience, I was not able to create a completely accurate model. For example, when a user moves the `Smiling` slider this can turn a face from masculine to feminine or from lighter skin to darker. 

## Accomplishments that I'm proud of

I'm proud I was able to use Generative Adversarial Networks to achieve a model that can somewhat realistically generate faces. This is the future that we are living in, where deepfakes of real-life people can be used for better or worse to change humanity. 

## What I learned

The basics of both Generative Adversarial Networks, and Convolutional Neural Networks. 

## What's next for ExpressionsAI

Fixing the bugs such as how certain absolute values are inaccurate on the model (when pushed far enough skin tone changes femininity for example). 
