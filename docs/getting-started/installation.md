# Installation Guide

Learn how to setup your new Runway account and get started using Runway now! 🚀

![Runway Maker](/../assets/images/getting-started/laptopmaker.jpg)

### Download Runway

Get started by downloading the [latest release of Runway](https://runwayml.com/download). Once you you have downloaded Runway, follow the steps below to create your new account and get started using Runway.

?> If you encounter any problems or issues with the installation, please visit the [Support Center](https://support.runwayml.com/).

?> Having trouble installing Runway on Linux? Check out this [Runway on Linux guide](https://support.runwayml.com/en/articles/3116268-runway-on-linux).

### Create an Account

Once you have downloaded the app, open Runway. If you haven't created an account yet click the **Create an account** button at the bottom of the login window.

<div class="Img-Small">
  <img src="assets/images/installation/login_01.png" alt="Runway Login Email Verification" >
  <p>Runway Login Window</p>
</div>

Next, add your email:

<div class="Img-Small">
  <img src="assets/images/installation/login_02.png" alt="Runway Account Creation" >
  <p>Add your email to your account</p>
</div>

Click next and create a new username and a strong password. Your username will be a unique identifier for your models.

<div class="Img-Small">
  <img src="assets/images/installation/login_03.png" alt="Runway Account Creation" >
  <p>Create your username and password</p>
</div>

?> We enforce minimum password strength requirements to protect users from automated password guessing attacks. We strongly recommend using a [password manager](https://en.wikipedia.org/wiki/Password_manager) like [1Password](https://1password.com/) or [LastPass](https://www.lastpass.com/) (free) to generate and store cryptographically random passwords.

Click next and add your final details. If you are planning on using Runway from an organization (company, school, NGO, research lab, etc) please enter the organization name.

<div class="Img-Small">
  <img src="assets/images/installation/login_04.png" alt="Runway Account Creation" >
  <p>Your account details</p>
</div>

Once your account has been created, you will need to verify the email associated with your account. Please check your inbox for a verification code. Be sure to **check your spam or promotions folder** if you don't receive a verification code after a few minutes.

<div class="Img-Small">
  <img src="assets/images/installation/login_05.png" alt="Runway Verification code" >
  <p>Enter the Verification Code</p>
</div>

After verifying your account you are good to go! If you log out of your account you can enter again by using either your email or username and your password. You can login and logout from any computer, but only one instance of Runway can be running at any given time using a single user account.

<div class="Img-Small">
  <img src="assets/images/installation/login_06.png" alt="Runway Account Verified" >
  <p>Account Verified. All Set!</p>
</div>

?> The app will auto-update every time there is a new update available. You will also see a message at the top right corner of the app if an update is ready. There's no need to manually download the app again to receive updates.

### Running Models Locally

At the core of Runway you will find machine learning models. Models can be used and run in Runway's cloud infrastructure or run locally on your computer.

When running models in Runway's cloud infrastructure, you'll be running them on ✨fast GPU enabled computers ✨, and credits will be deducted from your account. You will find that some models are only available on remote GPU and not to download locally. 

When running models locally, you'll need to download and install them individually. Some models require you to install [Docker](https://www.docker.com/) locally. Docker CE is a free and open-source software.

?>  **Keep in mind**: You **don't** need Docker to run models remotely!

You can download and install Docker using the following links:

- [Mac](https://download.docker.com/mac/stable/Docker.dmg)
- [Windows](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)
- [Linux](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

!> Docker for Windows requires Microsoft Hyper-V, which is supported only in the Pro, Enterprise or Education editions of Windows. If you don't have a Pro, Enterprise or Education Windows edition you will not be able to install Docker and you will be able to only run some Runway models. 

Once Docker is installed and running, you should see the following:

- **On Mac**: a Docker icon in the top status bar. This indicates that Docker is running and accessible from Runway.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-mac.png" alt="Docker Icon mac" >
  <p>A whale in the top status bar indicates that Docker is running.</p>
</div>

Please refer to [this official Docker](https://docs.docker.com/docker-for-mac/install/#install-and-run-docker-for-mac) installation guide on Mac if you are having any issues.

- **On Windows**: a Docker icon in the bottom notifications area. This indicates that Docker is running and accessible from Runway.

<div class="Img-Small">
  <img src="https://runway.nyc3.digitaloceanspaces.com/documentation/docker-bar-windows.png" alt="Docker Icon mac" >
  <p>Docker icon in the Notifications area or System tray. </p>
</div>

<p class='note'><b>Check your Firewall</b>: If you encounter any issues with Docker on Windows, please check your Windows Firewall and see that it is not affecting Docker. Also, be sure that Windows has at least one Share Drive with Docker.</p>

Please refer to [this official Docker](https://docs.docker.com/docker-for-windows/) installation guide on Windows if you are having any issues.

- **On Linux**: verify if docker is installed and running with the following command:

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

### Increase Docker Memory Limit

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