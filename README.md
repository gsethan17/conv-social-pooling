# Convolutional Social Pooling
Code for model proposed in [1].  
This repository is forked from [2].  


# Build Environment
* Linux
* Docker
* Implemented in Pytorch 0.4.0

1. Download the docker image for pytorch
  ```sudo docker pull pytorch/pytorch```
  
2. Run the docker for pytorch
  ```sudo docker run -it pytorch/pytorch```
  if you can see the ```/workspace#```, docker is run successfully.
  
3. Install the NVIDIA Container Toolkit to run GPU accelerated Docker containers.  
   (Note that you do not need to install the CUDA Toolkit on the host system, but the NVIDIA driver needs to be installed)  
   Please refer to [3] for the detail.
   
4. Run the nvidia-docker for pytorch with GPU accelrated.   
```sudo nvidia-docker run -it pytorch/pytorch```  
or
```sudo docker run -it --gpus all pytorch/pytorch```
if you run the docker with GPU accelrated, you can use NVIDIA-SMI on ```nvidia-smi``` commend.

5. Make sharing folder for docker  
make the folder for sharing named 'wspare' on the root directory.  
```sudo mkdir wspace```  
run the docker image with sharing folder as below command.  
```sudo nvidia-docker run -it -v /home/gsethan/wspace:/root/wspace/ pytorch/pytorch```  
or  
```sudo docker run -it -v /home/gsethan/wspace:/root/wspace/ --gpus all pytorch/pytorch```  
you can find sharing folder after below command.  
  ```
  cd ..
  cd root
  ls
  ```  

6. Install the Git in the docker images   
```apt-get update```  
```apt-get install git```  
to set the config of git,
```git config --global user.name "[user name]"```  
```git config --global user.email [email address]```  

# Execution  
1. Make the docker environment as a specific name  
```sudo docker run -it -v [own root directory]/wspace:/root/wspace/ --gpus all --name [Specific name] pytorch/pytorch```  
```(sudo docker run -it -v /home/gsethan/wspace:/root/wspace/ --gpus all --name AICM pytorch/pytorch)```  
when you restart to the docker,
```
sudo docker start [Specific name]
(sudo docker start AICM)
sudo docker attach [Specific name]
(sudo docker attach AICM)
```

2. Git clone on the `wspace` directory.
```git clone https://github.com/gsethan17/conv-social-pooling.git```  
to move to cloned folder.
```cd conv-social-pooling```  
to make the local branch as remoted execution branch  
```git checkout -t origin/ExecutionTest```


# Reference
[1] Nachiket Deo and Mohan M. Trivedi,"Convolutional Social Pooling for Vehicle Trajectory Prediction." CVPRW, 2018  
[2] [nachiket92/conv-social-pooling](https://github.com/nachiket92/conv-social-pooling)  
[3] [NVIDIA Container Toolkit](https://github.com/NVIDIA/nvidia-docker)
