# How-To: Run Models Locally

To run models locally, you need to download and install them individually. 

Some **local** models require you to install [Docker](https://www.docker.com/). Docker CE is a free and open-source software. You **do not** need Docker to run models remotely! 

If you need to install Docker, here are the steps:

## **Step 1: Download and install Docker from the following links:** 
* [Mac](https://download.docker.com/mac/stable/Docker.dmg)
* [Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)
* [Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

?> Docker for Windows requires Microsoft Hyper-V, which is supported only in the Pro, Enterprise, or Education editions of Windows. If you don't have a Pro, Enterprise ,or Education Windows edition then you will not be able to install Docker, and you can only run some RunwayML models. 

## **Step 2: Once Docker is installed and running, you should see the following:**

**On Mac**: a Docker icon in the top status bar. This indicates that Docker is running and accessible from RunwayML. Please refer to [this official Docker](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac) installation guide on Mac if you are having any issues.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-mac.png" alt="Docker Icon mac" >
  <p>A whale in the top status bar indicates that Docker is running.</p>
</div>

**On Windows**: a Docker icon in the bottom notifications area. This indicates that Docker is running and accessible from RunwayML. If you encounter any issues with Docker on Windows, please check that your Windows Firewall is not affecting Docker. Also, be sure that Windows has at least one Share Drive with Docker. Please refer to [this official Docker](https://docs.docker.com/docker-for-windows/) installation guide on Windows if you continue to have any issues.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-windows.png" alt="Docker Icon mac" >
  <p>Docker icon in the Notifications area or System tray. </p>
</div>

**On Linux**: verify if docker is installed and running with the following command: `docker --help`

## **Step 3: RunwayML will notify you if Docker is running or not:**
 In the bottom status bar inside RunwayML, look for a whale icon and a message that that Docker is available:

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-available-Runway.png" alt="Docker Icon mac" >
  <p>A whale icon in the bottom status bar inside RunwayML.</p>
</div>

If Docker is not installed, unavailable, or not running you will see the following message:

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-unavailable-Runway.png" alt="Docker Icon mac" >
  <p>If Docker is not available, RunwayML will show a "Docker Unavailable" message in the bottom status bar.</p>
</div>

?> **Increase Docker's Memory Limit:** Several models require a significant amount of memory in order to run properly. By default, Docker allocates a maximum of 2 GB of memory to run models. Some RunwayML models exceed that, which may lead to errors. Without enough memory models, may misbehave or fail silently without a helpful error message. To prevent that, you need to increase Docker's memory limit. Follow the steps in this related technical support article: [Docker Errors. Having trouble with Docker? Here are few tips.](https://support.runwayml.com/en/articles/3069033-docker-errors)