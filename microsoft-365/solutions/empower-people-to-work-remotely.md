---
title: Konfigurowanie infrastruktury do pracy hybrydowej z usługami Microsoft 365
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
- remotework
- m365solution-remotework
- m365solution-overview
- M365initiative-coredeploy
ms.custom: seo-marvel-jun2020
keywords: praca z domu, praca z domu, środowisko hybrydowe, pracownik zdalny, praca hybrydowa, zdalni pracownicy, łączność hybrydowa, dostęp zdalny, komunikacja telekomunikacyjna, teleworking, teleworking, praca w telefonie komórkowym, praca zdalna, praca z dowolnego miejsca, elastyczne miejsce pracy
description: Krok po kroku warstw infrastruktury, aby pracownicy hybrydowi mogą bezpiecznie uzyskać dostęp do zasobów lokalnych i Microsoft 365 lokalnych.
ms.openlocfilehash: 0370d30584021ab8560a24c7e54e3a7c7aadeb1f
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014841"
---
# <a name="set-up-your-infrastructure-for-hybrid-work-with-microsoft-365"></a>Konfigurowanie infrastruktury do pracy hybrydowej z usługami Microsoft 365

Aby zabezpieczyć i zoptymalizować produktywność i współpracę pracowników, musisz zezwolić pracownikom lokalnym i zdalnym na łatwe i bezpieczne uzyskiwanie dostępu do informacji, narzędzi i zasobów w chmurze organizacji. To rozwiązanie należy wykonać przez proces wdrażania kluczowych warstw infrastruktury, które dają pracownikom najlepsze wyniki, niezależnie od tego, gdzie się znajdują.

Pracownicy hybrydowi mogą pracować w miejscu lub zdalnie w różnych lokalizacjach. Zezwolenie pracownikom na pracę z dala od tradycyjnego biura jest ważne dla wielu organizacji:

- Zatrudnienie i zachowanie pracowników, którzy nie chcą przenosić pracowników lub wymagać elastycznego środowiska pracy.
- Ogranicz liczbę pracowników do pracy dojeżdżając do pracy, odchodząc od pracowników z więcej czasu, aby pracować wydajniej i aby ograniczyć stres poza pracą.
- Zaoszczędź miejsce w biurze.

Microsoft 365 funkcje, które dają pracownikom hybrydowym możliwość pracy w miejscu lub zdalnie.

![Zapewnij pracownikom hybrydowym Microsoft 365.](../media/empower-people-to-work-remotely/2-m365-remoteworker-solution-businessoverview.png)

> [!NOTE]
> Jeśli jesteś nowym użytkownik Microsoft 365 zapoznaj się z [tymi zasobami](https://www.microsoft.com/microsoft-365).

Obejrzyj ten klip wideo, aby uzyskać omówienie procesu wdrażania.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4F1af]

To rozwiązanie dla informatyków zarządzających infrastrukturą w chmurze i na miejscu w celu zwiększenia wydajności pracowników hybrydowych zapewnia następujące kluczowe możliwości:

- Połączono

  Z każdego miejsca na świecie i w dowolnym momencie Twoi pracownicy mogą mieć dostęp do:

  - Dane i usługi oparte na chmurze Microsoft 365 subskrypcji usługi.

  - Zasoby organizacji, takie jak zasoby oferowane przez lokalne centra danych aplikacji.

- Bezpieczne

  Logowanie jest zabezpieczone za pomocą uwierzytelniania wieloskładnikowego (MFA) oraz wbudowanych funkcji zabezpieczeń programów Microsoft 365 i Windows 11 lub 10 w celu ochrony przed złośliwym oprogramowaniem, złośliwymi atakami i utratą danych.

- Zarządzane

  Urządzeniami pracowników hybrydowych można zarządzać z chmury z ustawieniami zabezpieczeń, dozwolonymi aplikacjami i wymagać zgodności z kondycją systemu.

