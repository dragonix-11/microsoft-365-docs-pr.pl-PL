---
title: Krok nr 3. Konfigurowanie zasad zgodności dla urządzeń za pomocą usługi Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: Dowiedz się, jak tworzyć zasady zgodności urządzeń określające minimalne wymagania dotyczące uzyskiwania dostępu do środowiska przez urządzenie.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 7e55ad6bf1d1cb7d95e43cb23b9c74decc8548df
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015769"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>Krok nr 3. Konfigurowanie zasad zgodności dla urządzeń za pomocą usługi Intune

Zarejestrowanie urządzeń w zarządzaniu umożliwia jeszcze większe bezpieczeństwo i kontrolę nad danymi w środowisku. [Krok 2. Zarejestruj urządzenia w szczegółach](manage-devices-with-intune-enroll.md) zarządzania, jak to zrobić za pomocą usługi Intune i rozwiązania Autopilot. W tym artykule o pierwszym kroku, czyli skonfigurowaniu zasad zgodności urządzeń. 

![Kroki zarządzania urządzeniami](../media/devices/intune-mdm-step-2.png#lightbox)

Chcesz mieć pewność, że urządzenia, które mają dostęp do Twoich aplikacji i danych, spełniają minimalne wymagania, na przykład są chronione hasłem lub przypinaniem, a system operacyjny jest aktualny. Zasady zgodności są sposobem definiowania wymagań, które muszą spełnić urządzenia. MEM używa tych zasad zgodności do oznaczania urządzenia jako zgodnego lub niezgodnego Ten stan binarny jest przekazywany do usługi Azure AD, która może używać tego stanu w zasadach dostępu warunkowego w celu umożliwienia lub uniemożliwiania urządzeniu uzyskiwania dostępu do zasobów. 

## <a name="configuring-device-compliance-policies"></a>Konfigurowanie zasad zgodności urządzeń

Te wskazówki są ściśle skoordynowane z zalecanymi zasadami [dostępu do tożsamości i](../security/office-365-security/microsoft-365-policies-configurations.md) urządzeń bez zaufania.

Na poniższej ilustracji przedstawiono miejsce, w którym definiowanie zasad zgodności jest zgodne z ogólnym zestawem zalecanych zasad zerowego zaufania. 

[![Zasady zerowego zaufania w zakresie tożsamości i dostępu do urządzeń](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

Na poniższej ilustracji zdefiniowanie zasad zgodności urządzeń jest współzależnością osiągnięcia zalecanego poziomu ochrony w ramach struktury zerowego zaufania. 

Aby skonfigurować zasady zgodności urządzeń, skorzystaj z zalecanych wskazówek i ustawień określonych w zasadach zerowego zaufania dotyczących tożsamości [i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md). W poniższej tabeli znajdują się linki bezpośrednio do instrukcji dotyczących konfigurowania tych zasad w usłudze Intune, w tym do zalecanych ustawień poszczególnych platform.


|Policies (zasady) |Więcej informacji  |Licencjonowanie |
|---------|---------|---------|
|[Definiowanie zasad zgodności urządzeń ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  Jedna zasada dla każdej platformy       |  Microsoft 365 E3 lub E5       |
|  |         |         |

## <a name="next-steps"></a>Następne kroki

Przejdź do [kroku 4. Wymagaj urządzeń o dobrej kondycji](manage-devices-with-intune-require-compliance.md) i zgodności, aby uzyskać instrukcje dotyczące tworzenia reguły dostępu warunkowego w usłudze Azure AD.