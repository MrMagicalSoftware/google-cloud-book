# Computing with compute engine virtual machines



Per creare e configurare una macchina virtuale (VM) in Google Cloud, si può utilizzare la Console di Google Cloud, il Software Development Kit (SDK) di Google Cloud o Google Cloud Shell.
In questo caso, vedremo come farlo tramite la Console di Google Cloud, che è una GUI web per la gestione delle risorse.

Per iniziare, si accede al sito https://console.cloud.google.com nel  browser e si accede all' account. 
Una volta dentro,  selezionare un progetto esistente o crearne uno nuovo. 
Se è la prima volta che si lavora con una VM, potrebbe essere necessario configurare un account di fatturazione. 
In tal caso, vi verrà chiesto di fornire informazioni come nome, indirizzo e i dati della tua carta di credito. Una volta configurato l'account di fatturazione, si può accedere alla sezione di Compute Engine della console.

Per creare una nuova VM, clicca sul pulsante "Create Instance" che si trova nella parte superiore del pannello. Questo  permetterà di visualizzare il modulo di configurazione della VM, si potrà impostare i dettagli della macchina virtuale, come la zona, il tipo di macchina e il sistema operativo.

<img width="954" alt="Screenshot 2024-12-01 alle 16 08 19" src="https://github.com/user-attachments/assets/3d1af832-adc3-4075-8f1f-2fb8ff47903d">
<img width="949" alt="Screenshot 2024-12-01 alle 16 08 45" src="https://github.com/user-attachments/assets/610ea2ab-8de8-4df4-9900-567e3d68191c">
<img width="752" alt="Screenshot 2024-12-01 alle 16 09 06" src="https://github.com/user-attachments/assets/b46a8e7f-8d1f-4799-86ab-d22f63641303">
<img width="734" alt="Screenshot 2024-12-01 alle 16 09 27" src="https://github.com/user-attachments/assets/89b73afb-d2d8-41ec-91a1-9534fdf0658e">
<img width="457" alt="Screenshot 2024-12-01 alle 16 09 55" src="https://github.com/user-attachments/assets/3db9f74e-3547-40dc-9885-4e575b269355">


<img width="835" alt="Screenshot 2024-12-02 alle 07 38 05" src="https://github.com/user-attachments/assets/15aae62f-7829-4b21-aa55-2581757a4900">



Quando si configura una macchina virtuale (VM) in Google Cloud, dopo aver selezionato una regione e una zona, il sistema determina le VM disponibili in quella specifica zona. È importante notare che non tutte le zone offrono la stessa disponibilità di configurazioni. Ad esempio, per la serie E2 nella zona **us-east1-b**, sono elencati i tipi di macchina disponibili.

Google Cloud organizza le macchine virtuali in tre livelli principali: **famiglie di macchine**, **serie** e **tipi di macchina**. 

1. **Famiglie di macchine**: si riferiscono a insiemi di configurazioni hardware e di processori progettati per determinati carichi di lavoro, come scopi generici, ottimizzati per il calcolo o per la memoria.
2. **Serie**: all'interno di ogni famiglia, le macchine sono ulteriormente suddivise in serie e generazioni.
3. **Tipi di macchina**: all'interno di una serie, è possibile scegliere tra diversi tipi di macchina, che variano in base al numero di CPU virtuali e alla quantità di memoria.

Per applicazioni che richiedono un elevato livello di sicurezza, è possibile abilitare il servizio **Confidential VM**. Questo servizio mantiene i dati in memoria crittografati utilizzando chiavi di crittografia alle quali Google non ha accesso, garantendo così un maggiore isolamento e protezione.


<img width="589" alt="Screenshot 2024-12-02 alle 07 40 15" src="https://github.com/user-attachments/assets/0745f95b-2e06-48d9-8ace-c3dfe2aeeefe">


<img width="610" alt="Screenshot 2024-12-02 alle 07 41 29" src="https://github.com/user-attachments/assets/fdb79f02-7c85-438a-befe-04dcda6bfa79">


