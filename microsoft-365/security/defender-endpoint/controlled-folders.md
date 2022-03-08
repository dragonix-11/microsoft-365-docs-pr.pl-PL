---
title: Ochrona ważnych folderów przed oprogramowaniem wymuszającym okup przed zaszyfrowaniem plików za pomocą kontrolowanego dostępu do folderów
description: Pliki w folderach domyślnych mogą być chronione przed zmianą przez złośliwe aplikacje. Zapobiegaj szyfrowaniu plików przez oprogramowanie wymuszające okup.
keywords: Kontrolowany dostęp do folderów, windows 10, windows defender, oprogramowanie wymuszające okup, ochrona, pliki, foldery
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
ms.openlocfilehash: ea3e45a5469c9769f55f9ce90f799c54556de814
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322901"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>Co to jest kontrolowany dostęp do folderu?

Kontrolowany dostęp do folderu pomaga chronić cenne dane przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. Kontrolowany dostęp do folderu chroni Twoje dane, sprawdzając aplikacje przed listą znanych, zaufanych aplikacji. Obsługiwane w klientach Windows Server 2019, Windows Server 2022, Windows 10 i Windows 11, kontrolowany dostęp do folderu można włączona przy użyciu aplikacji Zabezpieczenia Windows, Microsoft Endpoint Configuration Manager lub Intune (w przypadku urządzeń zarządzanych).

> [!NOTE]
> Aparaty skryptów nie są zaufane i nie można na nie zezwolić na dostęp do chronionych folderów. Na przykład program PowerShell nie jest zaufany przez kontrolowany dostęp do folderu, nawet jeśli zezwala się na to ze wskaźnikami [plików i certyfikatów](/microsoft-365/security/defender-endpoint/indicator-certificates).

Kontrolowany dostęp do folderu działa najlepiej z programem [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md), który zapewnia szczegółowe raportowanie w zdarzeniach i blokach kontrolowanego dostępu do folderu jako część zwykłego [scenariuszy analizy alertów](investigate-alerts.md).

> [!TIP]
> Kontrolowane bloki dostępu do folderów nie generują alertów w [kolejce alertów](alerts-queue.md). W widoku osi czasu urządzenia możesz jednak wyświetlać informacje o blokach dostępu do folderów [kontrolowanych podczas zaawansowanego](investigate-machines.md) wyszukiwania lub z niestandardowymi [regułami wykrywania](custom-detection-rules.md).[](advanced-hunting-overview.md)

## <a name="how-does-controlled-folder-access-work"></a>Jak działa kontrolowany dostęp do folderu?

Kontrolowany dostęp do folderu działa tylko przez zezwolenie zaufanym aplikacjom na dostęp do folderów chronionych. Foldery chronione są określane po skonfigurowaniu kontrolowanego dostępu do folderu. Zazwyczaj często używane foldery, takie jak foldery używane do dokumentów, obrazów, pobierania itp., są uwzględniane na liście folderów kontrolowanych.

Kontrolowany dostęp do folderu działa z listą zaufanych aplikacji. Aplikacje dołączone do listy zaufanych programów działają zgodnie z oczekiwaniami. Aplikacje, których nie ma na liście, nie mogą wprowadzać żadnych zmian w plikach wewnątrz folderów chronionych.

Aplikacje są dodawane do listy na podstawie ich reputacji i reputacji. Aplikacje, które są bardzo rozpowszechnione w całej organizacji i które nigdy nie wyświetlały żadnych zachowań uznanych za złośliwe, są uznawane za wiarygodne. Te aplikacje zostaną automatycznie dodane do listy.

Aplikacje można również dodawać ręcznie do listy zaufanych przy użyciu aplikacji Menedżer konfiguracji Intune. Dodatkowe akcje można wykonywać z Microsoft 365 Defender portalu.

## <a name="why-controlled-folder-access-is-important"></a>Dlaczego kontrolowany dostęp do folderu jest ważny

