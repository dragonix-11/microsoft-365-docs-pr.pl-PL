---
title: Ukrywanie interfejsu Program antywirusowy Microsoft Defender
description: Kafelek Ochrona przed wirusami i zagrożeniami można ukryć w aplikacji Zabezpieczenia Windows.
keywords: blokada interfejsu użytkownika, tryb bez głowy, ukrywanie aplikacji, ukrywanie ustawień, ukrywanie interfejsu
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: fdd212efd50d55bbcdae80275f5d2ca8a97cdeb3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787671"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Uniemożliwianie użytkownikom korzystania z interfejsu użytkownika Program antywirusowy Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Możesz użyć zasady grupy, aby uniemożliwić użytkownikom w punktach końcowych wyświetlanie interfejsu Program antywirusowy Microsoft Defender. Można również uniemożliwić wstrzymywanie skanowania.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Ukrywanie interfejsu Program antywirusowy Microsoft Defender

W Windows 10 wersje 1703 ukrywanie interfejsu spowoduje ukrycie powiadomień Program antywirusowy Microsoft Defender i uniemożliwi wyświetlenie kafelka Ochrona przed zagrożeniami & wirusów w aplikacji Zabezpieczenia Windows.

Z ustawieniem ustawionym na **Włączone**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Zabezpieczenia Windows bez ikony osłony oraz sekcji ochrony przed wirusami i zagrożeniami" lightbox="../../media/wdav-headless-mode-off-1703.png":::

Ustawienie ma wartość **Wyłączone** lub nieskonfigurowane:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Sekcja Zabezpieczenia Windows z ikoną osłony i ochroną przed zagrożeniami" lightbox="../../media/wdav-headless-mode-1703.png":::

> [!NOTE]
> Ukrycie interfejsu uniemożliwi również wyświetlanie powiadomień Program antywirusowy Microsoft Defender w punkcie końcowym. Ochrona punktu końcowego w usłudze Microsoft Defender powiadomienia będą nadal wyświetlane. Można również indywidualnie [skonfigurować powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)

We wcześniejszych wersjach Windows 10 ustawienie spowoduje ukrycie interfejsu klienta Windows Defender. Jeśli użytkownik spróbuje go otworzyć, otrzyma ostrzeżenie z komunikatem "Administrator systemu ma ograniczony dostęp do tej aplikacji".

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="Komunikat ostrzegawczy, gdy tryb bezgłowy jest włączony w Windows 10, wersje starsze niż 1703" lightbox="../../media/wdav-headless-mode-1607.png":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Ukrywanie interfejsu av usługi Microsoft Defender przed użytkownikami za pomocą zasady grupy

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do **pozycji Konfiguracja komputera**.

3. Kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki > Program antywirusowy Microsoft Defender > interfejs klienta**.

5. Kliknij dwukrotnie ustawienie **Włącz tryb interfejsu użytkownika bez głowy** i ustaw opcję **Włączone**. Kliknij przycisk **OK**.

Zobacz [Uniemożliwianie użytkownikom lokalnego modyfikowania ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md) , aby uzyskać więcej opcji uniemożliwiających użytkownikom modyfikowanie ochrony na komputerach.

## <a name="prevent-users-from-pausing-a-scan"></a>Uniemożliwianie użytkownikom wstrzymywania skanowania

Możesz uniemożliwić użytkownikom wstrzymywanie skanów, co może być pomocne w zapewnieniu, że zaplanowane lub na żądanie skanowania nie zostaną przerwane przez użytkowników.

> [!NOTE]
> To ustawienie nie jest obsługiwane w Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Użyj zasady grupy, aby uniemożliwić użytkownikom wstrzymywanie skanowania

1. Na maszynie zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. Za pomocą **edytora zarządzania zasady grupy** przejdź do **pozycji Konfiguracja komputera**.

3. Kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **Skanuj**.

5. Kliknij dwukrotnie ustawienie **Zezwalaj użytkownikom na wstrzymanie skanowania** i ustaw opcję **Wyłączone**. Kliknij przycisk **OK**.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="related-articles"></a>Artykuły pokrewne

- [Konfiguruj powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurowanie interakcji użytkownika końcowego z Program antywirusowy Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
