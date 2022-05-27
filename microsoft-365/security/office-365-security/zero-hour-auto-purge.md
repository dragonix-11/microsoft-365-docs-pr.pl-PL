---
title: Automatyczne przeczyszczanie z zerową godziną w Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 96deb75f-64e8-4c10-b570-84c99c674e15
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Automatyczne przeczyszczanie bez godziny powoduje wsteczne przeniesienie dostarczonych wiadomości w skrzynce pocztowej Exchange Online do folderu Wiadomości-śmieci lub kwarantanny, które po dostarczeniu mogą być spamem, wyłudzaniem informacji lub złośliwym oprogramowaniem.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd9bb3f231e42c625c87669417210281d1d5a3df
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739466"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Automatyczne przeczyszczanie o zerowej godzinie (ZAP) w Exchange Online

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Podstawy automatycznego przeczyszczania o zerowej godzinie (ZAP)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online automatyczne przeczyszczanie o wartości zero godzin (ZAP) jest funkcją ochrony poczty e-mail, która wstecznie wykrywa i neutralizuje złośliwe wiadomości wyłudzające informacje, spam lub złośliwe oprogramowanie, które zostały już dostarczone do Exchange Online skrzynek pocztowych.

Zap nie działa w autonomicznych środowiskach Exchange Online Protection (EOP), które chronią lokalne Exchange skrzynki pocztowe.

## <a name="how-zap-works"></a>Jak działa zap

Sygnatury spamu i złośliwego oprogramowania są codziennie aktualizowane w usłudze w czasie rzeczywistym. Jednak użytkownicy nadal mogą otrzymywać złośliwe komunikaty z różnych powodów, w tym jeśli zawartość jest broniona po dostarczeniu do użytkowników. Zap rozwiązuje ten problem, stale monitorując aktualizacje sygnatur spamu i złośliwego oprogramowania w usłudze. Zap może znajdować i usuwać wiadomości, które znajdują się już w skrzynce pocztowej użytkownika.

Akcja zap jest bezproblemowa dla użytkownika; nie są powiadamiani, jeśli komunikat zostanie wykryty i przeniesiony.

[Sejf listy nadawców](create-safe-sender-lists-in-office-365.md), reguły przepływu poczty (nazywane również regułami transportu), reguły skrzynki odbiorczej lub dodatkowe filtry mają pierwszeństwo przed zap. Podobnie jak w przypadku przepływu poczty, oznacza to, że nawet jeśli usługa określi, że dostarczona wiadomość wymaga zap, wiadomość nie jest wykonywana ze względu na konfigurację bezpiecznych nadawców. Jest to kolejny powód, aby uważać na konfigurowanie komunikatów w celu obejścia filtrowania.

Obejrzyj ten krótki film wideo, aby dowiedzieć się, jak zap w Ochrona usługi Office 365 w usłudze Microsoft Defender automatycznie wykrywa i neutralizuje zagrożenia w wiadomości e-mail. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGrLg]

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Automatyczne przeczyszczanie bez godziny (ZAP) w przypadku złośliwego oprogramowania

W przypadku **komunikatów odczytanych lub nieprzeczytanych** , które zawierają złośliwe oprogramowanie po dostarczeniu, zap podda kwarantannie komunikat zawierający załącznik złośliwego oprogramowania. Domyślnie tylko administratorzy mogą wyświetlać komunikaty o złośliwym oprogramowaniu i zarządzać nimi. Administratorzy mogą jednak tworzyć _zasady kwarantanny_ i używać ich do definiowania, co użytkownicy mogą robić w przypadku komunikatów, które zostały poddane kwarantannie jako złośliwe oprogramowanie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

Zap dla złośliwego oprogramowania jest domyślnie włączona w zasadach ochrony przed złośliwym oprogramowaniem. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w ramach EOP](configure-anti-malware-policies.md).

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Automatyczne przeczyszczanie bez godzin (ZAP) w celu wyłudzania informacji

W przypadku **komunikatów odczytanych lub nieprzeczytanych** , które są identyfikowane jako wyłudzanie informacji po dostarczeniu, wynik zap zależy od akcji skonfigurowanej dla werdyktu filtrowania **wiadomości e-mail wyłudzającego informacje** w odpowiednich zasadach ochrony przed spamem. Dostępne akcje filtrowania werdyktu dotyczące wyłudzania informacji i ich możliwych wyników zap są opisane na następującej liście:

