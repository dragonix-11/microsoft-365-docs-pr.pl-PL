---
title: Konfigurowanie łącznika do archiwizowania danych Cisco Jabber w usłudze PostgreSQL w Microsoft 365
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak skonfigurować łącznik i użyć go w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane z aplikacji Cisco Jabber w usłudze PostgreSQL, aby Microsoft 365.
ms.openlocfilehash: a435ee321d14c6eddf445f6dddcfdecc86c1963b
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318817"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>Konfigurowanie łącznika w celu archiwizowania danych aplikacji Cisco Jabber w usłudze PostgreSQL

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane z platformy Cisco Jabber do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [Cisco Jabber on PostgreSQL](https://www.veritas.com/insights/merge1/jabber), który jest skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie) i importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość, taką jak wiadomości, czaty i zawartość udostępnioną z aplikacji Cisco Jabber w usłudze PostgreSQL, na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po przechowywaniu danych aplikacji Cisco Jabber w usłudze PostgreSQL w skrzynkach pocztowych użytkowników można zastosować funkcje Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Cisco Jabber on PostgreSQL może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>Omówienie archiwizacji danych Cisco Jabber w serwisie PostgreSQL

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych Cisco Jabber on PostgreSQL w Microsoft 365.

![Przepływ pracy archiwizacji danych Cisco Jabber w usłudze PostgreSQL.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmą Cisco Jabber w serwisie PostgreSQL, aby skonfigurować i skonfigurować witrynę Cisco Jabber w witrynie PostgreSQL.

2. Raz na 24 godziny elementy Cisco Jabber w witrynie PostgreSQL są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy Cisco Jabber w usłudze PostgreSQL na format wiadomości e-mail.

3. Łącznik Cisco Jabber on PostgreSQL tworzony w portalu zgodności, codziennie łączy się z witryną Veritas Merge1 i przesyła zawartość jabbera do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Cisco Jabber on PostgreSQL** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każdy element Jabber zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto Merge1 dla łączników firmy Microsoft. W tym celu skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/en_US). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik Cisco Jabber on PostgreSQL w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>Krok 1. Konfigurowanie łącznika Cisco Jabber on PostgreSQL

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla danych Jabber.

1. Przejdź do strony <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** &gt; danych **Cisco Jabber w aplikacji PostgreSQL**.

2. Na stronie Opis produktu **Cisco Jabber on PostgreSQL** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie aplikacji Cisco Jabber na serwerze PostgreSQL w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Cisco Jabber on PostgreSQL w witrynie Veritas Merge1. Aby uzyskać informacje o sposobie konfigurowania łącznika Cisco Jabber on PostgreSQL, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika łączników innych firm).](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf)

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj następujące kroki:

1. Na stronie **Map Cisco Jabber on PostgreSQL users to Microsoft 365 users (Mapuj użytkowników Aplikacji Cisco Jabber w usłudze PostgreSQL), aby Microsoft 365 użytkowników**, włącz automatyczne mapowanie użytkowników. Elementy aplikacji Cisco Jabber on PostgreSQL zawierają właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>Krok 4. Monitorowanie łącznika Cisco Jabber on PostgreSQL

Po utworzeniu łącznika Cisco Jabber on PostgreSQL możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com/> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik **Cisco Jabber w usłudze PostgreSQL** , aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
