## Python

### Table of Contents
* [Installation](#install)
* [Packages](#pack)

### Installation<a name="install"></a> 

#### Installation of Python from Source

If you want to install a local version of python (which allows you to add packages) on a server that does not give you root access you can do the following:

* Create local folder for your installation (`/path/to/python`)
* Download source code: [https://www.python.org/downloads/source](https://www.python.org/downloads/source)
* Configure Python: in `/path/to/python` do `./configure -prefix=/path/to/python-bin`
* Compile Python: `make`
* Install python to your local path: `make install`
* Add local path to your environment. In your `~./bashrc` add the following line:
```bash
export PATH=/path/to/python-bin/bin:${PATH}
```

#### Adding Packages on RCDC's clusters

You can always try to extend the installation by add the packages locally. For instance if I wanted to install a local copy of `pypesto`, you can run
``` bash
pip install pypesto --user
```

This will install the package you want locally without bothering the main installation branch.


### Packages

#### pyPESTO

`pyPESTO` can be downloaded here [https://pypi.org/project/pypesto](https://pypi.org/project/pypesto). 

#### Installation Python3.7.10 and Pymc3/Pypesto

`pyPESTO` is compatible with only certain versions of other modules (and python). Different samplers may require different packages. To get the pymc3Sampler running I needed to switch from Python3.7.9 to Python3.7.10. I first installed miniconda prebuilt with python3.7.10 and then pip-installed the remaining packages to make sure everything was compatible. 
Assuming you want to install in the following directory: 
`/PATH-TO-PYTHON-DIRECTORY/Python-3.7.10`

Here are the steps to do the same

``` bash
#Start the installer for miniconda with python3.7.10
bash /var/tmp/Miniconda3-py37_4.9.2-Linux-x86_64.sh  

#Accept the license agreement
#It asks where you want to install, type:
/PATH-TO-PYTHON-DIRECTORY/Python-3.7.10

#When it asks if you want to initialize conda, answer no.
#To install to the path, set PATH variable
export PATH=/PATH-TO-PYTHON-DIRECTORY/Python-3.7.10/bin:$PATH

conda install python=3.7.10 anaconda=custom

#CHECK VERSION
python --version

#double check other packages are okay
pip3 install pymc3==3.9.1 --no-cache
pip3 install theano==1.0.4 --no-cache
pip3 install pypesto --no-cache
pip3 install arviz==0.8.3 --no-cache
```
