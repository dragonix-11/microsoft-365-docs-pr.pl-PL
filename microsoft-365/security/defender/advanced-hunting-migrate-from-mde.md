---
title: Migrowanie zaawansowanych zapytań dotyczących wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak dostosować zapytania Ochrona punktu końcowego w usłudze Microsoft Defender, aby można było ich używać w Microsoft 365 Defender
keywords: zaawansowane polowanie, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń, wyszukiwanie zagrożeń cybernetycznych, Microsoft 365 Defender, microsoft 365, m365, Ochrona punktu końcowego w usłudze Microsoft Defender, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, mapowanie
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 9fd00df5e61d37e5133f23e5f06973ceb99c4636
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666179"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Migrowanie zaawansowanych zapytań dotyczących wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Przenieś zaawansowane przepływy pracy wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender, aby proaktywnie wyszukiwać zagrożenia przy użyciu szerszego zestawu danych. W Microsoft 365 Defender uzyskujesz dostęp do danych z innych Microsoft 365 rozwiązań zabezpieczeń, w tym:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Ochrona usługi Office 365 w usłudze Microsoft Defender
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

>[!NOTE]
>Większość Ochrona punktu końcowego w usłudze Microsoft Defender klientów może [korzystać z Microsoft 365 Defender bez dodatkowych licencji](prerequisites.md#licensing-requirements). Aby rozpocząć przenoszenie zaawansowanych przepływów pracy wyszukiwania zagrożeń z usługi Defender for Endpoint, [włącz Microsoft 365 Defender](m365d-enable.md).

Możesz przejść bez wpływu na istniejące przepływy pracy usługi Defender for Endpoint. Zapisane zapytania pozostają nienaruszone, a niestandardowe reguły wykrywania nadal uruchamiają i generują alerty. Będą one jednak widoczne w Microsoft 365 Defender.

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Tabele schematów tylko w Microsoft 365 Defender

Zaawansowany [schemat wyszukiwania zagrożeń Microsoft 365 Defender](advanced-hunting-schema-tables.md) udostępnia dodatkowe tabele zawierające dane z różnych rozwiązań zabezpieczeń Microsoft 365. Następujące tabele są dostępne tylko w Microsoft 365 Defender:

| Nazwa tabeli | Opis |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Pliki, adresy IP, adresy URL, użytkownicy lub urządzenia skojarzone z alertami |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Alerty z Ochrona punktu końcowego w usłudze Microsoft Defender, Ochrona usługi Office 365 w usłudze Microsoft Defender, Microsoft Defender for Cloud Apps i Microsoft Defender for Identity, w tym informacje o ważności i kategorie zagrożeń  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | Informacje o plikach dołączonych do wiadomości e-mail |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365 zdarzenia e-mail, w tym dostarczanie wiadomości e-mail i blokowanie zdarzeń |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Zdarzenia zabezpieczeń występujące po dostarczeniu, po Microsoft 365 dostarczyły wiadomości e-mail do skrzynki pocztowej adresata |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | Informacje o adresach URL wiadomości e-mail |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Zdarzenia z udziałem lokalnego kontrolera domeny z uruchomioną usługą Active Directory (AD). Ta tabela obejmuje szereg zdarzeń związanych z tożsamością i zdarzeń systemowych na kontrolerze domeny. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Informacje o kontach z różnych źródeł, w tym Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Zdarzenia uwierzytelniania w usługach Active Directory i Microsoft Usługi online |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Zapytania dotyczące obiektów usługi Active Directory, takich jak użytkownicy, grupy, urządzenia i domeny |

>[!IMPORTANT]
> Zapytania i wykrywanie niestandardowe korzystające z tabel schematów, które są dostępne tylko w Microsoft 365 Defender, można wyświetlać tylko w Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>Mapowanie tabeli DeviceAlertEvents

Tabele `AlertInfo` i `AlertEvidence` zastępują tabelę `DeviceAlertEvents` w schemacie Ochrona punktu końcowego w usłudze Microsoft Defender. Oprócz danych dotyczących alertów urządzeń te dwie tabele zawierają dane dotyczące alertów dotyczących tożsamości, aplikacji i wiadomości e-mail.

Użyj poniższej tabeli, aby sprawdzić, jak `DeviceAlertEvents` kolumny są mapowane na kolumny w tabelach `AlertInfo` i `AlertEvidence` .

> [!TIP]
> Oprócz kolumn w poniższej tabeli tabela zawiera wiele innych kolumn, `AlertEvidence` które zapewniają bardziej całościowy obraz alertów z różnych źródeł. [Zobacz wszystkie kolumny AlertEvidence](advanced-hunting-alertevidence-table.md)

| Kolumna DeviceAlertEvents | Gdzie znaleźć te same dane w Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` i  `AlertEvidence` tabele |
| `Timestamp` | `AlertInfo` i  `AlertEvidence` tabele |
| `DeviceId` | `AlertEvidence` Tabeli |
| `DeviceName` | `AlertEvidence` Tabeli |
| `Severity` | `AlertInfo` Tabeli |
| `Category` | `AlertInfo` Tabeli |
| `Title` | `AlertInfo` Tabeli |
| `FileName` | `AlertEvidence` Tabeli |
| `SHA1` | `AlertEvidence` Tabeli |
| `RemoteUrl` | `AlertEvidence` Tabeli |
| `RemoteIP` | `AlertEvidence` Tabeli |
| `AttackTechniques` | `AlertInfo` Tabeli |
| `ReportId` | Ta kolumna jest zwykle używana w Ochrona punktu końcowego w usłudze Microsoft Defender do lokalizowania powiązanych rekordów w innych tabelach. W Microsoft 365 Defender możesz pobrać powiązane dane bezpośrednio z `AlertEvidence` tabeli. |
| `Table` | Ta kolumna jest zwykle używana w Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać dodatkowe informacje o zdarzeniach w innych tabelach. W Microsoft 365 Defender możesz pobrać powiązane dane bezpośrednio z `AlertEvidence` tabeli. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Dostosowywanie istniejących zapytań Ochrona punktu końcowego w usłudze Microsoft Defender

Ochrona punktu końcowego w usłudze Microsoft Defender zapytania będą działać w następującym stanie, chyba że odwołują się do `DeviceAlertEvents` tabeli. Aby użyć tych zapytań w Microsoft 365 Defender, zastosuj następujące zmiany:

- Zastąp ciąg `DeviceAlertEvents` .`AlertInfo`
- `AlertInfo` Dołącz do tabel i, `AlertEvidence` `AlertId` aby uzyskać równoważne dane.

### <a name="original-query"></a>Oryginalne zapytanie

Następujące zapytanie używa `DeviceAlertEvents` w Ochrona punktu końcowego w usłudze Microsoft Defender, aby uzyskać alerty, które obejmują _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```

### <a name="modified-query"></a>Zmodyfikowane zapytanie

Następujące zapytanie zostało dostosowane do użycia w Microsoft 365 Defender. Zamiast sprawdzać nazwę pliku bezpośrednio z `DeviceAlertEvents`programu , dołącza `AlertEvidence` ona i sprawdza nazwę pliku w tej tabeli.

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)"
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Migrowanie niestandardowych reguł wykrywania

