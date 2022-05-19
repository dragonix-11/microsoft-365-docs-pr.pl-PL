---
title: Utwórz wskaźniki dla plików
ms.reviewer: ''
description: Utwórz wskaźniki dla skrótu pliku definiującego wykrywanie, zapobieganie i wykluczanie jednostek.
keywords: file, hash, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: da9e030d929f65c7ea5bd83010d2b7f49b1d90d9
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535597"
---
# <a name="create-indicators-for-files"></a>Utwórz wskaźniki dla plików

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft Defender dla Firm](../defender-business/mdb-overview.md)

> [!TIP]
> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Zapobiegaj dalszej propagacji ataku w organizacji, zakazując potencjalnie złośliwych plików lub podejrzewanego złośliwego oprogramowania. Jeśli znasz potencjalnie złośliwy przenośny plik wykonywalny (PE), możesz go zablokować. Ta operacja uniemożliwi jej odczytywanie, zapisywanie lub wykonywanie na urządzeniach w organizacji.

Istnieją trzy sposoby tworzenia wskaźników dla plików:

- Przez utworzenie wskaźnika za pośrednictwem strony ustawień
- Przez utworzenie wskaźnika kontekstowego przy użyciu przycisku dodaj wskaźnik na stronie szczegółów pliku
- Przez utworzenie wskaźnika za pośrednictwem [interfejsu API wskaźników](ti-indicator.md)

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed utworzeniem wskaźników dla plików ważne jest zrozumienie następujących wymagań wstępnych:

