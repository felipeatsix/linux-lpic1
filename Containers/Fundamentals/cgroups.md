## Install cgroup tools to be able to interact with cgroups
```bash
sudo apt install -y cgroup-tools
```

## List all cgroups on the system
```bash
lscgroup
```
## List cgroups associated with a process
```bash
sudo cat /proc/<PID>/cgroup
```

## The freezer cgroup

The cgroup called `freezer` allows a group of task to be suspended and then resumed.

In this cgroup, tasks have two states, `thawed` or `frozen` where `thawed` are resumed tasks and `frozen` are suspended tasks