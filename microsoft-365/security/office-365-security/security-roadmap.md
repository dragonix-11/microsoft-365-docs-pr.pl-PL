---
title: Microsoft 365 plan bezpieczeństwa — najważniejsze priorytety
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 08/20/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
ms.assetid: 28c86a1c-e4dd-4aad-a2a6-c768a21cb352
description: Najważniejsze zalecenia zespołu ds. cyberbezpieczeństwa firmy Microsoft dotyczące implementowania możliwości zabezpieczeń w celu ochrony środowiska Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6e6174da5a9cbac779c147fb0ea091080bf4338a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945434"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Plan bezpieczeństwa — najważniejsze priorytety dla pierwszych 30 dni, 90 dni i nie tylko

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Ten artykuł zawiera najważniejsze zalecenia zespołu ds. cyberbezpieczeństwa firmy Microsoft dotyczące implementowania możliwości zabezpieczeń w celu ochrony środowiska Microsoft 365. Ten artykuł został zaadaptowany na podstawie sesji konferencji Microsoft Ignite — [Zabezpieczanie Microsoft 365 jak profesjonalista ds. cyberbezpieczeństwa: najważniejsze priorytety pierwszych 30 dni, 90 dni i nie tylko](https://www.youtube.com/watch?v=luignzNyR-o). Ta sesja została opracowana i przedstawiona przez Marka Simosa i Matta Kemelhara, Enterprise Cybersecurity Architects.

W tym artykule:

- [Wyniki planu działania](security-roadmap.md#Roadmap)
- [30 dni — potężne szybkie wygrane](security-roadmap.md#Thirdaydays)
- [90 dni — rozszerzone zabezpieczenia](security-roadmap.md#Ninetydays)
- [Poza](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Wyniki planu działania
<a name="Roadmap"> </a>

Te zalecenia dotyczące planu działania są przygotowywane w trzech fazach w kolejności logicznej z następującymi celami.

|Ramy czasowe|Wyniki|
|---|---|
|30 dni|Szybka konfiguracja: <ul><li>Podstawowa ochrona administratora.</li><li>Rejestrowanie i analiza.</li><li>Podstawowa ochrona tożsamości.</li></ul> <p> Konfiguracja dzierżawy. <p> Przygotowywanie uczestników projektu.|
|90 dni|Zaawansowane zabezpieczenia: <ul><li>Konta administratorów.</li><li>Dane i konta użytkowników.</li></ul> <p> Wgląd w zgodność, zagrożenia i potrzeby użytkowników. <p> Dostosuj i zaimplementuj domyślne zasady i zabezpieczenia.|
|Poza|Dostosuj i uściślij kluczowe zasady i kontrolki. <p> Rozszerzanie ochrony na zależności lokalne. <p> Integracja z procesami biznesowymi i zabezpieczeń (zagrożenia prawne, wewnętrzne itp.).|

## <a name="30-days--powerful-quick-wins"></a>30 dni — potężne szybkie wygrane
<a name="Thirdaydays"> </a>

Te zadania można wykonać szybko i mieć niski wpływ na użytkowników.

|Obszar|Zadania|
|---|---|
|Zarządzanie zabezpieczeniami|<ul><li>Sprawdź wskaźnik bezpieczeństwa i zanotuj bieżący wynik (<https://security.microsoft.com/securescore>).</li><li>Włącz rejestrowanie inspekcji dla Office 365. Zobacz [Przeszukiwanie dziennika inspekcji](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[Skonfiguruj Microsoft 365 w celu zwiększenia bezpieczeństwa](tenant-wide-setup-for-increased-security.md).</li><li>Regularnie przeglądaj pulpity nawigacyjne i raporty w portalu Microsoft 365 Defender i Defender dla Chmury Apps.</li></ul>|
|Ochrona przed zagrożeniami|[Połączenie Microsoft 365 do Microsoft Defender for Cloud Apps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security), aby rozpocząć monitorowanie przy użyciu domyślnych zasad wykrywania zagrożeń dla nietypowych zachowań. Utworzenie punktu odniesienia wykrywania anomalii trwa siedem dni. <p>  Zaimplementuj ochronę kont administratorów:<ul><li>Użyj dedykowanych kont administratorów do działania administratora.</li><li>Wymuszanie uwierzytelniania wieloskładnikowego (MFA) dla kont administratorów.</li><li>Użyj [wysoce bezpiecznego urządzenia Windows](/windows-hardware/design/device-experiences/oem-highly-secure) do działania administratora.</li></ul>|
|Zarządzanie tożsamościami i dostępem|<ul><li>[Włącz usługę Azure Active Directory Identity Protection](/azure/active-directory/active-directory-identityprotection-enable).</li><li>W przypadku środowisk tożsamości federacyjnych wymuś zabezpieczenia konta (długość hasła, wiek, złożoność itp.).</li></ul>|
|Ochrona informacji|Przejrzyj przykładowe zalecenia dotyczące ochrony informacji. Ochrona informacji wymaga koordynacji w całej organizacji. Zacznij od następujących zasobów:<ul><li>[Office 365 Information Protection rodo](/compliance/regulatory/gdpr)</li><li>[Konfigurowanie Teams z trzema warstwami ochrony](../../solutions/configure-teams-three-tiers-protection.md) (w tym udostępnianiem, klasyfikacją, zapobieganiem utracie danych w usłudze Microsoft Purview i usługą Azure Information Protection)</li></ul>|

## <a name="90-days--enhanced-protections"></a>90 dni — rozszerzone zabezpieczenia
<a name="Ninetydays"> </a>

Planowanie i wdrażanie tych zadań zajmuje nieco więcej czasu, ale znacznie zwiększa stan zabezpieczeń.

|Obszar|Zadanie|
|---|---|
|Zarządzanie zabezpieczeniami|<ul><li>Sprawdź wskaźnik bezpieczeństwa pod kątem zalecanych akcji dla środowiska (<https://security.microsoft.com/securescore>).</li><li>Kontynuuj regularne przeglądanie pulpitów nawigacyjnych i raportów w portalu Microsoft 365 Defender, Defender dla Chmury Apps i narzędziach SIEM.</li><li>Wyszukaj i zaimplementuj aktualizacje oprogramowania.</li><li>Przeprowadzanie symulacji ataków w celu wyłudzania informacji, natrysku haseł i ataków z użyciem hasła siłowego przy użyciu [trenowania symulacji ataków](attack-simulation-training.md) (dołączonego [do Office 365 Threat Intelligence](office-365-ti.md)).</li><li>Poszukaj ryzyka udostępniania, przeglądając wbudowane raporty w usłudze Defender dla Chmury Apps (na karcie Badanie).</li><li>Sprawdź [Menedżera zgodności,](../../compliance/compliance-manager.md) aby sprawdzić stan, aby zapoznać się z przepisami dotyczącymi organizacji (takimi jak RODO, NIST 800-171).</li></ul>|
|Ochrona przed zagrożeniami|Zaimplementuj rozszerzone zabezpieczenia dla kont administratorów: <ul><li>Skonfiguruj [stacje robocze z dostępem uprzywilejowanym](/security/compass/privileged-access-devices) (PAW) na potrzeby działania administratora.</li><li>Konfigurowanie [usługi Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Skonfiguruj narzędzie do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), aby zbierać dane rejestrowania z Office 365, Defender dla Chmury Apps i innych usług, w tym usług AD FS. Dziennik inspekcji przechowuje dane tylko przez 90 dni. Przechwytywanie tych danych w narzędziu SIEM umożliwia przechowywanie danych przez dłuższy czas.</li></ul>|
|Zarządzanie tożsamościami i dostępem|<ul><li>Włączanie i wymuszanie uwierzytelniania wieloskładnikowego dla wszystkich użytkowników.</li><li>Zaimplementuj zestaw [dostępu warunkowego i powiązanych zasad](microsoft-365-policies-configurations.md).</li></ul>|
|Ochrona informacji| Dostosuj i zaimplementuj zasady ochrony informacji. Te zasoby obejmują przykłady: <ul><li>[Office 365 Information Protection rodo](/compliance/regulatory/gdpr)</li><li>[Konfigurowanie Teams z trzema warstwami ochrony](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Użyj zasad ochrony przed utratą danych i narzędzi do monitorowania w usłudze Microsoft Purview, aby uzyskać dane przechowywane w Microsoft 365 (zamiast Defender dla Chmury Apps). <p> Użyj Defender dla Chmury Apps z Microsoft 365, aby uzyskać zaawansowane funkcje alertów (inne niż zapobieganie utracie danych).|

## <a name="beyond"></a>Poza
<a name="Beyond"> </a>

Są to ważne środki bezpieczeństwa, które bazują na poprzednich pracach.

|Obszar|Zadanie|
|---|---|
|Zarządzanie zabezpieczeniami|<ul><li>Kontynuuj planowanie kolejnych akcji przy użyciu wskaźnika bezpieczeństwa (<https://security.microsoft.com/securescore>).</li><li>Kontynuuj regularne przeglądanie pulpitów nawigacyjnych i raportów w portalu Microsoft 365 Defender, Defender dla Chmury Apps i narzędziach SIEM.</li><li>Kontynuuj wyszukiwanie i implementowanie aktualizacji oprogramowania.</li><li>Integrowanie zbierania elektronicznych materiałów dowodowych w procesach prawnych i reagowania na zagrożenia.</li></ul>|
|Ochrona przed zagrożeniami|<ul><li>Zaimplementuj [bezpieczny dostęp uprzywilejowany](/windows-server/identity/securing-privileged-access/securing-privileged-access) (SPA) dla składników tożsamości w środowisku lokalnym (AD, AD FS).</li><li>Monitorowanie zagrożeń wewnętrznych za pomocą Defender dla Chmury Apps.</li><li>Odnajdywanie w tle użycia usług IT SaaS przy użyciu usługi Defender dla Chmury Apps.</li></ul>|
|Zarządzanie tożsamościami i dostępem|<ul><li>Uściślaj zasady i procesy operacyjne.</li><li>Używanie usługi Azure AD Identity Protection do identyfikowania zagrożeń wewnętrznych.</li></ul>|
|Ochrona informacji|Uściślij zasady ochrony informacji: <ul><li>Microsoft 365 i Office 365 etykiet poufności i ochrony przed utratą danych (DLP) lub azure Information Protection.</li><li>Defender dla Chmury Aplikacje — zasady i alerty.</li></ul>|

Zobacz również: [Jak uniknąć szybkich cyberataków, takich jak Petya i WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
