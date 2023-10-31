
# Code for the paper "On the means, costs, and system-level impacts of 24/7 carbon-free energy procurement"

This repository contains the code to reproduce the complete workflow behind the manuscript.

### Abstract

> A growing number of public and private energy buyers are interested in 24/7 carbon-free energy (CFE) procurement, which means that every kilowatt-hour of electricity consumption is met by carbon-free sources at all times.
> It has the potential to overcome the limitations of established procurement schemes, such as the temporal mismatch between clean electricity supply and buyers' demand that is inherent to "volumetric" matching.
> Yet it is unclear how 24/7 CFE procurement affects the rest of the power system, and whether this effect is consistent across regional contexts and different levels of system cleanness.
> We use a mathematical model to systematically examine different designs, optimal procurement strategies, costs, and impacts of the 24/7 CFE matching, both for participating buyers and for regions where voluntary procurement occurs.
> We examine mechanisms driving system-level emissions reduction and how they vary across regions and over time.
> Our results indicate that clean energy procurement commitments have consistent beneficial effects on participants and the electricity system.
> Even as grids become cleaner over time, the hourly matching strategy contributes significantly to system-level emissions reduction.
> In addition, voluntary commitments to 24/7 CFE have a further transformative effect on electricity systems through accelerated innovation and early deployment of advanced energy technologies.

### How to reproduce results from the paper?

1. Clone the repository:

```
git clone git@github.com:Irieo/247-procurement-paper.git
```

2. Install the necessary dependencies using `environment.yml` file. The following commands will do the job:

```
conda env create -f envs/environment.yml
conda activate 247-cfe
```
3. To run all the scenarios from the paper, run the [snakemake](https://snakemake.readthedocs.io/en/stable/) worflow:

```
snakemake -call
```

NB This call requires a high-performance computing environment.

It is possible to run a smaller version of the model by adjusting the settings in `config.yaml`. For example, changing the config setting `area` from "EU" to "regions" reduces the regional coverage of the model, making the size of the problem feasible to solve on a private laptop with 8GB RAM.

When the workflow is complete, the results will be stored in `results` directory. The directory will contain solved networks, plots, summary csvs and logs.

4. At this point, you can also compile the LaTeX project `/manuscript/manuscript.tex` to reproduce the paper .pdf file.

### Data requirements

The workflow is based on PyPSA networks exported from [PyPSA-Eur](https://github.com/PyPSA/pypsa-eur) built with `myopic` setting to get brownfield networks for 2025/2030. By default, the workflow uses already compiled networks located in the `input` folder.

Parallel to the repository you should also clone the [technology-data](https://github.com/PyPSA/technology-data) repository:

```
git clone git@github.com:PyPSA/technology-data.git
```

### Software requirements

The code is known to work with PyPSA 0.25.2, pandas 1.5.3, numpy 1.24.2, vresutils 0.3.1 and gurobi 10.0.1. The complete list of dependencies is in the [envs/environment.yml](envs/environment.yml) file.

If you have troubles with a slow [conda](https://docs.conda.io/en/latest/) installation, we recommend to install [mamba](https://mamba.readthedocs.io/en/latest/):

```
conda install -c conda-forge mamba
```

and then install the environment with a fast drop-in replacement via

```
mamba env create -f envs/environment.yml
```

## License

Different licenses apply to different parts of the repository. See [specifications here](.reuse/dep5).
