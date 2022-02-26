---
title: Ocenianie alertów podejrzaną aktywnością w przesyłaniu dalej wiadomości e-mail
description: Ocenianie alertów podejrzaną aktywnością przesyłania dalej poczty e-mail w celu przejrzenia alertów i podjęcia zalecanych działań w celu podjęcia działań naprawczych w celu ochrony sieci i ataków.
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
ms.openlocfilehash: fe4a5e97704cbf1d4851484397e7c4424c099d3c
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "62974143"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>Ocenianie alertów podejrzaną aktywnością w przesyłaniu dalej wiadomości e-mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Zagrożenie może używać naruszonych kont użytkowników do kilku złośliwych celów, takich jak odczytywanie wiadomości e-mail w skrzynce odbiorczej użytkownika, przesyłanie dalej wiadomości e-mail do adresatów zewnętrznych oraz wysyłanie wiadomości wyłudzających informacje. Użytkownik docelowy może nie być świadomy, że jego wiadomości e-mail są przekazywane dalej. Jest to bardzo częsty emotikon, który używa się podczas naruszonych kont użytkowników.

Wiadomości e-mail można przesyłać dalej ręcznie lub automatycznie przy użyciu reguł przesyłania dalej. Automatyczne przesyłanie dalej można zaimplementować na wiele sposobów, takich jak reguły skrzynki odbiorczej, reguły Exchange transportu (ETR) i przesyłanie dalej SMTP. Mimo że ręczne przesyłanie dalej wymaga bezpośredniej akcji ze strony użytkowników, mogą nie wiedzieć o wszystkich automatycznie przesyłanych wiadomościach e-mail. W Microsoft 365 e-mail jest wywoływany alert, gdy użytkownik automatycznie przesyła dalej wiadomość e-mail na potencjalnie złośliwy adres e-mail.

Ten podręcznik ułatwia badanie podejrzanych alertów dotyczących aktywności przesyłania dalej poczty e-mail i szybkie ocenianie ich jako prawdziwego dodatniego (TP) lub wyników fałszywie dodatnich (FP). Następnie możesz podjąć zalecane działania dla alertów TP, aby rozwiązać ten atak.

Aby uzyskać omówienie oceniania alertów dla programu Microsoft Defender dla programu Office 365 i programu Microsoft Defender dla aplikacji w chmurze, zobacz [artykuł wprowadzający](alert-grading-playbooks.md).

Wyniki korzystania z tego podręcznika są takie:

- Alerty skojarzone z automatycznie przesyłaną dalej wiadomościami e-mail zostały zidentyfikowane jako złośliwe (TP) lub szemrzone (FP).

  Jeśli jest złośliwy, funkcja automatycznego przesyłania dalej poczty [e-mail](../office-365-security/external-email-forwarding.md) dla skrzynek pocztowych, których dotyczy problem.

- Jeśli wiadomości e-mail zostały przekazane na złośliwy adres e-mail, zostały wykonane odpowiednie czynności.

## <a name="email-forwarding-rules"></a>Reguły przesyłania dalej poczty e-mail

Reguły przesyłania dalej poczty e-mail umożliwiają użytkownikom utworzenie reguły przesyłania dalej wiadomości e-mail wysyłanych do skrzynki pocztowej użytkownika do skrzynki pocztowej innego użytkownika w organizacji lub poza nią. Niektórzy użytkownicy poczty e-mail, zwłaszcza z wieloma skrzynkami pocztowymi, konfigurują reguły przesyłania dalej w celu przenoszenia wiadomości e-mail pracodawcy na ich prywatne konta e-mail. Przesyłanie dalej wiadomości e-mail jest przydatną funkcją, ale może także stanowić zagrożenie bezpieczeństwa ze względu na możliwość ujawnienia informacji. Atakujący mogą używać tych informacji do ataków na Twoją organizację lub jej partnerów.

### <a name="suspicious-email-forwarding-activity"></a>Podejrzane działania w zakresie przesyłania dalej poczty e-mail

