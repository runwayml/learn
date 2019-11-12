# Run Models in RunwayML

## Overview
If you're just getting started, check out our guide on how to [Use Models](https://learn.runwayml.com/#/how-to/use-models) for information on finding models in RunwayML, setting them up, running them, and stopping them inside of the app -- no coding required!

This guide provides additional information about requirements for running models on your computer's local CPU, local GPU (Linux only), and on a remote GPU. (Curious about the difference between a CPU and a GPU? Here's a [video from Mythbusters](https://www.youtube.com/watch?v=-P28LKWTzrI) that demonstrates the distinction.)

## Local CPU
To run models locally on your computer, you need to download and install them individually. Some local models require you to install Docker. Docker CE is free and open-source software. **You do not need Docker to run models [remotely](http://localhost:4000/#/how-to/run-models?id=remote-gpu)!** 

If you need to install Docker, here are the steps:

### **Step 1: Install Docker** 
Download Docker from the following links:
* [Mac](https://download.docker.com/mac/stable/Docker.dmg)
* [Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)
* [Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

?> Docker for Windows requires Microsoft Hyper-V, which is supported only in the Pro, Enterprise, or Education editions of Windows. If you don't have a Pro, Enterprise, or Education Windows edition then you will not be able to install Docker, and you can only run some RunwayML models. 

### **Step 2: Verify that Docker is Installed and Running**

**On Mac**: a Docker icon in the top status bar. This indicates that Docker is running and accessible from Runway. Please refer to [this official Docker](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac) installation guide on Mac if you are having any issues.

<!-- <div class="Img-Small"> -->
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-mac.png" alt="Docker Icon mac" >
  <p>A whale in the top status bar indicates that Docker is running.</p>
<!-- </div> -->

**On Windows**: a Docker icon in the bottom notifications area. This indicates that Docker is running and accessible from RunwayML. If you encounter any issues with Docker on Windows, please check that your Windows Firewall is not affecting Docker. Also, be sure that Windows has at least one Share Drive with Docker. Please refer to [this official Docker](https://docs.docker.com/docker-for-windows/) installation guide on Windows if you continue to have any issues.

<!-- <div class="Img-Small"> -->
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-windows.png" alt="Docker Icon mac" >
  <p>Docker icon in the Notifications area or System tray. </p>
<!-- </div> -->

**On Linux**: verify if Docker is installed and running with the following command: `docker --help`

### **Step 3: Check RunwayML for Docker's Status**
 In the bottom status bar inside RunwayML, look for a whale icon and a message that that Docker is available:

<!-- <div class="Img-Small"> -->
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-available-Runway.png" alt="Docker Icon mac" >
  <p>A whale icon in the bottom status bar inside RunwayML.</p>
<!-- </div> -->

If Docker is not installed, unavailable, or not running you will see the following message:

<!-- <div class="Img-Small"> -->
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-unavailable-Runway.png" alt="Docker Icon mac" >
  <p>If Docker is not available, RunwayML will show a "Docker Unavailable" message in the bottom status bar.</p>
<!-- </div> -->

### **Step 4: Increase Docker's Memory Limit (optional)** 
Several models require a significant amount of memory in order to run properly. By default, Docker allocates a maximum of 2 GB of memory to run models. Some RunwayML models exceed that, which may lead to errors. Without enough memory models, may misbehave or fail silently without a helpful error message. To prevent that, you need to increase Docker's memory limit. Follow the steps in this related technical support article: [Docker Errors. Having trouble with Docker? Here are few tips.](https://support.runwayml.com/en/articles/3069033-docker-errors)

Related Technical Support Resources:
* [Changing Where Local Models are Downloaded](https://support.runwayml.com/en/articles/3203817-changing-where-local-models-are-downloaded)
* [Deleting Local Models](https://support.runwayml.com/en/articles/3077861-deleting-local-models)
* [Docker Errors. Having trouble with Docker? Here are few tips.](https://support.runwayml.com/en/articles/3069033-docker-errors)
* [Running Docker without sudo](https://support.runwayml.com/en/articles/3359183-running-docker-without-sudo)



## Local GPU (Linux Only)
If you are running RunwayML on Linux and have an NVIDIA graphics card that supports CUDA, you can run models locally using your own GPU. This guide assumes that the reader is loosely familiar with installing software on Linux.

### Step 1: Prerequisites
In order to run models on your own GPU hardware, you must fulfill the following requirements:

1. You must be using RunwayML on Linux (Tested on Ubuntu 18.04)
1. You must have an NVIDIA GPU that supports CUDA. See a full list of supported GPUs [here](https://www.geforce.com/hardware/technology/cuda/supported-gpus).
1. You must have a recent version of the NVIDIA Linux drivers Download drivers from [NVIDIA's website directly](https://www.geforce.com/drivers) or from your package manager. You must have a driver version recent enough to support CUDA 9, 9.2, and 10. See this [version compatibility matrix](https://github.com/NVIDIA/nvidia-docker/wiki/CUDA#requirements) to make sure your drivers are up to date.
1. You must have [`nvidia-docker2`](https://github.com/NVIDIA/nvidia-docker/wiki/Installation-(version-2.0)) installed.

This tutorial assumes you've already fulfilled the first two prerequisites above. We'll walk you through installing the latest NVIDIA drivers for your graphics card as well as installing and configuring `nvidia-docker2` so that local RunwayML models can use your GPU hardware. We'll be installing these dependencies on Ubuntu 18.04. If you are using a different distribution or version, the logical steps will still apply, but the detailed commands will be different.

### Step 2: Installing Up-to-Date NVIDIA Drivers
Ubuntu 18.04's official package repository for NVIDIA drivers has out-of-date drivers. In order to install more recent drivers, you must add the graphics-drivers [PPA](https://itsfoss.com/ppa-guide/). Open up a terminal and run the following commands:

```bash
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```

Now that we've added the `graphics-drivers/ppa`, we can install the latest NVIDIA drivers via the `Additional Drivers` section in the `Software & Updates` GUI application.

Use your application launcher to open the `Software & Updates` program, then select the `Additional Drivers` section. After a few seconds, you should see several selectable options of the format `Using NVIDIA driver metapackage from nvidia-driver-XXX`. Select the drivers with the highest number replacing "XXX". At the time of this writing (July 2019), that's `nvidia-driver-430`, but you should feel confident choosing a more recent driver if you prefer.

![](assets/images/how-to/local-gpu/software-and-updates.png)

Once you've made your selection, click `Apply Changes`. You should now restart your computer for the changes to take effect.

Once your computer reboots, open a terminal and type `nvidia-smi`. You should see an ASCII table generated with a row for each NVIDIA graphics card you have attached to your machine. Once you see output similar to this, the NVIDIA drivers have been installed correctly, and you can move on to the next step.

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

### Step 3: Installing nvidia-docker2
The last dependency, after you've installed the NVIDIA drivers, is to install `nvidia-docker2`. We recommend following the install instructions in the [README](https://github.com/NVIDIA/nvidia-docker/wiki/Installation-(version-2.0)) of the `nvidia-docker2` package itself as the install method changes between releases.

?> We do not yet support the *very recent* `nvidia-container-toolkit`, so be sure you install `nvidia-docker2`. We have plans to upgrade to the newer NVIDIA Docker Toolkit soon! In the meantime, it is perfectly fine to have both `nvidia-docker2` and `nvidia-container-toolkit` installed on the same machine, so you should feel confident in installing `nvidia-docker2` even if you already have the more recent `nvidia-container-toolkit` installed.

Once you've installed `nvidia-docker2`, run the following command to test that Docker containers can access your graphics card device using the `nvidia` runtime:

```bash
docker run --runtime nvidia nvidia/cuda:9.0-base nvidia-smi
```

If all goes well you should see an ASCII table similar to the one that you saw before when you ran `nvidia-smi` manually after installing the NVIDIA drivers.

### Step 4: Running Local GPU Models in RunwayML

If the following steps went well, you should be ready to run GPU models locally inside of RunwayML. You can choose the "LOCAL" run location and the "GPU" hardware type of any model by selecting the "Advanced Options" link in the workspace view of RunwayML. You will then be prompted to download the model, and once that's done, you can run the model locally on your own GPU!

You can select Local GPU by clicking the `Advanced Options` link.

<img src="assets/images/how-to/local-gpu/run-local-gpu-1.png" style="width: 50%; margin: auto"/>

From there, select `LOCAL` as the `Run Option` and `GPU` as the `Hardware` option.

<img src="assets/images/how-to/local-gpu/run-local-gpu-2.png" style="width: 50%; margin: auto"/>

If you don't already have the GPU version of the model installed, you will be prompted to download and install it next.

<img src="assets/images/how-to/local-gpu/run-local-gpu-3.png" style="width: 50%; margin: auto"/>

Once the download is complete, you can run the model locally on your own GPU hardware!

<img src="assets/images/how-to/local-gpu/run-local-gpu-4.png" style="width: 50%; margin: auto"/>

?> Whenever a model is running on your local GPU, you can use the `nvidia-smi` command to inspect the GPU memory allocation and processor utilization of each model process.

Related Technical Support Resources: 
* [Local GPU (Linux Only)](https://support.runwayml.com/en/articles/3140813-local-gpu)
* [Deleting Local Models](https://support.runwayml.com/en/articles/3077861-deleting-local-models)
* [Docker Errors. Having trouble with Docker? Here are few tips.](https://support.runwayml.com/en/articles/3069033-docker-errors)
* [Running Docker without sudo](https://support.runwayml.com/en/articles/3359183-running-docker-without-sudo)



## Remote GPU
Running a model with fast GPU-enabled computer in RunwayML's cloud infrastructure, or Remote GPU, [uses credits](https://support.runwayml.com/credits-and-plans/how-much-does-runway-cost), but the model runs much faster than using your computer's local CPU. Some models are only available for Remote GPU and not available to download locally.

Related Technical Support Resources: 
* [Remote GPU](https://support.runwayml.com/en/articles/3059347-remote-gpu)
* [How Much Does RunwayML Cost?](https://support.runwayml.com/en/articles/3000086-how-much-does-runwayml-cost)
* [Adding Credits](https://support.runwayml.com/en/articles/2984968-adding-credits)
* [Redeeming Coupon Codes](https://support.runwayml.com/en/articles/3047429-redeeming-coupon-codes)