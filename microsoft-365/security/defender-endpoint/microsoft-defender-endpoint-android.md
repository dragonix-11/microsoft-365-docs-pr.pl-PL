---
title: Program Microsoft Defender for Endpoint w systemie Android
ms.reviewer: ''
description: W tym artykule opisano instalowanie i używanie programu Microsoft Defender for Endpoint w systemie Android
keywords: microsoft, defender, Microsoft Defender for Endpoint, android, installation, deploy, uninstallation, intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 7d4e553e89f83f9b641367bb4037b4eb7da21f8b
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011917"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Program Microsoft Defender for Endpoint w systemie Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W tym temacie opisano, jak instalować, konfigurować, aktualizować i używać programu Defender dla punktu końcowego w systemie Android.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych innych firm wraz z usługą Defender for Endpoint w systemie Android może powodować problemy z wydajnością i nieprzewidywalne błędy systemu.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Jak zainstalować program Microsoft Defender for Endpoint w systemie Android

### <a name="prerequisites"></a>Wymagania wstępne

- **Dla użytkowników końcowych**:
  - Licencja programu Microsoft Defender dla punktu końcowego przypisana do użytkowników końcowych aplikacji. Zobacz [Microsoft Defender, aby uzyskać informacje o wymaganiach licencyjnych dotyczących punktów końcowych](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)
  - Intune — Portal firmy aplikację można pobrać ze [sklepu Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) i jest ona dostępna na urządzeniu z systemem Android.
  - Ponadto urządzenia można zarejestrowanych za pośrednictwem aplikacji [](/mem/intune/user-help/enroll-device-android-company-portal) Intune — Portal firmy w celu wymuszenia zasad zgodności urządzeń Intune. Wymaga to przypisania użytkownikowi końcowej licencji Microsoft Intune licencji.
  - Aby uzyskać więcej informacji na temat przypisywania licencji, zobacz [Przypisywanie licencji do użytkowników](/azure/active-directory/users-groups-roles/licensing-groups-assign).

- **Dla administratorów**
   - Dostęp do portalu Microsoft 365 Defender sieci.
   - Dostęp [Microsoft Endpoint Manager administracyjnego do](https://go.microsoft.com/fwlink/?linkid=2109431)
       - Wdeksuj aplikację na zarejestrowanych grupach użytkowników w organizacji.
       - Skonfiguruj program Microsoft Defender dla sygnałów ryzyka punktu końcowego w zasadach ochrony aplikacji.
  
    > [!NOTE]
    > - Program Microsoft Defender for Endpoint rozszerza teraz ochronę na dane organizacji w obrębie zarządzanej aplikacji (MAM) dla urządzeń, które nie są zarejestrowane przy użyciu zarządzania urządzeniami przenośnymi (MDM), ale do zarządzania aplikacjami mobilnymi używa usługi Intune. Obejmuje to również klientów korzystających z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, jednocześnie używających usługi Intune do zarządzania aplikacjami mobilnymi [(MAM](/mem/intune/apps/mam-faq)).
    > - Ponadto usługa Microsoft Defender for Endpoint obsługuje już urządzenia zarejestrowane przy użyciu usługi Intune Mobile Device Management (MDM).


### <a name="network-requirements"></a>Wymagania dotyczące sieci

- Aby program Microsoft Defender dla punktu końcowego systemu Android działał po połączeniu z siecią, konieczne będzie skonfigurowanie zapory/serwera proxy w celu umożliwienia dostępu do usługi [Microsoft Defender dla adresów URL usługi punktu końcowego](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>Wymagania systemowe

- Telefony komórkowe z systemem Android 6.0 lub wyżej. **Telefony komórkowe z systemem Android go, tablety i inne urządzenia przenośne z systemem Android nie są obecnie obsługiwane.**
- Intune — Portal firmy zostanie pobrana i [zainstalowana ze sklepu Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). Aby zasady zgodności urządzeń usługi Intune wymuszały rejestrację urządzeń, jest ona wymagana.

### <a name="installation-instructions"></a>Instrukcje instalacji

Program Microsoft Defender for Endpoint w systemie Android obsługuje instalację na obu trybach zarejestrowanych urządzeń — starszym administratorze urządzenia i urządzeniu z systemem Android Enterprise trybach. **Obecnie urządzenia z profilem służbowym i w pełni zarządzanymi rejestracjami urządzeń użytkowników przez firmy są obsługiwane w systemie Android Enterprise. Obsługa innych trybów Enterprise Android zostanie ogłoszona, gdy tryby będą gotowe.**

- Wdrażanie programu Microsoft Defender for Endpoint w systemie Android jest dostępne za pośrednictwem Microsoft Intune (MDM). Aby uzyskać więcej informacji, zobacz [Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie Android Microsoft Intune](android-intune.md).
- Instalacja programu Microsoft Defender for Endpoint na urządzeniach, które nie zostały zarejestrowane przy użyciu zarządzania urządzeniami przenośnymi Intune (MDM), zobacz Konfigurowanie programu Microsoft Defender pod celu obsługi sygnałów ryzyka dla punktu końcowego w zasadach ochrony aplikacji [(MAM).](android-configure-mam.md)

> [!NOTE]
> **Program Microsoft Defender for Endpoint dla systemu Android jest już dostępny w [sklepie Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx) .**
>
> Możesz połączyć się ze sklepem Google Play z usługi Intune, aby wdrożyć aplikację Microsoft Defender dla punktu końcowego w administratorze urządzenia i aplikacji Enterprise trybachollmentu.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Jak skonfigurować usługę Microsoft Defender dla punktu końcowego w systemie Android

Wskazówki dotyczące konfigurowania programu Microsoft Defender dla funkcji punktu końcowego w systemie Android można uzyskać w tece Konfigurowanie programu [Microsoft Defender dla funkcji punktu końcowego w systemie Android](android-configure.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie Android za pomocą Microsoft Intune](android-intune.md)
- [Konfigurowanie programu Microsoft Defender dla funkcji punktu końcowego w systemie Android](android-configure.md)
- [Podstawy zarządzania aplikacjami mobilnymi (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