- Współpraca i produktywność

  Pracownicy hybrydowi mogą wydajnie pracować lokalnie w sposób wysoce współpracujący dzięki:

  - Spotkania online i sesje czatu z Teams.

  - Udostępnione obszary robocze do przechowywania plików w chmurze z globalnymi ułatwieniami dostępu i współpracą w czasie rzeczywistym SharePoint i OneDrive.

  - Udostępnione zadania i przepływy pracy służące do dzielenia pracy i wykonywania zadań.

Aby logowanie było bezproblemowe, lokalne konta Usługi domenowe w usłudze Active Directory użytkowników (AD DS) powinny być synchronizowane z usługą Azure Active Directory (Azure AD). Aby chronić Windows 11 lub 10 urządzeń, należy je zarejestrowanych w usłudze Intune. Oto widok wysokiego poziomu infrastruktury.

![Podstawowa infrastruktura dla pracowników hybrydowych z Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-basic-infrastructure.png)

Aby włączyć możliwości Microsoft 365 hybrydowych, skorzystaj z tych funkcji Microsoft 365 hybrydowych.

|Funkcja lub funkcja|Opis|Licencjonowanie|
|---|---|---|
|Uwierzytelniania wieloskładnikowego wymuszane przy użyciu domyślnych ustawień zabezpieczeń|Chroń przed naruszoną tożsamością i urządzeniami, wymagając drugiej formy uwierzytelniania dla logowania. Ustawienia domyślne zabezpieczeń wymagają uwierzytelniania MFA dla wszystkich kont użytkowników.|Microsoft 365 E3 lub E5|
|Uwierzytelniania wieloskładnikowego z dostępem warunkowym|Wymagaj uwierzytelniania wieloskładnikowego na podstawie właściwości logowania przy użyciu zasad dostępu warunkowego.|Microsoft 365 E3 lub E5|
|Uwierzytelniania wieloskładnikowego z dostępem warunkowym opartym na czynniku ryzyka|Wymagaj uwierzytelniania wieloskładnikowego na podstawie ryzyka związanego z logowaniem użytkownika przy użyciu usługi Azure AD Identity Protection.|Microsoft 365 E5 lub E3 z Azure AD — wersja Premium P2 licencji|
|Self-Service resetowania hasła (SSPR)|Zezwalaj użytkownikom na resetowanie lub odblokowywanie swoich haseł lub kont.|Microsoft 365 E3 lub E5|
|Serwer proxy aplikacji Azure AD|Zapewnij bezpieczny dostęp zdalny aplikacjom internetowym hostowanych na serwerach intranetowych.|Wymaga osobnej płatnej subskrypcji platformy Azure|
|Vpn typu punkt-lokacja na platformie Azure|Utwórz bezpieczne połączenie z urządzeniem pracownika zdalnego do intranetu za pośrednictwem sieci wirtualnej platformy Azure.|Wymaga osobnej płatnej subskrypcji platformy Azure|
|Windows 365|Obsługa pracowników zdalnych, którzy mogą korzystać z osobistych i nieza zarządzania urządzeniami wyłącznie na Windows chmurze w usłudze 365.|Wymaga osobnej płatnej subskrypcji platformy Azure|
|Pulpit zdalny |Zezwalaj pracownikom na łączenie się Windows komputerami w intranecie.|Microsoft 365 E3 lub E5|
|Brama usług pulpitu zdalnego|Szyfrowanie komunikacji i zapobieganie bezpośredniemu dostępowi hostów RDS do Internetu.|Wymaga oddzielnych Windows serwera|
|Microsoft Intune|Zarządzaj urządzeniami i aplikacjami.|Microsoft 365 E3 lub E5|
|Menedżer konfiguracji|Zarządzanie instalacjami, aktualizacjami i ustawieniami oprogramowania na urządzeniach|Wymaga oddzielnych Menedżer konfiguracji licencji|
|Analiza punktu końcowego|Określanie gotowości do aktualizacji Windows klientów.|Wymaga oddzielnych Menedżer konfiguracji licencji|
|Windows Autopilot|Konfiguruj i wstępnie konfiguruj nowe urządzenia z Windows 11 lub 10 urządzeń do wydajnego użytkowania.|Microsoft 365 E3 lub E5|
|Microsoft Teams, Exchange Online, SharePoint Online i OneDrive, Aplikacje Microsoft 365, Microsoft Power Platform i Yammer|Twórz, komunikuj się i współpracuj.|Microsoft 365 E3 lub E5|
||||

