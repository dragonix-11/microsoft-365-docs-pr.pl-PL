---
title: Uruchamianie i dostosowywanie zaplanowanych skanów i skanowania na żądanie
description: Dostosowywanie i inicjowanie Program antywirusowy Microsoft Defender skanowania punktów końcowych w całej sieci.
keywords: skanowanie, planowanie, dostosowywanie, wykluczenia, wykluczanie plików, środki zaradcze, wyniki skanowania, kwarantanna, usuwanie zagrożeń, szybkie skanowanie, pełne skanowanie, Program antywirusowy Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: f3e0cc7ffccf02e24b9746d539a44d3a72810ead
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2021
ms.locfileid: "62959206"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans--remediation"></a>Dostosowywanie, inicjowanie i przeglądanie wyników Program antywirusowy Microsoft Defender zaradczych i & działania naprawcze

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/)

Za pomocą zasady grupy, PowerShell i Windows Management Instrumentation (WMI) możesz skonfigurować Program antywirusowy Microsoft Defender skanów. 

## <a name="in-this-section"></a>W tej sekcji

| Artykuł | Opis |
|:---|:---|
|[Konfigurowanie i sprawdzanie poprawności wykluczeń plików, folderów i procesów podczas Program antywirusowy Microsoft Defender skanowania](configure-exclusions-microsoft-defender-antivirus.md) | Możesz wykluczać pliki (w tym pliki zmodyfikowane przez określone procesy) i foldery ze skanów na żądanie, zaplanowanych skanów oraz zawsze on-real-protection monitoring and scanning |
|[Konfigurowanie Program antywirusowy Microsoft Defender opcji skanowania](configure-advanced-scan-types-microsoft-defender-antivirus.md) | W skanach można Program antywirusowy Microsoft Defender uwzględnić określone typy plików magazynu poczty e-mail, punkty kopii zapasowej lub wymiany wiadomości oraz zarchiwizowane pliki (na przykład pliki .zip). Możesz również włączyć skanowanie plików w sieci. |
|[Konfigurowanie działań naprawczych dla skanów](configure-remediation-microsoft-defender-antivirus.md) | Skonfiguruj, Program antywirusowy Microsoft Defender zrobić, gdy wykryje zagrożenie, i jak długo pliki poddane kwarantannie powinny być przechowywane w folderze kwarantanny. |
|[Konfigurowanie zaplanowanych skanów](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | Konfigurowanie skanowania cyklicznego (zaplanowanego), w tym ich uruchamiania i tego, czy są one uruchamiane jako pełne, czy szybkie |
|[Konfigurowanie i uruchamianie skanów](run-scan-microsoft-defender-antivirus.md) | Uruchamianie i konfigurowanie skanów na żądanie przy użyciu programu PowerShell, Windows Management Instrumentation lub indywidualnie na punktach końcowych za pomocą Zabezpieczenia Windows aplikacji |
|[Przeglądanie wyników skanowania](review-scan-results-microsoft-defender-antivirus.md) | Przeglądanie wyników skanów za pomocą Microsoft Endpoint Configuration Manager, Microsoft Intune lub aplikacji Zabezpieczenia Windows skanowania |