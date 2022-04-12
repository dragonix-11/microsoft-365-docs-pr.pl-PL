---
title: Włącz kontrolowany dostępu do folderu
keywords: Kontrolowany dostęp do folderów, Windows 10, Windows 11, Windows Defender, ransomware, ochrona, pliki, foldery, włączanie, włączanie, używanie
description: Dowiedz się, jak chronić ważne pliki, włączając dostęp do kontrolowanych folderów
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
ms.openlocfilehash: 4854ca235790cc8400f3f5a962e4bff203f86f98
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788133"
---
# <a name="enable-controlled-folder-access"></a>Włącz kontrolowany dostępu do folderu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Kontrolowany dostęp do folderów](controlled-folders.md) pomaga chronić cenne dane przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. Kontrolowany dostęp do folderów jest dołączony do Windows 10, Windows 11 i Windows Server 2019. Kontrolowany dostęp do folderów jest również częścią [nowoczesnego, ujednoliconego rozwiązania dla Windows Server 2012R2 i 2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

Kontrolowany dostęp do folderów można włączyć przy użyciu dowolnej z następujących metod:

- [aplikacja Zabezpieczenia Windows *](#windows-security-app)
- [Microsoft Endpoint Manager](#endpoint-manager)
- [Mobile Zarządzanie urządzeniami (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Zasady grupy](#group-policy)
- [PowerShell](#powershell)

[Tryb inspekcji](evaluate-controlled-folder-access.md) umożliwia przetestowanie działania funkcji (i przeglądanie zdarzeń) bez wpływu na normalne korzystanie z urządzenia.

zasady grupy ustawienia, które wyłączają scalanie listy administratorów lokalnych, zastąpią ustawienia dostępu do kontrolowanych folderów. Przesłaniają również chronione foldery i dozwolone aplikacje ustawione przez administratora lokalnego za pośrednictwem kontrolowanego dostępu do folderów. Te zasady obejmują:

- Program antywirusowy Microsoft Defender **Konfigurowanie zachowania scalania administratora lokalnego dla list**
- System Center Endpoint Protection **Zezwalaj użytkownikom na dodawanie wykluczeń i przesłonięcia**

Aby uzyskać więcej informacji na temat wyłączania scalania listy lokalnej, zobacz [Zapobieganie lub zezwalanie użytkownikom na lokalne modyfikowanie ustawień zasad av usługi Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>aplikacja Zabezpieczenia Windows

1. Otwórz aplikację Zabezpieczenia Windows, wybierając ikonę osłony na pasku zadań. Możesz również wyszukać w menu Start **Zabezpieczenia Windows**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusów (lub ikonę osłony na pasku menu po lewej stronie), a następnie wybierz pozycję **Ochrona przed oprogramowaniem wymuszającym okup**.

3. Ustaw przełącznik dla **opcji Kontrolowany dostęp do folderu** **na wartość Włączone**.

> [!NOTE]
> *Ta metoda nie jest dostępna na serwerze Windows Server 2012R2 lub 2016.
> 
> Jeśli kontrolowany dostęp do folderu jest skonfigurowany przy użyciu zasady grupy, programu PowerShell lub dostawców CSP mdm, stan zmieni się w aplikacji Zabezpieczenia Windows po ponownym uruchomieniu urządzenia.
> Jeśli funkcja jest ustawiona na **tryb inspekcji** z dowolnym z tych narzędzi, aplikacja Zabezpieczenia Windows będzie wyświetlać stan **Wyłączone**.
> Jeśli chronisz dane profilu użytkownika, zalecamy, aby profil użytkownika był na domyślnym dysku instalacyjnym Windows.

## <a name="endpoint-manager"></a>Endpoint Manager

1. Zaloguj się do [Endpoint Manager](https://endpoint.microsoft.com) i otwórz **program Endpoint Security**.

2. Przejdź do **obszaru Zasady** zmniejszania \> **obszaru ataków**.

3. Wybierz **pozycję Platforma**, wybierz **pozycję Windows 10 i nowsze**, a następnie wybierz profil **Utwórz reguły** \> zmniejszania obszaru podatnego na ataki.

4. Nadaj zasadom nazwę i dodaj opis. Wybierz pozycję **Dalej**.

5. Przewiń w dół do dołu, wybierz listę rozwijaną **Włącz ochronę folderów** , a następnie wybierz pozycję **Włącz**.

6. Wybierz **pozycję Lista dodatkowych folderów, które mają być chronione** , i dodaj foldery, które muszą być chronione.

7. Wybierz **pozycję Lista aplikacji, które mają dostęp do folderów chronionych** , i dodaj aplikacje, które mają dostęp do folderów chronionych.

8. Wybierz pozycję **Wyklucz pliki i ścieżki z reguł zmniejszania obszaru ataków** i dodaj pliki i ścieżki, które należy wykluczyć z reguł zmniejszania obszaru ataków.

9. Wybierz pozycję **Przypisania** profilu, przypisz do pozycji **Wszyscy użytkownicy & Wszystkie urządzenia**, a następnie wybierz pozycję **Zapisz**.

10. Wybierz pozycję **Dalej** , aby zapisać każdy otwarty blok, a następnie **pozycję Utwórz**.

    > [!NOTE]
    > Symbole wieloznaczne są obsługiwane w przypadku aplikacji, ale nie dla folderów. Podfoldery nie są chronione. Dozwolone aplikacje będą nadal wyzwalać zdarzenia do momentu ich ponownego uruchomienia.

## <a name="mobile-device-management-mdm"></a>Mobile Zarządzanie urządzeniami (MDM)

Użyj [dostawcy ./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) configuration service provider (CSP), aby umożliwić aplikacjom wprowadzanie zmian w chronionych folderach.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. W Microsoft Endpoint Configuration Manager przejdź do obszaru **Zasoby i zgodność** \> **Endpoint Protection** \> **Windows Defender Exploit Guard**.

2. Wybierz pozycję **Strona główna** \> **Utwórz zasady funkcji Exploit Guard**.

3. Wprowadź nazwę i opis, wybierz pozycję **Kontrolowany dostęp do folderu**, a następnie wybierz pozycję **Dalej**.

4. Wybierz opcję blokuj lub przeprowadź inspekcję zmian, zezwalaj na inne aplikacje lub dodaj inne foldery, a następnie wybierz pozycję **Dalej**.

   > [!NOTE]
   > Symbol wieloznaczny jest obsługiwany w przypadku aplikacji, ale nie dla folderów. Podfoldery nie są chronione. Dozwolone aplikacje będą nadal wyzwalać zdarzenia do momentu ich ponownego uruchomienia.

5. Przejrzyj ustawienia i wybierz pozycję **Dalej** , aby utworzyć zasady.

6. Po utworzeniu zasad **zamknij**.

## <a name="group-policy"></a>Zasady grupy

1. Na urządzeniu do zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](https://technet.microsoft.com/library/cc731212.aspx), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > Windows Defender funkcji Exploit Guard > kontrolowany dostęp do folderu**.

4. Kliknij dwukrotnie ustawienie **Skonfiguruj dostęp do folderu kontrolowanego** i ustaw opcję **Włączone**. W sekcji opcje należy określić jedną z następujących opcji:
   - **Włącz** — złośliwe i podejrzane aplikacje nie będą mogły wprowadzać zmian w plikach w folderach chronionych. W dzienniku zdarzeń Windows zostanie wyświetlone powiadomienie.
   - **Wyłącz (ustawienie domyślne)** — funkcja kontrolowanego dostępu do folderu nie będzie działać. Wszystkie aplikacje mogą wprowadzać zmiany w plikach w folderach chronionych.
   - **Tryb inspekcji** — zmiany będą dozwolone, jeśli złośliwa lub podejrzana aplikacja spróbuje wprowadzić zmianę w pliku w folderze chronionym. Zostanie on jednak zapisany w dzienniku zdarzeń Windows, w którym można ocenić wpływ na organizację.
   - **Blokuj tylko modyfikowanie dysku** — próby zapisu w sektorach dysków przez niezaufane aplikacje będą rejestrowane w dzienniku zdarzeń Windows. Te dzienniki można znaleźć w dziennikach \> **aplikacji i usług** microsoft \> Windows \> Windows Defender \> identyfikator operacyjny \> 1123.
   - **Tylko inspekcja modyfikacji dysku** — tylko próby zapisu w chronionych sektorach dysków będą rejestrowane w dzienniku zdarzeń Windows (w obszarze **Dzienniki** \> aplikacji i usług **microsoft** \> **Windows Windows Defender** \>  \> identyfikator **operacyjny** \> **1124**). Próby modyfikowania lub usuwania plików w folderach chronionych nie będą rejestrowane.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="Wybrano opcję zasad grupy Włączone i Tryb inspekcji" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> Aby w pełni włączyć kontrolowany dostęp do folderów, należy ustawić opcję zasady grupy **na Włączone** i wybrać pozycję **Blokuj** w menu rozwijanym opcje.

## <a name="powershell"></a>PowerShell

1. Wpisz **program PowerShell** w menu Start, kliknij prawym przyciskiem myszy **Windows PowerShell** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

Funkcję można włączyć w trybie inspekcji`Enabled`, określając `AuditMode` zamiast .

Użyj polecenia `Disabled` , aby wyłączyć funkcję.

## <a name="see-also"></a>Zobacz też

- [Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów](controlled-folders.md)
- [Dostosuj kontrolowany dostęp do folderu](customize-controlled-folders.md)
- [Ocena ochrony punktu końcowego w usłudze Microsoft Defender](evaluate-mde.md)
