---
title: Urządzenia na urządzeniach i konfigurowanie programu Microsoft Defender na temat możliwości punktu końcowego
description: Dowiedz się Windows 10, jak uruchamiać na urządzeniach Windows, serwerach i innych urządzeniach oraz jak uruchamiać test wykrywania.
keywords: onboarding, Microsoft Defender for Endpoint onboarding, sccm, group policy, mdm, local script, detection test
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4492b50cfdfb0125a9079eb1f4a4945b6e06e011
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014701"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>Urządzenia na urządzeniach i konfigurowanie programu Microsoft Defender na temat możliwości punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Wdrażanie programu Microsoft Defender dla punktu końcowego jest procesem dwuetapowym.

- Urządzenia dołączane do usługi
- Konfigurowanie możliwości usługi

![Ilustracja przedstawiająca proces dołączania i konfigurowania](images/deployment-steps.png)

## <a name="onboard-devices-to-the-service"></a>Urządzenia dołączane do usługi
Aby wyjść z dowolnego z obsługiwanych urządzeń, musisz przejść do sekcji dołączania w portalu programu Defender for Endpoint. W zależności od urządzenia zostaną Ci przekazane odpowiednie instrukcje oraz odpowiednie opcje zarządzania i wdrażania odpowiednie dla urządzenia. 

Aby na ogół dołączać urządzenia do usługi:

- Sprawdzanie, czy urządzenie spełnia [minimalne wymagania](minimum-requirements.md)
- W zależności od urządzenia postępuj zgodnie z instrukcjami konfiguracji w sekcji dołączania do portalu programu Defender dla punktu końcowego.
- Użyj odpowiedniego narzędzia do zarządzania i metody wdrażania dla swoich urządzeń
- Uruchom test wykrywania, aby sprawdzić, czy urządzenia są poprawnie zainstalowane i że zgłaszają się do usługi



## <a name="onboarding-and-configuration-tool-options"></a>Opcje narzędzia do dołączania i konfiguracji
W poniższej tabeli wymieniono dostępne narzędzia na podstawie punktu końcowego, który trzeba do dyspozycji.

| Punkt końcowy     | Opcje narzędzia                       |
|--------------|------------------------------------------|
| **Windows**  |  [Skrypt lokalny (do 10 urządzeń)](configure-endpoints-script.md) <br>  [zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Menedżer urządzeń przenośnych](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z usługą Microsoft Defender dla chmury](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Skrypty lokalne](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Jamf Pro](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami przenośnymi](mac-install-with-other-mdm.md) |
| **Linux Server** | [Skrypt lokalny](linux-install-manually.md) <br> [Wytłaczenie](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)               |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)            | 


W poniższej tabeli wymieniono dostępne narzędzia na podstawie punktu końcowego, który trzeba do dyspozycji.

## <a name="configure-capabilities-of-the-service"></a>Konfigurowanie możliwości usługi
Urządzenia dołączające w praktyce wykrywanie i reagowanie w punktach końcowych funkcji Micorosft Defender for Endpoint.

Po włoceniu urządzeń konieczne będzie skonfigurowanie innych możliwości usługi. W poniższej tabeli wymieniono funkcje, które można skonfigurować w celu uzyskania najlepszej ochrony środowiska.

