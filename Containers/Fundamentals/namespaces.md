## List all namespaces for a particular process:

```bash
sudo ls -l /proc/<PID>/ns/
```

## Creating two networks separated by different namespaces:

```bash
# create two namespaces
sudo ip netns add namespace 1
sudo ip netns add namespace 2
# list newly created network namespaces
ip netns list
# Create a pair of interconnected virtual ethernet devices
sudo ip link add veth1 type veth peer name veth2
# Link each device to a namespace respectively
sudo ip link set veth1 netns namespace1
sudo ip link set veth2 netns namespace2
# Bring up the devices while assigning them IP addresss
sudo ip netns exec namespace1 ip link set dev veth1 up
sudo ip netns exec namespace2 ip link set dev veth2 up
sudo ip netns exec namespace1 ip addr add 192.168.1.1/24 dev veth1
sudo ip netns exec namespace2 ip addr add 192.168.1.2/24 dev veth2
# Test communication
sudo ip netns exec namespace1 ping -c5 192.168.1.2
sudo ip netns exec namespace1 ping -c5 192.168.1.1
# Delete namespaces
sudo ip netns delete namespace1
sudo ip netns delete namespace2
# Confirm namespaces were deleted
ip netns list
```