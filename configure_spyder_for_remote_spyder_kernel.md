# Configure spyder to connect to a remote spyder-kernel in a server

## The *first time*:

### LOCAL: ADD THE REMOTE SERVER IN THE SSH CONFIG, WITH PORT FORWARDING
    Host <name you give to the server>
        HostName    <server ip address>
        User    <your unibo username>
        LocalForward    8888 localhost:8888

### ACCESS THE SERVER AND INSTALL SPYDER-KERNELS 
    ssh <name you give to the server>
    pip install spyder-kernels

### SERVER: Launch a new kernel on the server, choosing the name of the configuration file you want to create 
    python -m spyder_kernels.console -f=./<name>.json
     
### LOCAL: copy the configuration file from remote server to your local computer (where you want to use Spyder)
    scp <name you give to the server>:/home/PERSONALE/<username>/<name>.json /your/local/path/

### LOCAL: install paramiko package in the same environment as Spyder
    conda install paramiko

## FROM NOW ON, FOLLOW THE FOLLOWING INSTRUNCTIONS *EACH TIME* YOU WOULD LIKE TO CONNECT

    ssh <name you give to the server> 
    python -m spyder_kernels.console -f=./<name>.json

The .json you create is likely equal to the old one you have stored locally the first time, so you do not have to copy it again with `scp`

### Open Spyder and click on `Console>Connect to an existing kernel`

`Kernel ID/Connection file`: browse to /your/local/path/ where you copied the kernel configuration file (<name>.json)  and choose it
`Host name`: `<username>:<remote_address>:22` (choosing port 22 is mandatory for Spyder)  
`Password`: the password you use to access the server
