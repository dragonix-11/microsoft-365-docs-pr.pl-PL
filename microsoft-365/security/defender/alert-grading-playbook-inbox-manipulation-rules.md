---
title: Ocenianie alertów dotyczących podejrzanych reguł manipulowania skrzynką odbiorczą
description: Ocenianie alertów w przypadku podejrzanych reguł manipulowania skrzynką odbiorczą w celu przejrzenia alertów i podjęcia zalecanych działań w celu podjęcia działań naprawczych po atakach i ochrony sieci.
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
ms.openlocfilehash: e1bfb37ebf88ffd67a7fcfaddde46141583fb717
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "62974141"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Ocenianie alertów dotyczących podejrzanych reguł manipulowania skrzynką odbiorczą

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Zagrożenie może korzystać z naruszonych kont użytkowników do wielu złośliwych celów, takich jak czytanie wiadomości e-mail w skrzynce odbiorczej użytkownika, tworzenie reguł skrzynki odbiorczej w celu przesyłania dalej wiadomości e-mail na konta zewnętrzne, usuwanie śladów i wysyłanie wiadomości wyłudzających informacje. Złośliwe reguły skrzynki odbiorczej są typowe w przypadku biznesowych kampanii w celu naruszenia zabezpieczeń poczty e-mail i wyłudzania informacji, dlatego ważne jest, aby stale je monitorować. 

Ten podręcznik ułatwia badanie wszelkich zdarzeń związanych z podejrzanymi regułami manipulowania skrzynkami odbiorczymi skonfigurowanymi przez atakujących oraz działania zalecane w celu korygowania ataków i ochrony sieci użytkownika. Ten podręcznik jest dla zespołów ds. zabezpieczeń, w tym analityków SOC (Security Operations Center) i administratorów IT, którzy przeglądają, analizują i oceniają alerty. Możesz szybko oceniać alerty jako prawdziwe dodatnie (TP) lub false positive (TP) i podjąć zalecane działania dla alertów TP, aby rozwiązać ten atak. 

Wyniki korzystania z tego podręcznika są takie:

- Zidentyfikowaliśmy alerty skojarzone z regułami manipulowania skrzynką odbiorczą jako złośliwe (TP) lub działania skojarzeń (FP).

  W przypadku złośliwego pliku usunięto reguły manipulowania złośliwymi skrzynkami odbiorczymi.

- Jeśli wiadomości e-mail zostały przekazane na złośliwy adres e-mail, zostały wykonane odpowiednie czynności.

## <a name="inbox-manipulation-rules"></a>Reguły manipulowania skrzynką odbiorczą

Reguły skrzynki odbiorczej są ustawione tak, aby automatycznie zarządzać wiadomościami e-mail na podstawie wstępnie zdefiniowanych kryteriów. Możesz na przykład utworzyć regułę skrzynki odbiorczej w celu przenoszenia wszystkich wiadomości od menedżera do innego folderu lub przesyłania dalej odebranych wiadomości na inny adres e-mail.

### <a name="malicious-inbox-manipulation-rules"></a>Reguły manipulowania złośliwymi skrzynkami odbiorczymi

Atakujący mogą skonfigurować reguły wiadomości e-mail w celu ukrywania przychodzących wiadomości e-mail w naruszonej skrzynce pocztowej użytkownika w celu przesłania ich złośliwych działań przed użytkownikiem. Ponadto mogą ustawiać reguły w naruszonej skrzynce pocztowej użytkownika w celu usuwania wiadomości e-mail, przenoszenia wiadomości e-mail do innego mniej zauważalnego folderu (na przykład RSS) lub przesyłania poczty dalej na konto zewnętrzne. Niektóre reguły mogą przenosić wszystkie wiadomości e-mail do innego folderu i oznaczać je jako "przeczytane", natomiast niektóre reguły mogą przenosić tylko wiadomości zawierające określone słowa kluczowe w wiadomości e-mail lub temacie. 

Na przykład regułę skrzynki odbiorczej można skonfigurować tak, aby między innymi wyszukiwała słowa kluczowe, takie jak "faktura", "wyłudzać", "nie odpowiadaj", "podejrzane wiadomości e-mail" lub "spam" i przenosić je na zewnętrzne konto e-mail. Atakujący mogą też rozpowszechniać spam, wiadomości e-mail służące do wyłudzania informacji lub złośliwe oprogramowanie, co może wymagać wykorzystania naruszonej skrzynki pocztowej użytkownika. 

## <a name="workflow"></a>Przepływ pracy

Oto przepływ pracy do identyfikowania podejrzanych działań w ramach reguły manipulowania skrzynką odbiorczą.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Przepływ pracy badania alertu dla reguł manipulowania skrzynką odbiorczą" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::


## <a name="investigation-steps"></a>Kroki badania

Ta sekcja zawiera szczegółowe instrukcje dotyczące reagowania na incydenty, a także kroki zalecane w celu ochrony organizacji przed dalszymi atakami.

### <a name="1-review-the-alerts"></a>1. Przeglądanie alertów

Oto przykład alertu reguły manipulowania skrzynką odbiorczą w kolejce alertów.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Przykład reguły manipulowania skrzynką odbiorczą" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

Oto przykładowe szczegóły alertu, który został wyzwolony przez regułę manipulowania złośliwą skrzynką odbiorczą.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Szczegóły alertu wyzwolone przez regułę manipulowania złośliwą skrzynką odbiorczą" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::


### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Badanie parametrów reguły manipulowania skrzynką odbiorczą 

Określ, czy reguły wyglądają podejrzanie, zgodnie z następującymi parametrami lub kryteriami reguły:

