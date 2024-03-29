# Identify and configure hardware
Identifying and configuring hardware on a Linux system involves the process of recognizing the hardware components connected to the system and configuring them to work optimally with the operating system. This task is crucial for ensuring proper functionality and compatibility between hardware and software.

When a Linux system is booted, the kernel initializes and probes the hardware devices present in the system. It uses various mechanisms such as device drivers, kernel modules, and system utilities to identify and configure the hardware.

The identification process involves detecting and recognizing devices such as processors, memory, storage drives, network interfaces, graphics cards, sound cards, and other peripherals. The Linux kernel maintains a vast database of device drivers that contain information and instructions for each supported hardware component. These drivers enable the kernel to communicate and interact with the hardware effectively.

Once the hardware is identified, the next step is to configure it. Configuration involves setting up parameters, options, and settings to optimize the performance and functionality of the hardware. This can include setting the resolution and refresh rate for a display, configuring network settings for a network interface, enabling specific features of a sound card, or fine-tuning parameters for other peripherals.

Linux provides various tools and utilities to manage hardware configuration. These tools include command-line utilities like lspci, lsusb, and lshw, which provide detailed information about the detected hardware components. Additionally, configuration files and system settings located in directories such as /etc or /sys can be modified to customize hardware behavior.

In some cases, additional drivers or firmware may need to be installed manually to support specific hardware that is not natively supported by the kernel. This typically involves downloading the necessary files from the manufacturer's website and following installation instructions.

Overall, identifying and configuring hardware on a Linux system is a fundamental aspect of system administration, ensuring that all hardware components are recognized and functioning correctly, and optimizing their performance to meet the user's needs.

### BIOS (EFI & UEFI)
BIOS stands for Basic Input/Output System. It is a `firmware` that resides on a computer's motherboard and provides the fundamental instructions and settings for the hardware components and the operating system to interact effectively.

The BIOS is responsible for initializing and configuring critical hardware components during the boot process, as well as providing basic input/output functions for the computer system. It is typically stored on a non-volatile memory chip on the motherboard, such as a ROM (Read-Only Memory) or EEPROM (Electrically Erasable Programmable Read-Only Memory).

Here are some key functions and features of the BIOS:

1. `Power-on self-test` (POST): When the computer is powered on, the BIOS performs a series of tests known as the POST to check the integrity and functionality of hardware components, such as the CPU, memory, and storage devices. It also detects and reports any errors or issues encountered during the test.

2. `System initialization`: The BIOS initializes and configures the hardware components during the boot process. This includes identifying and initializing the CPU, memory modules, hard drives, graphics cards, and other peripherals.

3. `Firmware settings`: The BIOS provides an interface, often accessed through a key combination during system startup (e.g., pressing Del or F2), to access and modify firmware settings. These settings include options related to boot order, CPU clock speed, memory timings, power management, and various other hardware-specific configurations.

4. `Boot loader`: The BIOS loads the initial boot loader, which is responsible for loading the operating system from the storage device into the computer's memory. This can be the Windows Boot Manager, GRUB (Grand Unified Bootloader) for Linux, or other boot loaders.

5. `Hardware interactions`: The BIOS provides low-level routines and drivers that allow the operating system and applications to interact with the hardware. This includes functions for keyboard input, screen output, disk operations, and other essential I/O operations.

6. `BIOS updates`: Manufacturers may release BIOS updates to improve system stability, compatibility, and security. Updating the BIOS involves flashing a new version of the firmware onto the motherboard's memory chip.

It's important to note that modern systems often use UEFI (Unified Extensible Firmware Interface) as a replacement for the traditional BIOS. UEFI offers enhanced capabilities and a graphical user interface (GUI) for firmware settings. However, the term "BIOS" is still commonly used to refer to the firmware in general, regardless of whether it is UEFI or the traditional BIOS.

Overall, the BIOS plays a critical role in the computer system, providing the foundation for hardware initialization, configuration, and interaction, ensuring the smooth operation of the computer during the boot process and beyond.

### IRQ
IRQ stands for Interrupt Request. It is a mechanism used in computer systems to manage and prioritize hardware interrupts. An interrupt is a signal sent by a hardware device to the processor, indicating that it requires attention or service from the system.

Each hardware device in a computer system is assigned a specific IRQ line, which is a dedicated electrical signal path used to deliver interrupt requests to the processor. When a hardware device needs to communicate with the CPU, it sends an interrupt request through its assigned IRQ line.

The IRQ system allows devices to request attention from the processor without having to constantly poll or check for events. When an interrupt occurs, the processor interrupts its current task, saves its state, and transfers control to an interrupt handler routine. The interrupt handler then processes the request and performs the necessary actions associated with the interrupt, such as reading data from a device or responding to a specific event.

