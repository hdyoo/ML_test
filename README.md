# access
### yshep server 2 ip: 165.132.111.50

# setup environment in anaconda (ROOT, pytorch, qiskit etc.)
### WRARNING!!! this recipe with csh or tcsh based

### add the following in your .cshrc (shell setup file => remove '!' in all below lines when you copy to your .cshrc file)
!# >>> conda initialize >>>

!# !! Contents within this block are managed by 'conda init' !!

!if ( -f "/home/anaconda3/etc/profile.d/conda.csh" ) then
    
!    source "/home/anaconda3/etc/profile.d/conda.csh"

!else
    
!    setenv PATH "/home/anaconda3/bin:$PATH"

!endif

!# <<< conda initialize <<<

### setup ROOT in anaconda (https://root.cern)
conda create -c conda-forge --name root_torch root

conda activate root_torch

conda config --add channels conda-forge

conda update --all  ## do this whenever you install some packages like below

### setup pytorch in the activated conda (https://pytorch.org)
conda install pytorch torchvision torchaudio cpuonly -c pytorch

(or try if above doesn't work: conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c nvidia)

### install qiskit (for QML with IBM QC resource)
pip install qiskit

pip install 'qiskit-terra[visualization]'

pip install 'qiskit[machine-learning]'

### in the case you need "uproot" package
conda install -c conda-forge uproot

# how to access Jupiter notebook remotely
### in remote server (like yshep server 2)
conda install jupyter

jupyter notebook --generate-config

vi ~/.jupyter/jupyter_notebook_config.py => c.NotebookApp.allow_remote_access=True

jupyter notebook password ## setup your password

### at local terminal
ssh -N -f -L 8880:localhost:9000 -p 4000 (your id)@165.132.111.50

http://localhost:8880/tree? ## in your browser (like chrome, safari etc.)

