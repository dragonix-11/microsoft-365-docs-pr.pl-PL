---
title: Konfigurowanie łącznika do archiwizowania danych Skype dla firm w Microsoft 365
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
description: Dowiedz się, jak skonfigurować łącznik i użyć go w portalu zgodności usługi Microsoft Purview w celu importowania i archiwizowania danych z Skype dla firm do Microsoft 365.
ms.openlocfilehash: 5fa8b0ddaa46a181fca4d2539a3ff4778e47c632
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078282"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>Konfigurowanie łącznika do archiwizowania danych Skype dla firm

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj łącznika Veritas w portalu zgodności usługi Microsoft Purview, aby zaimportować i zarchiwizować dane z platformy Skype dla firm do skrzynek pocztowych użytkowników w organizacji Microsoft 365. Usługa Veritas udostępnia łącznik [Skype dla firm](https://www.veritas.com/en/au/insights/merge1/skype-for-business) skonfigurowany do przechwytywania elementów ze źródła danych innych firm (regularnie) i importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość, taką jak wiadomości między użytkownikami, trwałe czaty i wiadomości konferencyjne z Skype dla firm na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po zapisaniu Skype dla firm danych w skrzynkach pocztowych użytkowników można zastosować funkcje usługi Microsoft Purview, takie jak blokada postępowania sądowego, zbieranie elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika Skype dla firm może pomóc twojej organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-skype-for-business-data"></a>Omówienie archiwizacji danych Skype dla firm

W poniższym omówieniu wyjaśniono proces korzystania z łącznika do archiwizowania danych Skype dla firm w Microsoft 365.

![Przepływ pracy archiwizacji danych Skype dla firm.](../media/SkypeforBusinessConnectorWorkflow.png)

1. Twoja organizacja współpracuje z Skype dla firm, aby skonfigurować i skonfigurować witrynę Skype dla firm.

2. Raz na 24 godziny Skype dla firm elementy są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy Skype dla firm na format wiadomości e-mail.

3. Łącznik Skype dla firm tworzony w portalu zgodności, codziennie łączy się z witryną Veritas Merge1 i przesyła zawartość Skype dla firm do bezpiecznej lokalizacji Storage platformy Azure w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Poczta e-mail* automatycznego mapowania użytkownika zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). Podfolder w folderze Skrzynka odbiorcza o nazwie **Skype dla firm** jest tworzony w skrzynkach pocztowych użytkownika, a elementy są importowane do tego folderu. Łącznik wykonuje to przy użyciu wartości właściwości *Poczta e-mail* . Każdy element Skype dla firm zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto Merge1 dla łączników firmy Microsoft. W tym celu skontaktuj się z [pomocą techniczną veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact.html). Musisz zalogować się do tego konta podczas tworzenia łącznika w kroku 1.

- Użytkownik, który tworzy łącznik Skype dla firm w kroku 1 (i kończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w portalu zgodności. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w portalu zgodności usługi Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych Veritas jest w publicznej wersji zapoznawczej w środowiskach GCC w chmurze Microsoft 365 us Government. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przesyłanie i przetwarzanie danych klientów organizacji w systemach innych firm, które znajdują się poza infrastrukturą Microsoft 365 i dlatego nie są objęte zobowiązaniami dotyczącymi usługi Microsoft Purview i ochrony danych. Firma Microsoft nie przedstawia żadnej reprezentacji, że użycie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedrampem.

## <a name="step-1-set-up-the-skype-for-business-connector"></a>Krok 1. Konfigurowanie łącznika Skype dla firm

Pierwszym krokiem jest dostęp do strony **Łączniki danych** w portalu zgodności i utworzenie łącznika dla Skype dla firm danych.

1. Przejdź do obszaru <https://compliance.microsoft.com> i kliknij pozycję **Łączniki** >  danych **Skype dla firm**.

2. Na **stronie Skype dla firm** opis produktu kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki korzystania z usługi** kliknij pozycję **Akceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta merge1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie Skype dla firm w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Skype dla firm w lokacji Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Skype dla firm, zobacz [Merge1 Third-Party Connectors User Guide (Scal1 łączniki innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf)).

Po kliknięciu **przycisku Zapisz & Zakończ** zostanie wyświetlona strona **Mapowanie użytkownika** w kreatorze łącznika w portalu zgodności.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w portalu zgodności, wykonaj następujące kroki:

1. Na stronie **Mapowanie Skype dla firm użytkowników do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Skype dla firm obejmują właściwość o nazwie *Email* zawierającą adresy e-mail dla użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z użytkownikiem Microsoft 365, elementy zostaną zaimportowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk Dalej**, przejrzyj ustawienia, a następnie przejdź do strony **Łączniki danych** , aby zobaczyć postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>Krok 4. Monitorowanie łącznika Skype dla firm

Po utworzeniu łącznika Skype dla firm możesz wyświetlić stan łącznika w portalu zgodności.

1. Przejdź do strony <https://compliance.microsoft.com/> i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki**, a następnie wybierz łącznik **Skype dla firm**, aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
