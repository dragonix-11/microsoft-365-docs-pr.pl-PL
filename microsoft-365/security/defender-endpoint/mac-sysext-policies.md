---
title: Nowe profile konfiguracji systemu macOS Catalina i nowsze wersje systemu macOS
description: W tym temacie opisano zmiany, które należy wprowadzić, aby skorzystać z rozszerzeń systemowych, które zastępują rozszerzenia kernel w systemie macOS Catalina i nowsze wersje systemu macOS.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, kernel, system, extensions, catalina
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: security
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
ROBOTS: noindex,nofollow
ms.technology: mde
ms.openlocfilehash: 53194aac16091b9afd9559b4f372c2d436c198bf
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474712"
---
# <a name="new-configuration-profiles-for-macos-catalina-and-newer-versions-of-macos"></a>Nowe profile konfiguracji systemu macOS Catalina i nowsze wersje systemu macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Zgodnie z dostosowaniem do wersji macOS, przygotowujemy aktualizację systemu Ochrona punktu końcowego w usłudze Microsoft Defender macOS, która korzysta z rozszerzeń systemowych, a nie rozszerzeń kernel. Ta aktualizacja będzie miała zastosowanie tylko do systemu macOS Catalina (10.15.4) i nowszej wersji systemu macOS.

Jeśli wdrożono usługę Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS w środowisku zarządzanym (za pośrednictwem usługi JAMF, Intune lub innego rozwiązania MDM), musisz wdrożyć nowe profile konfiguracji. W przypadku pomiń te czynności użytkownicy będą otrzymywać monity o zatwierdzenie w celu uruchomienia tych nowych składników.

## <a name="jamf"></a>JAMF

### <a name="jamf-system-extensions-policy"></a>Zasady rozszerzeń systemu JAMF

Aby zatwierdzić rozszerzenia systemu, utwórz następujący ład:

1. Na **> profilów konfiguracji** wybierz **pozycję Opcje > rozszerzenia systemu**.
2. Wybierz **pozycję Dozwolone rozszerzenia systemowe** z **listy** rozwijanej Typy rozszerzeń systemu.
3. Identyfikator **zespołu należy stosować w przypadku dokumentu UBF8T346G9** .
4. Dodaj następujące identyfikatory pakietów do listy **Dozwolonych rozszerzeń systemowych** :

    - **com.microsoft.wdav.epsext**
    - **com.microsoft.wdav.netext**

    :::image type="content" source="images/mac-approved-system-extensions.png" alt-text=" Strona Zatwierdzone rozszerzenia systemowe" lightbox="images/mac-approved-system-extensions.png":::

### <a name="privacy-preferences-policy-control"></a>Kontrola zasad preferencji prywatności

Dodaj następujący ładład usługi JAMF, aby udzielić pełnego dostępu dyskowego do Ochrona punktu końcowego w usłudze Microsoft Defender zabezpieczeń punktu końcowego. Te zasady są wymaganie wstępne dla uruchomienia rozszerzenia na Twoim urządzeniu.

