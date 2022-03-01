---
title: Konfigurowanie wykluczeń dla Program antywirusowy Microsoft Defender skanowania
description: Możesz wykluczyć pliki (w tym pliki zmodyfikowane przez określone procesy) i foldery z zeskanowanych przez Program antywirusowy Microsoft Defender. Sprawdź poprawność wykluczeń za pomocą programu PowerShell.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.technology: mde
ms.audience: ITPro
ms.topic: how-to
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 5a26951535b6e2197d8ada45b2108e62f15fda03
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009579"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Konfigurowanie i weryfikowanie wykluczeń Program antywirusowy Microsoft Defender skanowania

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


W skanach możesz wykluczyć określone pliki, foldery, procesy oraz pliki otwierane przy Program antywirusowy Microsoft Defender procesach. Takie wykluczenia [mają zastosowanie do](scheduled-catch-up-scans-microsoft-defender-antivirus.md) zaplanowanych skanów, skanów [na](run-scan-microsoft-defender-antivirus.md) żądanie oraz zawsze [w czasie rzeczywistym ochrony i monitorowania](configure-real-time-protection-microsoft-defender-antivirus.md). Wykluczenia dotyczące otwieranych plików przetwarzanych mają zastosowanie tylko do ochrony w czasie rzeczywistym.

## <a name="configure-and-validate-exclusions"></a>Konfigurowanie i weryfikowanie wykluczeń

Aby skonfigurować i zweryfikować wykluczenia, zobacz następujące informacje:

- [Konfigurowanie i sprawdzanie poprawności wykluczeń na podstawie nazwy pliku, rozszerzenia i lokalizacji folderu](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Możesz wykluczyć pliki z Program antywirusowy Microsoft Defender na podstawie ich rozszerzenia pliku, nazwy pliku lub lokalizacji.

- [Konfigurowanie i weryfikowanie wykluczeń plików otwieranych przez procesy](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Możesz wykluczyć pliki ze skanów, które zostały otwarte w określonym procesie.

## <a name="recommendations-for-defining-exclusions"></a>Rekomendacje definiowania wykluczeń

> [!IMPORTANT]
> Program antywirusowy Microsoft Defender uwzględnia wiele automatycznych wykluczeń opartych na znanych zachowaniach systemu operacyjnego i typowych plikach zarządzania, takich jak używane w zarządzaniu przedsiębiorstwem, zarządzaniu bazami danych i innych scenariuszach i sytuacjach przedsiębiorstwa.
>
> Zdefiniowanie wykluczeń obniża ochronę oferowaną przez Program antywirusowy Microsoft Defender. Zawsze należy oceniać ryzyko związane z implementowanie wykluczeń, a nie uwzględniać tylko plików, które na pewno nie są złośliwe.

Podczas definiowania wykluczeń należy pamiętać o następujących kwestiach:

- Wykluczenia są technicznie przerwą w ochronie. Podczas definiowania wykluczeń rozważ wszystkie opcje. Inne opcje mogą być proste: upewnianie się, że wykluczona lokalizacja ma odpowiednie listy kontroli dostępu (ACL) lub ustawienie najpierw zasad w celu trybu inspekcji.

- Należy okresowo przeglądać wykluczenia. W ramach procesu sprawdzania sprawdź ponownie i ponownie wymudź środki zaradcze.

- Najlepiej unikać definiowania wykluczeń, mając na celu aktywne działania. Na przykład nie wykluczaj czegoś tylko dlatego, że uważasz, że może to stanowić problem w przyszłości. Wykluczenia należy stosować tylko w przypadku określonych problemów, takich jak problemy dotyczące wydajności lub zgodności aplikacji, których wykluczenia mogłyby zmniejszyć.

- Przejrzyj zmiany na liście wykluczeń i przejdę ich inspekcję. Zespół zabezpieczeń powinien zachować kontekst, dlaczego dodano pewne wyłączenie, aby uniknąć zamieszania w późniejszym czasie. Zespół zabezpieczeń powinien być w stanie udzielić szczegółowych odpowiedzi na pytania dotyczące tego, dlaczego istnieją wykluczenia.

## <a name="see-also"></a>Zobacz też

- [Program antywirusowy Microsoft Defender wykluczenia dotyczące Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Typowe błędy, których należy unikać podczas definiowania wykluczeń](common-exclusion-mistakes-microsoft-defender-antivirus.md)
