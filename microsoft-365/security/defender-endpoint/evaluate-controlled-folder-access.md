---
title: Oceń kontrolowany dostęp do folderu
description: Zobacz, jak kontrolowany dostęp do folderów może pomóc w ochronie plików przed zmianą przez złośliwe aplikacje.
keywords: Exploit protection, Windows 10, Windows 11, Windows Defender, ransomware, protect, evaluate, test, demo, try
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
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 4ccb91f0a8c181697eb525dd8f5576e6f6cdc0d1
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789827"
---
# <a name="evaluate-controlled-folder-access"></a>Oceń kontrolowany dostęp do folderu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[Kontrolowany dostęp do folderów](controlled-folders.md) to funkcja, która pomaga chronić dokumenty i pliki przed modyfikacją przez podejrzane lub złośliwe aplikacje. Kontrolowany dostęp do folderów jest obsługiwany na klientach Windows Server 2019, Windows Server 2022, Windows 10 i Windows 11.

Jest to szczególnie przydatne w ochronie przed [oprogramowaniem wymuszającym okup](https://www.microsoft.com/wdsi/threats/ransomware) , które próbuje zaszyfrować pliki i zatrzymać je jako zakładników.

Ten artykuł ułatwia ocenę kontrolowanego dostępu do folderów. Wyjaśniono w nim, jak włączyć tryb inspekcji, aby można było przetestować tę funkcję bezpośrednio w organizacji.

> [!TIP]
> Możesz również odwiedzić witrynę internetową Ochrona punktu końcowego w usłudze Microsoft Defender scenariusza demonstracyjnego pod adresem [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby potwierdzić, że funkcja działa i zobaczyć, jak działa.

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

## <a name="use-audit-mode-to-measure-impact"></a>Mierzenie wpływu przy użyciu trybu inspekcji

Włącz kontrolowany dostęp do folderu w trybie inspekcji, aby wyświetlić rekord tego, co *by* się stało, gdyby był w pełni włączony. Sprawdź, jak ta funkcja będzie działać w organizacji, aby upewnić się, że nie wpływa ona na aplikacje biznesowe. Możesz również poznać liczbę podejrzanych prób modyfikacji plików w określonym okresie.

Aby włączyć tryb inspekcji, użyj następującego polecenia cmdlet programu PowerShell:

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> Jeśli chcesz w pełni sprawdzić, jak kontrolowany dostęp do folderów będzie działać w organizacji, musisz użyć narzędzia do zarządzania, aby wdrożyć to ustawienie na urządzeniach w sieciach.
Do skonfigurowania i wdrożenia ustawienia można również użyć zasady grupy, Intune, zarządzania urządzeniami przenośnymi (MDM) lub Microsoft Endpoint Manager, zgodnie z opisem w [temacie dotyczącym dostępu do folderów kontrolowanych](controlled-folders.md).

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Przejrzyj zdarzenia dostępu do folderów kontrolowanych w Windows Podgląd zdarzeń

Następujące zdarzenia dostępu do folderów kontrolowanych są wyświetlane w Windows Podgląd zdarzeń w folderze Microsoft/Windows/Windows Defender/Operational.

Identyfikator zdarzenia | Opis
-|-
 5007 | Zdarzenie po zmianie ustawień
 1124 | Zdarzenie dostępu do kontrolowanego folderu z inspekcją
 1123 | Zablokowane zdarzenie dostępu do folderu kontrolowanego

> [!TIP]
> Możesz skonfigurować [subskrypcję usługi Windows Event Forwarding](/windows/win32/wec/setting-up-a-source-initiated-subscription) w celu centralnego zbierania dzienników. 

## <a name="customize-protected-folders-and-apps"></a>Dostosowywanie chronionych folderów i aplikacji

Podczas oceny możesz dodać do listy folderów chronionych lub zezwolić niektórym aplikacjom na modyfikowanie plików.

Zobacz [Protect important folders with controlled folder access](controlled-folders.md) for configuring the feature with management tools, including zasady grupy, PowerShell, and MDM configuration service providers (CSP).

## <a name="see-also"></a>Zobacz też

* [Ochrona ważnych folderów za pomocą kontrolowanego dostępu do folderów](controlled-folders.md)
* [Ocena ochrony punktu końcowego w usłudze Microsoft Defender](evaluate-mde.md)
* [Korzystanie z trybu inspekcji](audit-windows-defender.md)
