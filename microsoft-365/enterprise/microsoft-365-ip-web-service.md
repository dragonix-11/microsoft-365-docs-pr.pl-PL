---
title: Office 365 usługi sieci Web adresów IP i adresów URL
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Dowiedz się, jak używać usługi internetowej Office 365 adresów IP i adresów URL, aby lepiej identyfikować i rozróżniać ruch sieciowy Office 365.
ms.openlocfilehash: b13377c6230c869231b7cecda8375f663cbcd33b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100638"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 usługi sieci Web adresów IP i adresów URL

Usługa internetowa adresów IP i adresów URL Office 365 pomaga lepiej identyfikować i rozróżniać ruch sieciowy Office 365, ułatwiając ocenę, konfigurowanie i aktualizowanie zmian. Ta oparta na protokole REST usługa internetowa zastępuje poprzednie pliki do pobrania XML, które zostały wycofane 2 października 2018 r.

Jako klient lub dostawca urządzeń obwodowych sieci można utworzyć względem usługi internetowej, aby Office 365 adres IP i wpisy FQDN. Dostęp do danych można uzyskać bezpośrednio w przeglądarce internetowej przy użyciu następujących adresów URL:

- Aby uzyskać najnowszą wersję adresów URL Office 365 i zakresów adresów IP, użyj polecenia [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- W przypadku danych na stronie adresów URL Office 365 i zakresów adresów IP dla zapór i serwerów proxy użyj polecenia [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Aby uzyskać wszystkie najnowsze zmiany od lipca 2018 r., kiedy usługa internetowa była po raz pierwszy dostępna, użyj polecenia [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Jako klient możesz użyć tej usługi internetowej, aby:

- Zaktualizuj skrypty programu PowerShell, aby uzyskać Office 365 danych punktu końcowego i zmodyfikować dowolne formatowanie dla urządzeń sieciowych.
- Te informacje umożliwiają zaktualizowanie plików PAC wdrożonych na komputerach klienckich.

Jako dostawca urządzeń obwodowych sieci można użyć tej usługi internetowej do:

- Utwórz i przetestuj oprogramowanie urządzenia, aby pobrać listę na potrzeby zautomatyzowanej konfiguracji.
- Sprawdź bieżącą wersję.
- Pobierz bieżące zmiany.

> [!NOTE]
> Jeśli używasz usługi Azure ExpressRoute do nawiązywania połączenia z Office 365, przejrzyj usługę [Azure ExpressRoute, aby uzyskać Office 365](azure-expressroute.md), aby zapoznać się z usługami Office 365 obsługiwanymi przez usługę Azure ExpressRoute. Zapoznaj się również z artykułem [Office 365 adresów URL i zakresów adresów IP](urls-and-ip-address-ranges.md), aby dowiedzieć się, które żądania sieciowe dla aplikacji Office 365 wymagają łączności z Internetem. Pomoże to lepiej skonfigurować urządzenia zabezpieczeń obwodowych.

Więcej informacji można znaleźć w następujących artykułach:

- [Wpis w blogu z ogłoszeniem na forum Office 365 Tech Community](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 Tech Community Forum dotyczące pytań dotyczących korzystania z usług internetowych](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Typowe parametry

Te parametry są typowe we wszystkich metodach usługi internetowej:

- **format=\<JSON \| CSV\>** — Domyślnie zwracany format danych to JSON. Użyj tego opcjonalnego parametru, aby zwrócić dane w formacie wartości rozdzielanych przecinkami (CSV).
- **ClientRequestId=\<guid\>** — wymagany identyfikator GUID generowany na potrzeby skojarzenia klienta. Wygeneruj unikatowy identyfikator GUID dla każdej maszyny, która wywołuje usługę internetową (skrypty zawarte na tej stronie generują identyfikator GUID). Nie używaj identyfikatorów GUID przedstawionych w poniższych przykładach, ponieważ mogą one zostać zablokowane przez usługę internetową w przyszłości. Format guid to _xxxxxxxx-xxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, gdzie x reprezentuje numer szesnastkowy.

  Aby wygenerować identyfikator GUID, możesz użyć polecenia [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) programu PowerShell lub użyć usługi online, takiej jak [generator identyfikatorów GUID online](https://www.guidgenerator.com/).

## <a name="version-web-method"></a>Metoda internetowa wersji

Firma Microsoft aktualizuje Office 365 adres IP i wpisy nazwY FQDN na początku każdego miesiąca. Aktualizacje poza pasmem są czasami publikowane z powodu zdarzeń pomocy technicznej, aktualizacji zabezpieczeń lub innych wymagań operacyjnych.

Dane dla każdego opublikowanego wystąpienia mają przypisany numer wersji, a metoda internetowa wersji umożliwia sprawdzenie najnowszej wersji każdego wystąpienia usługi Office 365. Zalecamy sprawdzenie wersji nie więcej niż raz na godzinę.

Parametry dla metody internetowej wersji to:

- **AllVersions=\<true \| false\>** — Domyślnie zwrócona wersja jest najnowsza. Dołącz ten opcjonalny parametr, aby zażądać wszystkich opublikowanych wersji od czasu pierwszego wydania usługi internetowej.
- **Format=\<JSON \| CSV \| RSS\>** — Oprócz formatów JSON i CSV metoda internetowa wersji obsługuje również usługę RSS. Możesz użyć tego opcjonalnego parametru wraz z parametrem _AllVersions=true_, aby zażądać kanału informacyjnego RSS, który może być używany z Outlook lub innymi czytnikami RSS.
- **Wystąpienie=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** — Ten opcjonalny parametr określa wystąpienie, dla które ma zostać zwrócona wersja. Jeśli zostaną pominięte, zostaną zwrócone wszystkie wystąpienia. Prawidłowe wystąpienia to: Worldwide, China, USGovDoD, USGovGCCHigh.

Metoda sieci Web w wersji nie jest ograniczona szybkością i nigdy nie zwraca kodów odpowiedzi HTTP 429. Odpowiedź na wersję metody internetowej zawiera nagłówek cache-control zalecający buforowanie danych przez 1 godzinę. Wynikiem metody internetowej wersji może być pojedynczy rekord lub tablica rekordów. Elementy każdego rekordu to:

- instance — krótka nazwa wystąpienia usługi Office 365.
- latest — najnowsza wersja dla punktów końcowych określonego wystąpienia.
- versions — lista wszystkich poprzednich wersji dla określonego wystąpienia. Ten element jest uwzględniany tylko wtedy, gdy parametr _AllVersions_ ma wartość true.

### <a name="version-web-method-examples"></a>Przykłady metod internetowych wersji

Przykład 1 identyfikator URI żądania: <https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten identyfikator URI zwraca najnowszą wersję każdego wystąpienia usługi Office 365. Przykładowy wynik:

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
> Identyfikator GUID parametru ClientRequestID w tych identyfikatorach URI jest tylko przykładem. Aby wypróbować identyfikatory URI usługi internetowej, wygeneruj własny identyfikator GUID. Identyfikatory GUID wyświetlane w tych przykładach mogą zostać w przyszłości zablokowane przez usługę internetową.

Przykład 2 identyfikatora URI żądania: <https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten identyfikator URI zwraca najnowszą wersję określonego wystąpienia usługi Office 365. Przykładowy wynik:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

Przykładowy identyfikator URI żądania 3: <https://endpoints.office.com/version/Worldwide?Format=CSV&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten identyfikator URI pokazuje dane wyjściowe w formacie CSV. Przykładowy wynik:

```csv
instance,latest
Worldwide,2018063000
```

Przykładowy identyfikator URI żądania 4: <https://endpoints.office.com/version/Worldwide?AllVersions=true&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten identyfikator URI przedstawia wszystkie wcześniejsze wersje, które zostały opublikowane dla Office 365 wystąpienia usługi na całym świecie. Przykładowy wynik:

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

Przykład 5 identyfikatora URI źródła danych RSS: <https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS>

Ten identyfikator URI przedstawia kanał informacyjny RSS opublikowanych wersji zawierający linki do listy zmian dla każdej wersji. Przykładowy wynik:

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

## <a name="endpoints-web-method"></a>Metoda internetowa punktów końcowych

Metoda internetowa punktów końcowych zwraca wszystkie rekordy dla zakresów adresów IP i adresów URL, które tworzą usługę Office 365. Najnowsze dane z metody internetowej punktów końcowych powinny być zawsze używane do konfiguracji urządzeń sieciowych. Firma Microsoft zapewnia powiadomienie z wyprzedzeniem na 30 dni przed opublikowaniem nowych dodatków, aby dać Ci czas na zaktualizowanie list kontroli dostępu i list obejścia serwera proxy. Zalecamy ponowne wywołanie metody sieci Web punktów końcowych tylko wtedy, gdy metoda internetowa wersji wskazuje, że jest dostępna nowa wersja danych.

Parametry metody internetowej punktów końcowych to:

- **ServiceAreas=\<Common \| Exchange \| SharePoint \| Skype\>** —Rozdzielana przecinkami lista obszarów usług. Prawidłowe elementy to _Common_, _Exchange_, _SharePoint_ i _Skype_. Ponieważ _typowe_ elementy obszaru usługi są wymaganiami wstępnymi dla wszystkich innych obszarów usług, usługa internetowa zawsze je zawiera. Jeśli ten parametr nie zostanie dołączony, zostaną zwrócone wszystkie obszary usługi.
- **TenantName=\<tenant_name\>** — Nazwa dzierżawy Office 365. Usługa internetowa przyjmuje podaną nazwę i wstawia ją w części adresów URL zawierających nazwę dzierżawy. Jeśli nie podasz nazwy dzierżawy, te części adresów URL mają symbol wieloznaczny (\*).
- **NoIPv6=\<true \| false\>** — Ustaw wartość _true_ , aby wykluczyć adresy IPv6 z danych wyjściowych, jeśli nie używasz protokołu IPv6 w sieci.
- **Wystąpienie=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** — Ten wymagany parametr określa wystąpienie, z którego mają zostać zwrócone punkty końcowe. Prawidłowe wystąpienia to: _Worldwide_, _China_, _USGovDoD_ i _USGovGCCHigh_.

Jeśli wywołasz metodę internetową punktów końcowych zbyt wiele razy z tego samego adresu IP klienta, może zostać wyświetlony kod odpowiedzi HTTP _429 (zbyt wiele żądań)_. Jeśli otrzymasz ten kod odpowiedzi, poczekaj 1 godzinę przed powtórzeniem żądania lub wygeneruj nowy identyfikator GUID dla żądania. Ogólnie rzecz biorąc, najlepszym rozwiązaniem jest wywołanie metody sieci Web punktów końcowych tylko wtedy, gdy metoda internetowa wersji wskazuje, że jest dostępna nowa wersja.

Wynikiem metody internetowej punktów końcowych jest tablica rekordów, w której każdy rekord reprezentuje określony zestaw punktów końcowych. Elementy dla każdego rekordu to:

- id — niezmienny numer identyfikatora zestawu punktów końcowych.
- serviceArea — obszar usługi, który jest częścią: _Common_, _Exchange_, _SharePoint_ lub _Skype_.
- urls — adresy URL zestawu punktów końcowych. Tablica JSON rekordów DNS. Pominięto, jeśli jest puste.
- tcpPorts — porty TCP dla zestawu punktów końcowych. Wszystkie elementy portów są sformatowane jako rozdzielana przecinkami lista portów lub zakresów portów oddzielonych znakiem kreski (-). Porty mają zastosowanie do wszystkich adresów IP i wszystkich adresów URL w punkcie końcowym ustawionym dla danej kategorii. Pominięto, jeśli jest puste.
- udpPorts — porty UDP dla zakresów adresów IP w tym zestawie punktów końcowych. Pominięto, jeśli jest puste.
- ips — zakresy adresów IP skojarzone z tym punktem końcowym ustawione jako skojarzone z wymienionymi portami TCP lub UDP. Tablica JSON zakresów adresów IP. Pominięto, jeśli jest puste.
- category — kategoria łączności dla zestawu punktów końcowych. Prawidłowe wartości to _Optymalizowanie_, _Zezwalaj_ i _Domyślne_. Jeśli wyszukasz dane wyjściowe metody internetowej punktów końcowych dla kategorii określonego adresu IP lub adresu URL, możliwe, że zapytanie zwróci wiele kategorii. W takim przypadku postępuj zgodnie z zaleceniem dla kategorii o najwyższym priorytecie. Jeśli na przykład punkt końcowy jest wyświetlany zarówno w _obszarze Optymalizuj_ , jak i _Zezwalaj_, należy postępować zgodnie z wymaganiami _dotyczącymi optymalizacji_. Wymagane.
- expressRoute — _prawda_ , jeśli ten zestaw punktów końcowych jest kierowany przez usługę ExpressRoute, _fałsz_ , jeśli nie.
- required — _wartość True_, jeśli ten zestaw punktów końcowych jest wymagany do zapewnienia łączności, aby Office 365 była obsługiwana. _Fałsz_ , jeśli ten zestaw punktów końcowych jest opcjonalny.
- uwagi — w przypadku opcjonalnych punktów końcowych w tym tekście opisano Office 365 funkcji, które byłyby niedostępne, jeśli adresy IP lub adresy URL w tym zestawie punktów końcowych nie będą dostępne w warstwie sieciowej. Pominięto, jeśli jest puste.

### <a name="endpoints-web-method-examples"></a>Przykłady metod internetowych punktów końcowych

Przykład 1 identyfikator URI żądania: <https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Ten identyfikator URI uzyskuje wszystkie punkty końcowe dla wystąpienia Office 365 na całym świecie dla wszystkich obciążeń. Przykładowy wynik pokazujący fragment danych wyjściowych:

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

Przykład 2 identyfikator URI żądania: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp; ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

W tym przykładzie uzyskuje punkty końcowe dla wystąpienia Office 365 Worldwide tylko dla Exchange Online i zależności.

Dane wyjściowe, na przykład 2, są podobne do przykładu 1, z tą różnicą, że wyniki nie obejmują punktów końcowych dla SharePoint Online lub Skype dla firm Online.

## <a name="changes-web-method"></a>Zmienia metodę internetową

Metoda sieci Web zmiany zwraca najnowsze aktualizacje, które zostały opublikowane, zazwyczaj w poprzednim miesiącu zmiany zakresów adresów IP i adresów URL.

Najważniejsze zmiany w danych punktów końcowych to nowe adresy URL i adresy IP. Nie można dodać adresu IP do listy kontroli dostępu zapory lub adresu URL do listy obejść serwera proxy może spowodować awarię dla Office 365 użytkowników za tym urządzeniem sieciowym. Niezależnie od wymagań operacyjnych nowe punkty końcowe są publikowane w usłudze internetowej z 30-dniowym wyprzedzeniem od daty aprowizowania punktów końcowych do użycia, aby dać ci czas na zaktualizowanie list kontroli dostępu i list obejścia serwera proxy.

Wymaganym parametrem dla metody internetowej zmian jest:

- **Wersja=\<YYYYMMDDNN>** —Wymagany parametr trasy adresu URL. Ta wartość jest wersją, która została obecnie zaimplementowana. Usługa internetowa zwróci zmiany od tej wersji. Format to _RRRRMMDDNN_, gdzie _NN_ jest liczbą naturalną zwiększaną, jeśli istnieje wiele wersji wymaganych do opublikowania w ciągu jednego dnia, a _00_ reprezentuje pierwszą aktualizację dla danego dnia. Usługa internetowa wymaga, aby parametr _wersji_ zawierał dokładnie 10 cyfr.

Metoda internetowa zmian jest ograniczona szybkością w taki sam sposób jak metoda internetowa punktów końcowych. Jeśli otrzymasz kod odpowiedzi HTTP 429, poczekaj 1 godzinę przed powtórzeniem żądania lub wygeneruj nowy identyfikator GUID dla żądania.

Wynikiem zmiany metody internetowej jest tablica rekordów, w których każdy rekord reprezentuje zmianę w określonej wersji punktów końcowych. Elementy dla każdego rekordu to:

- id — niezmienny identyfikator rekordu zmiany.
- endpointSetId — identyfikator rekordu zestawu punktów końcowych, który został zmieniony.
- disposition — opisuje zmiany w rekordzie zestawu punktów końcowych. Wartości są _zmieniane_, _dodawane_ lub _usuwane_.
- impact — nie wszystkie zmiany będą równie ważne dla każdego środowiska. W tym elemencie opisano oczekiwany wpływ tej zmiany na środowisko obwodowe sieci przedsiębiorstwa. Ten element jest uwzględniany tylko w rekordach zmian wersji **2018112800** i nowszych. Dostępne są następujące opcje: — AddedIp — adres IP został dodany do Office 365 i wkrótce będzie aktywny w usłudze. Oznacza to zmianę, którą należy włączyć na zaporze lub innym urządzeniu obwodowym sieci warstwy 3. Jeśli nie dodasz tego przed rozpoczęciem korzystania z niego, może wystąpić awaria.
  — AddedUrl — adres URL został dodany do Office 365 i wkrótce będzie aktywny w usłudze. Oznacza to zmianę, którą należy włączyć na serwerze proxy lub adresie URL analizowania sieciowego urządzenia obwodowego. Jeśli nie dodasz tego adresu URL przed rozpoczęciem korzystania z niego, może wystąpić awaria.
  — AddedIpAndUrl — dodano zarówno adres IP, jak i adres URL. Oznacza to zmianę, którą należy włączyć na urządzeniu warstwy zapory 3, serwerze proxy lub urządzeniu analizy adresów URL. Jeśli ta para adresów IP/ADRES URL nie zostanie dodana przed rozpoczęciem korzystania z niej, może wystąpić awaria.
  — RemovedIpOrUrl — co najmniej jeden adres IP lub adres URL został usunięty z Office 365. Usuń punkty końcowe sieci z urządzeń obwodowych, ale nie ma terminu, aby to zrobić.
  — ChangedIsExpressRoute — atrybut obsługi usługi ExpressRoute został zmieniony. Jeśli używasz usługi ExpressRoute, może być konieczne podjęcie akcji w zależności od konfiguracji.
  — MovedIpOrUrl — przenieśliśmy adres IP lub adres URL między tym zestawem punktów końcowych a innym. Zazwyczaj nie jest wymagana żadna akcja.
  — RemovedDuplicateIpOrUrl — usunęliśmy zduplikowany adres IP lub adres URL, ale jest on nadal publikowany dla Office 365. Zazwyczaj nie jest wymagana żadna akcja.
  — OtherNonPriorityChanges — zmieniliśmy coś mniej krytycznego niż wszystkie inne opcje, takie jak zawartość pola notatki.
- version — wersja opublikowanego zestawu punktów końcowych, w którym wprowadzono zmianę. Numery wersji mają format _YYYYMMDDNN_, gdzie _NN_ jest liczbą naturalną zwiększaną, jeśli istnieje wiele wersji wymaganych do opublikowania w ciągu jednego dnia.
- previous — podstruktura zawierająca szczegóły poprzednich wartości zmienionych elementów w zestawie punktów końcowych. Nie zostanie on uwzględniony w nowo dodanych zestawach punktów końcowych. Obejmuje  _usługi ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ i _notesy_.
- current — podstruktura zawierająca szczegółowe informacje o zaktualizowanych wartościach elementów zmian w zestawie punktów końcowych. Obejmuje _usługi ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_ i _notesy_.
- add — podstruktura zawierająca szczegóły elementów, które mają zostać dodane do kolekcji zestawów punktów końcowych. Pominięto, jeśli nie ma żadnych dodatków.
  — effectiveDate — definiuje dane, gdy dodatki będą aktywne w usłudze.
  — adresy IP — elementy, które mają zostać dodane do tablicy _adresów ips_ .
  — adresy URL — elementy, które mają zostać dodane do _tablicy adresów URL_ .
- remove — podstruktura zawierająca szczegóły elementów do usunięcia z zestawu punktów końcowych. Pominięto, jeśli nie ma żadnych przeprowadzek.
  — adresy IP — elementy, które mają zostać usunięte z tablicy _adresów ips_ .
  — adresy URL — elementy do usunięcia z _tablicy adresów URL_ .

### <a name="changes-web-method-examples"></a>Zmienia przykłady metod internetowych

Przykład 1 identyfikator URI żądania: <https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

Spowoduje to zażądanie wszystkich wcześniejszych zmian w wystąpieniu usługi Office 365 na całym świecie. Przykładowy wynik:

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

Przykład 2 identyfikatora URI żądania: <https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

To żądanie zmienia się od określonej wersji wystąpienia Office 365 Worldwide. W tym przypadku określona wersja jest najnowsza. Przykładowy wynik:

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

Możesz uruchomić ten skrypt programu PowerShell, aby sprawdzić, czy istnieją akcje, które należy wykonać w celu zaktualizowania danych. Ten skrypt można uruchomić jako zaplanowane zadanie, aby sprawdzić aktualizację wersji. Aby uniknąć nadmiernego obciążenia usługi internetowej, spróbuj nie uruchamiać skryptu więcej niż raz na godzinę.

Skrypt wykonuje następujące czynności:

- Sprawdza numer wersji bieżących punktów końcowych wystąpienia Office 365 Worldwide, wywołując interfejs API REST usługi internetowej.
- Sprawdza, czy plik bieżącej wersji ma _wartość $Env:TEMP\O365_endpoints_latestversion.txt_. Ścieżka zmiennej globalnej **$Env:TEMP** to zazwyczaj _C:\Users\\<username\>\AppData\Local\Temp_.
- Jeśli skrypt jest uruchamiany po raz pierwszy, skrypt zwraca bieżącą wersję oraz wszystkie bieżące adresy IP i adresy URL, zapisuje wersję punktów końcowych w pliku _$Env:TEMP\O365_endpoints_latestversion.txt_ , a dane wyjściowe punktów końcowych do pliku _$Env:TEMP\O365_endpoints_data.txt_. Ścieżkę i/lub nazwę pliku wyjściowego można zmodyfikować, edytując następujące wiersze:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- Przy każdym kolejnym wykonaniu skryptu, jeśli najnowsza wersja usługi internetowej jest identyczna z wersją w pliku _O365_endpoints_latestversion.txt_ , skrypt kończy działanie bez wprowadzania żadnych zmian.
- Gdy najnowsza wersja usługi internetowej jest nowsza niż wersja w pliku _O365_endpoints_latestversion.txt_ , skrypt zwraca punkty końcowe i filtry dla punktów końcowych kategorii **Zezwalaj** i **optymalizuj, aktualizuje** wersję w pliku _O365_endpoints_latestversion.txt_ i zapisuje zaktualizowane dane w pliku _O365_endpoints_data.txt_ .

Skrypt generuje unikatowy identyfikator _ClientRequestId_ dla komputera, na który jest wykonywany, i ponownie używa tego identyfikatora w wielu wywołaniach. Ten identyfikator jest przechowywany w pliku _O365_endpoints_latestversion.txt_ .

### <a name="to-run-the-powershell-script"></a>Aby uruchomić skrypt programu PowerShell

1. Skopiuj skrypt i zapisz go na lokalnym dysku twardym lub w lokalizacji skryptu jako _Get-O365WebServiceUpdates.ps1_.
1. Wykonaj skrypt w preferowanym edytorze skryptów, takim jak PowerShell ISE lub VS Code, lub z konsoli programu PowerShell przy użyciu następującego polecenia:

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

Oto skrypt języka Python przetestowany w języku Python 3.6.3 na Windows 10, który można uruchomić, aby sprawdzić, czy istnieją akcje, które należy wykonać w celu zaktualizowania danych. Ten skrypt sprawdza numer wersji punktów końcowych wystąpienia Office 365 Worldwide. W przypadku zmiany pobiera ona punkty końcowe i filtry dla punktów końcowych kategorii _Zezwalaj_ i _optymalizuj_ . Używa również unikatowego identyfikatora ClientRequestId w wielu wywołaniach i zapisuje najnowszą wersję znalezioną w pliku tymczasowym. Wywołaj ten skrypt raz na godzinę, aby sprawdzić aktualizację wersji.

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

## <a name="web-service-interface-versioning"></a>Przechowywanie wersji interfejsu usługi internetowej

Aktualizacje parametrów lub wyników dla tych metod usługi internetowej mogą być wymagane w przyszłości. Po opublikowaniu ogólnej wersji dostępności tych usług internetowych firma Microsoft dołoży rozsądnych starań, aby powiadomić o istotnych aktualizacjach usługi internetowej z wyprzedzeniem. Gdy firma Microsoft uzna, że aktualizacja będzie wymagać zmian klientów korzystających z usługi internetowej, firma Microsoft zachowa poprzednią wersję (jedną wersję z powrotem) usługi internetowej dostępną przez co najmniej 12 miesięcy po wydaniu nowej wersji. Klienci, którzy nie uaktualnili w tym czasie, mogą nie mieć dostępu do usługi internetowej i jej metod. Klienci muszą upewnić się, że klienci usługi internetowej kontynuują pracę bez błędu, jeśli wprowadzono następujące zmiany w sygnaturze interfejsu usługi internetowej:

- Dodanie nowego parametru opcjonalnego do istniejącej metody internetowej, która nie musi być udostępniana przez starszych klientów i nie ma wpływu na wynik, jaki otrzymuje starszy klient.
- Dodawanie nowego nazwanego atrybutu w jednym z elementów REST odpowiedzi lub innych kolumn do pliku CSV odpowiedzi.
- Dodawanie nowej metody internetowej o nowej nazwie, która nie jest wywoływana przez starszych klientów.

## <a name="update-notifications"></a>Aktualizowanie powiadomień

Możesz użyć kilku różnych metod, aby otrzymywać powiadomienia e-mail, gdy zmiany adresów IP i adresów URL są publikowane w usłudze internetowej.

- Aby użyć rozwiązania Power Automate, zobacz [Używanie Power Automate do odbierania wiadomości e-mail w celu wprowadzenia zmian Office 365 adresów IP i adresów URL](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- Aby wdrożyć aplikację logiki platformy Azure przy użyciu szablonu usługi ARM, zobacz [Office 365 Update Notification (wersja 1.1)](https://aka.ms/ipurlws-updates-template).
- Aby napisać własny skrypt powiadomień przy użyciu programu PowerShell, zobacz [Send-MailMessage](/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>Eksportowanie pliku PAC serwera proxy

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) to skrypt programu PowerShell, który odczytuje najnowsze punkty końcowe sieci z usługi internetowej adresów IP i adresów URL Office 365 oraz tworzy przykładowy plik PAC. Aby uzyskać informacje na temat korzystania z pliku Get-PacFile, zobacz [Używanie pliku PAC do bezpośredniego routingu istotnego ruchu Office 365](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>Tematy pokrewne
  
[Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md)
  
[Office 365 punktów końcowych — często zadawane pytania](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[zasady łączności sieciowej Office 365](microsoft-365-network-connectivity-principles.md)

[Office 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)

[Ocena łączności sieciowej Office 365](assessing-network-connectivity.md)
  
[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optymalizowanie sieci pod kątem Skype dla firm Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)
  
[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)
