---
title: Planowanie skanów antywirusowych przy użyciu zasady grupy
description: Konfigurowanie zasady grupy za pomocą programu antywirusowego
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
ms.openlocfilehash: 0e5e22b1c3f73f39ad65df39fd25e9b7b6e8a913
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "63007894"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>Planowanie skanów antywirusowych przy użyciu zasady grupy

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

W tym artykule opisano sposób konfigurowania zaplanowanych skanów przy zasady grupy. Aby dowiedzieć się więcej o planowaniu skanów i typach skanowania, zobacz Konfigurowanie zaplanowanego szybkiego lub pełnego Program antywirusowy Microsoft Defender [skanowania](schedule-antivirus-scans.md). 

## <a name="configure-antivirus-scans-using-group-policy"></a>Konfigurowanie skanów antywirusowych przy użyciu zasady grupy

1. Na komputerze zasady grupy do zarządzania składnikami,  \>  \> w Edytorze zasady grupy przejdź do strony Szablony administracyjne konfiguracji komputera **Windows składniki** \> **Program antywirusowy Microsoft Defender** \> **skanowanie**.

2. Kliknij prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

3. Określ ustawienia obiektu zasady grupy, a następnie wybierz przycisk **OK**. 

4. Powtórz kroki od 1 do 4 dla każdego ustawienia, które chcesz skonfigurować.

5. Wdeksuj zasady grupy obiekt w zwykły sposób. Jeśli potrzebujesz pomocy na temat zasady grupy obiektów, [zobacz Tworzenie zasady grupy obiektu](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object).

> [!NOTE]
> Podczas konfigurowania zaplanowanych skanów ustawienie Rozpocznij zaplanowane skanowanie tylko wtedy, gdy komputer jest **włączony, ale** nie jest w użyciu, które jest domyślnie włączone, może mieć wpływ na oczekiwaną zaplanowaną godzinę, wymagając najpierw bezczynności komputera.
>
> W przypadku skanów cotygodniowych zachowaniem na Windows Server jest skanowanie poza automatyczną konserwacją, gdy komputer jest bezczynny. Ustawieniem domyślnym Windows 10 i nowszych jest skanowanie podczas automatycznej konserwacji, gdy komputer jest bezczynny. Aby zmienić to zachowanie, zmodyfikuj ustawienia, wyłączając **scanOnlyIfIdle**, a następnie definiując harmonogram.

Aby uzyskać więcej informacji, zobacz temat Zarządzanie tym, kiedy [mają](manage-protection-update-schedule-microsoft-defender-antivirus.md) być pobierane i stosowane aktualizacje ochrony, oraz Uniemożliwianie użytkownikom lub zezwalanie na ich lokalne [modyfikowanie ustawień](configure-local-policy-overrides-microsoft-defender-antivirus.md) zasad.

## <a name="group-policy-settings-for-scheduling-scans"></a>zasady grupy dotyczące planowania skanów

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|:---|:---|:---|:---|
| Skanowanie | Określanie typu skanowania do użycia w zaplanowanym skanie | Szybkie skanowanie |
| Skanowanie | Określanie dnia tygodnia do uruchomienia zaplanowanego skanowania | Określ dzień (lub nigdy) do uruchomienia skanowania. | Nigdy |
| Skanowanie | Określanie czasu dnia do uruchomienia zaplanowanego skanowania | Określ liczbę minut po północy (na przykład wpisz **60** dla godziny 13). | 2:00 |
| Katalog główny | Randomizowanie zaplanowanych czasów zadań |W Program antywirusowy Microsoft Defender należy randomizować czas rozpoczęcia skanowania do dowolnego interwału z przedziału od 0 do 23 godzin. <p>W [danych SCEP](/mem/intune/protect/certificates-scep-configure) losowo skanuje do dowolnego interwału plus lub minus 30 minut. Może to być przydatne w przypadku maszyn wirtualnych lub wdrożeń VDI. | Włączone |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>zasady grupy dotyczące planowania skanów w przypadku, gdy punkt końcowy nie jest w użyciu

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|:---|:---|:---|:---|
| Skanowanie | Rozpoczynanie zaplanowanego skanowania tylko wtedy, gdy komputer jest wł., ale nie jest w użyciu | Zaplanowane skanowania nie będą uruchamiane, chyba że komputer jest uruchomiony, ale nie jest uruchomiony | Włączone |

> [!NOTE]
> W przypadku planowania skanowania w czasie, gdy punkty końcowe nie są w użyciu, skany nie korzystają z konfiguracji ograniczania procesora i w pełni korzystają z dostępnych zasobów, aby wykonać skanowanie tak szybko, jak to możliwe.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>zasady grupy dotyczące planowania skanów wymaganych w celu rozwiązywania problemów

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|---|---|---|---|
| Działania naprawcze | Określanie dnia tygodnia, w który ma zostać uruchomione zaplanowane pełne skanowanie w celu ukończenia działań naprawczych | Określ dzień (lub nigdy) do uruchomienia skanowania. | Nigdy |
| Działania naprawcze | Określanie czasu zaplanowanego pełnego skanowania w celu ukończenia działań naprawczych | Określ liczbę minut po północy (na przykład wpisz **60** dla godziny 1:00). | 2:00 |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>zasady grupy dotyczące planowania codziennych skanów

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane) |
|:---|:---|:---|:---|
| Skanowanie | Określanie interwału do uruchamiania szybkich skanów w ciągu dnia | Określ, ile godzin powinno upłynąć przed następnym szybkim skanowaniem. Aby na przykład uruchamiać co dwie godziny, wprowadź **wartość 2**, aby uruchamiać raz dziennie, wprowadź **wartość 24**. Wprowadź **wartość 0,** aby nigdy nie uruchamiać codziennego szybkiego skanowania. | Nigdy |
| Skanowanie | Określanie czasu dziennego szybkiego skanowania | Określ liczbę minut po północy (na przykład wpisz **60** dla godziny 1:00). | 2:00 |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>zasady grupy dotyczące planowania skanów po aktualizacjach ochrony

| Lokalizacja | Ustawienie | Opis | Ustawienie domyślne (jeśli nie jest skonfigurowane)|
|:---|:---|:---|:---|
| Aktualizacje podpisu | Włączanie skanowania po aktualizacji analizy zabezpieczeń | Skanowanie nastąpi natychmiast po pobraniu nowej aktualizacji ochrony | Włączone |

