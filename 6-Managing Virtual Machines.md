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



_____________________________________
















_____________________________________
