---
layout: default
title: Troubleshooting VirtualBox Guest Additions on Kali Linux
#nav_title: "Test Page"  # Custom title for navigation (optional, overrides 'title')
#nav_order: 4           # Order in the sidebar (e.g., 4th position)
#parent: "Test"    # Links this page under a parent item in navigation
---

# Troubleshooting VirtualBox Guest Additions on Kali Linux

If you're having trouble with VirtualBox Guest Additions on a Kali Linux virtual machine, there are several steps you can take to troubleshoot and resolve the issue. Here’s a detailed guide to help you get it working:

## Step 1: Update your system

First, ensure that your Kali Linux system is up to date.

    sudo apt update -y
    sudo apt upgrade -y

## Step 2: Install required packages

Make sure you have the necessary packages installed.

    sudo apt install -y build-essential dkms linux-headers-$(uname -r)

## Step 3: Install VirtualBox Guest Additions

1. **Insert the Guest Additions CD image:**
   - Start your Kali Linux VM.
   - In the VirtualBox menu, go to Devices > Insert Guest Additions CD image....

2. **Mount the CD image:**
   - Open a terminal in your Kali Linux VM.
   - Create a mount point and mount the CD image.

    ```bash
    sudo mkdir /mnt/cdrom
    sudo mount /dev/cdrom /mnt/cdrom
    ```

3. **Run the installer:**
   - Navigate to the mounted directory and run the installer.

    ```bash
    cd /mnt/cdrom
    sudo sh VBoxLinuxAdditions.run
    ```

4. **Reboot the VM:**
   - After the installation completes, reboot your VM.

    ```bash
    sudo reboot
    ```

## Step 4: Verify installation

After rebooting, verify that the Guest Additions are working correctly.

1. **Check the version:**
   - Open a terminal and check the version of the Guest Additions.

    ```bash
    VBoxControl --version
    ```

2. **Check shared clipboard and drag-and-drop:**
   - Test the shared clipboard and drag-and-drop features to ensure they are working.
