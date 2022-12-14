---
title:  Google Cloud Platform Virtual Machine Basics
categories: [Cloud Computing]
tags: [cloud computing, virtual machines]
img_path: /assets/images/gcp_vm_basics/
---

**This is a short tutorial explaining some basic Google Cloud Platform virtual machine stuff.  Basic setup, creating and editing a machine, creating a role, creating a schedule, SSHing into the machine, setting up a desktop environment, and connecting to the machine by remote desktop.**

---

## 1. Set up your Google account

- Create a <a href="https://google.com/" target="_blank">Google</a> account for yourself or your business if you don't already have one:

<img src="google_01.png" height="300">

- Add a payment method to the account so that you can use the Google Cloud Platform free tier:

<img src="google_02.png" height="300">


## 2. Set up your project

- Sign in to Google Cloud Console:
<a href="https://console.cloud.google.com" target="_blank">https://console.cloud.google.com</a>

- Create a new project:

<img src="google_03.png" height="300">

<img src="google_04.png" height="300">

- Select the project:

<img src="google_05.png" height="300">

- Go to Compute Engine:

<img src="google_06.png" height="300">

or

<img src="google_07.png" height="300">

- Enable the Compute Engine API:

<img src="google_08.png" height="300">


## 3. Create a Debian 11 Virtual Machine

- Create a new VM instance:

<img src="google_09.png" height="300">

- Configure it:

<img src="google_10.png" height="300">

<img src="google_11.png" height="300">


## 4. Edit the machine

- Stop the machine:

<img src="google_12.png" height="300">

- Edit the machine:

<img src="google_13.png" height="300">

- Change the RAM, disk size, etc.:

<img src="google_14.png" height="300">


## 5. Create a Role

- Navigate to the IAM page:

<img src="google_15.png" height="300">

- Go to Roles:

<img src="google_17.png" height="300">

- Create a Role:

<img src="google_18.png" height="300">

- Name it `stop/start instance`:

<img src="google_19.png" height="300">

- Set the Role launch stage to `General Availability`:

<img src="google_20.png" height="300">

- Add the permissions:

<img src="google_21.png" height="300">

<img src="google_22.png" height="300">

- The permissions we're adding are `compute.instances.start`:

<img src="google_23.png" height="300">

- And `compute.instances.stop`:

<img src="google_24.png" height="300">


## 6. Assign the Service Agent the role we just created

- Navigate to the IAM page:

<img src="google_15.png" height="300">

- Select "Include Google-provided role grants":

<img src="google_16.png" height="300">

- Edit the Service Agent with `@compute-system.iam.gserviceaccount.com`:

<img src="google_25.png" height="300">

- Add another Role:

<img src="google_26.png" height="300">

- Add the custom role `stop/start instance` we created earlier:

<img src="google_27.png" height="300">

We just gave our Service Agent the ability to stop and start our VM instance.


## 7. Create a schedule

- Go to Compute Engine and select Instance Schedules:

<img src="google_28.png" height="300">

- Create an Instance Schedule:

<img src="google_29.png" height="300">

- Configure the Instance Schedule:

<img src="google_30.png" height="300">

<img src="google_31.png" height="300">

- Add our VM instance to the schedule:

<img src="google_32.png" height="300">

<img src="google_33.png" height="300">

<img src="google_34.png" height="300">

We have now added a stop and start time to our VM instance.


## 8. SSH into the machine

- Start the machine:

<img src="google_35.png" height="300">

- SSH into the machine:

<img src="google_36.png" height="300">


## 9. Set up the machine

Set the password:
```terminal
sudo passwd
```

Set the timezone and update:
```terminal
sudo timedatectl set-timezone America/Toronto
sudo apt-get update -y && sudo apt-get -y upgrade
```

Install any packages you'll need:
```terminal
sudo apt-get install -y git python3-venv gnome-terminal
```

## 10. Install Chrome Remote Desktop, Xfce desktop environment, and Chrome browser

```terminal
sudo apt install --assume-yes wget tasksel

[[ $(/usr/bin/lsb_release --codename --short) == "stretch" ]] && \
	   sudo apt install --assume-yes libgbm1/stretch-backports

wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb
sudo apt-get install --assume-yes ./chrome-remote-desktop_current_amd64.deb

sudo DEBIAN_FRONTEND=noninteractive \
	    apt install --assume-yes xfce4 desktop-base dbus-x11 xscreensaver

sudo bash -c 'echo "exec /etc/X11/Xsession /usr/bin/xfce4-session" > /etc/chrome-remote-desktop-session'

sudo systemctl disable lightdm.service

wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install --assume-yes ./google-chrome-stable_current_amd64.deb
```

## 11. Set up Chrome Remote Desktop

- Go to Chrome Remote Desktop:
<a href="https://remotedesktop.google.com/" target="_blank">https://remotedesktop.google.com/</a>

- Click <kbd>Set up via SSH</kbd>, and <kbd>Begin</kbd>:

<img src="google_37.png" height="300">

- Click <kbd>Next</kbd> and <kbd>Authorize</kbd>:

- Copy the Debian Linux command:

<img src="google_38.png" height="300">

- Paste it into SSH console and create a 6 digit PIN

- Click <kbd>Remote Access</kbd>:

<img src="google_39.png" height="300">


## 12. Start the remote desktop connection

<img src="google_40.png" height="300">

- Disable the screensaver:

<img src="google_41.png" height="300">

<img src="google_42.png" height="300">

- Change the terminal color theme:

<img src="google_43.png" height="300">

<img src="google_44.png" height="300">

You now have a virtual machine running in the cloud that you can use through the browser.
