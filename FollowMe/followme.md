
# FollowMe Installation (Ubuntu)

FollowMe has a bunch of dependencies. Caffe is the most troublesome, so here's a guide.

How to build [this caffe version (ssd branch)](https://github.com/weiliu89/caffe/tree/ssd) from source:

1. Check out the SSD Branch:
   1. `git clone https://github.com/weiliu89/caffe.git`
   2. `cd caffe`
   3. `git checkout ssd`
2. Compilation Preparations:
   1. install prerequisites following the [official caffe installation guide](http://caffe.berkeleyvision.org/installation.html):
      1. `sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler`
      2. `sudo apt-get install --no-install-recommends libboost-all-dev`
      3. `sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev`
      4. `sudo apt-get install python-dev`
      5. optional: install CUDA / cuDNN if you want to use a GPU
      6. not sure which one of these you need:  
         - `sudo apt-get install libatlas-base-dev` (this one is the default I think)
         - `sudo apt-get install libopenblas-dev`
      7. you can check your version of opencv with `pkg-config --modversion opencv`
3. Modify the Makefile.config:
   1. `cp Makefile.config.example Makefile.config`
   2. `gedit Makefile.config`
      1. uncomment `USE_CUDNN := 1` if you want to use cuDNN
      2. uncomment `CPU_ONLY := 1` if you want to run without GPU (it's really slow, but it works)
      3. uncomment `PYTHON_LIBRARIES` and `PYTHON_INCLUDE` to enable Python3
      4. modify `INCLUDE_DIRS` and `LIBRARY_DIRS` to look like this:  
`INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/`  
`LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial`
4. Compilation:  
   1. `make all` (if you run into errors, first check [here](https://github.com/BVLC/caffe/wiki/Commonly-encountered-build-issues) before googling stuff)
   2. `make test`
   3. `make runtest`
   4. `make pycaffe`
   5. add `export PYTHONPATH=/path/to/caffe-weiliu89/python:$PYTHONPATH` to your `~/.bashrc`
   6. `bash` (to apply the `.bashrc` changes)
   7. test the caffe installation by running  
`python3`  
`import caffe`  
   8. if you didn't get an error, leave the python interpreter:  
`quit()`
5. Check out the FollowMe Repository:
   1. Move to a directory of your choice
   2. `git clone https://gitlab.com/rtlions/navigation/followme.git`
   3. `cd followme`
6. Test your webcam:
   1. `python3 camera_test.py`
   2. you should see a live feed of your webcam
   3. press `ESC` to close
7. Run FollowMe:
   1. `python3 person_followMe_gpu.py`