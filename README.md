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



# Reference
[1] Nachiket Deo and Mohan M. Trivedi,"Convolutional Social Pooling for Vehicle Trajectory Prediction." CVPRW, 2018  
[2] [nachiket92/conv-social-pooling](https://github.com/nachiket92/conv-social-pooling)  
[3] [NVIDIA Container Toolkit](https://github.com/NVIDIA/nvidia-docker)
