---
title: Microsoft 365 zabezpieczeń — najważniejsze priorytety
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
description: Najważniejsze zalecenia od zespołu firmy Microsoft dotyczące wdrażania funkcji zabezpieczeń w celu ochrony Twojego Microsoft 365 sieci.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9edfda495e1359ac5af74f86f65d33661a2f7059
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998966"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Plan zabezpieczeń — najważniejsze priorytety pierwszych 30 dni, 90 dni i później

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Ten artykuł zawiera najważniejsze zalecenia od zespołu firmy Microsoft dotyczące implementowania funkcji zabezpieczeń w celu ochrony Twojego Microsoft 365 sieci. Ten artykuł został zaadaptowany z sesji Konferencji Microsoft Ignite — Microsoft 365 bezpiecznej osoby: Najważniejsze priorytety na pierwsze [30 dni, 90](https://www.youtube.com/watch?v=luignzNyR-o) dni i później. Tę sesję zaprojektowali i zaprezentowali Mark Simos, Matt Kemelhar, Enterprise Architects.

W tym artykule:

- [Wyniki planu](security-roadmap.md#Roadmap)
- [30 dni — zaawansowane szybkie zwycięstwo](security-roadmap.md#Thirdaydays)
- [90 dni — ulepszone zabezpieczenia](security-roadmap.md#Ninetydays)
- [Beyond](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Wyniki planu
<a name="Roadmap"> </a>

Te zalecenia dotyczące planu są logicznie uporządkowane na trzech etapach z następującymi celami.

****

|Ramy czasowe|Wyniki|
|---|---|
|30 dni|Szybka konfiguracja: <ul><li>Podstawowe zabezpieczenia administratora.</li><li>Rejestrowanie i analiza.</li><li>Podstawowa ochrona tożsamości.</li></ul> <p> Konfiguracja dzierżawy. <p> Przygotowywanie uczestników projektu.|
|90 dni|Zaawansowane zabezpieczenia: <ul><li>Konta administratora.</li><li>Dane i konta użytkowników.</li></ul> <p> Wgląd w zgodność z przepisami, zagrożenia i potrzeby użytkowników. <p> Dostosowywanie i wdrażanie domyślnych zasad i ochrony.|
|Beyond|Dostosowywanie i uściślianie kluczowych zasad i kontrolek. <p> Rozszerzanie ochrony na zależności lokalne. <p> Integracja z procesami biznesowymi i procesami zabezpieczeń (informacjami prawnie, zagrożeniami niejawnego programu testów itp.).|
|

## <a name="30-days--powerful-quick-wins"></a>30 dni — zaawansowane szybkie zwycięstwo
<a name="Thirdaydays"> </a>

Te zadania można wykonać szybko i mają niski wpływ na użytkowników.

****

|Obszar|Zadania|
|---|---|
|Zarządzanie zabezpieczeniami|<ul><li>Sprawdzanie bezpiecznego wyniku i zanotuj bieżący wynik (<https://security.microsoft.com/securescore>).</li><li>Włącz rejestrowanie inspekcji dla Office 365. Zobacz [Przeszukiwanie dziennika inspekcji](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[Skonfiguruj Microsoft 365 w celu zwiększenia bezpieczeństwa](tenant-wide-setup-for-increased-security.md).</li><li>Regularnie przeglądaj pulpity nawigacyjne i raporty w portalu usługi Microsoft 365 Defender oraz usłudze Defender dla aplikacji w chmurze.</li></ul>|
|Ochrona przed zagrożeniami|[Połączenie Microsoft 365 usługi Microsoft Defender dla](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) aplikacji w chmurze, aby rozpocząć monitorowanie w przypadku nieomalalnych zachowań przy użyciu domyślnych zasad wykrywania zagrożeń. Tworzenie planu bazowego dla wykrywania anomalii trwa siedem dni. <p>  Implementowanie ochrony kont administratora:<ul><li>Korzystaj ze dedykowanych kont administratora na użytek działań administratora.</li><li>Wymuszanie uwierzytelniania wieloskładnikowego dla kont administratora.</li><li>Korzystaj z [wysoce bezpiecznego Windows do](/windows-hardware/design/device-experiences/oem-highly-secure) działań administratora.</li></ul>|
|Zarządzanie tożsamością i dostępem|<ul><li>[Włącz Azure Active Directory tożsamości](/azure/active-directory/active-directory-identityprotection-enable).</li><li>W przypadku środowisk tożsamości federacji wyegzekwuj zabezpieczenia konta (długość hasła, wiek, złożoność itp.).</li></ul>|
|Ochrona informacji|Przejrzyj przykładowe zalecenia dotyczące ochrony informacji. Ochrona informacji wymaga koordynacji działań w całej organizacji. Zacznij od następujących zasobów:<ul><li>[Office 365 ochrony informacji dla RODO](/compliance/regulatory/gdpr)</li><li>[Skonfiguruj Teams z trzema poziomami](../../solutions/configure-teams-three-tiers-protection.md) ochrony (obejmuje to udostępnianie, klasyfikację, ochronę przed utratą danych i usługę Azure Information Protection)</li></ul>|
|

## <a name="90-days--enhanced-protections"></a>90 dni — ulepszone zabezpieczenia
<a name="Ninetydays"> </a>

Planowanie i implementowanie tych zadań trwa nieco dłużej, ale znacznie zwiększa twoją wydajność zabezpieczeń.

****

|Obszar|Zadanie|
|---|---|
|Zarządzanie zabezpieczeniami|<ul><li>Sprawdź secure score for recommended actions for your environment (<https://security.microsoft.com/securescore>).</li><li>Kontynuuj regularne przeglądanie pulpitów nawigacyjnych i raportów w portalu usługi Microsoft 365 Defender, usłudze Defender dla aplikacji w chmurze i narzędziach SIEM.</li><li>Poszukaj i zaimplementowaj aktualizacje oprogramowania.</li><li>Przeprowadzaj symeterie ataków na wyłudzanie informacji, wymuszanie haseł i wymuszanie ataków na hasła za pomocą szkolenia symeteracyjnego z użyciem symeterii [ataków (](attack-simulation-training.md)zawartego w Office 365 [analizie](office-365-ti.md) zagrożeń.</li><li>Poszukaj ryzyka związanego z udostępnianiem, przeglądając wbudowane raporty w usłudze Defender dla aplikacji w chmurze (na karcie Badanie).</li><li>Sprawdź [Menedżera zgodności](../../compliance/compliance-manager.md) , aby sprawdzić stan przepisów dotyczących Twojej organizacji (takich jak RODO, NIST 800-171).</li></ul>|
|Ochrona przed zagrożeniami|Wdrażanie rozszerzonych zabezpieczeń kont administratora: <ul><li>Skonfiguruj [stacje robocze z](/security/compass/privileged-access-devices) uprawnieniami dostępu do działań administratorów.</li><li>Skonfiguruj [usługę Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Skonfiguruj narzędzie do zarządzania informacjami o zabezpieczeniach i zdarzeniami w celu zbierania danych rejestrowania z usługi Office 365, usługi Defender dla aplikacji w chmurze i innych usług, w tym usług AD FS. Dziennik inspekcji przechowuje dane tylko przez 90 dni. Przechwytywanie tych danych w narzędziu SIEM umożliwia przechowywanie danych przez dłuższy czas.</li></ul>|
|Zarządzanie tożsamością i dostępem|<ul><li>Włączanie i wymuszanie uwierzytelniania WIELOSKŁADNIKOWEGO dla wszystkich użytkowników.</li><li>Implementowanie zestawu dostępu [warunkowego i powiązanych zasad](microsoft-365-policies-configurations.md).</li></ul>|
|Ochrona informacji| Dostosowywanie i wdrażanie zasad ochrony informacji. Oto przykłady tych zasobów: <ul><li>[Office 365 ochrony informacji dla RODO](/compliance/regulatory/gdpr)</li><li>[Konfigurowanie Teams z trzema poziomami ochrony](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Korzystaj z zasad ochrony przed utratą danych i narzędzi do monitorowania Microsoft 365 danych przechowywanych w Microsoft 365 (zamiast usługi Defender dla aplikacji w chmurze). <p> Używaj usługi Defender dla aplikacji w chmurze Microsoft 365 do zaawansowanych funkcji alertów (innych niż ochrona przed utratą danych).|
|

## <a name="beyond"></a>Beyond
<a name="Beyond"> </a>

Są to ważne środki zabezpieczeń, które są opierane na wcześniejszych pracach.

****

|Obszar|Zadanie|
|---|---|
|Zarządzanie zabezpieczeniami|<ul><li>Kontynuuj planowanie kolejnych akcji przy użyciu bezpiecznego wyniku (<https://security.microsoft.com/securescore>).</li><li>Kontynuuj regularne przeglądanie pulpitów nawigacyjnych i raportów w portalu usługi Microsoft 365 Defender, usłudze Defender dla aplikacji w chmurze i narzędziach SIEM.</li><li>Nadal szukaj i implementuj aktualizacje oprogramowania.</li><li>Zintegruj zbierania elektronicznych materiałów dowodowych z procesami reakcji prawnej i zagrożeń.</li></ul>|
|Ochrona przed zagrożeniami|<ul><li>[Implementowanie bezpiecznego dostępu privileged](/windows-server/identity/securing-privileged-access/securing-privileged-access) (SPA) dla składników tożsamości w środowisku lokalnym (AD, AD FS).</li><li>Za pomocą usługi Defender for Cloud Apps możesz monitorować zagrożenia niejawnego programu testów.</li><li>Odkryj shadow IT SaaS usage (Użycie saaS w tle) za pomocą programu Defender dla aplikacji w chmurze.</li></ul>|
|Zarządzanie tożsamością i dostępem|<ul><li>Uściślij zasady i procesy operacyjne.</li><li>Za pomocą usługi Azure AD Identity Protection możesz identyfikować zagrożenia niejawnego programu testów.</li></ul>|
|Ochrona informacji|Uściślij zasady ochrony informacji: <ul><li>Microsoft 365 i Office 365 etykiety wrażliwości i ochrony przed utratą danych (DLP) lub usługi Azure Information Protection.</li><li>Zasady i alerty dotyczące usługi Defender for Cloud Apps.</li></ul>|
|

Zobacz też: [Jak zminimalizować szybkie cyberataki, takie jak Petya i WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
