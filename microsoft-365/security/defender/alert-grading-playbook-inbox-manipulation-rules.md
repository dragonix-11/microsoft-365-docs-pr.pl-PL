---
title: Klasyfikacja alertów dla reguł manipulowania podejrzaną skrzynką odbiorczą
description: Klasyfikacja alertów dla reguł podejrzanej manipulacji skrzynką odbiorczą w celu przejrzenia alertów i podjęcia zalecanych działań w celu skorygowania ataku i ochrony sieci.
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
ms.openlocfilehash: e663d02037633599b9dffc19e1ebbd174aa279e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663187"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Klasyfikacja alertów dla reguł manipulowania podejrzaną skrzynką odbiorczą

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Aktorzy zagrożeń mogą używać kont użytkowników, których zabezpieczenia zostały naruszone, do wielu złośliwych celów, w tym do odczytywania wiadomości e-mail w skrzynce odbiorczej użytkownika, tworzenia reguł skrzynki odbiorczej w celu przekazywania wiadomości e-mail do kont zewnętrznych, usuwania śladów i wysyłania wiadomości wyłudzających informacje. Złośliwe reguły skrzynki odbiorczej są powszechne podczas biznesowych naruszeń zabezpieczeń poczty e-mail i kampanii wyłudzania informacji i ważne jest, aby stale je monitorować.

Ten podręcznik pomaga zbadać wszelkie zdarzenia związane z podejrzanymi regułami manipulowania skrzynką odbiorczą skonfigurowanymi przez osoby atakujące i podjąć zalecane działania w celu skorygowania ataku i ochrony sieci. Ten podręcznik jest przeznaczony dla zespołów zabezpieczeń, w tym analityków centrum operacji zabezpieczeń (SOC) i administratorów IT, którzy przeglądają, badają i oceniają alerty. Alerty można szybko ocenić jako prawdziwie dodatnie (TP) lub fałszywie dodatnie (TP) i podjąć zalecane działania dla alertów TP w celu skorygowania ataku.

Wyniki korzystania z tego podręcznika to:

- Alerty skojarzone z regułami manipulowania skrzynką odbiorczą zostały zidentyfikowane jako złośliwe działania (TP) lub niegroźne (FP).

  W przypadku złośliwego działania usunięto złośliwe reguły manipulowania skrzynką odbiorczą.

- Podjęto niezbędne działania, jeśli wiadomości e-mail zostały przekazane na złośliwy adres e-mail.

## <a name="inbox-manipulation-rules"></a>Reguły manipulowania skrzynką odbiorczą

Reguły skrzynki odbiorczej są ustawiane tak, aby automatycznie zarządzały wiadomościami e-mail na podstawie wstępnie zdefiniowanych kryteriów. Możesz na przykład utworzyć regułę skrzynki odbiorczej, aby przenieść wszystkie komunikaty z menedżera do innego folderu lub przekazać wiadomości otrzymane na inny adres e-mail.

### <a name="malicious-inbox-manipulation-rules"></a>Złośliwe reguły manipulowania skrzynką odbiorczą

Osoby atakujące mogą skonfigurować reguły poczty e-mail, aby ukryć przychodzące wiadomości e-mail w skrzynce pocztowej użytkownika, których bezpieczeństwo zostało naruszone, aby ukryć złośliwe działania użytkownika. Mogą również ustawić reguły w skrzynce pocztowej użytkownika, których zabezpieczenia zostały naruszone, aby usuwać wiadomości e-mail, przenosić wiadomości e-mail do innego mniej zauważalnego folderu (takiego jak RSS) lub przekazywać wiadomości e-mail do konta zewnętrznego. Niektóre reguły mogą przenosić wszystkie wiadomości e-mail do innego folderu i oznaczać je jako "przeczytane", podczas gdy niektóre reguły mogą przenosić tylko wiadomości zawierające określone słowa kluczowe w wiadomości e-mail lub temacie.

Na przykład regułę skrzynki odbiorczej można ustawić tak, aby wyszukiwała słowa kluczowe, takie jak "faktura", "phish", "nie odpowiadaj", "podejrzana wiadomość e-mail" lub "spam" między innymi, i przenosiła je na zewnętrzne konto e-mail. Osoby atakujące mogą również używać skrzynki pocztowej użytkownika, którego zabezpieczenia zostały naruszone, do rozpowszechniania spamu, wiadomości e-mail wyłudzających informacje lub złośliwego oprogramowania.

## <a name="workflow"></a>Przepływu pracy

Oto przepływ pracy umożliwiający zidentyfikowanie podejrzanych działań reguł manipulowania skrzynką odbiorczą.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Przepływ pracy badania alertów dla reguł manipulowania skrzynką odbiorczą" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::

## <a name="investigation-steps"></a>Kroki badania

Ta sekcja zawiera szczegółowe wskazówki krok po kroku dotyczące reagowania na zdarzenie i wykonania zalecanych kroków w celu ochrony organizacji przed dalszymi atakami.

### <a name="1-review-the-alerts"></a>1. Przejrzyj alerty

Oto przykład alertu reguły manipulowania skrzynką odbiorczą w kolejce alertów.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Przykład reguły manipulowania skrzynką odbiorczą" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

Oto przykład szczegółów alertu, który został wyzwolony przez złośliwą regułę manipulowania skrzynką odbiorczą.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Szczegóły alertu, który został wyzwolony przez złośliwą regułę manipulowania skrzynką odbiorczą" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::

### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Badanie parametrów reguły manipulowania skrzynką odbiorczą

Ustal, czy reguły wyglądają podejrzanie zgodnie z następującymi parametrami lub kryteriami reguły:

