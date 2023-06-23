# Install Jupyter notebooks

## Prepare the Python environment

First, we need pip installed

    sudo apt install python3-pip

Then install virtualenv

    pip3 install virtualenv

If necessary append the installation path to the PATH variable

    export PATH=$PATH:/my/path

then we are ready to create a Python virtual environment

    virtualenv <myenv>

    
## Install Jupyter

Activate the environment

    source <myenv>/bin/activate

Install the Jupyter package

    pip install jupyter
    
Add some valuable packages for academic work

    pip install pandas numpy matplotlib
