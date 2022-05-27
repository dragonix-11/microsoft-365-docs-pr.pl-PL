---
title: Wyszukiwanie zagrożeń na urządzeniach, wiadomościach e-mail, aplikacjach i tożsamościach przy użyciu zaawansowanego wyszukiwania zagrożeń
description: Zapoznaj się z typowymi scenariuszami wyszukiwania zagrożeń i przykładowymi zapytaniami obejmującymi urządzenia, wiadomości e-mail, aplikacje i tożsamości.
keywords: zaawansowane wyszukiwanie zagrożeń, dane usługi Office 365, urządzenia Windows, normalizowanie wiadomości e-mail usługi Office365, wiadomości e-mail, aplikacje, tożsamości, wyszukiwanie zagrożeń cybernetycznych, wyszukiwanie, zapytania, dane telemetryczne, Microsoft 365, Microsoft 365 Defender
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
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 0ca9a951ffd561113a806341d25bc1f0661732cc
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739954"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>Wyszukiwanie zagrożeń na urządzeniach, w wiadomościach e-mail, aplikacjach i tożsamościach

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

[Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md) w Microsoft 365 Defender umożliwia aktywne wyszukiwanie zagrożeń w różnych obszarach:
- Urządzenia zarządzane przez Ochrona punktu końcowego w usłudze Microsoft Defender
- Wiadomości e-mail przetwarzane przez Microsoft 365
- Działania aplikacji w chmurze, zdarzenia uwierzytelniania i działania kontrolera domeny śledzone przez Microsoft Defender for Cloud Apps i Microsoft Defender for Identity

Dzięki temu poziomowi widoczności można szybko wyszukiwać zagrożenia przechodzące przez sekcje sieci, w tym zaawansowane włamania, które docierają do poczty e-mail lub sieci Web, podnieść poziom uprawnień lokalnych, uzyskać poświadczenia domeny uprzywilejowanej i przenieść się później na urządzenia. 

Poniżej przedstawiono ogólne techniki i przykładowe zapytania oparte na różnych scenariuszach wyszukiwania zagrożeń, które mogą pomóc w eksplorowaniu sposobu konstruowania zapytań podczas wyszukiwania takich zaawansowanych zagrożeń.

## <a name="get-entity-info"></a>Pobieranie informacji o jednostce
Skorzystaj z tych zapytań, aby dowiedzieć się, jak szybko uzyskać informacje o kontach użytkowników, urządzeniach i plikach. 

### <a name="obtain-user-accounts-from-email-addresses"></a>Uzyskiwanie kont użytkowników z adresów e-mail
Podczas konstruowania zapytań w [tabelach obejmujących urządzenia i wiadomości e-mail](advanced-hunting-schema-tables.md) prawdopodobnie będzie konieczne uzyskanie nazw kont użytkowników od nadawcy lub adresatów adresów e-mail. Zazwyczaj można to zrobić dla adresu adresata lub nadawcy przy użyciu *hosta lokalnego z adresu e-mail* .

W poniższym fragmencie kodu używamy funkcji Kusto [tostring(),](/azure/data-explorer/kusto/query/tostringfunction) aby wyodrębnić hosta lokalnego tuż przed `@` adresem e-mail adresata w kolumnie `RecipientEmailAddress`.

```kusto
//Query snippet showing how to extract the account name from an email address
AccountName = tostring(split(RecipientEmailAddress, "@")[0])
```
Poniższe zapytanie pokazuje, jak można użyć tego fragmentu kodu:

```kusto
EmailEvents
| where Timestamp > ago(7d)
| project RecipientEmailAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
```

### <a name="merge-the-identityinfo-table"></a>Scalanie tabeli IdentityInfo

Nazwy kont i inne informacje o koncie można uzyskać, scalając lub dołączając [tabelę IdentityInfo](advanced-hunting-identityinfo-table.md). Poniższe zapytanie uzyskuje listę wykrywania wyłudzania informacji i złośliwego oprogramowania z [tabeli EmailEvents](advanced-hunting-emailevents-table.md) , a następnie dołącza te informacje do `IdentityInfo` tabeli, aby uzyskać szczegółowe informacje o każdym adresacie. 

```kusto
EmailEvents
| where Timestamp > ago(7d)
//Get email processing events where the messages were identified as either phishing or malware
| where ThreatTypes has "Malware" or ThreatTypes has "Phish"
//Merge email events with identity info to get recipient details
| join (IdentityInfo | distinct AccountUpn, AccountDisplayName, JobTitle, 
Department, City, Country) on $left.RecipientEmailAddress == $right.AccountUpn 
//Show important message and recipient details
| project Timestamp, NetworkMessageId, Subject, ThreatTypes, 
SenderFromAddress, RecipientEmailAddress, AccountDisplayName, JobTitle, 
Department, City, Country
```

