# The World of GPU's

But what exactly is a GPU, why should you care, and why do you even need one?

## What is a GPU?

GPU stands for Graphics Processing Unit. It's often used in computers, to display images to monitors. GPU's are mostly used for rendering games and for other similar rendering intensive processes, but now they are also being used in AI advancements.

You may have also heard of the term CPU (central processing unit). A CPU is present in all computers and is often referred to as the brains of a computer. GPU's are different from CPU's, as a GPU can only do a fraction of the amount of work that a CPU can, but with at an incredibly high speed. As a result GPU's are very powerful and are now being used in ways beyond rendering images.

## GPU's and AI

In recent years, GPU's have been part of the driving force behind why we see so much advancement within AI. GPU's have allowed us to learn faster from vast amounts of data.


## Has my Machine got a GPU?

Here we have a guide depending on your OS, of how to identify if you have a GPU.

<!-- tabs:start -->

#### **Windows**

1. Click Start
2. On the Start menu, click Run
3. In the Open box, type "dxdiag" (without the quotation marks), and then click OK
4. The DirectX Diagnostic Tool opens. Click the Display tab
5. On the Display tab, information about your graphics card is shown in the Device section. You can see the name of your card, as well as how much video memory it has.

!> Newer Windows often do have a GPU in them! Currently our models support NVidia GPU's.

#### **Mac**

Some MacBook Pro's have one of the following GPU's:

* AMD Radeon Pro Vega 16
* Vega 20,
* Radeon Pro 555X
* 560X GPUs

In order to check if your Mac has a GPU.

1. Apple () menu > About this Mac
2. Overview > System Report
3. Hardware > Graphics/Displays
4. Look at the 'Type' field on this panel. If it says GPU, then you do have a GPU

!> Note that although newer versions of Macs do have a GPU, some models will not work with this GPU type. This is because many AI models, use NVidia GPU's. There are wider community groups working on forming models that will work on a  wider GPU basis.

#### **Linux**

Coming soon!
<!-- tabs:end -->

## GPU's in the Cloud

In Runway, you can choose to run models on remote cloud GPU's or locally with CPU support.

In order to run remotely, use the toggle switch within your workspace. This allows you to choose if you want to run on your machine or run in the cloud.

![Remote GPU](assets/images/model_101/running_remotely.png)
