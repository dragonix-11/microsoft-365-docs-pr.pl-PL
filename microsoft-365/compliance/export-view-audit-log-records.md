---
title: Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
ms.custom: seo-marvel-apr2020
description: W tym artykule dowiesz się, jak eksportować, konfigurować i wyświetlać Microsoft 365 dziennika inspekcji.
ms.openlocfilehash: efb71ea0ff0b7098c3524707cff101d7ba25877f
ms.sourcegitcommit: 678e827a1c3bc9f4edfc48003f9b29f7bbf20ab5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2021
ms.locfileid: "63020846"
---
# <a name="export-configure-and-view-audit-log-records"></a>Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji

Po przeszukiwaniu dziennika inspekcji i pobraniu wyników wyszukiwania do pliku CSV plik ten zawiera kolumnę o nazwie **Dane** inspekcji, która zawiera dodatkowe informacje o każdym z zdarzeń. Dane w tej kolumnie są formatowane jako obiekt JSON, który zawiera wiele właściwości skonfigurowanych jako *pary właściwość:* wartość rozdzielone przecinkami. Za pomocą funkcji przekształcania JSON w Edytorze dodatku Power Query w programie Excel można podzielić każdą właściwość w obiekcie JSON w kolumnie **Dane** inspekcji na wiele kolumn, dzięki czemu każda właściwość ma własną kolumnę. Pozwala to sortować i filtrować według jednej lub większej liczby tych właściwości, co może ułatwić szybkie zlokalizowanie określonych danych inspekcji.

## <a name="step-1-export-audit-log-search-results"></a>Krok 1. Eksportowanie wyników przeszukiwania dziennika inspekcji

Pierwszym krokiem jest przeszukanie dziennika inspekcji, a następnie wyeksportowanie wyników w pliku wartości rozdzielanych przecinkami (CSV) na komputer lokalny.
  
