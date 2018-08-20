Python Interface for preCICE
----------------------------

# Dependencies

Download and install Cython from http://cython.org/#download or install it using your package manager.

# Building

1. Open terminal in this folder.
2. (optional )Define the environment variable `PRECICE_MPI_IMPLEMENTATION` to either `openmpi` or `mpich`, depending on your MPI implementation. You can determine your implementation by typing `mpic++ -v` or `mpic++ --showme::version`. If you do not specify `PRECICE_MPI_IMPLEMENTATION`, we will assume you are using `openmpi`, if compilation breaks, try to define `PRECICE_MPI_IMPLEMENTATION` as `mpich`.
3. Execute the following command:

```
$ python setup.py build
```
This creates a folder `./build` with the binaries.
4. Run 
```
$ python setup.py install
```
to install the module on your system. You might need `sudo`, depending on the how you have installed python. You can use the option `--prefix=your/default/path` to install the module at an arbitrary path of your choice (for example, if you cannot or don't want to use `sudo`).

It is recommended to use preCICE as a shared library here.

# Using

1. Import `PySolverInterface` into your code:

```
import PySolverInterface
from PySolverInterface import *
```

2. If you use preCICE with MPI, you also have to add
   
```   
from mpi4py import MPI
```

To install mpi4py, you can e.g. (you need MPI already installed, e.g. libopenmpi-dev) 

```
sudo apt-get install python-pip
sudo pip install mpi4py
```


NOTE: 
- For an example of how the `PySolverInterface` can be used, refer to the 1D tutorial. (https://github.com/precice/elastictube1d/tree/master/PythonTube)
- In case the compilation fails with `shared_ptr.pxd not found` messages, check if you use the latest version of Cython.