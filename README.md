[![CircleCI](https://dl.circleci.com/status-badge/img/gh/osarenogae/predicube/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/osarenogae/predicube/tree/main)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl

# Summary of the Project
The project aimed at containerizing and deploying a Machine Learning application using Kubernetes. The application, which is a Python Flask app, serves out predictions about prices of houses through a microservice API. First of all, I setup my virtual environment, installing Hadolint, Minikube and Kubectl. After writing my Dockerfile, I used Hadolint to test for any issues. Given no issue, I proceeded to containerize the Machine Learning application using my Dockerfile. Once done,
I deployed the containerized application using Docker. I made some improvements in the logging of the python application and then configured Kubernetes to create a cluster for the containerized app. Afterwards, I deployed the containerized app in the Kubernetes cluster and integrated CircleCI to indicate the state of my workflow - Passed or Failed.

# Running the Scripts and Web App
### Set Up Virtual Environment:
     - make setup
     - source ~/.devops/bin/activate
     - make install
     - curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
     - sudo install minikube-linux-amd64 /usr/local/bin/minikube
     - curl curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-    release/release/stable.txt)/bin/linux/amd64/kubectl 
     - sudo chmod +x ./kubectl
     - sudo mv ./kubectl /usr/local/bin/kubectl
 ### Test Using Hadolint
     - make lint
     
 ### Deploy App in Docker and Make Prediction
     - bash run_docker.sh
     - bash make_prediction.sh
     
 ### Upload Docker Image to Kubernetes Cluster
      - bash upload_docker.sh
  
 ### Deploy on Kubernetes Cluster
      - bash run_kubernetes.sh
    
    

# Short description of Files
### run_docker.sh
- Builds a docker image and runs the flask app from that image.
### upload_docker.sh
- Uploads the Docker image to DockerHub to make it accessible to a Kubernetes cluster
### run_kubernetes.sh
- deploys application on the Kubernetes cluster.
### make_prediction.sh
- causes the Flask app to generate and output a prediction (inference).
### app.py 
- Flask app responsible for retrieving a prediction
### docker_out.txt
- contains terminal output when the app is run using Docker.
### kubernetes_out.txt 
- contains information such as the pod the container is running on, the status of the application, the port forwarding, and the handling text.
### requirements.txt
- contains a list of packages and their versions to be installed by pip.
### Makefile 
- defines a set of tasks to be executed and commands to execute them.
### Dockerfile 
- contains all the commands int he order they should run in order to assemble a Docker image.
### config.yml 
- provides the configuration settings for circleci in the order they must be followed when installing or setting up a project
### resize.sh 
- resize the EBS volume of a Cloud9 EC2 instance







