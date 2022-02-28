---
title: Używanie Power Automate
description: Dowiedz się więcej o automatyzacji zasilania Microsoft 365 Defender procesów i używaniu ich.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, schemat, secops
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a707de259897080f8e726aed70618ea6505bdea6
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2021
ms.locfileid: "62989720"
---
# <a name="use-power-automate-in-microsoft-365-defender"></a>Używanie Power Automate w programie Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

> Chcesz doświadczyć Microsoft 365 Defender? Można go [ocenić w środowisku laboratoryjnym](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) lub [uruchomić projekt pilotażowy w środowisku produkcyjnym](m365d-pilot.md?ocid=cx-evalpilot).
>

Nowoczesne zespoły ds. zabezpieczeń (SecOps) wymagają automatyzacji, aby efektywnie pracować. Aby skupić się na chłoowaniu i badaniu rzeczywistych zagrożeń, zespoły secopsów używają Power Automate do sprawdzania listy alertów i eliminowania tych, które nie są zagrożeniami.  

## <a name="criteria-for-resolving-alerts"></a>Kryteria rozwiązywania alertów

- Włączona wiadomość o biurze dla użytkownika

- Użytkownik nie jest otagowany jako użytkownik o wysokim poziomie ryzyka

Jeśli oba te oznaczenia są prawdziwe, program SecOps oznacza alert jako legalną podróż i rozwiązuje go. Po rozpoznaniu alertu Microsoft Teams powiadomienie jest publikowane w tym programie. 

## <a name="connect-power-automate-to-microsoft-cloud-app-security"></a>Połączenie Power Automate do Microsoft Cloud App Security

Aby utworzyć automatyzację, potrzebny jest token API, aby można było połączyć Power Automate z Microsoft Cloud App Security (MCAS). 

1. Kliknij **Ustawienia**, wybierz pozycję **Rozszerzenia zabezpieczeń**, a następnie kliknij pozycję **Dodaj token** na karcie **Tokeny API**. 

2. Podaj nazwę tokenu, a następnie kliknij pozycję **Generuj**. Zapisz token, ponieważ będzie potrzebny później.

## <a name="create-an-automated-flow"></a>Tworzenie zautomatyzowanego przepływu

Aby uzyskać szczegółowy opis procesu krok po kroku, zobacz klip wideo [tutaj](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn). 

W tym klipie wideo opisano również, jak połączyć automatyczne zasilanie z programem MCAS. 

## <a name="related-information"></a>Informacje pokrewne

- [Integracja Power Automate z Microsoft Cloud App Security](/cloud-app-security/flow-integration)

- [Dokumentacja Power Automate microsoft Power Automate](/power-automate)
