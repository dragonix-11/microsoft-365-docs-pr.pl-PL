---
title: Konfigurowanie łącznika do archiwizowania danych yieldbrokera w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych firmy Yieldbroker z veritas do Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 8e7ed4034bf2c0d3805cc3896a5986aaddd99305
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020762"
---
# <a name="set-up-a-connector-to-archive-yieldbroker-data"></a>Konfigurowanie łącznika do archiwizowania danych yieldbrokera

Za pomocą łącznika veritas w pliku Centrum zgodności platformy Microsoft 365 importować i archiwizować dane z pliku Yieldbroker do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [Yieldbroker](https://globanet.com/yieldbroker/), który jest skonfigurowany do przechwytywania elementów ze źródła danych innych firm i importowania tych elementów do Microsoft 365. Łącznik konwertuje zawartość firmy Yieldbroker na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po zapisaniu firmy Yieldbroker w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika yieldbroker może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-yieldbroker-data"></a>Omówienie archiwizowania danych yieldbrokera

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych narzędzia Yieldbroker w programie Microsoft 365.

![Zarchiwizowanie przepływu pracy dla danych Yieldbroker.](../media/YieldbrokerConnectorWorkflow.png)

1. Twoja organizacja współpracuje z serwisem Yieldbroker w celu skonfigurowania i skonfigurowania witryny Yieldbroker.

2. Elementy yieldbroker są kopiowane do witryny Veritas Merge1 co 24 godziny. Łącznik konwertuje także zawartość na format wiadomości e-mail.

3. Łącznik Yieldbroker tworzyć w Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła wiadomości do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik importuje przekonwertowane elementy Yieldbroker do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości *Email* automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Yieldbroker** , a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każda yieldbroker zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto korespondencji seryjnej Veritas merge1 dla łączników firmy Microsoft. Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Użytkownik, który tworzy łącznik Yieldbroker w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na stronie Łączniki danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w programie Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-yieldbroker-connector"></a>Krok 1. Konfigurowanie łącznika Yieldbroker

Pierwszym krokiem jest uzyskanie dostępu do strony  łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla yieldbrokera.

1. Przejdź do i [https://compliance.microsoft.com](https://compliance.microsoft.com/) kliknij pozycję **Łączniki danych** &gt; **Yieldbroker**.

2. Na stronie **Opis produktu Yieldbroker** kliknij pozycję **Dodaj nowy łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-yieldbroker-connector-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie łącznika Yieldbroker w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Yieldbroker w witrynie Merge1. Aby uzyskać informacje na temat konfigurowania usługi Yieldbroker, zobacz Przewodnik użytkownika usługi [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Yieldbroker%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika, wykonaj następujące czynności:

1. Na stronie **map użytkowników yieldbroker do Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Yieldbroker zawierają właściwość o nazwie *Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia i przejdź do strony Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-yieldbroker-connector"></a>Krok 4. Monitorowanie łącznika Yieldbroker

Po utworzeniu łącznika Yieldbroker możesz sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **Yieldbroker** , aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.