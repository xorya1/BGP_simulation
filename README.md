# README - Simulation BGP (ENST Multi-Homed Network)

## Introduction

This README file provides instructions for running the BGP simulation for the multi-homed network example of the ENST (AS1712). Before starting, ensure you understand the basic concepts of BGP and Autonomous Systems (AS). Please refer to the accompanying PDF for detailed explanations and questions to consider during the simulation.

## Objectives

1. Understand the BGP decision-making process.
2. Analyze traceroute outputs and explain the AS path.
3. Simulate the configuration of ENST (AS1712) with C-BGP.
4. Explore BGP message exchanges between ASs.

## Prerequisites

Before starting this TP, ensure you can answer the following questions:
- What is an AS (Autonomous System)?
- What is BGP?
- What is a BGP router?
- What information is exchanged by two BGP routers?

*Note: Please do not include answers to these questions in your report.*

## Getting Started

### 1. Follow the PDF

Refer to the PDF provided with this repository for step-by-step instructions on how to conduct the BGP simulation. This document outlines the necessary configurations and commands to execute.

### 2. Running the Simulation Files

To deploy the topology and start the simulation:

- If you are using Windows:
  - Download and extract the C-BGP tool from [here](http://deptinfo.cnam.fr/~seccis/TPBGP/index-en.htm).
  - Navigate to the extracted folder and run `run-cbgp.bat` to start C-BGP.
  
- If you are using Linux:
  - Connect to the server via SSH (ask your professor for the details).
  - Open your terminal and type the command: 
    ```bash
    cbgp -i
    ```
    *The `-i` option runs the program in interactive mode.*

### 3. Load the Topology

Once C-BGP is running, load the ENST topology with the following command:
```bash
cbgp> include "enst.cli"
```
This command will set up the necessary configuration for the routers in the simulation.

### 4. Exploring Commands

You can use various commands in C-BGP to check the routing tables and BGP neighbors. Here are some useful commands:

- To show BGP neighbors:
  ```bash
  bgp router x.x.x.x show peers
  ```

- To view the BGP routing table:
  ```bash
  bgp router x.x.x.x show rib *
  ```

*Make sure to replace `x.x.x.x` with the appropriate router IP address.*

## Important Notes

- Every time you edit the configuration file (e.g., `.cli`), you must restart the simulator and include the new version of the file to apply the changes.
- Use a text editor that maintains UNIX EOF coding (e.g., Notepad++ or PSPad) for editing configuration files.
- Follow the guidelines for routing decisions provided in the PDF.

## Simulation Cases

- **Failure Simulation**: You can simulate a failure between AS1712 and AS12322 by running:
  ```bash
  cbg> bgp router 137.194.1.1 peer 88.160.1.1 down
  ```
  Then execute the simulation using:
  ```bash
  sim run
  ```

### Questions to Explore

Refer to the PDF for specific questions that will guide your analysis and help you understand the simulation's results, including traceroute outputs and routing table changes.

## References

- [C-BGP Official Documentation](https://c-bgp.sourceforge.net)
- [C-BGP Download](https://c-bgp.sourceforge.net/downloads/cbgp-doc.pdf)
