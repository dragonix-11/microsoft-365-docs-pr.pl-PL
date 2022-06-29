---
title: Dowiedz się więcej o ochronie przed utratą danych punktu końcowego
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: 'Ochrona przed utratą danych punktu końcowego rozszerza monitorowanie działań plików i akcji ochronnych dla tych plików na punkty końcowe. Pliki są widoczne w rozwiązaniach zgodności '
ms.openlocfilehash: 015e219d1b3ed41605ae3b331488d8dec6e7751f
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530909"
---
# <a name="learn-about-endpoint-data-loss-prevention"></a>Dowiedz się więcej o ochronie przed utratą danych punktu końcowego

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Możesz użyć Ochrona przed utratą danych w Microsoft Purview (DLP) do monitorowania akcji wykonywanych na elementach, które zostały uznane za wrażliwe, i aby zapobiec niezamierzonemu udostępnianiu tych elementów. Aby uzyskać więcej informacji na temat ochrony przed [utratą danych, zobacz Dowiedz się więcej o zapobieganiu utracie danych](dlp-learn-about-dlp.md).

**Ochrona przed utratą danych punktu końcowego** (Endpoint DLP) rozszerza możliwości monitorowania aktywności i ochrony DLP na poufne elementy, które są fizycznie przechowywane na urządzeniach Windows 10, Windows 11 i macOS (Catalina 10.15 lub nowszych). Po dołączeniu urządzeń do rozwiązań Usługi Microsoft Purview informacje o tym, co użytkownicy robią z poufnymi elementami, są widoczne w [Eksploratorze aktywności](data-classification-activity-explorer.md) i można wymuszać akcje ochronne na tych elementach za pośrednictwem [zasad DLP](create-test-tune-dlp-policy.md).

