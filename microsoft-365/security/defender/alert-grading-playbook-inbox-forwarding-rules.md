---
title: Ocenianie alertów dla podejrzanych reguł przesyłania dalej skrzynki odbiorczej
description: Ocenianie alertów dla podejrzanych reguł przesyłania dalej skrzynki odbiorczej w celu przejrzenia alertów i podjęcia zalecanych działań w celu podjęcia działań naprawczych w przypadku ataków i ochrony sieci.
keywords: zdarzenia, alerty, badanie, analizowanie, odpowiedź, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: dee9c4a51175f9fbeac8b6d21f29490081258ba0
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "62974144"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Ocenianie alertów dla podejrzanych reguł przesyłania dalej skrzynki odbiorczej

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Zagrożenie może korzystać z naruszonych kont użytkowników do kilku złośliwych celów, takich jak odczytywanie wiadomości e-mail w skrzynce odbiorczej użytkownika, tworzenie reguł skrzynki odbiorczej w celu przesyłania dalej wiadomości e-mail na konta zewnętrzne, wysyłanie wiadomości wyłudzających informacje, między innymi. Złośliwe reguły skrzynki odbiorczej są powszechnie stosowane podczas biznesowych kampanii dotyczących naruszenia bezpieczeństwa poczty e-mail i wyłudzania informacji, dlatego ważne jest ich spójne monitorowanie.

Ten podręcznik ułatwia badanie alertów dla podejrzanych reguł przesyłania dalej skrzynek odbiorczych i szybkie ocenianie ich jako prawdziwego dodatniego (TP) lub wyników fałszywie dodatnich (TP). Następnie możesz podjąć zalecane działania dla alertów TP, aby rozwiązać ten atak. 

Aby uzyskać omówienie oceny alertów dla programu Microsoft Defender dla programu Office 365 i programu Microsoft Defender dla aplikacji w chmurze, zobacz [artykuł wprowadzający](alert-grading-playbooks.md).

Wyniki korzystania z tego podręcznika są takie:

- Alerty skojarzone z regułami przesyłania dalej skrzynki odbiorczej zostały zidentyfikowane jako złośliwe (TP) lub szmurzone (FP).

  W przypadku złośliwego działania usunięto reguły przesyłania dalej ze złośliwą skrzynką odbiorczą.

- Jeśli wiadomości e-mail zostały przekazane na złośliwy adres e-mail, zostały wykonane odpowiednie czynności.

## <a name="inbox-forwarding-rules"></a>Reguły przesyłania dalej skrzynki odbiorczej

Reguły skrzynki odbiorczej konfiguruje się w taki sposób, aby automatycznie zarządzać wiadomościami e-mail na podstawie wstępnie zdefiniowanych kryteriów. Możesz na przykład utworzyć regułę skrzynki odbiorczej w celu przenoszenia wszystkich wiadomości od menedżera do innego folderu lub przesyłania dalej odebranych wiadomości na inny adres e-mail.

### <a name="suspicious-inbox-forwarding-rules"></a>Podejrzane reguły przesyłania dalej skrzynki odbiorczej

Po uzyskaniu dostępu do skrzynek pocztowych użytkowników atakujący często tworzą regułę skrzynki odbiorczej umożliwiającą im eksfiltrowanie poufnych danych na zewnętrzny adres e-mail i używanie ich w złośliwych celach. 

Złośliwe reguły skrzynki odbiorczej automatyzują proces wykrzyknika. W przypadku określonych reguł każda wiadomość e-mail spełniająca kryteria reguły w skrzynce odbiorczej użytkownika docelowego jest przesyłana do skrzynki pocztowej atakującego. Na przykład atakujący może chcieć zebrać poufne dane związane z finansami. Tworzą regułę skrzynki odbiorczej, aby przesyłać dalej do swoich skrzynek pocztowych wszystkie wiadomości e-mail zawierające słowa kluczowe, takie jak "finanse" i "faktura" w temacie lub treści wiadomości.

Podejrzane reguły przesyłania dalej skrzynki odbiorczej mogą być bardzo trudne do wykrycia, ponieważ konserwacja reguł skrzynki odbiorczej jest często wykonywana przez użytkowników. Dlatego należy monitorować alerty. 

## <a name="workflow"></a>Przepływ pracy

Oto przepływ pracy do identyfikowania podejrzanych reguł przesyłania dalej wiadomości e-mail.
 
:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Przepływ pracy badania alertu dla reguł przesyłania dalej skrzynki odbiorczej" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>Kroki badania

Ta sekcja zawiera szczegółowe instrukcje dotyczące reagowania na incydenty, a także kroki zalecane w celu ochrony organizacji przed dalszymi atakami.

### <a name="review-generated-alerts"></a>Przeglądanie wygenerowanych alertów

Oto przykład alertu reguły przesyłania dalej skrzynki odbiorczej w kolejce alertu.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Przykład powiadomienia w kolejce alertów" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

Oto przykładowe szczegóły alertu, który został wyzwolony przez regułę przesyłania dalej złośliwej skrzynki odbiorczej.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Szczegóły alertu wyzwolone przez regułę przesyłania dalej złośliwej skrzynki odbiorczej" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Badanie parametrów reguły 

Celem tego etapu jest ustalenie, czy reguły wyglądają podejrzanie na podstawie określonych kryteriów:

Adresaci reguły przesyłania dalej:

