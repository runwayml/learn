# Running Models Using Your Own GPU

?> This document assumes the reader is loosely familiar with installing software on Linux.

Local GPU is here! If you are running Linux and have an NVIDIA graphics card that supports CUDA, you can now run models locally using your own GPU. This feature allows you to save money by running models on your own hardware for free!

## Prerequisites

In order to run models on your own GPU hardware, you must fulfill the following requirements:

1. You must be using Runway on Linux (We've tested on Ubuntu 18.04, but we expect it to work with other distros and Linux flavors as well)
1. You must have an NVIDIA GPU that supports CUDA (see a full list of supported GPUs [here](https://www.geforce.com/hardware/technology/cuda/supported-gpus))
1. You must have a recent version of the NVIDIA Linux drivers (Drivers can be downloaded from [NVIDIA's website directly](https://www.geforce.com/drivers) or from your package manager. You must have a driver version recent enough to support CUDA 9, 9.2, and 10. See this [version compatibility matrix](https://github.com/NVIDIA/nvidia-docker/wiki/CUDA#requirements) to make sure your drivers are up to date.)
1. You must have [NVIDIA Docker](https://github.com/NVIDIA/nvidia-docker) installed

This tutorial assumes you've already completed steps 1 and 2. We'll walk you through installing the latest NVIDIA drivers for your graphics card as well as installing and configuring NVIDIA Docker so that local runway models can take advantage of your GPU hardware.

In this tutorial, we'll be installing these dependencies on Ubuntu 18.04. If you are using a different distro or version, the logical steps will still apply, but the detailed commands will be different.

### Installing Up-to-Date NVIDIA Drivers

Ubuntu 18.04's official package repository for NVIDIA drivers has out-of-date drivers. In order to install more recent drivers, you must add the graphics-drivers [PPA](https://itsfoss.com/ppa-guide/). Open up a terminal and run the following commands:

```bash
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```

Now that we've added the `graphics-drivers/ppa`, we can install the latest NVIDIA drivers via the `Additional Drivers` section in the `Software & Updates` GUI application.

Use your application launcher to open the `Software & Updates` program, then select the `Additional Drivers` section. After a few seconds, you should see several selectable options of the format `Using NVIDIA driver metapackage from nvidia-driver-XXX`. Select the drivers with the highest number replacing "XXX". At the time of this writing, that's `nvidia-driver-430`, but you should feel confident choosing a more recent driver if you prefer.

Once you've made your selection, click `Apply Changes`. You should now restart your computer for the changes to take effect.

Once your computer reboots, open a terminal and type `nvidia-smi`. You should see an ascii table is generated with a row for each NVIDIA graphics card you have attached to your machine. Once you see output similar to this, the NVIDIA drivers have been installed correctly and you can move on to the next step.

### Installing NVIDIA Docker

The last dependency after you've installed the NVIDIA drivers is to install NVIDIA Docker. We recommend following the install instructions in the [README](https://github.com/NVIDIA/nvidia-docker) of the NVIDIA Docker package itself as the install method changes between releases.

?> The install procedure for NVIDIA Docker differs significantly depending on whether your Docker version is greater than or equal to 19.03. Run `docker --version` to check your docker version, and if its below 19.03 either update it before installing NVIDIA Docker (recommended) or [follow these instructions](https://github.com/NVIDIA/nvidia-docker/wiki/Installation-(version-2.0)) to install an older version of NVIDIA Docker.

Once you'be installed NVIDIA Docker, run the following command to test that Docker containers can access your graphics card device using the `nvidia` runtime:

```bash
docker run --gpus all nvidia/cuda:9.0-base nvidia-smi
```

If all goes well you should see an ascii table similar to the one that you saw before when you ran `nvidia-smi` manually after installing the NVIDIA drivers.

### Running Local GPU Models in Runway

If the following steps went well, you should now be ready to run GPU models locally inside of Runway. You can chose the "LOCAL" run location and the "GPU" hardware type of any model by selecting the "Advanced Opitions" link in the workspace view. You will then be prompted to download the model, and once that's done, you can run the model locally on your own GPU!

?> Whenever a model is running on your local GPU, you can use the `nvidia-smi` command to inspect the GPU memory allocation and processor utilization of each model process.
