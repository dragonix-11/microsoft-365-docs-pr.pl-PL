---
title: Microsoft 365 oceny sieci
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 oceny sieci
ms.openlocfilehash: d7fea3d4f2dfbe846a873b6ce0ea34d8373bcc12
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996407"
---
# <a name="microsoft-365-network-assessment"></a>Microsoft 365 oceny sieci

W centrum Administracja Microsoft 365 sieciowego oceniane są wartości zagregowane z  wielu metryk wydajności sieci, które są migawką kondycji obwodowej sieci przedsiębiorstwa. Ocena sieci informuje o tym, jaki wpływ na środowisko użytkownika ma Office 365 projektu sieci Office 365 klienta. Oceny sieci są dostępne zarówno dla całej dzierżawy, jak i do każdej lokalizacji geograficznej, z której użytkownicy łączą się z dzierżawą. Testy zapewniają Microsoft 365 administratorom łatwy sposób na natychmiastowe potwierdzenie kondycji sieci przedsiębiorstwa i szybkie przechodzenie do szczegółów szczegółowego raportu dla każdej globalnej lokalizacji biura.

Wartość punktów oceny sieci wynosi od 0 do 100 i jest średnim opóźnieniem TCP, szybkością pobierania i metrykami jakości połączenia UDP. Te metryki są skompilowane raz dziennie. Metryki wydajności dla sieci należących do firmy Microsoft są wykluczane z tych miar, aby mieć pewność, że wyniki testów są niejednoznaczne i specyficzne dla sieci firmowej.

