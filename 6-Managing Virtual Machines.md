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


### **Gestione degli Snapshots**  

Gli snapshots sono copie dei dati presenti su un disco persistente, utili per salvare lo stato del disco e ripristinarlo successivamente. Consentono di creare dischi persistenti con dati identici o di effettuare backup, permettendo il recupero dello stato del disco in un momento specifico.  

#### **Creazione e Aggiornamento degli Snapshots**  
- **Primo snapshot**: Viene effettuata una copia completa dei dati sul disco persistente.  
- **Snapshot successivi**: Solo i dati modificati rispetto all’ultimo snapshot vengono copiati, ottimizzando l'uso dello spazio di archiviazione.  

> **Nota importante**: Per evitare perdita di dati memorizzati in memoria, è necessario svuotare i buffer del disco prima di creare uno snapshot. Ad esempio, in MySQL si utilizza il comando `FLUSH`.  

#### **Ruoli e Permessi**  
Per gestire gli snapshots, è richiesto il ruolo di **Compute Storage Admin**. Per assegnare questo ruolo:  
1. Accedere alla pagina **Identity Access Management (IAM)**.  
2. Selezionare **Roles** e specificare l'indirizzo email dell'utente a cui assegnare il ruolo.  

#### **Creazione di uno Snapshot nella Cloud Console**  
1. Accedere alla sezione **Compute Engine** e selezionare **Snapshots** nel pannello di sinistra.  
2. Fare clic su **Create Snapshot** per aprire il modulo di configurazione.  
3. Specificare:  
   - **Nome**: Nome univoco per identificare lo snapshot.  
   - **Descrizione**: Dettaglio opzionale per descrivere lo snapshot.  
   - **Etichette**: Utile per una gestione ordinata. Le etichette possono indicare il tipo di dati e l’applicazione che utilizza i dati.  
4. Scegliere la **regione di archiviazione**:  
   - **Regionale**: Archiviazione limitata a una specifica regione.  
   - **Multiregionale**: Archiviazione distribuita su più regioni per maggiore resilienza.  

L'uso degli snapshots consente di garantire continuità operativa e protezione dei dati, mantenendo al contempo un controllo efficiente dello spazio di archiviazione.



___


### **Gestione delle Immagini in Google Cloud**  

Le immagini sono copie complete del contenuto di un disco, utilizzate per creare VM. Sebbene simili agli snapshots, differiscono per scopo e metodo di archiviazione:  
- **Snapshots**: Backup incrementali, utilizzati per ripristinare o duplicare dati su un disco.  
- **Immagini**: Backup completi, utilizzati per creare nuove VM.  
È possibile creare una VM anche da uno snapshot, ma solo se proviene da un disco di avvio (boot disk).  

<img width="653" alt="Screenshot 2024-12-02 alle 08 14 55" src="https://github.com/user-attachments/assets/0a29996d-a4fb-4825-af4f-1a3a5271be5a">
<img width="583" alt="Screenshot 2024-12-02 alle 08 15 15" src="https://github.com/user-attachments/assets/6e491649-f30d-4b24-a8a7-18d55b761e90">



#### **Fonti per la Creazione delle Immagini**  
Le immagini possono essere create a partire da:  
- **Dischi persistenti**  
- **Snapshots**  
- **Altre immagini**  
- **File in Cloud Storage**  
- **Dischi virtuali**  

#### **Creazione di un’Immagine**  
1. Accedere alla pagina **Compute Engine** nella Cloud Console.  
2. Selezionare **Images** per visualizzare la lista delle immagini disponibili.  
3. Fare clic su **Create Image** per aprire il modulo di configurazione.  
4. Configurare:  
   - **Nome**: Identificativo univoco per l’immagine.  
   - **Descrizione**: Opzionale, per fornire dettagli sull'immagine.  
   - **Etichette**: Utili per gestire immagini in modo organizzato.  
   - **Famiglia**: Attributo opzionale per raggruppare immagini. La più recente e non deprecata verrà usata come predefinita.  

#### **Selezione della Fonte**  
- **Immagine esistente**: È possibile scegliere immagini dal progetto corrente o da altri progetti.  
- **File in Cloud Storage**: Si può esplorare il bucket di archiviazione per selezionare un file come fonte.  