- **Dodaj nagłówek X**, **wiersz tematu przedpłaty z tekstem**, **Przekieruj wiadomość na adres e-mail**, **Usuń wiadomość**: ZAP nie podejmuje żadnych działań w tej wiadomości.

- **Przenieś wiadomość do wiadomości-śmieci**: zap przenosi wiadomość do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych w Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Komunikat kwarantanny**: zap kwarantanny komunikatu.

Domyślnie zap dla wyłudzania informacji jest włączona w zasadach ochrony przed spamem, a domyślną akcją dla werdyktu filtrowania **wiadomości e-mail wyłudzania informacji** jest **komunikat kwarantanny**, co oznacza, że zap do wyłudzania informacji kwarantanny wiadomości domyślnie.

Aby uzyskać więcej informacji na temat konfigurowania werdyktów filtrowania spamu, zobacz [Konfigurowanie zasad ochrony przed spamem w Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Automatyczne przeczyszczanie bez godziny (ZAP) w celu wyłudzania informacji o wysokim poziomie ufności

W przypadku **komunikatów odczytanych lub nieprzeczytanych** , które są identyfikowane jako wyłudzanie informacji o wysokim poziomie ufności po dostarczeniu, zap podda je kwarantannie. Domyślnie tylko administratorzy mogą wyświetlać komunikaty phish o wysokiej pewności i zarządzać nimi. Administratorzy mogą jednak tworzyć _zasady kwarantanny_ i używać ich do definiowania, co użytkownicy mogą robić w przypadku komunikatów, które zostały poddane kwarantannie jako wyłudzanie informacji o wysokim poziomie zaufania. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md)

Zap dla phish wysokiej ufności jest domyślnie włączona. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie domyślnie w Office 365](secure-by-default.md).

### <a name="zero-hour-auto-purge-zap-for-spam"></a>Automatyczne przeczyszczanie o zerowej godzinie (ZAP) w przypadku spamu

W przypadku **nieprzeczytanych wiadomości** zidentyfikowanych jako spam po dostarczeniu wynik zap zależy od akcji skonfigurowanej dla werdyktu filtrowania **spamu** w odpowiednich zasadach ochrony przed spamem. Dostępne akcje filtrowania werdyktu dotyczące spamu i ich możliwych wyników zap są opisane na następującej liście:

- **Dodaj nagłówek X**, **wiersz tematu przedpłaty z tekstem**, **Przekieruj wiadomość na adres e-mail**, **Usuń wiadomość**: ZAP nie podejmuje żadnych działań w tej wiadomości.

- **Przenieś wiadomość do wiadomości-śmieci**: zap przenosi wiadomość do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych w Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Komunikat kwarantanny**: zap kwarantanny komunikatu. Domyślnie użytkownicy końcowi mogą wyświetlać wiadomości poddane kwarantannie i zarządzać nimi, gdzie są adresatami. Administratorzy mogą jednak tworzyć _zasady kwarantanny_ i używać ich do definiowania, co użytkownicy mogą robić w przypadku wiadomości, które zostały poddane kwarantannie jako spam. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md)

Domyślnie zap spam jest włączony w zasadach antyspamowych, a domyślną akcją werdyktu filtrowania **spamu** jest **przenoszenie wiadomości do folderu Wiadomości-śmieci**, co oznacza, że spam ZAP domyślnie przenosi **nieprzeczytane** wiadomości do folderu Wiadomości-śmieci.

