---
title: Konfigurowanie łącznika do archiwizowania Cisco Jabber na SQL MS w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik, aby importować i archiwizować wtyczkę Cisco Jabber na SQL z veritas w Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 66f09f2fafcd33d8bc73bdaed61b41354e9633f7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319549"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>Konfigurowanie łącznika do archiwizowania Cisco Jabber na SQL MS

Za pomocą łącznika Veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane z platformy Cisco Jabber do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [Cisco Jabber](https://globanet.com/jabber/), który jest skonfigurowany do przechwytywania elementów z usługi MS SQL Database firmy Jabber, takich jak wiadomości czatu 1:1 i czatów grupowych, a następnie importowania tych elementów do Microsoft 365. Łącznik pobiera dane z serwera MS SQL Database Cisco Jabber, przetwarza je i konwertuje zawartość z konta Cisco Jabber użytkownika na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po przechowywaniu danych Cisco Jabber w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika Cisco Jabber może ułatwić organizacji pozostawanie w zachowuj zgodność z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Omówienie archiwizowania danych Cisco Jabber

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania cisco Jabber na SQL MS w Microsoft 365.

![Zarchiwizowanie przepływu pracy dla danych Cisco Jabber.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmą Cisco w celu skonfigurowania i skonfigurowania cisco Jabber na komputerze SQL DATABASE.

2. Co 24 godziny elementy Cisco Jabber są kopiowane z witryny Ms SQL Database do witryny Veritas Merge1. Łącznik konwertuje także treść wiadomości czatu na format wiadomości e-mail.

3. Łącznik Cisco Jabber tworzyć w usłudze Centrum zgodności platformy Microsoft 365 łączy się z witryną Veritas Merge1 każdego dnia i przenosi elementy do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Automatyczne mapowanie użytkowników jako łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* opisanej w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza Cisco **Jabber** SQL, a elementy wiadomości są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element Cisco Jabber zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Przed utworzeniem łącznika w kroku 1 SQL Database skonfigurować konto ms w celu pobierania elementów jabberu. W kroku 2 określisz ustawienia połączenia dla SQL Database Ms podczas konfigurowania łącznika Cisco Jabber. Aby uzyskać więcej informacji, zobacz Podręcznik użytkownika łączników innej [firmy Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- Użytkownik, który utworzy łącznik Cisco Jabber w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>Krok 1. Konfigurowanie wtyczki Cisco Jabber na łączniku SQL MS

Pierwszym krokiem jest uzyskanie dostępu do łączników danych w centrum Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla cisco Jabber na SQL DANYCH.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/)a następnie kliknij **pozycję Łączniki danychCisco** >  **Jabber na SQL**.

2. Na stronie **Cisco Jabber na stronie SQL** opis produktu firmy Ms kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Cisco Jabber na SQL MS w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie wtyczki Cisco Jabber na SQL MS w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania wtyczki Cisco Jabber na łączniku SQL MS, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurowanie łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie cisco Jabber na SQL ms w** celu Microsoft 365 użytkowników włącz automatyczne mapowanie użytkowników. Elementy SQL Cisco Jabber na komputerze MS zawierają właściwość *o nazwie Email*, która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia i przejdź do strony Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Krok 4. Monitorowanie łącznika Cisco Jabber

Po utworzeniu łącznika Cisco Jabber na SQL MS możesz sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki**, a następnie wybierz **wtyczkę Cisco Jabber** na łączniku SQL MS, aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
