---
title: Zagrożenia bez plików
ms.reviewer: ''
description: Dowiedz się więcej o kategoriach zagrożeń bez plików i złośliwego oprogramowania, które żyją poza krajem
keywords: fileless, fileless malware, living off the land, lolbins, amsi, behavior monitoring, memory scanning, boot sector protection, security, malware, Windows Defender ATP, antivirus, AV, Microsoft Defender ATP, ochrona nowej generacji
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 4db82cfc20bb1e27b2ef9a75793170c451c3868a
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665343"
---
# <a name="fileless-threats"></a>Zagrożenia bez plików

Co dokładnie to są zagrożenia bez plików? Termin "bez pliku" sugeruje, że zagrożenie nie pojawia się w pliku, takim jak tylne drzwi, które żyją tylko w pamięci maszyny. Nie ma jednak jednej definicji złośliwego oprogramowania bez plików. Termin ten jest używany szeroko, a czasami do opisywania rodzin złośliwego oprogramowania, które polegają na plikach do działania.

Ataki obejmują [kilka etapów](https://attack.mitre.org/wiki/ATT&CK_Matrix) funkcji, takich jak wykonywanie, trwałość lub kradzież informacji. Niektóre części łańcucha ataków mogą być bez plików, podczas gdy inne mogą obejmować system plików w jakiejś formie.

W celu zapewnienia przejrzystości zagrożenia bez plików są pogrupowane w różne kategorie.

![Kompleksowy diagram złośliwego oprogramowania bez plików.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Rysunek 1. Kompleksowy diagram złośliwego oprogramowania bez plików*

Zagrożenia bez plików można sklasyfikować według punktu wejścia, co wskazuje, jak złośliwe oprogramowanie bez plików może pojawić się na maszynie. Mogą one zostać dostarczone za pośrednictwem luki w zabezpieczeniach, za pośrednictwem zagrożonego sprzętu lub za pośrednictwem regularnego wykonywania aplikacji i skryptów.

Następnie wyświetl listę postaci punktu wejścia. Na przykład luki w zabezpieczeniach mogą być oparte na plikach lub danych sieciowych, urządzenia peryferyjne PCI są typem wektora sprzętowego, a skrypty i pliki wykonywalne są podkategoriami wektora wykonywania.

Na koniec należy sklasyfikować hosta infekcji. Na przykład aplikacja Flash może zawierać różne zagrożenia, takie jak exploit, prosty plik wykonywalny i złośliwe oprogramowanie układowe z urządzenia sprzętowego.

Klasyfikowanie ułatwia dzielenie i kategoryzowanie różnych rodzajów zagrożeń bez plików. Niektóre z nich są bardziej niebezpieczne, ale także trudniejsze do wdrożenia, podczas gdy inne są częściej używane, mimo że (lub właśnie z powodu) nie są bardzo zaawansowane.

Z tej kategoryzacji można zebrać trzy główne typy zagrożeń bez plików w zależności od tego, ile odcisku palca mogą pozostawić na zainfekowanych maszynach.

## <a name="type-i-no-file-activity-performed"></a>Typ I: Nie wykonano żadnego działania pliku

W pełni bezplikowe złośliwe oprogramowanie można uznać za takie, które nigdy nie wymaga pisania pliku na dysku. W jaki sposób takie złośliwe oprogramowanie zainfekowałoby maszynę w pierwszej kolejności? Jednym z przykładów jest to, że maszyna docelowa odbiera złośliwe pakiety sieciowe wykorzystujące lukę w zabezpieczeniach EternalBlue. Luka w zabezpieczeniach umożliwia instalację tylnych drzwi DoublePulsar, która kończy się w pamięci jądra. W takim przypadku nie ma pliku ani żadnych danych zapisanych w pliku.

Zagrożone urządzenie może mieć również złośliwy kod ukrywający się w oprogramowaniu układowym urządzenia (takim jak BIOS), urządzeniu peryferyjnym USB (takim jak atak BadUSB) lub w oprogramowaniu układowym karty sieciowej. Wszystkie te przykłady nie wymagają uruchomienia pliku na dysku i teoretycznie mogą być aktywne tylko w pamięci. Złośliwy kod przetrwa ponowny rozruch, przeformułowanie dysku i ponowne zainstalowanie systemu operacyjnego.

Infekcje tego typu mogą być szczególnie trudne do wykrycia, ponieważ większość produktów antywirusowych nie ma możliwości inspekcji oprogramowania układowego. W przypadkach, gdy produkt ma możliwość inspekcji i wykrywania złośliwego oprogramowania układowego, nadal istnieją istotne wyzwania związane z korygowania zagrożeń na tym poziomie. Ten typ złośliwego oprogramowania bez plików wymaga wysokiego poziomu wyrafinowania i często zależy od konkretnej konfiguracji sprzętu lub oprogramowania. Nie jest to wektor ataku, który można łatwo i niezawodnie wykorzystać. Zagrożenia tego typu są nietypowe i niepraktyczne w przypadku większości ataków.

## <a name="type-ii-indirect-file-activity"></a>Typ II: Pośrednie działanie pliku

Istnieją inne sposoby, w jakie złośliwe oprogramowanie może osiągnąć obecność bez plików na maszynie bez konieczności dużego nakładu pracy inżynieryjnej. Złośliwe oprogramowanie tego typu bez plików nie zapisuje bezpośrednio plików w systemie plików, ale może w końcu używać plików pośrednio. Na przykład przy użyciu narzędzia [Poshspy backdoor](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) osoby atakujące zainstalowały złośliwe polecenie programu PowerShell w repozytorium WMI i skonfigurowały filtr WMI do okresowego uruchamiania polecenia.

Taką instalację można przeprowadzić za pośrednictwem wiersza polecenia bez konieczności używania tylnego wejścia do pliku. Złośliwe oprogramowanie można zainstalować i teoretycznie uruchomić bez konieczności dotykania systemu plików. Jednak repozytorium WMI jest przechowywane w pliku fizycznym w centralnym obszarze magazynu zarządzanym przez Menedżera obiektów CIM i zwykle zawiera uzasadnione dane. Mimo że łańcuch infekcji technicznie używa pliku fizycznego, jest uważany za atak bez plików, ponieważ repozytorium WMI jest kontenerem danych wielozadaniowym, którego nie można wykryć i usunąć.

## <a name="type-iii-files-required-to-operate"></a>Typ III: Pliki wymagane do działania

Niektóre złośliwe oprogramowanie może mieć rodzaj trwałości bez plików, ale nie bez używania plików do działania. Przykładem tego scenariusza jest narzędzie Kovter, które tworzy procedurę obsługi zlecenia otwarcia powłoki w rejestrze dla losowego rozszerzenia pliku. Otwarcie pliku z takim rozszerzeniem spowoduje wykonanie skryptu za pośrednictwem legalnego narzędzia mshta.exe.

![Obraz przedstawiający klucz rejestru Kovtera.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Rysunek 2. Klucz rejestru Kovtera*

Po wywołaniu otwartego zlecenia zostanie uruchomione skojarzone polecenie z rejestru, co spowoduje wykonanie małego skryptu. Ten skrypt odczytuje dane z kolejnego klucza rejestru i wykonuje je, co z kolei prowadzi do załadowania końcowego ładunku. Aby jednak wyzwolić czasownik otwarty w pierwszej kolejności, narzędzie Kovter musi usunąć plik z tym samym rozszerzeniem docelowym przez czasownik (w powyższym przykładzie rozszerzenie to .bbf5590fd). Należy również ustawić klucz autorun skonfigurowany do otwierania takiego pliku podczas uruchamiania maszyny.

Kovter jest uważany za zagrożenie bez plików, ponieważ system plików nie ma praktycznego zastosowania. Pliki z losowymi rozszerzeniami zawierają dane śmieci, których nie można używać w weryfikowaniu obecności zagrożenia. Pliki, które przechowują rejestr, to kontenery, których nie można wykryć i usunąć w przypadku obecności złośliwej zawartości.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Kategoryzowanie zagrożeń bez plików według hosta infekcji

Po opisaniu szerokich kategorii możemy teraz zagłębić się w szczegóły i podać podział hostów infekcji. Ta kompleksowa klasyfikacja obejmuje panoramę tego, co jest zwykle nazywane złośliwym oprogramowaniem bez plików. Napędza nasze wysiłki w celu zbadania i opracowania nowych funkcji ochrony, które neutralizują klasy ataków i zapewniają, że złośliwe oprogramowanie nie uzyska przewagi w wyścigu zbrojeń.

### <a name="exploits"></a>Wykorzystuje

**Oparte na plikach** (typ III: plik wykonywalny, Flash, Java, dokumenty): Początkowy plik może wykorzystać system operacyjny, przeglądarkę, aparat Java, aparat Flash itp., aby wykonać kod powłoki i dostarczyć ładunek w pamięci. Podczas gdy ładunek jest bez plików, początkowy wektor wejściowy jest plikiem.

**Oparte na sieci** (typ I): komunikacja sieciowa wykorzystująca lukę w zabezpieczeniach na maszynie docelowej może osiągnąć wykonywanie kodu w kontekście aplikacji lub jądra. Przykładem jest WannaCry, która wykorzystuje wcześniej naprawioną lukę w zabezpieczeniach protokołu SMB w celu dostarczenia tylnych drzwi w pamięci jądra.

### <a name="hardware"></a>Sprzęt

**Oparte na urządzeniach** (typ I: karta sieciowa, dysk twardy): urządzenia takie jak dyski twarde i karty sieciowe wymagają mikroukładów i dedykowanego oprogramowania do działania. Oprogramowanie, które znajduje się i działa w chipsecie urządzenia, jest nazywane oprogramowaniem układowym. Chociaż jest to złożone zadanie, oprogramowanie układowe może zostać zainfekowane złośliwym oprogramowaniem, ponieważ [grupa szpiegostwa Równanie została przyłapana na działaniu](https://www.kaspersky.com/blog/equation-hdd-malware/7623/).

**Oparte na procesorze CPU** (typ I): Nowoczesne procesory CPU są złożone i mogą obejmować podsystemy z uruchomionym oprogramowaniem układowym do celów zarządzania. Takie oprogramowanie układowe może być narażone na przejęcie i umożliwić wykonanie złośliwego kodu, który będzie działać z poziomu procesora CPU. W grudniu 2017 r. dwóch badaczy zgłosiło lukę w zabezpieczeniach, która może umożliwić osobom atakującym wykonywanie kodu wewnątrz [aparatu zarządzania (ME)](https://en.wikipedia.org/wiki/Intel_Management_Engine) obecnego w dowolnym nowoczesnym procesorze INTEL. Tymczasem zaobserwowano, że grupa atakująca PLATINUM ma możliwość używania technologii [Active Management Technology (AMT)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) firmy Intel do wykonywania [niewidocznej komunikacji sieciowej](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/), pomijając zainstalowany system operacyjny. ME i AMT są zasadniczo autonomicznymi mikro-komputerami, które żyją wewnątrz procesora i działają na bardzo niskim poziomie. Ponieważ te technologie mają na celu zapewnienie zdalnego zarządzania, mają bezpośredni dostęp do sprzętu, są niezależne od systemu operacyjnego i mogą działać nawet wtedy, gdy komputer jest wyłączony.

Oprócz podatności na zagrożenia na poziomie oprogramowania układowego procesory CPU mogą być produkowane z tylnymi drzwiami włożonymi bezpośrednio do obwodów sprzętowych. Ten atak został [zbadany i okazał się możliwy](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) w przeszłości. Doniesiono, że niektóre modele procesorów x86 zawierają pomocniczy osadzony rdzeń procesora RISC, który może [skutecznie zapewnić tylne drzwi](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) , dzięki którym zwykłe aplikacje mogą uzyskać uprzywilejowane wykonywanie.

**Oparte na USB** (typ I): urządzenia USB wszelkiego rodzaju można przeprogramować złośliwym oprogramowaniem układowym, które może wchodzić w interakcje z systemem operacyjnym w nikczemny sposób. Na przykład [technika BadUSB](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) umożliwia przeprogramowanym pamięciom USB działanie jako klawiatura, która wysyła polecenia do maszyn za pośrednictwem naciśnięć klawiszy lub jako karta sieciowa, która może przekierować ruch do woli.

**Oparty na systemie BIOS** (typ I): SYSTEM BIOS to oprogramowanie układowe działające wewnątrz chipsetu. Jest on wykonywany, gdy maszyna jest włączona, inicjuje sprzęt, a następnie przenosi kontrolę do sektora rozruchowego. System BIOS jest ważnym składnikiem, który działa na niskim poziomie i jest wykonywany przed sektorem rozruchowym. Istnieje możliwość przeprogramowanie oprogramowania układowego BIOS ze złośliwym kodem, jak to miało miejsce w przeszłości z [zestawem rootkit Mebromi](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/).

**Oparte na funkcji Hypervisor** (typ I): nowoczesne procesory CPU zapewniają sprzętową obsługę funkcji hypervisor, dzięki czemu system operacyjny może tworzyć niezawodne maszyny wirtualne. Maszyna wirtualna działa w ograniczonym, symulowanym środowisku i teoretycznie nie wie o emulacji. Złośliwe oprogramowanie przejmujące maszynę może zaimplementować małą funkcję hypervisor, aby ukryć się poza obszarem uruchomionego systemu operacyjnego. Złośliwe oprogramowanie tego rodzaju było w przeszłości teoryzowane i w końcu [zaobserwowano](http://seclists.org/fulldisclosure/2017/Jun/29) prawdziwe zestawy rootkitów funkcji hypervisor, chociaż niewiele z nich jest do tej pory znanych.

### <a name="execution-and-injection"></a>Wykonywanie i iniekcja

**Oparte na plikach** (typ III: pliki wykonywalne, biblioteki DLL, pliki LNK, zaplanowane zadania): jest to standardowy wektor wykonywania. Prosty plik wykonywalny można uruchomić jako złośliwe oprogramowanie pierwszego etapu w celu uruchomienia dodatkowego ładunku w pamięci lub wstrzyknąć do innych legalnych procesów uruchomionych.

**Oparte na makrach** (typ III: Office dokumenty): [język VBA](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office) jest elastycznym i zaawansowanym narzędziem służącym do automatyzowania zadań edycji i dodawania dynamicznych funkcji do dokumentów. W związku z tym może być nadużywane przez osoby atakujące do wykonywania złośliwych operacji, takich jak dekodowanie, uruchamianie lub wstrzykiwanie ładunku wykonywalnego, a nawet implementowanie całego oprogramowania wymuszającego okup, jak w [przypadku QKG](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/). Makra są wykonywane w kontekście procesu Office (np. Winword.exe) i implementowane w języku skryptów. Nie ma pliku wykonywalnego binarnego, który program antywirusowy może sprawdzić. Chociaż aplikacje Office wymagają wyraźnej zgody użytkownika na wykonywanie makr z dokumentu, osoby atakujące używają technik inżynierii społecznej, aby skłonić użytkowników do umożliwienia wykonywania makr.

**Oparte na skryptach** (typ II: plik, usługa, rejestr, repozytorium WMI, powłoka): Języki skryptów JavaScript, VBScript i PowerShell są domyślnie dostępne na platformach Windows. Skrypty mają takie same zalety jak makra, są plikami tekstowymi (nie binarnymi plikami wykonywalnymi) i działają w kontekście interpretera (na przykład wscript.exe, powershell.exe), który jest czystym i uzasadnionym składnikiem. Skrypty są uniwersalne i mogą być uruchamiane z pliku (przez dwukrotne kliknięcie) lub wykonywane bezpośrednio w wierszu polecenia interpretera. Uruchomienie w wierszu polecenia umożliwia złośliwemu oprogramowaniu kodowanie złośliwych skryptów jako usług automatycznego startu wewnątrz [kluczy rejestru autorun](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) jako [subskrypcji zdarzeń WMI](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) z repozytorium WMI. Ponadto osoba atakująca, która uzyskała dostęp do zainfekowanego komputera, może wprowadzić skrypt w wierszu polecenia.

**Oparte na dysku** (typ II: rekord rozruchu): rekord rozruchu jest pierwszym sektorem dysku lub woluminu i zawiera kod wykonywalny wymagany do rozpoczęcia procesu rozruchu systemu operacyjnego. Zagrożenia takie jak [Petya](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) mogą zainfekować rekord rozruchowy, zastępując go złośliwym kodem. Po uruchomieniu maszyny złośliwe oprogramowanie natychmiast zyskuje kontrolę. Rekord rozruchu znajduje się poza systemem plików, ale jest dostępny przez system operacyjny. Nowoczesne produkty antywirusowe mogą je skanować i przywracać.

## <a name="defeating-fileless-malware"></a>Pokonanie złośliwego oprogramowania bez plików

W firmie Microsoft aktywnie monitorujemy poziom zabezpieczeń w celu identyfikowania nowych trendów zagrożeń i opracowywania rozwiązań w celu ograniczenia klas zagrożeń. Instrumentujemy trwałe zabezpieczenia, które są skuteczne przed szeroką gamą zagrożeń. Za pośrednictwem interfejsu skanowania oprogramowania chroniącego przed złośliwym kodem (AMSI), monitorowania zachowania, skanowania pamięci i ochrony sektora rozruchu [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) może sprawdzać zagrożenia bez plików nawet w przypadku dużego zaciemniania. Technologie uczenia maszynowego w chmurze umożliwiają skalowanie tych zabezpieczeń przed nowymi i pojawiającym się zagrożeniami.

Aby dowiedzieć się więcej, przeczytaj: [Poza zasięgiem wzroku, ale nie niewidoczne: Pokonanie złośliwego oprogramowania bez plików za pomocą monitorowania zachowania, amsi i nowej generacji AV](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/)

## <a name="additional-resources-and-information"></a>Dodatkowe zasoby i informacje

Dowiedz się, jak [wdrażać funkcje ochrony przed zagrożeniami w Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection).
