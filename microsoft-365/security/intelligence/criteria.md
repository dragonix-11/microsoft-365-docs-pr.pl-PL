---
title: Jak firma Microsoft identyfikuje złośliwe oprogramowanie i potencjalnie niechciane aplikacje
ms.reviewer: ''
description: Dowiedz się, jak firma Microsoft przegląda oprogramowanie pod kątem naruszeń prywatności i innych negatywnych zachowań, aby ustalić, czy jest to złośliwe oprogramowanie, czy potencjalnie niechciana aplikacja.
keywords: zabezpieczenia, złośliwe oprogramowanie, zagrożenia związane z badaniami nad wirusami, złośliwe oprogramowanie badawcze, ochrona urządzenia, infekcja komputera, infekcja wirusów, opisy, korygowanie, najnowsze zagrożenia, MMdevice, Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem, PUA, potencjalnie niechciane aplikacje
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
ms.date: 12/13/2021
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 1f210ee98c8fc51cfa6900b19bb3cb5d5465dbb3
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663539"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Jak firma Microsoft identyfikuje złośliwe oprogramowanie i potencjalnie niechciane aplikacje

Firma Microsoft ma na celu zapewnienie wspaniałego i produktywnego środowiska Windows, pracując nad zapewnieniem bezpieczeństwa i kontroli nad urządzeniami. Firma Microsoft pomaga chronić Cię przed potencjalnymi zagrożeniami, identyfikując i analizując oprogramowanie i zawartość online. Podczas pobierania, instalowania i uruchamiania oprogramowania sprawdzamy reputację pobranych programów i upewniamy się, że jesteś chroniony przed znanymi zagrożeniami. Zostanie również wyświetlone ostrzeżenie dotyczące nieznanego nam oprogramowania.  

