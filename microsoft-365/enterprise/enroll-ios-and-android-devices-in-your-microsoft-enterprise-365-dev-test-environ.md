---
title: Rejestrowanie urządzeń z systemami iOS/iPadOS i Android Microsoft 365 w środowisku testowania przedsiębiorstwa
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
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Skorzystaj z tego przewodnika laboratorium testowego, aby zarejestrować urządzenia Microsoft 365 testowania środowiska testowego i zarządzać nimi zdalnie.
ms.openlocfilehash: 7610348febcc8c2054c50d7f7a6f1433e9b62306
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985087"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Rejestrowanie urządzeń z systemami iOS i Android do Microsoft 365 do środowiska testowania przedsiębiorstwa

*Ten przewodnik laboratorium testowego może być używany tylko w Microsoft 365 testowych w przedsiębiorstwie.*

W tym artykule opisano, jak zarejestrować i przetestować podstawowe funkcje zarządzania urządzeniami przenośnymi dla urządzeń z systemami iOS/iPadOS i Android w środowisku testowania Microsoft 365 przedsiębiorstwa.

Rejestrowanie urządzeń z systemami iOS/iPadOS i Android w środowisku testowym składa się z trzech etapów:
- [Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Etap 2. Rejestrowanie urządzeń z systemami iOS/iPadOS i Android](#phase-2-enroll-your-ios-and-android-devices)
- [Etap 3. Zdalne zarządzanie urządzeniami z systemami iOS/iPadOS i Android](#phase-3-manage-your-ios-and-android-devices-remotely)

![Przewodniki laboratorium testowego dotyczące chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Aby uzyskać wizualną mapę do wszystkich artykułów w stosie przewodników laboratorium testowego Microsoft 365 dla przedsiębiorstw, przejdź do tematu Microsoft 365 — przewodnik laboratorium testowego w [przedsiębiorstwie](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Etap 1. Tworzenie środowiska testowego Microsoft 365 przedsiębiorstwa

Jeśli chcesz zarejestrować urządzenia z systemami iOS/iPadOS i Android w sposób minimalny, postępuj zgodnie z instrukcjami w konfiguracji [podstawowej.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Jeśli chcesz zarejestrować urządzenia z systemami iOS/iPadOS i Android w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w tece uwierzytelnianie [pass-through](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie automatycznego licencjonowania i członkostwa w grupach nie wymaga symulowanego środowiska testowania przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Usługi domenowe w usłudze Active Directory (AD DS). Jest on dostarczany jako opcja, która umożliwia testowanie automatycznego licencjonowania i członkostwa w grupach i eksperymentowanie z nim w środowisku reprezentującym typową organizację.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Etap 2. Rejestrowanie urządzeń z systemami iOS i Android

Jeśli rozważasz zarządzanie swoimi urządzeniami za pomocą rozwiązania do zarządzania urządzeniami przenośnymi (MDM), możesz skorzystać z Microsoft Intune. Podczas pracy z dowolnym dostawcą usługi MDM, w tym z usługą Intune, urządzenia są "rejestrowane". Po zarejestrowaniu osoby te otrzymują skonfigurowane przez Ciebie funkcje i ustawienia. 

W usłudze Intune istnieje kilka sposobów zarejestrowania urządzeń z systemami iOS/iPadOS i Android. Możesz wybrać opcję rejestracji, która będzie najlepsza dla Twojej organizacji. Aby uzyskać więcej informacji i wskazówki, zobacz następujące artykuły:

- [Przewodnik wdrażania: Rejestrowanie urządzeń z systemami iOS i iPadOS Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Przewodnik wdrażania: rejestrowanie urządzeń z systemem Android w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Jeśli chcesz korzystać z usługi Intune do zarządzania urządzeniami i potrzebujesz wskazówek, poniższe informacje mogą okazać się pomocne:

- [Omówienie zarządzania urządzeniami](/mem/intune/fundamentals/what-is-device-management)
- [Samouczek: przegląd usługi Intune w aplikacji Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Przewodnik wdrażania: konfigurowanie lub przechodzenie do Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Etap 3. Zdalne zarządzanie urządzeniami z systemami iOS i Android

Microsoft Intune oferuje funkcję zdalnego blokowania i resetowania kodu dostępu. Jeśli ktoś utraci swoje urządzenie, możesz je zdalnie zablokować. Jeśli ktoś zapomni kod dostępu, możesz go zdalnie zresetować.

- Aby zdalnie zablokować urządzenie z systemem iOS/iPadOS lub Android, zobacz [Zdalne blokowanie urządzeń za pomocą usługi Intune](/mem/intune/remote-actions/device-remote-lock).
- Aby zdalnie zresetować kod dostępu, zobacz [Resetowanie lub usuwanie kodu dostępu urządzenia w usłudze Intune](/mem/intune/remote-actions/device-passcode-reset).

Aby uzyskać informacje o dodatkowych zadaniach, które można uruchamiać zdalnie, zobacz [Dostępne akcje urządzenia](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Następny krok

Poznaj dodatkowe [funkcje i możliwości zarządzania urządzeniami](m365-enterprise-test-lab-guides.md#mobile-device-management) przenośnymi w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 laboratorium testowego dla przedsiębiorstw](m365-enterprise-test-lab-guides.md)
  
[Zasady zgodności urządzeń dla twojego Microsoft 365 w środowisku testowania przedsiębiorstwa](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)
