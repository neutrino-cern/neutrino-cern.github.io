# GPUs

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
You can view nodes with GPUs by specifying a constraint to `condor_status`, for example, to view all nodes with more than 2 GPUs:

```
condor_status -constraint 'GPUs > 2'
```

We can also filter by GPU type, however, due to the current migration process, this command is different for A100 GPUs and the rest:

- On A100
```
 condor_status -constraint 'regexp("A100", CUDADeviceName)'
```

- On everything else
```
 condor_status -constraint 'regexp("V100", GPUs_DeviceName)'
```

To increase your priority in the queue you can subscribe to the [`np-comp` group.](https://resources.web.cern.ch/resources/Manage/Linux/Subscribe.aspx)

To require a GPU when submitting a job to the HTCondor LXBATCH cluster, we can specify in our `.sub` the following requirement:
```
request_GPUs = 1
```


!!! info 
    Currently only machines with A100 GPUs will be assigned to your job by default. This is due to an ongoing upgrade of the nodes to AlmaLinux9, thus to run a job using V100 or T4 you must specify:

    ```
    requirements = TARGET.OpSysAndVer =?= "AlmaLinux9"
    ```
    If the job can run on both versions then:
    ```
    requirements = ( TARGET.OpSysAndVer =?= "AlmaLinux9" || TARGET.OpSysAndVer =?= "CentOS7")
    ```


