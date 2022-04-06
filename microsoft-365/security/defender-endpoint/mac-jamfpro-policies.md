---
title: Konfigurowanie zasad Ochrona punktu końcowego w usłudze Microsoft Defender macOS w programie Jamf Pro
description: Dowiedz się, jak skonfigurować zasady Ochrona punktu końcowego w usłudze Microsoft Defender macOS w programie Jamf Pro
keywords: policies, microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, installation, deploy, dezinstalacja, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 6e3a31343468b79ff1117a60eca6a87825562778
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466790"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>Konfigurowanie zasad Ochrona punktu końcowego w usłudze Microsoft Defender macOS w programie Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Program Defender dla punktu końcowego na komputerze Mac](microsoft-defender-endpoint-mac.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ta strona zawiera instrukcje niezbędne do skonfigurowania zasad macOS w programie Jamf Pro.

Musisz wykonać następujące czynności:

1. [Uzyskaj Ochrona punktu końcowego w usłudze Microsoft Defender pakietu dołączania](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [Tworzenie profilu konfiguracji w programie Jamf Pro przy użyciu pakietu dołączania](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender sieci](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender powiadomień](#step-4-configure-notifications-settings)
5. [Konfigurowanie programu Microsoft AutoUpdate (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [Udzielanie pełnego dostępu dyskowe do Ochrona punktu końcowego w usłudze Microsoft Defender](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [Zatwierdź rozszerzenie Kernel dla Ochrona punktu końcowego w usłudze Microsoft Defender](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [Zatwierdzanie rozszerzeń systemowych dla Ochrona punktu końcowego w usłudze Microsoft Defender](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [Konfigurowanie rozszerzenia sieci](#step-9-configure-network-extension)
10. [Planowanie skanów za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>Krok 1. Uzyskiwanie pakietu Ochrona punktu końcowego w usłudze Microsoft Defender dołączania

1. W [Microsoft 365 Defender](https://security.microsoft.com) przejdź do Ustawienia > **punktów końcowych > dołączanie**.

2. Jako metodę wdrażania wybierz system operacyjny macOS i Zarządzanie urządzeniami / Microsoft Intune dla urządzeń przenośnych.

   :::image type="content" source="images/onboarding-macos.png" alt-text="Strona Ustawienia strony Centrum zabezpieczeń usługi Microsoft Defender" lightbox="images/onboarding-macos.png":::

3. Wybierz **pozycję Pobierz pakiet dołączający** (WindowsDefenderATPOnboardingPackage.zip).

4. Wyodrębnij `WindowsDefenderATPOnboardingPackage.zip`.

5. Skopiuj plik do preferowanej lokalizacji. Na przykład `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>Krok 2. Tworzenie profilu konfiguracji w programie Jamf Pro przy użyciu pakietu dołączania

1. Znajdź plik z `WindowsDefenderATPOnboarding.plist` poprzedniej sekcji.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="The Windows Defender ATP Onboarding file" lightbox="images/plist-onboarding-file.png":::

2. Zaloguj się do usługi Jamf Pro do **opcji** **KomputeryKonfiguracja** >  Profile i wybierz pozycję **Nowy**.

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="Strona, na której tworzysz nowy pulpit nawigacyjny usługi Jamf Pro usługi" lightbox="images/jamf-pro-configure-profile.png":::

3. Wprowadź następujące szczegóły:

   **Informacje ogólne**:

   - Nazwa: Dołączanie do usługi MDE dla systemu macOS
   - Opis: dołączanie do EDR MDE dla systemu macOS
   - Kategoria: Brak
   - Metoda dystrybucji: automatyczne instalowanie
   - Poziom: Poziom komputera

4.  Przejdź do strony **& niestandardowej Ustawienia** i wybierz **pozycję Upload** >  **Add**.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="Konfigurowanie aplikacji i ustawień niestandardowych" lightbox="images/jamfpro-mac-profile.png":::

5. Wybierz **Upload Plik (plik PLIST),** a następnie w **preferencjach Domena wprowadź**: `com.microsoft.wdav.atp`.

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="Plik przekazywania pliku jamfpro plist" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="Właściwość przekazywania pliku Plik listy" lightbox="images/jamfpro-plist-file.png":::

6. Wybierz **pozycję** Otwórz i wybierz plik dołączania.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="Plik dołączania" lightbox="images/jamfpro-plist-file-onboard.png":::

7. Wybierz **Upload**.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="Plik plist przekazywania" lightbox="images/jamfpro-upload-plist.png":::

8. Wybierz **kartę Zakres** .

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="Karta Zakres" lightbox="images/jamfpro-scope-tab.png":::

9. Wybierz komputery docelowe.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="Komputery docelowe" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="Cele" lightbox="images/jamfpro-targets.png":::

10. Wybierz **Zapisz**.

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="Wdrażanie komputerów docelowych" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="Wybór komputerów docelowych" lightbox="images/jamfpro-target-selected.png":::

11. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="Komputery grupy docelowej" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="Lista profilów konfiguracji" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>Krok 3. Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender danych

Możesz użyć graficznego interfejsu użytkownika usługi JAMF Pro do edytowania poszczególnych ustawień konfiguracji usługi Ochrona punktu końcowego w usłudze Microsoft Defender lub użyć starszej metody, tworząc listę konfiguracji w edytorze tekstów i przesyłając ją do usługi JAMF Pro.

Zwróć uwagę, że należy dokładnie użyć domeny `com.microsoft.wdav` **preferencji**, `com.microsoft.wdav.ext` Ochrona punktu końcowego w usłudze Microsoft Defender tylko tej nazwy i załadować jej ustawienia zarządzane!

Ta wersja `com.microsoft.wdav.ext` może być używana w rzadkich przypadkach, gdy wolisz używać metody graficznego interfejsu użytkownika, ale musisz też skonfigurować ustawienie, które nie zostało jeszcze dodane do schematu.

### <a name="gui-method"></a>Metoda graficznego interfejsu użytkownika

1. Pobierz plik schema.json z repozytorium GitHub [Defender i](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) zapisz go w pliku lokalnym:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. Utwórz nowy profil konfiguracji w obszarze Komputery > profilów konfiguracji wprowadź następujące szczegóły na **karcie** Ogólne:

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Nowy profil" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - Nazwa: Ustawienia konfiguracji MDAV MDAV USŁUGI MDATP
    - Opis:\<blank\>
    - Kategoria: Brak (domyślna)
    - Poziom: Poziom komputera (domyślny)
    - Metoda dystrybucji: Instalacja automatycznie (domyślna)

3. Przewiń w dół do **karty & Niestandardowe Ustawienia** aplikacji, wybierz pozycję Aplikacje **zewnętrzne, kliknij** pozycję Dodaj  i użyj schematu  niestandardowego jako źródła do użycia w domenie preferencji.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="Dodawanie schematu niestandardowego" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. Wprowadź `com.microsoft.wdav` jako domenę preferencji, kliknij pozycję **Dodaj schemat** **i Upload** plik schema.json pobrany w kroku 1. Kliknij **Zapisz**.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="Upload schemat" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. Wszystkie obsługiwane ustawienia konfiguracji Ochrona punktu końcowego w usłudze Microsoft Defender można zobaczyć poniżej w obszarze **Preference Domain Properties (Właściwości domeny preferencji**). Kliknij **pozycję Dodaj/Usuń właściwości** , aby wybrać ustawienia, które mają być zarządzane, a następnie kliknij przycisk **OK** , aby zapisać zmiany. (Ustawienia pozostawione niewybrane nie zostaną uwzględnione w konfiguracji zarządzanej, użytkownik końcowy będzie mógł skonfigurować te ustawienia na swoich komputerach.

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="Wybrane ustawienia zarządzane" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. Zmień wartości ustawień na żądane wartości. Możesz kliknąć pozycję **Więcej informacji,** aby uzyskać dokumentację dla określonego ustawienia. (Możesz kliknąć pozycję **Podgląd listy,** aby sprawdzić, jak będzie wyglądała lista plist konfiguracji. Kliknij **pozycję Edytor formularzy** , aby powrócić do edytora wizualnego).

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="Strona, na której można zmienić wartości ustawień" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. Wybierz **kartę Zakres** .

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Zakres profilu konfiguracji" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. Wybierz **pozycję Grupa komputerowa firmy Contoso**.

9. Wybierz **pozycję Dodaj**, a następnie wybierz **pozycję Zapisz**.

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Strona, na której można dodać ustawienia konfiguracji" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Strona, na której można zapisać ustawienia konfiguracji" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy profil **konfiguracji**.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Strona, na której są ukończone ustawienia konfiguracji" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

Ochrona punktu końcowego w usłudze Microsoft Defender z czasem nowe ustawienia. Te nowe ustawienia zostaną dodane do schematu i nowa wersja zostanie opublikowana w witrynie Github.
Aby mieć aktualizacje, wystarczy pobrać zaktualizowany schemat, edytować istniejący profil konfiguracji i pozycję Edytuj schemat na karcie Niestandardowy &  **Ustawienia** aplikacji.

### <a name="legacy-method"></a>Starsza metoda

1. Użyj następujących Ochrona punktu końcowego w usłudze Microsoft Defender konfiguracji:

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

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="Strona z wyświetlonym nowym profilem" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Ustawienia konfiguracji MDAV MDAV USŁUGI MDATP
    - Opis:\<blank\>
    - Kategoria: Brak (domyślna)
    - Metoda dystrybucji: Zainstaluj automatycznie(domyślnie)
    - Poziom: Poziom komputera(domyślnie)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="Ustawienia konfiguracji MDAV MDAV usługi MDATP" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. W **czacie & Pozycję Ustawienia** pozycję **Konfiguruj**.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="Ustawienia aplikacji i niestandardowe" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. Wybierz **Upload plik (PLIST**).

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="Plik plist ustawień konfiguracji" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. W **oknie Preferencje** w domenie wpisz `com.microsoft.wdav`, a **następnie Upload plik PLIST**.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="Domena preferencji ustawień konfiguracji" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. Wybierz **pozycję Wybierz plik**.

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="Monit o wybranie pliku plist" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. Wybierz pozycję **MDATP_MDAV_configuration_settings.plist**, a następnie wybierz pozycję **Otwórz**.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="Ustawienia konfiguracji mdatpmdav" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. Wybierz **Upload**.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="Przekazywanie ustawień konfiguracji" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="Monit o przekazanie obrazu związanego z ustawieniami konfiguracji" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > Jeśli się zdarzy, że przekażesz Intune, zostanie wyświetlany następujący komunikat o błędzie:
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="Monit o przekazanie pliku intune związanego z ustawieniami konfiguracji" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. Wybierz **Zapisz**.

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="Opcja zapisania obrazu związanego z ustawieniami konfiguracji" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. Plik zostanie przekazany.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="Przekazany plik powiązany z ustawieniami konfiguracji" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="Strona ustawień konfiguracji" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. Wybierz **kartę Zakres** .

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="Zakres ustawień konfiguracji" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. Wybierz **pozycję Grupa komputerowa firmy Contoso**.

15. Wybierz **pozycję Dodaj**, a następnie wybierz **pozycję Zapisz**.

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="Ustawienia konfiguracji dodajeav" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="Powiadomienie o ustawieniach konfiguracji" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy profil **konfiguracji**.

    ![Obraz profilu konfiguracji ustawień konfiguracji.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="Ustawienia profilu konfiguracji" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

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

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="Strona nowego profilu konfiguracji systemu macOS" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - Powiadomienia **na karcie** Kliknij przycisk **Dodaj** i wprowadź następujące wartości:
        - **Identyfikator pakietu**: `com.microsoft.wdav.tray`
        - **Alerty krytyczne**: kliknij **pozycję Wyłącz**
        - **Powiadomienia**: Kliknij pozycję **Włącz.**
        - **Typ alertu na banerze**: Wybierz **pozycję Dołącz** **i Tymczasowy** *(domyślny)*
        - **Powiadomienia na ekranie blokady**: Kliknij pozycję **Ukryj**
        - **Powiadomienia w Centrum powiadomień**: Kliknij pozycję **Wyświetlanie**
        - **Ikona aplikacji znaczek**: kliknij pozycję **Wyświetlanie**

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="The configuration settings mdatpmdav notifications tray" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - Powiadomienia **na karcie** kliknij **pozycję Dodaj** jeszcze raz, przewiń w dół do **menu Nowe powiadomienia Ustawienia**
        - **Identyfikator pakietu**: `com.microsoft.autoupdate2`
        - Skonfiguruj pozostałe ustawienia na takie same wartości jak powyżej

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="Ustawienia konfiguracji mau powiadomień mdatpmdav" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        Zauważ, że teraz masz dwie "tabele" z konfiguracjami powiadomień: jedną dla identyfikatora pakietu **: com.microsoft.wdav.tray**, a drugą dla identyfikatora pakietu **: com.microsoft.autoupdate2**. Chociaż możesz skonfigurować ustawienia alertów zgodnie z wymaganiami, identyfikatory pakietów muszą być dokładnie takie same, jak opisano wcześniej, a przełącznik Dołącz  musi być włączony dla **powiadomień**.

3. Wybierz **kartę Zakres** , a następnie wybierz pozycję **Dodaj**.

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="Strona, na której można dodawać wartości w ustawieniach konfiguracji" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. Wybierz **pozycję Grupa komputerowa firmy Contoso**.

5. Wybierz **pozycję Dodaj**, a następnie wybierz **pozycję Zapisz**.

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="Strona, na której można zapisywać wartości w ustawieniach konfiguracji grupy komputera Contoso" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="Strona z powiadomieniem o ukończeniu ustawień konfiguracji" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. Wybierz pozycję **Gotowe**. Zostanie wyświetlony nowy profil **konfiguracji**.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="Ukończone ustawienia konfiguracji" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>Krok 5. Konfigurowanie programu Microsoft AutoUpdate (MAU)

1. Użyj następujących Ochrona punktu końcowego w usłudze Microsoft Defender konfiguracji:

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

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="Ustawienia konfiguracji" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Ustawienia MDATP MDAV MAU
    - Opis: Ustawienia programu Microsoft AutoUpdate w układzie MDATP dla systemu macOS
    - Kategoria: Brak (domyślna)
    - Metoda dystrybucji: Zainstaluj automatycznie(domyślnie)
    - Poziom: Poziom komputera(domyślnie)

5. W **czacie & Pozycję Ustawienia** pozycję **Konfiguruj**.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="Aplikacja ustawień konfiguracji i ustawienia niestandardowe" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. Wybierz **Upload plik (PLIST**).

7. W **preferencjach Domena** wprowadź: `com.microsoft.autoupdate2`, a **następnie Upload plik PLIST**.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="Domena preferencji ustawień konfiguracji" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. Wybierz **pozycję Wybierz plik**.

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="Monit o wybranie pliku dotyczącego ustawienia konfiguracji" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. Wybierz **MDATP_MDAV_MAU_settings.plist**.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="Ustawienia mdatpmdavmau" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. Wybierz **Upload**.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="Przekazywanie pliku dotyczące ustawienia konfiguracji" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="Strona z opcją przekazywania dla pliku związanego z ustawieniem konfiguracji" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. Wybierz **Zapisz**.

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="Strona z opcją zapisywania pliku dotyczącą ustawienia konfiguracji" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. Wybierz **kartę Zakres** .

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="Karta Zakres dla ustawień konfiguracji" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. Wybierz opcję **Dodaj**.

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="Opcja dodania celów wdrażania" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="Strona, na której dodaje się więcej wartości do ustawień konfiguracji" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="Strona, na której można dodać więcej wartości do ustawień konfiguracji" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="Powiadomienie o ukończeniu dotyczące ustawień konfiguracji" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>Krok 6. Udzielanie pełnego dostępu do Ochrona punktu końcowego w usłudze Microsoft Defender

1. Na pulpicie nawigacyjnym usługi Pro Jamf wybierz **pozycję Profile konfiguracji**.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="Profil, dla którego należy skonfigurować ustawienia" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. Wybierz **pozycję + Nowy**.

3. Wprowadź następujące szczegóły:

    **Ogólne**
    - Nazwa: MDAV MDAV MDAV — udzielanie pełnego dostępu EDR audio/wideo
    - Opis: W systemie macOS Catalina lub nowszej nowej kontroli zasad preferencji prywatności
    - Kategoria: Brak
    - Metoda dystrybucji: Instalowanie automatycznie
    - Poziom: poziom komputera

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="Ogólne ustawienie konfiguracji" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. W **oknie Konfigurowanie preferencji prywatności, kontrola zasad wybierz** **pozycję Konfiguruj**.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="Kontrola zasad zachowania poufności informacji dotyczących konfiguracji" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. W **oknie Kontrola zasad preferencji prywatności** wprowadź następujące szczegóły:

    - Identyfikator: `com.microsoft.wdav`
    - Typ identyfikatora: Identyfikator pakietu
    - Wymaganie kodu: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="Szczegóły kontroli zasad preferencji prywatności przy ustawianiu konfiguracji" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. Wybierz **pozycję + Dodaj**.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="Opcja dodawania zasad systemowych do wszystkich plików przez ustawienie konfiguracji" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - W obszarze Aplikacja lub usługa: Ustaw na **wartość SystemPolicyAllFiles**

    - W obszarze "dostęp": Ustaw na **zezwalanie**

7. Wybierz **pozycję** Zapisz (nie tę u dołu po prawej stronie).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="Operacja zapisywania dla ustawienia konfiguracji" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. Kliknij znak `+` obok pozycji **App Access,** aby dodać nową pozycję.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="Operacja zapisywania związana z ustawieniem konfiguracji" lightbox="images/tcc-add-entry.png":::

9. Wprowadź następujące szczegóły:

    - Identyfikator: `com.microsoft.wdav.epsext`
    - Typ identyfikatora: Identyfikator pakietu
    - Wymaganie kodu: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. Wybierz **pozycję + Dodaj**.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="The configuration setting tcc epsext entry" lightbox="images/tcc-epsext-entry.png":::

    - W obszarze Aplikacja lub usługa: Ustaw na **wartość SystemPolicyAllFiles**

    - W obszarze "dostęp": Ustaw na **zezwalanie**

11. Wybierz **pozycję** Zapisz (nie tę u dołu po prawej stronie).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="Drugie wystąpienie ustawień konfiguracji tcc epsext" lightbox="images/tcc-epsext-entry2.png":::

12. Wybierz **kartę Zakres** .

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="Strona przedstawiająca zakres ustawienia konfiguracji" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. Wybierz **pozycję + Dodaj**.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="Strona przedstawiająca ustawienie konfiguracji" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. Wybierz **pozycję Grupy komputerów** > **w obszarze** Nazwa > wybierz pozycję **Grupa maszynowa firmy Contoso**.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="The configuration setting contoso machine group" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. Wybierz opcję **Dodaj**.

16. Wybierz **Zapisz**.

17. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="Ustawienie konfiguracji contoso machine-group" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Ilustracja ustawień konfiguracji" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

Ewentualnie możesz pobrać [plik fullconfig.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) i przekazać go do profilów konfiguracji usługi JAMF zgodnie z opisem w tece Wdrażania niestandardowych profilów konfiguracji za pomocą usługi [Jamf Pro| Metoda 2. Upload profilu konfiguracji do usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>Krok 7. Zatwierdź rozszerzenie kernel dla Ochrona punktu końcowego w usłudze Microsoft Defender

> [!CAUTION]
> Urządzenia apple Silicon (M1) nie obsługują doc. Instalacja profilu konfiguracji składającego się z zasad KEXT nie powiedzie się na tych urządzeniach.

1. W profilu **konfiguracji** wybierz pozycję **+ Nowy**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Wpis w mediach społecznościowych Automatycznie wygenerowany Opis" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Rozszerzenie MDAV MDAV MDAV
    - Opis: rozszerzenie kernelu MDATP (kext)
    - Kategoria: Brak
    - Metoda dystrybucji: automatyczne instalowanie
    - Poziom: Poziom komputera

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="Ustawienia konfiguracji kernelu mdatpmdav" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. W **ustawień Configure Approved Kernel Extensions (Konfiguruj zatwierdzone rozszerzenia kernelu)** wybierz **pozycję Configure (Konfiguruj**).

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="Strona z wyświetlonymi ustawieniami konfiguracji zatwierdzonymi rozszerzeniami kernelu" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. W **zatwierdzonych rozszerzeniach kerneli** wprowadź następujące szczegóły:

    - Nazwa wyświetlana: Microsoft Corp.
    - Identyfikator zespołu: UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="Okienko Zatwierdzone rozszerzenia kernelu" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. Wybierz **kartę Zakres** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Karta Zakres konfiguracji" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Wybierz **pozycję + Dodaj**.

7. Wybierz **pozycję Grupy komputerów** > **obszarze** Nazwa > wybierz pozycję **Grupa komputerów firmy Contoso**.

8. Wybierz **pozycję + Dodaj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Strona, na której definiujesz dodatkowe wartości dla ustawień konfiguracji" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Wybierz **Zapisz**.

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="Rozszerzenie MDAV MDAV" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="Strona szczegółów profilów konfiguracji" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

Ewentualnie możesz pobrać [plik kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) i przekazać go do profilów konfiguracji usługi JAMF zgodnie z opisem w tece Wdrażania niestandardowych profilów konfiguracji za pomocą usługi [Jamf Pro| Metoda 2. Upload profilu konfiguracji do usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>Krok 8. Zatwierdzanie rozszerzeń systemu dla systemu Ochrona punktu końcowego w usłudze Microsoft Defender

1. W profilu **konfiguracji** wybierz pozycję **+ Nowy**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="Opis automatycznie wygenerowanego wpisu w mediach społecznościowych" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. Wprowadź następujące szczegóły:

    **Ogólne**

    - Nazwa: Rozszerzenia systemowe MDAV MDATP
    - Opis: Rozszerzenia systemowe MDATP
    - Kategoria: Brak
    - Metoda dystrybucji: automatyczne instalowanie
    - Poziom: Poziom komputera

    :::image type="content" source="images/sysext-new-profile.png" alt-text="Ustawienia konfiguracji sysext nowy profil" lightbox="images/sysext-new-profile.png":::

3. W **rozszerzeniach systemu** wybierz **pozycję Konfiguruj**.

   :::image type="content" source="images/sysext-configure.png" alt-text="Okienko z opcją Konfiguruj dla rozszerzeń systemowych" lightbox="images/sysext-configure.png":::

4. W **rozszerzeniach systemu** wprowadź następujące szczegóły:

   - Nazwa wyświetlana: Microsoft Corp. Rozszerzenia systemu
   - Typy rozszerzeń systemu: dozwolone rozszerzenia systemu
   - Identyfikator zespołu: UBF8T346G9
   - Dozwolone rozszerzenia systemowe:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="Okienko rozszerzeń MDATP systemu MDAV" lightbox="images/sysext-configure2.png":::

5. Wybierz **kartę Zakres** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Okienko zaznaczenia Komputery docelowe" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. Wybierz **pozycję + Dodaj**.

7. Wybierz **pozycję Grupy komputerów** > **obszarze** Nazwa > wybierz pozycję **Grupa komputerów firmy Contoso**.

8. Wybierz **pozycję + Dodaj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Okienko Nowy profil konfiguracji systemu macOS" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. Wybierz **Zapisz**.

   :::image type="content" source="images/sysext-scope.png" alt-text="Wyświetlanie opcji dotyczących rozszerzeń MDAV MDAV MDAV" lightbox="images/sysext-scope.png":::

10. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/sysext-final.png" alt-text="Ustawienia konfiguracji sysext - final" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>Krok 9. Konfigurowanie rozszerzenia sieci

W ramach funkcji wykrywania punktu końcowego i odpowiedzi użytkownicy Ochrona punktu końcowego w usłudze Microsoft Defender systemie macOS sprawdzają ruch sieciowy i raportują te informacje w portalu usługi Microsoft 365 Defender sieci. Poniższe zasady pozwalają na korzystanie z tej funkcji przez rozszerzenie sieci.

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

        :::image type="content" source="images/netext-create-profile.png" alt-text="Ustawienie konfiguracji mdatpmdav" lightbox="images/netext-create-profile.png":::

3. Wybierz **kartę Zakres** .

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="Karta zakresu ustawień konfiguracji" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. Wybierz **pozycję + Dodaj**.

5. Wybierz **pozycję Grupy komputerów** > **obszarze** Nazwa > wybierz pozycję **Grupa komputerów firmy Contoso**.

6. Wybierz **pozycję + Dodaj**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="Ustawienia konfiguracji adim" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. Wybierz **Zapisz**.

   :::image type="content" source="images/netext-scope.png" alt-text="Okienko Filtr zawartości" lightbox="images/netext-scope.png":::

8. Wybierz pozycję **Gotowe**.

   :::image type="content" source="images/netext-final.png" alt-text="Ustawienia konfiguracji netext - final" lightbox="images/netext-final.png":::

Ewentualnie możesz pobrać plik [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) i przekazać go do profilów konfiguracji usługi JAMF zgodnie z opisem w tece Wdrażania niestandardowych profilów konfiguracji za pomocą usługi [Jamf Pro| Metoda 2. Upload profilu konfiguracji do usługi Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>Krok 10. Planowanie skanów za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS

Postępuj zgodnie z instrukcjami [w tece Planowanie skanów za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>Krok 11. Wdrażanie usługi Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS

1. Przejdź do miejsca, w którym został zapisany.`wdav.pkg`

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="Pakiet wdav eksploratora plików" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. Zmień nazwę na `wdav_MDM_Contoso_200329.pkg`.

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="Pakiet wdavmdm w eksploratorze plików" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. Otwórz pulpit nawigacyjny usługi Jamf Pro jamf.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="Ustawienia konfiguracji jamfpro" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. Wybierz komputer i kliknij ikonę koła zębatego u góry, a następnie wybierz pozycję **Zarządzanie komputerem**.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="Ustawienia konfiguracji — zarządzanie komputerem" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. W **pakietuch** wybierz **pozycję + Nowy**.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="Opis ptaka dla automatycznie wygenerowanego pakietu" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. W **nowym pakiecie** Wprowadź następujące szczegóły:

    **Karta Ogólne**
    - Nazwa wyświetlana: na razie pozostaw to pole puste. Zostanie on zresetowany po wybraniu Twojego pkg.
    - Kategoria: Brak (domyślna)
    - Nazwa pliku: wybierz pozycję Plik

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="Karta Ogólne w ustawieniach konfiguracji" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    Otwórz plik i wskaż go lub `wdav.pkg` `wdav_MDM_Contoso_200329.pkg`.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="Ekran komputera z opisem pakietu wygenerowanego automatycznie" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. Wybierz opcję **Otwórz**. Ustaw nazwę **wyświetlaną na** Zaawansowana ochrona przed zagrożeniami w **uchcie microsoft Defender i Program antywirusowy Microsoft Defender**.

    **Plik manifestu** nie jest wymagany. Ochrona punktu końcowego w usłudze Microsoft Defender działa bez pliku manifestu.

    **Karta Opcje**: Zachowaj wartości domyślne.

    **Karta Ograniczenia**: Zachowaj wartości domyślne.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="Karta ograniczenia ustawień konfiguracji" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. Wybierz **Zapisz**. Pakiet zostanie przekazany do aplikacji Jamf Pro.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="Proces przekazywania pakietu ustawień konfiguracji dla pakietu związanego z ustawieniami konfiguracji" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   Może potrwać kilka minut, aby pakiet był dostępny do wdrożenia.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="Wystąpienie przekazywania pakietu w celu ustawienia konfiguracji" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. Przejdź do **strony Zasady** .

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="Zasady ustawień konfiguracji" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. Wybierz **pozycję + Nowy** , aby utworzyć nowe zasady.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="Nowe zasady ustawień konfiguracji" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. **Ogólne Wprowadź** następujące szczegóły:

    - Nazwa wyświetlana: Dołączanie usługi MDATP firmy Contoso 200329 od wersji 100.86.92 do wersji 100.86.92 lub nowszej

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="Ustawienia konfiguracji — onboard MDATP" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. Wybierz **pozycję Sprawdzanie cykliczne**.

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="Cykliczne sprawdzanie ustawień konfiguracji" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. Wybierz **Zapisz**.

14. Wybierz **pozycję Pakiety > Konfigurowanie**.

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="Opcja konfigurowania pakietów" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. Wybierz przycisk **Dodaj** obok usługi **Microsoft Defender Advanced Threat Protection i Program antywirusowy Microsoft Defender**.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="Opcja dodania kolejnych ustawień do MDATP MDA" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. Wybierz **Zapisz**.

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="Opcja zapisywania dla ustawień konfiguracji" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. Wybierz **kartę Zakres** .

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="Karta Zakres powiązana z ustawieniami konfiguracji" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. Wybierz komputery docelowe.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="Opcja dodawania grup komputerów" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **Zakres**

    Wybierz opcję **Dodaj**.

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="Ustawienia konfiguracji — ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="Ustawienia konfiguracji — ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **Samoobsługowa**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="Karta Samoobsługa dla ustawień konfiguracji" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. Wybierz pozycję **Gotowe**.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="Stan dołączania do firmy Contoso z opcją jego ukończenia" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="Strona zasad" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
