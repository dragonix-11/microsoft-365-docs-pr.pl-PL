---
title: Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS
ms.reviewer: ''
description: Opis sposobu instalowania i używania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, ios, overview, installation, deploy, uninstallation, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: dcc67b2d2a9ad03dc1235eebd577e3525ab07a03
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665937"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS** zapewnia ochronę przed wyłudzaniem informacji i niebezpiecznymi połączeniami sieciowymi z witryn internetowych, wiadomości e-mail i aplikacji. Wszystkie alerty będą dostępne za pośrednictwem jednego okienka szkła w portalu Microsoft 365 Defender. Portal udostępnia zespołom zabezpieczeń scentralizowany widok zagrożeń na urządzeniach z systemem iOS wraz z innymi platformami.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych obok usługi Defender for Endpoint w systemie iOS może powodować problemy z wydajnością i nieprzewidywalne błędy systemu.

## <a name="pre-requisites"></a>Wymagania wstępne

**Dla użytkowników końcowych**

- Ochrona punktu końcowego w usłudze Microsoft Defender licencji przypisanej do użytkowników końcowych aplikacji. Zobacz [wymagania dotyczące licencjonowania Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **W przypadku zarejestrowanych urządzeń**:
    - Urządzenia są [rejestrowane](/mem/intune/user-help/enroll-your-device-in-intune-ios) za pośrednictwem aplikacji Intune — Portal firmy w celu wymuszenia Intune zasad zgodności urządzeń. Wymaga to, aby użytkownikowi końcowemu przypisano licencję Microsoft Intune.
    - Intune — Portal firmy aplikację można pobrać z [App Store firmy Apple](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >Firma Apple nie zezwala na przekierowywanie użytkowników do pobierania innych aplikacji ze sklepu z aplikacjami, dlatego użytkownik musi wykonać ten krok przed dołączeniem do Ochrona punktu końcowego w usłudze Microsoft Defender aplikacji).
    
    - Urządzenia są zarejestrowane w Azure Active Directory. Wymaga to zalogowania użytkownika końcowego za pośrednictwem [aplikacji Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **W przypadku niezarejestrowanych urządzeń**: urządzenia są zarejestrowane w Azure Active Directory. Wymaga to zalogowania użytkownika końcowego za pośrednictwem [aplikacji Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- Aby uzyskać więcej informacji na temat przypisywania licencji, zobacz [Przypisywanie licencji do użytkowników](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**Dla administratorów**

- Dostęp do portalu Microsoft 365 Defender.

- Dostęp do [centrum administracyjnego Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), aby:
   - Wdróż aplikację w zarejestrowanych grupach użytkowników w organizacji.
   - Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sygnałów ryzyka w zasadach ochrony aplikacji (MAM)


    > [!NOTE]
    > - Ochrona punktu końcowego w usłudze Microsoft Defender teraz rozszerza ochronę na dane organizacji w aplikacji zarządzanej dla tych, którzy nie korzystają z zarządzania urządzeniami przenośnymi (MDM), ale używają Intune do zarządzania aplikacjami mobilnymi. Ta pomoc techniczna jest również rozszerzana na klientów korzystających z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, a jednocześnie korzysta z Intune do [zarządzania aplikacjami mobilnymi (MAM).](/mem/intune/apps/mam-faq)
    > - Ponadto Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje już urządzenia zarejestrowane przy użyciu Intune zarządzania urządzeniami przenośnymi (MDM).  

**Wymagania systemowe**

- Urządzenie z systemem iOS z systemem iOS 12.0 lub nowszym. Obsługiwane są również tablety iPad. *Należy pamiętać, że od 31 marca do 2022 r. minimalna obsługiwana wersja systemu iOS według Ochrona punktu końcowego w usłudze Microsoft Defender będzie mieć system iOS 13.0.*

- Urządzenie jest zarejestrowane w [aplikacji Intune — Portal firmy](https://apps.apple.com/us/app/intune-company-portal/id719171358) lub zarejestrowane w Azure Active Directory za pośrednictwem [Microsoft Authenticator](https://apps.apple.com/app/microsoft-authenticator/id983156458) przy użyciu tego samego konta.

## <a name="installation-instructions"></a>Instrukcje instalacji

Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS można wykonać za pośrednictwem Microsoft Endpoint Manager (MEM), a obsługiwane są zarówno urządzenia nadzorowane, jak i nienadzorowane. Użytkownicy końcowi mogą również bezpośrednio zainstalować aplikację ze [sklepu Apple App Store](https://aka.ms/mdatpiosappstore).

- Aby uzyskać informacje na temat wdrażania na zarejestrowanych urządzeniach za pośrednictwem Microsoft Endpoint Manager lub Intune, zobacz [Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS](ios-install.md).
- Aby uzyskać informacje na temat korzystania z usługi Defender for Endpoint w zasadach ochrony aplikacji (MAM), zobacz [Konfigurowanie zasad ochrony aplikacji w celu uwzględnienia sygnałów ryzyka usługi Defender for Endpoint (MAM)](ios-install-unmanaged.md)

## <a name="resources"></a>Zasoby

- Bądź na bieżąco z nadchodzącymi wersjami, odwiedzając stronę [Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS](ios-whatsnew.md) lub naszym [blogu](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- Przekazywanie opinii za pośrednictwem systemu opinii w aplikacji lub za pośrednictwem [ujednoliconej konsoli zabezpieczeń](https://security.microsoft.com)

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS za pośrednictwem Intune dla zarejestrowanych urządzeń](ios-install.md)
- [Konfigurowanie zasad ochrony aplikacji w celu uwzględnienia sygnałów ryzyka usługi Defender for Endpoint (MAM)](ios-install-unmanaged.md)
- [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)
- [Konfigurowanie zasad dostępu warunkowego na podstawie wyniku ryzyka urządzenia z Ochrona punktu końcowego w usłudze Microsoft Defender](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [Podstawy zarządzania aplikacjami mobilnymi (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
