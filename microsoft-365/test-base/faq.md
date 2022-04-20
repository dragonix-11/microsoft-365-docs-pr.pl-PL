---
title: Baza testów — często zadawane pytania
description: Przeglądanie często zadawanych pytań
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
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
ms.openlocfilehash: c7fd01b95d461332baaf4eac90aee4715da3e55e
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953035"
---
# <a name="test-base-faq"></a>Baza testów — często zadawane pytania

**Pyt.: Jak przesłać nasze pakiety do zespołu bazy testowej?**

**A:** Prześlij pakiety bezpośrednio do środowiska Bazy testów przy użyciu naszego portalu samoobsługowego.

Aby przesłać pakiet aplikacji, przejdź do [witryny Azure Portal](https://www.aka.ms/testbaseportal "Strona główna bazy testów") i przekaż spakowany folder zawierający pliki binarne, zależności i skrypty testowe aplikacji za pośrednictwem samoobsługowego pulpitu nawigacyjnego portalu Bazy testów.

Aby uzyskać więcej informacji, zobacz podręcznik użytkownika dołączania lub skontaktuj się z naszym zespołem, <testbasepreview@microsoft.com> aby uzyskać pomoc i uzyskać więcej informacji.

**Pyt.: Co to są testy out-of-box (OOB)?**

**A:** Testy out-of-box (OOB) są standardowymi, domyślnymi przebiegami testów, w których pakiety aplikacji są instalowane, uruchamiane i zamykane trzydzieści (30) razy, a następnie odinstalowywanie.

Pakiety utworzone dla bazy testów będą miały następujące skrypty testowe: instalowanie, uruchamianie, zamykanie i opcjonalnie skrypt odinstalowywania.

Testy out-of-box (OOB) zapewniają ustandaryzowane dane telemetryczne w aplikacji do porównania między kompilacjami Windows.

**Pyt.: Czy można przesyłać testy poza testami out-of-box (instalowanie, uruchamianie, zamykanie, odinstalowywanie skryptów testowych)?**

**A:** Tak, klienci mogą również przekazywać pakiety aplikacji do **testów funkcjonalnych** za pośrednictwem samoobsługowego pulpitu nawigacyjnego portalu.
**Testy funkcjonalne** to testy, które umożliwiają klientom wykonywanie skryptów w celu uruchamiania niestandardowych funkcji w aplikacji.

## <a name="testing"></a>Testowania

**Pyt.: Czy obsługujesz testy funkcjonalne?**

**A:** Tak, baza testów obsługuje testy funkcjonalne. Testy funkcjonalne to testy, które umożliwiają naszym klientom wykonywanie skryptów w celu uruchamiania niestandardowych funkcji w aplikacji.

Aby przesłać pakiet aplikacji do testowania funkcjonalnego, przekaż spakowany folder zawierający pliki binarne, zależności i skrypty testowe aplikacji za pośrednictwem naszego samoobsługowego pulpitu nawigacyjnego portalu.

Aby uzyskać więcej informacji, zobacz podręcznik użytkownika dołączania lub skontaktuj się z naszym zespołem, <testbasepreview@microsoft.com> aby uzyskać pomoc i uzyskać więcej informacji.

**Pyt.: Jak baza testów obsługuje nasze dane testowe?**

**A:** Baza testowa bezpiecznie zbiera dane testowe w środowisku platformy Azure i zarządza nimi.

**Pyt.: Czy baza testów może obsługiwać nasze testy automatyczne?**

**A:** Tak, baza testów obsługuje testy automatyczne, jednak obecnie nie obsługujemy testów ręcznych ze względu na możliwości usługi.

**Pyt.: Jakie języki i struktury testów automatycznych są obsługiwane?**

**A:** Obsługujemy wszystkie języki i struktury. Wywołujemy wszystkie skrypty za pośrednictwem programu PowerShell.

Należy również podać (przekazać) zależne pliki binarne wymaganej struktury.

**Pyt.: Jak szybko baza testów dostarcza wyniki testów?**

**A:** Dla każdego testu uruchamianego względem kompilacji wersji wstępnej w ciągu 48 godzin udostępnimy wyniki na pulpicie nawigacyjnym [witryny Azure Portal](https://www.aka.ms/testbaseportal "Strona główna bazy testów") .

**Pyt.: Czy można ponownie uruchomić po instalacji?**

**A:** Tak, nasz proces obsługuje ponowne uruchomienie po instalacji. Pamiętaj, aby wybrać tę opcję z listy rozwijanej "Ustawienia opcjonalne" podczas **ustawiania zadań** w portalu dołączania.

W przypadku testów out-of-box (OOB) można określić, czy dla _skryptu instalacji_ jest wymagany ponowny rozruch.

![Obraz ponownego rozruchu.](Media/reboot.png)

Podczas testów funkcjonalnych można określić, czy dla każdego dodanego skryptu jest wymagany ponowny rozruch.

![Jak wybrać testy funkcjonalne.](Media/functionalreboot.png)

**Pyt.: Jakie wersje Windows obsługujesz?**

**A:** Obecnie obsługujemy klientów Windows 10, Windows Server 2016, Windows Server 2016 Core, Windows Server 2019 i Windows Server 2019 Core.

**Pyt.: Jaka jest różnica między testami aktualizacji zabezpieczeń a testami aktualizacji funkcji?**

**A:** W przypadku testów aktualizacji zabezpieczeń testujemy **<ins>miesięczne aktualizacje zabezpieczeń w wersji wstępnej</ins>** na Windows, które koncentrują się na zapewnieniu naszym użytkownikom zawsze bezpieczeństwa i ochrony. W przypadku testów aktualizacji funkcji testujemy **<ins>aktualizacje funkcji przedpremierowych co dwa razy w roku</ins>**, które wprowadzają nowe funkcje i możliwości na Windows.

## <a name="debugging-options"></a>Opcje debugowania

**Pyt.: Czy uzyskujemy dostęp do Virtual Machines (maszyn wirtualnych) w przypadku awarii? Co współużytkuje baza testów?**

**A:** Aby usługa była zgodna, a aktualizacje wersji wstępnej były bezpieczne, tylko firma Microsoft ma dostęp do maszyn wirtualnych. Klienci mogą jednak wyświetlać wyniki testów i inne metryki testów na pulpicie nawigacyjnym portalu, w tym sygnały awarii i zawieszenia, metryki niezawodności, wykorzystanie pamięci i procesora CPU itp. Ponadto generujemy i udostępniamy dzienniki przebiegów testów na pulpicie nawigacyjnym do pobrania i dalszej analizy.

W razie potrzeby możemy również udostępnić zrzuty pamięci na potrzeby debugowania awaryjnego.

**Pyt.: Jeśli podczas testowania występują problemy, jakie są następne kroki rozwiązywania tych problemów?**

**A:** Zespół bazy testowej przeprowadzi początkowy proces klasyfikacji w celu określenia głównej przyczyny błędu, a następnie w zależności od naszych ustaleń przekierujemy do zespołów klienta lub wewnętrznych w firmie Microsoft w celu debugowania.

Zawsze ściśle współpracujemy z naszymi klientami we wspólnym korygowaniu, aby rozwiązać wszelkie problemy.

**Pyt.: Czy firma Microsoft przechowuje wydanie poprawki zabezpieczeń do czasu rozwiązania problemu? Jakie alternatywne rozwiązania są dostępne?**

**A:** Celem bazy testowej jest zapewnienie, że nasi wspólni klienci końcowi nie będą napotykać żadnych problemów. Będziemy ciężko współpracować z dostawcami oprogramowania, aby rozwiązać wszelkie problemy przed wydaniem, ale w przypadku, gdy poprawka nie jest możliwa, mamy inne rozwiązania, takie jak podkładki i bloki.

## <a name="miscellaneous"></a>Różne

**Pyt.: Jak usługa będzie działać z serwerem lokalnym?**

**A:** Obecnie nie zapewniamy obsługi serwerów lokalnych. Jeśli jednak serwer uwidacznia punkt końcowy HTTP, możemy nawiązać z nim połączenie przez Internet.

**Pyt.: KtoTo hostuje maszyny wirtualne?**

**A:** Firma Microsoft aprowizuje maszynę wirtualną dla tej usługi, pobierając obciążenie od klienta.

**Pyt.: Czy ta usługa obsługuje aplikacje internetowe, mobilne lub klasyczne?**

**A:** Obecnie koncentrujemy się na aplikacjach klasycznych, jednak planujemy dołączanie aplikacji internetowych w przyszłości, ale obecnie nie obsługujemy aplikacji mobilnych.

**Pyt.: Jaka jest różnica między bazą testową a SUVP?**

**A:** Największą różnicą między bazą testów a suvpem jest to, że nasi partnerzy dołączają swoje aplikacje do środowiska platformy Azure bazy testowej w celu weryfikacji, uruchamiając aktualizacje wersji wstępnej, zamiast przeprowadzać same testy.

Oprócz testowania aktualizacji zabezpieczeń w wersji wstępnej obsługujemy testowanie aktualizacji funkcji w wersji wstępnej na naszej platformie. Mamy wiele innych typów aktualizacji i testowania systemu operacyjnego w naszym planie działania.

**Pyt.: Czy istnieje koszt związany z usługą?**

**A:** Od 1 marca 2022 r. otrzymasz 100 bezpłatnych godzin (o wartości 800 USD) wygasających w ciągu 6 miesięcy w ramach subskrypcji na potrzeby weryfikacji. Po wykorzystaniu bezpłatnych godzin (lub wygaśnięciu przed użyciem) zostaniesz automatycznie taryfowany na 8 USD za godzinę w stosunku do użycia.

**Pyt.: Jak mogę przekazać opinię na temat bazy testowej?**

**A:** Aby udostępnić swoją opinię na temat bazy testowej, wybierz ikonę **Opinie** w lewym dolnym rogu portalu. Dołącz zrzut ekranu z przesłaniem, aby pomóc firmie Microsoft lepiej zrozumieć Twoją opinię.

Możesz również przesłać sugestie dotyczące produktów i wywołać inne pomysły pod adresem <testbasepreview@microsoft.com>.
