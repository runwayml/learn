# Installation

If you haven't yet downloaded Runway, then let's begin by getting you an [invite to download the app](https://runwayml.com/). You can do this through signing up on our list on [runwayml.com](https://runwayml.com/). Shortly after getting an email, you should receive a link to download Runway. Download the right version for your operating system.

?> If you encounter any problems or issues with the installation, please send us an email to [support@runwayml.com](mailto:support@runwayml.com).

## Create an Account

Once you have downloaded the app, open Runway by double clicking the icon and you will be prompt to create a new account. Start by entering the email you used to register with.

<div class="Img-Small">
  <img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/login_01.png" alt="Runway Login Email Verification" >
  <p>Enter your registered email.</p>
</div>

Next, create your Runway account. Choose your `username`, a strong `password` and enter your first and last name. If you are planning on using Runway from an organization (company, school, NGO, Research Lab, etc) please enter the organization name.

<div class="Img-Small">
  <img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/login_02.png" alt="Runway Account Creation" >
  <p>Create your Runway account.</p>
</div>

Once your account has been created, you will need to verify the email associated with your account. Please check your inbox for a verification code we will send. Check your spam or promotions folder in case you don't receive a verification code after a few minutes.

<div class="Img-Small">
  <img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/login_04.png" alt="Runway Verification code" >
  <p>Enter the Verification Code</p>
</div>

After verifying your account you are good to go! If you log out of your account you can enter again just by typing your email, username and password.

<div class="Img-Small">
  <img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/login_06.png" alt="Runway Account Verified" >
  <p>Account Verified. All Set!</p>
</div>

?> The app will auto-update every time there is a new update available. You will also see a message at the top right corner of the app if an update is ready. There's no need to manually download the app again to receive updates.

<p class='note'><b>Note for Linux users</b>: You will need to configure Runway to run as an AppImage. Please follow <a href="https://discourse.appimage.org/t/how-to-run-an-appimage/80">this extra step</a>.</p>

## Download Docker

In order to use all of Runway capabilities you will need to have [Docker](https://www.docker.com/) installed in your computer. This is only a requirement when you want to run some AI locally on your system. Docker is FREE and open-source software. Find out more, about [why we use Docker](getting-started/docker.md).

<!-- tabs:start -->

#### **Mac**

**Download Docker:** [Download Docker for Mac](https://download.docker.com/mac/stable/Docker.dmg)

**Verify Installation:** a Docker icon in the top status bar. This indicates that Docker is running and accessible from Runway.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-mac.png" alt="Docker Icon mac" >
  <p>A whale in the top status bar indicates that Docker is running.</p>
</div>

Please refer to [this official Docker](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac) installation guide on Mac if you are having any issues.


#### **Windows**

**Download Docker:** [Download Docker for Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)

!> For Windows, you'll need to have a Pro, Enterprise or Education edition of Windows, in order to install Docker. If you're unable to install Docker on your Windows machine, don't worry, some of our models will still work for you!

Once Docker is installed and running, you should see the following:


**Verify Installation:** a Docker icon in the bottom notifications area. This indicates that Docker is running and accessible from Runway.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-windows.png" alt="Docker Icon mac" >
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
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-available-Runway.png" alt="Docker Icon mac" >
  <p>A whale icon in the bottom status bar inside Runway.</p>
</div>

If Docker is not installed, unavailable or not running you will see the following message:

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-unavailable-Runway.png" alt="Docker Icon mac" >
  <p>If Docker is not available, Runway will show a "Docker Unavailable" message in the bottom status bar.</p>
</div>

<!-- tabs:end -->


## Increase Docker memory limit

By default, Docker allocates a maximum of 2 GB of memory to run models. Some Runway models exceed that, which may lead to errors. To prevent that, you need to increase Docker's memory limit. Open Docker Preferences:

<div class="Img-Small">
  <img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/docker_open_preferences.png" alt="Docker Open Preferences" >
  <p>Open Docker preferences.</p>
</div>

Go to the "Advanced" tab.

<div class="Img-Small">
  <img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/docker_advanced_tab.png" alt="Docker Open Preferences" >
  <p>Go to the "Advanced" tab in Preferences.</p>
</div>

Increase the "Memory" slider to 8.0 GB, then click "Apply & Restart."

<div class="Img-Small">
  <img src="https://runway.nyc3.cdn.digitaloceanspaces.com/documentation/docker_increase_limit.png" alt="Docker Open Preferences" >
  <p>Increase Docker's memory limit.</p>
</div>

All set!
