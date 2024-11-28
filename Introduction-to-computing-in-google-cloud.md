# Introduction to Computing in Google Cloud



**Compute Engine**
Compute Engine è il servizio di Google Cloud che permette di creare e gestire macchine virtuali (VM) nel cloud. Una VM in esecuzione viene spesso chiamata istanza.
Immagini delle Macchine Virtuali (VM Images)

Le istanze eseguono immagini, che includono il sistema operativo, librerie e altro codice necessario. È possibile scegliere tra:

Immagini pubbliche fornite da Google, che includono sia sistemi operativi Linux sia Windows.
Immagini pubbliche di terze parti, offerte da progetti open source o fornitori esterni.


![Screenshot 2024-11-28 alle 16 40 00](https://github.com/user-attachments/assets/bfbdc4f3-5b3a-415d-b8b2-077b3fcbc9a2)
![Screenshot 2024-11-28 alle 16 40 40](https://github.com/user-attachments/assets/57883823-b65c-48e8-893f-9f0d8fa958b5)


Le **immagini pubbliche** di Google Cloud includono una vasta gamma di sistemi operativi, tra cui:  
- **Linux**: CentOS, Debian, Red Hat Enterprise Linux, SUSE Enterprise Linux Server, Ubuntu.  
- **Windows**: Windows Server.  
- **Container-Optimized OS**: un sistema operativo ottimizzato da Google per eseguire container.

### **Immagini personalizzate**  
Se nessuna delle immagini pubbliche soddisfa le tue esigenze, si può creare un'immagine personalizzata:  
1. Partendo da un disco di avvio.  
2. Modificando un'altra immagine esistente.  

### **Creazione di una VM tramite la Console**  
Per creare un'istanza VM:  
1. Vai su **Compute Engine > VM Instances**.  
2. Clicca su **Create Instance**.  
3. Configura i seguenti parametri:  
   - **Nome**: specifica un nome per l'istanza.  
   - **Configurazione della macchina**: seleziona il numero di CPU, memoria e, se necessario, aggiungi GPU.  
   - **Sicurezza**: puoi abilitare il servizio **Confidential VM**, che garantisce la crittografia dei dati in memoria.  
   - **Disco di avvio**: specifica il nome, dimensione, immagine e tipo del disco.  

### **Account di Servizio**  
Ogni VM ha un account di servizio associato. Gli account di servizio, che non rappresentano utenti umani, possono avere ruoli specifici per eseguire operazioni in Google Cloud (approfondito nel Capitolo 3).  


![Screenshot 2024-11-28 alle 16 43 22](https://github.com/user-attachments/assets/3c36b793-e1a7-4962-bf16-9dedc033399b)

Le istanze di Compute Engine permettono un controllo dettagliato delle azioni consentite grazie a meccanismi come gli **access scopes**. Questi rappresentano un sistema di controllo accessi precedente all'implementazione del servizio IAM (Identity and Access Management). Gli access scopes predefiniti garantiscono un accesso minimo, limitato alla lettura dello storage e alla scrittura sui servizi di monitoraggio e logging. Tuttavia, oggi si preferisce utilizzare IAM, che offre una gestione più flessibile e granulare dei permessi.

Inoltre, è possibile configurare il traffico consentito verso l'istanza, specificando se accettare richieste HTTP, HTTPS, o entrambe. 

Per quanto riguarda le **configurazioni di rete**, nella sezione Networking della pagina di creazione dell'istanza si possono impostare:

- **Network tags**: etichette utili per definire regole di firewall.
- **Hostname**: nome dell'host assegnato all'istanza.
- **Performance di rete**: opzioni per ottimizzare la connettività.
- **Interfacce di rete aggiuntive**: possibilità di aggiungere più schede di rete, oltre a quella predefinita. 

Queste opzioni consentono di personalizzare il comportamento dell'istanza in base alle esigenze specifiche del carico di lavoro e della sicurezza.

![Screenshot 2024-11-28 alle 16 44 36](https://github.com/user-attachments/assets/7274bb50-3b4a-4518-9b34-576c81aa67e1)




Durante la creazione di un'istanza in Compute Engine, è possibile aggiungere e configurare dischi aggiuntivi oltre al disco di avvio. Queste sono le opzioni disponibili per i dischi: 

### Configurazioni per i dischi
1. **Nome e descrizione**: Specificare un nome identificativo e una descrizione per il disco.
2. **Tipo di disco**: Scegliere tra diverse opzioni, come SSD o HDD standard.
3. **Dimensioni**: Definire la capacità del disco.
4. **Pianificazione dei backup**: Impostare una schedulazione per creare snapshot regolari del disco.
5. **Impostazioni di crittografia**:
   - **Chiavi gestite da Google**: Google crea e gestisce automaticamente le chiavi di crittografia.
   - **Chiavi gestite dal cliente**: Il cliente crea e gestisce le chiavi, ma Google le conserva.
   - **Chiavi fornite dal cliente**: Le chiavi sono create e mantenute al di fuori di Google Cloud.

Tutti i dati in Google Cloud sono crittografati **a riposo** (encryption at rest). Non è possibile archiviare dati senza crittografia, ma si può scegliere il metodo di gestione delle chiavi.

### Altre opzioni per i dischi
- **Modalità di accesso**: I dischi possono essere configurati per l'accesso in lettura/scrittura o solo in lettura.
- **Persistenza del disco**: Di default, i dischi rimangono attivi anche dopo l'eliminazione dell'istanza, ma è possibile scegliere di eliminarli automaticamente insieme all'istanza.

---

### Funzionalità di sicurezza avanzata
Nella sezione **Sicurezza**, è possibile abilitare ulteriori opzioni per migliorare la protezione:
- **Secure Boot**: Protegge contro codice malevolo a livello di boot e kernel, come i rootkit.
- **Virtual Trusted Platform Module (vTPM)**: Valida l'integrità del boot e fornisce protezioni aggiuntive per la generazione e la protezione delle chiavi.
- **Integrity Monitoring**: Disponibile se vTPM è attivato, verifica l'integrità runtime della macchina virtuale. 


![Screenshot 2024-11-28 alle 16 48 09](https://github.com/user-attachments/assets/85fa225c-c936-45d0-84eb-c7ffa80dc74b)

![Screenshot 2024-11-28 alle 16 48 45](https://github.com/user-attachments/assets/22d61bb6-236b-438a-8d07-991a5d40b2ca)

![Screenshot 2024-11-28 alle 16 49 08](https://github.com/user-attachments/assets/332683b0-ef26-455c-9a11-9edddbe4bebd)


Durante la configurazione di un'istanza in Compute Engine, si possono applicare restrizioni di accesso e ottimizzazioni avanzate. Di seguito i punti principali:

---

### **Restrizioni di Accesso**
- **Ruoli IAM**: Consentono di gestire chi può accedere a un'istanza. Per abilitare questa funzione, è necessario assegnare ruoli specifici, come:
  - **Compute OS Login role**: Accesso di base all'istanza.
  - **Compute OS Admin Login role**: Accesso amministrativo all'istanza.
- **Disabilitazione delle chiavi SSH a livello di progetto**: Evita che chiunque abbia accesso al progetto possa accedere automaticamente a tutte le istanze tramite chiavi SSH.

---

### **Gestione e Disponibilità**
1. **Opzioni di Gestione**:
   - **Blocca eliminazione dell'istanza**: Evita che l'istanza venga eliminata accidentalmente.
   - **Prenotazioni di istanze**: Permette di acquistare tempo macchina a un costo scontato.
   - **Script di automazione**: È possibile configurare script da eseguire automaticamente al riavvio dell'istanza.

2. **Preemptible e Spot VMs**:
   - **Preemptible VMs**: Meno costose, ma possono essere interrotte da Google Cloud in qualsiasi momento. Originariamente, il loro limite massimo era di 24 ore.
   - **Spot VMs**: Hanno un modello di fatturazione simile, ma non sono soggette al limite di 24 ore.

3. **Parametri di Disponibilità**:
   - **Migrazione durante la manutenzione**: Decide se migrare automaticamente l'istanza durante una manutenzione del server.
   - **Riavvio automatico**: Configura il riavvio in caso di errori hardware o altre interruzioni.

---

### **Sole Tenancy**
- **Esclusività del server**: Permette di isolare le istanze in modo che solo quelle del progetto possano condividere lo stesso server fisico.
- **Affinità dei nodi**: Specifica etichette per assicurarsi che solo le istanze con etichette corrispondenti possano coesistere.
- **Overcommit delle CPU**: Migliora le prestazioni sfruttando al massimo le risorse del server quando le istanze non utilizzano tutte le CPU assegnate contemporaneamente.

---

### **Template e Machine Images**
1. **Template di istanza**:
   - Un template salva la configurazione di una VM. È utile per creare nuove istanze con parametri predefiniti senza doverli configurare ogni volta.

2. **Machine Images**:
   - Si può creare un'immagine della macchina virtuale da un'istanza esistente. 
   - Parametri configurabili:
     - Nome e descrizione.
     - VM di origine.
     - Posizione di archiviazione.
     - Gestione delle chiavi di crittografia.

Ecco un riepilogo delle caratteristiche principali e delle opzioni di Google Compute Engine, con un focus su macchine virtuali (VM), configurazioni personalizzate e usi pratici:

---

### **Macchine Virtuali e Progetti**
- **Progetti**: Le VM sono contenute nei progetti, che rappresentano il livello più basso nella gerarchia delle risorse di Google Cloud.
  - Ogni progetto può gestire risorse con policy comuni.
  - La creazione di una VM richiede l'assegnazione a un progetto.

---

### **Zone e Regioni**
- **Zone**: Rappresentano risorse simili a data center, all'interno delle regioni.
- **Regioni**: Suddivisioni geografiche globali (es. `us-east4`, `europe-west2`).
  - Fattori da considerare nella scelta:
    - **Costo**: Varia tra le regioni.
    - **Localizzazione dei dati**: Ad esempio, per conformarsi alle normative dell'UE.
    - **Alta disponibilità**: Distribuire VM in zone o regioni diverse per garantire continuità del servizio.
    - **Bassa latenza**: Avvicinare VM agli utenti finali per migliorare le prestazioni.
    - **Disponibilità hardware**: Alcuni processori sono disponibili solo in specifiche regioni.
    - **Impatto ambientale**: Preferire regioni con minore intensità di carbonio.

---

### **Ruoli e Permessi**
- **Ruoli IAM**:
  - **Compute Admin**: Controllo completo delle istanze Compute Engine.
  - **Compute Network Admin**: Gestione delle risorse di rete, con accesso limitato a firewall e SSL.
  - **Compute Security Admin**: Gestione di certificati SSL e regole firewall.
  - **Compute Viewer**: Solo visualizzazione delle risorse Compute Engine.
- **Livelli di accesso**:
  - A livello di progetto: I permessi si applicano a tutte le risorse del progetto.
  - A livello di risorsa: Permette di personalizzare i permessi per singole VM.

---

### **Preemptible e Spot VMs**
- **Preemptible VMs**:
  - Ideali per carichi di lavoro non critici (es. analisi big data, rendering).
  - Limitazioni:
    - Durata massima di 24 ore.
    - Nessuna migrazione o riavvio automatico.
    - Disponibilità limitata e senza SLA.
- **Spot VMs**: Simili alle Preemptible, ma senza il limite di 24 ore.

---

### **Macchine Virtuali Personalizzate**
- **Tipi predefiniti**:
  - Gruppi: Standard, High-Memory, High-CPU, Shared Core, Memory-Optimized.
  - Esempi: 
    - `n2-standard-2`: 2 vCPU, 8 GB RAM.
    - `m2-megamem-416`: 416 vCPU, 5.75 TB RAM.
- **Tipi personalizzati**:
  - Si possono configurare vCPU e RAM in base alle esigenze.
  - Le opzioni dipendono dalla serie (es. N2: fino a 80 vCPU e 640 GB RAM; N2D: fino a 96 vCPU e 768 GB RAM).
  - Il costo si basa sulle risorse configurate.

---

### **Casi d'Uso di Compute Engine**
Compute Engine è indicato per scenari che richiedono controllo completo:
- **Configurazione flessibile**: Scegliere immagini, installare software, configurare firewall e certificati SSL.
- **Carico amministrativo**: Più controllo implica maggiore responsabilità per la gestione delle risorse.
- **Uso combinato con altri servizi**: Ad esempio, un cluster di VM affidabili con VM preemptible per ridurre i costi.

Nota:
<pre>
Compute Engine è adatto per utenti che necessitano di risorse altamente configurabili e non temono di assumersi la responsabilità di gestirle.

  
</pre>





