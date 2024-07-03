---
title: Upgrade Ubuntu from 22.04 LTS to 24.04 LTS
date: 2024-07-03 12:00:00 +0800
categories: [Linux]
tags: [linux, ubuntu, bash, apt, proxmox]     # TAG names should always be lowercase
---
# Upgrade Ubuntu from 22.04 LTS to 24.04 LTS

Today, I want to use Ubuntu 24.04 for some testing. Instead of installing a new OS, I thought, why not upgrade the current Ubuntu 22.04 VM in Proxmox to 24.04? This simple guide will walk through the steps to upgrade from Ubuntu 22.04 LTS to 24.04 LTS.

## Step 1: Update System

First, ensure current system is up-to-date. Open a terminal and run:

```bash
sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y
```

## Step 2: Install the Upgrade Tool

Install the `ubuntu-release-upgrader-core` package, which provides the necessary tools for upgrading:

```bash
sudo apt install ubuntu-release-upgrader-core
```

## Step 3: Start the Upgrade Process

With the system updated and the upgrade tool installed, we can now begin the upgrade process. Run the following command to start upgrading:

```bash
sudo do-release-upgrade
```

Follow the on-screen prompts to complete the upgrade. The system will automatically handle the rest, including downloading the necessary packages and upgrading system to Ubuntu 24.04 LTS.

## Final Steps

Once the upgrade is complete, it's a good idea to restart your system to ensure all changes take effect:

```bash
sudo reboot
```
