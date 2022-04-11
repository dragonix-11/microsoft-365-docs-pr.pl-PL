---
title: Archiwizowanie danych zbierania elektronicznych materiałów dowodowych usługi Slack w celu Microsoft 365 przy użyciu łącznika danych dostarczonego przez firmę Microsoft
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
description: Dowiedz się, jak skonfigurować i użyć łącznika danych zbierania elektronicznych materiałów dowodowych usługi Slack dostarczonego przez firmę Microsoft w celu importowania i archiwizowania danych wiadomości błyskawicznych.
ms.openlocfilehash: 7ff8140ee75c146f79f14fbd474ab4e6780156ad
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760894"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data-preview"></a>Konfigurowanie łącznika do archiwizowania danych zbierania elektronicznych materiałów dowodowych usługi Slack (wersja zapoznawcza)

Łącznik danych usługi Slack eDiscovery udostępniany przez firmę Microsoft ułatwia importowanie i archiwizowanie danych wiadomości błyskawicznych (takich jak wiadomości, załączniki, linki i poprawki) z obszarów roboczych usługi Slack w organizacji w celu Microsoft 365. Łącznik danych pobiera dane z interfejsu API usługi Slack, konwertuje je na format wiadomości e-mail, a następnie importuje je do skrzynek pocztowych użytkowników w Microsoft 365. Po zaimportowaniu danych usługi Slack możesz zastosować rozwiązania zgodności, takie jak blokada postępowania sądowego, Advanced eDiscovery, zgodność z komunikacją i ustawienia przechowywania do zawartości usługi Slack. Importowanie i archiwizowanie danych w Microsoft 365 przy użyciu łącznika danych zbierania elektronicznych materiałów dowodowych usługi Slack może pomóc organizacji zachować zgodność z zasadami rządowymi i regulacyjnymi.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Omówienie archiwizacji danych zbierania elektronicznych materiałów dowodowych usługi Slack

W poniższym omówieniu wyjaśniono proces korzystania z łącznika danych firmy Microsoft do archiwizowania danych usługi Slack w Microsoft 365.

![Przepływ pracy archiwizacji zbierania elektronicznych materiałów dowodowych usługi Slack.](../media/SlackMSFTConnectorWorkflow.png)

1. Twoja organizacja współpracuje z usługą Slack w celu skonfigurowania i skonfigurowania obszaru roboczego usługi Slack.

2. Po skonfigurowaniu łącznika danych wiadomości z obszarów roboczych usługi Slack w organizacji są kopiowane do skrzynek pocztowych użytkowników w Microsoft 365. Łącznik danych konwertuje również zawartość wiadomości czatu na format wiadomości e-mail.

3. Łącznik importuje przekonwertowane wiadomości czatu do skrzynek pocztowych określonych użytkowników. Podfolder w folderze Skrzynka odbiorcza o nazwie **Slack eDiscovery** jest tworzony w skrzynkach pocztowych użytkownika, a elementy wiadomości czatu są importowane do tego folderu.

## <a name="before-you-set-up-a-connector"></a>Przed skonfigurowaniem łącznika

