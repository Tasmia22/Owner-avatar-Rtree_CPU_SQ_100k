# DPU-Based Project

This project implements a **Processing-In-Memory (PIM)** solution using **UPMEM DPUs**. The code consists of a **host-side** and a **DPU-side**, where the host program orchestrates data transfer and computation across DPUs.

## Directory Structure

```
.
├── dpu/            # DPU-side source code
├── host/           # Host-side source code
├── common/         # Common header files
├── build/          # Build directory (created during compilation)
├── Makefile        # Makefile for compilation
└── README.md       # This readme file
```

## Prerequisites

Before running this project, ensure you have the following installed:

- **UPMEM SDK** (including `dpu-upmem-dpurte-clang` for DPU compilation)
- **C Compiler (GCC/Clang)**
- **Linux Environment**

## Compilation & Execution

### 1. Build the Project
Run the following command to compile both the host and DPU programs:
```sh
make
```
This will generate the following files in the `build/` directory:
- `build/host`  → Host executable
- `build/dpu`   → DPU binary

### 2. Run the Program
After successful compilation, execute the host program using:
```sh
make test
```
Or run the host program manually:
```sh
./build/host
```

### 3. Clean the Build
To remove compiled files and reset the build, run:
```sh
make clean
```

## Configuration
The following parameters can be adjusted in the `Makefile`:

- `NR_TASKLETS` → Number of tasklets per DPU (default: 11)
- `NR_DPUS` → Number of DPUs used (default: 16)

To modify these, edit the `Makefile` or override them during compilation:
```sh
make NR_TASKLETS=8 NR_DPUS=32
```

## Troubleshooting
- Ensure **UPMEM SDK** is installed and correctly configured.
- Check if the DPUs are correctly detected using:
  ```sh
  dpuinfo
  ```
- Verify that the `build/` directory exists and contains compiled files.


