---
title: Intune wdrażania opartego na programach Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac
description: Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender mac, używając programu Microsoft Intune.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, instalacja, wdrażanie, dezinstalacja, intune, jamf, macos, catalina, mojave, high sierra
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a511405c2d8fb4753debbadf0744d6277639648b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475262"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Intune oparte na programie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W tym temacie opisano, jak wdrożyć Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS za pośrednictwem Intune. Pomyślne wdrożenie wymaga wykonania wszystkich następujących kroków:

1. [Pobierz pakiet dołączający](#download-the-onboarding-package)
1. [Konfiguracja urządzenia klienckiego](#client-device-setup)
1. [Zatwierdzanie rozszerzeń systemu](#approve-system-extensions)
1. [Tworzenie profilów konfiguracji systemu](#create-system-configuration-profiles)
1. [Publikowanie aplikacji](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zapoznaj się z główną stroną Ochrona punktu końcowego w usłudze Microsoft Defender [macOS](microsoft-defender-endpoint-mac.md), aby uzyskać opis wymagań wstępnych i wymagań systemowych bieżącej wersji oprogramowania.

## <a name="overview"></a>Omówienie

W poniższej tabeli podsumowano czynności, które należy wykonać, aby wdrożyć aplikację i zarządzać Ochrona punktu końcowego w usłudze Microsoft Defender komputerach Mac za pośrednictwem Intune. Bardziej szczegółowe instrukcje przedstawiono poniżej.

<br>

****

|Krok|Przykładowe nazwy plików|BundleIdentifier|
|---|---|---|
|[Pobierz pakiet dołączający](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Zatwierdź rozszerzenie systemu dla Ochrona punktu końcowego w usłudze Microsoft Defender](#approve-system-extensions)|MDATP_SysExt.xml|Nie dotyczy|
|[Zatwierdź rozszerzenie kernelu dla Ochrona punktu końcowego w usłudze Microsoft Defender](#download-the-onboarding-package)|MDATP_KExt.xml|Nie dotyczy|
|[Udzielanie pełnego dostępu dyskowe do Ochrona punktu końcowego w usłudze Microsoft Defender](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Zasady rozszerzenia sieci](#network-filter)|MDATP_NetExt.xml|Nie dotyczy|
|[Konfigurowanie programu Microsoft AutoUpdate (MAU)](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[Ochrona punktu końcowego w usłudze Microsoft Defender konfiguracji](mac-preferences.md#intune-full-profile) <p> **Uwaga:** Jeśli planujesz uruchomienie innej firmy audio/wideo dla systemu macOS, ustaw wartość `passiveMode` `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender i powiadomień programu MS AutoUpdate (MAU)](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 lub com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Pobierz pakiet dołączający

Pobierz pakiety dołączania z Microsoft 365 Defender sieci:

1. W Microsoft 365 Defender sieci Web przejdź do **Ustawienia** \> **Do punktów końcowych** \> **Dołączanie** \> **urządzeń do zarządzania urządzeniami**.

2. Ustaw system operacyjny na **macOS** i metodę wdrażania na Mobile **Zarządzanie urządzeniami /Microsoft Intune**.

   :::image type="content" source="images/macos-install-with-intune.png" alt-text="Strona Ustawień dołączania" lightbox="images/macos-install-with-intune.png":::

3. Wybierz **pozycję Pobierz pakiet dołączający**. Zapisz jako _WindowsDefenderATPOnboardingPackage.zip_ w tym samym katalogu.

4. Wyodrębnianie zawartości pliku .zip pliku:

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    warning:  WindowsDefenderATPOnboardingPackage.zip appears to use backslashes as path separators
      inflating: intune/kext.xml
      inflating: intune/WindowsDefenderATPOnboarding.xml
      inflating: jamf/WindowsDefenderATPOnboarding.plist
    ```

## <a name="create-system-configuration-profiles"></a>Tworzenie profilów konfiguracji systemu

Następnym krokiem jest utworzenie profilów konfiguracji systemu, które Ochrona punktu końcowego w usłudze Microsoft Defender potrzeb.
W centrum [Microsoft Endpoint Manager otwórz](https://endpoint.microsoft.com/) **pozycję Profile** \> **konfiguracji urządzeń**.

### <a name="onboarding-blob"></a>Obiekt blob dołączania

Ten profil zawiera informacje o licencji na Ochrona punktu końcowego w usłudze Microsoft Defender. Bez tego profilu Ochrona punktu końcowego w usłudze Microsoft Defender, że nie jest licencjonowany.

1. Wybierz **pozycję Utwórz profil w** **obszarze Profile konfiguracji**.
1. Wybierz **PlatformmacOS**=, **Profile** **typeTemplates**=. **Nazwa szablonu**= **Niestandardowe**. Kliknij **przycisk Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-1.png" alt-text="Strona tworzenia niestandardowego profilu konfiguracji" lightbox="images/mdatp-6-systemconfigurationprofiles-1.png":::

1. Wybierz nazwę profilu, na przykład "dołączanie do Defender dla Chmury lub punktu końcowego dla systemu macOS". Kliknij **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Pole Nazwa niestandardowego profilu konfiguracji" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Wybierz nazwę dla nazwy profilu konfiguracji, na przykład "Defender for Endpoint onboarding for macOS".
1. Wybierz kanał [wdrożenia](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. Wybierz pozycję intune/WindowsDefenderATPOnboarding.xml wyodrębniona z powyższego pakietu dołączania jako plik profilu konfiguracji.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles.png" alt-text="Importowanie konfiguracji z pliku do profilu konfiguracji niestandardowej" lightbox="images/mdatp-6-systemconfigurationprofiles.png":::

1. Kliknij **Dalej**.
1. Przypisz urządzenia na **karcie Zadanie** . Kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Niestandardowy profil konfiguracji — przypisanie" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Przejrzyj i **utwórz**.
1. Otwórz **profile** \> **konfiguracji urządzeń**. Tam możesz wyświetlić utworzony profil.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-3.png" alt-text="Ukończenie niestandardowego profilu konfiguracji" lightbox="images/mdatp-6-systemconfigurationprofiles-3.png":::

### <a name="approve-system-extensions"></a>Zatwierdź rozszerzenia systemowe

Ten profil jest potrzebny dla systemu macOS 10.15 (Catalina) lub nowszego. W starszych systemach macOS są ignorowane.

1. Wybierz **pozycję Utwórz profil w** **obszarze Profile konfiguracji**.
1. Wybierz **PlatformmacOS**=, **Profile** **typeTemplates**=. **Nazwa szablonu**= **Rozszerzenia**. Kliknij **przycisk Utwórz**.
1. Na karcie **Podstawy** nadaj nazwę temu noweowi profilowi.
1. Na karcie **Ustawienia konfiguracji** rozwiń **pozycję Rozszerzenia** systemowe, a następnie dodaj następujące wpisy w sekcji **Dozwolone rozszerzenia** systemowe:

    |Identyfikator pakietu|Identyfikator zespołu|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Ustawienia rozszerzenia systemu" lightbox="images/mac-system-extension-intune2.png":::

1. Na karcie **Zadania przypisz** ten profil wszystkim użytkownikom i **& wszystkich urządzeniach**.
1. Przejrzyj i utwórz ten profil konfiguracji.

### <a name="kernel-extensions"></a>Rozszerzenia kernelów

Ten profil jest potrzebny dla systemu macOS 10.15 (Catalina) lub starszego. W przypadku nowszego systemu macOS zostanie on zignorowany.

> [!CAUTION]
> Urządzenia apple Silicon (M1) nie obsługują doc. Instalacja profilu konfiguracji składającego się z zasad KEXT nie powiedzie się na tych urządzeniach.

1. Wybierz **pozycję Utwórz profil w** **obszarze Profile konfiguracji**.
1. Wybierz **PlatformmacOS**=, **Profile** **typeTemplates**=. **Nazwa szablonu**= **Rozszerzenia**. Kliknij **przycisk Utwórz**.
1. Na karcie **Podstawy** nadaj nazwę temu noweowi profilowi.
1. Na karcie **Ustawienia konfiguracji** rozwiń pozycję **Rozszerzenia kernel.**
1. Ustaw **identyfikator zespołu** **na UBF8T346G9** i kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Ustawienia kernelu rozszerzenia systemu" lightbox="images/mac-system-extension-intune2.png":::

1. Na karcie **Zadania przypisz** ten profil wszystkim użytkownikom i **& wszystkich urządzeniach**.
1. Przejrzyj i utwórz ten profil konfiguracji.

### <a name="full-disk-access"></a>Pełny dostęp do dysku

   > [!CAUTION]
   > System macOS 10.15 (Catalina) zawiera nowe udoskonalenia zabezpieczeń i prywatności. Począwszy od tej wersji aplikacje nie mogą domyślnie uzyskać dostępu do określonych lokalizacji na dysku (takich jak Dokumenty, Pliki do pobrania, Pulpit itp.) bez wyraźnej zgody. W przypadku braku tej zgody Ochrona punktu końcowego w usłudze Microsoft Defender może w pełni chronić Twojego urządzenia.
   >
   > Ten profil konfiguracji udziela pełnej wersji dostępu dyskowego Ochrona punktu końcowego w usłudze Microsoft Defender. Jeśli wcześniej skonfigurowano usługę Ochrona punktu końcowego w usłudze Microsoft Defender za pośrednictwem Intune, zalecamy zaktualizowanie wdrożenia przy użyciu tego profilu konfiguracji.

Pobierz [**plik fullconfig.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) z [GitHub repozytorium aplikacji](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Postępuj zgodnie z instrukcjami dotyczącymi obiektu [blob](#onboarding-blob) dołączania z powyższej strony, używając jako nazwy profilu "Defender for Endpoint Full Disk Access" i **pobranego pliku fullconfig.mobileconfig** jako nazwy profilu konfiguracji.

### <a name="network-filter"></a>Filtr sieci

W ramach funkcji wykrywania punktu końcowego i odpowiedzi użytkownicy Ochrona punktu końcowego w usłudze Microsoft Defender systemie macOS sprawdzają ruch sieciowy i raportują te informacje w portalu usługi Microsoft 365 Defender sieci. Poniższe zasady pozwalają na korzystanie z tej funkcji przez rozszerzenie sieci.

Pobierz [**plik netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) z [GitHub repozytorium.](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles)

Wykonaj instrukcje dotyczące obiektu [blob dołączania](#onboarding-blob) z powyższej strony, używając jako nazwy profilu "Defender for Endpoint Network Filter" i pobranego **pliku netfilter.mobileconfig** jako nazwy profilu konfiguracji.

### <a name="notifications"></a>Powiadomienia

Ten profil jest używany w celu umożliwienia użytkownikom Ochrona punktu końcowego w usłudze Microsoft Defender macOS i Microsoft Auto Update wyświetlania powiadomień w interfejsie użytkownika systemu macOS 10.15 (Catalina) lub nowszego.

Pobierz [**plik notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) z [GitHub repozytorium](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Postępuj zgodnie z instrukcjami dotyczącymi obiektu [blob](#onboarding-blob) dołączania z powyższej strony, używając jako nazwy profilu "Defender for Endpoint Notifications" i **pobranego pliku notif.mobileconfig** jako nazwy profilu konfiguracji.

### <a name="view-status"></a>Wyświetl stan

Po propagacji Intune na zarejestrowanych urządzeniach możesz wyświetlić je w obszarze **Monitoruj** \> **stan urządzenia**:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/mdatp-7-devicestatusblade.png" alt-text="Widok stanu urządzenia" lightbox="images/mdatp-7-devicestatusblade.png":::

## <a name="publish-application"></a>Publikowanie aplikacji

Ten krok umożliwia wdrożenie Ochrona punktu końcowego w usłudze Microsoft Defender na zarejestrowanych komputerach.

1. W centrum [Microsoft Endpoint Manager otwórz](https://endpoint.microsoft.com/) pozycję **Aplikacje**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-8-app-before.png" alt-text="Strona podglądu aplikacji" lightbox="images/mdatp-8-app-before.png":::

1. Wybierz pozycję Według platformy > systemie macOS > Dodaj.
1. Wybierz **pozycję Typ** **aplikacjimacOS**= i kliknij pozycję **Wybierz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-9-app-type.png" alt-text="Określony typ aplikacji" lightbox="images/mdatp-9-app-type.png":::

1. Zachowaj wartości domyślne, kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-10-properties.png" alt-text="Strona właściwości aplikacji" lightbox="images/mdatp-10-properties.png":::

1. Dodaj zadania i kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-11-assignments.png" alt-text="Strona Intune informacji o zadaniach" lightbox="images/mdatp-11-assignments.png":::

1. Przejrzyj i **utwórz**.
1. Możesz odwiedzić stronę **Aplikacje** \> **według platformy** \> **macOS** , aby wyświetlić ją na liście wszystkich aplikacji.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-12-applications.png" alt-text="Strona z listą aplikacji" lightbox="images/mdatp-12-applications.png":::

Aby uzyskać więcej informacji, zobacz [Dodawanie Ochrona punktu końcowego w usłudze Microsoft Defender do urządzeń z systemem macOS przy Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos)).

   > [!CAUTION]
   > Należy utworzyć wszystkie wymagane profile konfiguracji i wypchnąć je na wszystkie komputery, jak wyjaśniono powyżej.

## <a name="client-device-setup"></a>Konfiguracja urządzenia klienckiego

Nie potrzebujesz żadnej specjalnej obsługi administracyjnej dla komputerów Mac poza standardową Portal firmy [instalacji](/intune-user-help/enroll-your-device-in-intune-macos-cp).

1. Potwierdź zarządzanie urządzeniami.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-3-confirmdevicemgmt.png" alt-text="Strona Potwierdzanie zarządzania urządzeniami" lightbox="images/mdatp-3-confirmdevicemgmt.png":::

    Wybierz **pozycję Otwórz preferencje systemowe**, **zlokalizuj pozycję Profil** zarządzania na liście i wybierz pozycję **Zatwierdź...**. Twój profil zarządzania będzie wyświetlany jako **Zweryfikowany**:

    :::image type="content" source="images/mdatp-4-managementprofile.png" alt-text="Strona Profilu zarządzania" lightbox="images/mdatp-4-managementprofile.png":::

2. Wybierz **pozycję Kontynuuj** i ukończ rejestrację.

   Możesz teraz zarejestrować więcej urządzeń. Możesz je również zarejestrować później po zakończeniu inicjowania obsługi administracyjnej pakietów aplikacji i konfiguracji systemu.

3. W Intune otwórz menu **Zarządzaj urządzeniami** \>  \> **Wszystkie urządzenia**. Tutaj możesz zobaczyć swoje urządzenie spośród wymienionych na liście:

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mdatp-5-alldevices.png" alt-text="Strona Wszystkie urządzenia" lightbox="images/mdatp-5-alldevices.png":::

## <a name="verify-client-device-state"></a>Weryfikowanie stanu urządzenia klienckiego

1. Po wdrożeniu profilów konfiguracji na twoich urządzeniach otwórz profile **preferencji systemowych** \> **na urządzeniu** Mac.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-13-systempreferences.png" alt-text="Strona Preferencje systemowe" lightbox="images/mdatp-13-systempreferences.png":::

   :::image type="content" source="images/mdatp-14-systempreferencesprofiles.png" alt-text="Strona Profile preferencji systemowych" lightbox="images/mdatp-14-systempreferencesprofiles.png":::

2. Sprawdź, czy są obecne i zainstalowane następujące profile konfiguracji. Profil **zarządzania powinien** być profilem Intune systemu. _Wdav-config_ _i wdav-kext_ to profile konfiguracji systemu, które zostały dodane Intune:

   :::image type="content" source="images/mdatp-15-managementprofileconfig.png" alt-text="Strona Profile" lightbox="images/mdatp-15-managementprofileconfig.png":::

3. W prawym górnym rogu powinna Ochrona punktu końcowego w usłudze Microsoft Defender również ikona aplikacji:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Ikona Ochrona punktu końcowego w usłudze Microsoft Defender na pasku stanu" lightbox="images/mdatp-icon-bar.png":::

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Problem: Nie znaleziono licencji.

Rozwiązanie: Wykonaj powyższe czynności, aby utworzyć profil urządzenia przy użyciu WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>Problemy z instalacją rejestrowania

Aby uzyskać więcej informacji na temat sposobu znalezienia automatycznie wygenerowanego dziennika, który jest tworzony przez instalatora w przypadku wystąpienia błędu, zobacz Rejestrowanie [problemów z instalacją](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Dezinstalacja

Zobacz [Odinstalowywanie](mac-resources.md#uninstalling), aby uzyskać szczegółowe informacje na temat usuwania Ochrona punktu końcowego w usłudze Microsoft Defender macOS z urządzeń klienckich.
