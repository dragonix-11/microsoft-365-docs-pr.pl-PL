---
title: Importowanie importowanych Advanced eDiscovery przypadku
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Użyj narzędzia importu, aby szybko dodać wiele elementów do przechowywania danych i skojarzonych z nimi źródeł danych do sprawy w Advanced eDiscovery.
ms.openlocfilehash: 5e2ce53a227462a1fddd7785faf83355ca70611c
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2021
ms.locfileid: "63007864"
---
# <a name="import-custodians-to-an-advanced-ediscovery-case"></a>Importowanie importowanych Advanced eDiscovery przypadku

W Advanced eDiscovery przypadków, w których znajduje się wiele elementów przechowaczy, można zaimportować wiele elementów przechowywczych jednocześnie przy użyciu pliku CSV zawierającego informacje niezbędne do dodania ich do sprawy.

## <a name="import-custodians"></a>Importowanie importowanych importerów

1. Otwórz kartę Advanced eDiscovery i wybierz **kartę Źródła** danych.

2. Kliknij **pozycję Dodaj źródło** **danychImportuj** >  opiekunów.

3. Na stronie **wysuwanego importowania** importowania kliknij  pozycję Pobierz pusty szablon, aby pobrać plik CSV z szablonem do wytyczania i importowania.

   ![Pobierz szablon CSV ze strony wysuwanych importowania wytłaczanych plików.](../media/ImportCustodians1.png)

