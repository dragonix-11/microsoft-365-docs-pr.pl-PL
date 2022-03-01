---
title: Krok nr 1. Konfigurowanie planu bazowego zabezpieczeń
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: oprogramowanie wymuszające okup, oprogramowanie wymuszające okup obsługiwane przez człowieka, oprogramowanie wymuszające okup przez człowieka, humor, ataki wymuszające okup, ataki oprogramowania wymuszającego okup, szyfrowanie, kryptografia, zerowe zaufanie
description: Użyj planu bazowego zabezpieczeń, aby chronić zasoby Microsoft 365 przed atakami oprogramowania wymuszającego okup.
ms.openlocfilehash: 66218d15a36faa510bd246b46dbc0dcd0f9948fb
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014864"
---
# <a name="step-1-configure-security-baselines"></a>Krok nr 1. Konfigurowanie planu bazowego zabezpieczeń

Pierwszym krokiem do zabezpieczenia przed atakami wymuszającym okup jest skonfigurowanie następujących linii bazowych zabezpieczeń zdefiniowanych przez firmę Microsoft:

- [Microsoft 365 zabezpieczeń](#microsoft-365-security-baseline)
- [Exchange e-mail](#exchange-email-management-baseline)
- [Dodatkowe linie bazowe dla Windows i oprogramowania klienckiego](#additional-baselines)

Te linie bazowe zawierają ustawienia konfiguracyjne i reguły dobrze znane atakującym, których brak jest szybko zauważyć i często wykorzystywany.

## <a name="microsoft-365-security-baseline"></a>Microsoft 365 planu bazowego zabezpieczeń

Najpierw oceń i zmierz swoją postawę zabezpieczeń przy użyciu funkcji [Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score) , a następnie postępuj zgodnie z instrukcjami, aby ją ulepszyć zgodnie z potrzebami.

Następnie użyj reguł [ograniczania powierzchni ataków,](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) aby zablokować podejrzane działania i narażona na nie zawartość. Te reguły uniemożliwiają:

- Wszystkie Office z tworzenia procesów podrzędnych
- Wykonywalna zawartość z klienta poczty e-mail i poczty internetowej
- Uruchamianie plików wykonywalnych, jeśli nie spełniają one kryterium listy zaufanej, jego wieku lub wieku
- Wykonywanie potencjalnie złożonych skryptów
- JavaScript lub VBScript z uruchamiania pobranej zawartości wykonywalnego
- Office tworzenia zawartości wykonywalnego przez aplikacje
- Office aplikacji ze wsadu kodu do innych procesów
- Office aplikacji do komunikacji z tworzenia procesów podrzędnych
- Niezaufane i niepodpisane procesy uruchamiane z usb
- Zapewnianie trwałych Windows subskrypcji zdarzeń interfejsu zarządzania (WMI)
- Kradzież poświadczeń z podsystemu Windows Local Security Authority (lsass.exe)
- Tworzenie procesów na podstawie poleceń PSExec i WMI

## <a name="exchange-email-management-baseline"></a>Exchange planu bazowego zarządzania pocztą e-mail 

Pomóż zapobiec początkowemu dostępowi do dzierżawy w przypadku ataku opartego na wiadomościach e-mail za pomocą tych Exchange podstawowych poczty e-mail:

- Włącz [Program antywirusowy Microsoft Defender skanowanie wiadomości e-mail](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus).
- Korzystaj z usługi Microsoft Defender [Office 365 ochrony i](/microsoft-365/security/office-365-security/anti-phishing-protection) ochrony przed nowymi zagrożeniami i wariantami polymorphic.
- Sprawdź ustawienia Office 365 filtrowania wiadomości e-mail, aby mieć pewność, że wiadomości e-mail, które są sfałszowane, spam i wiadomości e-mail są blokowane za pomocą złośliwego oprogramowania. Korzystaj z usługi Defender Office 365 ochrony i ochrony przed wyłudzaniem informacji przed nowymi zagrożeniami i wariantami polymorphic. Skonfiguruj usługę Defender for Office 365, aby ponownie [sprawdzać linki](/microsoft-365/security/office-365-security/atp-safe-links) kliknięciem i [](/microsoft-365/security/office-365-security/zero-hour-auto-purge) usuwać dostarczone wiadomości w odpowiedzi na nowo nabytą analizę zagrożeń.
- Przejrzyj najnowsze ustawienia usługi  [EOP i Defender oraz](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp) zaktualizuj je do najnowszych ustawień w Office 365 zabezpieczeń.
- Skonfiguruj usługę Defender dla Office 365, aby ponownie [sprawdzać linki](/microsoft-365/security/office-365-security/set-up-safe-links-policies) kliknięciem i usuwać dostarczone wiadomości w odpowiedzi na nowo nabytą analizę zagrożeń.

## <a name="additional-baselines"></a>Dodatkowe linie bazowe

Stosowanie [planu bazowego zabezpieczeń](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) dla:

- Microsoft Windows 11 lub 10
- Aplikacje Microsoft 365 dla Enterprise
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>Wpływ na użytkowników i zarządzanie zmianami

Jako najlepsze rozwiązanie dla reguły ograniczania powierzchni ataków oceń wpływ reguły na Twoją sieć, otwierając zalecenie dotyczące bezpieczeństwa dla tej reguły w programie Zarządzanie zagrożeniami i lukami. W okienku szczegółów rekomendacji opisano wpływ na użytkowników, przy użyciu którego można określić procent urządzeń, które mogą zaakceptować nowe zasady umożliwiające regułę w trybie blokowania bez negatywnego wpływu na wydajność użytkowników.

Ponadto ustawienia Exchange-mail mogą blokować przychodzące wiadomości e-mail i uniemożliwiać wysyłanie wiadomości e-mail lub klikanie linków w wiadomościach e-mail. Informacje dla pracowników dotyczące tego zachowania i powody, dla których są podejmowane te środki ostrożności.

## <a name="resulting-configuration"></a>Wynikowa konfiguracja

Oto ochrona przed oprogramowaniem wymuszającym okup dla Twojej dzierżawy po tym kroku.

![Ochrona przed oprogramowaniem wymuszającym okup dla Microsoft 365 dzierżawy po kroku 1](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)


## <a name="next-step"></a>Następny krok

[![Krok 2 ochrony przed oprogramowaniem wymuszającym okup przy użyciu oprogramowania Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

Przejdź do [kroku 2,](ransomware-protection-microsoft-365-attack-detection-response.md) aby wdrożyć funkcje wykrywania ataków i odpowiedzi dla Microsoft 365 dzierżawy.
