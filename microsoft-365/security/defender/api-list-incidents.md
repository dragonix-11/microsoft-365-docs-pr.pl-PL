---
title: Interfejs API zdarzeń listy w programie Microsoft 365 Defender
description: Dowiedz się, jak wyświetlić interfejs API zdarzeń w programie Microsoft 365 Defender
keywords: list, incident, incidents, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 03fbcb70588158919b54c9153b5d8d32d416cc75
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013694"
---
# <a name="list-incidents-api-in-microsoft-365-defender"></a>Interfejs API zdarzeń listy w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Niektóre informacje odnoszą się do wstępnie wypuszczonych produktów, które mogą zostać znacząco zmodyfikowane przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

## <a name="api-description"></a>Opis interfejsu API

Interfejs API zdarzeń dotyczących list umożliwia sortowanie zdarzeń w celu utworzenia przejętnego reagowania na zdarzenia. Udostępnia on kolekcję zdarzeń oflagowanych w Twojej sieci w zakresie czasu określonym przez zasady przechowywania środowiska. Najnowsze zdarzenia są wyświetlane u góry listy. Każde zdarzenie zawiera tablicę powiązanych alertów i powiązanych z nimi jednostek.

Interfejs API obsługuje następujące **operatory OData** :

- `$filter`na , `lastUpdateTime``createdTime`i `status`właściwościach `assignedTo`
- `$top`o maksymalnej wartości **100**
- `$skip`

## <a name="limitations"></a>Ograniczenia

1. Maksymalny rozmiar strony to **100 zdarzeń**.
2. Maksymalna liczba zgłoszeń to **50 połączeń na** minutę i **1500 połączeń na godzinę**.

## <a name="permissions"></a>Uprawnienia

Do wywołania tego interfejsu API jest wymagane jedno z następujących uprawnień. Aby dowiedzieć się więcej, w tym jak wybrać uprawnienia, zobacz Interfejsy [API Microsoft 365 Defender Access](api-access.md).

Typ uprawnień|Uprawnienie|Nazwa wyświetlana uprawnień
---|---|---
Aplikacja|Incident.Read.All|Odczytywanie wszystkich zdarzeń
Aplikacja|Incident.ReadWrite.All|Czytanie i pisanie wszystkich zdarzeń
Delegowane (konto służbowe)|Incident.Read|Czytanie zdarzeń
Delegowane (konto służbowe)|Incident.ReadWrite|Zdarzenia przeczytania i pisania

> [!NOTE]
> W przypadku uzyskiwania tokenu przy użyciu poświadczeń użytkownika:
>
> - Użytkownik musi mieć uprawnienia do wyświetlania zdarzeń w portalu.
> - Odpowiedź będzie dotyczyć tylko zdarzeń, na które użytkownik jest ujawniony.

## <a name="http-request"></a>Żądanie HTTP

```HTTP
GET /api/incidents
```

## <a name="request-headers"></a>Żądaj nagłówków

Name (Nazwa)|Wpisać|Opis
---|---|---
Autoryzacja|Ciąg|Użytkownik {token}. **Wymagane**

## <a name="request-body"></a>Treść wniosku

Brak.

## <a name="response"></a>Odpowiedź

Jeśli ta metoda się powiedzie`200 OK`, ta metoda zwróci wartość , [](api-incident.md) a w treści odpowiedzi zostanie wyświetlona lista zdarzeń.

## <a name="schema-mapping"></a>Mapowanie schematu

### <a name="incident-metadata"></a>Metadane zdarzenia

