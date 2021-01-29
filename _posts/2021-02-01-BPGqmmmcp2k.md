---
title: 'Best Practice Guide for Biomolecular QM/MM simulations with CP2K'
date: 2021-02-01
permalink: /posts/2021/02/BPGqmmmcp2k/
tags:
  - cool posts
  - qmmm
  - CP2K
  - BPG
---


A Best Practice Guide for Biomolecular QM/MM simulations with CP2K for beginners
----------

As part of my work in the BioExcel-2 project at the EPCC, I co-wrote a best practice guide on how to perform QM/MM simulations of biomolecules using CP2K. We provided an overview of the main steps in setting up and running a QM/MM simulation in CP2K. We cover steps starting from preparing your system to running a production QM/MM run. This BPG is designed to be read from the point of view of beginner users. 

Here is the link: 
[Best Practice Guide for Biomolecular QM/MM simulations with CP2K](https://docs.bioexcel.eu/qmmm_bpg/en/main/)

**Authors:** [Dr Holly Judge](https://www.epcc.ed.ac.uk/about/staff/holly-judge), **Dr Salome Llabres** and [Dr Arno Proeme](https://www.epcc.ed.ac.uk/about/staff/dr-arno-proeme)


A set of tools to set up simulations in QM/MM using CP2K
----------

Also, I developed a set of python3 tools to deal with the set up of CP2K simulations. I hope you find them useful!

Here you have the link to the [Bioexcel repository](https://github.com/bioexcel/CP2K_qmmm_input_preparation_scripts)

This repository contains the following scripts:

**cp2krestart2gromacs.py**

This script converts CP2K restart file to GROMACS files. It follows these steps:

1 - Reads CP2K restart file.

2 - Generates a AMBER restart file.

3 - Convert AMBER (.prmtop and .inpcrd) to GROMACS format (.top and .gro) via parmed. 

4 - Rewrites GROMACS coordinates to include velocities. 

Requirements:
Parmed. 

It requires the CP2K restart file and a basename to name the gromacs files. 

It outputs these files:

   AMBER restart file:                  basename.inpcrd 
   GROMACS topology:                    basename.top 
   GROMACS coordinates:                 basename.gro 
   GROMACS coordinates + velocities:    basename.vel.gro 

```bash
$ python3 cp2krestart2gromacs.py -h 

Usage: cp2krestart2gromacs [options] infile outfile

Converts CP2K restart file to GROMACS format (including velocities).

positional arguments:
  infile          CP2K restart file
  outfile         basename for gromacs files

optional arguments:
  -h, --help  show this help message and exit
  -v          show program's version number and exit
```

