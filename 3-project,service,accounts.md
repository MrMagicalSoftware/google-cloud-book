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



**Politiche dell'Organizzazione**  
Google Cloud offre il servizio *Organization Policy Service*, che controlla l'accesso alle risorse di un'organizzazione. Questo servizio si integra con l'IAM (Identity and Access Management). Mentre IAM definisce chi può eseguire determinati compiti sulle risorse, il servizio delle politiche dell'organizzazione stabilisce *cosa* può essere fatto con tali risorse.

**Vincoli sulle Risorse**  
Le politiche dell'organizzazione si basano su *vincoli* imposti alle risorse. Google Cloud distingue tra vincoli di tipo *elenco* e *Booleani*. I vincoli di tipo elenco definiscono le opzioni consentite o negate per una risorsa (ad esempio, consentire o negare determinati valori). I vincoli booleani, invece, determinano se una condizione è vera o falsa e se il vincolo viene applicato o meno (ad esempio, disabilitare l'accesso alle porte seriali su VM).

**Valutazione delle Politiche**  
Le organizzazioni possono avere politiche permanenti per proteggere i dati e le risorse nel cloud. Ad esempio, può esserci una regola che limita chi può abilitare un'API o creare un account di servizio. Un approccio efficiente consiste nel definire politiche che limitano cosa può essere fatto e applicarle a oggetti nell'intera gerarchia delle risorse. Queste politiche vengono ereditate da tutti i livelli inferiori e non possono essere disattivate o sovrascritte, ma è possibile impedirne l'eredità impostando il parametro *inheritFromParent* su false.

**Gestione dei Progetti**  
Una delle prime attività quando si avvia una nuova iniziativa nel cloud è configurare un progetto. Questo può essere fatto tramite il Google Cloud Console. Dopo aver effettuato l'accesso, nella homepage della console è possibile creare e gestire i progetti, applicando le politiche appropriate alla gerarchia di risorse.


![Screenshot 2024-11-28 alle 13 16 59](https://github.com/user-attachments/assets/08fc3287-de4e-41a0-9bb1-75a9b86a713a)

![Screenshot 2024-11-28 alle 13 17 15](https://github.com/user-attachments/assets/8040b9de-61ab-46e7-851d-bc92a1b00ff6)

![Screenshot 2024-11-28 alle 13 17 48](https://github.com/user-attachments/assets/ec1597ff-4fa9-4251-aa4c-0a41661fabe9)

![Screenshot 2024-11-28 alle 13 18 05](https://github.com/user-attachments/assets/33acd9ba-f096-4554-a844-280f13ac59df)


From there, you can click Create Project, which displays the New Project dialog box.
Here, you can enter the name of a project and select an organization (Figure 3.8 and
Figure 3.9).

![Screenshot 2024-11-28 alle 13 19 18](https://github.com/user-attachments/assets/9a4fb01c-ecbc-4e6c-a47e-0442672d4828)







