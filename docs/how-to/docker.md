# Running Models Locally

With Runway, you can choose to run model remotely with GPU support or locally in your computer with CPU support. *Only* when running models locally, you will need to install and use Docker. Here we discuss why we need to install Docker when you run Runway models locally.


## Which models can be run Locally?

The model information regarding CPU and GPU support lives inside every model view page. If the model supports CPU and/or GPU will be described in the characteristics table. If the model supports CPU you can run it locally on your computer. For example, we can see that the model called Facial Landmarks is able to run locally:

![CPU model](assets/images/how-to/run-locally/model-cpu.png)

## What is Docker?

[Docker](https://www.docker.com/) is a tool designed to run, deploy and create applications that live inside containers. Containers are a way of making closed and specific environments for every application. This allows to control what is installed within a container for your application, so you can have only the things that are needed.

[Docker](https://www.docker.com/) is not the same as a virtual machine (VM). Docker differs from a VM, as a VM will include a complete OS. The VM will act and run independently from your computer. But Docker in many ways, has a pick-and-choose kinder attitude and will use your computer's resources, so it's less independent and arguably in many ways lighter to use.


When running a [local model](getting-started/model-101), Runway will ask you to download and install the container that runs that specific model and will handle all necessary installation and configurations.

## Download Docker

Only when running models locally, you will need to have [Docker](https://www.docker.com/) installed in your computer. This is only a requirement when running models locally. Docker is FREE and open-source software. Find out more, about [why we use Docker](getting-started/docker.md).

<!-- tabs:start -->

#### **Mac**

**Download Docker:** [Download Docker for Mac](https://download.docker.com/mac/stable/Docker.dmg)

**Verify Installation:** a Docker icon in the top status bar. This indicates that Docker is running and accessible from Runway.

<div class="Img-Small">
  <img src="assets/images/how-to/run-locally/docker-bar-mac.png" alt="Docker Icon mac" >
  <p>A whale in the top status bar indicates that Docker is running.</p>
</div>

Please refer to [this official Docker](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac) installation guide on Mac if you are having any issues.


#### **Windows**

**Download Docker:** [Download Docker for Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)

!> For Windows, you'll need to have a Pro, Enterprise or Education edition of Windows, in order to install Docker. If you're unable to install Docker on your Windows machine, don't worry, some of our models will still work for you!

Once Docker is installed and running, you should see the following:


**Verify Installation:** a Docker icon in the bottom notifications area. This indicates that Docker is running and accessible from Runway.

<div class="Img-Small">
  <img src="assets/images/how-to/run-locally/docker-bar-windows.png" alt="Docker Icon mac" >
  <p>Docker icon in the Notifications area or System tray. </p>
</div>

<p class='note'><b>Check your Firewall</b>: If you encounter any issues with Docker on Windows, please check your Windows Firewall and see that it is not affecting Docker. Also, be sure that Windows has at least one Share Drive with Docker.</p>

Please refer to [this official Docker](https://docs.docker.com/docker-for-windows/) installation guide on Windows if you are having any issues.


#### **Linux**

**Download Docker:** [Download Docker for Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

**Verify Installation:** verify if docker is installed and running with the following command:

```sh
docker --help
```

Runway will notify you if Docker is running or not. In the bottom status bar inside Runway you will see a whale icon and a message that indicates that Docker is available:

<div class="Img-Small">
  <img src="assets/images/how-to/run-locally/docker-available-Runway.png" alt="Docker Icon mac" >
  <p>A whale icon in the bottom status bar inside Runway.</p>
</div>

If Docker is not installed, unavailable or not running you will see the following message:

<div class="Img-Small">
  <img src="assets/images/how-to/run-locally/docker-unavailable-Runway.png" alt="Docker Icon mac" >
  <p>If Docker is not available, Runway will show a "Docker Unavailable" message in the bottom status bar.</p>
</div>

<!-- tabs:end -->

## Increase Docker memory limit

By default, Docker allocates a maximum of 2 GB of memory to run models. Some Runway models exceed that, which may lead to errors. To prevent that, you need to increase Docker's memory limit. Open Docker Preferences:

<div class="Img-Small">
  <img src="assets/images/how-to/run-locally/docker_open_preferences.png" alt="Docker Open Preferences" >
  <p>Open Docker preferences.</p>
</div>

Go to the "Advanced" tab.

<div class="Img-Small">
  <img src="assets/images/how-to/run-locally/docker_advanced_tab.png" alt="Docker Open Preferences" >
  <p>Go to the "Advanced" tab in Preferences.</p>
</div>

Increase the "Memory" slider to 8.0 GB, then click "Apply & Restart."

<div class="Img-Small">
  <img src="assets/images/how-to/run-locally/docker_increase_limit.png" alt="Docker Open Preferences" >
  <p>Increase Docker's memory limit.</p>
</div>

All set!


### Links

If you're still interested in learning more about Docker, we recommend reading some of the following resources

* [Docker Tutorial for Beginners](https://www.youtube.com/watch?v=JBtWxj9l7zM), By LearnCode.academy