1. Wybierz pozycję **Opcje Preferencje** \> **prywatności Kontrola zasad**.
2. Użyj `com.microsoft.wdav.epsext` jako typu **Identyfikator** i `Bundle ID` **jako pakietu**.
3. Ustaw wymaganie kodu na `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
4. Ustaw **dla aplikacji lub usługi** **wartość SystemPolicyAllFiles i** dostęp do **zezwalania**.

   :::image type="content" source="images/mac-system-extension-privacy.png" alt-text=" Element menu Sterowanie zasadami preferencji prywatności" lightbox="images/mac-system-extension-privacy.png":::

### <a name="network-extension-policy"></a>Zasady rozszerzenia sieci

W ramach funkcji wykrywania punktu końcowego i odpowiedzi użytkownicy Ochrona punktu końcowego w usłudze Microsoft Defender systemie macOS sprawdzają ruch sieciowy i raportują te informacje w portalu usługi Microsoft 365 Defender sieci. Poniższe zasady pozwalają na korzystanie z tej funkcji przez rozszerzenie sieci.

> [!NOTE]
> Program JAMF nie ma wbudowanej obsługi zasad filtrowania zawartości, które są wymaganie wstępne dla włączenia rozszerzeń sieciowych, które Ochrona punktu końcowego w usłudze Microsoft Defender w instalacjach systemu macOS na urządzeniu. Ponadto niekiedy program JAMF zmienia treść wdrażanych zasad.
> W związku z tym poniższe kroki zapewniają obejście, które obejmuje podpisywanie profilu konfiguracji.

1. Zapisz na urządzeniu następującą zawartość jako edytor `com.microsoft.network-extension.mobileconfig` tekstu:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1">
        <dict>
            <key>PayloadUUID</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadType</key>
            <string>Configuration</string>
            <key>PayloadOrganization</key>
            <string>Microsoft Corporation</string>
            <key>PayloadIdentifier</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft Defender Network Extension</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>PayloadRemovalDisallowed</key>
            <true/>
            <key>PayloadScope</key>
            <string>System</string>
            <key>PayloadContent</key>
            <array>
                <dict>
                    <key>PayloadUUID</key>
                    <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                    <key>PayloadType</key>
                    <string>com.apple.webcontent-filter</string>
                    <key>PayloadOrganization</key>
                    <string>Microsoft Corporation</string>
                    <key>PayloadIdentifier</key>
                    <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                    <key>PayloadDisplayName</key>
                    <string>Approved Network Extension</string>
                    <key>PayloadDescription</key>
                    <string/>
                    <key>PayloadVersion</key>
                    <integer>1</integer>
                    <key>PayloadEnabled</key>
                    <true/>
                    <key>FilterType</key>
                    <string>Plugin</string>
                    <key>UserDefinedName</key>
                    <string>Microsoft Defender Network Extension</string>
                    <key>PluginBundleID</key>
                    <string>com.microsoft.wdav</string>
                    <key>FilterSockets</key>
                    <true/>
                    <key>FilterDataProviderBundleIdentifier</key>
                    <string>com.microsoft.wdav.netext</string>
                    <key>FilterDataProviderDesignatedRequirement</key>
                    <string>identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                </dict>
            </array>
        </dict>
    </plist>
    ```

2. Sprawdź, czy powyższy plik został poprawnie skopiowany, uruchamiając narzędzie `plutil` w programie Terminal:

    ```bash
    $ plutil -lint <PathToFile>/com.microsoft.network-extension.mobileconfig
    ```

    Jeśli na przykład plik był przechowywany w dokumentach:

    ```bash
    $ plutil -lint ~/Documents/com.microsoft.network-extension.mobileconfig
    ```

    Sprawdź, czy wyniki poleceń `OK`.

    ```bash
    <PathToFile>/com.microsoft.network-extension.mobileconfig: OK
    ```

