---
title: Rejestrowanie urządzeń z systemami iOS/iPadOS i Android w środowisku testowym Microsoft 365 dla przedsiębiorstw
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
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Skorzystaj z tego przewodnika po laboratorium testowym, aby zarejestrować urządzenia w środowisku testowym Microsoft 365 i zarządzać nimi zdalnie.
ms.openlocfilehash: 5cefabf6b995754f6febe117776ad2de97443df0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092938"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Rejestrowanie urządzeń z systemem iOS i Android w Microsoft 365 dla środowiska testowego przedsiębiorstwa

*Tego przewodnika laboratorium testowego można używać tylko w przypadku Microsoft 365 dla środowisk testowych przedsiębiorstwa.*

W tym artykule opisano sposób rejestrowania i testowania podstawowych funkcji zarządzania urządzeniami przenośnymi dla urządzeń z systemami iOS/iPadOS i Android w Microsoft 365 dla środowiska testowego przedsiębiorstwa.

Rejestrowanie urządzeń z systemami iOS/iPadOS i Android w środowisku testowym obejmuje trzy fazy:
- [Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Faza 2. Rejestrowanie urządzeń z systemami iOS/iPadOS i Android](#phase-2-enroll-your-ios-and-android-devices)
- [Faza 3. Zdalne zarządzanie urządzeniami z systemami iOS/iPadOS i Android](#phase-3-manage-your-ios-and-android-devices-remotely)

![Przewodniki laboratorium testowego dla chmury firmy Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Aby uzyskać wizualną mapę na wszystkie artykuły w stosie przewodnika Microsoft 365 dla laboratorium testowego dla przedsiębiorstw, przejdź do [Microsoft 365 stosu przewodników laboratorium testowego dla przedsiębiorstw](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Faza 1. Tworzenie Microsoft 365 dla środowiska testowego przedsiębiorstwa

Jeśli chcesz zarejestrować urządzenia z systemami iOS/iPadOS i Android w sposób uproszczony z minimalnymi wymaganiami, postępuj zgodnie z instrukcjami w temacie [Uproszczona konfiguracja podstawowa](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Jeśli chcesz zarejestrować urządzenia z systemami iOS/iPadOS i Android w symulowanym przedsiębiorstwie, postępuj zgodnie z instrukcjami w temacie [Uwierzytelnianie przekazywane](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testowanie automatycznego licencjonowania i członkostwa w grupach nie wymaga symulowanego środowiska testowego przedsiębiorstwa, które obejmuje symulowany intranet połączony z Internetem i synchronizację katalogów dla lasu Active Directory Domain Services (AD DS). Jest ona dostępna w tym miejscu jako opcja, dzięki czemu można przetestować automatyczne licencjonowanie i członkostwo w grupach, a następnie eksperymentować z nim w środowisku reprezentującym typową organizację.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Faza 2. Rejestrowanie urządzeń z systemami iOS i Android

Jeśli rozważasz rozwiązanie do zarządzania urządzeniami przenośnymi (MDM) do zarządzania urządzeniami, możesz użyć Microsoft Intune. Podczas pracy z dowolnym dostawcą mdm, w tym Intune, urządzenia są "zarejestrowane". Po zarejestrowaniu otrzymują skonfigurowane funkcje i ustawienia. 

W Intune istnieje kilka sposobów rejestrowania urządzeń z systemami iOS/iPadOS i Android. Możesz wybrać opcję rejestracji, która najlepiej sprawdza się w Twojej organizacji. Aby uzyskać więcej informacji i wskazówek, zobacz następujące artykuły:

- [Przewodnik wdrażania: rejestrowanie urządzeń z systemem iOS i iPadOS w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Przewodnik wdrażania: rejestrowanie urządzeń z systemem Android w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Jeśli wszystko jest gotowe do użycia Intune do zarządzania urządzeniami i potrzebujesz wskazówek, poniższe informacje mogą pomóc:

- [Omówienie zarządzania urządzeniami](/mem/intune/fundamentals/what-is-device-management)
- [Samouczek: przewodnik Intune w Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Przewodnik wdrażania: Konfigurowanie lub przechodzenie do Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Faza 3. Zdalne zarządzanie urządzeniami z systemami iOS i Android

Microsoft Intune udostępnia funkcję zdalnego blokowania i resetowania kodu dostępu. Jeśli ktoś utraci urządzenie, możesz zdalnie zablokować urządzenie. Jeśli ktoś zapomni kodu dostępu, możesz go zdalnie zresetować.

- Aby zdalnie zablokować urządzenie z systemem iOS/iPadOS lub Android, zobacz [Zdalne blokowanie urządzeń z Intune](/mem/intune/remote-actions/device-remote-lock).
- Aby zdalnie zresetować kod dostępu, zobacz [Resetowanie lub usuwanie kodu dostępu urządzenia w Intune](/mem/intune/remote-actions/device-passcode-reset).

Aby uzyskać dodatkowe zadania, które można uruchomić zdalnie, zobacz [dostępne akcje urządzenia](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Następny krok

Zapoznaj się z dodatkowymi [funkcjami i możliwościami zarządzania urządzeniami przenośnymi](m365-enterprise-test-lab-guides.md#mobile-device-management) w środowisku testowym.

## <a name="see-also"></a>Zobacz też

[Microsoft 365 dla przewodników laboratorium testowego w przedsiębiorstwie](m365-enterprise-test-lab-guides.md)
  
[Zasady zgodności urządzeń dla Microsoft 365 dla środowiska testowego przedsiębiorstwa](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)
