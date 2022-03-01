---
title: Konfigurowanie łącznika do archiwizowania danych fx Połączenie w programie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z usługi Veritas FX Połączenie w Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w programie Microsoft 365 w celu zarządzania danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze standardami prawnie, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 1ea9d4f9a02d94ab3e16bf5ddadd6ec32bfe36bc
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020749"
---
# <a name="set-up-a-connector-to-archive-fx-connect-data"></a>Konfigurowanie łącznika do archiwizowania danych Połączenie FX

Za pomocą łącznika veritas w p Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane z platformy współpracy Połączenie FX do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [fx Połączenie](https://globanet.com/fx-connect/), który jest skonfigurowany do przechwytywania Połączenie FX i importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość z usługi FX Połączenie, taką jak transakcje, wiadomości i inne szczegóły z konta FX Połączenie organizacji, na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po zapisaniu Połączenie FX w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie Połączenie w programie Microsoft 365 za pomocą łącznika funkcji FX może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-fx-connect-data"></a>Omówienie archiwizowania danych FX Połączenie danych

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych FX w Połączenie w Microsoft 365.

![Archiwizowanie przepływu pracy dla Połączenie FX.](../media/FXConnectConnectorWorkflow.png)

1. Twoja organizacja współpracuje z Połączenie FX w celu skonfigurowania i skonfigurowania witryny Połączenie FX.

2. Raz na 24 godziny elementy z kont Połączenie FX są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy fx na Połączenie wiadomości e-mail.

3. Łącznik FX Połączenie, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przenosi elementy fx Połączenie do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza **o nazwie FX Połączenie**, a elementy są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy Połączenie FX zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika tego elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft.  Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://globanet.com/ms-connectors-contact). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik funkcji FX Połączenie w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-fx-connect-connector"></a>Krok 1. Konfigurowanie łącznika fx Połączenie łącznika

Pierwszym krokiem jest uzyskanie dostępu do strony  łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych Połączenie FX.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danychFX** >  **Połączenie**.

2. Na stronie **FX Połączenie** opis produktu kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-fx-connect-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika fx Połączenie w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika fx Połączenie w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika fx Połączenie, zobacz [Podręcznik użytkownika scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20FX%20Connect%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie Połączenie użytkowników do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy fx Połączenie właściwość o nazwie *Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-fx-connect-connector"></a>Krok 4. Monitorowanie łącznika fx Połączenie fx

Po utworzeniu łącznika fx Połączenie można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com/> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki**, a następnie wybierz łącznik **fx Połączenie**, aby wyświetlić stronę wysuwu. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.