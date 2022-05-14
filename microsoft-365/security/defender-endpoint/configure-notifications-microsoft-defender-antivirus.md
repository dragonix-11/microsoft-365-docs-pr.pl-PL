---
title: Konfigurowanie powiadomień Program antywirusowy Microsoft Defender
description: Dowiedz się, jak skonfigurować i dostosować zarówno standardowe, jak i inne powiadomienia Program antywirusowy Microsoft Defender w punktach końcowych.
keywords: powiadomienia, obrońca, oprogramowanie antywirusowe, punkt końcowy, zarządzanie, administrator
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 6c9dfd603a128de4a94c9cf49faa6ba9ca940d9b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418187"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Konfigurowanie powiadomień Program antywirusowy Microsoft Defender wyświetlanych w punktach końcowych

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

W Windows 10 i Windows 11 powiadomienia aplikacji dotyczące wykrywania i korygowania złośliwego oprogramowania są bardziej niezawodne, spójne i zwięzłe. Program antywirusowy Microsoft Defender powiadomienia są wyświetlane w punktach końcowych po zakończeniu skanowania i wykryciu zagrożeń. Powiadomienia są wykonywane zarówno po zaplanowanych, jak i ręcznie wyzwalanych skanowaniach. Te powiadomienia są również wyświetlane w **Centrum powiadomień**, a podsumowanie skanów i wykrywania zagrożeń jest wyświetlane w regularnych odstępach czasu.

Jeśli jesteś członkiem zespołu ds. zabezpieczeń organizacji, możesz skonfigurować sposób wyświetlania powiadomień w punktach końcowych, na przykład powiadomienia monitujące o ponowne uruchomienie systemu lub wskazujące, że wykryto i skorygowano zagrożenie.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>Konfigurowanie powiadomień antywirusowych przy użyciu zasady grupy lub aplikacji Zabezpieczenia Windows

Możesz skonfigurować wyświetlanie dodatkowych powiadomień, takich jak ostatnie podsumowania wykrywania zagrożeń, w [aplikacji Zabezpieczenia Windows](microsoft-defender-security-center-antivirus.md) i za pomocą zasady grupy.

> [!NOTE]
> W Windows 10 wersja 1607 ta funkcja została **nazwana Rozszerzone powiadomienia** i została skonfigurowana **w** \> Windows Ustawienia **Update & Windows Defender zabezpieczeń**\>. W zasady grupy ustawień dla wszystkich wersji Windows 10 i Windows 11 funkcja powiadomień nosi nazwę **Powiadomienia rozszerzone**.

### <a name="use-group-policy-to-disable-additional-notifications"></a>Wyłączanie dodatkowych powiadomień przy użyciu zasady grupy

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

4. Wybierz pozycję **Szablony administracyjne**.

5. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** >  **Raportowanie**.

6. Kliknij dwukrotnie **pozycję Wyłącz powiadomienia rozszerzone** i ustaw opcję **Włączone**. Następnie wybierz przycisk **OK**. Uniemożliwi to wyświetlanie dodatkowych powiadomień.

> [!IMPORTANT]
> Wyłączenie dodatkowych powiadomień nie spowoduje wyłączenia powiadomień krytycznych, takich jak alerty wykrywania zagrożeń i korygowania.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Wyłączanie dodatkowych powiadomień za pomocą aplikacji Zabezpieczenia Windows

1. Otwórz aplikację Zabezpieczenia Windows, klikając ikonę osłony na pasku zadań lub wyszukując menu Start dla pozycji **Zabezpieczenia**.

2. Wybierz kafelek **Ochrona przed zagrożeniami &** wirusami (lub ikona osłony na pasku menu po lewej stronie), a następnie wybierz pozycję **Ustawienia ochrony przed zagrożeniami & wirusów**

3. Przewiń do sekcji **Powiadomienia** i wybierz pozycję **Zmień ustawienia powiadomień**.

4. Przesuń przełącznik do **pozycji Wyłączone** lub **Włączone** , aby wyłączyć lub włączyć dodatkowe powiadomienia.

> [!IMPORTANT]
> Wyłączenie dodatkowych powiadomień nie spowoduje wyłączenia powiadomień krytycznych, takich jak alerty wykrywania zagrożeń i korygowania.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>Konfigurowanie standardowych powiadomień w punktach końcowych przy użyciu zasady grupy

Możesz użyć zasady grupy, aby:

- Wyświetl dodatkowy, dostosowany tekst w punktach końcowych, gdy użytkownik musi wykonać akcję
- Ukryj wszystkie powiadomienia w punktach końcowych
- Ukryj powiadomienia ponownego uruchamiania w punktach końcowych

Ukrywanie powiadomień może być przydatne w sytuacjach, w których nie można ukryć całego interfejsu Program antywirusowy Microsoft Defender. Aby uzyskać więcej informacji, zobacz [Zapobieganie wyświetlaniu lub interakcji użytkowników z interfejsem użytkownika Program antywirusowy Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md). Ukrywanie powiadomień będzie miało miejsce tylko w punktach końcowych, do których zostały wdrożone zasady. Powiadomienia związane z akcjami, które należy wykonać (na przykład ponowny rozruch), będą nadal wyświetlane na [Microsoft Endpoint Manager Endpoint Protection pulpitu nawigacyjnego monitorowania i raportów](/configmgr/protect/deploy-use/monitor-endpoint-protection). 

Aby dodać niestandardowe informacje kontaktowe do powiadomień punktu końcowego, zobacz [Dostosowywanie aplikacji Zabezpieczenia Windows dla organizacji](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>Ukrywanie powiadomień przy użyciu zasady grupy

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**, a następnie wybierz pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **interfejs klienta**. 

5. Kliknij dwukrotnie **pozycję Pomiń wszystkie powiadomienia** i ustaw opcję **Włączone**. 

6. Wybierz przycisk **OK**. Uniemożliwi to wyświetlanie dodatkowych powiadomień.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Ukrywanie powiadomień o ponownym uruchomieniu przy użyciu zasady grupy

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera**.

3. Kliknij pozycję **Szablony administracyjne**.

4. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **interfejs klienta**.

5. Kliknij **dwukrotnie pozycję Pomija powiadomienia ponownego uruchamiania** i ustaw opcję **Włączone**. 

5. Wybierz przycisk **OK**. Uniemożliwi to wyświetlanie dodatkowych powiadomień.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)