Obejrzyj ten [krótki film wideo](https://www.youtube.com/watch?v=8qZx7Pp5XgM), aby dowiedzieć się, jak używać język zapytań Kusto do łączenia tabel.  

### <a name="get-device-information"></a>Pobieranie informacji o urządzeniu

[Zaawansowany schemat wyszukiwania zagrożeń](advanced-hunting-schema-tables.md) zawiera obszerne informacje o urządzeniu w różnych tabelach. Na przykład [tabela DeviceInfo](advanced-hunting-deviceinfo-table.md) zawiera kompleksowe informacje o urządzeniu na podstawie regularnie agregowanych danych zdarzeń. To zapytanie używa `DeviceInfo` tabeli, aby sprawdzić, czy potencjalnie naruszony użytkownik (`<account-name>`) zalogował się na dowolnych urządzeniach, a następnie wyświetla listę alertów, które zostały wyzwolone na tych urządzeniach.

>[!Tip]
> To zapytanie służy `kind=inner` do określania [sprzężenia wewnętrznego](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor), co zapobiega deduplikacji wartości po lewej stronie dla `DeviceId`elementu .

```kusto
DeviceInfo
//Query for devices that the potentially compromised account has logged onto
| where LoggedOnUsers contains '<account-name>'
| distinct DeviceId
//Crosscheck devices against alert records in AlertEvidence and AlertInfo tables
| join kind=inner AlertEvidence on DeviceId
| project AlertId
//List all alerts on devices that user has logged on to
| join AlertInfo on AlertId
| project AlertId, Timestamp, Title, Severity, Category 
```


### <a name="get-file-event-information"></a>Pobieranie informacji o zdarzeniu pliku

Użyj następującego zapytania, aby uzyskać informacje o zdarzeniach związanych z plikami. 

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceFileEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="get-network-event-information"></a>Uzyskiwanie informacji o zdarzeniach sieciowych

Użyj następującego zapytania, aby uzyskać informacje o zdarzeniach związanych z siecią.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-agent-version-information"></a>Pobieranie informacji o wersji agenta urządzenia

Użyj następującego zapytania, aby pobrać wersję agenta uruchomioną na urządzeniu.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="example-query-for-macos-devices"></a>Przykładowe zapytanie dotyczące urządzeń macOS

Użyj następującego przykładowego zapytania, aby wyświetlić wszystkie urządzenia z systemem macOS z wersją starszą niż Catalina.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OSPlatform == "macOS" and  OSVersion !contains "10.15" and OSVersion !contains "11."
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-status-info"></a>Pobieranie informacji o stanie urządzenia

Użyj następującego zapytania, aby uzyskać stan urządzenia. W poniższym przykładzie zapytanie sprawdza, czy urządzenie jest dołączone.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OnboardingStatus != "Onboarded"
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


## <a name="hunting-scenarios"></a>Scenariusze wyszukiwania zagrożeń

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>Wyświetlanie listy działań logowania użytkowników, którzy otrzymali wiadomości e-mail, które nie zostały pomyślnie zamapowane

[Automatyczne przeczyszczanie bez godziny (ZAP)](../office-365-security/zero-hour-auto-purge.md) adresuje złośliwe wiadomości e-mail po ich otrzymaniu. Jeśli zap nie powiedzie się, złośliwy kod może ostatecznie uruchomić na urządzeniu i pozostawić konta naruszone. To zapytanie sprawdza działanie logowania wykonane przez adresatów wiadomości e-mail, które nie zostały pomyślnie rozwiązane przez zap.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfully
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

### <a name="get-logon-attempts-by-domain-accounts-targeted-by-credential-theft"></a>Pobieranie prób logowania przez konta domeny objęte kradzieżą poświadczeń

To zapytanie najpierw identyfikuje wszystkie alerty dostępu do poświadczeń w `AlertInfo` tabeli. Następnie scala lub łączy tabelę `AlertEvidence` , która analizuje nazwy kont docelowych i filtry tylko dla kont przyłączonych do domeny. Na koniec sprawdza tabelę `IdentityLogonEvents` , aby uzyskać wszystkie działania logowania przez przyłączone do domeny konta docelowe.

```kusto
AlertInfo
| where Timestamp > ago(30d)
//Get all credential access alerts
| where Category == "CredentialAccess"
//Get more info from AlertEvidence table to get the SID of the target accounts
| join AlertEvidence on AlertId
| extend IsJoined=(parse_json(AdditionalFields).Account.IsDomainJoined)
| extend TargetAccountSid=tostring(parse_json(AdditionalFields).Account.Sid)
//Filter for domain-joined accounts only
| where IsJoined has "true"
//Merge with IdentityLogonEvents to get all logon attempts by the potentially compromised target accounts
| join kind=inner IdentityLogonEvents on $left.TargetAccountSid == $right.AccountSid
//Show only pertinent info, such as account name, the app or service, protocol, the accessed device, and type of logon
| project AccountDisplayName, TargetAccountSid, Application, Protocol, DeviceName, LogonType
```

### <a name="check-if-files-from-a-known-malicious-sender-are-on-your-devices"></a>Sprawdzanie, czy na urządzeniach znajdują się pliki od znanego złośliwego nadawcy

Zakładając, że znasz adres e-mail wysyłający złośliwe pliki (`MaliciousSender@example.com`), możesz uruchomić to zapytanie, aby ustalić, czy pliki tego nadawcy istnieją na urządzeniach. Za pomocą tego zapytania możesz na przykład zidentyfikować urządzenia, których dotyczy kampania dystrybucji złośliwego oprogramowania.

```kusto
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
//Get emails with attachments identified by a SHA-256
| where isnotempty(SHA256)
| join (
//Check devices for any activity involving the attachments
DeviceFileEvents
| project FileName, SHA256, DeviceName, DeviceId
) on SHA256
| project Timestamp, FileName , SHA256, DeviceName, DeviceId,  NetworkMessageId, SenderFromAddress, RecipientEmailAddress
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>Przeglądanie prób logowania po otrzymaniu złośliwych wiadomości e-mail

To zapytanie znajduje 10 najnowszych logowania wykonanych przez adresatów poczty e-mail w ciągu 30 minut od otrzymania znanych złośliwych wiadomości e-mail. To zapytanie umożliwia sprawdzenie, czy konta adresatów wiadomości e-mail zostały naruszone.

```kusto
//Define new table for malicious emails
let MaliciousEmails=EmailEvents
//List emails detected as malware, getting only pertinent columns
| where ThreatTypes has "Malware" 
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
MaliciousEmails
| join (
//Merge malicious emails with logon events to find logons by recipients
IdentityLogonEvents
| project LogonTime = Timestamp, AccountName, DeviceName
) on AccountName 
//Check only logons within 30 minutes of receipt of an email
| where (LogonTime - TimeEmail) between (0min.. 30min)
| take 10
```

### <a name="review-powershell-activities-after-receipt-of-emails-from-known-malicious-sender"></a>Przejrzyj działania programu PowerShell po otrzymaniu wiadomości e-mail od znanego złośliwego nadawcy

Złośliwe wiadomości e-mail często zawierają dokumenty i inne specjalnie spreparowane załączniki, które uruchamiają polecenia programu PowerShell w celu dostarczenia dodatkowych ładunków. Jeśli wiesz, że wiadomości e-mail pochodzą od znanego złośliwego nadawcy (`MaliciousSender@example.com`), możesz użyć tego zapytania do wyświetlenia listy i przejrzenia działań programu PowerShell, które wystąpiły w ciągu 30 minut po odebraniu wiadomości e-mail od nadawcy.  

```kusto
//Define new table for emails from specific sender
let EmailsFromBadSender=EmailEvents
| where SenderFromAddress =~ "MaliciousSender@example.com"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
//Merge emails from sender with process-related events on devices
EmailsFromBadSender
| join (
DeviceProcessEvents
//Look for PowerShell activity
| where FileName =~ "powershell.exe"
//Add line below to check only events initiated by Outlook
//| where InitiatingProcessParentFileName =~ "outlook.exe"
| project TimeProc = Timestamp, AccountName, DeviceName, InitiatingProcessParentFileName, InitiatingProcessFileName, FileName, ProcessCommandLine
) on AccountName 
//Check only PowerShell activities within 30 minutes of receipt of an email
| where (TimeProc - TimeEmail) between (0min.. 30min)
```

## <a name="related-topics"></a>Tematy pokrewne

- [Omówienie zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Nauka języka zapytań](advanced-hunting-query-language.md)
- [Praca z wynikami zapytań](advanced-hunting-query-results.md)
- [Używanie zapytań udostępnionych](advanced-hunting-shared-queries.md)
- [Analiza schematu](advanced-hunting-schema-tables.md)
- [Stosowanie najlepszych rozwiązań dla zapytań](advanced-hunting-best-practices.md)
