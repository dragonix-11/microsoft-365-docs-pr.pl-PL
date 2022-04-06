---
title: Klasyfikacja alertów dla podejrzanych reguł przekazywania skrzynki odbiorczej
description: Klasyfikacja alertów dla podejrzanych reguł przekazywania skrzynki odbiorczej w celu przejrzenia alertów i podjęcia zalecanych działań w celu skorygowania ataku i ochrony sieci.
keywords: zdarzenia, alerty, badanie, analizowanie, reagowanie, korelacja, atak, maszyny, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: dca305b88e6e8db25e0a798c4361086bd7cb1e8b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666025"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Klasyfikacja alertów dla podejrzanych reguł przekazywania skrzynki odbiorczej

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Aktorzy zagrożeń mogą używać kont użytkowników, których zabezpieczenia zostały naruszone, do kilku złośliwych celów, w tym do odczytywania wiadomości e-mail w skrzynce odbiorczej użytkownika, tworzenia reguł skrzynki odbiorczej w celu przekazywania wiadomości e-mail do kont zewnętrznych, wysyłania wiadomości wyłudzających informacje, między innymi. Złośliwe reguły skrzynki odbiorczej są powszechnie powszechne podczas kampanii wyłudzania informacji i naruszenia zabezpieczeń poczty e-mail w firmie i wyłudzania informacji. Ważne jest, aby stale je monitorować.

Ten podręcznik pomaga zbadać alerty pod kątem podejrzanych reguł przekazywania skrzynki odbiorczej i szybko ocenić je jako prawdziwie dodatnie (TP) lub fałszywie dodatnie (TP). Następnie możesz podjąć zalecane działania dla alertów TP w celu skorygowania ataku.

Aby zapoznać się z omówieniem klasyfikacji alertów dla Ochrona usługi Office 365 w usłudze Microsoft Defender i Microsoft Defender for Cloud Apps, zobacz [artykuł wprowadzający](alert-grading-playbooks.md).

Wyniki korzystania z tego podręcznika to:

- Alerty skojarzone z regułami przekazywania skrzynki odbiorczej zostały zidentyfikowane jako działania złośliwe (TP) lub niegroźne (FP).

  W przypadku złośliwego działania usunięto złośliwe reguły przekazywania skrzynki odbiorczej.

- Podjęto niezbędne działania, jeśli wiadomości e-mail zostały przekazane na złośliwy adres e-mail.

## <a name="inbox-forwarding-rules"></a>Reguły przekazywania skrzynki odbiorczej

Reguły skrzynki odbiorczej można skonfigurować do automatycznego zarządzania wiadomościami e-mail na podstawie wstępnie zdefiniowanych kryteriów. Możesz na przykład utworzyć regułę skrzynki odbiorczej, aby przenieść wszystkie komunikaty z menedżera do innego folderu lub przekazać wiadomości otrzymane na inny adres e-mail.

### <a name="suspicious-inbox-forwarding-rules"></a>Podejrzane reguły przesyłania dalej w skrzynce odbiorczej

Po uzyskaniu dostępu do skrzynek pocztowych użytkowników osoby atakujące często tworzą regułę skrzynki odbiorczej, która umożliwia im eksfiltrację poufnych danych na zewnętrzny adres e-mail i używanie ich do złośliwych celów.

Złośliwe reguły skrzynki odbiorczej automatyzują proces eksfiltracji. W przypadku określonych reguł każda wiadomość e-mail w skrzynce odbiorczej użytkownika docelowego zgodna z kryteriami reguły zostanie przekazana do skrzynki pocztowej osoby atakującej. Na przykład osoba atakująca może chcieć zebrać poufne dane związane z finansami. Tworzą regułę skrzynki odbiorczej, aby przekazywać wszystkie wiadomości e-mail zawierające słowa kluczowe, takie jak "finanse" i "faktura" w treści tematu lub wiadomości, do skrzynki pocztowej.

Podejrzane reguły przekazywania skrzynki odbiorczej mogą być bardzo trudne do wykrycia, ponieważ konserwacja reguł skrzynki odbiorczej jest typowym zadaniem wykonywanym przez użytkowników. Dlatego ważne jest, aby monitorować alerty.

## <a name="workflow"></a>Przepływu pracy

Oto przepływ pracy umożliwiający zidentyfikowanie podejrzanych reguł przekazywania wiadomości e-mail.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Przepływ pracy badania alertów dla reguł przekazywania skrzynki odbiorczej" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>Kroki badania

Ta sekcja zawiera szczegółowe wskazówki krok po kroku dotyczące reagowania na zdarzenie i wykonania zalecanych kroków w celu ochrony organizacji przed dalszymi atakami.

### <a name="review-generated-alerts"></a>Przejrzyj wygenerowane alerty

Oto przykład alertu reguły przekazywania skrzynki odbiorczej w kolejce alertów.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Przykład powiadomienia w kolejce alertów" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

Oto przykład szczegółów alertu, który został wyzwolony przez złośliwą regułę przekazywania skrzynki odbiorczej.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Szczegóły alertu, który został wyzwolony przez złośliwą regułę przekazywania skrzynki odbiorczej" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Badanie parametrów reguły

