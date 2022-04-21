---
title: Konfigurowanie łącznika do archiwizowania danych Red tail Speak w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych Red tail Speak z usługi Veritas do Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizowania tych danych można zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak blokada prawna, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 46b9646fee78fa0589a9af41db35cf79a71e508f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994573"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>Konfigurowanie łącznika do archiwizowania danych Redtail Speak

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane ze skrzynek pocztowych Redtail Speak to user w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [Redtail Speak](https://globanet.com/redtail/) skonfigurowany do przechwytywania elementów z serwera SFTP w organizacji, na którym elementy są odbierane z usługi Redtail. Łącznik konwertuje zawartość z funkcji Redtail Speak na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po zapisaniu danych Redtail Speak w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Za pomocą łącznika Redtail Speak do importowania i archiwizowania danych w Microsoft 365 może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>Omówienie archiwizacji danych Redtail Speak

W poniższym omówieniu wyjaśniono proces używania łącznika do archiwizowania danych Redtail Speak w Microsoft 365.

![Przepływ pracy archiwizacji danych Redtail Speak.](../media/RedtailSpeakConnectorWorkflow.png)

1. Twoja organizacja współpracuje z firmą Redtail Speak w celu skonfigurowania i skonfigurowania bramy SMTP, w której codziennie komunikaty są przekazywane z aplikacji Redtail Speak do serwera SFTP w organizacji.

2. Raz na 24 godziny elementy Redtail Speak są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy Redtail Speak na format wiadomości e-mail.

3. Łącznik Redtail Speak tworzony w portalu zgodności codziennie łączy się z witryną Veritas Merge1 i przesyła komunikaty do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy Redtail Speak do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Redtail Speak** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element Redtail Speak zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/content/support/). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- W kroku 2 należy określić serwer SFTP organizacji. Ten krok jest niezbędny, aby veritas merge1 mógł skontaktować się z nim w celu zebrania danych Redtail Speak za pośrednictwem protokołu SFTP.

- Użytkownik, który tworzy łącznik redtail speak importera w kroku 1 (i kończy go w kroku 3) musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>Krok 1. Konfigurowanie łącznika Redtail Speak

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla danych Redtail Speak.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) i wybierz pozycję **Łączniki** &gt; danych **Redtail Speak**.

2. Na stronie Opis produktu **Redtail Speak** wybierz pozycję **Dodaj nowy łącznik**.

3. Na stronie **Warunki użytkowania** wybierz pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie wybierz pozycję **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Redtail Speak w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Redtail Speak w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Redtail Speak, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf)).

Po wybraniu pozycji **Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika, wykonaj następujące kroki:

1. Na stronie **Map Redtail Speak users to Microsoft 365 users (Mapuj użytkowników do Microsoft 365 użytkowników**) włącz automatyczne mapowanie użytkowników. Elementy Redtail Speak obejmują właściwość o nazwie *Email*, która zawiera adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Wybierz pozycję **Dalej**, przejrzyj ustawienia i przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>Krok 4. Monitorowanie łącznika Redtail Speak

Po utworzeniu łącznika Redtail Speak możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do obszaru [https://compliance.microsoft.com](https://compliance.microsoft.com/) i wybierz pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Wybierz kartę **Łączniki,** a następnie wybierz łącznik **Redtail Speak** , aby wyświetlić stronę wysuwaną. Na tej stronie są wyświetlane właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** wybierz link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.