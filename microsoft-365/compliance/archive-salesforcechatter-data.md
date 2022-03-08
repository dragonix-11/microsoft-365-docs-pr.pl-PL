---
title: Konfigurowanie łącznika w celu archiwizowania danych chatteru usługi Salesforce w Microsoft 365
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
description: Administratorzy mogą skonfigurować łącznik do importowania i archiwizowania danych chatteru usługi Salesforce z veritas do Microsoft 365. Ten łącznik umożliwia archiwizowanie danych ze źródeł danych innych firm w Microsoft 365. Po zarchiwizować te dane możesz zarządzać danymi innych firm za pomocą funkcji zgodności, takich jak archiwizacja ze względu na przepisy prawne, wyszukiwanie zawartości i zasady przechowywania.
ms.openlocfilehash: bb52bd95d11a93c2bbb6816ed189ef5e0594ffac
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327424"
---
# <a name="set-up-a-connector-to-archive-salesforce-chatter-data"></a>Konfigurowanie łącznika do archiwizowania danych chatteru usługi Salesforce

Za pomocą łącznika veritas w Centrum zgodności platformy Microsoft 365 można importować i archiwizować dane z platformy Chatter usługi Salesforce do skrzynek pocztowych użytkowników w Microsoft 365 organizacji. Veritas udostępnia łącznik [Czat usługi Salesforce](http://globanet.com/chatter/), który przechwyci elementy z zewnętrznego źródła danych i zaim importuje je do Microsoft 365. Łącznik konwertuje zawartość, taką jak czaty, załączniki i wpisy z chatteru usługi Salesforce, na format wiadomości e-mail, a następnie importuje te elementy do skrzynki pocztowej użytkownika w programie Microsoft 365.

Po zapisaniu danych programu Salesforce Chatter w skrzynkach pocztowych użytkowników możesz stosować funkcje zgodności usługi Microsoft 365, takie jak Zastosowanie w związku z postępowaniem sądowym, zbierania elektronicznych materiałów dowodowych, zasady przechowywania i etykiety przechowywania. Importowanie i archiwizowanie danych w programie Microsoft 365 za pomocą łącznika Czat usługi Salesforce może ułatwić organizacji zachowania zgodności z zasadami rządowymi i przepisami regulowymi.

## <a name="overview-of-archiving-salesforce-chatter-data"></a>Omówienie archiwizowania danych chatteru usługi Salesforce

Poniższe omówienie przedstawia proces używania łącznika do archiwizowania danych chatteru usługi Salesforce w Microsoft 365.

![Archiwizowanie przepływu pracy dla danych chatteru usługi Salesforce.](../media/SalesforceChatterConnectorWorkflow.png)

1. Twoja organizacja współpracuje z czatem usługi Salesforce, aby skonfigurować witrynę Chatter usługi Salesforce.

2. Co 24 godziny elementy rozmów usługi Salesforce są kopiowane do witryny Veritas Merge1. Łącznik zawiera również elementy czatów usługi Salesforce do formatu wiadomości e-mail.

3. Łącznik Czat usługi Salesforce, który tworzysz w usłudze Centrum zgodności platformy Microsoft 365, łączy się z witryną Korespondencja seryjna1 Veritas każdego dnia i przesyła zawartość Chatter do bezpiecznej lokalizacji usługi Azure Storage w chmurze firmy Microsoft.

4. Łącznik zaim importuje przekonwertowane elementy do skrzynek pocztowych określonych użytkowników przy użyciu wartości właściwości  Email (Poczta e-mail) automatycznego mapowania użytkowników zgodnie z opisem w [kroku 3](#step-3-map-users-and-complete-the-connector-setup). W skrzynkach pocztowych użytkowników jest tworzony podfolder w folderze Skrzynka odbiorcza o nazwie **Czat usługi Salesforce** , a elementy są importowane do tego folderu. Łącznik określa skrzynkę pocztową, do której mają być importowane elementy, przy użyciu wartości właściwości *Email* . Każdy element Chatter zawiera tę właściwość, która jest wypełniana adresem e-mail każdego uczestnika tego elementu.

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Utwórz konto Merge1 dla łączników Microsoft. Aby utworzyć konto, skontaktuj się z działem [obsługi klienta firmy Veritas](https://www.veritas.com/content/support/). Podczas tworzenia łącznika w kroku 1 należy zalogować się do tego konta.

- Utwórz aplikację Salesforce i uzyskaj token w .[https://salesforce.com](https://salesforce.com) Musisz zalogować się do konta usługi Salesforce jako administrator i uzyskać osobisty token użytkownika do zaimportowania danych. Ponadto wyzwalacze muszą zostać opublikowane w witrynie Chatter, aby przechwytywać aktualizacje, usunięcia i zmiany. Te wyzwalacze powodują utworzenie wpisu w kanale, a merge1 przechwyci informacje z tego kanału. Aby uzyskać instrukcje krok po kroku dotyczące tworzenia aplikacji i nabywania tokenu, zobacz Przewodnik użytkownika do [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

- Użytkownik, który utworzy łącznik Czat usługi Salesforce w kroku 1 (i ukończy go w kroku 3), musi mieć przypisaną rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na **stronie Łączniki** danych w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w sekcji Uprawnienia w Centrum zabezpieczeń & [zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Administrator w organizacji może również utworzyć niestandardową grupę ról, przypisać rolę administrator łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w sekcji Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ten łącznik danych usługi Veritas jest w publicznej wersji zapoznawczej GCC w środowisku danych Microsoft 365 chmurze dla instytucji rządowych Stanów Zjednoczonych. Aplikacje i usługi innych firm mogą obejmować przechowywanie, przekazywanie i przetwarzanie danych klienta Organizacji w systemach innych firm, które znajdują się poza infrastrukturą firmy Microsoft 365 i dlatego nie są objęte zobowiązaniami firmy Microsoft 365 w zakresie zgodności z przepisami i ochrony danych. Firma Microsoft nie zapewnia, że używanie tego produktu do łączenia się z aplikacjami innych firm oznacza, że te aplikacje innych firm są zgodne z fedRAMP.

## <a name="step-1-set-up-the-salesforce-chatter-connector"></a>Krok 1. Konfigurowanie łącznika Czat usługi Salesforce

Pierwszym krokiem jest uzyskanie dostępu do strony  łączników danych w Centrum zgodności platformy Microsoft 365 i utworzenie łącznika dla danych chatteru.

1. Przejdź do i [https://compliance.microsoft.com](https://compliance.microsoft.com/) kliknij pozycję **Łączniki** **danychSalesforce** >  Chatter.

2. Na stronie **Opis produktu Czat usługi Salesforce** kliknij pozycję **Dodaj łącznik**.

3. Na stronie **Warunki użytkowania usługi** kliknij pozycję **Zaakceptuj**.

4. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**.

5. Zaloguj się do konta korespondencji seryjnej1, aby skonfigurować łącznik.

## <a name="step-2-configure-the-salesforce-chatter-on-the-veritas-merge1-site"></a>Krok 2. Konfigurowanie chatteru salesforce w witrynie Veritas Merge1

Drugim krokiem jest skonfigurowanie łącznika Czat usług Salesforce w witrynie Veritas Merge1. Aby uzyskać informacje na temat konfigurowania łącznika Salesforce Chatter, zobacz Przewodnik użytkownika dotyczący [scalania1 łączników innych firm](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

Po kliknięciu **przycisku Zapisz & zakończ** zostanie **wyświetlona** strona Mapowanie użytkowników w kreatorze łączników w Centrum zgodności platformy Microsoft 365 stronie.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Krok 3. Mapowanie użytkowników i ukończenie konfiguracji łącznika

Aby zamapować użytkowników i ukończyć konfigurację łącznika w Centrum zgodności platformy Microsoft 365, wykonaj następujące czynności:

1. Na stronie **Mapowanie użytkowników chatterów usługi Salesforce Microsoft 365 użytkowników** włącz automatyczne mapowanie użytkowników. Elementy Czat usługi Salesforce zawierają właściwość o nazwie *Email*, która zawiera adresy e-mail użytkowników w Twojej organizacji. Jeśli łącznik może skojarzyć ten adres z Microsoft 365, elementy są importowane do skrzynki pocztowej tego użytkownika.

2. Kliknij **przycisk** Dalej, przejrzyj ustawienia, a następnie przejdź do strony  Łączniki danych, aby wyświetlić postęp procesu importowania nowego łącznika.

## <a name="step-4-monitor-the-salesforce-chatter-connector"></a>Krok 4. Monitorowanie łącznika Czat usługi Salesforce

Po utworzeniu łącznika Czat usługi Salesforce możesz sprawdzić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do łączników [https://compliance.microsoft.com](https://compliance.microsoft.com/) **danych w lewym okienku narracji i** kliknij je.

2. Kliknij **kartę Łączniki** , a następnie kliknij łącznik **Czat usługi Salesforce** , aby wyświetlić stronę wysuwu zawierającą właściwości i informacje o łączniku.

3. W **obszarze Stan łącznika ze** źródłem **kliknij link Pobierz** dziennik, aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane, które zostały zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie importowanie załączników ani elementów większych niż 10 MB nie jest obsługuje. Obsługa większych elementów będzie dostępna w późniejszym terminie.