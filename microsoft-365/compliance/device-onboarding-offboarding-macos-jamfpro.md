---
title: Urządzenia z systemem macOS w nowych Microsoft 365 zgodności przy użyciu usługi JAMF Pro (wersja zapoznawcza)
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
description: Dowiedz się, jak korzystać z urządzeń z systemem macOS w nowych Microsoft 365 zgodności przy użyciu usługi JAMF Pro (wersja zapoznawcza)
ms.openlocfilehash: e66c9ba88e7c829af3695675a72e264da17e7dc4
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525253"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview"></a>Urządzenia z systemem macOS w nowych Microsoft 365 zgodności przy użyciu usługi JAMF Pro (wersja zapoznawcza)

Za pomocą usługi JAMF można Pro urządzeń z systemem macOS do Microsoft 365 rozwiązań zgodności, takich jak zapobieganie utracie danych w punktach końcowych.

> [!IMPORTANT]
> Skorzystaj z tej ***procedury, jeśli*** na urządzeniach z systemem macOS nie wdrożono programu Microsoft Defender for Endpoint (MDE)

**Dotyczy:**

- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Przed rozpoczęciem

- Upewnij się, że urządzenia [z systemem macOS](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) są zarządzane za pośrednictwem usługi JAMF pro i są skojarzone z tożsamością (dołączoną do upN usługi Azure AD) za pośrednictwem usługi JAMF Połączenie lub Intune.
- Instalowanie przeglądarki Edge w wersji 95+ na urządzeniach z systemem macOS 

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>Urządzenia w nowych rozwiązaniach Microsoft 365 zgodności przy użyciu usługi JAMF Pro

1. Te pliki będą potrzebne do tej procedury.

