---
title: Tworzenie niestandardowego procesu stopniowego wdrażanie aktualizacji programu Microsoft Defender
description: Dowiedz się, jak używać obsługiwanych narzędzi do tworzenia niestandardowego procesu stopniowego wdrażanie aktualizacji
keywords: update tools, gpo, intune, mdm, microsoft endpoint manager, policy, powershell
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4261e32721da86233a0a929a435c318904d6ac12
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324147"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Tworzenie niestandardowego procesu stopniowego wdrażanie aktualizacji programu Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Ta funkcja wymaga Program antywirusowy Microsoft Defender wersji 4.18.2106.X lub nowszej.

Aby utworzyć własny niestandardowy proces stopniowego wdrażanie aktualizacji programu Defender, możesz użyć poleceń zasady grupy, Microsoft Endpoint Manager i PowerShell.

W poniższej tabeli wymieniono dostępne ustawienia zasad grupy dotyczące konfigurowania kanałów aktualizacji:

<br>

****

|Ustawianie tytułu|Opis|Lokalizacja|
|---|---|---|
|Wybierz stopniową comiesięczny kanał aktualizacji platformy Microsoft Defender|Włącz te zasady, aby określić, kiedy urządzenia będą otrzymywać aktualizacje platformy Microsoft Defender podczas comiesięcznego stopniowego wdrażanie. <p> Kanał beta: Urządzenia ustawione dla tego kanału będą pierwszymi użytkownikami, które otrzymają nowe aktualizacje. Wybierz pozycję Kanał Beta, aby wziąć udział w identyfikowaniu problemów i zgłaszaniu problemów firmie Microsoft. Urządzenia w niejawnym Windows są domyślnie subskrybowane w tym kanale. Do używania tylko w (ręcznym) środowisku testowym i w ograniczonej liczbie urządzeń. <p> Bieżący kanał (wersja Preview): Urządzenia ustawione dla tego kanału będą oferowane najwcześniej w trakcie miesięcznego, stopniowego cyklu wydań. Sugerowane dla środowisk przedprodukennych/sprawdzania poprawności. <p> Bieżący kanał (etapowy): Urządzenia będą oferowane po miesięcznym, stopniowym cyklu wydań. Sugerowane zastosowanie do małej, reprezentatywnej części populacji produkcyjnej (~10%). <p> Bieżący kanał (Broad): Urządzenia będą oferowane dopiero po zakończeniu stopniowego cyklu wydań. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%). <p> Opóźnienie krytyczne — czas: Dla urządzeń będą oferowane aktualizacje z 48-godzinnym opóźnieniem. Sugerowane tylko w środowiskach krytycznych. <p>Jeśli wyłączysz lub nie skonfigurujesz tych zasad, urządzenie będzie automatycznie aktualizowane w trakcie stopniowego cyklu wydania. Ta możliwość jest przeznaczona dla większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|Wybierz stopniową aktualizację miesięcznego aparatu usługi Microsoft Defender|Włącz te zasady, aby określić, kiedy urządzenia będą otrzymywać aktualizacje aparatu Microsoft Defender podczas comiesięcznego stopniowego wdrażanie. <p> Kanał beta: Urządzenia ustawione dla tego kanału będą pierwszymi użytkownikami, które otrzymają nowe aktualizacje. Wybierz pozycję Kanał Beta, aby wziąć udział w identyfikowaniu problemów i zgłaszaniu problemów firmie Microsoft. Urządzenia w niejawnym Windows są domyślnie subskrybowane w tym kanale. Do używania tylko w (ręcznym) środowisku testowym i w ograniczonej liczbie urządzeń. <p> Bieżący kanał (wersja Preview): Urządzenia ustawione dla tego kanału będą oferowane najwcześniej w trakcie miesięcznego, stopniowego cyklu wydań. Sugerowane dla środowisk przedprodukennych/sprawdzania poprawności. <p> Bieżący kanał (etapowy): Urządzenia będą oferowane po miesięcznym, stopniowym cyklu wydań. Sugerowane zastosowanie do małej, reprezentatywnej części populacji produkcyjnej (~10%). <p> Bieżący kanał (Broad): Urządzenia będą oferowane dopiero po zakończeniu stopniowego cyklu wydań. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%). <p> Opóźnienie krytyczne — czas: Dla urządzeń będą oferowane aktualizacje z 48-godzinnym opóźnieniem. Sugerowane tylko w środowiskach krytycznych.<p> Jeśli wyłączysz lub nie skonfigurujesz tych zasad, urządzenie będzie automatycznie aktualizowane w trakcie stopniowego cyklu wydania. Ta możliwość jest przeznaczona dla większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|Wybieranie stopniowego kanału wdrażanie aktualizacji codziennej analizy zabezpieczeń usługi Microsoft Defender|Włącz te zasady, aby określić, kiedy urządzenia będą otrzymywać aktualizacje analizy zabezpieczeń programu Microsoft Defender podczas dziennego stopniowego wdrażanie. <p> Bieżący kanał (etapowy): Urządzenia będą oferowane aktualizacje po cyklu wydania. Sugerowane zastosowanie do małej, reprezentatywnej części populacji produkcyjnej (~10%). <p> Bieżący kanał (Broad): Urządzenia będą oferowane dopiero po zakończeniu stopniowego cyklu wydań. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%). <p>  Jeśli wyłączysz lub nie skonfigurujesz tych zasad, urządzenie będzie automatycznie aktualizowane w trakcie dziennego cyklu wydania. Ta możliwość jest przeznaczona dla większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|Wyłączanie stopniowego wdrażanie aktualizacji programu Microsoft Defender|Włącz te zasady, aby wyłączyć stopniowe wdrażanie aktualizacji usługi Defender. <p> Bieżący kanał (Broad): Urządzenia ustawione dla tego kanału będą oferowane jako ostatnie w trakcie stopniowego cyklu wydania. Najlepsze w przypadku komputerów centrów danych, które otrzymują tylko ograniczone aktualizacje. <p> Uwaga: To ustawienie dotyczy zarówno comiesięcznych, jak i codziennych aktualizacji usługi Defender i zastępuje wszelkie wcześniej skonfigurowane wybory kanałów dla aktualizacji platformy i aparatu. <p> Jeśli wyłączysz lub nie skonfigurujesz tych zasad, urządzenie pozostanie w bieżącym kanale (ustawienie domyślne), chyba że określono inaczej w określonych kanałach do aktualizacji platformy i aparatu. Bądź na bieżąco automatycznie w trakcie stopniowego cyklu wydań. Ta możliwość jest przeznaczona dla większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|