- Sprawdź, czy docelowy adres e-mail nie jest dodatkową skrzynką pocztową należącą do tego samego użytkownika (unikanie przypadków, w których użytkownik samodzielnie przesyła wiadomości e-mail między osobistymi skrzynkami pocztowymi). 
- Sprawdź, czy docelowy adres e-mail nie jest adresem wewnętrznym ani poddomeną należącą do firmy.

Filtry:
 
- Jeśli reguła skrzynki odbiorczej zawiera filtry wyszukające określone słowa kluczowe w temacie lub treści wiadomości e-mail, sprawdź, czy podane słowa kluczowe, takie jak finanse, poświadczenia i sieci, nie wydają się związane ze złośliwą aktywnością. Filtry te znajdują się w następujących atrybutach (co jest widać w kolumnie zdarzenia RawEventData): "BodyContainsWords", "SubjectContainsWords" lub "SubjectOrBodyContainsWords"
- Jeśli atakujący zdecyduje się nie ustawiać żadnego filtru dla poczty, a zamiast tego reguła skrzynki odbiorczej przesyła wszystkie elementy skrzynki pocztowej do skrzynki pocztowej atakującego, takie zachowanie również jest podejrzane. 

### <a name="investigate-ip-address"></a>Badanie adresu IP

Przejrzyj atrybuty związane z adresem IP, który wykonał istotne zdarzenie związane z tworzeniem reguł:

1. Wyszukaj inne podejrzane działania w chmurze pochodzące z tego samego adresu IP w dzierżawie. Podejrzane działanie może na przykład wymagać wielu nieudanych prób logowania. 
2. Czy ten użytkownik jest wspólnym i rozsądnym użytkownikiem u każdego z tych użytkowników?
3. Czy lokalizacja jest wspólna i rozsądna dla tego użytkownika?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Badanie podejrzanych działań ze skrzynką odbiorczą użytkownika przed utworzeniem reguł

Możesz przeglądać wszystkie działania użytkowników przed utworzeniem reguł, sprawdzać wskaźniki naruszenia i badać działania użytkowników, które wydają się podejrzane. Na przykład wiele nieudanych logowania.  

- Logowanie: 

  Sprawdź, czy działanie logowania przed zdarzeniem tworzenia reguły nie jest podejrzane (na przykład wspólna lokalizacja, isp lub agent użytkownika). 

- Inne alerty lub zdarzenia 

   - Czy przed utworzeniem reguły dla użytkownika wyzwolą inne alerty. Jeśli tak, może to oznaczać, że użytkownik został naruszony. 

   - Jeśli alert jest skorelowany z innymi alertami w celu wskazania zdarzenia, czy zdarzenie zawiera inne prawdziwe alerty dodatnie? 

## <a name="advanced-hunting-queries"></a>Zaawansowane zapytania myśliwskie

[Zaawansowane wyszukiwania to](advanced-hunting-overview.md) oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które umożliwia sprawdzanie zdarzeń w sieci i lokalizowanie wskaźników zagrożeń. 

Uruchom to zapytanie, aby znaleźć wszystkie nowe zdarzenia reguły skrzynki odbiorczej w określonym oknie czasu.  

```kusto
let start_date = now(-10h); 
let end_date = now();
let user_id = ""; // enter here the user id
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where AccountObjectId == user_id
| where Application == @"Microsoft Exchange Online"
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
```

*Konfiguracja reguły* będzie zawierać konfigurację reguły.

Uruchom to zapytanie, aby sprawdzić, czy jest to popularne dla użytkownika przez zapytanie w historii użytkownika.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Uruchom to zapytanie, aby sprawdzić, czy kraj jest wspólny dla użytkownika, patrząc na historię użytkownika.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Uruchom to zapytanie, aby sprawdzić, czy agent użytkownika jest wspólny dla użytkownika, patrząc na historię użytkownika.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Uruchom to zapytanie, aby sprawdzić, czy inni użytkownicy tworzyli regułę przesyłania dalej do tego samego miejsca docelowego (może to wskazywać, że inni użytkownicy także są naruszoni).

```kusto
let start_date = now(-10h); 
let end_date = now();
let dest_email = ""; // enter here destination email as seen in the alert
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
| where RuleConfig has dest_email
```

## <a name="recommended-actions"></a>Zalecane akcje

1. Wyłącz regułę złośliwej skrzynki odbiorczej. 
2. Zresetuj poświadczenia konta użytkownika. Możesz także sprawdzić, czy konto użytkownika zostało naruszone przez program Microsoft Defender for Cloud Apps, co jest sygnałem zabezpieczeń z usługi Azure Active Directory (Azure AD) Identity Protection.
3. Wyszukaj inne złośliwe działania wykonywane przez użytkownika, u których ten wpływ ma wpływ.
4. Aby znaleźć innych naruszonych użytkowników, sprawdź, czy w dzierżawie nie ma podejrzanych działań pochodzących od tego samego adresu IP lub od tego samego internetowego (o ile ten sam użytkownik jest nietypowy).

## <a name="see-also"></a>Zobacz też

- [Omówienie oceny alertów](alert-grading-playbooks.md)
- [Podejrzane działania w zakresie przesyłania dalej poczty e-mail](alert-grading-playbook-email-forwarding.md)
- [Podejrzane reguły manipulowania skrzynką odbiorczą](alert-grading-playbook-inbox-manipulation-rules.md)
- [Badanie alertów](investigate-alerts.md)
