---
title: Klasyfikacja alertów dla podejrzanego działania przekazywania wiadomości e-mail
description: Klasyfikacja alertów dla podejrzanego działania przekazywania wiadomości e-mail w celu przejrzenia alertów i podjęcia zalecanych działań w celu skorygowania ataku i ochrony sieci.
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
ms.openlocfilehash: dcfb6d01503dd4499ce6431b95a433c4cb598de1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663231"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>Klasyfikacja alertów dla podejrzanego działania przekazywania wiadomości e-mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Aktorzy zagrożeń mogą używać kont użytkowników z naruszeniem zabezpieczeń do kilku złośliwych celów, w tym odczytywania wiadomości e-mail w skrzynce odbiorczej użytkownika, przekazywania wiadomości e-mail do zewnętrznych adresatów i wysyłania wiadomości wyłudzających informacje. Użytkownik docelowy może nie wiedzieć, że wiadomości e-mail są przesyłane dalej. Jest to bardzo powszechna taktyka używana przez osoby atakujące w przypadku naruszenia zabezpieczeń kont użytkowników.

Wiadomości e-mail można przekazywać ręcznie lub automatycznie przy użyciu reguł przekazywania dalej. Automatyczne przekazywanie można zaimplementować na wiele sposobów, takich jak reguły skrzynki odbiorczej, Exchange reguła transportu (ETR) i przekazywanie SMTP. Chociaż ręczne przekazywanie dalej wymaga bezpośredniego działania ze strony użytkowników, mogą oni nie być świadomi wszystkich automatycznie przekazywanych wiadomości e-mail. W Microsoft 365 alert jest zgłaszany, gdy użytkownik automatycznie przekazuje wiadomość e-mail na potencjalnie złośliwy adres e-mail.

Ten podręcznik pomaga zbadać alerty dotyczące podejrzanych działań przekazywania wiadomości e-mail i szybko ocenić je jako prawdziwie dodatnie (TP) lub fałszywie dodatnie (FP). Następnie możesz podjąć zalecane działania dla alertów TP w celu skorygowania ataku.

Aby zapoznać się z omówieniem klasyfikacji alertów dla Ochrona usługi Office 365 w usłudze Microsoft Defender i Microsoft Defender for Cloud Apps, zobacz [artykuł wprowadzający](alert-grading-playbooks.md).

Wyniki korzystania z tego podręcznika to:

- Alerty skojarzone z automatycznym przekazywaniem wiadomości e-mail zostały zidentyfikowane jako złośliwe (TP) lub łagodne działania (FP).

  W przypadku złośliwego działania [zatrzymano automatyczne przekazywanie wiadomości e-mail](../office-365-security/external-email-forwarding.md) dla skrzynek pocztowych, których dotyczy problem.

- Podjęto niezbędne działania, jeśli wiadomości e-mail zostały przekazane na złośliwy adres e-mail.

## <a name="email-forwarding-rules"></a>Reguły przekazywania wiadomości e-mail

Reguły przekazywania wiadomości e-mail umożliwiają użytkownikom tworzenie reguły przesyłania dalej wiadomości e-mail wysyłanych do skrzynki pocztowej użytkownika do skrzynki pocztowej innego użytkownika w organizacji lub poza nią. Niektórzy użytkownicy poczty e-mail, zwłaszcza użytkownicy z wieloma skrzynkami pocztowymi, konfigurują zasady przekazywania, aby przenieść wiadomości e-mail pracodawcy na swoje prywatne konta e-mail. Przekazywanie wiadomości e-mail jest przydatną funkcją, ale może również stanowić zagrożenie dla bezpieczeństwa ze względu na potencjalne ujawnienie informacji. Osoby atakujące mogą użyć tych informacji do ataku na organizację lub jej partnerów.

### <a name="suspicious-email-forwarding-activity"></a>Podejrzane działania w zakresie przesyłania dalej wiadomości e-mail

Osoby atakujące mogą skonfigurować reguły poczty e-mail, aby ukryć przychodzące wiadomości e-mail w skrzynce pocztowej użytkownika, których bezpieczeństwo zostało naruszone, aby ukryć złośliwe działania użytkownika. Mogą również ustawić reguły w skrzynce pocztowej użytkownika, których zabezpieczenia zostały naruszone, aby usuwać wiadomości e-mail, przenosić wiadomości e-mail do innego mniej zauważalnego folderu, takiego jak folder RSS, lub przekazywać wiadomości e-mail do konta zewnętrznego.

