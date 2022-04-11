---
title: Konfigurowanie łącznika do archiwizowania danych youtube w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych youtube z usługi Veritas do Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po archiwizacji tych danych można używać funkcji zgodności, takich jak blokada prawna, zbieranie elektronicznych materiałów dowodowych i zasady przechowywania, do zarządzania danymi innych firm.
ms.openlocfilehash: 20343411a77210845bfad22e34dfcada6f8ca9b9
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759462"
---
# <a name="set-up-a-connector-to-archive-youtube-data"></a>Konfigurowanie łącznika do archiwizowania danych youtube

Użyj łącznika Veritas w Centrum zgodności platformy Microsoft 365, aby zaimportować i zarchiwizować dane z usługi YouTube do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik skonfigurowany do przechwytywania elementów ze źródła danych innych firm i importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość, taką jak czaty, załączniki, zadania, notatki i wpisy z serwisu YouTube, na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkownika w Microsoft 365.

Po zapisaniu danych youtube w skrzynkach pocztowych użytkowników można zastosować Microsoft 365 funkcje zgodności, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika YouTube może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-youtube-data"></a>Omówienie archiwizowania danych w serwisie YouTube

W poniższym omówieniu wyjaśniono proces korzystania z łącznika do archiwizowania danych YouTube w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych YouTube.](../media/YouTubeConnectorWorkflow.png)

1. Twoja organizacja współpracuje z YouTube w celu skonfigurowania i skonfigurowania witryny YouTube.

2. Raz na 24 godziny elementy YouTube są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy YouTube na format wiadomości e-mail.

3. Łącznik YouTube utworzony w Centrum zgodności platformy Microsoft 365 codziennie łączy się z witryną Veritas Merge1 i przesyła zawartość serwisu YouTube do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **YouTube** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową do zaimportowania elementów przy użyciu wartości właściwości *Poczta e-mail* . Każdy element YouTube zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto Merge1 dla łączników firmy Microsoft. Aby utworzyć to konto, skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Utwórz aplikację YouTube, aby pobrać dane z konta YouTube. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf)).

- Użytkownik, który utworzy łącznik YouTube w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-set-up-the-youtube-connector"></a>Krok 1. Konfigurowanie łącznika YouTube

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych YouTube.

1. Przejdź do pozycji <https://compliance.microsoft.com> , a następnie kliknij pozycję **Łączniki** >  **danychUżytk.**

2. Na stronie opisu produktu **YouTube** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-youtube-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie serwisu YouTube w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika YouTube w witrynie Veritas Merge1. Aby uzyskać informacje na temat sposobu konfigurowania łącznika YouTube, zobacz [Merge1 Third-Party Connectors User Guide (Przewodnik użytkownika dotyczący łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w Centrum zgodności platformy Microsoft 365.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące kroki:

1. Na stronie **Mapowanie użytkowników YouTube do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy YouTube zawierają właściwość o nazwie *Email*, która zawiera adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-youtube-connector"></a>Krok 4. Monitorowanie łącznika YouTube

Po utworzeniu łącznika YouTube możesz wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do strony <https://compliance.microsoft.com/> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki,** a następnie wybierz łącznik **YouTube** , aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
