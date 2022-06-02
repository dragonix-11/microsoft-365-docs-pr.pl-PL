---
title: Ochrona ważnych folderów przed oprogramowaniem wymuszającym okup przed szyfrowaniem plików przy użyciu kontrolowanego dostępu do folderów
description: Pliki w folderach domyślnych mogą być chronione przed zmianą przez złośliwe aplikacje. Zapobiegaj szyfrowaniu plików przez oprogramowanie wymuszające okup.
keywords: kontrolowany dostęp do folderów, windows 10, windows defender, ransomware, ochrona, pliki, foldery
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
audience: ITPro
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 02017a614544cfb10eb43d375212fc7e37124ad3
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840392"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Dotyczy**
- System Windows


> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>Co to jest kontrolowany dostęp do folderu?

Kontrolowany dostęp do folderów pomaga chronić cenne dane przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. Kontrolowany dostęp do folderów chroni dane, sprawdzając aplikacje pod kątem listy znanych, zaufanych aplikacji. Obsługiwane na Windows Server 2019, Windows Server 2022, Windows 10 i Windows 11 klientów, kontrolowany dostęp do folderów można włączyć przy użyciu aplikacji Zabezpieczenia Windows, Microsoft Endpoint Configuration Manager lub Intune (dla urządzeń zarządzanych).

> [!NOTE]
> Aparaty skryptów nie są zaufane i nie można zezwolić im na dostęp do kontrolowanych chronionych folderów. Na przykład program PowerShell nie jest zaufany przez kontrolowany dostęp do folderów, nawet jeśli zezwalasz na [użycie wskaźników certyfikatu i pliku](/microsoft-365/security/defender-endpoint/indicator-certificates).

Kontrolowany dostęp do folderów działa najlepiej w przypadku [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md), co zapewnia szczegółowe raportowanie zdarzeń i bloków dostępu do kontrolowanych folderów w ramach [typowych scenariuszy badania alertów](investigate-alerts.md).

> [!TIP]
> Kontrolowane bloki dostępu do folderów nie generują alertów w [kolejce alertów](alerts-queue.md). Można jednak wyświetlać informacje o kontrolowanych blokach dostępu do folderów w [widoku osi czasu urządzenia](investigate-machines.md), podczas korzystania z [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md) lub z [niestandardowymi regułami wykrywania](custom-detection-rules.md).

## <a name="how-does-controlled-folder-access-work"></a>Jak działa kontrolowany dostęp do folderów?

Kontrolowany dostęp do folderów działa tylko przez zezwolenie zaufanym aplikacjom na dostęp do chronionych folderów. Chronione foldery są określane podczas konfigurowania kontrolowanego dostępu do folderów. Zazwyczaj na liście kontrolowanych folderów znajdują się często używane foldery, takie jak foldery używane w dokumentach, obrazach, plikach do pobrania itd.

Kontrolowany dostęp do folderów działa z listą zaufanych aplikacji. Aplikacje znajdujące się na liście zaufanego oprogramowania działają zgodnie z oczekiwaniami. Aplikacje, które nie znajdują się na liście, nie mogą wprowadzać żadnych zmian w plikach w chronionych folderach.

Aplikacje są dodawane do listy na podstawie ich powszechności i reputacji. Aplikacje, które są wysoce rozpowszechnione w całej organizacji i które nigdy nie wyświetlały żadnego zachowania uznanego za złośliwe, są uważane za godne zaufania. Te aplikacje są automatycznie dodawane do listy.

Aplikacje można również dodać ręcznie do listy zaufanej przy użyciu Configuration Manager lub Intune. Dodatkowe akcje można wykonać z poziomu portalu Microsoft 365 Defender.

## <a name="why-controlled-folder-access-is-important"></a>Dlaczego kontrolowany dostęp do folderów jest ważny

