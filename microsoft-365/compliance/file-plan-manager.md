---
title: Zarządzanie etykietami przechowywania na przestrzeni całego cyklu życia zawartości przy użyciu planu przechowywania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: af398293-c69d-465e-a249-d74561552d30
description: Plan zarządzania plikami zapewnia zaawansowane funkcje zarządzania etykietami przechowywania.
ms.custom: seo-marvel-may2020
ms.openlocfilehash: 2e028bae676b949c662a86178bac5e8ccdc557bf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317713"
---
# <a name="use-file-plan-to-create-and-manage-retention-labels"></a>Tworzenie etykiet przechowywania i zarządzanie nimi przy użyciu planu plików

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Mimo że można tworzyć etykiety przechowywania i zarządzać nimi na podstawie zarządzania informacjami w aplikacji Centrum zgodności platformy Microsoft 365, plan ewidencji z zarządzania  rekordami **oferuje dodatkowe** funkcje zarządzania:

- Etykiety przechowywania można tworzyć zbiorczo, importując odpowiednie informacje z arkusza kalkulacyjnego.

- Możesz wyeksportować informacje z istniejących etykiet przechowywania do analizy i współpracy w trybie offline.

- Wyświetlane są więcej informacji na temat etykiet przechowywania, aby ułatwić przeglądanie ustawień wszystkich etykiet przechowywania i ich wyświetlanie w jednym widoku.

- Deskrypcje planu plików obsługują dodatkowe i opcjonalne informacje na temat poszczególnych etykiet.

Plan przechowywania może być używany dla wszystkich etykiet przechowywania, nawet jeśli zawartość nie jest oznaczana jako rekord.

Aby uzyskać informacje na temat etykiet przechowywania i sposobu ich używania, zobacz Informacje [o zasadach przechowywania i etykietach przechowywania](retention.md).

## <a name="accessing-file-plan"></a>Uzyskiwanie dostępu do planu plików

Aby uzyskać dostęp do planu plików, musisz mieć jedną z następujących ról administratora:
    
- Menedżer przechowywania

- Menedżer przechowywania tylko do wyświetlania

W Centrum zgodności platformy Microsoft 365 przejdź do **tematu Plan zarządzania** plikami **SolutionsRecords** >  > **:**

![Strona planu plików](../media/compliance-file-plan.png). 

Jeśli **zarządzanie rekordami** nie jest wyświetlane w okienku nawigacji, najpierw przewiń w dół i wybierz pozycję **Pokaż wszystko**.

## <a name="navigating-your-file-plan"></a>Nawigowanie po planie plików

Jeśli utworzono już etykiety przechowywania na podstawie  zarządzania informacjami w skoroszycie Centrum zgodności platformy Microsoft 365, etykiety te będą automatycznie wyświetlane w planie przechowywania. 

Podobnie, jeśli teraz utworzysz etykiety przechowywania w planie plików, będą one również  dostępne na stronie zarządzania informacjami, jeśli etykiety nie są skonfigurowane do oznaczania zawartości jako rekordu.

Na stronie **Plan** plików są dostępne wszystkie etykiety ze stanem i ustawieniami, opcjonalne deskryptory planu plików, opcja eksportu do analizowania lub włączania recenzji etykiet w trybie offline oraz opcja importu do tworzenia etykiet przechowywania. 

### <a name="label-settings-columns"></a>Ustawienia etykiet, kolumny

Wszystkie kolumny oprócz **etykiety Nazwa** można wyświetlać lub ukrywać, wybierając opcję **Dostosuj** kolumny. Jednak domyślnie w kilku pierwszych kolumnach są wyświetlane informacje o stanie etykiety i jego ustawieniach: 

- **Stan** określa, czy etykieta jest uwzględniana w zasadach etykiet, czy zasadach automatycznego stosowania (**Aktywne**), czy nie (**Nieaktywny**).

- **Na podstawie** tego, jak lub kiedy zaczyna się okres przechowywania. Prawidłowe wartości:
    - Zdarzenie
    - Po utworzeniu
    - Ostatnia modyfikacja
    - Po etykiecie

