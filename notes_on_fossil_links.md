Potete creare file di documentazione stile wiki, sempre contenuti nel repository! potete inoltre usare file del repository per la documentazione, basta usare gli indirizzi relativi all'indirizzo speciale

    ./doc/tip/<posizione del file nella directory del repository>

Se volessi inserire delle formule in latex nelle pagine, posso includere la libreria Mathjax

    <script type="text/x-mathjax-config">
      MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], 
                                                 ['\\(','\\)']
                                                ]}});
    </script>
    <script type="text/javascript" async
      src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_CHTML">
    </script>


    When $a \\ne 0$, there are two solutions to \\(ax^2 + bx + c = 0\\) and they are
    $$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}.$$

Se volessi usare i notebook ipython per fare delle presentazione, devo includere `Reveal.js` nel repository 
(oppure trovare una fonte esterna della libreria), e poi compilare il notebook in maniera statica tramite l'uso di nbconvert.

Assumendo di aver messo `reveal.js` in una cartella con lo stesso nome nel mio repository, posso compilare il notebook con:

    jupyter nbconvert --to slides mynotebook.ipynb --reveal-prefix './reveal.js'

ed includere il file html risultante nel repository.

Posso includere dei feed RSS a delle risorse specifiche per mantenermi 
aggiornato sull'evoluzione di un repository senza doverlo andare a controllare manualmente.

Il link per l'aggiornamento su tutto è

    <baseulr>/timeline.rss

Se invece si vogliono soltanto aggiornamenti specifici, si può inserire una query. Ad esempio, aggiornamenti solo del repository è:

    <baseurl>/timeline.rss?y=ci

si possono anche seguire singole pagine wiki, singoli ticket, branch del repository, etc..

Posso collegare i ticket ed i checkin simplicemente includendo i loro rispettivi ID 
(10 caratteri alfanumerici) nel titolo di chi vi fa riferimento, racchiuso fra parentesi quadre.

se ho un ticket con ID `0123456789`, il commit che lo risolve può inserire questo codice nel messaggio:

    commit -m "risolve il ticket [0123456789]"

la home page può essere una wiki, oppure una pagina presa dal repository.
Questo può essere settato dalla pagina di admin nella sezione "Config"

Per scaricare l'intero progetto come uno zip, posso collegarmi alla pagina:

    <baseurl>/zip/<myfilename>.zip

se voglio scaricare una versione specifica posso usare

    <baseurl>/zip/<myfilename>.zip?uuid=<versionIwant>

scarica esclusivamente il contenuto del repository non della documentazione o di altro.

posso fare un link ad una versione di un file che evidenzi delle linee specifiche da usare in un eventuale ticket.
Per farlo posso usare il comando `./file/`

visualizzo le linee nel file:

    <baseurl>/file/<nomefile>?ln

evidenzio le linee dalla 5 alla 10 (incluse, partendo da 1):

    <baseurl>/file/<nomefile>?ln=5-10

Questi comandi si riferiscono alla versione più aggiornata del file.
Se voglio collegarlo ad una versione specifica, posso indicare il checkin specifico:

    <baseurl>/file/<nomefile>?ln=5-10&ci=<checkin code>
    
## edit the structure of tickets

The default ticket system have several rough edges that can be easily improved.

### types of tickets

One commeon thing is that for data analysis projects the standard tickets definition does not map well.
This cna be changed in the `Admin` panel, following the `Tickets` link and then the `Common`.

At this point one can edit the choices available when creating a new ticket.
in particolar, possible kinds of tickets are:

        set type_choices {
           Code_Defect
           Data_Issue
           Theory_Issue
           Paper_Issues
           External_Feedback
           Documentation
           Feature_Request
           Incident
        }
