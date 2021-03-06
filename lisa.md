# LISA GPU-island

## Account creation

Ask for an account by sending an email to <helpdesk@surfsara.nl>.
Add the following [information](https://userinfo.surfsara.nl/systems/lisa/account) in your email.
Note that a (short) support letter from your advisor is mandatory to get approved.  
It should normally take 1-2 days.

## Hostname

`login-gpu.lisa.surfsara.nl` to access GPU nodes.

The head node has GPUs. You can debug your code there for 15 min.

## Useful things to have in your `.bashrc`

```bash
module load eb
module load CUDA
module load cuDNN
```

You need to load `eb` first to have access to the CUDA modules.

Pick the version you want for CUDA by looking at what's available `module avail CUDA`

## Get a node with torque

```bash
qsub -I -lwalltime=HH:MM:SS -qgpu
```

`-I` interactive session  
`-lwalltime` maximum of 5 days (120:00:00)  
`-qgpu` get a node with GPUs

You can also submit a job instead of using an interactive session:

```bash
qsub -lwalltime=HH:MM:SS -qgpu myjob.sh
```

torque will provide a job id. Use that id if you want to remove yourself from the queue with `qdel [job id]`.

## Monitor node usage

```bash
qstat -n gpu && qstat -q gpu
```

Also useful to see only the queue:

```bash
qstat -i gpu
```

## Disk space

You will be allocated 200GB on your home folder.

There are also temporary storage space and project space available. Check this [page](https://userinfo.surfsara.nl/systems/lisa/getting-started#filesystems).


## Credit system

You can monitor your credits through `accinfo`, which gives an overview of your account information and your credit budget, or `accuse` which shows your monthly usage.

Make sure that you don't have a credit of 0, otherwise ask Boy Menist <b.n.j.menist@uva.nl> to fix your account.  

At first, 10k credits are assigned to new users.
If you run out of credits (i.e. negative number), ask the helpdesk for more credits and put Boy Menist on cc.

One hour of computation on a GPU node is equivalent to 48 credits.

## More info

Read the [starting guide](https://userinfo.surfsara.nl/systems/lisa/getting-started) for more info.