> [!TIP]
> Jeśli szukasz kontroli urządzenia dla magazynu wymiennego, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender Device Control Removable Storage Access Control](../security/defender-endpoint/device-control-removable-storage-access-control.md#microsoft-defender-for-endpoint-device-control-removable-storage-access-control).

> [!NOTE]
> W usłudze Microsoft Purview ocena zasad DLP elementów poufnych odbywa się centralnie, więc nie ma opóźnienia czasowego dystrybucji zasad i aktualizacji zasad do poszczególnych urządzeń. Aktualizacja zasad w Centrum zgodności zwykle trwa około godziny, zanim te aktualizacje zostaną zsynchronizowane w całej usłudze. Po zsynchronizowania aktualizacji zasad elementy na urządzeniach docelowych są automatycznie ponownie oceniane przy następnym uzyskaniu dostępu lub modyfikacji.

## <a name="endpoint-activities-you-can-monitor-and-take-action-on"></a>Działania punktu końcowego, które można monitorować i podejmować

Protokół DLP punktu końcowego umożliwia przeprowadzanie inspekcji następujących typów działań, które użytkownicy przyjmują na poufnych elementach, które są fizycznie przechowywane Windows 10, Windows 11 lub urządzeniach z systemem macOS.

|Działanie |Opis  |Windows 10 1809 i nowsze/Windows 11| macOS Catalina 10.15| Możliwość inspekcji/ograniczenia|
|---------|---------|---------|---------|---------|
|przekazywanie do usługi w chmurze lub dostęp przez niedozwolone przeglądarki    | Wykrywa, kiedy użytkownik próbuje przekazać element do domeny usługi z ograniczeniami lub uzyskać dostęp do elementu za pośrednictwem przeglądarki.  Jeśli korzystają z przeglądarki, która jest wyświetlana w programie DLP jako niezauzwalana przeglądarka, działanie przekazywania zostanie zablokowane, a użytkownik zostanie przekierowany do korzystania z przeglądarki Microsoft Edge. Przeglądarka Microsoft Edge zezwoli lub zablokuje przekazywanie lub dostęp na podstawie konfiguracji zasad DLP         |Obsługiwane | Obsługiwane|możliwość przeprowadzania inspekcji i ograniczania|
|kopiowanie do innej aplikacji    |Wykrywa, kiedy użytkownik próbuje skopiować informacje z chronionego elementu, a następnie wkleić je do innej aplikacji, procesu lub elementu. To działanie nie wykrywa kopiowania i wklejania informacji w tej samej aplikacji, procesie lub elemencie.|Obsługiwane|Obsługiwane         | możliwość przeprowadzania inspekcji i ograniczania|
|kopiowanie na nośnik wymienny USB |Wykrywa, kiedy użytkownik próbuje skopiować element lub informacje na nośnik wymienny lub urządzenie USB.|Obsługiwane|Obsługiwane         | możliwość przeprowadzania inspekcji i ograniczania|
|kopiowanie do udziału sieciowego    |Wykrywa, kiedy użytkownik próbuje skopiować element do udziału sieciowego lub zamapowanego dysku sieciowego |Obsługiwane|Obsługiwane         |możliwość przeprowadzania inspekcji i ograniczania|
|drukowanie dokumentu    |Wykrywa, kiedy użytkownik próbuje wydrukować chroniony element na drukarce lokalnej lub sieciowej.|Obsługiwane|Obsługiwane|możliwość przeprowadzania inspekcji i ograniczania         |
|kopiowanie do sesji zdalnej|Wykrywa, kiedy użytkownik próbuje skopiować element do sesji pulpitu zdalnego |Obsługiwane|nieobsługiwane|  możliwość przeprowadzania inspekcji i ograniczania|
|kopiowanie na urządzenie Bluetooth|Wykrywa, kiedy użytkownik próbuje skopiować element do niedozwolonej aplikacji Bluetooth (zgodnie z definicją na liście niedozwolonych interfejsów API Bluetooth w ustawieniach DLP punktu końcowego).|Obsługiwane|nieobsługiwane| możliwość przeprowadzania inspekcji i ograniczania|
|tworzenie elementu|Wykrywa, kiedy użytkownik tworzy element|Obsługiwane |Obsługiwane |z możliwością inspekcji|
|zmienianie nazwy elementu|Wykrywa, kiedy użytkownik zmienia nazwę elementu|Obsługiwane |Obsługiwane |z możliwością inspekcji|

## <a name="best-practice-for-endpoint-dlp-policies"></a>Najlepsze rozwiązanie dotyczące zasad DLP punktu końcowego

Załóżmy, że chcesz zablokować wszystkim elementom, które zawierają numery kart kredytowych, pozostawienie punktów końcowych użytkowników działu finansów. Zalecamy:

- Tworzenie zasad i określanie zakresu do punktów końcowych i do tej grupy użytkowników.
- Utwórz regułę w zasadach, która wykrywa typ informacji, które chcesz chronić. W takim przypadku **zawartość zawiera** wartość *Typ informacji poufnych**, a następnie wybierz pozycję **Karta kredytowa**.
- Ustaw akcje dla każdego działania na **Wartość Blokuj**.

Aby uzyskać więcej wskazówek dotyczących projektowania zasad DLP, zobacz [Projektowanie zasad ochrony przed utratą danych](dlp-policy-design.md) .

## <a name="monitored-files"></a>Monitorowane pliki

Program Endpoint DLP obsługuje monitorowanie tych typów plików. DLP przeprowadza inspekcję działań dla tych typów plików, nawet jeśli nie ma dopasowania zasad. 

- Pliki programu Word
- Pliki programu PowerPoint
- Pliki programu Excel
- Pliki PDF
- pliki .csv
- Pliki tsv
- pliki .txt
- Pliki rtf
- Pliki .c
- Pliki klasy
- Pliki cpp
- Pliki cs
- Pliki .h
- Pliki java
 
Jeśli chcesz tylko monitorować dane z dopasowań zasad, możesz wyłączyć **działanie Zawsze przeprowadzaj inspekcję plików dla urządzeń w ustawieniach** globalnych DLP punktu końcowego.

> [!NOTE]
> Jeśli **ustawienie Zawsze sprawdzaj działanie pliku dla urządzeń** jest włączone, działania dotyczące dowolnego pliku programu Word, PowerPoint, Excel, PDF i .csv są zawsze poddawane inspekcji, nawet jeśli urządzenie nie jest objęte żadnymi zasadami.

> [!TIP]
> Aby upewnić się, że działania są poddawane inspekcji dla wszystkich obsługiwanych typów plików, utwórz [niestandardowe zasady DLP](create-test-tune-dlp-policy.md).

Program DLP punktu końcowego monitoruje działanie oparte na typie MIME, więc działania zostaną przechwycone, nawet jeśli rozszerzenie pliku zostanie zmienione.

### <a name="file-types"></a>Typy plików

Typy plików to grupa formatów plików, które są używane do ochrony określonych przepływów pracy lub obszarów działalności. W zasadach DLP można użyć co najmniej jednego typu plików.

|Typ pliku |Aplikacja  |monitorowane rozszerzenia plików  |
|---------|---------|---------|
|przetwarzanie tekstu |Word, PDF | .doc, .docx, .docm, .dot, .dotx, .dotm, .docb, .pdf |
|Arkusza kalkulacyjnego    |Excel, CSV, TSV |.xls, .xlsx, .xlt, .xlm, .xlsm, .xltx, .xltm, .xlsb, .xlw, .csv, .tsv         |
|Prezentacji |PowerPoint|.ppt, .pptx, .pos, .pps, .pptm, .potx, .potm, .ppam, .ppsx|
|Archiwum  |narzędzia archiwum plików i kompresji | .zip, .zipx, .rar, .7z, .tar, .gz        |
|Adres e-mail    |Outlook |.pst, .ost, .msg         |

### <a name="file-extensions"></a>Rozszerzenia plików

Jeśli typy plików nie obejmują rozszerzeń plików, które należy wyświetlić jako warunek w zasadach, możesz użyć rozszerzeń plików rozdzielonych przecinkami.

> [!IMPORTANT]
> Opcji rozszerzeń plików i typów plików nie można używać jako warunków w tej samej regule. Jeśli chcesz używać ich jako warunków w tych samych zasadach, muszą one być w oddzielnych regułach. 

> [!IMPORTANT]
> Te wersje systemu Windows obsługują typy plików i funkcje rozszerzenia plików:
>- Windows 10 wersje 20H1/20H2/21H1 (KB 5006738)
>- Windows 10 wersje 19H1/19H2 (KB 5007189)
>- Windows 10 RS5 (KB 5006744)


## <a name="whats-different-in-endpoint-dlp"></a>Co się różni w programie Endpoint DLP

Istnieje kilka dodatkowych pojęć, o których należy pamiętać przed rozpoczęciem analizy DLP punktu końcowego.

### <a name="enabling-device-management"></a>Włączanie zarządzania urządzeniami

Zarządzanie urządzeniami to funkcja, która umożliwia zbieranie danych telemetrycznych z urządzeń i wprowadza ją do rozwiązań usługi Microsoft Purview, takich jak endpoint DLP i [zarządzanie ryzykiem wewnętrznym](insider-risk-management.md). Musisz dołączyć wszystkie urządzenia, których chcesz użyć jako lokalizacji w zasadach DLP.

> [!div class="mx-imgBorder"]
> ![włączanie zarządzania urządzeniami.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

Dołączanie i odłączanie są obsługiwane za pośrednictwem skryptów pobranych z centrum zarządzania urządzeniami. Centrum ma niestandardowe skrypty dla każdej z tych metod wdrażania:

- skrypt lokalny (maksymalnie 10 maszyn)
- Zasady grupy
- System Center Configuration Manager (wersja 1610 lub nowsza)
- Zarządzanie urządzeniami/Microsoft Intune mobilne
- Skrypty dołączania interfejsu VDI dla maszyn nietrwałych

> [!div class="mx-imgBorder"]
> ![strony dołączania urządzenia.](../media/endpoint-dlp-learn-about-3-device-onboarding-page.png)

 Procedury opisane w temacie [Wprowadzenie do usługi DLP punktu końcowego platformy Microsoft 365](endpoint-dlp-getting-started.md) umożliwiają dołączanie urządzeń.

Jeśli urządzenia zostały dołączone za pośrednictwem [Ochrona punktu końcowego w usłudze Microsoft Defender](../security/defender-endpoint/configure-machines-onboarding.md), te urządzenia zostaną automatycznie wyświetlone na liście urządzeń. Dzieje się tak, ponieważ dołączanie do usługi Defender również dołącza urządzenia do usługi DLP. Aby używać protokołu DLP punktu końcowego, wystarczy **włączyć monitorowanie** urządzenia. .

> [!div class="mx-imgBorder"]
> ![listy urządzeń zarządzanych.](../media/endpoint-dlp-learn-about-2-device-list.png)

### <a name="viewing-endpoint-dlp-data"></a>Wyświetlanie danych DLP punktu końcowego

Alerty związane z zasadami DLP wymuszanymi na urządzeniach punktu końcowego można wyświetlić, przechodząc do [pulpitu nawigacyjnego zarządzania alertami DLP](dlp-configure-view-alerts-policies.md).

> [!div class="mx-imgBorder"]
> ![Informacje o alertach.](../media/Alert-info-1.png)

Możesz również wyświetlić szczegóły skojarzonego zdarzenia z bogatymi metadanymi na tym samym pulpicie nawigacyjnym

> [!div class="mx-imgBorder"]
> ![informacje o zdarzeniu.](../media/Event-info-1.png)

Po dołączeniu urządzenia informacje o inspekcji działań są przepływane do Eksploratora działań jeszcze przed skonfigurowaniem i wdrożeniem wszystkich zasad DLP, które mają urządzenia jako lokalizację.

> [!div class="mx-imgBorder"]
> ![zdarzenia dlp punktu końcowego w Eksploratorze działań.](../media/endpoint-dlp-learn-about-4-activity-explorer.png)

Punkt końcowy DLP zbiera obszerne informacje na temat inspekcji działania.

Jeśli na przykład plik zostanie skopiowany na wymienny nośnik USB, te atrybuty zostaną wyświetlone w szczegółach działania:

- typ działania
- adres IP klienta
- docelowa ścieżka pliku
- wystąpił sygnatura czasowa
- nazwa pliku
- Użytkownika
- Formatem
- rozmiar pliku
- typ informacji poufnych (jeśli dotyczy)
- wartość sha1
- wartość sha256
- poprzednia nazwa pliku
- Lokalizacji
- Nadrzędny
- Filepath
- typ lokalizacji źródłowej
- Platformy
- nazwa urządzenia
- typ lokalizacji docelowej
- aplikacja, która wykonała kopię
- Ochrona punktu końcowego w usłudze Microsoft Defender identyfikator urządzenia (jeśli dotyczy)
- producent wymiennych urządzeń multimedialnych
- model urządzenia nośnika wymiennego
- numer seryjny urządzenia nośnika wymiennego

> [!div class="mx-imgBorder"]
> ![kopiuj do atrybutów działania usb.](../media/endpoint-dlp-learn-about-5-activity-attributes.png)

## <a name="next-steps"></a>Następne kroki

Po zapoznaniu się z punktem końcowym DLP wykonaj następujące czynności:

1. [Dołączanie urządzeń Windows 10 lub Windows 11 do usługi Microsoft Purview — omówienie](device-onboarding-overview.md)
1. [Dołączanie urządzeń z systemem macOS do usługi Microsoft Purview — omówienie](device-onboarding-macos-overview.md)
1. [Konfigurowanie ustawień ochrony przed utratą danych punktu końcowego](dlp-configure-endpoint-settings.md)
1. [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do ochrony przed utratą danych w punkcie końcowym firmy Microsoft](endpoint-dlp-getting-started.md)
- [Używanie ochrony przed utratą danych w punkcie końcowym firmy Microsoft](endpoint-dlp-using.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)
