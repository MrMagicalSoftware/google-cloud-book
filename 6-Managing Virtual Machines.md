# Managing Virtual machines



**Gestione delle singole istanze di macchine virtuali**  

Dopo la creazione delle macchine virtuali (VM), è necessario gestire sia le istanze singole sia i gruppi di istanze configurati nello stesso modo, chiamati *instance groups*. Qui viene spiegata la gestione delle singole VM, non incluse in gruppi o cluster, utilizzando Cloud Console, Cloud Shell o il Cloud SDK.  

### Gestione delle singole VM nella Console  
Le operazioni principali di gestione includono la creazione, l'arresto e l'eliminazione delle istanze. La creazione è stata trattata nel capitolo precedente, quindi qui ci si concentra su arresto, avvio, reset, ed eliminazione.  

#### Arrestare, avviare e resettare le istanze  
Accedendo alla **Google Cloud Console** e selezionando **Compute Engine > VM Instances**, si visualizza l'elenco delle VM disponibili. Ogni riga elenca le proprietà della VM e, accanto a ciascuna, c'è un'icona con tre punti che apre un menu con diverse opzioni.  

- **Arresto delle VM**:  
  L'opzione *Stop* nel menu arresta una VM, interrompendo il consumo di risorse computazionali. Questo stato permette di riutilizzarla in futuro. Quando si arresta una VM, il segno verde accanto al nome cambia in un cerchio grigio con un quadrato bianco, e l'opzione SSH viene disabilitata.  

- **Avvio delle VM**:  
  Per avviare una VM arrestata, si seleziona *Start* dallo stesso menu. Questo riattiva la macchina e ripristina l'accesso SSH.  

- **Reset delle VM**:  
  Il comando *Reset* riavvia la VM senza alterarne le proprietà, ma cancella i dati in memoria.  

#### Eliminare le istanze  
Quando una VM non è più necessaria, può essere eliminata. Questa operazione rimuove la macchina dalla console e libera le risorse associate, come lo spazio di archiviazione utilizzato dall'immagine della VM. Durante l'eliminazione, viene mostrato un messaggio di avviso per confermare l'operazione.  

<img width="696" alt="Screenshot 2024-12-02 alle 08 03 24" src="https://github.com/user-attachments/assets/4ff4030d-9a2b-4651-b5c5-fd0d77f74dbc">


<img width="686" alt="Screenshot 2024-12-02 alle 08 03 34" src="https://github.com/user-attachments/assets/0306c50a-0963-4bc7-a43b-8634b62791be">

<img width="681" alt="Screenshot 2024-12-02 alle 08 03 57" src="https://github.com/user-attachments/assets/7be0de5e-225b-4140-bf90-3e26629d0a29">
<img width="657" alt="Screenshot 2024-12-02 alle 08 04 13" src="https://github.com/user-attachments/assets/36fb6cfe-f265-4d93-98f6-08dc01ba74c1">
<img width="671" alt="Screenshot 2024-12-02 alle 08 04 36" src="https://github.com/user-attachments/assets/d851d698-4bd3-4f64-aa89-cad8bd7c5f3e">
<img width="672" alt="Screenshot 2024-12-02 alle 08 05 51" src="https://github.com/user-attachments/assets/75c7e622-33b2-42af-a29a-c202160d1798">
<img width="676" alt="Screenshot 2024-12-02 alle 08 06 08" src="https://github.com/user-attachments/assets/34c1fa6a-3ba2-4057-8738-a5a25f65a33d">



_____________________________________


**Visualizzare l'inventario delle macchine virtuali**  

La pagina **VM Instances** nella **Google Cloud Console** elenca tutte le macchine virtuali presenti nel progetto corrente. In caso di numerose istanze, è possibile filtrare l'elenco per visualizzare solo quelle di interesse.  

### Uso del filtro  
Sopra l'elenco delle VM è presente una casella denominata *Filter VM Instances*. Specificando un criterio, si possono visualizzare solo le istanze corrispondenti. Ad esempio, inserendo il nome di un'istanza come *instance-2*, si mostreranno solo le VM con quel nome.  

