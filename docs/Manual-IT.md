> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; 🇮🇹 IT &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manuale Moduli di Feedback OS-S88n

**Supporta: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Tutte e tre le varianti del modulo OS-S88n](all.png)

*Da sinistra a destra: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Introduzione

I moduli OS-S88n forniscono funzionalità di feedback per plastici ferroviari DCC utilizzando il protocollo S88n standardizzato. Questi moduli consentono il monitoraggio in tempo reale dell'occupazione dei blocchi e degli eventi del plastico, inviando i dati alla propria centrale di comando o al software di controllo su PC.

Sono disponibili tre varianti per soddisfare diverse esigenze di rilevamento:

- **OS-S88n GND** — rilevamento a contatto con la massa, adatto per plastici a 3 rotaie (stile Märklin)
- **OS-S88n CS** — rilevamento a sensore di corrente, adatto per plastici digitali a 2 e 3 rotaie
- **OS-S88n OPTO** — ingressi digitali optoisolati, da utilizzare con sensori esterni come rilevatori IR o sensori Hall

Tutte le varianti includono:

- Connettori S88n a cascata (RJ-45)
- Morsetti a vite per tutte le connessioni dei sensori
- Compatibilità con tutte le principali centrali di comando e software (iTrain, Rocrail, Windigipet, ecc.)

---

## Varianti del Modulo

### OS-S88n GND — Rilevamento a Contatto con la Massa

![Scheda OS-S88n GND](OS-S88n-GND.png)

Il modulo GND dispone di 16 ingressi che si attivano quando l'ingresso viene portato a massa. I sensori e i metodi di rilevamento compatibili includono:

- Contatti Reed
- Pulsanti
- Assili metallici che cortocircuitano le rotaie su un plastico a 3 rotaie (stile Märklin)

⚠️ **Importante — plastici a 3 rotaie:** quando si utilizza il modulo GND su un plastico a 3 rotaie, la propria centrale di comando e tutti i booster **devono** essere del tipo a massa comune. Se la centrale di comando utilizza un'uscita a ponte H, l'utilizzo del modulo GND **danneggerà la centrale**. In tal caso utilizzare invece la variante OPTO.

---

### OS-S88n CS — Sensore di Corrente

![Scheda OS-S88n CS](OS-S88n-CS.png)

Il modulo CS dispone di 16 ingressi che si attivano ogni volta che viene assorbita corrente attraverso una sezione di binario monitorata. Qualsiasi materiale rotabile che assorbe corrente attiverà il rilevamento, inclusi:

- Locomotive
- Carrozze illuminate
- Vagoni dotati di resistore a scopo di rilevamento

Adatto sia per plastici digitali a 2 che a 3 rotaie.

---

### OS-S88n OPTO — Rilevamento a Ingresso Optoisolato

![Scheda OS-S88n OPTO](OS-S88n-OPTO.png)

Il modulo OPTO dispone di 16 ingressi digitali completamente optoisolati. Il pieno isolamento galvanico tra i sensori e il bus S88 rende questa variante ideale per:

- Rilevatori IR
- Sensori Hall
- Interruttori situati lontano dal modulo
- Ambienti sensibili ai disturbi
- Plastici in cui i loop di massa o le interferenze elettriche rappresentano un problema

⚠️ Il modulo OPTO **non** rileva di per sé l'occupazione del binario — richiede sensori esterni che forniscano un segnale a livello logico.

---

## Caratteristiche

- Completamente compatibile con il protocollo di feedback S88n
- Connettori RJ-45 per il collegamento a cascata dei moduli
- 16 ingressi per modulo
- Fino a 31 moduli in una singola catena
- Morsetti a vite per tutte le connessioni dei sensori
- La versione OPTO fornisce pieno isolamento galvanico

---

## Collegamento dei Moduli

### Alimentazione e Segnale

Collegare i moduli alla propria centrale di comando utilizzando cavi Ethernet UTP standard. **Tutti gli 8 fili devono essere collegati** — evitare cavi patch di bassa qualità che omettono alcuni fili interni.

- Connettore **S88n OUT** → ingresso S88n della centrale (o ingresso IN del modulo precedente)
- Connettore **S88n IN** → modulo successivo nella catena (lasciare vuoto sull'ultimo modulo)

### Cablaggio dei Sensori

**OS-S88n CS — sensore di corrente**

![Cablaggio della versione a sensore di corrente](image.png)

Instradare i fili di alimentazione del binario per ciascuna sezione di rilevamento attraverso gli ingressi del sensore di corrente. Qualsiasi treno che assorba corrente in quella sezione attiva l'ingresso corrispondente.

---

**OS-S88n GND — contatto con la massa**

![Cablaggio della versione GND](image-1.png)

Collegare una rotaia (o l'uscita del sensore) a un morsetto di ingresso e la rotaia comune al morsetto COM. Gli assili che cortocircuitano entrambe le rotaie completano il circuito verso la massa e attivano l'ingresso.

⚠️ *Quando si utilizza la versione GND su un plastico a 3 rotaie, è indispensabile che la centrale e i booster siano del tipo a massa comune. Se si utilizza la versione GND con una centrale a ponte H, si danneggerà la centrale. Utilizzare invece la variante OPTO.*

---

**OS-S88n OPTO — optoisolato**

![Cablaggio della versione OPTO](image-3.png)

Collegare l'uscita del segnale del sensore al morsetto di ingresso e la massa del sensore al morsetto COM. La tensione di ingresso dipende dall'alimentazione del sensore; verificare le indicazioni sulla scheda per il campo supportato.

---

**Collegamento a cascata di più moduli**

![Collegamento a cascata di più moduli OS-S88n](image-2.png)

Collegare l'OUT di ciascun modulo all'IN del successivo. L'OUT del primo modulo va alla centrale. Lasciare vuoto il connettore IN dell'ultimo modulo della catena.

---

## Risoluzione dei Problemi

**Nessun feedback ricevuto**
- Verificare il cablaggio RJ-45 e confermare la presenza di tutti gli 8 conduttori
- Confermare che il connettore OUT sia orientato verso la centrale (non IN)
- Verificare che l'intervallo di indirizzi del modulo nel software corrisponda alla posizione del modulo nella catena

**Attivazioni false**
- Versione GND: verificare la presenza di cortocircuiti nel cablaggio o interferenze tra le sezioni di rilevamento
- Versione CS: verificare il consumo di corrente minimo — i vagoni con soli LED potrebbero necessitare di un resistore per attivare il rilevamento
- Versione OPTO: verificare la tensione di alimentazione del sensore e la polarità del segnale
- Evitare cavi Ethernet più lunghi di 5 m

**Feedback in ritardo**
- Ridurre l'intervallo di polling nella centrale o nel software su PC
- Verificare il corretto indirizzamento degli ingressi nel software
