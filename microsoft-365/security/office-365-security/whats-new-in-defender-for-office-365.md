---
title: Co nowego w ochronie usługi Office 365 w usłudze Microsoft Defender?
description: Dowiedz się więcej o nowych funkcjach dostępnych w najnowszej wersji Ochrona usługi Office 365 w usłudze Microsoft Defender.
keywords: co nowego w Ochrona usługi Office 365 w usłudze Microsoft Defender, ga, ogólnie dostępne, możliwości, dostępne, nowe
search.appverid: met150
ms.sitesec: library
ms.pagetype: security
f1.keywords: NOCSH
ms.author: tracyp
author: msfttracyp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 82b23047b8013f9916168d46b5b595b326f6d1e5
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530537"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>Co nowego w ochronie usługi Office 365 w usłudze Microsoft Defender?

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy:**

- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ten artykuł zawiera listę nowych funkcji w najnowszej wersji Ochrona usługi Office 365 w usłudze Microsoft Defender. Funkcje, które są obecnie w wersji zapoznawczej, są oznaczane **(wersja zapoznawcza).**

Dowiedz się więcej, oglądając [ten film wideo](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).

Aby uzyskać więcej informacji na temat nowości w innych produktach zabezpieczeń usługi Microsoft Defender, zobacz:

- [Co nowego w usłudze Microsoft 365 Defender](../defender/whats-new.md)
- [Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [Co nowego w Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [Co nowego w Microsoft Cloud App Security](/cloud-app-security/release-notes)


## <a name="june-2022"></a>Czerwiec 2022

- [Fałszowanie umożliwia przesyłanie danych przez administratora](allow-block-email-spoof.md#use-admin-submission-in-microsoft-365-defender): tworzenie dozwolonych fałszywych wpisów nadawcy przy użyciu listy dozwolonych/zablokowanych dzierżawców.

- [Personifikacja umożliwia przesyłanie przez administratora](allow-block-email-spoof.md#create-impersonated-sender-entries): opcja Dodaj umożliwia personifikowanie nadawców przy użyciu strony Przesłane w Microsoft 365 Defender.

- [Wyświetl przekonwertowane przesyłanie przez administratora z przesłania przez użytkownika](admin-submission.md#convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission): skonfiguruj niestandardową skrzynkę pocztową w celu przechwycenia wiadomości zgłoszonych przez użytkownika bez wysyłania wiadomości do firmy Microsoft w celu analizy.

- [Wyświetl skojarzony alert dotyczący przesyłania przez użytkowników i administratorów](admin-submission.md#view-associated-alert-for-user-and-admin-email-submissions): wyświetl odpowiedni alert dla każdego zgłoszonego przez użytkownika komunikatu phish i przesłania wiadomości e-mail administratora. 

- [Konfigurowalna ochrona przed personifikacją niestandardowych użytkowników i domen oraz zwiększony zakres w ramach wstępnie ustawionych zasad](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/configurable-impersonation-protection-and-scope-for-preset/ba-p/3294459):
  - (Wybierz opcję) Zastosuj wstępnie ustawione zasady ścisłe/standardowe do całej organizacji i unikaj kłopotliwego wybierania określonych użytkowników, grup lub domen adresatów, a tym samym zabezpieczania wszystkich użytkowników adresatów w organizacji. 
  - Skonfiguruj ustawienia ochrony przed personifikacją dla użytkowników niestandardowych i domen niestandardowych w ramach wstępnie ustawionych zasad ścisłych/standardowych oraz automatycznie chroń docelowych użytkowników i domenę docelową przed atakami personifikacji.

- [Upraszczanie środowiska kwarantanny (część druga) w Microsoft 365 Defender dla usługi Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience-part-two/ba-p/3354687): wyróżnia dodatkowe funkcje, aby jeszcze bardziej ułatwić korzystanie z kwarantanny.

## <a name="april-2022"></a>Kwiecień 2022 r.

- [Wprowadzenie do tabeli URLClickEvents w Microsoft 365 Defender Advanced Hunting](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-the-urlclickevents-table-in-advanced-hunting-with/ba-p/3295096): Introducing the UrlClickEvents table in advanced hunting with Ochrona usługi Office 365 w usłudze Microsoft Defender (Zaawansowane wyszukiwanie zagrożeń: wprowadzenie do tabeli UrlClickEvents w zaawansowanym polowaniu z użyciem Ochrona usługi Office 365 w usłudze Microsoft Defender).
- [Ulepszenia ręcznego korygowania poczty e-mail](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365): wprowadzenie ręcznych akcji przeczyszczania poczty e-mail podjętych w Ochrona usługi Office 365 w usłudze Microsoft Defender do ujednoliconego centrum akcji Microsoft 365 Defender (M365D) przy użyciu nowego badania ukierunkowanego na akcje.
- [Wprowadzenie do zróżnicowanej ochrony kont priorytetowych w Ochrona usługi Office 365 w usłudze Microsoft Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-differentiated-protection-for-priority-accounts-in/ba-p/3283838): wprowadzenie ogólnej dostępności zróżnicowanej ochrony dla kont priorytetowych. 
 
## <a name="march-2022"></a>Marzec 2022 r.

- [Usprawniono środowisko przesyłania w Ochrona usługi Office 365 w usłudze Microsoft Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/streamlining-the-submissions-experience-in-microsoft-defender/ba-p/3152080): wprowadzenie do nowego ujednoliconego i usprawniony proces przesyłania, aby uprościć środowisko pracy.

## <a name="january-2022"></a>Styczeń 2022

- [Zaktualizowano środowiska wyszukiwania zagrożeń i badania dla Ochrona usługi Office 365 w usłudze Microsoft Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/updated-hunting-and-investigation-experiences-for-microsoft/ba-p/3002015): wprowadzenie do panelu podsumowania wiadomości e-mail dla środowisk w Ochrona usługi Office 365 w usłudze Defender, a także aktualizacje środowiska dla Eksploratora zagrożeń i czasu rzeczywistego Wykrywania.

## <a name="october-2021"></a>Październik 2021

- [Zaawansowane rozszerzenie DKIM dostarczania](configure-advanced-delivery.md): dodano obsługę wpisu domeny DKIM w ramach konfiguracji symulacji wyłudzania informacji innych firm.
- [Zabezpiecz domyślnie](secure-by-default.md): domyślnie rozszerzone zabezpieczenia dla reguł przepływu poczty programu Exchange (nazywanych również regułami transportu).

## <a name="september-2021"></a>Wrzesień 2021

- [Ulepszone środowisko raportowania w Ochrona usługi Office 365 w usłudze Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/improving-the-reporting-experience-in-microsoft-defender-for/ba-p/2760898)
- [Zasady kwarantanny](quarantine-policies.md): administratorzy mogą skonfigurować szczegółową kontrolę dostępu adresatów do komunikatów poddanych kwarantannie i dostosować powiadomienia o spamie użytkowników końcowych.
  - [Wideo z doświadczeniem administratora](https://youtu.be/vnar4HowfpY)
  - [Wideo przedstawiające środowisko użytkownika końcowego](https://youtu.be/s-vozLO43rI)
  - Inne nowe możliwości, które pojawią się w środowisku kwarantanny, zostały opisane w tym wpisie w blogu: [Upraszczanie środowiska kwarantanny](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience/ba-p/2676388).
- Domyślnie rozpoczyna się przekierowanie portalu, przekierowując użytkowników z usługi Security & Compliance do Microsoft 365 Defender <https://security.microsoft.com>. Aby uzyskać więcej informacji na ten temat, zobacz [Przekierowywanie kont z Office 365 Security & Compliance Center do Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection)

## <a name="august-2021"></a>Sierpień 2021

- [Administracja przeglądu zgłoszonych komunikatów](admin-review-reported-message.md): administratorzy mogą teraz wysyłać szablonowe komunikaty z powrotem do użytkowników końcowych po przejrzeniu zgłoszonych komunikatów. Szablony można dostosować dla organizacji i na podstawie werdyktu administratora.
- [Dodaj opcje zezwalania na korzystanie z listy dozwolonych/blokowych dzierżawy](manage-tenant-allows.md): możesz teraz dodać wpisy zezwalania do listy dozwolonych/zablokowanych dzierżaw, jeśli zablokowany komunikat został przesłany w ramach procesu przesyłania przez administratora. W zależności od charakteru bloku przesłany adres URL, plik i/lub zezwolenie nadawcy zostaną dodane do listy dozwolonych/zablokowanych dzierżaw. W większości przypadków, pozwala są dodawane, aby dać systemowi trochę czasu i pozwolić mu naturalnie, jeśli jest to uzasadnione. W niektórych przypadkach firma Microsoft zarządza zezwoleniem dla Ciebie.

## <a name="july-2021"></a>Lipiec 2021

- [Ulepszenia analizy poczty e-mail w zautomatyzowanych badaniach](email-analysis-investigations.md)
- [Zaawansowane dostarczanie](configure-advanced-delivery.md): wprowadzenie nowej możliwości konfigurowania dostarczania symulacji wyłudzania informacji innych firm użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych operacji zabezpieczeń.
- [Bezpieczne linki dla usługi Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- Nowe zasady alertów dla następujących scenariuszy: zagrożone skrzynki pocztowe, wyłudzanie informacji o formularzach, złośliwe wiadomości e-mail dostarczane z powodu przesłonięć i zaokrąglanie zap
  - Podejrzane działania w zakresie przesyłania dalej wiadomości e-mail
  - Użytkownik nie może udostępniać formularzy i zbierać odpowiedzi
  - Formularz zablokowany z powodu potencjalnej próby wyłudzania informacji
  - Formularz oflagowany i potwierdzony jako wyłudzanie informacji
  - [Nowe zasady alertów dla zap](../../compliance/new-defender-alert-policies.md)
- Ochrona usługi Office 365 w usłudze Microsoft Defender alerty są teraz zintegrowane z Microsoft 365 Defender — [Microsoft 365 Defender kolejki ujednoliconych alertów i ujednoliconej kolejki alertów](../defender/investigate-alerts.md)
- [Tagi użytkowników](user-tags.md) są teraz zintegrowane z środowiskami alertów Ochrona usługi Office 365 w usłudze Microsoft Defender, w tym: kolejką alertów i szczegółami w Office 365 Zgodność & zabezpieczeń oraz określaniem zakresu niestandardowych zasad alertów dla tagów użytkowników w celu utworzenia docelowych zasad alertów.
  - Tagi są również dostępne w kolejce ujednoliconych alertów w portalu Microsoft 365 Defender (Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2)

## <a name="june-2021"></a>Czerwiec 2021

- Nowe ustawienie porad dotyczących zabezpieczeń pierwszego kontaktu w ramach zasad ochrony przed wyłudzaniem informacji. Ta wskazówka dotycząca bezpieczeństwa jest wyświetlana, gdy adresaci po raz pierwszy otrzymują wiadomość e-mail od nadawcy lub często nie otrzymują wiadomości e-mail od nadawcy. Aby uzyskać więcej informacji na temat tego ustawienia i sposobu jego konfigurowania, zobacz następujące artykuły:
  - [Porada bezpieczeństwa pierwszego kontaktu](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w usłudze EOP](configure-anti-phishing-policies-eop.md)
  - [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>Kwiecień/maj 2021 r.

- [Strona jednostki poczty e-mail](mdo-email-entity-page.md): ujednolicony 360-stopniowy widok wiadomości e-mail z wzbogaconymi informacjami o zagrożeniach, uwierzytelnianiu i wykrywaniu, szczegółach detonacji i zupełnie nowym środowisku podglądu wiadomości e-mail.
- [interfejs API zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events): Aktualizacje do usługi EmailEvents (RecordType 28), aby dodać akcję dostarczania, oryginalne i najnowsze lokalizacje dostarczania oraz zaktualizowane szczegóły wykrywania.
- [Analiza zagrożeń dla Ochrona usługi Office 365 w usłudze Defender](/microsoft-365/security/defender/threat-analytics): wyświetlanie aktywnych aktorów zagrożeń, popularnych technik i obszarów ataków, a także obszerne raporty naukowców firmy Microsoft dotyczące trwających kampanii.

## <a name="februarymarch-2021"></a>Luty/marzec 2021 r.

- Integracja identyfikatora alertu (wyszukiwanie przy użyciu identyfikatora alertu i nawigacji Alert-Explorer) w [środowiskach wyszukiwania zagrożeń](threat-explorer.md)
- Zwiększenie limitów eksportu rekordów z 9990 do 200 000 w [środowiskach wyszukiwania zagrożeń](threat-explorer.md)
- Rozszerzanie przechowywania danych Eksploratora (i wykrywania w czasie rzeczywistym) i limitu wyszukiwania dla dzierżaw wersji próbnej z 7 (poprzedni limit) do 30 dni w [środowiskach wyszukiwania zagrożeń](threat-explorer.md)
- Nowe wykresy przestawne wyszukiwania zagrożeń o nazwie **Personifikowana domena** i **Personifikowany użytkownik** w Eksploratorze (i wykrywanie w czasie rzeczywistym) w celu wyszukiwania ataków personifikacji na chronionych użytkowników lub domeny. Aby uzyskać więcej informacji, zobacz [szczegóły](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains). (Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 lub plan 2)

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2

Czy wiesz, że Ochrona usługi Office 365 w usłudze Microsoft Defender jest dostępna w dwóch planach? [Dowiedz się więcej o tym, co zawiera każdy plan](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="see-also"></a>Zobacz też

- [Plan działania platformy Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap)
- [Opis usługi Ochrona usługi Office 365 w usłudze Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