Nazwa pola|Opis|Wartość przykładowa
---|---|---
incidentId|Unikatowy identyfikator reprezentujący zdarzenie|924565
redirectIncidentId|Dane są wypełniane tylko w przypadku zgrupowania zdarzenia razem z innym zdarzeniem w ramach logiki przetwarzania zdarzeń.|924569
nazwa_zdarzenia|Wartość ciągu dostępna dla każdego zdarzenia.|Aktywność oprogramowania wymuszającego okup
createdTime|Czas utworzenia zdarzenia.|2020-09-06T14:46:57.073333Z
lastUpdateTime|Godzina ostatniej aktualizacji zdarzenia w zapleczam. <p> To pole może być używane, gdy ustawiasz parametr żądania na przedział czasu pobierania zdarzeń.|2020-09-06T14:46:57.29Z
assignedTo|Właściciel zdarzenia lub wartość *null* , jeśli nie przypisano żadnego właściciela.|secop2@contoso.com
klasyfikacja|Specyfikacja zdarzenia. Wartości właściwości to: *Nieznany*, *FalsePositive*, *TruePositive*|Unknown
wyznaczanie|Określa określenie zdarzenia. Wartości właściwości są: *NotAvailable*, *Apt*, *Malware*, *SecurityPersonnel*, *SecurityTesting*, *UnwantedSoftware*, *Other*|NotAvailable
detectionSource (Źródło wykrywania)|Określa źródło wykrywania.|Defender for Cloud Apps
stan|Kategoryzowanie zdarzeń (jako *aktywnych* lub *rozwiązanych*). Może ułatwić organizowanie reakcji na zdarzenia i zarządzanie nimi.|Aktywny
ważność|Wskazuje możliwy wpływ na zasoby. Im wyższa ważność, tym większe znaczenie. Zazwyczaj elementy o wyższym poziomie ważności wymagają natychmiastowej uwagi. <p> Jedna z następujących wartości: *Informacyjne, Niskie*, *Średnie i *Wysokie*.|Średni
tagi|Tablica tagów niestandardowych skojarzonych z zdarzeniem, na przykład w celu oflagowania grupy zdarzeń o wspólnym cechu.|\[\]
komentarze|Tablica komentarzy tworzona przez zabezpieczanie podczas zarządzania zdarzeniem, na przykład dodatkowe informacje o wyborze klasyfikacji.|\[\]
alerty|Tablica zawierająca wszystkie alerty dotyczące zdarzenia oraz inne informacje, takie jak ważność, jednostki, które uczestniczyły w alercie, oraz źródło alertów.|\[\] (zobacz szczegóły w polach alertów poniżej)

### <a name="alerts-metadata"></a>Alerty metadanych

