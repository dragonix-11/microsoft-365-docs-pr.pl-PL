---
title: Włączanie ochrony sieci
description: Włącz ochronę sieci za zasady grupy, PowerShell lub Mobile Zarządzanie urządzeniami i Configuration Manager.
keywords: Ochrona sieci, wykorzystywanie, złośliwa witryna internetowa, ip, domena, domeny, włączanie, włączanie
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
ms.openlocfilehash: 4c3b74179294d0b028dd07c3a6f4f28e844237d3
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469938"
---
# <a name="turn-on-network-protection"></a>Włączanie ochrony sieci

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Ochrona sieci](network-protection.md) pomaga zapobiec używaniu przez pracowników dowolnej aplikacji w celu uzyskania dostępu do niebezpiecznych domen, które mogą czynami wyłudzania informacji, oszustwami i złośliwą zawartością w Internecie. Możesz sprawdzić [ochronę sieci w](evaluate-network-protection.md) środowisku testowym, aby przed jej włączeniem sprawdzić, które aplikacje byłyby blokowane.

[Dowiedz się więcej o opcjach konfiguracji filtrowania sieci.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>Sprawdzanie, czy jest włączona ochrona sieci

Za pomocą edytora rejestru sprawdź, czy na urządzeniu lokalnym włączono ochronę sieci.

1. Wybierz przycisk **Start** na pasku zadań i wpisz **polecenie regedit** , aby otworzyć edytor rejestru.

2. Wybierz **HKEY_LOCAL_MACHINE** z menu bocznego.

3. Przejdź przez menu zagnieżdżone do pozycji **Zasady OPROGRAMOWANIA** \>  \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

Jeśli brakuje klucza, przejdź do **części SOFTWARE** \> **Microsoft Windows Defender** \>  \> **Windows Defender Exploit Guard** \> **Network Protection**.

4. Wybierz **pozycję EnableNetworkProtection** , aby wyświetlić bieżący stan ochrony sieci na urządzeniu:

   - 0 lub **Wył.**
   - 1 lub **Wł.**
   - 2 lub **tryb inspekcji**

    :::image type="content" source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" alt-text="Klucz rejestru usługi Network Protection" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::

## <a name="enable-network-protection"></a>Włączanie ochrony sieci

Włącz ochronę sieci, używając dowolnej z tych metod:

- [PowerShell](#powershell)
- [Aplikacje Zarządzanie urządzeniami-komórkowych (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager)
- [Zasady grupy](#group-policy)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. Wpisz **tekst powershell** w menu Start kliknij prawym **przyciskiem myszy Windows PowerShell** a następnie wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. Opcjonalnie: Włącz funkcję w trybie inspekcji przy użyciu następującego polecenia cmdlet:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    Użyj `Disabled` zamiast funkcji `AuditMode` lub `Enabled` do jej wyłączenia.

### <a name="mobile-device-management-mdm"></a>Zarządzanie urządzeniami przenośnymi

Użyj konfiguracji [./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) usługodawca (CSP), aby włączyć lub wyłączyć ochronę sieci albo włączyć tryb inspekcji.

[Zaktualizuj platformę programu Microsoft Defender ochrony przed złośliwym oprogramowaniem](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc) do najnowszej wersji, zanim włączysz lub wyłączysz ochronę sieci lub tryb inspekcji.


### <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

1. Zaloguj się do Microsoft Endpoint Manager administracyjnego (https://endpoint.microsoft.com).

2. Przejdź do **strony** **DevicesConfiguration** >  **profilesTworzenie** >  profilu.

3. W **wysuwanym czacie** Tworzenie profilu wybierz **pozycję Platforma** , a następnie wybierz **typ profilu jako** **szablony**.

4. W **imieniu szablonu** wybierz **pozycję Ochrona punktu końcowego** z listy szablonów, a następnie wybierz pozycję **Utwórz**.

4. Przejdź do **punktu końcowego** >  **ochronyPodstawy**, podaj nazwę profilu, a następnie wybierz pozycję **Dalej**.

5. W sekcji **Ustawienia konfiguracji** przejdź do sekcji **Microsoft Defender Exploit Guard** >  Nawłaściwą >  >  ochronę sieci lub **Inspekcja**. Wybierz pozycję **Dalej**.

6. Wybierz odpowiednie tagi **zakresu**, **przydziały** i reguły **stosowania** wymagane przez Twoją organizację. Administratorzy mogą ustawić więcej wymagań.

7. Przejrzyj wszystkie informacje, a następnie wybierz pozycję **Utwórz**.

### <a name="group-policy"></a>Zasady grupy

Aby włączyć ochronę sieci na komputerach przyłącznych do domeny lub na komputerze autonomicznym, skorzystaj z poniższej procedury.

1. Na komputerze autonomicznym przejdź do menu **Start** , a następnie wpisz i wybierz **pozycję Edytuj zasady grupy**.

    *— Lub —*

    Na przyłączeniu do domeny zasady grupy zarządzania domenami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](https://technet.microsoft.com/library/cc731212.aspx) prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **edytorze zasady grupy zarządzania** przejdź do **strony Konfiguracja komputera i** wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **Windows Defender ochrona sieci Exploit Guard**\>.

   > [!NOTE]
   > W starszych wersjach programu Windows ścieżka zasad grupy może mieć ścieżkę "Program antywirusowy Windows Defender" zamiast "Program antywirusowy Microsoft Defender".

4. Kliknij dwukrotnie ustawienie **Uniemożliwiaj użytkownikom i aplikacjom uzyskiwanie dostępu do niebezpiecznej** witryny sieci Web i ustaw dla tej opcji wartość **Włączone**. W sekcji opcji należy określić jedną z następujących opcji:
    - **Blokowanie** — użytkownicy nie mogą uzyskać dostępu do złośliwych adresów IP i domen.
    - **Wyłącz (domyślne)** — funkcja Ochrona sieci nie będzie działać. Użytkownicy nie będą mieć dostępu do złośliwych domen.
    - **Tryb inspekcji** — jeśli użytkownik odwiedza złośliwy adres IP lub domenę, zdarzenie zostanie zarejestrowane w Windows zdarzeń. Jednak użytkownikowi nie zostanie zablokowana blokada na ten adres.

   > [!IMPORTANT]
   > Aby w pełni włączyć ochronę sieci, należy zasady grupy opcję **Włączone**, a następnie wybrać polecenie Zablokuj w menu  rozwijaym opcji.

Upewnij się, że ochronę sieci włączono na komputerze lokalnym przy użyciu edytora rejestru:

1. Wybierz **przycisk Start** i **wpisz polecenie regedit** , aby **otworzyć Edytor rejestru**.

2. Przejdź do **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Windows Defender Exploit Guard\Network Protection\EnableNetworkProtection**

3. Wybierz **pozycję EnableNetworkProtection** i potwierdź wartość:
   - 0=Wyłączone
   - 1=Wł.
   - 2=Inspekcja

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Otwórz konsolę Configuration Manager.

2. Przejdź do **zasobów i zgodności** >  **Endpoint Protection** >  **Windows Defender Exploit Guard**. 

3. Wybierz **pozycję Utwórz zasady exploit Guard** na wstążce, aby utworzyć nowe zasady.
   - Aby edytować istniejące zasady, wybierz zasady, a następnie wybierz pozycję **Właściwości** na wstążce lub w menu kontekstowym. Edytuj opcję **Konfiguruj ochronę sieci** na **karcie Ochrona** sieci.  

4. Na **stronie Ogólne** określ nazwę nowych zasad i sprawdź, czy **opcja Ochrona** sieci jest włączona. 

5. Na stronie **Ochrona sieci** wybierz jedno z następujących ustawień dla opcji **Konfiguruj ochronę** sieci:
   - **Blokuj**
   - **Inspekcja**
   - **Wyłączone**
   
6. Wykonaj pozostałe kroki i zapisz zasady. 

7. Na wstążce wybierz pozycję **Wdeksuj** , aby wdrożyć zasady w kolekcji.


> [!IMPORTANT]
> Po wdrożeniu zasad exploit Guard z programu Configuration Manager ustawienia exploit Guard nie zostaną usunięte z klientów w przypadku usunięcia wdrożenia. `Delete not supported`jest rejestrowany w pliku Configuration Manager exploitGuardHandler.log klienta po usunięciu wdrożenia exploit Guard tego klienta. <!--CMADO8538577-->
> Aby usunąć te ustawienia, w kontekście systemu można uruchomić następujący skrypt programu PowerShell:<!--CMADO9907132-->
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

- [Ochrona sieci i trójkierunkowy uścisk dłoni protokołu TCP](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Ocenianie ochrony sieci](evaluate-network-protection.md)

- [Rozwiązywanie problemów z ochroną sieci](troubleshoot-np.md)
