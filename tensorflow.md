# tensorflow
## GPU setup
The procedure for Ubuntu 18.04 can be found [here][Install CUDA with apt]

[Install CUDA with apt]:https://www.tensorflow.org/install/gpu#install_cuda_with_apt

## cuDNN
install the cuDNN library with the correct version, refer to the documentation [2.3.4.1 Ubuntu network Installation][NVIDIA CUDNN]

[NVIDIA CUDNN]:https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html

to check the package version in the repository, use:

  apt-cache search <packagename>
  apt-cache policy <packagename>
 
  
## errors
* cannot find libcusolver.so.11
  sudo find / -name 'libcudart.so.11.0'
  
  export LD_LIBRARY_PATH=/usr/local/cuda-11.0/lib64:/usr/local/cuda-11.0/lib64
  
  sudo ln -s /usr/local/cuda-11.0/targets/x86_64-linux/lib/libcusolver.so.10 /usr/local/cuda-11.0/targets/x86_64-linux/lib/libcusolver.so.11
  
* cannot find libcusolver.so.11 (22/nov/2021)
  
  reinstall cuda with deb(local) option
  
  https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local


## GPU driver
* problem: CUDA_ERROR_NO_DEVICE: no CUDA-capable device is detecte
  
  sudo apt-get -y install cuda
  
  ubuntu-drivers devices
  
  sudo apt install nvidia-driver-520
  
  
  Mauel:
  Nvidia graphics drivers were missing.
    sudo lshw -C display

    https://www.nvidia.com/Download/index.aspx?lang=en-us
    The NVIDIA driver provided by Ubuntu can be installed by launching the
     "Software & Updates" application, and by selecting the NVIDIA driver from the
     "Additional Drivers" tab
  
  Second-problem
  https://github.com/NVIDIA/nvidia-docker/issues/1328
  
  TEST:
  tf.config.list_physical_devices('GPU')
  
 
 # One successful example
  
install GPU support by following commands suggested at [here][Install CUDA with apt] (cudatoolkit=11.2 cudnn=8.1.0)

install tensorflow with pip specifying the version 2.9.2 (tensorflow=2.9.2)

### encoutered problem and solutions
#### cuBLAS
downgrade tensorflow from 2.10 to 2.9.2

https://github.com/google-research/multinerf/issues/47

#### Tensorflow
"RuntimeError: The Session graph is empty. Add operations to the graph before calling run()"
https://github.com/OlafenwaMoses/ImageAI/issues/400

Add tf.compat.v1.disable_eager_execution() in the starting of algorithm

#### Tensorflow probability
install tensorflow probality version that is in compile with tensorflow version (0.17.0 & 2.9.2)
https://github.com/tensorflow/probability/releases

  
