> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; 🇵🇹 PT

# Manual dos Módulos de Retorno OS-S88n

**Suporta: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![As três variantes do módulo OS-S88n](all.png)

*Da esquerda para a direita: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Introdução

Os módulos OS-S88n fornecem funcionalidade de retorno para ferrovias em miniatura DCC utilizando o protocolo S88n normalizado. Estes módulos permitem a monitorização em tempo real da ocupação de blocos e eventos da maquete, enviando dados para a sua central de comando ou software de controlo em PC.

Estão disponíveis três variantes para satisfazer diferentes necessidades de detecção:

- **OS-S88n GND** — detecção por contacto com a massa, adequada para maquetes de 3 carris (tipo Märklin)
- **OS-S88n CS** — detecção por detecção de corrente, adequada para maquetes digitais de 2 e 3 carris
- **OS-S88n OPTO** — entradas digitais com isolamento óptico, para uso com sensores externos como detectores IR ou sensores Hall

Todas as variantes incluem:

- Conectores S88n encadeáveis (RJ-45)
- Bornes de parafuso para todas as ligações de sensores
- Compatibilidade com todas as principais centrais de comando e software (iTrain, Rocrail, Windigipet, etc.)

---

## Variantes dos Módulos

### OS-S88n GND — Detecção por Contacto com Massa

![Placa OS-S88n GND](OS-S88n-GND.png)

O módulo GND tem 16 entradas que disparam quando a entrada é ligada à massa. Os sensores e métodos de detecção compatíveis incluem:

- Contactos de reed
- Botões de pressão
- Rodados metálicos que fazem ponte entre os carris numa maquete de 3 carris (tipo Märklin)

⚠️ **Importante — maquetes de 3 carris:** Ao utilizar o módulo GND numa maquete de 3 carris, a sua central de comando e todos os boosters **devem** ser do tipo com massa comum. Se a sua central utiliza uma saída em ponte H, o uso do módulo GND **danificará a central**. Utilize a variante OPTO nesse caso.

---

### OS-S88n CS — Detecção de Corrente

![Placa OS-S88n CS](OS-S88n-CS.png)

O módulo CS tem 16 entradas que se activam sempre que é consumida corrente numa secção de via monitorizada. Qualquer material circulante que consuma corrente dispara a detecção, incluindo:

- Locomotivas
- Carruagens iluminadas
- Vagões equipados com resistência para fins de detecção

Adequado para maquetes digitais de 2 e 3 carris.

---

### OS-S88n OPTO — Detecção de Entrada com Isolamento Óptico

![Placa OS-S88n OPTO](OS-S88n-OPTO.png)

O módulo OPTO tem 16 entradas digitais com isolamento óptico total. O isolamento galvânico completo entre os sensores e o barramento S88 torna esta variante ideal para:

- Detectores IR
- Sensores Hall
- Interruptores localizados a grande distância do módulo
- Ambientes sujeitos a ruído eléctrico
- Maquetes onde os anéis de terra ou as interferências eléctricas são uma preocupação

⚠️ O módulo OPTO **não** detecta ocupação de via por si próprio — requer sensores externos que forneçam um sinal de nível lógico.

---

## Características

- Totalmente compatível com o protocolo de retorno S88n
- Conectores RJ-45 para encadeamento de módulos
- 16 entradas por módulo
- Ligação de até 31 módulos numa única cadeia
- Bornes de parafuso para todas as ligações de sensores
- A versão OPTO oferece isolamento galvânico total

---

## Ligação dos Módulos

### Alimentação e Sinal

Ligue os módulos à sua central de comando utilizando cabos Ethernet UTP normais. **Todos os 8 fios devem estar ligados** — evite cabos de ligação de baixa qualidade que omitem fios internos.

- Conector **S88n OUT** → entrada S88n da central de comando (ou o IN do módulo anterior)
- Conector **S88n IN** → módulo seguinte na cadeia (deixe vazio no último módulo)

### Ligação dos Sensores

**OS-S88n CS — detecção de corrente**

![Ligação da versão de Detecção de Corrente](image.png)

Encaminhe os fios de alimentação de via de cada secção de detecção pelas entradas de detecção de corrente. Qualquer comboio que consuma corrente nessa secção activa a entrada correspondente.

---

**OS-S88n GND — contacto com massa**

![Ligação da versão GND](image-1.png)

Ligue um carril (ou saída do sensor) a um terminal de entrada e o carril comum ao terminal COM. Os rodados a fazer ponte entre ambos os carris completam o circuito para a massa e disparam a entrada.

⚠️ *Ao utilizar a versão GND numa maquete de 3 carris, é imperativo que a central de comando e os boosters sejam do tipo com massa comum. Se utilizar a versão GND com uma central com saída em ponte H, destruirá a central. Utilize a variante OPTO em alternativa.*

---

**OS-S88n OPTO — isolamento óptico**

![Ligação da versão OPTO](image-3.png)

Ligue a saída de sinal do sensor ao terminal de entrada e a massa do sensor ao terminal COM. A tensão de entrada depende da alimentação do sensor; consulte as marcações da placa para o intervalo suportado.

---

**Encadeamento de múltiplos módulos**

![Encadeamento de vários módulos OS-S88n](image-2.png)

Ligue o OUT de cada módulo ao IN do seguinte. O OUT do primeiro módulo vai para a central de comando. Deixe o conector IN do último módulo na cadeia vazio.

---

## Resolução de Problemas

**Nenhum retorno recebido**
- Verifique a cablagem RJ-45 e confirme que todos os 8 condutores estão presentes
- Confirme que o conector OUT aponta para a central de comando (e não o IN)
- Verifique se o intervalo de endereços do módulo no seu software corresponde à posição do módulo na cadeia

**Disparos falsos**
- Versão GND: verifique curto-circuitos na cablagem ou interferências entre secções de detecção
- Versão CS: verifique o consumo mínimo de corrente — vagões apenas com LED podem necessitar de uma resistência para disparar a detecção
- Versão OPTO: verifique a tensão de alimentação do sensor e a polaridade do sinal
- Evite cabos Ethernet com mais de 5 m

**Retorno com atraso**
- Reduza o intervalo de interrogação na sua central de comando ou software de PC
- Verifique o endereçamento correcto das entradas no seu software
