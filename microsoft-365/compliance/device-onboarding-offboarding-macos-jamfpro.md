---
title: Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu narzędzia JAMF Pro
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
description: Dowiedz się, jak dołączać i dołączać urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu narzędzia JAMF Pro
ms.openlocfilehash: bf15868b865afa80146df2b16199caf360a55ce2
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953432"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Dołączanie i dołączanie urządzeń z systemem macOS do rozwiązań usługi Microsoft Purview przy użyciu narzędzia JAMF Pro

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Za pomocą narzędzia JAMF Pro można dołączyć urządzenia z systemem macOS do rozwiązań usługi Microsoft Purview, takich jak ochrona przed utratą danych punktów końcowych.

> [!IMPORTANT]
> Użyj tej procedury, jeśli ***na*** urządzeniach z systemem macOS nie wdrożono Ochrona punktu końcowego w usłudze Microsoft Defender (MDE)

**Dotyczy:**

- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, że [urządzenia z systemem macOS są zarządzane za pośrednictwem narzędzia JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) i są skojarzone z tożsamością (nazwa UPN przyłączona do usługi Azure AD) za pośrednictwem Połączenie jamf lub Intune.
- Instalowanie przeglądarki v95+ Edge na urządzeniach z systemem macOS

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Dołączanie urządzeń do rozwiązań usługi Microsoft Purview przy użyciu Pro JAMF

1. Te pliki będą potrzebne do tej procedury.

