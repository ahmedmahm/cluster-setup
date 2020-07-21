# Kubernetes setup
<p align="center"><img src="https://magazine.odroid.com/wp-content/uploads/Kubernetes-logo.png" width="400"></p>

# Table of content
* [Start](#Start)
* [Requirements](#requirements)
* [Install cluster](#install-cluster)
* [Tools](#tools)

## Start

  Introduction of what is this entire setup:
  
  Each microservice is built and deployed as a Docker container.
  
  Managing Docker containers can be painful without an orchestrator and that's where Kubernetes comes in. Take a look at [this](https://cloud.google.com/kubernetes-engine/kubernetes-comic/) very cool comic story about Docker containers and the need for Kubernetes orchestration.
  
  Since I'm a DevOps/Backend Kubernetes is my main infrastructure for our Staging and Live environments it's crucial to also use Kubernetes for development to simulate and test the connection between the microservices you are currently working on (locally or remotelly). That's why minikube comes in handy.
  
  Minikube is a single node Kubernetes cluster running in your Mac Book and that's what you are about to install in your local environment.
  
  While using Minikube you will have to maintain it with some commands in  `cluster-setup/bin`.
  
  Development can be smooth with the following commands.

   * So after installing the Requirements you will be able to start your development environment and a basic flow could be the following:
     *  Install your cluster with `bin/bootstrap-on-macos`.
     
     *  Happy helming!
  
  In the sequence you will find more details about the previous basic flow and more tools to help you with your development environment so make sure to read it!

## Requirements
* Docker (https://download.docker.com/mac/stable/Docker.dmg)
* Xcode
* Brew (`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`)

## Install Cluster
If already installed before, you can clean up the old minikube, kubectl and helm installations
by running the following command:
```bash
$ rm -rf ~/.minikube/ ~/.kube/ ~/.helm/
$ bin/bootstrap-on-macos
```
* start docker
* run `bin/bootstrap-on-macos`
  * this will require you root password to install new components (please **don't** run with sudo)
  * this will take some time
  * to validate if it's working please run `minikube dashboard &` as soon as this opens a browser window you can continue
  * can be run with the `--nodeps` parameter skip the reinstallation of dependencies (for setups after it was already run)
  
* to install/update more use `bin/install images/<componentname>`
 * under construction
 
 
* to delete use `bin/delete images/<componentname>`
  * can be run with the `--kill` parameter to also delete the image from the repo inside of minikube
  
* when done please check `minikube dashboard &` -> `Overview`
  * wait until it says 100%

* At this point all database will fail still because database is not configured.

## Tools
* stop the cluster: `bin/stop-cluster`
* start the cluster: `bin/start-cluster`
* delete the cluster: `bin/delete-cluster`
