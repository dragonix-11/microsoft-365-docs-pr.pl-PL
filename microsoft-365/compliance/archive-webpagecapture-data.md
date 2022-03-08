---
title: Konfigurowanie łącznika do archiwizowania danych strony sieci Web w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych przechwyconych stron sieci Web z witryny Veritas w Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w programie Microsoft 365 w celu zarządzania danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja ze standardami prawnie, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 27e4491325a712e679cfe47e0ce7b1c8706119a6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317260"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Konfigurowanie łącznika do archiwizowania danych strony sieci Web

Za pomocą łącznika veritas w Centrum zgodności platformy Microsoft 365 można importować dane ze stron sieci Web do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Witryna Veritas udostępnia łącznik [przechwytywania](https://globanet.com/webpage-capture) strony sieci Web, który przechwyci określone strony internetowe (oraz linki na tych stronach) w konkretnej witrynie internetowej lub w całej domenie. Łącznik konwertuje zawartość strony sieci Web na format PDF, PNG lub niestandardowy, a następnie dołącza przekonwertowane pliki do wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po przechowywaniu zawartości strony sieci Web w skrzynkach pocztowych użytkowników można stosować funkcje zgodności Microsoft 365, takie jak zastosowanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych oraz zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika przechwytywania strony sieci Web może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami.

## <a name="overview-of-archiving-webpage-data"></a>Omówienie archiwizowania danych strony sieci Web

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania zawartości strony sieci web w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych strony sieci Web.](../media/WebPageCaptureConnectorWorkflow.png)

1. Organizacja współpracuje ze źródłem strony sieci Web, aby skonfigurować witrynę przechwytywania strony sieci Web.

2. Elementy źródeł stron sieci Web są kopiowane do witryny Veritas Merge1 co 24 godziny. Łącznik konwertuje też zawartość strony sieci Web i dołącza do niej wiadomość e-mail.

3. Łącznik przechwytywania strony sieci Web tworzyć w Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 codziennie i przesyła elementy strony sieci Web do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy strony sieci Web do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder  w folderze Skrzynka odbiorcza o nazwie Przechwytywanie strony sieci Web, a elementy strony sieci Web są importowane do tego folderu. Łącznik robi to przy użyciu wartości właściwości *Email* . Każdy element strony sieci Web zawiera tę właściwość, która jest wypełniana adresami e-mail dostarczonymi podczas konfigurowania łącznika Przechwytywanie strony sieci Web w [kroku 2](#step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site).

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Do tego konta zalogujesz się podczas tworzenia łącznika w kroku 1.

- Aby skonfigurować niestandardowy format pliku w celu przekonwertowania elementów strony internetowej, musisz współpracować z pomocą techniczną Veritas. Aby uzyskać więcej informacji, zobacz Podręcznik użytkownika łączników innej [firmy Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

- Użytkownik, który utworzy łącznik Przechwytywanie strony sieci Web w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-webpage-capture-connector"></a>Krok 1. Konfigurowanie łącznika Przechwytywanie strony sieci Web

Pierwszym krokiem jest uzyskanie dostępu do łączników **danych** i utworzenie łącznika dla danych źródłowych strony sieci Web.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danych** >  **Przechwytywanie strony sieci Web**.

2. Na stronie **Opis produktu przechwyć** stronę sieci Web kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika przechwytywania strony sieci Web w witrynie Veritas Merge1

Drugi krok to skonfigurowanie łącznika przechwytywania strony sieci Web w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Przechwytywanie strony sieci Web, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj poniższe czynności:

1. Na stronie **Mapowanie użytkowników przechwyconych na Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy przechwytywania strony sieci Web zawierają właściwość o nazwie *Poczta* e-mail, która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia i przejdź do strony Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>Krok 4. Monitorowanie łącznika przechwytywania strony sieci Web

Po utworzeniu łącznika Przechwytywanie strony sieci Web możesz sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **Przechwytywanie strony sieci Web** , aby wyświetlić stronę wysuwną. Ta strona zawiera właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.