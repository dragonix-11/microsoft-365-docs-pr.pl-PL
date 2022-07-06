---
title: Konfigurowanie łącznika do archiwizowania aplikacji Cisco Jabber na danych MS SQL na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania aplikacji Cisco Jabber na danych MS SQL z usługi Veritas na platformie Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm na platformie Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 39a41ab4d89023c263cea43c2ac89a9b174f3235
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636904"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>Konfigurowanie łącznika do archiwizowania aplikacji Cisco Jabber na danych MS SQL

Użyj łącznika Veritas w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane z platformy Cisco Jabber do skrzynek pocztowych użytkowników w organizacji platformy Microsoft 365. Usługa Veritas udostępnia łącznik [Cisco Jabber](https://globanet.com/jabber/) skonfigurowany do przechwytywania elementów z SQL Database MS firmy Jabber, takich jak wiadomości czatu 1:1 i czaty grupowe, a następnie importowania tych elementów na platformę Microsoft 365. Łącznik pobiera dane z SQL Database MS firmy Cisco Jabber, przetwarza je i konwertuje zawartość z konta Cisco Jabber użytkownika na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w usłudze Microsoft 365.

Po zapisaniu danych aplikacji Cisco Jabber w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w usłudze Microsoft 365 przy użyciu łącznika Cisco Jabber może pomóc Organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Omówienie archiwizacji danych Cisco Jabber

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania aplikacji Cisco Jabber na danych MS SQL na platformie Microsoft 365.

![Przepływ pracy archiwizacji danych Cisco Jabber.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmą Cisco w celu skonfigurowania i skonfigurowania aplikacji Cisco Jabber w usłudze MS SQL Database.

2. Raz na 24 godziny elementy Cisco Jabber są kopiowane z SQL Database MS do witryny Veritas Merge1. Łącznik konwertuje również zawartość wiadomości czatu na format wiadomości e-mail.

3. Łącznik Cisco Jabber tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przenosi elementy do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Automatyczne mapowanie użytkownika jako łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* opisanej w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Cisco Jabber w programie MS SQL** jest tworzony w skrzynkach pocztowych użytkownika, a elementy wiadomości są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element Cisco Jabber zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Skonfiguruj SQL Database ms, aby pobrać elementy Jabber przed utworzeniem łącznika w kroku 1. Podczas konfigurowania łącznika Cisco Jabber w kroku 2 określisz ustawienia połączenia dla SQL Database MS. Aby uzyskać więcej informacji, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf)).

- Użytkownikowi, który utworzy łącznik Cisco Jabber w kroku 1 (i ukończy go w kroku 3) musi mieć przypisaną rolę Administracja łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>Krok 1. Konfigurowanie aplikacji Cisco Jabber w łączniku MS SQL

Pierwszym krokiem jest uzyskanie dostępu do **łączników danych** w portalu zgodności i utworzenie łącznika dla aplikacji Cisco Jabber na danych MS SQL.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com/), a następnie kliknij pozycję **Łączniki** >  danych **Cisco Jabber w usłudze MS SQL**.

2. Na stronie Opis produktu **Cisco Jabber w witrynie MS SQL** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie aplikacji Cisco Jabber w łączniku MS SQL w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie aplikacji Cisco Jabber w łączniku MS SQL w witrynie Veritas Merge1. Aby uzyskać informacje o sposobie konfigurowania aplikacji Cisco Jabber w łączniku MS SQL, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika dotyczący łączników innych firm).](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf)

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj następujące kroki:

1. Na stronie **Map Cisco Jabber on MS SQL users to Microsoft 365 users (Mapowanie aplikacji Cisco Jabber na użytkowników MS SQL do użytkowników platformy Microsoft 365** ) włącz automatyczne mapowanie użytkowników. Elementy Cisco Jabber w usłudze MS SQL zawierają właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem platformy Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Krok 4. Monitorowanie łącznika Cisco Jabber

Po utworzeniu aplikacji Cisco Jabber w łączniku MS SQL możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz pozycję **Cisco Jabber w łączniku MS SQL** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
