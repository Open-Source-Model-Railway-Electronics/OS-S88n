> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; 🇨🇿 CS &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manuál zpětnovazebních modulů OS-S88n

**Podporuje: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Všechny tři varianty modulu OS-S88n](all.png)

*Zleva doprava: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Úvod

Moduly OS-S88n zajišťují zpětnovazební funkci pro DCC modelové železnice pomocí standardizovaného protokolu S88n. Tyto moduly umožňují sledování obsazení bloků a událostí na kolejišti v reálném čase a odesílají data do vaší příkazové stanice nebo počítačového řídicího softwaru.

K dispozici jsou tři varianty pro různé detekční potřeby:

- **OS-S88n GND** — detekce uzemnění, vhodná pro kolejiště s 3 kolejnicemi (ve stylu Märklin)
- **OS-S88n CS** — detekce proudu, vhodná pro digitální kolejiště se 2 i 3 kolejnicemi
- **OS-S88n OPTO** — opticky izolované digitální vstupy pro použití s externími senzory jako jsou IR detektory nebo Hallovy senzory

Všechny varianty obsahují:

- Řetězitelné S88n konektory (RJ-45)
- Šroubové svorky pro všechna připojení senzorů
- Kompatibilita se všemi hlavními příkazovými stanicemi a softwarem (iTrain, Rocrail, Windigipet atd.)

---

## Varianty modulů

### OS-S88n GND — Detekce uzemnění

![Deska OS-S88n GND](OS-S88n-GND.png)

Modul GND má 16 vstupů, které se aktivují při přivedení vstupu na zem. Kompatibilní senzory a detekční metody zahrnují:

- Reedovy spínače
- Tlačítka
- Kovová kolová soustrojí přemosťující koleje na kolejišti se 3 kolejnicemi (ve stylu Märklin)

⚠️ **Důležité — kolejiště se 3 kolejnicemi:** Při použití modulu GND na kolejišti se 3 kolejnicemi musí vaše příkazová stanice a všechny zesilovače **být** typu se společnou zemí. Pokud vaše příkazová stanice používá H-můstkový výstup, použití modulu GND **poškodí vaši příkazovou stanici**. V takovém případě použijte místo toho variantu OPTO.

---

### OS-S88n CS — Měření proudu

![Deska OS-S88n CS](OS-S88n-CS.png)

Modul CS má 16 vstupů, které se aktivují vždy, když prochází proud přes sledovaný kolejový úsek. Jakýkoli kolejový vozidlo odebírající proud spustí detekci, včetně:

- Lokomotiv
- Osvětlených vozů
- Vozů vybavených odporem pro účely detekce

Vhodné pro digitální kolejiště se 2 i 3 kolejnicemi.

---

### OS-S88n OPTO — Opticky izolovaná vstupní detekce

![Deska OS-S88n OPTO](OS-S88n-OPTO.png)

Modul OPTO má 16 plně opticky izolovaných digitálních vstupů. Úplná galvanická izolace mezi senzory a S88 sběrnicí činí tuto variantu ideální pro:

- IR detektory
- Hallovy senzory
- Spínače umístěné daleko od modulu
- Prostředí citlivá na rušení
- Kolejiště, kde jsou problémem zemní smyčky nebo elektrické rušení

⚠️ Modul OPTO sám o sobě **nedetekuje** obsazení koleje — vyžaduje externí senzory poskytující logický signál.

---

## Vlastnosti

- Plně kompatibilní s protokolem zpětné vazby S88n
- Konektory RJ-45 pro řetězení modulů
- 16 vstupů na modul
- Řetězení až 31 modulů v jednom řetězci
- Šroubové svorky pro všechna připojení senzorů
- Verze OPTO poskytuje plnou galvanickou izolaci

---

## Připojení modulů

### Napájení a signál

Připojte moduly k vaší příkazové stanici pomocí standardních UTP ethernetových kabelů. **Všechny 8 vodičů musí být zapojeny** — vyhýbejte se levně vyrobeným patch kabelům, které vynechávají vnitřní vodiče.

- Konektor **S88n OUT** → vstup S88n příkazové stanice (nebo vstup IN předchozího modulu)
- Konektor **S88n IN** → následující modul v řetězci (na posledním modulu nechte prázdný)

### Zapojení senzorů

**OS-S88n CS — měření proudu**

![Zapojení verze s měřením proudu](image.png)

Veďte napájecí vodiče koleje pro každý detekční úsek přes vstupy proudového senzoru. Jakýkoli vlak odebírající proud v daném úseku aktivuje odpovídající vstup.

---

**OS-S88n GND — uzemnění**

![Zapojení verze GND](image-1.png)

Připojte jednu kolejnici (nebo výstup senzoru) ke vstupní svorce a společnou kolejnici ke svorce COM. Kolová soustrojí přemosťující obě kolejnice uzavírají obvod na zem a aktivují vstup.

⚠️ *Při použití verze GND na kolejišti se 3 kolejnicemi je nezbytné, aby příkazová stanice a zesilovače byly typu se společnou zemí. Pokud použijete verzi GND s příkazovou stanicí s H-můstkem, zničíte svou příkazovou stanici. Použijte místo toho variantu OPTO.*

---

**OS-S88n OPTO — opticky izolovaná**

![Zapojení verze OPTO](image-3.png)

Připojte signálový výstup vašeho senzoru ke vstupní svorce a uzemnění senzoru ke svorce COM. Vstupní napětí závisí na napájení vašeho senzoru; zkontrolujte potisk na desce pro podporovaný rozsah.

---

**Řetězení více modulů**

![Řetězení několika modulů OS-S88n](image-2.png)

Připojte OUT každého modulu k IN dalšího. OUT prvního modulu jde k příkazové stanici. Konektor IN posledního modulu v řetězci nechte prázdný.

---

## Řešení problémů

**Není přijímána žádná zpětná vazba**
- Zkontrolujte kabeláž RJ-45 a potvrďte, že jsou přítomny všechny 4 páry (8 vodičů)
- Ověřte, že konektor OUT směřuje k příkazové stanici (nikoli IN)
- Ověřte, že rozsah adres modulu ve vašem softwaru odpovídá pozici modulu v řetězci

**Falešné spuštění**
- Verze GND: zkontrolujte zkraty v zapojení nebo rušení mezi detekčními úseky
- Verze CS: zkontrolujte minimální odběr proudu — vozy pouze s LED mohou potřebovat odpor pro spuštění detekce
- Verze OPTO: zkontrolujte napájecí napětí senzoru a polaritu signálu
- Vyhýbejte se ethernetovým kabelům delším než 5 m

**Zpožděná zpětná vazba**
- Snižte interval dotazování v příkazové stanici nebo počítačovém softwaru
- Ověřte správné adresování vstupů ve vašem softwaru
