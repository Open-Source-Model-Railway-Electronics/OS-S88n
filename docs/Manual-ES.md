> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; 🇪🇸 ES &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manual de los Módulos de Retroalimentación OS-S88n

**Compatible con: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Las tres variantes del módulo OS-S88n](all.png)

*De izquierda a derecha: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Introducción

Los módulos OS-S88n proporcionan funcionalidad de retroalimentación para maquetas de ferrocarril DCC mediante el protocolo S88n estandarizado. Estos módulos permiten la monitorización en tiempo real de la ocupación de bloques y los eventos de la maqueta, enviando datos a la central de mando o al software de control basado en PC.

Hay tres variantes disponibles para diferentes necesidades de detección:

- **OS-S88n GND** — detección por contacto a masa, adecuada para maquetas de 3 carriles (estilo Märklin)
- **OS-S88n CS** — detección por sensor de corriente, adecuada para maquetas digitales de 2 y 3 carriles
- **OS-S88n OPTO** — entradas digitales optoacopladas, para uso con sensores externos como detectores IR o sensores Hall

Todas las variantes incluyen:

- Conectores S88n encadenables (RJ-45)
- Bornes de tornillo para todas las conexiones de sensores
- Compatibilidad con todas las principales centrales de mando y programas (iTrain, Rocrail, Windigipet, etc.)

---

## Variantes del Módulo

### OS-S88n GND — Detección por Contacto a Masa

![Placa OS-S88n GND](OS-S88n-GND.png)

El módulo GND tiene 16 entradas que se activan cuando la entrada se lleva a masa. Los sensores y métodos de detección compatibles incluyen:

- Contactos reed
- Pulsadores
- Ruedas metálicas que puentean los carriles en una maqueta de 3 carriles (estilo Märklin)

⚠️ **Importante — maquetas de 3 carriles:** Al usar el módulo GND en una maqueta de 3 carriles, la central de mando y todos los amplificadores **deben** ser del tipo de masa común. Si su central usa una salida en puente H, usar el módulo GND **dañará su central**. En ese caso utilice la variante OPTO.

---

### OS-S88n CS — Sensor de Corriente

![Placa OS-S88n CS](OS-S88n-CS.png)

El módulo CS tiene 16 entradas que se activan cuando hay circulación de corriente a través de una sección de vía monitorizada. Cualquier material rodante que consuma corriente activará la detección, incluyendo:

- Locomotoras
- Coches iluminados
- Vagones equipados con una resistencia para fines de detección

Adecuado tanto para maquetas digitales de 2 como de 3 carriles.

---

### OS-S88n OPTO — Detección de Entradas Optoacopladas

![Placa OS-S88n OPTO](OS-S88n-OPTO.png)

El módulo OPTO tiene 16 entradas digitales completamente optoacopladas. El aislamiento galvánico total entre los sensores y el bus S88 hace que esta variante sea ideal para:

- Detectores IR
- Sensores Hall
- Interruptores ubicados lejos del módulo
- Entornos sensibles al ruido eléctrico
- Maquetas donde los bucles de masa o las interferencias eléctricas son una preocupación

⚠️ El módulo OPTO **no** detecta la ocupación de vía por sí solo — requiere sensores externos que proporcionen una señal de nivel lógico.

---

## Características

- Totalmente compatible con el protocolo de retroalimentación S88n
- Conectores RJ-45 para encadenamiento de módulos
- 16 entradas por módulo
- Encadene hasta 31 módulos en una sola cadena
- Bornes de tornillo para todas las conexiones de sensores
- La versión OPTO proporciona aislamiento galvánico completo

---

## Conexión de los Módulos

### Alimentación y Señal

Conecte los módulos a su central mediante cables Ethernet UTP estándar. **Deben conectarse los 8 conductores** — evite cables de conexión de baja calidad que omitan conductores internos.

- Conector **S88n OUT** → entrada S88n de la central (o el IN del módulo anterior)
- Conector **S88n IN** → siguiente módulo de la cadena (déjelo vacío en el último módulo)

### Cableado de Sensores

**OS-S88n CS — sensor de corriente**

![Cableado de la versión de sensor de corriente](image.png)

Encamine los cables de alimentación de vía de cada sección de detección a través de las entradas del sensor de corriente. Cualquier tren que consuma corriente en esa sección activa la entrada correspondiente.

---

**OS-S88n GND — contacto a masa**

![Cableado de la versión GND](image-1.png)

Conecte un carril (o la salida del sensor) a un borne de entrada y el carril común al borne COM. Las ruedas que puentean ambos carriles completan el circuito a masa y activan la entrada.

⚠️ *Al usar la versión GND en una maqueta de 3 carriles, es imprescindible que la central y los amplificadores sean del tipo de masa común. Si usa la versión GND con una central de puente H, destruirá su central. Utilice la variante OPTO en su lugar.*

---

**OS-S88n OPTO — optoacoplado**

![Cableado de la versión OPTO](image-3.png)

Conecte la salida de señal del sensor al borne de entrada y la masa del sensor al borne COM. La tensión de entrada depende de la alimentación de su sensor; compruebe las marcas de la placa para conocer el rango admitido.

---

**Encadenamiento de múltiples módulos**

![Encadenamiento de varios módulos OS-S88n](image-2.png)

Conecte el OUT de cada módulo al IN del siguiente. El OUT del primer módulo va a la central. Deje vacío el conector IN del último módulo de la cadena.

---

## Resolución de Problemas

**No se recibe retroalimentación**
- Compruebe el cableado RJ-45 y confirme que los 8 conductores están presentes
- Compruebe que el conector OUT apunta hacia la central (no el IN)
- Verifique que el rango de direcciones del módulo en su software coincide con la posición del módulo en la cadena

**Activaciones falsas**
- Versión GND: compruebe cortocircuitos en el cableado o interferencias entre secciones de detección
- Versión CS: compruebe la corriente mínima consumida — los vagones con solo LED pueden necesitar una resistencia para activar la detección
- Versión OPTO: compruebe la tensión de alimentación del sensor y la polaridad de la señal
- Evite cables Ethernet de más de 5 m

**Retroalimentación retrasada**
- Reduzca el intervalo de sondeo en su central o software de PC
- Verifique el direccionamiento de entradas correcto en su software
