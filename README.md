# Analyzing coherent structures in unsteady flows by means of dynamic mode decomposition (DMD)

This repository accompanies the training session on DMD analysis of unsteady flows given at the [17th OpenFOAM workshop](https://openfoamworkshop.org/) in Cambridge (2022).

## Dependencies

### OpenFOAM

Without modification, the simulations will only work with **OpenFOAM-v2206**. You can use the [pre-compiled binaries](https://develop.openfoam.com/Development/openfoam/-/wikis/precompiled) or the provided Singularity container. To build the container, run:

```
sudo singularity build of2206.sif docker://andreweiner/of_pytorch:of2206-py1.11.0-cpu
```
When working with the container, use the *Allrun.singularity* instead of the *Allrun* scripts and make sure to set the image location in each script.

### flowTorch

[flowTorch](https://github.com/FlowModelingControl/flowtorch) is a Python library for the analysis and modeling of fluid flows. We use flowTorch to access OpenFOAM data in Python and to perform modal analysis (DMD, proper orthogonal decomposition). For this training, you need the latest development version, which can be conveniently installed via *pip* and *git*:

```
pip3 install git+https://github.com/FlowModelingControl/flowtorch.git@aweiner
```

### Data

The simulations require 40 MPI ranks and run for approximately 2 days in total. For the preliminary flow analysis and the DMD analysis in flowTorch, you can also download the following archives:
- probe and force data, *fullCase*, ~30MB ([link](https://cloudstorage.tu-braunschweig.de/getlink/fiYCtHTABXFekyyc937Cwp91/preliminary_post.tar.gz))
- sample planes, *fullCaseDMD*, ~1.2GB ([link](https://cloudstorage.tu-braunschweig.de/getlink/fi5h5DdjB2hj83u346B3CCxS/surface.tar.gz))


## Training material overview

- training slides, [link](https://andreweiner.github.io/reveal.js/ofw2022_dmd_training.html#/)
- modified *surfaceMountedCube* tutorial ([original setup](https://www.openfoam.com/documentation/guides/latest/doc/verification-validation-turbulent-surface-mounted-cube.html))
- preliminary flow analysis, [notebook](preliminary_flow_analysis.ipynb)
- DMD analysis with flowTorch, [notebook](dmd_flowtorch.ipynb)

## How to run the simulations

The current setup requires **40** MPI ranks. The suggested workflow to execute the simulations is as follows:

```
# we are at the top-level of this repository
mkdir run
cp -r surfaceMountedCube run/
cd run/surfaceMountedCube
./Allrun
# or with the container
./Allrun.singularity
```

## Getting in touch

For questions, corrections, etc. after the workshop, open a new issue in this repository.
