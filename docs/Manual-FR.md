> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; 🇫🇷 FR &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manuel des modules de retour OS-S88n

**Prend en charge : OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Les trois variantes du module OS-S88n](all.png)

*De gauche à droite : OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Introduction

Les modules OS-S88n fournissent des fonctionnalités de retour d'information pour les réseaux ferroviaires miniatures DCC en utilisant le protocole standardisé S88n. Ces modules permettent la surveillance en temps réel de l'occupation des cantons et des événements du réseau, en transmettant les données à votre centrale ou logiciel de commande sur PC.

Trois variantes sont disponibles pour répondre à différents besoins de détection :

- **OS-S88n GND** — détection par contact à la masse, adaptée aux réseaux à 3 rails (style Märklin)
- **OS-S88n CS** — détection par mesure de courant, adaptée aux réseaux numériques 2 et 3 rails
- **OS-S88n OPTO** — entrées numériques à isolation optique, pour une utilisation avec des capteurs externes tels que des détecteurs IR ou des capteurs à effet Hall

Toutes les variantes incluent :

- Connecteurs S88n enchaînables (RJ-45)
- Borniers à vis pour toutes les connexions de capteurs
- Compatibilité avec toutes les principales centrales et logiciels (iTrain, Rocrail, Windigipet, etc.)

---

## Variantes du module

### OS-S88n GND — Détection par contact à la masse

![Carte OS-S88n GND](OS-S88n-GND.png)

Le module GND dispose de 16 entrées qui se déclenchent lorsque l'entrée est amenée à la masse. Les capteurs et méthodes de détection compatibles comprennent :

- Contacts reed
- Boutons poussoirs
- Essieux métalliques pontant les rails sur un réseau à 3 rails (style Märklin)

⚠️ **Important — réseaux à 3 rails :** Lors de l'utilisation du module GND sur un réseau à 3 rails, votre centrale et tous les boosters **doivent** être du type à masse commune. Si votre centrale utilise une sortie en pont H, utiliser le module GND **endommagera votre centrale**. Utilisez à la place la variante OPTO dans ce cas.

---

### OS-S88n CS — Mesure de courant

![Carte OS-S88n CS](OS-S88n-CS.png)

Le module CS dispose de 16 entrées qui s'activent dès qu'un courant est consommé dans une section de voie surveillée. Tout matériel roulant consommant du courant déclenchera la détection, notamment :

- Les locomotives
- Les voitures éclairées
- Les wagons équipés d'une résistance à des fins de détection

Adapté aux réseaux numériques 2 et 3 rails.

---

### OS-S88n OPTO — Détection par entrée à isolation optique

![Carte OS-S88n OPTO](OS-S88n-OPTO.png)

Le module OPTO dispose de 16 entrées numériques entièrement à isolation optique. L'isolation galvanique complète entre les capteurs et le bus S88 rend cette variante idéale pour :

- Les détecteurs IR
- Les capteurs à effet Hall
- Les interrupteurs situés loin du module
- Les environnements sensibles aux perturbations
- Les réseaux où les boucles de masse ou les interférences électriques sont une préoccupation

⚠️ Le module OPTO ne **détecte pas** l'occupation de la voie par lui-même — il nécessite des capteurs externes fournissant un signal de niveau logique.

---

## Caractéristiques

- Entièrement compatible avec le protocole de retour S88n
- Connecteurs RJ-45 pour l'enchaînement des modules
- 16 entrées par module
- Enchaînement jusqu'à 31 modules dans une seule chaîne
- Borniers à vis pour toutes les connexions de capteurs
- La version OPTO offre une isolation galvanique complète

---

## Connexion des modules

### Alimentation et signal

Connectez les modules à votre centrale à l'aide de câbles Ethernet UTP standard. **Les 8 fils doivent être connectés** — évitez les câbles de brassage bon marché qui omettent des fils internes.

- Connecteur **S88n OUT** → entrée S88n de la centrale (ou l'IN du module précédent)
- Connecteur **S88n IN** → module suivant dans la chaîne (laisser vide sur le dernier module)

### Câblage des capteurs

**OS-S88n CS — mesure de courant**

![Câblage de la version à mesure de courant](image.png)

Faites passer les fils d'alimentation de voie pour chaque section de détection à travers les entrées de capteur de courant. Tout train consommant du courant dans cette section active l'entrée correspondante.

---

**OS-S88n GND — contact à la masse**

![Câblage de la version GND](image-1.png)

Connectez un rail (ou la sortie du capteur) à une borne d'entrée et le rail commun à la borne COM. Les essieux pontant les deux rails complètent le circuit vers la masse et déclenchent l'entrée.

⚠️ *Lors de l'utilisation de la version GND sur un réseau à 3 rails, il est impératif que la centrale et les boosters soient du type à masse commune. Si vous utilisez la version GND avec une centrale à pont H, vous détruirez votre centrale. Utilisez plutôt la variante OPTO.*

---

**OS-S88n OPTO — à isolation optique**

![Câblage de la version OPTO](image-3.png)

Connectez la sortie de signal de votre capteur à la borne d'entrée et la masse du capteur à la borne COM. La tension d'entrée dépend de l'alimentation de votre capteur ; vérifiez les marquages de la carte pour la plage prise en charge.

---

**Enchaînement de plusieurs modules**

![Enchaînement de plusieurs modules OS-S88n](image-2.png)

Connectez la sortie OUT de chaque module à l'entrée IN du suivant. La sortie OUT du premier module va vers la centrale. Laissez le connecteur IN du dernier module de la chaîne vide.

---

## Dépannage

**Aucun retour reçu**
- Vérifiez le câblage RJ-45 et confirmez que les 8 conducteurs sont présents
- Confirmez que le connecteur OUT est orienté vers la centrale (et non l'IN)
- Vérifiez que la plage d'adresses du module dans votre logiciel correspond à la position du module dans la chaîne

**Déclenchements intempestifs**
- Version GND : vérifiez les courts-circuits de câblage ou les interférences entre les sections de détection
- Version CS : vérifiez la consommation de courant minimale — les wagons à LED uniquement peuvent nécessiter une résistance pour déclencher la détection
- Version OPTO : vérifiez la tension d'alimentation du capteur et la polarité du signal
- Évitez les câbles Ethernet de plus de 5 m

**Retour différé**
- Réduisez l'intervalle d'interrogation dans votre centrale ou logiciel PC
- Vérifiez l'adressage d'entrée correct dans votre logiciel
