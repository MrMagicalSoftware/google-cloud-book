
# Computing with Kubernetes.md

Kubernetes, un sistema di orchestrazione dei container creato e open-sourced da Google.  l'architettura di Kubernetes serve a gestisce i carichi di lavoro sui nodi di un cluster. Inoltre, viene esplorato come gestire le risorse di Kubernetes tramite Cloud Console, Cloud Shell e Cloud SDK, nonché come distribuire i pod dell'applicazione, monitorare e registrare le risorse Kubernetes.

### Introduzione a Kubernetes Engine (GKE)

**Google Kubernetes Engine (GKE)** è un servizio di Kubernetes gestito da Google Cloud che permette agli utenti di creare e mantenere cluster Kubernetes senza doversi preoccupare della gestione della piattaforma Kubernetes. Kubernetes esegue i container su un cluster di macchine virtuali (VM), determinando dove eseguire i container, monitorando la salute dei container e gestendo l'intero ciclo di vita delle istanze VM. Questa gestione è nota come "orchestrazione dei container".

Anche se i **gruppi di istanze** possono sembrare simili a un cluster Kubernetes, ci sono differenze significative. In effetti, GKE utilizza i gruppi di istanze per gestire le VM sottostanti nei cluster GKE. I container sono più leggeri e veloci rispetto alle VM tradizionali e non richiedono la replicazione di un sistema operativo completo.

### Architettura di Kubernetes

Un cluster Kubernetes è composto da due principali componenti:

- **Control Plane**: gestisce il cluster e può essere replicato per alta disponibilità e tolleranza ai guasti. Gestisce i servizi come l'API Kubernetes, i controller e gli scheduler.
  
- **Nodes**: sono le macchine (tipicamente VM) che eseguono i carichi di lavoro nel cluster. Ogni nodo esegue un agente chiamato **kubelet** che comunica con il control plane.

Alcuni dei componenti principali del **Control Plane** includono:
- **API Server**: espone l'API Kubernetes.
- **Scheduler**: assegna i pod ai nodi.
- **Controller Manager**: gestisce i controller delle risorse come il node controller.
- **etcd**: un archivio chiave-valore altamente disponibile.
- **Kubelet**: un agente che esegue su ogni nodo.
- **Container Runtime**: gestisce l'esecuzione dei container.
- **Kube-proxy**: un proxy di rete che gira su ogni nodo.

### Oggetti Kubernetes

I carichi di lavoro sono distribuiti sui nodi in un cluster Kubernetes, e per capire come il lavoro è distribuito, è importante conoscere alcuni oggetti fondamentali:

- **Pods**: sono singole istanze di un processo in esecuzione nel cluster. Ogni pod può contenere uno o più container.
- **Services**: forniscono un punto di accesso stabile per le applicazioni in esecuzione nei pod.
- **Deployments**: sono insiemi di pod identici, che vengono gestiti tramite un controller chiamato **ReplicaSet**.
- **ReplicaSets**: assicurano che il numero corretto di pod identici sia in esecuzione.
- **StatefulSets**: simili ai deployments, ma assegnano identificatori unici ai pod, utili per applicazioni che necessitano di identità o archiviazione persistente.
- **Jobs**: creano pod per eseguire un lavoro finché non viene completato.
- **Volumes**: forniscono una soluzione di archiviazione persistente per i dati, anche se un pod fallisce o viene riavviato.
- **Namespaces**: un'astrazione logica che separa le risorse nel cluster per progetti, team o gruppi diversi.
- **Node Pools**: gruppi di nodi con configurazioni simili, che possono essere aggiunti a un cluster per gestire nodi con caratteristiche specifiche, come nodi su VM preemptible.


<img width="624" alt="Screenshot 2024-12-02 alle 08 39 46" src="https://github.com/user-attachments/assets/367b4386-72ed-4ed9-acc6-0ee529d0f73b">

