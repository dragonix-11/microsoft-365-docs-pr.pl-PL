---
title: Automatyczne czyszczenie zerowej godziny w programie Microsoft Defender dla Office 365
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
description: Automatyczne czyszczenie zerowej godziny (ZAP) powoduje ponowne przeniesienie dostarczonych wiadomości ze skrzynki pocztowej programu Exchange Online do folderu wiadomości-śmieci lub kwarantanny, w przypadku których wiadomość jest spamem, próbą wyłudzenia informacji lub która zawiera złośliwe oprogramowanie po dostarczeniu.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a48f5eb1d45af16ab275c16d2965dc9a578d9312
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009801"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Automatyczne czyszczenie zerowej godziny (ZAP) w programie Exchange Online

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Podstawowe informacje o godzinie automatycznego przeczyszczania (ZAP)

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w programie Exchange Online automatyczne przeczyszczanie bezgodzinne to funkcja ochrony poczty e-mail, która wykrywa i wykrywa złośliwe wiadomości służące do wyłudzania informacji, spamu lub złośliwego oprogramowania, które już zostały dostarczone do skrzynek pocztowych programu Exchange Online.

Zap nie działa w środowiskach autonomicznych usługi Exchange Online Protection (EOP), które chronią lokalne skrzynki pocztowe Exchange pocztowych.

## <a name="how-zap-works"></a>Jak działa zap

Podpisy spamu i złośliwego oprogramowania są codziennie aktualizowane w usłudze w czasie rzeczywistym. Użytkownicy mogą jednak nadal otrzymywać złośliwe wiadomości z różnych powodów, w tym w przypadku, gdy zawartość została zweryfikowana po dostarczaniu jej do użytkowników. Zap rozwiązuje ten problem, stale monitorując aktualizacje podpisów spamu i złośliwego oprogramowania w usłudze. Zap umożliwia znajdowanie i usuwanie wiadomości, które znajdują się już w skrzynce pocztowej użytkownika.

Akcja ZAP dla użytkownika jest bezproblemowa; nie są oni powiadomieni, jeśli wiadomość zostanie wykryta i przeniesiona.

[Sejf listy nadawców](create-safe-sender-lists-in-office-365.md), reguły przepływu poczty (nazywane także regułami transportu), reguły skrzynki odbiorczej lub dodatkowe filtry mają pierwszeństwo przed zap zapami. Podobnie jak w przypadku przepływu poczty e-mail, oznacza to, że nawet jeśli usługa określi, że dostarczona wiadomość wymaga zap, nie zostanie ona w związku z konfiguracją bezpiecznych nadawców. Jest to jeszcze jeden powód, dla którego należy zachować ostrożność przy konfigurowaniu wiadomości, aby pominąć filtrowanie.

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Automatyczne czyszczenie o zerowej godzinie (ZAP) dla złośliwego oprogramowania

W **przypadku przeczytanych lub nieprzeczytanych wiadomości** , które po dostarczeniu zawierają złośliwe oprogramowanie, program ZAP podda wiadomość zawierającą załącznik złośliwego oprogramowania. Domyślnie tylko administratorzy mogą wyświetlać wiadomości z kwarantanną złośliwego oprogramowania i zarządzać nimi. Jednak administratorzy mogą tworzyć zasady kwarantanny  i używać ich w celu określenia, co użytkownicy mogą robić w przypadku wiadomości poddanych kwarantannie jako złośliwe oprogramowanie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

W zasadach ochrony przed złośliwym oprogramowaniem zap dla złośliwego oprogramowania jest domyślnie włączone. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w uchcie EOP](configure-anti-malware-policies.md).

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Automatyczne przeczyszczanie bez godzin w celu wyłudzania informacji

W **przypadku przeczytanych** lub nieprzeczytanych wiadomości zidentyfikowanych jako próby wyłudzenia informacji po dostarczeniu wynik zap zależy od akcji skonfigurowanej  na podstawie werdyktu filtrowania wiadomości wyłudzających informacje w obowiązujących zasadach ochrony przed spamem. Dostępne akcje dyktowania filtrowania na rzecz wyłudzania informacji i ich możliwych wyników za działania zap opisano na poniższej liście:

