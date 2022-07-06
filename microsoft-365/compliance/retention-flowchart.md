---
title: Schemat blokowy do określania, kiedy element jest zachowywany lub usuwany
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Użyj schematu blokowego, aby określić wynik, gdy element ma wiele zasad przechowywania lub etykietę przechowywania i zasady przechowywania
ms.openlocfilehash: 4e5c1cf887144f89764e88a39ba14a95a2df576c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633460"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>Schemat blokowy określający, kiedy element zostanie zachowany lub trwale usunięty

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Użyj poniższego schematu blokowego, aby zastosować [zasady przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence) do elementu, aby określić, czy system będzie go zachować, czy trwale usunąć go w wyniku etykiety przechowywania lub zasad przechowywania.

Ten przepływ logiki jest używany dla elementu w przypadku zastosowania jednego z następujących warunków:

- Zastosowano więcej niż jedną zasadę przechowywania
- Istnieje etykieta przechowywania i co najmniej jedna zasady przechowywania

Gdy element podlega blokadzie zbierania elektronicznych materiałów dowodowych (lub starszym technologiom archiwum sporów sądowych lub In-Place blokady), zawsze będzie przechowywany przed podjęciem decyzji o zasadach przechowywania i etykiecie przechowywania.

Jeśli którykolwiek z terminów używanych w tym schemacie blokowym nie jest ci znany, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).


   ![Schemat blokowy określający, kiedy element zostanie zachowany lub trwale usunięty.](../media/retention-flowchart.svg)

> [!NOTE]
> Ważne jest rozróżnienie między najdłuższym okresem przechowywania elementu a najdłuższym określonym okresem w zasadach przechowywania lub etykiecie. Podobnie między najkrótszą datą wygaśnięcia elementu a najkrótszym określonym okresem w zasadach przechowywania.
> 
> Aby uzyskać więcej informacji, zobacz objaśnienie po grafice w sekcji [zasady przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence) .
