---
title: Konfigurowanie łącznika do archiwizowania danych CellTrust w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych CellTrust z veritas do usługi Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: fd2ae7c905a1f0104112d30b8a4f195ccd146a07
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020788"
---
# <a name="set-up-a-connector-to-archive-celltrust-data"></a>Konfigurowanie łącznika do archiwizowania danych CellTrust

Użyj łącznika Veritas w p Centrum zgodności platformy Microsoft 365, aby zaimportować i zarchiwizować dane z platformy CellTrust do skrzynek pocztowych użytkowników Microsoft 365 organizacji. Veritas udostępnia łącznik [CellTrust](https://globanet.com/celltrust/), który przechwyca elementy ze źródła danych innej firmy i importuje je do Microsoft 365. Łącznik konwertuje zawartość wiadomości SMS z kont CellTrust na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w Microsoft 365.

Po zapisaniu danych CellTrust w skrzynkach pocztowych użytkowników można stosować funkcje zgodności usługi Microsoft 365, takie jak zawieszenie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania oraz zgodność komunikacji. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika CellTrust może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami.

## <a name="overview-of-archiving-celltrust-data"></a>Omówienie archiwizowania danych funkcji CellTrust

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych CellTrust w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych CellTrust.](../media/CellTrustConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą CellTrust w celu skonfigurowania witryny CellTrust.

2. Elementy CellTrust są kopiowane do witryny Veritas Merge1 co 24 godziny. Łącznik konwertuje także zawartość wiadomości na format wiadomości e-mail.

3. Łącznik CellTrust, który tworzysz w Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Automatyczne mapowanie użytkowników jako łącznik importuje elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* opisanej w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **CellTrust** , a elementy wiadomości są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element CellTrust zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto Merge1 dla łączników Microsoft. Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik CellTrust w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-celltrust-connector"></a>Krok 1. Konfigurowanie łącznika CellTrust

Pierwszym krokiem jest uzyskanie dostępu do łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych CellTrust.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki danych** \> **, CellTrust**.

2. Na stronie **Opis produktu CellTrust** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-celltrust-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika CellTrust w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika CellTrust w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika CellTrust, zobacz Przewodnik użytkownika do [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20CellTrust%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurowanie łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników funkcji CellTrust Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy CellTrust zawierają właściwość o nazwie *Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia i przejdź do strony Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-celltrust-connector"></a>Krok 4. Monitorowanie łącznika CellTrust

Po utworzeniu łącznika CellTrust można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **CellTrust** , aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.