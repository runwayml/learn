# Running Models Locally

Here at Runway, we use [Docker](https://www.docker.com/) to help us run our AI models locally. You only need to use Docker, if you'd like to run some of the models locally. Here we discuss why we need to install Docker when you run Runway.

![Select Model](assets/images/tutorials/tutorial_docker/docker-runway.png)


## Which models can be run Locally?

When you browse models, you can see in the model information, if it supports CPU and/or GPU. If the model supports CPU you can run on your local harddrive. Here we see the model Facial Landmarks is able to run locally.

![CPU model](assets/images/how-to/run-locally/model-cpu.png)

## What is Docker?

[Docker](https://www.docker.com/) is a tool which is designed to run, deploy and create applications, in a container. Containers are a way of making an environment similar to that of your computers Operating System (OS). This allows us to control what is installed within a container for your application, so we have only the things that are needed.

Some of you may wonder if [Docker](https://www.docker.com/) is the same as a virtual machine (VM). Docker differs from a VM, as a VM will include a complete OS. The VM will act and run independently from your computer. But Docker in many ways, has a pick-and-choose kinder attitude and will use your computers resources, so it's less independent and arguably in many ways lighter to use.

AI is usually pretty difficult to build and run, as there are often a lot requirements needed. By using Docker, we have already made these containers to run our AI capabilities. So you don't have to worry about creating or using Docker! We take the pains of installation away, to ensure you get to focus on being creative.

When you add a [local model](getting-started/model-101) to your workspace, Runway asks Docker to download and launch one of our containers. Now Runway directs both your input and output from the Docker container.

<Insert diagram>

## Download Docker

In order to use all of Runway capabilities you will need to have [Docker](https://www.docker.com/) installed in your computer. This is only a requirement when you want to run some AI locally on your system. Docker is FREE and open-source software. Find out more, about [why we use Docker](getting-started/docker.md).

### Is Docker free?

Yes! We have chosen to use Docker, as we want to ensure everyone can use Runway. By using Docker, it allows you to run our local models on your computer.


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
