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

__

**Ruoli e Identità in Google Cloud**

Oltre a gestire le risorse, come ingegnere del cloud, sarà necessario gestire anche l'accesso a queste risorse, utilizzando ruoli e identità.

**Ruoli in Google Cloud**  
Un *ruolo* è una raccolta di permessi, che vengono assegnati agli utenti tramite il binding di un utente a un ruolo. Le *identità* sono gli oggetti che rappresentano un utente umano o un account di servizio in Google Cloud. Ad esempio, Alice è una sviluppatrice di software con l'identità *alice@example.com*. I ruoli sono assegnati a questa identità, così Alice può creare, modificare, eliminare e utilizzare risorse in Google Cloud.

Esistono tre tipi di ruoli in Google Cloud:
1. **Ruoli di base**: in precedenza chiamati ruoli primitivi, includono Owner, Editor e Viewer, che forniscono privilegi ampi e applicabili a molte risorse. È consigliabile usare ruoli predefiniti invece di quelli di base, poiché i ruoli di base concedono permessi troppo ampi che potrebbero non essere necessari per l'utente.
2. **Ruoli predefiniti**: offrono un accesso granulare alle risorse specifiche di Google Cloud, gestiti e aggiornati da Google. Ad esempio, in App Engine ci sono:
   - *appengine.appAdmin*: consente di leggere, scrivere e modificare tutte le impostazioni dell'applicazione.
   - *appengine.ServiceAdmin*: consente accesso in sola lettura alle impostazioni dell'app e in scrittura a livello di modulo e versione.
   - *appengine.appViewer*: consente solo la lettura delle applicazioni.
3. **Ruoli personalizzati**: permettono agli amministratori del cloud di creare e gestire i propri ruoli, selezionando i permessi definiti in IAM. Tuttavia, alcuni permessi, come *iam.ServiceAccounts.getAccessToken*, non sono disponibili nei ruoli personalizzati.

**Assegnazione dei Ruoli alle Identità**  
Una volta determinati i ruoli da assegnare agli utenti, è possibile farlo tramite la console IAM. È importante sapere che i permessi non possono essere assegnati direttamente agli utenti, ma solo ai ruoli, che vengono poi assegnati agli utenti. Dalla console IAM, è possibile selezionare un progetto e visualizzare l'interfaccia di gestione dei permessi. Si può quindi selezionare l'opzione "Aggiungi" per inserire i nomi utente e i ruoli associati.

![Screenshot 2024-11-28 alle 13 22 59](https://github.com/user-attachments/assets/bae55ed8-4d30-48fb-994d-32af098af955)

![Screenshot 2024-11-28 alle 13 23 20](https://github.com/user-attachments/assets/e50d0e15-045c-4929-8ab6-d2f5a333d994)
![Screenshot 2024-11-28 alle 13 23 41](https://github.com/user-attachments/assets/e91fe261-3365-4b02-9b40-c22c326b9626)



**Account di Servizio**  

Gli account di servizio sono utilizzati quando le applicazioni o le macchine virtuali (VM) devono eseguire operazioni a nome di un utente o per svolgere attività per le quali l'utente non ha i permessi necessari. Ad esempio, un'applicazione potrebbe necessitare di accedere a un database senza consentire agli utenti dell'applicazione di farlo direttamente. In questo caso, si crea un account di servizio con accesso al database e si assegna a quell'applicazione, permettendo all'applicazione di eseguire query a nome degli utenti senza dover dare loro accesso diretto al database.

Gli account di servizio sono particolari perché possono essere trattati sia come risorse sia come identità. Quando si assegna un ruolo a un account di servizio, lo si considera come un'identità. Quando si concedono permessi a un utente per accedere a un account di servizio, lo si considera come una risorsa.

Esistono due tipi di account di servizio:
1. **Account di servizio gestiti dall'utente**: gli utenti possono creare fino a 100 account di servizio per progetto. Quando si crea un progetto con l'API Compute Engine abilitata, viene creato automaticamente un account di servizio per Compute Engine. Allo stesso modo, se si ha un'applicazione App Engine, Google Cloud creerà automaticamente un account di servizio per App Engine. Questi account vengono automaticamente dotati di ruoli di editor nei progetti in cui sono creati. È anche possibile creare account di servizio personalizzati nei progetti.
2. **Account di servizio gestiti da Google**: Google crea e gestisce account di servizio utilizzati per vari servizi di Google Cloud.

Gli account di servizio possono essere gestiti a livello di progetto o a livello di singolo account di servizio. Ad esempio, se si concede il permesso `iam.serviceAccountUser` a un utente per un progetto specifico, quell'utente avrà la possibilità di gestire tutti gli account di servizio nel progetto. Se si preferisce limitare la gestione a determinati account, si può assegnare `iam.serviceAccountUser` a un singolo account di servizio.

Gli account di servizio vengono creati automaticamente quando vengono creati determinate risorse. Ad esempio, verrà creato un account di servizio per una VM quando questa viene creata. Se si desidera creare un account di servizio per un'applicazione specifica, si può fare tramite la console IAM & Admin, selezionando "Account di servizio" e poi cliccando su "Crea account di servizio".

![Screenshot 2024-11-28 alle 13 24 48](https://github.com/user-attachments/assets/23ac685c-7451-4f25-a91a-5149ff13bb28)

______________________________




Billing












