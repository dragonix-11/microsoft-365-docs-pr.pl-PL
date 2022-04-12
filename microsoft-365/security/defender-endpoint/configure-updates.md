---
title: Tworzenie niestandardowego procesu stopniowego wdrażania aktualizacji usługi Microsoft Defender
description: Dowiedz się, jak za pomocą obsługiwanych narzędzi utworzyć niestandardowy proces stopniowego wdrażania aktualizacji
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
ms.openlocfilehash: 4a963172e69b61a7cb33486132630e0d56d0420b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788551"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Tworzenie niestandardowego procesu stopniowego wdrażania aktualizacji usługi Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> [!NOTE]
> Ta funkcja wymaga Program antywirusowy Microsoft Defender wersji 4.18.2106.X lub nowszej.

Aby utworzyć własny niestandardowy proces stopniowego wdrażania aktualizacji usługi Defender, możesz użyć zasady grupy, Microsoft Endpoint Manager i programu PowerShell.

Poniższa tabela zawiera listę dostępnych ustawień zasad grupy do konfigurowania kanałów aktualizacji:

<br>

****

|Ustawianie tytułu|Opis|Lokalizacja|
|---|---|---|
|Wybieranie stopniowego miesięcznego kanału wdrażania aktualizacji platformy w usłudze Microsoft Defender|Włącz te zasady, aby określić, kiedy urządzenia otrzymują aktualizacje platformy Microsoft Defender podczas comiesięcznego stopniowego wdrażania. <p> Kanał beta: urządzenia ustawione na ten kanał będą pierwszymi, które otrzymają nowe aktualizacje. Wybierz pozycję Beta Channel, aby wziąć udział w identyfikowaniu i zgłaszaniu problemów firmie Microsoft. Urządzenia w programie Windows Insider Program są domyślnie subskrybowane w tym kanale. Do użytku tylko w środowiskach testowych (ręcznych) i ograniczonej liczbie urządzeń. <p> Bieżący kanał (wersja zapoznawcza): urządzenia ustawione na ten kanał będą oferowane najwcześniej podczas miesięcznego stopniowego cyklu wydawania. Sugerowane dla środowisk przedprodukcyjnych/walidacyjnych. <p> Bieżący kanał (etapowe): urządzenia będą oferowane aktualizacje po comiesięcznym stopniowej wersji. Sugerowane zastosowanie do niewielkiej, reprezentatywnej części populacji produkcyjnej (~10%). <p> Bieżący kanał (szeroki): urządzenia będą oferowane aktualizacje dopiero po zakończeniu stopniowego cyklu wydawania. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%). <p> Krytyczne — opóźnienie czasu: urządzenia będą oferowane aktualizacje z 48-godzinnym opóźnieniem. Sugerowane tylko dla środowisk krytycznych. <p>Jeśli te zasady zostaną wyłączone lub nie zostaną skonfigurowane, urządzenie będzie aktualizowane automatycznie podczas stopniowego cyklu wydawania. Nadaje się do większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|Wybieranie kanału stopniowego comiesięcznego wdrażania aktualizacji aparatu w usłudze Microsoft Defender|Włącz te zasady, aby określić, kiedy urządzenia odbierają aktualizacje aparatu usługi Microsoft Defender podczas comiesięcznego stopniowego wdrażania. <p> Kanał beta: urządzenia ustawione na ten kanał będą pierwszymi, które otrzymają nowe aktualizacje. Wybierz pozycję Beta Channel, aby wziąć udział w identyfikowaniu i zgłaszaniu problemów firmie Microsoft. Urządzenia w programie Windows Insider Program są domyślnie subskrybowane w tym kanale. Do użytku tylko w środowiskach testowych (ręcznych) i ograniczonej liczbie urządzeń. <p> Bieżący kanał (wersja zapoznawcza): urządzenia ustawione na ten kanał będą oferowane najwcześniej podczas miesięcznego stopniowego cyklu wydawania. Sugerowane dla środowisk przedprodukcyjnych/walidacyjnych. <p> Bieżący kanał (etapowe): urządzenia będą oferowane aktualizacje po comiesięcznym stopniowej wersji. Sugerowane zastosowanie do niewielkiej, reprezentatywnej części populacji produkcyjnej (~10%). <p> Bieżący kanał (szeroki): urządzenia będą oferowane aktualizacje dopiero po zakończeniu stopniowego cyklu wydawania. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%). <p> Krytyczne — opóźnienie czasu: urządzenia będą oferowane aktualizacje z 48-godzinnym opóźnieniem. Sugerowane tylko dla środowisk krytycznych.<p> Jeśli te zasady zostaną wyłączone lub nie zostaną skonfigurowane, urządzenie będzie aktualizowane automatycznie podczas stopniowego cyklu wydawania. Nadaje się do większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|Wybieranie kanału stopniowego wdrażania codziennych aktualizacji analizy zabezpieczeń usługi Microsoft Defender|Włącz te zasady, aby określić, kiedy urządzenia otrzymują aktualizacje analizy zabezpieczeń usługi Microsoft Defender podczas codziennego stopniowego wdrażania. <p> Bieżący kanał (etapowe): urządzenia będą oferowane aktualizacje po cyklu wydania. Sugerowane zastosowanie do niewielkiej, reprezentatywnej części populacji produkcyjnej (~10%). <p> Bieżący kanał (szeroki): urządzenia będą oferowane aktualizacje dopiero po zakończeniu stopniowego cyklu wydawania. Sugerowane zastosowanie do szerokiego zestawu urządzeń w populacji produkcyjnej (~10–100%). <p>  Jeśli te zasady zostaną wyłączone lub nie zostaną skonfigurowane, urządzenie będzie aktualizowane automatycznie podczas codziennego cyklu wydawania. Nadaje się do większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|Wyłączanie stopniowego wdrażania aktualizacji usługi Microsoft Defender|Włącz te zasady, aby wyłączyć stopniowe wdrażanie aktualizacji usługi Defender. <p> Bieżący kanał (szeroki): urządzenia ustawione na ten kanał będą oferowane aktualizacje ostatnio podczas stopniowego cyklu wydawania. Najlepiej w przypadku maszyn centrów danych, które otrzymują tylko ograniczone aktualizacje. <p> Uwaga: to ustawienie dotyczy zarówno aktualizacji miesięcznych, jak i codziennych aktualizacji usługi Defender i zastąpi wszystkie wcześniej skonfigurowane opcje kanału dla aktualizacji platformy i aparatu. <p> Jeśli te zasady zostaną wyłączone lub nie zostaną skonfigurowane, urządzenie pozostanie w bieżącym kanale (domyślnym), chyba że określono inaczej w określonych kanałach aktualizacji platformy i aparatu. Bądź na bieżąco automatycznie podczas stopniowego cyklu wydawania. Nadaje się do większości urządzeń.|Windows Components\Program antywirusowy Microsoft Defender|
|

