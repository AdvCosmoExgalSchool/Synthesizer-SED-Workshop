# Synthesizer-SED-Workshop

Welcome to this synthetic observations and SED fitting workshop! This repository will guide you through:

- Inferring the physical properties of galaxies using [Bagpipes](https://github.com/ACCarnall/bagpipes).
- Forward modelling particle based simulation outputs using [Synthesizer](https://github.com/flaresimulations/synthesizer).
- Testing SED fitting performance using parametric galaxy models.

Each of these sections are contained within their own notebook, numbered one through three and example solutions are collated in the fourth. The results can vary significantly depending on different factors, so make sure to compare results at each stage with your colleagues to get a handle on this variability. Please see the section below for a list of required software and installation instructions.

## Software

Before doing anything make sure to have an up to date installation of both [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and Python. The notebooks were written using version 3.10 which can easily be selected when using a version manager like [pyenv](https://github.com/pyenv/pyenv). Once you have these, you can then clone this repository by running:
```
git clone https://github.com/AdvCosmoExgalSchool/Synthesizer-SED-Workshop
```
in the desired directory. Now we should create a virtual environment which will contain all the software necessary for running the notebooks, without interfering with any of your previous installations. You can create a virtual environment using:
```
python -m venv venv_name
```
which will create a virtual environment named `venv_name`. Activate the environment by running:
```
source venv_name/bin/activate
```
and you are free to start installing the software listed below. 

You will first need to install [Synthesizer](https://github.com/flaresimulations/synthesizer) by following the instructions on the GitHub page. This should install most of the required Python packages, but you can install those remaining by running:
```
 pip install bagpipes ipykernel
```
The notebooks assume you are using the "MultiNest" sampler for running Bagpipes for which you can find installation instructions [here](https://bagpipes.readthedocs.io/en/latest/index.html). These don't always work, but if you have trouble it should be fine to use the "nautilus" sampler instead.

## Set Up

Before we can run the notebooks we need to ensure Synthesizer and Bagpipes have everything they need to work as we want them to. For Synthesizer we need to download the SPS model "test_grid" using:
```
synthesizer-download --test-grids --destination /path/to/destination
```
where `/path/to/destination` should point to a `grids` directory. You will also need the [BC03](https://www.dropbox.com/scl/fi/25mw3gk28k7jkae7tkbug/bc03_chabrier03-0.1-100_cloudy-c17.03.hdf5?rlkey=28uqjqrurtywfyj03yqegr0s9&dl=0) and [BPASS](https://www.dropbox.com/scl/fo/3n8v3o4m85b0t8fl8pm0n/h?dl=0&e=1&preview=bpass-2.2.1-bin_chabrier03-0.1%2C300.0_cloudy-c23.01-sps.hdf5&rlkey=9x4cijjnmvw5m6plnyovywuva) grids which can be downloaded directly and placed in the same directory.

Now for Bagpipes, enter your virtual environment folder, find `config.py` in `lib/python{version}/site-packages/bagpipes` and change the maximum redshift to 20. Make sure to save the file! In the same Bagpipes directory, enter `models/grids` and delete `d_igm_grid_inoue14.fits` if it exists.

Finally, move the files in the `filters` directory within this repository to `lib/python{version}/site-packages/bagpipes/filters` in your virtual environment.

You should now be ready to begin the workshop!