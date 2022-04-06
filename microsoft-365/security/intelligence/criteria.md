---
title: Sposób, w jaki firma Microsoft identyfikuje złośliwe oprogramowanie i potencjalnie niechciane aplikacje
ms.reviewer: ''
description: Dowiedz się, jak firma Microsoft przegląda oprogramowanie pod kątem naruszeń prywatności i innych negatywnych zachowań, aby ustalić, czy jest to złośliwe oprogramowanie lub potencjalnie niechciana aplikacja.
keywords: zabezpieczenia, złośliwe oprogramowanie, zagrożenia związane z badaniami wirusów, złośliwe oprogramowanie, ochrona urządzeń, zainfekowanie komputera, zainfekowanie komputera, zainfekowanie komputera, opisy, działania naprawcze, najnowsze zagrożenia, MMdevice, Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem, pua, potencjalnie niechciane aplikacje
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
ms.openlocfilehash: 3eb7eefb5309383b46189f784f811224dcfb2b28
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705890"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Sposób, w jaki firma Microsoft identyfikuje złośliwe oprogramowanie i potencjalnie niechciane aplikacje

Firma Microsoft zapewnia miła i wydajną Windows, pracując nad zapewnieniem bezpieczeństwa i kontroli nad swoimi urządzeniami. Firma Microsoft pomaga chronić Cię przed potencjalnymi zagrożeniami, identyfikując i analizując oprogramowanie i zawartość online. Podczas pobierania, instalowania i uruchamiania oprogramowania sprawdzamy reputację pobranych programów i zapewniamy ochronę przed znanymi zagrożeniami. Ponadto jest ostrzegany o nieznanym oprogramowaniu.  

