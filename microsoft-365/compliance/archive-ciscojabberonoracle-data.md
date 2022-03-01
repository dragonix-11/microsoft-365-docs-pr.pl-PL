---
title: Konfigurowanie łącznika do archiwizowania cisco Jabber w danych Oracle w programie Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik w aplikacji Centrum zgodności platformy Microsoft 365 w celu importowania i archiwizowania danych z cisco Jabber w oracle w celu Microsoft 365.
ms.openlocfilehash: 6d38abfbbb8380a6f7eb5bc617460a1a3b8e6e73
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020712"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-oracle-data"></a>Konfigurowanie łącznika do archiwizowania Cisco Jabber na danych Oracle

Za pomocą łącznika Veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane z platformy Cisco Jabber na platformie Oracle do skrzynek pocztowych użytkowników Microsoft 365 organizacji. Veritas udostępnia [łącznik Cisco Jabber on Oracle](https://www.veritas.com/insights/merge1/jabber), który jest skonfigurowany do regularnego przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik konwertuje zawartość, na przykład pliki i operacje na plikach, komentarze i zawartość udostępnioną z Cisco Jabber w systemie Oracle, na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po przechowywaniu danych Cisco Jabber w oracle w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika Cisco Jabber on Oracle może pomóc Twojej organizacji zachować zgodność z zasadami rządowymi i regulami regulacyjną.

## <a name="overview-of-archiving-cisco-jabber-on-oracle-data"></a>Omówienie archiwizowania cisco jabber w danych Oracle

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych Cisco Jabber w oracle w programie Microsoft 365.

![Zarchiwizowanie przepływu pracy dla Cisco Jabber w danych Oracle.](../media/CiscoJabberOnOracleConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmą Cisco Jabber w witrynie Oracle w celu skonfigurowania i skonfigurowania cisco Jabber w witrynie Oracle.

2. Co 24 godziny element Cisco Jabber w programie Oracle jest kopiowany do witryny Veritas Merge1. Łącznik konwertuje również wtyczkę Cisco Jabber w elementach Oracle na format wiadomości e-mail.

3. Łącznik Cisco Jabber on Oracle, który tworzysz w Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła zawartość typu Jabber do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Cisco Jabber w** programie Oracle, a elementy są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy element elementu Jabber zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto Merge1 dla łączników Microsoft. W tym celu skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/content/support/en_US). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik Cisco Jabber na łączniku Oracle w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w programie Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-oracle-connector"></a>Krok 1. Konfigurowanie łącznika Cisco Jabber na łączniku Oracle

Pierwszym krokiem jest uzyskanie dostępu do strony **Łączniki** danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych typu Jabber.

1. Przejdź do łączników <https://compliance.microsoft.com> danych, a **następnie** kliknij pozycję **Łączniki danychCisco** >  Jabber w oracle.

2. Na stronie **Cisco Jabber on Oracle product description (Opis produktu Firmy Oracle** ) kliknij pozycję **Add connector (Dodaj łącznik**).

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-cisco-jabber-on-oracle-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie przełącznika Cisco Jabber w witrynie Oracle w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Cisco Jabber on Oracle w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Cisco Jabber on Oracle, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20Oracle%20User%20Guide.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników usługi Cisco Jabber na Microsoft 365 Oracle** włącz automatyczne mapowanie użytkowników. Elementy Cisco Jabber on Oracle zawierają właściwość *o nazwie Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-cisco-jabber-on-oracle-connector"></a>Krok 4. Monitorowanie wtyczki Cisco Jabber na łączniku Oracle

Po utworzeniu łącznika Cisco Jabber na łączniku Oracle możesz wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com/> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **Cisco Jabber on Oracle** , aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
