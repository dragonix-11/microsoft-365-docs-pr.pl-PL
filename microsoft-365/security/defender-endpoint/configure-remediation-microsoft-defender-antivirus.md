---
title: Konfiguruj korygowanie wykryć programu antywirusowego Microsoft Defender
description: Skonfiguruj, co Program antywirusowy Microsoft Defender zrobić, gdy wykryje zagrożenie i jak długo pliki poddane kwarantannie powinny być przechowywane w folderze kwarantanny
keywords: korygowanie, naprawianie, usuwanie, zagrożenia, kwarantanna, skanowanie, przywracanie
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 257a3bfc4fc9dcb6353bb158bc3cd4296891ae76
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790157"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Konfiguruj korygowanie wykryć programu antywirusowego Microsoft Defender


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Gdy Program antywirusowy Microsoft Defender uruchamia skanowanie, podejmuje próbę skorygowania lub usunięcia wykrytych zagrożeń. Można skonfigurować sposób, w jaki Program antywirusowy Microsoft Defender powinny rozwiązywać pewne zagrożenia, czy należy utworzyć punkt przywracania przed korygowaniem i kiedy należy usunąć zagrożenia.

W tym artykule opisano sposób konfigurowania tych ustawień przy użyciu zasady grupy, ale można również użyć [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) i [Microsoft Intune](/intune/device-restrictions-configure).

Do skonfigurowania tych ustawień można również użyć [`Set-MpPreference` polecenia cmdlet programu PowerShell](/powershell/module/defender/set-mppreference) lub [`MSFT_MpPreference` klasy WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) .

## <a name="configure-remediation-options"></a>Konfigurowanie opcji korygowania

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i kliknij przycisk **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, aby **Windows składniki** \> **Program antywirusowy Microsoft Defender**.

4. Korzystając z poniższej tabeli, wybierz lokalizację, a następnie w razie potrzeby edytuj zasady.

5. Wybierz przycisk **OK**.

<br/><br/>

|Lokalizacja|Ustawienie|Opis|Ustawienie domyślne (jeśli nie jest skonfigurowane)|
|---|---|---|---|
|Skanowania|Tworzenie punktu przywracania systemu|Punkt przywracania systemu zostanie utworzony każdego dnia przed podjęciem próby czyszczenia lub skanowania|Wyłączona|
|Skanowania|Włączanie usuwania elementów z folderu historii skanowania|Określanie liczby dni przechowywania elementów w historii skanowania|30 dni|
|Głównego|Wyłączanie rutynowego korygowania|Możesz określić, czy Program antywirusowy Microsoft Defender automatycznie koryguje zagrożenia, czy też powinien zapytać użytkownika punktu końcowego, co należy zrobić.|Wyłączone (zagrożenia są korygowane automatycznie)|
|Kwarantanna|Konfigurowanie usuwania elementów z folderu Kwarantanna|Określ liczbę dni przechowywania elementów w kwarantannie przed usunięciem|90 dni|
|Zagrożeń|Określanie poziomów alertów o zagrożeniach, przy których nie należy wykonywać akcji domyślnej po wykryciu|Każde zagrożenie wykryte przez Program antywirusowy Microsoft Defender ma przypisany poziom zagrożenia (niski, średni, wysoki lub poważny). To ustawienie służy do definiowania sposobu korygowania wszystkich zagrożeń dla każdego z poziomów zagrożeń (poddawanych kwarantannie, usuwanych lub ignorowanych)|Nie dotyczy|
|Zagrożeń|Określanie zagrożeń, dla których nie należy podejmować akcji domyślnej po wykryciu|Określ sposób korygowania określonych zagrożeń (przy użyciu ich identyfikatora zagrożenia). Możesz określić, czy określone zagrożenie powinno zostać poddane kwarantannie, usunięte lub zignorowane|Nie dotyczy|

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender wykrywa i koryguje pliki na podstawie wielu czynników. Czasami ukończenie korygowania wymaga ponownego uruchomienia. Nawet jeśli wykrywanie zostanie później uznane za fałszywie dodatnie, ponowne uruchomienie musi zostać ukończone, aby upewnić się, że wszystkie dodatkowe kroki korygowania zostały ukończone.
>
> Jeśli masz pewność, Program antywirusowy Microsoft Defender plik został poddany kwarantannie na podstawie fałszywie dodatniego wyniku, możesz przywrócić plik z kwarantanny po ponownym uruchomieniu urządzenia. Zobacz [Przywracanie plików poddanych kwarantannie w Program antywirusowy Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> Aby uniknąć tego problemu w przyszłości, możesz wykluczyć pliki ze skanowania. Zobacz [Konfigurowanie i weryfikowanie wykluczeń dla skanowania Program antywirusowy Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

Zobacz również [Konfigurowanie wymaganych do korygowania zaplanowanych pełnych skanów Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed), aby uzyskać więcej ustawień związanych z korygowania.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Konfiguruj opcje skanowania programu antywirusowego Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Konfigurowanie zaplanowanych skanów Program antywirusowy Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Konfiguruj i uruchom skanowania programu antywirusowego Microsoft Defender na żądanie](run-scan-microsoft-defender-antivirus.md)
- [Konfiguruj powiadomienia wyświetlane w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurowanie interakcji Program antywirusowy Microsoft Defender użytkownika końcowego](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Dostosowywanie, inicjowanie i przeglądanie wyników skanowania i korygowania Program antywirusowy Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
