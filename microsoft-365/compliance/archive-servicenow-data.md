---
title: Konfigurowanie łącznika do archiwizowania danych usługiNow w programie Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych usługiNow z veritas do usługi Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: 34cca3d8988f25a6082a8a000335a311343fc76d
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2021
ms.locfileid: "63020805"
---
# <a name="set-up-a-connector-to-archive-servicenow-data"></a>Konfigurowanie łącznika do archiwizowania danych w serwisieNow

Użyj łącznika veritas w usłudze Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych z platformy ServiceNow do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Usługa Veritas udostępnia [łącznik ServiceNow](https://globanet.com/servicenow/), który przechwyci elementy ze źródła danych innej firmy i zaimportuje je do Microsoft 365. Łącznik konwertuje zawartość, na przykład wiadomości na żywo, załączniki i wpisy z witryny ServiceNow, na format wiadomości e-mail, a następnie importuje te elementy do skrzynek pocztowych użytkowników w programie Microsoft 365.

Gdy dane usługi ServiceNow będą przechowywane w skrzynkach pocztowych użytkowników, możesz stosować funkcje zgodności Microsoft 365, takie jak przechowywanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika ServiceNow może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulacyjną.

## <a name="overview-of-archiving-servicenow-data"></a>Omówienie archiwizowania danych usługiNow

W poniższym o omówieniem wyjaśniono proces używania łącznika do archiwizowania danych ServiceNow w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych ServiceNow.](../media/ServiceNowConnectorWorkflow.png)

1. Twoja organizacja współpracuje z serwisem ServiceNow w celu skonfigurowania witryny ServiceNow.

2. Co 24 godziny elementy serviceNow są kopiowane do witryny Veritas Merge1. Łącznik konwertuje również elementy ServiceNow na format wiadomości e-mail.

3. Łącznik ServiceNow, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną Veritas Merge1 każdego dnia i przesyła zawartość ServiceNow do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników zostanie utworzony podfolder w folderze Skrzynka odbiorcza o nazwie **ServiceNow** , a elementy zostaną zaimportowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element ServiceNow zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto Merge1 dla łączników Microsoft. Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Utwórz aplikację ServiceNow, aby pobierać dane z konta ServiceNow. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).

- Użytkownik, który tworzy łącznik ServiceNow w kroku 1 (i ukończy go w kroku 3), musi być przypisany do roli importowania i eksportowania skrzynek pocztowych w programie Exchange Online. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Domyślnie ta rola nie jest przypisana do żadnej grupy ról w Exchange Online. Rolę importowania i eksportowania skrzynek pocztowych możesz dodać do grupy ról Zarządzanie organizacją w programie Exchange Online. Możesz też utworzyć grupę ról, przypisać rolę importowania i eksportowania skrzynek pocztowych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać więcej informacji, zobacz sekcje [Tworzenie grup ról](/Exchange/permissions-exo/role-groups#create-role-groups) [lub](/Exchange/permissions-exo/role-groups#modify-role-groups) Modyfikowanie grup ról w artykule "Zarządzanie grupami ról w aplikacji Exchange Online".

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-servicenow-connector"></a>Krok 1. Konfigurowanie łącznika ServiceNow

Pierwszym krokiem jest uzyskanie dostępu do strony **łączników** danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych ServiceNow.

1. Przejdź do, [https://compliance.microsoft.com](https://compliance.microsoft.com/) a następnie kliknij pozycję **Łączniki** **danychServiceNow** > .

2. Na stronie **ServiceNow** product description (Opis produktu ServiceNow) kliknij pozycję **Add connector (Dodaj łącznik**).

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-servicenow-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie usługi ServiceNow w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika ServiceNow w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika ServiceNow, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników usługiNow Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy ServiceNow zawierają właściwość o nazwie *Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-servicenow-connector"></a>Krok 4. Monitorowanie łącznika ServiceNow

Po utworzeniu łącznika ServiceNow można sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie wybierz łącznik **ServiceNow** , aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.