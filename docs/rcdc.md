## RCDC

### Table of Contents
* [General Information](#info)
* [Allocations](#alloc)
* [Creating an Account](#account)
* [Interactive Jobs](#inter)
* [Job Submission Files](#jobsub)
* [SSH Keys](#sshkeys)
* [CLAIRE](#claire)

### General Information<a name="info"></a> 

For more information on how to access advanced computing resources at RCDC visit the following web page:

* [RCDC webpage](https://uh.edu/rcdc)
* [getting started](https://uh.edu/rcdc/support-services/user-guide/getting-started-clusters)

To learn how the available SUS will be affected by executing software on a particular hardware, see [allocations](https://uh.edu/rcdc/support-services/user-guide/allocations).

### Allocations on RCDC Clusters<a name="alloc"></a> 

* Opuntia
	* Awarded allocation: 50,000 SUs
	* Start date: September 1st 2020
	* Renewal date: July 2021.

* Sabine
	* Awarded allocation: 25,000 SUs
	* Start date: September 1st 2020
	* Renewal date: July 2021.


### Creating an Account<a name="account"></a> 

To create an account for one of the RCDC clusters go here:
[https://uh.edu/rcdc/getting-started/request-account.php](https://uh.edu/rcdc/getting-started/request-account.php)

Information to be entered:

* Principle Investigator: Andreas Mang
* PI Email Address: andreas@math.uh.edu
* Grant Information: UH allocation of amang (PI)
* If you want to execute / develop GPU code use Sabine [ Resource ( Cluster ) ]
* For CPU code, use "Opuntia" [ Resource ( Cluster ) ]
* For your login shell select `bash` (if you don't know what you are doing)


### Interactive Jobs<a name="inter"></a>

On the compute nodes, to run an interactive job (log into a compute node requesting one node and 20 cores) you need to do the following:
```
srun -A mang -n 20 -t 2:00:00 -p medium --pty /bin/bash -l
```

in your command window. To request a GPU do
```
srun -A mang -t 3:00:00 -n 1 -p volta --gres=gpu:1 -N 1 --pty /bin/bash -l
```

You can define an ALIAS in your `~/.bashrc` to make your live easier. Here are two examples:
```
alias irun='srun -A mang -t 3:00:00 -n 1 -p volta --gres=gpu:1 -N 1 --pty /bin/bash -l'
```

```
alias irun='srun -A mang -n 20 -t 2:00:00 -p medium --pty /bin/bash -l'
```

### Job Submission Files<a name="jobsub"></a>

An exemplary job submission file (one node with 20 CPU cores)
```bash
#!/bin/bash
### sbatch parameters
#SBATCH -J #ADD YOUR JOB NAME HERE
#SBATCH -N 1
#SBATCH -n 20
#SBATCH -o hostname.out
#SBATCH -e hostname.err
#SBATCH -t 0-04:00:00
#SBATCH --mail-user= #ADD YOUR EMAIL HERE
#SBATCH --mail-type=begin
#SBATCH --mail-type=end
#SBATCH --mail-type=fail
#SBATCH -A mang
export I_MPI_PIN_DOMAIN=omp
export OMP_NUM_THREADS=1
module load # ADD YOUR MODULES HERE
### directory of your code
CDIR= #ADD YOUR CODE DIRECTORY HERE (NO EMPTY SPACE AFTER =)
DDIR= #ADD YOUR DATA DIRECTORY DIRECTORY HERE (NO EMPTY SPACE AFTER =)
#### define paths
# ADD DEFINITION FOR PATHS HERE IF YOU HAVE ANY
#### submitt job
# ADD COMMAND YOU WOULD LIKE TO EXECUTE HERE
```


### SSH Keys<a name="sshkeys"></a>

To prevent having to enter your password whenever you check out code on a compute node add your SSH key to GitHub.

General instructions can be found here: [ssh-agent](https://docs.github.com/en/github-ae@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

```
ssh-keygen -t ed25519 -C "YOUREMAIL_GIT@uh.edu"
```
To enable this functionality on SABINE you will also need to modify `~/.ssh/config`. Add the following:
```bash
Host *
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_ed25519
```


### CLAIRE<a name="claire"></a>


#### Compilation of CLAIRE on Sabine

* Set of modules loaded:
```bash
module load python
module load CMake
module load OpenMPI/intel/4.0.1
module load CUDA/10.0.130 (edited) 
```
* Compilation of dependencies:
```bash
cd deps
make -j
cd ..
```

* Compilation of CLAIRE:
```bash
source deps/env_source.sh
make -j
``` 
