---
title: Zagrożenia bez plików
ms.reviewer: ''
description: Dowiedz się więcej o kategoriach zagrożeń bez plików i złośliwego oprogramowania, które niegroźne
keywords: bez plików, złośliwe oprogramowanie bez plików, mieszkające z ziemi, anabiny, amsi, monitorowanie zachowania, skanowanie pamięci, ochrona sektora rozruchu, zabezpieczenia, złośliwe oprogramowanie, Windows Defender ATP, oprogramowanie antywirusowe, audio/wideo, Microsoft Defender ATP, ochrona następnej generacji
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
ms.openlocfilehash: 97545714ff468c7be238585ab5d137a1ac93a5f9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705920"
---
# <a name="fileless-threats"></a>Zagrożenia bez plików

Czym dokładnie są zagrożenia bez plików? Termin "bez plików" sugeruje, że w pliku nie może dojść do zagrożenia, takiego jak backdoor, który mieszka tylko w pamięci komputera. Jednak nie istnieje jedna definicja złośliwego oprogramowania bez plików. Ten termin jest stosowany ogólnie i czasami opisywał rodziny złośliwego oprogramowania, które korzystają z plików do obsługi.

Ataki dotyczą [kilku etapów działania](https://attack.mitre.org/wiki/ATT&CK_Matrix) , takich jak wykonywanie, zachowywanie się lub kradzież informacji. Niektóre części łańcucha ataków mogą być bez plików, podczas gdy inne mogą obejmować system plików w pewien sposób.

W celu zwiększenia przejrzystości zagrożenia bez plików są pogrupowane w różne kategorie.

![Kompleksowy diagram złośliwego oprogramowania bez plików.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Rysunek 1. Kompleksowy diagram złośliwego oprogramowania bez plików*

Zagrożenia bez plików można klasyfikować według ich punktów wejścia, co wskazuje, jak złośliwe oprogramowanie bez plików może dotrzeć na komputer. Można je uzyskać za pośrednictwem luki w zabezpieczeniach sprzętu lub poprzez regularne wykonywanie aplikacji i skryptów.

Następnie należy wyświetlić formularz punktu wejścia. Na przykład exploity mogą być oparte na plikach lub danych sieciowych, urządzenia zewnętrzne PCI to rodzaj wektora sprzętowego, a skrypty i pliki wykonywalne to podkategorie wektora wykonywania.

Na koniec sklasyfikuj hosta tej wirusem. Na przykład aplikacja Flash może zawierać wiele zagrożeń, takich jak exploit, proste wykonywalne i złośliwe oprogramowanie układowe z urządzenia.

Klasyfikowanie ułatwia dzielenie i kategoryzowanie różnych rodzajów zagrożeń bez plików. Niektóre są bardziej niebezpieczne, ale także trudniejsze do wdrożenia, natomiast inne są częściej używane mimo tego, że nie są zbyt zaawansowane (lub precyzyjnie z tego powodu).

Na podstawie tej kategoryzacji możesz określić trzy główne typy zagrożeń bez plików na podstawie tego, ile odcisków palca mogą one pozostawić na zainfekowanych komputerach.

## <a name="type-i-no-file-activity-performed"></a>Typ I: Nie wykonano żadnych działań na plikach

Całkowicie niebędące plikiem złośliwe oprogramowanie można uznać za takie, które nigdy nie wymaga pisania pliku na dysku. Jak takie złośliwe oprogramowanie infekuje komputer w pierwszej kolejności? Przykładem jest to, że komputer docelowy odbiera złośliwe pakiety sieciowe wykorzystujące lukę w zabezpieczeniach blue. Ta luka pozwala na zainstalowanie backdooru DoublePulsar, który znajduje się jedynie w pamięci kernelu. W takim przypadku plik nie jest zapisywany ani nie są zapisane żadne dane.

Naruszone urządzenie może również zawierać złośliwy kod, który ukrywa oprogramowanie układowe urządzenia (na przykład HTML), urządzenie zewnętrzne USB (takie jak atak BadUSB) lub oprogramowanie układowe karty sieciowej. Wszystkie te przykłady nie wymagają uruchamiania pliku na dysku i mogą być wczytyne tylko w pamięć. Złośliwy kod może wystarczyć podczas ponownego rozruchu, ponownego sformatowania dysku i ponownej instalacji systemu operacyjnego.

Ten typ może być szczególnie trudny do wykrycia, ponieważ większość produktów antywirusowych nie ma możliwości sprawdzania oprogramowania układowego. W przypadkach, gdy produkt ma możliwość sprawdzania i wykrywania złośliwego oprogramowania układowego, nadal występują istotne problemy związane ze rozwiązywaniem problemów na tym poziomie. Tego typu złośliwe oprogramowanie bez użycia plików wymaga wysokiego poziomu zaawansowania i często zależy od konkretnej konfiguracji sprzętu lub oprogramowania. Nie jest to wektor ataków, który można łatwo i niezawodnie wykorzystać. Mimo że są niebezpieczne, zagrożenia tego typu są nietypowe i niepraktyczne w przypadku większości ataków.

## <a name="type-ii-indirect-file-activity"></a>Typ II. Pośrednia aktywność plików

Istnieją inne sposoby, za pomocą których złośliwe oprogramowanie może zapewnić obecność bez plików na komputerze bez konieczności wytłaniania znacznych prac inżynierskich. Złośliwe oprogramowanie tego typu bez plików nie zapisuje bezpośrednio plików w systemie plików, ale może korzystać z plików pośrednio. Na przykład po zainstalowaniu przez atakujących [backdoorów poshspy](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) złośliwego polecenia programu PowerShell w repozytorium WMI i skonfigurowaniu filtru WMI do okresowego uruchamiania tego polecenia.

Taką instalację można przeprowadzić za pośrednictwem wiersza polecenia bez konieczności wcześniejszego doinstalowania pliku za pomocą backdooru. Złośliwe oprogramowanie można zainstalować i uruchomić bez konieczności dotykania systemu plików. Repozytorium WMI jest jednak przechowywane w pliku fizycznym w centralnym obszarze magazynu zarządzanym przez menedżera obiektów CIM i zwykle zawiera wiarygodne dane. Mimo że łańcuch żywnościowy zawiera technicznie plik fizyczny, jest to uznawane za atak bez plików, ponieważ repozytorium WMI to wielozadaniowy kontener danych, który nie może zostać wykryty i usunięty.

## <a name="type-iii-files-required-to-operate"></a>Typ III. Pliki wymagane do obsługi

Niektóre złośliwe oprogramowanie może zachowywać się bez plików, ale nie bez używania plików do obsługi. Przykładem w tym scenariuszu jest Kovter, który tworzy w rejestrze program obsługi otwartych czasowników powłoki dla losowego rozszerzenia pliku. Otwarcie pliku z takim rozszerzeniem spowoduje wykonanie skryptu za pośrednictwem wiarygodnego narzędzia, które mshta.exe.

![Obraz klucza rejestru Kovtera.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Rysunek 2. Klucz rejestru Kovtera*

Po wywołaniu otwartego czasownika jest uruchomione skojarzone polecenie z rejestru, co powoduje wykonanie małego skryptu. Skrypt ten odczytuje dane z dodatkowo klucza rejestru i wykonuje je, co z kolei prowadzi do ładowania końcowego obciążenia. Jednak aby w pierwszej kolejności wyzwolić czasownik otwarty, Kovter musi upuścić plik z tym samym rozszerzeniem, do którym kierowane jest czasownik (w powyższym przykładzie rozszerzenie to bbf5590fd). Musi też ustawić klucz autowy uruchamiania skonfigurowany do otwierania takiego pliku podczas uruchamiania komputera.

Kovter jest uważany za zagrożenie bez pliku, ponieważ system plików nie jest praktyczne. Pliki z losowymi rozszerzeniami zawierają dane-śmieci, których nie można używać do sprawdzania obecności zagrożenia. Pliki przechowywane w rejestrze to kontenery, których nie można wykrywać ani usuwać w przypadku wykrycia złośliwej zawartości.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Kategoryzowanie zagrożeń bez plików przez hosta hostów wirusów

Po opisaniu szerokich kategorii możemy teraz przejść do szczegółowych informacji i udostępnić zestawienie hostów infekcji. Ta pełna klasyfikacja obejmuje panoramę tego, co jest zwykle nazywane złośliwym oprogramowaniem bez plików. Są to nasze wysiłki w zakresie badań i opracowywania nowych funkcji ochrony, które chronią klasy ataków i zapewniają, że złośliwe oprogramowanie nie dostąpy do ręki w wyścigu na ręce.

### <a name="exploits"></a>Exploits

**Oparte** na plikach (typ III: wykonywalny, Flash, Java, dokumenty): początkowy plik może wykorzystać system operacyjny, przeglądarkę, aparat Java, aparat Flash itp. w celu wykonania kodu powłoki i dostarczenia ładu w pamięci. Chociaż ład jest bez plików, początkowy wektor wprowadzania to plik.

**Oparte na sieci** (typ I): komunikacja sieciowa, która wykorzystuje luki w zabezpieczeniach na komputerze docelowym, może zapewnić wykonywanie kodu w kontekście aplikacji lub kernel. Przykład to WannaCry, który wykorzystuje wcześniej usuniętą lukę w protokole SMB w celu dostarczania backdooru w pamięci kernelu.

### <a name="hardware"></a>Sprzęt

**Urządzenia (typ** I: karta sieciowa, dysk twardy): Urządzenia takie jak dyskietki twarde i karty sieciowe wymagają oprogramowania dedykowanego do działania. Oprogramowanie przechowające i działające w tym urządzeniu nosi nazwę oprogramowania układowego. Mimo że jest to skomplikowane zadanie, oprogramowanie układowe może zostać zainfekowane złośliwym oprogramowaniem, na co nałożony został zespół ds. [równań](https://www.kaspersky.com/blog/equation-hdd-malware/7623/).

**Procesor (typ** I): nowoczesne procesory CPU są złożone i mogą zawierać podsystemy z oprogramowaniem układowym do celów zarządzania. Oprogramowanie układowe może być narażona na przechwytanie i umożliwić wykonywanie złośliwego kodu, który będzie działać z poziomu procesora. W grudniu 2017 r. dwóch przestępców zgłosiło lukę, która może umożliwić atakującym wykonywanie kodu wewnątrz aparatu zarządzania [obecnego](https://en.wikipedia.org/wiki/Intel_Management_Engine) na każdym nowoczesnym procesorze firmy Intel. W międzyczasie grupa atakująca PLATINUM została obserwowana i ma możliwość używania technologii [Active Management Technology (AMT)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) firmy Intel do niewidocznej komunikacji w [sieci z](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/) pominięciem zainstalowanego systemu operacyjnego. Me and AMT are essentially micro-computers that live inside the CPU and that operate at a very low level. Ponieważ celem tych technologii jest zapewnienie możliwości zdalnego zarządzania, mają one bezpośredni dostęp do sprzętu, są niezależne od systemu operacyjnego i mogą działać nawet wtedy, gdy komputer jest wyłączony.

Poza tym, że oprogramowanie jest narażone na poziom oprogramowania układowego, procesory cpu mogą być stosowane przy użyciu backdoorów wstawionych bezpośrednio do obwodu sprzętu. Ten atak został [zbadany i udowodniony](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) w przeszłości. Zgłoszono, że niektóre modele procesorów x86 zawierają pomocniczy osadzony procesor RISC, który w praktyce może zapewnić [backdoor](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) , dzięki którym zwykłe aplikacje mogą uzyskać wykonywanie bardziej uprzywilejowanych.

**Usb-based** (Type I): urządzenia USB wszelkiego rodzaju można ponownie zaprogramować za pomocą złośliwego oprogramowania układowego umożliwiającego interakcję z systemem operacyjnym w fikcyjny sposób. Na przykład technika [BadUSB](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) umożliwia ponownemu programowanemu dyskowi USB działanie jako klawiatury, która wysyła polecenia do komputerów za pomocą naciśnięć klawiszy lub jako kartę sieciową, która może przekierować ruch w sposób.

**NA PODSTAWIE (** typ I): STEROWNIK TO oprogramowanie układowe działające wewnątrz firmy. Wykonuje się wtedy, gdy komputer jest włączony, inicjuje sprzęt, a następnie przenosi kontrolkę do sektora rozruchu. KOD.S.ODS to ważny składnik, który działa na niskim poziomie i wykonuje się przed sektora rozruchowego. Możliwe jest ponowne przeprogramowanie oprogramowania układowego IT za pomocą złośliwego kodu, jak to miało miejsce w przeszłości, dzięki programowi [Rootkit firmy Mebromi](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/).

**Oparty na funkcji Hypervisor** (typ I): nowoczesne procesory CPU obsługują hipervisor sprzętowy, co pozwala systemowi operacyjnemu na tworzenie niezawodnych maszyn wirtualnych. Maszynę wirtualną działa w zamkniętym, symulowanym środowisku, a z drugiej względów nie jest świadoma emulacji. Złośliwe oprogramowanie przejmuje komputer, może zaimplementować niewielki hipervisor, aby ukryć się poza obszarem uruchomionego systemu operacyjnego. Tego rodzaju złośliwe oprogramowanie było theorized w przeszłości i obserwowano prawdziwe programy rootkitów hipervisorów [, chociaż](http://seclists.org/fulldisclosure/2017/Jun/29) do tej pory jest ich niewiele.

### <a name="execution-and-injection"></a>Wykonywanie i wkierowanie

**Oparty na plikach** (typ III: pliki wykonywalne, biblioteki DLL, pliki LNK, zaplanowane zadania): jest to standardowy wektor wykonywania. Prosty plik wykonywalny można uruchomić jako pierwszego złośliwego oprogramowania w celu uruchomienia dodatkowego obciążenia pamięci lub dodać go do innych legalnych uruchomionych procesów.

**Oparte na makrach** (typ III: Office dokumenty): język [VBA](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office) to elastyczne i zaawansowane narzędzie służące do automatyzowania zadań edytowania i dodawania dynamicznych funkcji do dokumentów. Dlatego może być nadużyciem przez atakujących w celu przeprowadzania złośliwych operacji, takich jak dekodowanie, uruchamianie lub wsadanie pliku wykonywalnego payload, a nawet implementowanie całego oprogramowania wymuszającego okup, na przykład w przypadku [QKG](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/). Makra są wykonywane w ramach procedury Office (np. Winword.exe) i implementowane w języku skryptów. Nie istnieje plik binarny wykonywalny, który może zostać sprawdzony przez oprogramowanie antywirusowe. Mimo Office aplikacji wymagane jest wyraźna zgoda użytkownika na wykonywanie makr na podstawie dokumentu, jednak przestępcy korzystają z technik socjograficznych, aby nakłaniać użytkowników do wykonywania makr.

**Script-based** (Type II: file, service, registry, WMI repo, shell): Języki skryptów JavaScript, VBScript i PowerShell są domyślnie dostępne na Windows platformach. Skrypty mają taką samą zaletę jak makra, są plikami tekstowym (a nie plikami wykonywalnymi binarnymi) i uruchamiane w kontekście tego użytkownika (takiego jak wscript.exe, powershell.exe), który jest czystym i uzasadnionym składnikiem. Skrypty są elastyczne i można je uruchamiać z pliku (przez dwukrotne kliknięcie) lub uruchamiać bezpośrednio w wierszu polecenia użytkownika. Uruchomienie w wierszu polecenia umożliwia złośliwemu oprogramowaniu kodowanie złośliwych skryptów jako usług autostartu w kluczach rejestru [Autorun](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) jako subskrypcji zdarzeń [usługi WMI](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) z repo usługi WMI. Ponadto atakujący, który uzyskał dostęp do zainfekowanego komputera, może wprowadzić skrypt w wierszu polecenia.

**Oparty na** dysku (Typ II: Rekord rozruchu): Rekord rozruchu to pierwszy rodzaj dysku lub woluminu i zawiera wykonywalny kod wymagany do rozpoczęcia procesu rozruchu systemu operacyjnego. Zagrożenia, [takie jak Petya](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) , mogą zainfekować rekord rozruchu przez nadpisanie go złośliwym kodem. Po uruchomieniu komputera złośliwe oprogramowanie natychmiast zyskuje kontrolę. Rekord rozruchu znajduje się poza systemem plików, ale jest dostępny dla systemu operacyjnego. Nowoczesne produkty antywirusowe mogą je skanować i przywracać.

## <a name="defeating-fileless-malware"></a>Pokonanie złośliwego oprogramowania bez plików

Firma Microsoft aktywnie monitoruje poziom zabezpieczeń, aby identyfikować nowe trendy zagrożeń i tworzyć rozwiązania w celu ograniczenia klasy zagrożeń. Trwałe zabezpieczenia, które są skuteczne w odniesieniu do szerokiej gamy zagrożeń, są trwałe. Za pośrednictwem interfejsu AMSI (AntiMalware Scan Interface), monitorowania zachowania, skanowania pamięci i ochrony sektora rozruchu program [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) może sprawdzać zagrożenia bez użycia plików nawet w przypadku intensywnego zasłaniania plików. Technologie uczenia maszynowego w chmurze umożliwiają skalowanie tych zabezpieczeń przed nowymi i pojawiającymi się zagrożeniami.

Aby dowiedzieć się więcej, przeczytaj: Poza wzrokiem, ale nie niewidoczny: Pokonanie złośliwego oprogramowania bez plików, monitorowanie zachowania [, AMSI i audio/wideo nowej generacji](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/)

## <a name="additional-resources-and-information"></a>Dodatkowe zasoby i informacje

Dowiedz się, jak [wdrożyć funkcje ochrony przed zagrożeniami w Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection).
