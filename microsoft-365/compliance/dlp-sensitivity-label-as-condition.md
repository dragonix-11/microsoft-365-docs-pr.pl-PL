---
title: Używanie etykiet poufności jako warunków w zasadach DLP
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się więcej o usługach i typach elementów, których można używać jako warunków w zasadach DLP
ms.openlocfilehash: bf0fcb327b2869e21a54de22822d0d51c72e25b8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438471"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>Używanie etykiet poufności jako warunków w zasadach DLP

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Etykiet [poufności](sensitivity-labels.md) można użyć jako warunku w zasadach DLP dla tych lokalizacji:

- Exchange Online wiadomości e-mail
- SharePoint Online
- witryny OneDrive dla Firm
- urządzenia Windows 10

Etykiety poufności są wyświetlane jako opcja na liście **Zawartość zawiera** .

> [!div class="mx-imgBorder"]
> ![etykieta poufności jako warunek.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> **Etykiety poufności** jako warunek nie będą dostępne, jeśli wybrano **Teams wiadomości czatu i kanału** jako lokalizację do zastosowania zasad DLP.


## <a name="supported-items-scenarios-and-policy-tips"></a>Obsługiwane elementy, scenariusze i porady dotyczące zasad

Etykiet poufności można używać jako warunków dla tych elementów i w tych scenariuszach.

### <a name="supported-items"></a>Obsługiwane elementy

|Usługa  |Typ elementu  |Porada dotycząca zasad dostępna dla zasad  |Wykonalne  |
|---------|---------|---------|---------|
|Exchange    |wiadomość e-mail         |Tak         |Tak         |
|Exchange    |załącznik wiadomości e-mail         |Nr         |Tak *         |
|SharePoint Online     |elementy w usłudze SharePoint Online         |Tak         |Tak         |
|OneDrive dla Firm     |Elementy         |Tak         |Tak         |
|Teams     |komunikaty Teams i kanałów         |nie dotyczy         |nie dotyczy         |
|Teams     |Załączniki         |Tak **         |Tak **         |
|urządzenia Windows 10     |Elementy         |Tak         |Tak         |
|MCAS (wersja zapoznawcza) |Elementy         |Tak         |Tak         |

\*Wykrywanie przez DLP załączników wiadomości e-mail z etykietami poufności jest obsługiwane tylko w przypadku typów plików Office opartych na formacie Open XML.

\** Załączniki wysyłane w Teams ponad 1:1 czat lub kanały są automatycznie przekazywane do OneDrive dla Firm i SharePoint. Jeśli więc SharePoint Online lub OneDrive dla Firm są uwzględnione jako lokalizacje w zasadach DLP, załączniki wysyłane w Teams zostaną automatycznie uwzględnione w zakresie tego warunku. Teams jako lokalizacja nie musi być wybrana w zasadach DLP.

> [!NOTE]
> Zdolność DLP do wykrywania etykiet poufności w SharePoint i OneDrive dla firm jest ograniczona. Aby uzyskać więcej informacji, zobacz [Włączanie etykiet poufności dla plików Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>Obsługiwane scenariusze

- Administrator DLP będzie mógł wyświetlić listę wszystkich etykiet poufności w dzierżawie, gdy zdecyduje się na uwzględnienie co najmniej jednej etykiety poufności jako warunku.

- Używanie etykiet poufności jako warunku jest obsługiwane we wszystkich obciążeniach, jak wskazano w powyższej macierzy obsługi.

- Porady dotyczące zasad DLP będą nadal wyświetlane w obciążeniach (z wyjątkiem Outlook Win32) dla zasad DLP, które zawierają etykietę poufności jako warunek.

- Etykiety poufności będą również wyświetlane jako część wiadomości e-mail raportu o zdarzeniu, jeśli zostaną dopasowane zasady DLP z etykietą poufności jako warunkiem.

- Szczegóły etykiety poufności będą również wyświetlane w dzienniku inspekcji zgodności reguł DLP dla dopasowania zasad DLP, który zawiera etykietę poufności jako warunek.


### <a name="support-policy-tips"></a>Porady dotyczące zasad pomocy technicznej


|Obciążenia  |Obsługiwane/nieobsługiwane porady dotyczące zasad  |
|---------|---------|
|OWA |    Obsługiwane     |
|Outlook Win 32    |  nieobsługiwane       |
|SharePoint   |   Obsługiwane      |
|OneDrive dla Firm    |    Obsługiwane     |
|urządzenia punktu końcowego   |  nieobsługiwane       |
