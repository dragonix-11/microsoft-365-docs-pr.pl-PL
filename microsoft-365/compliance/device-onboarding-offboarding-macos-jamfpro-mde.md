---
title: Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu narzędzia JAMF Pro dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Dowiedz się, jak dołączać i dołączać urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu narzędzia JAMF Pro dla klientów Ochrona punktu końcowego w usłudze Microsoft Defender
ms.openlocfilehash: 97ab1dbccc28cd1f9d14635c2fa351d0295202c1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622926"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers"></a>Dołączanie i odłączanie urządzeń z systemem macOS do rozwiązań zgodności przy użyciu narzędzia JAMF Pro dla klientów usługi Ochrony punktu końcowego w usłudze Microsoft Defender

Za pomocą narzędzia JAMF Pro można dołączyć urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview.

> [!IMPORTANT]
> Użyj tej procedury ***, jeśli wdrożono*** Ochrona punktu końcowego w usłudze Microsoft Defender (MDE) na urządzeniach z systemem macOS

**Dotyczy:**

- Klienci, którzy wdrożyli rozwiązanie MDE na swoich urządzeniach z systemem macOS.
- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)


## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, że [urządzenia z systemem macOS są zarządzane za pośrednictwem narzędzia JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) i są skojarzone z tożsamością (Azure AD połączoną nazwą UPN) za pośrednictwem narzędzia JAMF Connect lub Intune.
- Instalowanie przeglądarki v95+ Edge na urządzeniach z systemem macOS

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Dołączanie urządzeń do rozwiązań usługi Microsoft Purview przy użyciu narzędzia JAMF Pro

Dołączanie urządzenia z systemem macOS do rozwiązań zgodności jest procesem wielofazowym.

### <a name="download-the-configuration-files"></a>Pobieranie plików konfiguracji

1. Te pliki będą potrzebne do tej procedury.

|plik wymagany do |Źródła |
|---------|---------|
|Dostępności |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Preferencja zarządzania urządzeniami przenośnymi |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> Pliki *mobileconfig* można pobrać pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie ponowne pobranie połączonego pliku lub pojedynczego zaktualizowanego pliku indywidualnie.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>Aktualizowanie istniejącego profilu domeny preferencji MDE przy użyciu konsoli JAMF PRO

1. Zaktualizuj profil schema.xml przy użyciu właśnie pobranego pliku **schema.json** .

1. W obszarze **Właściwości domeny preferencji mde** wybierz te ustawienia
    - Funkcje 
        - Korzystanie z rozszerzeń systemowych: `enabled` — wymagane dla rozszerzeń sieciowych w catalina
        - Ochrona przed utratą danych: `enabled`

1. Wybierz kartę **Zakres** .

1. Wybierz grupy do wdrożenia tego profilu konfiguracji.

1. Wybierz pozycję **Zapisz**. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Aktualizowanie profilu konfiguracji w celu udzielenia pełnego dostępu do dysku

1. Zaktualizuj istniejący profil pełnego dostępu do dysku przy użyciu pliku **fulldisk.mobileconfig** .

1. Przekaż plik **fulldisk.mobileconfig** do narzędzia JAMF. Zapoznaj się [z tematem Wdrażanie niestandardowych profilów konfiguracji przy użyciu narzędzia JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>Udzielanie dostępu ułatwień dostępu do usługi DLP

1. Użyj wcześniej pobranego pliku accessibility.mobileconfig.

1. Przekaż do narzędzia JAMF zgodnie z opisem w [temacie Wdrażanie niestandardowych profilów konfiguracji przy użyciu narzędzia Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>Sprawdzanie urządzenia z systemem macOS 

1. Uruchom ponownie urządzenie z systemem macOS.

1. Otwórz **profile** **preferencji systemowych** > .

1. Powinny zostać wyświetlone następujące elementy:
    - Accessiblity
    - Pełny dostęp do dysku
    - Profil rozszerzenia jądra
    - MAU
    - Dołączanie MDATP
    - Preferencje zarządzania urządzeniami przenośnymi
    - Profil zarządzania
    - Filtr sieciowy
    - Powiadomienia
    - Profil rozszerzenia systemu

## <a name="offboard-macos-devices-using-jamf-pro"></a>Odłączanie urządzeń z systemem macOS przy użyciu narzędzia JAMF Pro

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.

Aby odłączyć urządzenie z systemem macOS, wykonaj następujące kroki

 1. W obszarze **Właściwości domeny preferencji mde** usuń wartości dla tych ustawień
    - Funkcje 
        - Korzystanie z rozszerzeń systemu
        - Używanie ochrony przed utratą danych

1. Wybierz pozycję **Zapisz**.
