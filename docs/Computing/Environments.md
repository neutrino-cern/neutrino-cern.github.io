# Environments

## Using LCG Views 
The [LCG Releases](https://ep-dep-sft.web.cern.ch/document/lcg-releases) provide an extensive collection of regularly updated software. The list of available software can be seen [here](https://lcginfo.cern.ch/). 

After selecting an appropriate view we can load by sourcing a `setup.sh` file from `cvmfs` (this would be available on any `lxplus` machine):
```bash
source /cvmfs/sft.cern.ch/lcg/views/<release>/<platform>/setup.sh
```

## Combining a Virtual Python Env with LGC Views
If we want to customize the software packages provided by the LCG view, we can create a virtual environment on top of the view, thus only installing extra packages, or upgrading existing ones, without having to build a complete environment from scratch. 

we begin by sourcing the LCG view as above:
```bash
source /cvmfs/sft.cern.ch/lcg/views/<release>/<platform>/setup.sh
```
Then we can create a virtual environment and activate it 

```bash
python3 -m venv --system-site-packages myenv
source myenv/bin/activate   # activate the environment
```

Finally, if we need to upgrade a certain package we can use `pip`:

```bash
pip install --upgrade tensorflow=newer.version
```

## Using `conda`
!!! warning
    We highly recommend that you used a virtual environment on top of LCG. However it is possible to set up a complete environment from scratch using conda.

To set up a conda environment we suggest that your first increase your AFS quota, by following [this](https://resources.web.cern.ch/resources/Help/?kbid=067040) guide.

If you still require more space. i.e `/afs/cern.ch/user/<initial>/<username>` is filling up, you can point `conda` to the work directory `/afs/cern.ch/work/<initial>/<username>`. To do this we need to edit the `~/.condarc` file.

```bash 
pkgs_dirs: 
  - /afs/cern.ch/work/<initial>/<username>/public/pkgs
envs_dirs:
  - /afs/cern.ch/work/<initial>/<username>/public/envs
```
