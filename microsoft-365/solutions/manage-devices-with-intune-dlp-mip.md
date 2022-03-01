---
title: Krok 7. Wdrażanie funkcji ochrony przed utratą danych (DLP, data loss prevention) za pomocą funkcji ochrony informacji
ms.author: bcarter
author: brendacarter
f1.keywords:
- Endpoint dlp
- data loss prevention
- dlp policies
manager: dougeby
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- endpoint dlp
- data loss prevention
- dlp policies
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
description: Implementowanie zasad DLP punktów końcowych przez pracę ze swoim zespołem ds. ochrony informacji i zarządzania w celu tworzenia zasad DLP dla organizacji.
ms.openlocfilehash: c38171d790ffd376c7886da0547345cf7e74e36c
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010418"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>Krok 7. Wdrażanie funkcji ochrony przed utratą danych (DLP, data loss prevention) za pomocą funkcji ochrony informacji


Jeśli Twoja organizacja już nałożyła czas na zrozumienie Twoich danych, opracowanie schematu wrażliwości danych i zastosowanie schematu, być może możesz być gotowy do rozszerzenia elementów tego schematu na punkty końcowe przy użyciu zasad ochrony przed utratą danych (DLP). 

Ochrona przed utratą danych w punkcie końcowym firmy Microsoft (Endpoint DLP) obecnie dotyczy:
- Windows 10, Windows 11
- macOS

Zasady DLP są tworzone przez Twój zespół ds. ochrony informacji i zarządzania. Każda zasady DLP określają, które elementy w zestawie danych mają być szukaj, takie jak etykiety lub typy informacji poufnych, oraz sposób ochrony tych danych. 

Na przykład zasady DLP mogą szukać danych osobowych, takich jak numer paszportu. Zasady DLP będą zawierać warunek wyzwalacy działanie zasady, na przykład gdy numer paszportu jest udostępniany osobom spoza organizacji. Można również skonfigurować działanie, które będą podejmuje zasady. Zakres opcji to raportowanie akcji administratorom, ostrzeżenie dla użytkowników, a nawet zapobieganie udostępnianiu danych.

Zasady DLP określają również lokalizację, do których mają być stosowane zasady, na przykład adres e-mail Exchange i SharePoint witryn. Jedną z lokalizacji dostępnych dla administratorów są urządzenia. Jeśli wybrano opcję Urządzenia, możesz określić, do których użytkowników i grup użytkowników mają być stosowane zasady. Możesz także określić użytkowników i grupy użytkowników, które mają być wykluczane z zasad.

Jeśli Twój zespół ds. ochrony informacji i zarządzania jest gotowy do rozszerzenia zasad DLP na punkty końcowe, musisz skoordynować z nimi, aby umożliwić im obsługę funkcji DLP w punktach końcowych, testować i dostrajać zasady DLP, przeszkolić użytkowników i monitorować wyniki. 

![Endpoint DLP steps for the device admin](../media/devices/endpoint-dlp-steps.png#lightbox)

Jeśli ukończono [krok 2. Zarejestruj urządzenia do zarządzania i](manage-devices-with-intune-enroll.md) [krok 6. Zarejestruj urządzenia w u programie Defender for Endpoint, aby monitorować](manage-devices-with-intune-monitor-risk.md) ryzyko i zgodność urządzeń z planami bazowymi zabezpieczeń. Twoje urządzenia są już włączone pod względem funkcji DLP punktu końcowego. 


Aby współpracować z zespołem ds. ochrony informacji, należy wykonać poniższe czynności.


|Krok  |Opis  |
|---------|---------|
|1     |  [Dowiedz się więcej Microsoft 365 ochrony przed utratą danych w punktach końcowych](../compliance/endpoint-dlp-learn-about.md).        |
|2     | Włącz urządzenia dla funkcji DLP punktu końcowego. Jeśli urządzenia zostały włączone do programu Microsoft Defender dla punktu końcowego, dla tych urządzeń włączono już funkcję DLP punktu końcowego. Jeśli Twoje urządzenia nie są podłączone do usługi Defender for Endpoint, zobacz Wprowadzenie do ochrony przed utratą danych w punkcie [końcowym](../compliance/endpoint-dlp-getting-started.md) , aby uzyskać instrukcje.|
|3     |   We współpracy ze swoim zespołem ds. ochrony informacji i zarządzania informacjami możesz definiować, testować i dostrajać zasady. Obejmuje to monitorowanie wyników. Zobacz następujące zasoby:<br>- [Korzystanie z ochrony przed utratą danych w punkcie końcowym](../compliance/endpoint-dlp-using.md)<br>- [Wyświetlanie raportów w celu ochrony przed utratą danych](../compliance/view-the-dlp-reports.md)      |
|     |         |