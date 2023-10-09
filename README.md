
# Navigating to a greener Europe with 24/7 hourly carbon-free electricity procurement (working title)

abstract

### How to reproduce results from the paper
...

## Data requirements

The folder `data` should contain PyPSA networks exported from [PyPSA-Eur-Sec](https://github.com/PyPSA/pypsa-eur-sec) built with `myopic` setting to get brownfield networks for 2025/2030. To get started, you can use sample networks from the `input` folder.

Parallel to the repository you should also clone the [technology-data](https://github.com/PyPSA/technology-data) repository.

### Software 

The code is known to work with PyPSA 0.18.1, pandas 1.2.4, numpy 1.19.0, vresutils 0.3.1 and gurobi 9.1.2.

The complete list of package requirements is in the [envs/environment.yml](envs/environment.yml) file. The environment can be installed and activated using:

```
.../247-cfe % conda env create -f envs/environment.yml
.../247-cfe % conda activate 247-cfe
```

If you have troubles with a slow [conda](https://docs.conda.io/en/latest/) installation, we recommend to install [mamba](https://mamba.readthedocs.io/en/latest/):

```
conda install -c conda-forge mamba
```

and then install the environment with a fast drop-in replacement via

```
mamba env create -f envs/environment.yml
```

## License

Copyright 2022 Tom Brown, Iegor Riepin.

This code is licensed under the open source MIT License.
