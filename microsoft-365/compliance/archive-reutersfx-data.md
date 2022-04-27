---
title: Konfigurowanie łącznika do archiwizowania danych reuters FX w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych reuters FX z veritas do Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 02029e2107107261c532efad479fb0dd6cafd23b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094102"
---
# <a name="set-up-a-connector-to-archive-reuters-fx-data"></a>Konfigurowanie łącznika do archiwizowania danych reuters FX

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane z platformy Reuters FX do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [FX reutersa](https://globanet.com/reuters-fx/), który jest skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie), a następnie importowania tych elementów do Microsoft 365. Łącznik konwertuje waluty i kursy walutowe z konta REUTERS FX na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po przechowywaniu danych fx reutersa w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika FX agencji Reuters może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-reuters-fx-data"></a>Omówienie archiwizacji danych REUTERS FX

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych reuters FX w Microsoft 365.

![Przepływ pracy archiwizacji dla danych FX agencji Reuters.](../media/ReutersFXConnectorWorkflow.png)

1. Twoja organizacja współpracuje z agencją Reuters FX w celu skonfigurowania i skonfigurowania witryny Reuters FX.

2. Raz na 24 godziny elementy FX agencji Reuters są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy na format wiadomości e-mail.

3. Łącznik FX agencji Reuters tworzony w portalu zgodności, codziennie łączy się z witryną Veritas Merge1 i przesyła zawartość do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Reuters FX** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element FX reuters zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [pomocą techniczną veritas](https://globanet.com/contact-us). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownikowi, który utworzy łącznik FX reutersa w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-reuters-fx-connector"></a>Krok 1. Konfigurowanie łącznika Reuters FX

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w Microsoft 365 i utworzenie łącznika dla danych fx reutersa.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  **danychWyślij fx**.

2. Na stronie Opis produktu **Reuters FX** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-reuters-fx-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Reuters FX w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Reuters FX w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Reuters FX, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20FX%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj poniższe kroki:

1. Na stronie **Map Reuters FX users to Microsoft 365 users (Mapuj użytkowników FX**) włącz automatyczne mapowanie użytkowników.

   Elementy FX reuters obejmują właściwość o nazwie *Email*, która zawiera adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-reuters-fx-connector"></a>Krok 4. Monitorowanie łącznika Reuters FX

Po utworzeniu łącznika REUTERS FX możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com/> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik **Reuters FX** , aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.