#### **Gestione delle Immagini**  
- **Eliminazione**: Rimuove completamente l'immagine.  
- **Deprecazione**: Segnala che l'immagine non è più supportata, permettendo di specificare un’immagine di sostituzione. Le immagini deprecate restano disponibili, ma non vengono aggiornate per patch di sicurezza o miglioramenti.  
- **Creazione di una VM**: Dopo aver creato un’immagine, è possibile usarla per creare una VM selezionando **Create Instance** nella barra dei comandi sopra la lista delle immagini.  

La gestione delle immagini garantisce flessibilità per il provisioning di VM e una facile transizione a versioni più recenti, riducendo i rischi associati a immagini obsolete.


___



### **Introduzione ai Gruppi di Istanze (Instance Groups)**

I **gruppi di istanze** sono insiemi di VM gestite come un’unica entità. Ogni comando **gcloud** o console applicato a un gruppo di istanze viene applicato a tutte le istanze del gruppo. Google offre due tipi di gruppi di istanze: **gestiti** e **non gestiti**.

<img width="611" alt="Screenshot 2024-12-02 alle 08 17 29" src="https://github.com/user-attachments/assets/f80ff5d8-1aa8-42bb-9c0c-1d2091761ad5">




- **Gruppi gestiti**: Composti da VM identiche. Questi gruppi sono creati utilizzando un **modello di istanza** che specifica la configurazione della VM, come il tipo di macchina, l'immagine del disco di avvio, la zona, le etichette e altre proprietà. I gruppi gestiti possono scalare automaticamente il numero di istanze al loro interno e essere usati con il bilanciamento del carico per distribuire i carichi di lavoro. Se un'istanza si guasta, viene ricreata automaticamente. I gruppi gestiti sono la tipologia preferita.
  
- **Gruppi non gestiti**: Utilizzati quando è necessario lavorare con configurazioni differenti all’interno delle istanze del gruppo. Non supportano l'autoscaling o il bilanciamento del carico, quindi sono meno flessibili rispetto ai gruppi gestiti.

### **Creazione e Rimozione di Gruppi di Istanze e Modelli**

1. **Creazione di un Gruppo di Istanze**:  
   Per creare un gruppo di istanze, è necessario prima creare un **modello di istanza**.  
   Il comando per creare un modello di istanza è:
   ```bash
   gcloud compute instance-templates create INSTANCE
   ```
   È possibile specificare una VM esistente come sorgente del modello di istanza usando il parametro `--source-instance`:
   ```bash
   gcloud compute instance-templates create instance-template-1 --source-instance=instance-1
   ```
   I modelli di istanza possono anche essere creati dalla console, utilizzando la **pagina dei modelli di gruppo di istanze**.

2. **Gruppi Zonal e Regionali**:  
   I gruppi di istanze possono contenere istanze in una singola zona (**gruppo gestito zonale**) o distribuite su più zone (**gruppo gestito regionale**). I gruppi regionali sono consigliati perché distribuiscono il carico di lavoro su più zone, aumentando la resilienza.  
   È possibile specificare una **politica di distribuzione**:
   - **Distribuzione uniforme**: Distribuisce le istanze in modo uniforme tra le zone.
   - **Distribuzione bilanciata**: Distribuisce le istanze il più uniformemente possibile, tenendo conto delle risorse disponibili.
   - **Distribuzione qualsiasi**: Distribuisce le istanze tra le zone in base alla disponibilità e alle riserve.

3. **Rimozione di Modelli e Gruppi di Istanze**:  
   - **Rimuovere un modello di istanza**:  
     Per eliminare un modello di istanza, selezionarlo dalla pagina dei modelli di gruppo di istanze e fare clic sull'icona di eliminazione.  
     È possibile eliminare un modello anche con il comando:
     ```bash
     gcloud compute instance-templates delete INSTANCE-TEMPLATE-NAME
     ```
   - **Elencare modelli e gruppi di istanze**:  
     Per visualizzare i modelli di istanza e i gruppi di istanze, si usano i seguenti comandi:
     ```bash
     gcloud compute instance-templates list
     gcloud compute instance-groups managed list-instances
     ```

### **Considerazioni Finali NOTE **
I **gruppi gestiti** sono la scelta migliore per la gestione di VM in un ambiente scalabile e resiliente, grazie alla capacità di ridimensionarsi automaticamente e di riprendersi dai guasti. I **gruppi non gestiti** sono più adatti per casi in cui le VM richiedono configurazioni diverse, ma non beneficiano delle funzionalità avanzate come il bilanciamento del carico e l'autoscaling.