|Plik wymagany do|Źródło|
|---|---|
|Dołączanie pakietu|Pobrany z **pakietu dołączania** portalu zgodności, nazwa pliku *DeviceComplianceOnboarding.plist*|
|Dostępności|[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku|[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Filtr sieciowy| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Rozszerzenia systemu|[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|Preferencja zarządzania urządzeniami przenośnymi|[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|Preferencja MAU|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Pakiet instalacyjny|pobrany z portalu zgodności **Pakiet instalacyjny**, nazwa *\*pliku wdav.pkg*\*|

> [!TIP]
> Pliki *mobileconfig* można pobrać pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
>
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie ponowne pobranie połączonego pliku lub pojedynczego zaktualizowanego pliku.

Dołączanie urządzenia z systemem macOS do rozwiązań zgodności jest procesem wielofazowym.

### <a name="get-the-device-onboarding-package"></a>Pobieranie pakietu dołączania urządzenia

1. W **centrum zgodności** otwórz **Ustawienia** >  **Device Onboarding** i wybierz pozycję **Dołączanie**.

1. W obszarze **Wybierz system operacyjny, aby rozpocząć proces dołączania** wybierz system **macOS**

1. W obszarze **Metoda wdrażania** wybierz pozycję **Mobile Zarządzanie urządzeniami/Microsoft Intune**

1. Wybierz pozycję **Pobierz pakiet dołączania**

1. Wyodrębnij zawartość pakietu dołączania urządzenia. W folderze JAMF powinien zostać wyświetlony plik *DeviceComplainceOnboarding.plist* .

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Tworzenie profilu konfiguracji Pro JAMF dla pakietu dołączania

1. Utwórz nowy profil konfiguracji w Pro JAMF. Zapoznaj się z [przewodnikiem administratorów Pro JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Użyj następujących wartości:
    - Nazwa: `MDATP onboarding for macOS`
    - Opis: `MDATP EDR onboarding for macOS`
    - Kategorii: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

2. W konsoli Pro JAMF > **Ustawienia niestandardowe & aplikacji** wybierz pozycję **Przekaż**, a następnie **dodaj**. Użyj tej wartości:
    - Domena preferencji: `com.microsoft.wdav.atp`

3. Wybierz **pozycję Przekaż** i wybierz plik dołączania **DeviceComplianceOnboarding.plist**.

4. Wybierz kartę **zakresu** .

5. Wybierz komputery docelowe.

6. Wybierz pozycję **Zapisz**.

7. Wybierz pozycję **Done** (Gotowe).

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>Konfigurowanie domeny preferencji przy użyciu konsoli JAMF PRO

> [!IMPORTANT]
> Jako wartości Domeny preferencji należy użyć pliku ***com.microsoft.wdav** _. Ochrona punktu końcowego w usłudze Microsoft Defender używa tej nazwy i _ *_com.microsoft.wdav.ext_** do załadowania ustawień zarządzanych.

1. Utwórz nowy profil konfiguracji w Pro JAMF. Zapoznaj się z [przewodnikiem administratorów Pro JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Użyj następujących wartości:
    - Nazwa: `MDATP MDAV configuration settings`
    - Opis: pozostaw to puste
    - Kategorii: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

1. Na karcie **Application & Custom Ustawienia** wybierz pozycję **Aplikacje zewnętrzne**, wybierz pozycję **Dodaj** i wybierz pozycję **Schemat niestandardowy** dla domeny preferencji. Użyj tej wartości:
    - Domena preferencji: `com.microsoft.wdav`

1. Wybierz **pozycję Dodaj schemat** i **Upload**, aby przekazać plik *schema.json*.

1. Wybierz pozycję **Zapisz**.

1. W obszarze **Właściwości domeny preferencji** wybierz te ustawienia
    - Funkcje
        - Korzystanie z rozszerzeń systemowych: `enabled` — wymagane dla rozszerzeń sieciowych w catalina
        - Ochrona przed utratą danych: `enabled`
    - Aparat antywirusowy > tryb pasywny: `true|false`. Użyj polecenia `true`, jeśli wdrażasz tylko DLP. Użyj `false` wartości lub nie przypisz jej w przypadku wdrażania DLP i Ochrona punktu końcowego w usłudze Microsoft Defender (MDE).

1. Wybierz kartę **Zakres** .

1. Wybierz grupy do wdrożenia tego profilu konfiguracji.

1. Wybierz pozycję **Zapisz**.

### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Tworzenie i wdrażanie profilu konfiguracji dla usługi Microsoft AutoUpdate (MAU)

1. Utwórz plik konfiguracji jamf Pro przy użyciu **pliku com.microsoft.autoupdate2.plist**. Zapoznaj się z [przewodnikiem administratorów Pro JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Użyj następujących wartości:
    - Nazwa: `MDATP MDAV MAU settings`
    - Opis: `Microsoft AutoUPdate settings for MDATP for macOS`
    - Kategorii: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

1. W **obszarze & niestandardowe Ustawienia** wybierz **pozycję Upload** i **Dodaj**.

1. W **obszarze Preferencje wprowadź domenę**`com.microsoft.autoupdate2`, a następnie wybierz **pozycję Upload**.

1. Wybierz plik **com.microsoft.autoupdate2.plist** .

1. Wybierz pozycję **Zapisz**.

1. Wybierz kartę **Zakres** .

1. Wybierz komputery docelowe.

1. Wybierz pozycję **Zapisz**.

1. Wybierz pozycję **Done** (Gotowe).

### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Tworzenie i wdrażanie profilu konfiguracji w celu udzielenia pełnego dostępu do dysku

1. Użyj pliku **fulldisk.mobileconfig** .

1. Upload plik **fulldisk.mobileconfig** do pliku JAMF. Zapoznaj się [z tematem Wdrażanie niestandardowych profilów konfiguracji przy użyciu Pro JAMF](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Tworzenie i wdrażanie profilu konfiguracji dla rozszerzeń systemu

1. Utwórz plik konfiguracji jamf Pro przy użyciu procedur w [przewodniku jamf Pro administratorów](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Użyj następujących wartości:
    - Nazwa: `MDATP MDAV System Extensions`
    - Opis: `MDATP system extensions`
    - Kategorii: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

1. W obszarze Profil **rozszerzeń systemu** wprowadź następujące wartości:
    - Nazwa wyświetlana: `Microsoft Corp. System Extensions`
    - Typy rozszerzeń systemu: `Allowed System Extensions`
    - Identyfikator zespołu: `UBF8T346G9`
    - Dozwolone rozszerzenia systemowe: `com.microsoft.wdav.epsext`, i `com.microsoft.wdav.netext`

1. Wybierz kartę **Zakres** .

1. Wybierz komputery docelowe.

1. Wybierz pozycję **Zapisz**.

1. Wybierz pozycję **Done** (Gotowe).

### <a name="configure-network-extension"></a>Konfigurowanie rozszerzenia sieci

1. Użyj pliku **netfilter.mobileconfig** pobranego z GitHub.

2. Upload do narzędzia JAMF zgodnie z opisem w temacie [Wdrażanie niestandardowych profilów konfiguracji przy użyciu narzędzia Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>Udzielanie dostępu ułatwień dostępu do usługi DLP

1. Użyj pliku **accessibility.mobileconfig** pobranego z GitHub.

2. Upload do narzędzia JAMF zgodnie z opisem w temacie [Wdrażanie niestandardowych profilów konfiguracji przy użyciu narzędzia Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Pobieranie pakietu instalacyjnego

1. W **centrum zgodności** otwórz **Ustawienia** >  **Device Onboarding** i wybierz pozycję **Dołączanie**.

1. W obszarze **Wybierz system operacyjny, aby rozpocząć proces dołączania** wybierz system **macOS**

1. W obszarze **Metoda wdrażania** wybierz pozycję **Mobile Zarządzanie urządzeniami/Microsoft Intune**

1. Wybierz pozycję **Pobierz pakiet instalacyjny**. Spowoduje to podanie pliku *wdav.pkg* .

### <a name="deploy-the-installation-package"></a>Wdrażanie pakietu instalacyjnego

1. Przejdź do miejsca, w którym zapisano `wdav.pkg` plik.

1. Otwórz pulpit nawigacyjny Pro JAMF.

1. Wybierz komputer i kliknij koło zębate u góry, a następnie wybierz pozycję **Zarządzanie komputerem**.

1. W **obszarze Pakiety** wybierz pozycję **+Nowy**. Wprowadź następujące szczegóły:
    - Nazwa wyświetlana: pozostaw wartość pustą, ponieważ zostanie ona zresetowana po wybraniu pliku pkg.
    - Kategoria: Brak (wartość domyślna)
    - Nazwa pliku: wybierz plik, w tym przypadku `wdav.pkg` plik.

1. Wybierz pozycję **Otwórz**. Ustawić:
    - **Nazwa wyświetlana**: `Microsoft Endpoint Technology`
    - **Plik manifestu**: nie jest wymagany
    - **Karta Opcje**: pozostaw wartości domyślne
    - **Karta Ograniczenia**: pozostaw wartości domyślne

1. Wybierz pozycję **Zapisz**. Spowoduje to przekazanie pakietu do Pro JAMF.

1. Otwórz stronę **Zasady** .

1. Wybierz pozycję **+Nowy,** aby utworzyć nowe zasady.

1. Wprowadź te wartości
    - **Nazwa wyświetlana**: `MDATP Onboarding200329 v100.86.92 or later`

1. Wybierz **pozycję Cykliczne zaewidencjonowanie**.

1. Wybierz pozycję **Zapisz**.

1. Wybierz **pozycję** **PakietyKonfiguruj** > .

1. Wybierz pozycję **Add** (Dodaj).

1. Wybierz pozycję **Zapisz**.

1. Wybierz kartę **Zakres** .

1. Wybierz komputery docelowe.

1. Wybierz pozycję **Add** (Dodaj).

1. Wybierz pozycję **Samoobsługowe**.

1. Wybierz pozycję **Done** (Gotowe).

### <a name="check-the-macos-device"></a>Sprawdzanie urządzenia z systemem macOS

1. Uruchom ponownie urządzenie z systemem macOS.

1. Otwórz **pozycję Preferencje** **systemoweProfile** > .

1. Powinny zostać wyświetlone następujące elementy:
    - Accessiblity
    - Pełny dostęp do dysku
    - MAU
    - Dołączanie MDATP
    - Preferencje zarządzania urządzeniami przenośnymi
    - Profil zarządzania
    - Filtr sieciowy
    - Profil rozszerzenia systemu

## <a name="offboard-macos-devices-using-jamf-pro"></a>Odłączanie urządzeń z systemem macOS przy użyciu Pro JAMF

1. Odinstaluj aplikację (jeśli nie używasz rozwiązania MDE)
    1. Zobacz JAMF Pro Docs - Package Deployment — [JAMF Pro administratorów guideJamf](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Pro Administrator's Guide (Przewodnik administratora Pro JAMF)

1. Uruchom ponownie urządzenie z systemem macOS — niektóre aplikacje mogą utracić funkcjonalność drukowania do momentu ich ponownego uruchomienia

> [!IMPORTANT]
> Odłączanie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołanie do wszelkich alertów, które miał, zostaną zachowane przez maksymalnie 6 miesięcy.
