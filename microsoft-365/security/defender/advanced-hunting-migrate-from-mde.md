---
title: Migrowanie zaawansowanych zapytań myśliwnych z programu Microsoft Defender dla punktu końcowego
description: Dowiedz się, jak dostosować usługę Microsoft Defender dla zapytań końcowych, aby można było ich używać w Microsoft 365 Defender
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, Microsoft Defender for Endpoint, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, kusto, mapowanie
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
ms.openlocfilehash: e64d1a56468d6e87d23c5720bb231e17ecd5679a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013662"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Migrowanie zaawansowanych zapytań myśliwnych z programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Przenieś zaawansowane przepływy pracy wyszukiwania z usługi Microsoft Defender for Endpoint, aby aktywnie poszukać zagrożeń przy użyciu szerszego zestawu danych. W Microsoft 365 Defender uzyskujesz dostęp do danych z innych Microsoft 365 zabezpieczeń, takich jak:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Usługa Microsoft Defender dla Office 365
- Usługa Microsoft Defender dla aplikacji w chmurze
- Microsoft Defender for Identity

>[!NOTE]
>Większość klientów korzystających z usługi Microsoft Defender dla [punktu końcowego Microsoft 365 Defender może korzystać z usługi bez dodatkowych licencji](prerequisites.md#licensing-requirements). Aby rozpocząć przechodzenie zaawansowanych przepływów pracy chłoniania z usługi Defender for Endpoint, [włącz program Microsoft 365 Defender](m365d-enable.md).

Możesz przejść bez wpływu na istniejące przepływy pracy usługi Defender for Endpoint. Zapisane zapytania pozostaną niezmienione, a niestandardowe reguły wykrywania będą nadal uruchamiać i generować alerty. Będą one jednak widoczne w programie Microsoft 365 Defender. 

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Tylko tabele schematów Microsoft 365 Defender schematów
Zaawansowane [Microsoft 365 Defender dla łów](advanced-hunting-schema-tables.md) zapewnia dodatkowe tabele zawierające dane z różnych Microsoft 365 zabezpieczeń. Następujące tabele są dostępne tylko w Microsoft 365 Defender:

| Nazwa tabeli | Opis |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Pliki, adresy IP, adresy URL, użytkownicy lub urządzenia skojarzone z alertami |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Alerty z programu Microsoft Defender dla punktu końcowego, programu Microsoft Defender dla aplikacji Office 365, programu Microsoft Defender dla aplikacji w chmurze i usługi Microsoft Defender dla tożsamości, w tym informacje o ważności i kategoriach zagrożeń  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | Informacje o plikach dołączonych do wiadomości e-mail |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365 e-mail, w tym dostarczanie i blokowanie zdarzeń wiadomości e-mail |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Zdarzenia zabezpieczeń występujące po dostarczeniu po Microsoft 365 wiadomości e-mail do skrzynki pocztowej adresata |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | Informacje o adresach URL w wiadomościach e-mail |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Zdarzenia dotyczące lokalnego kontrolera domeny z uruchomionym usługą Active Directory (AD). W poniższej tabeli o zajmę się szeregiem zdarzeń związanych z tożsamością i zdarzeń systemowych na kontrolerze domeny. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Informacje o koncie z różnych źródeł, w tym Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Zdarzenia uwierzytelniania w usługach Active Directory i Microsoft Online Services |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Zapytania dotyczące obiektów usługi Active Directory, takich jak użytkownicy, grupy, urządzenia i domeny |

>[!IMPORTANT]
> Zapytania i wykrywanie niestandardowe, które korzystają z tabel schematu dostępnych tylko w Microsoft 365 Defender, można wyświetlać tylko w Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>Mapowanie tabeli DeviceAlertEvents
Tabele `AlertInfo` i `AlertEvidence` zastąpią tabelę `DeviceAlertEvents` w schemacie programu Microsoft Defender dla punktu końcowego. Oprócz danych dotyczących alertów urządzenia te dwie tabele zawierają dane dotyczące alertów dla tożsamości, aplikacji i wiadomości e-mail.

Skorzystaj z poniższej tabeli, aby sprawdzić `DeviceAlertEvents` , jak kolumny są mapowanie na kolumny w tabelach `AlertInfo` i `AlertEvidence` .

>[!TIP]
>Oprócz kolumn w poniższej tabeli tabela zawiera wiele innych kolumn, `AlertEvidence` które zapewniają bardziej obraz obrazów alertów z różnych źródeł. [Wyświetlanie wszystkich kolumn alertów](advanced-hunting-alertevidence-table.md) 

| Kolumna DeviceAlertEvents | Gdzie można znaleźć te same dane w aplikacji Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` i  `AlertEvidence` tabele |
| `Timestamp` | `AlertInfo` i  `AlertEvidence` tabele |
| `DeviceId` | `AlertEvidence` tabela |
| `DeviceName` | `AlertEvidence` tabela |
| `Severity` | `AlertInfo` tabela |
| `Category` | `AlertInfo` tabela |
| `Title` | `AlertInfo` tabela |
| `FileName` | `AlertEvidence` tabela |
| `SHA1` | `AlertEvidence` tabela |
| `RemoteUrl` | `AlertEvidence` tabela |
| `RemoteIP` | `AlertEvidence` tabela |
| `AttackTechniques` | `AlertInfo` tabela |
| `ReportId` | Ta kolumna jest zwykle używana w programie Microsoft Defender for Endpoint do znajdowania powiązanych rekordów w innych tabelach. W Microsoft 365 Defender można pobrać powiązane dane bezpośrednio z `AlertEvidence` tabeli. |
| `Table` | Ta kolumna jest zazwyczaj używana w programie Microsoft Defender for Endpoint do dodatkowych informacji o zdarzeniach w innych tabelach. W Microsoft 365 Defender można pobrać powiązane dane bezpośrednio z `AlertEvidence` tabeli. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Dostosowywanie istniejących zapytań programu Microsoft Defender dla punktów końcowych
Zapytania programu Microsoft Defender for Endpoint będą działać bez odwołania do tabeli, chyba że odwołują się do `DeviceAlertEvents` tabeli. Aby używać tych zapytań w Microsoft 365 Defender, zastosuj następujące zmiany:

- Zamień `DeviceAlertEvents` na `AlertInfo`.
- Połącz tabele `AlertInfo` i tabele `AlertEvidence` , aby `AlertId` uzyskać równoważne dane.

### <a name="original-query"></a>Oryginalne zapytanie
Poniższe zapytanie używa programu `DeviceAlertEvents` Microsoft Defender for Endpoint do zwracania alertów dotyczących _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```
### <a name="modified-query"></a>Zmodyfikowano zapytanie
Następujące zapytanie zostało dostosowane do użycia w Microsoft 365 Defender. Zamiast sprawdzać nazwę pliku bezpośrednio z , `DeviceAlertEvents`program dołącza `AlertEvidence` i sprawdza nazwę pliku w tej tabeli.

```kusto
AlertInfo 
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" 
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Migrowanie niestandardowych reguł wykrywania

Podczas edytowania reguł programu Microsoft Defender for Endpoint Microsoft 365 Defender działają one tak, jak przed, jeśli wynikowe zapytanie będzie dotyczyło tylko tabel urządzeń. 

Na przykład alerty generowane przez niestandardowe reguły wykrywania, które wysyłają zapytania tylko do tabel urządzeń, nadal będą dostarczane do Twojego serwera SIEM i będą generować powiadomienia e-mail w zależności od sposobu ich skonfigurowania w programie Microsoft Defender for Endpoint. Wszelkie istniejące reguły konkurencji w programie Defender for Endpoint również będą obowiązywać.

Po edytowaniu reguły usługi Defender dla punktu końcowego w celu zapytania o tabele tożsamości i poczty e-mail, które są dostępne tylko w programie Microsoft 365 Defender, reguła jest automatycznie przenoszony do Microsoft 365 Defender. 

Alerty generowane przez migrowane reguły:

- Nie są już widoczne w portalu programu Defender for Endpoint (Centrum zabezpieczeń usługi Microsoft Defender)
- Przestań dostarczać wiadomości do SIEM lub wygeneruj powiadomienia e-mail. Aby zmienić tę zmianę, skonfiguruj powiadomienia za pośrednictwem Microsoft 365 Defender, aby otrzymywać alerty. Za pomocą interfejsu [API Microsoft 365 Defender możesz](api-incident.md) otrzymywać powiadomienia dotyczące alertów wykrywania klientów lub powiązanych zdarzeń.
- Reguły obowiązujące w programie Microsoft Defender dla punktów końcowych nie będą pomijane. Aby uniemożliwić generowanie alertów dla określonych użytkowników, urządzeń lub skrzynek pocztowych, zmodyfikuj odpowiadające im zapytania, aby jawnie wykluczyć te jednostki.

Jeśli edytujesz regułę w ten sposób, przed zastosowaniem takich zmian zostanie wyświetlony monit o potwierdzenie.

Nowe alerty generowane przez niestandardowe reguły wykrywania w aplikacji Microsoft 365 Defender są wyświetlane na stronie alertów, która zawiera następujące informacje:

- Tytuł i opis alertu 
- Mają wpływ środki trwałe
- Działania podejmowane w odpowiedzi na alert
- Wyniki kwerendy, które wyzwoliły alert 
- Informacje na temat niestandardowej reguły wykrywania 
 
> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="Przykład strony alertów z wyświetlonymi nowymi alertami wygenerowanmi przez niestandardowe reguły wykrywania w Microsoft 365 Defender sieci Web" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>Pisanie zapytań bez deviceAlertEvents

W schemacie `AlertInfo` `AlertEvidence` Microsoft 365 Defender i tabele są dostępne w celu dostosowania zróżnicowanego zestawu informacji, który towarzyszą alertom z różnych źródeł. 

Aby uzyskać te same informacje alertów `DeviceAlertEvents` , które są używane w tabeli w schemacie programu Microsoft Defender for Endpoint, `AlertInfo` `ServiceSource` `AlertEvidence` przefiltruj tabelę, a następnie dołącz do niej każdy unikatowy identyfikator za pomocą tabeli, która zawiera szczegółowe informacje o zdarzeniu i encji. 

Zobacz przykładowe zapytanie poniżej:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

To zapytanie zwraca o wiele więcej kolumn niż `DeviceAlertEvents` w schemacie programu Microsoft Defender for Endpoint. Aby zarządzać wynikami, użyj tej funkcji `project` , aby uzyskać tylko te kolumny, które Cię interesują. W poniższym przykładzie kolumny projektów, które mogą Cię zainteresować, gdy wykryto aktywność programu PowerShell:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine 
```

Jeśli chcesz filtrować według określonych jednostek uczestniczących w alertach, `EntityType` możesz to zrobić, określając typ encji i wartość, według których chcesz filtrować dane. Poniższy przykład wyszukuje konkretny adres IP:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId 
| where EntityType == "Ip" and RemoteIP == "192.88.99.01" 
```

## <a name="see-also"></a>Zobacz też
- [Włączanie Microsoft 365 Defender](advanced-hunting-query-language.md)
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Opis schematu](advanced-hunting-schema-tables.md)
- [Zaawansowane szukanie w programie Microsoft Defender dla punktu końcowego](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