Możesz pomóc firmie Microsoft [, przesyłając nieznane lub podejrzane oprogramowanie do analizy](https://www.microsoft.com/wdsi/filesubmission/). Pomoże to zagwarantować, że nieznane lub podejrzane oprogramowanie zostanie przeskanowane przez nasz system w celu rozpoczęcia ustanawiania reputacji. [Dowiedz się więcej na temat przesyłania plików do analizy](submission-guide.md)

Następne sekcje zawierają omówienie klasyfikacji używanych dla aplikacji oraz typów zachowań, które prowadzą do tej klasyfikacji.

>[!NOTE]
> Nowe formy złośliwego oprogramowania i potencjalnie niechcianych aplikacji są opracowywane i szybko dystrybuowane. Poniższa lista może nie być wyczerpująca, a firma Microsoft zastrzega sobie prawo do ich dostosowywania, rozszerzania i aktualizowania bez wcześniejszego powiadomienia lub powiadomienia.

## <a name="unknown--unrecognized-software"></a>Nieznane — nierozpoznane oprogramowanie  

Żaden program antywirusowy ani technologia ochrony nie są idealne. Identyfikowanie i blokowanie złośliwych witryn i aplikacji oraz ufanie nowo wydanym programom i certyfikatom zajmuje trochę czasu. Z prawie 2 miliardów stron internetowych i oprogramowania stale aktualizowane i wydawane, nie można mieć informacji o każdej witrynie i programie.

Jako system wczesnego ostrzegania dla potencjalnie niewykrytego złośliwego oprogramowania należy traktować nieznane/niezbyt często pobierane ostrzeżenia. Zwykle występuje opóźnienie od czasu wydania nowego złośliwego oprogramowania do momentu jego zidentyfikowania. Nie wszystkie nietypowe programy są złośliwe, ale ryzyko w nieznanej kategorii jest znacznie wyższe dla typowego użytkownika. Ostrzeżenia dotyczące nieznanego oprogramowania nie są blokami. Użytkownicy mogą pobrać i uruchomić aplikację normalnie, jeśli chcą.

Po zebraniu wystarczającej ilości danych rozwiązania firmy Microsoft w zakresie zabezpieczeń mogą podjąć decyzję. Nie znaleziono żadnych zagrożeń lub aplikacja lub oprogramowanie jest klasyfikowane jako złośliwe oprogramowanie lub potencjalnie niechciane oprogramowanie.

## <a name="malware"></a>Złośliwego oprogramowania

Złośliwe oprogramowanie to nadrzędna nazwa aplikacji i innego kodu, takiego jak oprogramowanie, które firma Microsoft klasyfikuje bardziej szczegółowo jako *złośliwe oprogramowanie* lub *niechciane oprogramowanie*.

### <a name="malicious-software"></a>Złośliwe oprogramowanie

Złośliwe oprogramowanie to aplikacja lub kod, który zagraża bezpieczeństwu użytkowników. Złośliwe oprogramowanie może ukraść twoje dane osobowe, zablokować urządzenie do momentu zapłacenia okupu, użyć urządzenia do wysyłania spamu lub pobrać inne złośliwe oprogramowanie. Ogólnie rzecz biorąc, złośliwe oprogramowanie chce oszukać, oszukać lub oszukać użytkowników, umieszczając ich w stanach narażonych na zagrożenia.

Firma Microsoft klasyfikuje najbardziej złośliwe oprogramowanie do jednej z następujących kategorii:

* **Backdoor:** Typ złośliwego oprogramowania, który zapewnia złośliwym hakerom zdalny dostęp do urządzenia i kontrolę nad tym urządzeniem.

* **Polecenia i kontrolki:** Typ złośliwego oprogramowania, który infekuje urządzenie i nawiązuje komunikację z serwerem dowodzenia i kontroli hakerów, aby otrzymywać instrukcje. Po ustanowieniu komunikacji hakerzy mogą wysyłać polecenia, które mogą kraść dane, wyłączać i ponownie uruchamiać urządzenie oraz zakłócać działanie usług internetowych.

* **Downloader:** Typ złośliwego oprogramowania, który pobiera inne złośliwe oprogramowanie na urządzenie. Aby pobrać pliki, musi nawiązać połączenie z Internetem.

* **Kroplomierzem:** Typ złośliwego oprogramowania, który instaluje inne pliki złośliwego oprogramowania na urządzeniu. W przeciwieństwie do pobierania, dropper nie musi łączyć się z Internetem, aby usunąć złośliwe pliki. Porzucone pliki są zazwyczaj osadzone w samym zasuwce.

* **Wykorzystać:** Fragment kodu, który używa luk w zabezpieczeniach oprogramowania w celu uzyskania dostępu do urządzenia i wykonywania innych zadań, takich jak instalowanie złośliwego oprogramowania. [Zobacz więcej informacji o exploitach](exploits-malware.md).

* **Hacktool:** Typ narzędzia, którego można użyć do uzyskania nieautoryzowanego dostępu do urządzenia.

* **Wirus makr:** Typ złośliwego oprogramowania, który rozprzestrzenia się po zainfekowanych dokumentach, takich jak Microsoft Word lub Excel dokumentów. Wirus jest uruchamiany po otwarciu zainfekowanego dokumentu.

* **Zaciemniacz:** Typ złośliwego oprogramowania, który ukrywa swój kod i przeznaczenie, co utrudnia wykrywanie lub usuwanie oprogramowania zabezpieczającego.

* **Kradzież haseł:** Typ złośliwego oprogramowania, który zbiera twoje dane osobowe, takie jak nazwy użytkowników i hasła. Często współpracuje z keyloggerem, który zbiera i wysyła informacje o klawiszach, które naciskasz, i odwiedzanych witrynach internetowych.

* **Ransomware:** Typ złośliwego oprogramowania, który szyfruje pliki lub wprowadza inne modyfikacje, które mogą uniemożliwić korzystanie z urządzenia. Następnie zostanie wyświetlona nota okupu z informacją, że musisz zapłacić pieniądze lub wykonać inne akcje, zanim będzie można ponownie korzystać z urządzenia. [Zobacz więcej informacji o oprogramowaniu wymuszającym okup](/security/compass/human-operated-ransomware).

* **Nieautoryzowane oprogramowanie zabezpieczające:** Złośliwe oprogramowanie, które udaje oprogramowanie zabezpieczające, ale nie zapewnia żadnej ochrony. Ten typ złośliwego oprogramowania zwykle wyświetla alerty dotyczące nieistniejących zagrożeń na urządzeniu. Próbuje również przekonać Cię do płacenia za swoje usługi.

* **Trojan:** Typ złośliwego oprogramowania, który próbuje wydawać się nieszkodliwy. W przeciwieństwie do wirusa lub robaka, trojan nie rozprzestrzenia się sam. Zamiast tego stara się wyglądać legalnie, aby nakłonić użytkowników do pobrania i zainstalowania go. Po zainstalowaniu trojany wykonują różne złośliwe działania, takie jak kradzież danych osobowych, pobieranie innego złośliwego oprogramowania lub udzielanie osobom atakującym dostępu do urządzenia.

* **Kliknięcie trojana:** Typ trojana, który automatycznie klika przyciski lub podobne kontrolki w witrynach internetowych lub aplikacjach. Osoby atakujące mogą użyć tego konia trojańskiego do kliknięcia reklam online. Te kliknięcia mogą niesymetryczność ankiet online lub innych systemów śledzenia, a nawet instalować aplikacje na urządzeniu.

* **Robak:** Typ złośliwego oprogramowania, który rozprzestrzenia się na inne urządzenia. Robaki mogą rozprzestrzeniać się za pośrednictwem poczty e-mail, wiadomości błyskawicznych, platform udostępniania plików, sieci społecznościowych, udziałów sieciowych i dysków wymiennych. Zaawansowane robaki wykorzystują luki w zabezpieczeniach oprogramowania do propagacji.

### <a name="unwanted-software"></a>Niechciane oprogramowanie

Firma Microsoft uważa, że należy mieć kontrolę nad środowiskiem Windows. Oprogramowanie działające na Windows powinno zapewniać kontrolę nad urządzeniem za pomocą świadomych opcji i dostępnych kontrolek. Firma Microsoft identyfikuje zachowania oprogramowania, które gwarantują, że pozostajesz pod kontrolą. Klasyfikujemy oprogramowanie, które nie w pełni demonstruje te zachowania jako "niechciane oprogramowanie".

#### <a name="lack-of-choice"></a>Brak wyboru

Musisz otrzymać powiadomienie o tym, co dzieje się na urządzeniu, w tym o tym, jakie oprogramowanie działa i czy jest aktywne.

Oprogramowanie, które wykazuje brak wyboru, może:

* Nie należy zwracać znaczącej uwagi na temat zachowania oprogramowania oraz jego przeznaczenia i intencji.

* Nie można wyraźnie wskazać, kiedy oprogramowanie jest aktywne. Może również próbować ukryć lub ukryć swoją obecność.

* Instalowanie, ponowne instalowanie lub usuwanie oprogramowania bez twojej zgody, interakcji lub zgody.

* Zainstaluj inne oprogramowanie bez wyraźnego wskazania jego relacji z oprogramowaniem podstawowym.

* Obejście okien dialogowych zgody użytkownika z przeglądarki lub systemu operacyjnego.

* Fałszywie twierdzą, że oprogramowanie firmy Microsoft.

Oprogramowanie nie może wprowadzać w błąd ani utrudniać podejmowania decyzji dotyczących urządzenia. Uważa się, że zachowanie ogranicza wybór. Oprócz poprzedniej listy oprogramowanie, które wykazuje brak wyboru, może:

* Wyświetlanie przesadnych oświadczeń dotyczących kondycji urządzenia.

* Wprowadzaj w błąd lub niedokładne oświadczenia dotyczące plików, wpisów rejestru lub innych elementów na urządzeniu.

* Wyświetlaj oświadczenia w niepokojący sposób dotyczące kondycji urządzenia i wymagaj płatności lub niektórych akcji w zamian za rozwiązanie rzekomych problemów.

Oprogramowanie, które przechowuje lub przesyła działania lub dane użytkownika, musi:

* Zwróć uwagę i uzyskaj na to zgodę. Oprogramowanie nie powinno zawierać opcji, która konfiguruje je w celu ukrycia działań związanych z przechowywaniem lub przesyłaniem danych.

#### <a name="lack-of-control"></a>Brak kontroli

Musisz mieć możliwość kontrolowania oprogramowania na urządzeniu. Musisz mieć możliwość uruchamiania, zatrzymywania lub w inny sposób odwoływania autoryzacji do oprogramowania.

Oprogramowanie, które wykazuje brak kontroli, może:

* Uniemożliwia lub ogranicza wyświetlanie lub modyfikowanie funkcji lub ustawień przeglądarki.

* Otwórz okna przeglądarki bez autoryzacji.

* Przekieruj ruch internetowy bez powiadomienia i uzyskania zgody.

* Modyfikowanie lub manipulowanie zawartością strony internetowej bez twojej zgody.

Oprogramowanie, które zmienia środowisko przeglądania, musi używać tylko obsługiwanego przez przeglądarkę modelu rozszerzalności na potrzeby instalacji, wykonywania, wyłączania lub usuwania. Przeglądarki, które nie zapewniają obsługiwanych modeli rozszerzalności, są uważane za nierozpuszczalne i nie powinny być modyfikowane.

#### <a name="installation-and-removal"></a>Instalacja i usuwanie

Musisz mieć możliwość uruchamiania, zatrzymywania lub w inny sposób odwoływania autoryzacji udzielonej oprogramowaniu. Oprogramowanie powinno uzyskać zgodę użytkownika przed zainstalowaniem i musi zapewnić jasny i prosty sposób instalowania, odinstalowywania lub wyłączania.

Oprogramowanie, które zapewnia *słabe środowisko instalacji* , może zostać spakowane lub pobrane inne "niechciane oprogramowanie" sklasyfikowane przez firmę Microsoft.

Oprogramowanie, które zapewnia *słabe środowisko usuwania* , może:

* Prezentuj mylące lub wprowadzające w błąd monity lub wyskakujące okienka podczas próby jego odinstalowania.

* Nie można używać standardowych funkcji instalacji/odinstalowywania, takich jak Dodawanie/usuwanie programów.

#### <a name="advertising-and-advertisements"></a>Reklamy i reklamy

Oprogramowanie, które promuje produkt lub usługę poza samym oprogramowaniem, może zakłócać środowisko obliczeniowe. Podczas instalowania oprogramowania, które prezentuje reklamy, należy mieć jasny wybór i kontrolę.

Reklamy prezentowane przez oprogramowanie muszą:

* Uwzględnij oczywisty sposób zamykania anonsu przez użytkowników. Akt zamknięcia reklamy nie może otwierać innego anonsu.

* Dołącz nazwę oprogramowania, które przedstawiło reklamę.

Oprogramowanie, które prezentuje te reklamy, musi:

* Podaj standardową metodę odinstalowywania oprogramowania o tej samej nazwie, jak pokazano w prezentowej anonsie.

Wyświetlane reklamy muszą:

* Odróżniaj się od zawartości witryny internetowej.

* Nie wprowadzaj w błąd, oszukuj ani nie wprowadzaj w błąd.

* Nie zawiera złośliwego kodu.

* Nie wywołaj pobierania pliku.

#### <a name="consumer-opinion"></a>Opinia konsumentów

Firma Microsoft utrzymuje ogólnoświatową sieć analityków i systemów wywiadowczych, w której można [przesyłać oprogramowanie do analizy](https://www.microsoft.com/wdsi/filesubmission). Twój udział pomaga firmie Microsoft szybko identyfikować nowe złośliwe oprogramowanie. Po analizie firma Microsoft tworzy analizę zabezpieczeń dla oprogramowania spełniającego opisane kryteria. Ta analiza zabezpieczeń identyfikuje oprogramowanie jako złośliwe oprogramowanie i jest dostępne dla wszystkich użytkowników za pośrednictwem Program antywirusowy Microsoft Defender i innych rozwiązań firmy Microsoft do ochrony przed złośliwym kodem.

## <a name="potentially-unwanted-application-pua"></a>Potencjalnie niechciana aplikacja (PUA)

Nasza ochrona pua ma na celu ochronę produktywności użytkowników i zapewnienie przyjemnych środowisk Windows. Ta ochrona pomaga zapewnić bardziej wydajne, wydajne i wspaniałe środowiska Windows. Aby uzyskać instrukcje dotyczące włączania ochrony pua w Chromium opartych na Microsoft Edge i Program antywirusowy Microsoft Defender, zobacz [Wykrywanie i blokowanie potencjalnie niechcianych aplikacji](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*PuAs nie są uważane za złośliwe oprogramowanie.*

Firma Microsoft używa określonych kategorii i definicji kategorii do klasyfikowania oprogramowania jako pua.

* **Oprogramowanie reklamowe:** Oprogramowanie, które wyświetla reklamy lub promocje, lub monituje o ukończenie ankiet dotyczących innych produktów lub usług w oprogramowaniu innym niż samo w sobie. Obejmuje to oprogramowanie, które wstawia anonsy do stron internetowych.

* **Oprogramowanie Torrent (tylko Enterprise):** oprogramowanie, które jest używane do tworzenia lub pobierania potoków lub innych plików używanych specjalnie z technologiami udostępniania plików równorzędnych.

* **Oprogramowanie kryptograficzne (tylko Enterprise):** oprogramowanie, które używa zasobów urządzenia do wydobywania kryptowalut.

* **Łączenie oprogramowania:** Oprogramowanie, które oferuje instalację innego oprogramowania, które nie jest opracowywane przez tę samą jednostkę lub które nie jest wymagane do uruchomienia oprogramowania. Ponadto oprogramowanie, które oferuje instalację innego oprogramowania, które kwalifikuje się jako pua na podstawie kryteriów opisanych w tym dokumencie.

* **Oprogramowanie marketingowe:** Oprogramowanie, które monitoruje i przesyła działania użytkowników do aplikacji lub usług innych niż samo w sobie na potrzeby badań marketingowych.

* **Oprogramowanie do uchylania się od płacenia podatków:** Oprogramowanie, które aktywnie próbuje uniknąć wykrycia przez produkty zabezpieczające, w tym oprogramowanie, które zachowuje się inaczej w obecności produktów zabezpieczających.

* **Słaba reputacja branży:** Oprogramowanie wykrywane przez zaufanych dostawców zabezpieczeń przy użyciu swoich produktów zabezpieczających. Branża zabezpieczeń zajmuje się ochroną klientów i ulepszaniem ich doświadczeń. Firma Microsoft i inne organizacje w branży zabezpieczeń stale wymieniają się wiedzą na temat plików, które przeanalizowaliśmy, aby zapewnić użytkownikom najlepszą możliwą ochronę.

