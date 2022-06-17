---
title: Dostosuj kontrolowany dostęp do folderu
description: Dodaj inne foldery, które powinny być chronione przez kontrolowany dostęp do folderów lub zezwalaj aplikacjom, które niepoprawnie blokują zmiany w ważnych plikach.
keywords: Kontrolowany dostęp do folderów, Windows 10, Windows 11, Windows Defender, ransomware, ochrona, pliki, foldery, dostosowywanie, dodawanie folderu, dodawanie aplikacji, zezwalanie, dodawanie pliku wykonywalnego
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde, dbodorin, vladiso, nixanm, anvascon
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.date: ''
ms.openlocfilehash: 3d6f763bd2ac2c4352f1b200c05c3079bc615aaf
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139346"
---
# <a name="customize-controlled-folder-access"></a>Dostosuj kontrolowany dostęp do folderu

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> [!TIP]
> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kontrolowany dostęp do folderów pomaga chronić cenne dane przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. Kontrolowany dostęp do folderów jest obsługiwany na klientach Windows Server 2019, Windows Server 2022, Windows 10 i Windows 11. W tym artykule opisano sposób dostosowywania możliwości kontrolowanego dostępu do folderów i przedstawiono następujące sekcje:

- [Ochrona dodatkowych folderów](#protect-additional-folders)
- [Dodawanie aplikacji, które powinny mieć dostęp do chronionych folderów](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [Zezwalaj podpisanym plikom wykonywalnym na dostęp do folderów chronionych](#allow-signed-executable-files-to-access-protected-folders)
- [Dostosuj powiadomienie](#customize-the-notification)

> [!IMPORTANT]
> Kontrolowany dostęp do folderów monitoruje aplikacje pod kątem działań wykrytych jako złośliwe. Czasami legalne aplikacje nie mogą wprowadzać zmian w plikach. Jeśli kontrolowany dostęp do folderów wpływa na wydajność organizacji, możesz rozważyć uruchomienie tej funkcji w [trybie inspekcji](audit-windows-defender.md) , aby w pełni ocenić wpływ.

## <a name="protect-additional-folders"></a>Ochrona dodatkowych folderów

Kontrolowany dostęp do folderów ma zastosowanie do wielu folderów systemowych i lokalizacji domyślnych, w tym folderów, takich jak **Dokumenty**, **Obrazy** i **Filmy**. Możesz dodać inne foldery do ochrony, ale nie możesz usunąć folderów domyślnych na liście domyślnej.

Dodawanie innych folderów do kontrolowanego dostępu do folderów może być przydatne w przypadkach, gdy pliki nie są przechowywane w domyślnych bibliotekach Windows lub zmieniono domyślną lokalizację bibliotek.

Można również określić udziały sieciowe i zamapowane dyski. Obsługiwane są zmienne środowiskowe i symbole wieloznaczne. Aby uzyskać informacje na temat używania symboli wieloznacznych, zobacz [Używanie symboli wieloznacznych na liście wykluczeń nazwy pliku i folderu lub rozszerzenia](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Do dodawania i usuwania chronionych folderów można użyć aplikacji Zabezpieczenia Windows, zasady grupy, poleceń cmdlet programu PowerShell lub dostawców usług konfiguracji zarządzania urządzeniami przenośnymi.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Ochrona dodatkowych folderów przy użyciu aplikacji Zabezpieczenia Windows

1. Otwórz aplikację Zabezpieczenia Windows, wybierając ikonę osłony na pasku zadań lub wyszukując *zabezpieczenia* w menu Start.

2. Wybierz pozycję **Ochrona przed zagrożeniami & wirusami**, a następnie przewiń w dół do sekcji **Ochrona przed oprogramowaniem wymuszającym okup** .

3. Wybierz pozycję **Zarządzaj ochroną przed oprogramowaniem wymuszającym okup** , aby otworzyć okienko **Ochrona przed oprogramowaniem wymuszającym okup** .

4. W sekcji **Kontrolowany dostęp do folderów** wybierz pozycję **Foldery chronione**.

5. Wybierz pozycję **Tak** w wierszu Access Control **użytkownika**. Zostanie **wyświetlone okienko Chronione foldery** .

6. Wybierz **pozycję Dodaj folder chroniony** i postępuj zgodnie z monitami, aby dodać foldery.

### <a name="use-group-policy-to-protect-additional-folders"></a>Ochrona dodatkowych folderów przy użyciu zasady grupy

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Zasady** \> **konfiguracji** \> komputera **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> Windows Defender **dostęp do folderu z kontrolą** **funkcji Exploit Guard**\>. <br/>**UWAGA**: W starszych wersjach Windows mogą być widoczne **Program antywirusowy Windows Defender** zamiast **Program antywirusowy Microsoft Defender**.

5. Kliknij dwukrotnie **pozycję Skonfigurowano foldery chronione**, a następnie ustaw opcję **Włączone**. Wybierz pozycję **Pokaż** i określ każdy folder, który chcesz chronić.

6. Wdróż obiekt zasady grupy tak jak zwykle.

### <a name="use-powershell-to-protect-additional-folders"></a>Ochrona dodatkowych folderów przy użyciu programu PowerShell

1. Wpisz **program PowerShell** w menu Start, kliknij prawym przyciskiem myszy **Windows PowerShell** i wybierz pozycję **Uruchom jako administrator**

2. Wpisz następujące polecenie cmdlet programu PowerShell, zastępując `<the folder to be protected>` ciąg ścieżką folderu (np `"c:\apps\"`. ):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Powtórz krok 2 dla każdego folderu, który chcesz chronić. Foldery, które są chronione, są widoczne w aplikacji Zabezpieczenia Windows.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="Okno programu PowerShell z wyświetlonym poleceniem cmdlet" lightbox="images/cfa-allow-folder-ps.png":::

> [!IMPORTANT]
> Użyj polecenia `Add-MpPreference` , aby dołączyć lub dodać aplikacje do listy, a nie `Set-MpPreference`. `Set-MpPreference` Użycie polecenia cmdlet spowoduje zastąpienie istniejącej listy.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Ochrona dodatkowych folderów przy użyciu dostawców CSP mdm

Użyj [dostawcy ./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) configuration service provider (CSP), aby zezwolić aplikacjom na wprowadzanie zmian w chronionych folderach.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Zezwalaj określonym aplikacjom na wprowadzanie zmian w kontrolowanych folderach

Możesz określić, czy niektóre aplikacje są zawsze uważane za bezpieczne i przyznać dostęp do zapisu do plików w folderach chronionych. Zezwalanie na aplikacje może być przydatne, jeśli określona aplikacja, którą znasz i której ufasz, jest blokowana przez funkcję kontrolowanego dostępu do folderu.

> [!IMPORTANT]
> Domyślnie Windows dodaje aplikacje, które są uważane za przyjazne dla listy dozwolonych. Takie aplikacje, które są dodawane automatycznie, nie są rejestrowane na liście wyświetlanej w aplikacji Zabezpieczenia Windows ani przy użyciu skojarzonych poleceń cmdlet programu PowerShell. Nie należy dodawać większości aplikacji. Dodaj aplikacje tylko wtedy, gdy są one blokowane i możesz sprawdzić ich wiarygodność.

Po dodaniu aplikacji musisz określić lokalizację aplikacji. Tylko aplikacja w tej lokalizacji będzie mieć dostęp do chronionych folderów. Jeśli aplikacja (o tej samej nazwie) znajduje się w innej lokalizacji, nie zostanie dodana do listy dozwolonych i może zostać zablokowana przez kontrolowany dostęp do folderu.

Dozwolona aplikacja lub usługa ma dostęp do zapisu do kontrolowanego folderu tylko po jego uruchomieniu. Na przykład usługa aktualizacji będzie nadal wyzwalać zdarzenia po jej zezwoleniu, dopóki nie zostanie zatrzymana i ponownie uruchomiona.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Zezwalanie na określone aplikacje przy użyciu aplikacji Windows Defender Security

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując menu Start dla pozycji **Zabezpieczenia**.

2. Wybierz kafelek **Ochrona przed zagrożeniami & wirusów** (lub ikonę osłony na pasku menu po lewej stronie), a następnie wybierz pozycję **Zarządzaj ochroną przed oprogramowaniem wymuszającym okup**.

3. W sekcji **Kontrolowany dostęp do folderu** wybierz pozycję **Zezwalaj aplikacji za pośrednictwem kontrolowanego dostępu do folderu**

4. Wybierz **pozycję Dodaj dozwoloną aplikację** i postępuj zgodnie z monitami, aby dodać aplikacje.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="Przycisk Dodaj dozwoloną aplikację" lightbox="images/cfa-allow-app.png":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Zezwalanie na określone aplikacje przy użyciu zasady grupy

1. Na urządzeniu do zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> Windows Defender **dostęp do folderu z kontrolą** **funkcji Exploit Guard**\>.

4. Kliknij dwukrotnie ustawienie **Skonfiguruj dozwolone aplikacje** i ustaw opcję **Włączone**. Wybierz pozycję **Pokaż** i wprowadź każdą aplikację.

### <a name="use-powershell-to-allow-specific-apps"></a>Zezwalanie na określone aplikacje przy użyciu programu PowerShell

1. Wpisz **program PowerShell** w menu Start, kliknij prawym przyciskiem myszy **Windows PowerShell** i wybierz pozycję **Uruchom jako administrator**
2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Aby na przykład dodać *test.exe* wykonywalny znajdujący się w folderze *C:\apps*, polecenie cmdlet będzie wyglądać następująco:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Nadal używaj polecenia `Add-MpPreference -ControlledFolderAccessAllowedApplications` , aby dodać więcej aplikacji do listy. Aplikacje dodane przy użyciu tego polecenia cmdlet będą wyświetlane w aplikacji Zabezpieczenia Windows.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="Polecenie cmdlet programu PowerShell umożliwiające korzystanie z aplikacji" lightbox="images/cfa-allow-app-ps.png":::

> [!IMPORTANT]
> Służy `Add-MpPreference` do dołączania lub dodawania aplikacji do listy. `Set-MpPreference` Użycie polecenia cmdlet spowoduje zastąpienie istniejącej listy.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Zezwalanie na określone aplikacje przy użyciu dostawców CSP mdm

Użyj [programu ./Vendor/MSFT/Policy/Config/Defender/ControlledFolderAccessAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) configuration service provider (CSP), aby umożliwić aplikacjom wprowadzanie zmian w chronionych folderach.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>Zezwalaj podpisanym plikom wykonywalnym na dostęp do folderów chronionych

Ochrona punktu końcowego w usłudze Microsoft Defender wskaźniki certyfikatów i plików mogą zezwalać podpisanym plikom wykonywalnym na dostęp do chronionych folderów. Aby uzyskać szczegółowe informacje o implementacji, zobacz [Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md).

> [!Note]
> Nie dotyczy to aparatów skryptów, w tym programu PowerShell

## <a name="customize-the-notification"></a>Dostosuj powiadomienie

Aby uzyskać więcej informacji na temat dostosowywania powiadomienia po wyzwoleniu reguły i zablokowaniu aplikacji lub pliku, zobacz [Konfigurowanie powiadomień o alertach w Ochrona punktu końcowego w usłudze Microsoft Defender](configure-email-notifications.md).

## <a name="see-also"></a>Zobacz też

- [Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów](controlled-folders.md)
- [Włącz kontrolowany dostępu do folderu](enable-controlled-folders.md)
- [Włączanie reguł zmniejszania obszaru ataków](enable-attack-surface-reduction.md)
