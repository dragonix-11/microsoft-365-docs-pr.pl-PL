---
title: Zasady zgodności urządzeń dla twojego Microsoft 365 w środowisku testowania przedsiębiorstwa
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Skorzystaj z tego przewodnika laboratorium testowego, aby dodać zasady zgodności urządzeń intune do Microsoft 365 dla środowiska testowania przedsiębiorstwa.
ms.openlocfilehash: ec73211a21e9e064b729b93d9e88b7c5c69b21fe
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977614"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Zasady zgodności urządzeń dla twojego Microsoft 365 w środowisku testowania przedsiębiorstwa

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

W tym artykule opisano, jak dodać zasady zgodności urządzeń intune dla Windows 10 i Aplikacje Microsoft 365 dla przedsiębiorstw do środowiska testowania Microsoft 365 przedsiębiorstwa.

Dodawanie zasad zgodności urządzeń usługi Intune obejmuje dwa etapy:
- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Tworzenie zasad zgodności urządzeń dla Windows 10 urządzenia](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz skonfigurować zasady zarządzania aplikacjami mobilnymi tylko w sposób podstawowy z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w [tece Konfiguracja podstawowa.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Jeśli chcesz skonfigurować zasady zarządzania aplikacjami mobilnymi w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w tece uwierzytelnianie [pass-through](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie automatycznego licencjonowania i członkostwa w grupach nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Ta opcja jest dostępna jako opcja, która umożliwia testowanie automatycznego licencjonowania i członkostwa w grupach oraz eksperymentowanie z nim w środowisku reprezentującym typową organizację.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Etap 2. Tworzenie zasad zgodności urządzeń dla Windows 10 urządzenia

W tym etapie utworzysz zasady zgodności urządzeń dla Windows 10 urządzeniach. W tej fazie Microsoft Intune grupy i centrum [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) administracyjnego, aby dodać grupę, oraz utworzyć zasady zgodności.

1. Przejdź do centrum [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com), zaloguj się do subskrypcji Microsoft 365 testowej za pomocą konta administratora globalnego i wybierz centrum administracyjne usługi Endpoint Manager <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">administracyjne.</a>

    Jeśli jest wyświetlany komunikat podobny do **Nie** włączono jeszcze zarządzania urządzeniami, wybierz pozycję Intune jako urząd mdm. Aby uzyskać szczegółowe instrukcje, zobacz [Ustawianie urzędu zarządzania urządzeniami przenośnymi](/mem/intune/fundamentals/mdm-authority-set).

    Centrum Endpoint Manager dotyczy zarządzania urządzeniami i aplikacji. Aby uzyskać przewodnik po tym centrum administracyjnym, zobacz [Samouczek: instruktaż usługi Intune w programie Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. W **grupach** dodaj **nową Microsoft 365** zabezpieczeń o nazwie Użytkownicy  Windows 10 urządzeniach **z** **przypisanym typem** członkostwa. W następnych krokach przypiszesz do tej grupy swoje zasady zgodności. 

    Aby uzyskać szczegółowe instrukcje oraz uzyskać informacje na **temat** Microsoft 365 lub **grup** zabezpieczeń, zobacz Dodawanie grup w celu [organizowania użytkowników i urządzeń](/mem/intune/fundamentals/groups-add).

3. Na **urządzeniach** utwórz zasady Windows 10 zgodności. Przypisz te zasady do **utworzonej grupy Windows 10 użytkowników** urządzeń.

    W Twoich zasadach możesz blokować proste hasła, wymagać zapory, wymagać działania usługi Microsoft Defender Antimalware i nie tylko. Zasady zgodności zwykle zawierają podstawowe ustawienia lub minimalne wartości, które powinny być stosowane na każdym urządzeniu.

    Aby uzyskać szczegółowe instrukcje i uzyskać informacje na temat dostępnych ustawień zgodności, które można skonfigurować, zobacz Ustawianie reguł dla urządzeń, które zarządzasz, za pomocą zasad [zgodności](/mem/intune/protect/device-compliance-get-started).

Po zakończeniu masz zasady zgodności urządzenia do testowania członków w grupie Zarządzane Windows 10 **użytkowników** urządzeń.
  
## <a name="next-step"></a>Następny krok

Poznaj dodatkowe [funkcje i możliwości zarządzania urządzeniami](m365-enterprise-test-lab-guides.md#mobile-device-management) przenośnymi w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md).
  
[Rejestrowanie urządzeń z systemami iOS i Android do Microsoft 365 do środowiska testowania przedsiębiorstwa](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
