---
title: Konfigurowanie łącznika do archiwizowania danych z czerwonego Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik w celu importowania i archiwizowania danych z wersji Veritas na Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: bce266bebd38e49e8ad756dc4100050694bc5d8c
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020747"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>Konfigurowanie łącznika do archiwizowania danych redtail Speak

Za pomocą łącznika veritas w skoroszycie Centrum zgodności platformy Microsoft 365 i zarchiwizować dane ze strony Redtail Speak do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas zapewnia łącznik [Redtail Speak](https://globanet.com/redtail/) skonfigurowany do przechwytywania elementów z serwera SFTP organizacji, na którym elementy są odbierane z usługi Redtail. Łącznik konwertuje zawartość ze strony Redtail Speak na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po zapisaniu danych funkcji Redtail Speak w skrzynkach pocztowych użytkowników można stosować funkcje zgodności Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika Redtail Speak może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>Omówienie archiwizowania danych funkcji Redtail Speak

W poniższym omówienia wyjaśniono proces używania łącznika do archiwizowania danych Funkcji Redtail Speak w programie Microsoft 365.

![Archiwizowanie przepływu pracy dla danych typu Szczegóły szczegóły.](../media/RedtailSpeakConnectorWorkflow.png)

1. Twoja organizacja współpracuje z programem Redtail Speak, aby skonfigurować bramę SMTP, w której wiadomości są codziennie przekazywane z programu Redtail Speak do serwera SFTP organizacji.

2. Co 24 godziny elementy typu Redtail Speak są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy Redtail Speak na format wiadomości e-mail.

3. Łącznik Redtail Speak tworzyć w usłudze Centrum zgodności platformy Microsoft 365 łączy się z witryną veritas merge1 każdego dnia i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy Redtail Speak do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników zostanie utworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Redtail Speak** , a elementy zostaną zaimportowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element Redtail Speak zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- W kroku 2 należy określić serwer SFTP organizacji. Ten krok jest niezbędny, aby firma Veritas Merge1 była w stanie skontaktować się z tą usługą w celu zebrania danych o stronie Redtail Speak za pośrednictwem portalu SFTP.

- Użytkownik, który utworzy łącznik Redtail Speak Importer w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na stronie Łączniki danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról Exchange Online grupie. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>Krok 1. Konfigurowanie łącznika Redtail Speak

Pierwszym krokiem jest uzyskanie dostępu do strony  Łączniki danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych Redtail Speak.

1. Przejdź do i [https://compliance.microsoft.com](https://compliance.microsoft.com/) wybierz pozycję **Redtail Speak łączników** &gt; danych.

2. Na stronie **Opis produktu Redtail Speak** wybierz pozycję **Dodaj nowy łącznik**.

3. Na stronie **Warunki użytkowania usługi** wybierz pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie wybierz pozycję **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Redtail Speak w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Redtail Speak w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Redtail Speak, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

Po wybraniu **przycisku Zapisz & Zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników redtail Speak to Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Redtail Speak obejmują właściwość o nazwie *Poczta* e-mail, która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Wybierz **pozycję** Dalej, przejrzyj ustawienia i przejdź **do strony** Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>Krok 4. Monitorowanie łącznika Redtail Speak

Po utworzeniu łącznika Redtail Speak można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) **danych w lewym okienku naw i** zaznacz je.

2. Wybierz **kartę Łączniki** , a następnie wybierz **łącznik Redtail Speak,** aby wyświetlić stronę wysuwu. Na tej stronie są wyświetlane właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze źródłem** **wybierz link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.