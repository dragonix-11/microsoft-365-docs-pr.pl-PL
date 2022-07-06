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
ms.openlocfilehash: 55803a2c354890264f99753af2aa6337cf49182a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632404"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>Używanie etykiet poufności jako warunków w zasadach DLP

Etykiet [poufności](sensitivity-labels.md) można użyć jako warunku w zasadach DLP dla tych lokalizacji:

- Exchange Online wiadomości e-mail
- SharePoint Online
- witryny OneDrive dla Firm
- urządzenia Windows 10

Etykiety poufności są wyświetlane jako opcja na liście **Zawartość zawiera** .

> [!div class="mx-imgBorder"]
> ![etykieta poufności jako warunek.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> **Etykiety poufności** jako warunek nie będą dostępne, jeśli wybrano opcję **Wiadomości czatu i kanału usługi Teams** jako lokalizację do zastosowania zasad DLP.


## <a name="supported-items-scenarios-and-policy-tips"></a>Obsługiwane elementy, scenariusze i porady dotyczące zasad

Etykiet poufności można używać jako warunków dla tych elementów i w tych scenariuszach.

### <a name="supported-items"></a>Obsługiwane elementy

|Usługa  |Typ elementu  |Porada dotycząca zasad dostępna dla zasad  |Wykonalne  |
|---------|---------|---------|---------|
|Exchange    |wiadomość e-mail         |Tak         |Tak         |
|Exchange    |załącznik wiadomości e-mail         |Nr         |Tak *         |
|SharePoint Online     |elementy w usłudze SharePoint Online         |Tak         |Tak         |
|OneDrive dla Firm     |Elementy         |Tak         |Tak         |
|Teams     |Komunikaty zespołów i kanałów         |nie dotyczy         |nie dotyczy         |
|Teams     |Załączniki         |Tak **         |Tak **         |
|urządzenia Windows 10     |Elementy         |Tak         |Tak         |
|MCAS (wersja zapoznawcza) |Elementy         |Tak         |Tak         |

\* Wykrywanie przez DLP załączników wiadomości e-mail z etykietami poufności jest obsługiwane tylko w przypadku typów plików pakietu Office opartych na formacie Open XML.

\** Załączniki wysyłane w usłudze Teams w ramach czatu 1:1 lub kanałów są automatycznie przekazywane do OneDrive dla Firm i programu SharePoint. Jeśli więc usługa SharePoint Online lub OneDrive dla Firm są uwzględnione jako lokalizacje w zasadach DLP, załączniki wysyłane w usłudze Teams zostaną automatycznie uwzględnione w zakresie tego warunku. W zasadach DLP nie trzeba wybierać aplikacji Teams jako lokalizacji.

> [!NOTE]
> Możliwość wykrywania etykiet poufności w programach SharePoint i OneDrive dla firm jest ograniczona. Aby uzyskać więcej informacji, zobacz [Włączanie etykiet poufności dla plików pakietu Office w programach SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>Obsługiwane scenariusze

- Administracja DLP będą mogli wyświetlić listę wszystkich etykiet poufności w dzierżawie, gdy zdecydują się na uwzględnienie co najmniej jednej etykiety poufności jako warunku.

- Używanie etykiet poufności jako warunku jest obsługiwane we wszystkich obciążeniach, jak wskazano w powyższej macierzy obsługi.

- Porady dotyczące zasad DLP będą nadal wyświetlane w obciążeniach (z wyjątkiem programu Outlook Win32) dla zasad DLP, które zawierają etykietę poufności jako warunek.

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
