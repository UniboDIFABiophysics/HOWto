# Configura spyder per connettersi a un server remoto

## La *prima volta*:

### LOCALE: AGGIUNGERE IL REMOTE SERVER NEL SSH CONFIG CON IL PORT FORWARD 
    Host bio6
        HostName    <bio6 ip address>
        User    <your unibo username>
        LocalForward    8888 localhost:8888

### ACCEDI AL SERVER E INSTALLA SPYDER-KERNELS 
    ssh bio6
    pip install spyder-kernels

### SERVER: Lancia un nuovo kernel nel server, scegliendo il nome del file di configurazione che vuoi creare 
    python -m spyder_kernels.console -f=./<name>.json
     
### LOCALE: copia il file di configurazione da server remoto al tuo pc locale (in cui vuoi usare Spyder)
    scp bio6:/home/PERSONALE/<username>/<name>.json /your/local/path/

### LOCALE: installare il package paramiko nello stesso environment in cui sta Spyder
    conda install paramiko

## D'ORA IN POI, SEGUI QUESTA PROCEDURA *OGNI VOLTA* CHE VUOI CONNETTERTI

    ssh bio6
    python -m spyder_kernels.console -f=./remote_machine.json

Il file creato sarà identico a quello che hai già in locale, per cui non serve copiarlo di nuovo con `scp`

### Apri Spyder e clicca su `Console>Connect to an existing kernel`

`Kernel ID/Connection file`: browse fino al /your/local/path/ in cui hai copiato il file di configurazione (<name>.json)  
`Host name`: `<username>:<remote_address>:22` (scegliere la porta 22 è necessario per Spyder)  
`Password`: la tua password di accesso al server