|Plik potrzebny dla |Źródło |
|---------|---------|
|Pakiet dołączający    |Pobrany z pakietu **dołączania portalu** zgodności, nazwa pliku *DeviceComplianceOnboarding.plist* |
|ułatwienia dostępu |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
pełny dostęp do dysku     |[fullconfig.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Filtr sieci| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Rozszerzenia systemu |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|Preferencja MDE     |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|Preferencja użytkownika mau|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Pakiet instalacyjny     |pobrane z pakietu instalacyjnego portalu **zgodności**, nazwa pliku *\*wdav.pkg*\* |

> [!TIP]
> Możesz pobrać pliki *.mobileconfig* pojedynczo lub w [jednym połączonym pliku](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , który zawiera:
> - accessibility.mobileconfig
> - fullconfig.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Jeśli którykolwiek z tych pojedynczych plików zostanie zaktualizowany, konieczne będzie pobranie ponownie połączonego pliku lub pojedynczego aktualizowanego pliku.

Dołączanie urządzenia z systemem macOS do rozwiązań zgodności jest procesem wielofazowym.

### <a name="get-the-device-onboarding-package"></a>Pobierz pakiet dołączania urządzenia

1. W **Centrum zgodności otwórz** **Ustawienia** >  **Dołączanie i** wybierz pozycję **Dołączanie**.
 
1. Aby **rozpocząć proces dołączania do aplikacji Wybierz system operacyjny** , wybierz **macOS**
 
1. W **przypadku metody wdrażania** **wybierz pozycję Zarządzanie urządzeniami przenośnymi/Microsoft Intune**
 
1. Wybierz **pozycję Pobierz pakiet dołączający**
 
1. Wyodrębnianie zawartości pakietu dołączania urządzenia. W folderze JAMF powinien zostać wyświetlony plik *DeviceCompcompboarding.plist* .

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Tworzenie profilu konfiguracji Pro JAMF dla pakietu dołączania

1. Utwórz nowy profil konfiguracji w programie JAMF Pro. Zobacz przewodnik [administratorów usługi JAMF Pro.](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Użyj tych wartości:
    - Nazwa: `MDATP onboarding for macOS`
    - Opis: `MDATP EDR onboarding for macOS`
    - Kategoria: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

2. W konsoli Pro JAMF > **aplikacji & ustawienia niestandardowe** wybierz pozycję **przekaż**, a następnie **dodaj**. Użyj tej wartości:
    - Domena preferencji: `com.microsoft.wdav.atp`

3. Wybierz **pozycję przekaż** i wybierz plik dołączający **DeviceComplianceOnboarding.plist**.

4. Wybierz **kartę zakres** .

5. Wybierz komputery docelowe.

6. Wybierz pozycję **Zapisz**.

7. Wybierz pozycję **Done** (Gotowe).

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>Konfigurowanie domeny preferencji przy użyciu konsoli JAMF PRO

> [!IMPORTANT]
> Jako wartości Domena preferencji należy użyć wartości ***com.microsoft.wdav** _. Program Microsoft Defender for Endpoint używa tej nazwy i pliku _ *_com.microsoft.wdav.ext_**, aby załadować swoje ustawienia zarządzane.

1. Utwórz nowy profil konfiguracji w programie JAMF Pro. Zobacz przewodnik [administratorów usługi JAMF Pro.](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Użyj tych wartości:
    - Nazwa: `MDATP MDAV configuration settings`
    - Opis: pozostaw to pole puste
    - Kategoria: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

1. Na karcie **& niestandardowej Ustawienia** wybierz pozycję Aplikacje **zewnętrzne, wybierz** pozycję Dodaj, a następnie wybierz  pozycję **Schemat niestandardowy** dla domeny preferencji. Użyj tej wartości:
    - Domena preferencji: `com.microsoft.wdav`

1. Wybierz **pozycję Dodaj schemat** **i Upload**, aby przekazać *plik schema.json*.

1. Wybierz pozycję **Zapisz**.

1. W **obszarze Preference Domain Properties (Właściwości domeny preferencji** ) wybierz te ustawienia
    - Funkcje 
        - Użyj rozszerzeń systemowych: `enabled` — wymagane dla rozszerzeń sieciowych w Catalina
        - Korzystanie z ochrony przed utratą danych: `enabled`
    - Aparat antywirusowy > tryb pasywny: `true|false`. Użyj, `true`jeśli wdrażasz tylko DLP. Użyj `false` wartości lub nie przypisz jej, jeśli wdrażasz funkcję DLP i program Microsoft Defender for Endpoint (MDE).

1. Wybierz **kartę Zakres** .

1. Wybierz grupy, w których chcesz wdrożyć ten profil konfiguracji.

1. Wybierz pozycję **Zapisz**. 


### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Tworzenie i wdrażanie profilu konfiguracji dla programu Microsoft AutoUpdate (MAU)

1. Utwórz plik konfiguracyjnych Pro JAMF przy użyciu **pliku com.microsoft.autoupdate2.plist**. Zobacz przewodnik [administratorów usługi JAMF Pro.](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Użyj tych wartości:
    - Nazwa: `MDATP MDAV MAU settings`
    - Opis: `Microsoft AutoUPdate settings for MDATP for macOS`
    - Kategoria: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

1. W **czacie & niestandardowy Ustawienia** wybierz pozycję **Upload** pozycję **Dodaj**.

1. W **preferencjach Domena** wprowadź tekst`com.microsoft.autoupdate2`, a następnie **wybierz pozycję Upload**.

1. Wybierz **plik com.microsoft.autoupdate2.plist** .

1. Wybierz pozycję **Zapisz**.

1. Wybierz **kartę Zakres** .

1. Wybierz komputery docelowe.

1. Wybierz pozycję **Zapisz**.

1. Wybierz pozycję **Done** (Gotowe).


### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Tworzenie i wdrażanie profilu konfiguracji w celu przyznania pełnego dostępu do dysku

1. Użyj **pliku fullconfig.mobileconfig** .

1. Upload **plik fullconfig.mobileconfig** do usługi JAMF. Zobacz Wdrażanie [niestandardowych profilów konfiguracji za pomocą usługi JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Tworzenie i wdrażanie profilu konfiguracji dla rozszerzeń systemu

1. Utwórz plik konfiguracji Pro JAMF za pomocą procedur w przewodniku administratora Pro [JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Użyj tych wartości:
    - Nazwa: `MDATP MDAV System Extensions`
    - Opis: `MDATP system extensions`
    - Kategoria: `none`
    - Metoda dystrybucji: `install automatically`
    - Poziom: `computer level`

1. W **profilu rozszerzenia systemu** wprowadź następujące wartości:
    - Nazwa wyświetlana: `Microsoft Corp. System Extensions`
    - Typy rozszerzeń systemu: `Allowed System Extensions`
    - Identyfikator zespołu: `UBF8T346G9`
    - Dozwolone rozszerzenia systemowe: `com.microsoft.wdav.epsext`, i `com.microsoft.wdav.netext`

1. Wybierz **kartę Zakres** .

1. Wybierz komputery docelowe.

1. Wybierz pozycję **Zapisz**.

1. Wybierz pozycję **Done** (Gotowe).

### <a name="configure-network-extension"></a>Konfigurowanie rozszerzenia sieci

1.  Użyj **pliku netfilter.mobileconfig** pobranego z programu GitHub.

2.  Upload do usługi JAMF zgodnie z opisem w tece Wdrażanie niestandardowych profilów konfiguracji za [pomocą usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>Udzielanie dostępu do funkcji DLP

1. Użyj pliku **accessibility.mobileconfig** pobranego z programu GitHub.

2.  Upload do usługi JAMF zgodnie z opisem w tece Wdrażanie niestandardowych profilów konfiguracji za [pomocą usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Uzyskaj pakiet instalacyjny

1. W **Centrum zgodności otwórz** **Ustawienia** >  **Dołączanie i** wybierz pozycję **Dołączanie**.
 
1. Aby **rozpocząć proces dołączania do aplikacji Wybierz system operacyjny** , wybierz **macOS**
 
1. W **przypadku metody wdrażania** **wybierz pozycję Zarządzanie urządzeniami przenośnymi/Microsoft Intune**
 
1. Wybierz **pozycję Pobierz pakiet instalacyjny**. Spowoduje to nadanie *pliku wdav.pkg* .


### <a name="deploy-the-installation-package"></a>Wdrażanie pakietu instalacyjnego

1. Przejdź do miejsca, w którym został zapisany `wdav.pkg` plik.

1. Otwórz pulpit nawigacyjny usługi JAMF Pro jamf.

1. Wybierz komputer i kliknij ikonę koła zębatego u góry, a następnie wybierz pozycję **Zarządzanie komputerem**.

1. W **pakietuch** wybierz **pozycję +Nowy**. Wprowadź te szczegóły:
    - Nazwa wyświetlana: pozostaw puste pole, ponieważ po wybraniu pliku pkg zostanie ono zresetowane.
    - Kategoria: Brak (domyślna)
    - Nazwa_pliku: wybierz plik, w tym przypadku plik `wdav.pkg` .

1. Wybierz **pozycję Otwórz**. Ustaw:
    - **Nazwa wyświetlana**: `Microsoft Endpoint Technology`
    - **Plik manifestu**: nie jest wymagany
    - **Karta Opcje**: pozostaw wartości domyślne
    - **Karta Ograniczenia**: pozostaw wartości domyślne

1. Wybierz pozycję **Zapisz**. Pakiet jest przesyłany do pliku JAMF Pro.

1. Otwórz **stronę Zasady** .

1. Wybierz **pozycję +Nowy** , aby utworzyć nowe zasady.

1. Wprowadź te wartości
    - **Nazwa wyświetlana**: `MDATP Onboarding200329 v100.86.92 or later`

1. Wybierz **pozycję Sprawdzanie cykliczne**.

1. Wybierz pozycję **Zapisz**.

1. Wybierz **pozycję PackagesConfigure** >  **(PakietyKonfiguracyjne**).

1. Wybierz pozycję **Add** (Dodaj).

1. Wybierz pozycję **Zapisz**. 

1. Wybierz **kartę Zakres** .

1. Wybierz komputery docelowe.

1. Wybierz pozycję **Add** (Dodaj).

1. Wybierz **pozycję Samoobsługa**.

1. Wybierz pozycję **Done** (Gotowe).

### <a name="check-the-macos-device"></a>Sprawdź urządzenie z systemem macOS 

1. Uruchom ponownie urządzenie z systemem macOS.

1. Otwórz **okno Preferencje** >  **systemowePropliki**.

1. Powinien zostać wyświetlony:
    - Accessiblity
    - Pełny dostęp do dysku
    - MAU
    - Dołączanie do USŁUGI MDATP
    - Preferencje MDE
    - Profil zarządzania
    - Filtr sieci
    - Profil rozszerzenia systemu

## <a name="offboard-macos-devices-using-jamf-pro"></a>Urządzenia przenośne z systemem macOS korzystające z usługi JAMF Pro

1. Odinstaluj aplikację (jeśli nie korzystasz z usługi MDE)
    1. Zobacz przewodnik dla administratorów usługi JAMF Pro docs - Wdrażanie pakietów — przewodnik Pro usługi [JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Pro przewodnik administratora

1. Uruchom ponownie urządzenie z systemem macOS — niektóre aplikacje mogą utracić funkcje drukowania do momentu ponownego uruchomienia

> [!IMPORTANT]
> Wynoszenie powoduje, że urządzenie przestaje wysyłać dane czujnika do portalu, ale dane z urządzenia, w tym odwołania do wszelkich posiadanych alertów, będą przechowywane przez maksymalnie 6 miesięcy.