Możesz pomóc firmie Microsoft [przesyłając nieznane lub podejrzane oprogramowanie do analizy](https://www.microsoft.com/wdsi/filesubmission/). Pomoże to zapewnić, że nieznane lub podejrzane oprogramowanie jest skanowane przez nasz system w celu rozpoczęcia ustanawiania reputacji. [Dowiedz się więcej o przesyłaniu plików do analizy](submission-guide.md)

W następnych sekcjach przedstawiono omówienie klasyfikacji, których używamy dla aplikacji, i typów zachowań, które prowadzą do tej klasyfikacji.

>[!NOTE]
> Nowe formy złośliwego oprogramowania i potencjalnie niepożądanych aplikacji są szybko opracowywane i rozpowszechniane. Ta lista może nie być pełna i firma Microsoft zastrzega sobie prawo do ich dostosowania, rozszerzenia i zaktualizowania bez wcześniejszego powiadomienia lub powiadomienia.

## <a name="unknown--unrecognized-software"></a>Nieznane — nierozpoznane oprogramowanie  

Żadna technologia oprogramowania antywirusowego ani ochrony nie jest idealna. Rozpoznawanie i blokowanie złośliwych witryn i aplikacji lub ufanie nowo wydanym programom i certyfikatom zajmuje trochę czasu.Niemal 2 miliardy witryn internetowych i oprogramowania są stale aktualizowane i wydane, dlatego nie można mieć informacji o każdej pojedynczej witrynie i programie.

Ostrzeżenia o nieznanym/nietypowym pobraniu są systemami wczesnego ostrzeżenia dla potencjalnie niezauwaganych złośliwego oprogramowania. Zazwyczaj czas, w który nowe złośliwe oprogramowanie zostanie wydane, jest opóźniony do czasu jego zidentyfikowania. Nie wszystkie nietypowe programy są złośliwe, ale ryzyko w tej kategorii jest znacznie większe dla typowego użytkownika. Ostrzeżenia dla nieznanego oprogramowania nie są blokami. Jeśli chcesz, użytkownicy mogą pobrać i uruchomić aplikację normalnie.

Po zsyłaniu wystarczającej ilości danych rozwiązania zabezpieczające firmy Microsoft mogą dokonać wyznaczania. Nie zostaną znalezione żadne zagrożenia albo aplikacja lub oprogramowanie zostaną sklasyfikowane jako złośliwe oprogramowanie lub potencjalnie niechciane oprogramowanie.

## <a name="malware"></a>Złośliwe oprogramowanie

Złośliwe oprogramowanie to zbyt wiele nazw aplikacji i innych kodów, takich jak oprogramowanie, które firma Microsoft klasyfikuje bardziej szczegółowie jako złośliwe *oprogramowanie lub* *niechciane oprogramowanie*.

### <a name="malicious-software"></a>Złośliwe oprogramowanie

Złośliwe oprogramowanie to aplikacja lub kod, który może naruszyć bezpieczeństwo użytkowników. Złośliwe oprogramowanie może ukraść informacje osobiste, zablokować urządzenie do czasu zapłacenia okupu, używania urządzenia do wysyłania spamu lub pobierania innego złośliwego oprogramowania. Na ogół złośliwe oprogramowanie chce nakłonić użytkowników, oszukiwać ich lub wyzywać ich w stanach zagrożenia.

Firma Microsoft klasyfikuje najbardziej złośliwe oprogramowanie w jednej z następujących kategorii:

* **Backdoor:** Typ złośliwego oprogramowania, które umożliwia złośliwym hakerom zdalny dostęp do urządzenia i sterowanie jego urządzeniem.

* **Polecenia i kontrolki:** Typ złośliwego oprogramowania, które infekuje urządzenie i nawiązuje komunikację z serwerem poleceń i sterowania hakerów w celu otrzymywania instrukcji. Po nawiązaniu komunikacji hakerzy mogą wysyłać polecenia, które mogą ukraść dane, zamknąć i ponownie uruchomić urządzenie oraz zakłócić działanie usług sieci Web.

* **Pobierzer:** Rodzaj złośliwego oprogramowania, które pobiera na urządzenie inne złośliwe oprogramowanie. Aby można było pobierać pliki, musi ono nawiązać połączenie z Internetem.

* **Dropper:** Typ złośliwego oprogramowania, które instaluje na urządzeniu inne pliki złośliwego oprogramowania.W przeciwieństwie do narzędzia do pobierania, upuszczanie nie musi łączyć się z Internetem w celu upuszczenia złośliwych plików. Porzucone pliki są zwykle osadzone w samym upuszczeniu.

* **Exploit:** Fragment kodu, który wykorzystuje luki w zabezpieczeniach oprogramowania w celu uzyskania dostępu do urządzenia i wykonania innych zadań, takich jak instalowanie złośliwego oprogramowania. [Zobacz więcej informacji na temat wykorzystania danych](exploits-malware.md).

* **Narzędzie Hacktool:** Jest to rodzaj narzędzia, za pomocą których można uzyskać nieautoryzowany dostęp do urządzenia.

* **Wirus makr:** Rodzaj złośliwego oprogramowania, które rozpowszechnia się po zainfekowanych dokumentach, takich jak Microsoft Word lub Excel dokumenty. Wirus zostanie uruchomiony, gdy otworzysz zainfekowany dokument.

* **Opis:** Rodzaj złośliwego oprogramowania, które ukrywa kod i przeznaczenie, co utrudnia wykrycie lub usunięcie oprogramowania zabezpieczającego.

* **Kradzież haseł:** Rodzaj złośliwego oprogramowania, które zbiera informacje osobiste, takie jak nazwy użytkowników i hasła. Często współpracuje z innymi użytkownikami, którzy zbierają i wysyłają informacje o naciskanych klawiszach i odwiedzanych witrynach internetowych.

* **Oprogramowanie wymuszające okup:** Typ złośliwego oprogramowania, które szyfruje pliki lub wprowadza inne modyfikacje, które mogą uniemożliwiać korzystanie z urządzenia. Następnie jest wyświetlany komunikat o ransomie z informacjami, że należy zapłacić pieniądze lub wykonać inne czynności, zanim będzie można ponownie korzystać z urządzenia. [Zobacz więcej informacji na temat oprogramowania wymuszającego okup](/security/compass/human-operated-ransomware).

* **Oprogramowanie zabezpieczające rogue:** Złośliwe oprogramowanie, które wydaje się być oprogramowaniem zabezpieczającym, ale nie zapewnia żadnej ochrony. Tego typu złośliwe oprogramowanie zazwyczaj wyświetla alerty o brakach zabezpieczeń na Twoim urządzeniu. Ponadto próbuje przekonać Cię o zapłaceni za jej usługi.

* **Trojański:** Typ złośliwego oprogramowania, które próbuje wyglądać na nieszkodliwe. W przeciwieństwie do wirusa lub robaka, trojański nie rozpowszechnia się sam. Zamiast tego próbuje on wyglądać na wiarygodnego na przykład dla użytkowników pobierających i instalując je. Po zainstalowaniu trojańskie wykonują różne złośliwe działania, takie jak kradzież informacji osobistych, pobieranie innego złośliwego oprogramowania lub udzielanie atakującym dostępu do Twojego urządzenia.

* **Trojański kliker:** Rodzaj trojańskiego, który automatycznie klika przyciski lub podobne kontrolki w witrynach internetowych lub aplikacjach. Atakujący mogą używać tego trojańskiego do klikania reklam online. Te kliknięcia mogą skość ankiety online lub inne systemy śledzenia, a nawet zainstalować aplikacje na urządzeniu.

* **Robak:** Typ złośliwego oprogramowania, które można rozpowszechniać na innych urządzeniach. Robaki można rozpowszechniać za pośrednictwem poczty e-mail, wiadomości błyskawicznych, platform udostępniania plików, sieci społecznościowych, udziałów sieciowych i dysków wymiennych. Zaawansowane robaki wykorzystuje luki w zabezpieczeniach oprogramowania, aby je propagować.

### <a name="unwanted-software"></a>Niechciane oprogramowanie

Firma Microsoft uważa, że należy mieć kontrolę nad swoim Windows klienta. Oprogramowanie działające w Windows powinno kontrolować Twoje urządzenie za pośrednictwem świadomych wyborów i kontrolek z ułatwieniami dostępu. Firma Microsoft identyfikuje zachowania oprogramowania, które zapewniają Ci pełną kontrolę. Klasyfikowamy oprogramowanie, które nie przedstawia w pełni tych zachowań jako "niechciane oprogramowanie".

#### <a name="lack-of-choice"></a>Brak możliwości wyboru

Musisz być powiadamiany o tym, co dzieje się na Twoim urządzeniu, w tym o tym, jakie oprogramowanie działa i czy jest aktywne.

Oprogramowanie, które jest w brak możliwości wyboru, może:

* Nie dostarczaj widocznych informacji na temat zachowania oprogramowania oraz jego przeznaczenia i przeznaczenia.

* Nie można wyraźnie wskazać, kiedy oprogramowanie jest aktywne. Może też próbować ukryć lub ukryć informacje o jego obecności.

* Instaluj, ponownie instaluj lub usuwaj oprogramowanie bez Twojej zgody, interakcji lub zgody.

* Instaluj inne oprogramowanie bez wyraźnego wskazania jego zależności z oprogramowaniem podstawowym.

* Obejście okien dialogowych zgody użytkownika z przeglądarki lub systemu operacyjnego.

* Fałszywie podszywuje się pod firmę Microsoft jako oprogramowanie.

Oprogramowanie nie może wprowadzać w błąd ani nakłonić użytkownika do podejmowania decyzji dotyczących posiadanych urządzeń. Jest to zachowanie, które ogranicza dostępne wybory. Poza poprzednią listą oprogramowanie, które nie ma wyboru, może:

* Wyświetl przesadzone oświadczenia dotyczące kondycji urządzenia.

* Wywrzeć mylące lub nieprawidłowe roszczenia dotyczące plików, wpisów rejestru lub innych elementów na urządzeniu.

* Wyświetl roszczenia w alarmujący sposób na temat kondycji urządzenia i wymagaj płatności lub pewnych działań w zamian za rozwiązanie tych rzekomo problemów.

Oprogramowanie, które przechowuje lub przesyła dane lub działania użytkownika, musi:

* Daj Ci powiadomienie i uzyskaj na to zgodę. Oprogramowanie nie powinno zawierać opcji służącej do konfigurowania jej w celu ukrywania działań związanych z przechowywaniem lub przekazywaniem danych.

#### <a name="lack-of-control"></a>Brak kontroli

Musisz mieć możliwość sterowania oprogramowaniem na twoim urządzeniu. Użytkownik musi mieć możliwość uruchomienia, zatrzymania lub cofnięcia w inny sposób autoryzacji oprogramowania.

Oprogramowanie w przypadku braku kontroli może:

* Uniemożliwianie lub ograniczanie możliwości wyświetlania lub modyfikowania ustawień lub funkcji przeglądarki.

* Otwieranie okien przeglądarki bez autoryzacji.

* Przekieruj ruch internetowy bez powiadomienia i uzyskiwania zgody.

* Modyfikuj zawartość stron sieci Web lub manipuluj nią bez Twojej zgody.

Oprogramowanie, które zmienia środowisko przeglądania, musi korzystać z obsługiwanego w przeglądarce modelu rozszerzalności tylko do instalacji, wykonywania, wyłączania lub usuwania. Przeglądarki, które nie zapewniają obsługiwanych modeli rozszerzalności, są traktowane jako nieu rozszerzalne i nie powinny być modyfikowane.

#### <a name="installation-and-removal"></a>Instalacja i usuwanie

Użytkownik musi mieć możliwość uruchomienia, zatrzymania lub cofnięcia w inny sposób autoryzacji udzielonej oprogramowaniu. Oprogramowanie powinno uzyskać Twoją zgodę przed rozpoczęciem instalacji, a musi zapewnić przejrzyste i bezpośrednie rozwiązanie do instalacji, odinstalowywania i wyłączania oprogramowania.

Oprogramowanie o złej *jakości instalacji może* zawierać lub pobierać inne "niechciane oprogramowanie" sklasyfikowane przez firmę Microsoft.

Oprogramowanie, które zapewnia *słabe usuwanie może* :

* Podczas próby odinstalowania tej aplikacji mogą pojawiać się mylące lub mylące monity lub wyskakujące okienka.

* Nie korzystaj ze standardowych funkcji instalacji/odinstalowywania, takich jak Dodawanie/usuwanie programów.

#### <a name="advertising-and-advertisements"></a>Reklamy i reklamy

Oprogramowanie promujące produkt lub usługę poza oprogramowaniem może zakłócać działanie oprogramowania. Podczas instalowania oprogramowania, które prezentuje reklamy, musisz mieć jasny wybór i kontrolę.

Anonsy prezentowane przez oprogramowanie muszą:

* Uwzględnij oczywiste sposób zamykania ogłoszenia przez użytkowników. Czynności zamykania ogłoszenia nie mogą otwierać kolejnych reklam.

* Dołącz nazwę oprogramowania, które zaprezentowało reklamę.

Oprogramowanie, które prezentuje te reklamy, musi:

* Podaj standardową metodę odinstalowywania oprogramowania pod taką samą nazwą, jak w anonsie, która się w nim przedstawia.

Wyświetlane ogłoszenia:

* Należy odróżnić ją od zawartości witryny internetowej.

* Nie wolno wprowadzać w błąd, wprowadzać w błąd ani mylić.

* Nie zawiera złośliwego kodu.

* Nie wywołaj pobierania pliku.

#### <a name="consumer-opinion"></a>Opinie konsumentów

Firma Microsoft utrzymuje globalną sieć analityków i systemów analizy, w której [można przesyłać oprogramowanie do analizy](https://www.microsoft.com/wdsi/filesubmission). Uczestnictwo w programie pomaga firmie Microsoft szybko zidentyfikować nowe złośliwe oprogramowanie. Po zakończeniu analizy firma Microsoft tworzy analizę zabezpieczeń dla oprogramowania spełniającego opisane kryteria. Ta inteligencja zabezpieczeń identyfikuje oprogramowanie jako złośliwe oprogramowanie i jest dostępne dla wszystkich użytkowników za pośrednictwem programu Program antywirusowy Microsoft Defender i innych rozwiązań firmy Microsoft chroniących przed złośliwym kodem.

## <a name="potentially-unwanted-application-pua"></a>Potencjalnie niechciana aplikacja (PUA)

Ochrona klienta klienta w celu zabezpieczenia wydajności użytkowników i zapewnienia odpowiedniego Windows użytkowania. Ta ochrona zapewnia większą produktywność, wydajność i zadowolenie Windows środowiska. Aby uzyskać instrukcje dotyczące włączania ochrony za Chromium PUA w aplikacjach opartych na Microsoft Edge i Program antywirusowy Microsoft Defender, zobacz Wykrywanie i blokowanie potencjalnie niechcianych [aplikacji](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*Programy pua nie są uznawane za złośliwe oprogramowanie.*

Firma Microsoft używa określonych kategorii i definicji kategorii w celu klasyfikowania oprogramowania jako oprogramowania pua.

* **Oprogramowanie do reklam:** Oprogramowanie wyświetlace reklamy lub promocje albo monity o wypełnij ankiety dotyczące innych produktów lub usług w oprogramowaniu innym niż jego oprogramowanie. Dotyczy to oprogramowania służącego do wstawiania reklam do stron internetowych.

* **Oprogramowanie Firmy Enterprise):** oprogramowanie służące do tworzenia lub pobierania potoków bądź innych plików używanych specjalnie z technologiami udostępniania plików w p2p.

* **Cryptomining software (Enterprise):** Oprogramowanie, które korzysta z zasobów urządzenia w celu minowania zasobów.

* **Oprogramowanie do tworzenie pakietów:** Oprogramowanie udostępniace do zainstalowania innego oprogramowania, które nie jest opracowywane przez tę samą jednostkę lub które nie jest wymagane do jego uruchamiania. Ponadto oprogramowanie udostępniające możliwość zainstalowania innego oprogramowania, które kwalifikuje się jako pakiet PUA na podstawie kryteriów przedstawionych w tym dokumencie.

* **Oprogramowanie marketingowe:** Oprogramowanie, które monitoruje i przesyła działania użytkowników do aplikacji lub usług innych niż własne w celu badań marketingowych.

* **Oprogramowania, które jest wyeksłowyw** Oprogramowanie, które aktywnie próbuje wykrywać wykrycie przez produkty zabezpieczające, w tym oprogramowanie, które działa inaczej w przypadku obecności produktów zabezpieczających.

* **Niska reputacja branży:** Oprogramowanie wykrywane przez zaufanych dostawców zabezpieczeń razem z produktami zabezpieczającymi. Branża zabezpieczeń jest przeznaczona do ochrony klientów i ulepszania ich środowiska. Firma Microsoft i inne organizacje w branży zabezpieczeń nieustannie wymieniają się wiedzą na temat analizowanych plików, aby zapewnić użytkownikom jak najlepszą ochronę.

