---
title: Wyłącz ochronę sieci
description: Włącz ochronę sieci za pomocą zasady grupy, programu PowerShell lub usługi Mobile Zarządzanie urządzeniami i Configuration Manager.
keywords: Ochrona sieci, luki w zabezpieczeniach, złośliwa witryna internetowa, adres IP, domena, domeny, włączanie, włączanie
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 9e94b164dd5c4863b792acdfdd36756ebd94347a
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66574008"
---
# <a name="turn-on-network-protection"></a>Wyłącz ochronę sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> [!TIP]
> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Ochrona sieci](network-protection.md) pomaga uniemożliwić pracownikom korzystanie z dowolnej aplikacji w celu uzyskania dostępu do niebezpiecznych domen, które mogą hostować wyłudzanie informacji, luki w zabezpieczeniach i inne złośliwe treści w Internecie. Ochronę [sieci można przeprowadzać](evaluate-network-protection.md) w środowisku testowym, aby sprawdzić, które aplikacje zostaną zablokowane przed włączeniem ochrony sieci.

[Dowiedz się więcej o opcjach konfiguracji filtrowania sieci.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>Sprawdzanie, czy ochrona sieci jest włączona

Sprawdź, czy ochrona sieci została włączona na urządzeniu lokalnym przy użyciu edytora rejestru.

1. Wybierz przycisk **Start** na pasku zadań i wpisz **regedit** , aby otworzyć edytor rejestru.

2. Wybierz **pozycję HKEY_LOCAL_MACHINE** z menu bocznego.

3. Przejdź przez zagnieżdżone menu do **obszaru Zasady** **oprogramowania** \> **Microsoft** \> \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

Jeśli brakuje klucza, **przejdź do** \> oprogramowania **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

4. Wybierz pozycję **EnableNetworkProtection** , aby wyświetlić bieżący stan ochrony sieci na urządzeniu:

   - 0 lub **Wyłączone**
   - 1 lub **Włączone**
   - 2 lub tryb **inspekcji**

    :::image type="content" source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" alt-text="Klucz rejestru usługi Network Protection" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::

## <a name="enable-network-protection"></a>Włączanie ochrony sieci

Włącz ochronę sieci przy użyciu dowolnej z następujących metod:

- [PowerShell](#powershell)
- [Zarządzanie urządzeniami przenośnymi (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager)
- [Zasady grupy](#group-policy)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. Wpisz **program PowerShell** w menu Start, kliknij prawym przyciskiem myszy **Windows PowerShell** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. Opcjonalnie: Włącz funkcję w trybie inspekcji przy użyciu następującego polecenia cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    Użyj `Disabled` zamiast `AuditMode` lub `Enabled` , aby wyłączyć funkcję.

### <a name="mobile-device-management-mdm"></a>Zarządzanie urządzeniami przenośnymi (MDM)

Użyj [dostawcy ./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) configuration service provider (CSP), aby włączyć lub wyłączyć ochronę sieci lub włączyć tryb inspekcji.

[Zaktualizuj platformę ochrony przed złośliwym kodem w usłudze Microsoft Defender do najnowszej wersji](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc) przed włączeniem lub wyłączeniem ochrony sieci lub włączeniem trybu inspekcji.


### <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

#### <a name="microsoft-defender-for-endpoint-baseline-method"></a>Ochrona punktu końcowego w usłudze Microsoft Defender metoda bazowa

1. Zaloguj się do centrum administracyjnego usługi Microsoft Endpoint Manager (https://endpoint.microsoft.com).
2. Przejdź do pozycji **Punkty odniesienia** >  zabezpieczeń  > **punktu końcowego** **Ochrona punktu końcowego w usłudze Microsoft Defender Punkt odniesienia**.
3. Wybierz **pozycję Utwórz profil**, a następnie podaj nazwę profilu, a następnie wybierz pozycję **Dalej**.
4. W sekcji **Ustawienia konfiguracji** przejdź do pozycji **Reguły zmniejszania obszaru podatnego na ataki** > ustawić **ustawienie Blokuj**, **Włącz** lub **Przeprowadź inspekcję** w **celu włączenia ochrony sieci**. Wybierz pozycję **Dalej**.
5. Wybierz odpowiednie **tagi zakresu** i **przypisania** zgodnie z wymaganiami organizacji.
7. Przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.

#### <a name="antivirus-policy-method"></a>Metoda zasad ochrony antywirusowej
1. Zaloguj się do centrum administracyjnego usługi Microsoft Endpoint Manager (https://endpoint.microsoft.com).
2. Przejdź do programu **antywirusowego** zabezpieczeń  > **punktu końcowego**
3. Wybierz **pozycję Utwórz zasady**
4. W oknie **wysuwnym Tworzenie zasad wybierz pozycję** **Windows 10, Windows 11 i Windows Server** z listy **Platforma**.
5. Wybierz pozycję **Microsoft Defender Antivirus** z listy **Profil** , a następnie wybierz pozycję **Utwórz**
6. Podaj nazwę profilu, a następnie wybierz pozycję **Dalej**.
7. W sekcji **Ustawienia konfiguracji** wybierz pozycję **Wyłączone**, **Włączone (tryb bloku)** lub **Włączone (tryb inspekcji)** w obszarze **Włącz ochronę sieci**, a następnie wybierz pozycję **Dalej**.
8. Wybierz odpowiednie **przypisania** i **tagi zakresu** zgodnie z wymaganiami organizacji.
9. Przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.

#### <a name="configuration-profile-method"></a>Metoda profilu konfiguracji

1. Zaloguj się do centrum administracyjnego usługi Microsoft Endpoint Manager (https://endpoint.microsoft.com).

2. Przejdź do **pozycji Profile** >  konfiguracji **urządzeń** > **Utwórz profil**.

3. W **wysuwnym Tworzenie profilu** wybierz pozycję **Platforma** i wybierz **typ profilu** jako **szablony**.

4. W **polu Nazwa szablonu** wybierz pozycję **Ochrona punktu końcowego** z listy szablonów, a następnie wybierz pozycję **Utwórz**.

4. Przejdź do pozycji **Podstawy** **programu Endpoint Protection** > , podaj nazwę profilu, a następnie wybierz pozycję **Dalej**.

5. W sekcji **Ustawienia konfiguracji** przejdź do obszaru **Filtrowanie** >  sieci **programu Microsoft Defender Exploit Guard** > **Ochrona** >  sieci **włącz** lub **przeprowadź inspekcję**. Wybierz pozycję **Dalej**.

6. Wybierz odpowiednie **tagi zakresu**, **przypisania** i **reguły stosowania** zgodnie z wymaganiami organizacji. Administratorzy mogą ustawić więcej wymagań.

7. Przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.

### <a name="group-policy"></a>Zasady grupy

Poniższa procedura umożliwia włączenie ochrony sieci na komputerach przyłączonych do domeny lub na komputerze autonomicznym.

1. Na komputerze autonomicznym przejdź do pozycji **Start** , a następnie wpisz i wybierz pozycję **Edytuj zasady grupy**.

    *-Or-*

    Na komputerze do zarządzania zasady grupy przyłączonym do domeny otwórz [konsolę zarządzania zasady grupy](https://technet.microsoft.com/library/cc731212.aspx), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo do **składników** \> systemu Windows **Microsoft Defender Antivirus** \> **Windows Defender exploit guard** \> **ochrony sieci**.

   > [!NOTE]
   > W starszych wersjach systemu Windows ścieżka zasad grupy może zawierać ciąg "Program antywirusowy Windows Defender" zamiast "Program antywirusowy Microsoft Defender".

4. Kliknij dwukrotnie ustawienie **Uniemożliwiaj użytkownikom i aplikacjom uzyskiwanie dostępu do niebezpiecznych witryn internetowych** i ustaw opcję **Włączone**. W sekcji opcje należy określić jedną z następujących opcji:
    - **Blokuj** — użytkownicy nie mogą uzyskiwać dostępu do złośliwych adresów IP i domen.
    - **Wyłącz (ustawienie domyślne)** — funkcja ochrony sieci nie będzie działać. Dostęp użytkowników do złośliwych domen nie zostanie zablokowany.
    - **Tryb inspekcji** — jeśli użytkownik odwiedzi złośliwy adres IP lub domenę, zdarzenie zostanie zarejestrowane w dzienniku zdarzeń systemu Windows. Jednak nie będzie można zablokować użytkownikowi możliwości odwiedzenia adresu.

   > [!IMPORTANT]
   > Aby w pełni włączyć ochronę sieci, należy ustawić opcję zasady grupy **włączone**, a także wybrać pozycję **Blokuj** w menu rozwijanym opcje.

   > [!NOTE]
   > Opcjonalnie: wykonaj kroki opisane w temacie [Sprawdzanie, czy włączono ochronę sieci](#check-if-network-protection-is-enabled), aby sprawdzić, czy ustawienia zasady grupy są poprawne.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Otwórz konsolę Configuration Manager.

2. Przejdź do **obszaru Assets and Compliance** > **Endpoint Protection** >  **Windows Defender Exploit Guard**.

3. Wybierz pozycję **Utwórz zasady funkcji Exploit Guard** na wstążce, aby utworzyć nowe zasady.
   - Aby edytować istniejące zasady, wybierz zasady, a następnie wybierz pozycję **Właściwości** na wstążce lub w menu kliknij prawym przyciskiem myszy. **Edytuj opcję Konfiguruj ochronę sieci** na karcie **Ochrona sieci**.  

4. Na stronie **Ogólne** określ nazwę nowych zasad i sprawdź, czy opcja **Ochrona sieci** jest włączona.

5. Na stronie **Ochrona sieci** wybierz jedno z następujących ustawień opcji **Konfiguruj ochronę sieci** :
   - **Blokuj**
   - **Inspekcji**
   - **Wyłączona**
   
6. Wykonaj pozostałe kroki i zapisz zasady. 

7. Na wstążce wybierz pozycję **Wdróż** , aby wdrożyć zasady w kolekcji.


> [!IMPORTANT]
> Po wdrożeniu zasad funkcji Exploit Guard z Configuration Manager ustawienia funkcji Exploit Guard nie zostaną usunięte z klientów po usunięciu wdrożenia. `Delete not supported`jest rejestrowany w Configuration Manager klienta ExploitGuardHandler.log, jeśli usuniesz wdrożenie funkcji Exploit Guard klienta. <!--CMADO8538577-->
> Następujący skrypt programu PowerShell można uruchomić w kontekście SYSTEMU, aby usunąć te ustawienia:<!--CMADO9907132-->
>
> ```powershell
> $defenderObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_Defender02" -Filter "InstanceID='Defender' and ParentID='./Vendor/MSFT/Policy/Config'"
> $defenderObject.AttackSurfaceReductionRules = $null
> $defenderObject.AttackSurfaceReductionOnlyExclusions = $null
> $defenderObject.EnableControlledFolderAccess = $null
> $defenderObject.ControlledFolderAccessAllowedApplications = $null
> $defenderObject.ControlledFolderAccessProtectedFolders = $null
> $defenderObject.EnableNetworkProtection = $null
> $defenderObject.Put()
>
> $exploitGuardObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_ExploitGuard02" -Filter "InstanceID='ExploitGuard' and ParentID='./Vendor/MSFT/Policy/Config'"
> $exploitGuardObject.ExploitProtectionSettings = $null
> $exploitGuardObject.Put()
>```  

## <a name="see-also"></a>Zobacz też

- [Ochrona sieci](network-protection.md)

- [Ochrona sieci i trójstopnie uzgadnianie protokołu TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Oceń ochronę sieci](evaluate-network-protection.md)

- [Rozwiązywanie problemów z ochroną sieci](troubleshoot-np.md)
