# Vulkan Setup for Windows Using CMake and Visual Studio Code

There are various vulkan resources and tutorial that shows how to setup vulkan but I could not find any that set it up from scratch using VSCode and CMake on Windows.

The goal of here is to setup base vulkan setup on WINDOWS using `CMake` on VSCode. The only Vulkan tutorial I found that shows how to setup Vulkan with CMake was from "Brendan Galea" on of his vulkan tutorials videos series. [Project Restructure and CMake - Vulkan Game Engine Tutorial 23](https://www.youtube.com/watch?v=ZuHK_5cJ6B8&list=PL8327DO66nu9qYVKLDmdLW_84-yE4auCR&index=31). This happened later on after the series has gone far.  But I was able to use this to come up with this basic setup.

Finally, The steps are what are found in [vulkan Tutorial](https://www.vulkan-tutorial.com) site in section on [Development Environment for Windows](https://vulkan-tutorial.com/Development_environment#page_Windows)

## Download and Installations

- Make sure you have Visual Studio and it development kit installed.
- Get `Vulkan SDK` and make sure it's installed on your Computer
- Find Get `GLFW` and `GLM`
You can get full installation instruction on [Vulkan Tutorial Dev. Env. for Windows](https://vulkan-tutorial.com/Development_environment#page_Windows){:target="_blank"}


## Setting up Visual Studio Code

1. Once you have Vulkan, GLFW and GLM on your PC, Create a folder, I will call mine `vulkan_sample` give it whatever name you want. This will be your root folder

2. Then create the following sub folders in side your top folder(`vulkan_sample` in my case), `library` and `src`. Inside the `library folder`


## Optional CMake setup

set()
file(GLOB_RECURSE)