1. W razie [potrzeby uruchom przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md#search-the-audit-log) i w razie potrzeby poprawiaj kryteria wyszukiwania, aż zostaną uzyskane odpowiednie wyniki.

2. Na stronie wyników wyszukiwania kliknij pozycję **EksportujPobierz** >  **wszystkie wyniki**.

   ![Kliknij pozycję Pobierz wszystkie wyniki.](../media/ExportAuditSearchResults.png)

   Ta opcja powoduje wyeksportowanie wszystkich rekordów inspekcji z przeszukiwania dziennika inspekcji, które uruchomiono w kroku 1, i dodanie nieprzetworzonych danych z dziennika inspekcji do pliku CSV. Przygotowanie pliku do pobrania dla dużego wyszukiwania zajmuje trochę czasu. Duże pliki będą powodować wyszukiwanie wszystkich działań lub korzystanie z szerokiego zakresu dat.

3. Po zakończeniu procesu eksportowania w górnej części okna zostanie wyświetlony komunikat z monitem o otwarcie pliku CSV i zapisanie go na komputerze lokalnym. Dostęp do pliku CSV możesz również uzyskać w folderze Pobrane.

   > [!NOTE]
   > Z jednego przeszukiwania dziennika inspekcji do pliku CSV można pobrać maksymalnie 50 000 wpisów. Jeśli do pliku CSV zostanie pobranych 50 000 wpisów, można z pewnością założyć, że istnieje ponad 50 000 zdarzeń, które spełniają kryteria wyszukiwania. Aby wyeksportować dane powyżej tego limitu, spróbuj użyć węższego zakresu dat w celu zmniejszenia liczby rekordów dziennika inspekcji. W celu wyeksportowania ponad 50 000 wpisów może być konieczne uruchomienie wielu wyszukiwań z mniejszymi zakresami dat.

## <a name="step-2-format-the-exported-audit-log-using-the-power-query-editor"></a>Krok 2. Formatowanie wyeksportowanego dziennika inspekcji przy użyciu Edytora dodatku Power Query

Następnym krokiem jest podzielenie każdej właściwości obiektu JSON w kolumnie **Dane** inspekcji na własną kolumnę za pomocą funkcji przekształcania JSON w Edytorze dodatku Power Query w programie Excel. Następnie filtruje się kolumny, aby wyświetlić rekordy na podstawie wartości określonych właściwości. Może to ułatwić szybkie znalezienie określonych danych inspekcji, których szukasz.

1. Otwórz pusty skoroszyt w programie Excel dla Office 365, Excel 2019 lub Excel 2016.

2. Na karcie **Dane** w grupie Wstążki **& Przekształcanie** danych kliknij pozycję **Z tekstu/pliku CSV**.

    ![Na karcie Dane kliknij pozycję Z tekstu/pliku CSV.](../media/JSONTransformOpenCSVFile.png)

3. Otwórz plik CSV pobrany w kroku 1.

4. W wyświetlonym oknie kliknij pozycję **Przekształć dane**.

   ![Kliknij pozycję Przekształć dane.](../media/JSONOpenPowerQuery.png)

   Plik CSV zostanie otwarty w **Edytorze zapytań**. Istnieją cztery kolumny: **CreationDate**, **UserIds**, **Operations** i **AuditData**. Kolumna **Dane inspekcji** to obiekt JSON, który zawiera wiele właściwości. Następnym krokiem jest utworzenie kolumny dla każdej właściwości obiektu JSON.

5. Kliknij prawym przyciskiem myszy tytuł w kolumnie **Dane** inspekcji, **kliknij polecenie** Przekształć, a następnie kliknij polecenie **JSON**. 

   ![Kliknij prawym przyciskiem myszy kolumnę Dane inspekcji, kliknij polecenie Przekształć, a następnie wybierz pozycję JSON.](../media/JSONTransform.png)

6. W prawym górnym rogu kolumny **Dane** inspekcji kliknij ikonę rozwijania.

   ![W kolumnie Dane inspekcji kliknij ikonę rozwijania.](../media/JSONTransformExpandIcon.png)

   Zostanie wyświetlona częściowa lista właściwości w obiektach JSON w kolumnie **Dane** inspekcji.

7. Kliknij **pozycję Załaduj** więcej, aby wyświetlić wszystkie właściwości obiektów JSON w kolumnie **Dane** inspekcji.

   ![Kliknij pozycję Załaduj więcej, aby wyświetlić wszystkie właściwości obiektu JSON.](../media/JSONTransformLoadJSONProperties.png)

   Możesz usunąć zaznaczenie pola wyboru obok dowolnej właściwości, której nie chcesz uwzględniać. Wyeliminowanie kolumn, które nie są przydatne w trakcie prowadzonych badań, to dobry sposób na zmniejszenie ilości danych wyświetlanych w dzienniku inspekcji. 

   > [!NOTE]
   > Właściwości JSON wyświetlane na poprzednim zrzucie ekranu (po kliknięciu przycisku Załaduj **więcej) są** oparte na właściwościach znalezionych w kolumnie **Dane** inspekcji z pierwszych 1000 wierszy w pliku CSV. Jeśli po pierwszych 1000 wierszach istnieją inne właściwości JSON w rekordach, te właściwości (i odpowiadająca mu kolumna) nie zostaną uwzględnione, gdy kolumna **Dane** inspekcji zostanie podzielona na wiele kolumn. Aby temu zapobiec, rozważ ponowne uruchomienie wyszukiwania w dzienniku inspekcji i zawężenie kryteriów wyszukiwania, aby zwrócono mniej rekordów. Innym obejściem tego problemu jest filtrowanie elementów w kolumnie Operacje w celu zmniejszenia liczby wierszy (przed wykonaniem kroku 5 powyżej) przed przekształceniem obiektu JSON w kolumnie **Dane** inspekcji.

   > [!TIP]
   > Aby wyświetlić atrybut na liście, taki jak AuditData.AffectedItems, kliknij ikonę  Rozwiń w prawym górnym rogu kolumny, z której chcesz przeciągnąć atrybut, a następnie wybierz pozycję Rozwiń do nowego **wiersza.**  W tym miejscu będzie to rekord. Możesz kliknąć ikonę Rozwiń w prawym górnym rogu kolumny, wyświetlić atrybuty i wybrać ten, który chcesz wyświetlić lub wyodrębnić.

8. Wykonaj jedną z następujących czynności, aby sformatować tytuł kolumn dodawanych dla każdej wybranej właściwości JSON.

    - Usuń zaznaczenie pola **wyboru Użyj oryginalnej nazwy kolumny** jako prefiksu, aby użyć nazwy właściwości JSON jako nazw kolumn. na przykład **RecordType lub** **SourceFileName**.

    - Pozostaw **zaznaczone pole wyboru Użyj oryginalnej nazwy kolumny** jako prefiksu, aby dodać prefiks Dane inspekcji do nazw kolumn; na przykład **AuditData.RecordType lub** **AuditData.SourceFileName**.

9. Kliknij przycisk **OK**.

    Kolumna **Dane inspekcji** jest podzielona na wiele kolumn. Każda nowa kolumna odpowiada właściwości obiektu JSON Dane inspekcji. Każdy wiersz w kolumnie zawiera wartość właściwości. Jeśli właściwość nie zawiera wartości, zostanie *wyświetlona wartość null* . Na Excel komórki o wartościach null są puste.
  
10. Na karcie **Narzędzia** główne kliknij pozycję Zamknij i **& Załaduj**, aby zamknąć Edytor dodatku Power Query i otworzyć przekształcony plik CSV w skoroszycie Excel skoroszycie.

## <a name="use-powershell-to-search-and-export-audit-log-records"></a>Przeszukiwanie i eksportowanie rekordów dziennika inspekcji za pomocą programu PowerShell

Zamiast korzystać z narzędzia do przeszukiwania dziennika inspekcji w programie Centrum zgodności platformy Microsoft 365, można użyć polecenia cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) w programie Exchange Online PowerShell w celu wyeksportowania wyników przeszukiwania dziennika inspekcji do pliku CSV. Następnie możesz wykonać tę samą procedurę opisaną w kroku 2, aby sformatować dziennik inspekcji przy użyciu edytora dodatku Power Query. Jedną z zalet korzystania z polecenia cmdlet programu PowerShell jest możliwość wyszukiwania zdarzeń z określonej usługi za pomocą *parametru RecordType* . Oto kilka przykładów eksportowania rekordów inspekcji do pliku CSV za pomocą programu PowerShell w celu przekształcenia obiektu JSON w kolumnie **Dane** inspekcji za pomocą edytora dodatku Power Query, zgodnie z opisem w kroku 2.

