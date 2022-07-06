---
title: Konfigurowanie łącznika do archiwizowania danych reuters FX na platformie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych reuters FX z usługi Veritas na platformę Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm na platformie Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: defc9ddf4003c35b976ec06b7a4cc8e28328954b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624692"
---
# <a name="set-up-a-connector-to-archive-reuters-fx-data"></a>Konfigurowanie łącznika do archiwizowania danych reuters FX

Użyj łącznika Veritas w portal zgodności Microsoft Purview, aby zaimportować i zarchiwizować dane z platformy Reuters FX do skrzynek pocztowych użytkowników w organizacji platformy Microsoft 365. Usługa Veritas udostępnia łącznik [FX reutersa](https://globanet.com/reuters-fx/) , który jest skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie), a następnie importowania tych elementów na platformę Microsoft 365. Łącznik konwertuje waluty i kursy walutowe z konta REUTERS FX na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika na platformie Microsoft 365.

Po przechowywaniu danych fx reutersa w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych na platformie Microsoft 365 przy użyciu łącznika REUTERS FX może pomóc Organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-reuters-fx-data"></a>Omówienie archiwizacji danych REUTERS FX

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych reuters FX na platformie Microsoft 365.

![Przepływ pracy archiwizacji dla danych FX agencji Reuters.](../media/ReutersFXConnectorWorkflow.png)

1. Twoja organizacja współpracuje z agencją Reuters FX w celu skonfigurowania i skonfigurowania witryny Reuters FX.

2. Raz na 24 godziny elementy FX agencji Reuters są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy na format wiadomości e-mail.

3. Łącznik FX reuters tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przesyła zawartość do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Reuters FX** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element FX reuters zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [pomocą techniczną veritas](https://globanet.com/contact-us). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownikowi, który utworzy łącznik fx reutersa w kroku 1 (i ukończy go w kroku 3) musi mieć przypisaną rolę łącznika danych Administracja. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę Administracja łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portal zgodności Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze microsoft 365 US Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą platformy Microsoft 365 i w związku z tym nie są objęte zobowiązaniami microsoft purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-reuters-fx-connector"></a>Krok 1. Konfigurowanie łącznika Reuters FX

Pierwszym krokiem jest uzyskanie dostępu do strony **Łączniki danych** w usłudze Microsoft 365 i utworzenie łącznika dla danych fx agencji Reuters.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  danych **Reuters FX**.

2. Na stronie Opis produktu **Reuters FX** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-reuters-fx-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Reuters FX w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Reuters FX w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Reuters FX, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20FX%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj poniższe kroki:

1. Na stronie **Mapuj użytkowników fx reutersa na użytkowników platformy Microsoft 365** włącz automatyczne mapowanie użytkowników.

   Elementy FX reuters obejmują właściwość o nazwie *Email*, która zawiera adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem platformy Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-reuters-fx-connector"></a>Krok 4. Monitorowanie łącznika Reuters FX

Po utworzeniu łącznika REUTERS FX możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com/> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik **Reuters FX** , aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych, które zostały zaimportowane do chmury firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Wyświetlanie dzienników administratora łączników danych](data-connector-admin-logs.md).

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.