Quando si configura una macchina virtuale (VM) in Google Cloud, si ha  l’opzione di eseguire un **container** direttamente nella VM. In tal caso, è necessario specificare un container presente in un repository pubblico o nel **Google Container Registry**. Questa funzionalità è utile per eseguire container con software specializzato o configurazioni personalizzate.

### Configurazione del Disco di Avvio
Nella sezione del **Boot Disk**, viene mostrata una configurazione predefinita. Facendo clic su **Change**, si può selezionare il sistema operativo desiderato e specificare il tipo e la dimensione del disco di avvio. Le opzioni per il disco includono:
- **Balanced Persistent Disk**: SSD con un equilibrio tra costi e prestazioni.
- **Extreme Persistent Disk**: SSD ad alte prestazioni con input-output operations per second (IOPS) configurabili.
- **SSD Persistent Disk**: dischi solid-state per prestazioni elevate.
- **Standard Persistent Disk**: HDD tradizionali, ideali per costi contenuti.

### Identità e Accesso alle API
Nella sezione **Identity and API Access**, si può:
- Specificare un **account di servizio** per la VM.
- Definire l'ambito di accesso alle API, limitando le API che possono essere utilizzate dai processi della VM.

### Traffico HTTP/HTTPS
Puoi selezionare se la VM deve accettare traffico HTTP e/o HTTPS. Questa configurazione è utile per i server web o applicazioni esposte su Internet.

### Configurazioni Avanzate
Facendo clic su **Management, Security, Disks, Networking, and Sole Tenancy**, si può accedere a opzioni avanzate.

#### Tab Gestione (Management)
Nella scheda **Management**, si può:
- Inserire una descrizione della VM.
- Aggiungere **etichette** (key-value pairs) per organizzare e identificare le VM in ambienti complessi con numerosi server. Utilizzare descrizioni e etichette è una **best practice** per mantenere una gestione ordinata delle risorse.

<img width="538" alt="Screenshot 2024-12-02 alle 07 45 25" src="https://github.com/user-attachments/assets/f0721564-7eed-4531-8525-d1d9ab15d46a">


Quando si configura una macchina virtuale (VM) su Google Cloud, si può scegliere diverse opzioni avanzate per personalizzare il  comportamento e la sua gestione:

### **Protezione dalla Cancellazione**
È possibile attivare la **Deletion Protection** per impedire eliminazioni accidentali. Se abilitata, qualsiasi tentativo di eliminare l'istanza fallirà.

### **Script di Avvio e Metadata**
SI può definire uno **startup script** in linguaggi come Bash o Python, copiandolo direttamente in un'apposita sezione. Inoltre, è possibile aggiungere **metadata**, che consistono in coppie chiave-valore memorizzate in un server di metadati. Questi dati possono essere utilizzati per personalizzare il comportamento degli script o altre configurazioni della VM.

### **Policy di Disponibilità**
Nella sezione **Availability Policy**, ci sono opzioni come:
- **VM Provisioning Model**: scegliere tra una modalità standard o spot (più economica ma soggetta a interruzioni con un preavviso di 30 secondi).
- **On Host Maintenance**: indicare se la VM deve essere migrata in caso di manutenzione del server fisico.
- **Automatic Restart**: specificare se la VM deve riavviarsi automaticamente in caso di guasti.

### **Sicurezza**
La scheda **Security** consente di abilitare funzionalità come:
- **Shielded VM**, che include:
  - **Secure Boot**: verifica l'autenticità del software di avvio tramite firme digitali.
  - **Virtual Trusted Platform Module (vTPM)**: fornisce una sicurezza aggiuntiva per chiavi e certificati.
  - **Integrity Monitoring**: confronta le misurazioni di avvio con una baseline per rilevare anomalie.
- **Chiavi SSH a livello di progetto**: puoi consentire o bloccare l'accesso tramite chiavi SSH condivise per tutti gli utenti del progetto.

