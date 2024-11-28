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


<br><br><br>


_____________________________________________________________________________________




---

### **Test: Cloud Computing e Servizi Associati**

#### 1. Qual è una caratteristica distintiva dei servizi serverless?  
a) Richiedono configurazione manuale di server o cluster.  
b) Si adattano automaticamente al carico di lavoro senza intervento umano.  
c) Sono utilizzabili solo con VMs preconfigurate.  
d) Non supportano API per l'integrazione con altre applicazioni.  

---

#### 2. Quale dei seguenti è un tipo di peering offerto da Google Cloud?  
a) Firewall Peering.  
b) Direct Peering.  
c) Cloud Identity Peering.  
d) VM Networking Peering.  

---

#### 3. Per quale scenario è più adatto il **block storage**?  
a) Archiviazione di grandi quantità di dati senza necessità di accesso al filesystem.  
b) Creazione di dischi persistenti che continuano a esistere anche dopo lo spegnimento di una VM.  
c) Accesso rapido ai dati per ridurre la latenza.  
d) Conservazione di dati ridondanti su più regioni.  

---

#### 4. Cosa caratterizza i servizi specializzati come AutoML o Recommendations AI?  
a) Sono configurabili solo tramite console di amministrazione.  
b) Richiedono conoscenze avanzate di machine learning per essere utilizzati.  
c) Sono serverless e accessibili tramite API.  
d) Richiedono l'uso esclusivo di VPC privati.  

---

#### 5. Quale opzione è la migliore per ridurre la latenza di accesso ai dati?  
a) Caches.  
b) File storage.  
c) Object storage.  
d) Persistent block storage.  

---

#### 6. Quale dei seguenti servizi Google Cloud è serverless e progettato per rispondere ad eventi?  
a) Cloud Filestore.  
b) Cloud Functions.  
c) Cloud Run.  
d) App Engine.  

---

#### 7. Quale vantaggio offre l'object storage rispetto al block storage?  
a) Accesso rapido ai dati tramite filesystem.  
b) Scalabilità illimitata senza dipendenza dai dischi fisici.  
c) Persistenza dei dati anche dopo lo spegnimento della VM.  
d) Latenza sub-millisecond per operazioni di lettura/scrittura.  

---

#### 8. Quale strumento del cloud permette di gestire il traffico in entrata e in uscita per le subnet o le VMs?  
a) Firewall rules.  
b) Interconnects.  
c) Load balancer.  
d) Static IP settings.  

---

#### 9. Quale servizio Google Cloud è indicato per applicazioni di lunga durata come un backend di un sito web?  
a) Cloud Functions.  
b) Cloud Run.  
c) App Engine.  
d) Kubernetes Engine.  

---

#### 10. Qual è una sfida comune nell’uso delle cache?  
a) La gestione della scalabilità dinamica.  
b) Il costo elevato del filesystem associato.  
c) La sincronizzazione tra la cache e il sistema di verità.  
d) La necessità di ridondanza geografica per la disponibilità.  

---

### **Risposte corrette**
1. b) Si adattano automaticamente al carico di lavoro senza intervento umano.  
2. b) Direct Peering.  
3. b) Creazione di dischi persistenti che continuano a esistere anche dopo lo spegnimento di una VM.  
4. c) Sono serverless e accessibili tramite API.  
5. a) Caches.  
6. b) Cloud Functions.  
7. b) Scalabilità illimitata senza dipendenza dai dischi fisici.  
8. a) Firewall rules.  
9. c) App Engine.  
10. c) La sincronizzazione tra la cache e il sistema di verità.  