Gdy reguły Ochrona punktu końcowego w usłudze Microsoft Defender są edytowane w Microsoft 365 Defender, nadal działają tak jak poprzednio, jeśli wynikowe zapytanie analizuje tylko tabele urządzeń.

Na przykład alerty generowane przez niestandardowe reguły wykrywania, które wysyłają zapytania tylko do tabel urządzeń, będą nadal dostarczane do rozwiązania SIEM i generują powiadomienia e-mail, w zależności od tego, jak zostały skonfigurowane w Ochrona punktu końcowego w usłudze Microsoft Defender. Wszelkie istniejące reguły pomijania w usłudze Defender for Endpoint również będą nadal stosowane.

Po edytowaniu reguły usługi Defender for Endpoint w taki sposób, aby wysyłała zapytania dotyczące tabel tożsamości i wiadomości e-mail, które są dostępne tylko w Microsoft 365 Defender, reguła jest automatycznie przenoszona do Microsoft 365 Defender.

Alerty generowane przez zmigrowane reguły:

- Nie są już widoczne w portalu usługi Defender for Endpoint (Centrum zabezpieczeń usługi Microsoft Defender)
- Zatrzymaj dostarczanie do rozwiązania SIEM lub wygeneruj powiadomienia e-mail. Aby obejść tę zmianę, skonfiguruj powiadomienia za pośrednictwem Microsoft 365 Defender, aby uzyskać alerty. Interfejs [API Microsoft 365 Defender](api-incident.md) umożliwia otrzymywanie powiadomień dotyczących alertów wykrywania klientów lub powiązanych zdarzeń.
- Nie będą pomijane przez reguły pomijania Ochrona punktu końcowego w usłudze Microsoft Defender. Aby zapobiec generowaniu alertów dla niektórych użytkowników, urządzeń lub skrzynek pocztowych, zmodyfikuj odpowiednie zapytania, aby jawnie wykluczyć te jednostki.

