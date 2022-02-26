---
title: Podręczniki oceniania alertów
description: Przejrzyj alerty dotyczące dobrze znanych ataków i podjąć zalecane działania w celu podjęcia działań naprawczych w celu ochrony sieci.
keywords: zdarzenia, alerty, badanie, analizowanie, odpowiedź, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
search.appverid: met150
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
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: fe0beb88cf613a5a966fc0534dfa4def715e81d2
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2022
ms.locfileid: "62974012"
---
# <a name="alert-grading-playbooks"></a>Podręczniki oceniania alertów

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Podręczniki oceniania alertów pozwalają na ich metody przejrzenie i szybkie klasyfikowanie w przypadku dobrze znanych ataków oraz podjęcia zalecanych działań w celu podjęcia działań naprawczych w celu ochrony sieci i ataków. Ocena alertów pomoże także w prawidłowym klasyfikowaniu ogólnego zdarzenia.

Jako analityk centrum zabezpieczeń (SOC, Security Operations Center), musisz mieć dostęp do portalu Microsoft 365 Defender, aby:

- Oceniaj i przejrzyj wygenerowane alerty i skojarzone zdarzenia. Zobacz [badanie alertów](investigate-alerts.md).
- Przeszukaj dane sygnału zabezpieczeń dzierżawcy i sprawdź, czy są to potencjalne zagrożenia i podejrzane działania. Zobacz [zaawansowane łowy](advanced-hunting-overview.md).

>[!Note]
>Możesz przekazać firmie Microsoft opinię na temat alertów dotyczących prawdziwych dodatnich i fałszywie dodatnich wyników, nie tylko na końcu badania, ale również w trakcie procesu badania. Może to ułatwić firmie Microsoft analizę i klasyfikację zdarzeń zabezpieczeń w przyszłości.
>

## <a name="microsoft-defender-for-office-365"></a>Program Microsoft Defender dla Office 365

[Usługa Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) chroni organizację przed złośliwymi zagrożeniami, które mogą być ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy. Program Defender for Office 365 oferuje:

- Zasady ochrony przed zagrożeniami

   Zdefiniuj zasady ochrony przed zagrożeniami, aby ustawić odpowiedni poziom ochrony dla organizacji.

- Raporty

  Wyświetlaj raporty w czasie rzeczywistym, aby monitorować program Defender Office 365 wydajności w organizacji.

- Możliwości analizy zagrożeń i reakcji

  Za pomocą narzędzi z krawędziami wiodącymi możesz badać zagrożenia, zrozumieć je, zasymulować i zapobiegać im.

- Funkcje automatycznego badania i odpowiedzi

  Oszczędzaj czas i wysiłku podczas badań i ograniczania zagrożeń.

Defender for Office 365 alerts can be classified as: 

- True positive (TP) for confirmed malicious activity. 
- Wartość fałszywie dodatnia (FP) dla potwierdzonej niech złośliwych aktywności.

>[!Note]
>Microsoft 365 Defender łączy [https://security.microsoft.com](https://security.microsoft.com) funkcje istniejących portali zabezpieczeń firmy Microsoft. W portalu Microsoft 365 Defender się szybki dostęp do informacji, prostsze układy i połączenie powiązanych informacji w celu łatwiejszego korzystania z nich.
>

## <a name="microsoft-defender-for-cloud-apps"></a>Usługa Microsoft Defender dla aplikacji w chmurze

[Microsoft Defender for Cloud Apps](/defender-cloud-apps) is a Cloud Access Security Broker (CASB) that supports various deployment modes including log collection, API connectors, and reverse proxy. Zapewnia on zaawansowaną widoczność, kontrolę nad podróżami danych oraz zaawansowane analizy w celu identyfikowania i zwalczania cyberataków we wszystkich usługach firmy Microsoft i innych firm w chmurze.

Usługa Defender for Cloud Apps natywnie integruje się z wiodącymi rozwiązaniami firmy Microsoft i została zaprojektowana z myślą o specjalistach bezpieczeństwa. Zapewnia ona proste wdrożenie, scentralizowane zarządzanie i innowacyjne funkcje automatyzacji.

Usługa Defender for Cloud Apps framework oferuje możliwość ochrony sieci przed cyberatakami i anomaliami, wykrywa nietypowe zachowanie w aplikacjach w chmurze w celu zidentyfikowania oprogramowania wymuszającego okup, naruszonych użytkowników lub aplikacji zaatakowanych przez oszustów. Umożliwia on analizę użycia wysokiego ryzyka i może automatycznie rekultywować w celu ograniczenia tego ryzyka do organizacji.

Alerty usługi Defender dla aplikacji w chmurze można sklasyfikować jako: 

- TP dla potwierdzonej złośliwej aktywności. 
- Chowaj wartości dodatnie (B-TP) dla podejrzanych, ale nie złośliwych działań, takich jak test penetracyjnych lub inne podejrzane działania autoryzowane. 
- FP dla potwierdzonej nie złośliwych aktywności.

## <a name="alert-grading-playbooks"></a>Podręczniki oceniania alertów

Zapoznaj się z tymi podręcznikami, aby dowiedzieć się, jak szybciej ocenić alerty dotyczące następujących zagrożeń:

- [Podejrzane działania w zakresie przesyłania dalej poczty e-mail](alert-grading-playbook-email-forwarding.md)
- [Podejrzane reguły manipulowania skrzynką odbiorczą](alert-grading-playbook-inbox-manipulation-rules.md)
- [Podejrzane reguły przesyłania dalej skrzynki odbiorczej](alert-grading-playbook-inbox-forwarding-rules.md)

Zobacz [Badanie alertów,](investigate-alerts.md) aby uzyskać informacje na temat sprawdzania alertów za pomocą Microsoft 365 Defender internetowego.
