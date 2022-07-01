---
title: Badanie zdarzeń utraty danych za pomocą Microsoft 365 Defender
description: Badanie utraty danych w Microsoft 365 Defender.
keywords: Zapobieganie utracie danych, zdarzenia, alerty, badanie, analizowanie, reagowanie, korelacja, atak, maszyny, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
f1.keywords:
- NOCSH
ms.prod: m365-security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: a92e3b206b10b68ecc3ff2f94870a9174185b63b
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66574308"
---
# <a name="investigate-data-loss-incidents-with-microsoft-365-defender"></a>Badanie zdarzeń utraty danych za pomocą Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender

Zdarzenia dotyczące Ochrona przed utratą danych w Microsoft Purview (DLP) można teraz zarządzać w portalu Microsoft 365 Defender. Zdarzeniami DLP można zarządzać wraz z zdarzeniami zabezpieczeń z obszaru **Zdarzenia & alerty** \> **Zdarzenia** na szybkim uruchomieniu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>. Na tej stronie możesz:

- Wyświetl wszystkie alerty DLP pogrupowane w ramach zdarzeń w kolejce zdarzeń Microsoft 365 Defender.
- Wyświetl alerty inteligentne między rozwiązaniami (DLP-MDE, DLP-MDO) i intra-solution (DLP-DLP) skorelowane w ramach pojedynczego zdarzenia.
- Wyszukiwanie dzienników zgodności wraz z zabezpieczeniami w obszarze Zaawansowane wyszukiwanie zagrożeń.
- Akcje korygowania administratora w miejscu dotyczące użytkownika, pliku i urządzenia. 
- Skojarz tagi niestandardowe ze zdarzeniami DLP i filtruj według nich.
- Filtruj według nazwy zasad DLP, tagu, daty, źródła usługi, stanu zdarzenia i użytkownika w ujednoliconej kolejce zdarzeń. 

Łącznik Microsoft 365 Defender w usłudze Microsoft Sentinel umożliwia również ściąganie zdarzeń DLP wraz ze zdarzeniami i dowodami w usłudze Microsoft Sentinel w celu zbadania i skorygowania.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Aby zbadać Ochrona przed utratą danych w Microsoft Purview zdarzeń w portalu Microsoft 365 Defender, potrzebujesz licencji z jednej z następujących subskrypcji: 

- Microsoft Office 365 E5/A5
- Microsoft 365 E5/A5
- Zgodność Microsoft 365 E5/A5
- zabezpieczenia Microsoft 365 E5/A5
- Microsoft 365 E5/A5 Information Protection i ład

> [!NOTE] 
> Jeśli masz licencję i kwalifikujesz się do tej funkcji, alerty DLP będą automatycznie przepływać do Microsoft 365 Defender. Otwórz przypadek pomocy technicznej, jeśli chcesz wyłączyć tę funkcję. 

## <a name="dlp-investigation-experience-in-the-microsoft-365-defender-portal"></a>Środowisko badania DLP w portalu Microsoft 365 Defender