<img width="644" alt="Screenshot 2024-12-02 alle 08 40 43" src="https://github.com/user-attachments/assets/c7d071e7-a2bb-4cff-b644-248632bf9e24">

<img width="614" alt="Screenshot 2024-12-02 alle 08 41 09" src="https://github.com/user-attachments/assets/3da8a964-188e-486e-84f8-538ea4628ab0">



### Distribuire Cluster Kubernetes

I cluster Kubernetes possono essere distribuiti utilizzando **Cloud Console**, la riga di comando in **Cloud Shell**, o l'ambiente locale se è installato il **Cloud SDK**.

### Distribuire Cluster Kubernetes tramite Cloud Console

Per utilizzare **Kubernetes Engine (GKE)**, è necessario abilitare l'API di Kubernetes Engine. Una volta abilitata l'API, puoi accedere alla pagina **Kubernetes Engine** nella Cloud Console.

Quando crei un cluster, hai l'opzione di scegliere tra due modalità:

1. **Modalità standard**: Paghi per le risorse del cluster che configuri, gestisci l'infrastruttura dei nodi e determini la configurazione dei nodi.
2. **Modalità autopilot**: GKE gestisce l'infrastruttura del cluster e dei nodi, e paghi solo per le risorse utilizzate quando le applicazioni sono in esecuzione. La modalità autopilot è quella consigliata poiché GKE ottimizza e preconfigura la gestione del cluster.

In **modalità autopilot**, GKE gestisce automaticamente l'infrastruttura dei nodi, la rete VPC-nativa per il traffico pubblico e privato, utilizza nodi **Shielded GKE** (più sicuri) e offre funzionalità di logging e monitoraggio. Devi solo specificare il nome del cluster, la descrizione e la regione in cui creare il cluster. Inoltre, puoi scegliere se il cluster deve essere **privato** o **pubblico**.

- **Cluster privati**: I nodi hanno solo indirizzi IP privati, e tutta la comunicazione tra il piano di controllo e i nodi avviene tramite indirizzi privati. Questo aumenta la sicurezza, isolando il traffico da IP non autorizzati.
- **Cluster pubblici**: I nodi hanno indirizzi IP pubblici, e la comunicazione può avvenire tramite l'Internet pubblico.

### Opzioni di rete avanzate

Nella sezione **Networking Options** della creazione di un cluster autopilot, puoi abilitare ulteriori configurazioni di rete, come:

- **Authorized Networks**: abilita solo le reti di Google Cloud per accedere al piano di controllo tramite HTTPS, bloccando IP non fidati.
- Specifica la rete, la sottorete dei nodi e gli intervalli di indirizzi per i pod e i servizi, usando la notazione CIDR, ad esempio `192.168.0.0/16`.
  
Inoltre, puoi configurare una **finestra di manutenzione** per definire un orario preferito per eseguire operazioni di manutenzione di routine su Kubernetes. Per default, queste operazioni possono essere eseguite in qualsiasi momento.

### Funzionalità di sicurezza

Puoi abilitare varie funzionalità di sicurezza, tra cui:

- **Google Groups per RBAC**: per concedere ruoli ai membri di un Google Workspace Group.
- **Crittografia dei segreti**: per criptare i segreti memorizzati in **etcd**, la parte del piano di controllo di Kubernetes.
- **Chiavi gestite dal cliente**: per criptare il disco di avvio dei nodi, migliorando la sicurezza dei dati.

### Gestione dei cluster

Una volta che il cluster è stato creato, dalla pagina di elenco dei cluster puoi:

- **Modificare**, **eliminare** o **connetterti** al cluster.
- Quando clicchi su **Connetti**, riceverai un comando **gcloud** per connetterti al cluster dalla riga di comando.

Puoi anche visualizzare la pagina **Workloads**, dove puoi monitorare e gestire le applicazioni in esecuzione nel cluster.

### Configurazione di un Cluster in Modalità Standard