Atakujący mogą skonfigurować reguły wiadomości e-mail w celu ukrywania przychodzących wiadomości e-mail w naruszonej skrzynce pocztowej użytkownika w celu przesłania ich złośliwych działań przed użytkownikiem. Ponadto mogą ustawiać reguły w naruszonej skrzynce pocztowej użytkownika w celu usuwania wiadomości e-mail, przenoszenia wiadomości e-mail do innego mniej zauważalnego folderu, takiego jak folder RSS, lub przesyłania dalej wiadomości e-mail na konto zewnętrzne.  

Niektóre reguły mogą przenosić wszystkie wiadomości e-mail do innego folderu i oznaczać je jako "przeczytane", natomiast niektóre reguły mogą przenosić tylko wiadomości zawierające określone słowa kluczowe w wiadomości e-mail lub temacie. Na przykład regułę skrzynki odbiorczej można skonfigurować tak, aby między innymi wyszukiwała słowa kluczowe, takie jak "faktura", "wyłudzać", "nie odpowiadaj", "podejrzane wiadomości e-mail" lub "spam" i przenosić je na zewnętrzne konto e-mail. Atakujący mogą też rozpowszechniać spam, wiadomości e-mail służące do wyłudzania informacji lub złośliwe oprogramowanie, co może wymagać wykorzystania naruszonej skrzynki pocztowej użytkownika.
 
Usługa Microsoft Defender for Office 365 może wykrywać i ostrzegać o podejrzanych zasadach przesyłania dalej wiadomości e-mail, umożliwiając znalezienie i usunięcie ukrytych reguł w źródle.

Aby uzyskać więcej informacji, zobacz następujące wpisy w blogu:

