# Docker

Here we discuss why we need to install Docker when you run Runway.

![Select Model](images/tutorial_docker/docker.png)

### What is Docker?

[Docker](https://www.docker.com/) is a tool which is designed to run, deploy and create applications, in a container. Containers are a way of making an environment similar to that of your computers Operating System (OS). This allows us to control what is installed within a container for your application, so we have only the things that are needed.

Some of you may wonder if [Docker](https://www.docker.com/) is the same as a virtual machine (VM). Docker differs from a VM, as a VM will include a complete OS. The VM will act and run independently from your computer. But Docker in many ways, has a pick-and-choose kinder attitude and will use your computers resources, so it's less independent and arguably in many ways lighter to use.

### Runway Using Docker

Here at Runway, we use [Docker](https://www.docker.com/) to help us run our AI models. AI is usually pretty difficult to build and run, as there are often a lot requirements needed. By using Docker, we have already made these containers to run our AI capabilities. So you don't have to worry about creating or using Docker! We take the pains of installation away, to ensure you get to focus on being creative.

When you add a [local model](getting-started/model-101) to your workspace, Runway asks Docker to download and launch one of our containers. Now Runway directs both your input and output from the Docker container.

<Insert diagram>

### What do I need to do with Docker?

Nothing! Just make sure it's installed and working in the background. For installation of Docker, [check out our installation guide](getting-started/installation).

### Is Docker really free?

Of course! We have chosen to use Docker, as we want to ensure everyone can use Runway. By using Docker, it allows you to run our local models on your computer.

### Links

If you're still interested in learning more about Docker, we recommend reading some of the following resources

* [Docker Tutorial for Beginners](https://www.youtube.com/watch?v=JBtWxj9l7zM), By LearnCode.academy
