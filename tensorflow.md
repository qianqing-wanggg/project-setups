# tips-and-tricks

## cuDNN
install the cuDNN library with the correct version, refer to the documentation [2.3.4.1 Ubuntu network Installation][NVIDIA CUDNN]

[NVIDIA CUDNN]:https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html

to check the package version in the repository, use:
  apt-cache search <packagename>
  apt-cache policy <packagename>
 
  
## errors
* cannot find libcusolver.so.11
  sudo ln -s /usr/local/cuda-11.0/targets/x86_64-linux/lib/libcusolver.so.10 /usr/local/cuda-11.0/targets/x86_64-linux/lib/libcusolver.so.11