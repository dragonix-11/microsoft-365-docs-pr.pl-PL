---
title: Konfigurowanie łącznika do archiwizowania danych w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z Veritas Na Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 308448087481affae6a1de430c49e084b9ac681b
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020735"
---
# <a name="set-up-a-connector-to-archive-symphony-data"></a>Konfigurowanie łącznika do archiwizowania danych

Za pomocą łącznika veritas w pliku Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Na tej platformie stosowanej w branży usług finansowych jest używana platforma do obsługi wiadomości i współpracy. Veritas udostępnia łącznik [](https://globanet.com/symphony) danych Wi-Centrum zgodności platformy Microsoft 365, który można konfigurować do regularnego przechwytywania elementów ze źródła danych innych firm, a następnie importowania ich do skrzynek pocztowych użytkowników. Łącznik konwertuje zawartość elementu z konta Wi-Mail na format wiadomości e-mail, a następnie importuje ten element do skrzynki pocztowej w Microsoft 365.

Po przechowywaniu komunikacji między użytkownikami w skrzynkach pocztowych użytkowników można stosować funkcje zgodności usługi Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika do importowania i archiwizowania danych w programie Microsoft 365 organizacji zgodnie z zasadami rządowymi i przepisami prawa.

## <a name="overview-of-archiving-symphony-data"></a>Omówienie archiwizowania danych

W poniższym o omówieniem wyjaśniono proces używania łącznika danych do archiwizowania komunikacji w programie Microsoft 365.

![Archiwizowanie przepływu pracy.](../media/SymphonyConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmaMich w celu skonfigurowania i skonfigurowania witryny Firmy.

2. Raz na 24 godziny wiadomości czatu od Ciesiego są kopiowane do witryny Veritas Merge1. Łącznik konwertuje także treść wiadomości czatu na format wiadomości e-mail.

3. Łącznik tworzymy w usłudze Centrum zgodności platformy Microsoft 365 i każdego dnia łączy się z witryną scalania Veritas i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaimnuje przekonwertowane elementy wiadomości do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w kroku 3. W skrzynkach pocztowych użytkowników zostanie utworzony nowy podfolder  w folderze Skrzynka odbiorcza, a elementy wiadomości zostaną zaimportowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każda wiadomość czatu zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://globanet.com/ms-connectors-contact). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Użytkownik, który tworzy łącznik w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-symphony-connector"></a>Krok 1. Konfigurowanie łącznika Nasadki

Pierwszym krokiem jest uzyskanie dostępu do strony  łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych Łowecz.

1. Przejdź do [https://compliance.microsoft.com](https://compliance.microsoft.com/), a następnie kliknij pozycję **Łączniki danychSymphony** > .

2. Na stronie **Description (Opis** produktu) kliknij pozycję **Add connector (Dodaj łącznik**).

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="configure-the-symphony-connector-on-the-veritas-merge1-site"></a>Konfigurowanie łącznika Dlay w witrynie Veritas Merge1

Drugi krok to skonfigurowanie łącznika Na tym etapie w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Werony w witrynie Veritas Merge1, zobacz Przewodnik użytkownika do [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Symphony%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników zewnętrznych Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Podczas9y zawierają właściwość o nazwie *Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-symphony-connector"></a>Krok 4. Monitorowanie łącznika Nasadki

Po utworzeniu łącznika Nasadki można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **Nasadka** , aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.