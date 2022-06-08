---
title: Opcje nawigacji dla usługi SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: W tym artykule opisano witryny opcji nawigacji z włączoną funkcją publikowania programu SharePoint w usłudze SharePoint Online.
ms.openlocfilehash: c95666a0fdb78fa584d9ca32ce19f10e4db89753
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940937"
---
# <a name="navigation-options-for-sharepoint-online"></a>Opcje nawigacji dla usługi SharePoint Online

W tym artykule opisano witryny opcji nawigacji z włączoną funkcją publikowania programu SharePoint w usłudze SharePoint Online. Wybór i konfiguracja nawigacji znacząco wpływa na wydajność i skalowalność witryn w usłudze SharePoint Online. Szablon witryny publikowania programu SharePoint powinien być używany tylko wtedy, gdy jest to wymagane dla scentralizowanego portalu, a funkcja publikowania powinna być włączona tylko w określonych witrynach i tylko wtedy, gdy jest to absolutnie wymagane, ponieważ może mieć wpływ na wydajność w przypadku nieprawidłowego użycia.

>[!NOTE]
>Jeśli używasz nowoczesnych opcji nawigacji programu SharePoint, takich jak mega menu, nawigacja kaskadowo lub nawigacja w centrum, ten artykuł nie ma zastosowania do witryny. Nowoczesne architektury witryn programu SharePoint korzystają z bardziej spłaszczanej hierarchii lokacji i modelu piasty i szprych. Dzięki temu można osiągnąć wiele scenariuszy, które NIE wymagają użycia funkcji publikowania programu SharePoint.

## <a name="overview-of-navigation-options"></a>Omówienie opcji nawigacji

Konfiguracja dostawcy nawigacji może znacząco wpłynąć na wydajność całej witryny i należy wziąć pod uwagę, aby wybrać dostawcę nawigacji i konfigurację, która jest efektywnie skalowana pod kątem wymagań witryny programu SharePoint. Istnieją dwaj dostawcy nawigacji na zewnątrz, a także niestandardowe implementacje nawigacji.

