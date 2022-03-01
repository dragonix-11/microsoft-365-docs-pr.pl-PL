---
title: Szacowanie kontrolowanego dostępu do folderu
description: Zobacz, jak kontrolowany dostęp do folderów może pomóc chronić pliki przed  zmianą przez złośliwe aplikacje.
keywords: Exploit protection, windows 10, windows 11, windows defender, ransomware, protect, evaluate, test, demo, try
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365initiative-m365-defender
ms.date: ''
ms.openlocfilehash: 996a96f957d7446b0b951d4f1b3a34c822f64f49
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019373"
---
# <a name="evaluate-controlled-folder-access"></a>Szacowanie kontrolowanego dostępu do folderu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[Kontrolowany dostęp do folderów](controlled-folders.md) to funkcja, która pomaga chronić dokumenty i pliki przed modyfikacjami przez podejrzane lub złośliwe aplikacje. Kontrolowany dostęp do folderu jest obsługiwany na Windows Server 2019, Windows Server 2022, Windows 10 i Windows 11 klientów.

Jest to szczególnie przydatne w przypadku ochrony przed oprogramowaniem [wymuszającym okup](https://www.microsoft.com/wdsi/threats/ransomware) , który próbuje zaszyfrować pliki i trzymać ich u hosta.

Ten artykuł ułatwia ocenianie kontrolowanego dostępu do folderu. Wyjaśniono w nim, jak włączyć tryb inspekcji, aby przetestować tę funkcję bezpośrednio w organizacji.

> [!TIP]
> Możesz również odwiedzić witrynę internetową scenariusza pokazu programu Microsoft Defender for Endpoint [w witrynie demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) , aby sprawdzić, czy ta funkcja działa i jak działa.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="use-audit-mode-to-measure-impact"></a>Mierzenie wpływu za pomocą trybu inspekcji

Włącz kontrolowany dostęp do folderu w trybie inspekcji, aby zobaczyć, co  się działo, gdyby w pełni włączono tę funkcję. Przetestuj, jak ta funkcja będzie działać w Twojej organizacji, aby upewnić się, że nie wpływa ona na aplikacje biznesowe. Możesz również dowiedzieć się, ile podejrzanych prób modyfikacji pliku zazwyczaj odbywa się w określonym czasie.

Aby włączyć tryb inspekcji, użyj następującego polecenia cmdlet programu PowerShell:

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> Jeśli chcesz w pełni sprawdzić, jak kontrolowany dostęp do folderów będzie działać w Twojej organizacji, musisz użyć narzędzia do zarządzania w celu wdrożenia tego ustawienia na urządzeniach w Twojej sieci.
Ustawienia można także skonfigurować zasady grupy, Intune, zarządzania urządzeniami przenośnymi (MDM) lub programu Microsoft Endpoint Manager, zgodnie z opisem w głównym temacie dotyczącym dostępu do [folderu](controlled-folders.md).

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Przeglądanie zdarzeń kontrolowanego dostępu do folderu w Windows Zdarzeń

Następujące zdarzenia kontrolowanego dostępu do folderu są wyświetlane w podglądzie Windows zdarzeń w folderze Microsoft/Windows/Windows Defender/Operacyjne.

Identyfikator zdarzenia | Opis
-|-
 5007 | Zdarzenie w przypadku zmiany ustawień
 1124 | Zdarzenie kontrolowanego dostępu do folderu
 1123 | Zdarzenie zablokowanego dostępu do folderu

> [!TIP]
> Możesz skonfigurować subskrypcję usługi [Windows przesyłanie](/windows/win32/wec/setting-up-a-source-initiated-subscription) dalej zdarzeń, aby centralnie zbierać dzienniki. 

## <a name="customize-protected-folders-and-apps"></a>Dostosowywanie chronionych folderów i aplikacji

Podczas oceny można dodać foldery chronione do listy lub zezwolić określonym aplikacjom na modyfikowanie plików.

Zobacz [Chronienie ważnych folderów za](controlled-folders.md) pomocą kontrolowanego dostępu do folderów w celu skonfigurowania funkcji za pomocą narzędzi do zarządzania, takich zasady grupy, programu PowerShell i dostawców usług konfiguracji mdM.

## <a name="see-also"></a>Zobacz też

* [Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów](controlled-folders.md)
* [Szacowanie programu Microsoft Defender pod celu punktu końcowego](evaluate-mde.md)
* [Korzystanie z trybu inspekcji](audit-windows-defender.md)