| Funkcja | Opis |
|-|-|
| [Konfigurowanie zarządzania & zagrożeniami (TVM)](tvm-prerequisites.md) | Zarządzanie & zagrożeniami i lukami w zabezpieczeniach to składnik programu Microsoft Defender for Endpoint, który zapewnia unikatowych wartości zarówno administratorom zabezpieczeń, jak i zespołom operacji zabezpieczeń, w tym: <br><br> - Szczegółowe informacje o wykrywanie i reagowanie w punktach końcowych (EDR) skorelowane z lukami w zabezpieczeniach punktów końcowych w czasie rzeczywistym. <br><br> - Nieocenieni kontekstowe luki w zabezpieczeniach urządzeń podczas badania zdarzeń. <br><br> - Wbudowane procesy rozwiązywania problemów za pośrednictwem usług firmy Microsoft Intune i Microsoft System Center Configuration Manager.  |
| [Konfigurowanie ochrony następnej generacji (NGP)](configure-microsoft-defender-antivirus-features.md) | Program antywirusowy Microsoft Defender to wbudowane rozwiązanie ochrony przed złośliwym oprogramowaniem, które zapewnia ochronę komputerów stacjonarnych, przenośnych i serwerów następnej generacji. Program antywirusowy Microsoft Defender zawiera:<br> <br>- Zapewnianie ochrony w chmurze w celu natychmiastowego wykrywania i blokowania nowych i pojawiających się zagrożeń. Oprócz uczenia maszynowego i inteligentnego Graph ochrona w chmurze jest częścią technologii nowej generacji, które są zaawansowane dla Program antywirusowy Microsoft Defender.<br> <br> - Skanowanie zawsze przy użyciu zaawansowanego monitorowania zachowania plików i procesów oraz innych funkcji heuristics (nazywanych również "ochroną w czasie rzeczywistym").<br><br> - Dedykowane aktualizacje ochrony oparte na uczeniem maszynowym, analizie danych big-data przez ludzi oraz szczegółowe badania nad odpornością na zagrożenia. |
| [Konfigurowanie zmniejszenia powierzchni ataków (ASR)](overview-attack-surface-reduction.md) | Funkcje ograniczania powierzchni ataków w programie Microsoft Defender dla punktu końcowego pomagają chronić urządzenia i aplikacje w organizacji przed nowymi i pojawiającymi się zagrożeniami. |
| [Konfigurowanie funkcji automatycznego & zaradczego (AIR)](configure-automated-investigations-remediation.md) | Program Microsoft Defender for Endpoint używa zautomatyzowanych analiz w celu znacznego zmniejszenia liczby alertów, które trzeba zbadać indywidualnie. Funkcja automatycznego badania korzysta z różnych algorytmów inspekcji i procesów używanych przez analityków (takich jak podręczniki) do badania alertów i podejmowania natychmiastowych działań naprawczych w celu rozwiązania naruszeń. Znacząco zmniejsza to liczbę alertów, umożliwiając ekspertom z operacji zabezpieczeń skoncentrowanie się na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokich wartościach. |
| [Konfigurowanie Microsoft Threat Experts (MTE)](configure-microsoft-threat-experts.md) | Microsoft Threat Experts to zarządzana służba chłoń, która zapewnia centrach operacji zabezpieczeń (SOC, Security Operation Center) z specjalistycznej kontroli i analizy, aby zapewnić, że nie przegapisz krytycznych zagrożeń w ich unikatowych środowiskach.      |


## <a name="supported-capabilities-for-windows-devices"></a>Obsługiwane funkcje Windows urządzeniach

|System operacyjny  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |<sup>Windows Server 2016[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**Zapobieganie**    |         |         |         |         |         |
|Reguły zmniejszania powierzchni w przypadku ataków     |    T     |   T      |    T     |    T     |    T     |
|Sterowanie urządzeniem     |     T    |    N     |    N     |    N     |    N     |  
|Zapora     |      T   |    T     |     T    |    T    |    T   |
|Ochrona sieci     |      T   |    T     |     T    |    T    |    T   |
|Ochrona następnej generacji     |      T   |    T     |     T    |    T    |    T   |
|Ochrona przed naruszeniami     |        T   |    T     |     T    |    T    |    T   |
|Ochrona sieci Web     |       T   |    T     |     T    |    T    |    T   |
|||||||
|**Wykrywanie**     |         |         |         |||
|Zaawansowane łowiectwo     |      T   |    T     |     T    |    T    |    T   |
|Wskaźniki plików niestandardowych     |      T   |    T     |     T    |    T    |    T   |
|Niestandardowe wskaźniki sieci     |      T   |    T     |     T    |    T    |    T   |
|EDR tryb & pasywny     |      T   |    T     |     T    |    T    |    T   |
|Czujnik wykrywania  sense     |      T   |    T     |     T    |    T    |    T   |
|Punkt & odnajdowania urządzeń sieciowych     |      T   |    N     |     N    |    N    |    N   |
|||||||
|**Odpowiedź**     |         |         |         |||
|Automated Investigation & Response (AIR)    |      T   |    T     |     T    |    T    |    T   |
|Funkcje odpowiedzi urządzenia: izolacji, zbierania pakietu badania, uruchamianie skanowania audio/wideo     |      T   |    T     |     T    |    T    |    T   |
|Funkcje odpowiedzi na pliki: zbieranie plików, analiza głębokości, blokowanie plików, zatrzymywanie i poddaj kwarantannie procesy     |      T   |    T     |     T    |    T    |    T   |
|Odpowiedź na żywo    |      T   |    T     |     T    |    T    |    T   |

(<a id="fn1">1</a>) Odwołuje się do nowoczesnego, ujednoliconego rozwiązania dla Windows Server 2012 i 2016. Aby uzyskać więcej informacji, [zobacz Onboard Windows Servers to the Defender for Endpoint service](configure-server-endpoints.md) (Wewnechaj serwery serwerów do usługi Defender for Endpoint).

>[!NOTE]
>Windows 7, 8.1, Windows Server 2008 R2 obsługują czujnik EDR i audio/wideo przy użyciu System Center Endpoint Protection (SCEP).