Se scegli di creare un cluster in **modalità standard**, vedrai un modulo che ti permetterà di configurare il nome e la posizione del cluster. Se scegli di creare un **cluster zonale**, la posizione sarà una zona. Se scegli di creare un **cluster regionale**, la posizione sarà una regione. I cluster regionali, per default, hanno nodi distribuiti su tre zone, ma puoi specificare zone specifiche se preferisci.

I cluster sono configurati per default con un **Release Channel**, che abilita l'aggiornamento automatico del software del cluster. Se preferisci un controllo maggiore sul processo di aggiornamento, puoi scegliere di configurare un **canale statico**, che non aggiorna automaticamente il software del cluster.

---


______________________________



Ecco il test riscritto con le risposte distribuite in modo casuale:

### Domande

1. **Che cos'è Google Kubernetes Engine (GKE)?**
   - A) Un sistema di gestione dei database
   - B) Un servizio che consente di gestire e distribuire cluster Kubernetes su Google Cloud
   - C) Un servizio di gestione dei dati su Google Cloud
   - D) Un sistema di virtualizzazione delle macchine

2. **Qual è la principale differenza tra la modalità standard e la modalità autopilot in GKE?**
   - A) In modalità autopilot, GKE gestisce l'infrastruttura e i nodi, mentre in modalità standard l'utente gestisce l'infrastruttura e le risorse del nodo.
   - B) In modalità standard, GKE gestisce l'infrastruttura, mentre in modalità autopilot l'utente deve gestirla.
   - C) In entrambe le modalità, GKE gestisce completamente l'infrastruttura.
   - D) La modalità standard è più sicura della modalità autopilot.

3. **Cosa succede se si crea un cluster privato in GKE?**
   - A) Il traffico tra il piano di controllo e i nodi avverrà tramite indirizzi privati.
   - B) I nodi del cluster avranno indirizzi IP pubblici.
   - C) Non è possibile configurare un cluster privato in GKE.
   - D) Il cluster avrà un accesso pubblico limitato.

4. **Cosa fa la funzionalità "Authorized Networks" quando viene abilitata in GKE?**
   - A) Blocco il traffico tra i nodi del cluster.
   - B) Limita l'accesso al piano di controllo del cluster solo alle reti di Google Cloud.
   - C) Permette solo gli utenti con un account Google a connettersi al cluster.
   - D) Aumenta la disponibilità del cluster in più regioni.

5. **Cosa è possibile configurare durante la creazione di un cluster in modalità autopilot?**
   - A) Il numero di nodi che compongono il cluster.
   - B) La regione e la configurazione della rete per il cluster.
   - C) Le risorse del nodo, poiché GKE gestisce tutto.
   - D) Nessuna delle precedenti.

6. **Cos'è un "Release Channel" in GKE?**
   - A) Un canale per l'accesso a software aggiuntivo su GKE.
   - B) Una configurazione che consente agli utenti di bypassare gli aggiornamenti di GKE.
   - C) Un sistema di aggiornamento automatico del cluster.
   - D) Una funzione che consente agli utenti di accedere a versioni sperimentali di Kubernetes.

### Risposte corrette

1. **B**: Google Kubernetes Engine è un servizio che consente di gestire e distribuire cluster Kubernetes su Google Cloud.
2. **A**: In modalità autopilot, GKE gestisce l'infrastruttura e i nodi, mentre in modalità standard l'utente gestisce l'infrastruttura e le risorse del nodo.
3. **A**: In un cluster privato, il traffico tra il piano di controllo e i nodi avviene tramite indirizzi privati.
4. **B**: "Authorized Networks" limita l'accesso al piano di controllo del cluster solo alle reti di Google Cloud.
5. **B**: In modalità autopilot, è possibile configurare la regione e la rete, ma GKE gestisce le risorse del nodo.
6. **C**: Un "Release Channel" è un sistema di aggiornamento automatico del cluster.





















