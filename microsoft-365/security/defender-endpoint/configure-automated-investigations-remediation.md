---
title: Konfigurowanie zautomatyzowanych możliwości badania i rozwiązywania problemów
description: Skonfiguruj funkcje automatycznego badania i rozwiązywania problemów w programie Microsoft Defender for Endpoint.
keywords: konfigurowanie, konfigurowanie, zautomatyzowane, badanie, wykrywanie, alerty, działania naprawcze, reagowanie
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
ms.date: 01/27/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.openlocfilehash: f8416d480731c133e93a0a6e22e5b5b32913ba57
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327619"
---
# <a name="configure-automated-investigation-and-remediation-capabilities-in-microsoft-defender-for-endpoint"></a>Konfigurowanie funkcji automatycznego badania i rozwiązywania problemów w programie Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Jeśli Twoja organizacja używa programu [Microsoft Defender for Endpoint](/windows/security/threat-protection/) (Defender for Endpoint), automatyczne [badania](/microsoft-365/security/defender-endpoint/automated-investigations) i funkcje rozwiązywania problemów mogą zaoszczędzić czas i nakład pracy zespołowej związanej z operacjami zabezpieczeń. Jak opisano w [tym wpisie](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/enhance-your-soc-with-microsoft-defender-atp-automatic/ba-p/848946) w blogu, te funkcje naśladowały idealne kroki, które analityk zabezpieczeń podejmuje w celu zbadania i rozwiązania zagrożeń. [Dowiedz się więcej o zautomatyzowanym śledztwie i rozwiązywaniu problemów](/microsoft-365/security/defender-endpoint/automated-investigations).

Aby skonfigurować zautomatyzowane badania i rozwiązywanie problemów:

1. [Włącz funkcje](#turn-on-automated-investigation-and-remediation). i
2. [Skonfiguruj grupy urządzeń](#set-up-device-groups).

## <a name="turn-on-automated-investigation-and-remediation"></a>Włączanie automatycznego badania i rozwiązywania problemów

1. Jako administrator globalny lub administrator zabezpieczeń przejdź do portalu Microsoft 365 Defender (<https://security.microsoft.com>) i zaloguj się.
2. W okienku nawigacji wybierz pozycję **Ustawienia**.
3. W sekcji **Ogólne** wybierz pozycję **Funkcje zaawansowane**.
4. Włącz zarówno automatyczne **rozwiązywanie alertów,** **jak i automatyczne rozwiązywanie problemów**.

## <a name="set-up-device-groups"></a>Konfigurowanie grup urządzeń

1. W portalu Microsoft 365 Defender (<https://security.microsoft.com>) na **stronie Ustawienia** w **obszarze** Uprawnienia wybierz **pozycję Grupy urządzeń**.
2. Wybierz **pozycję + Dodaj grupę urządzeń**.
3. Utwórz co najmniej jedną grupę urządzeń w następujący sposób:
   - Określ nazwę i opis grupy urządzeń.
   - Z listy **Poziom automatyzacji** wybierz poziom, na przykład Pełny **— automatycznie reagotuj zagrożenia**. Poziom automatyzacji określa, czy działania naprawcze są podejmowane automatycznie, czy tylko po zatwierdzeniu. Aby dowiedzieć się więcej, zobacz [Poziomy automatyzacji w automatycznym śledztwie i rozwiązywaniu problemów](automation-levels.md).
   - W sekcji **Członkowie** określ i uwzględnij urządzenia przy użyciu jednego lub większej liczby warunków.
   - Na **karcie Dostęp użytkowników** wybierz grupy Azure Active Directory, [](/azure/active-directory/fundamentals/active-directory-manage-groups?context=azure/active-directory/users-groups-roles/context/ugr-context) które powinny mieć dostęp do grupy urządzeń, które tworzysz.
4. Po **zakończeniu** konfigurowania grupy urządzeń wybierz pozycję Gotowe.

## <a name="next-steps"></a>Następne kroki

- [Odwiedź Centrum akcji, aby wyświetlić oczekujące i ukończone akcje naprawcze](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
- [Przeglądanie i zatwierdzanie oczekujących akcji](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

## <a name="see-also"></a>Zobacz też

- [Adres dodatnich/ujemnych wyników fałszywie dodatnich w programie Microsoft Defender dla punktu końcowego](defender-endpoint-false-positives-negatives.md)
