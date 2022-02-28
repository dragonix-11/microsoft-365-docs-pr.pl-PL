---
title: Opcje nawigacji dla aplikacji SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule opisano witryny opcji nawigacji z włączoną SharePoint publikowanie w SharePoint Online.
ms.openlocfilehash: c59006db8505991bd41d29714caae144b284f07d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984379"
---
# <a name="navigation-options-for-sharepoint-online"></a>Opcje nawigacji dla aplikacji SharePoint Online

W tym artykule opisano witryny opcji nawigacji z włączoną SharePoint publikowanie w SharePoint Online. Wybór i konfiguracja nawigacji znacząco wpływa na wydajność i skalowalność witryn w u SharePoint Online. Szablon SharePoint Witryny publikowania powinien być używany tylko w przypadku, gdy jest wymagany w przypadku scentralizowanego portalu, a funkcja publikowania powinna być włączona tylko w określonych witrynach i tylko wtedy, gdy jest to bezwzględnie wymagane, ponieważ może to wpłynąć na wydajność w przypadku niepoprawnego korzystania z niego.

>[!NOTE]
>Jeśli korzystasz z nowoczesnych opcji nawigacji SharePoint, takich jak mega menu, nawigacja kaskadowa lub nawigacja w centrum, ten artykuł nie dotyczy Twojej witryny. Nowoczesne SharePoint witryn są współużytkowane w hierarchii witryn oraz w modelu z wzorem dla centrum i wyczyszczania. Dzięki temu można osiągnąć wiele scenariuszy, które NIE wymagają używania SharePoint publikowania.

## <a name="overview-of-navigation-options"></a>Omówienie opcji nawigacji

Konfiguracja dostawcy nawigacji może znacząco wpłynąć na wydajność całej witryny, a także należy starannie rozważyć wybór dostawcy nawigacji i konfigurację, która skutecznie spełnia wymagania witryny SharePoint nawigacji. Istnieje dwóch znanych dostawców nawigacji, a także niestandardowe implementacje nawigacji.

