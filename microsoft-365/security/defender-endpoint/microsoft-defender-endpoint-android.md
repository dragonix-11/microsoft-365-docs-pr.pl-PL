---
title: Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android
ms.reviewer: ''
description: Opis sposobu instalowania i używania Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, android, instalacja, wdrażanie, odinstalowywanie, intune
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
ms.openlocfilehash: ea1c551c216dffe8d9ac4e0cedd5679146483e5e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666245"
---
# <a name="microsoft-defender-for-endpoint-on-android"></a>Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W tym temacie opisano sposób instalowania, konfigurowania, aktualizowania i używania usługi Defender for Endpoint w systemie Android.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych innych firm obok usługi Defender for Endpoint w systemie Android może powodować problemy z wydajnością i nieprzewidywalne błędy systemowe.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-android"></a>Jak zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android

### <a name="prerequisites"></a>Wymagania wstępne

- **Dla użytkowników końcowych**:
  - Ochrona punktu końcowego w usłudze Microsoft Defender licencji przypisanej do użytkowników końcowych aplikacji. Zobacz [wymagania dotyczące licencjonowania Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/minimum-requirements#licensing-requirements)
  - Intune — Portal firmy aplikację można pobrać z [sklepu Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) i jest dostępna na urządzeniu z systemem Android.
  - Ponadto urządzenia można [zarejestrować](/mem/intune/user-help/enroll-device-android-company-portal) za pośrednictwem aplikacji Intune — Portal firmy w celu wymuszenia Intune zasad zgodności urządzeń. Wymaga to, aby użytkownikowi końcowemu przypisano licencję Microsoft Intune.
  - Aby uzyskać więcej informacji na temat przypisywania licencji, zobacz [Przypisywanie licencji do użytkowników](/azure/active-directory/users-groups-roles/licensing-groups-assign).

- **Dla administratorów**
   - Dostęp do portalu Microsoft 365 Defender.
   - Dostęp [Microsoft Endpoint Manager centrum administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431) do
       - Wdróż aplikację w zarejestrowanych grupach użytkowników w organizacji.
       - Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sygnałów ryzyka w zasadach ochrony aplikacji.
  
    > [!NOTE]
    > - Ochrona punktu końcowego w usłudze Microsoft Defender teraz rozszerza ochronę na dane organizacji w ramach aplikacji zarządzanej (MAM) dla urządzeń, które nie są zarejestrowane przy użyciu zarządzania urządzeniami przenośnymi (MDM), ale używają Intune do zarządzania aplikacjami mobilnymi. Ta pomoc techniczna jest również rozszerzana na klientów korzystających z innych rozwiązań do zarządzania mobilnością w przedsiębiorstwie, a jednocześnie korzysta z Intune do [zarządzania aplikacjami mobilnymi (MAM).](/mem/intune/apps/mam-faq)
    > - Ponadto Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje już urządzenia zarejestrowane przy użyciu Intune zarządzania urządzeniami przenośnymi (MDM).


### <a name="network-requirements"></a>Wymagania dotyczące sieci

- Aby Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android działały po nawiązaniu połączenia z siecią, należy skonfigurować zaporę/serwer proxy, aby [umożliwić dostęp do adresów URL usługi Ochrona punktu końcowego w usłudze Microsoft Defender](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

### <a name="system-requirements"></a>Wymagania systemowe

- Telefony komórkowe z systemem Android 6.0 lub nowszym. **Telefony komórkowe z systemem Android go, tabletami i innymi urządzeniami przenośnymi z systemem Android nie są obecnie obsługiwane.**
- Intune — Portal firmy aplikacja jest pobierana z [sklepu Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) i instalowana. Rejestrowanie urządzeń jest wymagane do wymuszania zasad zgodności Intune urządzeniami.

### <a name="installation-instructions"></a>Instrukcje instalacji

Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android obsługuje instalację w obu trybach zarejestrowanych urządzeń — w starszych trybach administratora urządzeń i systemu Android Enterprise. **Obecnie urządzenia osobiste z profilem służbowym i w pełni zarządzanymi rejestracjami urządzeń użytkowników należących do firmy są obsługiwane w systemie Android Enterprise. Obsługa innych trybów Enterprise systemu Android zostanie ogłoszona, gdy będzie gotowa.**

- Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android odbywa się za pośrednictwem Microsoft Intune (MDM). Aby uzyskać więcej informacji, zobacz [Deploy Ochrona punktu końcowego w usłudze Microsoft Defender on Android with Microsoft Intune (Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android z Microsoft Intune](android-intune.md)).
- Instalacja Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach, które nie są zarejestrowane przy użyciu Intune zarządzania urządzeniami przenośnymi (MDM), zobacz [Konfigurowanie sygnałów ryzyka Ochrona punktu końcowego w usłudze Microsoft Defender w aplikacji zasady ochrony (MAM).](android-configure-mam.md)

> [!NOTE]
> **Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android jest teraz dostępna w [sklepie Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx).**
>
> Możesz nawiązać połączenie z sklepem Google Play z Intune, aby wdrożyć aplikację Ochrona punktu końcowego w usłudze Microsoft Defender w trybach administratora urządzeń i systemu Android Enterprise rejestracji.

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-android"></a>Jak skonfigurować Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android

Wskazówki dotyczące konfigurowania Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu Android są dostępne w [temacie Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu Android](android-configure.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Wdrażaj usługę ochrony punktu końcowego w usłudze Microsoft Defender w systemie Android za pomocą usługi Microsoft Intune](android-intune.md)
- [Konfiguruj usługę ochrony punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
- [Podstawy zarządzania aplikacjami mobilnymi (MAM)](/mem/intune/apps/app-management#mobile-application-management-mam-basics)
