# project , service , accounts and billing



In Google Cloud, un'organizzazione rappresenta la radice gerarchica delle risorse, di solito corrispondente a una azienda o entità. Può essere collegata a un dominio di Google Workspace (che include servizi come Gmail, Docs e Drive) o a un account Cloud Identity, il servizio di gestione delle identità di Google.

Un'organizzazione è associata a una singola identità cloud, che viene gestita da super amministratori. 
Questi super amministratori assegnano il ruolo di "Amministratore 
dell'Organizzazione" all'interno di Identity and Access Management (IAM) agli utenti responsabili della gestione dell'organizzazione. 
Inoltre, Google Cloud assegna automaticamente ai membri del dominio i ruoli di "Creatore di progetti" e "Creatore di account di fatturazione", 
permettendo loro di creare progetti e gestire la fatturazione per le risorse utilizzate.

Il ruolo di Amministratore dell'Organizzazione include compiti importanti come:
- Definire la struttura gerarchica delle risorse
- Definire le politiche IAM per l'organizzazione
- Delegare i compiti di gestione ad altri utenti

Quando un utente crea un account di fatturazione o un progetto all'interno dell'organizzazione, 
Google Cloud crea automaticamente una risorsa organizzativa. 
Da quel momento in poi, tutti i progetti e gli account di fatturazione sono considerati sotto l'organizzazione, e gli utenti al suo interno possono accedere alle risorse di Google Cloud.


![Screenshot 2024-11-28 alle 13 12 31](https://github.com/user-attachments/assets/4942dc11-2d7c-429c-8db0-3679d1a20de1)


## folder

Le *Cartelle* sono i mattoni fondamentali per costruire gerarchie organizzative multilivello in Google Cloud. Un'organizzazione può contenere delle cartelle, e queste a loro volta possono contenere altre cartelle o progetti. Le cartelle sono opzionali e non è necessario utilizzarle. Una singola cartella può quindi contenere sia altre cartelle che progetti. La struttura delle cartelle solitamente riflette i tipi di servizi offerti dalle risorse nei progetti contenuti, così come le politiche di accesso e gestione ad esse associate.

Ad esempio, immaginate un'organizzazione con quattro dipartimenti: finanza, marketing, sviluppo software e legale. Il dipartimento di finanza ha bisogno di tenere separati i propri conti da quelli delle risorse "Conti da ricevere" e "Conti da pagare", quindi l'amministratore crea due cartelle all'interno della cartella principale "Finanza". Il dipartimento di sviluppo software utilizza diversi ambienti come *Dev*, *Test*, *Staging* e *Produzione*. Poiché l'accesso a ciascun ambiente è regolato da politiche specifiche, si organizza ogni ambiente in una cartella separata. Per marketing e legale, invece, visto che le risorse possono essere condivise tra i membri dello stesso dipartimento, è sufficiente una sola cartella per entrambi.

Questa organizzazione consente una gestione chiara e centralizzata delle risorse, facilitando la creazione di progetti che corrispondono alle necessità di ogni dipartimento o gruppo.

![Screenshot 2024-11-28 alle 13 13 34](https://github.com/user-attachments/assets/b06d443a-8dd2-4b3c-a6a4-fe87f74b54e0)


___

I Progetti sono una delle componenti più importanti della gerarchia di Google Cloud. All'interno dei progetti si creano risorse, si utilizzano i servizi di Google Cloud, si gestiscono le autorizzazioni e le opzioni di fatturazione.

Il primo passo per lavorare con un progetto è crearne uno. Chiunque possieda il permesso IAM resourcemanager.projects.create può creare un progetto. Di default, quando viene creata un'organizzazione, ogni utente nel dominio riceve automaticamente questo permesso.

Ogni organizzazione ha una quota di progetti che può creare. Tale quota può variare tra le organizzazioni, in base all'uso tipico, alla cronologia dell'utente e ad altri fattori. Se si raggiunge il limite di progetti e si tenta di crearne un altro, verrà chiesto di fare richiesta per un aumento della quota, fornendo informazioni sul numero di progetti aggiuntivi necessari e sul loro utilizzo.

Una volta creata la gerarchia delle risorse, è possibile definire le politiche che ne regolano la gestione e l'accesso.



![Screenshot 2024-11-28 alle 13 14 38](https://github.com/user-attachments/assets/869d5b43-052f-4995-910e-ddf68677b510)