4. Dodaj informacje typu poszukasz w pliku CSV i zapisz go na komputerze lokalnym. Aby uzyskać [informacje na](#custodian-csv-file) temat wymaganych właściwości w pliku CSV, zobacz sekcję Zbędna plik CSV.

5. Po przygotowaniu pliku CSV  >  z informacjami o kopiach wróć na kartę Źródła danych i  ponownie kliknij pozycję Dodaj źródło **danychImportuj pliki przechowywania**.

6. Na stronie **wysuwanego importowania** importowania kliknij przycisk **Przeglądaj** , a następnie przekaż plik CSV zawierający informacje o tym pliku.

   Po przesłaniu pliku CSV zostanie utworzone zadanie o nazwie **BulkAddCustodian**, które będzie wyświetlane na **karcie** Zadania. Zadanie sprawdza poprawność przechowywania i skojarzonych z nimi źródeł danych, a następnie dodaje je do  strony Źródła danych sprawy.

## <a name="custodian-csv-file"></a>Szybki plik CSV

Po pobraniu szablonu wszerego w formacie CSV możesz dodać opiekunów i ich źródło danych w każdym wierszu. Nie zmieniaj nazw kolumn w wierszu nagłówka. Kolumny lokalizacji typu obciążenia i obciążenia pracą można skojarzyć z innymi źródłami danych.

| Nazwa kolumny|Opis|
|:------- |:------------------------------------------------------------|
|**Wybłędy kontaktoweEmail**     |Adres e-mail upn użytkownika w uchocie Na przykład: sarad@contoso.onmicrosoft.com.           |
|**Exchange włączone** | Wartość PRAWDA/FAŁSZ uwzględnia skrzynkę pocztową użytkownika- lub nie.      |
|**OneDrive włączone** | Wartość PRAWDA/FAŁSZ, aby uwzględnić lub nie uwzględnić konta OneDrive dla Firm- |
|**Is OnHold**        | Wartość PRAWDA/FAŁSZ wskazująca, czy należy umieścić wstrzymywanie źródeł danych w danych do przechowywania. <sup>1</sup>     |
|**Workload1 Type**         |Wartość ciągu wskazująca typ źródła danych, które ma skojarzyć ze współpracownikiem. Możliwe wartości: <br/>- ExchangeMailbox<br/> - SharePointSite<br/>- <sup>TeamsMailbox2</sup><br/>- <sup>YammerMailbox2</sup>| 
|**Lokalizacja obciążenia pracą1**     | W zależności od typu obciążenia pracą będzie to lokalizacja źródła danych. Może to być na przykład adres e-mail Exchange skrzynki pocztowej lub adres URL SharePoint pocztowej. |
|||

> [!NOTE]
> <sup>1</sup> Jeśli wstrzymasz więcej niż 1000 skrzynek pocztowych lub 100 witryn, system automatycznie przeskaluje hold usługi zbierania elektronicznych materiałów dowodowych zgodnie z potrzebami. Oznacza to, że system automatycznie doda lokalizacje danych do wielu blokady, zamiast dodawać je do jednego blokady. Nadal jednak obowiązuje limit 10 000 przypadków na organizację. Aby uzyskać więcej informacji na temat limitów blokowania, [zobacz Limity w Advanced eDiscovery](limits-ediscovery20.md#hold-limits).
<br>
> <sup>2</sup> Jeśli dołączysz obciążenia usługi TeamsMailbox i YammerMailbox do pliku CSV, witryna grupy (TeamSite i YammerSite) zostanie domyślnie dodana automatycznie. Nie musisz osobno określać w pliku CSV teamssite i yammersite.

Oto przykładowy plik CSV z informacjami o użytkownikach:<br/><br/>

|Wybłędy kontaktoweEmail      | Exchange włączone | OneDrive włączone | Is OnHold | Workload1 Type | Lokalizacja obciążenia pracą1             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@contoso.onmicrosoft.com | TRUE (PRAWDA)             | TRUE (PRAWDA)             | TRUE (PRAWDA)      | SharePointSite | https://contoso.sharepoint.com |
|pillarp@contoso.onmicrosoft.com | TRUE (PRAWDA)             | TRUE (PRAWDA)             | TRUE (PRAWDA)      | |  |
|johnj@contoso.onmicrosoft.com|TRUE (PRAWDA)|TRUE (PRAWDA)|TRUE (PRAWDA)||
|sarad@contoso.onmicrosoft.com|TRUE (PRAWDA)|TRUE (PRAWDA)|TRUE (PRAWDA)|ExchangeMailbox|saradavis@contoso.onmicrosoft.com
||||||

> [!NOTE]
> Aby zaimportować nieaktywną skrzynkę pocztową jako opiekuna lub skojarzyć nieaktywną skrzynkę pocztową z innym opiekunem, dodaj prefiks "." do adresu UPN nieaktywnej skrzynki pocztowej.

## <a name="custodian-and-data-source-validation"></a>Poprawność danych źródłowych i źródłowych danych

Po przesłaniu pliku CSV z wiadącym Advanced eDiscovery czynności:

1. Sprawdza poprawność pochłoników i ich źródeł danych.

2. Indeksuje wszystkie źródła danych dla każdego sygnaleratora i umieszcza je w hold (jeśli dla właściwości **Is OnHold** w pliku CSV ustawiono wartość TRUE).

### <a name="custodian-validation"></a>Sprawdzanie poprawności danych po stronie wytłaczyń

Obecnie importowanie jest możliwe tylko w przypadku osób, które są uwzględnione w Azure Active Directory organizacji (Azure AD).

Narzędzie do importowania wiadów umożliwia znalezienie i zweryfikowanie poprawność po stronie poprawność danych po stronie nagłówków przy użyciu wartości UPN w kolumnie Dane kontaktowe i poczty **e-mail w** pliku CSV. Źródła danych, których poprawności jest sprawdzana, są automatycznie dodawane do sprawy i **wymienione na karcie** Źródła danych sprawy. Jeśli nie można sprawdzić poprawność wołodnego, jest on wymieniony w dzienniku błędów zadania BulkAddCustodian wyświetlonego na karcie Zadania  w tym przypadku. Nieuprawnione przechowywania nie są dodawane do sprawy ani wyświetlane na **karcie Źródła** danych.

### <a name="data-source-validation"></a>Sprawdzanie poprawności źródła danych

Po weryfikacji i dodaniu do sprawy wszystkich podstawowych skrzynek pocztowych i kont OneDrive powiązanych z przechowacyjną skrzynką pocztową.

Jeśli jednak nie będzie można odnaleźć żadnego z innych źródeł danych (takich jak witryny SharePoint, Microsoft Teams, grupy Microsoft 365 lub grupy Yammer) skojarzone z opiekunem, żaden z nich nie zostanie przypisany do osoby przechłodnej, a wartość Nie poprawność jest wyświetlana w kolumnie Stan obok właściwości w źródłach  **danych**   .

Aby dodać sprawdzane źródła danych dla opiekuna:

1. Na karcie **Źródła** danych wybierz kartę przechowawczy zawierającą źródła danych, które nie są sprawdzane.

2. Na stronie wysuwu wiadce można przewinąć do sekcji **Lokalizacje** przechowywania, aby wyświetlić sprawdzane i nieuprawnione źródła danych skojarzone z lokalizacjami przechowywania.

3. Kliknij **pozycję** Edytuj w górnej części wysuwu strony, aby usunąć nieprawidłowe źródła danych lub dodać nowe.

4. Po usunięciu nieuprawnionych źródeł danych lub dodaniu nowego źródła danych wartość  Aktywny jest wyświetlana  w kolumnie Stan dla opiekuna na **karcie Źródła** danych. Aby dodać źródła, które wcześniej wydawały się być nieprawidłowe, wykonaj poniższe kroki zaradcze w celu ich ręcznego dodania do opiekuna.

### <a name="remediating-invalid-data-sources"></a>Rozwiązywanie problemów z nieprawidłowymi źródłami danych

Aby ręcznie dodać i skojarzyć wcześniej nieprawidłowe źródło danych:

1. Na karcie **Źródła** danych wybierz opiekuna, który ma ręcznie dodać i skojarzyć nieprawidłowe wcześniej źródło danych.

2. Kliknij **pozycję Edytuj** w górnej części wysuwu strony, aby skojarzyć skrzynki pocztowe, witryny, Teams lub Yammer z opiekunem. W tym celu kliknij **pozycję Edytuj** obok odpowiedniego typu lokalizacji danych.

3. Kliknij **przycisk Dalej** , aby wyświetlić **stronę Ustawienia wstrzymywania** i skonfigurować ustawienie blokowania dla dodanych źródeł danych.

4. Kliknij **przycisk Dalej** , aby wyświetlić **stronę Przeglądanie treści** , a następnie kliknij **przycisk Prześlij,** aby zapisać zmiany.
