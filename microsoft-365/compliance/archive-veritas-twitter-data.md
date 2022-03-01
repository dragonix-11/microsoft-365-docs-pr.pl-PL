---
title: Konfigurowanie łącznika do archiwizowania danych z serwisu Twitter w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych z usługi Twitter z veritas do usługi Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizowania tych danych możesz zarządzać danymi innych firm przy użyciu funkcji zgodności, takich jak archiwizacja prawnie, zbierania elektronicznych materiałów dowodowych i zasady przechowywania.
ms.openlocfilehash: 294dd933025c688e425badb6594c1aff968a9434
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020732"
---
# <a name="set-up-a-connector-to-archive-twitter-data-preview"></a>Konfigurowanie łącznika do archiwizowania danych w serwisie Twitter (wersja zapoznawcza)

Za pomocą łącznika veritas w aplikacji Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych z platformy Twitter do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Serwis Veritas udostępnia [łącznik usługi Twitter](https://www.veritas.com/insights/merge1/twitter), który jest skonfigurowany do przechwytywania elementów z zewnętrznego źródła danych i importowania ich do Microsoft 365. Łącznik konwertuje zawartość, taką jak tweety, przepisy i komentarze z serwisu Twitter, na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Po przechowywaniu danych serwisu Twitter w skrzynkach pocztowych użytkowników można stosować funkcje zgodności usługi Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika usługi Twitter może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-twitter-data"></a>Omówienie archiwizowania danych w serwisie Twitter

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych usługi Twitter w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych usługi Twitter.](../media/VeritasTwitterConnectorWorkflow.png)

1. Twoja organizacja współpracuje z serwisem Twitter w celu skonfigurowania i skonfigurowania witryny w serwisie Twitter. Twoja organizacja również współpracuje z serwisem Veritas w celu skonfigurowania witryny merge1.

2. Co 24 godziny elementy serwisu Twitter są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy usługi Twitter na format wiadomości e-mail.

3. Łącznik serwisu Twitter, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła zawartość serwisu Twitter do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Twitter** , a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element w serwisie Twitter zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika tego elementu.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Utwórz konto Merge1 dla łączników Microsoft. Aby utworzyć to konto, skontaktuj się z [działem obsługi klienta firmy Veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Utwórz aplikację Twitter w celu <https://developer.twitter.com> pobrania danych z konta w serwisie Twitter. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

- Użytkownik, który utworzy łącznik z witryny YouTube w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w programie Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-twitter-connector"></a>Krok 1. Konfigurowanie łącznika serwisu Twitter

Pierwszym krokiem jest uzyskanie dostępu do strony **łączników** danych w aplikacji Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych w serwisie Twitter.

1. Przejdź do, <https://compliance.microsoft.com> a następnie kliknij pozycję **Łączniki danychDążenie** > **.**

2. Na stronie **Opis produktu w** serwisie Twitter kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-twitter-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie serwisu Twitter w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika serwisu Twitter w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika usługi Twitter, zobacz Przewodnik użytkownika usługi [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników serwisu Twitter Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy serwisu Twitter zawierają właściwość Email (Poczta *e-mail*), która zawiera adresy e-mail użytkowników w organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-twitter-connector"></a>Krok 4. Monitorowanie łącznika usługi Twitter

Po utworzeniu łącznika w serwisie Twitter możesz sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników <https://compliance.microsoft.com/> **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik w serwisie **Twitter** , aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.