Przed rozpoczęciem [włącz alerty dla wszystkich zasad DLP](/microsoft-365/compliance/dlp-configure-view-alerts-policies#alert-configuration-experience) w <a href="https://purview.microsoft.com" target="_blank">portal zgodności Microsoft Purview</a>.

1. Przejdź do portalu Microsoft 365 Defender i wybierz pozycję **Incydenty** w menu nawigacji po lewej stronie, aby otworzyć stronę zdarzeń.

2. Wybierz pozycję **Filtry** w prawym górnym rogu, a następnie wybierz pozycję **Źródło usługi: Zapobieganie utracie danych** , aby wyświetlić wszystkie zdarzenia z alertami DLP.

3. Wyszukaj nazwę zasad DLP alertów i zdarzeń, które Cię interesują.

4. Aby wyświetlić stronę podsumowania zdarzenia, wybierz zdarzenie z kolejki. Podobnie wybierz alert, aby wyświetlić stronę alertu DLP.

5. Wyświetl **historię alertu** , aby uzyskać szczegółowe informacje o zasadach i typach informacji poufnych wykrytych w alercie. Wybierz zdarzenie w sekcji **Zdarzenia pokrewne** , aby wyświetlić szczegóły działania użytkownika.

6. Wyświetl dopasowaną zawartość poufną na karcie **Typy informacji poufnych** i zawartość pliku na karcie **Źródło** , jeśli masz wymagane uprawnienie (zobacz szczegóły <a href="/microsoft-365/compliance/dlp-alerts-dashboard-get-started#roles" target="_blank">tutaj</a>).

7. Zaawansowane wyszukiwanie zagrożeń umożliwia również przeszukiwanie dzienników inspekcji użytkowników, plików i lokalizacji lokacji na potrzeby badania. Tabela **CloudAppEvents** zawiera wszystkie dzienniki inspekcji we wszystkich lokalizacjach, takich jak Sharepoint, OneDrive, Exchange i Urządzenia.

8. Możesz również pobrać wiadomość e-mail, wybierając pozycję **Akcje** \> **Pobierz wiadomość e-mail**. 

9. W przypadku akcji korygowania plików w witrynach SPO lub ODB można zobaczyć akcje, takie jak:

    - Stosowanie etykiety przechowywania
    - Stosowanie etykiety poufności
    - Usuń udostępnianie pliku
    - Usuń

   W przypadku akcji korygowania wybierz **kartę Użytkownik** w górnej części strony alertu, aby otworzyć szczegóły użytkownika.

   W obszarze Alerty DLP urządzeń wybierz kartę urządzenia w górnej części strony alertu, aby wyświetlić szczegóły urządzenia i podjąć akcje korygowania na urządzeniu.

10. Przejdź do strony podsumowania zdarzenia i wybierz pozycję **Zarządzaj incydentem** , aby dodać tagi zdarzeń, przypisać lub rozwiązać zdarzenie.

## <a name="dlp-investigation-experience-in-microsoft-sentinel"></a>Środowisko badania DLP w usłudze Microsoft Sentinel

Łącznik Microsoft 365 Defender w usłudze Microsoft Sentinel umożliwia zaimportowanie wszystkich zdarzeń DLP do usługi Sentinel w celu rozszerzenia korelacji, wykrywania i badania w innych źródłach danych oraz rozszerzenia zautomatyzowanych przepływów orkiestracji przy użyciu natywnych funkcji soar usługi Sentinel. 

1. Postępuj zgodnie z instrukcjami dotyczącymi łączenia danych z Microsoft 365 Defender do usługi Microsoft Sentinel, aby zaimportować wszystkie zdarzenia, w tym zdarzenia DLP i alerty do usługi Sentinel. Włącz `CloudAppEvents` łącznik zdarzeń, aby ściągnąć wszystkie dzienniki inspekcji usługi O365 do usługi Sentinel.

   Po skonfigurowaniu powyższego łącznika powinno być możliwe wyświetlanie zdarzeń DLP w usłudze Sentinel.

2. Wybierz pozycję **Alerty,** aby wyświetlić stronę alertu.

3. Możesz użyć **alertType**, **startTime** i **endTime** , aby wykonać zapytanie dotyczące tabeli **CloudAppEvents** , aby uzyskać wszystkie działania użytkownika, które przyczyniły się do alertu. Użyj tego zapytania, aby zidentyfikować podstawowe działania:

```kusto
let Alert = SecurityAlert 
| where TimeGenerated  > ago(30d) 
| where SystemAlertId == "" // insert the systemAlertID here 
CloudAppEvents 
| extend correlationId = parse_json(tostring(RawEventData.Data)).cid
| join kind=inner Alert on $left.correlationId == $right.AlertType 
| where RawEventData.CreationTime > StartTime and RawEventData.CreationTime < EndTime
```

## <a name="related-articles"></a>Powiązane artykuły:

- [Omówienie zdarzeń](incidents-overview.md)
- [Określanie priorytetów zdarzeń](incident-queue.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
