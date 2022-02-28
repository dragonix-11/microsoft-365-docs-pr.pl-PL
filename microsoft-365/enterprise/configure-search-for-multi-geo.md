---
title: Konfigurowanie wyszukiwania Microsoft 365 wielowymiarowych
ms.reviewer: adwood
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-mar2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Dowiedz się, jak skonfigurować wyszukiwanie w środowisku wielolokalowym. Tylko niektórzy klienci, na przykład OneDrive, mogą zwracać wyniki w środowisku wielolokalowym.
ms.openlocfilehash: d6d6895c6dc393bb1f28dff60dea996bf80aad5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988047"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>Konfigurowanie funkcji wyszukiwania Microsoft 365 wielolokalizacji

W środowisku wielowymiarowym każda lokalizacja geograficzna ma własny indeks wyszukiwania i Centrum wyszukiwania. Podczas wyszukiwania przez użytkownika zapytanie jest zwracane na wszystkie indeksy, a zwracane wyniki są scalane.

Na przykład użytkownik w jednej lokalizacji geograficznej może wyszukiwać zawartość przechowywaną w innej lokalizacji geograficznej lub zawartość w witrynie usługi SharePoint, która jest ograniczona do innej lokalizacji geograficznej. Jeśli użytkownik ma dostęp do tej zawartości, wyszukiwanie będzie wyświetlać wynik.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Którzy klienci wyszukiwania pracują w środowisku z wieloma lokalizacjami geograficznymi?

Ci klienci mogą zwracać wyniki ze wszystkich lokalizacji geograficznych:

- OneDrive
- Delve
- Strona SharePoint głównej
- Centrum wyszukiwania
- Niestandardowe aplikacje wyszukiwania, które korzystają z SharePoint API wyszukiwania

### <a name="onedrive"></a>OneDrive

Po skonfigurowaniu środowiska wielowymiarowego użytkownicy wyszuk korzystający z OneDrive mogą uzyskać wyniki ze wszystkich lokalizacji geograficznych.

### <a name="delve"></a>Delve

Zaraz po skonfigurowaniu środowiska wielowymiarowego użytkownicy wyszuk korzystający z Delve otrzymają wyniki ze wszystkich lokalizacji geograficznych.

W Delve kanału informacyjnego i na karcie profilu są wyświetlane tylko podglądy plików przechowywanych w lokalizacji centralnej. W przypadku plików przechowywanych w lokalizacjach satelitarnych zamiast nich jest wyświetlana ikona typu pliku.

### <a name="the-sharepoint-home-page"></a>Strona SharePoint głównej

Po skonfigurowaniu środowiska wielolokalowego użytkownicy zobaczą na swojej stronie głównej wiadomości, ostatnio obserwowane i obserwowane witryny z SharePoint lokalizacji geograficznych. Jeśli użytkownik użyje pola wyszukiwania na SharePoint głównej, otrzyma scalone wyniki z wielu lokalizacji geograficznych.

### <a name="the-search-center"></a>Centrum wyszukiwania

