# types of cloud services

I provider di cloud pubblico come Google, Amazon e Microsoft offrono una vasta gamma di servizi per infrastrutture di calcolo, archiviazione, rete e servizi specializzati per supportare applicazioni e servizi aziendali. 

Ci sono due principali tipologie di utenti del cloud:  
1. **Startup e nuove aziende**: iniziano direttamente nel cloud e scelgono servizi adatti alle loro esigenze senza preoccuparsi di infrastrutture esistenti. Ad esempio, possono utilizzare servizi come Google Cloud Identity per la gestione delle identità.  
2. **Grandi imprese con data center propri**: integrano il cloud con le infrastrutture esistenti. Questo comporta sfide, come l'integrazione tra i sistemi di identità esistenti (es. Microsoft Active Directory) e quelli del cloud, oltre alla gestione di reti sicure tra il cloud e le risorse locali.

Per la connessione tra data center on-premises e cloud, le imprese possono optare per:  
- **Connessioni dedicate** (costose ma adatte a traffico elevato).  
- **VPN su Internet pubblico** (più economiche ma richiedono maggiore gestione).

I servizi offerti dai provider cloud rientrano in quattro categorie principali:  
- **Risorse di calcolo**  
- **Archiviazione**  
- **Networking**  
- **Servizi specializzati** (ad esempio, machine learning).

In genere, i clienti combinano servizi di più categorie per soddisfare le proprie necessità.





**Risorse di calcolo nel cloud pubblico**  
- **Virtual Machines (VMs):** Unità base di risorse di calcolo. Si possono configurare, gestire e scalare manualmente o automaticamente. Utili per personalizzazione completa e alta disponibilità.  
- **Cluster Kubernetes gestiti:** Usano container per isolare processi. La gestione del cluster è automatizzata (monitoraggio, scalabilità). Ideali per applicazioni basate su microservizi.  
- **Computing serverless:** Elimina la necessità di gestire infrastrutture (es. VMs). Opzioni:  
  - **App Engine:** Per applicazioni di lunga durata.  
  - **Cloud Run:** Per container con rapida scalabilità.  
  - **Cloud Functions:** Per eseguire codice in risposta a eventi.

**Tipologie di storage nel cloud**  
- **Object storage:** Archivia oggetti (es. file) in bucket accessibili via URL. È scalabile, serverless, e ridondante, ma non adatto all'accesso a livello di filesystem.  
- **File storage:** Sistemi gerarchici per l'accesso tradizionale ai file (es. NFS). Decouplati dalle VMs.  
- **Block storage:** Archivia dati in blocchi fissi. Adatto a dischi persistenti (indipendenti dalla vita della VM) o effimeri (dati persi alla chiusura della VM). Permette accesso rapido a livello di filesystem.  
- **Cache:** Memorie in RAM per ridurre la latenza (es. submillisecondi). Utili per accesso rapido, ma volatili e costose. Richiedono strategie per mantenere coerenza con i dati persistenti.

**Confronto tra storage**  
- **Cache:** Velocissima ma volatile e cara.  
- **Block storage:** Veloce e persistente.  
- **Object storage:** Scalabile ma più lento, utile per grandi volumi di dati.  

La scelta tra VMs, cluster gestiti o computing serverless, e tra diversi tipi di storage, dipende dalle esigenze di scalabilità, personalizzazione e costi.


### Riassunto sintetico in italiano

**Networking nel cloud**  
- **Indirizzi IP:** Ogni dispositivo o servizio nel cloud necessita di un IP. Esistono:  
  - **Indirizzi interni:** Accessibili solo nella rete privata virtuale (VPC).  
  - **Indirizzi esterni:** Accessibili da Internet, possono essere statici o effimeri (rilasciati quando una VM si spegne).  
- **Firewall:** Regolano il traffico in entrata/uscita nelle subnet o VMs, per esempio limitando l’accesso a un database solo ai server applicativi.  
- **Peering:** Consente di collegare reti distinte (es. tra data center on-premises e VPC) attraverso VPN, Interconnects o altre soluzioni.

**Servizi specializzati**  
- Offrono funzionalità avanzate come traduzioni, analisi di immagini o testi tramite API, senza dover configurare server.  
- Esempi in Google Cloud:  
  - **AutoML:** Machine learning.  
  - **Cloud Natural Language:** Analisi del testo.  
  - **Speech-to-Text:** Conversione voce-testo.  
  - **Recommendations AI:** Raccomandazioni personalizzate.  
- Rendono accessibili tecnologie avanzate anche a chi non è esperto in machine learning o elaborazione del linguaggio naturale.

**Cloud Computing vs Data Center tradizionali**  
- **Cloud:** Si noleggiano risorse su richiesta, pagando in base all'uso. Ideale per gestire picchi di carico (es. vendite stagionali) senza investire in hardware.  
- **Data Center:** Implica acquisto o leasing a lungo termine di server e attrezzature, utile per carichi costanti ma inefficiente per variazioni significative.  

**Vantaggi dei servizi specializzati nel cloud**  
- Accessibilità economica grazie alla condivisione dei costi tra più utenti.  
- Democratizzazione di tecnologie avanzate per sviluppatori e aziende senza risorse interne per ricerca e sviluppo.