- Słowa kluczowe

   Atakujący może stosować regułę manipulowania wyłącznie do wiadomości e-mail z określonymi wyrazami. Te słowa kluczowe można znaleźć w pewnych atrybutach, takich jak: "BodyContainsWords", "SubjectContainsWords" lub "SubjectOrBodyContainsWords". 

   Jeśli istnieją filtry według słów kluczowych, sprawdź, czy słowa kluczowe wyglądają podejrzanie (typowe scenariusze to filtrowanie wiadomości e-mail związanych z działaniami atakujących, takimi jak "wyłudzy", "spam", "nie odpowiadaj".

   Jeśli filtr nie jest filtrowany, może być również podejrzany.

- Folder docelowy

   Aby uniknąć wykrywania zabezpieczeń, atakujący może przenieść te wiadomości do mniej zauważalnego folderu i oznaczać te wiadomości jako przeczytane (na przykład do folderu "RSS"). Jeśli atakujący stosuje akcje "MoveToFolder" i "MarkAsRead", sprawdź, czy folder docelowy jest w jakiś sposób powiązany ze słowami kluczowymi w  reguły, aby zdecydować, czy wydaje się podejrzany, czy nie. 

- Usuń wszystko

   Niektórzy atakujący usuną tylko wszystkie przychodzące wiadomości e-mail, aby ukryć ich aktywność. Na ogół reguła "usuń wszystkie przychodzące wiadomości e-mail" bez filtrowania ich za pomocą słów kluczowych jest wskaźnikiem złośliwej aktywności. 
 
Oto przykład konfiguracji reguły "usuń wszystkie przychodzące wiadomości e-mail" (jak w przypadku rawEventData.Parameters) odpowiedniego dziennika zdarzeń. 

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Przykład usuwania konfiguracji reguły wszystkich przychodzących wiadomości e-mail" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::


### <a name="3-investigate-the-ip-address"></a>3. Badanie adresu IP

Przejrzyj atrybuty adresu IP, dla których wystąpiło odpowiednie zdarzenie związane z tworzeniem reguł:

- Wyszukaj inne podejrzane działania w chmurze pochodzące z tego samego adresu IP w dzierżawie. Podejrzane działanie może na przykład wymagać wielu nieudanych prób logowania. 
- Czy ten użytkownik jest wspólnym i rozsądnym użytkownikiem u każdego z tych użytkowników?
- Czy lokalizacja jest wspólna i rozsądna dla tego użytkownika?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Badanie podejrzanych działań przez użytkownika przed utworzeniem reguł

Możesz przeglądać wszystkie działania użytkowników przed ich utworzeniam, sprawdzać wskaźniki naruszenia i badać działania użytkowników, które wydają się podejrzane. 

Na przykład w przypadku wielu nieudanych logowania sprawdź: 

- Aktywność logowania 

   Sprawdź, czy działanie logowania przed utworzeniem reguły nie jest podejrzane. (common location /ISP/user-agent). 

- Alerty

   Sprawdź, czy użytkownik otrzymał alerty przed utworzeniem reguł. Może to oznaczać, że konto użytkownika może zostać naruszone. Na przykład: niemożliwe alerty dotyczące podróży, kraj rzadko się powiodło, między innymi wiele nieudanych logowania).

- Zdarzenie

   Sprawdź, czy alert jest skojarzony z innymi alertami wskazującymi na zdarzenie. Jeśli tak, sprawdź, czy zdarzenie zawiera inne prawdziwe alerty dodatnie.

## <a name="advanced-hunting-queries"></a>Zaawansowane zapytania myśliwskie

[Zaawansowane wyszukiwania](advanced-hunting-overview.md) to oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które umożliwia sprawdzanie zdarzeń w sieci w celu znalezienia wskaźników zagrożeń. 

Użyj tego zapytania, aby znaleźć wszystkie nowe zdarzenia reguł skrzynki odbiorczej w określonym oknie czasu.  

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

Kolumna *RuleConfig* (Konfiguracja reguły) będzie zawierała nową konfigurację reguły skrzynki odbiorczej.

Użyj tego zapytania, aby sprawdzić, czy jest to popularne dla użytkownika przez sprawdzenie historii użytkownika.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Użyj tego zapytania, aby sprawdzić, czy kraj jest wspólny dla użytkownika, patrząc na historię użytkownika.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Użyj tego zapytania, aby sprawdzić, czy agent użytkownika jest często spotykany przez użytkownika, patrząc na historię użytkownika.

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
2. Zresetuj poświadczenia konta użytkownika. Możesz także sprawdzić, czy konto użytkownika zostało naruszone przez program Microsoft Defender for Cloud Apps, co jest sygnałem zabezpieczeń z usługi Azure Active Directory (Azure AD) Identity Protection.
3. Wyszukaj inne złośliwe działania wykonywane przez konto użytkownika, na które wpływa to zagrożenie.
4. Aby znaleźć inne naruszone konta użytkowników, sprawdź, czy w dzierżawie nie ma innych podejrzanych działań pochodzących od tego samego adresu IP lub od tego samego istego adresu internetowego.

## <a name="see-also"></a>Zobacz też

- [Omówienie oceny alertów](alert-grading-playbooks.md)
- [Podejrzane działania w zakresie przesyłania dalej poczty e-mail](alert-grading-playbook-email-forwarding.md)
- [Podejrzane reguły przesyłania dalej skrzynki odbiorczej](alert-grading-playbook-inbox-forwarding-rules.md)
- [Badanie alertów](investigate-alerts.md)
