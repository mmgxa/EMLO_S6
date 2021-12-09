# EMLO Session 6

The objective of this class is to start/install and run Kubeflow pipeline and train a Pytorch Resnet18 model on the CIFAR dataset.

# Requirements
- [x] 3-4 different runs
- [x] change the model to resnet18
- [x] train for 3-4 epochs (3 done)
- [x] tensorboard loss curve
- [x] confusion matix


# Preparing Piepline

To run the pipeline, we need to generate it first. This was done from the samples provided. However, a few changes were made; these changes are mentioned in the next section


![C1](./img/c1.png)

Running the first `python3` command generates a folder called `yaml`. Executing the last step generates a file `pytorch_cifar10.yaml` that is the pipeline.


# Changes Made

## Model

In the files `classifier.py` and `cifar10_train.py`, the model (specified using `self.model_conv`) was changes from resnet50 to resnet18.

## Typo

After generating the YAML files, there was a few typos that had to be fixed. In the files `ax_train_component.yaml`, `train_component.yaml`, and `preprocess_component.yaml`, the key `command` had an incorrect value (`"command to execute"`), and had to be changed to the example specified in the comment.

## Epochs

In `pipeline.py`, we changed `max_epochs=3` in the `ptl_args` string.



changes made resnet 
and [command to execute']

# Installation

As instructed on the [Local Deployment](https://www.kubeflow.org/docs/components/pipelines/installation/localcluster-deployment/) page, K3s was installed. 

`Kind` and `minikube` gave errors (twice) while creating the pipeline - K3s only gave a single warning regarding the versioning. K3ai actually ran k3s in the background.



![C1](./img/c2.png)

At this step, we wait till all pods have either the Running/Completed state. This takes a long time since it downloads images.


![C1](./img/c3.png)

# Running Pipeline

The last step above can be used to start the Pipeline.

### Create Experiment

![](./img/1_create_exp.png)

### Upload Pipeline

![](./img/2_upload_pl.png)

### Create Run

![](./img/3_create_run.png)

### Start Run
![](./img/4_start_run.png)

### Running Visualization Part
![](./img/5_vis_pod_in.png)

### After Visualization Part Completes

![](./img/6_vis_comp.png)

### Running Preprocess/Transform Part

![](./img/7_prep_pod_in.png)

### After Preprocess/Transform Part Completes

![](./img/8_prep_comp.png)

### Running Training Part

![](./img/9_train_run.png)


### Training - Epoch 1 Starts
![](./img/10_train_e1.png)

### Training - Epoch 1 Ends

![](./img/11_train_e1_end.png)

### Training - Epoch 2 Ends

![](./img/12_train_e2_end.png)

### Training - Epoch 3 Ends

![](./img/13_train_e3_end.png)

### Training Ends - Profiler

![](./img/14_train_prof_log.png)

### Training Ends - Graph

![](./img/15_train_comp.png)

### Training Ends - Success Message

![](./img/16_train_suc.png)

### Pipeline Ends - Graph

![](./img/17_complete.png)
# Tensorboard Curves

![C1](./img/tensorboard.png)


# Confusion Matrix

![C1](./img/conf_mat.png)

# Profiler

![C1](./img/profiler.png)

# Multiple Runs

Subsequent Runs were much faster since docker images and other data need not be downloaded. This can be seen in the `duration` column below.

![C1](./img/runs.png)


