# Install Jupyter notebooks

## Prepare the python environment

First we need pip installed

    sudo apt install python3-pip

Then install virtualenv

    pip3 install virtualenv

If necessary append instalation path to the PATH variable

    export PATH=$PATH:/my/path

then we are ready to create a python virtual environment

    virtualenv myenv

    
## Install Jupyter

    pip install jupyter
    
Add some useful packages for academic work

    pip install pandas numpy matplotlib
