---
title: Ochrona sieci Web
description: Dowiedz się więcej na temat ochrony sieci Web w Ochrona punktu końcowego w usłudze Microsoft Defender i sposobu ochrony organizacji
keywords: ochrona sieci Web, ochrona przed zagrożeniami w Internecie, przeglądanie internetu, zabezpieczenia, wyłudzanie informacji, złośliwe oprogramowanie, luki w zabezpieczeniach, witryny internetowe, ochrona sieci, Przeglądarka Edge, Internet Explorer, Chrome, Firefox, przeglądarka internetowa, złośliwe witryny internetowe
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
ms.openlocfilehash: 4184948316e683a59b45b9397aaea74260e290ee
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664177"
---
# <a name="web-protection"></a>Ochrona sieci Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>Informacje o ochronie w Internecie

Ochrona sieci Web w Ochrona punktu końcowego w usłudze Microsoft Defender to funkcja, która składa się z [ochrony przed zagrożeniami w sieci Web](web-threat-protection.md), [filtrowania zawartości sieci Web](web-content-filtering.md) i [wskaźników niestandardowych](manage-indicators.md). Ochrona w Internecie pozwala zabezpieczyć urządzenia przed zagrożeniami internetowymi i pomaga regulować niechcianą zawartość. Raporty dotyczące ochrony sieci Web można znaleźć w portalu Microsoft 365 Defender, przechodząc do pozycji **Raporty > ochrony sieci Web**.

:::image type="content" source="images/web-protection.png" alt-text="Karty ochrony sieci Web" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Ochrona przed zagrożeniami sieci Web

Karty, które tworzą ochronę przed zagrożeniami **internetowymi, to wykrywanie zagrożeń internetowych w czasie** i **podsumowanie zagrożeń internetowych**.

Ochrona przed zagrożeniami internetowymi obejmuje:

- Kompleksowy wgląd w zagrożenia internetowe wpływające na organizację.
- Możliwości badania aktywności związanej z zagrożeniami w Internecie za pośrednictwem alertów i kompleksowych profilów adresów URL i urządzeń uzyskujących dostęp do tych adresów URL.
- Pełny zestaw funkcji zabezpieczeń, które śledzą ogólne trendy dostępu do złośliwych i niechcianych witryn internetowych.

Aby uzyskać więcej informacji, zobacz [Ochrona przed zagrożeniami w sieci Web](web-threat-protection.md).

### <a name="custom-indicators"></a>Wskaźniki niestandardowe

Wykrywanie niestandardowych wskaźników jest również podsumowane w raportach dotyczących zagrożeń internetowych organizacji w ramach **wykrywania zagrożeń internetowych w czasie** i **podsumowania zagrożeń internetowych**.

Wskaźnik niestandardowy obejmuje:

- Możliwość tworzenia wskaźników naruszenia zabezpieczeń opartych na adresach IP i adresach URL w celu ochrony organizacji przed zagrożeniami.
- Możliwości badania działań związanych z niestandardowymi profilami adresów IP/adresów URL oraz urządzeniami uzyskującymi dostęp do tych adresów URL.
- Możliwość tworzenia zasad Zezwalaj, Blokuj i Ostrzegaj dla adresów IP i adresów URL.

