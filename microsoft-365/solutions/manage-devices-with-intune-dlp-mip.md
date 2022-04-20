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
description: Zaimplementuj program Endpoint DLP, współpracując z zespołem ds. ochrony informacji i ładu w celu utworzenia zasad DLP dla organizacji.
ms.openlocfilehash: 3670dd7e204562d2974ae815babe541c608bfacf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943222"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>Krok 7. Wdrażanie funkcji ochrony przed utratą danych (DLP, data loss prevention) za pomocą funkcji ochrony informacji


Jeśli Organizacja już włożyła czas na zrozumienie danych, opracowanie schematu poufności danych i zastosowanie schematu, możesz być gotowy do rozszerzenia elementów tego schematu na punkty końcowe przy użyciu zasad ochrony przed utratą danych (DLP) usługi Microsoft Purview. 

Ochrona przed utratą danych punktu końcowego (Endpoint DLP) ma obecnie zastosowanie do:
- Windows 10, Windows 11
- macOS

Zasady DLP są tworzone przez zespół ds. ochrony informacji i ładu. Każda zasada DLP definiuje elementy w zestawie danych do wyszukania, takie jak poufne typy informacji lub etykiety, oraz sposób ochrony tych danych. 

Na przykład zasady DLP mogą wyszukiwać dane osobowe, takie jak numer paszportu. Zasady DLP będą zawierać warunek, który wyzwala zasady do podjęcia działań, na przykład gdy numer paszportu jest udostępniany osobom spoza organizacji. Można również skonfigurować akcję wykonywaną przez zasady. Opcje obejmują po prostu raportowanie akcji administratorom, ostrzeganie użytkowników, a nawet zapobieganie udostępnianiu danych.

Zasady DLP określają również lokalizację do zastosowania zasad, na przykład Exchange poczty e-mail i witryn SharePoint. Jedną z lokalizacji dostępnych dla administratorów są urządzenia. Jeśli wybrano urządzenia, możesz określić, do których użytkowników i grup użytkowników mają zostać zastosowane zasady. Można również określić użytkowników i grupy użytkowników do wykluczenia z zasad.

Jeśli twój zespół ds. ochrony informacji i ładu jest gotowy rozszerzyć zasady DLP na punkty końcowe, musisz je koordynować, aby włączyć urządzenia dla programu Endpoint DLP, przetestować i dostroić zasady DLP, wytrenować użytkowników i monitorować wyniki. 

![Kroki DLP punktu końcowego dla administratora urządzenia](../media/devices/endpoint-dlp-steps.png#lightbox)


Wykonaj poniższe kroki, aby współpracować z zespołem ds. ochrony informacji.


|Krok  |Opis  |
|---------|---------|
|1     |  [Dowiedz się więcej o zapobieganiu utracie danych punktu końcowego](../compliance/endpoint-dlp-learn-about.md).        |
|2     | Włącz urządzenia dla punktu końcowego DLP. Jeśli urządzenia zostały dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender, urządzenia są już włączone dla punktu końcowego DLP. Jeśli urządzenia nie są dołączone do usługi Defender for Endpoint, zobacz [Wprowadzenie z zapobieganiem utracie danych punktu końcowego](../compliance/endpoint-dlp-getting-started.md), aby uzyskać instrukcje.|
|3     |   Współpracuj z zespołem ds. ochrony informacji i nadzoru, aby definiować, testować i dostrajać zasady. Obejmuje to monitorowanie wyników. Zobacz następujące zasoby:<br>- [Korzystanie z ochrony przed utratą danych punktu końcowego](../compliance/endpoint-dlp-using.md)<br>- [Wyświetlanie raportów dotyczących zapobiegania utracie danych](../compliance/view-the-dlp-reports.md)      |
