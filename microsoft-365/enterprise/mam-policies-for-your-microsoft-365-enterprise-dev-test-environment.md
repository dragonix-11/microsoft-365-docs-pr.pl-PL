---
title: Zasady zgodności urządzeń dla Microsoft 365 dla środowiska testowego przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Skorzystaj z tego przewodnika po laboratorium testowym, aby dodać zasady zgodności urządzeń Intune do Microsoft 365 dla środowiska testowego przedsiębiorstwa.
ms.openlocfilehash: 3037ca846fe74fb8de51c78799e69c510821a034
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099460"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Zasady zgodności urządzeń dla Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

W tym artykule opisano sposób dodawania zasad zgodności urządzeń Intune dla urządzeń Windows 10 i Aplikacje Microsoft 365 dla przedsiębiorstw do Microsoft 365 dla środowiska testowego przedsiębiorstwa.

Dodanie zasad zgodności urządzeń Intune obejmuje dwie fazy:
- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Tworzenie zasad zgodności urządzeń dla urządzeń Windows 10](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz skonfigurować zasady zarządzania aplikacjami mobilnymi tylko w lekki sposób z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz skonfigurować zasady zarządzania aplikacjami mobilnymi w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie automatycznego licencjonowania i członkostwa w grupach nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna tutaj jako opcja, dzięki czemu można przetestować automatyczne licencjonowanie i członkostwo w grupie i eksperymentować z nim w środowisku reprezentującym typową organizację.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Faza 2. Tworzenie zasad zgodności urządzeń dla urządzeń Windows 10

W tej fazie utworzysz zasady zgodności urządzeń dla urządzeń Windows 10. Ta faza używa Microsoft Intune i [centrum administracyjnego Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), aby dodać grupę i utworzyć zasady zgodności.

1. Przejdź do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com), zaloguj się do subskrypcji laboratorium testowego Microsoft 365 przy użyciu konta administratora globalnego i wybierz <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">centrum administracyjne Endpoint Manager</a>.

    Jeśli zostanie wyświetlony komunikat podobny do komunikatu Nie **włączono jeszcze zarządzania urządzeniami**, wybierz pozycję Intune jako urząd MDM. Aby zapoznać się z konkretnymi [krokami, zobacz Ustawianie urzędu zarządzania urządzeniami przenośnymi](/mem/intune/fundamentals/mdm-authority-set).

    Centrum administracyjne Endpoint Manager koncentruje się na zarządzaniu urządzeniami i zarządzaniu aplikacjami. Aby zapoznać się z przewodnikiem po tym centrum administracyjnym, zobacz [Samouczek: przewodnik Intune w Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. W **obszarze Grupy** dodaj nową **Microsoft 365** lub grupę **zabezpieczeń** o nazwie **Managed Windows 10 użytkowników urządzeń** z **przypisanym** typem członkostwa. W następnych krokach przypiszesz zasady zgodności do tej grupy. 

    Aby uzyskać szczegółowe informacje na temat **Microsoft 365** lub grup **zabezpieczeń**, zobacz [Dodawanie grup w celu organizowania użytkowników i urządzeń](/mem/intune/fundamentals/groups-add).

3. W **obszarze Urządzenia** utwórz zasady zgodności Windows 10. Przypisz te zasady do utworzonej grupy **użytkowników urządzeń Windows 10 zarządzanych**.

    W zasadach można blokować proste hasła, wymagać zapory, wymagać uruchomienia usługi Ochrony przed złośliwym kodem w usłudze Microsoft Defender i nie tylko. Zasady zgodności zwykle obejmują ustawienia podstawowe lub minimum, które powinno mieć każde urządzenie.

    Aby uzyskać szczegółowe informacje na temat dostępnych ustawień zgodności, które można skonfigurować, zobacz [Ustawianie reguł dla zarządzanych urządzeń przy użyciu zasad zgodności](/mem/intune/protect/device-compliance-get-started).

Po zakończeniu masz zasady zgodności urządzeń do testowania elementów członkowskich w grupie **Zarządzane Windows 10 użytkowników urządzeń**.
  
## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi [funkcjami i możliwościami zarządzania urządzeniami przenośnymi](m365-enterprise-test-lab-guides.md#mobile-device-management) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md).
  
[Rejestrowanie urządzeń z systemem iOS i Android w Microsoft 365 dla środowiska testowego przedsiębiorstwa](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
