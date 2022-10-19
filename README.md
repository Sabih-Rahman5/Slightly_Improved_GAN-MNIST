# Slightly Improved GAN-MNIST
This project is a slightly improved version of a generative adversarial network of the popular MNIST handwritten digits dataset.

The changes mainly include:
### 1. Slightly higher learning rate for the discriminator (Two Time-Scale Update Rule): 
The intuition was that the discriminator would reach a specific accuracy quickly (around a 100 epochs) and spend the rest of the time oscillating between a set range of accuracies. This would allocate majority of our computational resources towards training the generator.

### 2. Additional linear and Relu activation layers for both the generator and descriminator:
Done to simply improve the power of both the models. Implementing additional layers was the only way to increase power without going towards Conv2d and Conv transpose layers in a Deep Convolutional GAN (DC-GAN).

### 3. One sided Label Smoothing (discriminator side): 
A label smoothing of 0.1 for false (generated images) and 0.9 for true (real images from dataset). This was used to reduce the overconfidence of the discriminator by avoiding only a 1 or 0 output and increasing the variation of the models outputs that can be used as loss.

### 4. Training for an aditional 50 epochs:
An additional 50 epochs (a total of 350 epochs) for a much cleaner output.

## Results:
1. Losses:

![losses](https://user-images.githubusercontent.com/112173249/196696199-f917cb63-c461-40fa-8704-9a000d2a3b46.png)

2. Scores:

![scores](https://user-images.githubusercontent.com/112173249/196696222-8054c982-3912-4229-989a-a43d00cd9aed.png)

## Outputs after:
1. 1 Epoch:

![1 epoch](https://user-images.githubusercontent.com/112173249/196696822-881f8d46-7a6a-4865-9115-c6f32480ebd4.png)

2. 50 Epochs:

![50 epochs](https://user-images.githubusercontent.com/112173249/196696834-7ae0bb7a-6a30-48dc-b3a1-679ee11f9528.png)

3. 100 Epochs:

![100 epochs](https://user-images.githubusercontent.com/112173249/196696850-de2ebdb1-7c2c-4750-8ab5-d140cc036aa9.png)

4. 200 Epochs:

![200 epochs](https://user-images.githubusercontent.com/112173249/196696936-2640c014-d484-4d44-bff2-f9fe8ee83d91.png)

5. 250 Epochs:

![250 epochs](https://user-images.githubusercontent.com/112173249/196696945-d30246cb-a52c-4b32-b9f4-ad59813e3b02.png)

6. 300 Epochs:

![300 epochs](https://user-images.githubusercontent.com/112173249/196696955-ea1f2284-0909-4dbe-ac6d-0ac15106f280.png)

7. 350 Epochs:

![350 epochs](https://user-images.githubusercontent.com/112173249/196696970-fa5721a9-59d0-49bc-a76a-fca121d4ea9b.png)

### Training from 0 to 350 epochs at 8 epochs per second:

![gans_training](https://user-images.githubusercontent.com/112173249/196697677-692e375d-f298-4f4f-9896-ed9bf783ad02.gif)

## Conclusion:
The models seem to converge much more quickly to equilibrium however at the end of training cycle the models started showing patterns of over-fitting. Perhaps removing the additional 50 epochs and training only for 300 epochs might eliminate these patterns.
