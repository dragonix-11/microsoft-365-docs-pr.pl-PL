---
title: Office 365 adresu IP i usługi sieci Web adresu URL
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: Dowiedz się, jak używać usługi sieci web Office 365 IP i adresu URL, aby ułatwić identyfikowanie i Office 365 ruchu sieciowego.
ms.openlocfilehash: e4976bafbedc8f5289e2992569bbd5de28e9de75
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63494488"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 adresu IP i usługi sieci Web adresu URL

Usługa Office 365 i adres IP sieci Web ułatwiają identyfikowanie i rozróżnianie ruchu sieciowego w usłudze Office 365, co ułatwia ocenę, skonfigurowanie i pozostawanie na bieżąco ze zmianami. Ta usługa sieci Web oparta na usłudze REST zastępuje poprzednie pliki XML, które zostały wycofane w dniu 2 października 2018 r.

Jako klient lub dostawca urządzenia sieci obwodowej, możesz tworzyć rozwiązania z usługą sieci Web pod Office 365 adresów IP i domen FQDN. Dostęp do danych można uzyskać bezpośrednio w przeglądarce internetowej, korzystając z tych adresów URL:

- Aby uzyskać najnowszą wersję Office 365 URL i zakresów adresów IP, użyj .[https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)
- Aby uzyskać dane na stronie Office 365 URL i zakresów adresów IP dla zapór i serwerów proxy, użyj wartości [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Aby uzyskać wszystkie najnowsze zmiany od lipca 2018 r., gdy usługa sieci Web była dostępna po raz pierwszy, użyj .[https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

Jako klient, możesz korzystać z tej usługi sieci Web w celu:

- Zaktualizuj skrypty programu PowerShell, Office 365 dane punktów końcowych i zmodyfikuj wszelkie formatowanie urządzeń sieciowych.
- Skorzystaj z tych informacji, aby zaktualizować pliki PAC wdrożone na komputerach klienckich.

Jako dostawca urządzenia sieci obwodowej, możesz korzystać z tej usługi sieci Web w celu:

- Utwórz i przetestuj oprogramowanie urządzenia, aby pobrać listę do automatycznej konfiguracji.
- Sprawdź, czy jest dostępna bieżąca wersja.
- Pobierz bieżące zmiany.

> [!NOTE]
> Jeśli łączysz się z usługą Office 365 za pomocą usługi Azure ExpressRoute, zapoznaj się z usługą [Azure ExpressRoute](azure-expressroute.md) dla usługi Office 365, aby zapoznać się z usługami Office 365 obsługiwanymi przez usługę Azure ExpressRoute. Zapoznaj się również z [artykułem Office 365 url i](urls-and-ip-address-ranges.md) zakresów adresów IP, aby dowiedzieć się, które żądania sieciowe dla Office 365 wymagają łączności z Internetem. Pomoże to lepiej skonfigurować urządzenia zabezpieczeń obwodu.

Więcej informacji można znaleźć w następujących artykułach:

- [Wpis w blogu z ogłoszeniem na forum Office 365 tech Community](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 tech Community na pytania dotyczące korzystania z usług sieci Web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Typowe parametry

Te parametry są wspólne we wszystkich metodach usługi sieci Web:

- **format=\<JSON \| CSV\>** — Domyślnie format zwracanych danych to JSON. Użyj tego parametru opcjonalnego, aby zwrócić dane w formacie wartości rozdzielanych przecinkami (CSV).
- **ClientRequestId=\<guid\>** — Wymagany identyfikator GUID generowany dla skojarzenia klienta. Wygeneruj unikatowy identyfikator GUID dla każdego komputera, który wywołuje usługę sieci Web (skrypty zawarte na tej stronie generują identyfikator GUID). Nie używaj identyfikatorów GUID pokazanych w poniższych przykładach, ponieważ mogą zostać zablokowane przez usługę sieci Web w przyszłości. Format identyfikatora GUID to _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, gdzie x reprezentuje liczbę szesnastkową.

  Aby wygenerować identyfikator GUID, można użyć polecenia [programu PowerShell New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) lub usługi online, takiej jak [generator identyfikatorów GUID w trybie online](https://www.guidgenerator.com/).

## <a name="version-web-method"></a>Metoda sieci Web Version (Wersja)

Firma Microsoft aktualizuje Office 365 adres IP i pozycje FQDN na początku każdego miesiąca. Aktualizacje pozapasmowe są czasami publikowane ze względu na zdarzenia związane z obsługą, aktualizacje zabezpieczeń lub inne wymagania operacyjne.

Do danych dla każdego opublikowanego wystąpienia jest przypisany numer wersji, a metoda sieci Web Version (Wersja) umożliwia sprawdzenie, czy jest dostępna najnowsza wersja każdego Office 365 wystąpienia usługi. Zalecamy sprawdzenie wersji nie więcej niż raz na godzinę.

Parametry metody sieci Web Version (Wersja) to:

- **AllVersions=\<true \| false\>** — Domyślnie jest zwracana najnowsza wersja. Dołącz ten parametr opcjonalny, aby zażądać wszystkich opublikowanych wersji od czasu pierwszej publikacji usługi sieci Web.
- **Format=\<JSON \| CSV \| RSS\>** — Oprócz formatów JSON i CSV metoda sieci Web version (Wersja) obsługuje również funkcję RSS. Możesz użyć tego parametru opcjonalnego wraz z parametrem _AllVersions=true_, aby zażądać kanału informacyjnego RSS, który może być używany z Outlook innymi czytnikami RSS.
- **Instance=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** — Ten parametr opcjonalny określa wystąpienie, dla których ma być zwracana wersja. W razie pominięcia zostaną zwrócone wszystkie wystąpienia. Prawidłowe wystąpienia to: Worldwide, China, USGovDoD, USGovGCCHigh.

Metoda sieci Web Version (Wersja) nie jest ograniczona i nie zwraca 429 kodów odpowiedzi HTTP. Odpowiedź na metodę sieci Web Version (Wersja) zawiera nagłówek kontrolki pamięci podręcznej polecający buforowanie danych na 1 godzinę. Wynikiem metody sieci Web Version (Wersja) może być pojedynczy rekord lub tablica rekordów. Elementy każdego rekordu to:

- instance — krótka nazwa wystąpienia Office 365 usługi.
- latest — najnowsza wersja dla punktów końcowych określonego wystąpienia.
- versions — lista wszystkich poprzednich wersji dla określonego wystąpienia. Ten element jest uwzględniany tylko w przypadku, gdy parametr _AllVersions_ jest prawdziwy.

### <a name="version-web-method-examples"></a>Przykłady metody sieci Web Version (Wersja)

Przykład 1. <https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten URI zwraca najnowszą wersję każdego wystąpienia Office 365 usługi. Przykład wyniku:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> Identyfikator GUID parametru ClientRequestID w tych identyfikatorach  URI to tylko przykład. Aby wypróbować identyfikatory  URI usługi sieci Web, wygeneruj własny identyfikator GUID. Identyfikatory GUID pokazane w tych przykładach mogą zostać w przyszłości zablokowane przez usługę sieci Web.

Przykład 2. <https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten adres URI zwraca najnowszą wersję określonego Office 365 wystąpienia usługi. Przykład wyniku:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

Przykład 3. <https://endpoints.office.com/version/Worldwide?Format=CSV&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten URI pokazuje dane wyjściowe w formacie CSV. Przykład wyniku:

```csv
instance,latest
Worldwide,2018063000
```

Przykład 4. <https://endpoints.office.com/version/Worldwide?AllVersions=true&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten URI pokazuje wszystkie wcześniejsze wersje, które zostały opublikowane dla wystąpienia usługi Office 365 Worldwide. Przykład wyniku:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

Przykład 5. Adres URI kanału informacyjnego RSS: <https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS>

Ten adres URI pokazuje kanał informacyjny RSS opublikowanych wersji, który zawiera linki do listy zmian dla każdej wersji. Przykład wyniku:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>Metoda sieci Web Endpoints (Punkty końcowe)

Metoda sieci Web Endpoints (Punkty końcowe) zwraca wszystkie rekordy dla zakresów adresów IP i adresów URL, które Office 365 adresach URL. Najnowsze dane z metody sieci Web Endpoints (Punkty końcowe) powinny być zawsze używane do konfiguracji urządzenia sieciowego. Firma Microsoft udostępnia powiadomienie z wyprzedzeniem 30 dni przed opublikowaniem nowych dodatków, aby zapewnić Ci czas na zaktualizowanie list kontrolek dostępu i list obejść serwera proxy. Zalecamy, aby ponownie wywołać metodę sieci Web Endpoints (Punkty końcowe), gdy metoda sieci Web Version (Wersja) wskazuje, że jest dostępna nowa wersja danych.

Parametry metody sieci Web Endpoints (Punkty końcowe) to:

- **ServiceAreas=\<Common \| Exchange \| SharePoint \| Skype\>** — Rozdzielona przecinkami lista obszarów usługi. Prawidłowe elementy to _Common_, _Exchange_, _SharePoint_ i _Skype_. Elementy _obszaru_ usługi Common są wymaganiem wstępnym dla wszystkich pozostałych obszarów usługi, dlatego usługa sieci Web zawsze je zawiera. Jeśli nie uwzględnisz tego parametru, zostaną zwrócone wszystkie obszary usługi.
- **TenantName=\<tenant_name\>** — Nazwa Office 365 dzierżawy. Usługa sieci Web pobiera Twoją podaną nazwę i wstawia ją w częściach adresów URL, które zawierają nazwę dzierżawy. Jeśli nie podawsz nazwy dzierżawy, te części adresów URL będą mieć symbol wieloznaczny (\*).
- **NoIPv6=\<true \| false\>** — Ustaw wartość True ( _Prawda), aby_ wykluczyć adresy IPv6 z wyników, jeśli nie korzystasz z protokołu IPv6 w Twojej sieci.
- **Instance=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** — Ten parametr wymagany określa wystąpienie, z którego mają być zwracane punkty końcowe. Prawidłowe wystąpienia to: _Worldwide_, _China_, _USGovDoD_ i _USGovGCCHigh_.

Jeśli wywołasz metodę sieci Web Endpoints (Punkty końcowe) zbyt wiele razy z tego samego adresu IP klienta, może zostać wyświetlony kod odpowiedzi HTTP _429 (Zbyt wiele żądań)._ Jeśli otrzymasz ten kod odpowiedzi, poczekaj 1 godzinę, zanim powtórzysz żądanie, lub wygeneruj nowy identyfikator GUID dla żądania. Ogólnie najlepszym rozwiązaniem jest wywołanie metody sieci Web Endpoints (Punkty końcowe) tylko wtedy, gdy metoda sieci Web Version (Wersja) wskazuje, że jest dostępna nowa wersja.

Wynikiem metody sieci Web Endpoints (Punkty końcowe) jest tablica rekordów, w której każdy rekord reprezentuje określony zestaw punktów końcowych. Elementy dla każdego rekordu to:

- id — niezmienialny numer identyfikacyjny zestawu punktów końcowych.
- serviceArea — obszar usługi, do których to należy: _Common_, _Exchange_, _SharePoint_ lub _Skype_.
- adresy URL — adresy URL dla zestawu punktów końcowych. Tablica JSON rekordów DNS. Pominięte, jeśli wartość jest pusta.
- tcpPorts — porty TCP dla zestawu punktów końcowych. Wszystkie elementy portów są formatowane jako rozdzielona przecinkami lista portów lub zakresy portów rozdzielone znakiem kreski (-). Porty dotyczą wszystkich adresów IP i wszystkich adresów URL w zestawie punktów końcowych dla danej kategorii. Pominięte, jeśli wartość jest pusta.
- udpPorts — porty UDP dla zakresów adresów IP w tym zestawie punktów końcowych. Pominięte, jeśli wartość jest pusta.
- ips — zakresy adresów IP skojarzone z tym zestawem punktów końcowych jako skojarzone z wymienionymi portami TCP lub UDP. Tablica JSON zakresów adresów IP. Pominięte, jeśli wartość jest pusta.
- kategoria — kategoria łączność dla zestawu punktów końcowych. Prawidłowe wartości to _: Optimize (Optymalizuj_), _Allow (_ Zezwalaj) _i Default (Domyślne_). Jeśli przeszukujesz wynik metody sieci Web Endpoints (Punkty końcowe) dla kategorii określonego adresu IP lub adresu URL, możliwe, że zapytanie zwróci wiele kategorii. W takim przypadku postępuj zgodnie z zaleceniami dla kategorii o najwyższym priorytecie. Jeśli na przykład punkt końcowy jest wyświetlany zarówno w menu _Optymalizuj__, jak_ i w allow, należy postępować zgodnie z wymaganiami _optymalizowania_. Wymagane.
- expressRoute — _True (Prawda),_ jeśli ten zestaw punktów końcowych jest przekierowywowany przez usługi ExpressRoute, lub _False (Fałsz_ ), jeśli nie jest.
- required — _True (Prawda_), jeśli ten zestaw punktów końcowych jest wymagany do Office 365 być obsługiwany. _False_ (Fałsz), jeśli ten zestaw punktów końcowych jest opcjonalny.
- uwagi — w przypadku opcjonalnych punktów końcowych w tym tekście opisano funkcje Office 365, które będą niedostępne, jeśli adresy IP lub adresy URL z tego zestawu punktów końcowych nie będą dostępne w warstwie sieciowej. Pominięte, jeśli wartość jest pusta.

### <a name="endpoints-web-method-examples"></a>Przykłady metody sieci Web Endpoints (Punkty końcowe)

Przykład 1. <https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten URI uzyskuje wszystkie punkty końcowe dla wystąpienia Office 365 Worldwide dla wszystkich obciążeń. Przykład wyniku, który pokazuje fragment danych wyjściowych:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

Pełne dane wyjściowe żądania w tym przykładzie będą zawierać inne zestawy punktów końcowych.

Przykład 2.Uri żądania: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp; ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Ten przykład uzyskuje punkty końcowe tylko dla wystąpienia Office 365 Worldwide dla Exchange Online i zależności.

Wynik, na przykład 2, jest podobny do przykładu 1 z tym wyjątkiem, że wyniki nie będą zawierać punktów końcowych dla usługi SharePoint Online lub Skype dla firm Online.

## <a name="changes-web-method"></a>Metoda sieci Web Changes (Zmiany)

Metoda sieci Web Changes (Zmiany) zwraca najnowsze opublikowane aktualizacje, zazwyczaj zmiany z poprzedniego miesiąca w zakresach adresów IP i adresach URL.

Najważniejszymi zmianami danych punktów końcowych są nowe adresy URL i adresy IP. Nieudane dodanie adresu IP do listy kontroli dostępu zapory lub adresu URL do listy obejść serwera proxy może spowodować awarię sieci dla użytkowników Office 365 korzystających z tego urządzenia sieciowego. Niezależnie od wymagań operacyjnych nowe punkty końcowe są publikowane w usłudze sieci Web 30 dni przed datą ich obsługi administracyjnej w celu zapewnienia ci czasu na zaktualizowanie list kontroli dostępu i list obejść serwera proxy.

Parametr wymagany dla metody sieci Web Changes (Zmiany) to:

- **Version=\<YYYYMMDDNN>** — Wymagany parametr trasy adresu URL. Ta wartość to wersja, która jest obecnie zaimplementowana. Usługa sieci Web zwróci zmiany od tej wersji. Format to _RRRRMMDDNN_, gdzie _NN_ to liczba naturalna zwiększana, jeśli jednego dnia jest wymagane opublikowanie wielu wersji, z których _00_ reprezentuje pierwszą aktualizację danego dnia. Usługa sieci Web wymaga _, aby parametr wersji_ zawierał dokładnie 10 cyfr.

Szybkość metody sieci Web Changes (Zmiany) jest ograniczona w taki sam sposób, jak metoda sieci Web Endpoints (Punkty końcowe). Jeśli otrzymasz kod odpowiedzi HTTP 429, odczekaj 1 godzinę, zanim powtórzysz żądanie lub wygeneruj nowy identyfikator GUID dla żądania.

Wynikiem metody sieci Web Changes (Zmiany) jest tablica rekordów, w której każdy rekord odzwierciedla zmianę w określonej wersji punktów końcowych. Elementy dla każdego rekordu to:

- id — niezmienialny identyfikator rekordu zmiany.
- endpointSetId — identyfikator zmienionego rekordu zestawu punktów końcowych.
- disposition — zawiera opis zmiany w rekordzie zestawu punktów końcowych. Wartości są _zmieniane_, _dodawania_ lub _usuwania_.
- wpływ — nie wszystkie zmiany będą jednakowo ważne w każdym środowisku. Ten element opisuje oczekiwany wpływ tej zmiany na środowisko obwodu sieci przedsiębiorstwa. Ten element jest uwzględniany tylko w rekordach zmian wersji **2018112800** i nowszych. Mają to wpływ na następujące opcje: — AddedIp — do usługi Office 365 dodano adres IP i wkrótce pojawi się on w tej usłudze. Oznacza to zmianę, która należy zrobić na zaporze lub innym urządzeniu sieci obwodowej warstwy 3. Jeśli nie dodasz go przed rozpoczęciem korzystania z niego, może na przykład wystąpić błąd.
  — AddedUrl — adres URL został dodany do Office 365 i wkrótce pojawi się w usłudze. Oznacza to zmianę, która należy zrobić na serwerze proxy lub urządzeniu sieci obwodowej do analizowania adresów URL. Jeśli nie dodasz tego adresu URL przed rozpoczęciem używania go, może na przykład wystąpić błąd.
  — AddedIpAndUrl — dodano zarówno adres IP, jak i adres URL. Oznacza to zmianę, która należy zrobić na urządzeniu zapory w warstwie 3 albo na serwerze proxy albo urządzeniu do analizowania adresów URL. Jeśli nie dodasz tej pary adresów IP/URL przed rozpoczęciem korzystania z tej pary, może wystąpić błąd.
  — RemovedIpOrUrl — co najmniej jeden adres IP lub adres URL został usunięty z Office 365. Usuń punkty końcowe sieci z urządzeń obwodowych, ale nie ma dla Ciebie ostatecznego terminu wykonania tej pracy.
  — ChangedIsExpressRoute — zmieniono atrybut obsługi expressRoute. Jeśli korzystasz z usługi ExpressRoute, może być konieczne podjęcie działań w zależności od konfiguracji.
  — MovedIpOrUrl — Przenieśliśmy adres IP lub adres URL między tym zestawem punktów końcowych a innym. Zasadniczo nie jest wymagane żadne działanie.
  — RemovedDuplicateIpOrUrl — Usunęliśmy zduplikowany adres IP lub adres URL, ale jest on nadal publikowany dla Office 365. Zasadniczo nie jest wymagane żadne działanie.
  — OtherNonPriorityChanges — Zmieniliśmy element mniej krytyczny niż wszystkie inne opcje, na przykład zawartość pola notatki.
- version — wersja opublikowanego zestawu punktów końcowych, w którym wprowadzono zmianę. Numery wersji są w formacie _RRRRMMDDNN_, gdzie _NN_ jest liczbą naturalną zwiększaną, jeśli jednego dnia jest wymagane opublikowanie wielu wersji.
- previous — strukturę podrzędną z wyszczególnionymi poprzednimi wartościami zmienionych elementów w zestawie punktów końcowych. Ta wartość nie zostanie uwzględniona w przypadku nowo dodanych zestawów punktów końcowych. Obejmuje  _usługi ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ i _notatki_.
- current — podstruktura z wyszczególnioną zaktualizowanymi wartościami elementów zmian w zestawie punktów końcowych. Obejmuje _usługi ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ i _notatki_.
- add — strukturę podrzędną z wyszczególnioną elementami do dodania do kolekcji zestawu punktów końcowych. Pominięte, jeśli nie ma dodatków.
  — effectiveDate — definiuje dane, kiedy dodatki będą nadal obowiązywać w usłudze.
  — ips — elementy do dodania do _tablicy adresów IP_ .
  — adresy URL — elementy do dodania do _tablicy adresów URL_ .
- remove — strukturę podrzędną z wyszczególnioną elementami do usunięcia z zestawu punktów końcowych. Pominięte, jeśli nie ma usunięcia.
  — ips — elementy do usunięcia z _tablicy adresów IP_ .
  — adresy URL — elementy do usunięcia z _tablicy adresów URL_ .

### <a name="changes-web-method-examples"></a>Przykłady metody sieci Web Changes (Zmiany)

Przykład 1. <https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

To żąda wszystkich wcześniejszych zmian w wystąpieniu Office 365 Worldwide. Przykład wyniku:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

Przykład 2. <https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

To żąda zmian od określonej wersji w wystąpieniu Office 365 Worldwide. W tym przypadku określona wersja jest najnowszą wersją. Przykład wyniku:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>Przykładowy skrypt programu PowerShell

Możesz uruchomić ten skrypt programu PowerShell, aby sprawdzić, czy istnieją akcje do podjęcia w przypadku zaktualizowanych danych. Ten skrypt można uruchomić jako zaplanowane zadanie w celu sprawdzenia, czy nie ma aktualizacji wersji. Aby uniknąć nadmiernego ładowania w usłudze sieci Web, postaraj się nie uruchamiać skryptu więcej niż raz na godzinę.

Skrypt obsługuje następujące czynności:

- Sprawdza numer wersji bieżącego wystąpienia Office 365 Worldwide, wywołując interfejs API REST usługi sieci Web.
- Sprawdza bieżący plik wersji w cenie _$Env:TEMP\O365_endpoints_latestversion.txt_. Ścieżka zmiennej globalnej o **adresie $Env:TEMP** to zwykle _C:\Użytkownicy\\<\> nazwa_użytkownika\AppData\Local\Temp_.
- Jeśli jest to pierwsze uruchomienie skryptu, skrypt zwraca bieżącą wersję oraz wszystkie bieżące adresy IP i adresy URL, zapisuje wersję punktów końcowych w pliku _$Env:TEMP\O365_endpoints_latestversion.txt_ i dane wyjściowe danych punktów końcowych do pliku _$Env:TEMP\O365_endpoints_data.txt_. Edytując następujące wiersze, można zmodyfikować ścieżkę i/lub nazwę pliku wyjściowego:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- Przy każdym kolejnym wykonaniu skryptu, jeśli najnowsza wersja usługi sieci Web jest identyczna z wersją w pliku _O365_endpoints_latestversion.txt_ , skrypt zostanie zakończyny bez jakichkolwiek zmian.
- Gdy najnowsza wersja usługi sieci Web jest nowsza  niż wersja w pliku _O365_endpoints_latestversion.txt_, skrypt zwraca punkty końcowe i filtry dla punktów końcowych kategorii Zezwalaj i Optymalizuj,  aktualizuje wersję w pliku _O365_endpoints_latestversion.txt_ i zapisuje zaktualizowane dane w plikuO365_endpoints_data.txt.__

Skrypt generuje unikatowy identyfikator _ClientRequestId_ dla komputera, na który jest wykonywany, i ponownie używa tego identyfikatora w wielu połączeniach. Ten identyfikator jest przechowywany w _O365_endpoints_latestversion.txt_ pliku.

### <a name="to-run-the-powershell-script"></a>Aby uruchomić skrypt programu PowerShell

1. Skopiuj skrypt i zapisz go na lokalnym dysku twardym lub w lokalizacji skryptu jako _Get-O365WebServiceUpdates.ps1_.
1. Wykonaj skrypt w preferowanym edytorze skryptów, takim jak PowerShell ISE lub VS Code, albo z konsoli programu PowerShell, używając następującego polecenia:

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    Nie ma parametrów do przekazania do skryptu.

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a>Przykładowy skrypt języka Python

Oto skrypt w języku Python przetestowany w języku Python 3.6.3 na Windows 10, który można uruchomić, aby sprawdzić, czy istnieją akcje do podjęcia dla zaktualizowanych danych. Ten skrypt sprawdza numer wersji dla punktów końcowych Office 365 Worldwide. W przypadku zmiany pobiera on punkty końcowe i filtruje punkty końcowe kategorii _Zezwalaj_ i Optymalizuj. Używa on również unikatowego wartości ClientRequestId w wielu połączeniach i zapisuje najnowszą znalezioną wersję w pliku tymczasowym. Zadzwoń do tego skryptu raz na godzinę, aby sprawdzić, czy nie ma aktualizacji wersji.

```python
import json
import tempfile
from pathlib import Path
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Wersja interfejsu usługi sieci Web

W przyszłości mogą być wymagane aktualizacje parametrów lub wyników tych metod usługi sieci Web. Po opublikowaniu wersji tych usług sieci Web o ogólnej dostępności firma Microsoft podjąć uzasadnione starania w celu wcześniejszego powiadomienia o istotnych aktualizacjach usługi sieci Web. Gdy firma Microsoft uzna, że aktualizacja będzie wymagała zmian w klientach korzystających z usługi sieci Web, zachowaje dostępną poprzednią wersję (jedną wersję wstecz) usługi sieci Web przez co najmniej 12 miesięcy od wydania nowej wersji. Klienci, którzy nie uaktualnią w tym czasie, mogą nie być w stanie uzyskać dostępu do usługi sieci Web i jej metod. Klienci muszą zapewnić, że klienci usługi sieci Web będą nadal działać bez błędu, jeśli w podpisie interfejsu usługi sieci Web zostaną wprowadzone następujące zmiany:

- Dodanie nowego parametru opcjonalnego do istniejącej metody sieci Web, która nie musi być dostarczana przez starszych klientów i nie ma wpływu na wynik obierania przez starszego klienta.
- Dodanie nowego nazwanego atrybutu w jednym z elementów odpowiedzi REST lub innych kolumn do pliku CSV odpowiedzi.
- Dodanie nowej metody sieci Web z nową nazwą, która nie jest wywoływana przez starszych klientów.

## <a name="update-notifications"></a>Powiadomienia o aktualizacjach

Aby otrzymywać powiadomienia e-mail po opublikowaniu zmian adresów IP i adresów URL w usłudze sieci Web, możesz użyć kilku różnych metod.

- Aby skorzystać z Power Automate, zobacz [Otrzymywanie wiadomości e-Power Automate](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651) e-mail ze zmianami w adresach IP i Office 365 URL.
- Aby wdrożyć aplikację Azure Logic przy użyciu szablonu ARM, zobacz Office 365 [powiadomienia o aktualizacji (wersja 1.1)](https://aka.ms/ipurlws-updates-template).
- Aby napisać własny skrypt powiadomień przy użyciu programu PowerShell, zobacz [Send-MailMessage](/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>Eksportowanie pliku PAC serwera proxy

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) to skrypt programu PowerShell, który odczytuje najnowsze punkty końcowe sieci z usługi sieci web programu Office 365 i adresu IP oraz tworzy przykładowy plik PAC. Aby uzyskać informacje na temat korzystania z pliku Get-PacFile, zobacz Używanie pliku PAC do bezpośredniego routingu najważniejszych Office 365 [ruchu](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>Tematy pokrewne
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Zarządzanie Office 365 punktami końcowymi](managing-office-365-endpoints.md)
  
[Office 365 punkty końcowe — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 zasad łączności sieciowej](microsoft-365-network-connectivity-principles.md)

[Office 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

[Ocena Office 365 sieci](assessing-network-connectivity.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością Office 365](performance-troubleshooting-plan.md)