## <a name="group-policy"></a>zasady grupy

> [!NOTE]
> Zaktualizowany szablon Defender ADMX zostanie opublikowany wraz z wydaniem 21h2 tego Windows 10. Nie localized version is available to download at https://github.com/microsoft/defender-updatecontrols.

Za [pomocą zasady grupy do](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) konfigurowania i zarządzania Program antywirusowy Microsoft Defender punktami końcowymi.

Poniższej procedury można na ogół używać do konfigurowania lub zmieniania Program antywirusowy Microsoft Defender zasad grupy:

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami **zasady grupy, kliknij** prawym przyciskiem myszy obiekt **zasady grupy(** GPO), który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. Za pomocą edytora zasady grupy zarządzania przejdź do **opcji Konfiguracja komputera**.

3. Kliknij **pozycję Szablony administracyjne**.

4. Rozwiń drzewo, **aby Windows składniki > Program antywirusowy Microsoft Defender**.

5. Rozwiń sekcję (podaną  w tym temacie jako Lokalizacja) zawierającą ustawienie, które chcesz skonfigurować, kliknij dwukrotnie to ustawienie, aby je otworzyć, i dokonaj zmian w konfiguracji.

6. [Wdeksuj zaktualizowanych zasad grupy tak jak zwykle](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

Wykonaj instrukcje z poniższego linku, aby utworzyć zasady niestandardowe w usłudze Intune:

[Dodawanie niestandardowych ustawień dla Windows 10 w aplikacji Microsoft Intune — Azure \|Microsoft Docs](/mem/intune/configuration/custom-settings-windows-10)

Aby uzyskać więcej informacji na temat programu CSP usługi Defender używanego w procesie stopniowego wdrażanie, zobacz Program [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

Użyj polecenia `Set-MpPreference` cmdlet, aby skonfigurować wdrażanie stopniowej aktualizacji.

Użyj następujących parametrów:

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Przykład:

Umożliwia `Set-MpPreference -PlatformUpdatesChannel Beta` skonfigurowanie aktualizacji platformy, aby trafiały z kanału Beta.

Aby uzyskać więcej informacji na temat parametrów i sposobu ich konfigurowania, zobacz [Set-MpPreference (Program antywirusowy Microsoft Defender)| Microsoft Docs](/powershell/module/defender/set-mppreference).