Kontrolowany dostęp do folderów jest szczególnie przydatny w ochronie dokumentów i informacji przed [oprogramowaniem wymuszającym okup](https://www.microsoft.com/wdsi/threats/ransomware). W przypadku ataku wymuszającego okup pliki mogą stać się szyfrowane i przetrzymywane jako zakładniki. Po kontrolowanym dostępie do folderu na komputerze, na którym aplikacja próbowała wprowadzić zmiany w pliku w folderze chronionym, zostanie wyświetlone powiadomienie. Powiadomienie można [dostosować przy](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) użyciu danych firmy i informacji kontaktowych. Można również włączyć reguły indywidualnie, aby dostosować techniki monitorów funkcji.

[Foldery chronione](#review-controlled-folder-access-events-in-windows-event-viewer) obejmują typowe foldery systemowe (w tym sektory rozruchu) i można [dodać więcej folderów](customize-controlled-folders.md#protect-additional-folders). Możesz również [zezwolić aplikacjom na udzielanie](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) im dostępu do chronionych folderów.

Tryb [inspekcji](audit-windows-defender.md) umożliwia ocenę wpływu kontrolowanego dostępu do folderów na organizację, jeśli zostałaby włączona. Możesz również odwiedzić witrynę internetową Windows Defender Test ground pod adresem [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby potwierdzić, że funkcja działa i zobaczyć, jak działa.

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

Kontrolowany dostęp do folderów jest obsługiwany w następujących wersjach Windows:

- [Windows 10, wersja 1709](/windows/whats-new/whats-new-windows-10-version-1709) i nowsze
- Windows 11
- Windows 2012 R2
- Windows 2016 r.
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows foldery systemowe są domyślnie chronione

Windows foldery systemowe są domyślnie chronione wraz z kilkoma innymi folderami:

Foldery chronione obejmują typowe foldery systemowe (w tym sektory rozruchu) i można dodawać dodatkowe foldery. Możesz również zezwolić aplikacjom na udzielanie im dostępu do chronionych folderów.  Foldery systemów Windows, które są domyślnie chronione, to:

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

Foldery domyślne są wyświetlane w profilu użytkownika w obszarze **Ten komputer**.
   > [!div class="mx-imgBorder"]
   > ![Domyślne foldery systemów chronionych Windows](images/defaultfolders.png)

> [!NOTE]
> Można skonfigurować dodatkowe foldery jako chronione, ale nie można usunąć Windows folderów systemowych, które są domyślnie chronione.

## <a name="requirements-for-controlled-folder-access"></a>Wymagania dotyczące kontrolowanego dostępu do folderów

Kontrolowany dostęp do folderów wymaga włączenia [Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md).

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>Przejrzyj zdarzenia dostępu do folderów kontrolowanych w portalu Microsoft 365 Defender

Usługa Defender for Endpoint udostępnia szczegółowe raporty dotyczące zdarzeń i bloków w ramach [scenariuszy badania alertów](investigate-alerts.md) w portalu Microsoft 365 Defender; zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender in Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

Możesz wykonywać zapytania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender danych przy użyciu [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md). Jeśli używasz [trybu inspekcji](audit-windows-defender.md), możesz użyć [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md) , aby zobaczyć, jak kontrolowane ustawienia dostępu do folderów wpłyną na środowisko, jeśli zostały włączone.

Przykładowe zapytanie:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Przejrzyj zdarzenia dostępu do folderów kontrolowanych w Windows Podgląd zdarzeń

Możesz przejrzeć dziennik zdarzeń Windows, aby wyświetlić zdarzenia utworzone podczas kontrolowanych bloków dostępu do folderów (lub inspekcji) aplikacji:

1. Pobierz [pakiet ewaluacyjny](https://aka.ms/mp7z2w) i wyodrębnij plik *cfa-events.xml* do łatwo dostępnej lokalizacji na urządzeniu.
2. Wpisz podgląd **zdarzeń** w menu Start, aby otworzyć Windows Podgląd zdarzeń.
3. Na panelu po lewej stronie w obszarze **Akcje** wybierz pozycję **Importuj widok niestandardowy...**.
4. Przejdź do miejsca wyodrębnienia *cfa-events.xml* i wybierz go. Alternatywnie [skopiuj plik XML bezpośrednio](event-views.md).
5. Wybierz przycisk **OK**.

W poniższej tabeli przedstawiono zdarzenia związane z kontrolowanym dostępem do folderów:

<br/><br/>

|Identyfikator zdarzenia|Opis|
|---|---|
|5007|Zdarzenie po zmianie ustawień|
|1124|Zdarzenie dostępu do kontrolowanego folderu z inspekcją|
|1123|Zablokowane zdarzenie dostępu do folderu kontrolowanego|

## <a name="view-or-change-the-list-of-protected-folders"></a>Wyświetlanie lub zmienianie listy folderów chronionych

Możesz użyć aplikacji Zabezpieczenia Windows, aby wyświetlić listę folderów chronionych przez kontrolowany dostęp do folderów.

1. Na urządzeniu Windows 10 lub Windows 11 otwórz aplikację Zabezpieczenia Windows.
2. Wybierz pozycję **Ochrona przed wirusami i zagrożeniami**.
3. W obszarze **Ochrona przed oprogramowaniem wymuszającym okup** wybierz pozycję **Zarządzaj ochroną przed oprogramowaniem wymuszającym okup**.
4. Jeśli kontrolowany dostęp do folderu jest wyłączony, musisz go włączyć. Wybierz **foldery chronione**.
5. Wykonaj jedną z następujących czynności:
   - Aby dodać folder, wybierz pozycję **+ Dodaj folder chroniony**.
   - Aby usunąć folder, wybierz go, a następnie wybierz pozycję **Usuń**.

> [!NOTE]
> [Windows foldery systemowe](#windows-system-folders-are-protected-by-default) są domyślnie chronione i nie można ich usunąć z listy.
