# Prince Cluster

![prince-cluster](https://wikis.nyu.edu/download/attachments/82709666/AccessingPrinceXYZY.png)

### Login from outside NYU network

```bash
  ssh <nyu-netid>@hpc.nyu.edu
  ssh <nyu-netid>@prince.hpc.nyu.edu
```

### Login from within NYU network

```bash
  ssh <nyu-netid>@prince.hpc.nyu.edu
```

# SLURM Job Scheduler

## Interactive Job:

```bash
  srun <options> --pty /bin/bash
```

IvyBridge CPU nodes (20-cores @3.0GHz, 62GB memory):
```bash
  srun --nodes 4 --ntasks-per-node=1 --cpus-per-task=20 --mem=62GB --time=5:00:00 --partition="c28,c29,c30,c31,c32_41" --pty /bin/bash
```

Broadwell CPU nodes (28-cores @ 2.6GHz, 125GB memory):
```bash
  srun --nodes 2 --ntasks-per-node=1 --cpus-per-task=28 --mem=125GB --time=5:00:00 --partition="c01_17" --pty /bin/bash
```

Broadwell GPU nodes (28-cores @2.6GHz, 125GB memory, 4 Tesla P40):
```bash
  srun --nodes 1 --ntasks-per-node=1 --cpus-per-task=28 --mem=125GB --time=5:00:00 --partition="p40_4" --gres=gpu:4 --pty /bin/bash
```

Skylake GPU nodes (40-cores @2.4GHz, 384GB memory, 4 Tesla V100 SXM2):
```bash
  srun --nodes 1 --ntasks-per-node=1 --cpus-per-task=20 --mem=375GB --time=1:00:00 --partition="v100_sxm2_4" --gres=gpu:4 --pty /bin/bash
```


## Job Scripts:

```bash
  sbatch <script-file-name>
```

Script file structure:
```bash
  #!/bin/bash
  #SBATCH <options>
  mpirun ...
```

## Job Options:

-  --nodes=1
-  --ntasks-per-node=1
-  --cpus-per-task=20
-  --time=5:00:00
-  --mem=2GB
-  --partition="partition-list"
-  --gres=gpu:k80:3 -c3


## Cancel Job:

```bash
  scancel jobid
```

## Miscellaneous:

```bash
  squeue -u $USER # list jobs and status
  sinfo           # list node-partitions and status
```

## References:

* https://wikis.nyu.edu/display/NYUHPC/Getting+started+on+Prince
* https://wikis.nyu.edu/display/NYUHPC/Accessing+the+Prince+cluster
* https://wikis.nyu.edu/display/NYUHPC/Slurm+Tutorial
* https://wikis.nyu.edu/display/NYUHPC/Requesting+resources+via+Slurm
* https://wikis.nyu.edu/display/NYUHPC/Running+interactive+jobs
* https://wikis.nyu.edu/display/NYUHPC/Putting+all+pieces+together
* https://github.com/cvalenzuela/hpc
