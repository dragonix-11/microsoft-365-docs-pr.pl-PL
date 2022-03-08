---
title: Konfigurowanie łącznika do wtyczki Webex Teams danych w programie Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z łącznika Webex Teams Veritas w programie Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w programie Microsoft 365 w celu zarządzania danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze standardami prawnie, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 0906156f5c0c796deaa5bd72738813d912e30b47
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312309"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Konfigurowanie łącznika do archiwizowania danych programu Webex Teams webex

Za pomocą łącznika veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane z programu Webex Teams do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [webex Teams](https://globanet.com/webex-teams/), który jest skonfigurowany do przechwytywania elementów komunikacji programu Webex Teams i importowania ich do Microsoft 365. Łącznik konwertuje zawartość z programu Webex Teams, taką jak czaty 1:1, konwersacje grupowe, konwersacje w kanale i załączniki z konta programu Webex Teams organizacji na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po zapisaniu danych programu Webex Teams w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak Zawieszenie w związku z postępowaniem sądowym, Zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie Teams Webex w programie Microsoft 365 za pomocą łącznika Webex Microsoft 365 może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-webex-teams-data"></a>Omówienie archiwizowania danych w witrynie Webex Teams danych

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych programu Webex Teams w programie Microsoft 365.

![Archiwizowanie przepływu pracy dla programu Webex Teams danych.](../media/WebexTeamsConnectorWorkflow.png)

1. Organizacja współpracuje z witryną Webex Teams, aby skonfigurować witrynę internetową Webex Teams webex.

2. Co 24 godziny elementy witryny Webex Teams są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy wtyczki Webex Teams na format wiadomości e-mail.

3. Łącznik webex Teams, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z usługą Veritas Merge1 każdego dnia i przenosi elementy oprogramowania Webex Teams do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Webex Teams**, a elementy są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy element Teams Webex zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika tego elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://globanet.com/ms-connectors-contact). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Utwórz aplikację w witrynie, [https://developer.webex.com/](https://developer.webex.com) aby pobrać dane z konta usługi Webex Teams konta. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

   Podczas tworzenia tej aplikacji platforma Webex generuje zestaw unikatowych poświadczeń. Te poświadczenia są używane w kroku 2 podczas konfigurowania łącznika Webex Teams w witrynie Globalne scalanie1.

- Użytkownik, który tworzy łącznik wtyczki Webex Teams w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-webex-teams-connector"></a>Krok 1. Konfigurowanie łącznika Webex Teams Webex

Pierwszym krokiem jest uzyskanie dostępu do łączników danych **i skonfigurowanie** łącznika [Webex Teams](https://globanet.com/webex-teams/) webex.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki** **danychWebex** >  Teams.

2. Na stronie **Webex Teams** opis produktu kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika webex Teams w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Webex Teams w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Webex Teams, zobacz Przewodnik użytkownika do [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie Teams Webex, aby Microsoft 365 użytkowników**, włącz automatyczne mapowanie użytkowników. Elementy webex Teams mają właściwość o nazwie *Email*, która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Krok 4. Monitorowanie łącznika Webex Teams Webex

Po utworzeniu łącznika Webex Teams można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki**, a następnie wybierz **łącznik Webex Teams**, aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.