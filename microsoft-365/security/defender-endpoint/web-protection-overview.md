---
title: Ochrona sieci Web
description: Dowiedz się więcej o ochronie sieci Web w programie Microsoft Defender dla punktu końcowego i o tym, jak może chronić Twoją organizację
keywords: ochrona sieci Web, ochrona przed zagrożeniami w sieci Web, przeglądanie Internetu, zabezpieczenia, wyłudzanie informacji, złośliwe oprogramowanie, exploit, witryny internetowe, ochrona sieci, Edge, Internet Explorer, Chrome, Firefox, przeglądarka internetowa, złośliwe witryny internetowe
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d21fdd481ade59ca869d5cfe086e537c0c431228
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013288"
---
# <a name="web-protection"></a>Ochrona sieci Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>Informacje o ochronie sieci Web

Ochrona sieci Web w programie Microsoft Defender for Endpoint to funkcja, która składa się z funkcji ochrony przed zagrożeniami internetowymi [,](web-threat-protection.md) filtrowania zawartości sieci [Web](web-content-filtering.md) i [wskaźników niestandardowych](manage-indicators.md). Ochrona sieci Web umożliwia zabezpieczanie urządzeń przed zagrożeniami internetowymi i pomaga regulować niechcianą zawartość. Raporty dotyczące ochrony sieci Web można znaleźć w portalu Microsoft 365 Defender sieci Web, przechodząc do strony Raporty **> sieci Web**.

:::image type="content" alt-text="Obraz wszystkich kart ochrony sieci Web." source="images/web-protection.png" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Ochrona przed zagrożeniami internetowymi

Karty, które chronią przed zagrożeniami internetowymi, to wykrywanie zagrożeń internetowych **w** czasie i **podsumowanie zagrożeń internetowych**.

Ochrona przed zagrożeniami internetowymi obejmuje:

- Pełna widoczność zagrożeń w sieci Web mających wpływ na twoją organizację.
- Możliwości analizy aktywności związanej z zagrożeniami w sieci Web za pośrednictwem alertów i kompleksowych profilów adresów URL oraz urządzeń, które mają dostęp do tych adresów URL.
- Pełny zestaw funkcji zabezpieczeń, które śledzą ogólne trendy dostępu do złośliwych i niechcianych witryn internetowych.

Aby uzyskać więcej informacji, zobacz [Ochrona przed zagrożeniami w sieci Web](web-threat-protection.md).

### <a name="custom-indicators"></a>Wskaźniki niestandardowe

Wykrywanie wskaźników niestandardowych jest również podsumowywane w raportach organizacji dotyczących zagrożeń sieci **Web** w obszarze wykrywania zagrożeń internetowych w czasie i podsumowania **zagrożeń internetowych**.

Wskaźnik niestandardowy zawiera:

- Możliwość tworzenia wskaźników adresów IP i opartych na adresach URL w celu ochrony organizacji przed zagrożeniami.
- Przeszukaj możliwości związane z działaniami związanymi z niestandardowymi profilami adresów IP/URL i urządzeniami, które mają dostęp do tych adresów URL.
- Możliwość tworzenia zasad Zezwalaj, Blokuj i Ostrzegaj dla adresów IP i adresów URL.

