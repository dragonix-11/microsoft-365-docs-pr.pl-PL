---
title: Co nowego w programie Microsoft Defender dla systemu Office 365
description: Dowiedz się więcej o nowych funkcjach dostępnych w najnowszej wersji programu Microsoft Defender dla Office 365.
keywords: co nowego w programie Microsoft Defender dla Office 365, ga, ogólnie dostępne, funkcje, dostępne, nowe
search.appverid: met150
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.date: 12/03/2021
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5ae288b2d7dbaec9f66a501f7177741a5df48d0c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323951"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>Co nowego w programie Microsoft Defender dla systemu Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy:**

- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ten artykuł zawiera listę nowych funkcji w najnowszej wersji programu Microsoft Defender dla Office 365. Funkcje, które są obecnie w wersji preview, są oznaczane **(wersja zapoznawcza)**.

Dowiedz się więcej, oglądając [ten klip wideo](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).

> [!TIP]
> Nie masz jeszcze programu Microsoft Defender Office 365? [Skontaktuj się ze sprzedażą, aby rozpocząć okres próbny](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html).

Aby uzyskać więcej informacji o nowościach w innych produktach zabezpieczeń Microsoft Defender, zobacz:

- [Co nowego w programie Microsoft 365 Defender](../defender/whats-new.md)
- [Co nowego w programie Microsoft Defender dla punktu końcowego](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Co nowego w programie Microsoft Defender dla tożsamości](/defender-for-identity/whats-new)
- [Co nowego w programie Microsoft Cloud App Security](/cloud-app-security/release-notes)

## <a name="march-2022"></a>Marzec 2022 r.

- [Usprawnione środowisko przesyłania w programie Microsoft Defender Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/streamlining-the-submissions-experience-in-microsoft-defender/ba-p/3152080): Wprowadzenie nowego, ujednoliconego i usprawnionego procesu przesyłania w celu uproszczenia pracy.


## <a name="january-2022"></a>Styczeń 2022

- [Zaktualizowano środowisko](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/updated-hunting-and-investigation-experiences-for-microsoft/ba-p/3002015) wyszukiwania i badania dla programu Microsoft Defender dla programu Office 365: wprowadzenie panelu podsumowania wiadomości e-mail do obsługi doświadczeń w programie Defender Office 365 oraz aktualizacji obsługi eksploratora zagrożeń i wykrywania w czasie rzeczywistym.


## <a name="october-2021"></a>Październik 2021

- [Rozszerzenie DKIM zaawansowanego zarządzania](configure-advanced-delivery.md) dostarczaniem: Dodano obsługę wprowadzania domeny DKIM w ramach konfiguracji symulacyjnej wyłudzania informacji innej firmy.
- [Domyślnie bezpieczne](secure-by-default.md): Rozszerzone zabezpieczenie domyślnie dla Exchange przepływu poczty e-mail (nazywane również regułami transportu).

## <a name="september-2021"></a>Wrzesień 2021