Kontrolowany dostęp do folderów jest szczególnie przydatny w ochronie dokumentów i informacji przed oprogramowaniem wymuszającym [okup](https://www.microsoft.com/wdsi/threats/ransomware). W przypadku ataku oprogramowania wymuszającego okup pliki mogą zostać zaszyfrowane i utrzymywane u hosta. W przypadku kontrolowanego dostępu do folderu na komputerze, na którym aplikacja próbowała wprowadzić zmiany w pliku w chronionym folderze, jest wyświetlane powiadomienie. Możesz dostosować [powiadomienie, modyfikując](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) je wraz ze szczegółami twojej firmy i informacjami kontaktowymi. Można również włączyć poszczególne reguły, aby dostosować techniki monitorów funkcji.

Chronione [foldery obejmują](#review-controlled-folder-access-events-in-windows-event-viewer) typowe foldery systemowe (w tym foldery rozruchu), w [tym foldery, w których można dodać więcej folderów](customize-controlled-folders.md#protect-additional-folders). Możesz również [zezwolić aplikacjom](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) na nadaj im dostęp do chronionych folderów.

Za pomocą trybu [inspekcji można](audit-windows-defender.md) ocenić wpływ kontrolowanego dostępu do folderu na organizację, jeśli został włączony. Możesz również odwiedzić witrynę internetową testów Windows Defender w witrynie demo.wd.microsoft.com, [](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) aby upewnić się, że funkcja działa i jak działa.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

Kontrolowany dostęp do folderów jest obsługiwany w następujących wersjach programu Windows:

- [Windows 10, wersja 1709](/windows/whats-new/whats-new-windows-10-version-1709) i nowsze
- Windows 11
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows folderów systemowych są domyślnie chronione

Windows folderów systemowych są domyślnie chronione wraz z kilkoma innymi folderami:

Chronione foldery obejmują typowe foldery systemowe (w tym foldery rozruchu), w tym foldery, w których można dodawać kolejne foldery. Możesz również zezwolić aplikacjom na nadaj im dostęp do chronionych folderów.  Foldery Windows, które są domyślnie chronione, to:

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

Foldery domyślne są wyświetlane w profilu użytkownika w **obszarze Ten komputer**.
   > [!div class="mx-imgBorder"]
   > ![Chronione Windows domyślnych folderów systemowych](images/defaultfolders.png)

> [!NOTE]
> Dodatkowe foldery można skonfigurować jako chronione, ale nie można Windows folderów systemowych, które są domyślnie chronione.

## <a name="requirements-for-controlled-folder-access"></a>Wymagania dotyczące kontrolowanego dostępu do folderu

Kontrolowany dostęp do folderu wymaga [Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md).

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>Przeglądanie zdarzeń kontrolowanego dostępu do folderu w Microsoft 365 Defender folderów

Usługa Defender for Endpoint udostępnia szczegółowe raportowanie zdarzeń i bloków w ramach scenariuszy analizy [alertów](investigate-alerts.md) w portalu Microsoft 365 Defender; zobacz Program [Microsoft Defender for Endpoint w](../defender/microsoft-365-security-center-mde.md) Microsoft 365 Defender.

Program Microsoft Defender umożliwia wyszukiwanie danych punktu końcowego przy użyciu wyszukiwania [zaawansowanego](advanced-hunting-overview.md). Jeśli korzystasz [z trybu inspekcji](audit-windows-defender.md), możesz użyć zaawansowanego [](advanced-hunting-overview.md) wyszukiwania, aby zobaczyć, jak kontrolowane ustawienia dostępu do folderu wpływają na Twoje środowisko, jeśli zostały włączone.

Przykładowe zapytanie:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Przeglądanie zdarzeń kontrolowanego dostępu do folderu w Windows Zdarzeń

Możesz przejrzeć dziennik Windows zdarzeń, aby zobaczyć zdarzenia utworzone w przypadku kontrolowanego dostępu do folderu (lub inspekcji) w aplikacji:

1. Pobierz pakiet [oceny i](https://aka.ms/mp7z2w) wyodrębnij plik *cfa-events.xml* w łatwo dostępnej lokalizacji na urządzeniu.
2. Wpisz **Podgląd zdarzeń** w menu Start, aby otworzyć Windows Podgląd zdarzeń.
3. W panelu po lewej stronie w **obszarze Akcje** wybierz pozycję **Importuj widok niestandardowy...**.
4. Przejdź do wyodrębnianych *cfa-events.xml* zaznacz je. Ewentualnie skopiuj [kod XML bezpośrednio](event-views.md).
5. Wybierz przycisk **OK**.

W poniższej tabeli przedstawiono zdarzenia związane z kontrolowanym dostępem do folderu:

<br/><br/>

|Identyfikator zdarzenia|Opis|
|---|---|
|5007|Zdarzenie w przypadku zmiany ustawień|
|1124|Zdarzenie kontrolowanego dostępu do folderu|
|1123|Zdarzenie zablokowanego dostępu do folderu|

## <a name="view-or-change-the-list-of-protected-folders"></a>Wyświetlanie lub zmienianie listy folderów chronionych

Za pomocą tej Zabezpieczenia Windows możesz wyświetlić listę folderów chronionych przez kontrolowany dostęp do folderów.

1. Na urządzeniu Windows 10 lub Windows 11 otwórz Zabezpieczenia Windows aplikację.
2. Wybierz **pozycję Ochrona & przed zagrożeniami**.
3. W **obszarze Ochrona przed oprogramowaniem wymuszającym** okup wybierz **pozycję Zarządzaj ochroną oprogramowania wymuszającego okup**.
4. Jeśli kontrolowany dostęp do folderu jest wyłączony, musisz go włączyć. Wybieranie **folderów chronionych**.
5. Wykonaj jedną z następujących czynności:
   - Aby dodać folder, wybierz **pozycję + Dodaj chroniony folder**.
   - Aby usunąć folder, zaznacz go, a następnie wybierz pozycję **Usuń**.

> [!NOTE]
> [Windows folderów systemowych](#windows-system-folders-are-protected-by-default) są domyślnie chronione i nie można ich usuwać z listy.
