---
title: Dołączanie i wydoszczenie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi JAMF Pro dla klientów programu Microsoft Defender for Endpoint (wersja preview)
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
description: Dowiedz się, jak dołączać i wydojać urządzenia macOS do Microsoft 365 zgodności przy użyciu usługi JAMF Pro dla klientów programu Microsoft Defender dla punktów końcowych (wersja zapoznawcza)
ms.openlocfilehash: 7e2109f52590cc4d9ad23700fa4b51a09ae4b5db
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526474"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview"></a>Dołączanie i wydoszczenie urządzeń macOS w rozwiązaniach zgodności przy użyciu usługi JAMF Pro dla klientów programu Microsoft Defender for Endpoint (wersja preview)

Za pomocą usług JAMF Pro w nowych rozwiązaniach dotyczących zgodności można Microsoft 365 macOS.

> [!IMPORTANT]
> Skorzystaj z tej ***procedury, jeśli program*** Microsoft Defender for Endpoint (MDE) został wdrożony na urządzeniach z systemem macOS

**Dotyczy:**

- Klienci, którzy wdrożyli aplikację MDE na swoich urządzeniach z systemem macOS.
- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, że urządzenia [z systemem macOS są przyłączone do usługi Azure AD](https://docs.jamf.com/10.30.0/jamf-pro/administrator-guide/Azure_AD_Integration.html)
- Upewnij się, że [urządzenia z systemem macOS są zarządzane za pośrednictwem usługi JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) 
- Instalowanie przeglądarki Edge w wersji 95+ na urządzeniach z systemem macOS 

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>Urządzenia w nowych rozwiązaniach Microsoft 365 zgodności przy użyciu usługi JAMF Pro

Proces dołączania urządzenia z systemem macOS do rozwiązań zgodności jest procesem wielofazowym.

### <a name="download-the-configuration-files"></a>Pobieranie plików konfiguracji

1. Te pliki będą potrzebne do tej procedury.

|wymagany dla |źródło |
|---------|---------|
|ułatwienia dostępu |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku     |[fullconfig.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Preferencja MDE |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> Możesz pobrać pliki *.mobileconfig* pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
> - accessibility.mobileconfig
> - fullconfig.mobileconfig
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie pobranie ponownie połączonego pliku lub pojedynczego aktualizowanego pliku.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>Aktualizowanie istniejącego profilu domeny preferencji MDE przy użyciu konsoli JAMF PRO

1. Zaktualizuj schema.xml o pobrany plik **schema.json** .

1. W **obszarze Właściwości domeny preferencji MDE** wybierz te ustawienia
    - Funkcje 
        - Użyj rozszerzeń systemowych: `enabled` — wymagane dla rozszerzeń sieciowych w Catalina
        - Korzystanie z ochrony przed utratą danych: `enabled`

1. Wybierz **kartę Zakres** .

1. Wybierz grupy, w których chcesz wdrożyć ten profil konfiguracji.

1. Wybierz pozycję **Zapisz**. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Aktualizowanie profilu konfiguracji w celu udzielenia pełnego dostępu do dysku

1. Zaktualizuj istniejący pełny profil dostępu do dysku przy użyciu **pliku fullconfig.mobileconfig** .

1. Upload **plik fullconfig.mobileconfig** do usługi JAMF. Zobacz Wdrażanie [niestandardowych profilów konfiguracji za pomocą usługi JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>Udzielanie dostępu do funkcji DLP

1. Użyj pobranego wcześniej pliku accessibility.mobileconfig.

1. Upload do usługi JAMF zgodnie z opisem w tece Wdrażanie niestandardowych profilów konfiguracji za [pomocą usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>Sprawdź urządzenie z systemem macOS 

1. Uruchom ponownie urządzenie z systemem macOS.

1. Otwórz **okno Preferencje** >  **systemowePropliki**.

1. Powinien zostać wyświetlony:
    - Accessiblity
    - Pełny dostęp do dysku
    - Profil rozszerzenia kernelu
    - MAU
    - Dołączanie do USŁUGI MDATP
    - Preferencje MDE
    - Profil zarządzania
    - Filtr sieci
    - Powiadomienia
    - Profil rozszerzenia systemu

## <a name="offboard-macos-devices-using-jamf-pro"></a>Urządzenia przenośne z systemem macOS korzystające z usługi JAMF Pro

> [!IMPORTANT]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.

Aby wyłączyć urządzenie z systemem macOS, wykonaj następujące czynności

 1. W **obszarze Właściwości domeny preferencji MDE** usuń wartości tych ustawień.
    - Funkcje 
        - Używanie rozszerzeń systemowych
        - Korzystanie z ochrony przed utratą danych

1. Wybierz pozycję **Zapisz**.
