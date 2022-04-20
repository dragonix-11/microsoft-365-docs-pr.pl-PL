---
title: Konfigurowanie łącznika w celu archiwizacji aplikacji Cisco Jabber w usłudze MS SQL danych w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania aplikacji Cisco Jabber w usłudze MS SQL danych z usługi Veritas w Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 691b27b59b6ade98523f0324e22e0e0cb533fabd
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946753"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>Konfigurowanie łącznika w celu archiwizacji aplikacji Cisco Jabber w usłudze MS SQL danych

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane z platformy Cisco Jabber do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [Cisco Jabber](https://globanet.com/jabber/) skonfigurowany do przechwytywania elementów z SQL Database MS firmy Jabber, takich jak wiadomości czatu 1:1 i czaty grupowe, a następnie importowanie tych elementów do Microsoft 365. Łącznik pobiera dane z SQL Database MS firmy Cisco Jabber, przetwarza je i konwertuje zawartość z konta Cisco Jabber użytkownika na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po zapisaniu danych aplikacji Cisco Jabber w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Za pomocą łącznika Cisco Jabber do importowania i archiwizowania danych w Microsoft 365 może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Omówienie archiwizacji danych Cisco Jabber

W poniższym omówieniu wyjaśniono proces korzystania z łącznika do archiwizowania aplikacji Cisco Jabber w usłudze MS SQL danych w Microsoft 365.

![Przepływ pracy archiwizacji danych Cisco Jabber.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmą Cisco w celu skonfigurowania i skonfigurowania aplikacji Cisco Jabber w usłudze MS SQL Database.

2. Raz na 24 godziny elementy Cisco Jabber są kopiowane z SQL Database MS do witryny Veritas Merge1. Łącznik konwertuje również zawartość wiadomości czatu na format wiadomości e-mail.

3. Łącznik Cisco Jabber tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przenosi elementy do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Automatyczne mapowanie użytkownika jako łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* opisanej w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Cisco Jabber w usłudze MS SQL** jest tworzony w skrzynkach pocztowych użytkownika, a elementy wiadomości są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element Cisco Jabber zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Skonfiguruj SQL Database ms, aby pobrać elementy Jabber przed utworzeniem łącznika w kroku 1. Podczas konfigurowania łącznika Cisco Jabber w kroku 2 określisz ustawienia połączenia dla SQL Database MS. Aby uzyskać więcej informacji, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf)).

- Użytkownik, który tworzy łącznik Cisco Jabber w kroku 1 (i kończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>Krok 1. Konfigurowanie łącznika Cisco Jabber w usłudze MS SQL

Pierwszym krokiem jest dostęp do **łączników danych** w portalu zgodności i utworzenie łącznika dla aplikacji Cisco Jabber w usłudze MS SQL danych.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/), a następnie kliknij pozycję **Łączniki** >  **danychCisco Jabber w witrynie MS SQL**.

2. Na stronie **Opis produktu Cisco Jabber w witrynie MS SQL** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Cisco Jabber w usłudze MS SQL w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Cisco Jabber w usłudze MS SQL w witrynie Veritas Merge1. Aby uzyskać informacje o sposobie konfigurowania aplikacji Cisco Jabber w łączniku ms SQL, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj następujące kroki:

1. Na stronie **Map Cisco Jabber on MS SQL users to Microsoft 365 users (Mapuj aplikację Cisco Jabber w usłudze MS SQL użytkowników do Microsoft 365 użytkowników**) włącz automatyczne mapowanie użytkowników. Elementy aplikacji Cisco Jabber w usłudze MS SQL obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Krok 4. Monitorowanie łącznika Cisco Jabber

Po utworzeniu aplikacji Cisco Jabber w łączniku ms SQL możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik **Cisco Jabber w usłudze MS SQL**, aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
