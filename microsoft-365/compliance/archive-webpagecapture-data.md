---
title: Konfigurowanie łącznika do archiwizowania danych strony internetowej w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania strony internetowej Przechwytywanie danych z usługi Veritas w Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365, dzięki czemu można używać funkcji zgodności, takich jak archiwizowanie prawne, wyszukiwanie zawartości i zasady przechowywania w celu zarządzania danymi innych firm w organizacji.
ms.openlocfilehash: 1e8fdc71a2d37a80488db4d2a62ae1ab77aeb123
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094080"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Konfigurowanie łącznika do archiwizowania danych strony internetowej

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane ze stron internetowych do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [przechwytywania stron sieci Web](https://globanet.com/webpage-capture) , który przechwytuje określone strony internetowe (i linki na tych stronach) w określonej witrynie internetowej lub całej domenie. Łącznik konwertuje zawartość strony internetowej na format PDF, PNG lub plik niestandardowy, a następnie dołącza przekonwertowane pliki do wiadomości e-mail, a następnie importuje te elementy poczty e-mail do skrzynek pocztowych użytkownika w Microsoft 365.

Po zapisaniu zawartości strony internetowej w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, pozyskiwanie elektronicznych materiałów dowodowych oraz zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika przechwytywania strony internetowej może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-webpage-data"></a>Omówienie archiwizowania danych strony internetowej

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania zawartości strony internetowej w Microsoft 365.

![Przepływ pracy archiwizacji danych strony internetowej.](../media/WebPageCaptureConnectorWorkflow.png)

1. Twoja organizacja współpracuje ze źródłem strony internetowej w celu skonfigurowania i skonfigurowania witryny przechwytywania stron sieci Web.

2. Raz na 24 godziny elementy źródeł strony internetowej są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również i dołącza zawartość strony internetowej do wiadomości e-mail.

3. Łącznik przechwytywania strony internetowej tworzony w portalu zgodności, codziennie łączy się z witryną Veritas Merge1 i przesyła elementy strony internetowej do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy strony internetowej do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Webpage Capture** jest tworzony w skrzynkach pocztowych użytkownika, a elementy strony internetowej są importowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każdy element strony internetowej zawiera tę właściwość, która jest wypełniana adresami e-mail podanymi podczas konfigurowania łącznika przechwytywania strony internetowej w [kroku 2](#step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site).

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Aby skonfigurować niestandardowy format pliku w celu konwertowania elementów strony internetowej, musisz współpracować z obsługą usługi Veritas. Aby uzyskać więcej informacji, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf)).

- Użytkownik, który utworzy łącznik przechwytywania strony internetowej w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-webpage-capture-connector"></a>Krok 1. Konfigurowanie łącznika przechwytywania strony internetowej

Pierwszym krokiem jest uzyskanie dostępu do **łączników danych** i utworzenie łącznika dla danych źródłowych strony sieci Web.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com/), a następnie kliknij pozycję **Łączniki** >  **danychWychwyć stronę internetową**.

2. Na **stronie Internetowej Przechwytywanie** opisu produktu kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika przechwytywania strony internetowej w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika przechwytywania strony internetowej w witrynie Veritas Merge1. Aby uzyskać informacje o sposobie konfigurowania łącznika przechwytywania strony internetowej, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika dotyczący łączników](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf) innych firm).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj poniższe kroki:

1. Na **stronie Mapowanie strony sieci Web Przechwytywanie użytkowników do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy przechwytywania strony internetowej obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>Krok 4. Monitorowanie łącznika przechwytywania strony internetowej

Po utworzeniu łącznika przechwytywania strony internetowej możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik **Przechwytywanie strony internetowej** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.