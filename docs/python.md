## Python

### Table of Contents
* [Installation](#install)

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
