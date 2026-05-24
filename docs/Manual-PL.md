> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; 🇵🇱 PL &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Instrukcja modułów zwrotnych OS-S88n

**Obsługuje: OS-S88n GND · OS-S88n CS · OS-S88n OPTO**

![Wszystkie trzy warianty modułów OS-S88n](all.png)

*Od lewej do prawej: OS-S88n CS, OS-S88n GND, OS-S88n OPTO*

---

## Wprowadzenie

Moduły OS-S88n zapewniają funkcję zwrotną dla makiet kolejowych DCC przy użyciu standardowego protokołu S88n. Moduły te umożliwiają monitorowanie w czasie rzeczywistym zajętości blokady i zdarzeń na makiecie, wysyłając dane do stacji sterującej lub oprogramowania sterującego na PC.

Dostępne są trzy warianty dostosowane do różnych potrzeb detekcji:

- **OS-S88n GND** — detekcja kontaktu z masą, odpowiednia dla makiet 3-szynowych (w stylu Märklin)
- **OS-S88n CS** — detekcja prądu, odpowiednia dla cyfrowych makiet 2-szynowych i 3-szynowych
- **OS-S88n OPTO** — optoizolowane wejścia cyfrowe, do użytku z zewnętrznymi czujnikami, takimi jak czujniki IR lub czujniki Halla

Wszystkie warianty zawierają:

- Łańcuchowalne złącza S88n (RJ-45)
- Zaciski śrubowe do wszystkich połączeń czujników
- Kompatybilność ze wszystkimi głównymi stacjami sterującymi i oprogramowaniem (iTrain, Rocrail, Windigipet itp.)

---

## Warianty modułów

### OS-S88n GND — detekcja kontaktu z masą

![Płytka OS-S88n GND](OS-S88n-GND.png)

Moduł GND ma 16 wejść, które wyzwalają się, gdy wejście zostanie podciągnięte do masy. Kompatybilne czujniki i metody detekcji obejmują:

- Kontraktrony (przełączniki trzcinowe)
- Przyciski
- Metalowe zestawy kół zwierające szyny na makiecie 3-szynowej (w stylu Märklin)

⚠️ **Ważne — makiety 3-szynowe:** Przy używaniu modułu GND na makiecie 3-szynowej stacja sterująca i wszystkie wzmacniacze **muszą** być typu z wspólną masą. Jeśli stacja sterująca ma wyjście z mostkiem H, używanie modułu GND **uszkodzi stację sterującą**. Zamiast tego użyj wariantu OPTO.

---

### OS-S88n CS — detekcja prądu

![Płytka OS-S88n CS](OS-S88n-CS.png)

Moduł CS ma 16 wejść, które aktywują się za każdym razem, gdy przez monitorowany odcinek torowy przepływa prąd. Każdy tabor pobierający prąd wyzwoli detekcję, w tym:

- Lokomotywy
- Wagony z oświetleniem
- Wagony wyposażone w rezystor do celów detekcji

Odpowiedni zarówno dla cyfrowych makiet 2-szynowych, jak i 3-szynowych.

---

### OS-S88n OPTO — optoizolowana detekcja wejść

![Płytka OS-S88n OPTO](OS-S88n-OPTO.png)

Moduł OPTO ma 16 w pełni optoizolowanych wejść cyfrowych. Pełna izolacja galwaniczna między czujnikami a magistralą S88 sprawia, że ten wariant jest idealny dla:

- Czujników IR
- Czujników Halla
- Przełączników zlokalizowanych daleko od modułu
- Środowisk wrażliwych na zakłócenia
- Makiet, w których problematyczne są pętle masy lub zakłócenia elektryczne

⚠️ Moduł OPTO **nie wykrywa** sam z siebie zajętości toru — wymaga zewnętrznych czujników dostarczających sygnał na poziomie logicznym.

---

## Właściwości

- W pełni kompatybilny z protokołem zwrotnym S88n
- Złącza RJ-45 do łańcuchowego łączenia modułów
- 16 wejść na moduł
- Łączenie w łańcuchy do 31 modułów
- Zaciski śrubowe do wszystkich połączeń czujników
- Wersja OPTO zapewnia pełną izolację galwaniczną

---

## Podłączanie modułów

### Zasilanie i sygnał

Podłącz moduły do stacji sterującej przy użyciu standardowych kabli Ethernet UTP. **Wszystkie 8 przewodów musi być podłączonych** — unikaj tanich kabli krosowniczych, którym brakuje wewnętrznych przewodów.

- Złącze **S88n OUT** → wejście S88n stacji sterującej (lub wejście IN poprzedniego modułu)
- Złącze **S88n IN** → następny moduł w łańcuchu (pozostaw puste na ostatnim module)

### Okablowanie czujników

**OS-S88n CS — detekcja prądu**

![Okablowanie wersji z detekcją prądu](image.png)

Przeprowadź przewody zasilania torowego dla każdej sekcji detekcji przez wejścia czujnika prądu. Każdy pociąg pobierający prąd w tej sekcji aktywuje odpowiednie wejście.

---

**OS-S88n GND — kontakt z masą**

![Okablowanie wersji GND](image-1.png)

Podłącz jedną szynę (lub wyjście czujnika) do zacisku wejściowego, a wspólną szynę do zacisku COM. Zestawy kół zwierające obie szyny domykają obwód do masy i wyzwalają wejście.

⚠️ *Przy używaniu wersji GND na makiecie 3-szynowej bezwzględnie konieczne jest, aby stacja sterująca i wzmacniacze były typu z wspólną masą. Używanie wersji GND ze stacją sterującą z mostkiem H spowoduje jej uszkodzenie. Zamiast tego użyj wariantu OPTO.*

---

**OS-S88n OPTO — optoizolowany**

![Okablowanie wersji OPTO](image-3.png)

Podłącz wyjście sygnałowe czujnika do zacisku wejściowego, a masę czujnika do zacisku COM. Napięcie wejściowe zależy od zasilania czujnika; sprawdź oznaczenia na płytce pod kątem obsługiwanego zakresu.

---

**Łańcuchowe łączenie wielu modułów**

![Łańcuchowe łączenie kilku modułów OS-S88n](image-2.png)

Podłącz OUT każdego modułu do IN następnego. OUT pierwszego modułu trafia do stacji sterującej. Złącze IN ostatniego modułu w łańcuchu pozostaw puste.

---

## Rozwiązywanie problemów

**Brak sygnału zwrotnego**
- Sprawdź okablowanie RJ-45 i upewnij się, że wszystkie 8 przewodów jest podłączonych
- Upewnij się, że złącze OUT kieruje się w stronę stacji sterującej (nie IN)
- Sprawdź w oprogramowaniu, czy zakres adresów modułu odpowiada pozycji modułu w łańcuchu

**Fałszywe wyzwolenia**
- Wersja GND: sprawdź zwarcia w okablowaniu lub zakłócenia między sekcjami detekcji
- Wersja CS: sprawdź minimalny pobór prądu — wagony wyłącznie z LED mogą wymagać rezystora do wyzwolenia detekcji
- Wersja OPTO: sprawdź napięcie zasilania czujnika i polaryzację sygnału
- Unikaj kabli Ethernet dłuższych niż 5 m

**Opóźniony sygnał zwrotny**
- Skróć interwał odpytywania w stacji sterującej lub oprogramowaniu na PC
- Sprawdź prawidłowe adresowanie wejść w oprogramowaniu