- Twoja organizacja potrzebuje subskrypcji usługi Enterprise Grid dla usługi Slack. Aby uzyskać więcej informacji, zobacz [Subskrypcje i funkcje usługi Slack](https://slack.com/intl/en-gb/help/articles/115003205446-Slack-subscriptions-and-features-).

- Użytkownik, który tworzy łącznik danych, musi mieć przypisaną rolę aplikacji **Właściciele organizacji** w organizacji usługi Slack. Aby uzyskać więcej informacji, zobacz [Typy ról w usłudze Slack](https://slack.com/intl/en-gb/help/articles/360018112273-Types-of-roles-in-Slack).

- Uzyskaj nazwę użytkownika i hasło dla konta usługi Slack enterprise w organizacji. Te poświadczenia są używane do logowania się do tego konta podczas tworzenia łącznika danych. Zaleca się również automatyczne aprowizowanie użytkowników w organizacji usługi Slack skonfigurowane do korzystania z logowania jednokrotnego. [Role w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Użytkownikowi, który tworzy łącznik usługi Slack eDiscovery, należy przypisać rolę administratora łącznika danych. Ta rola jest wymagana do dodawania łączników na stronie **Łączniki danych** w Centrum zgodności platformy Microsoft 365. Ta rola jest domyślnie dodawana do wielu grup ról. Aby uzyskać listę tych grup ról, zobacz sekcję "Role w centrach zabezpieczeń i zgodności" w obszarze [Uprawnienia w Centrum zgodności & zabezpieczeń](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatywnie administrator w organizacji może utworzyć niestandardową grupę ról, przypisać rolę administratora łącznika danych, a następnie dodać odpowiednich użytkowników jako członków. Aby uzyskać instrukcje, zobacz sekcję "Tworzenie niestandardowej grupy ról" w obszarze [Uprawnienia w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-a-slack-ediscovery-connector"></a>Krok 1. Tworzenie łącznika zbierania elektronicznych materiałów dowodowych usługi Slack

1. Przejdź do <https://compliance.microsoft.com> obszaru i kliknij pozycję **Łączniki danych** w okienku nawigacji po lewej stronie.

2. Na karcie **Przegląd** kliknij pozycję **Filtruj** i wybierz pozycję **Według firmy Microsoft**, a następnie zastosuj filtr.

3. Kliknij **pozycję Slack eDiscovery (wersja zapoznawcza)**.

4. Na stronie Opis produktu **Slack eDiscovery (wersja zapoznawcza)** kliknij pozycję **Dodaj łącznik**.

5. Na stronie Kreator **warunków użytkowania usługi** kliknij pozycję **Akceptuj**.

6. Wprowadź unikatową nazwę identyfikującą łącznik, a następnie kliknij przycisk **Dalej**. Wprowadzona nazwa zidentyfikuje łącznik na stronie **Łączniki danych** po jego utworzeniu.

## <a name="step-2-sign-into-your-slack-organization"></a>Krok 2. Logowanie się do organizacji usługi Slack

1. Na stronie Kreator **logowania do usługi Slack** kliknij pozycję **Zaloguj się do usługi Slack** , aby zalogować się do obszaru roboczego usługi Slack w organizacji.

2. Na stronie **Slack Sign into your workspace (Zaloguj się do obszaru roboczego** ) wpisz nazwę obszaru roboczego, z którego chcesz zarchiwizować dane, a następnie kliknij przycisk **Kontynuuj**.

   Zostanie wyświetlona strona z nazwą obszaru roboczego usługi Slack i monitem o zalogowanie się.

3. Kliknij link w ciągu **Właściciele organizacji mogą również zalogować się tutaj**.

4. Na stronie logowania obszaru roboczego wprowadź adres e-mail i hasło dla konta usługi Slack enterprise w organizacji, a następnie kliknij pozycję **Zaloguj** się.

   Po pomyślnym zalogowaniu zostanie wyświetlona strona, która żąda uprawnień dostępu do organizacji usługi Slack przez aplikację łącznika.

5. Kliknij pozycję **Zezwalaj** , aby zezwolić aplikacji na administrowanie organizacją.

   Po kliknięciu przycisku **Zezwalaj** zostanie zamknięta strona usługi Slack i zostanie **wyświetlona strona Map Slack eDiscovery users to Microsoft 365 users (Map Slack eDiscovery users to Microsoft 365 users page in the connector wizard(Map Slack eDiscovery users to Microsoft 365 users**) w kreatorze łącznika.

## <a name="step-3-specify-the-users-to-import-data-for"></a>Krok 3. Określanie użytkowników do zaimportowania danych

Wybierz jedną z następujących opcji, aby określić użytkowników, których dane zbierania elektronicznych materiałów dowodowych usługi Slack mają zostać zaimportowane.

- **Wszyscy użytkownicy w organizacji**. Wybierz tę opcję, aby zaimportować dane dla wszystkich użytkowników.

- **Blokada dotyczy tylko użytkowników w postępowaniu sądowym**. Wybierz tę opcję, aby zaimportować dane tylko dla użytkowników, których skrzynki pocztowe zostały wstrzymane w postępowaniu sądowym. Ta opcja importuje dane do skrzynek pocztowych użytkowników z właściwością LitigationHoldEnabled ustawioną na wartość True. Aby uzyskać więcej informacji, zobacz [Tworzenie blokady postępowania sądowego](create-a-litigation-hold.md).

## <a name="step-4-map-users-and-select-data-types-to-import"></a>Krok 4. Mapowanie użytkowników i wybieranie typów danych do zaimportowania

1. Skonfiguruj jedną lub obie z następujących opcji, aby mapować użytkowników usługi Slack na skrzynki pocztowe Microsoft 365.

   - **Automatyczne mapowanie użytkownika**. Wybierz tę opcję, aby automatycznie mapować nazwy użytkowników usługi Slack na Microsoft 365 skrzynki pocztowe. Łącznik używa wartości właściwości *Email* , która zawiera każdy komunikat lub element usługi Slack. Ta właściwość jest wypełniana adresem e-mail każdego uczestnika wiadomości. Jeśli łącznik może skojarzyć adresy e-mail z odpowiednimi użytkownikami Microsoft 365, element zostanie zaimportowany do Microsoft 365 skrzynki pocztowej tych użytkowników. Aby użyć tej opcji, musisz mieć skonfigurowane logowania jednokrotnego dla swojej organizacji usługi Slack.

   - **Mapowanie użytkownika niestandardowego**. Istnieje również możliwość użycia mapowania użytkownika niestandardowego zamiast (lub oprócz) automatycznego mapowania użytkowników. Za pomocą tej opcji należy utworzyć plik CSV, a następnie przekazać go, który mapuje identyfikator członka usługi Slack użytkowników na ich Microsoft 365 adres e-mail. W tym celu kliknij pozycję **Pobierz szablon mapowania CSV**, wypełnij plik CSV identyfikatorem członka usługi Slack i Microsoft 365 adres e-mail dla wszystkich użytkowników w organizacji, a następnie wybierz i przekaż plik CSV do kreatora. Pamiętaj, aby nie zmieniać nagłówków kolumn w pliku CSV. Oto przykład pliku mapowania CSV:

     |**ExternalUserId**  | **O365UserMailbox**   |
     |:-------------------|:-----------------------|
     | U01MDTF0QV6        | alexjones@contoso.onmicrosoft.com |
     | U02MDTF1RW7| pilarp@contoso.onmicrosoft.com|
     | U03MDTF2SX8 | sarad@contoso.onmicrosoft.com|
     |||

   > [!TIP]
   > Identyfikatory elementów członkowskich dla użytkowników można uzyskać, klikając przycisk ... Przycisk Więcej w profilu użytkownika, a następnie wybierz pozycję **Kopiuj identyfikator członka**. Alternatywnie możesz użyć [metody interfejsu API users.list](https://api.slack.com/methods/users.list) usługi Slack, aby uzyskać identyfikatory dla wszystkich członków zespołu usługi Slack.

   Jeśli włączysz automatyczne mapowanie użytkowników i udostępnisz niestandardowy plik mapowania, łącznik najpierw przyjrzy się niestandardowemu plikowi mapowania, aby zamapować użytkownika usługi Slack na Microsoft 365 skrzynkę pocztową. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 odpowiadającego użytkownikowi usługi Slack, łącznik użyje właściwości *Poczta e-mail* elementu Slack. Jeśli łącznik nie znajdzie prawidłowego użytkownika Microsoft 365 w niestandardowym pliku mapowania lub we właściwości *Email* elementu wiadomości, element nie zostanie zaimportowany.

2. Na stronie **Kreator wybierania typów danych do zaimportowania** wybierz typy danych usługi Slack, które chcesz zaimportować. Jeśli chcesz zaimportować komunikaty ze wszystkich kanałów, wybierz wszystkie opcje. W przeciwnym razie wybierz tylko typy danych, które chcesz zaimportować.

     Oprócz komunikatów usługi Slack można również określić inne typy zawartości usługi Slack do zaimportowania do Microsoft 365. 

3. Po skonfigurowaniu typów danych do zaimportowania kliknij przycisk **Dalej**, przejrzyj ustawienia łącznika, a następnie kliknij przycisk **Zakończ** , aby utworzyć łącznik.

## <a name="step-5-monitor-the-slack-ediscovery-connector"></a>Krok 5. Monitorowanie łącznika zbierania elektronicznych materiałów dowodowych usługi Slack

Po utworzeniu łącznika usługi Slack eDiscovery możesz wyświetlić stan łącznika w Centrum zgodności platformy Microsoft 365.

1. Przejdź do strony [https://compliance.microsoft.com](https://compliance.microsoft.com/) i kliknij pozycję **Łączniki danych** w lewym pasku nawigacyjnym.

2. Kliknij kartę **Łączniki** , a następnie wybierz łącznik **Slack eDiscovery** , aby wyświetlić stronę wysuwaną zawierającą właściwości i informacje o łączniku.

3. W obszarze **Stan łącznika ze źródłem** kliknij link **Pobierz dziennik** , aby otworzyć (lub zapisać) dziennik stanu łącznika. Ten dziennik zawiera dane zaimportowane do chmury firmy Microsoft.

## <a name="known-issues"></a>Znane problemy

- Obecnie nie obsługujemy importowania załączników ani elementów o rozmiarze większym niż 10 MB. Obsługa większych elementów będzie dostępna w późniejszym terminie.
