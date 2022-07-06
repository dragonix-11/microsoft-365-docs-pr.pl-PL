---
title: Konfigurowanie łącznika do danych usługi Webex Teams na platformie Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z łącznika usługi Webex Teams w usłudze Veritas na platformie Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w usłudze Microsoft 365, dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania w celu zarządzania danymi innych firm w organizacji.
ms.openlocfilehash: 1a1823c4928ac310aa3bbfe7b5c6e0a26408f964
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621276"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Konfigurowanie łącznika do archiwizowania danych usługi Webex Teams

Użyj łącznika Veritas w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane z usługi Webex Teams do skrzynek pocztowych użytkowników w organizacji platformy Microsoft 365. Usługa Veritas udostępnia łącznik [usługi Webex Teams](https://globanet.com/webex-teams/) , który jest skonfigurowany do przechwytywania elementów komunikacji usługi Webex Teams i importowania ich na platformę Microsoft 365. Łącznik konwertuje zawartość z usługi Webex Teams, taką jak czaty 1:1, konwersacje grupowe, konwersacje kanałowe i załączniki z konta usługi Webex Teams w organizacji, na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika na platformie Microsoft 365.

Po zapisaniu danych usługi Webex Teams w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w usłudze Microsoft 365 przy użyciu łącznika usługi Webex Teams może pomóc Twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-webex-teams-data"></a>Omówienie archiwizacji danych usługi Webex Teams

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych usługi Webex Teams na platformie Microsoft 365.

![Przepływ pracy archiwizacji danych usługi Webex Teams.](../media/WebexTeamsConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą Webex Teams w celu skonfigurowania i skonfigurowania witryny usługi Webex Teams.

2. Raz na 24 godziny elementy usługi Webex Teams są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy usługi Webex Teams na format wiadomości e-mail.

3. Łącznik usługi Webex Teams tworzony w portalu zgodności, codziennie łączy się z usługą Veritas Merge1 i przesyła elementy usługi Webex Teams do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Webex Teams** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każdy element usługi Webex Teams zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://globanet.com/ms-connectors-contact). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Utwórz aplikację pod adresem, [https://developer.webex.com/](https://developer.webex.com) aby pobrać dane z konta usługi Webex Teams. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji, zobacz [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Podczas tworzenia tej aplikacji platforma Webex generuje zestaw unikatowych poświadczeń. Te poświadczenia są używane w kroku 2 podczas konfigurowania łącznika usługi Webex Teams w witrynie Global Merge1.

- Użytkownikowi, który tworzy łącznik usługi Webex Teams w kroku 1 (i kończy go w kroku 3) musi mieć przypisaną rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-webex-teams-connector"></a>Krok 1. Konfigurowanie łącznika usługi Webex Teams

Pierwszym krokiem jest uzyskanie dostępu do **łączników danych** i skonfigurowanie łącznika [usługi Webex Teams](https://globanet.com/webex-teams/) .

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com/), a następnie kliknij pozycję **Łączniki** >  danych **Webex Teams**.

2. Na stronie Opis produktu **Webex Teams** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika usługi Webex Teams w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika usługi Webex Teams w witrynie Merge1. Aby uzyskać informacje o sposobie konfigurowania łącznika usługi Webex Teams, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj następujące kroki:

1. Na stronie **Mapowanie użytkowników aplikacji Webex Teams na użytkowników platformy Microsoft 365** włącz automatyczne mapowanie użytkowników. Elementy usługi Webex Teams obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem platformy Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Krok 4. Monitorowanie łącznika usługi Webex Teams

Po utworzeniu łącznika usługi Webex Teams możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik **Webex Teams** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.