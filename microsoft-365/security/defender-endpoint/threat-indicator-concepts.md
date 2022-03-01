---
title: Opis pojęć analizy zagrożeń w programie Microsoft Defender dla punktu końcowego
description: Tworzenie niestandardowych alertów o zagrożeniach dla organizacji i poznanie pojęć związanych z analizą zagrożeń w programie Microsoft Defender for Endpoint
keywords: analizę zagrożeń, definicje alertów, wskaźniki naruszenia bezpieczeństwa, ioc
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 440f788c4adb757013611bb05621b4eb4f4e9715
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996388"
---
# <a name="understand-threat-intelligence-concepts"></a>Opis pojęć analizy zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-threatindicator-abovefoldlink)

Zaawansowane ataki dotyczące bezpieczeństwa bezpieczeństwa obejmują wiele złożonych złośliwych zdarzeń, atrybutów i informacji kontekstowych. Określenie, które z tych działań można zakwalifikować jako podejrzane, i określenie tych działań może być trudnym zadaniem. Wiedza o znanych atrybutach i nieprawidłowych działaniach specyficznych dla danej branży jest podstawową wiedzą, kiedy można nazwać obserwowane zachowanie jako podejrzane.

Za Microsoft 365 Defender można tworzyć niestandardowe alerty o zagrożeniach, które ułatwiają śledzenie możliwych działań ataków w organizacji. Możesz oflagować podejrzane zdarzenia, aby zasłaniać zawęgiem wskazówek i w miarę możliwości zatrzymać łańcuch ataków. Te niestandardowe alerty o zagrożeniach będą wyświetlane tylko w Twojej organizacji i będą oznaczać zdarzenia, dla których ustawiono śledzenie.

Przed utworzeniem niestandardowych alertów o zagrożeniach należy poznać pojęcia związane z definicjami alertów i wskaźnikami naruszenia zabezpieczeń (IOCs) i relacji między nimi.

## <a name="alert-definitions"></a>Definicje alertów
Definicje alertów to atrybuty kontekstowe, których można używać zbiorczo w celu identyfikowania wczesnych wskazówek dotyczących możliwego ataków na bezpieczeństwo. Te wskaźniki to zwykle połączenie działań, cech i akcji podejmowane przez atakującego w celu pomyślnego osiągnięcia celu ataków. Monitorowanie tych kombinacji atrybutów ma kluczowe znaczenie dla uzyskania punktu wyjścia przed atakami i ewentualnego zakłócania łańcucha zdarzeń przed dotarciem do celu atakującego.

## <a name="indicators-of-compromise-ioc"></a>Wskaźniki naruszenia (IOC)
IOCs to pojedyncze znane złośliwe zdarzenia, które wskazują, że sieć lub urządzenie już zostało naruszone. W odróżnieniu od definicji alertów te wskaźniki są uznawane za dowód naruszenia zabezpieczeń. Są one często widoczne po zakończeniu ataków i osiągnięciu celu, takiego jak ekscygacja. Śledzenie kodów IOCs jest również ważne podczas dochodzenia sądowego. Mimo że nie może on być w stanie schować się za pomocą łańcucha ataków, zbieranie tych wskaźników może być przydatne do tworzenia lepszej ochrony przed ewentualnymi przyszłymi atakami.

## <a name="relationship-between-alert-definitions-and-iocs"></a>Relationship between alert definitions and IOCs
W kontekście usług Microsoft 365 Defender i Microsoft Defender for Endpoint definicje alertów to kontenery dla obiektów IOCs i definiują alert, łącznie z metadanymi, które są wywoływane w celu konkretnego dopasowania IOC. W ramach definicji alertów dostępne są różne metadane. Metadane, takie jak nazwa definicji alertu dla ataków, ważności i opisu, są udostępniane wraz z innymi opcjami.

Każda wartość IOC definiuje logikę wykrywania konkretny na podstawie jej typu, wartości i akcji, która określa sposób dopasowania. Jest ona powiązana z określoną definicją alertu, która definiuje sposób wyświetlania wykrywania jako alertu na konsoli Microsoft 365 Defender serwera.

Oto przykładowa aplikacja IOC:
- Typ: Sha1
- Wartość: 92cfceb39d57d914ed8b14d0e37643de0797ae56
- Akcja: równa się

Relacje wiele-do-jednego z definicjami alertów są typu "wiele-do-jednego", na przykład definicja alertu może mieć wiele odpowiadających jej wartości we/WI.


## <a name="related-topics"></a>Tematy pokrewne
- [Zarządzanie wskaźnikami](manage-indicators.md)