- Ta funkcja jest dostępna, jeśli organizacja używa **Program antywirusowy Microsoft Defender (w trybie aktywnym)** i **włączono ochronę opartą na chmurze**. Aby uzyskać więcej informacji, zobacz [Zarządzanie ochroną opartą na chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- Wersja klienta ochrony przed złośliwym kodem musi mieć wersję 4.18.1901.x lub nowszą. Zobacz [Miesięczne wersje platformy i aparatu](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Obsługiwane na urządzeniach z Windows 10 w wersji 1703 lub nowszej, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 i Windows Server 2022.
    
   > [!NOTE]
   > Windows Server 2016 i Windows Server 2012 R2 należy dołączyć, korzystając z instrukcji zawartych w temacie [Dołączanie serwerów Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała. Niestandardowe wskaźniki plików z akcjami Zezwalaj, Blokuj i Koryguj są teraz również dostępne w [publicznej wersji zapoznawczej dla rozszerzonych możliwości aparatu ochrony przed złośliwym kodem dla macOS i Linux](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-engine-capabilities-for-linux-and-macos/ba-p/3292003).

- Aby rozpocząć blokowanie plików, należy najpierw [włączyć funkcję "blokuj lub zezwalaj"](advanced-features.md) w Ustawienia.

Ta funkcja ma na celu zapobieganie pobieraniu z Sieci Web podejrzanego złośliwego oprogramowania (lub potencjalnie złośliwych plików). Obecnie obsługuje przenośne pliki wykonywalne (PE), w tym pliki .exe i .dll. Pokrycie zostanie przedłużone w czasie.

> [!IMPORTANT]
> W usłudze Defender for Endpoint Plan 1 i Defender for Business możesz utworzyć wskaźnik blokujący lub zezwalany na plik. W usłudze Defender dla firm wskaźnik jest stosowany w całym środowisku i nie może być ograniczony do konkretnych urządzeń.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Tworzenie wskaźnika dla plików na stronie ustawień

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Wskaźniki** **punktów końcowych** (w obszarze **Reguły**\>).

2. Wybierz kartę **Skróty plików** .

3. Wybierz pozycję **Dodaj element**.

4. Określ następujące szczegóły:
    - Wskaźnik — określ szczegóły jednostki i zdefiniuj wygaśnięcie wskaźnika.
    - Akcja — określ akcję do wykonania i podaj opis.
    - Zakres — zdefiniuj zakres grupy urządzeń (określanie zakresu nie jest dostępne w [usłudze Defender dla firm](../defender-business/mdb-overview.md)).

5. Przejrzyj szczegóły na karcie Podsumowanie, a następnie wybierz pozycję **Zapisz**.

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Tworzenie wskaźnika kontekstowego na stronie szczegółów pliku

Jedną z opcji podczas wykonywania [akcji odpowiedzi w pliku](respond-file-alerts.md) jest dodanie wskaźnika dla pliku. Po dodaniu skrótu wskaźnika dla pliku możesz zgłosić alert i zablokować plik za każdym razem, gdy urządzenie w organizacji podejmie próbę jego uruchomienia.

Pliki automatycznie blokowane przez wskaźnik nie będą wyświetlane w centrum akcji pliku, ale alerty będą nadal widoczne w kolejce alertów.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>Publiczna wersja zapoznawcza: Alerty dotyczące akcji blokowania plików

> [!IMPORTANT]
> Informacje w tej sekcji (**publiczna wersja zapoznawcza dla aparatu automatycznego badania i korygowania**) odnoszą się do produktu wstępnego, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Bieżące obsługiwane akcje dla mkolu plików to zezwalanie, inspekcja i blokowanie i korygowanie. Po wybraniu opcji zablokowania pliku możesz wybrać, czy wyzwalanie alertu jest wymagane. W ten sposób będzie można kontrolować liczbę alertów docieranych do zespołów ds. operacji zabezpieczeń i upewnić się, że są zgłaszane tylko wymagane alerty.

W Microsoft 365 Defender przejdź do **pozycji Ustawienia** >  EndpointsIndicatorsDodaj >  >  **skrót nowego pliku**.

Wybierz opcję Blokuj i skoryguj plik.

Określ, czy chcesz wygenerować alert dla zdarzenia bloku pliku i zdefiniuj ustawienia alertów:

- Tytuł alertu
- Ważność alertu
- Kategoria
- Opis
- Zalecane akcje

:::image type="content" source="images/indicators-generate-alert.png" alt-text="Ustawienia alertu dla wskaźników plików" lightbox="images/indicators-generate-alert.png":::

> [!IMPORTANT]
>
> - Zazwyczaj bloki plików są wymuszane i usuwane w ciągu kilku minut, ale może to potrwać ponad 30 minut.
> - Jeśli istnieją powodujące konflikt zasady IoC plików o tym samym typie wymuszania i celu, zasady bardziej bezpiecznego skrótu zostaną zastosowane. Zasady IoC skrótu pliku SHA-256 zostaną przejęte przez zasady IoC skrótu plików SHA-1, które zostaną przejęte przez zasady IoC skrótu pliku MD5, jeśli typy skrótów zdefiniują ten sam plik. Jest to zawsze prawdziwe niezależnie od grupy urządzeń.
> - We wszystkich innych przypadkach, jeśli powodujące konflikt zasady IoC plików z tym samym obiektem docelowym wymuszania są stosowane do wszystkich urządzeń i do grupy urządzenia, a następnie dla urządzenia, zasady w grupie urządzeń wygra.
> - Jeśli zasady grupy EnableFileHashComputation są wyłączone, dokładność blokowania IoC pliku zostanie zmniejszona. Jednak włączenie `EnableFileHashComputation` może mieć wpływ na wydajność urządzenia. Na przykład kopiowanie dużych plików z udziału sieciowego na urządzenie lokalne, zwłaszcza za pośrednictwem połączenia sieci VPN, może mieć wpływ na wydajność urządzenia.
>
> Aby uzyskać więcej informacji na temat zasad grupy EnableFileHashComputation, zobacz [Dostawca CSP usługi Defender](/windows/client-management/mdm/defender-csp).

## <a name="public-preview-advanced-hunting-capabilities"></a>Publiczna wersja zapoznawcza: zaawansowane możliwości wyszukiwania zagrożeń

> [!IMPORTANT]
> Informacje w tej sekcji (**publiczna wersja zapoznawcza automatycznego badania i aparatu korygowania**) odnoszą się do produktu wstępnego, który może zostać znacząco zmodyfikowany przed jego komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do podanych tutaj informacji.

Możesz wykonać zapytanie dotyczące działania akcji odpowiedzi z wyprzedzeniem. Poniżej znajduje się przykładowe zapytanie wyszukiwania zagrożeń z wyprzedzeniem:

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania zagrożeń, zobacz [Proaktywne wyszukiwanie zagrożeń z zaawansowanym wyszukiwaniem zagrożeń](advanced-hunting-overview.md).

Poniżej przedstawiono dodatkowe nazwy wątków, których można użyć w przykładowym zapytaniu z góry:

Pliki:

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

Certyfikaty:

- EUS:Win32/CustomCertEnterpriseBlock!cl

Działanie akcji odpowiedzi można również wyświetlić na osi czasu urządzenia.

## <a name="policy-conflict-handling"></a>Obsługa konfliktów zasad

Konflikt obsługi zasad IoC certyfikatów i plików będzie postępować zgodnie z poniższą kolejnością:

- Jeśli plik nie jest dozwolony przez Windows Defender kontrolkę aplikacji i funkcję AppLocker, wymuś zasady/zasady trybu, a następnie **zablokuj**
- W przeciwnym razie, jeśli plik jest dozwolony przez wykluczenie Program antywirusowy Microsoft Defender,
- W przeciwnym razie, jeśli plik jest zablokowany lub ostrzegany przez blok lub ostrzeżenie pliku IoC, a następnie **blokuj/ostrzegaj**
- W przeciwnym razie, jeśli plik jest dozwolony przez zasady IoC pliku zezwalania, a następnie **zezwalaj**
- Jeśli plik jest zablokowany przez reguły asr, CFA, AV, SmartScreen, a następnie **blokuj**
- Else **Allow** (przechodzi Windows Defender kontrolki aplikacji & zasad funkcji AppLocker, żadne reguły IoC nie mają do niego zastosowania)

>[!NOTE]
> W sytuacjach, gdy Program antywirusowy Microsoft Defender jest ustawiona na **wartość Blokuj**, ale w usłudze Defender dla punktu końcowego ustawiono wartość **Zezwalaj**, zasady będą domyślnie **zezwalać**.

Jeśli istnieją powodujące konflikt zasady IoC plików o tym samym typie wymuszania i celu, zostaną zastosowane zasady bardziej bezpiecznego (czyli dłuższego) skrótu. Na przykład zasady skrótu pliku SHA-256 IoC zostaną przejęte przez zasady IoC skrótu pliku MD5, jeśli oba typy skrótów zdefiniują ten sam plik.

> [!WARNING]
> Obsługa konfliktów zasad dla plików i certyfikatów różni się od obsługi konfliktów zasad dla domen/adresów URL/adresów IP.

Funkcje aplikacji narażonych na zagrożenia i zarządzanie lukami w zabezpieczeniach bloku używają plików IoCs do wymuszania i będą zgodne z powyższą kolejnością obsługi konfliktów.

### <a name="examples"></a>Przykłady

<br>

****

|Składnik|Wymuszanie składników|Akcja wskaźnika pliku|Result (Wynik)|
|---|---|---|---|
|Wykluczenie ścieżki pliku zmniejszania obszaru podatnego na ataki|Zezwalaj|Blokuj|Blokuj|
|Reguła zmniejszania obszaru podatnego na ataki|Blokuj|Zezwalaj|Zezwalaj|
|Windows Defender kontrolka aplikacji|Zezwalaj|Blokuj|Zezwalaj|
|Windows Defender kontrolka aplikacji|Blokuj|Zezwalaj|Blokuj|
|wykluczenie Program antywirusowy Microsoft Defender|Zezwalaj|Blokuj|Zezwalaj|
|

## <a name="see-also"></a>Zobacz też

- [Utwórz wskaźniki](manage-indicators.md)
- [Utwórz wskaźniki adresów IP i adresów URL/domen](indicator-ip-domain.md)
- [Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md)
- [Zarządzaj wskaźnikami](indicator-manage.md)
