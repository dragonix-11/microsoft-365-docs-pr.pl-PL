---
title: Włączanie kontrolowanego dostępu do folderu
keywords: Kontrolowany dostęp do folderów, windows 10, windows 11, windows defender, oprogramowanie wymuszające okup, ochrona, pliki, foldery, włączanie, włączanie, używanie
description: Dowiedz się, jak chronić swoje ważne pliki przez włączenie kontrolowanego dostępu do folderu
ms.prod: m365-security
ms.topic: article
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: b62ff851cbee58cf3b29a2b4dde6fb1b6107dd85
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472820"
---
# <a name="enable-controlled-folder-access"></a>Włączanie kontrolowanego dostępu do folderu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Kontrolowany dostęp do folderu](controlled-folders.md) pomaga chronić cenne dane przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. Kontrolowany dostęp do folderu jest zawarty w Windows 10, Windows 11 i Windows Server 2019. Kontrolowany dostęp do folderu jest również uwzględniony w nowoczesnym, ujednoliconym rozwiązaniu dla Windows [Server 2012R2 i 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

Kontrolowany dostęp do folderu można włączyć przy użyciu dowolnej z tych metod:

- [Zabezpieczenia Windows aplikacja *](#windows-security-app)
- [Microsoft Endpoint Manager](#endpoint-manager)
- [Aplikacje Zarządzanie urządzeniami-komórkowych (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Zasady grupy](#group-policy)
- [PowerShell](#powershell)

[Tryb inspekcji](evaluate-controlled-folder-access.md) pozwala sprawdzić, jak będzie działać ta funkcja (i przeglądać zdarzenia) bez wpływu na normalne korzystanie z urządzenia.

zasady grupy, które wyłączą scalanie listy administratorów lokalnych, zastąpią kontrolowane ustawienia dostępu do folderu. Zastępują one również foldery chronione i dozwolone aplikacje ustawione przez administratora lokalnego za pośrednictwem kontrolowanego dostępu do folderów. Są to między innymi poniższe zasady:

- Program antywirusowy Microsoft Defender **zachowania scalania administratora lokalnego dla list**
- System Center Endpoint Protection **Zezwalaj użytkownikom na dodawanie wykluczeń i zastępować**

Aby uzyskać więcej informacji na temat wyłączania scalania list lokalnych, zobacz Uniemożliwianie użytkownikom i zezwalanie na ich lokalne modyfikowanie ustawień zasad [audio/wideo programu Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>Zabezpieczenia Windows aplikacji

1. Otwórz Zabezpieczenia Windows, wybierając ikonę tarczy na pasku zadań. W menu Start możesz również znaleźć **Zabezpieczenia Windows**.

2. Wybierz **kafelek Ochrona przed & przed zagrożeniami** (lub ikonę tarczy na lewym pasku menu), a następnie wybierz pozycję **Ochrona przed oprogramowaniem wymuszającym okup**.

3. Ustaw przełącznik **kontrolowanego dostępu do folderu** na **Wartość Wł**.

> [!NOTE]
> *Ta metoda nie jest dostępna w Windows Server 2012R2 lub 2016.
> 
> Jeśli kontrolowany dostęp do folderu zostanie skonfigurowany za pomocą poleceń zasady grupy, PowerShell lub MDM, stan w aplikacji Zabezpieczenia Windows zmieni się po ponownym uruchomieniu urządzenia.
> Jeśli dla funkcji ustawiono tryb **inspekcji** dla dowolnego z tych narzędzi, w Zabezpieczenia Windows będzie dla tej aplikacji pokazywany stan **Wyłączone**.
> Jeśli chronisz dane profilu użytkownika, zalecamy, aby profil użytkownika był na domyślnym Windows instalacji.

## <a name="endpoint-manager"></a>Endpoint Manager

1. Zaloguj się do centrum [Endpoint Manager](https://endpoint.microsoft.com) i otwórz **okno Zabezpieczenia punktu końcowego**.

2. Przejdź do **zasad ograniczania powierzchni ataków** \> **.**

3. Wybierz **platformę**, wybierz **pozycję Windows 10 później** i wybierz profil Utwórz reguły zmniejszania **powierzchni ataków** \> **.**

4. Nadaj zasadom nazwę i dodaj opis. Wybierz pozycję **Dalej**.

5. Przewiń w dół, wybierz listę rozwijaną **Włącz ochronę** folderów i wybierz pozycję **Włącz**.

6. Wybierz **pozycję Lista dodatkowych folderów, które muszą być chronione** , i dodaj foldery, które mają być chronione.

7. Wybierz **pozycję Lista aplikacji, które mają dostęp do chronionych folderów,** i dodaj aplikacje, które mają dostęp do folderów chronionych.

8. Wybierz **pozycję Wyklucz pliki i ścieżki z reguł** zmniejszania powierzchni ataków i dodaj pliki i ścieżki, które muszą być wykluczone z reguł ograniczania powierzchni ataków.

9. Wybierz pozycję Zadania **profilu**, przypisz do **wszystkich użytkowników & Wszystkich urządzeniach** i wybierz pozycję **Zapisz**.

10. Wybierz **pozycję Dalej** , aby zapisać każdą otwartą tarczę, a następnie **pozycję Utwórz**.

    > [!NOTE]
    > Symbole wieloznaczne są obsługiwane w aplikacjach, ale nie w przypadku folderów. Podfoldery nie są chronione. Dozwolone aplikacje będą wyzwalać zdarzenia do momentu ich ponownego uruchomienia.

## <a name="mobile-device-management-mdm"></a>Aplikacje Zarządzanie urządzeniami-komórkowych (MDM)

Użyj konfiguracji [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) usługodawca (CSP), aby zezwolić aplikacjom na zmiany w chronionych folderach.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. W Microsoft Endpoint Configuration Manager przejdź do zasobów i **zgodności w** \> **Endpoint Protection** \> **Windows Defender Exploit Guard**.

2. Wybierz **pozycję Zasady Exploit** \> **Guard dla użytkowników domowych.**

3. Wprowadź nazwę i opis, wybierz pozycję **Kontrolowany dostęp do folderu** i wybierz pozycję **Dalej**.

4. Określ, czy chcesz zablokować lub przesieć zmiany, zezwolić na inne aplikacje, czy dodać inne foldery, a następnie wybierz pozycję **Dalej**.

   > [!NOTE]
   > Symbole wieloznaczne są obsługiwane w aplikacjach, ale nie w przypadku folderów. Podfoldery nie są chronione. Dozwolone aplikacje będą wyzwalać zdarzenia do momentu ich ponownego uruchomienia.

5. Przejrzyj ustawienia i wybierz pozycję **Dalej** , aby utworzyć zasady.

6. Po utworzeniu **zasad zamknij.**

## <a name="group-policy"></a>Zasady grupy

1. Na zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](https://technet.microsoft.com/library/cc731212.aspx) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **edytorze zasady grupy zarządzania** przejdź do **strony Konfiguracja komputera i** wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > Windows Defender exploit Guard > kontrolowanego dostępu do folderu**.

4. Kliknij dwukrotnie ustawienie **Konfiguruj kontrolowany dostęp do folderu** i ustaw **opcję Włączone.** W sekcji opcji należy określić jedną z następujących opcji:
   - **Włącz** — złośliwe i podejrzane aplikacje nie będą mogły wprowadzać zmian w plikach w chronionych folderach. Powiadomienie zostanie podane w dzienniku Windows zdarzeń.
   - **Wyłącz (domyślnie)** — funkcja kontrolowanego dostępu do folderu nie będzie działać. Wszystkie aplikacje mogą wprowadzać zmiany w plikach w chronionych folderach.
   - **Tryb inspekcji** — zmiany będą dozwolone, jeśli złośliwa lub podejrzana aplikacja spróbuje wprowadzić zmiany w pliku w chronionym folderze. Jednak będą one rejestrowane w dzienniku Windows, w którym można ocenić wpływ na organizację.
   - **Blokuj tylko modyfikację** dysku — próby zapisu na dysku przez niezaufane aplikacje będą rejestrowane w Windows zdarzeń. Dzienniki te można znaleźć w dziennikach **aplikacji** \> i usług firmy Microsoft \> \> Windows Windows Defender \> identyfikatora \> operacyjnego 1123.
   - **Tylko** modyfikacja dysku inspekcji — w dzienniku zdarzeń programu Windows zostaną zarejestrowane tylko próby zapisu na chronionym dysku ( \>  \> w obszarze Dzienniki aplikacji i usług Microsoft **Windows** \> **Windows Defender** \> **Identyfikator** \> operacyjny **1124**). Próby modyfikowania lub usuwania plików w chronionych folderach nie są rejestrowane.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="Zaznaczona opcja zasad grupy Włączone i Tryb inspekcji" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> Aby w pełni włączyć kontrolowany dostęp do folderu, musisz zasady grupy opcję Włączone i wybrać  pozycję Zablokuj w  menu rozwijaym opcji.

## <a name="powershell"></a>PowerShell

1. Wpisz **tekst powershell** w menu Start kliknij prawym **przyciskiem myszy Windows PowerShell** a następnie wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

Funkcję można włączyć w trybie inspekcji, określając zamiast `AuditMode` `Enabled`.

Umożliwia `Disabled` wyłączenie tej funkcji.

## <a name="see-also"></a>Zobacz też

- [Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów](controlled-folders.md)
- [Dostosowywanie kontrolowanego dostępu do folderu](customize-controlled-folders.md)
- [Ocena ochrony punktu końcowego w usłudze Microsoft Defender](evaluate-mde.md)