Pierwsza opcja, [**nawigacja strukturalna**](#using-structural-navigation-in-sharepoint-online), to zalecana opcja nawigacji w usłudze SharePoint Online dla klasycznych witryn programu SharePoint, **jeśli włączysz buforowanie nawigacji strukturalnej dla witryny**. Ten dostawca nawigacji wyświetla elementy nawigacji poniżej bieżącej witryny i opcjonalnie bieżącą witrynę i jej elementy równorzędne. Zapewnia dodatkowe możliwości, takie jak przycinanie zabezpieczeń i wyliczenie struktury lokacji. Jeśli buforowanie jest wyłączone, wpłynie to negatywnie na wydajność i skalowalność i może podlegać ograniczaniu przepustowości.

Druga opcja, [**nawigacja zarządzana (metadane),**](#using-managed-navigation-and-metadata-in-sharepoint-online) reprezentuje elementy nawigacji przy użyciu zestawu terminów zarządzanych metadanych. Zalecamy wyłączenie przycinania zabezpieczeń, chyba że jest to wymagane. Przycinanie zabezpieczeń jest włączone jako ustawienie bezpieczne domyślnie dla tego dostawcy nawigacji; Jednak wiele witryn nie wymaga narzutu związanego z przycinaniem zabezpieczeń, ponieważ elementy nawigacji są często spójne dla wszystkich użytkowników witryny. Dzięki zalecanej konfiguracji wyłączania przycinania zabezpieczeń ten dostawca nawigacji nie wymaga wyliczania struktury lokacji i jest wysoce skalowalny z akceptowalnym wpływem na wydajność.

Oprócz dostawców nawigacji out-of-the-box wielu klientów pomyślnie zaimplementowano alternatywne niestandardowe implementacje nawigacji. Zobacz [Skrypty po stronie klienta oparte na wyszukiwaniu](#using-search-driven-client-side-scripting) w tym artykule.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Zalety i wady opcji nawigacji usługi SharePoint Online

Poniższa tabela zawiera podsumowanie zalet i wad każdej opcji.

|Nawigacja strukturalna  |Nawigacja zarządzana  |Nawigacja oparta na wyszukiwaniu  |Dostawca nawigacji niestandardowej  |
|---------|---------|---------|---------|
|Plusy:<br/><br/>Łatwe w obsłudze<br/>Obcięte zabezpieczenia<br/>Automatycznie aktualizuje w ciągu 24 godzin po zmianie zawartości<br/>     |Plusy:<br/><br/>Łatwe w obsłudze<br/>|Plusy:<br/><br/>Obcięte zabezpieczenia<br/>Automatyczne aktualizowanie w miarę dodawania witryn<br/>Szybki czas ładowania i lokalnie buforowana struktura nawigacji<br/>|Plusy:<br/><br/>Szerszy wybór dostępnych opcji<br/>Szybkie ładowanie podczas prawidłowego korzystania z buforowania<br/>Wiele opcji dobrze współpracuje z dynamicznym projektem strony<br/>|
|Minusy:<br/><br/>**Wpływa na wydajność, jeśli buforowanie jest wyłączone**<br/>Z zastrzeżeniem ograniczania przepustowości<br/>|Minusy:<br/><br/>Nie są automatycznie aktualizowane w celu odzwierciedlenia struktury lokacji<br/>**Wpływa na wydajność, jeśli jest włączone przycinanie zabezpieczeń** lub gdy struktura nawigacji jest złożona<br/>|Minusy:<br/><br/>Brak możliwości łatwego zamawiania witryn<br/>Wymaga dostosowania strony wzorcowej (wymagane są umiejętności techniczne)<br/>|Minusy:<br/><br/>Tworzenie niestandardowe jest wymagane<br/>Wymagane jest zewnętrzne źródło danych/pamięć podręczna, np. platforma Azure<br/>|

Najbardziej odpowiednia opcja dla twojej witryny będzie zależeć od wymagań witryny i możliwości technicznych. Jeśli potrzebujesz łatwego do skonfigurowania dostawcy nawigacji, który automatycznie aktualizuje zawartość po zmianie, dobrym rozwiązaniem jest nawigacja strukturalna [z włączonym buforowaniem](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) .

>[!NOTE]
>Zastosowanie tej samej zasady co nowoczesne witryny programu SharePoint przez uproszczenie ogólnej struktury witryny do bardziej płaskiej, nie hierarchicznej struktury zwiększa wydajność i upraszcza przechodzenie do nowoczesnych witryn programu SharePoint. Oznacza to, że zamiast jednego zbioru witryn z setkami witryn (podsieci), lepszym podejściem jest posiadanie wielu zbiorów witryn z bardzo małą liczbą podwitryn (podsieci).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>Analizowanie wydajności nawigacji w usłudze SharePoint Online

[Narzędzie Diagnostyka strony dla programu SharePoint](./page-diagnostics-for-spo.md) to rozszerzenie przeglądarki przeglądarki Microsoft Edge i przeglądarki Chrome, które analizuje zarówno nowoczesny portal usługi SharePoint Online, jak i klasyczne strony witryn publikowania. To narzędzie działa tylko dla usługi SharePoint Online i nie może być używane na stronie systemu programu SharePoint.

Narzędzie generuje raport dla każdej analizowanej strony pokazujący, jak strona działa względem wstępnie zdefiniowanego zestawu reguł i wyświetla szczegółowe informacje, gdy wyniki testu wykraczają poza wartość punktu odniesienia. Administratorzy i projektanci usługi SharePoint Online mogą używać narzędzia do rozwiązywania problemów z wydajnością, aby upewnić się, że nowe strony są zoptymalizowane przed opublikowaniem.

**W szczególności sprequestDuration** to czas potrzebny na przetworzenie strony przez program SharePoint. Intensywna nawigacja (na przykład strony w nawigacji), złożone hierarchie lokacji oraz inne opcje konfiguracji i topologii mogą znacznie przyczynić się do dłuższego czasu trwania.

## <a name="using-structural-navigation-in-sharepoint-online"></a>Korzystanie z nawigacji strukturalnej w usłudze SharePoint Online

Jest to wbudowana nawigacja używana domyślnie i jest najprostszym rozwiązaniem. Nie wymaga żadnych dostosowań, a użytkownik nietechnologii może również łatwo dodawać elementy, ukrywać elementy i zarządzać nawigacją na stronie ustawień. Zalecamy [włączenie buforowania, w](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) przeciwnym razie występuje kosztowny kompromis wydajności.

### <a name="how-to-implement-structural-navigation-caching"></a>Jak zaimplementować buforowanie nawigacji strukturalnej

W obszarze **Ustawienia** >  witryny **Look and Feel** > **Navigation** możesz sprawdzić, czy nawigacja strukturalna jest wybrana dla nawigacji globalnej lub bieżącej nawigacji. Wybranie pozycji **Pokaż strony** będzie miało negatywny wpływ na wydajność.

![Nawigacja strukturalna z wybraną opcją Pokaż podwitryny.](../media/SPONavOptionsStructuredShowSubsites.png)

Buforowanie można włączyć lub wyłączyć na poziomie zbioru witryn i na poziomie witryny i jest domyślnie włączone dla obu tych funkcji. Aby włączyć na poziomie zbioru witryn, w obszarze Ustawienia **witryny** > **Administracja** >  zbiorem **witryn Nawigacja zbioru witryn** zaznacz pole wyboru **Włącz buforowanie**.

![Włącz buforowanie na poziomie zbioru witryn.](../media/structural-nav/structural-nav-caching-site-coll.png)

Aby włączyć na poziomie lokacji, w obszarze **Nawigacji** **ustawień** >  witryny zaznacz pole wyboru **Włącz buforowanie**.

![Włącz buforowanie na poziomie lokacji.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Korzystanie z zarządzanej nawigacji i metadanych w usłudze SharePoint Online

Nawigacja zarządzana to kolejna dostępna opcja, która umożliwia ponowne utworzenie większości tych samych funkcji co nawigacja strukturalna. Zarządzane metadane można skonfigurować tak, aby przycinanie zabezpieczeń było włączone lub wyłączone. Po skonfigurowaniu z wyłączonym przycinaniem zabezpieczeń nawigacja zarządzana jest dość wydajna, ponieważ ładuje wszystkie linki nawigacji ze stałą liczbą wywołań serwera. Włączenie przycinania zabezpieczeń neguje jednak niektóre zalety wydajności nawigacji zarządzanej.

Jeśli musisz włączyć przycinanie zabezpieczeń, zalecamy:

- Zaktualizuj wszystkie przyjazne linki URL do prostych linków
- Dodawanie wymaganych węzłów przycinania zabezpieczeń jako przyjaznych adresów URL
- Ogranicz liczbę elementów nawigacji do nie więcej niż 100 i nie więcej niż 3 poziomy głębokie

Wiele witryn nie wymaga przycinania zabezpieczeń, ponieważ struktura nawigacji jest często spójna dla wszystkich użytkowników witryny. Jeśli przycinanie zabezpieczeń jest wyłączone i do nawigacji zostanie dodany link, do których nie wszyscy użytkownicy mają dostęp, link będzie nadal wyświetlany, ale spowoduje odmowę dostępu. Nie ma ryzyka przypadkowego dostępu do zawartości.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Jak zaimplementować nawigację zarządzane i wyniki

Istnieje kilka artykułów na temat docs.microsoft.com na temat szczegółów nawigacji zarządzanej. Zobacz na przykład [Omówienie nawigacji zarządzanej w programie SharePoint Server](/sharepoint/administration/overview-of-managed-navigation).

Aby zaimplementować nawigację zarządzane, należy skonfigurować terminy z adresami URL odpowiadającymi strukturze nawigacji witryny. Zarządzana nawigacja może nawet zostać ręcznie wyselekcjonowana w celu zastąpienia nawigacji strukturalnej w wielu przypadkach. Przykład:

![Struktura witryny usługi SharePoint Online.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Używanie skryptów po stronie klienta opartych na wyszukiwaniu

Jedna z typowych klas niestandardowych implementacji nawigacji obejmuje wzorce projektowe renderowane przez klienta, które przechowują lokalną pamięć podręczną węzłów nawigacji.

Ci dostawcy nawigacji mają kilka kluczowych zalet:

- Zazwyczaj dobrze sprawdzają się w dynamicznych projektach stron.
- Są one niezwykle skalowalne i wydajne, ponieważ mogą być renderowane bez kosztów zasobów (i odświeżane w tle po przekroczeniu limitu czasu).
- Ci dostawcy nawigacji mogą pobierać dane nawigacji przy użyciu różnych strategii, od prostych konfiguracji statycznych po różnych dynamicznych dostawców danych.

Przykładem dostawcy danych jest użycie **nawigacji opartej na wyszukiwaniu**, która umożliwia elastyczność wyliczania węzłów nawigacji i wydajnego obsługi przycinania zabezpieczeń.

Istnieją inne popularne opcje tworzenia **niestandardowych dostawców nawigacji**. Zapoznaj się z [rozwiązaniami nawigacji dla portali usługi SharePoint Online](/sharepoint/dev/solution-guidance/portal-navigation) , aby uzyskać dalsze wskazówki dotyczące tworzenia niestandardowego dostawcy nawigacji.

Za pomocą wyszukiwania możesz wykorzystać indeksy utworzone w tle przy użyciu przeszukiwania ciągłego. Wyniki wyszukiwania są pobierane z indeksu wyszukiwania, a wyniki są obcięte zabezpieczeniami. Jest to zazwyczaj szybsze niż dostawcy nawigacji na zewnątrz, gdy wymagane jest przycinanie zabezpieczeń. Użycie wyszukiwania nawigacji strukturalnej, zwłaszcza jeśli masz złożoną strukturę lokacji, znacznie przyspieszy czas ładowania stron. Główną zaletą tej funkcji w stosunku do nawigacji zarządzanej jest to, że korzystasz z przycinania zabezpieczeń.

Takie podejście polega na utworzeniu niestandardowej strony wzorcowej i zastąpieniu wbudowanego kodu nawigacyjnego niestandardowym kodem HTML. Wykonaj tę procedurę opisaną w poniższym przykładzie, aby zastąpić kod nawigacji w pliku `seattle.html`. W tym przykładzie otworzysz `seattle.html` plik i zastąpisz cały element `id="DeltaTopNavigation"` niestandardowym kodem HTML.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Przykład: zastąp kod nawigacji na stronie wzorcowej

1. Przejdź do strony Ustawienia witryny.
2. Otwórz galerię stron wzorcowych, klikając pozycję **Strony wzorcowe**.
3. W tym miejscu możesz przejść przez bibliotekę i pobrać plik `seattle.master`.
4. Edytuj kod przy użyciu edytora tekstów i usuń blok kodu na poniższym zrzucie ekranu.<br/>![Usuń pokazany blok kodu.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Usuń kod między tagami `<SharePoint:AjaxDelta id="DeltaTopNavigation">` i `<\SharePoint:AjaxDelta>` i zastąp go następującym fragmentem kodu:<br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. Zastąp adres URL tagu kotwicy obrazu ładowania na początku linkiem do obrazu ładowania w zbiorze witryn. Po wprowadzeniu zmian zmień nazwę pliku, a następnie przekaż go do galerii stron wzorcowych. Spowoduje to wygenerowanie nowego pliku master.<br/>
7. Ten kod HTML to podstawowa adiustacja, która zostanie wypełniona przez wyniki wyszukiwania zwrócone z kodu JavaScript. Musisz edytować kod, aby zmienić wartość var root = "adres URL zbioru witryn", jak pokazano w poniższym fragmencie kodu:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Wyniki są przypisywane do tablicy self.nodes, a hierarchia jest kompilowana z obiektów przy użyciu linq.js przypisywania danych wyjściowych do tablicy self.hierarchy. Ta tablica jest obiektem powiązanym z kodem HTML. Odbywa się to w funkcji toggleView(), przekazując obiekt self do funkcji ko.applyBinding().<br/>Spowoduje to powiązanie tablicy hierarchii z następującym kodem HTML:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

Programy obsługi zdarzeń i `mouseenter` `mouseexit` są dodawane do nawigacji najwyższego poziomu w celu obsługi menu rozwijanych podwitryn, które są wykonywane w `addEventsToElements()` funkcji.

W naszym złożonym przykładzie nawigacji nowe ładowanie strony bez lokalnego buforowania pokazuje, że czas spędzony na serwerze został skrócony z nawigacji strukturalnej testu porównawczego, aby uzyskać podobny wynik jak w przypadku zarządzanego podejścia nawigacji.

### <a name="about-the-javascript-file"></a>Informacje o pliku JavaScript...

>[!NOTE]
>Jeśli używasz niestandardowego języka JavaScript, upewnij się, że publiczna sieć CDN jest włączona, a plik znajduje się w lokalizacji cdn.

Cały plik JavaScript jest następujący:

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

Aby podsumować kod pokazany powyżej w `jQuery $(document).ready` funkcji, utworzono funkcję `viewModel object` , a następnie `loadNavigationNodes()` wywoływana jest funkcja w tym obiekcie. Ta funkcja ładuje wcześniej utworzoną hierarchię nawigacji przechowywaną w magazynie lokalnym HTML5 przeglądarki klienckiej lub wywołuje funkcję `queryRemoteInterface()`.

`QueryRemoteInterface()` Tworzy żądanie przy użyciu `getRequest()` funkcji z parametrem zapytania zdefiniowanym wcześniej w skrypcie, a następnie zwraca dane z serwera. Te dane są zasadniczo tablicą wszystkich witryn w zbiorze witryn reprezentowanych jako obiekty transferu danych o różnych właściwościach.

Te dane są następnie analizowane we wcześniej zdefiniowanych `SPO.Models.NavigationNode` obiektach, które umożliwiają `Knockout.js` tworzenie zauważalnych właściwości do użycia przez dane łączące wartości z wcześniej zdefiniowanym kodem HTML.

Obiekty są następnie umieszczane w tablicy wyników. Ta tablica jest analizowana w formacie JSON przy użyciu narzędzia Knockout i przechowywana w magazynie przeglądarki lokalnej w celu zwiększenia wydajności podczas przyszłych obciążeń stron.

### <a name="benefits-of-this-approach"></a>Zalety tego podejścia

Jedną z głównych zalet [tego podejścia jest to](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) , że przy użyciu magazynu lokalnego HTML5 nawigacja jest przechowywana lokalnie dla użytkownika podczas następnego ładowania strony. Uzyskujemy znaczne ulepszenia wydajności z korzystania z interfejsu API wyszukiwania dla nawigacji strukturalnej; Jednak wykonanie i dostosowanie tej funkcji wymaga pewnych możliwości technicznych.

W [przykładowej implementacji](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) lokacje są uporządkowane w taki sam sposób jak wbudowana nawigacja strukturalna; porządku alfabetycznego. Jeśli chcesz odejść od tej kolejności, bardziej skomplikowane byłoby opracowanie i utrzymanie. Ponadto takie podejście wymaga odbiegania od obsługiwanych stron wzorcowych. Jeśli niestandardowa strona wzorca nie jest obsługiwana, witryna nie będzie zawierać aktualizacji i ulepszeń wprowadzanych przez firmę Microsoft na stronach wzorcowych.

Powyższy [kod](#about-the-javascript-file) ma następujące zależności:

- jQuery — https://jquery.com/
- KnockoutJS — https://knockoutjs.com/
- Linq.js — `https://linqjs.codeplex.com/`lub github.com/neuecc/linq.js

Bieżąca wersja linqJS nie zawiera metody ByHierarchy używanej w powyższym kodzie i spowoduje przerwanie kodu nawigacji. Aby rozwiązać ten problem, dodaj następującą metodę do pliku Linq.js przed wierszem `Flatten: function ()`.

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>Tematy pokrewne

[Omówienie nawigacji zarządzanej w programie SharePoint Server](/sharepoint/administration/overview-of-managed-navigation)

[Buforowanie i wydajność nawigacji strukturalnej](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)