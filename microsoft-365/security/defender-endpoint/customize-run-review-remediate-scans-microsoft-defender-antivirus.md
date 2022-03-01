---
title: Uruchamianie i dostosowywanie zaplanowanych skanów i skanowania na żądanie.
description: Dostosowywanie i inicjowanie Program antywirusowy Microsoft Defender skanowania punktów końcowych w sieci
keywords: skanowanie, planowanie, dostosowywanie, wykluczenia, wykluczanie plików, środki zaradcze, wyniki skanowania, kwarantanna, usuwanie zagrożeń, szybkie skanowanie, pełne skanowanie, Program antywirusowy Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9acac2868b0bd2449338f4a61f663d8cfe8a8ee4
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996801"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans-and-remediation"></a>Dostosowywanie, inicjowanie i przeglądanie wyników skanów Program antywirusowy Microsoft Defender środków zaradczych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Za pomocą zasady grupy, PowerShell i Windows Management Instrumentation (WMI) możesz Program antywirusowy Microsoft Defender skanów. 

## <a name="in-this-section"></a>W tej sekcji

Temat | Opis
---|---
[Konfigurowanie i sprawdzanie poprawności wykluczeń plików, folderów i procesów podczas Program antywirusowy Microsoft Defender skanowania](configure-exclusions-microsoft-defender-antivirus.md) | Możesz wykluczać pliki (w tym pliki zmodyfikowane przez określone procesy) i foldery ze skanów na żądanie, zaplanowanych skanów oraz zawsze on-real-protection monitoring and scanning
[Konfigurowanie Program antywirusowy Microsoft Defender opcji skanowania](configure-advanced-scan-types-microsoft-defender-antivirus.md) | Możesz skonfigurować Program antywirusowy Microsoft Defender przechowywania niektórych typów plików magazynu poczty e-mail, kopii zapasowej lub punktów ponownego przetwarzania oraz zarchiwizowane pliki (na przykład pliki .zip) w skanach. Możesz również włączyć skanowanie plików w sieci.
[Konfigurowanie działań naprawczych dla skanów](configure-remediation-microsoft-defender-antivirus.md) | Skonfiguruj, Program antywirusowy Microsoft Defender zrobić, gdy wykryje zagrożenie, i jak długo pliki poddane kwarantannie powinny być przechowywane w folderze kwarantanny.
[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Konfigurowanie skanowania cyklicznego (zaplanowanego), w tym ich uruchamiania i tego, czy są one uruchamiane jako pełne, czy szybkie
[Konfigurowanie i uruchamianie skanów](run-scan-microsoft-defender-antivirus.md) | Uruchamianie i konfigurowanie skanów na żądanie przy użyciu programu PowerShell, Windows Management Instrumentation lub indywidualnie na punktach końcowych za pomocą Zabezpieczenia Windows programu
[Przeglądanie wyników skanowania](review-scan-results-microsoft-defender-antivirus.md) | Przeglądanie wyników skanów przy użyciu aplikacji Microsoft Endpoint Configuration Manager, Microsoft Intune lub Zabezpieczenia Windows skanowania