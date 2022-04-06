---
title: Krok nr 3. Konfigurowanie zasad zgodności dla urządzeń z Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: Dowiedz się, jak utworzyć zasady zgodności urządzeń określające minimalne wymagania dotyczące dostępu urządzenia do środowiska.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: f93642984ecb2439ab6e4ad484ea4f6f3303c0ce
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651372"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>Krok nr 3. Konfigurowanie zasad zgodności dla urządzeń z Intune

Rejestrowanie urządzeń w celu Intune daje możliwość uzyskania jeszcze większego bezpieczeństwa i kontroli nad danymi w środowisku. [Krok 2. Rejestrowanie urządzeń w celu Intune](manage-devices-with-intune-enroll.md) szczegółów, jak to zrobić przy użyciu Intune. W tym artykule opisano następny krok, który polega na skonfigurowaniu zasad zgodności urządzeń. 

![Kroki zarządzania urządzeniami](../media/devices/intune-mdm-step-2.png#lightbox)

Chcesz mieć pewność, że urządzenia uzyskujące dostęp do aplikacji i danych spełniają minimalne wymagania, na przykład są chronione hasłem lub przypinaniem, a system operacyjny jest aktualny. Zasady zgodności to sposób definiowania wymagań, które muszą spełniać urządzenia. Usługa MEM używa tych zasad zgodności do oznaczania urządzenia jako zgodnego lub niezgodnego Ten stan binarny jest przekazywany do usługi Azure AD, która może używać tego stanu w regułach dostępu warunkowego, aby zezwolić urządzeniu na dostęp do zasobów lub uniemożliwić mu dostęp do zasobów. 

## <a name="configuring-device-compliance-policies"></a>Konfigurowanie zasad zgodności urządzeń

Te wskazówki są ściśle skoordynowane z zalecanymi [zasadami Zero Trust tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md).

Na tej ilustracji przedstawiono, gdzie praca nad definiowaniem zasad zgodności mieści się w ogólnym Zero Trust zalecanego zestawu zasad. 

[![Zero Trust zasad dostępu do tożsamości i urządzeń](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

Na tej ilustracji definiowanie zasad zgodności urządzeń jest zależnością w celu osiągnięcia zalecanego poziomu ochrony w ramach struktury Zero Trust. 

Aby skonfigurować zasady zgodności urządzeń, skorzystaj z zalecanych wskazówek i ustawień określonych w [zasadach Zero Trust tożsamości i dostępu do urządzeń](../security/office-365-security/microsoft-365-policies-configurations.md). Poniższa tabela zawiera linki bezpośrednio do instrukcji dotyczących konfigurowania tych zasad w Intune, w tym zalecanych ustawień dla każdej platformy.


|Policies (zasady) |Więcej informacji  |Licencjonowanie |
|---------|---------|---------|
|[Definiowanie zasad zgodności urządzeń ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  Jedna zasada dla każdej platformy       |  Microsoft 365 E3 lub E5       |
|  |         |         |

## <a name="next-steps"></a>Następne kroki

Przejdź do [kroku 4. Wymagaj urządzeń w dobrej kondycji i zgodnych,](manage-devices-with-intune-require-compliance.md) aby uzyskać instrukcje dotyczące tworzenia reguły dostępu warunkowego w usłudze Azure AD.