Jeśli edytujesz regułę w ten sposób, zostanie wyświetlony monit o potwierdzenie przed zastosowaniem takich zmian.

Nowe alerty generowane przez niestandardowe reguły wykrywania w Microsoft 365 Defender są wyświetlane na stronie alertu zawierającej następujące informacje:

- Tytuł i opis alertu
- Zasoby, których dotyczy problem
- Akcje podjęte w odpowiedzi na alert
- Wyniki zapytania, które wyzwoliły alert
- Informacje o niestandardowej regule wykrywania

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="Przykład strony alertu, która wyświetla nowe alerty generowane przez niestandardowe reguły wykrywania w portalu Microsoft 365 Defender" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>Pisanie zapytań bez funkcji DeviceAlertEvents

W schemacie Microsoft 365 Defender tabele i `AlertEvidence` są dostarczane w `AlertInfo` celu uwzględnienia zróżnicowanego zestawu informacji towarzyszących alertom z różnych źródeł.

Aby uzyskać te same informacje o alertach, które zostały użyte do pobrania z `DeviceAlertEvents` tabeli w schemacie Ochrona punktu końcowego w usłudze Microsoft Defender, przefiltruj `AlertInfo` tabelę według`ServiceSource`, a następnie dołącz każdy unikatowy identyfikator do `AlertEvidence` tabeli, która zawiera szczegółowe informacje o zdarzeniach i jednostkach.

Zobacz przykładowe zapytanie poniżej:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

To zapytanie zwraca o wiele więcej kolumn niż `DeviceAlertEvents` w schemacie Ochrona punktu końcowego w usłudze Microsoft Defender. Aby zapewnić zarządzanie wynikami, użyj polecenia `project` , aby uzyskać tylko interesujące Cię kolumny. W poniższym przykładzie przedstawiono kolumny projektów, które mogą cię zainteresować, gdy badanie wykryło działanie programu PowerShell:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine
```

Jeśli chcesz filtrować określone jednostki biorące udział w alertach, możesz to zrobić, określając typ jednostki i `EntityType` wartość, dla których chcesz filtrować. Poniższy przykład szuka określonego adresu IP:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId
| where EntityType == "Ip" and RemoteIP == "192.88.99.01"
```

## <a name="see-also"></a>Zobacz też

- [Włączanie usługi Microsoft 365 Defender](advanced-hunting-query-language.md)
- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Zaawansowane wyszukiwanie zagrożeń w Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
