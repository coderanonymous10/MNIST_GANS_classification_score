There are five types of GAN mentioned: <br />
1: AAE <br />
2: conditional GAN <br />
3: Deep convolutional GAN <br />
4: WGAN <br />
5: INFO GAN <br />
===========================================================================================================
#There are two types of evaluation done:
1: Classification score(CS)<br />
	-a: Direct_classification(C2)<br />
	-b: Indirect_classification(C3)<br />
	-c: Blind_classification(C4)<br />
2: Distribution score(DS)<br />
============================================================================================================
mnist_splitter_dataset:

This dataset contains randomly splitted mnist dataset
-------->mnist-splitter/stdash_dataloader
-------->mnist-splitter/svdash_dataloader

USE:<br />
	use above data as a input to trainloader for GAN training<br />
	"train_loader = torch.load('../input/mnist-splitter/stdash_dataloader')"<br />
============================================================================================================
CNN C1 MODEL:<br />
mnist_cnn_c1<br />
-------> Above folder contains the pt file of the cnn_c1 model which will be use to predict the label of the images generated from GAN.

USE:<br />
	use above data as a input to cnn_c1 model<br />
	cnn_c1 = torch.load('../input/cnn-c1/cnn_c1(2).pt')<br />
============================================================================================================

1: Classification score(CS):<br />
Each gan is mentioned as MNIST_gan_name.ipynb<br />
After running the above file with required dataset(mnist_splitter and cnn_c1)<br />
each gan will generated the images as dataloader and save as well and (FID,IS,PSNR,MMD) will be calculated and print on screen for below epochs:<br />
"checkpoint = [1,10,20,30,40,50,100,150,200]"<br />
==================================================================================================================

A: Direct_classification(C2):<br />
to calulate the direct classification values for each epochs we need to run the file mnist-cnn-c2_direct_classification.ipynb<br />
use this "train_loader = torch.load('../input/mnist-splitter/stdash_dataloader')" to train the convolutional neural network<br />
and use "dcgan_loader = torch.load('../input/conditional-gan/gan_data_epoch_EPOCH')" where EPOCH=[1,10,20,30,40,50,100,150,200] to test and get the result<br />

==================================================================================================================

B: Indirect_classification(C3):
to calulate the indirect classification values for each epochs we need to run the file mnist-cnn-c3_indirect_classification.ipynb
use this "cgan_data = torch.load('../input/conditional-gan/gan_data_epoch_EPOCH')" where EPOCH=[1,10,20,30,40,50,100,150,200] to train the convolutional neural network
and use "testloader = torch.load('../input/mnist-splitter/svdash_dataloader')" to test and get the result

==================================================================================================================

C: Blind_classification(C4):<br />
to calulate the blind classification values for each epochs we need to run the file mnist-cnn-c4_blind_classification.ipynb<br />
use this "testloader = torch.load('../input/mnist-splitter/svdash_dataloader')" to train the convolutional neural network<br />
and use "cgan_data = torch.load('../input/conditional-gan/gan_data_epoch_EPOCH')" where EPOCH=[1,10,20,30,40,50,100,150,200]  to test and get the result

==================================================================================================================