### **Dischi di Avvio e Aggiuntivi**
Nel pannello **Boot Disk**, puoi decidere:
- Se eliminare il disco quando viene eliminata la VM.
- Il tipo di gestione delle chiavi di cifratura (gestite da Google, dal cliente o fornite dal cliente stesso).
Puoi anche aggiungere nuovi dischi o collegare dischi esistenti. I dischi possono essere configurati come **Read/Write** o **Read-Only** e possono essere conservati o eliminati insieme alla VM.

### **Rete**
Nella scheda **Networking**, si può configurare:
- Interfacce di rete, incluso l'indirizzo IP.
- Interfacce multiple per connettere la VM a più reti, utili per scenari come proxy o gestione del traffico.
- **Network tags** per categorizzare e gestire le VM.

### **Tenancy Dedicata**
Se si ha  bisogno che le  VM girino esclusivamente su server dedicati ai  workload, si piò scegliere l'opzione di **Sole Tenancy**. Questa configurazione consente:
- Overcommitting delle risorse CPU (se il server ha almeno quattro CPU).
- Uso di **node affinity labels** per definire su quali nodi fisici le VM possono essere eseguite.

Queste opzioni avanzate  permettono di ottimizzare le VM per casi d'uso specifici, migliorando la sicurezza, le prestazioni e la gestione operativa.



____________________________________________________________



### Domande a Risposta Multipla

1. **Cosa permette di fare l'opzione Deletion Protection su una VM?**  
   - a) Proteggere i dati memorizzati nel disco di avvio.  
   - b) Impedire l'eliminazione accidentale della VM.  
   - c) Migrare automaticamente la VM in caso di manutenzione.  
   - d) Bloccare l'accesso tramite chiavi SSH.

2. **Qual è lo scopo principale dei metadata associati a una VM?**  
   - a) Memorizzare informazioni per la configurazione delle reti.  
   - b) Fornire coppie chiave-valore per personalizzare script e configurazioni.  
   - c) Proteggere la VM con firme digitali.  
   - d) Permettere il riavvio automatico della VM in caso di guasti.

3. **Quale vantaggio offre il provisioning modello spot?**  
   - a) La VM è protetta da cancellazioni accidentali.  
   - b) Il costo della VM è più basso rispetto al provisioning standard.  
   - c) La VM non si ferma mai per motivi di manutenzione.  
   - d) Garantisce una maggiore sicurezza con Shielded VM.

4. **Quale delle seguenti opzioni è una funzionalità di Shielded VM?**  
   - a) Secure Boot.  
   - b) Aggiunta automatica di dischi aggiuntivi.  
   - c) Virtual Trusted Platform Module (vTPM).  
   - d) Integrity Monitoring.  

5. **Cosa consente di configurare nella scheda Boot Disk di una VM?**  
   - a) L'eliminazione automatica del disco insieme alla VM.  
   - b) L'indirizzo IP statico della VM.  
   - c) Il tipo di rete utilizzato dalla VM.  
   - d) La dimensione e il tipo di disco.

6. **Cosa permette di fare la scheda Networking?**  
   - a) Aggiungere o collegare dischi aggiuntivi.  
   - b) Configurare le interfacce di rete della VM.  
   - c) Selezionare un modello di provisioning spot.  
   - d) Definire le chiavi di crittografia del disco.

7. **Cosa rappresenta la configurazione Sole Tenancy?**  
   - a) Un'opzione per utilizzare dischi SSD estremamente performanti.  
   - b) La possibilità di far girare le VM solo su nodi dedicati al proprio progetto.  
   - c) Un'opzione per evitare il riavvio automatico delle VM.  
   - d) Una modalità di configurazione per aumentare la sicurezza delle VM.

8. **Qual è una funzionalità del Virtual Trusted Platform Module (vTPM)?**  
   - a) Migrare la VM durante eventi di manutenzione.  
   - b) Proteggere risorse come chiavi e certificati.  
   - c) Permettere l'accesso a specifiche API.  
   - d) Gestire il traffico tra reti multiple.

---

### Risposte  
1. **b**  
2. **b**  
3. **b**  
4. **a, c, d**  
5. **a, d**  
6. **b**  
7. **b**  
8. **b**



























