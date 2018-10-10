When using fossil for version control, it can be helpful to use one of our servers as a remote location.

This is the sequence of steps that I found most comfortable to do so.

I will assume that the repository already exists in a FOSSIL directory, with some code/data already in it.

## configure username and password locally

from a checkout of the repository (or from a `fossil all`) call:

    fossil ui
  
this will open the web interface in the local repository.
under the `Admin` tab, `Users` link, one can set the password for the administrator user (the Users table, bottom of the page).
Use the password you prefer.
This is going to be the one you will need also for remote access.

remember to control what your username is, it will be needed later.

## setting permissions for other users

Given that the access will be public (knowing the exact address, but still public) a good idea is to set
everything as private as much as possible.

This is done from the same `Admin/Users`

The users `nobody` and `anonymous` are the privileges for those that are not logged in to the repository.
Click on their name and untick all the boxes to remove all privileges.

## setting the ssh for the tunnelling

Given that the servers are set to stop all connections from the outside, it is necessary to use a ssh connection 
to make a tunnel and being able to use the remote server as a service on our local machine.

to do this, you have to add to the ssh config file found in `.ssh/config` the following lines:

    Host bio8
        HostName    <ip of the bio8 server>
        User    <your unibo account>
        LocalForward    <remote port number> localhost:<local port number>
        ServerAliveInterval 240
        
* the `User` setting is your unibo account, that will make it easier to do the ssh login
* `LocalForward` perform the tunnelling. This is the most important one.
  It can be used multiple times if one wants to run multiple services.
* `ServerAliveInterval` will make sure that the ssh will send a sign of life to the server so that 
  the connection does not drop automatically if inactive for long.
  This allow the service to be run long term without issues.

## Copy the fossil file in the server

from your FOSSIL directory run:

    scp <yourfile>.fossil bio8:~/FOSSIL
    
## Run the remote fossil server

login in the server with:

    ssh bio8
    
it will ask for your unibo password (see a reference on how to do passwordless access possible).
Once you have logged in, you can type:

    fossil server ./FOSSIL  --port <remote port number>
    
to run all the fossil repositories that you have in the remote FOSSIL directory at the same time.
at this point you will be able to see the web interface at the address:

    localhost:<local port number>/<yourfile>/
    
for example, if you bind the port `8881` and the repository file was called `myrepo.fossil` the address will be:

    localhost:8881/myrepo/
    
if you set up the permission properly, you should see the login form, as you need to be logged in to see anything at all

## setting up the remote-url for the local fossil repository

last step, we need to tell the local repository of the existance of the remote one.
if your account name in the fossil repository is `<username>`, you will need this command:

    fossil remote-url http://<username>@localhost:<local port number>/<yourfile>/
    
at this point fossil will automatically sync your repo with the remote one everytime you do a commit.

## bonus: push the configurations of the web interface

web interface configurations are not automatically synced with the remote repository, as they are not linked to commits.

One have to explicitely push to (or pull from) the remote repository to sync the two.
To do this, the command is:

    fossil configuration push all
    
or 

    fossil configuration pull all
    
to copy from the server instead of pushing to it.
