# team_f_mamba_group

Kuzey's approach:

[VM-UNet: Vision Mamba UNet for Medical Image Segmentation](https://arxiv.org/pdf/2402.02491)

When they initialized VM-UNET with VMamba-T and VMamba-S pre-trained weights, they demonstrated significant improvement especialy for VMamba-S weights. Could we find pre-trained models for our task?
Discussions on pre-trained weights for satellite image classification: [https://gis.stackexchange.com/questions/361890/pre-trained-transfer-learning-models-for-satellite-image-classification]

Some tensorflow [pre-trained weights](https://bigearth.net/)?


(https://github.com/microsoft/torchgeo)

The [code](https://github.com/JCruan519/VM-UNet) they provided on their GitHub was designed for a Linux environment. I have spent hours trying to reconstruct the environment but am still encountering errors.

[VisionMamba](https://github.com/kyegomez/VisionMamba)

```https://anaconda.org/nvidia/cuda-toolkit```



I believe I’ve successfully created the VM-UNet environment. As far as I understand, we need a Linux environment to run this version, and it seems all other Mamba versions require this too. I created the environment using WSL.

One important aspect to consider is which CUDA Toolkit version to use. I encountered issues where some code was consuming too much disk space. Using conda install nvidia/label/cuda-11.8.0::cuda-toolkit helped me resolve some of that.

Initially, I installed the CUDA Toolkit and then proceeded to download other packages. 