## <a name="group-policy"></a>Zasady grupy

> [!NOTE]
> Zaktualizowany szablon usługi Defender ADMX zostanie opublikowany wraz z wersją 21H2 Windows 10. Wersja niezlokalizowana jest dostępna do pobrania pod adresem https://github.com/microsoft/defender-updatecontrols.

Za pomocą [zasady grupy](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) można konfigurować Program antywirusowy Microsoft Defender i zarządzać nimi w punktach końcowych.

Ogólnie rzecz biorąc, można użyć następującej procedury, aby skonfigurować lub zmienić ustawienia zasad grupy Program antywirusowy Microsoft Defender:

1. Na maszynie zarządzania zasady grupy otwórz **konsolę zarządzania zasady grupy**, kliknij prawym przyciskiem myszy **obiekt zasady grupy** , który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Za pomocą edytora zarządzania zasady grupy przejdź do **pozycji Konfiguracja komputera**.

3. Kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender**.

5. Rozwiń sekcję (określaną jako **Lokalizacja** w tabeli w tym temacie), która zawiera ustawienie, które chcesz skonfigurować, kliknij dwukrotnie ustawienie, aby je otworzyć, i wprowadź zmiany konfiguracji.

6. [Wdróż zaktualizowany obiekt zasad grupy tak, jak zwykle](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

Postępuj zgodnie z instrukcjami w poniższym linku, aby utworzyć zasady niestandardowe w Intune:

[Dodawanie ustawień niestandardowych dla urządzeń Windows 10 w Microsoft Intune — Azure \|Microsoft Docs](/mem/intune/configuration/custom-settings-windows-10)

Aby uzyskać więcej informacji na temat dostawcy CSP usługi Defender używanego do stopniowego wdrażania, zobacz [Dostawca CSP usługi Defender](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

`Set-MpPreference` Użyj polecenia cmdlet, aby skonfigurować wdrażanie aktualizacji stopniowych.

Użyj następujących parametrów:

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Przykład:

Użyj polecenia `Set-MpPreference -PlatformUpdatesChannel Beta` , aby skonfigurować aktualizacje platformy do odebrania z kanału beta.

Aby uzyskać więcej informacji na temat parametrów i sposobu ich konfigurowania, zobacz [Set-MpPreference (Program antywirusowy Microsoft Defender)|Microsoft Docs](/powershell/module/defender/set-mppreference).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)