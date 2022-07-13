[![JPaul23](https://circleci.com/gh/JPaul23/project-ml-microservice-kubernetes.svg?style=shield)](https://app.circleci.com/pipelines/github/JPaul23/project-ml-microservice-kubernetes/1/workflows/4d6e2149-ee7a-4d85-9d10-f815fa8654c0)

## Project Overview

I was given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. The data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). In this project I put my ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

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

### Files explanation
1. `config.yml` : CircleCI configuration file for running the tests
2. `app.py` : Python flask app that serves out predictions (inference) about housing prices through API calls
3. `Dockerfile`: Dockerfile for building the image
4. `make_prediction.sh` : Send a request to the Python flask app to get a prediction, for localhost
5. `make_prediction_2.sh` : Send a request to the Python flask app to get a prediction, for minikube kubernetes
6. `Makefile` : includes instructions on environment setup and lint tests
7. `run_docker.sh` : Script to get Docker running locally.
8. `run_kubernetes.sh` : Script to run the app in kubernetes cluster.
9. `upload_docker.sh` : Script to upload the image to docker hub.

## Run the project
You should have a minikube installed. To start a local cluster, type the terminal command:

`minikube start`

To deploy this application in kubernetes run:

`./run_kubernetes.sh`

After you’ve called run_kubernetes.sh, and a pod is up and running, make a prediction using a separate terminal tab and run:

`./make_prediction2.sh`
Delete the cluster:

`minikube delete`