- [Firmowe konto e-mail](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [Za kulisami biznesowego naruszenia zabezpieczeń poczty e-mail: przerywanie dużej kampanii przy użyciu danych zagrożeń między domenami](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)


## <a name="alert-details"></a>Szczegóły alertu

Aby przejrzeć alert Podejrzane działania przesyłania dalej poczty e-mail, otwórz stronę **Alerty** w celu sprawdzenia **sekcji Lista** działań. Oto przykład.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="Lista działań związanych z alertem" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

Wybierz **pozycję**  Aktywność, aby wyświetlić szczegóły tego działania na pasku bocznym. Oto przykład.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="Szczegóły działania" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

Pole **Przyczyna** zawiera następujące informacje dotyczące tego alertu.

- Typ przekazywania (FT) jest jednym z następujących:

    -  Exchange transportowych: Przesyłanie dalej przy użyciu i Exchange transportowego 

    -  SMTP: Przesyłanie dalej przy użyciu przesyłania dalej skrzynki pocztowej

    -  InboxRule: Forwarded using an Inbox Rule

- Identyfikator śledzenia wiadomości (MTI): jest to identyfikator (NetworkMessageId) wiadomości e-mail, która wyzwoliła ten alert. NetworkMessageId to identyfikator unikatowy e-mail w Twojej organizacji.
- Forwarder (F): Użytkownik, który przesyłał dalej tę wiadomość e-mail.
- Podejrzana lista adresatów: lista adresatów uznanych za podejrzanych w tej wiadomości e-mail.
- Lista adresatów: lista wszystkich adresatów tej wiadomości e-mail.

## <a name="investigation-workflow"></a>Przepływ pracy Badania

Podczas badania tego alertu należy ustalić:

- Czy konto użytkownika i jego skrzynka pocztowa są naruszone?
- Czy działania są złośliwe?

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>Czy konto użytkownika i jego skrzynka pocztowa są naruszone?

Patrząc na zachowania nadawcy w przeszłości i ostatnie działania, należy ustalić, czy konto użytkownika powinno być traktowane jako naruszone, czy nie. W portalu można wyświetlić szczegóły alertów podniesionych ze strony Microsoft 365 Defender użytkowników. 

Możesz również analizować te dodatkowe działania dla skrzynki pocztowej, dla których ma to wpływ:

- Używanie Eksploratora zagrożeń do zrozumienia zagrożeń związanych z pocztą e-mail

    - Sprawdź, ile najnowszych wiadomości e-mail wysłanych przez nadawcę jest wykrywanych jako wyłudzy, spam lub złośliwe oprogramowanie.

    - Sprawdź, ile z wysłanych wiadomości e-mail zawiera informacje poufne. 

- Oceń ryzykowne zachowanie podczas logowania się Microsoft Azure portalu.
- Sprawdź, czy na urządzeniu użytkownika nie ma żadnych złośliwych działań.

### <a name="are-the-activities-malicious"></a>Czy działania są złośliwe?

Badanie działania przesyłania dalej poczty e-mail. Na przykład sprawdź typ wiadomości e-mail, adresat tej wiadomości e-mail lub sposób jej przesyłania dalej. 

Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

- [Szczegółowe informacje o wiadomościach przesyłanych automatycznie](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [Nowi użytkownicy przesyłający dalej informacje o wiadomościach e-mail](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [Odpowiadanie na naruszone konto e-mail](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [Zgłaszanie wyników fałszywie dodatnich i ujemnych w Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

Oto przepływ pracy do identyfikowania podejrzanych działań przesyłania dalej wiadomości e-mail.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="Przepływ pracy Badania alertu dla przesyłania dalej poczty e-mail" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

Możesz zbadać alert przesyłania dalej wiadomości e-mail przy użyciu Eksploratora zagrożeń lub zaawansowanych zapytań myśliwski, w zależności od dostępności funkcji w Microsoft 365 Defender portali. Możesz w razie potrzeby wykonać cały proces lub jego część.

## <a name="using-threat-explorer"></a>Korzystanie z Eksploratora zagrożeń

Eksplorator zagrożeń udostępnia interakcyjne środowisko analizy zagrożeń związanych z pocztą e-mail w celu określenia, czy dane działanie jest podejrzane. W informacjach o alertach można używać następujących wskaźników:

- Adres SRL/RL: Użyj listy (podejrzanej) adresatów (SRL), aby znaleźć następujące szczegóły:
 
    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="Przykład listy adresatów" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

    - KtoTo inne osoby przesyłały dalej wiadomości e-mail do tych adresatów?

    - Ilu wiadomości e-mail zostało przesyłanych dalej do tych adresatów?

    - Jak często wiadomości e-mail są przekazywane dalej do tych adresatów?
 

- MTI: Aby znaleźć te szczegóły, użyj identyfikatora śledzenia wiadomości/identyfikatora wiadomości sieciowej:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="Przykład identyfikatora wiadomości sieciowej" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

    - Jakie dodatkowe szczegóły są dostępne dla tej wiadomości e-mail? Na przykład: temat, ścieżka zwrotna i sygnatura czasowa.

    - Jakie jest pochodzenie tej wiadomości e-mail? Czy są jakieś podobne wiadomości e-mail?

    - Czy ta wiadomość e-mail zawiera jakiekolwiek adresy URL? Czy adres URL zawiera jakiekolwiek poufne dane?

    - Czy wiadomość e-mail zawiera jakiekolwiek załączniki? Czy załączniki zawierają informacje poufne?

    - Jakie działanie dzieje się w wiadomości e-mail? Czy plik został usunięty, oznaczony jako przeczytany lub przeniesiony do innego folderu?

    - Czy z tą wiadomością e-mail są skojarzone jakiekolwiek zagrożenia? Czy ta wiadomość e-mail jest częścią jakiejkolwiek kampanii?

Na podstawie odpowiedzi na te pytania należy ustalić, czy wiadomość e-mail jest złośliwa, czy szemrna.

## <a name="advanced-hunting-queries"></a>Zaawansowane zapytania myśliwskie

Aby używać [zaawansowanych zapytań wyszukiwania](advanced-hunting-overview.md) w celu zbierania informacji związanych z alertem i określania, czy dane działanie jest podejrzane, upewnij się, że masz dostęp do następujących tabel:

- EmailEvents — zawiera informacje dotyczące przepływu poczty e-mail.

- EmailUrlInfo — zawiera informacje dotyczące adresów URL w wiadomościach e-mail.

- CloudAppEvents — zawiera dziennik inspekcji działań użytkowników.

- IdentityLogonEvents — zawiera informacje logowania dla wszystkich użytkowników.

>[!Note]
>Niektóre parametry są unikatowe dla Twojej organizacji lub sieci. Wypełnij te konkretne parametry zgodnie z instrukcjami w każdym zapytaniu.
>

Uruchom to zapytanie, aby dowiedzieć się, kto jeszcze przesyłał dalej wiadomości e-mail do tych adresatów (SRL/RL).

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

Uruchom to zapytanie, aby dowiedzieć się, ile wiadomości e-mail zostało przesyłanych dalej do tych adresatów.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

Uruchom to zapytanie, aby dowiedzieć się, jak często wiadomości e-mail są przekazywane dalej do tych adresatów.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress, bin(Timestamp, 1d)
```

Uruchom to zapytanie, aby dowiedzieć się, czy wiadomość e-mail zawiera jakiekolwiek adresy URL.
 
```kusto
let mti='{MTI}'; //Replace {MTI} with MTI from alert
EmailUrlInfo
| where NetworkMessageId == mti
```

Uruchom to zapytanie, aby dowiedzieć się, czy wiadomość e-mail zawiera jakiekolwiek załączniki.

   ```kusto
   let mti='{MTI}'; //Replace {MTI} with MTI from alert
   EmailAttachmentInfo
   | where NetworkMessageId == mti
   ```

Uruchom to zapytanie, aby dowiedzieć się, czy nadawca (nadawca) utworzył jakiekolwiek nowe reguły.

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

Uruchom to zapytanie, aby dowiedzieć się, czy ten użytkownik nie ma żadnych anomalnych zdarzeń logowania. Przykład: nieznane ip, nowe aplikacje, nietypowe kraje, wiele zdarzeń logowaniaFailed.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder 
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>Badanie reguł przesyłania dalej

Podejrzane reguły przesyłania dalej można też znaleźć, korzystając Exchange centrum administracyjnego w oparciu o typ reguły (wartość FT w alercie).

- ETR 

  Exchange transportu są wymienione w **sekcji** Reguły. Upewnij się, że wszystkie reguły są zgodnie z oczekiwaniami.

- SMTP

  Aby wyświetlić reguły przesyłania dalej skrzynki pocztowej, wybierz skrzynkę pocztową nadawcy Zarządzanie ustawieniami **przepływu poczty e-mail \> \> Edycja.\>**

- InboxRule

  Reguły skrzynki odbiorczej są konfigurowane z klientem poczty e-mail. Aby wyświetlić listę reguł skrzynki odbiorczej utworzonych przez użytkowników, możesz użyć polecenia cmdlet [Get-InboxRule](/powershell/module/exchange/get-inboxrule) programu PowerShell.

### <a name="additional-investigation"></a>Dodatkowe badanie

Wraz z wykrytym do tej pory dowodem możesz ustalić, czy istnieją nowe reguły przesyłania dalej. Zbadaj adres IP skojarzony z regułą. Upewnij się, że nie jest to anomalny adres IP i jest zgodny z zwykłymi działaniami wykonywanymi przez użytkownika.

## <a name="recommended-actions"></a>Zalecane akcje

Po określeniu, że skojarzone działania sprawiają, że alert jest prawdziwy dodatni, sklasyfikuj alert i podejmie działania naprawcze:

1. Wyłącz i usuń regułę przesyłania dalej skrzynki odbiorczej.
2. W przypadku typu Przesyłanie dalej przez Skrzynkę odbiorczą zresetuj poświadczenia konta użytkownika.
3. W przypadku typu przesyłania dalej SMTP lub ETR należy zbadać działania konta użytkownika, które utworzyło alert.

    - Badanie wszelkich podejrzanych działań a administratorów.

    - Zresetuj poświadczenia konta użytkownika.

4. Sprawdź, czy nie ma dodatkowych działań pochodzących z kont, adresów IP i podejrzanych nadawców.

## <a name="see-also"></a>Zobacz też

- [Omówienie oceny alertów](alert-grading-playbooks.md)
- [Podejrzane reguły przesyłania dalej skrzynki odbiorczej](alert-grading-playbook-inbox-forwarding-rules.md)
- [Podejrzane reguły manipulowania skrzynką odbiorczą](alert-grading-playbook-inbox-manipulation-rules.md)
- [Badanie alertów](investigate-alerts.md)
