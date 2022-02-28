---
title: Baza testowa — często zadawane pytania
description: Przeglądanie często zadawanych pytań
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 668631563b35a848df5bfbdfd930be17efce8c04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988040"
---
# <a name="test-base-faq"></a>Baza testowa — często zadawane pytania

**P: Jak przesyłamy nasze pakiety do zespołu Test Base?**

**O.** Przesyłaj pakiety bezpośrednio do środowiska Test Base, korzystając z naszego portalu samoobsługowego.

Aby przesłać pakiet aplikacji, przejdź do portalu [Azure Portal](https://www.aka.ms/testbaseportal "Test Base Homepage") i przekaż spakowany folder zawierający binaries, zależności i skrypty testowe aplikacji za pośrednictwem samoobsługowego pulpitu nawigacyjnego portalu Test Base. 

Aby uzyskać więcej informacji, zobacz podręcznik użytkownika dołączania do programu lub <testbasepreview@microsoft.com> skontaktuj się z naszym zespołem, aby uzyskać pomoc i więcej informacji.

**P: Co to są testy typu "nieobce"?**

**O.** Testy typu "out-of-box" (OOB) są znormalizowane, test domyślny jest uruchamiany w miejscu, w którym są instalowane, uruchamiane i zamykane 30 razy, a następnie odinstalowywać. 

Pakiety utworzone dla bazy testowej będą zawierały następujące skrypty testowe: zainstaluj, uruchom, zamknij i opcjonalnie skrypt odinstalowywania. 

Testy typu "od urządzenia" (OOB) zapewniają usterektowany telemetrię aplikacji do porównywania w Windows kompilacjach.

**P. Czy można przesyłać testy poza testami odinstalowywania (instalowanie, uruchamianie, zamykanie i odinstalowywanie skryptów testowych)?**

**O.** Tak, klienci mogą również przekazywać pakiety aplikacji **do testów** funkcjonalności za pośrednictwem samoobsługowego pulpitu nawigacyjnego portalu.
**Testy funkcjonalności** to testy umożliwiające klientom uruchamianie niestandardowych funkcji w aplikacji.


## <a name="testing"></a>Testowanie

**P: Czy obsługujesz testy funkcjonalności?**

**O.** Tak, baza testowa obsługuje testy funkcjonalności. Testy funkcjonalności to testy umożliwiające naszym klientom uruchamianie skryptów niestandardowych w swoich aplikacjach. 

Aby przesłać pakiet aplikacji na testy funkcjonalności, po prostu przekaż spakowany folder zawierający binaries, zależności i skrypty testowe Twojej aplikacji za pośrednictwem naszego samoobsługowego pulpitu nawigacyjnego portalu. 

Aby uzyskać więcej informacji, zobacz podręcznik użytkownika dołączania do programu lub <testbasepreview@microsoft.com> skontaktuj się z naszym zespołem, aby uzyskać pomoc i więcej informacji.

**P: Jak baza testowa obsługuje dane testowe?**

**O.** Baza testowa bezpiecznie zbiera Twoje dane testowe i zarządza nimi w środowisku platformy Azure. 

**P: Czy baza testowa może obsługiwać nasze testy automatyczne?**

**O.** Tak, baza testowa obsługuje testy automatyczne, jednak obecnie nie obsługuje testów ręcznych ze względu na możliwości usługi.

**P: Jakie języki i struktury testów automatycznych obsługujesz?**

**O.** Obsługujemy wszystkie języki i struktury. Wszystkie skrypty są wywoływane za pośrednictwem programu PowerShell. 

Konieczne będzie także podanie (przekazanie) danych binralnych zależnych z wymaganej struktury.

**P: Jak szybko baza testowa dostarcza wyników testów?**

**O.** Dla każdego testu, który uruchamiamy dla kompilacji przedpremierowych, udostępnimy wyniki w ciągu 48 godzin na pulpicie nawigacyjnym [portalu Azure Portal](https://www.aka.ms/testbaseportal "Test Base Homepage") .

**P: Czy można ponownie uruchomić urządzenie po instalacji?**

**O.** Tak, nasz proces obsługuje ponowne uruchomienie po instalacji. Pamiętaj, aby wybrać tę opcję z listy rozwijanej "Ustawienia opcjonalne" podczas ustawiania **zadań** w portalu dołączania.

W przypadku testów typu "out-of-box" (OOB) możesz określić, czy w skrypcie instalacji jest wymagane ponowne _uruchomienie._

![Ponowne uruchamianie obrazu.](Media/reboot.png)

Podczas testów funkcjonalnych możesz określić, czy dla każdego dodanego skryptu jest wymagane ponowne uruchomienie.

![Jak wybrać testy funkcjonalności.](Media/functionalreboot.png)

**P. Jakie Windows wersje obsługujesz?**

**O.** Obecnie obsługujemy Windows 10, Windows Server 2016, Windows Server 2016 Core, Windows Server 2019 i Windows Server 2019 Core.

**P: Jaka jest różnica między testami aktualizacji zabezpieczeń a testami aktualizacji funkcji?**

**O.** W przypadku testów aktualizacji zabezpieczeń testujemy comiesięczne przedpremierowe aktualizacje zabezpieczeń na platformie Windows które koncentrują się na zapewnianiu naszym użytkownikom bezpieczeństwa i ochrony.**<ins></ins>** W przypadku testów aktualizacji funkcji testujemy na dwuroczne wersje wstępne aktualizacji funkcji, które wprowadzono nowe funkcje i możliwości w zakresie Windows.**<ins></ins>**

## <a name="debugging-options"></a>Opcje debugowania

**P. Czy uzyskujemy dostęp do maszyn wirtualnych w przypadku błędów? Co udostępnia baza testowa?**

**O.** Aby usługa była zgodna i aktualizacje w wersji wstępnej są bezpieczne, tylko firma Microsoft ma dostęp do maszyn wirtualnych. Jednak klienci mogą wyświetlać wyniki testów i inne metryki testów na swoich pulpitach nawigacyjnych portalu, takie jak sygnały awarii i zawieszania się, metryki niezawodności, użycia pamięci i procesora itp. Generujemy i dostarczamy dzienniki testów uruchamiane na pulpicie nawigacyjnym w celu pobrania i dalszej analizy. 

Możemy również udostępnić zrzuty pamięci do debugowania awarii zgodnie z potrzebami.

**P. Jeśli podczas testowania zostaną znalezione problemy, jakie są następne kroki rozwiązywania tych problemów?**

**O.** Zespół bazy testowej wykona początkowy proces sprawdzania, aby ustalić główną przyczynę błędu, a następnie, w zależności od naszych wyników, przekierujemy do klienta lub wewnętrznych zespołów w ramach firmy Microsoft w celu debugowania. 

Zawsze ściśle współpracujemy z naszymi klientami w ramach wspólnych działań naprawczych, aby rozwiązać wszelkie problemy. 

**P. Czy firma Microsoft wstrzyma wydanie poprawki zabezpieczeń do czasu rozwiązania problemu? Jakie alternatywne rozwiązania są dostępne?**

**O.** Celem bazy testowej jest zapewnienie, że nasi wspólną klienci końcowi nie będą mieć żadnych problemów. Na wypadek, gdy poprawka nie będzie możliwa, będziemy współpracować z dostawcami oprogramowania nad rozwiązywania problemów przed wydaniem, ale na wypadek, gdy rozwiązanie nie będzie możliwe, mamy inne rozwiązania, takie jak migowy i bloki.

## <a name="miscellaneous"></a>Postanowienia różne

**P. Jak usługa będzie działać z serwerem w konfiguracji wstępnej?**

**O.** Obecnie nie zapewniamy obsługi serwerów wydobytych przez serwer. Jeśli jednak serwer ujawnia punkt końcowy HTTP, możemy połączyć się z nim przez Internet.

**P. KtoTo hostuje maszyny wirtualne?**

**O.** Firma Microsoft iniekuje maszyny wirtualnej dla tej usługi, przejmąc to od klienta.

**P. Czy ta usługa obsługuje aplikacje internetowe, mobilne lub klasyczne?**

**O.** Obecnie fokus znajduje się na aplikacjach klasycznych, jednak w przyszłości planujemy wdowy aplikacji sieci Web, ale obecnie nie obsługujemy aplikacji mobilnych.

**P: Jaka jest różnica między bazą testową a PROGRAMEM TEST?**

**O.** Podstawowa różnica między bazą testową a programem CENA.POŚR polega na tym, że nasi partnerzy uruchamiają swoje aplikacje do środowiska Test Base Azure w celu sprawdzania poprawności na podstawie aktualizacji przed ich wydaniem, zamiast przeprowadzać same testy. 

Poza testami aktualizacji zabezpieczeń w wersji wstępnej, obsługujemy testowanie aktualizacji funkcji przed ich wydaniem na naszej platformie. W planach mamy wiele innych typów aktualizacji i testów systemu operacyjnego.

**P. Czy z usługą jest skojarzony koszt?**

**O.** Usługa Test Base będzie bezpłatna dla użytkowników do czasu jej ogólno dostępnej dostępności. Wtedy ogłosimy strukturę kosztów, która będzie obowiązywać dla wszystkich klientów. 

**P: Jak mogę przekazać opinię na temat bazy testowej?**

**O.** Aby podzielić się opinią na temat bazy testowej, wybierz ikonę **Opinia** w lewym dolnym rogu portalu. Dołącz zrzut ekranu do swojego zgłoszenia, aby pomóc firmie Microsoft w lepszym zrozumieniu Twojej opinii. 

Sugestie dotyczące produktu i inne pomysły można też przesłać na stronie <testbasepreview@microsoft.com>.
