---
title: Konfigurowanie łącznika do archiwizacji danych symphony w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z veritas symphony do Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: b1a368fc7bce9e7b66021d7351139a78e6e6ac97
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093619"
---
# <a name="set-up-a-connector-to-archive-symphony-data"></a>Konfigurowanie łącznika do archiwizacji danych Symphony

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane symphony do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Symphony to platforma do obsługi wiadomości i współpracy używana w branży usług finansowych. Usługa Veritas udostępnia łącznik danych [Symphony](https://globanet.com/symphony) w portalu zgodności, który można skonfigurować do przechwytywania elementów ze źródła danych innych firm (regularnie), a następnie importowania tych elementów do skrzynek pocztowych użytkowników. Łącznik konwertuje zawartość elementu z konta Symphony na format wiadomości e-mail, a następnie importuje element do skrzynki pocztowej w Microsoft 365.

Po przechowywaniu komunikacji symphony w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, elektroniczne wykrywanie, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Symphony może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-symphony-data"></a>Omówienie archiwizacji danych symfonicznych

W poniższym omówieniu wyjaśniono proces korzystania z łącznika danych do archiwizowania komunikacji Symphony w Microsoft 365.

![Przepływ pracy archiwizacji symfonicznej.](../media/SymphonyConnectorWorkflow.png)

1. Twoja organizacja współpracuje z Symphony w celu skonfigurowania i skonfigurowania witryny Symphony.

2. Raz na 24 godziny wiadomości czatu z Symphony są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również zawartość wiadomości czatu na format wiadomości e-mail.

3. Łącznik Symphony tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy wiadomości do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w kroku 3. Nowy podfolder w folderze Skrzynka odbiorcza o nazwie **Symphony** jest tworzony w skrzynkach pocztowych użytkownika, a elementy wiadomości są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każda wiadomość czatu zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [pomocą techniczną veritas](https://globanet.com/ms-connectors-contact). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który utworzy łącznik Symphony w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-symphony-connector"></a>Krok 1. Konfigurowanie łącznika Symphony

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla danych symphony.

1. Przejdź do pozycji [https://compliance.microsoft.com](https://compliance.microsoft.com/) , a następnie kliknij pozycję **Łączniki** >  **danychSymphony**.

2. Na stronie Opis produktu **Symphony** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="configure-the-symphony-connector-on-the-veritas-merge1-site"></a>Konfigurowanie łącznika Symphony w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Symphony w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Symphony w witrynie Veritas Merge1, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika łączników](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Symphony%20User%20Guide%20.pdf) innych firm).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj następujące kroki:

1. Na stronie **Mapowanie użytkowników zewnętrznych na Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy symphony obejmują właściwość o nazwie *Email*, która zawiera adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-symphony-connector"></a>Krok 4. Monitorowanie łącznika Symphony

Po utworzeniu łącznika Symphony możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik **Symphony** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych zaimportowanych do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.