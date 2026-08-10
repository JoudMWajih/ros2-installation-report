# ROS 2 Installation Report Using UTM

## Project Overview

This report documents the installation process of ROS 2 on Ubuntu using UTM on macOS.

The goal of this task is to prepare a Linux environment for robotics development and install ROS 2 successfully.

---

## Tools Used

- macOS
- UTM Virtual Machine
- Ubuntu
- Terminal
- ROS 2

---

## Installation Environment

| Item | Description |
|---|---|
| Virtual Machine Tool | UTM |
| Operating System | Ubuntu |
| ROS Version | ROS 2 |
| Installation Method | Terminal commands |

---

## Step 1: Create Ubuntu Virtual Machine Using UTM

First, UTM was opened on macOS to create a new Linux virtual machine.

The Ubuntu ISO file was selected using the **Boot from ISO image** option.

### Screenshot

![UTM Ubuntu Setup](images/01-utm-ubuntu.png)

---

## Step 2: Start Ubuntu

After creating the virtual machine, Ubuntu was launched successfully inside UTM.

### Screenshot

![Ubuntu Started](images/02-ubuntu-started.png)

---

## Step 3: Check Ubuntu Version

Before installing ROS 2, the Ubuntu version was checked to make sure the system is ready.

```bash
lsb_release -a
```

### Screenshot

![Ubuntu Version](images/03-ubuntu-version.png)

---

## Step 4: Update System Packages

The system package list was updated using the following command:

```bash
sudo apt update
```

### Screenshot

![Update System](images/04-update-system.png)

---

## Step 5: Install Required Tools

Some required tools were installed before adding the ROS 2 repository.

```bash
sudo apt install software-properties-common curl -y
```

### Screenshot

![Install Required Tools](images/05-required-tools.png)

---

## Step 6: Enable Universe Repository

The Universe repository was enabled because ROS 2 requires some packages from it.

```bash
sudo add-apt-repository universe
```

### Screenshot

![Enable Universe](images/06-enable-universe.png)

---

## Step 7: Add ROS 2 GPG Key

The ROS 2 GPG key was added to allow the system to verify ROS 2 packages.

```bash
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

### Screenshot

![ROS 2 Key](images/07-ros2-key.png)

---

## Step 8: Add ROS 2 Repository

The ROS 2 repository was added to the Ubuntu package sources list.

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

### Screenshot

![ROS 2 Repository](images/08-ros2-repository.png)

---

## Step 9: Update Package List Again

After adding the ROS 2 repository, the package list was updated again.

```bash
sudo apt update
```

### Screenshot

![Update After Repository](images/09-update-after-repository.png)

---

## Step 10: Install ROS 2

ROS 2 was installed using the following command:

```bash
sudo apt install ros-humble-desktop -y
```

### Screenshot

![Install ROS 2](images/10-install-ros2.png)

---

## Step 11: Source ROS 2 Environment

To use ROS 2 commands in the terminal, the ROS 2 setup file was sourced.

```bash
source /opt/ros/humble/setup.bash
```

To make ROS 2 available automatically in every new terminal, the command was added to `.bashrc`.

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### Screenshot

![Source ROS 2](images/11-source-ros2.png)

---

## Step 12: Test ROS 2 Installation

The ROS 2 installation was tested by running:

```bash
ros2
```

If the installation is successful, the terminal displays the available ROS 2 commands.

### Screenshot

![ROS 2 Test](images/12-ros2-test.png)

---

## Result

ROS 2 was installed successfully on Ubuntu using UTM.

The system recognized the `ros2` command, which confirms that the installation was completed.

---

## Problems Faced

During the installation process, some issues may happen, such as:

- Slow installation because UTM is running a virtual machine
- Internet connection problems
- Missing packages
- Forgetting to source the ROS 2 environment
- Using an Ubuntu version that does not match the ROS 2 version

---

## Conclusion

This task helped in understanding how to prepare a Linux environment for robotics development.

The installation process included setting up Ubuntu on UTM, updating the system, adding the ROS 2 repository, installing ROS 2, and testing the installation using the terminal.
