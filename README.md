# Rancher Desktop Demo / Workshop

**Rancher Desktop** is an open-source desktop application for Mac, Windows and Linux. Rancher Desktop runs Kubernetes and container management on your desktop. You can choose the version of Kubernetes you want to run. You can build, push, pull, and run container images using either containerd or Moby (dockerd). The container images you build can be run by Kubernetes immediately without the need for a registry.

- Website: https://rancherdesktop.io/
- Docs: https://docs.rancherdesktop.io/
- Github: https://github.com/rancher-sandbox/rancher-desktop/

![Rancher Desktop Settings](https://rancherdesktop.io/images/kubernetes-settings.png)

## AlphaBravo Rancher Desktop Demo Slides

Please find the Slides in the following link. They may be updated as the product matures. 

Rancher Desktop Slides: https://docs.google.com/presentation/d/1kdM3yKWAioWd0zMSrYcxJFp3iTrDQX4rx3-WI_2HyN4/edit?usp=sharing

## Rancher Desktop Labs **BETA**

If you would like to follow some hands on labs to get started working with Rancher Desktop, open the `labs` folder in this repo and follow along.

Labs are currently in Beta and being tested for functionality and accuracy. Your mileage may vary.

## Installing Rancher Desktop

Rancher desktop supports MacOS, Windows and Linux systems. To get started installing, visit here: https://docs.rancherdesktop.io/getting-started/installation/

## Nerdctl and Docker commands.

In addition to being able to choose the version of Kubernetes you deploy, you also have the option of deploying `containerd` or `docker(moby)` as the container runtime.

If you choose `containerd`, then `nerdctl` will be you new way of pushing, pulling and building images files as well as working with docker-compose files.

Since many of the commands for `nerdctl` are identical to the `docker` commands you might be used to running, you may be able to alias `nerctl` to `docker`.

More information on using `nerdctl` can be found at the following links:

- Working with Images: https://docs.rancherdesktop.io/tutorials/working-with-images
- Working with Containers: https://docs.rancherdesktop.io/tutorials/working-with-containers

## About Alphabravo

**AlphaBravo** provides products, services, and training for Cybersecurity, Kubernetes, Cloud, and DevSecOps. AlphaBravo is a Rancher training and services partner.

Contact **AB** today to learn how we can help you.

* **Web:** https://alphabravo.io
* **Email:** info@alphabravo.io
* **Phone:** 301-337-8141