Celem tego etapu jest ustalenie, czy reguły wyglądają podejrzanie według określonych kryteriów:

Adresaci reguły przesyłania dalej:

- Sprawdź, czy docelowy adres e-mail nie jest dodatkową skrzynką pocztową należącą do tego samego użytkownika (unikając przypadków, w których użytkownik samodzielnie przekazuje wiadomości e-mail między osobistymi skrzynkami pocztowymi).
- Sprawdź, czy docelowy adres e-mail nie jest adresem wewnętrznym ani poddomeną należącą do firmy.

Filtry:

- Jeśli reguła skrzynki odbiorczej zawiera filtry, które wyszukują określone słowa kluczowe w temacie lub treści wiadomości e-mail, sprawdź między innymi, czy podane słowa kluczowe, takie jak finanse, poświadczenia i sieć, wydają się być związane ze złośliwym działaniem. Te filtry można znaleźć w następujących atrybutach (które są wyświetlane w kolumnie RawEventData zdarzeń): "BodyContainsWords", "SubjectContainsWords" lub "SubjectOrBodyContainsWords"
- Jeśli atakujący zdecyduje się nie ustawiać żadnego filtru na wiadomości e-mail, a zamiast tego reguła skrzynki odbiorczej przekazuje wszystkie elementy skrzynki pocztowej do skrzynki pocztowej osoby atakującej), takie zachowanie również jest podejrzane.

### <a name="investigate-ip-address"></a>Badanie adresu IP

Przejrzyj atrybuty związane z adresem IP, który wykonał odpowiednie zdarzenie tworzenia reguły:

1. Wyszukaj inne podejrzane działania w chmurze pochodzące z tego samego adresu IP w dzierżawie. Na przykład podejrzane działanie może być wieloma nieudanymi próbami logowania.
2. Czy usługodawca jest typowy i rozsądny dla tego użytkownika?
3. Czy lokalizacja jest wspólna i rozsądna dla tego użytkownika?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Badanie wszelkich podejrzanych działań przy użyciu skrzynki odbiorczej użytkownika przed utworzeniem reguł

Przed utworzeniem reguł możesz przejrzeć wszystkie działania użytkowników, sprawdzić wskaźniki naruszenia zabezpieczeń i zbadać akcje użytkowników, które wydają się podejrzane. Na przykład wiele nieudanych logowań.

- Logowania:

  Sprawdź, czy działanie logowania przed zdarzeniem tworzenia reguły nie jest podejrzane (np. wspólna lokalizacja, usługodawca sieciowy lub agent użytkownika).

- Inne alerty lub zdarzenia
  - Czy inne alerty zostały wyzwolone dla użytkownika przed utworzeniem reguły. Jeśli tak, może to oznaczać, że użytkownik został naruszona.
  - Jeśli alert jest skorelowany z innymi alertami wskazującymi zdarzenie, to czy zdarzenie zawiera inne prawdziwie dodatnie alerty?

## <a name="advanced-hunting-queries"></a>Zaawansowane zapytania dotyczące wyszukiwania zagrożeń

[Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md) to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które umożliwia inspekcję zdarzeń w sieci i lokalizowanie wskaźników zagrożeń.

Uruchom to zapytanie, aby znaleźć wszystkie nowe zdarzenia reguł skrzynki odbiorczej w określonym przedziale czasu.

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

*Polecenie RuleConfig* będzie zawierać konfigurację reguły.

Uruchom to zapytanie, aby sprawdzić, czy usługodawca jest typowy dla użytkownika, przeglądając historię użytkownika.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Uruchom to zapytanie, aby sprawdzić, czy kraj jest typowy dla użytkownika, przeglądając historię użytkownika.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Uruchom to zapytanie, aby sprawdzić, czy agent-użytkownik jest typowy dla użytkownika, przeglądając historię użytkownika.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Uruchom to zapytanie, aby sprawdzić, czy inni użytkownicy utworzą regułę przekazywania do tego samego miejsca docelowego (może to oznaczać, że inni użytkownicy również są narażeni na naruszenia zabezpieczeń).

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
2. Zresetuj poświadczenia konta użytkownika. Możesz również sprawdzić, czy bezpieczeństwo konta użytkownika zostało naruszone za pomocą Microsoft Defender for Cloud Apps, który pobiera sygnały zabezpieczeń z usługi Azure Active Directory (Azure AD) Identity Protection.
3. Wyszukaj inne złośliwe działania wykonywane przez użytkownika, na który ma to wpływ.
4. Sprawdź inne podejrzane działania w dzierżawie pochodzące z tego samego adresu IP lub z tego samego usługodawcy sieciowego (jeśli usługodawca sieciowy jest nietypowy), aby znaleźć innych użytkowników, których bezpieczeństwo zostało naruszone.

## <a name="see-also"></a>Zobacz też

- [Omówienie klasyfikacji alertów](alert-grading-playbooks.md)
- [Podejrzane działania w zakresie przesyłania dalej wiadomości e-mail](alert-grading-playbook-email-forwarding.md)
- [Podejrzane reguły manipulowania skrzynką odbiorczą](alert-grading-playbook-inbox-manipulation-rules.md)
- [Badaj alerty](investigate-alerts.md)
