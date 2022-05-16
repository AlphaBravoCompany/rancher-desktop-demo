# Lab 03 - Interacting with Internal K8s Services

This lab will show you how to expose internal Kubernetes services to you local machine so you can interact with them.

## Agenda:

- Deploy the Bitnami Wordpress Helm Chart and view the default WP site in a browser
- Expose the MariaDB database via `Port Forwarding`
- Modify the Database using `Beekeeper Studio` (or PHPMyAdmin in a container)
- Refresh WP in the browser to verify the changes were made

## Setup

For this exercise we need to install [Beekeeper Studio](https://www.beekeeperstudio.io/) or another database management tool locally. If you cant, see the step for deploying PHPMyAdmin in a container and port forwarding to the interface locally.

## 