1. Add a new 10 GB disk and create partitions using MBR:
```
# run the fdisk command and go through the application navigation options.

# After done, press down the key 'w' to save it.

# Then verify the changes using "fdisk -l <name of drive>"
```

2. Change a partition size
```
use the command "parted" and iside of it use the command "resizepart <id> <end of partition>
```

3. Define a swap partition filesystem
```
mkswap <partition>
```