# Running Models Using Your Own GPU

?> This document assumes the reader is loosely familiar with installing software on Linux.

Local GPU is here! If you are running Linux and have an NVIDIA graphics card that supports CUDA, you can now run models using your own GPU hardware. This feature allows you to save money by running models on your own hardware for free!

## Prerequisites

In order to run models on your own GPU hardware, you must fulfill the following requirements:

1. You must be using Runway on Linux (We've tested on Ubuntu 18.04, but we expect it to work with other distros and Linux flavors as well)
1. You must have an NVIDIA GPU that supports CUDA (see a full list of supported GPUs here)
1. You must have a recent version of the NVIDIA Linux drivers (Drivers can be downloaded from NVIDIA's website directly or from your package manager. You must have a driver version recent enough to support CUDA 9, 9.2, and 10. See this version compatibility matrix to make sure your drivers are up to date.)
1. You must have `nvidia-docker` installed

This tutorial assumes you've already completed steps 1 and 2. We'll walk you through installing the latest NVIDIA drivers for your graphics card as well as installing and configuring `nvidia-docker` so that local runway models can take advantage of your GPU hardware.

In this tutorial, we'll be installing these dependencies on Ubuntu 18.04. If you are using a different distro or version, the logical steps will still apply, but the detailed commands will be different.

### Installing Up-to-Date NVIDIA Drivers