Po skonfigurowaniu środowiska wielowymiarowego każde Centrum wyszukiwania nadal wyświetla wyniki tylko z ich lokalizacji geograficznej. Administratorzy muszą [zmienić ustawienia poszczególnych Centrum wyszukiwania](#_Set_up_a_1) , aby uzyskać wyniki ze wszystkich lokalizacji geograficznych. Później użytkownicy, którzy wyszukają w Centrum wyszukiwania, otrzymają wyniki ze wszystkich lokalizacji geograficznych.

### <a name="custom-search-applications"></a>Niestandardowe aplikacje wyszukiwania

W normalny sposób niestandardowe aplikacje wyszukiwania współdziałają z indeksami wyszukiwania przy użyciu istniejących SharePoint interfejsów API usługi REST wyszukiwania. Aby uzyskać wyniki ze wszystkich lub niektórych lokalizacji geograficznych, aplikacja musi wywołać interfejs [API](#_Get_custom_search) i uwzględnić w żądaniu nowe parametry zapytania wielowymiarowego. W ten sposób wyzwoli wentylatora z zapytania do wszystkich lokalizacji geograficznych.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Czym się różni wyszukiwanie w środowisku wielolokalowym?

Niektóre funkcje wyszukiwania, które możesz znać, działają inaczej w środowisku wielolokalowym.

<table>
<thead>
<tr class="header">
<th align="left">Funkcja</th>
<th align="left">Jak to działa</th>
<th align="left">Obejście problemu</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Promowane wyniki</td>
<td align="left">Można tworzyć reguły zapytań o promowanych wynikach na różnych poziomach: dla całej dzierżawy, dla zbioru witryn lub dla witryny. W środowisku z wieloma lokalizacjami geograficznymi zdefiniuj promowane wyniki na poziomie dzierżawy, aby promować wyniki do centrów wyszukiwania we wszystkich lokalizacjach geograficznych. Jeśli chcesz promować wyniki tylko w Centrum wyszukiwania, które znajduje się w lokalizacji geograficznej zbioru witryn lub witryny, zdefiniuj promowane wyniki na poziomie zbioru witryn lub witryny. Te wyniki nie są promowane w innych lokalizacjach geograficznych.</td>
<td align="left">Jeśli nie potrzebujesz różnych promowanych wyników dla lokalizacji geograficznej, na przykład różnych reguł dotyczących podróży, zalecamy zdefiniowanie promowanych wyników na poziomie dzierżawy.</td>
</tr>
<tr class="even">
<td align="left">Uściślij wyszukiwanie</td>
<td align="left">Wyszukiwanie zwraca funkcje uściślinia ze wszystkich lokalizacji geograficznych dzierżawy, a następnie agreguje je. Agregacja to najlepszy nakład pracy, co oznacza, że zliczanie przez uściślicie może nie być w 100% dokładne. W większości scenariuszy sterowanych wyszukiwaniem ta dokładność jest wystarczająca. 
</td>
<td align="left">W przypadku aplikacji sterowanych wyszukiwaniem, które zależą od kompletności uściślij, wykonaj zapytanie dotyczące każdej lokalizacji geograficznej niezależnie.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Wyszukiwanie wielowymiarowe nie obsługuje dynamicznego zasobników dla funkcji uściśłek liczbowych.</td>
<td align="left">Użyj <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">parametru "Dyskretyzuj" dla funkcji uściślijących</a> wartości liczbowe.</td>
</tr>
<tr class="even">
<td align="left">Identyfikatory dokumentów</td>
<td align="left">Jeśli opracowujesz aplikację sterowane wyszukiwaniem zależną od identyfikatorów dokumentów, pamiętaj, że identyfikatory dokumentów w środowisku wielolokalowym nie są unikatowe w różnych lokalizacjach geograficznych, są unikatowe dla poszczególnych lokalizacji geograficznych.</td>
<td align="left">Dodaliśmy kolumnę identyfikującą lokalizację geograficzną. Ta kolumna pozwala osiągnąć unikatowość. Ta kolumna nosi nazwę "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Liczba wyników</td>
<td align="left">Strona wyników wyszukiwania zawiera połączone wyniki z lokalizacji geograficznych, ale nie można wyświetlać ponad 500 wyników.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Wyszukiwanie hybrydowe</td>
<td align="left">W środowisku hybrydowym SharePoint hybrydowym z wyszukiwaniem hybrydowym w <a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">chmurze zawartość</a> lokalna jest dodawana Microsoft 365 indeksu lokalizacji centralnej.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Co nie jest obsługiwane w przypadku wyszukiwania w środowisku wielolokalowym?

Niektóre funkcje wyszukiwania, które możesz znać, nie są obsługiwane w środowisku wielolokalowym.

<table>
<thead>
<tr class="header">
<th align="left">Funkcja wyszukiwania</th>
<th align="left">Uwaga</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Uwierzytelnianie oparte tylko na aplikacji</td>
<td align="left">Uwierzytelnianie tylko przez aplikację (dostęp z usług) nie jest obsługiwane w wyszukiwanie w wielu lokalizacjach geograficznych.</td>
</tr>
<tr class="even">
<td align="left">Goście</td>
<td align="left">Goście otrzymują wyniki tylko z lokalizacji geograficznej, z której wyszukują.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Jak działa wyszukiwanie w środowisku wielolokalowym?

Wszyscy klienci wyszukiwania używają istniejących interfejsów API SharePoint REST do interakcji z indeksami wyszukiwania.

![Diagram przedstawiający sposób SharePoint interfejsów API rest wyszukiwania na indeksach wyszukiwania.](../media/configure-search-for-multi-geo-image1-1.png)

1. Klient wyszukiwania wywołuje punkt końcowy usługi REST wyszukiwania za pomocą właściwości zapytania EnableMultiGeoSearch= true.
2. Zapytanie jest wysyłane do wszystkich lokalizacji geograficznych w dzierżawie.
3. Wyniki wyszukiwania z poszczególnych lokalizacji geograficznych są scalane i klasyfikowane.
4. Klient otrzymuje ujednolicone wyniki wyszukiwania.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Zwróć uwagę, że nie scalamy wyników wyszukiwania, dopóki nie otrzymamy wyników ze wszystkich lokalizacji geograficznych. Oznacza to, że wyszukiwania wielowymiarowe mają dodatkowe opóźnienia w porównaniu z wyszukiwaniami w środowisku z tylko jedną lokalizacją geograficzną.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Uzyskiwanie Centrum wyszukiwania w celu pokazania wyników ze wszystkich lokalizacji geograficznych

Każde Centrum wyszukiwania ma kilka pionowych poziomych poziomych i każdą z nich należy skonfigurować osobno.

1. Upewnij się, że te czynności wykonujesz przy użyciu konta, które ma uprawnienia do edytowania strony wyników wyszukiwania i składników Web Part wyników wyszukiwania.

2. Przejdź do strony wyników wyszukiwania (zobacz [listę](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) stron wyników wyszukiwania)

3. Wybierz pozycję pionową do skonfigurowania, **kliknij Ustawienia koła** zębatego w prawym górnym rogu, a następnie kliknij pozycję **Edytuj stronę**. Strona wyników wyszukiwania zostanie otwarta w trybie edycji.

   ![Edytowanie zaznaczenia strony w Ustawienia.](../media/configure-search-for-multi-geo-image2.png)

4. W obszarze Web Part wyników wyszukiwania przenieś wskaźnik do prawego górnego rogu tego składników, kliknij strzałkę, a następnie w menu kliknij polecenie Edytuj składników **Web Part** . Pod wstążką w prawym górnym rogu strony zostanie otwarte okienko narzędzi składników Web Part wyników wyszukiwania.

   ![Edytowanie zaznaczenia składników Web Part.](../media/configure-search-for-multi-geo-image3.png)

5. W okienku narzędzi składników Web Part w sekcji **Ustawienia** w obszarze Ustawienia kontrolki wyników wybierz pozycję Pokaż wyniki dla  wielu lokalizacji geograficznych **, aby** uzyskać web Part wyników wyszukiwania w celu pokazania wyników ze wszystkich lokalizacji geograficznych.

6. Kliknij **przycisk OK** , aby zapisać zmianę i zamknąć okienko narzędzi składników Web Part.

7. Sprawdź wprowadzone zmiany w składnikiu Web Part wyników wyszukiwania, klikając pozycję Zaewidencjulator **na karcie** Strona w menu głównym.

8. Opublikuj zmiany za pomocą linku podanego w notacie u góry strony.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Uzyskiwanie niestandardowych aplikacji wyszukiwania w celu pokazania wyników ze wszystkich lub niektórych lokalizacji geograficznych

Niestandardowe aplikacje wyszukiwania uzyskają wyniki ze wszystkich lub niektórych lokalizacji geograficznych, określając parametry zapytania wraz z żądaniem do SharePoint interfejsu API REST wyszukiwania. W zależności od parametrów zapytania zapytanie jest fanned out to all geo locations, or to some geo locations. Jeśli na przykład chcesz utworzyć zapytanie tylko dla podzestawu lokalizacji geograficznych w celu znalezienia odpowiednich informacji, możesz kontrolować tylko te zasady dla użytkownika. Jeśli żądanie zakończy się powodzeniem, interfejs API SharePoint REST zwraca dane odpowiedzi.

### <a name="requirement"></a>Wymaganie

Dla każdej lokalizacji geograficznej należy się upewnić, że wszystkim użytkownikom w organizacji przyznano poziom uprawnień Odczyt  dla głównej witryny sieci Web (na przykład **contosoAPAC.sharepoint.com/** i **contosoEU.sharepoint.com/**). [Informacje o uprawnieniach](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>Parametry kwerendy

EnableMultiGeoSearch — wartość logiczna określająca, czy kwerenda ma zostać podpięta do indeksów innych lokalizacji geograficznych dzierżawy wielowymiarowej. Ustaw wartość **True (Prawda),** aby wychylić zapytanie; **false** , aby nie wychwytować zapytania. Jeśli nie uwzględnisz tego parametru, wartość domyślna ma wartość **fałszywą, z** wyjątkiem sytuacji, gdy w wywołaniu interfejsu API REST dla witryny korzystającej z szablonu Centrum wyszukiwania usługi Enterprise w tym przypadku wartość domyślna **jest prawdziwa**. Jeśli używasz parametru w środowisku, które nie korzysta z wielu lokalizacji geograficznych, parametr jest ignorowany.

ClientType (Typ Klienta) — jest to ciąg. Wprowadź unikatową nazwę klienta dla każdej aplikacji wyszukiwania. Jeśli nie uwzględnisz tego parametru, zapytanie nie zostanie przechyłowane do innych lokalizacji geograficznych.

MultiGeoSearchConfiguration — opcjonalna lista lokalizacji geograficznych w dzierżawie wielowymiarowej, która umożliwia wyszukiwanie zapytania w przypadku, gdy wartość **EnableMultiGeoSearch** jest **prawdziwa**. Jeśli nie uwzględnisz tego parametru lub pozostawisz to pole puste, zapytanie zostanie fanowane we wszystkich lokalizacjach geograficznych. Dla każdej lokalizacji geograficznej wprowadź następujące elementy w formacie JSON:

<table>
<thead>
<tr class="header">
<th align="left">Element</th>
<th align="left">Opis</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">Lokalizacja geograficzna, na przykład NAM.</td>
</tr>
<tr class="even">
<td align="left">EndPoint</td>
<td align="left">Punkt końcowy, z który ma nawiązać połączenie, na przykład https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">Identyfikator GUID źródła wyników, na przykład B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Pominięcie lokalizacji danych lub punktu końcowego lub zduplikowanie lokalizacji danych kończy się niepowodzeniem. [Informacje o punkcie końcowym lokalizacji geograficznych](/sharepoint/dev/solution-guidance/multigeo-discovery) dzierżawcy można uzyskać, używając usługi Microsoft Graph.

### <a name="response-data"></a>Dane odpowiedzi

MultiGeoSearchStatus — jest to właściwość zwracana przez SharePoint API wyszukiwania w odpowiedzi na żądanie. Wartość właściwości jest ciągiem i zawiera następujące informacje o wynikach zwracanych przez SharePoint API wyszukiwania:

<table>
<thead>
<tr class="header">
<th align="left">Value</th>
<th align="left">Opis</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Pełne</td>
<td align="left">Pełne wyniki ze <strong>wszystkich</strong> lokalizacji geograficznych.</td>
</tr>
<tr class="even">
<td align="left">Częściowe</td>
<td align="left">Częściowe wyniki z co najmniej jednej lokalizacji geograficznej. Wyniki są niepełne ze względu na błąd przejściowy.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Kwerenda przy użyciu usługi REST

Żądanie GET umożliwia określenie parametrów zapytania w adresie URL. W przypadku żądania POST parametry zapytania są przekaże się w treści w formacie JSON (JavaScript Object Notation).

#### <a name="request-headers"></a>Żądaj nagłówków

<table>
<thead>
<tr class="header">
<th align="left">Name (Nazwa)</th>
<th align="left">Value (Wartość)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Typ zawartości</td>
<td align="left">application/json;odata=verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Przykładowe żądanie GET, które zostało zdjęte do **wszystkich** lokalizacji geograficznych

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Przykładowa prośba GET o zachęt do **pewnych** lokalizacji geograficznych

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> Przecinki i dwukropki na liście lokalizacji geograficznych właściwości MultiGeoSearchConfiguration są poprzedzone znakiem **ukośnika** odwrotnego. Jest tak, ponieważ żądania GET oddzielają właściwości średnikami i właściwości przy użyciu dwukropków. Bez ukośnika odwrotnego jako znaku ucieczki właściwość MultiGeoSearchConfiguration jest interpretowana błędnie.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Przykładowe żądanie post, które zostało przechowane do **wszystkich** lokalizacji geograficznych

```http
    {
    "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }
```

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Przykładowe żądanie post, które zostało przechowane w **niektórych** lokalizacjach geograficznych

```http
    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }
```

### <a name="query-using-csom"></a>Kwerenda korzystająca z csom

Oto przykładowe zapytanie CSOM, które zostało przepięte na **wszystkie lokalizacje** geograficzne:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
