---
title: Dołącz urządzenia i konfiguruj możliwości usługi ochrony punktu końcowego w usłudze Microsoft Defender
description: Dołącz Windows 10 urządzenia, serwery, urządzenia inne niż Windows i dowiedz się, jak uruchomić test wykrywania.
keywords: dołączanie, dołączanie Ochrona punktu końcowego w usłudze Microsoft Defender, sccm, zasady grupy, mdm, skrypt lokalny, test wykrywania
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
ms.openlocfilehash: 4489709312470d44994828f7f39da72c2a714e08
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651460"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>Dołącz urządzenia i konfiguruj możliwości usługi ochrony punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender jest procesem dwuetapowym.

- Dołączanie urządzeń do usługi
- Konfigurowanie możliwości usługi

:::image type="content" source="images/deployment-steps.png" alt-text="Proces dołączania i konfiguracji" lightbox="images/deployment-steps.png":::

## <a name="onboard-devices-to-the-service"></a>Dołączanie urządzeń do usługi
Aby dołączyć dowolne z obsługiwanych urządzeń, musisz przejść do sekcji dołączania w portalu usługi Defender for Endpoint. W zależności od urządzenia należy wykonać odpowiednie kroki oraz udostępnić opcje narzędzi do zarządzania i wdrażania odpowiednie dla urządzenia. 

Ogólnie rzecz biorąc, aby dołączyć urządzenia do usługi:

- Sprawdź, czy urządzenie spełnia [minimalne wymagania](minimum-requirements.md)
- W zależności od urządzenia wykonaj kroki konfiguracji podane w sekcji dołączania w portalu usługi Defender for Endpoint
- Używanie odpowiedniego narzędzia do zarządzania i metody wdrażania dla urządzeń
- Uruchom test wykrywania, aby sprawdzić, czy urządzenia są prawidłowo dołączone i są raportowane do usługi



## <a name="onboarding-and-configuration-tool-options"></a>Opcje narzędzia do dołączania i konfiguracji
W poniższej tabeli wymieniono dostępne narzędzia oparte na punkcie końcowym, który należy dołączyć.

| Punkt końcowy     | Opcje narzędzi                       |
|--------------|------------------------------------------|
| **Windows**  |  [Skrypt lokalny (maksymalnie 10 urządzeń)](configure-endpoints-script.md) <br>  [Zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile Menedżer urządzeń](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md) <br> [Integracja z Microsoft Defender dla Chmury](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Skrypty lokalne](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Pro JAMF](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami mobilne](mac-install-with-other-mdm.md) |
| **Serwer z systemem Linux** | [Skrypt lokalny](linux-install-manually.md) <br> [Lalek](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)               |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)            | 


W poniższej tabeli wymieniono dostępne narzędzia oparte na punkcie końcowym, który należy dołączyć.

## <a name="configure-capabilities-of-the-service"></a>Konfigurowanie możliwości usługi
Dołączanie urządzeń skutecznie umożliwia wykrywanie i reagowanie w punktach końcowych możliwości Ochrona punktu końcowego w usłudze Microsoft Defender.

Po dołączeniu urządzeń należy skonfigurować inne możliwości usługi. W poniższej tabeli wymieniono możliwości, które można skonfigurować, aby uzyskać najlepszą ochronę środowiska.

