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

https://zenodo.org/records/13743856




```conda init```

```exec $SHELL```

```conda activate vmunet```

__Regarding the group meeting:__

 -We need to resize our input images to 128×128×12.
- Triton may be installed if a higher version of Python is used, as Dorathea shared the link (the Python version for VM-UNET is 3.8).
- Our group will make a presentation next week. I have divided the sections across five dates and shared the details in the team-F channel (thanks to @Anum for suggestion).
- I also added the Google Slides link.
- Isabella has also successfully constructed the environment for VM-UNET, so if we get stuck, we can reach out to her for assistance.

```cd /mnt/c/Users/Kuzey/VM-Unet```

__Error!!!__ ```Could not load library libcudnn_cnn_infer.so.8. Error: libcuda.so: cannot open shared object file: No such file or directory```

The code ilne provided in the [link](https://discuss.pytorch.org/t/libcudnn-cnn-infer-so-8-library-can-not-found/164661) solved the issue: ```export LD_LIBRARY_PATH=/usr/lib/wsl/lib:$LD_LIBRARY_PATH```

__Error!!!__ ```torch.cuda.OutOfMemoryError: CUDA out of memory. Tried to allocate 48.00 MiB (GPU 0; 6.00 GiB total capacity; 5.25 GiB already allocated; 0 bytes free; 5.34 GiB reserved in total by PyTorch) If reserved memory is >> allocated memory try setting max_split_size_mb to avoid fragmentation.  See documentation for Memory Management and PYTORCH_CUDA_ALLOC_CONF```

Decreasing the batch size and resizing images to 128×128 solved the problem!

![](https://github.com/f-kuzey-edes-huyal/team_f_mamba_group/blob/main/figures/visual_mamba_unet_first_run.png)

__Notes from the meeting with Anum, Kuzey, Verena, and Dorothea:__

- Kuzey gave a presentation on how she installed ```VM-UNET``` and discussed the challenges she faced during the process.

- Anum asked whether it would be possible to create an environment that does not require a GPU and mentioned she would attempt to construct such an environment.

- Dorothea suggested exploring other ```Mamba``` versions that might not depend on ```Triton``` and could potentially run in a Windows environment. She also proposed checking for ```Mamba``` versions that do not require a GPU and recommended using Kaggle notebooks for running the code( which needs GPU).
  
- Anum and Kuzey noted that their primary experience has been with Google Colab, where the GPU runtime often stops after some time, which can disrupt the workflow.

- Verena will update the team if her team manages to run the environment successfully on a Windows system.
