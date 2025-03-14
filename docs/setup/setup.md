---
title: Setup Guide
layout: default
nav_order: 4
has_children: true
---
# Setup Guide

## Step 1: Install Git

Download and install Git from [https://git-scm.com/](https://git-scm.com/).

## Step 2: Install Docker

For linux system follow [this](https://docs.docker.com/engine/install/ubuntu/)

## Step 3: Set Up an IDE

Choose one of the following:

### Using Visual Studio Code:

1. Download and install Visual Studio Code from [https://code.visualstudio.com/](https://code.visualstudio.com/).
2. Install the Flutter and Dart extensions.

#### Coding inside Docker Container

##### Android

To help contributors working with the same dependencies and SDKs, in .devcontainer folder there a Dockerfile with all the necessary for coding.

On VSCode install [Dev Container exentension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers). This extension allows you to coding inside a Docker container directly in VSCode.

Once the extension in installed at the bottom left corner of VSCode window click on "Open a Remote Window" then click on "Reopen in Container". This will create a Docker container inside which you'll have all the necessary dependencies for coding.

### Using IntelliJ IDEA or Android Studio:

1. Download and install IntelliJ IDEA or Android Studio.
2. Install the Flutter and Dart plugins.

## Step 4: Fork the repository

This is very simple, just go to the Sossoldi repository on GitHub and click on the “Fork” on the top right corner. By doing this you will create a copy of the repository on your account and it will allow you to make changes without affecting the main repository.

## (Optional) Download GitHub Desktop

If you are unfamiliar with Git you might want to use GitHub Desktop.

1. Go to this link and download GitHub Desktop. With this it will be easier to manage and submit the changes that you will do. After the download, set up your account.
2. Now comeback to your repository on GitHub and click on Code -> Open with GitHub Desktop
3. This will open GitHub Desktop and it should ask you to add the path in which you want to save the folder with the project. Then click on clone.

## (Optional) Running Android app via adb debugging (wifi)

- make sure both the Android device and your computer are connected to the same WiFi
- on your Android device go under *"System" > "Developer options" > "Debug wireless"* and click on *"Pair device with pairing code"*
- run the project inside the container and run

```sh
adb pair [ip]:[port]
```

*ip* and *port* are given by the device when clicking on *"Pair device with pairing code"*

- enter the pairing code
- on your android device close the pairing screen and look at the *"IP address and port"*

```sh
adb connect [ip]:[port]
adb devices
flutter run -d 192.168.0.102:40945
```

to run in debug mode add the following config inside .vscode/launch.json (if this file does not exist, create it)

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Flutter on Device",
      "type": "dart",
      "request": "launch",
      "flutterMode": "debug",
      "deviceId": "192.168.0.102:40945"
    }
  ]
}
```

Once this config is set, you can use it by clicking on the "Run and Debug" icon in the left sidebar menu.