3. Postępuj zgodnie z instrukcjami [na tej](https://www.jamf.com/jamf-nation/articles/649/creating-a-signing-certificate-using-jamf-pro-s-built-in-certificate-authority) stronie, aby utworzyć certyfikat podpisywania przy użyciu wbudowanego urzędu certyfikacji usługi JAMF.

4. Po utworzeniu i zainstalowaniu certyfikatu na urządzeniu uruchom następujące polecenie z aplikacji Terminal, aby podpisać plik:

    ```bash
    $ security cms -S -N "<CertificateName>" -i <PathToFile>/com.microsoft.network-extension.mobileconfig -o <PathToSignedFile>/com.microsoft.network-extension.signed.mobileconfig
    ```

    Jeśli na przykład nazwa certyfikatu to **SigningCertificate** , a podpisany plik zostanie zapisany w dokumentach:

    ```bash
    $ security cms -S -N "SigningCertificate" -i ~/Documents/com.microsoft.network-extension.mobileconfig -o ~/Documents/com.microsoft.network-extension.signed.mobileconfig
    ```

5. W portalu USŁUGI JAMF przejdź do strony Profile **konfiguracji** i kliknij **przycisk Upload** konfiguracji. Wybierz `com.microsoft.network-extension.signed.mobileconfig` po wyświetleniu monitu o plik.

## <a name="intune"></a>Intune

### <a name="intune-system-extensions-policy"></a>Intune rozszerzeń systemu

Aby zatwierdzić rozszerzenia systemowe:

1. W Intune otwórz **okno Zarządzanie konfiguracją** \> **urządzenia**. Wybierz **pozycję Zarządzaj profilami** \>  \> **Utwórz profil**.
2. Wybierz nazwę profilu. Zmień **platformę=macOS** na **Profile type=Extensions**. Wybierz pozycję **Utwórz**.
3. Na karcie `Basics` nadaj nazwę temu noweowi profilowi.
4. Na karcie `Configuration settings` dodaj następujące wpisy w sekcji `Allowed system extensions` :

   <br>

   ****

   |Identyfikator pakietu|Identyfikator zespołu|
   |---|---|
   |com.microsoft.wdav.epsext|UBF8T346G9|
   |com.microsoft.wdav.netext|UBF8T346G9|
   |||

   :::image type="content" source="images/mac-system-extension-intune2.png" alt-text=" Strona Profile konfiguracji systemu" lightbox="images/mac-system-extension-intune2.png":::

5. Na karcie `Assignments` przypisz ten profil wszystkim użytkownikom & **Wszystkich urządzeniach**.
6. Przejrzyj i utwórz ten profil konfiguracji.

### <a name="create-and-deploy-the-custom-configuration-profile"></a>Tworzenie i wdrażanie niestandardowego profilu konfiguracji

Poniższy profil konfiguracji umożliwia rozszerzenie sieci i udziela pełnego dostępu na dysku do rozszerzenia systemu zabezpieczeń punktu końcowego.

Zapisz następującą zawartość w pliku o **nazwiesysext.xml**:

```xml
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft Corporation</string>
        <key>PayloadIdentifier</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender System Extensions</string>
        <key>PayloadDescription</key>
        <string/>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                <key>PayloadType</key>
                <string>com.apple.webcontent-filter</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                <key>PayloadDisplayName</key>
                <string>Approved Network Extension</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>FilterType</key>
                <string>Plugin</string>
                <key>UserDefinedName</key>
                <string>Microsoft Defender Network Extension</string>
                <key>PluginBundleID</key>
                <string>com.microsoft.wdav</string>
                <key>FilterSockets</key>
                <true/>
                <key>FilterDataProviderBundleIdentifier</key>
                <string>com.microsoft.wdav.netext</string>
                <key>FilterDataProviderDesignatedRequirement</key>
                <string>identifier &quot;com.microsoft.wdav.netext&quot; and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
            </dict>
            <dict>
                <key>PayloadUUID</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadType</key>
                <string>com.apple.TCC.configuration-profile-policy</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadDisplayName</key>
                <string>Privacy Preferences Policy Control</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>Services</key>
                <dict>
                    <key>SystemPolicyAllFiles</key>
                    <array>
                        <dict>
                            <key>Identifier</key>
                            <string>com.microsoft.wdav.epsext</string>
                            <key>CodeRequirement</key>
                            <string>identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                            <key>IdentifierType</key>
                            <string>bundleID</string>
                            <key>StaticCode</key>
                            <integer>0</integer>
                            <key>Allowed</key>
                            <integer>1</integer>
                        </dict>
                    </array>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

Sprawdź, czy powyższy plik został prawidłowo skopiowany. Z terminalu uruchom następujące polecenie i sprawdź, czy jest wyprowadzzone `OK`:

```bash
$ plutil -lint sysext.xml
sysext.xml: OK
```

Aby wdrożyć ten niestandardowy profil konfiguracji:

1. W Intune otwórz **okno Zarządzanie konfiguracją** \> **urządzenia**. Wybierz **pozycję Zarządzaj profilami** \>  \> **Utwórz profil**.
2. Wybierz nazwę profilu. Zmień **platformę=macOS** i **profile type=Custom**. Wybierz **pozycję Konfiguruj**.
3. Otwórz profil konfiguracji i przekaż **sysext.xml**. Ten plik został utworzony w poprzednim kroku.
4. Wybierz przycisk **OK**.

   :::image type="content" source="images/mac-system-extension-intune.png" alt-text="Rozszerzenie systemu na Intune sieci Web" lightbox="images/mac-system-extension-intune.png":::

5. Na karcie `Assignments` przypisz ten profil wszystkim użytkownikom & **Wszystkich urządzeniach**.
6. Przejrzyj i utwórz ten profil konfiguracji.