- **Dodaj nagłówek X**, wiersz tematu Przed **tekstem****,** Przekieruj wiadomość na adres e-mail **, Usuń** wiadomość: ZAP nie ma nic przeciwko wiadomości.

- **Przenieś wiadomość do folderu Wiadomości-śmieci**: zap przenosi tę wiadomość do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci Exchange Online pocztowych w programie Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Poddaj wiadomość** kwarantannie: zap podda wiadomość kwarantannie.

W zasadach ochrony przed spamem jest domyślnie włączone zap dla wyłudzania informacji, a domyślną akcją dla werdyktu filtrowania wiadomości wyłudzających informacje jest kwarantanna **wiadomości, co** oznacza, że zap dla kwarantanny służącej do wyłudzania informacji jest domyślnie sprawdzana.

Aby uzyskać więcej informacji na temat konfigurowania werdyktów filtrowania spamu, zobacz Konfigurowanie zasad ochrony [przed spamem w programie Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Automatyczne przeczyszczanie bez godzin w celu wyłudzania informacji o wysokiej pewności

W **przypadku wiadomości przeczytanych lub nieprzeczytanych** , które po dostarczeniu są oznaczone jako próby wyłudzenia informacji o wysokiej pewności, program ZAP podda wiadomość kwarantannie. Domyślnie tylko administratorzy mogą wyświetlać wiadomości o wysokiej ufności w kwarantannie i zarządzać nimi. Jednak administratorzy mogą tworzyć zasady kwarantanny  i używać ich w celu określenia, co użytkownicy mogą robić w wiadomościach poddanych kwarantannie jako próby wyłudzenia dużej pewności. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

Zap dla funkcji wysokiej ufności jest domyślnie włączona. Aby uzyskać więcej informacji, zobacz [Domyślnie bezpieczne w aplikacji Office 365](secure-by-default.md).

### <a name="zero-hour-auto-purge-zap-for-spam"></a>Automatyczne czyszczenie o zerowej godzinie dla spamu

W **przypadku nieprzeczytanych** wiadomości zidentyfikowanych jako spam po dostarczeniu wynik zap zależy od akcji skonfigurowanej werdyktu  filtrowania spamu w obowiązujących zasadach ochrony przed spamem. Dostępne akcje werdyktu filtrowania dotyczące spamu i ich możliwych wyników zap opisano na poniższej liście:

- **Dodaj nagłówek X**, wiersz tematu Przed **tekstem****,** Przekieruj wiadomość na adres e-mail **, Usuń** wiadomość: ZAP nie ma nic przeciwko wiadomości.

- **Przenieś wiadomość do folderu Wiadomości-śmieci**: zap przenosi tę wiadomość do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci Exchange Online pocztowych w programie Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Poddaj wiadomość** kwarantannie: zap podda wiadomość kwarantannie. Domyślnie użytkownicy końcowi mogą wyświetlać wiadomości poddanych kwarantannie antyspamowej, do których są adresatami, i zarządzać nimi. Jednak administratorzy mogą tworzyć zasady kwarantanny  i używać ich w celu określenia, co użytkownicy mogą robić w przypadku wiadomości poddanych kwarantannie jako spam. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

W zasadach ochrony przed spamem jest domyślnie włączone zap spamu, a domyślną akcją  werdykt filtrowania spamu jest Przenoszenie wiadomości do folderu Wiadomości-śmieci **, co** oznacza, że zap spamu domyślnie przenosi nieprzeczytane wiadomości do folderu Wiadomości-śmieci.

Aby uzyskać więcej informacji na temat konfigurowania werdyktów filtrowania spamu, zobacz Konfigurowanie zasad ochrony [przed spamem w programie Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Zagadnienia dotyczące zerowej godziny automatycznego przeczyszczania programu Microsoft Defender dla systemu Office 365

Zap nie będzie poddać kwarantannie żadnych wiadomości, które [](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) są w trakcie procesu dostarczania dynamicznego w skanowanie zasad załączników programu Sejf, ani tam, gdzie filtrowanie złośliwego oprogramowania usługi EOP już zamieniło załącznik na plik Text.txtmalware.**** Jeśli dla tego typu wiadomości odebrano sygnał wyłudzania informacji lub spamu, a werdykt filtrowania w zasadach ochrony przed spamem jest ustawiony tak, aby podjąć określone działanie w  związku z wiadomością (Przenieś do wiadomości-śmieci, Przekieruj, Usuń lub Poddaj kwarantannie), program ZAP domyślnie ustawi akcję "Przenieś do wiadomości-śmieci".

## <a name="how-to-see-if-zap-moved-your-message"></a>Jak sprawdzić, czy zap przeniesiono wiadomość

Aby ustalić, czy zap przeniesiono wiadomość, dostępne są następujące opcje:

- **Liczba wiadomości**: Użyj widoku [Przepływ](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) poczty w raporcie o stanie przepływu poczty, aby sprawdzić liczbę wiadomości, których dotyczy problem z zapami w określonym zakresie dat.
- **Szczegóły wiadomości**: Za pomocą [Eksploratora zagrożeń (i wykrywania](threat-explorer.md) w czasie rzeczywistym)  możesz filtrować wszystkie zdarzenia wiadomości e-mail według wartości **ZAP** dla **kolumny Akcja** dodatkowa.

**Uwaga**: Zap nie jest rejestrowane w dziennikach inspekcji Exchange jako akcja systemowa.

## <a name="zero-hour-auto-purge-zap-faq"></a>Automatyczne przeczyszczanie bez godzin (ZAP) — często zadawane pytania

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Co się stanie, jeśli legalna wiadomość zostanie przeniesiona do folderu Wiadomości-śmieci?

Należy postępować zgodnie z normalnym procesem raportowania dla [wyników fałszywie dodatnich](report-junk-email-messages-to-microsoft.md). Jedynym powodem, dla którego wiadomość zostałaby przeniesiona ze skrzynki odbiorczej do folderu Wiadomości-śmieci, jest to, że usługa ustali, że wiadomość jest spamem lub złośliwym.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Co zrobić, jeśli użyję folderu kwarantanny zamiast folderu Wiadomości-śmieci?

Zap podejmie działanie na wiadomości na podstawie konfiguracji zasad ochrony przed spamem w sposób opisany wcześniej w tym artykule.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Co zrobić, jeśli korzystam z listy bezpiecznych nadawców, reguł przepływu poczty e-mail lub list dozwolonych/zablokowanych nadawców?

Sejf, reguły przepływu poczty e-mail lub blokowanie i zezwalanie na ustawienia organizacyjne mają pierwszeństwo. Te wiadomości są wykluczone z zap, ponieważ usługa robi to, co skonfigurowano. Jest to jeszcze jeden powód, dla którego należy zachować ostrożność przy konfigurowaniu wiadomości, aby pominąć filtrowanie.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Jakie są wymagania licencyjne dotyczące działania automatycznego przeczyszczania bez godzin?

Nie ma żadnych ograniczeń dotyczących licencji. Zap działa we wszystkich skrzynkach pocztowych hostowanych Exchange online. Zap nie działa w środowiskach autonomicznych usługi Exchange Online Protection (EOP), które chronią lokalne skrzynki pocztowe Exchange pocztowych.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Co zrobić, jeśli wiadomość zostanie przeniesiona do innego folderu (np. do reguł skrzynki odbiorczej)?

Automatyczne czyszczenie o zerowej godzinie nadal działa, o ile wiadomość nie została usunięta albo jeśli nie zastosowano jeszcze tej samej lub silniejszej akcji. Jeśli na przykład zasady ochrony przed wyłudzaniem informacji są ustawione w kwarantannie, a wiadomość znajduje się już w folderze Wiadomości-śmieci, program ZAP podejmie działania w celu kwarantanny wiadomości.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Jaki wpływ na skrzynki pocztowe wstrzymywane są zap?

Automatyczne czyszczenie zerowej godziny będzie wstrzymywać wiadomości ze skrzynek pocztowych w kwarantannie. Zap może przenosić wiadomości do folderu Wiadomości-śmieci na podstawie akcji skonfigurowanej na podstawie werdyktu spamu lub próby wyłudzenia informacji w zasadach ochrony przed spamem.

Aby uzyskać więcej informacji na temat blokady w Exchange Online, zobacz Blokady [w](/Exchange/security-and-compliance/in-place-and-litigation-holds) miejscu i Zawieszenie w związku z postępowaniem sądowym w Exchange Online.
