---
title: Środowisko usługi Microsoft Defender dla punktu końcowego w symulowanych atakach
description: Uruchom dostępne przykłady scenariuszy ataków, aby zobaczyć, jak usługa Microsoft Defender dla punktu końcowego może wykrywać, badać naruszenia i reagować na nie.
keywords: test, scenariusz, atak, symulacja, symulowany, diy, Microsoft Defender for Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/20/2018
ms.technology: mde
ms.openlocfilehash: da02e1391b7624dc3e091ca1024a68c5756227a2
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996755"
---
# <a name="experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>Środowisko usługi Microsoft Defender dla punktu końcowego w symulowanych atakach 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-abovefoldlink)

> [!TIP]
>
> - Dowiedz się więcej o najnowszych ulepszeniach w programie Microsoft Defender for Endpoint: Co nowego w [programie Defender for Endpoint?](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/15/whats-new-in-windows-defender-atp/).
> - Program Defender for Endpoint zademonstrował wiodące w branży kable i funkcje wykrywania w ostatnim czasie oceny miTRE. Przeczytaj: [Szczegółowe informacje z miTRE ATT&oceny na podstawie CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

Warto użyć usługi Defender for Endpoint przed dodaniem do usługi więcej niż kilku urządzeń. W tym celu możesz uruchomić zdalnie sterowane symulacyjne ataki na kilku urządzeniach testowych. Po uruchomieniu symulowanych ataków możesz sprawdzić, w jaki sposób program Defender for Endpoint pokazuje złośliwą aktywność i zbadać, jak umożliwia skuteczną reakcję.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby uruchomić dowolną z podanych symulowań, potrzebujesz co najmniej [jednego urządzenia uruchamianego na urządzeniu.](onboard-configure.md)

Przeczytaj dokument instruktażowy z każdym scenariuszem ataków. Każdy dokument zawiera informacje o systemach operacyjnych i wymaganiach aplikacji, a także szczegółowe instrukcje dotyczące scenariusza ataków.

## <a name="run-a-simulation"></a>Uruchamianie symulacyjnej

1. W **samouczkach** \>  \> & oceny punktów końcowych **i samouczków &** i symulacyjnych wybierz jeden z dostępnych scenariuszy ataków, które chcesz symulować:
   - **Scenariusz 1. Dokument jest przenoszony przez backdoor** — symuluje dostarczanie dokumentu o przeznaczycie społecznościowym. W dokumencie jest uruchamiany specjalnie przygotowany backdoor, który zapewnia atakującym kontrolę.
   - **Scenariusz 2. Skrypt programu PowerShell** w atakach bez plików — symulowany jest atak bez pliku, który jest opierany na programie PowerShell, i pokazuje zmniejszenie powierzchni ataków i wykrywanie urządzeń wykrywania złośliwej aktywności pamięci.
   - **Scenariusz 3. Zautomatyzowane** reagowanie na incydenty — wyzwala zautomatyzowane badanie, które automatycznie wykrywa i rekultywuje artefakty naruszenia w celu skalowania wydajności reakcji na incydenty.

2. Pobierz i przeczytaj odpowiedni dokument instruktażowy odpowiedni dla wybranego scenariusza.

3. Pobierz plik symulacyjnej lub skopiuj skrypt symulacyjnej, przechodząc do **samouczków & samouczków** \> & **samouczków**. Możesz pobrać plik lub skrypt na urządzenie testowe, ale nie jest to obowiązkowe.

4. Uruchom plik symulacyjnej lub skrypt na urządzeniu testowym zgodnie z instrukcjami w dokumencie instruktażu.

> [!NOTE]
> Pliki symulacyjne lub skrypty symulowają działania ataków, ale w rzeczywistości są wyszkodliwe i nie będą uszkodzić ani nie łamania urządzenia testowego.
>
> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-belowfoldlink)

## <a name="related-topics"></a>Tematy pokrewne

- [Urządzenia wyniesiene na urządzeniach w](onboard-configure.md)
- [Urządzenia Windows urządzeniach](configure-endpoints.md)
