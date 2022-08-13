
[![CircleCI](https://dl.circleci.com/status-badge/img/gh/jic4real/operationalize-machine-learning/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/jic4real/operationalize-machine-learning/tree/main)

## Project Overview

This project is a Python flask app that serves out predictions (inference) about housing prices through API calls.

The Operationalize Machine Learning project contains a Machine Learning Microservice, built on `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing)


### Requirements and Dependencies

* Python 
https://www.python.org/downloads/

* Docker Desktop
Install Docker here: https://docs.docker.com/install/ based on your operating system.

* Kubernetes
You would need to install any one tool for creating a Kubernetes cluster - KubeOne / Minikube / kubectl on top of Docker Desktop:
 1. https://kubernetes.io/docs/tasks/tools/install-kubectl/ directly on top of Docker desktop - For Windows/macOS
 2. https://kubernetes.io/docs/tasks/tools/install-minikube/ - For Linux/macOS
 
* Hadolint
Install hadolint following the instructions, https://github.com/hadolint/hadolint

## Short description of folders and files in the repo
* .circleci: For the CircleCI build server
* model_data : this folder contains the pretrained sklearn model and housing csv files
* output_txt_files: folder contains sample output logs from running ./run_docker.sh and ./run_kubernetes.sh
* app.py : contains the flask app
* Dockerfile: contains instructions to containerize the application
* Makefile : contains instructions for environment setup and lint tests
* requirements.txt: list of required dependencies
* run_docker.sh: bash script to build Docker image and run the application in a Docker container
* upload_docker.sh: bash script to upload the built Docker image to Dockerhub
* run_kubernetes.sh: bash script to run the application in a Kubernetes cluster
* make_prediction.sh: bash script to make predictions against the Docker container and k8s cluster
* README.md: this README file

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
