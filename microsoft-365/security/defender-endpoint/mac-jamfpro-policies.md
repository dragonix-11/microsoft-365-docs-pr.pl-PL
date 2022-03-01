---
title: Konfigurowanie programu Microsoft Defender for Endpoint w zasadach macOS w programie Jamf Pro
description: Dowiedz się, jak skonfigurować program Microsoft Defender for Endpoint w zasadach macOS w programie Jamf Pro
keywords: policies, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 981e2afc2bfe3ff27bf5be492c98f96229a6deab
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011911"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Konfigurowanie programu Microsoft Defender for Endpoint w zasadach macOS w programie Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Program Defender dla punktu końcowego na komputerze Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ta strona zawiera instrukcje niezbędne do skonfigurowania zasad macOS w programie Jamf Pro.

Musisz wykonać następujące czynności:

1. [Uzyskaj pakiet dołączania do programu Microsoft Defender for Endpoint](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Tworzenie profilu konfiguracji w programie Jamf Pro przy użyciu pakietu dołączania](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Konfigurowanie programu Microsoft Defender dla ustawień punktu końcowego](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Konfigurowanie ustawień powiadomień programu Microsoft Defender dla punktu końcowego](#step-4-configure-notifications-settings)
5. [Konfigurowanie programu Microsoft AutoUpdate (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [Udzielanie pełnego dostępu dysku do programu Microsoft Defender dla punktu końcowego](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Zatwierdź rozszerzenie Kernel dla programu Microsoft Defender dla punktu końcowego](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Zatwierdzanie rozszerzeń systemowych dla programu Microsoft Defender dla punktu końcowego](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Konfigurowanie rozszerzenia sieci](#step-9-configure-network-extension)
10. [Planowanie skanowania za pomocą programu Microsoft Defender for Endpoint w systemie macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Krok 1. Uzyskaj pakiet dołączania do programu Microsoft Defender for Endpoint

1. W [Microsoft 365 Defender](https://security.microsoft.com) przejdź do Ustawienia > **punktów końcowych > dołączanie**.

2. Wybierz system macOS jako system operacyjny i zarządzanie urządzeniami przenośnymi / Microsoft Intune jako metodę wdrażania.

    ![Obraz Centrum zabezpieczeń usługi Microsoft Defender.](images/onboarding-macos.png)

3. Wybierz **pozycję Pobierz pakiet dołączający** (WindowsDefenderATPOnboardingPackage.zip).

4. Wyodrębnij `WindowsDefenderATPOnboardingPackage.zip`.

5. Skopiuj plik do preferowanej lokalizacji. Na przykład `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Krok 2. Tworzenie profilu konfiguracji w programie Jamf Pro przy użyciu pakietu dołączania

1. Znajdź plik z `WindowsDefenderATPOnboarding.plist` poprzedniej sekcji.

   ![Obraz pliku WindowsDefenderATPOnboarding.](images/plist-onboarding-file.png)

2. Zaloguj się do usługi Jamf Pro do **opcji** **KomputeryKonfiguracja** >  Profile i wybierz pozycję **Nowy**.

    ![Obraz tworzenia nowego pulpitu nawigacyjnego do Pro Jamf.](images/jamf-pro-configure-profile.png)

3. Wprowadź następujące szczegóły:

   **Informacje ogólne**:

   - Nazwa: Dołączanie do usługi MDE dla systemu macOS
   - Opis: dołączanie do EDR MDE dla systemu macOS
   - Kategoria: Brak
   - Metoda dystrybucji: automatyczne instalowanie
   - Poziom: Poziom komputera

4.  Przejdź do strony **& niestandardowej Ustawienia** i wybierz **pozycję Upload** >  **Add**.

    ![Obraz konfigurowania aplikacji i ustawień niestandardowych.](images/jamfpro-mac-profile.png)

5. Wybierz **Upload Plik (plik PLIST),** a następnie w **preferencjach Domena wprowadź**: `com.microsoft.wdav.atp`.

    ![Obraz pliku przekazywania jamfpro plist.](images/jamfpro-plist-upload.png)

    ![Obraz właściwości Pliku przekazywania Plik listy.](images/jamfpro-plist-file.png)

6. Wybierz **pozycję** Otwórz i wybierz plik dołączania.

    ![Obraz pliku dołączania.](images/jamfpro-plist-file-onboard.png)

7. Wybierz **Upload**.

    ![Obraz przekazywania pliku plist.](images/jamfpro-upload-plist.png)

8. Wybierz **kartę Zakres** .

    ![Obraz karty Zakres.](images/jamfpro-scope-tab.png)

9. Wybierz komputery docelowe.

    ![Obraz komputerów docelowych.](images/jamfpro-target-computer.png)

    ![Obraz celów.](images/jamfpro-targets.png)

10. Wybierz **Zapisz**.

    ![Obraz komputerów docelowych wdrożenia.](images/jamfpro-deployment-target.png)

    ![Obraz zaznaczonych komputerów docelowych.](images/jamfpro-target-selected.png)

11. Wybierz pozycję **Gotowe**.

    ![Obraz komputerów grupy docelowej.](images/jamfpro-target-group.png)

    ![Lista profilów konfiguracji.](images/jamfpro-configuration-policies.png)

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Krok 3. Konfigurowanie programu Microsoft Defender dla ustawień punktu końcowego

Możesz użyć graficznego interfejsu użytkownika usługi JAMF Pro do edytowania poszczególnych ustawień programu Microsoft Defender for Endpoint konfiguracji lub użyć starszej metody, tworząc listę konfiguracji w edytorze tekstów i przesyłając ją do usługi JAMF Pro.

Zwróć uwagę, że należy dokładnie użyć domeny `com.microsoft.wdav` **preferencji**, a program Microsoft Defender for Endpoint `com.microsoft.wdav.ext` używa tylko tej nazwy i do ładowania jej ustawień zarządzanych.

Ta wersja `com.microsoft.wdav.ext` może być używana w rzadkich przypadkach, gdy wolisz używać metody graficznego interfejsu użytkownika, ale musisz też skonfigurować ustawienie, które nie zostało jeszcze dodane do schematu.

### <a name="gui-method"></a>Metoda graficznego interfejsu użytkownika

1. Pobierz plik schema.json z repozytorium GitHub [Defender i](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) zapisz go w pliku lokalnym:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Utwórz nowy profil konfiguracji w obszarze Komputery > profilów konfiguracji wprowadź następujące szczegóły na **karcie** Ogólne:

    ![Nowy profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

    - Nazwa: Ustawienia konfiguracji MDAV MDAV USŁUGI MDATP
    - Opis:\<blank\>
    - Kategoria: Brak (domyślna)
    - Poziom: Poziom komputera (domyślny)
    - Metoda dystrybucji: Instalacja automatycznie (domyślna)

3. Przewiń w dół do **karty & Niestandardowe Ustawienia** aplikacji, wybierz pozycję Aplikacje **zewnętrzne, kliknij** pozycję Dodaj  i użyj schematu  niestandardowego jako źródła do użycia w domenie preferencji.

    ![Dodawanie schematu niestandardowego.](images/4137189bc3204bb09eed3aabc41afd78.png)

4. Wprowadź `com.microsoft.wdav` jako domenę preferencji, kliknij pozycję **Dodaj schemat** **i Upload** plik schema.json pobrany w kroku 1. Kliknij **Zapisz**.

    ![Upload schemat.](images/a6f9f556037c42fabcfdcb1b697244cf.png)

5. Poniżej w obszarze Preference Domain Properties (Właściwości domeny preferencji) możesz zobaczyć wszystkie obsługiwane ustawienia konfiguracji programu Microsoft Defender **for Endpoint**. Kliknij **pozycję Dodaj/Usuń właściwości** , aby wybrać ustawienia, które mają być zarządzane, a następnie kliknij przycisk **OK** , aby zapisać zmiany. (Ustawienia pozostawione niewybrane nie zostaną uwzględnione w konfiguracji zarządzanej, użytkownik końcowy będzie mógł skonfigurować te ustawienia na swoich komputerach.

    ![Wybierz ustawienia zarządzane.](images/817b3b760d11467abe9bdd519513f54f.png)

6. Zmień wartości ustawień na żądane wartości. Możesz kliknąć pozycję **Więcej informacji,** aby uzyskać dokumentację dla określonego ustawienia. (Możesz kliknąć pozycję **Podgląd listy,** aby sprawdzić, jak będzie wyglądała lista plist konfiguracji. Kliknij **pozycję Edytor formularzy** , aby powrócić do edytora wizualnego).

    ![Zmień wartości ustawień.](images/a14a79efd5c041bb8974cb5b12b3a9b6.png)

7. Wybierz **kartę Zakres** .

    ![Zakres profilu konfiguracji.](images/9fc17529e5577eefd773c658ec576a7d.png)

8. Wybierz **pozycję Grupa komputerowa firmy Contoso**.

9. Wybierz **pozycję Dodaj**, a następnie wybierz **pozycję Zapisz**.

    ![Ustawienia konfiguracji — dodaj.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Ustawienia konfiguracji — zapisywanie.](images/6f093e42856753a3955cab7ee14f12d9.png)

10. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy profil **konfiguracji**.

    ![Ustawienia konfiguracji — gotowe.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

Program Microsoft Defender for Endpoint dodaje z czasem nowe ustawienia. Te nowe ustawienia zostaną dodane do schematu i nowa wersja zostanie opublikowana w witrynie Github.
Aby mieć aktualizacje, wystarczy pobrać zaktualizowany schemat, edytować istniejący profil konfiguracji i pozycję Edytuj schemat na karcie Niestandardowy &  **Ustawienia** aplikacji.

### <a name="legacy-method"></a>Starsza metoda

1. Użyj następujących ustawień konfiguracji programu Microsoft Defender for Endpoint:

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > Domyślnie nie włączone, jeśli planujesz uruchomienie innej firmy audio/wideo dla systemu macOS, ustaw ją na `true`.

    - wykluczenia
    - excludedPath
    - excludedFileExtension (Wykluczanie pliku)
    - excludedFileName
    - exclusionsMergePolicy
    - allowedThreats

    > [!NOTE]
    > Jeżeli test dotyczy dowodu koncepcji, należy go usunąć, szczególnie jeśli test jest testem EICAR.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - tagi
    - hideStatusMenuIcon

     Aby uzyskać informacje, zobacz [Lista właściwości dla pełnego profilu konfiguracji usługi JAMF](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. Zapisz plik jako `MDATP_MDAV_configuration_settings.plist`.

3. Na pulpicie nawigacyjnym usługi Pro Jamf otwórz **okno Komputery** i ich **profile konfiguracji**. Kliknij **pozycję** Nowy i przejdź do **karty** Ogólne.

    ![Nowy profil.](images/644e0f3af40c29e80ca1443535b2fe32.png)

4. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Ustawienia konfiguracji MDAV MDAV USŁUGI MDATP
    - Opis:\<blank\>
    - Kategoria: Brak (domyślna)
    - Metoda dystrybucji: Zainstaluj automatycznie(domyślnie)
    - Poziom: Poziom komputera(domyślnie)

    ![Obraz ustawień konfiguracji MDAV MDAV.](images/3160906404bc5a2edf84d1d015894e3b.png)

5. W **czacie & Pozycję Ustawienia** pozycję **Konfiguruj**.

    ![Obraz aplikacji i ustawień niestandardowych.](images/e1cc1e48ec9d5d688087b4d771e668d2.png)

6. Wybierz **Upload plik (PLIST**).

    ![Obraz ustawień konfiguracji pliku plist.](images/6f85269276b2278eca4bce84f935f87b.png)

7. W **oknie Preferencje** w domenie wpisz `com.microsoft.wdav`, a **następnie Upload plik PLIST**.

    ![Obraz domeny preferencji ustawień konfiguracji.](images/db15f147dd959e872a044184711d7d46.png)

8. Wybierz **pozycję Wybierz plik**.

    ![Obraz ustawień konfiguracji wybierz plik.](images/526e978761fc571cca06907da7b01fd6.png)

9. Wybierz pozycję **MDATP_MDAV_configuration_settings.plist**, a następnie wybierz pozycję **Otwórz**.

    ![Obraz ustawień konfiguracji mdatpmdav.](images/98acea3750113b8dbab334296e833003.png)

10. Wybierz **Upload**.

    ![Obraz przekazywania ustawień konfiguracji.](images/0adb21c13206861ba9b30a879ade93d3.png)

    ![Obraz przekazywania ustawień konfiguracji.](images/f624de59b3cc86e3e2d32ae5de093e02.png)

    > [!NOTE]
    > Jeśli się zdarzy, że przekażesz plik intune, zostanie wyświetlany następujący błąd:
    >
    >![Obraz ustawień konfiguracji przekazywania pliku intune.](images/8e69f867664668796a3b2904896f0436.png)

11. Wybierz **Zapisz**.

    ![Obraz ustawień konfiguracji Zapisz obraz.](images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png)

12. Plik zostanie przekazany.

    ![Obraz przekazanego pliku ustawień konfiguracji.](images/33e2b2a1611fdddf6b5b79e54496e3bb.png)

    ![Obraz przekazanego pliku ustawień konfiguracji.](images/a422e57fe8d45689227e784443e51bd1.png)

13. Wybierz **kartę Zakres** .

    ![Obraz zakresu ustawień konfiguracji.](images/9fc17529e5577eefd773c658ec576a7d.png)

14. Wybierz **pozycję Grupa komputerowa firmy Contoso**.

15. Wybierz **pozycję Dodaj**, a następnie wybierz **pozycję Zapisz**.

    ![Obraz ustawień konfiguracji addsav.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![Obraz ustawień konfiguracji zapisz dodaj.](images/6f093e42856753a3955cab7ee14f12d9.png)

16. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy profil **konfiguracji**.

    ![Obraz profilu konfiguracji ustawień konfiguracji.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

## <a name="step-4-configure-notifications-settings"></a>Krok 4. Konfigurowanie ustawień powiadomień

Te kroki mają zastosowanie do systemu macOS 10.15 (Catalina) lub nowszego.

1. Na pulpicie nawigacyjnym usługi Pro Jamf wybierz pozycję **Komputery**, a następnie **pozycję Profile konfiguracji**.

2. Kliknij **pozycję** Nowy i wprowadź następujące **szczegóły opcji:**

    - Karta **Ogólne**:
        - **Nazwa**: Ustawienia powiadomień MDAV MDAV MDATP
        - **Opis**: macOS 10.15 (Catalina) lub nowsze
        - **Kategoria**: Brak *(domyślna)*
        - **Metoda dystrybucji**: Instalacja automatycznie *(domyślna)*
        - **Poziom**: Poziom komputera *(domyślny)*

        ![Obraz nowego ekranu profilu konfiguracji systemu macOS.](images/c9820a5ff84aaf21635c04a23a97ca93.png)

    - Powiadomienia **na karcie** Kliknij przycisk **Dodaj** i wprowadź następujące wartości:
        - **Identyfikator pakietu**: `com.microsoft.wdav.tray`
        - **Alerty krytyczne**: kliknij **pozycję Wyłącz**
        - **Powiadomienia**: Kliknij pozycję **Włącz.**
        - **Typ alertu na banerze**: Wybierz **pozycję Dołącz** **i Tymczasowy** *(domyślny)*
        - **Powiadomienia na ekranie blokady**: Kliknij pozycję **Ukryj**
        - **Powiadomienia w Centrum powiadomień**: Kliknij pozycję **Wyświetlanie**
        - **Ikona aplikacji znaczek**: kliknij pozycję **Wyświetlanie**

        ![Obraz ustawień konfiguracji w pasku powiadomień mdatpmdav.](images/7f9138053dbcbf928e5182ee7b295ebe.png)

    - Powiadomienia **na karcie** kliknij **pozycję Dodaj** jeszcze raz, przewiń w dół do **menu Nowe powiadomienia Ustawienia**
        - **Identyfikator pakietu**: `com.microsoft.autoupdate2`
        - Skonfiguruj pozostałe ustawienia na takie same wartości jak powyżej

        ![Obraz ustawień konfiguracji mau powiadomień mdatpmdav.](images/4bac6ce277aedfb4a674f2d9fcb2599a.png)

        Zauważ, że teraz masz dwie "tabele" z konfiguracjami powiadomień: jedną dla identyfikatora pakietu **: com.microsoft.wdav.tray**, a drugą dla identyfikatora pakietu **: com.microsoft.autoupdate2**. Chociaż możesz skonfigurować ustawienia alertów zgodnie z wymaganiami, identyfikatory pakietów muszą być dokładnie takie same, jak opisano wcześniej, a przełącznik Dołącz  musi być włączony dla **powiadomień**.

3. Wybierz **kartę Zakres** , a następnie wybierz pozycję **Dodaj**.

    ![Obraz dodawania zakresu ustawień konfiguracji.](images/441aa2ecd36abadcdd8aed03556080b5.png)

4. Wybierz **pozycję Grupa komputerowa firmy Contoso**.

5. Wybierz **pozycję Dodaj**, a następnie wybierz **pozycję Zapisz**.

    ![Obraz ustawień konfiguracji zapisywanie gry o komputerze firmy Contoso.](images/09a275e321268e5e3ac0c0865d3e2db5.png)

    ![Obraz ustawień konfiguracji: dodawanie zapisu.](images/4d2d1d4ee13d3f840f425924c3df0d51.png)

6. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy profil **konfiguracji**.

    ![Obraz ustawień konfiguracji done img.](images/633ad26b8bf24ec683c98b2feb884bdf.png)

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Krok 5. Konfigurowanie programu Microsoft AutoUpdate (MAU)

1. Użyj następujących ustawień konfiguracji programu Microsoft Defender for Endpoint:

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
   </dict>
   </plist>
   ```

2. Zapisz jako `MDATP_MDAV_MAU_settings.plist`.

3. Na pulpicie nawigacyjnym Pro Jamf wybierz pozycję **Ogólne**.

    ![Obraz ogólny ustawień konfiguracji.](images/eaba2a23dd34f73bf59e826217ba6f15.png)

4. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Ustawienia MDATP MDAV MAU
    - Opis: Ustawienia programu Microsoft AutoUpdate w układzie MDATP dla systemu macOS
    - Kategoria: Brak (domyślna)
    - Metoda dystrybucji: Zainstaluj automatycznie(domyślnie)
    - Poziom: Poziom komputera(domyślnie)

5. W **czacie & Pozycję Ustawienia** pozycję **Konfiguruj**.

    ![Obraz aplikacji ustawień konfiguracji i ustawień niestandardowych.](images/1f72e9c15eaafcabf1504397e99be311.png)

6. Wybierz **Upload plik (PLIST**).

    ![Obraz ustawień konfiguracji plist.](images/1213872db5833aa8be535da57653219f.png)

7. W **preferencjach Domena** wprowadź: `com.microsoft.autoupdate2`, a **następnie Upload plik PLIST**.

    ![Obraz ustawień konfiguracji wstępnej domeny.](images/1213872db5833aa8be535da57653219f.png)

8. Wybierz **pozycję Wybierz plik**.

    ![Obraz ustawień konfiguracji choosefile.](images/335aff58950ce62d1dabc289ecdce9ed.png)

9. Wybierz **MDATP_MDAV_MAU_settings.plist**.

    ![Obraz ustawień konfiguracji mdatpmdavmau.](images/a26bd4967cd54bb113a2c8d32894c3de.png)

10. Wybierz **Upload**.
    ![Obraz konfigurowania konfiguracji.](images/4239ca0528efb0734e4ca0b490bfb22d.png)

    ![Obraz konfigurowania uplimg.](images/4ec20e72c8aed9a4c16912e01692436a.png)

11. Wybierz **Zapisz**.

    ![Obraz ustawień konfiguracji saveimg.](images/253274b33e74f3f5b8d475cf8692ce4e.png)

12. Wybierz **kartę Zakres** .

     ![Obraz: karta Zakres ustawień konfiguracji.](images/10ab98358b2d602f3f67618735fa82fb.png)

13. Wybierz opcję **Dodaj**.

    ![Obraz dodatku addimg1 ustawień konfiguracji.](images/56e6f6259b9ce3c1706ed8d666ae4947.png)

    ![Obraz konfigurowania addimg2.](images/38c67ee1905c4747c3b26c8eba57726b.png)

    ![Obraz ustawień konfiguracji addimg3.](images/321ba245f14743c1d5d51c15e99deecc.png)

14. Wybierz pozycję **Gotowe**.

    ![Obraz doneimage ustawień konfiguracji.](images/ba44cdb77e4781aa8b940fb83e3c21f7.png)

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Krok 6. Udzielanie pełnego dostępu do usługi Microsoft Defender dla punktu końcowego na dysku

1. Na pulpicie nawigacyjnym usługi Pro Jamf wybierz **pozycję Profile konfiguracji**.

    ![Obraz profilu konfiguracji ustawień konfiguracji.](images/264493cd01e62c7085659d6fdc26dc91.png)

2. Wybierz **pozycję + Nowy**.

3. Wprowadź następujące szczegóły:

    **Ogólne**
    - Nazwa: MDAV MDAV MDAV — udzielanie pełnego dostępu EDR audio/wideo
    - Opis: W systemie macOS Catalina lub nowszej nowej kontroli zasad preferencji prywatności
    - Kategoria: Brak
    - Metoda dystrybucji: Instalowanie automatycznie
    - Poziom: poziom komputera

    ![Obraz ogólnych ustawień konfiguracji.](images/ba3d40399e1a6d09214ecbb2b341923f.png)

4. W **oknie Konfigurowanie preferencji prywatności, kontrola zasad wybierz** **pozycję Konfiguruj**.

    ![Obraz kontroli zasad zachowania poufności informacji dotyczących konfiguracji.](images/715ae7ec8d6a262c489f94d14e1e51bb.png)

5. W **oknie Kontrola zasad preferencji prywatności** wprowadź następujące szczegóły:

    - Identyfikator: `com.microsoft.wdav`
    - Typ identyfikatora: Identyfikator pakietu
    - Wymaganie kodu: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    ![Obraz konfigurowania ustawień preferencji prywatności i szczegółów kontroli zasad.](images/22cb439de958101c0a12f3038f905b27.png)

6. Wybierz **pozycję + Dodaj**.

    ![Obraz ustawień konfiguracji: dodawanie zasad systemowych do wszystkich plików.](images/bd93e78b74c2660a0541af4690dd9485.png)

    - W obszarze Aplikacja lub usługa: Ustaw na **wartość SystemPolicyAllFiles**

    - W obszarze "dostęp": Ustaw na **zezwalanie**

7. Wybierz **pozycję** Zapisz (nie tę u dołu po prawej stronie).

    ![Obraz ustawień konfiguracji zapisywania obrazów.](images/6de50b4a897408ddc6ded56a09c09fe2.png)

8. Kliknij znak `+` obok pozycji **App Access,** aby dodać nową pozycję.

    ![Obraz konfigurowania dostępu do aplikacji.](images/tcc-add-entry.png)

9. Wprowadź następujące szczegóły:

    - Identyfikator: `com.microsoft.wdav.epsext`
    - Typ identyfikatora: Identyfikator pakietu
    - Wymaganie kodu: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Wybierz **pozycję + Dodaj**.

    ![Obraz pozycji ustawień konfiguracji tcc epsext.](images/tcc-epsext-entry.png)

    - W obszarze Aplikacja lub usługa: Ustaw na **wartość SystemPolicyAllFiles**

    - W obszarze "dostęp": Ustaw na **zezwalanie**

11. Wybierz **pozycję** Zapisz (nie tę u dołu po prawej stronie).

    ![Obraz ustawień konfiguracji tcc epsext image2.](images/tcc-epsext-entry2.png)

12. Wybierz **kartę Zakres** .

    ![Obraz zakresu ustawień konfiguracji.](images/2c49b16cd112729b3719724f581e6882.png)

13. Wybierz **pozycję + Dodaj**.

    ![Obraz dodatku ustawień konfiguracji.](images/57cef926d1b9260fb74a5f460cee887a.png)

14. Wybierz **pozycję Grupy komputerów** > **w obszarze** Nazwa > wybierz pozycję **Grupa maszynowa firmy Contoso**.

    ![Obraz ustawień konfiguracji contoso machinegrp.](images/368d35b3d6179af92ffdbfd93b226b69.png)

15. Wybierz opcję **Dodaj**.

16. Wybierz **Zapisz**.

17. Wybierz pozycję **Gotowe**.

    ![Obraz ustawień konfiguracji donimg.](images/809cef630281b64b8f07f20913b0039b.png)

    ![Obraz ustawień konfiguracji donimg2.](images/6c8b406ee224335a8c65d06953dc756e.png)

Ewentualnie możesz pobrać [plik fullconfig.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) i przekazać go do profilów konfiguracji usługi JAMF zgodnie z opisem w tece Wdrażania niestandardowych profilów konfiguracji za pomocą usługi [Jamf Pro| Metoda 2. Upload profilu konfiguracji do usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Krok 7. Zatwierdzanie rozszerzenia Kernel dla programu Microsoft Defender dla punktu końcowego

> [!CAUTION]
> Urządzenia apple Silicon (M1) nie obsługują doc. Instalacja profilu konfiguracji składającego się z zasad KEXT nie powiedzie się na tych urządzeniach.

1. W profilu **konfiguracji** wybierz pozycję **+ Nowy**.

    ![Zrzut ekranu przedstawiający automatycznie wygenerowany wpis w mediach społecznościowych Opis.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Rozszerzenie MDAV MDAV MDAV
    - Opis: rozszerzenie kernelu MDATP (kext)
    - Kategoria: Brak
    - Metoda dystrybucji: automatyczne instalowanie
    - Poziom: Poziom komputera

    ![Obraz ustawień konfiguracji kernelu mdatpmdav.](images/24e290f5fc309932cf41f3a280d22c14.png)

3. W **ustawień Configure Approved Kernel Extensions (Konfiguruj zatwierdzone rozszerzenia kernelu)** wybierz **pozycję Configure (Konfiguruj**).

    ![Obraz ustawień konfiguracji zatwierdzonych jako kernel ext.](images/30be88b63abc5e8dde11b73f1b1ade6a.png)

4. W **zatwierdzonych rozszerzeniach kerneli** wprowadź następujące szczegóły:

    - Nazwa wyświetlana: Microsoft Corp.
    - Identyfikator zespołu: UBF8T346G9

    ![Obraz ustawień konfiguracji rozszerzenia kernelu.](images/39cf120d3ac3652292d8d1b6d057bd60.png)

5. Wybierz **kartę Zakres** .

    ![Obraz karty img zakresu ustawień konfiguracji.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. Wybierz **pozycję + Dodaj**.

7. Wybierz **pozycję Grupy komputerów** > **obszarze** Nazwa > wybierz pozycję **Grupa komputerów firmy Contoso**.

8. Wybierz **pozycję + Dodaj**.

    ![Obraz ustawień konfiguracji : dodawanie obrazów.](images/0dde8a4c41110dbc398c485433a81359.png)

9. Wybierz **Zapisz**.

    ![Obraz ustawień konfiguracji saveimag.](images/0add8019b85a453b47fa5c402c72761b.png)

10. Wybierz pozycję **Gotowe**.

    ![Obraz ustawień konfiguracji doneimag.](images/1c9bd3f68db20b80193dac18f33c22d0.png)

Ewentualnie możesz pobrać [plik kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) i przekazać go do profilów konfiguracji usługi JAMF zgodnie z opisem w tece Wdrażania niestandardowych profilów konfiguracji za pomocą usługi [Jamf Pro| Metoda 2. Upload profilu konfiguracji do usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Krok 8. Zatwierdzanie rozszerzeń systemowych dla programu Microsoft Defender dla punktu końcowego

1. W profilu **konfiguracji** wybierz pozycję **+ Nowy**.

    ![Zrzut ekranu przedstawiający automatycznie wygenerowany wpis w mediach społecznościowych Opis.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Rozszerzenia systemowe MDAV MDATP
    - Opis: Rozszerzenia systemowe MDATP
    - Kategoria: Brak
    - Metoda dystrybucji: automatyczne instalowanie
    - Poziom: Poziom komputera

    ![Obraz ustawień konfiguracji sysext new prof.](images/sysext-new-profile.png)

3. W **rozszerzeniach systemu** wybierz **pozycję Konfiguruj**.

   ![Obraz ustawień konfiguracji konfiguracji konfiguracyjnych.](images/sysext-configure.png)

4. W **rozszerzeniach systemu** wprowadź następujące szczegóły:

   - Nazwa wyświetlana: Microsoft Corp. Rozszerzenia systemu
   - Typy rozszerzeń systemu: dozwolone rozszerzenia systemu
   - Identyfikator zespołu: UBF8T346G9
   - Dozwolone rozszerzenia systemowe:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    ![Obraz ustawień konfiguracji sysextconfig2.](images/sysext-configure2.png)

5. Wybierz **kartę Zakres** .

    ![Obraz obrazu zakresu ustawień konfiguracji.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. Wybierz **pozycję + Dodaj**.

7. Wybierz **pozycję Grupy komputerów** > **obszarze** Nazwa > wybierz pozycję **Grupa komputerów firmy Contoso**.

8. Wybierz **pozycję + Dodaj**.

   ![Obraz dodatku ustawień konfiguracji.](images/0dde8a4c41110dbc398c485433a81359.png)

9. Wybierz **Zapisz**.

   ![Obraz sysext scope of configuration settings (Zakres ustawień konfiguracji).](images/sysext-scope.png)

10. Wybierz pozycję **Gotowe**.

    ![Obraz ustawień konfiguracji sysext-final.](images/sysext-final.png)

## <a name="step-9-configure-network-extension"></a>Krok 9. Konfigurowanie rozszerzenia sieci

W ramach funkcji wykrywania punktu końcowego i odpowiedzi usługa Microsoft Defender for Endpoint w systemie macOS sprawdza ruch sieciowy i raportuje te informacje w portalu usługi Microsoft 365 Defender sieci. Poniższe zasady pozwalają na korzystanie z tej funkcji przez rozszerzenie sieci.

Te kroki mają zastosowanie do systemu macOS 10.15 (Catalina) lub nowszego.

1. Na pulpicie nawigacyjnym usługi Pro Jamf wybierz pozycję **Komputery**, a następnie **pozycję Profile konfiguracji**.

2. Kliknij **pozycję** Nowy i wprowadź następujące **szczegóły opcji:**

    - Karta **Ogólne**:
        - **Nazwa**: Rozszerzenie Microsoft Defender Network
        - **Opis**: macOS 10.15 (Catalina) lub nowsze
        - **Kategoria**: Brak *(domyślna)*
        - **Metoda dystrybucji**: Instalacja automatycznie *(domyślna)*
        - **Poziom**: Poziom komputera *(domyślny)*

    - Filtr **zawartości karty**:
        - **Nazwa filtru**: Microsoft Defender Content Filter
        - **Identyfikator**: `com.microsoft.wdav`
        - **Pozostaw pole Adres usługi**, **Organizacja**, **Nazwa użytkownika**, **Hasło**, **Certyfikat** puste (**pole** *Dołącz nie jest* zaznaczone)
        - **Kolejność filtrowania**: Inspektor
        - **Filtr nasadki**: `com.microsoft.wdav.netext`
        - **Wyznaczony wymaganie filtru socketu**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - **Pozostaw pola filtru** sieci puste (**pole** *Dołącz nie jest* zaznaczone)

        Należy pamiętać, **że identyfikator**, **filtr głaszy** i filtr **socketów mają** określone dokładne wartości określone powyżej.

        ![Obraz ustawień konfiguracji mdatpmdav.](images/netext-create-profile.png)
        
 > [!NOTE]
 > Program Jamf obsługuje wbudowane ustawienia filtrowania zawartości, które można ustawiać bezpośrednio za pośrednictwem interfejsu.

3. Wybierz **kartę Zakres** .

   ![Obraz karty sco ustawień konfiguracji.](images/0df36fc308ba569db204ee32db3fb40a.png)

4. Wybierz **pozycję + Dodaj**.

5. Wybierz **pozycję Grupy komputerów** > **obszarze** Nazwa > wybierz pozycję **Grupa komputerów firmy Contoso**.

6. Wybierz **pozycję + Dodaj**.

    ![Obraz adim ustawień konfiguracji.](images/0dde8a4c41110dbc398c485433a81359.png)

7. Wybierz **Zapisz**.

    ![Obraz ustawień konfiguracji savimg netextscop.](images/netext-scope.png)

8. Wybierz pozycję **Gotowe**.

    ![Obraz ustawień konfiguracji netextfinal.](images/netext-final.png)

Ewentualnie możesz pobrać plik [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) i przekazać go do profilów konfiguracji usługi JAMF zgodnie z opisem w tece Wdrażania niestandardowych profilów konfiguracji za pomocą usługi [Jamf Pro| Metoda 2. Upload profilu konfiguracji do usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Krok 10. Planowanie skanowania za pomocą programu Microsoft Defender dla punktu końcowego w systemie macOS

Wykonaj instrukcje z [harmonogramu skanowania za pomocą programu Microsoft Defender dla punktu końcowego w systemie macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Krok 11. Wdrażanie programu Microsoft Defender dla punktu końcowego w systemie macOS

1. Przejdź do miejsca, w którym został zapisany.`wdav.pkg`

    ![Obraz eksploratora plików wdav pkg.](images/8dde76b5463047423f8637c86b05c29d.png)

2. Zmień nazwę na `wdav_MDM_Contoso_200329.pkg`.

    ![Obraz eksploratora plików1 wdavmdmpkg.](images/fb2220fed3a530f4b3ef36f600da0c27.png)

3. Otwórz pulpit nawigacyjny usługi Jamf Pro jamf.

    ![Obraz: jamfpro ustawień konfiguracji.](images/990742cd9a15ca9fdd37c9f695d1b9f4.png)

4. Wybierz komputer i kliknij ikonę koła zębatego u góry, a następnie wybierz pozycję **Zarządzanie komputerem**.

    ![Obraz ustawień konfiguracji compmgmt.](images/b6d671b2f18b89d96c1c8e2ea1991242.png)

5. W **pakietuch** wybierz **pozycję + Nowy**.
    ![Obraz zawierający opis ptaka automatycznie wygenerowany pakiet nowy.](images/57aa4d21e2ccc65466bf284701d4e961.png)

6. W **nowym pakiecie** Wprowadź następujące szczegóły:

    **Karta Ogólne**
    - Nazwa wyświetlana: na razie pozostaw to pole puste. Zostanie on zresetowany po wybraniu Twojego pkg.
    - Kategoria: Brak (domyślna)
    - Nazwa pliku: wybierz pozycję Plik

    ![Obraz karty Ogólne ustawień konfiguracji.](images/21de3658bf58b1b767a17358a3f06341.png)

    Otwórz plik i wskaż go lub `wdav.pkg` `wdav_MDM_Contoso_200329.pkg`.

    ![Zrzut ekranu przedstawiający automatycznie wygenerowany opis ekranu komputera.](images/1aa5aaa0a387f4e16ce55b66facc77d1.png)

7. Wybierz opcję **Otwórz**. Ustaw nazwę **wyświetlaną na** Zaawansowana ochrona przed zagrożeniami w **uchcie microsoft Defender i Program antywirusowy Microsoft Defender**.

    **Plik manifestu** nie jest wymagany. Program Microsoft Defender for Endpoint działa bez pliku manifestu.

    **Karta Opcje**: Zachowaj wartości domyślne.

    **Karta Ograniczenia**: Zachowaj wartości domyślne.

     ![Obraz karty ograniczenia ustawień konfiguracji.](images/56dac54634d13b2d3948ab50e8d3ef21.png)

8. Wybierz **Zapisz**. Pakiet zostanie przekazany do aplikacji Jamf Pro.

   ![Obraz ustawień konfiguracji pakietu upl jamf pro.](images/33f1ecdc7d4872555418bbc3efe4b7a3.png)

   Może potrwać kilka minut, aby pakiet był dostępny do wdrożenia.

   ![Obraz pakietu upl ustawień konfiguracji.](images/1626d138e6309c6e87bfaab64f5ccf7b.png)

9. Przejdź do **strony Zasady** .

    ![Obraz ustawień konfiguracji polocies.](images/f878f8efa5ebc92d069f4b8f79f62c7f.png)

10. Wybierz **pozycję + Nowy** , aby utworzyć nowe zasady.

    ![Obraz ustawień konfiguracji, nowe zasady.](images/847b70e54ed04787e415f5180414b310.png)


11. **Ogólne Wprowadź** następujące szczegóły:

    - Nazwa wyświetlana: Dołączanie usługi MDATP firmy Contoso 200329 od wersji 100.86.92 do wersji 100.86.92 lub nowszej

    ![Obraz ustawień konfiguracjimdatponboard.](images/625ba6d19e8597f05e4907298a454d28.png)

12. Wybierz **pozycję Sprawdzanie cykliczne**.

    ![Obraz ustawień konfiguracji powtarza się ponownie.](images/68bdbc5754dfc80aa1a024dde0fce7b0.png)

13. Wybierz **Zapisz**.

14. Wybierz **pozycję Pakiety > Konfigurowanie**.

    ![Obraz konfigurowania pakietu ustawień konfiguracji.](images/8fb4cc03721e1efb4a15867d5241ebfb.png)

15. Wybierz przycisk **Dodaj** obok usługi **Microsoft Defender Advanced Threat Protection i Program antywirusowy Microsoft Defender**.

    ![Obraz ustawień konfiguracji, dodawanie ustawień MDATP i MDA.](images/526b83fbdbb31265b3d0c1e5fbbdc33a.png)

16. Wybierz **Zapisz**.

    ![Obraz ustawień konfiguracjisavimg.](images/9d6e5386e652e00715ff348af72671c6.png)

17. Wybierz **kartę Zakres** .

    ![Obraz ustawień konfiguracji scptab.](images/8d80fe378a31143db9be0bacf7ddc5a3.png)

18. Wybierz komputery docelowe.

    ![Obraz ustawień konfiguracji tgtcomp.](images/6eda18a64a660fa149575454e54e7156.png)

    **Zakres**

    Wybierz opcję **Dodaj**.

    ![Obraz ustawień konfiguracji ad1img.](images/1c08d097829863778d562c10c5f92b67.png)

    ![Obraz ustawień konfiguracji ad2img.](images/216253cbfb6ae738b9f13496b9c799fd.png)

    **Samoobsługowa**

    ![Obraz selfservice ustawień konfiguracji.](images/c9f85bba3e96d627fe00fc5a8363b83a.png)

19. Wybierz pozycję **Gotowe**.

    ![Obraz ustawień konfiguracji do1img.](images/99679a7835b0d27d0a222bc3fdaf7f3b.png)

    ![Obraz ustawień konfiguracji do2img.](images/632aaab79ae18d0d2b8e0c16b6ba39e2.png)