- [Ulepszone środowisko raportowania w programie Defender dla Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/improving-the-reporting-experience-in-microsoft-defender-for/ba-p/2760898)
- [Zasady kwarantanny](quarantine-policies.md): Administratorzy mogą skonfigurować szczegółową kontrolę nad dostępem adresatów do wiadomości poddanych kwarantannie i dostosowywać powiadomienia użytkowników końcowych o spamie.
  - [Klip wideo: środowisko administratora](https://youtu.be/vnar4HowfpY)
  - [Klip wideo: środowisko użytkownika końcowego](https://youtu.be/s-vozLO43rI)
  - Inne nowe funkcje dostępne w kwarantannie opisano w tym wpisie w blogu: [Upraszczanie obsługi kwarantanny](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience/ba-p/2676388).
- Domyślnie zaczyna się przekierowywanie portalu, przekierowywanie użytkowników z zabezpieczeń i zgodności & do Microsoft 365 Defender<https://security.microsoft.com>. Aby uzyskać więcej informacji na ten temat, zobacz: [Przekierowywanie kont z Office 365 zabezpieczeń i zgodności do Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection)

## <a name="august-2021"></a>Sierpień 2021

- [Recenzja dla zgłoszonych wiadomości](admin-review-reported-message.md) przez administratora: Po przejrzeniu zgłoszonych wiadomości administratorzy mogą wysyłać te wiadomości z szablonami z powrotem do użytkowników końcowych. Szablony można dostosować do potrzeb organizacji, a także na podstawie werdyktów administratora.
- [Opcja Dodaj umożliwia na](manage-tenant-allows.md) liście zezwalania/blokowania dzierżawy: Teraz możesz dodawać wpisy zezwalania do listy zezwalania/blokowania dzierżawy, jeśli zablokowana wiadomość została przesłana w ramach procesu przesyłania przez administratora. W zależności od rodzaju bloku przesłany adres URL, plik i/lub zezwalanie nadawcy zostaną dodane do listy zezwalania/blokowania dzierżawy. W większości przypadków zezwala się na dodanie systemu w sposób naturalny, jeśli jest to uzasadnione. W niektórych przypadkach zezwala na to firma Microsoft.

## <a name="july-2021"></a>Lipiec 2021

- [Ulepszenia analizy poczty e-mail w zautomatyzowanych badaniach](email-analysis-investigations.md)
- [Dostarczanie zaawansowane](configure-advanced-delivery.md): Wprowadzenie nowej funkcji konfigurowania innej firmy do obsługi symulacyjnych wyłudzania informacji dla użytkowników i niefiltrowanych wiadomości do skrzynek pocztowych operacji zabezpieczeń.
- [Sejf linków dla Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- Nowe zasady alertów dotyczące następujących scenariuszy: naruszone skrzynki pocztowe, wyłudzanie informacji za pośrednictwem formularzy, złośliwe wiadomości dostarczane z powodu zastępować i zaokrąglania zap
  - Podejrzane działania w zakresie przesyłania dalej poczty e-mail
  - Użytkownik ograniczony do udostępniania formularzy i zbierania odpowiedzi
  - Formularz zablokowany ze względu na potencjalną próbę wyłudzenia informacji
  - Formularz oflagowany i potwierdzony jako wyłudzanie informacji
  - [Nowe zasady alertów dotyczące zap](../../compliance/new-defender-alert-policies.md)
- Alerty usługi Microsoft Defender dla Office 365 są teraz zintegrowane z usługą Microsoft 365 Defender — Microsoft 365 Defender z ujednoliconą kolejką alertów i kolejką [ujednoliconych alertów](../defender/investigate-alerts.md)
- [](user-tags.md) Tagi użytkowników są teraz zintegrowane z usługą Microsoft Defender dla środowiska alertów programu Office 365, w tym: kolejką alertów i szczegółami w uchcie zabezpieczeń & zgodności programu Office 365 oraz określanie zakresu niestandardowych zasad alertów dla tagów użytkowników w celu utworzenia ukierunkowanych zasad alertów.
  - Tagi są również dostępne w kolejce alertów ujednoliconych w portalu usługi Microsoft 365 Defender (Microsoft Defender for Office 365 Plan 2)

## <a name="june-2021"></a>Czerwiec 2021

- Ustawienie Nowy pierwszy kontakt porada dotycząca bezpieczeństwa w ramach zasad ochrony przed wyłudzaniem informacji. Ten porada dotycząca bezpieczeństwa jest wyświetlany, gdy adresaci po raz pierwszy otrzymają wiadomość e-mail od nadawcy lub nie często otrzymują wiadomości e-mail od tego nadawcy. Aby uzyskać więcej informacji na temat tego ustawienia i sposobu jego konfigurowania, zobacz następujące artykuły:
  - [Pierwszy kontakt porada dotycząca bezpieczeństwa](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP](configure-anti-phishing-policies-eop.md)
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>Kwiecień 2021 r.

- [Strona jednostki](mdo-email-entity-page.md) poczty e-mail: ujednolicony widok wiadomości e-mail o 360 stopni z wzbogaceniem informacji na temat zagrożeń, uwierzytelniania i wykrywania, szczegółów detonacji oraz zupełnie nowego interfejsu podglądu wiadomości e-mail.
- [Office 365 interfejsu API](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events) zarządzania: Aktualizacje zdarzeń emailEvents (RecordType 28) w celu dodania akcji dostarczania, oryginalnych i najnowszych lokalizacji dostarczania oraz zaktualizowanych szczegółów wykrywania.
- [Analiza zagrożeń dla usługi Defender dla Office 365](/microsoft-365/security/defender/threat-analytics): Wyświetlaj aktywne śledzenia zagrożeń, popularne techniki i powierzchnie ataków oraz rozbudowane raporty od firmy Microsoft dotyczące trwających kampanii.

## <a name="februarymarch-2021"></a>Luty/marzec 2021 r.

- Integracja identyfikatora alertu (wyszukiwanie przy użyciu identyfikatora alertu i nawigacji Alert-Explorer) w [środowiskach pracy myśliwskiej](threat-explorer.md)
- Zwiększenie limitów eksportu rekordów z 9990 do 200 000 podczas pracy [myśliwskiej](threat-explorer.md)
- Rozszerzenie zakresu przechowywania danych w Eksploratorze (i wykrywania w czasie rzeczywistym) i limitu wyszukiwania dla dzierżawców wersji próbnych z 7 (poprzedni limit) do 30 dni [](threat-explorer.md) podczas pracy chłoń
- Nowe tabele wyszukiwania o nazwach **Personifikowany** domena i **Personifikowany** użytkownik w Eksploratorze (i wykrywanie w czasie rzeczywistym) w celu wyszukiwania ataków personifikacji na chronionych użytkownikach lub domenach. Aby uzyskać więcej informacji, zobacz [szczegóły](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains). (Microsoft Defender dla Office 365 Plan 1 lub Plan 2)


## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender dla Office 365 Plan 1 i Plan 2

Czy wiesz, że program Microsoft Defender dla Office 365 jest dostępny w dwóch planach? [Dowiedz się więcej o tym, co obejmuje każdy plan](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="see-also"></a>Zobacz też

[Microsoft 365 przewodnik](https://www.microsoft.com/microsoft-365/roadmap)

[Opis usługi Microsoft Defender Office 365 usługi](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
