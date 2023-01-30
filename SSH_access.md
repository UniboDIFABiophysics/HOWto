# Accessing remote servers with SSH

## step 1 - installing ssh

On linux install **openssh**.
One can find it in their distribution package manager.

to activate openssh on windows 10, look at a guide such as:
* [https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/](https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/)

> **`NOTE`**: this should be replace with a proper guide locally


## step 2 - setting the ssh for the tunnelling

Given that the servers are set to stop all connections from the outside, it is necessary to use a ssh connection 
to make a tunnel and being able to use the remote server as a service on our local machine.

to do this, you have to add to the ssh config file found in `~/.ssh/config` (if it does not exist, create it) the following lines:

    Host <choose an server name>
        HostName    <ip of the server>
        User    <your unibo account>
        LocalForward    <remote port number> localhost:<local port number>
        ServerAliveInterval 240
        
* the `User` setting is your unibo account, that will make it easier to do the ssh login. Students should insert the full email account in the form `name.surname@studio.unibo.it`
* `LocalForward` perform the tunnelling. This is the most important one.
  It can be used multiple times if one wants to run multiple services.
* `ServerAliveInterval` will make sure that the ssh will send a sign of life to the server so that 
  the connection does not drop automatically if inactive for long.
  This allow the service to be run long term without issues.

for example, this is my configuration for a server:

    Host myserver
        Hostname 127.0.0.2
        User enrico.giampieri2
        LocalForward    8883 localhost:8883
        ServerAliveInterval 240

## step 3 - connect with the server

open a terminal and type `ssh <server name>`.
it will ask for your password (the one of you unibo account), and once it accept it, ssh will open a new bash console on the remote server.

## launch byobu

in the server there should be a program called `byobu`.
as soon as you log in in the server, launch from the terminal.
it will replace it with a new one that will remain active even if you close the connection (such as closing ssh or turning off the pc).

This will garantee that your remote executions will keep running even



## working with python on the remote server

### option 1 - launch `jupyterlab`

This option will run python on the server, and will create an interface from the local computer to work on it.

Once one is in the server and launched byobu, launch jupyterlab from the console:

* `jupyter lab --port <chosen remote port> --no-browser`

For the `<chosen remote port>` please chose a random value in the 8800-8899 range, to avoid overlapping with other users.

it will run and will print some connection information that looks like:

> Jupyter Server 1.1.3 is running at:
>
> **http://localhost:8883/lab?token=c7e3852a42e7af5537ed59531ecbac1f4928271d97001c16**



now you can open your browser at the page that is highlighted in you computer.
One should replace the `8883` with the chosen remote

### option 2 - remote kernel
Using this option one will have python run remotely, but using it as an engine for a local program such as `atom` or `spyder`.

see: 
* [configure_atom_for_remote_jupyter_kernel.md](./configure_atom_for_remote_jupyter_kernel.md)
* [Connect_to_remote_kernel_Spyder3.md](./Connect_to_remote_kernel_Spyder3.md)

### option 3 - run python directly on the server - not recommended

Not much to say there.
Just edit the code and executely remotely completely.
In this case one would need a program that allow editing and executing completely remotely such as `vim` (or the [spacevim distribution](https://spacevim.org)) and is by far **the most difficult option, and I would not recommend it**.