Aby uzyskać więcej informacji, [zobacz Tworzenie wskaźników adresów IP i adresów URL/domen.](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Filtrowanie zawartości sieci Web

Filtrowanie zawartości sieci **Web obejmuje działania w sieci Web według kategorii**, podsumowanie **filtrowania zawartości sieci Web** i **podsumowanie aktywności w sieci Web**.

Filtrowanie zawartości sieci Web obejmuje:

- Użytkownicy nie mogą uzyskać dostępu do witryn internetowych w kategoriach zablokowanych, niezależnie od tego, czy przeglądają witryny lokalne, czy z dala od sieci.
- Możesz wygodnie wdrażać różne zasady dla różnych zestawów użytkowników przy użyciu grup urządzeń zdefiniowanych w ustawieniach kontroli dostępu opartych na rolach programu [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/rbac).
- Możesz uzyskać dostęp do raportów sieci Web w tej samej centralnej lokalizacji, dzięki widoczności na rzeczywistych blokach i użyciu sieci Web.

Aby uzyskać więcej informacji, zobacz [Filtrowanie zawartości sieci Web](web-content-filtering.md).

## <a name="order-of-precedence"></a>Kolejność pierwszeństwa

Ochrona sieci Web składa się z następujących składników wymienionych w kolejności pierwszeństwa. Każdy z tych składników jest wymuszany przez klienta SmartScreen w programie Microsoft Edge i przez klienta ochrony sieci we wszystkich innych procesach i przeglądarkach.

- Wskaźniki niestandardowe (adresy IP/URL, zasady programu Microsoft Defender dla aplikacji w chmurze)
  - Zezwalaj
  - Ostrzegaj
  - Blokuj

- Zagrożenia internetowe (złośliwe oprogramowanie, wyłudzy)
  - SmartScreen Intel, w tym Exchange Online Protection (EOP)
  - Eskalacji

- Filtrowanie zawartości sieci Web (WCF)

> [!NOTE]
> Program Microsoft Defender for Cloud Apps obecnie generuje wskaźniki tylko dla zablokowanych adresów URL.

Kolejność pierwszeństwa odnosi się do kolejności operacji, według której jest szacowany adres URL lub ADRES IP. Na przykład jeśli masz zasady filtrowania zawartości sieci Web, możesz tworzyć wykluczenia za pomocą niestandardowych wskaźników adresów IP/URL. Niestandardowe wskaźniki naruszenia zabezpieczeń (IoC) są wyżej uporządkowane w kolejności pierwszeństwa niż bloki WCF.

Podobnie w przypadku konfliktu między wskaźnikami zawsze mają pierwszeństwo przed blokami (zastępuje logikę). Oznacza to, że nad dowolnym wskaźnikiem blokowania, który istnieje, zostanie nadwyrężyć wskaźnik zezwalania.

W poniższej tabeli zestawiliśmy niektóre typowe konfiguracje, które mogą prezentować konflikty w stosie ochrony sieci Web. Określa także wynikowe wyznaczanie na podstawie pierwszeństwa wymienionego powyżej.

<br>

****

|Zasady dotyczące wskaźników niestandardowych|Zasady dotyczące zagrożeń w sieci Web|Zasady WCF|Zasady usługi Defender dla aplikacji w chmurze|Result (Wynik)|
|---|---|---|---|---|
|Zezwalaj|Blokuj|Blokuj|Blokuj|Zezwalaj (zastępowanie ochrony sieci Web)|
|Zezwalaj|Zezwalaj|Blokuj|Blokuj|Allow (wyjątek WCF)|
|Ostrzegaj|Blokuj|Blokuj|Blokuj|Ostrzeganie (zastępowanie)|
|

Wewnętrzne adresy IP nie są obsługiwane przez wskaźniki niestandardowe. W przypadku zasad ostrzegawczych pomijanych przez użytkownika końcowego witryna będzie domyślnie odblokowana przez 24 godziny dla tego użytkownika. Ten okres może zostać zmodyfikowany przez administratora i przekazany przez usługę w chmurze SmartScreen. Możliwość pomijania ostrzeżenia można również wyłączyć w programie Microsoft Edge CSP w przypadku bloków zagrożeń sieci Web (złośliwe oprogramowanie/wyłudzanie informacji). Aby uzyskać więcej informacji, zobacz [Microsoft Edge Filtr SmartScreen Ustawienia](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Ochrona przeglądarek

We wszystkich scenariuszach ochrony sieci Web filtr SmartScreen i ochrona sieci mogą być używane razem w celu zapewnienia ochrony zarówno w przeglądarkach i procesach pierwszej firmy, jak i przez inne firmy. Filtr SmartScreen jest wbudowany bezpośrednio Microsoft Edge sieci, natomiast ochrona sieci monitoruje ruch w przeglądarkach i procesach innych firm. Na poniższym diagramie przedstawiono to pojęcie. Ten diagram przedstawiający dwóch klientów pracujących razem w celu zapewnienia wielu zakresów przeglądarek i aplikacji jest dokładny dla wszystkich funkcji ochrony sieci Web (wskaźniki, zagrożenia sieci Web, filtrowanie zawartości).

:::image type="content" alt-text="Używanie filtru SmartScreen i ochrony sieci jednocześnie." source="../../media/web-protection-protect-browsers.png" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Rozwiązywanie problemów z blokami punktów końcowych

Odpowiedzi z chmury SmartScreen są znormalizowane. Narzędzia, takie jak Fiddler, mogą być używane do sprawdzania odpowiedzi z usługi w chmurze, co pomoże ustalić źródło bloku.

Gdy usługa w chmurze SmartScreen odpowiada z zezwalaniem, blokowaniem lub ostrzeganiem, kategoria odpowiedzi i kontekst serwera są ponownie przekazywane do klienta. W Microsoft Edge kategoria odpowiedzi służy do określania odpowiedniej strony blokady do pokazania (złośliwej, wyłudzania informacji, zasad organizacyjnych).

W poniższej tabeli przedstawiono odpowiedzi i ich skorelowane funkcje.

<br>

****

|ResponseCategory|Funkcja odpowiedzialna za blok|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|Wskaźniki niestandardowe|
|CasbPolicy|Defender for Cloud Apps|
|Złośliwy|Zagrożenia w sieci Web|
|Wyłudzanie informacji|Zagrożenia w sieci Web|
|||

## <a name="advanced-hunting-for-web-protection"></a>Zaawansowane szukanie ochrony w sieci Web

Za pomocą zapytań Kusto podczas zaawansowanego wyszukiwania można podsumowywane bloki ochrony sieci Web w organizacji na maksymalnie 30 dni. Te zapytania używają podanych powyżej informacji do odróżniania różnych źródeł bloków i podsumowywania ich w sposób przyjazny dla użytkownika. Na przykład poniższe zapytanie zawiera listę wszystkich bloków pliku WCF pochodzących Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomBlockList"
```

Podobnie możesz użyć poniższego zapytania, aby wyświetlić listę wszystkich bloków pliku WCF pochodzących z usługi Network Protection (na przykład bloku usługi WCF w przeglądarce innej firmy). Pamiętaj, że działanie ActionType zostało zaktualizowane, a środowisko "Środowisko" zostało zmienione na "ResponseCategory".

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Aby wyświetlić listę bloków danych spowodowanych innymi funkcjami (na przykład wskaźnikami niestandardowymi), należy zapoznać się z tabelą powyżej z wykazem poszczególnych funkcji i odpowiednich kategorii odpowiedzi. Te zapytania mogą również zostać zmodyfikowane w celu wyszukania telemetrii powiązanej z określonymi komputerami w organizacji. Pamiętaj, że opcja ActionType (Typ Akcji) pokazana w każdym z powyższych zapytań będzie pokazywać tylko te połączenia, które zostały zablokowane przez funkcję Web Protection, a nie cały ruch sieciowy.

## <a name="user-experience"></a>Środowisko użytkownika

Jeśli użytkownik odwiedza stronę internetową, która stwarza ryzyko złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń, program Microsoft Edge wyzwoli stronę zablokowaną z informacją "Ta witryna została zgłoszone jako niebezpieczna" oraz informacjami o zagrożeniach.

> [!div class="mx-imgBorder"]
> ![Strona blokowana przez Microsoft Edge.](../../media/web-protection-malicious-block.png)

Jeśli jest blokowana przez witrynę WCF lub wskaźnik niestandardowy, na stronie blokady jest Microsoft Edge, który informuje użytkownika o zablokowaniu tej witryny przez jego organizację.

> [!div class="mx-imgBorder"]
> ![Strona zablokowana przez Twoją organizację.](../../media/web-protection-indicator-blockpage.png)

W każdym przypadku w przeglądarkach innych firm nie są wyświetlane żadne blokowane strony, a użytkownik widzi stronę "Bezpieczne połączenie nie powiodło się" wraz z wyskakującego powiadomienia. W zależności od zasad odpowiedzialnych za zablokowanie w wyskakującego powiadomieniach użytkownik zobaczy inny komunikat. Na przykład filtrowanie zawartości sieci Web spowoduje wyświetlenie komunikatu "Ta zawartość jest zablokowana".

> [!div class="mx-imgBorder"]
> ![Strona zablokowana przez usługę WCF.](../../media/web-protection-np-block.png)

## <a name="report-false-positives"></a>Zgłaszanie wyników fałszywie dodatnich

Aby zgłosić wynik fałszywie dodatni dla witryn uznanych za niebezpieczne przez filtr SmartScreen, użyj linku wyświetlanego na stronie blokady w programie Microsoft Edge (jak pokazano powyżej).

W przypadku usługi WCF można spory dotyczące kategorii domeny. Przejdź do karty **Domeny** w raportach WCF, a następnie kliknij pozycję **Nieścisłości raportu**. Zostanie otwarte wysuw. Ustaw priorytet zdarzenia i podaj dodatkowe informacje, na przykład kategorię sugerowaną. Aby uzyskać więcej informacji na temat sposobu włączania usługi WCF i sposobu rozstrzygania sporów między [kategoriami, zobacz Filtrowanie zawartości sieci Web](web-content-filtering.md).

Aby uzyskać więcej informacji na temat przesyłania wyników fałszywie dodatnich/ujemnych, zobacz Adres wyników fałszywie dodatnich/ujemnych w programie [Microsoft Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md).

## <a name="related-information"></a>Informacje pokrewne

<br>

****

|Temat|Opis|
|---|---|
|[Ochrona przed zagrożeniami internetowymi](web-threat-protection.md) | Zatrzymywanie dostępu do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w witrynach, niezaufanych lub o niskiej reputacji oraz witryn, które zostały zablokowane.|
|[Filtrowanie zawartości sieci Web](web-content-filtering.md) | Śledź i wyreguluj dostęp do witryn internetowych na podstawie ich kategorii zawartości.|
|
