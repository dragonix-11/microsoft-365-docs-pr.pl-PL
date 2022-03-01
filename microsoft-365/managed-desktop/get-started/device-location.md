---
title: Windows 10 lokalizacji
description: W tym artykule opisano Windows usług lokalizacji dla urządzeń
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: b12f0d188c8347762443cc80e24cfdd7c6280acc
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2022
ms.locfileid: "63013871"
---
# <a name="windows-10-location-service"></a>Windows 10 lokalizacji

Urządzenia w Microsoft Managed Desktop są zarejestrowane za pomocą rozwiązania Windows Autopilot. Ten proces umożliwia nam zarządzanie nimi za pomocą Azure Active Directory i Microsoft Intune.

Domyślnie usługa lokalizacji Windows 10 jest wyłączona, gdy urządzenie jest włączone po raz pierwszy, chyba że ta funkcja jest włączona w ustawieniach prywatności podczas "out of box experience". Te ustawienia są ukryte podczas rejestrowania rozwiązania Autopilot w programie Microsoft Managed Desktop. Aby uzyskać więcej informacji na temat sposobu skonfigurowania rozwiązania Autopilot, zobacz Środowisko pierwszego uruchomienia z rozwiązania [Autopilot i strona stanu rejestracji](esp-first-run.md).

Z tego powodu Microsoft Managed Desktop nie mogą uzyskać lokalizacji urządzenia i ograniczają funkcjonalność kilku Windows, takich jak strefy czasowe. Aby uzyskać więcej informacji na temat Windows 10 lokalizacji, zobacz Windows 10 [usługi lokalizacji i prywatności](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).

Aby uczestniczyć w programie, nie musisz korzystać z usługi Microsoft Managed Desktop. Środowisko użytkownika zostanie ograniczone. Na przykład urządzenia nie będą mogły automatycznie określić strefy czasowej, w których pracują użytkownicy pracują w innej strefie czasowej.

## <a name="enable-the-location-service"></a>Włączanie usługi lokalizacji

Możesz:

- zrezygnować z usługi lokalizacji podczas rejestrowania urządzeń w Microsoft Managed Desktop usługi lub
- Po zarejestrowaniu możesz włączyć lub wyłączyć usługę.

### <a name="opt-in-during-enrollment"></a>Zarejestrowanie się podczas rejestracji

Możesz włączyć Microsoft Managed Desktop lokalizacji. Podczas sekwencji rejestracji zostaniesz poproszony o określenie, czy chcesz zezwolić na Windows 10 lokalizacji na urządzeniach.

### <a name="control-the-location-service-after-enrollment"></a>Kontrolowanie usługi lokalizacji po rejestracji

Usługę lokalizacji można w każdej chwili włączona (lub wyłączona), przesyłając wniosek o pomoc [techniczną za](../working-with-managed-desktop/admin-support.md) pośrednictwem [portalu administracyjnego](access-admin-portal.md).

## <a name="how-microsoft-managed-desktop-configures-the-windows-10-location-service"></a>Jak Microsoft Managed Desktop konfigurowanie usługi Windows 10 lokalizacji

Jeśli zdecydujesz się na korzystanie z usługi lokalizacji, użyjemy minimalnych niezbędnych ustawień bez wpływu na prywatność użytkowników. Aby uzyskać więcej informacji, [zobacz Windows 10 usługi lokalizacji i prywatności](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).

Microsoft Managed Desktop ustawienia prywatności **Lokalizacja w** Windows **w** pozycji **Zezwalaj na dostęp do lokalizacji na tym urządzeniu**. Interfejs użytkownika wygląda następująco:

 :::image type="content" source="../../media/MMD-location-services-UI.png" alt-text="Ustawienia lokalizacji w Windows sieci.":::

> [!NOTE]
> Jeśli zdecydujesz się na korzystanie z usługi lokalizacji, dotyczy to tylko Windows systemu operacyjnego. Aplikacje nie mogą korzystać z usług lokalizacji. Każdy użytkownik może określić, czy zezwolić aplikacjom na uzyskiwanie dostępu do swojej lokalizacji.
