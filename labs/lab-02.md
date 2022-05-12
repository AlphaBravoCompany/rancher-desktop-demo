# Lab 02 - Running and Modifying a Workload

This lab will show you how to work with source code, container and Kubernetes on your local machine.

## Agenda:

- Build an initial container image of 0.1.0
- Deploy a sample app using Helm using the 0.1.0 image
- Update the app on the local machine in a Docker container and build the modified program as 0.2.0
- Update the Helm deployment to use the new 0.2.0 image

**IMPORTANT**: Make sure your system is using `dockerd (moby)` as the container runtime for this lab.

**NOTE**: These labs download a number of containers to the local system. If you are limited on disk space or have a slow internet connection, you will likely have a bad time.

## Setup

1. Create a new temporary folder for these labs.
2. In that folder we are going to clone 2 repositories. Run the following commands (or download the zip from Github and unpack).

- `git clone https://github.com/abenginerd/dc-hello-world.git`
- `git clone https://github.com/abenginerd/dc-hello-world-chart.git`


## Build the initial image

1. Change in the `dc-hello-world` directory and build the initial image using the following command:

- `docker build -t dc-hello-world:0.1.0 .`

2. Once complete, confirm the image exists by running `docker image ls`

## Run the Helm chart with version 0.1.0

1. Change into the `dc-hello-world-chart` directory and run the following command to deploy the Helm chart.

- `helm install hello-world .`

2. To see that the deployment is running, open the Dashboard and navigate to `Workload` -> `Pods`. Or you can run `kubectl get pods`.

3. To view the page, open `Port Forwarding` and port forward the `hello-world-dc-hello-world-chart` service.  Note the local port the interface provides. Open your browser and visit localhost:port to see the page display `Hello Rancher Desktop`.

But, this is supposed to be a `Hello World` app...

## Modify the code and build a new image

1. Install the `Remote - Containers` extension from Microsoft. The `dc-hello-world` project includes a `.devcontainer` directory that allows you to do all development inside a container without needing to install addl tools on your local machine.

2. Open the `dc-hello-world` directory in VScode. When prompted with `Folder contains a Dev Container configuration file. Reopen folder to develop in a container (learn more).`, chose `Reopen in container`.

3. Review the `Dockerfile` file and note that this is a multi-stage build. This allows use to only include the final binary in the image and not the GoLang build tools. More about this later.

4. Open the `main.go` file and find the line that begins with `const out`. Change `Hello Rancher Desktop` to `Hello World` and save the file.

5. We can test that this worked before we build a new container. Run `go run main.go --debug` and open your browser to `localhost:3000` to make sure the changes are reflected.

6. Close VScode if everything looks good and in a terminal window, open the `dc-hello-world` directory.

7. Run `docker build -t dc-hello-world:0.2.0 .` to build a new version of the container with your changes in it.

8. Once complete, confirm the new image exists by running `docker image ls`. Note that the `dc-hello-world:0.2.0` is only 6MB but the <none> container which is the GoLang container from the first stage of the `Dockerfile` is over 1GB! Multi-stage builds for the win.

## Updating the Helm deployment

1. Change into the `dc-hello-world-chart` directory and run the following command to deploy the Helm chart.

- `helm upgrade hello-world . --set image.tag=0.2.0`

2. To see that the deployment is running, open the Dashboard and navigate to `Workload` -> `Pods`. Or you can run `kubectl get pods`.

3. If your previous port forward is still in place, refresh the `localhost:port` page you were on and you should see the new `Hello World` message.

## Cleanup

1. From the terminal, run `helm delete hello-world -n default`

2. From the terminal, run `docker image prune` to cleanup unneeded images.

2. Remove the temporary directory with the cloned repositories.


## That's all for Lab 02!