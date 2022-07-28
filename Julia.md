# Install Julia for Jupyter notebooks

Download the Julia 64 bit glic version and uncompress Julia from https://julialang.org/downloads/

    wget https://julialang-s3.julialang.org/bin/linux/x64/1.6/julia-1.6.7-linux-x86_64.tar.gz
    tar xvzf julia-1.6.7-linux-x86_64.tar.gz

Move uncompressed folder to /opt

    mv julia-1.6.7 /opt/
    
Add julia binary folder to path 

    export PATH=$PATH:/opt/julia-1.6.7/bin/

activate the jupyter virtual enviroment

    source jupyter/bin/activate
    
install Julia kernel (case sensitive)

    using Pkg
    Pkg.add(“IJulia”)

