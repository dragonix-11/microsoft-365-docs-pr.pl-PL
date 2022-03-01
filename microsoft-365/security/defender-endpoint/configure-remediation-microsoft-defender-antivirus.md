---
title: Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender wykrywania błędów
description: Skonfiguruj, Program antywirusowy Microsoft Defender zrobić, gdy wykryje zagrożenie, i jak długo pliki poddane kwarantannie powinny być przechowywane w folderze kwarantanny.
keywords: remediation, fix, remove, threats, quarantine, scan, restore
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
ms.openlocfilehash: 182e0b39c1a9c7795fbdd716fc2e260d06d5c451
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996779"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Konfigurowanie działań naprawczych Program antywirusowy Microsoft Defender wykrywania błędów


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Po Program antywirusowy Microsoft Defender skanowania próbuje on rozwiązać lub usunąć wykryte zagrożenia. Możesz skonfigurować sposób, Program antywirusowy Microsoft Defender się z niektórymi zagrożeniami, czy punkt przywracania powinien zostać utworzony przed podjęciem działań naprawczych i kiedy zagrożenia powinny zostać usunięte.

W tym artykule opisano sposób konfigurowania tych ustawień przy użyciu programu zasady grupy, ale można też używać aplikacji [Microsoft Endpoint Configuration Manager i](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) [Microsoft Intune](/intune/device-restrictions-configure).

Te ustawienia możesz również [`Set-MpPreference` skonfigurować za pomocą polecenia cmdlet](/powershell/module/defender/set-mppreference) [`MSFT_MpPreference`](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) programu PowerShell lub klasy WMI.

## <a name="configure-remediation-options"></a>Konfigurowanie opcji rozwiązywania problemów

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie kliknij pozycję **Edytuj**.

2. W **administracyjnym zasady grupy zarządzania przejdź** do **strony Konfiguracja komputera i** wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender**\>.

4. W poniższej tabeli wybierz lokalizację, a następnie edytuj zasady zgodnie z potrzebami.

5. Wybierz przycisk **OK**.

<br/><br/>

|Lokalizacja|Ustawienie|Opis|Ustawienie domyślne (jeśli nie jest skonfigurowane)|
|---|---|---|---|
|Skanowanie|Tworzenie punktu przywracania systemu|Każdego dnia przed próbą czyszczenia lub skanowania zostanie utworzony punkt przywracania systemu|Wyłączone|
|Skanowanie|Włączanie usuwania elementów z folderu historii skanowania|Określanie dni zachowywania elementów w historii skanowania|30 dni|
|Katalog główny|Wyłączanie rutynowych działań naprawczych|Możesz określić, czy będą Program antywirusowy Microsoft Defender rozwiązywanie zagrożeń, czy też należy zapytać użytkownika końcowego, co należy zrobić.|Wyłączone (zagrożenia są usuwane automatycznie)|
|Kwarantanna|Konfigurowanie usuwania elementów z folderu kwarantanny|Określ, ile dni elementy mają być przechowywane w kwarantannie przed usunięciem|90 dni|
|Zagrożenia|Określanie poziomów alertów o zagrożeniach, na których domyślne działania nie powinny być podejmowane podczas wykrywania|Każde zagrożenie wykryte przez Program antywirusowy Microsoft Defender jest przypisywane jako poziom zagrożenia (niski, średni, wysoki lub poważny). Za pomocą tego ustawienia można zdefiniować sposób korygowania wszystkich zagrożeń dla poszczególnych poziomów zagrożeń (poddanych kwarantannie, usuniętych lub zignorowanych).|Nie dotyczy|
|Zagrożenia|Określanie zagrożeń, w przypadku których nie należy stosować akcji domyślnej w przypadku wykrycia|Określ, w jaki sposób mają zostać usunięte określone zagrożenia (używając ich identyfikatora zagrożeń). Możesz określić, czy określone zagrożenie ma zostać poddane kwarantannie, usunięte lub zignorowane.|Nie dotyczy|

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender wykrywa i rekultywuje pliki na podstawie wielu czynników. Czasami ukończenie działania naprawczego wymaga ponownego uruchomienia komputera. Nawet jeśli wykrywanie zostanie później określone jako fałszywie dodatnie, ponowne uruchomienie musi zostać ukończone, aby zapewnić, że zostały wykonane wszystkie dodatkowe kroki rozwiązywania problemów.
>
> Jeśli masz pewność, Program antywirusowy Microsoft Defender w kwarantannie pliku na podstawie wyników fałszywie dodatnich, możesz przywrócić go z kwarantanny po ponownym uruchomieniu urządzenia. Zobacz [Przywracanie plików poddanych kwarantannie w Program antywirusowy Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> Aby uniknąć tego problemu w przyszłości, możesz wykluczyć pliki ze skanów. Zobacz [Konfigurowanie i weryfikowanie wykluczeń Program antywirusowy Microsoft Defender skanowania.](configure-exclusions-microsoft-defender-antivirus.md)

Zobacz też [Konfigurowanie wymaganych w harmonogramie pełnych Program antywirusowy Microsoft Defender,](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) aby uzyskać więcej ustawień związanych z działaniami naprawczymi.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie Program antywirusowy Microsoft Defender opcji skanowania](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Konfigurowanie zaplanowanych Program antywirusowy Microsoft Defender skanowania](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Konfigurowanie i uruchamianie skanowania na żądanie Program antywirusowy Microsoft Defender skanowania](run-scan-microsoft-defender-antivirus.md)
- [Konfigurowanie powiadomień wyświetlanych w punktach końcowych](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurowanie interakcji użytkownika końcowego Program antywirusowy Microsoft Defender użytkownika](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Dostosowywanie, inicjowanie i przeglądanie wyników skanów Program antywirusowy Microsoft Defender środków zaradczych](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