> [!div class="mx-imgBorder"]
> ![Wartość oceny sieci.](../media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Bardzo niska wartość oceny sieci sugeruje, że klienci Microsoft 365 będą mieć istotne problemy podczas nawiązywania połączenia z dzierżawą lub utrzymywania szybkości interfejsu użytkownika. Wysoka wartość oznacza prawidłowo skonfigurowaną sieć z kilkoma trwającymi problemami z wydajnością. Wartość 80% oznacza ważny plan bazowy, powyżej którego nie należy oczekiwać regularnych skarg użytkowników dotyczących łączności Microsoft 365 czasu reakcji ze względu na wydajność sieci. W związku z tym wprowadzono iteracyjne ulepszenia łączności sieciowej, wraz z użytkownikami zwiększana jest ta wartość.

| Ocena sieci | Oczekiwane środowisko użytkownika |
| :----------------- | :----------------------- |
| 100                | Najlepsza                     |
| 80                 | Spełnia zalecenia    |
| 60                 | Zadowalające               |
| 40                 | Użytkownicy mogą mieć problemy |
| 20                 | Użytkownicy mogą narzekać       |
| 0                  | Problemy z siecią to częsty temat dyskusji |

>[!IMPORTANT]
>Szczegółowe informacje o sieci, zalecenia dotyczące wydajności i oceny w centrum Administracja Microsoft 365 są obecnie w stanie podglądu i są dostępne tylko dla dzierżaw usługi Microsoft 365, które zostały zarejestrowane w programie podglądu funkcji.

## <a name="network-assessment-panel"></a>Panel oceny sieci

W przypadku każdej oceny sieci, zarówno w zakresie dzierżawy, jak i konkretnej lokalizacji biura, jest przedstawiany panel ze szczegółami na temat tej oceny. Ten panel przedstawia wykres słupkowy oceny zarówno jako wartość procentową, jak i łączną liczbę punktów dla każdego obciążenia składników, łącznie tylko z obciążeniami pracą, w przypadku których otrzymano dane pomiarów. Na potrzeby oceny sieci lokalizacji biura pokazywane jest również porównanie procentowej klientów usługi Microsoft 365 z każdego z pięciu lotów, które zgłosiły dane w tym samym mieście, co lokalizacja biura.

> [!div class="mx-imgBorder"]
> ![Przykładowa wartość oceny sieci.](../media/m365-mac-perf/m365-mac-perf-overview-score.png)

Podział **oceny w** panelu przedstawia ocenę dla każdego obciążenia składników.

Historia **testów** zawiera dane z ostatnich 30 dni testów i analizy porównawczej. Możesz również raportować na temat historii metryk dla dowolnej lokalizacji biura przez maksymalnie dwa lata, korzystając z karty Historia. Karta historia umożliwia wybranie atrybutów do raportu. Wybierając ramy czasowe raportu, możesz wyróżnić wpływ projektu aktualizacji sieci i zobaczyć ulepszenie oceny sieci.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Oceny sieci dzierżawy i oceny sieci lokalizacji biura

Ocena sieci mierzy projekt obwodu sieci lokalizacji biura w sieci firmy Microsoft. Ulepszenia obwodu sieci najlepiej wykonać w każdej lokalizacji biura.

Na stronie przeglądu wydajności sieci pokazujemy wartość oceny sieci Microsoft 365 dzierżawy sieci. Jest to średnia ważona oceny sieci dla wszystkich lokalizacji biurowych. Na stronie podsumowania tej lokalizacji jest również konkretną wartość oceny sieci dla każdej wykrytej lokalizacji biura.

## <a name="exchange-online"></a>Exchange Online

Na Exchange Online jest mierzone opóźnienie protokołu TCP z komputera klienckiego Exchange frontem usługi. Na to opóźnienie może mieć wpływ odległość między siecią a siecią WAN i siecią LAN u klientów. Może to mieć również wpływ na urządzenia lub usługi pośredniej sieci, co opóźnia łączność lub powoduje ponowne wysłany pakiet. A to wpływa na to, jak daleko od najbliższej Exchange front front door jest. Mediana (znana również jako 50-ty percentyl lub miara P50) jest przyjmowana dla wszystkich miar z poprzednich trzech dni.

Ocena Exchange Online jest wykonana przy użyciu poniższej tabeli. Każdy numer opóźnienia TCP między progami jest przypisywany liniowo w obrębie bandyty.

| Opóźnienie TCP   | Punkty |
| :------------ | :----- |
| 10 ms lub mniej  | 100    |
| 25 ms          | 80     |
| 100 ms         | 60     |
| 200 ms         | 40     |
| 300 ms         | 20     |
| 350 ms lub więcej | 0      |

## <a name="sharepoint-online"></a>SharePoint Online

W SharePoint online mierzona jest szybkość pobierania dostępna dla użytkownika w celu uzyskania dostępu do dokumentu SharePoint lub OneDrive dokumencie. Może to mieć wpływ na przepustowość dostępną w obwodach sieciowych między maszyną klienckią a siecią firmy Microsoft. Jest to często wpływane na przeciążenie sieci, które występuje w wąskich gardełach w złożonych urządzeniach sieciowych lub o słabym zasięgu Wi-Fi obszarach. Szybkość pobierania jest mierzona w megabajtach na sekundę, co oznacza około jedną dziesiątą obwodów ocenionych jako megabity na sekundę. Megabajt na sekundę jest przydatny, ponieważ pozwala bezpośrednio sprawdzić, jaki plik rozmiaru można pobrać w ciągu 1 sekundy. 25. percentyl (nazywany również miarą P25) jest przyjmowany dla wszystkich pomiarów z poprzednich trzech dni. Ten 25-ty percentyl pomaga zmniejszyć wpływ różnych przeciążeń w czasie.

Ocena SharePoint online jest wykonana przy użyciu poniższej tabeli. Każdy numer szybkości pobierania między progami jest przypisywany (w sposób liniowy) w obrębie zespołu.

| Szybkość pobierania | Punkty |
| :------------- | :----- |
| Co najmniej 20 MB/s | 100    |
| 14 MB/s         | 80     |
| 8 MB/s          | 60     |
| 4 MB/s          | 40     |
| 2 MB/s          | 20     |
| 0 MB/s          | 0      |

## <a name="microsoft-teams"></a>Microsoft Teams

Na Microsoft Teams jakość sieci jest mierzona jako opóźnienie UDP, zakłóceń UDP i utraty pakietów UDP. Protokołu UDP używa się do obsługi połączeń i konferencji audio i wideo z multimediami na Microsoft Teams. Mogą na to mieć wpływ te same czynniki, co opóźnienia i szybkość pobierania, a nie tylko przerwy w łączności w obsługie protokołu UDP sieci, ponieważ protokół UDP jest konfigurowany oddzielnie do bardziej typowego protokołu TCP. Mediana (znana również jako 50-ty percentyl lub miara P50) jest przyjmowana dla wszystkich miar z poprzednich trzech dni. 

Obliczamy średni wynik oceny na podstawie tych pomiarów UDP dla skali od jednej do pięciu. Następnie mapuje to na skalę 0–100 punktów na Microsoft Teams sieci.  Ogólne dobre jest powyżej 87,5 punktu, a ogólne złe wynosi poniżej 50 punktów.

## <a name="related-topics"></a>Tematy pokrewne

[Łączność sieciowa w Administracja Microsoft 365 center](office-365-network-mac-perf-overview.md)

[Microsoft 365 informacji o wydajności sieci](office-365-network-mac-perf-insights.md)

[Microsoft 365 testu łączności sieciowej](office-365-network-mac-perf-onboarding-tool.md)

[Microsoft 365 lokalizacji łączności sieciowej](office-365-network-mac-location-services.md)