- **Is record** identifies if the item is marked as a record when the label is applied. Prawidłowe wartości:
    - Nie
    - Tak
    - Tak(przepisy)

- **Czas trwania przechowywania** określa okres przechowywania. Prawidłowe wartości:
    - Dni
    - Miesiące
    - Lata
    - Wieki
    - Brak

- **Typ zawartości** określa, co dzieje się z zawartością na koniec okresu przechowywania. Prawidłowe wartości:
    - Brak akcji
    - Automatyczne usuwanie
    - Wymagana recenzja

### <a name="file-plan-descriptors-columns"></a>Deskryptory planów plików w kolumnach

Plan przechowywania pozwala na dołączanie dodatkowych informacji jako części etykiet przechowywania. Te deskryptory planu plików zapewniają więcej opcji w celu poprawy możliwości zarządzania zawartością, która ma być oznaczona etykietą, i organizacji.

Domyślnie, począwszy od **identyfikatora** odwołania, w następnych kilku kolumnach są wyświetlane opcjonalne deskryptory planu plików, które można określić podczas tworzenia etykiety przechowywania lub edytowania istniejącej etykiety. 

Na początek możesz sprawdzić, czy są dostępne pewne wartości do wyboru dla następujących deskryptorów planu plików: 
- Funkcja/dział biznesowy
- Kategoria
- Typ urzędu
- Inicjowanie obsługi administracyjnej/cytat 

Przykładowe deskryptory planu przechowywania podczas tworzenia lub edytowania etykiety przechowywania:

![Deskrypcje planu przechowywania podczas tworzenia lub edytowania etykiety przechowywania.](../media/file-plan-descriptors.png)

Po wybraniu **przycisku** Wybierz dla każdego z tych opcjonalnych deskryptorów możesz wybrać jedną z dostępnych wartości lub utworzyć własne, a następnie wybrać je. Przykład: 

![Utwórz nowy deskryptor planu plików dla inicjowania obsługi/cytatu.](../media/file-plan-descriptors-create.png)

## <a name="create-retention-labels"></a>Tworzenie etykiet przechowywania

1. Na stronie **Plan plików** wybierz pozycję **+ Utwórz etykietęWklejanie** >  **pliku**

