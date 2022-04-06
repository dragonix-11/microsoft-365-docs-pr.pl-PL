---
title: Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w pierścieniach
description: Dowiedz się, jak wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender w pierścieniach
keywords: wdrażanie, pierścienie, ocena, pilot, niejawny program testów szybki, niejawny program testów wolny, konfiguracja, wdrożenie, faza, wdrożenie, wdrażanie, wdrażanie, konfigurowanie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 116960ed6e7d4a765479f0c76715e48ec8312e3b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472094"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w pierścieniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender można wykonać przy użyciu wdrożenia opartego na pierścieniu.

Pierścienie wdrażania można stosować w następujących scenariuszach:

- [Nowe wdrożenia](#new-deployments)
- [Istniejące wdrożenia](#existing-deployments)

## <a name="new-deployments"></a>Nowe wdrożenia

:::image type="content" source="images/deployment-rings.png" alt-text="Pierścienie wdrożenia" lightbox="images/deployment-rings.png":::

Metoda oparta na pierścieniu jest metodą identyfikowania zestawu punktów końcowych do doniania i sprawdzania, czy są spełnione określone kryteria, przed przystąpieniem do wdrażania usługi na większym zestawie urządzeń. Możesz zdefiniować kryteria wyjścia dla każdego pierścienia i upewnić się, że są one odpowiednie, zanim przejdą do następnego pierścienia.

Wdrożenie oparte na pierścieniu pomaga ograniczyć potencjalne problemy, które mogą się pojawić podczas wdrażania usługi. Pilotażowanie określonej liczby urządzeń pozwala na zidentyfikowanie potencjalnych problemów i ograniczenie potencjalnych zagrożeń, które mogą się pojawić.

Tabela 1 zawiera przykładowe pierścienie wdrażania, których możesz użyć.

**Tabela 1**.

<br>

****

|Pierścień wdrożenia|Opis|
|---|---|
|Szacowanie|Pierścień 1. Identyfikowanie 50 systemów na testy pilotażowe|
|Pilot|Pierścień 2. Identyfikowanie kolejnych 50–100 punktów końcowych w środowisku produkcyjnym|
|Pełne wdrożenie|Pierścień 3. Wdniaj usługę do pozostałych środowisk w większym przyrostach|
|

### <a name="exit-criteria"></a>Kryteria wyjścia

Przykładowy zestaw kryteriów wyjścia dla tych pierścieni może obejmować:

- Urządzenia są wyświetlane na liście zasobów w spisie
- Alerty są wyświetlane na pulpicie nawigacyjnym
- [Uruchamianie testu wykrywania](run-detection-test.md)
- [Uruchamianie symulowanego ataku na urządzeniu](attack-simulations.md)

### <a name="evaluate"></a>Szacowanie

Zidentyfikuj niewielką liczbę komputerów testowych w środowisku, aby do usługi do nich dołyszyć. Najlepiej, jeśli te komputery będą mieć mniej niż 50 punktów końcowych.

### <a name="pilot"></a>Pilot

Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje wiele punktów końcowych, które można dodać do usługi. W tym pierścieniu określ kilka urządzeń do wdrożenia i na podstawie kryteriów wyjścia, które zdefiniowasz, przejdź do następnego pierścienia wdrożenia.

W poniższej tabeli przedstawiono obsługiwane punkty końcowe i odpowiadające im narzędzie, za pomocą których można dodać urządzenia do usługi.

| Punkt końcowy     | Narzędzie wdrażania                       |
|--------------|------------------------------------------|
| **Windows**  |  [Skrypt lokalny (do 10 urządzeń)](configure-endpoints-script.md) <br> UWAGA: Jeśli chcesz wdrożyć więcej niż 10 urządzeń w środowisku produkcyjnym, użyj zamiast tego metody zasady grupy lub innych obsługiwanych narzędzi wymienionych poniżej.<br>  [Zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Urządzenie Menedżer urządzeń](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z Microsoft Defender dla Chmury](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Skrypt lokalny](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Jamf Pro](mac-install-with-jamf.md) <br> [Urządzenia Zarządzanie urządzeniami](mac-install-with-other-mdm.md) |
| **Linux Server** | [Skrypt lokalny](linux-install-manually.md) <br> [Wytłaczenie](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               |

### <a name="full-deployment"></a>Pełne wdrożenie

Na tym etapie możesz użyć materiałów do planowania wdrożenia, aby ułatwić Ci zaplanowanie wdrożenia.[](deployment-strategy.md)

Użyj następującego materiału, aby wybrać odpowiednią architekturę Ochrona punktu końcowego w usłudze Microsoft Defender najlepszą dla Twojej organizacji.

|**Element**|**Opis**|
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Strategia w zakresie Ochrona punktu końcowego w usłudze Microsoft Defender wdrażania" lightbox="images/mde-deployment-strategy.png":::](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Materiał architektoniczny ułatwia zaplanowanie wdrożenia z następującymi architekturami: <ul><li> Natywne w chmurze </li><li> Współzawłasnie </li><li> Lokalne</li><li>Oceny i lokalne dołączanie</li></ul>

## <a name="existing-deployments"></a>Istniejące wdrożenia

### <a name="windows-endpoints"></a>Windows punktów końcowych

W Windows i/lub Windows wybierz kilka komputerów do przetestowania z wyprzedzeniem (przed poprawką we wtorek) przy użyciu programu sprawdzania poprawności aktualizacji zabezpieczeń **(STEAMP**).

Więcej informacji można znaleźć w następujących artykułach:

- [Co to jest program sprawdzania poprawności aktualizacji zabezpieczeń](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [Program sprawdzania poprawności aktualizacji oprogramowania i Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem - Interakcyjna oś czasu TwC Część 4](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>Inne niż Windows punkty końcowe

W systemach macOS i Linux możesz skorzystać z kilku systemów i uruchomić go w kanale beta.

> [!NOTE]
> Najlepiej, aby co najmniej jeden administrator zabezpieczeń i jeden deweloper był w stanie znaleźć problemy ze zgodnością, wydajnością i niezawodnością przed rozpoczęciem kompilacji w bieżącym kanale.

Wybór kanału zależy od typu i częstotliwości aktualizacji oferowanych dla Twojego urządzenia. Urządzenia w wersji Beta są pierwszymi urządzeniami, które otrzymują aktualizacje i nowe funkcje, a następnie są dostępne w wersji Preview, a w końcu bieżącej.

:::image type="content" source="images/insider-rings.png" alt-text="Pierścienie niejawnego programu testów" lightbox="images/insider-rings.png":::


W celu wyświetlania w wersji zapoznawczej nowych funkcji i wczesnych opinii zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie do korzystania z wersji Beta lub Preview.

> [!WARNING]
> Przełączenie kanału po początkowej instalacji wymaga ponownego zainstalowania produktu. Aby przełączyć kanał produktu: odinstaluj istniejący pakiet, ponownie skonfiguruj urządzenie do korzystania z nowego kanału, a następnie postępuj zgodnie z instrukcjami w tym dokumencie, aby zainstalować pakiet z nowej lokalizacji.
