---
title: Dostosowywanie kontrolowanego dostępu do folderu
description: Dodaj inne foldery, które powinny być chronione przez kontrolowany dostęp do folderów, lub zezwalaj aplikacjom, które nieprawidłowo blokują zmiany w ważnych plikach.
keywords: Kontrolowany dostęp do folderu, windows 10, windows 11, windows defender, oprogramowanie wymuszające okup, ochrona, pliki, foldery, dostosowywanie, dodawanie folderu, dodawanie aplikacji, zezwalanie, dodawanie pliku wykonywalnego
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
ms.openlocfilehash: b9af738d4b1f59705132a84239d06dc762447417
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683762"
---
# <a name="customize-controlled-folder-access"></a>Dostosowywanie kontrolowanego dostępu do folderu

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Kontrolowany dostęp do folderu pomaga chronić cenne dane przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. Kontrolowany dostęp do folderu jest obsługiwany na Windows Server 2019, Windows Server 2022, Windows 10 i Windows 11 klientów. W tym artykule opisano sposób dostosowywania funkcji kontrolowanego dostępu do folderu i przedstawiono następujące sekcje:

- [Ochrona dodatkowych folderów](#protect-additional-folders)
- [Dodawanie aplikacji, które powinny mieć dostęp do folderów chronionych](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [Zezwalanie podpisanym plikom wykonywalnym na uzyskiwanie dostępu do folderów chronionych](#allow-signed-executable-files-to-access-protected-folders)
- [Dostosowywanie powiadomienia](#customize-the-notification)

> [!IMPORTANT]
> Kontrolowany dostęp do folderu monitoruje aplikacje pod celu wykrycia działań, które są wykrywane jako złośliwe. Czasami prawowite aplikacje mają zablokowaną opcję dokonywania zmian w plikach. Jeśli kontrolowany dostęp do folderów wpływa na wydajność organizacji, możesz rozważyć uruchomienie tej funkcji w trybie inspekcji [, aby w](audit-windows-defender.md) pełni ocenić ten wpływ.

## <a name="protect-additional-folders"></a>Ochrona dodatkowych folderów

Kontrolowany dostęp do folderów dotyczy wielu folderów systemowych i lokalizacji domyślnych, w tym folderów, takich jak **Dokumenty**, **Obrazy** i **Filmy**. Możesz dodać inne foldery, które mają być chronione, ale nie możesz usunąć folderów domyślnych z listy domyślnej.

Dodawanie innych folderów do kontrolowanego dostępu do folderów może być pomocne w przypadkach, gdy nie przechowujesz plików w domyślnych Windows bibliotek lub zmieniono domyślną lokalizację bibliotek.

Można także określić udziały sieciowe i zamapowane dyski. Zmienne środowiskowe i symbole wieloznaczne są obsługiwane. Aby uzyskać informacje dotyczące używania symboli wieloznacznych, zobacz Używanie symboli wieloznacznych w nazwach plików [i ścieżkach folderów lub na listach wykluczeń rozszerzenia](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Aby dodać i usunąć chronione foldery, Zabezpieczenia Windows użyć aplikacji programu zasady grupy, poleceń cmdlet programu PowerShell lub dostawców usług konfiguracji zarządzania urządzeniami przenośnymi.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Ochrona dodatkowych folderów za pomocą Zabezpieczenia Windows folderów

1. Otwórz aplikację Zabezpieczenia Windows, wybierając ikonę tarczy na pasku zadań lub wyszukując *zabezpieczenia* w menu Start.

2. Wybierz **pozycję ochrona & przed zagrożeniami**, a następnie przewiń w dół do sekcji **Ochrona oprogramowania wymuszającego okup** .

3. Wybierz **pozycję Zarządzaj ochroną oprogramowania wymuszającego okup** , aby otworzyć **okienko Ochrona oprogramowania wymuszającego okup** .

4. W sekcji **Kontrolowany dostęp do folderu** wybierz pozycję **Foldery chronione**.

5. Wybierz **pozycję Tak** w **wierszu polecenia Kontrola dostępu użytkownika** . Zostanie **wyświetlone okienko Foldery** chronione.

6. Wybierz **pozycję Dodaj chroniony folder i** postępuj zgodnie z monitami, aby dodać foldery.

### <a name="use-group-policy-to-protect-additional-folders"></a>Ochrona zasady grupy folderów za pomocą funkcji folderów

1. Na komputerze zasady grupy zarządzania otwórz [konsolę zasady grupy zarządzania danymi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **Edytorze zasady grupy zarządzaniem** przejdź do **strony Szablony** **administracyjne Zasady konfiguracji** \> \> **komputera**.

4. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> Windows Defender dostęp do folderów z **kontrolą** **exploit guard**\>. <br/>**UWAGA**: W starszych wersjach programu Windows może być **Program antywirusowy Windows Defender zamiast** **Program antywirusowy Microsoft Defender**.

5. Kliknij dwukrotnie **pozycję Skonfigurowane foldery chronione**, a następnie ustaw **opcję Włączone.** Wybierz **pozycję** Pokaż i określ foldery, które chcesz chronić.

6. Wdeksuj obiekt zasady grupy tak jak zwykle.

### <a name="use-powershell-to-protect-additional-folders"></a>Ochrona dodatkowych folderów za pomocą programu PowerShell

1. Wpisz **program PowerShell** w menu Start kliknij prawym **przyciskiem myszy Windows PowerShell** a następnie wybierz pozycję **Uruchom jako administrator**

2. Wpisz następujące polecenie cmdlet programu PowerShell, zastępując `<the folder to be protected>` ścieżką folderu (na przykład `"c:\apps\"`):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Powtórz krok 2 dla każdego folderu, który chcesz chronić. Chronione foldery są widoczne w Zabezpieczenia Windows aplikacji.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="Okno programu PowerShell z pokazanym poleceniem cmdlet.":::

> [!IMPORTANT]
> Użyj, `Add-MpPreference` aby dołączyć aplikacje do listy lub dodać je do listy, a nie .`Set-MpPreference` Użycie polecenia `Set-MpPreference` cmdlet spowoduje zastąpienie istniejącej listy.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Ochrona dodatkowych folderów za pomocą csP usługi MDM

Użyj pliku [konfiguracji ./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) usługodawca (CSP), aby zezwolić aplikacjom na zmiany w chronionych folderach.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Zezwalanie określonym aplikacjom na zmiany w folderach kontrolowanych

Możesz określić, czy określone aplikacje są zawsze traktowane jako bezpieczne, i udzielić dostępu do zapisu plików w chronionych folderach. Zezwolenie na aplikacje może być przydatne, jeśli określonej aplikacji, o której wiesz i której ufasz, jest blokowana przez funkcję kontrolowanego dostępu do folderu.

> [!IMPORTANT]
> Domyślnie program Windows aplikacje uznane za przyjazne dla listy dozwolonych. Takie aplikacje, które są dodawane automatycznie, nie są zapisywane na liście wyświetlanej w aplikacji Zabezpieczenia Windows ani przy użyciu skojarzonych poleceń cmdlet programu PowerShell. Nie musisz dodawać większości aplikacji. Dodawanie aplikacji jest możliwe tylko wtedy, gdy są blokowane i można zweryfikować ich wiarygodności.

Podczas dodawania aplikacji musisz określić jej lokalizację. Tylko aplikacja w tej lokalizacji będzie mieć dozwolony dostęp do chronionych folderów. Jeśli aplikacja (o tej samej nazwie) znajduje się w innej lokalizacji, nie zostanie dodana do listy zezwalań i może zostać zablokowana przez kontrolowany dostęp do folderu.

Dozwolona aplikacja lub usługa ma dostęp do zapisu w folderze kontrolowanym tylko po jego uruchamianiu. Na przykład usługa aktualizacji będzie nadal wyzwalać zdarzenia po jej zatrzymaniu i ponownym uruchomieniu.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Zezwalaj na Windows Defender za pomocą aplikacji zabezpieczenia sieci Web

1. Otwórz aplikację Zabezpieczenia Windows, wyszukując w menu Start pozycję **Zabezpieczenia**.

2. Wybierz **kafelek Ochrona przed & przed zagrożeniami** (lub ikonę tarczy na lewym pasku menu), a następnie wybierz pozycję **Zarządzaj ochroną oprogramowania wymuszającego okup**.

3. W sekcji **Kontrolowany dostęp do folderu** wybierz opcję **Zezwalaj aplikacji za pośrednictwem kontrolowanego dostępu do folderu**

4. Wybierz **pozycję Dodaj dozwoloną aplikację i** postępuj zgodnie z monitami, aby dodać aplikacje.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="Dodaj dozwolony przycisk aplikacji.":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Zezwalaj zasady grupy aplikacji za pomocą aplikacji

1. Na zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **edytorze zasady grupy zarządzaniem** przejdź do **strony Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> Windows Defender dostęp do folderów z **kontrolą** **exploit guard**\>.

4. Kliknij dwukrotnie ustawienie **Konfiguruj dozwolone aplikacje** i ustaw dla opcji wartość **Włączone**. Wybierz **pozycję Pokaż** i wprowadź poszczególne aplikacje.

### <a name="use-powershell-to-allow-specific-apps"></a>Zezwalanie na określone aplikacje przy użyciu programu PowerShell

1. Wpisz **program PowerShell** w menu Start kliknij prawym **przyciskiem myszy Windows PowerShell** a następnie wybierz pozycję **Uruchom jako administrator**
2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Aby na przykład dodać plik wykonywalny *test.exe* się w folderze *C:\apps*, polecenie cmdlet może być następujące:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Nadal używaj dodawania `Add-MpPreference -ControlledFolderAccessAllowedApplications` kolejnych aplikacji do listy. Aplikacje dodane przy użyciu tego polecenia cmdlet będą widoczne w Zabezpieczenia Windows aplikacji.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="Polecenie cmdlet programu PowerShell umożliwiające aplikację.":::

> [!IMPORTANT]
> Użyj, `Add-MpPreference` aby dołączyć aplikacje do listy lub dodać je do listy. Użycie polecenia `Set-MpPreference` cmdlet spowoduje zastąpienie istniejącej listy.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Zezwalanie na określone aplikacje za pomocą SPP mdM

Użyj pliku [konfiguracji ./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) usługodawca (CSP), aby zezwolić aplikacjom na zmiany w chronionych folderach.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>Zezwalanie podpisanym plikom wykonywalnym na uzyskiwanie dostępu do folderów chronionych

Program Microsoft Defender for Endpoint certificate and file indicators can allow signed wykonywaable files to access protected folders. Aby uzyskać szczegóły implementacji, [zobacz Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md).

> [!Note]
> Nie dotyczy to aparatów skryptów, w tym programu PowerShell.

## <a name="customize-the-notification"></a>Dostosowywanie powiadomienia

Aby uzyskać więcej informacji na temat dostosowywania powiadomienia o wyzwoleniu reguły i blokowania aplikacji lub pliku, zobacz Konfigurowanie powiadomień [alertów w programie Microsoft Defender dla punktu końcowego](configure-email-notifications.md).

## <a name="see-also"></a>Zobacz też

- [Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów](controlled-folders.md)
- [Włączanie kontrolowanego dostępu do folderu](enable-controlled-folders.md)
- [Ocenianie reguł zmniejszania powierzchni ataków](evaluate-attack-surface-reduction.md)
