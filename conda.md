# 🚀 Conda
### Create a new environment
    conda create --name myenv python=3.11
### Activate it
    conda activate myenv
### Install a package
    conda install numpy
### List all environments
    conda env list
### Export environment
    conda env export > environment.yml
### Create env from file
    conda env create -f environment.yml