Aby uzyskać kryteria zabezpieczeń i zgodności, zobacz [Wdrażanie zabezpieczeń i zgodności dla pracowników zdalnych](empower-people-to-work-remotely-security-compliance.md).

<a name="poster"></a> Aby uzyskać 2-stronowe podsumowanie tego rozwiązania, zobacz plakat "Zwiększ możliwości [pracowników hybrydowych"](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf).

[![Plakat "Zwiększ możliwości pracowników hybrydowych".](../media/empower-people-to-work-remotely/empower-remote-workers-poster.png)](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf)

## <a name="provide-hybrid-working-for-all-of-your-workers"></a>Zapewnienie pracy hybrydowej wszystkim pracownikom

Za pomocą tych urządzeń możesz umożliwić wszystkim pracownikom wydajną pracę z dowolnego miejsca:

- Nowoczesne urządzenie, takie jak laptop Surface i Windows 11 lub 10, które oferuje funkcje, zabezpieczenia i wydajność, aby uzyskać dostęp do aplikacji i usług Microsoft 365 w chmurze bezpośrednio za pośrednictwem Internetu.

- Każde urządzenie, w tym starsze komputery przenośne lub stacjonarne używane z domu, które może uzyskać dostęp Microsoft 365 usług i aplikacji w chmurze za pośrednictwem komputera [Windows 365 w chmurze](empower-people-to-work-remotely-remote-access.md#deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices). Ta opcja zapewnia wysoką wydajność, silne zabezpieczenia i uproszczone zarządzanie indywną.

## <a name="next-steps"></a>Następne kroki

Skorzystaj z tych kroków, aby zabezpieczyć i zoptymalizować dostęp do serwerów i usług w chmurze organizacji oraz zmaksymalizować wydajność Twojego pracownika hybrydowego.

1. [Zwiększanie zabezpieczeń logowania za pomocą uwierzytelniania wieloskładnikowego](empower-people-to-work-remotely-secure-sign-in.md)
2. [Zapewnianie dostępu zdalnego do aplikacji i usług lokalnych](empower-people-to-work-remotely-remote-access.md)
3. [Wdrażanie usług zabezpieczeń i zgodności](empower-people-to-work-remotely-security-compliance.md)
4. [Wdrażanie zarządzania punktami końcowymi dla urządzeń, komputerów i innych punktów końcowych](empower-people-to-work-remotely-manage-endpoints.md)
5. [Wdrażanie aplikacji i usług zwiększających produktywność pracowników hybrydowych](empower-people-to-work-remotely-teams-productivity-apps.md)
6. [Szkolenie pracowników i korzystanie z informacji zwrotnych o użyciu](empower-people-to-work-remotely-train-monitor-usage.md)

[![Czynności, które należy wykonać w celu skonfigurowania infrastruktury hybrydowej z usługą Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-step-grid.png)](empower-people-to-work-remotely-secure-sign-in.md)

Aby dowiedzieć się, jak fikcyjna, ale reprezentatywna wielonarodowa organizacja schłoniła swoją infrastrukturę do pracy hybrydowej, zobacz Odpowiedź i infrastruktura firmy [Contoso COVID-19](contoso-remote-onsite-work.md) na temat pracy hybrydowej.
