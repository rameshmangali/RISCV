# RISC-V Steel: Complete Hardware and Software Implementation
 - ## [Using Vivado](#Installation-Guide-for-Linux-Ubuntu-Toolchain-and-Vivado-Simulator)
 - ## [Using Spike simulator](#Installing-RISCV-Steel-on-Ubuntu-by-using-spike-simulator)

## Installation Guide for Linux, Ubuntu, Toolchain, and Vivado Simulator

This README provides a step-by-step guide to install the required software: Linux (via WSL for Windows), Ubuntu, the RISC-V GNU Toolchain, and Vivado Simulator.

### Table of Contents

1. [Pre-requisites](#pre-requisites)
2. [Step 1: Clone the Repository](#step-1-clone-the-repository)
3. [Step 2: Clone the Toolchain](#step-2-clone-the-toolchain)
4. [Step 3: Install Linux via WSL](#step-3-install-linux-via-wsl)
5. [Step 4: Initial Ubuntu Setup](#step-4-initial-ubuntu-setup)
6. [Step 5: Update Ubuntu](#step-5-update-ubuntu)
7. [Step 6: Install Toolchain Dependencies](#step-6-install-toolchain-dependencies)
8. [Step 7: Clone Repositories in Ubuntu](#step-7-clone-repositories-in-ubuntu)
9. [Step 8: Navigate to Toolchain Directory](#step-8-navigate-to-toolchain-directory)
10. [Step 9: Configure Toolchain](#step-9-configure-toolchain)
11. [Step 10: Build Toolchain](#step-10-build-toolchain)
12. [Step 11: Run Hello World Example](#step-11-run-hello-world-example)
13. [Step 12: Download and Install Vivado](#step-12-download-and-install-vivado)
14. [Step 13: Extract the Vivado Installation Files](#step-13-extract-the-vivado-installation-files)
15. [Step 14: Install Vivado Using xsetup](#step-14-install-vivado-using-xsetup)

---

### Pre-requisites

Before starting, ensure you have:
- **GitBash** (for Windows users)
- **Windows Subsystem for Linux (WSL)**



### Step 1: Clone the Repository

1. Open GitBash or terminal.
2. Clone the RISC-V Steel repository:
   ```bash
   git clone https://github.com/riscv-steel/riscv-steel



### Step 2: Clone the Toolchain
1. In the terminal (GitBash or Linux), clone the RISC-V GNU Toolchain by running the following command:
    ```bash
    git clone https://github.com/riscv/riscv-gnu-toolchain
    ```
2. This will clone the RISC-V GNU Toolchain repository to your local machine.


### Step 3: Install Linux via WSL
1. For Windows users, open PowerShell with Administrator privileges.
2. Run the following command to install Linux via Windows Subsystem for Linux (WSL):
    ```bash
    wsl --install
    ```
3. After WSL is installed, Ubuntu will automatically be installed.
4. Close PowerShell and restart your PC to finalize the installation.


### Step 4: Initial Ubuntu Setup
1. Open the newly installed Ubuntu application.
2. When prompted, create a unique username and password. The password will not be visible as you type.
3. Confirm your password by retyping it.


### Step 5: Update Ubuntu
1. Once you're inside the Ubuntu terminal, update your system by running the following commands:
    ```bash
    sudo apt-get update
    sudo apt-get upgrade
    ```
   This will ensure that you have the latest versions of all necessary packages.


### Step 6: Install Toolchain Dependencies
1. To install the necessary dependencies for building the toolchain, run the following command in Ubuntu:
    ```bash
    sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev
    ```
   This will install essential development tools and libraries required to build the RISC-V toolchain.


### Step 7: Clone Repositories in Ubuntu
1. Clone the RISC-V Steel repository again, but this time inside Ubuntu:
    ```bash
    git clone https://github.com/riscv-steel/riscv-steel
    ```
2. Similarly, clone the RISC-V GNU Toolchain in Ubuntu:
    ```bash
    git clone https://github.com/riscv/riscv-gnu-toolchain
    ```
3. After cloning both repositories, verify that they have been successfully cloned by running the following command to list the contents of the directory:
    ```bash
    ls
    ```

### Step 8: Navigate to Toolchain Directory
1. Navigate to the `riscv-gnu-toolchain` directory by using the following command:
    ```bash
    cd riscv-gnu-toolchain/
    ```
2. You should now see the contents of the `riscv-gnu-toolchain` directory.

### Step 9: Configure Toolchain
1. Run the configuration command to prepare the toolchain for building:
    ```bash
    ./configure --prefix=/opt/riscv --with-arch=rv32izicsr --with-abi=ilp32
    ```
   The `--with-arch` and `--with-abi` options are specific to the architecture and ABI of your system. Make sure these match your requirements.


### Step 10: Build Toolchain
1. Start building the toolchain by running the following command:
    ```bash
    sudo make
    ```
   This process will take some time as it downloads and compiles a large number of files (~5 million objects). Be patient and allow the process to complete.

2. Once the process finishes, verify that the build was successful by running:
    ```bash
    sudo make
    ```

3. Exit the toolchain directory by running:
    ```bash
    cd ../
    ```

   Then, list the contents of the directory using the `ls` command to ensure everything is in place.


### Step 11: Run Hello World Example
1. Navigate to the hello_world example directory:
   ```bash
   cd ./riscv-steel/examples/hello_world/software
2. Once inside, compile the example program by running:
   ```bash
   make
3. If any errors occur during this process, follow the troubleshooting guide provided in the RISC-V Steel documentation or visit the repository for further assistance.


### Step 12: Download and Install Vivado
1. **Download Vivado SDK:**
   - Visit the Xilinx download page [here](https://www.xilinx.com/support/download.html).
   - Download the Vivado SDK file (`Xilinx_Vivado_SDK_2018.3_1207_2324.tar.gz`).
   - This is a large file, so make sure you have sufficient space on your system (around 20GB).
2. create a new directory named vivado in the ubuntu by using the command
   ```bash
   cd ~
   mkdir vivado
4. **Move the Downloaded File to Ubuntu:** After downloading the Vivado `.tar.gz` file, it will likely be in your Windows Downloads folder. Follow these steps to copy the file to your Ubuntu environment:
   - Open the Ubuntu terminal and type the following command to navigate to your Downloads folder:
     ```bash
     cd /mnt/c/Users/<Your-Username>/Downloads/
     ```
   - Copy the Vivado SDK file to a preferred directory in Ubuntu (e.g., `~/vivado`):
     ```bash
     cp -r Xilinx_Vivado_SDK_2018.3_1207_2324.tar.gz ~/vivado/
     ```
   - Now, navigate to the directory where you copied the file:
     ```bash
     cd ~/vivado/
     ```


### Step 13: Extract the Vivado Installation Files
1. In the Ubuntu terminal, extract the contents of the `.tar.gz` file by running the following command:
   ```bash
   tar -xvzf Xilinx_Vivado_SDK_2018.3_1207_2324.tar.gz

2. The -xvzf flags ensure the file is extracted, and you can see the extraction process in real-time.
3. Once the extraction is complete, list the contents of the directory using:
   ```bash
   ls
 You should see the extracted files and folders, including the xsetup file.



 ### Step 14: Install Vivado Using xsetup
1. To begin the Vivado installation, run the `xsetup` script from the extracted files:
   ```bash
   sudo ./xsetup
2. The Vivado installer will launch. Follow these steps during the installation process:

   - Select Installation Directory: Choose the default directory or specify a custom directory for installation.
   - Vivado Edition: Select the edition you want to install (WebPack edition or another, depending on your needs).
   - Download Required Components: Ensure that all necessary components and tools are selected for installation.
3. Once the installation completes, Vivado will be successfully installed on your Ubuntu system.
4. After installation, you can verify if Vivado has been installed properly by running:
   ```bash
   vivado
  This command should launch the Vivado GUI, confirming that the installation was successful.

  In the same repository, I will make reports in PDF format. When you click on the text below, it will navigate to the PDF I have posted in that repository:

### Step 15: Create a Project

1. **Open Command Prompt (CMD)**  
   - Launch the CMD terminal.  
   - Navigate to the appropriate directory.  
   - Run the following command:  
     ```bash
     vivado -source create_project_arty_a7_100t.tcl
     ```

This will open the Vivado project.

### Step 16: Add Source Files

1. Go to the **"Source"** tab.
2. Click on the **"+" (Add Source)** button.
3. Proceed to the next window and add the Verilog files (`.v` files) from the **hardware folder** located in the **board folder**.
4. Click **Finish** to complete adding the files.


### Step 17: Run Synthesis

1. Click **Run Synthesis**.
2. Wait for the synthesis process to complete successfully.


### Step 18: Run Implementation

1. After successful synthesis, click **Run Implementation**.
2. Wait for the implementation process to complete.
3. Next, go to **Netlist** and select **rvsteel_mcu_instance**, then click on **Schematic**.


### Step 19: View the Device Output

1. After both synthesis and implementation are complete, you can view the device output.
2. Navigate to the **Netlist** tab.
3. Follow the directions to click on **Schematic**.


### Step 20: View the Block Diagram

1. Double-click on the **Block Diagram** in the project window.
2. The schematic view of the **RISC-V architecture** will appear.
   - You can view the [Schematic Report](https://github.com/rameshmangali/RISCV/blob/main/Schematic%20Analysis%20Report.pdf) for more details.

### Step 21: View Reports

1. At the lower panel, go to the **Reports** section.
2. Here, you can observe the reports for both the **Synthesis** and **Implementation** processes.

   - You can view the [Synthesis Report](https://github.com/rameshmangali/RISCV/blob/main/Final_Synthesis_Report.pdf) for more details.

   - You can view the [Implementation Report](https://github.com/rameshmangali/RISCV/blob/main/Final_Implementation_Report.pdf) for more details.


### Step 22: Power Analysis

1. Click on the **Power Report** to check the power consumption of both the synthesis and implementation phases.

   - You can view the [Power synthesis Report](https://github.com/rameshmangali/RISCV/blob/main/Power%20Analysis_synthesis.pdf) for more details.

   - You can view the [Power implementation Report](https://github.com/rameshmangali/RISCV/blob/main/Power%20Analysis_implementation.pdf) for more details.


### Step 23: Timing Analysis

1. To generate a timing report, run the following command in the Vivado terminal:
   ```bash
      report_timing -max_paths 1 -nworst 1 -delay_type max -sort_by slack
   ```
   - You can view the [Timing Report](https://github.com/rameshmangali/RISCV/blob/main/timing_report_content.pdf) for more details.

---
## Installing RISCV Steel on Ubuntu by using spike simulator

### Table of Contents
1. [Install WSL and Ubuntu](#1-install-wsl-and-ubuntu)
2. [Download RISC-V Tarball](#2-download-risc-v-tarball)
3. [Access Ubuntu Terminal](#3-access-ubuntu-terminal)
4. [Navigate to the Downloaded File](#4-navigate-to-the-downloaded-file)
5. [Prepare the RISC-V File](#5-prepare-the-risc-v-file)
6. [Extract the RISC-V File](#6-extract-the-risc-v-file)
7. [Verify Extraction](#7-verify-extraction)
8. [Update and Upgrade Packages](#8-update-and-upgrade-packages)
9. [Install Required Libraries](#9-install-required-libraries)
10. [Update PATH](#10-update-path)
11. [Verify RISC-V GCC Installation](#11-verify-risc-v-gcc-installation)
12. [Clone RISC-V ISA Simulator](#12-clone-risc-v-isa-simulator)
13. [Install Additional Packages](#13-install-additional-packages)
14. [Clone RISC-V Proxy Kernel](#14-clone-risc-v-proxy-kernel)
15. [Set Up RISC-V Proxy Kernel Build](#15-set-up-risc-v-proxy-kernel-build)
16. [Install Proxy Kernel](#16-install-proxy-kernel)
17. [Create and Compile Hello World Program](#17-create-and-compile-hello-world-program)
18. [Compile and Run Hello World](#18-compile-and-run-hello-world)
19. [Generate Assembly Code](#19-generate-assembly-code)
20. [Run with Spike in Simulation Mode](#20-run-with-spike-in-simulation-mode)

### Step 1: Install WSL and Ubuntu

   1. **Check Available Distributions**:
   
      ```bash
      wsl --list --online
   2. **Install Ubuntu 20.04**:
      ```bash
      wsl --install Ubuntu-20.04
      ```
   3. **Set Up User**:
      - create a username and password and confirm it (password will be invisible).
 
### Step 2: Download RISC-V Tarball
   - [**Download**](https://github.com/riscv-collab/riscv-gnu-toolchain/releases/download/2024.09.03/riscv64-elf-ubuntu-20.04-gcc-nightly-2024.09.03-nightly.tar.gz) the zip file from the provided link.

### Step 3: Access Ubuntu Terminal
   1. **Open windows** and search for **Ubuntu 20.04.6** in the search box.

### Step 4: Navigate to the Downloaded File
   1. **Change Directory**:
      ```bash
      cd ../..
      cd mnt/d
      ls
      ```

### Step 5: Prepare the RISC-V File
   1. **Rename the tar.gz File**:
      - Rename the downloaded file to `riscv.tar.gz`.
   2. **Copy the File**:
      ```bash
      cp -r riscv.tar.gz /home/your_username
      ```
      *Replace `your_username` with your actual username.*
   3. **Navigate to root Directory**:
      ```bash
      cd ~
      ls
      ```
### Step 6: Extract the RISC-V File
   ```bash
   tar -xvzf riscv.tar.gz
   ```
### Step 7: Verify Extraction
   - Use the commands
     ```bash
     ls
     ls riscv/bin
     ```
     
### Step 8: Update and Upgrade Packages
   ```bash
   sudo apt-get update
   sudo apt-get upgrade
   ```
### Step 9: Install Required Libraries
   ```bash
   sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat1-dev ninja-build git cmake libglib2.0-dev libslirp-dev
   ```
### Step 10: Update PATH
   1. **Check Present Working Directory**:
      ```bash
      pwd
      ```
   2. **Edit .bashrc**:
      ```bash
      nano ~/.bashrc
      ```
      - Add the following line at the end of the nano window:
      ```bash
      export PATH="/home/your_username/riscv/bin:$PATH"
      ```
      - Save with `Ctrl + S` and exit with `Ctrl + X`.
### Step 11: Verify RISC-V GCC Installation
   ```bash
   riscv64-unknown-elf-gcc -v
   which riscv64-unknown-elf-gcc
   echo $PATH
   source ~/.bashrc
   which riscv64-unknown-elf-gcc
   ```
### Step 12: Clone RISC-V ISA Simulator
   ```bash
   git clone https://github.com/riscv-software-src/riscv-isa-sim.git
   cd riscv-isa-sim
   ```
### Step 13: Install Additional Packages
   ```bash
   sudo apt-get install device-tree-compiler libboost-regex-dev libboost-system-dev
   mkdir build
   cd build
   ../configure --prefix=/home/your_username/riscv
   make
   sudo make install
   ```
   - **Run Spike**:
   ```bash
   spike
   ```
### Step 14: Clone RISC-V Proxy Kernel
   ```bash
   cd ../..
   git clone https://github.com/riscv-software-src/riscv-pk.git
   cd riscv-pk
   ```
### Step 15: Set Up RISC-V Proxy Kernel Build
   ```bash
   sudo mkdir build
   cd build
   sudo -i
   cd /home/your_username/riscv-pk/build
   make clean
   ```
### Step 16: Install Proxy Kernel
   1. **Run the Following Commands**:
   ```bash
   which riscv64-unknown-elf-gcc
   ls /home/your_username/riscv/bin
   export PATH=/home/your_username/riscv/bin:$PATH
   which riscv64-unknown-elf-gcc
   ../configure --prefix=/home/your_username/riscv --host=riscv64-unknown-elf --with-arch=rv64gc_zifencei
   make
   make install
   ```
### Step 17: Create and Compile Hello World Program
   1. **Navigate Up**:
   ```bash
   cd ../..
   ```
   2. **Create Hello World File**:
   ```bash
   nano hello.c
   ```
   - Add the following code:
      ```c
      #include <stdio.h>
      int main() {
          printf("Hello, World!");
          return 0;
      }
      ```
   - Save with `Ctrl + S` and exit with `Ctrl + X`.
### Step 18: Compile and Run Hello World
   ```bash
   riscv64-unknown-elf-gcc hello.c
   spike pk a.out
   ```
   - **Output**: "Hello, World!" should be displayed.
### Step 19: Generate Assembly Code
   ```bash
   riscv64-unknown-elf-gcc hello.c -S
   cat hello.s
   ```
   - This displays the RISC-V assembly code of `hello.c`.
### Step 20: Run with Spike in Simulation Mode
   ```bash
   spike pk -s a.out
   ```
- This command runs the program in simulation mode, providing additional debugging output.