Aby uzyskać więcej informacji, zobacz [Tworzenie wskaźników dla adresów IP i adresów URL/domen](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Filtrowanie zawartości sieci Web

Filtrowanie zawartości sieci Web obejmuje **działanie sieci Web według kategorii**, **podsumowanie filtrowania zawartości sieci Web** i **podsumowanie działań sieci Web**.

Filtrowanie zawartości internetowej obejmuje:

- Użytkownicy nie mogą uzyskiwać dostępu do witryn internetowych w zablokowanych kategoriach, niezależnie od tego, czy przeglądają w środowisku lokalnym, czy poza siecią.
- Możesz wygodnie wdrażać różne zasady dla różnych zestawów użytkowników przy użyciu grup urządzeń zdefiniowanych w [Ochrona punktu końcowego w usłudze Microsoft Defender ustawień kontroli dostępu opartej na rolach](/microsoft-365/security/defender-endpoint/rbac).
- Możesz uzyskiwać dostęp do raportów internetowych w tej samej centralnej lokalizacji z widocznością rzeczywistych bloków i użycia sieci Web.

Aby uzyskać więcej informacji, zobacz [Filtrowanie zawartości sieci Web](web-content-filtering.md).

## <a name="order-of-precedence"></a>Kolejność pierwszeństwa

Ochrona sieci Web składa się z następujących składników wymienionych w kolejności pierwszeństwa. Każdy z tych składników jest wymuszany przez klienta SmartScreen w Microsoft Edge i przez klienta ochrony sieci we wszystkich innych przeglądarkach i procesach.

- Wskaźniki niestandardowe (ip/adres URL, zasady Microsoft Defender for Cloud Apps)
  - Zezwalaj
  - Ostrzec
  - Blokuj

- Zagrożenia internetowe (złośliwe oprogramowanie, phish)
  - SmartScreen Intel, w tym Exchange Online Protection (EOP)
  - Eskalacji

- Filtrowanie zawartości sieci Web (WCF)

> [!NOTE]
> Microsoft Defender for Cloud Apps obecnie generuje wskaźniki tylko dla zablokowanych adresów URL.

Kolejność pierwszeństwa odnosi się do kolejności operacji, według której oceniany jest adres URL lub adres IP. Jeśli na przykład masz zasady filtrowania zawartości internetowej, możesz tworzyć wykluczenia za pomocą niestandardowych wskaźników adresu IP/adresu URL. Niestandardowe wskaźniki naruszenia zabezpieczeń (IoC) są wyższe w kolejności pierwszeństwa niż bloki WCF.

Podobnie podczas konfliktu między wskaźnikami zezwala na pierwszeństwo przed blokami (zastąp logikę). Oznacza to, że wskaźnik zezwalania zdobędzie wszystkie obecne wskaźniki blokowe.

Poniższa tabela zawiera podsumowanie niektórych typowych konfiguracji, które powodują konflikty w stosie ochrony sieci Web. Identyfikuje również wynikowe ustalenia na podstawie powyższego pierwszeństwa.

<br>

****

|Niestandardowe zasady wskaźników|Zasady dotyczące zagrożeń internetowych|Zasady WCF|zasady aplikacji Defender dla Chmury|Result (Wynik)|
|---|---|---|---|---|
|Zezwalaj|Blokuj|Blokuj|Blokuj|Zezwalaj (przesłonięcia ochrony sieci Web)|
|Zezwalaj|Zezwalaj|Blokuj|Blokuj|Zezwalaj (wyjątek WCF)|
|Ostrzec|Blokuj|Blokuj|Blokuj|Ostrzegaj (przesłoń)|
|

Wewnętrzne adresy IP nie są obsługiwane przez wskaźniki niestandardowe. W przypadku zasad ostrzegania po pominięciu przez użytkownika końcowego witryna zostanie domyślnie odblokowana przez 24 godziny dla tego użytkownika. Ten przedział czasowy może zostać zmodyfikowany przez administratora i przekazany przez usługę SmartScreen w chmurze. Możliwość obejścia ostrzeżenia można również wyłączyć w Microsoft Edge przy użyciu dostawcy CSP dla bloków zagrożeń internetowych (złośliwe oprogramowanie/wyłudzanie informacji). Aby uzyskać więcej informacji, zobacz [Microsoft Edge SmartScreen Ustawienia](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Ochrona przeglądarek

We wszystkich scenariuszach ochrony sieci Web filtr SmartScreen i usługa Network Protection mogą być używane razem w celu zapewnienia ochrony zarówno w przeglądarkach, jak i procesach innych firm. Filtr SmartScreen jest wbudowany bezpośrednio w Microsoft Edge, a usługa Network Protection monitoruje ruch w przeglądarkach i procesach innych firm. Na poniższym diagramie przedstawiono tę koncepcję. Ten diagram dwóch klientów pracujących razem w celu zapewnienia wielu pokrycia przeglądarki/aplikacji jest dokładny dla wszystkich funkcji ochrony sieci Web (wskaźniki, zagrożenia internetowe, filtrowanie zawartości).

:::image type="content" source="../../media/web-protection-protect-browsers.png" alt-text="Użycie filtru smartScreen i ochrony sieci razem" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Rozwiązywanie problemów z blokami punktów końcowych

Odpowiedzi z chmury SmartScreen są standaryzowane. Narzędzia takie jak Fiddler mogą służyć do sprawdzania odpowiedzi z usługi w chmurze, co pomoże określić źródło bloku.

Gdy usługa SmartScreen w chmurze odpowiada z odpowiedzią zezwalania, blokowania lub ostrzegania, kategoria odpowiedzi i kontekst serwera są przekazywane z powrotem do klienta. W Microsoft Edge kategoria odpowiedzi jest używana do określenia odpowiedniej strony bloku do wyświetlenia (złośliwe, wyłudzanie informacji, zasady organizacyjne).

W poniższej tabeli przedstawiono odpowiedzi i ich skorelowane funkcje.

<br>

****

|Kategoria odpowiedzi|Funkcja odpowiedzialna za blok|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|Wskaźniki niestandardowe|
|CasbPolicy|Defender for Cloud Apps|
|Złośliwy|Zagrożenia internetowe|
|Wyłudzanie informacji|Zagrożenia internetowe|
|||

## <a name="advanced-hunting-for-web-protection"></a>Zaawansowane wyszukiwanie zagrożeń w zakresie ochrony w Internecie

Kusto zapytań w zaawansowanym wyszukiwaniu zagrożeń można używać do podsumowania bloków ochrony sieci Web w organizacji przez maksymalnie 30 dni. Te zapytania używają informacji wymienionych powyżej, aby rozróżnić różne źródła bloków i podsumować je w przyjazny dla użytkownika sposób. Na przykład poniższe zapytanie zawiera listę wszystkich bloków WCF pochodzących z Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomBlockList"
```

Podobnie możesz użyć poniższego zapytania, aby wyświetlić listę wszystkich bloków WCF pochodzących z usługi Network Protection (na przykład bloku WCF w przeglądarce innej firmy). Pamiętaj, że element ActionType został zaktualizowany, a element "Experience" został zmieniony na "ResponseCategory".

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Aby wyświetlić listę bloków, które są spowodowane innymi funkcjami (takimi jak wskaźniki niestandardowe), zapoznaj się z powyższą tabelą przedstawiającą każdą funkcję i ich odpowiednią kategorię odpowiedzi. Te zapytania mogą być również modyfikowane w celu wyszukiwania danych telemetrycznych związanych z określonymi maszynami w organizacji. Zwróć uwagę, że element ActionType wyświetlany w każdym z powyższych zapytań będzie pokazywać tylko te połączenia, które zostały zablokowane przez funkcję ochrony sieci Web, a nie cały ruch sieciowy.

## <a name="user-experience"></a>Środowisko użytkownika

Jeśli użytkownik odwiedzi stronę internetową, która stwarza ryzyko złośliwego oprogramowania, wyłudzania informacji lub innych zagrożeń internetowych, Microsoft Edge wyzwoli stronę blokady z napisem "Ta witryna została zgłoszona jako niebezpieczna" wraz z informacjami dotyczącymi zagrożenia.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-malicious-block.png" alt-text="Strona zablokowana przez Microsoft Edge" lightbox="../../media/web-protection-malicious-block.png":::

W przypadku zablokowania przez program WCF lub niestandardowy wskaźnik strona bloku zostanie wyświetlona w Microsoft Edge informująca użytkownika, że ta witryna jest zablokowana przez organizację.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-indicator-blockpage.png" alt-text="Strona zablokowana przez organizację" lightbox="../../media/web-protection-indicator-blockpage.png":::

W każdym razie żadne strony blokowe nie są wyświetlane w przeglądarkach innych firm, a użytkownik widzi stronę "Bezpieczne połączenie nie powiodło się" wraz z wyskakującym powiadomieniem. W zależności od zasad odpowiedzialnych za blok użytkownik zobaczy inny komunikat w wyskakujących powiadomieniach. Na przykład filtrowanie zawartości internetowej spowoduje wyświetlenie komunikatu "Ta zawartość jest zablokowana".

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-np-block.png" alt-text="Strona zablokowana przez program WCF" lightbox="../../media/web-protection-np-block.png":::

## <a name="report-false-positives"></a>Zgłaszanie wyników fałszywie dodatnich

Aby zgłosić fałszywie dodatni wynik dla witryn, które zostały uznane za niebezpieczne przez filtr SmartScreen, użyj linku wyświetlanego na stronie bloku w Microsoft Edge (jak pokazano powyżej).

W przypadku programu WCF można zakwestionować kategorię domeny. Przejdź do karty **Domeny raportów** WCF, a następnie kliknij pozycję **Nieścisłości raportu**. Zostanie otwarte okno wysuwane. Ustaw priorytet zdarzenia i podaj dodatkowe szczegóły, takie jak sugerowana kategoria. Aby uzyskać więcej informacji na temat włączania programu WCF i sposobu kwestionowania kategorii, zobacz [Filtrowanie zawartości sieci Web](web-content-filtering.md).

Aby uzyskać więcej informacji na temat sposobu przesyłania wyników fałszywie dodatnich/ujemnych, zobacz [Address false positives/negatives in Ochrona punktu końcowego w usłudze Microsoft Defender (Adresowanie fałszywych alarmów/negatywów w Ochrona punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)).

## <a name="related-information"></a>Informacje pokrewne

<br>

****

|Temat|Opis|
|---|---|
|[Ochrona przed zagrożeniami sieci Web](web-threat-protection.md) | Zatrzymaj dostęp do witryn wyłudzających informacje, wektorów złośliwego oprogramowania, witryn wykorzystujących luki w zabezpieczeniach, witryn niezaufanych lub witryn o niskiej reputacji oraz witryn, które zostały zablokowane.|
|[Filtrowanie zawartości sieci Web](web-content-filtering.md) | Śledzenie i regulowanie dostępu do witryn internetowych na podstawie ich kategorii zawartości.|
|
