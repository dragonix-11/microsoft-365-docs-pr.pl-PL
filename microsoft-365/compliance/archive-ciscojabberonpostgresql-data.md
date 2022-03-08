---
title: Konfigurowanie łącznika do archiwizowania danych Cisco Jabber w raportach PostgreSQL w Microsoft 365
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Dowiedz się, jak skonfigurować łącznik w aplikacji Centrum zgodności platformy Microsoft 365 i archiwizować dane z Cisco Jabber w  technologii PostgreSQL w celu Microsoft 365.
ms.openlocfilehash: 946a43155ed085575e9aef97b04f0828338963e5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328837"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>Konfigurowanie łącznika do archiwizowania cisco Jabber w danych PostgreSQL

Za pomocą łącznika Veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane z platformy Cisco Jabber do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [Cisco Jabber on PostgreSQL](https://www.veritas.com/insights/merge1/jabber), który jest skonfigurowany do regularnego przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik konwertuje zawartość, taką jak wiadomości, czaty i udostępnioną zawartość z Cisco Jabber w postgreSQL, na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po przechowywaniu danych Cisco Jabber w chmurze PostgreSQL w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą przełącznika Cisco Jabber w łączniku PostgreSQL może ułatwić twojej organizacji zgodność z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>Omówienie archiwizowania danych Cisco Jabber w danych PostgreSQL

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych Cisco Jabber w tabelach PostgreSQL w programie Microsoft 365.

![Zarchiwizowanie przepływu pracy dla Cisco Jabber w danych PostgreSQL.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. Twoja organizacja współpracuje z cisco Jabber w witrynie PostgreSQL w celu skonfigurowania i skonfigurowania cisco Jabber w witrynie PostgreSQL.

2. Co 24 godziny usługa Cisco Jabber w elementach PostgreSQL jest kopiowana do witryny Veritas Merge1. Łącznik konwertuje również wtyczkę Cisco Jabber w elementach PostgreSQL na format wiadomości e-mail.

3. Łącznik Cisco Jabber on PostgreSQL, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła zawartość oprogramowania Jabber do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Cisco Jabber on PostgreSQL** , a elementy są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy element elementu Jabber zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto Merge1 dla łączników Microsoft. W tym celu skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/content/support/en_US). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik Cisco Jabber na łączniku PostgreSQL w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>Krok 1. Konfigurowanie wtyczki Cisco Jabber na łączniku PostgreSQL

Pierwszym krokiem jest uzyskanie dostępu do strony **Łączniki** danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych typu Jabber.

1. Przejdź do łączników <https://compliance.microsoft.com> danych, a **następnie** &gt; **kliknij pozycję Cisco Jabber w postgreSQL**.

2. Na stronie **Cisco Jabber on PostgreSQL** product description (Opis produktu: Cisco Jabber) kliknij pozycję **Add connector (Dodaj łącznik**).

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie cisco Jabber w witrynie Veritas Merge1 w witrynie PostgreSQL

Drugim krokiem jest skonfigurowanie łącznika Cisco Jabber na łączniku PostgreSQL w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Cisco Jabber na łączniku PostgreSQL, zobacz Przewodnik użytkownika do [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników usługi Cisco Jabber on PostgreSQL do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Cisco Jabber on PostgreSQL zawierają właściwość *o nazwie Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>Krok 4. Monitorowanie wtyczki Cisco Jabber na łączniku PostgreSQL

Po utworzeniu łącznika Cisco Jabber na stronie PostgreSQL można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com/> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz wtyczkę **Cisco Jabber w łączniku PostgreSQL** , aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
