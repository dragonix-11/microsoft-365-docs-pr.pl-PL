---
title: Krok nr 1. Planowanie na Microsoft 365 Defender operacji
description: Podstawowe informacje na temat planowania Microsoft 365 Defender gotowości podczas integrowania Microsoft 365 Defender z operacjami zabezpieczeń.
keywords: zdarzenia, alerty, badanie, korelacja, ataki, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki, zabezpieczenia, operacje zabezpieczeń, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: bb3759b673475690a49e0909e2da67644990950e
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010374"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>Krok nr 1. Planowanie na Microsoft 365 Defender operacji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Niezależnie od bieżącej terminu płatności za pomocą zabezpieczeń należy dostosować je do centrum operacji zabezpieczeń (SOC, Security Operations Center). Mimo że nie istnieje jeden model, który pasuje do każdej organizacji, istnieją pewne aspekty, które są najczęściej spotykane niż inne. 

W poniższych sekcjach opisano funkcje podstawowe soc.

## <a name="provide-situational-awareness-of-modern-threats"></a>Zapewnij sytą świadomość nowoczesnych zagrożeń

Zespół SOC przygotowuje się i poszuka nowych i przychodzących zagrożeń, aby współpracować z organizacją w celu ustanawiania środków zaradczych i odpowiedzi. Zespół soc powinien mieć pracowników, którzy są wysoce przeszkoleni w zakresie nowoczesnych metod ataków i technik oraz zrozumienia  wymusze zagrożeń. Udostępniona inteligencja i struktury zagrożeń, takie jak [Cyber Kill Chain](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) czy [MITRE ATT&CK](https://attack.mitre.org/) , mogą udostępnić Twoim pracownikom analityków zagrożeń i stropów zagrożeń.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>Zapewnianie reakcji pierwszego, drugiego i potencjalnie trzeciego poziomu na zdarzenia i zdarzenia cyberzagrożenia

SOC to front ochrony przed zdarzeniami i zdarzeniami zabezpieczającymi. Gdy zdarzenie, zagrożenie, atak, naruszenie zasad lub znalezienie inspekcji powoduje wyzwolenie alertu lub wywołania akcji, zespół SOC wykonuje ocenę w celu jej przechowania i zawierania lub eskalowania w celu badania. Dlatego responderzy pierwszej linii SOC muszą mieć wiedzę techniczną na temat zdarzeń i wskaźników zabezpieczeń.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>Scentralizowane monitorowanie i rejestrowanie źródeł zabezpieczeń organizacji 

Zazwyczaj podstawową funkcją zespołu SOC jest upewnianie się, że wszystkie urządzenia zabezpieczające, takie jak zapory, systemy ochrony przed nieuprawnianiem, systemy ochrony przed utratą danych, systemy Zarządzanie zagrożeniami i lukami i systemy tożsamości działają prawidłowo i są monitorowane. Zespoły SOC będą pracować z szerszymi operacjami sieci, takimi jak tożsamość, usługa DevOps, chmura, aplikacja, nauki o danych i inne zespoły biznesowe, w celu zapewnienia scentralizowanego i zabezpieczonego analizowania informacji zabezpieczających. Ponadto soc jest odpowiedzialny za prowadzenie dzienników danych w łatwo dostępnych i czytelnych formatach, co może obejmować analizowanie i normalizowanie różnych formatów.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>Ustanawianie gotowości operacyjnej zespołu w kolorze czerwonym, niebieskim i fioletowym

Każdy zespół soc powinien przetestować jego przygotowanie na reagowanie na incydenty cyberataczne. Testy można wykonać za pomocą ćwiczeń, takich jak pierwsze miejsce na tabeli, oraz ćwiczenia z różnymi osobami w it, zabezpieczeniach i na poziomie biznesowym. Indywidualne zespoły ćwiczeń są tworzone na podstawie ról reprezentacyjnych i pełnią rolę defendera (Niebieski zespół), atakującego (Czerwony zespół) lub jako obserwatorzy szukający metod i technik zarówno zespołów niebieskich, jak i czerwonych poprzez silne i wytęg, które zostaną odkryte podczas ćwiczeń (Purple Team).

## <a name="next-step"></a>Następny krok

[Krok 2. Przeprowadzanie oceny gotowości integracji soc przy użyciu struktury zerowego zaufania](integrate-microsoft-365-defender-secops-readiness.md)
