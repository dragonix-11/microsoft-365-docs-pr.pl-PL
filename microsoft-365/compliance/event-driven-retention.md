---
title: Rozpoczynanie przechowywania w przypadku wystąpienia zdarzenia
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-may2020
- seo-marvel-jun2020
description: Zazwyczaj jest to część rozwiązania do zarządzania rekordami, które pozwala skonfigurować etykietę przechowywania w celu rozpoczęcia okresu przechowywania na podstawie identyfikowanego zdarzenia.
ms.openlocfilehash: ad5fb2ef567525fa021acb0388ebc5cc98b1148c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313303"
---
# <a name="start-retention-when-an-event-occurs"></a>Rozpoczynanie przechowywania w przypadku wystąpienia zdarzenia

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Okres przechowywania zawartości często zależy od wieku jej zawartości. Na przykład możesz przechowywać dokumenty przez siedem lat od ich utworzenia, a następnie je usuwać. Jednak podczas konfigurowania [etykiet przechowywania](retention.md#retention-labels) można również określić okres przechowywania na podstawie wystąpienia określonego typu zdarzenia. Zdarzenie wyzwala początek okresu przechowywania, a cała zawartość z etykietą przechowywania zastosowaną do tego typu zdarzenia wymusza na nich akcje przechowywania etykiety.
  
Przykłady korzystania z przechowywania opartego na zdarzeniach:
  
- **Pracownicy odchodzą z organizacji** Załóżmy, że rekordy pracowników muszą być przechowywane przez 10 lat od chwili odejm przez pracownika od organizacji. Po upływie 10 lat wszystkie dokumenty związane z zatrudnieniem, wynikami i rozwiązaniem tego pracownika muszą zostać usunięte. Zdarzeniem wyzwalanym przez 10-letni okres przechowywania jest opuszczenie organizacji przez pracownika. 
    
- **Wygasanie umowy** Załóżmy, że wszystkie rekordy związane z umowami muszą być przechowywane przez pięć lat od czasu wygaśnięcia umowy. Zdarzenie, które powoduje wyzwolenie 5-letniego okresu przechowywania, oznacza wygaśnięcie umowy. 
    
- **Okres ważności produktu** Twoja organizacja może mieć wymagania przechowywania związane z ostatnią datą produkcji produktów w odniesieniu do zawartości, takiej jak specyfikacje techniczne. W tym przypadku ostatnią datą produkcji jest zdarzenie wyzwalanie okresu przechowywania. 
    
Przechowywanie oparte na zdarzeniach jest zwykle używane w ramach procesu zarządzania rekordami. Oznacza to, że:
  
- Etykiety przechowywania oparte na zdarzeniach zazwyczaj również oznaczają elementy jako rekordy w ramach rozwiązania do zarządzania rekordami. Aby uzyskać więcej informacji, zobacz [Informacje na temat zarządzania rekordami](records-management.md).

- Dokument, który został zadeklarowany jako rekord, ale którego wyzwalacz zdarzenia jeszcze się nie wydarzył, jest zachowywany przez czas nieograniczony (nie można trwale usuwać rekordów) do momentu wyzwolenia okresu przechowywania tego dokumentu.
    
- Etykiety przechowywania na podstawie zdarzeń zwykle powodują przegląd usuwania po zakończeniu okresu przechowywania, tak aby menedżer rekordów może ręcznie przeglądać i usuwać zawartość. Aby uzyskać więcej informacji, zobacz [Ich zawartość](disposition.md).
    

Etykieta przechowywania oparta na zdarzeniu ma te same możliwości, co każda etykieta przechowywania w Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>Opis relacji między typami zdarzeń, etykietami, zdarzeniami i identyfikatorami elementów zawartości

Aby pomyślnie używać przechowywania opartego na zdarzeniach, należy zrozumieć relację między typami zdarzeń, etykietami przechowywania, zdarzeniami i identyfikatorami elementów zawartości, jak pokazano na diagramach, oraz następujące wyjaśnienie: 
  
![Diagram 1 z 2: Typ zdarzenia, etykiety, zdarzenia i identyfikatory elementów zawartości.](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![Diagram 2 z 2: Typ zdarzenia, etykiety, zdarzenia i identyfikatory elementów zawartości.](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. Etykiety przechowywania można tworzyć dla różnych typów zawartości, a następnie skojarzyć je z typem zdarzenia. Na przykład etykiety przechowywania dla różnych typów plików i rekordów produktów są skojarzone z typem zdarzenia o nazwie Okres istnienia produktu, ponieważ te rekordy muszą być przechowywane przez 10 lat od czasu zakończenia użytkowania produktu.
    
2. Użytkownicy (zazwyczaj menedżerowie rekordów) stosują te etykiety przechowywania do zawartości i (w przypadku dokumentów w aplikacjach SharePoint i OneDrive) wprowadzić identyfikator składnika majątku dla każdego elementu. W tym przykładzie identyfikator środka trwałego to nazwa produktu lub kod używany przez organizację. Następnie do rekordów każdego produktu jest przypisywana etykieta przechowywania, a do każdego rekordu jest przypisana właściwość zawierająca identyfikator składnika majątku. Diagram przedstawia **całą zawartość wszystkich** rekordów produktów w organizacji, a każdy element zawiera identyfikator środka trwałego produktu, którego rekord się znajduje. 
    
3. Okres istnienia produktu jest typem zdarzenia. Określony produkt, dla których kończy się okres użytkowania, to wydarzenie. Gdy wystąpi zdarzenie tego typu — w tym przypadku, gdy produkt dotrze do końca użytkowania — tworzy się zdarzenie, które określa:
    
   - Identyfikator środka trwałego (na SharePoint i OneDrive dokumentów)
    
   - Słowa kluczowe (dla Exchange elementów). W tym przykładzie organizacja używa kodu produktu w wiadomościach zawierających rekordy produktów, więc słowo kluczowe dla elementów Exchange działa tak samo, jak identyfikator SharePoint i OneDrive dokumentów.
    
   - Data wystąpienia zdarzenia. Ta data jest używana jako początek okresu przechowywania. Może to być data bieżąca, przeszła lub przyszła.

4. Po utworzeniu zdarzenia ta data zdarzenia zostanie zsynchronizowana ze wszystkimi elementami zawartości, dla których jest oznaczona etykieta przechowywania tego typu i która zawiera określony identyfikator zasobu lub słowo kluczowe. Ta synchronizacja, podobnie jak każda etykieta przechowywania, może potrwać do siedmiu dni. Na poprzednim diagramie wszystkie elementy zakreślone na czerwono mają okres przechowywania wyzwolony przez to zdarzenie. Innymi słowy, po zakończeniu użytkowania tego produktu to zdarzenie powoduje wyzwolenie okresu przechowywania rekordów tego produktu.

Ważne jest, aby zrozumieć, że jeśli nie określisz identyfikatora zasobu lub słów kluczowych dla **zdarzenia, dla** całej zawartości z etykietą przechowywania tego typu zdarzenia zostanie wyzwolony okres przechowywania. Oznacza to, że na poprzednim diagramie cała zawartość zacznie być zachowywana. To może być nie to, co zamierzasz.

Na koniec należy pamiętać, że każda etykieta przechowywania ma własne ustawienia przechowywania. W tym przykładzie wszystkie określają 10 lat, ale zdarzenie może wyzwalać etykiety przechowywania, gdy każda etykieta ma inny okres przechowywania.
  
## <a name="how-to-set-up-event-driven-retention"></a>Jak skonfigurować przechowywanie oparte na zdarzeniach

Przepływ pracy wysokiego poziomu do przechowywania opartego na zdarzeniach:
  
![Diagram przepływu pracy do konfigurowania przechowywania opartego na zdarzeniach.](../media/event-based-retention-process.png)
  
> [!TIP]
> Zobacz [Zarządzanie cyklem](auto-apply-retention-labels-scenario.md) życia dokumentów przechowywanych w programie SharePoint za pomocą etykiet przechowywania, aby uzyskać szczegółowy scenariusz użycia właściwości zarządzanych w programie SharePoint w celu automatycznego stosowania etykiet przechowywania i implementowania przechowywania sterowanego zdarzeniami.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>Krok 1. Tworzenie etykiety, której okres przechowywania jest oparty na zdarzeniu

Aby utworzyć i skonfigurować etykietę przechowywania, zobacz instrukcje Tworzenie etykiet [](file-plan-manager.md#create-retention-labels) przechowywania do zarządzania rekordami lub Jak tworzyć etykiety przechowywania [na temat zarządzania informacjami](create-retention-labels-information-governance.md). Jednak specyficzne dla przechowywania opartego na zdarzeniach,  na stronie Definiowanie ustawień przechowywania podczas tworzenia etykiety przechowywania po Rozpoczęciu okresu przechowywania na podstawie wybierz jeden z domyślnych typów zdarzeń z listy rozwijanej lub utwórz własne, wybierając pozycję Utwórz nowy typ **zdarzenia:**

![Utwórz nowy typ zdarzenia dla etykiety przechowywania.](../media/SPRetention6.png)

Typ zdarzenia jest po prostu ogólnym opisem zdarzenia, które chcesz skojarzyć z etykietą przechowywania.

Na liście rozwijanej domyślne typy zdarzeń są zawierały (typ zdarzenia **)** po nazwie w celu ułatwienia identyfikacji,  >  a typ zdarzenia można również wyświetlić i utworzyć na karcie Zarządzanie zdarzeniami rekordów > **Zarządzanie** typami zdarzeń.

Przechowywanie oparte na zdarzeniach wymaga ustawień przechowywania, które:
  
- Zachowywanie zawartości.
    
- Zawartość należy usuwać automatycznie lub wyzwalać recenzję usuwania po zakończeniu okresu przechowywania.
  
Przechowywanie oparte na zdarzeniach jest zwykle używane dla zawartości deklarowanej jako rekord, więc jest to dobry czas na sprawdzenie, czy należy również zaznaczyć opcję oznaczania zawartości jako [rekordu](records-management.md#records).

Jeśli zamiast tworzenia nowego typu zdarzenia używasz istniejącego typu zdarzenia, przejdź do kroku 3.

> [!NOTE]
> Po wybraniu typu zdarzenia i zapisaniu etykiety przechowywania nie można go zmienić.

### <a name="step-2-create-a-new-event-type-for-your-label"></a>Krok 2. Tworzenie nowego typu zdarzenia dla etykiety

W ustawieniach przechowywania, jeśli wybrano **pozycję Utwórz nowy typ zdarzenia**, wprowadź nazwę i opis typu zdarzenia. Następnie wybierz **pozycję Dalej**, **Prześlij** i **Gotowe**.

Na stronie **Definiowanie ustawień przechowywania** w celu rozpoczęcia okresu przechowywania na podstawie wybierz utworzony typ zdarzenia z listy rozwijanej.

  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>Krok 3. Publikowanie lub automatyczne stosowanie etykiet przechowywania opartych na zdarzeniach

Aby etykieta była ręcznie lub automatycznie stosowana do zawartości, podobnie jak każda etykieta przechowywania, trzeba opublikować lub automatycznie zastosować etykietę opartą na zdarzeniach:
- [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)

### <a name="step-4-enter-an-asset-id"></a>Krok 4. Wprowadzanie identyfikatora środka trwałego

Po zastosowaniu etykiety opartej na zdarzeniu do zawartości możesz wprowadzić identyfikator zasobu dla każdego elementu. Na przykład organizacja może używać:
  
- Kody produktów, za pomocą których można zachować zawartość tylko dla określonego produktu.
    
- Project, których można użyć do przechowywania zawartości tylko dla określonego projektu.
    
- Identyfikatory pracowników, za pomocą których można przechowywać zawartość tylko określonej osoby.
    
Identyfikator zasobu to po prostu inna właściwość dokumentu, która jest dostępna w SharePoint i OneDrive. Twoja organizacja może już klasyfikować zawartość za pomocą innych właściwości dokumentów i identyfikatorów. Jeśli tak, możesz również użyć tych właściwości i wartości podczas tworzenia zdarzenia — zobacz krok 6 poniżej. Ważne jest, aby skojarzyć ten element z typem zdarzenia za pomocą kombinacji właściwość *:* wartość we właściwościach dokumentu.
  
![Pole tekstowe służące do wprowadzania identyfikatora zasobu.](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>Krok 5. Tworzenie zdarzenia

Gdy wystąpi konkretne wystąpienie tego typu zdarzenia, na przykład produkt zostanie wycofaniem z użytkowania, przejdź do strony **Zarządzanie** >  rekordami Zdarzenia w Centrum zgodności platformy Microsoft 365 i wybierz pozycję **+** Utwórz, aby utworzyć zdarzenie. Tutaj zdarzenie jest wyzwalane przez jego utworzenie.

![Utwórz zdarzenie, aby wyzwalać rozpoczęcie przechowywania dla etykiet przechowywania opartych na zdarzeniach.](../media/create-event-records-management.png)

W jednej dzierżawie jest obsługiwanych do miliona zdarzeń.

### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>Krok 6. Wybieranie typu zdarzenia używanego na etykiecie w kroku 2

Podczas tworzenia zdarzenia wybierz ten sam typ zdarzenia określony w ustawieniach etykiet przechowywania w kroku 2. Jeśli na przykład jako typ zdarzenia  dla ustawień etykiet wybrano element Okres istnienia produktu, podczas tworzenia  zdarzenia wybierz pozycję Okres istnienia produktu. Tylko zawartość z zastosowanymi etykietami przechowywania dla tego typu zdarzenia będzie wyzwalana.

![Opcja w ustawieniach zdarzenia umożliwia wybranie typu zdarzenia.](../media/choose-event-type-records-management.png)

Ewentualnie, jeśli chcesz utworzyć zdarzenie dla wielu etykiet przechowywania, które mają różne typy zdarzeń, wybierz opcję **Wybierz istniejące etykiety** . Następnie wybierz etykiety skonfigurowane dla typów zdarzeń, które chcesz skojarzyć z tym zdarzeniem.

### <a name="step-7-enter-keywords-or-query-for-exchange-asset-id-for-sharepoint-and-onedrive"></a>Krok 7. Wprowadzanie słów kluczowych lub zapytania Exchange, identyfikatora zasobu dla SharePoint i OneDrive

Teraz zawęzisz zakres zawartości. W Exchange zawartości można to zrobić przez określenie słów kluczowych lub zapytania. W SharePoint zawartości OneDrive zawartości można to zrobić, określając identyfikatory środków trwałych.

Aby Exchange, użyj słów kluczowych lub zapytania, które używa języka Keyword Query Language (KQL). Aby uzyskać więcej informacji na temat składni zapytania, zobacz Informacje dotyczące składni w języku słowa kluczowego [(KQL](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)). Aby uzyskać więcej informacji na temat właściwości, których można używać na Exchange, zobacz Zapytania słów kluczowych i warunki wyszukiwania [dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md).

W przypadku identyfikatorów środków trwałych przechowywanie będzie wymuszane tylko na zawartości z określoną parą właściwość *:wartość* . Jeśli na przykład używasz właściwości Identyfikator zasobu, `ComplianceAssetID:<value>` wprowadź w polu identyfikatory środków trwałych przedstawione na poniższej ilustracji.

Jeśli nie zostanie wprowadzony identyfikator zasobu, to do całej zawartości z etykietami tego typu zdarzenia będzie stosowana ta sama data przechowywania.

Być może w Organizacji do dokumentów związanych z tym typem zdarzenia zostały zastosowane inne właściwości i identyfikatory. Jeśli na przykład trzeba wykryć rekordy określonego produktu, identyfikator może być połączeniem właściwości niestandardowej ProductID i wartości "XYZ". W takim przypadku należy wprowadzić `ProductID:XYZ` pole identyfikatorów środków trwałych pokazanych na poniższej ilustracji.

Na koniec wybierz datę wystąpienia zdarzenia. Data ta jest używana jako początek okresu przechowywania. Po utworzeniu zdarzenia ta data zdarzenia zostanie zsynchronizowana ze wszystkimi elementami zawartości z etykietą przechowywania tego typu zdarzenia, identyfikatorem zasobu oraz słowami kluczowymi lub kwerendami. Tak jak w przypadku każdej etykiety przechowywania, synchronizacja może potrwać do siedmiu dni.
  
![Strona ustawień zdarzenia.](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

Po utworzeniu zdarzenia ustawienia przechowywania są obowiązywać dla zawartości, która jest już oznaczona etykietą i zindeksowana. Jeśli etykieta przechowywania zostanie dodana do nowej zawartości po utworzeniu zdarzenia, musisz utworzyć nowe zdarzenie o takich samych szczegółach.

Usunięcie zdarzenia nie oznacza anulowania ustawień przechowywania, które są obecnie obowiązywały dla zawartości, która została już oznaczona etykietą. Obecnie po wyzwoleniu zdarzeń nie można ich anulować.

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>Wyszukiwanie zawartości w celu znalezienia całej zawartości z określoną etykietą lub identyfikatorem zasobu

Po przypisaniu etykiet przechowywania do zawartości możesz użyć funkcji wyszukiwania zawartości, aby znaleźć całą zawartość, która jest klasyfikowana przy użyciu określonej etykiety przechowywania lub zawiera określony identyfikator zasobu:
  
- Aby znaleźć całą zawartość z określoną etykietą przechowywania, wybierz warunek Etykieta przechowywania, a następnie wprowadź pełną nazwę etykiety lub jej część i użyj symbolu wieloznacznego. 
    
- Aby znaleźć całą zawartość o określonym identyfikatorze zasobu, wprowadź właściwość **ComplianceAssetID** i wartość, używając formatu `ComplianceAssetID:<value>`. 
    
Aby uzyskać więcej informacji, zobacz [Zapytania słów kluczowych i warunki wyszukiwania dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md).

## <a name="automate-events-by-using-powershell"></a>Automatyzowanie zdarzeń przy użyciu programu PowerShell

Za pomocą skryptu programu PowerShell możesz zautomatyzować przechowywanie oparte na zdarzeniach z aplikacji biznesowych. Polecenia cmdlet programu PowerShell dostępne na wypadek przechowywania na podstawie zdarzeń:
  
- [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype)
    
- [New-ComplianceRetentionEventType](/powershell/module/exchange/new-complianceretentioneventtype)
    
- [Remove-ComplianceRetentionEventType](/powershell/module/exchange/remove-complianceretentioneventtype)
    
- [Set-ComplianceRetentionEventType](/powershell/module/exchange/set-complianceretentioneventtype)
    
- [Get-ComplianceRetentionEvent](/powershell/module/exchange/get-complianceretentionevent)
    
- [New-ComplianceRetentionEvent](/powershell/module/exchange/new-complianceretentionevent)
    

## <a name="automate-events-by-using-a-rest-api"></a>Automatyzowanie zdarzeń przy użyciu interfejsu API usługi REST

Możesz użyć interfejsu API usługi REST, aby automatycznie utworzyć zdarzenia wyzwalane po rozpoczęciu czasu przechowywania.

Interfejs API usługi REST to punkt końcowy usługi obsługujący zestawy operacji HTTP (metod), które zapewniają dostęp do zasobów usługi (create/retrieve/update/delete). Aby uzyskać więcej informacji, [zobacz Składniki żądania/odpowiedzi interfejsu API REST](/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse). Za pomocą interfejsu API Microsoft 365 REST można tworzyć i pobierać zdarzenia przy użyciu metod POST i GET.

Istnieją dwie opcje korzystania z interfejsu API usługi REST:

- **Firma Microsoft Power Automate lub podobnej aplikacji** w celu automatycznego wyzwolenia wystąpienia zdarzenia. Microsoft Power Automate to system do łączenia się z innymi systemami, więc nie musisz pisać rozwiązania niestandardowego. Aby uzyskać więcej informacji, zobacz Power Automate [sieci Web](https://flow.microsoft.com/en-us/).

- **Program PowerShell lub klient HTTP do** wywołania interfejsu API REST w celu tworzenia zdarzeń przy użyciu programu PowerShell (w wersji 6 lub nowszej), który jest częścią rozwiązania niestandardowego.

Przed użyciem interfejsu API usługi REST jako administrator globalny potwierdź adres URL, który ma być używać do wywołania zdarzenia przechowywania. W tym celu uruchom wywołanie zdarzenia przechowywania GET przy użyciu adresu URL interfejsu API rest:

```http
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

Sprawdź kod odpowiedzi. Jeśli jest to wartość 302, uzyskaj przekierowany adres URL z właściwości Location nagłówka odpowiedzi i użyj tego adresu URL `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` zamiast w poniższych instrukcjach.

Zdarzenia tworzone automatycznie można potwierdzić, wyświetlając je w Centrum zgodności platformy Microsoft 365 > **Zarządzanie** >   **rekordami**.

### <a name="use-microsoft-power-automate-to-create-the-event"></a>Tworzenie zdarzenia Power Automate za pomocą aplikacji Microsoft Power Automate

Utwórz przepływ, który tworzy zdarzenie przy użyciu Microsoft 365 API REST:

![Tworzenie Flow przy użyciu aplikacji.](../media/automate-event-driven-retention-flow-1.png)

![Używanie przepływu do wywołania interfejsu API REST.](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>Tworzenie zdarzenia

Przykładowy kod wywołujący interfejs API REST:

- **Metoda**: POST
- **Adres URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Nagłówki**: Key = Content-Type, Value = application/atom+xml
- **Treść**:

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'?>
    
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'
    
    xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'
    
    xmlns='http://www.w3.org/2005/Atom'>
    
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />
    
    <updated>9/9/2017 10:50:00 PM</updated>
    
    <content type='application/xml'>
    
    <m:properties>
    
    <d:Name>Employee Termination </d:Name>
    
    <d:EventType>99e0ae64-a4b8-40bb-82ed-645895610f56</d:EventType>
    
    <d:SharePointAssetIdQuery>1234</d:SharePointAssetIdQuery>
    
    <d:EventDateTime>2018-12-01T00:00:00Z </d:EventDateTime>
    
    </m:properties>
    
    </content>
    
    </entry>
    ```

- **Uwierzytelnianie**: podstawowe
- **Nazwa użytkownika**: "Complianceuser"
- **Hasło**: "Compliancepassword"


##### <a name="available-parameters"></a>Dostępne parametry


|Parametry|Opis|Uwagi|
|--- |--- |--- |
|<d:Nazwa></d:Nazwa>|Nadaj wydarzeniu unikatową nazwę,|Nie może zawierać spacji na trailu ani następujących znaków: % * \ & < \> \| # ? , : ;|
|<d:EventType></d:EventType>|Wprowadź nazwę typu zdarzenia (lub wartość Guid),|Przykład: "Rozwiązanie umowy przez pracownika". Typ zdarzenia musi być skojarzony z etykietą przechowywania.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|Wprowadź "ComplianceAssetId:" + identyfikator pracownika|Przykład: "ComplianceAssetId:12345"|
|<d:EventDateTime></d:EventDateTime>|Data i godzina zdarzenia|Format: yyyy-MM-ddTHH:mm:ssZ, Przykład: 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>Kody odpowiedzi

| Kod odpowiedzi | Opis       |
| ----------------- | --------------------- |
| 302               | Przekierowywanie              |
| 201               | Utwórz               |
| 403               | Autoryzacja nie powiodła się  |
| 401               | Uwierzytelnienie nie powiodło się |

##### <a name="get-events-based-on-a-time-range"></a>Uzyskiwanie zdarzeń na podstawie zakresu czasu

- **Metoda**: GET

- **Adres URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **Nagłówki**: Key = Content-Type, Value = application/atom+xml

- **Uwierzytelnianie**: podstawowe

- **Nazwa użytkownika**: "Complianceuser"

- **Hasło**: "Compliancepassword"

###### <a name="response-codes"></a>Kody odpowiedzi

| Kod odpowiedzi | Opis                   |
| ----------------- | --------------------------------- |
| 200               | OK, lista zdarzeń w atom+ xml |
| 404               | Nie znaleziono                         |
| 302               | Przekierowywanie                          |
| 401               | Autoryzacja nie powiodła się              |
| 403               | Uwierzytelnienie nie powiodło się             |

##### <a name="get-an-event-by-id"></a>Uzyskiwanie zdarzenia według identyfikatora

- **Metoda**: GET

- **Adres URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **Nagłówki**: Key = Content-Type, Value = application/atom+xml

- **Uwierzytelnianie**: podstawowe

- **Nazwa użytkownika**: "Complianceuser"

- **Hasło**: "Compliancepassword"

###### <a name="response-codes"></a>Kody odpowiedzi

| Kod odpowiedzi | Opis                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, treść odpowiedzi zawiera zdarzenie w formacie atom+xml |
| 404               | Nie znaleziono                                            |
| 302               | Przekierowywanie                                             |
| 401               | Autoryzacja nie powiodła się                                 |
| 403               | Uwierzytelnienie nie powiodło się                                |

##### <a name="get-an-event-by-name"></a>Uzyskiwanie zdarzenia według nazwy

- **Metoda**: GET

- **Adres URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **Nagłówki**: Key = Content-Type, Value = application/atom+xml

- **Uwierzytelnianie**: podstawowe

- **Nazwa użytkownika**: "Complianceuser"

- **Hasło**: "Compliancepassword"

###### <a name="response-codes"></a>Kody odpowiedzi

| Kod odpowiedzi | Opis                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, treść odpowiedzi zawiera zdarzenie w formacie atom+xml |
| 404               | Nie znaleziono                                            |
| 302               | Przekierowywanie                                             |
| 401               | Autoryzacja nie powiodła się                                 |
| 403               | Uwierzytelnienie nie powiodło się                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>Tworzenie zdarzenia przy użyciu programu PowerShell lub dowolnego klienta HTTP

Program PowerShell musi być w wersji 6 lub nowszej.

W sesji programu PowerShell uruchom następujący skrypt:

```powershell
param([string]$baseUri)

$userName = "UserName"

$password = "Password"

$securePassword = ConvertTo-SecureString $password -AsPlainText -Force

$credentials = New-Object System.Management.Automation.PSCredential($userName, $securePassword)

$EventName="EventByRESTPost-$(([Guid]::NewGuid()).ToString('N'))"

Write-Host "Start to create an event with name: $EventName"

$body = "<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'

xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'

xmlns='http://www.w3.org/2005/Atom'>

<category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />

<updated>7/14/2017 2:03:36 PM</updated>

<content type='application/xml'>

<m:properties>

<d:Name>$EventName</d:Name>

<d:EventType>e823b782-9a07-4e30-8091-034fc01f9347</d:EventType>

<d:SharePointAssetIdQuery>'ComplianceAssetId:123'</d:SharePointAssetIdQuery>

</m:properties>

</content>

</entry>"

$event = $null

try

{

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri "$baseUri/ComplianceRetentionEvent" -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

catch

{

$response = $_.Exception.Response

if($response.StatusCode -eq "Redirect")

{

$url = $response.Headers.Location

Write-Host "redirected to $url"

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri $url -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

}

$event | fl *
```
