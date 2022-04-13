---
title: Krok nr 1. Konfigurowanie planu bazowego zabezpieczeń
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
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
keywords: ransomware, oprogramowanie wymuszające okup obsługiwane przez człowieka, oprogramowanie wymuszające okup obsługiwane przez człowieka, HumOR, atak wymuszenia, atak ransomware, szyfrowanie, kryptowirtuologia, zero zaufania
description: Użyj punktów odniesienia zabezpieczeń, aby chronić zasoby Microsoft 365 przed atakami wymuszania okupu.
ms.openlocfilehash: 925a64e1d7852aeed6f596e99b20dbff8b34d1be
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825107"
---
# <a name="step-1-configure-security-baselines"></a>Krok nr 1. Konfigurowanie planu bazowego zabezpieczeń

Pierwszym krokiem do przeciwdziałania atakom wymuszającym okup jest skonfigurowanie następujących punktów odniesienia zabezpieczeń zdefiniowanych przez firmę Microsoft:

- [Centrum zabezpieczeń platformy Microsoft 365](#microsoft-365-security-baseline)
- [zarządzanie pocztą e-mail Exchange](#exchange-email-management-baseline)
- [Dodatkowe punkty odniesienia dla urządzeń Windows i oprogramowania klienckiego](#additional-baselines)

Te punkty odniesienia zawierają ustawienia konfiguracji i reguły, które są dobrze znane przez osoby atakujące, których brak jest szybko zauważany i często wykorzystywany.

## <a name="microsoft-365-security-baseline"></a>Microsoft 365 punkt odniesienia zabezpieczeń

Najpierw oceń i zmierz stan zabezpieczeń przy użyciu wskaźnika bezpieczeństwa [firmy Microsoft](/microsoft-365/security/defender/microsoft-secure-score) i postępuj zgodnie z instrukcjami, aby je ulepszyć w razie potrzeby.

Następnie użyj [reguł zmniejszania obszaru ataków](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) , aby zablokować podejrzane działania i podatną na zagrożenia zawartość. Te reguły obejmują zapobieganie:

- Wszystkie Office aplikacje z tworzenia procesów podrzędnych
- Zawartość wykonywalna z klienta poczty e-mail i poczty internetowej
- Uruchamianie plików wykonywalnych, chyba że spełniają kryterium występowania, wieku lub listy zaufanych
- Wykonywanie potencjalnie zaciemnionych skryptów
- Uruchamianie pobranej zawartości wykonywalnej w języku JavaScript lub VBScript
- Office aplikacjom tworzenie zawartości wykonywalnej
- Office aplikacjom wstrzykiwanie kodu do innych procesów
- Office aplikacji komunikacyjnej z tworzenia procesów podrzędnych
- Niezaufane i niepodpisane procesy uruchamiane z portu USB
- Trwałość za pośrednictwem subskrypcji zdarzeń interfejsu zarządzania Windows (WMI)
- Kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń (lsass.exe)
- Tworzenie procesów pochodzące z poleceń PSExec i WMI

## <a name="exchange-email-management-baseline"></a>Exchange punktu odniesienia zarządzania pocztą e-mail

Zapobiegaj początkowemu dostępowi do dzierżawy przed atakiem opartym na wiadomościach e-mail przy użyciu tych ustawień punktu odniesienia poczty e-mail Exchange:

- Włącz [skanowanie Program antywirusowy Microsoft Defender wiadomości e-mail](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus).
- Użyj Ochrona usługi Office 365 w usłudze Microsoft Defender, aby [zwiększyć ochronę przed wyłudzaniem informacji](/microsoft-365/security/office-365-security/anti-phishing-protection) i ochronę przed nowymi zagrożeniami i wariantami polimorficznymi.
- Sprawdź ustawienia filtrowania wiadomości e-mail Office 365, aby upewnić się, że blokujesz fałszywe wiadomości e-mail, spam i wiadomości e-mail ze złośliwym oprogramowaniem. Użyj Ochrona usługi Office 365 w usłudze Defender, aby zwiększyć ochronę przed wyłudzaniem informacji i ochronę przed nowymi zagrożeniami i wariantami polimorficznymi. Skonfiguruj Ochrona usługi Office 365 w usłudze Defender, aby [ponownie sprawdzać linki po kliknięciu](/microsoft-365/security/office-365-security/atp-safe-links) i [usunięciu dostarczonych wiadomości e-mail](/microsoft-365/security/office-365-security/zero-hour-auto-purge) w odpowiedzi na nowo uzyskaną analizę zagrożeń.
- Przejrzyj i zaktualizuj najnowsze [zalecane ustawienia dotyczące EOP i zabezpieczeń Ochrona usługi Office 365 w usłudze Defender](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp).
- Skonfiguruj Ochrona usługi Office 365 w usłudze Defender, aby [ponownie sprawdzać linki po kliknięciu](/microsoft-365/security/office-365-security/set-up-safe-links-policies) i usunięciu dostarczonych wiadomości e-mail w odpowiedzi na nowo uzyskaną analizę zagrożeń.

## <a name="additional-baselines"></a>Dodatkowe punkty odniesienia

Stosowanie [punktów odniesienia zabezpieczeń](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) dla:

- Microsoft Windows 11 lub 10
- Aplikacje Microsoft 365 dla Enterprise
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>Wpływ na użytkowników i zarządzanie zmianami

Najlepszym rozwiązaniem dla reguły zmniejszania obszaru ataków jest ocena wpływu reguły na sieć, otwierając zalecenie dotyczące zabezpieczeń dla tej reguły w Zarządzanie zagrożeniami i lukami. W okienku szczegółów rekomendacji opisano wpływ użytkownika, którego można użyć do określenia, jaki procent urządzeń może zaakceptować nowe zasady umożliwiające regułę w trybie blokowania bez negatywnego wpływu na produktywność użytkowników.

Ponadto Exchange ustawienia punktu odniesienia poczty e-mail mogą blokować przychodzące wiadomości e-mail i uniemożliwiać wysyłanie wiadomości e-mail lub klikanie linków w wiadomości e-mail. Poinformuj pracowników o tym zachowaniu i o przyczynie, dla którego podejmowane są te środki ostrożności.

## <a name="resulting-configuration"></a>Konfiguracja wyniku

Oto ochrona przed oprogramowaniem wymuszającym okup dla dzierżawy po tym kroku.

![Ochrona przed oprogramowaniem wymuszającym okup dla dzierżawy Microsoft 365 po kroku 1](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)

## <a name="next-step"></a>Następny krok

[![Krok 2 dotyczący ochrony przed oprogramowaniem wymuszającym okup za pomocą Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

Przejdź do [kroku 2](ransomware-protection-microsoft-365-attack-detection-response.md), aby wdrożyć funkcje wykrywania ataków i reagowania na nie dla dzierżawy Microsoft 365.
