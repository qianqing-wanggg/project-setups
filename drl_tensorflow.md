
# The State of Sparse Training in Deep Reinforcement Learning

ML course project 2: reproducibiliyt challenge - [The State of Sparse Training in Deep Reinforcement Learning](https://github.com/google-research/rigl/tree/master/rigl/rl#the-state-of-sparse-training-in-deep-reinforcement-learning)

## Main steps
1. Check GPU by:
  > nvidia-smi
  If Nvidia graphics drivers were missing, *The NVIDIA driver provided by Ubuntu can be installed by launching the "Software & Updates" application, and by selecting the NVIDIA driver from the "Additional Drivers" tab*.
2. install GPU support tensorflow by following [official guidelines](https://www.tensorflow.org/install/gpu#install_cuda_with_apt) (cudatoolkit=11.2 cudnn=8.1.0)
3. install tensorflow with pip specifying the version 2.9.2 (tensorflow=2.9.2)
4. downgrade tensorflow from 2.10 to 2.9.2. issue with **cuBLAS** and [solution](https://github.com/google-research/multinerf/issues/47)
5. install tensorflow probality version that is compatible with tensorflow version [0.17.0 & 2.9.2](https://github.com/tensorflow/probability/releases)
  > pip install tensorflow_probability==0.17.0

## Other steps
- when such problem pops out:
  > "RuntimeError: The Session graph is empty. Add operations to the graph before calling run()"
  add the [following codes](https://github.com/OlafenwaMoses/ImageAI/issues/400):
  > tf.compat.v1.disable_eager_execution()
- when such problem pops out:
  > cannot find libcusolver.so.11
  you need to find the missing file first and add it to path:
  > sudo find / -name 'libcudart.so.11.0'
  > export LD_LIBRARY_PATH=/usr/local/cuda-11.0/lib64:/usr/local/cuda-11.0/lib64



# Archived logs
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



  
