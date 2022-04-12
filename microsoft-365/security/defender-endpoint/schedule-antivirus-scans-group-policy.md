---
title: Planowanie skanowania antywirusowego przy użyciu zasady grupy
description: Konfigurowanie skanowania antywirusowego przy użyciu zasady grupy
keywords: szybkie skanowanie, pełne skanowanie, harmonogram, zasady grupy, oprogramowanie antywirusowe
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/10/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: dbd3f2b4342757509a6440ff87a112b75b663f22
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788045"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>Planowanie skanowania antywirusowego przy użyciu zasady grupy

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

W tym artykule opisano sposób konfigurowania zaplanowanych skanów przy użyciu zasady grupy. Aby dowiedzieć się więcej na temat planowania skanowania i typów skanowania, zobacz [Konfigurowanie zaplanowanych szybkich lub pełnych skanów Program antywirusowy Microsoft Defender](schedule-antivirus-scans.md). 

## <a name="configure-antivirus-scans-using-group-policy"></a>Konfigurowanie skanowania antywirusowego przy użyciu zasady grupy

1. Na maszynie zarządzania zasady grupy w edytorze zasady grupy przejdź do pozycji **Konfiguracja** \> komputera **Szablony** \> administracyjne **Windows Składniki** \> **Program antywirusowy Microsoft Defender** \> **Skanowania**.

2. Kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. Określ ustawienia obiektu zasady grupy, a następnie wybierz przycisk **OK**. 

4. Powtórz kroki 1–4 dla każdego ustawienia, które chcesz skonfigurować.

5. Wdróż obiekt zasady grupy tak, jak zwykle. Jeśli potrzebujesz pomocy dotyczącej obiektów zasady grupy, zobacz [Tworzenie obiektu zasady grupy](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object).

> [!NOTE]
> Podczas konfigurowania zaplanowanych skanów ustawienie **Uruchom zaplanowane skanowanie tylko wtedy, gdy komputer jest włączony, ale nie jest używany**, co jest domyślnie włączone, może mieć wpływ na oczekiwany zaplanowany czas, wymagając, aby maszyna była w stanie bezczynności.
>
> W przypadku skanowania tygodniowego domyślnym zachowaniem na serwerze Windows Jest skanowanie poza automatyczną konserwacją, gdy maszyna jest bezczynna. Domyślnym ustawieniem Windows 10 i nowszych jest skanowanie podczas automatycznej konserwacji, gdy maszyna jest bezczynna. Aby zmienić to zachowanie, zmodyfikuj ustawienia, wyłączając **polecenie ScanOnlyIfIdle**, a następnie zdefiniuj harmonogram.

Aby uzyskać więcej informacji, zobacz [Temat Zarządzanie aktualizacjami ochrony, które mają być pobierane i stosowane](manage-protection-update-schedule-microsoft-defender-antivirus.md) , oraz [Zapobieganie lub zezwalanie użytkownikom na lokalne modyfikowanie ustawień zasad](configure-local-policy-overrides-microsoft-defender-antivirus.md) .

## <a name="group-policy-settings-for-scheduling-scans"></a>zasady grupy ustawienia planowania skanowania

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|:---|:---|:---|:---|
| Skanowania | Określanie typu skanowania do użycia w przypadku zaplanowanego skanowania | Szybkie skanowanie |
| Skanowania | Określ dzień tygodnia, w którym ma zostać uruchomione zaplanowane skanowanie | Określ dzień (lub nigdy), w którym ma zostać uruchomione skanowanie. | Nigdy nie |
| Skanowania | Określanie godziny uruchomienia zaplanowanego skanowania | Określ liczbę minut po północy (na przykład wprowadź **wartość 60** dla godziny 1:00). | 2:00. |
| Głównego | Losowe zaplanowanych godzin zadań |W Program antywirusowy Microsoft Defender losowe godziny rozpoczęcia skanowania do dowolnego interwału od 0 do 23 godzin. <p>W [programie SCEP](/mem/intune/protect/certificates-scep-configure) losowe skanowanie do dowolnego interwału plus lub minus 30 minut. Może to być przydatne w przypadku maszyn wirtualnych lub wdrożeń VDI. | Włączone |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>zasady grupy ustawienia planowania skanowania, gdy punkt końcowy nie jest używany

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|:---|:---|:---|:---|
| Skanowania | Uruchamianie zaplanowanego skanowania tylko wtedy, gdy komputer jest włączony, ale nie jest używany | Zaplanowane skanowanie nie zostanie uruchomione, chyba że komputer jest włączony, ale nie jest używany | Włączone |

> [!NOTE]
> Jeśli planujesz skanowanie w czasie, gdy punkty końcowe nie są używane, skany nie uwzględniają konfiguracji ograniczania przepustowości procesora CPU i w pełni wykorzystują dostępne zasoby, aby jak najszybciej ukończyć skanowanie.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>zasady grupy ustawienia planowania skanowania wymaganego do korygowania

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|---|---|---|---|
| Korygowania | Określ dzień tygodnia, w którym ma zostać uruchomione zaplanowane pełne skanowanie w celu ukończenia korygowania | Określ dzień (lub nigdy), w którym ma zostać uruchomione skanowanie. | Nigdy nie |
| Korygowania | Określ godzinę uruchomienia zaplanowanego pełnego skanowania w celu ukończenia korygowania | Określ liczbę minut po północy (na przykład wprowadź **wartość 60** dla godziny 1:00) | 2:00. |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>zasady grupy ustawienia planowania codziennych skanów

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|:---|:---|:---|:---|
| Skanowania | Określanie interwału do uruchamiania szybkich skanów dziennie | Określ, ile godzin powinno upłynąć przed następnym szybkim skanowaniem. Aby na przykład uruchamiać co dwie godziny, wprowadź **wartość 2** raz dziennie, wprowadź **wartość 24**. Wprowadź **wartość 0,** aby nigdy nie uruchamiać codziennego szybkiego skanowania. | Nigdy nie |
| Skanowania | Określanie czasu codziennego szybkiego skanowania | Określ liczbę minut po północy (na przykład wprowadź **wartość 60** dla godziny 1:00) | 2:00. |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>zasady grupy ustawienia planowania skanowania po aktualizacji ochrony

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane)|
|:---|:---|:---|:---|
| Aktualizacje podpisów | Włączanie skanowania po aktualizacji analizy zabezpieczeń | Skanowanie nastąpi natychmiast po pobraniu nowej aktualizacji ochrony | Włączone |

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)