### Altri criteri di filtro  
Oltre al nome, si possono filtrare le istanze utilizzando i seguenti criteri:  
- **Etichette (Labels)**: Filtrare in base alle etichette assegnate.  
- **IP interno** e **IP esterno**: Cercare VM con specifici indirizzi IP.  
- **Stato**: Mostrare istanze in esecuzione, arrestate o con altri stati.  
- **Zona**: Limitare la ricerca alle VM in una specifica zona geografica.  
- **Rete**: Filtrare per rete di appartenenza.  
- **Protezione dalla cancellazione**: Individuare VM con protezione contro l'eliminazione attivata.  

### Condizioni multiple  
Se si impostano più condizioni di filtro, tutte devono essere vere affinché una VM sia mostrata. Per includere istanze che soddisfano una qualsiasi delle condizioni, è necessario specificare esplicitamente l'operatore *OR*.  

Questo strumento permette di gestire e monitorare in modo efficiente anche progetti con un elevato numero di VM, semplificando la ricerca e l'organizzazione delle risorse.
<img width="664" alt="Screenshot 2024-12-02 alle 08 07 50" src="https://github.com/user-attachments/assets/1a460b92-a1ca-43fd-9a0d-4761aaeaf62d">


## Attaching GPUs to an Instance


**Utilizzo delle GPU nelle macchine virtuali**  

Le GPU (Graphics Processing Units) sono essenziali per applicazioni che richiedono calcoli intensivi, come la visualizzazione di dati e il machine learning. Consentono di delegare parte del lavoro computazionale dal processore (CPU) alla GPU, migliorando le prestazioni. **Google Compute Engine** offre una famiglia di macchine appositamente progettata per VMs con GPU.  

<img width="652" alt="Screenshot 2024-12-02 alle 08 10 15" src="https://github.com/user-attachments/assets/5a763e20-61c4-4689-af7c-daf0aa688ae4">



### Configurazione delle GPU  
Quando si crea un'istanza nella **Google Cloud Console**, si può selezionare la famiglia di macchine GPU per accedere alle opzioni disponibili. È necessario:  
1. Usare un'immagine di sistema con driver GPU già installati o pianificare l'installazione manuale dei driver. Google Cloud fornisce immagini preconfigurate, come quelle per il deep learning.  
2. Verificare che la zona selezionata supporti GPU.  

I parametri configurabili includono:  
- **Tipo di GPU**: Ad esempio, NVIDIA Tesla A100 o Tesla T4.  
- **Numero di GPU**: La quantità varia a seconda del tipo di GPU scelto. Ad esempio:  
  - **Tesla A100**: Configurazioni da 1, 2, 4, 8 o 16 GPU.  
  - **Tesla T4**: Configurazioni da 1, 2 o 4 GPU.  

<img width="669" alt="Screenshot 2024-12-02 alle 08 10 45" src="https://github.com/user-attachments/assets/fcd7ff66-d467-4f00-a2aa-00949910c5a9">



### Scelta della piattaforma CPU  
Oltre al tipo di macchina, è possibile selezionare una piattaforma CPU specifica (ad esempio, Intel Skylake o Intel Ivy Bridge). In assenza di una selezione, Compute Engine sceglie automaticamente la piattaforma più adatta.  

### Restrizioni  
Le GPU non possono essere utilizzate con macchine che condividono memoria. Per conoscere i dettagli aggiornati sulle restrizioni e la disponibilità delle GPU nelle varie zone, si può consultare la documentazione ufficiale: [Google Cloud GPU Documentation](https://cloud.google.com/compute/docs/gpus).  

L'integrazione delle GPU nelle VM consente di affrontare carichi di lavoro complessi con maggiore efficienza, sfruttando configurazioni flessibili e ottimizzate per le esigenze specifiche.









_____________________________________
