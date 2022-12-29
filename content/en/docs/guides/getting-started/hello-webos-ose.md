---
title: "Hello, webOS OSE!"
date: 2022-12-27
weight: 10
toc: true
---

Welcome to the webOS Open Source Edition (OSE)! This page will guide you through the process of setting up the environment and developing your first app.

## Environment Setup

First, let's set up your environment.

webOS OSE provides you with two options for the target environment.

* **Real device**: For those of you who want to test on a real device, webOS OSE supports **Raspberry Pi (RPi)**.

    | Version | Support Device |
    |---------|----------------|
    | For webOS OSE 2.0.0 or Higher | Raspberry Pi 4 Model B |
    | For webOS OSE 1.x | Raspberry Pi 3 Model B |

* **Emulator**: For developers who don't have RPi on hand or prefer to work on a virtual environment, webOS OSE provides the **emulator** as a part of its SDK.

You need to create an image for the desired target and prepare the target environment.

### Real Device

* Before you begin, check the [system requirements]({{< relref "system-requirements" >}}).
* [Build the source code]({{< relref "building-webos-ose" >}}) to create an image for RPi. Ensure that you set up the build for RPi at the [configuration step]({{< relref "building-webos-ose#configuring-the-build" >}}).
* [Flash the built image]({{< relref "flashing-webos-ose" >}}) to RPi.
* [Set up networking]({{< relref "setting-up-network" >}}) between the host machine and RPi.
* If you use webOS OSE 2.0 or higher and RPi 4 for a target device, consider setting up [dual displays]({{< relref "setting-up-dual-displays" >}}).

### Emulator

* Before you begin, check the system requirements for the [build system]({{< relref "system-requirements#build-system-requirements" >}}), [host machine]({{< relref "system-requirements#host-machine-requirements" >}}), and the [emulator host]({{< relref "emulator-user-guide#system-requirements" >}}).
* [Build the source code]({{< relref "building-webos-ose" >}}) to create an image for the emulator. Make sure that you set up the build for the emulator at the [configuration step]({{< relref "building-webos-ose#configuring-the-build" >}}).
* Set up the emulator by following the steps in [emulator user guide]({{< relref "emulator-user-guide" >}}).

## Your First webOS OSE App

If you finished setting up the environment, it's time to start developing your first app running on webOS OSE, which will be an external web app.

### Install CLI

To develop an external web app, you will use Command-Line Interface (CLI), which is provided as a part of webOS OSE SDK. You can also use CLI to develop external JavaScript (JS) services.

Proceed to [install CLI]({{< relref "cli-user-guide#installing-cli" >}}) for your operating system.

### Develop the External Web App

Follow the steps described in the [Developing External Web Apps]({{< relref "developing-external-web-apps" >}}) tutorial.

## What's Next

* If you are interested in developing an external JS service, which will be packaged along with the web app you've just created, check the [Developing External JS Services]({{< relref "developing-external-js-services" >}}) tutorial.