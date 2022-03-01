---
title: Rozwiązywanie problemów z regułami ograniczania powierzchni ataków
description: Zasoby i przykładowy kod do rozwiązywania problemów związanych z regułami ograniczania powierzchni ataków w programie Microsoft Defender for Endpoint.
keywords: troubleshoot, error, fix, windows defender eg, asr, rules, hips, troubleshoot, audit, exclusion, false positive, broken, blocking, Microsoft Defender for Endpoint
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.date: 03/27/2019
ms.reviewer: ''
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: c503c3ed4cfea4ed0645cf18a9c9bf4ebe4a5ade
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014692"
---
# <a name="troubleshoot-attack-surface-reduction-rules"></a>Rozwiązywanie problemów z regułami zmniejszania powierzchni ataków

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Podczas używania [reguł zmniejszania powierzchni ataków](attack-surface-reduction.md) mogą wystąpić problemy, takie jak:

- Reguła blokuje plik, proces lub wykonuje inną akcję, która nie powinna (wynik fałszywie dodatni)
- Reguła nie działa zgodnie z opisem ani nie blokuje pliku lub procesu, który powinien (wynik fałszywie ujemny)

Rozwiązywanie tych problemów można rozwiązać w czterech krokach:

1. [Potwierdź wymagania wstępne](#confirm-prerequisites)
2. [Testowanie reguły przy użyciu trybu inspekcji](#use-audit-mode-to-test-the-rule)
3. [Dodawanie wykluczeń określonej reguły](#add-exclusions-for-a-false-positive) (dla wyników fałszywie dodatnich)
4. [Przesyłanie dzienników pomocy technicznej](#collect-diagnostic-data-for-file-submissions)

## <a name="confirm-prerequisites"></a>Potwierdź wymagania wstępne

Reguły zmniejszania powierzchni ataków będą działać tylko na urządzeniach z następującymi warunkami:

- Punkty końcowe działają Windows 10 Enterprise wersji 1709 (znanej również jako Aktualizacja Fall Creators Update).

- Punkty końcowe są używania Program antywirusowy Microsoft Defender jako jedynej aplikacji ochrony antywirusowej. [Korzystanie z dowolnej innej aplikacji antywirusowej spowoduje, Program antywirusowy Microsoft Defender ją wyłączyć](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

- [Jest włączona ochrona w](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) czasie rzeczywistym.

- Tryb inspekcji nie jest włączony. Użyj zasady grupy, aby ustawić dla reguły wartość **Wyłączone** (wartość **: 0**), jak opisano w tece [Włączanie reguł zmniejszania powierzchni ataków](enable-attack-surface-reduction.md).

Jeśli wszystkie te wymagania wstępne zostały spełnione, przejdź do następnego kroku w celu przetestowania reguły w trybie inspekcji.

## <a name="use-audit-mode-to-test-the-rule"></a>Testowanie reguły przy użyciu trybu inspekcji

Możesz odwiedzić witrynę internetową testów Windows Defender w witrynie [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby sprawdzić, czy reguły ograniczania powierzchni ataków na ogół działają dla wstępnie skonfigurowanych procesów i scenariuszy na urządzeniu, lub możesz użyć trybu inspekcji, który umożliwia raportowanie tylko reguł.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

Postępuj zgodnie z tymi instrukcjami w używanie narzędzia [pokazowego](evaluate-attack-surface-reduction.md) , aby zobaczyć, jak działają reguły ograniczania powierzchni ataków, aby przetestować określoną regułę, z jaką napotykasz problemy.

1. Włącz tryb inspekcji dla określonej reguły, którą chcesz przetestować. Użyj zasady grupy, aby ustawić dla reguły tryb **inspekcji (wartość****: 2**), jak opisano w tece Włączanie [reguł zmniejszania powierzchni ataków](enable-attack-surface-reduction.md). Tryb inspekcji umożliwia  reguła zgłaszanie pliku lub procesu, ale nadal pozwala na jego uruchamianie.

2. Wykonywanie czynności powodującej problem (na przykład otwarcie lub wykonanie pliku lub procesu, który powinien zostać zablokowany, ale jest dozwolony).

3. [Przejrzyj dzienniki zdarzeń ograniczania](attack-surface-reduction.md) powierzchni ataków, aby sprawdzić, czy reguła nie zablokowałaby pliku lub procesu, jeśli dla reguły ustawiono opcję **Włączone**.

Jeśli reguła nie blokuje pliku ani procesu, który powinien zostać zablokowany, najpierw sprawdź, czy jest włączony tryb inspekcji.

Być może tryb inspekcji został włączony do testowania innej funkcji lub przez zautomatyzowany skrypt programu PowerShell i mógł nie zostać wyłączony po ukończeniu testów.

Jeśli przetestowano regułę za pomocą narzędzia pokazowego i trybu inspekcji, a reguły ograniczania powierzchni ataków działają we wstępnie skonfigurowanych scenariuszach, ale reguła nie działa zgodnie z oczekiwaniami, przejdź do jednej z poniższych sekcji w zależności od sytuacji:

1. Jeśli reguła ograniczania powierzchni ataków blokuje element, który nie powinien być blokowany (nazywany również wynikami fałszywie dodatnimi), możesz najpierw dodać wykluczenie reguły ograniczania powierzchni [ataków](#add-exclusions-for-a-false-positive).

2. Jeśli reguła zmniejszania powierzchni ataków nie blokuje czegoś, co powinna zablokować (znana również jako wynik fałszywie ujemny), możesz przejść od razu do ostatniego [kroku,](#collect-diagnostic-data-for-file-submissions) zbierając dane diagnostyczne i przesyłając problem do nas.

## <a name="add-exclusions-for-a-false-positive"></a>Dodawanie wykluczeń dla wyników fałszywie dodatnich

Jeśli reguła ograniczania powierzchni ataków blokuje coś, co nie powinno być blokowane (nazywane również wynikami fałszywie dodatnimi), możesz dodać wykluczenia, aby zapobiec ocenianiu wykluczanych plików lub folderów przez reguły ograniczania powierzchni ataków.

Aby dodać wykluczenie, zobacz [Dostosowywanie zmniejszania powierzchni ataków](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules).

> [!IMPORTANT]
> Można określać poszczególne pliki i foldery do wykluczenia, ale nie można określać poszczególnych reguł.
> Oznacza to, że wszelkie pliki i foldery wykluczonych zostaną wykluczone ze wszystkich reguł asr.

## <a name="report-a-false-positive-or-false-negative"></a>Zgłaszanie wyników fałszywie dodatnich lub ujemnych

Formularz przesyłania [Windows Defender analizy](https://www.microsoft.com/wdsi/filesubmission) zabezpieczeń sieci Web służy do zgłaszania wyników fałszywie ujemnych lub fałszywie dodatnich w celu ochrony sieci. W przypadku Windows E5 możesz także podać [link do dowolnego skojarzonego alertu](alerts-queue.md).

## <a name="collect-diagnostic-data-for-file-submissions"></a>Zbieranie danych diagnostycznych dla przesyłania plików

Podczas zgłaszania problemu związanego z regułami zmniejszania powierzchni ataków pojawia się prośba o zbieranie i przesyłanie danych diagnostycznych, które mogą być używane przez zespoły pomocy technicznej i inżynierów firmy Microsoft w celu rozwiązywania problemów.

1. Otwórz wiersz polecenia z podwyższonym poziomem uprawnień i zmień go na Windows Defender wiersza:

   ```console
   cd "c:\program files\windows defender"
   ```

2. Uruchom to polecenie, aby wygenerować dzienniki diagnostyczne:

   ```console
   mpcmdrun -getfiles
   ```

3. Domyślnie są one zapisywane w `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`. Dołącz plik do formularza przesyłania.

## <a name="related-articles"></a>Artykuły pokrewne

- [Reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction.md)
- [Włączanie reguł ograniczania powierzchni ataków](enable-attack-surface-reduction.md)
- [Ocenianie reguł zmniejszania powierzchni ataków](evaluate-attack-surface-reduction.md)
