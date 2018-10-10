## ATTIVARE ACCESSO SSH SENZA PASSWORD (token)
https://debian-administration.org/article/530/SSH_with_authentication_key_instead_of_password

## AGGIUNGERE IL REMOTE SERVER NEL SSH CONFIG CON IL PORT FORWARD
    Host bio6
        HostName    <bio6 ip address>
        User    <your unibo username>
        LocalForward    8888 localhost:8888

## FARE IL LOGIN DAL PC LOCAL PER ATTIVARE IL PORT FORWARD

    ssh bio6

## CREARE SUL SERVER IL FILE DI CONFIGURAZIONE DEL NOTEBOOK SERVER

    jupyter notebook --generate-config

## MODIFICARE IL FILE DI CONFIGURAZIONE

in `~/.jupyter/jupyter_notebook_config.py`
settare:

    c.NotebookApp.token = '<my_secret_token>'

## FAR PARTIRE IL KERNEL REMOTO

    jupyter notebook --port=8888 --no-browser

## CONFIGURARE SU ATOM HYDROGEN IL REMOTE GATEWAY

inserire nella sezione remote gateway:

    [{ "name": "remote kernel", "options": {"baseUrl": "http://localhost:8888", "token": "<my_secret_token>"}}]

## DAL MENU DI HYDROGEN

selezionare la voce `connect to remote kernel`