IRQs are typically prioritized based on their urgency and importance. Higher-priority interrupts are handled first, while lower-priority interrupts may be temporarily delayed until the CPU is available to process them. The prioritization scheme helps ensure that critical events are handled promptly and efficiently.

In early computer systems, IRQs were typically represented by a numeric value from 0 to 15. Each number corresponded to a specific hardware interrupt line, and devices were assigned a particular IRQ number. However, modern systems, especially those using the Advanced Programmable Interrupt Controller (APIC) architecture, provide a more flexible and expanded IRQ system.

IRQ conflicts can occur when multiple devices attempt to use the same IRQ line simultaneously. Such conflicts can lead to malfunctions or system instability. Operating systems, including Windows and Linux, employ techniques to manage and resolve IRQ conflicts, such as reassigning IRQs or using software-based interrupt sharing.

In summary, IRQs are a vital component of computer systems, enabling hardware devices to communicate with the processor through interrupt requests. They help facilitate efficient and timely handling of device-related events and contribute to the overall functioning and responsiveness of the system.

### /proc
The `/proc` directory in a Linux system is a virtual filesystem that provides a view into the kernel and processes running on the system. It contains a wealth of information about system resources, hardware, processes, and their configurations. It is used for real-time monitoring, debugging, and accessing runtime information about the system and its components.

### /proc/interrupts
List IRQ's
```bash
cat /proc/interrupts
```

### /proc/ioports
List I/O addresses
```bash
cat /proc/ioports
```

### proc/cpuinfo
List cpu information
```bash
cat /proc/cpuinfo
```

### proc/cmdline
Read parameters the boot process passed on to the system kernel
```bash
cat /proc/cmdline
```

### proc/meminfo
List ram information
```bash
cat /proc/meminfo
```

### proc/mounts
Contains mounted partitions information
```bash
cat /proc/mounts
```

### /proc/dma
DMA (Direct Memory Access) devices are hardware components in a computer system that are capable of transferring data directly to and from memory without involving the CPU. They offload data transfer tasks from the CPU, allowing for more efficient and faster data movement between devices and memory. DMA devices are commonly found in peripherals such as network cards, sound cards, and storage devices.
```bash
cat /proc/dma
```

### BUS
A bus, such as PCI (Peripheral Component Interconnect) and USB (Universal Serial Bus), is a communication pathway that enables data transfer between various hardware components in a computer system. PCI is primarily used for connecting internal devices, such as expansion cards and graphics cards, while USB is predominantly used for connecting external devices, including keyboards, mice, printers, and storage devices. Both buses provide standardized protocols and interfaces for reliable and efficient data transmission.

### lspci
```bash
# Show devices connected through the PCI bus
lspci

# Same as above but expand details
lspci -v

# Same as above but for a specific device
lspci -s <device ID> -v
```

### lsusb
Note that each USB bus can have multiple devices connected to it.
```bash
# Show devices connected through USB bus
lsusb

# Same as above but showing device details
lsusb -v

# Same as above but for a specific device
lsusb <bus:device> -v
```

# Virtual partitions
Virtual partitions in a Linux system are software-based divisions of storage that appear as separate entities, allowing users to manage and allocate resources efficiently.

Show system partitions
```bash
# Show all partitions, including virtual ones
df -a
```

Show swap file systems
```bash
cat swaps
```

### /proc 
Information of active processes and hardware resources

### /sys
Information of hardware devices (sysfs)

### /dev
References of system devices, including storage (udev)

# System processes

### udev
A device manager process
```bash
# Keep monitoring device events
udevadm monitor
```

### dbus/hald
A process that manages communication between processes. Inform processes the situation of hardware devices

> You can find these processes with the following commands
```bash
ps axu | grep udev
ps axu | grep dbus
```

# Device modules
```bash
# Display kernel version
uname -r

# List device modules folders
ls /lib/modules/<kernel version>/kernel
```

### lsmod
Show status of modules in the Linux kernel

### modinfo <module>
Show detailed information of a given linux kernel module

### rmmod <module>
Remove a given linux kernel module

### insmod <module path>
Add a given linux kernel module, insmod `does not load any module dependency`
> Example
```bash
# Find psmousr module path
modinfo psmouse

# Add psmouse with insmod command
insmod /lib/modules/<kernel version>/kernel/drivers/input/psmouse.ko
```

### modprob
Similar to insmod, but it does not require module path and it does load all module dependencies
> Example
```bash
# Load bluecard_cs module
modprobe bluecard_cs

# List bluecard drivers, the bluecard_cs should be displayed along with its required dependencies
lsmod | grep blue

# Remove a module, along with its dependencies
modprobe -r bluecard_cs
```