Aby uzyskać więcej informacji na temat konfigurowania werdyktów filtrowania spamu, zobacz [Konfigurowanie zasad ochrony przed spamem w Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Zagadnienia dotyczące automatycznego przeczyszczania (ZAP) w godzinach zerowych dla Ochrona usługi Office 365 w usłudze Microsoft Defender

Zap nie będzie kwarantanny żadnych komunikatów, które są w trakcie [dynamicznego dostarczania](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) w Sejf skanowanie zasad załączników, lub gdy filtrowanie złośliwego oprogramowania EOP już zastąpił załącznik z **alertem złośliwego oprogramowania Text.txt** pliku. Jeśli otrzymasz sygnał wyłudzania informacji lub spamu dla tego typu wiadomości, a werdykt filtrowania w zasadach ochrony przed spamem zostanie ustawiony na podjęcie pewnych działań w wiadomości (Przenoszenie do wiadomości-śmieci, Przekierowanie, Usuwanie lub Kwarantanna), zap domyślnie użyje akcji "Przenieś na śmieci".

## <a name="how-to-see-if-zap-moved-your-message"></a>Jak sprawdzić, czy zap przeniósł komunikat

Aby ustalić, czy zap przeniósł komunikat, masz następujące opcje:

- **Liczba komunikatów**: użyj [widoku Przepływ poczty w raporcie o stanie przepływu poczty](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) , aby wyświetlić liczbę komunikatów, których dotyczy problem z zap dla określonego zakresu dat.
- **Szczegóły komunikatu**: użyj [Eksploratora zagrożeń (i wykrywania w czasie rzeczywistym),](threat-explorer.md) aby filtrować **wszystkie zdarzenia poczty e-mail** według wartości **ZAP** dla kolumny **Dodatkowa akcja** .

> [!NOTE]
> Zap nie jest zalogowany w Exchange dzienników inspekcji skrzynki pocztowej jako akcja systemu.

## <a name="zero-hour-auto-purge-zap-faq"></a>Automatyczne przeczyszczanie o zerowej godzinie (ZAP) — często zadawane pytania

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Co się stanie, jeśli legalna wiadomość zostanie przeniesiona do folderu Wiadomości-śmieci?

Należy postępować zgodnie z normalnym procesem raportowania [dla wyników fałszywie dodatnich](report-junk-email-messages-to-microsoft.md). Jedynym powodem przeniesienia wiadomości ze skrzynki odbiorczej do folderu Wiadomości-śmieci będzie fakt, że usługa ustaliła, że wiadomość była spamem lub złośliwym.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Co zrobić, jeśli użyję folderu Kwarantanna zamiast folderu Wiadomości-śmieci?

Zap podejmie działania na podstawie komunikatu na podstawie konfiguracji zasad ochrony przed spamem zgodnie z opisem we wcześniejszej części tego artykułu.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Co zrobić, jeśli używam bezpiecznych nadawców, reguł przepływu poczty lub list dozwolonych/zablokowanych nadawców?

Sejf nadawcy, reguły przepływu poczty lub blokuj i zezwalaj na ustawienia organizacyjne mają pierwszeństwo. Te komunikaty są wykluczone z zap, ponieważ usługa robi to, co skonfigurowano do wykonania. Jest to kolejny powód, aby uważać na konfigurowanie komunikatów w celu obejścia filtrowania.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Jakie są wymagania licencyjne dotyczące automatycznego przeczyszczania w godzinach zerowych do działania?

Nie ma żadnych ograniczeń dotyczących licencji. Zap działa na wszystkich skrzynkach pocztowych hostowanych w Exchange online. Zap nie działa w autonomicznych środowiskach Exchange Online Protection (EOP), które chronią lokalne Exchange skrzynki pocztowe.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Co zrobić, jeśli komunikat zostanie przeniesiony do innego folderu (np. reguł skrzynki odbiorczej)?

Automatyczne przeczyszczanie zerogodzin nadal działa, dopóki komunikat nie został usunięty lub dopóki nie zastosowano jeszcze tej samej lub silniejszej akcji. Jeśli na przykład zasady ochrony przed wyłudzaniem informacji są ustawione na kwarantannę, a komunikat znajduje się już w wiadomości-śmieci, zap podejmie działania w celu kwarantanny komunikatu.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Jak zap wpływa na skrzynki pocztowe zawieszone?

Automatyczne przeczyszczanie o wartości zero godzin spowoduje kwarantannę wiadomości ze skrzynek pocztowych wstrzymanych. Zap może przenosić wiadomości do folderu Wiadomości-śmieci na podstawie akcji skonfigurowanej pod kątem spamu lub werdyktu wyłudzania informacji w zasadach ochrony przed spamem.

Aby uzyskać więcej informacji na temat blokad w Exchange Online, zobacz [In-Place Hold and Litigation Hold in Exchange Online (Blokada w miejscu i blokada sporów w Exchange Online](/Exchange/security-and-compliance/in-place-and-litigation-holds)).
