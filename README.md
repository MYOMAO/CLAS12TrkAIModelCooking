# CLAS12TrkAIModelCooking

## Overview

`CLAS12TrkAIModelCooking` is a repository for the **AI-based tracking model validation of the CLAS12 Forward Tracker**, developed by **Tongtong Cao**.

This repository contains the configuration files, run lists, and production information required to validate the new AI tracking model for the following CLAS12 data-taking periods:

- RG-A
- RG-B
- RG-C
- RG-D
- RG-E
- RG-F
- RG-K
- RG-L
- RG-M

The validation campaign includes:

- **High Luminosity Runs**
- **Gold Runs**

The reconstructed output is produced in the CLAS12 HIPO reconstruction format:

```
dchv
```

---

## Repository Structure

```
CLAS12TrkAIModelCooking/
│
├── YamlFiles/
│   ├── rga*.yaml
│   ├── rgb*.yaml
│   ├── rgc*.yaml
│   └── ...
│
├── RunLists.png
│
└── README.md
```

---

## Run Lists

The complete list of validated runs is available here:

[RunLists.png](https://github.com/MYOMAO/CLAS12TrkAIModelCooking/blob/main/RunLists.png)

The run lists include all production runs used in the AI tracking validation campaign.

---

## YAML Configuration Files

Orginally, the yaml files are obtained from following link:

```
https://github.com/JeffersonLab/clas12-config/tree/main/wok
```

All YAML configuration files for different run groups and data-taking periods are stored in:

```
YamlFiles/
```

Each YAML file is named with the corresponding run group at the beginning of the filename.

Examples:

```
YamlFiles/RG-A_*.yaml
YamlFiles/RG-B_*.yaml
YamlFiles/RG-C_*.yaml
```

These YAML files contain the run-dependent configuration required for CLAS12 reconstruction and AI tracking validation.

---

# Software Environment

The CLAS12 reconstruction production was performed using the **CLAS12 coatjava framework**.

## coatjava Version and Code Configuration

### Runs with Run Number < 18000

The software code is based on the:

```
git branch: dc1_dev6
```

Commit:

```
0f98fdb3b31a4bab19e90db68e88b4a0d0df11ea
```

Repository:

https://github.com/JeffersonLab/coatjava/commit/0f98fdb3b31a4bab19e90db68e88b4a0d0df11ea


### Runs with Run Number > 18000

The software code is based on the:

```
git branch: development
```

Commit:

```
34b31de82e45bb66ae9812663680eef9f5206f65
```

Repository:

https://github.com/JeffersonLab/coatjava/commit/34b31de82e45bb66ae9812663680eef9f5206f65

---

## Compiled Software Locations

The compiled coatjava/software builds are available on the Jefferson Lab ifarm cluster.

### Run Number < 18000

```
/w/hallb-scshelf2102/hps/zshi/CLAS12Work/DataCooking/NewType/
```

### Run Number > 18000

```
/w/hallb-scshelf2102/hps/zshi/CLAS12Work/DataCooking/NewAbove18000/
```

---

# Production Output

The reconstructed production files are stored on JLab ifarm:

```
/volatile/clas12/users/zshi/data_prod/AITrackingCalib/
```

Output format:

```
HIPO (dchv)
```

---

# Data Cooking Workflow

The data cooking workflow uses the **CLARA framework** on the `clara2501` node.

Standard production configuration:

- **15 threads per job**
- **10 EVIO input files per job**
- Output converted to reconstructed HIPO format

Example command for RG-C Run 17800:

```bash
/w/hallb-scshelf2102/hps/zshi/CLAS12Work/DataCooking/NewTest/coatjava/coatjava/bin/run-clara \
-y rgcSpring23Pass1.yaml \
-t 15 \
-c /w/hallb-scshelf2102/hps/zshi/CLAS12Work/DataCooking/NewTest/clara/install \
/cache/clas12/rg-c/data/clas_017800/clas_017800.evio.0070*
```

---

# Reproducing Production

To reproduce the reconstruction production:

1. Select the appropriate YAML configuration file:

```bash
YamlFiles/
```

2. Select the correct coatjava version based on the run number.

3. Run the CLARA reconstruction workflow on the JLab ifarm cluster.

4. Retrieve the reconstructed HIPO output from:

```bash
/volatile/clas12/users/zshi/data_prod/AITrackingCalib/
```

---

# Run Coverage

This validation campaign covers the following CLAS12 run groups:

| Run Group | Included |
|----------|----------|
| RG-A | ✓ |
| RG-B | ✓ |
| RG-C | ✓ |
| RG-D | ✓ |
| RG-E | ✓ |
| RG-F | ✓ |
| RG-K | ✓ |
| RG-L | ✓ |
| RG-M | ✓ |

---

# Contact

For questions, issues, or additional information, please contact:

**Zhaozhong Shi**

Jefferson Lab

Email:

- zshi@jlab.org
- zshi1@lamar.edu

---

# Acknowledgement

This work is part of the **CLAS12 AI tracking model validation effort** and uses computing resources provided by **Jefferson Lab**.