2. Postępuj zgodnie z monitami w procesie konfiguracji. Należy zachować ostrożność przy wybieranej nazwie, ponieważ po zapisaniu etykiety nie można jej zmienić.
    
    Aby uzyskać więcej informacji o ustawieniach przechowywania, [zobacz Ustawienia zachowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).
    
    Aby użyć etykiety przechowywania w celu deklarowania rekordów, wybierz pozycję Oznacz elementy jako **rekordy** lub **Oznacz elementy jako rekordy prawne**. Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiet przechowywania w celu deklarowania rekordów](declare-records.md#configuring-retention-labels-to-declare-records).

3. Po utworzeniu etykiety i wyświetleniu opcji publikowania etykiety, automatycznego zastosowania etykiety lub po prostu zapisania etykiety: Wybierz pozycję Po prostu zapisz na razie etykietę **, a** następnie wybierz pozycję **Gotowe**.

4. Powtórz te czynności, aby utworzyć więcej etykiet.

## <a name="edit-retention-labels"></a>Edytowanie etykiet przechowywania

Aby edytować istniejącą etykietę przechowywania, zaznacz ją na stronie **Plan** plików, a następnie wybierz opcję  Edytuj etykietę, aby rozpocząć proces edytowania przechowywania, który umożliwia zmianę opisu etykiety i wszystkich kwalifikujących się ustawień.

Po utworzeniu i zapisaniu etykiety nie można zmienić niektórych ustawień, takich jak:
- Nazwa etykiety przechowywania i ustawienia przechowywania z wyjątkiem okresu przechowywania. Nie można jednak zmienić okresu przechowywania, gdy okres przechowywania jest oparty na oznaczaniu elementów etykietą.
- Opcja oznaczania elementów jako rekordu.

## <a name="delete-retention-labels"></a>Usuwanie etykiet przechowywania

Możesz usunąć etykiety przechowywania, które nie są obecnie uwzględnione w żadnych [](create-apply-retention-labels.md) opublikowanych ani [automatycznych](apply-retention-labels-automatically.md) zasadach etykiet przechowywania, które nie są skonfigurowane na wypadek przechowywania opartego na zdarzeniach, lub oznaczać elementy jako rekordy prawne.

W przypadku etykiet przechowywania, które można usunąć, jeśli zostały one zastosowane do elementów, usunięcie zakończy się niepowodzeniem i zostanie wyświetlony link do Eksploratora zawartości identyfikujący elementy oznaczone etykietą.

Jednak wyświetlanie oznaczonych elementów w Eksploratorze zawartości może potrwać do dwóch dni. W tym scenariuszu etykieta przechowywania może zostać usunięta bez pokazywania linku do Eksploratora zawartości.

## <a name="export-all-retention-labels-to-analyze-or-enable-offline-reviews"></a>Eksportowanie wszystkich etykiet przechowywania w celu analizowania lub włączania recenzji w trybie offline

W planie przechowywania można wyeksportować szczegóły wszystkich etykiet przechowywania do pliku .csv, aby ułatwić okresowe przeglądy zgodności z uczestnikami projektu zarządzania danymi w organizacji.

Aby wyeksportować wszystkie etykiety przechowywania: Na **stronie Plan plików** kliknij pozycję **Eksportuj**:

![Opcja eksportu planu plików.](../media/compliance-file-plan-export-labels.png)

Zostanie otwarty .csv *, który zawiera wszystkie istniejące etykiety przechowywania. Przykład:

![Plik CSV zawierający wszystkie etykiety przechowywania.](../media/file-plan-csv-file.png)

## <a name="import-retention-labels-into-your-file-plan"></a>Importowanie etykiet przechowywania do planu plików

W planie plików nowe etykiety przechowywania można importować zbiorczo, używając .csv pliku o określonym formacie: 

1. Na stronie **Plan plików** kliknij pozycję **Importuj**: ![Opcja importowania planu plików](../media/compliance-file-plan-import-labels.png)

2. W **okienku Wypełnij i zaimportuj plan** plików wybierz **pozycję Pobierz pusty szablon**:

   ![Opcja pobrania szablonu pustego planu plików](../media/file-plan-blank-template-option.png)

3. Po pobraniu szablonu dodaj jeden wiersz na każdą etykietę i zapisz plik. W [następnej sekcji opisano](#information-about-the-label-properties-for-import) właściwości i prawidłowe wartości poszczególnych właściwości.
    
    Przykład wypełnionego szablonu:
    
    ![Szablon planu pliku z wypełnionymi informacjami.](../media/file-plan-filled-out-template.png)

4. Wybierz **Upload, aby** przekazać wypełniony szablon.
    
   Plan plików przekaże plik i poprawność wpisów.

5. W zależności od wyników sprawdzania poprawności:
    
    - Jeśli sprawdzanie poprawności zakończy się niepowodzeniem: zwróć uwagę na numer wiersza i nazwę kolumny, które należy poprawić w pliku importu. Popraw błędy w pliku i zapisz go, a następnie powtórz krok 4.
    
    - Jeśli sprawdzanie poprawności przejdzie pomyślnie: zostanie wyświetlony błąd Pomyślnie **zaimportowano plan plików, a** wpisy zostały pomyślnie przekonwertowane na etykiety przechowywania. Wybierz **pozycję** Gotowe, aby zamknąć okienko i automatycznie odświeżyć **stronę Plan** plików w celu wyświetlenia nowych etykiet.

Teraz możesz publikować nowe etykiety przechowywania lub stosować je automatycznie. Obie opcje możesz wykonać na karcie **Zasady etykiet** , wybierając pozycję **Publikuj** etykiety lub **Automatycznie zastosuj etykietę**.

### <a name="information-about-the-label-properties-for-import"></a>Informacje o właściwościach etykiety do zaimportowania

Poniższe informacje ułatwiają wypełnianie pobranego szablonu w celu zaimportowania nowych etykiet przechowywania. Importowanie może mieć długość maksymalną dla niektórych wartości:

- **LabelName**: Maksymalna długość 64 znaków
- **Komentarz** i **uwagi**: Maksymalna długość 1024 znaków
- Wszystkie inne wartości: Nieograniczona długość
<br/>

|Właściwość|Wpisać|Wymagany|Prawidłowe wartości|
|:-----|:-----|:-----|:-----|
|LabelName|Ciąg|Tak|Ta właściwość określa nazwę etykiety przechowywania i musi być unikatowa w dzierżawie. Obsługiwane znaki importowane: a-z, A-Z, 0-9, łącznik (-) i znak spacji.|
|Komentowanie|Ciąg|Nie|Ta właściwość pozwala dodać opis etykiety przechowywania dla administratorów. Ten opis jest wyświetlany tylko administratorom, którzy zarządzają etykietą przechowywania w centrum zgodności.|
|Uwagi|Ciąg|Nie|Ta właściwość pozwala dodać opis etykiety przechowywania dla użytkowników. Ten opis jest wyświetlany, gdy użytkownicy umieszczają wskaźnik myszy na etykiecie aplikacji, Outlook, SharePoint i OneDrive. Jeśli pozostawisz tę właściwość pustą, zostanie wyświetlony domyślny opis, który wyjaśnia ustawienia przechowywania etykiety. |
|IsRecordLabel|Ciąg|Nie, chyba **że** regulacyjna ma **wartość PRAWDA**|Ta właściwość określa, czy etykieta oznacza zawartość jako rekord. Prawidłowe wartości to: </br>**PRAWDA**: Etykieta oznacza element jako rekord, dlatego nie można go usunąć. </br>**FAŁSZ**: Etykieta nie oznacza zawartości jako rekordu. Jest to wartość domyślna. </br> </br> Zależności grup: Po określonej właściwości należy również określić grupę RetentionAction, RetentionDuration i RetentionType (Typ przechowywania).|
|RetentionAction|Ciąg|Nie, chyba **że określono wartość RetentionDuration**, **RetentionType** lub **ReviewerEmail**|Ta właściwość określa, jakie działanie ma być podjęcia po wygaśnięciu wartości określonej przez właściwość RetentionDuration (jeśli jest określona). Prawidłowe wartości to: </br>**Usuń**. Elementy starsze niż wartość określona przez właściwość RetentionDuration są usuwane.</br>**Zachowaj**. Zachowaj elementy przez czas określony przez właściwość Okres przechowywania i nie robisz nic po wygaśnięciu okresu. </br>**KeepAndDelete**: Zachowaj elementy przez czas trwania określony przez właściwość RetentionDuration i usuwaj je po wygaśnięciu okresu. </br> </br> Zależności grup: Gdy ta właściwość jest określona, należy również określić wartości RetentionDuration i RetentionType (Typ przechowywania). |
|Okres przechowywania|Ciąg|Nie, chyba **że określono funkcje** przechowywania **lub typ** przechowywania|Ta właściwość określa liczbę dni przechowywania zawartości. Prawidłowe wartości to: </br>**Bez ograniczeń**: elementy będą przechowywane przez czas nieograniczony. </br>**_n_*: dodatnia liczba całkowita w dniach; na przykład **365**. Maksymalna obsługiwana liczba to 24 855 ( 68 lat). Jeśli potrzebujesz więcej niż wartość maksymalna, użyj funkcji Bez ograniczeń.</br> </br> Zależności grup: Po określonej właściwości należy również określić właściwości RetentionAction i RetentionType (Typ przechowywania).
|RetentionType (Typ przechowywania)|Ciąg|Nie, chyba **że określono funkcje** **przechowywania lub Okres** przechowywania|Ta właściwość określa, czy czas trwania przechowywania (jeśli jest określony) jest obliczany na podstawie daty utworzenia zawartości, daty zdarzenia, daty oznaczonej etykietą lub daty ostatniej modyfikacji. Prawidłowe wartości to: </br>**CreationAgeInDays**</br>**EventAgeInDays**</br>**TaggedAgeInDays**</br>**ModificationAgeInDays** </br> </br> Zależności grup: Po określonej właściwości należy również określić grupę RetentionAction i RetentionDuraction.|
|ReviewerEmail|SmtpAddress|Nie|Gdy ta właściwość jest określona, po wygaśnięciu czasu trwania przechowywania zostanie wyzwolona recenzja rozsyłania. Ta właściwość określa adres e-mail recenzenta w dzierżawie dla akcji przechowywania **KeepAndDelete** . </br> </br> Możesz dołączyć adresy e-mail poszczególnych użytkowników, grup dystrybucyjnych lub grup zabezpieczeń w dzierżawie. Określ wiele adresów e-mail, oddzielając je średnikami. </br> </br> Zależności grup: Po określonej właściwości należy również określić grupę **RetentionAction** (musi to być **KeepAndDelete**), **RetentionDuration** i **RetentionType** (Typ przechowywania).|
|ReferenceId|Ciąg|Nie|Ta właściwość określa wartość wyświetlaną w deskryptorze  planu pliku identyfikatora odwołania, którego można użyć jako unikatowej wartości dla organizacji.| 
|DepartmentName|Ciąg|Nie|Ta właściwość określa wartość wyświetlaną w deskryptorze planu pliku funkcja **/** dział.|
|Kategoria|Ciąg|Nie|Ta właściwość określa wartość wyświetlaną w deskryptorze  planu pliku kategorii.|
|Podkategoria|Ciąg|Nie|Ta właściwość określa wartość wyświetlaną w deskryptorze **planu pliku** podkategorie.|
|AuthorityType (Typ_urzędu)|Ciąg|Nie|Ta właściwość określa wartość wyświetlaną w deskryptorze **planu pliku typu** Urząd.|
|CitationName|Ciąg|Nie|Ta właściwość określa nazwę cytatu wyświetlanego w deskrypcie Plan pliku **inicjowania/** cytowania. Na przykład "Sarbanes-Oxley Act of 2002". |
|CitationUrl|Ciąg|Nie|Ta właściwość określa adres URL wyświetlany w deskryptorze planu pliku **inicjowania/** cytowania.|
|CitationJurisdiction|Ciąg|Nie|Ta właściwość określa jurysdykcję lub agencję wyświetlaną w deskrypcie planu pliku inicjowania **/** cytowania. Na przykład "U.S. Securities and Exchange Commission (SEC)".|
|Przepisy|Ciąg|Nie|Ta właściwość określa, czy etykieta oznacza zawartość jako rekord prawa, który jest [bardziej](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) restrykcyjny niż rekord. Aby użyć tej konfiguracji etykiet, dzierżawa musi zostać skonfigurowana w taki sposób, aby była wyświetlana opcja oznaczania zawartości jako rekordu [prawnego lub sprawdzanie](declare-records.md#how-to-display-the-option-to-mark-content-as-a-regulatory-record) poprawności importu nie powiedzie się. Prawidłowe wartości to: </br>**PRAWDA**: etykieta oznacza element jako rekord przepisów prawa. Należy również ustawić dla właściwości **IsRecordLabel wartość** TRUE.</br>**FAŁSZ**: Etykieta nie oznacza zawartości jako rekordu prawnego. Jest to wartość domyślna.|
|EventType|Ciąg|Nie, chyba **że typ przechowywania** **to EventAgeInDays**|Ta właściwość określa typ zdarzenia używany do przechowywania [opartego na zdarzeniach](event-driven-retention.md). Określanie istniejącego typu zdarzenia, który jest wyświetlany **w zarządzanie** rekordamiZ  > **zarządzanie** >  **typami zdarzeń**. Możesz również użyć polecenia [cmdlet Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype) , aby wyświetlić dostępne typy zdarzeń. Mimo że istnieje kilka wbudowanych typów zdarzeń, takich jak Aktywność  pracownika i Okres istnienia **produktu, możesz** również tworzyć własne typy zdarzeń. </br> </br> Jeśli określisz własny typ zdarzenia, musi on istnieć przed importowaniem, ponieważ poprawność nazwy jest sprawdzana w ramach procesu importowania.|
|||

## <a name="next-steps"></a>Następne kroki

Teraz, po utworzeniu etykiet przechowywania, można je dodawać do elementów przez opublikowanie etykiet lub automatyczne stosowanie:
- [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)