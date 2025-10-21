### Software and Tools

#### To create a local environment for this course

* install miniconda from https://www.anaconda.com/download/success 
* (Optional) run 3 command lines that appear if error occors when you try the first command below
* create environment. You can use other environment name in place of mlpi

```console
conda install -y jupyter
conda create -n mlpi
conda activate mlpi
```
* install jupyterlab

```console
conda install conda-forge::jupyterlab
```

* install packages

```console
pip install matplotlib pandas scikit-learn torch torchvision torchaudio
```
* Register the environment
* 
```console
python -m ipykernel install --user --name mlpi --display-name "mlpi"
```

# launch jupyterlab with this command

jupyter lab
