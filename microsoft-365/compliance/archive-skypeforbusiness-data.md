---
title: Konfigurowanie łącznika do archiwizowania Skype dla firm danych w Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik w aplikacji Centrum zgodności platformy Microsoft 365 w celu importowania i archiwizowania danych z Skype dla firm do Microsoft 365.
ms.openlocfilehash: a783ad4bea9b06fcef3f7da4f67a98c17310a38e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314608"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>Konfigurowanie łącznika do archiwizowania Skype dla firm danych

Za pomocą łącznika veritas w centrum Centrum zgodności platformy Microsoft 365 importowania i archiwizowania danych z platformy Skype dla firm do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [Skype dla firm](https://www.veritas.com/en/au/insights/merge1/skype-for-business), który jest skonfigurowany do regularnego przechwytywania elementów ze źródła danych innej firmy i importowania ich do Microsoft 365. Łącznik konwertuje zawartość, na przykład wiadomości między użytkownikami, rozmowy trwałe i wiadomości z konferencji z programu Skype dla firm na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po Skype dla firm przechowywanych w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności z przepisami Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie Skype dla firm w programie Microsoft 365 za pomocą łącznika sieci w celu zachowania zgodności z zasadami rządowymi i przepisami regulowymi.

## <a name="overview-of-archiving-skype-for-business-data"></a>Omówienie archiwizowania Skype dla firm danych

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania Skype dla firm danych w Microsoft 365.

![Zarchiwizowanie przepływu Skype dla firm danych.](../media/SkypeforBusinessConnectorWorkflow.png)

1. Organizacja współpracuje z Skype dla firm, aby skonfigurować witrynę sieci Skype dla firm sieci Web.

2. Elementy są kopiowane Skype dla firm do witryny Veritas Merge1 co 24 godziny. Łącznik konwertuje także elementy Skype dla firm na format wiadomości e-mail.

3. Łącznik Skype dla firm, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, codziennie łączy się z witryną Veritas Merge1 i przesyła zawartość z usługi Skype dla firm do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony **podfolder** w folderze Skrzynka odbiorcza Skype dla firm, a elementy są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy Skype dla firm zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika tego elementu.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto Merge1 dla łączników Microsoft. W tym celu skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact.html). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który utworzy łącznik Skype dla firm w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-skype-for-business-connector"></a>Krok 1. Konfigurowanie łącznika Skype dla firm danych

Pierwszym krokiem jest uzyskanie dostępu do strony  łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla Skype dla firm danych.

1. Przejdź do łączników <https://compliance.microsoft.com> **danych** >  **i kliknij Skype dla firm**.

2. Na stronie **Skype dla firm** opis produktu kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie Skype dla firm w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Skype dla firm w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Skype dla firm, zobacz Podręcznik użytkownika [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie Skype dla firm użytkowników do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Skype dla firm mają właściwość *o nazwie Poczta* e-mail, która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>Krok 4. Monitorowanie łącznika Skype dla firm danych

Po utworzeniu łącznika Skype dla firm można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com/> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki**, a następnie **Skype dla firm łącznik,** aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