Ecco alcune domande a risposta multipla sul capitolo riguardante la gestione delle istanze e dei gruppi di istanze:

---

**1. Cosa sono i gruppi di istanze gestiti?**

a) Gruppi di VM con configurazioni differenti tra loro.  
b) Gruppi di VM identiche create usando un modello di istanza.  
c) Gruppi di VM che non supportano il bilanciamento del carico.  
d) Gruppi di VM che non possono scalare automaticamente.

---

**2. Qual è la differenza principale tra immagini e snapshot?**

a) Gli snapshot offrono backup incrementali, mentre le immagini sono backup completi.  
b) Le immagini offrono backup incrementali, mentre gli snapshot sono backup completi.  
c) Gli snapshot vengono utilizzati per creare VM, mentre le immagini vengono utilizzate per salvare dati su disco.  
d) Le immagini non possono essere utilizzate per creare VM, ma solo per ripristinare dischi.

---

**3. Quali dei seguenti strumenti si possono utilizzare per gestire le istanze su Google Cloud?**

a) Cloud Console.  
b) Cloud Shell.  
c) Cloud SDK (gcloud).  
d) Tutte le precedenti.

---

**4. Come si può creare un modello di istanza per un gruppo di istanze gestite?**

a) Utilizzando la Cloud Console e selezionando "Crea modello di istanza".  
b) Eseguendo il comando `gcloud compute instance-templates create`.  
c) Creando un'immagine da un'istanza esistente.  
d) Nessuna delle risposte precedenti.

---

**5. Cosa accade se un'istanza in un gruppo di istanze gestito si guasta?**

a) Il gruppo non reagisce al guasto dell'istanza.  
b) L'istanza viene ricreata automaticamente dal sistema.  
c) L'istanza viene eliminata permanentemente.  
d) Il carico di lavoro viene trasferito manualmente a un'altra istanza.

---

**6. Qual è il comando per elencare tutti i modelli di istanza in Google Cloud?**

a) `gcloud compute instance-groups list`  
b) `gcloud compute instance-templates list`  
c) `gcloud compute instance-groups managed list-instances`  
d) `gcloud compute list-templates`

---

**7. Quale delle seguenti affermazioni è vera riguardo i gruppi di istanze regionali?**

a) I gruppi regionali distribuiscono le VM solo su una zona.  
b) I gruppi regionali non sono raccomandati per aumentare la resilienza.  
c) I gruppi regionali distribuiscono automaticamente le istanze su più zone per aumentare la resilienza.  
d) I gruppi regionali possono essere utilizzati solo con un numero specifico di zone.

---

**8. Come si può creare un'immagine di un'istanza in Google Cloud?**

a) Usando il comando `gcloud compute images create`.  
b) Selezionando l'istanza dalla Cloud Console e cliccando "Crea immagine".  
c) Creando un'istanza e selezionando "Crea immagine" dal menu delle opzioni.  
d) Tutte le risposte precedenti.

---

**9. Quale tipo di distribuzione di istanze consente di distribuire istanze in modo uniforme tra le zone?**

a) Distribuzione qualsiasi.  
b) Distribuzione bilanciata.  
c) Distribuzione uniforme.  
d) Nessuna delle risposte precedenti.

---

**10. Quando è consigliato utilizzare i gruppi di istanze non gestiti?**

a) Quando si desidera che tutte le VM nel gruppo siano identiche.  
b) Quando si vogliono configurazioni differenti tra le istanze del gruppo.  
c) Quando si desidera scalare automaticamente le istanze.  
d) Quando si usa il bilanciamento del carico.

---

**Risposte corrette**:

1. b) Gruppi di VM identiche create usando un modello di istanza.  
2. a) Gli snapshot offrono backup incrementali, mentre le immagini sono backup completi.  
3. d) Tutte le precedenti.  
4. b) Eseguendo il comando `gcloud compute instance-templates create`.  
5. b) L'istanza viene ricreata automaticamente dal sistema.  
6. b) `gcloud compute instance-templates list`.  
7. c) I gruppi regionali distribuiscono automaticamente le istanze su più zone per aumentare la resilienza.  
8. d) Tutte le risposte precedenti.  
9. c) Distribuzione uniforme.  
10. b) Quando si vogliono configurazioni differenti tra le istanze del gruppo.