Nazwa pola|Opis|Wartość przykładowa
---|---|---
alertId|Unikatowy identyfikator reprezentujący alert|caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC
incidentId|Unikatowy identyfikator reprezentujący zdarzenie, z które jest skojarzony ten alert|924565
serviceSource (Źródłos usług)|Usługa, z której pochodzi alert, na przykład Program Microsoft Defender for Endpoint, Microsoft Defender for Cloud Apps, Microsoft Defender for Identity lub Microsoft Defender for Office 365.|MicrosoftCloudAppSecurity
creationTime|Czas utworzenia alertu.|2020-09-06T14:46:55.7182276Z
lastUpdatedTime|Czas ostatniej aktualizacji alertu w zapleczam.|2020-09-06T14:46:57.2433333Z
resolvedTime|Czas rozwiązania alertu.|2020-09-10T05:22:59Z
firstActivity|Czas, gdy alert informował po raz pierwszy, że działanie zostało zaktualizowane w zapleczam.|2020-09-04T05:22:59Z
tytuł|Dostępna krótka wartość identyfikująca ciąg dla każdego alertu.|Aktywność oprogramowania wymuszającego okup
opis|Wartość ciągu opisująca poszczególne alerty.|Użytkownik testowy User2 (testUser2@contoso.com) manipulował 99 plikami o wielu rozszerzeniach kończących się nietypowym rozszerzeniem *herunterladen*. Jest to nietypowej liczby manipulowania plikami i jest chwałą potencjalnego ataku oprogramowania wymuszającego okup.
kategoria|Wizualny i numeryczny widok tego, jak daleko przebiegają ataki wzdłuż łańcucha killów. Dostosowane do struktury [CK™&ATT MITRE](https://attack.mitre.org/).|Wpływ
stan|Kategoryzowanie alertów (jako *Nowy*, *Aktywny* lub *Rozwiązany*). Może ułatwić porządkowanie odpowiedzi na alerty i zarządzanie nimi.|Nowy
ważność|Wskazuje możliwy wpływ na zasoby. Im wyższa ważność, tym większe znaczenie. Zazwyczaj elementy o wyższym poziomie ważności wymagają natychmiastowej uwagi.<br>Jedna z następujących wartości: *Informacyjne, Niskie*, *Średnie* i *Wysokie*.|Średni
investigationId|Zautomatyzowany identyfikator badania wyzwolony przez ten alert.|1234
investigationState|Informacje o bieżącym stanie badania. Jedna z następujących *wartości: Nieznany**, Zakończony*, *PomyślniePolecony**, Niepowodzenie**, Niepowodzenie*, Częściowo *Bezpośrednio*, *Uruchomiony,* *PendingApproval*, *PendingResource*, *PartiallyWestigated*, *TerminatedByUser, TerminatedBySystem*, *Queued*, *InnerFailure*, *PreexistingAlert*, *UnsupportedOs*, *UnsupportedAlertType*, *PomińAlert*.|UnsupportedAlertType
klasyfikacja|Specyfikacja zdarzenia. Wartości właściwości to: *Nieznany*, *FalsePositive*, *TruePositive* lub *null*|Unknown
wyznaczanie|Określa określenie zdarzenia. Wartości właściwości są: *NotAvailable*, *Apt*, *Malware*, *SecurityPersonnel*, *SecurityTesting*, *UnwantedSoftware*, *Other* or  *null*|M
assignedTo|Właściciel zdarzenia lub wartość *null* , jeśli nie przypisano żadnego właściciela.|secop2@contoso.com
actorName|Grupa działań skojarzona z tym alertem (o ile taka grupa jest skojarzona).|BORON
threatFamilyName|Rodzina zagrożeń skojarzona z tym alertem.|null
mitreTechniques|Techniki ataków zgodne z programem [MITRE ATT&CK](https://attack.mitre.org/)™.|\[\]
urządzenia|Wszystkie urządzenia, na których zostały wysłane alerty związane z incydentem.|\[\] (zobacz szczegóły dotyczące pól encji poniżej)

### <a name="device-format"></a>Format urządzenia

Nazwa pola|Opis|Wartość przykładowa
---|---|---
DeviceId|Identyfikator urządzenia wskazany w programie Microsoft Defender for Endpoint.|24c222b0b60fe148eeece49ac83910cc6a7ef491
aadDeviceId|Identyfikator urządzenia wskazany w [Azure Active Directory.](/azure/active-directory/fundamentals/active-directory-whatis) Dostępne tylko dla urządzeń przyłącznych do domeny.|null
deviceDnsName|W pełni kwalifikowana nazwa domeny urządzenia.|user5cx.middleeast.corp.contoso.com
osPlatform|Platforma systemu operacyjnego, na której urządzenie działa.|WindowsServer2016
osBuild|Wersja kompilacji systemu operacyjnego, na który jest uruchomione urządzenie.|14393
rbacGroupName|Grupa [kontroli dostępu oparta na rolach](/azure/role-based-access-control/overview) (RBAC, role based access control) skojarzona z urządzeniem.|WDATP-Ring0
firstSeen|Czas, gdy urządzenie zostało widziane po raz pierwszy.|2020-02-06T14:16:01.9330135Z
healthStatus (Stan kondycji)|Stan kondycji urządzenia.|Aktywny
riskScore|Wynik ryzyka dla urządzenia.|High (Wysoki)
jednostki|Wszystkie jednostki, które zostały zidentyfikowane jako część danego alertu lub z nim powiązane.|\[\] (zobacz szczegóły dotyczące pól encji poniżej)

### <a name="entity-format"></a>Format encja

Nazwa pola|Opis|Wartość przykładowa
---|---|---
entityType|Jednostki, które zostały zidentyfikowane jako część danego alertu lub z nim powiązane.<br>Wartości właściwości to: *Użytkownik*, *Ip*, *Adres URL**, Plik*, *Proces*, *MailBox*, *MailMessage*, *MailCluster*, *Rejestr*|Użytkownik
sha1|Dostępny, jeśli element entityType to *File*.<br>Skrót pliku dla alertów skojarzonych z plikiem lub procesem.|5de839186691aa96ee2ca6d74f0a38fb8d1bd6ddd
sha256|Dostępny, jeśli element entityType to *File*.<br>Skrót pliku dla alertów skojarzonych z plikiem lub procesem.|28cb017dfc99073aa1b47c1b30f413e3ce774c4991eb4158de50f9dbb36d8043
nazwa_pliku|Dostępny, jeśli element entityType to *File*.<br>Nazwa pliku alertów skojarzonych z plikiem lub procesem|Detector.UnitTests.dll
filePath|Dostępny, jeśli element entityType to *File*.<br>Ścieżka pliku alertów skojarzonych z plikiem lub procesem|C:\\\agent_work_temp\Deploy\SYSTEM\2020-09-06 12_14_54\Out
processId|Dostępny, jeśli element entityType to *Proces*.|24348
processCommandLine|Dostępny, jeśli element entityType to *Proces*.|"Plik jest gotowy do pobrania1911150169.exe\_ "
processCreationTime|Dostępny, jeśli element entityType to *Proces*.|2020-07-18T03:25:38.5269993Z
parentProcessId|Dostępny, jeśli element entityType to *Proces*.|16840
parentProcessCreationTime|Dostępny, jeśli element entityType to *Proces*.|2020-07-18T02:12:32.8616797Z
ipAddress|Dostępny, jeśli entityType to *Ip*. <br>Adres IP alertów skojarzonych ze zdarzeniami sieciowym, takich jak *Komunikacja ze złośliwym miejscem docelowym sieci*.|62.216.203.204
adres URL|Dostępny, jeśli element entityType to *Url*. <br>Adres URL alertów skojarzonych ze zdarzeniami sieciowym, takimi jak Komunikacja *ze złośliwym miejscem docelowym sieci*.|down.esales360.cn
accountName|Dostępny, jeśli element entityType to *Użytkownik*.|testUser2
nazwa_domeny|Dostępny, jeśli element entityType to *Użytkownik*.|europe.corp.contoso
userSid|Dostępny, jeśli element entityType to *Użytkownik*.|S-1-5-21-1721254763-462695806-1538882281-4156657
aadUserId|Dostępny, jeśli element entityType to *Użytkownik*.|fc8f7484-f813-4db2-afab-bc1507913fb6
userPrincipalName|Dostępny, jeśli element entityType to *UserMailBoxMailMessage*//.|testUser2@contoso.com
mailboxDisplayName|Dostępny, jeśli element entityType to *MailBox*.|testowanie użytkownika 2
mailboxAddress|Dostępny, jeśli element entityType to *UserMailBoxMailMessage*//.|testUser2@contoso.com
clusterBy|Dostępny, jeśli element entityType to  *MailCluster*.|Temat; P2SenderDomain; ContentType
nadawca|Dostępny, jeśli element entityType to *UserMailBoxMailMessage*//.|user.abc@mail.contoso.co.in
adresat|Dostępny, jeśli element entityType to *MailMessage*.|testUser2@contoso.com
Temat|Dostępny, jeśli element entityType to *MailMessage*.|\[UWAGA ZEWNĘTRZNA\]
deliveryAction|Dostępny, jeśli element entityType to *MailMessage*.|Dostarczono
securityGroupId|Jeśli element entityType to  *SecurityGroup, jest dostępny*.|301c47c8-e15f-4059-ab09-e2ba9ffd372b
securityGroupName|Jeśli element entityType to  *SecurityGroup, jest dostępny*.|Operatory konfiguracji sieci
registryHive|Dostępny, jeśli element entityType  *to Registry*.|HKEYLOCALMACHINE\_\_|
klucz rejestru|Dostępny, jeśli element entityType  *to Registry*.|SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
registryValueType|Dostępny, jeśli element entityType  *to Registry*.|Ciąg
registryValue|Dostępny, jeśli element entityType  *to Registry*.|31-00-00-00
deviceId|Identyfikator (jeśli wie) urządzenia powiązanego z jednostką.|986e5df8b73dacd43c8917d17e523e76b13c75cd

## <a name="example"></a>Przykład

### <a name="request-example"></a>Przykład żądania

```HTTP
GET https://api.security.microsoft.com/api/incidents
```

### <a name="response-example"></a>Przykład odpowiedzi

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Incidents",
    "value": [
            {
            "incidentId": 924565,
            "redirectIncidentId": null,
            "incidentName": "Ransomware activity",
            "createdTime": "2020-09-06T14:46:57.0733333Z",
            "lastUpdateTime": "2020-09-06T14:46:57.29Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Medium",
            "tags": [],
            "comments": [
                {
                    "comment": "test comment for docs",
                    "createdBy": "secop123@contoso.com",
                    "createdTime": "2021-01-26T01:00:37.8404534Z"
                }
            ],
            "alerts": [
                {
                    "alertId": "caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC",
                    "incidentId": 924565,
                    "serviceSource": "MicrosoftCloudAppSecurity",
                    "creationTime": "2020-09-06T14:46:55.7182276Z",
                    "lastUpdatedTime": "2020-09-06T14:46:57.2433333Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-04T05:22:59Z",
                    "lastActivity": "2020-09-04T05:22:59Z",
                    "title": "Ransomware activity",
                    "description": "The user Test User2 (testUser2@contoso.com) manipulated 99 files with multiple extensions ending with the uncommon extension herunterladen. This is an unusual number of file manipulations and is indicative of a potential ransomware attack.",
                    "category": "Impact",
                    "status": "New",
                    "severity": "Medium",
                    "investigationId": null,
                    "investigationState": "UnsupportedAlertType",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "MCAS",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "User",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": "testUser2",
                            "domainName": "europe.corp.contoso",
                            "userSid": "S-1-5-21-1721254763-462695806-1538882281-4156657",
                            "aadUserId": "fc8f7484-f813-4db2-afab-bc1507913fb6",
                            "userPrincipalName": "testUser2@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "62.216.203.204",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924521,
            "redirectIncidentId": null,
            "incidentName": "'Mimikatz' hacktool was detected on one endpoint",
            "createdTime": "2020-09-06T12:18:03.6266667Z",
            "lastUpdateTime": "2020-09-06T12:18:03.81Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Low",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "da637349914833441527_393341063",
                    "incidentId": 924521,
                    "serviceSource": "MicrosoftDefenderATP",
                    "creationTime": "2020-09-06T12:18:03.3285366Z",
                    "lastUpdatedTime": "2020-09-06T12:18:04.2566667Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:15:07.7272048Z",
                    "lastActivity": "2020-09-06T12:15:07.7272048Z",
                    "title": "'Mimikatz' hacktool was detected",
                    "description": "Readily available tools, such as hacking programs, can be used by unauthorized individuals to spy on users. When used by attackers, these tools are often installed without authorization and used to compromise targeted machines.\n\nThese tools are often used to collect personal information from browser records, record key presses, access email and instant messages, record voice and video conversations, and take screenshots.\n\nThis detection might indicate that Windows Defender Antivirus has stopped the tool from being installed and used effectively. However, it is prudent to check the machine for the files and processes associated with the detected tool.",
                    "category": "Malware",
                    "status": "New",
                    "severity": "Low",
                    "investigationId": null,
                    "investigationState": "UnsupportedOs",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "WindowsDefenderAv",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": "Mimikatz",
                    "mitreTechniques": [],
                    "devices": [
                        {
                            "mdatpDeviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491",
                            "aadDeviceId": null,
                            "deviceDnsName": "user5cx.middleeast.corp.contoso.com",
                            "osPlatform": "WindowsServer2016",
                            "version": "1607",
                            "osProcessor": "x64",
                            "osBuild": 14393,
                            "healthStatus": "Active",
                            "riskScore": "High",
                            "rbacGroupName": "WDATP-Ring0",
                            "rbacGroupId": 9,
                            "firstSeen": "2020-02-06T14:16:01.9330135Z"
                        }
                    ],
                    "entities": [
                        {
                            "entityType": "File",
                            "sha1": "5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd",
                            "sha256": null,
                            "fileName": "Detector.UnitTests.dll",
                            "filePath": "C:\\Agent\\_work\\_temp\\Deploy_SYSTEM 2020-09-06 12_14_54\\Out",
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491"
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924518,
            "redirectIncidentId": null,
            "incidentName": "Email reported by user as malware or phish",
            "createdTime": "2020-09-06T12:07:55.1366667Z",
            "lastUpdateTime": "2020-09-06T12:07:55.32Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Informational",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "faf8edc936-85f8-a603-b800-08d8525cf099",
                    "incidentId": 924518,
                    "serviceSource": "OfficeATP",
                    "creationTime": "2020-09-06T12:07:54.3716642Z",
                    "lastUpdatedTime": "2020-09-06T12:37:40.88Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:04:00Z",
                    "lastActivity": "2020-09-06T12:04:00Z",
                    "title": "Email reported by user as malware or phish",
                    "description": "This alert is triggered when any email message is reported as malware or phish by users -V1.0.0.2",
                    "category": "InitialAccess",
                    "status": "InProgress",
                    "severity": "Informational",
                    "investigationId": null,
                    "investigationState": "Queued",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "OfficeATP",
                    "assignedTo": "Automation",
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser3@contoso.com",
                            "mailboxDisplayName": "test User3",
                            "mailboxAddress": "testUser3@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser4@contoso.com",
                            "mailboxDisplayName": "test User4",
                            "mailboxAddress": "test.User4@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailMessage",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "test.User4@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": "user.abc@mail.contoso.co.in",
                            "recipient": "test.User4@contoso.com",
                            "subject": "[EXTERNAL] Attention",
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "49.50.81.121",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        ...
    ]
}
```

## <a name="related-articles"></a>Artykuły pokrewne

- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Informacje o limitach i licencjonowaniu interfejsu API](api-terms.md)
- [Opis kodów błędów](api-error-codes.md)
- [Omówienie zdarzeń](incidents-overview.md)
- [Interfejsy API zdarzenia](api-incident.md)
- [Aktualizowanie interfejsu API zdarzenia](api-update-incidents.md)
