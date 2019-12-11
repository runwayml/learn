# How-To: Use Your Own GPU (Linux Only)

?> This document assumes the reader is loosely familiar with installing software on Linux.

Local GPU is here! If you are running RunwayML on Linux and have an NVIDIA graphics card that supports CUDA, you can now run models locally using your own GPU.

### Prerequisites

In order to run models on your own GPU hardware, you must fulfill the following requirements:

1. You must be using RunwayML on Linux (Tested on Ubuntu 18.04)
1. You must have an NVIDIA GPU that supports CUDA (see a full list of supported GPUs [here](https://www.geforce.com/hardware/technology/cuda/supported-gpus))
1. You must have a recent version of the NVIDIA Linux drivers (Drivers can be downloaded from [NVIDIA's website directly](https://www.geforce.com/drivers) or from your package manager. You must have a driver version recent enough to support CUDA 9, 9.2, and 10. See this [version compatibility matrix](https://github.com/NVIDIA/nvidia-docker/wiki/CUDA#requirements) to make sure your drivers are up to date.)
1. You must have [`nvidia-docker2`](https://github.com/NVIDIA/nvidia-docker/wiki/Installation-(version-2.0)) installed

This tutorial assumes you've already completed steps 1 and 2. We'll walk you through installing the latest NVIDIA drivers for your graphics card as well as installing and configuring `nvidia-docker2` so that local runway models can take advantage of your GPU hardware.

In this tutorial, we'll be installing these dependencies on Ubuntu 18.04. If you are using a different distribution or version, the logical steps will still apply, but the detailed commands will be different.

### Installing Up-to-Date NVIDIA Drivers

Ubuntu 18.04's official package repository for NVIDIA drivers has out-of-date drivers. In order to install more recent drivers, you must add the graphics-drivers [PPA](https://itsfoss.com/ppa-guide/). Open up a terminal and run the following commands:

```bash
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```

Now that we've added the `graphics-drivers/ppa`, we can install the latest NVIDIA drivers via the `Additional Drivers` section in the `Software & Updates` GUI application.

Use your application launcher to open the `Software & Updates` program, then select the `Additional Drivers` section. After a few seconds, you should see several selectable options of the format `Using NVIDIA driver metapackage from nvidia-driver-XXX`. Select the drivers with the highest number replacing "XXX". At the time of this writing, that's `nvidia-driver-430`, but you should feel confident choosing a more recent driver if you prefer.

![](assets/images/how-to/local-gpu/software-and-updates.png)

Once you've made your selection, click `Apply Changes`. You should now restart your computer for the changes to take effect.

Once your computer reboots, open a terminal and type `nvidia-smi`. You should see an ascii table is generated with a row for each NVIDIA graphics card you have attached to your machine. Once you see output similar to this, the NVIDIA drivers have been installed correctly and you can move on to the next step.

```
Mon Jul 29 18:19:40 2019
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 430.26       Driver Version: 430.26       CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1080    Off  | 00000000:01:00.0  On |                  N/A |
|  0%   49C    P0    46W / 180W |   1119MiB /  8116MiB |      1%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1689      G   /usr/lib/xorg/Xorg                            40MiB |
|    0      1736      G   /usr/bin/gnome-shell                          50MiB |
+-----------------------------------------------------------------------------+
```

### Installing `nvidia-docker2`

The last dependency after you've installed the NVIDIA drivers is to install `nvidia-docker2`. We recommend following the install instructions in the [README](https://github.com/NVIDIA/nvidia-docker/wiki/Installation-(version-2.0)) of the `nvidia-docker2` package itself as the install method changes between releases.

?> We do not yet support the *very recent* `nvidia-container-toolkit`, so be sure you install `nvidia-docker2`. We have plans to upgrade to the newer NVIDIA Docker Toolkit soon! In the meantime, it is perfectly fine to have both `nvidia-docker2` and `nvidia-container-toolkit` installed on the same machine, so you should feel confident in installing `nvidia-docker2` even if you already have the more recent `nvidia-container-toolkit` installed.

Once you've installed `nvidia-docker2`, run the following command to test that Docker containers can access your graphics card device using the `nvidia` runtime:

```bash
docker run --runtime nvidia nvidia/cuda:9.0-base nvidia-smi
```

If all goes well you should see an ascii table similar to the one that you saw before when you ran `nvidia-smi` manually after installing the NVIDIA drivers.

### Running Local GPU Models in RunwayML

If the following steps went well, you should now be ready to run GPU models locally inside of RunwayML. You can choose the "LOCAL" run location and the "GPU" hardware type of any model by selecting the "Advanced Options" link in the workspace view of RunwayML. You will then be prompted to download the model, and once that's done, you can run the model locally on your own GPU!

You can select Local GPU by clicking the `Advanced Options` link.

<img src="assets/images/how-to/local-gpu/run-local-gpu-1.png" style="display: block; width: 50%; margin: auto"/>

From there, select `LOCAL` as the `Run Option` and `GPU` as the `Hardware` option.

<img src="assets/images/how-to/local-gpu/run-local-gpu-2.png" style="display: block; width: 50%; margin: auto"/>

If you don't already have the GPU version of the model installed, you will be prompted to download and install it next.

<img src="assets/images/how-to/local-gpu/run-local-gpu-3.png" style="display: block; width: 50%; margin: auto"/>

Once the download is complete, you can run the model locally on your own GPU hardware!

<img src="assets/images/how-to/local-gpu/run-local-gpu-4.png" style="display: block; width: 50%; margin: auto"/>

?> Whenever a model is running on your local GPU, you can use the `nvidia-smi` command to inspect the GPU memory allocation and processor utilization of each model process.