- Słowa kluczowe

   Osoba atakująca może zastosować regułę manipulacji tylko do wiadomości e-mail zawierających określone słowa. Słowa kluczowe można znaleźć w niektórych atrybutach, takich jak: "BodyContainsWords", "SubjectContainsWords" lub "SubjectOrBodyContainsWords".

   Jeśli istnieją filtrowanie według słów kluczowych, sprawdź, czy słowa kluczowe wydają się podejrzane (typowe scenariusze to filtrowanie wiadomości e-mail związanych z działaniami osoby atakującej, takich jak "phish", "spam", "nie odpowiadaj" między innymi).

   Jeśli nie ma żadnego filtru, może to być również podejrzane.

- Folder docelowy

   Aby uniknąć wykrywania zabezpieczeń, osoba atakująca może przenieść wiadomości e-mail do mniej zauważalnego folderu i oznaczyć wiadomości e-mail jako przeczytane (na przykład folder "RSS"). Jeśli osoba atakująca zastosuje akcję "MoveToFolder" i "MarkAsRead", sprawdź, czy folder docelowy jest w jakiś sposób powiązany ze słowami kluczowymi w regule, aby zdecydować, czy wydaje się to podejrzane.

- Usuń wszystko

   Niektórzy atakujący po prostu usunie wszystkie przychodzące wiadomości e-mail, aby ukryć swoją aktywność. Przeważnie reguła "usuń wszystkie przychodzące wiadomości e-mail" bez filtrowania ich za pomocą słów kluczowych jest wskaźnikiem złośliwego działania.

Oto przykład konfiguracji reguły "usuń wszystkie przychodzące wiadomości e-mail" (jak pokazano w pliku RawEventData.Parameters) odpowiedniego dziennika zdarzeń.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Przykład konfiguracji reguły usuwania wszystkich przychodzących wiadomości e-mail" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::

### <a name="3-investigate-the-ip-address"></a>3. Zbadaj adres IP

Przejrzyj atrybuty adresu IP, który wykonał odpowiednie zdarzenie tworzenia reguły:

- Wyszukaj inne podejrzane działania w chmurze pochodzące z tego samego adresu IP w dzierżawie. Na przykład podejrzane działania mogą być wieloma nieudanymi próbami logowania.
- Czy usługodawca jest typowy i rozsądny dla tego użytkownika?
- Czy lokalizacja jest wspólna i rozsądna dla tego użytkownika?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Badanie podejrzanych działań użytkownika przed utworzeniem reguł

Możesz przejrzeć wszystkie działania użytkowników przed utworzeniem reguł, sprawdzić wskaźniki naruszenia zabezpieczeń i zbadać akcje użytkownika, które wydają się podejrzane.

Na przykład w przypadku wielu nieudanych logowań sprawdź:

- Działanie logowania

   Sprawdź, czy działanie logowania przed utworzeniem reguły nie jest podejrzane. (wspólna lokalizacja / usługodawca sieciowy / użytkownik-agent).

- Alerty

   Sprawdź, czy użytkownik otrzymał alerty przed utworzeniem reguł. Może to wskazywać, że konto użytkownika może zostać naruszone. Na przykład alert o niemożliwej podróży, rzadki kraj, wiele nieudanych logowań, między innymi).

- Incydent

   Sprawdź, czy alert jest skojarzony z innymi alertami wskazującymi zdarzenie. Jeśli tak, sprawdź, czy zdarzenie zawiera inne prawdziwie dodatnie alerty.

## <a name="advanced-hunting-queries"></a>Zaawansowane zapytania dotyczące wyszukiwania zagrożeń

[Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md) to narzędzie do wyszukiwania zagrożeń oparte na zapytaniach, które umożliwia inspekcję zdarzeń w sieci w celu zlokalizowania wskaźników zagrożeń.

Użyj tego zapytania, aby znaleźć wszystkie nowe zdarzenia reguł skrzynki odbiorczej w określonym przedziale czasu.

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

Kolumna *RuleConfig* zawiera nową konfigurację reguły skrzynki odbiorczej.

Użyj tego zapytania, aby sprawdzić, czy usługodawca jest typowy dla użytkownika, przeglądając historię użytkownika.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Użyj tego zapytania, aby sprawdzić, czy kraj jest typowy dla użytkownika, przeglądając historię użytkownika.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Użyj tego zapytania, aby sprawdzić, czy agent użytkownika jest typowy dla użytkownika, przeglądając historię użytkownika.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

## <a name="recommended-actions"></a>Zalecane akcje

1. Wyłącz regułę złośliwej skrzynki odbiorczej.
2. Zresetuj poświadczenia konta użytkownika. Możesz również sprawdzić, czy bezpieczeństwo konta użytkownika zostało naruszone za pomocą Microsoft Defender for Cloud Apps, który pobiera sygnały zabezpieczeń z usługi Azure Active Directory (Azure AD) Identity Protection.
3. Wyszukaj inne złośliwe działania wykonywane przez konto użytkownika, na które ma to wpływ.
4. Sprawdź inne podejrzane działania w dzierżawie, które pochodzą z tego samego adresu IP lub z tego samego usługodawcy sieciowego (jeśli usługodawca sieciowy jest nietypowy), aby znaleźć inne konta użytkowników, których bezpieczeństwo zostało naruszone.

## <a name="see-also"></a>Zobacz też

- [Omówienie klasyfikacji alertów](alert-grading-playbooks.md)
- [Podejrzane działania w zakresie przesyłania dalej wiadomości e-mail](alert-grading-playbook-email-forwarding.md)
- [Podejrzane reguły przesyłania dalej w skrzynce odbiorczej](alert-grading-playbook-inbox-forwarding-rules.md)
- [Badaj alerty](investigate-alerts.md)