Pierwszą opcją [**,**](#using-structural-navigation-in-sharepoint-online) nawigacja strukturalna, jest zalecana opcja nawigacji w aplikacji SharePoint Online dla klasycznych witryn sieci SharePoint, jeśli w twojej witrynie włączyć buforowanie nawigacji **strukturalnej**. Ten dostawca nawigacji wyświetla elementy nawigacji poniżej bieżącej witryny oraz opcjonalnie bieżącej witryny i jej elementów równorzędnych. Udostępnia on dodatkowe funkcje, takie jak przycinanie zabezpieczeń i wyliczenie struktury witryny. Jeśli buforowanie jest wyłączone, będzie to miało negatywny wpływ na wydajność i skalowalność oraz może podlegać ograniczaniu.

Druga opcja, [**nawigacja zarządzana (metadane),**](#using-managed-navigation-and-metadata-in-sharepoint-online) reprezentuje elementy nawigacji przy użyciu zestawu terminów zarządzanych metadanych. Zalecamy, aby przycinać zabezpieczenia, o ile nie jest to wymagane. Przycinanie zabezpieczeń jest włączane jako domyślne ustawienie bezpieczne dla tego dostawcy nawigacji. Wiele witryn nie wymaga jednak nakładu pracy związanej z zabezpieczeniami, ponieważ elementy nawigacji często są spójne dla wszystkich użytkowników witryny. W przypadku zalecanej konfiguracji w celu wyłączenia przycinania zabezpieczeń ten dostawca nawigacji nie wymaga wyliczenia struktury witryny i jest wysoce skalowalny, co ma dopuszczalny wpływ na wydajność.

Oprócz tego, że wielu klientów zaimplementowało alternatywne niestandardowe implementacje nawigacji, wielu klientów pomyślnie zaimplementowało alternatywne niestandardowe implementacje nawigacji. Zobacz [wykonywanie skryptów po stronie klienta oparte na](#using-search-driven-client-side-scripting) wyszukiwaniu w tym artykule.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Zalety i wady opcji nawigacji SharePoint Online

W poniższej tabeli podsumowano zalety i wady poszczególnych opcji.

|Nawigacja strukturalna  |Nawigacja zarządzana  |Nawigacja sterowany wyszukiwaniem  |Dostawca nawigacji niestandardowej  |
|---------|---------|---------|---------|
|Zawodowcy:<br/><br/>Łatwa obsługa<br/>Przycięty zabezpieczenia<br/>Automatyczne aktualizacje w ciągu 24 godzin po zmianie zawartości<br/>     |Zawodowcy:<br/><br/>Łatwa obsługa<br/>|Zawodowcy:<br/><br/>Przycięty zabezpieczenia<br/>Automatyczne aktualizacje w przypadku do dodania witryn<br/>Szybki czas ładowania i lokalnie buforowana struktura nawigacji<br/>|Zawodowcy:<br/><br/>Szerszy wybór dostępnych opcji<br/>Szybkie ładowanie podczas poprawnego korzystania z buforowania<br/>Wiele opcji dobrze się układa w elastycznym projekcie strony<br/>|
|Wady:<br/><br/>**Wpływa na wydajność, jeśli buforowanie jest wyłączone**<br/>Podlega ograniczaniu<br/>|Wady:<br/><br/>Nie jest automatycznie aktualizowana w celu odzwierciedlenia struktury witryny<br/>**Wpływa na wydajność, jeśli jest włączone przycinanie zabezpieczeń** lub struktura nawigacji jest złożona<br/>|Wady:<br/><br/>Brak możliwości łatwego zamawiania witryn<br/>Wymaga dostosowania strony wzorcowej (wymagane umiejętności techniczne)<br/>|Wady:<br/><br/>Wymagany jest niestandardowy rozwój<br/>Zewnętrzne źródło danych/ przechowywana pamięć podręczna są potrzebne np. azure<br/>|

Wybór najbardziej odpowiedniej opcji w witrynie zależy od jej wymagań i możliwości technicznych. Jeśli chcesz, aby dostawca nawigacji był łatwy w konfiguracji i automatycznie aktualizowany po zmianie zawartości, dobrym rozwiązaniem jest nawigacja strukturalna z włączonym buforowaniem.[](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)

>[!NOTE]
>Stosowanie tej samej zasady, co nowoczesne witryny SharePoint przez uproszczenie ogólnej struktury witryn do prostszej, nie hierarchicznej struktury zwiększa wydajność i upraszcza przechodzenie do nowoczesnych SharePoint witryn. Oznacza to, że zamiast mieć jeden zbiór witryn z setkami witryn (podwebami), lepszym rozwiązaniem jest posiadanie wielu zbiorów witryn z bardzo kilkoma podwitrynami (podwitrynami).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>Analizowanie wydajności nawigacji w u SharePoint Online

Narzędzie [Diagnostyka stron dla SharePoint](./page-diagnostics-for-spo.md) to rozszerzenie przeglądarki dla przeglądarek Microsoft Edge i Chrome, które analizuje zarówno nowoczesne portal SharePoint Online, jak i klasyczne strony witryn publikowania. To narzędzie działa tylko w SharePoint Online i nie można go używać na SharePoint stronie systemu.

Narzędzie generuje dla każdej analizowanej strony raport pokazujący, jak strona wykonuje się na podstawie wstępnie zdefiniowanego zestawu reguł, i wyświetla szczegółowe informacje, gdy wyniki testu spoza wartości bazowej. SharePoint online administratorzy i projektanci mogą używać tego narzędzia do rozwiązywania problemów z wydajnością w celu zapewnienia optymalizacji nowych stron przed opublikowaniem.

**W szczególności SPRequestDuration** to czas przetwarzania SharePoint strony. Bardziej skomplikowana nawigacja (na przykład ze stronami w nawigacji), złożone hierarchie witryn oraz inne opcje konfiguracji i topologii mogą znacznie skrócić czas trwania.

## <a name="using-structural-navigation-in-sharepoint-online"></a>Korzystanie z nawigacji strukturalnej w u SharePoint Online

Jest to domyślna nawigacja, która jest obecnie używana, i jest najprostszym rozwiązaniem. Nie wymaga on żadnych dostosowań, a użytkownik niebędący użytkownikiem technicznym może też łatwo dodawać elementy, ukrywać elementy i zarządzać nawigacją ze strony ustawień. Zalecamy włączenie [buforowania](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), w przeciwnym razie kosztowna wydajność jest kosztowna.

### <a name="how-to-implement-structural-navigation-caching"></a>Jak zaimplementować buforowanie nawigacji strukturalnej

W **obszarze Ustawienia** >  **Oki i Nawigacja** **feelNavigation** >  możesz sprawdzić, czy nawigacja strukturalna jest zaznaczona dla nawigacji globalnej, czy dla bieżącej nawigacji. Wybranie **opcji Pokaż strony** będzie miało negatywny wpływ na wydajność.

![Nawigacja strukturalna z zaznaczoną witrynie Pokaż podwitryny.](../media/SPONavOptionsStructuredShowSubsites.png)

Buforowanie włączać lub wyłączać na poziomie zbioru witryn i na poziomie witryny, a także jest domyślnie włączone dla obu. Aby włączyć tę funkcję na poziomie zbioru witryn,  >  w Ustawienia **Nawigacja** >  zbioru witryn z witrynami administracji zbioru **witryn zaznacz pole** wyboru Włącz **buforowanie**.

![Włączanie buforowania na poziomie witryny.](../media/structural-nav/structural-nav-caching-site-coll.png)

Aby włączyć na poziomie witryny, w obszarze **Ustawienia** >  **Nawigacja** witryny zaznacz pole wyboru **Włącz buforowanie**.

![Włączanie buforowania na poziomie witryny.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Korzystanie z zarządzanej nawigacji i metadanych w u SharePoint Online

Nawigacja zarządzana to inna, odtworzona, dostępna w jednym przypadku opcja, która umożliwia ponowne utworzenie większości funkcji nawigacji strukturalnej. Zarządzane metadane można skonfigurować tak, aby włączono lub wyłączono przycinanie zabezpieczeń. Po skonfigurowaniu z wyłączonym przycinaniem zabezpieczeń nawigacja zarządzana jest dość wydajna, ponieważ ładuje wszystkie linki nawigacji ze stałą liczbą połączeń z serwerem. Włączenie przycinania zabezpieczeń ma jednak negatyw niektóre z zalet wydajności zarządzanej nawigacji.

Jeśli musisz włączyć funkcję przycinania zabezpieczeń, zalecamy:

- Aktualizowanie wszystkich przyjaznych linków w adresie URL do prostych linków
- Dodawanie wymaganych węzłów do przycinania zabezpieczeń jako przyjaznych adresów URL
- Ograniczanie liczby elementów nawigacyjnych do nie więcej niż 100 i nie więcej niż 3 poziomów głębokości

Wiele witryn nie wymaga przycinania zabezpieczeń, ponieważ struktura nawigacji jest często spójna dla wszystkich użytkowników witryny. Jeśli przycinanie zabezpieczeń jest wyłączone i do nawigacji zostanie dodany link, do których nie wszyscy użytkownicy mają dostęp, link nadal będzie wyświetlany, ale będzie prowadzić do komunikatu o odmowie dostępu. Nie ma ryzyka przypadkowego dostępu do zawartości.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Jak wdrożyć nawigację zarządzaną i wyniki

Istnieje kilka artykułów na docs.microsoft.com na temat szczegółów nawigacji zarządzanej. Na przykład zobacz [Omówienie nawigacji zarządzanej w programie SharePoint Server](/sharepoint/administration/overview-of-managed-navigation).

Aby wdrożyć nawigację zarządzaną, należy skonfigurować terminy z adresami URL odpowiadającymi strukturze nawigacji witryny. Nawigację zarządzaną można nawet w wielu przypadkach zarządzać ręcznie, aby zastąpić nawigację strukturalną. Przykład:

![SharePoint witryny online.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Używanie skryptów po stronie klienta sterowanych wyszukiwaniem

Jedna typowa klasa niestandardowych implementacji nawigacji zapewnia renderowane przez klienta wzorce projektowania przechowujące lokalną pamięć podręczną węzłów nawigacji.

Poniższe dostawcy nawigacji mają kilka kluczowych zalet:

- Na ogół dobrze się one działają z szybko reagującymi projektami stron.
- Są one bardzo skalowalne i performacyjnie, ponieważ mogą być renderowane bez kosztów zasobów (i odświeżane w tle po przeli czasie).
- Ci dostawcy nawigacji mogą pobierać dane nawigacji za pomocą różnych strategii, od prostych konfiguracji statycznych po różnych dynamicznych dostawców danych.

Przykładem dostawcy danych jest korzystanie z nawigacji opartej na wyszukiwaniu **, która** pozwala na elastyczne wyliczanie węzłów nawigacji i wydajną obsługę przycinania zabezpieczeń.

Istnieją inne popularne opcje tworzenia niestandardowych **dostawców nawigacji**. Zapoznaj się [z rozwiązaniami nawigacji dla SharePoint Online,](/sharepoint/dev/solution-guidance/portal-navigation) aby uzyskać dalsze wskazówki dotyczące tworzenia dostawcy nawigacji niestandardowej.

Za pomocą wyszukiwania możesz korzystać z indeksów wbudowanych w tle przy użyciu przeszukiwania ciągłego. Wyniki wyszukiwania są przyciągane z indeksu wyszukiwania, a wyniki są przycinane w zabezpieczeniach. Jest to zazwyczaj szybsze niż gdy wymagane jest obcięcie zabezpieczeń przez dostawców nawigacji. Wyszukiwanie nawigacji strukturalnej, zwłaszcza w przypadku złożonej struktury witryny, znacznie przyspiesza ładowanie strony. Główną zaletą tej możliwości w przypadku nawigacji zarządzanej jest to, że korzystasz z przycinania zabezpieczeń.

Ta metoda obejmuje utworzenie niestandardowej strony wzorcowej i zastąpienie niestandardowego kodu nawigacyjnego HTML. Aby zastąpić kod nawigacyjny w pliku, wykonaj tę procedurę podaną w poniższym przykładzie `seattle.html`. W tym przykładzie otworzysz `seattle.html` plik i zamienisz cały element `id="DeltaTopNavigation"` na niestandardowy kod HTML.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Przykład: zamienianie kodu nawigacji, który jest już na stronie wzorcowej,

1. Przejdź do strony Ustawienia witryny.
2. Otwórz galerię stron wzorcowych, klikając **pozycję Strony wzorcowe**.
3. W tym miejscu możesz poruszać się po bibliotece i pobrać plik `seattle.master`.
4. Edytuj kod za pomocą edytora tekstów i usuń blok kodu na poniższym zbędnie.<br/>![Usuń pokazany blok kodu.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Usuń kod między tagami `<SharePoint:AjaxDelta id="DeltaTopNavigation">` i `<\SharePoint:AjaxDelta>` zamień go na następujący fragment:<br/>

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
6. Zamień adres URL tagu zakotwiczenia obrazu ładowania na początku na link do obrazu ładowania w zbiorze witryn. Po wgraniu zmian zmień nazwę pliku, a następnie przekaż go do galerii stron wzorcowych. Zostanie wygenerowany nowy plik główny.<br/>
7. Ten kod HTML to podstawowa markup, która zostanie wypełniona wynikami wyszukiwania zwróconmi z kodu JavaScript. Należy edytować kod w celu zmiany wartości var root = "adres URL zbioru witryn", jak pokazano w poniższym fragmencie:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Wyniki są przypisywane do tablicy self.nodes, a na obiektach jest wbudowana hierarchia, która linq.js danych wyjściowych do self.hierarchy tablicy. Ta tablica jest obiektem powiązanym z kodem HTML. Robi się to w funkcji toggleView(), przekazując obiekt sobie do funkcji ko.applyBinding().<br/>Spowoduje to, że tablica hierarchii zostanie powiązana z następującym kodem HTML:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

Program obsługi zdarzeń dla `mouseenter` nawigacji `mouseexit` najwyższego poziomu i jest dodawany do nich w celu obsługi menu rozwijanych podwiter, które są wykonywane w `addEventsToElements()` funkcji.

W naszym złożonym przykładzie nawigacji nowe obciążenie strony bez lokalnego buforowania wskazuje, że czas spędzony na serwerze został obcięty z nawigacji strukturalnej wzorcowej w celu uzyskania podobnego wyniku jak metoda nawigacji zarządzanej.

### <a name="about-the-javascript-file"></a>Informacje o pliku JavaScript...

>[!NOTE]
>W przypadku używania niestandardowego kodu JavaScript upewnij się, CDN włączono obsługę plików publicznych i że plik znajduje się CDN lokalizacji.

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

Aby podsumować kod pokazany powyżej w `jQuery $(document).ready` funkcji, jest tworzona funkcja `viewModel object` `loadNavigationNodes()` tego obiektu. Ta funkcja ładuje poprzednio zbudowaną hierarchię nawigacji przechowywaną w lokalnym magazynie HTML5 przeglądarki klienckiej lub wywołuje tę funkcję `queryRemoteInterface()`.

`QueryRemoteInterface()` tworzy żądanie przy użyciu funkcji z `getRequest()` parametrem zapytania zdefiniowanym wcześniej w skrypcie, a następnie zwraca dane z serwera. Te dane to zasadniczo tablica wszystkich witryn w zbiorze witryn reprezentowanych jako obiekty transferu danych o różnych właściwościach.

Te dane są następnie analizowane `SPO.Models.NavigationNode` `Knockout.js` z wcześniej zdefiniowanymi obiektami, które używają do tworzenia obserwowalnych właściwości do użytku przez powiązanie danych z zdefiniowanym wcześniej kodem HTML wartości.

Obiekty są następnie umieszczane w tablicy wyników. Ta tablica jest analizowana do JSON przy użyciu nokautów i przechowywana w lokalnym magazynie przeglądarki w celu poprawy wydajności podczas ładowania stron w przyszłości.

### <a name="benefits-of-this-approach"></a>Zalety tego rozwiązania

Jedną z głównych zalet [tego](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) rozwiązania jest to, że korzystając z lokalnego magazynu HTML5, nawigacja jest przechowywana lokalnie dla użytkownika, gdy następnym razem załaduje stronę. Korzystając z interfejsu API wyszukiwania do nawigacji strukturalnej, ulepszamy wydajność; Jednak wykonywanie i dostosowywanie tej funkcji wymaga pewnych funkcji technicznych.

W [przykładowej implementacji](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) witryny są uporządkowane w taki sam sposób, jak w przypadku nawigacji strukturalnej, gdy jesteś w pracy. w kolejności alfabetycznej. Jeśli chcesz odchylić się od tej kolejności, opracowywanie i obsługa byłaby bardziej skomplikowana. Ponadto ta metoda wymaga odejmacji od obsługiwanych stron wzorcowych. Jeśli niestandardowa strona wzorcowa nie zostanie zachowana, w witrynie zostaną pominięte aktualizacje i ulepszenia wprowadzone przez firmę Microsoft w tych stronach wzorcowych.

Powyższy [kod ma](#about-the-javascript-file) następujące zależności:

- jQuery - https://jquery.com/
- KnockoutJS - https://knockoutjs.com/
- Linq.js - https://linqjs.codeplex.com/lub github.com/neuecc/linq.js

Bieżąca wersja systemu LinqJS nie zawiera metody ByHierarchy używanej w powyższym kodzie i spowoduje zerwanie kodu nawigacji. Aby rozwiązać ten problem, dodaj do pliku Linq.js przed wierszem następującą metodę `Flatten: function ()`.

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

[Buforowanie nawigacji strukturalnej i wydajność](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)