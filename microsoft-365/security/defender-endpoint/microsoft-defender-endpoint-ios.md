---
title: Program Microsoft Defender for Endpoint w systemie iOS
ms.reviewer: ''
description: W tym artykule opisano, jak zainstalować program Microsoft Defender for Endpoint i używać go w systemie iOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, omówienie, instalacja, wdrożenie, dezinstalacja, intune
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
ms.openlocfilehash: c144eb3cd0cec2d96f20294475618e7e9c49c816
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014820"
---
# <a name="microsoft-defender-for-endpoint-on-ios"></a>Program Microsoft Defender for Endpoint w systemie iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

**Program Microsoft Defender for Endpoint w systemie iOS** zapewnia ochronę przed wyłudzaniem informacji i niebezpiecznymi połączeniami sieciowymi z witryn internetowych, wiadomości e-mail i aplikacji. Wszystkie alerty będą dostępne za pośrednictwem pojedynczego okienka w okienku zeszytowym w Microsoft 365 Defender wiadomości. Portal udostępnia zespołom zabezpieczeń scentralizowany widok zagrożeń na urządzeniach z systemem iOS wraz z innymi platformami.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych innych firm wraz z usługą Defender for Endpoint w systemie iOS może powodować problemy z wydajnością i nieprzewidywalne błędy systemu.

## <a name="pre-requisites"></a>Wymagania wstępne

**Dla użytkowników końcowych**

- Licencja programu Microsoft Defender dla punktu końcowego przypisana do użytkowników końcowych aplikacji. Zobacz [Program Microsoft Defender, aby uzyskać informacje o wymaganiach licencyjnych dotyczących punktów końcowych](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements).

- **Dla zarejestrowanych urządzeń**:
    - Urządzenia są rejestrowane za [pośrednictwem](/mem/intune/user-help/enroll-your-device-in-intune-ios) aplikacji Intune — Portal firmy, aby wymusić zasady zgodności urządzeń Intune. Wymaga to przypisania użytkownikowi końcowej licencji Microsoft Intune licencji.
    - Intune — Portal firmy aplikację można pobrać ze [sklepu App Store firmy Apple](https://apps.apple.com/us/app/intune-company-portal/id719171358).
    
    >[!NOTE]
    >Firma Apple nie zezwala na przekierowywanie użytkowników do pobierania innych aplikacji ze sklepu z aplikacjami, więc ten krok musi zostać wykonane przez użytkownika przed dodaniem do aplikacji Microsoft Defender dla punktu końcowego).
    
    - Urządzenia są zarejestrowane w Azure Active Directory. Wymaga to zalogowania się użytkownika końcowego za [pośrednictwem Microsoft Authenticator aplikacji](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- **W przypadku nierejestrowanych** urządzeń: urządzenia są zarejestrowane w Azure Active Directory. Wymaga to zalogowania się użytkownika końcowego za [pośrednictwem Microsoft Authenticator aplikacji](https://apps.apple.com/app/microsoft-authenticator/id983156458).

- Aby uzyskać więcej informacji na temat przypisywania licencji, zobacz [Przypisywanie licencji do użytkowników](/azure/active-directory/users-groups-roles/licensing-groups-assign).

**Dla administratorów**

- Dostęp do portalu Microsoft 365 Defender sieci.

- Dostęp do [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431):
   - Wdeksuj aplikację na zarejestrowanych grupach użytkowników w organizacji.
   - Konfigurowanie programu Microsoft Defender pod celu obsługi sygnałów ryzyka dla punktu końcowego w zasadach ochrony aplikacji (MAM)


    > [!NOTE]
    > - Program Microsoft Defender for Endpoint rozszerza teraz ochronę na dane organizacji w zarządzanej aplikacji dla osób, które nie zarządzają urządzeniami przenośnymi (MDM), ale zarządzają aplikacjami mobilnymi za pomocą usługi Intune. Obejmuje to również klientów korzystających z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, jednocześnie używających usługi Intune do zarządzania aplikacjami mobilnymi [(MAM](/mem/intune/apps/mam-faq)).
    > - Ponadto usługa Microsoft Defender for Endpoint obsługuje już urządzenia zarejestrowane przy użyciu usługi Intune Mobile Device Management (MDM).  

**Wymagania systemowe**

- Urządzenie z systemem iOS w systemie iOS 12.0 lub wyżej. Obsługiwane są również tablety iPad. *Od 31 marca 2022 r. minimalna obsługiwana przez usługę Microsoft Defender for Endpoint wersja systemu iOS będzie w systemie iOS 13.0.*

- Urządzenie zostało zarejestrowane za pomocą aplikacji [Intune — Portal firmy lub](https://apps.apple.com/us/app/intune-company-portal/id719171358) zarejestrowane w usłudze Azure Active Directory za [pośrednictwem](https://apps.apple.com/app/microsoft-authenticator/id983156458) Microsoft Authenticator przy użyciu tego samego konta.

## <a name="installation-instructions"></a>Instrukcje instalacji

Wdrażanie programu Microsoft Defender for Endpoint w systemie iOS można wykonać za pośrednictwem programu Microsoft Endpoint Manager (MEM) oraz urządzeń nadzorowanych i niesąparowanych. Użytkownicy końcowi mogą również zainstalować aplikację bezpośrednio ze sklepu [z aplikacjami firmy Apple](https://aka.ms/mdatpiosappstore).

- Aby uzyskać informacje na temat wdrażania na zarejestrowanych urządzeniach za pośrednictwem usługi Microsoft Endpoint Manager lub Intune, zobacz [Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie iOS](ios-install.md).
- Aby uzyskać informacje na temat używania usługi Defender dla punktu końcowego w zasadach ochrony aplikacji (MAM), zobacz Konfigurowanie zasad ochrony aplikacji tak, aby uwzględniały program Defender dla sygnałów ryzyka punktu [końcowego (MAM)](ios-install-unmanaged.md)

## <a name="resources"></a>Zasoby

- Bądź na bieżąco z informacjami o nadchodzących wersjach, odwiedzając stronę Co nowego w programie [Microsoft Defender for Endpoint w systemie iOS](ios-whatsnew.md) lub nasz [blog](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

- Opinie w systemie opinii w aplikacji lub za [pośrednictwem ujednoliconej konsoli zabezpieczeń](https://security.microsoft.com)

## <a name="next-steps"></a>Następne kroki

- [Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie iOS za pośrednictwem usługi Intune dla zarejestrowanych urządzeń](ios-install.md)
- [Konfigurowanie zasad ochrony aplikacji tak, aby uwzględniały usługę Defender dla sygnałów ryzyka punktu końcowego (MAM)](ios-install-unmanaged.md)
- [Konfigurowanie programu Microsoft Defender dla punktu końcowego w funkcjach systemu iOS](ios-configure-features.md)
- [Konfigurowanie zasad dostępu warunkowego na podstawie wyników ryzyka urządzenia z programu Microsoft Defender dla punktu końcowego](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios)
- [Podstawy zarządzania aplikacjami mobilnymi (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
