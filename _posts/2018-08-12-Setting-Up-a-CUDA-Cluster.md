---
layout: post
title:  "Setting Up a CUDA Cluster."
subtitle: Here you'll learn how to build your own cluster that uses CUDA library to execute programs in parallel mode.
date:   2018-08-12 00:15:12 -0500
categories: Cluster-Computing
---
# Cluster

Using our cluster created [GPUJcluster][GPUJcluster_link].  
We need to install CUDA (Compute Unified Device Architecture).

# CUDA

Is a platform of parallel computing that includes a compiler and a set of toolkits created by nVidia.  
CUDA allows to developers use a variation of C language to code in GPU nVidia.

# How to install CUDA

We will install CUDA 9.0 version.

* First of all, we check our GPU description:

      lspci | grep ' VGA ' | cut -d" " -f 1 | xargs -i lspci -v -s {}

   The output should show the GPU name and the driver
   ![gpu-features](/assets/clusterComputing/GPU/gpu-features.png)

* Next, Update your GPU driver:

      sudo add-apt-repository ppa:graphics-drivers/ppa
      sudo apt update
      sudo apt install nvidia-390

* Then, Reboot your computer. To verify the installation, open a terminal and run the following command:

      nvidia-smi

  You should see this kind of information:
  ![nvidia-smi](/assets/clusterComputing/GPU/nvidia-smi.png)

* Once installed nvidia-drivers, we need to install cuda library, first download file installer:

      wget https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda-repo-ubuntu1704-9-0-local_9.0.176-1_amd64-deb
      sudo dpkg -i cuda-repo-ubuntu1704-9-0-local_9.0.176-1_amd64.deb
      sudo apt-key add /var/cuda-repo-9-0-local/7fa2af80.pub
      sudo apt-get update
      sudo apt-get install cuda

* Finally, modify `.bashrc` file, write these lines:

      export PATH=/usr/local/cuda-9.0/bin${PATH:+:$PATH}}
      export LD_LIBRARY_PATH=/usr/local/cuda-9.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

## Error with compiler gcc/g++ compatibility

* First, identify with error do you have (compiler version), then install it (in this case is gcc-6):

      sudo apt install gcc-6 g++-6

* And link the gcc cuda compiler with gcc-version (in this case 6):

      sudo ln -s /usr/bin/gcc-6 /usr/local/cuda/bin/gcc 
      sudo ln -s /usr/bin/g++-6 /usr/local/cuda/bin/g++

* Try `helloWorld.cu`:

   ``` c++
   #include <stdio.h>
       
   const int N = 16; 
   const int blocksize = 16; 
         
   __global__ 
   void hello(char *a, int *b) {
     a[threadIdx.x] += b[threadIdx.x];
   }
         
   int main(){
     char a[N] = "Hello \0\0\0\0\0\0";
     int b[N] = {15, 10, 6, 0, -11, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0};
     char *ad;
     int *bd;
     const int csize = N*sizeof(char);
     const int isize = N*sizeof(int);
       
     printf("%s", a);
       
     cudaMalloc( (void**)&ad, csize ); 
     cudaMalloc( (void**)&bd, isize ); 
     cudaMemcpy( ad, a, csize, cudaMemcpyHostToDevice ); 
     cudaMemcpy( bd, b, isize, cudaMemcpyHostToDevice ); 
       
     dim3 dimBlock( blocksize, 1 );
     dim3 dimGrid( 1, 1 );
     hello<<<dimGrid, dimBlock>>>(ad, bd);
     cudaMemcpy( a, ad, csize, cudaMemcpyDeviceToHost ); 
     cudaFree( ad );
     cudaFree( bd );
       
     printf("%s\n", a);
     return EXIT_SUCCESS;
   }
  ```
 
* Compile and execute with:
 
      nvcc hellWorld.cu -o helloWorld
      ./helloWorld

[GPUJcluster_link]:   /cluster-computing/Setting-up-a-GPU-Cluster-in-linux-machines