Niektóre reguły mogą przenosić wszystkie wiadomości e-mail do innego folderu i oznaczać je jako "przeczytane", podczas gdy niektóre reguły mogą przenosić tylko wiadomości zawierające określone słowa kluczowe w wiadomości e-mail lub temacie. Na przykład regułę skrzynki odbiorczej można ustawić tak, aby wyszukiwała słowa kluczowe, takie jak "faktura", "phish", "nie odpowiadaj", "podejrzana wiadomość e-mail" lub "spam" między innymi, i przenosiła je na zewnętrzne konto e-mail. Osoby atakujące mogą również używać skrzynki pocztowej użytkownika, którego zabezpieczenia zostały naruszone, do rozpowszechniania spamu, wiadomości e-mail wyłudzających informacje lub złośliwego oprogramowania.

Ochrona usługi Office 365 w usłudze Microsoft Defender może wykrywać i wysyłać alerty dotyczące podejrzanych reguł przekazywania wiadomości e-mail, co umożliwia znajdowanie i usuwanie ukrytych reguł w źródle.

Aby uzyskać więcej informacji, zobacz następujące wpisy w blogu:

- [Naruszenie zabezpieczeń poczty e-mail firmy](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [Za kulisami naruszenia zabezpieczeń poczty e-mail w firmie: Używanie danych zagrożeń między domenami w celu zakłócenia dużej kampanii BEC](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)

## <a name="alert-details"></a>Szczegóły alertu

Aby przejrzeć alert Dotyczący podejrzanego działania przekazywania wiadomości e-mail, otwórz stronę **Alerty** , aby wyświetlić sekcję **Lista działań** . Oto przykład.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="Lista działań związanych z alertem" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

Wybierz pozycję **Działanie**  , aby wyświetlić szczegóły tego działania na pasku bocznym. Oto przykład.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="Szczegóły działania" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

Pole **Przyczyna** zawiera następujące informacje związane z tym alertem.

- Typ przekazywania (FT) jest jednym z następujących:
  - reguła transportu Exchange (ETR): przekazywana dalej przy użyciu reguły transportu i Exchange
  - SMTP: przesyłane dalej przy użyciu przekazywania skrzynek pocztowych
  - InboxRule: przekazywane przy użyciu reguły skrzynki odbiorczej

- Identyfikator śledzenia komunikatów (MTI): jest to identyfikator (NetworkMessageId) przesłanej dalej wiadomości e-mail, która wyzwoliła ten alert. NetworkMessageId to unikatowy identyfikator wiadomości e-mail w organizacji.
- Usługa przesyłania dalej (F): użytkownik, który przekazał tę wiadomość e-mail dalej.
- Lista podejrzanych adresatów (SRL): lista adresatów uważanych za podejrzanych w tej wiadomości e-mail.
- Lista adresatów (RL): lista wszystkich adresatów w tej wiadomości e-mail.

## <a name="investigation-workflow"></a>Przepływ pracy badania

Podczas badania tego alertu należy określić:

- Czy konto użytkownika i jego skrzynka pocztowa zostały naruszone?
- Czy działania są złośliwe?

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>Czy konto użytkownika i jego skrzynka pocztowa zostały naruszone?

Patrząc na wcześniejsze zachowanie nadawcy i ostatnie działania, powinno być możliwe określenie, czy konto użytkownika powinno zostać uznane za naruszone. Szczegóły alertów zgłaszanych ze strony użytkownika można wyświetlić w portalu Microsoft 365 Defender.

Możesz również przeanalizować te dodatkowe działania dla skrzynki pocztowej, których dotyczy problem:

- Używanie Eksploratora zagrożeń do zrozumienia zagrożeń związanych z pocztą e-mail
  - Sprawdź, ile ostatnio wysłanych wiadomości e-mail wysyłanych przez nadawcę jest wykrywanych jako fałszywe, spam lub złośliwe oprogramowanie.
  - Sprawdź, ile wysłanych wiadomości e-mail zawiera informacje poufne.

- Ocena ryzykownego zachowania logowania w portalu Microsoft Azure.
- Sprawdź, czy na urządzeniu użytkownika nie występują złośliwe działania.

### <a name="are-the-activities-malicious"></a>Czy działania są złośliwe?

Zbadaj działanie przekazywania wiadomości e-mail. Na przykład sprawdź typ wiadomości e-mail, adresata tej wiadomości e-mail lub sposób przekazywania wiadomości e-mail.

Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

- [Szczegółowe informacje o komunikatach przesyłanych automatycznie](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [Nowi użytkownicy przekazujący szczegółowe informacje e-mail](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [Odpowiadanie na naruszone konto e-mail](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [Zgłaszanie wyników fałszywie dodatnich i fałszywie ujemnych w Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

Oto przepływ pracy umożliwiający zidentyfikowanie podejrzanych działań przekazywania wiadomości e-mail.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="Przepływ pracy badania alertów na potrzeby przekazywania wiadomości e-mail" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

Alert przekazywania wiadomości e-mail można zbadać przy użyciu Eksploratora zagrożeń lub zaawansowanych zapytań dotyczących wyszukiwania zagrożeń w oparciu o dostępność funkcji w portalu Microsoft 365 Defender. W razie potrzeby możesz wykonać cały proces lub część procesu.

## <a name="using-threat-explorer"></a>Korzystanie z Eksploratora zagrożeń

Eksplorator zagrożeń udostępnia interaktywne środowisko badania zagrożeń związanych z pocztą e-mail w celu określenia, czy to działanie jest podejrzane. Z informacji o alertach można użyć następujących wskaźników:

- SRL/RL: użyj (podejrzanej) listy adresatów (SRL), aby znaleźć następujące szczegóły:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="Przykład listy adresatów" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

  - KtoTo jeszcze przekazała wiadomości e-mail do tych adresatów?
  - Ile wiadomości e-mail zostało przekazanych do tych adresatów?
  - Jak często wiadomości e-mail są przekazywane do tych adresatów?

- MTI: użyj identyfikatora śledzenia komunikatów/identyfikatora komunikatu sieciowego, aby znaleźć następujące szczegóły:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="Przykład identyfikatora komunikatu sieciowego" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

  - Jakie dodatkowe szczegóły są dostępne dla tej wiadomości e-mail? Na przykład: temat, ścieżka powrotna i sygnatura czasowa.
  - Jakie jest źródło tej wiadomości e-mail? Czy są jakieś podobne wiadomości e-mail?
  - Czy ta wiadomość e-mail zawiera jakiekolwiek adresy URL? Czy adres URL wskazuje na jakiekolwiek dane poufne?
  - Czy wiadomość e-mail zawiera załączniki? Czy załączniki zawierają informacje poufne?
  - Jaka była akcja podjęta w wiadomości e-mail? Czy został usunięty, oznaczony jako przeczytany lub przeniesiony do innego folderu?
  - Czy są jakieś zagrożenia związane z tą wiadomością e-mail? Czy ta wiadomość e-mail jest częścią jakiejkolwiek kampanii?

Na podstawie odpowiedzi na te pytania należy mieć możliwość określenia, czy wiadomość e-mail jest złośliwa, czy niegroźna.

## <a name="advanced-hunting-queries"></a>Zaawansowane zapytania dotyczące wyszukiwania zagrożeń

Aby użyć zaawansowanych zapytań [wyszukiwania zagrożeń](advanced-hunting-overview.md) w celu zebrania informacji związanych z alertem i określenia, czy działanie jest podejrzane, upewnij się, że masz dostęp do następujących tabel:

- EmailEvents — zawiera informacje związane z przepływem poczty e-mail.

- EmailUrlInfo — zawiera informacje związane z adresami URL w wiadomościach e-mail.

- CloudAppEvents — zawiera dziennik inspekcji działań użytkowników.

- IdentityLogonEvents — zawiera informacje logowania dla wszystkich użytkowników.

> [!NOTE]
> Niektóre parametry są unikatowe dla twojej organizacji lub sieci. Podaj te konkretne parametry zgodnie z instrukcjami w każdym zapytaniu.

Uruchom to zapytanie, aby dowiedzieć się, kto jeszcze przekazał wiadomości e-mail do tych adresatów (SRL/RL).

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

Uruchom to zapytanie, aby dowiedzieć się, ile wiadomości e-mail zostało przekazanych do tych adresatów.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

Uruchom to zapytanie, aby dowiedzieć się, jak często wiadomości e-mail są przekazywane do tych adresatów.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress, bin(Timestamp, 1d)
```

Uruchom to zapytanie, aby dowiedzieć się, czy wiadomość e-mail zawiera adresy URL.

```kusto
let mti='{MTI}'; //Replace {MTI} with MTI from alert
EmailUrlInfo
| where NetworkMessageId == mti
```

Uruchom to zapytanie, aby dowiedzieć się, czy wiadomość e-mail zawiera załączniki.

   ```kusto
   let mti='{MTI}'; //Replace {MTI} with MTI from alert
   EmailAttachmentInfo
   | where NetworkMessageId == mti
   ```

Uruchom to zapytanie, aby dowiedzieć się, czy usługa przesyłania dalej (nadawca) utworzyła nowe reguły.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with display name of Forwarder
let action_types = pack_array(
    "New-InboxRule",
    "UpdateInboxRules",
    "Set-InboxRule",
    "Set-Mailbox",
    "New-TransportRule",
    "Set-TransportRule");
CloudAppEvents
| where AccountDisplayName == sender
| where ActionType in (action_types)
```

Uruchom to zapytanie, aby dowiedzieć się, czy były jakieś nietypowe zdarzenia logowania od tego użytkownika. Na przykład: nieznane adresy IP, nowe aplikacje, nietypowe kraje, wiele zdarzeń logowania nie powiodło się.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>Badanie reguł przekazywania

Podejrzane reguły przekazywania można również znaleźć przy użyciu centrum administracyjnego Exchange na podstawie typu reguły (wartość FT w alercie).

- ETR

  Exchange reguł transportu są wymienione w sekcji **Reguły**. Sprawdź, czy wszystkie reguły są zgodnie z oczekiwaniami.

- SMTP

  Reguły przekazywania skrzynek pocztowych można wyświetlić, wybierając skrzynkę pocztową nadawcy **Zarządzanie ustawieniami \> przepływu poczty E-mail Edytuj przekazywanie \> wiadomości e-mail.\>**

- Reguła skrzynki odbiorczej

  Reguły skrzynki odbiorczej są konfigurowane za pomocą klienta poczty e-mail. Aby wyświetlić listę reguł skrzynki odbiorczej utworzonych przez użytkowników, możesz użyć polecenia cmdlet [Get-InboxRule](/powershell/module/exchange/get-inboxrule) programu PowerShell.

### <a name="additional-investigation"></a>Dodatkowe badanie

Wraz z odnalezionymi do tej pory dowodami można określić, czy są tworzone nowe reguły przekazywania. Zbadaj adres IP skojarzony z regułą. Upewnij się, że nie jest to nietypowy adres IP i jest zgodny ze zwykłymi działaniami wykonywanymi przez użytkownika.

## <a name="recommended-actions"></a>Zalecane akcje

Po ustaleniu, że skojarzone działania sprawiają, że ten alert jest prawdziwie dodatni, należy sklasyfikować alert i wykonać następujące akcje w celu skorygowania:

1. Wyłącz i usuń regułę przekazywania skrzynki odbiorczej.
2. W przypadku typu przekazywania inboxRule zresetuj poświadczenia konta użytkownika.
3. W przypadku typu przekazywania SMTP lub ETR zbadaj działania konta użytkownika, które utworzyło alert.

    - Zbadaj wszelkie inne podejrzane działania administratora.

    - Zresetuj poświadczenia konta użytkownika.

4. Sprawdź dodatkowe działania pochodzące z kont, adresów IP i podejrzanych nadawców, których dotyczy problem.

## <a name="see-also"></a>Zobacz też

- [Omówienie klasyfikacji alertów](alert-grading-playbooks.md)
- [Podejrzane reguły przesyłania dalej w skrzynce odbiorczej](alert-grading-playbook-inbox-forwarding-rules.md)
- [Podejrzane reguły manipulowania skrzynką odbiorczą](alert-grading-playbook-inbox-manipulation-rules.md)
- [Badaj alerty](investigate-alerts.md)
