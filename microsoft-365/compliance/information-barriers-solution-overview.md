---
title: Bariery informacyjne
description: Dowiedz się, jak skonfigurować bariery informacyjne w Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, zgodność, bariery informacyjne
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- m365solution-scenario
ms.openlocfilehash: aaba1c642d4615d3eb5163736450f3f8f3c27062
ms.sourcegitcommit: 99494a5530ad64802f341573ad42796134190296
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2022
ms.locfileid: "65396184"
---
# <a name="information-barriers"></a>Bariery informacyjne

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft 365 umożliwia komunikację i współpracę między grupami i organizacjami oraz obsługuje sposoby ograniczania komunikacji i współpracy między określonymi grupami użytkowników w razie potrzeby. Może to obejmować sytuacje lub scenariusze, w których chcesz ograniczyć komunikację i współpracę między dwiema grupami, aby uniknąć konfliktu interesów w organizacji. Może to również obejmować sytuacje, w których konieczne jest ograniczenie komunikacji i współpracy między niektórymi osobami w organizacji w celu ochrony informacji wewnętrznych.

Microsoft Purview Bariery informacyjne (IB) są obsługiwane w usługach Microsoft Teams, SharePoint Online i OneDrive dla Firm. Administrator zgodności lub administrator IB może zdefiniować zasady umożliwiające lub uniemożliwiające komunikację między grupami użytkowników w Microsoft Teams. Zasady IB mogą być używane w takich sytuacjach:

- Użytkownik w grupie przedsiębiorców dnia nie powinien komunikować się ani udostępniać plików zespołowi ds. marketingu
- Personel finansowy pracujący nad poufnymi informacjami firmy nie powinien komunikować się ani udostępniać plików określonym grupom w organizacji
- Wewnętrzny zespół z materiałami z tajemnicy handlowej nie powinien dzwonić ani rozmawiać online z osobami w niektórych grupach w swojej organizacji
- Zespół badawczy powinien dzwonić lub rozmawiać online tylko z zespołem deweloperów produktów

## <a name="configure-information-barriers"></a>Konfigurowanie barier informacyjnych

Aby skonfigurować protokół IB dla organizacji, wykonaj następujące kroki:

![Kroki barier w zakresie informacji o rozwiązaniu ryzyka wewnętrznego.](../media/ir-solution-ib-steps.png)

1. Dowiedz się więcej o [barierach informacyjnych](information-barriers.md)
2. Konfigurowanie [wymagań wstępnych i uprawnień](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)
3. [Segmentuj użytkowników w organizacji](information-barriers-policies.md#step-2-segment-users-in-your-organization)
4. Tworzenie i konfigurowanie [zasad IB](information-barriers-policies.md#step-3-create-ib-policies)
5. Stosowanie [zasad IB](information-barriers-policies.md#step-4-apply-ib-policies)

## <a name="more-information-about-information-barriers"></a>Więcej informacji o barierach informacyjnych

- [Atrybuty zasad IB](information-barriers-attributes.md)
- [Edytowanie lub usuwanie zasad IB](information-barriers-edit-segments-policies.md)
