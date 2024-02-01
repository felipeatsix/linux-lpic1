# UnionFS

UnionFS transparently overlays files and directories of separate filesystems, to create a unified seamless
filesystem. Each participant directory is referred to as a branch and we may set priorities and access
modes while mounting branches.


## Install unionfs tool
```bash
sudo apt install -y unionfs-fuse
```

## Create a unionfs
```bash
# Create 2 branches (directories) each containing  1 file with different names
mkdir dir1
mkdir dir2
touch ./dir1/f1
touch ./dir2/f2
# Create the union directory which will later be associated with unionfs
mkdir union
# Mount the two branches dir1 and dir2
unionfs dir1/:dir2 union/
# List files, you should see both f1 and f2
ls union/
```