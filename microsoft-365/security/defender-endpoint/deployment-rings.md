---
title: Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w pierścieniach
description: Dowiedz się, jak wdrażać Ochrona punktu końcowego w usłudze Microsoft Defender w pierścieniach
keywords: deploy, rings, evaluate, pilot, insider fast, insider slow, setup, onboard, phase, deployment, deploying, adoption, configuring
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
ms.openlocfilehash: 41f47720582f715e6c5d28276ddd87777e9669d5
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783386"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w pierścieniach

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender można wykonać przy użyciu podejścia do wdrażania opartego na pierścieniu.

Pierścienie wdrażania można zastosować w następujących scenariuszach:

- [Nowe wdrożenia](#new-deployments)
- [Istniejące wdrożenia](#existing-deployments)

## <a name="new-deployments"></a>Nowe wdrożenia

:::image type="content" source="images/deployment-rings.png" alt-text="Pierścienie wdrażania" lightbox="images/deployment-rings.png":::

Podejście oparte na pierścieniu to metoda identyfikowania zestawu punktów końcowych do dołączenia i sprawdzania, czy pewne kryteria zostały spełnione przed kontynuowaniem wdrażania usługi na większym zestawie urządzeń. Możesz zdefiniować kryteria zakończenia dla każdego pierścienia i upewnić się, że są one spełnione przed przejściem do następnego pierścienia.

Wdrożenie oparte na pierścieniu pomaga zmniejszyć potencjalne problemy, które mogą wystąpić podczas wdrażania usługi. Najpierw przeprowadzając pilotaż pewnej liczby urządzeń, możesz zidentyfikować potencjalne problemy i ograniczyć potencjalne zagrożenia, które mogą wystąpić.

Tabela 1 zawiera przykładowe pierścienie wdrażania, których można użyć.

**Tabela 1**:

<br>

****

|Pierścień wdrożenia|Opis|
|---|---|
|Oceny|Pierścień 1: Identyfikowanie 50 systemów do testowania pilotażowego|
|Pilot|Pierścień 2. Identyfikowanie kolejnych 50–100 punktów końcowych w środowisku produkcyjnym|
|Pełne wdrożenie|Pierścień 3: Wdrażanie usługi dla pozostałej części środowiska w większych przyrostach|
|

### <a name="exit-criteria"></a>Kryteria zakończenia

Przykładowy zestaw kryteriów zakończenia dla tych pierścieni może obejmować:

- Urządzenia są wyświetlane na liście spisu urządzeń
- Alerty są wyświetlane na pulpicie nawigacyjnym
- [Uruchamianie testu wykrywania](run-detection-test.md)
- [Uruchamianie symulowanego ataku na urządzenie](attack-simulations.md)

### <a name="evaluate"></a>Oceny

Zidentyfikuj niewielką liczbę maszyn testowych w środowisku, które mają zostać dołączone do usługi. Najlepiej byłoby, gdyby te maszyny miały mniej niż 50 punktów końcowych.

### <a name="pilot"></a>Pilot

Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje różne punkty końcowe, które można dołączyć do usługi. W tym pierścieniu zidentyfikuj kilka urządzeń do dołączenia i na podstawie zdefiniowanych kryteriów zakończenia, aby przejść do następnego pierścienia wdrożenia.

W poniższej tabeli przedstawiono obsługiwane punkty końcowe i odpowiednie narzędzie, którego można użyć do dołączania urządzeń do usługi.

| Punkt końcowy     | Narzędzie do wdrażania                       |
|--------------|------------------------------------------|
| **Windows**  |  [Skrypt lokalny (maksymalnie 10 urządzeń)](configure-endpoints-script.md) <br> UWAGA: Jeśli chcesz wdrożyć więcej niż 10 urządzeń w środowisku produkcyjnym, zamiast tego użyj metody zasady grupy lub innych obsługiwanych narzędzi wymienionych poniżej.<br>  [Zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile Menedżer urządzeń](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z Microsoft Defender dla Chmury](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **macOS**    | [Skrypt lokalny](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Pro JAMF](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami mobilne](mac-install-with-other-mdm.md) |
| **Serwer z systemem Linux** | [Skrypt lokalny](linux-install-manually.md) <br> [Lalek](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               |

### <a name="full-deployment"></a>Pełne wdrożenie

Na tym etapie możesz użyć materiałów [planów wdrażania](deployment-strategy.md) , aby ułatwić planowanie wdrożenia.

Użyj poniższego materiału, aby wybrać odpowiednią architekturę Ochrona punktu końcowego w usłudze Microsoft Defender, która najlepiej odpowiada Twojej organizacji.

|**Element**|**Opis**|
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Strategia wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender" lightbox="images/mde-deployment-strategy.png":::](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Materiał architektoniczny pomaga zaplanować wdrożenie dla następujących architektur: <ul><li> Natywny dla chmury </li><li> Współzarządzanie </li><li> Lokalnie</li><li>Ocena i dołączanie lokalne</li></ul>

## <a name="existing-deployments"></a>Istniejące wdrożenia

### <a name="windows-endpoints"></a>punkty końcowe Windows

W przypadku serwerów Windows i/lub Windows należy wybrać kilka maszyn do przetestowania z wyprzedzeniem (przed wtorkiem poprawki) przy użyciu **programu weryfikacji aktualizacji zabezpieczeń (SUVP).**

Więcej informacji można znaleźć w następujących artykułach:

- [Co to jest program sprawdzania poprawności aktualizacji zabezpieczeń](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [Program walidacji aktualizacji oprogramowania i Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem Establishment — interaktywna oś czasu TwC — część 4](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>Punkty końcowe inne niż Windows

W systemach macOS i Linux można korzystać z kilku systemów i uruchamiać je w kanale beta.

> [!NOTE]
> Najlepiej, aby co najmniej jeden administrator zabezpieczeń i jeden deweloper mogli znaleźć problemy ze zgodnością, wydajnością i niezawodnością, zanim kompilacja przejdzie do bieżącego kanału.

Wybór kanału określa typ i częstotliwość aktualizacji oferowanych urządzeniu. Urządzenia w wersji beta to pierwsze urządzenia, które otrzymują aktualizacje i nowe funkcje, a następnie wersja zapoznawcza i ostatnia wersja bieżąca.

:::image type="content" source="images/insider-rings.png" alt-text="Pierścienie insiderów" lightbox="images/insider-rings.png":::


Aby zapoznać się z nowymi funkcjami i przekazać wczesną opinię, zaleca się skonfigurowanie niektórych urządzeń w przedsiębiorstwie do korzystania z wersji beta lub wersji zapoznawczej.

> [!WARNING]
> Przełączenie kanału po początkowej instalacji wymaga ponownej instalacji produktu. Aby przełączyć kanał produktu: odinstaluj istniejący pakiet, skonfiguruj ponownie urządzenie do korzystania z nowego kanału i wykonaj kroki opisane w tym dokumencie, aby zainstalować pakiet z nowej lokalizacji.
