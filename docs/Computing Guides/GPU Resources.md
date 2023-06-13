# GPUs at CERN

## LXPLUS 

The easiest way to access a GPU is by using the LXPLUS service:

```
ssh yourusername@lxplus-gpu.cern.ch
```
The GPUs are usually an NVIDIA T4. 


## SWAN

You can also access GPUs on the [SWAN Service](https://swan-k8s.cern.ch/hub/spawn). You will have to create a ticket to be granted access, you will be pointed to the link for this when you try to create a session. 

Using SWAN you have access to GPUs, using CERN's modified version of [jupyter notebooks](https://jupyter.org/) - you can run code interactively, thus it is very good for prototyping. 

A detailed view of the software available on SWAN is listed on the [LCG Release](https://lcginfo.cern.ch/) website.

## Kubeflow
The [CERN Kubeflow service](https://ml.docs.cern.ch/) is focused on deep learning workflows. It contains notebooks, tools for ML pipelines and hyper-parameter optimization.


## LXBATCH

!!! warning
    There should be a page describing how to submit basic jobs to the cluster. 


To require a GPU when submitting a job to the HTCondor LXBATCH cluster, we can specify in our `.sub` the following requirement:
```
request_GPUs = 1
```
