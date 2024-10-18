# Installation Guide for Linux, Ubuntu, Toolchain, and Vivado Simulator

This README provides a step-by-step guide to install the required software: Linux (via WSL for Windows), Ubuntu, the RISC-V GNU Toolchain, and Vivado Simulator.

## Table of Contents

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

## Pre-requisites

Before starting, ensure you have:
- **GitBash** (for Windows users)
- **Windows Subsystem for Linux (WSL)**

---

## Step 1: Clone the Repository

1. Open GitBash or terminal.
2. Clone the RISC-V Steel repository:
   ```bash
   git clone https://github.com/riscv-steel/riscv-steel

---

## Step 2: Clone the Toolchain
1. In the terminal (GitBash or Linux), clone the RISC-V GNU Toolchain by running the following command:
    ```bash
    git clone https://github.com/riscv/riscv-gnu-toolchain
    ```
2. This will clone the RISC-V GNU Toolchain repository to your local machine.

---

## Step 3: Install Linux via WSL
1. For Windows users, open PowerShell with Administrator privileges.
2. Run the following command to install Linux via Windows Subsystem for Linux (WSL):
    ```bash
    wsl --install
    ```
3. After WSL is installed, Ubuntu will automatically be installed.
4. Close PowerShell and restart your PC to finalize the installation.

---

## Step 4: Initial Ubuntu Setup
1. Open the newly installed Ubuntu application.
2. When prompted, create a unique username and password. The password will not be visible as you type.
3. Confirm your password by retyping it.

---

## Step 5: Update Ubuntu
1. Once you're inside the Ubuntu terminal, update your system by running the following commands:
    ```bash
    sudo apt-get update
    sudo apt-get upgrade
    ```
   This will ensure that you have the latest versions of all necessary packages.

---

## Step 6: Install Toolchain Dependencies
1. To install the necessary dependencies for building the toolchain, run the following command in Ubuntu:
    ```bash
    sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev
    ```
   This will install essential development tools and libraries required to build the RISC-V toolchain.

---

## Step 7: Clone Repositories in Ubuntu
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

---

## Step 8: Navigate to Toolchain Directory
1. Navigate to the `riscv-gnu-toolchain` directory by using the following command:
    ```bash
    cd riscv-gnu-toolchain/
    ```
2. You should now see the contents of the `riscv-gnu-toolchain` directory.

---

## Step 9: Configure Toolchain
1. Run the configuration command to prepare the toolchain for building:
    ```bash
    ./configure --prefix=/opt/riscv --with-arch=rv32izicsr --with-abi=ilp32
    ```
   The `--with-arch` and `--with-abi` options are specific to the architecture and ABI of your system. Make sure these match your requirements.

---

## Step 10: Build Toolchain
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

---

## Step 11: Run Hello World Example
1. Navigate to the hello_world example directory:
   ```bash
   cd ./riscv-steel/examples/hello_world/software
2. Once inside, compile the example program by running:
   ```bash
   make
3. If any errors occur during this process, follow the troubleshooting guide provided in the RISC-V Steel documentation or visit the repository for further assistance.

---

## Step 12: Download and Install Vivado
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

---

## Step 13: Extract the Vivado Installation Files
1. In the Ubuntu terminal, extract the contents of the `.tar.gz` file by running the following command:
   ```bash
   tar -xvzf Xilinx_Vivado_SDK_2018.3_1207_2324.tar.gz

2. The -xvzf flags ensure the file is extracted, and you can see the extraction process in real-time.
3. Once the extraction is complete, list the contents of the directory using:
   ```bash
   ls
 You should see the extracted files and folders, including the xsetup file.

 ---

 ## Step 14: Install Vivado Using xsetup
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

---

## Step 15: Create a Project

1. **Open Command Prompt (CMD)**  
   - Launch the CMD terminal.  
   - Navigate to the appropriate directory.  
   - Run the following command:  
     ```bash
     vivado -source create_project_arty_a7_100t.tcl
     ```

This will open the Vivado project.

---

## Step 16: Add Source Files

1. Go to the **"Source"** tab.
2. Click on the **"+" (Add Source)** button.
3. Proceed to the next window and add the Verilog files (`.v` files) from the **hardware folder** located in the **board folder**.
4. Click **Finish** to complete adding the files.

---

## Step 17: Run Synthesis

1. Click **Run Synthesis**.
2. Wait for the synthesis process to complete successfully.

---

## Step 18: Run Implementation

1. After successful synthesis, click **Run Implementation**.
2. Wait for the implementation process to complete.
3. Next, go to **Netlist** and select **rvsteel_mcu_instance**, then click on **Schematic**.

---

## Step 19: View the Device Output

1. After both synthesis and implementation are complete, you can view the device output.
2. Navigate to the **Netlist** tab.
3. Follow the directions to click on **Schematic**.

---

## Step 20: View the Block Diagram

1. Double-click on the **Block Diagram** in the project window.
2. The schematic view of the **RISC-V architecture** will appear.
You can view the [Schematic Report](https://github.com/rameshmangali/RISCV/blob/main/Schematic%20Analysis%20Report.pdf) for more details.
---

## Step 21: View Reports

1. At the lower panel, go to the **Reports** section.
2. Here, you can observe the reports for both the **Synthesis** and **Implementation** processes.

You can view the [Power Synthesis Report](https://github.com/rameshmangali/RISCV/blob/main/Power%20Analysis_implementation.pdf) for more details.

You can view the [Power Implementation Report](https://github.com/rameshmangali/RISCV/blob/main/Power%20Analysis_synthesis.pdf) for more details.

---

## Step 22: Power Analysis

1. Click on the **Power Report** to check the power consumption of both the synthesis and implementation phases.

You can view the [Power Report](https://github.com/rameshmangali/RISCV/blob/main/Power%20Analysis_synthesis.pdf) for more details.

---

## Step 23: Timing Analysis

1. To generate a timing report, run the following command in the Vivado terminal:
   ```bash
   report_timing -max_paths 1 -nworst 1 -delay_type max -sort_by slack
You can view the [Timing Report](https://github.com/rameshmangali/RISCV/blob/main/timing_report_content.pdf) for more details.
