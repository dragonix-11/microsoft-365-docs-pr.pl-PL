---
title: Wdrożenie oparte na Intune dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac
description: Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac przy użyciu Microsoft Intune.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 4c2c1f7c11c57ca45411b74023807077f73ba8bf
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044111"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>Wdrożenie oparte na Intune dla Ochrona punktu końcowego w usłudze Microsoft Defender na macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Usługa ochrony punktu końcowego w usłudze Microsoft Defender w systemie macOS](microsoft-defender-endpoint-mac.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 

W tym temacie opisano sposób wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender na macOS za pośrednictwem Intune. Pomyślne wdrożenie wymaga wykonania wszystkich następujących kroków:

1. [Pobieranie pakietu dołączania](#download-the-onboarding-package)
1. [Konfiguracja urządzenia klienckiego](#client-device-setup)
1. [Zatwierdzanie rozszerzeń systemu](#approve-system-extensions)
1. [Tworzenie profilów konfiguracji systemu](#create-system-configuration-profiles)
1. [Publikowanie aplikacji](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zapoznaj się z [głównym Ochrona punktu końcowego w usłudze Microsoft Defender na stronie macOS](microsoft-defender-endpoint-mac.md), aby zapoznać się z opisem wymagań wstępnych i wymagań systemowych dotyczących bieżącej wersji oprogramowania.

## <a name="overview"></a>Omówienie

Poniższa tabela zawiera podsumowanie kroków, które należy wykonać w celu wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender i zarządzania nimi na komputerach Mac za pośrednictwem Intune. Bardziej szczegółowe kroki są dostępne poniżej.

<br>

****

|Krok|Przykładowe nazwy plików|BundleIdentifier|
|---|---|---|
|[Pobieranie pakietu dołączania](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[Zatwierdzanie rozszerzenia systemu dla Ochrona punktu końcowego w usłudze Microsoft Defender](#approve-system-extensions)|MDATP_SysExt.xml|nd.|
|[Zatwierdzanie rozszerzenia jądra dla Ochrona punktu końcowego w usłudze Microsoft Defender](#download-the-onboarding-package)|MDATP_KExt.xml|nd.|
|[Udzielanie pełnego dostępu do dysku Ochrona punktu końcowego w usłudze Microsoft Defender](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[Zasady rozszerzenia sieci](#network-filter)|MDATP_NetExt.xml|nd.|
|[Konfigurowanie usługi Microsoft AutoUpdate (MAU)](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[ustawienia konfiguracji Ochrona punktu końcowego w usłudze Microsoft Defender](mac-preferences.md#intune-full-profile) <p> **Uwaga:** Jeśli planujesz uruchomić usługę av innej firmy dla macOS, ustaw wartość `passiveMode` `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[Konfigurowanie powiadomień Ochrona punktu końcowego w usłudze Microsoft Defender i MS AutoUpdate (MAU)](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 lub com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>Pobieranie pakietu dołączania

Pobierz pakiety dołączania z portalu Microsoft 365 Defender:

1. W portalu Microsoft 365 Defender przejdź do **obszaru Ustawienia** \> **Endpoints** \> **Dołączanie** do **zarządzania urządzeniami**\>.

2. Ustaw system operacyjny na **macOS**, a metodę wdrażania na **Zarządzanie urządzeniami/Microsoft Intune** mobilną.

   :::image type="content" source="images/macos-install-with-intune.png" alt-text="Strona ustawień dołączania" lightbox="images/macos-install-with-intune.png":::

3. Wybierz pozycję **Pobierz pakiet dołączania**. Zapisz go jako _WindowsDefenderATPOnboardingPackage.zip_ w tym samym katalogu.

4. Wyodrębnij zawartość pliku .zip:

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

Następnym krokiem jest utworzenie profilów konfiguracji systemu, które Ochrona punktu końcowego w usłudze Microsoft Defender potrzebne.
W [centrum administracyjnym Microsoft Endpoint Manager](https://endpoint.microsoft.com/) otwórz **pozycję Profile konfiguracji** **urządzeń**\>.

### <a name="onboarding-blob"></a>Dołączanie obiektu blob

Ten profil zawiera informacje o licencji dla Ochrona punktu końcowego w usłudze Microsoft Defender. Bez tego profilu Ochrona punktu końcowego w usłudze Microsoft Defender zgłosi, że nie ma licencji.

1. Wybierz pozycję **Utwórz profil** w obszarze **Profile konfiguracji**.
1. Wybierz pozycję **Platforma**= **macOS**, **Typ**= profilu **Szablony**. **Nazwa**= szablonu **Niestandardowe**. Kliknij **pozycję Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-1.png" alt-text="Strona tworzenia profilu konfiguracji niestandardowej" lightbox="images/mdatp-6-systemconfigurationprofiles-1.png":::

1. Wybierz nazwę profilu, np. "Defender dla Chmury lub dołączanie punktu końcowego do macOS". Kliknij **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Pole Nazwa profilu konfiguracji niestandardowej" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Wybierz nazwę profilu konfiguracji, np. "Dołączanie usługi Defender dla punktu końcowego dla macOS".
1. Wybierz [kanał wdrażania](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. Wybierz pozycję intune/WindowsDefenderATPOnboarding.xml wyodrębnioną z powyższego pakietu dołączania jako plik profilu konfiguracji.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles.png" alt-text="Importowanie konfiguracji z pliku dla niestandardowego profilu konfiguracji" lightbox="images/mdatp-6-systemconfigurationprofiles.png":::

1. Kliknij **Dalej**.
1. Przypisz urządzenia na karcie **Przypisanie** . Kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="Niestandardowy profil konfiguracji — przypisanie" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. Przejrzyj i **utwórz**.
1. Otwórz **pozycję Profile konfiguracji** **urządzeń**\>. Zostanie tam wyświetlony utworzony profil.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-3.png" alt-text="Ukończenie niestandardowego profilu konfiguracji" lightbox="images/mdatp-6-systemconfigurationprofiles-3.png":::

### <a name="approve-system-extensions"></a>Zatwierdzanie rozszerzeń systemu

Ten profil jest wymagany dla macOS 10.15 (Catalina) lub nowszych. Zostanie on zignorowany na starszych macOS.

1. Wybierz pozycję **Utwórz profil** w obszarze **Profile konfiguracji**.
1. Wybierz pozycję **Platforma**= **macOS**, **Typ**= profilu **Szablony**. **Nazwa**= szablonu **Rozszerzenia**. Kliknij **pozycję Utwórz**.
1. Na **karcie Podstawy** nadaj nazwę temu nowemu profilowi.
1. Na karcie **Ustawienia konfiguracji** rozwiń węzeł **Rozszerzenia systemu** dodaj następujące wpisy w sekcji **Dozwolone rozszerzenia systemu** :

    |Identyfikator pakietu|Identyfikator zespołu|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="Ustawienia rozszerzenia systemu" lightbox="images/mac-system-extension-intune2.png":::

1. Na **karcie Przypisania** przypisz ten profil do pozycji **Wszyscy użytkownicy & wszystkie urządzenia**.
1. Przejrzyj i utwórz ten profil konfiguracji.

### <a name="kernel-extensions"></a>Rozszerzenia jądra

Ten profil jest wymagany dla macOS 10.15 (Catalina) lub starszych. Zostanie on zignorowany w nowszych macOS.

> [!CAUTION]
> Urządzenia Apple Silicon (M1) nie obsługują protokołu KEXT. Instalacja profilu konfiguracji składającego się z zasad KEXT zakończy się niepowodzeniem na tych urządzeniach.

1. Wybierz pozycję **Utwórz profil** w obszarze **Profile konfiguracji**.
1. Wybierz pozycję **Platforma**= **macOS**, **Typ**= profilu **Szablony**. **Nazwa**= szablonu **Rozszerzenia**. Kliknij **pozycję Utwórz**.
1. Na **karcie Podstawy** nadaj nazwę temu nowemu profilowi.
1. Na karcie **Ustawienia konfiguracji** rozwiń węzeł **Rozszerzenia jądra**.
1. Ustaw **identyfikator zespołu** na **UBF8T346G9** i kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-kernel-extension-intune2.png" alt-text="Dozwolone identyfikatory zespołu dla rozszerzeń jądra." lightbox="images/mac-kernel-extension-intune2.png":::

1. Na **karcie Przypisania** przypisz ten profil do pozycji **Wszyscy użytkownicy & wszystkie urządzenia**.
1. Przejrzyj i utwórz ten profil konfiguracji.

### <a name="full-disk-access"></a>Pełny dostęp do dysku

   > [!CAUTION]
   > macOS 10.15 (Catalina) zawiera nowe ulepszenia zabezpieczeń i prywatności. Począwszy od tej wersji, domyślnie aplikacje nie mogą uzyskać dostępu do niektórych lokalizacji na dysku (takich jak Dokumenty, Pliki do pobrania, Pulpit itp.) bez wyraźnej zgody. W przypadku braku tej zgody Ochrona punktu końcowego w usłudze Microsoft Defender nie jest w stanie w pełni chronić urządzenia.
   >
   > Ten profil konfiguracji zapewnia dostęp do pełnego dysku do Ochrona punktu końcowego w usłudze Microsoft Defender. Jeśli wcześniej skonfigurowano Ochrona punktu końcowego w usłudze Microsoft Defender za pośrednictwem Intune, zalecamy zaktualizowanie wdrożenia przy użyciu tego profilu konfiguracji.

Pobierz [**plik fulldisk.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) z [naszego repozytorium GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Postępuj zgodnie z instrukcjami dotyczącymi [dołączania obiektu blob](#onboarding-blob) z góry, używając nazwy profilu "Defender for Endpoint Full Disk Access" i pobierz **plik fulldisk.mobileconfig** jako nazwę profilu konfiguracji.

### <a name="network-filter"></a>Filtr sieciowy

W ramach funkcji wykrywania punktów końcowych i reagowania Ochrona punktu końcowego w usłudze Microsoft Defender na macOS sprawdza ruch gniazd i zgłasza te informacje do portalu Microsoft 365 Defender. Poniższe zasady umożliwiają rozszerzeniu sieci wykonywanie tej funkcji.

Pobierz [**plik netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) z [naszego repozytorium GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Postępuj zgodnie z instrukcjami dotyczącymi [dołączania obiektu blob](#onboarding-blob) z góry, używając opcji "Defender for Endpoint Network Filter" jako nazwy profilu i pobranej nazwy profilu **netfilter.mobileconfig** jako nazwy profilu konfiguracji.

### <a name="notifications"></a>Powiadomienia

Ten profil umożliwia Ochrona punktu końcowego w usłudze Microsoft Defender w macOS i automatycznej aktualizacji firmy Microsoft wyświetlanie powiadomień w interfejsie użytkownika w wersji macOS 10.15 (Catalina) lub nowszej.

Pobierz [**plik notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) z [naszego repozytorium GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

Postępuj zgodnie z instrukcjami dotyczącymi [dołączania obiektu blob](#onboarding-blob) z góry, używając nazwy profilu "Defender for Endpoint Notifications" i pobierz plik **notif.mobileconfig** jako nazwę profilu konfiguracji.

### <a name="view-status"></a>Wyświetl stan

Po propagacji zmian Intune do zarejestrowanych urządzeń można je wyświetlić w obszarze **Monitorowanie** \> **stanu urządzenia**:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/mdatp-7-devicestatusblade.png" alt-text="Widok stanu urządzenia" lightbox="images/mdatp-7-devicestatusblade.png":::

## <a name="publish-application"></a>Publikowanie aplikacji

Ten krok umożliwia wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na zarejestrowanych maszynach.

1. W [centrum administracyjnym Microsoft Endpoint Manager](https://endpoint.microsoft.com/) otwórz pozycję **Aplikacje**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-8-app-before.png" alt-text="Strona przeglądu aplikacji" lightbox="images/mdatp-8-app-before.png":::

1. Wybierz pozycję Według platformy > macOS > Dodaj.
1. Wybierz **pozycję Typ**= aplikacji **macOS** kliknij pozycję **Wybierz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-9-app-type.png" alt-text="Określony typ aplikacji" lightbox="images/mdatp-9-app-type.png":::

1. Zachowaj wartości domyślne, kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-10-properties.png" alt-text="Strona właściwości aplikacji" lightbox="images/mdatp-10-properties.png":::

1. Dodaj przypisania, kliknij przycisk **Dalej**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-11-assignments.png" alt-text="Strona informacji o przypisaniach Intune" lightbox="images/mdatp-11-assignments.png":::

1. Przejrzyj i **utwórz**.
1. Możesz odwiedzić stronę **Aplikacje** \> **według platformy** \> **macOS**, aby wyświetlić ją na liście wszystkich aplikacji.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-12-applications.png" alt-text="Strona listy aplikacji" lightbox="images/mdatp-12-applications.png":::

Aby uzyskać więcej informacji, zobacz [Dodawanie Ochrona punktu końcowego w usłudze Microsoft Defender do macOS urządzeń przy użyciu Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos)).

   > [!CAUTION]
   > Musisz utworzyć wszystkie wymagane profile konfiguracji i wypchnąć je na wszystkie maszyny, jak wyjaśniono powyżej.

## <a name="client-device-setup"></a>Konfiguracja urządzenia klienckiego

Nie potrzebujesz żadnej specjalnej aprowizacji dla urządzenia Mac poza standardową [instalacją Portal firmy](/intune-user-help/enroll-your-device-in-intune-macos-cp).

1. Potwierdź zarządzanie urządzeniami.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-3-confirmdevicemgmt.png" alt-text="Strona Potwierdzanie zarządzania urządzeniami" lightbox="images/mdatp-3-confirmdevicemgmt.png":::

    Wybierz pozycję **Otwórz preferencje systemowe**, znajdź na liście **pozycję Profil zarządzania** , a następnie wybierz pozycję **Zatwierdź...**. Twój profil zarządzania będzie wyświetlany jako **Zweryfikowane**:

    :::image type="content" source="images/mdatp-4-managementprofile.png" alt-text="Strona Profil zarządzania" lightbox="images/mdatp-4-managementprofile.png":::

2. Wybierz pozycję **Kontynuuj** i zakończ rejestrację.

   Teraz możesz zarejestrować więcej urządzeń. Można je również zarejestrować później, po zakończeniu aprowizowania konfiguracji systemu i pakietów aplikacji.

3. W Intune otwórz pozycję **Zarządzaj urządzeniami** \>  \> **Wszystkie urządzenia**. Tutaj możesz zobaczyć swoje urządzenie wśród wymienionych:

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mdatp-5-alldevices.png" alt-text="Strona Wszystkie urządzenia" lightbox="images/mdatp-5-alldevices.png":::

## <a name="verify-client-device-state"></a>Weryfikowanie stanu urządzenia klienckiego

1. Po wdrożeniu profilów konfiguracji na urządzeniach otwórz **pozycję Profile preferencji systemowych** \> na urządzeniu Mac.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-13-systempreferences.png" alt-text="Strona Preferencje systemowe" lightbox="images/mdatp-13-systempreferences.png":::

   :::image type="content" source="images/mdatp-14-systempreferencesprofiles.png" alt-text="Strona Profile preferencji systemowych" lightbox="images/mdatp-14-systempreferencesprofiles.png":::

2. Sprawdź, czy są obecne i zainstalowane następujące profile konfiguracji. **Profil zarządzania** powinien być profilem systemu Intune. _Wdav-config_ i _wdav-kext_ to profile konfiguracji systemu dodane w Intune:

   :::image type="content" source="images/mdatp-15-managementprofileconfig.png" alt-text="Strona Profile" lightbox="images/mdatp-15-managementprofileconfig.png":::

3. W prawym górnym rogu powinna również zostać wyświetlona ikona Ochrona punktu końcowego w usłudze Microsoft Defender:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="Ikona Ochrona punktu końcowego w usłudze Microsoft Defender na pasku stanu" lightbox="images/mdatp-icon-bar.png":::

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Problem: Nie znaleziono licencji.

Rozwiązanie: wykonaj powyższe kroki, aby utworzyć profil urządzenia przy użyciu WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>Problemy z instalacją rejestrowania

Aby uzyskać więcej informacji na temat znajdowania automatycznie wygenerowanego dziennika utworzonego przez instalatora w przypadku wystąpienia błędu, zobacz Problemy z [instalacją rejestrowania](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>Dezinstalacji

Aby uzyskać szczegółowe informacje na temat usuwania Ochrona punktu końcowego w usłudze Microsoft Defender na macOS z urządzeń klienckich, zobacz [Odinstalowywanie](mac-resources.md#uninstalling).
