# Instructions for Servers on UH's RCDC

## Table of Content
* [General Information](#info)
* [Allocations](#alloc)
* [Creating an Account](#account)
* [Interactive Jobs](#inter)
* [Job Submission Files](#jobsub)

##<a name="info"></a>  General Information

For more information on how to access advanced computing resources at RCDC visit the following web page:

* [RCDC webpage](https://uh.edu/rcdc)
* [getting started](https://uh.edu/rcdc/support-services/user-guide/getting-started-clusters)

To learn how the available SUS will be affected by executing software on a particular hardware, see [allocations](https://uh.edu/rcdc/support-services/user-guide/allocations).

##<a name="alloc"></a> Allocations on RCDC Clusters

* Opuntia
	* Awarded allocation: 50,000 SUs
	* Start date: September 1st 2020
	* Renewal date: July 2021.

* Sabine
	* Awarded allocation: 25,000 SUs
	* Start date: September 1st 2020
	* Renewal date: July 2021.


##<a name="account"></a> Creating an Account

To create an account for one of the RCDC clusters go here:
[https://uh.edu/rcdc/getting-started/request-account.php](https://uh.edu/rcdc/getting-started/request-account.php)

Information to be entered:

* Principle Investigator: Andreas Mang
* PI Email Address: andreas@math.uh.edu
* Grant Information: UH allocation of amang (PI)
* If you want to execute / develop GPU code use Sabine [ Resource ( Cluster ) ]
* For CPU code, use "Opuntia" [ Resource ( Cluster ) ]
* For your login shell select `bash` (if you don't know what you are doing)


###<a name="inter"></a> # Interactive Jobs

On the compute nodes, to run an interactive job (log into a compute node) you need to do the following:
```
srun -n 20 -t 2:00:00 --pty /bin/bash -l
```

in your command window



##<a name="jobsub"></a> Job Submission Files

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