## ACTIVATE THE PASSWORD-LESS ACCESS TO THE SERVER (TOKEN)
https://debian-administration.org/article/530/SSH_with_authentication_key_instead_of_password

## ADD THE REMOTE SERVER TO THE SSH CONFIG WITH THE PORT FORWARD ACTIVATED
you have to pick a `<server name>` that is easy to remember, and a a port (both in your local computer and in the remote server) for the ssh port forwarding. In the remote server, make sure that the port does not conflict with other users' selection, so avoid the default '8888' and similar that are normally used by jupyter.

    Host <server name>
        HostName    <server ip address>
        User    <your unibo username>
        LocalForward    <chosen local port> localhost:<chosen remote port>

## LOGIN FROM THE LOCAL PC TO THE REMOTE SERVER TO ACTIVATE THE PORT-FORWARD
    ssh <server name>

## CREATE ON THE REMOTE SERVER A CONFIGURATION FILE FOR THE NOTEBOOK SERVER
    jupyter notebook --generate-config

## MODIFY THE CONFIGURATION FILE TO ADD A FIXED TOKEN
in `~/.jupyter/jupyter_notebook_config.py`
set:

    c.NotebookApp.token = '<my_secret_token>'

## START THE REMOTE KERNEL
    jupyter notebook --port=<chosen remote port> --no-browser

## CONFIGURE ATOM HYDROGEN TO USE THE REMOTE GATEWAY
insert in the "remote gateway" section the following:

    [{ "name": "remote kernel", "options": {"baseUrl": "http://localhost:<chosen local port>", "token": "<my_secret_token>"}}]

## FROM THE HYDROGEN MENU
select the `connect to remote kernel` item

