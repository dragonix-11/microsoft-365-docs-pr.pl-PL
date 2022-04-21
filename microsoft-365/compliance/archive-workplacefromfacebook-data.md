---
title: Konfigurowanie łącznika do archiwizowania danych aplikacji Workplace z serwisu Facebook w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z usługi Workplace z serwisu Facebook, który jest archiwizowany w witrynie Merge1 firmy Veritas, do Microsoft 365. Skonfigurowanie łącznika wymaga współpracy z usługą Veritas Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365, dzięki czemu można używać funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania w celu zarządzania danymi innych firm w organizacji.
ms.openlocfilehash: 0dbd1bfaeea6a42db03793941b1fea894ee391b5
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001461"
---
# <a name="set-up-a-connector-to-archive-workplace-from-facebook-data"></a>Konfigurowanie łącznika do archiwizowania danych aplikacji Workplace z serwisu Facebook

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane z usługi Workplace z serwisu Facebook do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [Workplace from Facebook](https://globanet.com/workplace/), który jest skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie) i importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość, taką jak czaty, załączniki, wpisy i filmy wideo z miejsca pracy, na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w Microsoft 365.

Po przechowywaniu danych w miejscu pracy w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność z komunikacją. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Workplace from Facebook może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-workplace-from-facebook-data"></a>Omówienie archiwizacji danych z serwisu Facebook w miejscu pracy

W poniższym omówieniu wyjaśniono proces korzystania z łącznika do archiwizowania danych miejsca pracy w Microsoft 365.

![Przepływ pracy archiwizacji danych aplikacji Workplace z serwisu Facebook.](../media/WorkplaceConnectorWorkflow.png)

1. Twoja organizacja współpracuje z aplikacją Workplace z serwisu Facebook w celu skonfigurowania i skonfigurowania witryny Workplace.

2. Raz na 24 godziny elementy z miejsca pracy są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również zawartość tych elementów na format wiadomości e-mail.

3. Łącznik Workplace from Facebook tworzony w portalu zgodności, codziennie łączy się z usługą Veritas Merge1 i przenosi elementy workplace do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w kroku 3. Zostanie utworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Workplace z serwisu Facebook** , a elementy workplace zostaną zaimportowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każdy element workplace zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika czatu lub wpisu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://globanet.com/ms-connectors-contact). Zalogujesz się do tego konta podczas tworzenia łącznika w kroku 1.

- Utwórz niestandardową integrację w witrynie , https://my.workplace.com/work/admin/apps/ aby pobierać dane z usługi Workplace za pośrednictwem interfejsów API w celu zapewnienia zgodności i zbierania elektronicznych materiałów dowodowych.

   Podczas tworzenia integracji platforma Workplace generuje zestaw unikatowych poświadczeń używanych do generowania tokenów używanych do uwierzytelniania. Te tokeny są używane w kreatorze konfiguracji łącznika Workplace from Facebook w kroku 2. Instrukcje krok po kroku dotyczące sposobu tworzenia aplikacji można znaleźć w [temacie Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf)).

- Użytkownikowi, który utworzy łącznik Workplace from Facebook w kroku 1 (i ukończy go w kroku 3) musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-workplace-from-facebook-connector"></a>Krok 1. Konfigurowanie łącznika Workplace from Facebook

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla danych w miejscu pracy.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com/), a następnie kliknij pozycję **Łączniki** >  **danychPrób z serwisu Facebook**.

2. Na stronie Opis produktu **Workplace from Facebook** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-workplace-from-facebook-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Workplace from Facebook w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Workplace from Facebook w witrynie Merge1. Aby uzyskać informacje o sposobie konfigurowania łącznika Workplace from Facebook, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj następujące kroki:

1. Na stronie **Mapowanie użytkowników zewnętrznych na Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy workplace zawierają właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-workplace-from-facebook-connector"></a>Krok 4. Monitorowanie łącznika Workplace from Facebook

Po utworzeniu łącznika Workplace from Facebook możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik **Workplace z usługi Facebook** , aby wyświetlić stronę wysuwaną. Ta strona zawiera właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera informacje o danych zaimportowanych do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.