| Możliwości | Opis |
|-|-|
| [Konfigurowanie zarządzania lukami w zabezpieczeniach & zagrożeń (TVM)](tvm-prerequisites.md) | Zarządzanie lukami w zabezpieczeniach & zagrożeń jest składnikiem Ochrona punktu końcowego w usłudze Microsoft Defender i zapewnia zarówno administratorom zabezpieczeń, jak i zespołom ds. operacji zabezpieczeń unikatową wartość, w tym: <br><br> — Szczegółowe informacje dotyczące wykrywanie i reagowanie w punktach końcowych w czasie rzeczywistym (EDR) skorelowane z lukami w zabezpieczeniach punktów końcowych. <br><br> — Nieoceniony kontekst luk w zabezpieczeniach urządzenia podczas badania zdarzeń. <br><br> — Wbudowane procesy korygowania za pośrednictwem Microsoft Intune i microsoft System Center Configuration Manager.  |
| [Konfigurowanie ochrony następnej generacji (NGP)](configure-microsoft-defender-antivirus-features.md) | Program antywirusowy Microsoft Defender to wbudowane rozwiązanie chroniące przed złośliwym kodem, które zapewnia ochronę następnej generacji dla komputerów stacjonarnych, komputerów przenośnych i serwerów. Program antywirusowy Microsoft Defender obejmuje:<br> <br>-Zapewniana w chmurze ochrona przed niemal natychmiastowym wykrywaniem i blokowaniem nowych i pojawiających się zagrożeń. Oprócz uczenia maszynowego i inteligentnego Graph zabezpieczeń ochrona dostarczana w chmurze jest częścią technologii nowej generacji, które zasilają Program antywirusowy Microsoft Defender.<br> <br> - Zawsze włączone skanowanie przy użyciu zaawansowanego monitorowania zachowania plików i procesów oraz innych heurystycznych (znanych również jako "ochrona w czasie rzeczywistym").<br><br> - Dedykowane aktualizacje ochrony oparte na uczeniu maszynowym, ludzkiej i zautomatyzowanej analizie danych big data oraz dogłębnych badaniach odporności na zagrożenia. |
| [Konfigurowanie zmniejszania obszaru ataków (ASR)](overview-attack-surface-reduction.md) | Możliwości zmniejszania obszaru podatnego na ataki w Ochrona punktu końcowego w usłudze Microsoft Defender pomagają chronić urządzenia i aplikacje w organizacji przed nowymi i pojawiającym się zagrożeniami. |
| [Konfigurowanie funkcji automatycznego badania & korygowania (AIR)](configure-automated-investigations-remediation.md) | Ochrona punktu końcowego w usłudze Microsoft Defender używa zautomatyzowanych badań w celu znacznego zmniejszenia liczby alertów, które należy zbadać indywidualnie. Funkcja zautomatyzowanego badania wykorzystuje różne algorytmy inspekcji i procesy używane przez analityków (np. podręczniki) do badania alertów i natychmiastowego korygowania w celu rozwiązania problemów z naruszeniami. Znacznie zmniejsza to liczbę alertów, dzięki czemu eksperci ds. operacji zabezpieczeń mogą skupić się na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokiej wartości. |
| [Konfigurowanie możliwości Microsoft Threat Experts (MTE)](configure-microsoft-threat-experts.md) | Microsoft Threat Experts to zarządzana usługa wyszukiwania zagrożeń, która zapewnia centra operacji zabezpieczeń (SOC) z specjalistycznym monitorowaniem i analizą, aby zapewnić, że krytyczne zagrożenia w ich unikatowych środowiskach nie zostaną pominięte.      |


## <a name="supported-capabilities-for-windows-devices"></a>Obsługiwane możliwości dla urządzeń Windows

|System operacyjny  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |<sup>Windows Server 2016[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**Zapobiegania**    |         |         |         |         |         |
|Reguły zmniejszania obszaru podatnego na ataki     |    T     |   T      |    T     |    T     |    T     |
|Kontrola urządzenia     |     T    |    N     |    N     |    N     |    N     |  
|Zapory     |      T   |    T     |     T    |    T    |    T   |
|Ochrona sieci     |      T   |    T     |     T    |    T    |    T   |
|Ochrona nowej generacji     |      T   |    T     |     T    |    T    |    T   |
|Ochrona przed naruszeniami     |        T   |    T     |     T    |    T    |    T   |
|Ochrona w Sieci Web     |       T   |    T     |     T    |    T    |    T   |
|||||||
|**Wykrywania**     |         |         |         |||
|Zaawansowane wyszukiwanie zagrożeń     |      T   |    T     |     T    |    T    |    T   |
|Niestandardowe wskaźniki plików     |      T   |    T     |     T    |    T    |    T   |
|Niestandardowe wskaźniki sieci     |      T   |    T     |     T    |    T    |    T   |
|EDR blokuj tryb pasywny &     |      T   |    T     |     T    |    T    |    T   |
|Czujnik wykrywania zmysłów     |      T   |    T     |     T    |    T    |    T   |
|Odnajdywanie urządzeń sieciowych & punktu końcowego     |      T   |    N     |     N    |    N    |    N   |
|||||||
|**Odpowiedzi**     |         |         |         |||
|Automatyczna odpowiedź & badania (AIR)    |      T   |    T     |     T    |    T    |    T   |
|Możliwości reagowania na urządzenia: izolacja, zbieranie pakietu badania, uruchamianie skanowania av     |      T   |    T     |     T    |    T    |    T   |
|Możliwości odpowiedzi na pliki: zbieranie plików, głęboka analiza, blok plików, zatrzymywanie i procesy kwarantanny     |      T   |    T     |     T    |    T    |    T   |
|Odpowiedź na żywo    |      T   |    T     |     T    |    T    |    T   |

(<a id="fn1">1</a>) Odnosi się do nowoczesnego, ujednoliconego rozwiązania dla Windows Server 2012 R2 i 2016. Aby uzyskać więcej informacji, zobacz [Dołączanie serwerów Windows do usługi Defender for Endpoint](configure-server-endpoints.md).

>[!NOTE]
>Windows 7, 8.1, Windows Server 2008 R2 obejmują obsługę czujnika EDR i av przy użyciu System Center Endpoint Protection (SCEP).