W tym przykładzie uruchom następujące polecenia, aby zwrócić wszystkie rekordy związane SharePoint udostępnianiem.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointSharingOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

Wyniki wyszukiwania są eksportowane do pliku CSV o nazwie *PowerShellAuditlog* zawierającego cztery kolumny: CreationDate, UserIds, RecordType, AuditData).

Możesz również użyć nazwy lub wartości wyli dodanej dla typu rekordu jako wartości *parametru RecordType* . Aby uzyskać listę nazw typów rekordów i odpowiadających im wartości wyliszczenia, zobacz tabelę *AuditLogRecordType* w schemacie interfejsu API działań zarządzania Office 365 [zarządzaniem](/office/office-365-management-api/office-365-management-activity-api-schema#enum-auditlogrecordtype---type-edmint32).

Dla parametru *RecordType* można dołączyć tylko jedną wartość. Aby wyszukać rekordy inspekcji dla innych typów rekordów, należy ponownie uruchomić dwa poprzednie polecenia w celu określenia innego typu rekordu i dołączyć te wyniki do oryginalnego pliku CSV. Na przykład można uruchomić dwa poniższe polecenia, aby dodać działania związane z SharePoint pliku z tego samego zakresu dat do PowerShellAuditlog.csv pliku.

```powershell
$auditlog = Search-UnifiedAuditLog -StartDate 06/01/2019 -EndDate 06/30/2019 -RecordType SharePointFileOperation
```

```powershell
$auditlog | Select-Object -Property CreationDate,UserIds,RecordType,AuditData | Export-Csv -Append -Path c:\AuditLogs\PowerShellAuditlog.csv -NoTypeInformation
```

## <a name="tips-for-exporting-and-viewing-the-audit-log"></a>Wskazówki eksportowania i wyświetlania dziennika inspekcji

Poniżej przedstawiono kilka porad i przykładów eksportowania i wyświetlania dziennika inspekcji przed użyciem funkcji przekształcania JSON i po jego użyciu w celu podzielenia kolumny **Dane** inspekcji na wiele kolumn.

- **Przefiltruj kolumnę RecordType (Typ** Rekordu), aby wyświetlić tylko rekordy z określonej usługi lub obszaru funkcjonalności. Aby na przykład pokazać zdarzenia związane z udostępnianiem SharePoint, należy wybrać **wartość 14** (wartość wyli roku dla rekordów wyzwalanych przez SharePoint udostępniania). Aby uzyskać listę usług odpowiadających wartościom wyliczem wyświetlanym w kolumnie **RecordType (Typ** Rekordu), zobacz [Szczegółowe właściwości w dzienniku inspekcji](detailed-properties-in-the-office-365-audit-log.md).

- Filtrowanie **kolumny Operacje** w celu wyświetlenia rekordów dla określonych działań. Aby uzyskać listę operacji, które odpowiadają działaniu z przeszukiwalnym działaniem w narzędziu do przeszukiwania dziennika inspekcji w programie Centrum zgodności platformy Microsoft 365, zobacz sekcję "Działania inspekcji" w sekcji Przeszukiwanie dziennika [inspekcji](search-the-audit-log-in-security-and-compliance.md#audited-activities).
