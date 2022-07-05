---
title: 12 najważniejszych zadań dla zespołów zabezpieczeń do obsługi pracy z domu
f1.keywords:
- CSH
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- remotework
ms.custom: admindeeplinkDEFENDER
description: Ochrona firmowych wiadomości e-mail i danych przed zagrożeniami cybernetycznymi, w tym oprogramowaniem wymuszającym okup, wyłudzaniem informacji i złośliwymi załącznikami.
ms.openlocfilehash: bc1dd84e83e5c5f1828e65203585d38acc28de5e
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617265"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>12 najważniejszych zadań dla zespołów zabezpieczeń do obsługi pracy z domu

Jeśli jesteś jak [firma Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) i nagle znajdziesz wsparcie głównie pracowników domowych, chcemy pomóc Ci upewnić się, że Twoja organizacja pracuje tak bezpiecznie, jak to możliwe. Ten artykuł określa priorytety zadań, aby pomóc zespołom zabezpieczeń w jak najkrótszym wdrożeniu najważniejszych funkcji zabezpieczeń.

:::image type="content" source="../media/security/security-support-remote-work.png" alt-text="Najważniejsze zadania do wykonania w celu obsługi pracy z domu" lightbox="../media/security/security-support-remote-work.png":::


Jeśli jesteś małą lub średnią organizacją korzystającą z jednego z planów biznesowych firmy Microsoft, zobacz następujące zasoby:

- [Najlepsze rozwiązania dotyczące zabezpieczania planów platformy Microsoft 365 dla firm](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 for Campaigns](../business-premium/index.md) (obejmuje zalecaną konfigurację zabezpieczeń dla platformy Microsoft 365 Business)

W przypadku klientów korzystających z naszych planów dla przedsiębiorstw firma Microsoft zaleca wykonanie zadań wymienionych w poniższej tabeli, które mają zastosowanie do planu usługi. Jeśli zamiast kupować plan platformy Microsoft 365 enterprise, łączysz subskrypcje, zwróć uwagę na następujące kwestie:

- Microsoft 365 E3 obejmuje Enterprise Mobility + Security (EMS) E3 i Azure AD P1
- Microsoft 365 E5 obejmuje EMS E5 i Azure AD P2

****

|Krok|Zadanie|Wszystkie plany Office 365 Enterprise|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[Włączanie Azure AD uwierzytelniania wieloskładnikowego (MFA)](#1-enable-azure-ad-multi-factor-authentication-mfa)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[Ochrona przed zagrożeniami](#2-protect-against-threats)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Konfigurowanie Ochrona usługi Office 365 w usłudze Microsoft Defender](#3-configure-microsoft-defender-for-office-365)|||![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[Konfigurowanie Microsoft Defender for Identity](#4-configure-microsoft-defender-for-identity)|||![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[Włączanie usługi Microsoft 365 Defender](#5-turn-on-microsoft-365-defender)|||![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[Konfigurowanie ochrony aplikacji mobilnych Intune dla telefonów i tabletów](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[Konfigurowanie uwierzytelniania wieloskładnikowego i dostępu warunkowego dla gości, w tym Intune ochrony aplikacji](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[Rejestrowanie komputerów w zarządzaniu urządzeniami i wymaganie zgodnych komputerów](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[Optymalizowanie sieci pod kątem łączności w chmurze](#9-optimize-your-network-for-cloud-connectivity)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[Szkolenie użytkowników](#10-train-users)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[Wprowadzenie do usługi Microsoft Defender for Cloud Apps](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[Monitorowanie pod kątem zagrożeń i podjęcie akcji](#12-monitor-for-threats-and-take-action)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Zawarte.](../media/d238e041-6854-4a78-9141-049224df0795.png)|

Przed rozpoczęciem sprawdź wskaźnik [bezpieczeństwa platformy Microsoft 365](./defender/microsoft-secure-score.md) w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>. Ze scentralizowanego pulpitu nawigacyjnego można monitorować i ulepszać zabezpieczenia tożsamości, danych, aplikacji, urządzeń i infrastruktury platformy Microsoft 365. Otrzymujesz punkty dotyczące konfigurowania zalecanych funkcji zabezpieczeń, wykonywania zadań związanych z zabezpieczeniami (takich jak wyświetlanie raportów) lub rozwiązywania problemów z zaleceniami za pomocą aplikacji lub oprogramowania innej firmy. Zalecane zadania w tym artykule podniosą twój wynik.

:::image type="content" source="../media/secure-score.png" alt-text="Ekran Wskaźnik bezpieczeństwa firmy Microsoft w portalu Microsoft 365 Defender" lightbox="../media/secure-score.png":::

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1: Włączanie uwierzytelniania wieloskładnikowego Azure AD (MFA)

Najlepszą rzeczą, jaką możesz zrobić, aby zwiększyć bezpieczeństwo pracowników pracujących z domu, jest włączenie uwierzytelniania wieloskładnikowego. Jeśli nie masz jeszcze procesów, traktuj to jako pilotaż awaryjny i upewnij się, że masz pracowników pomocy technicznej gotowych pomóc pracownikom, którzy utkną. Ponieważ prawdopodobnie nie można rozpowszechniać sprzętowych urządzeń zabezpieczających, użyj Windows Hello biometrii i aplikacji do uwierzytelniania smartfonów, takich jak Microsoft Authenticator.

Zwykle firma Microsoft zaleca użytkownikom 14 dni na zarejestrowanie urządzenia na potrzeby uwierzytelniania wieloskładnikowego przed wymaganiem uwierzytelniania wieloskładnikowego. Jeśli jednak pracownicy nagle pracują z domu, przejdź do przodu i wymagaj uwierzytelniania wieloskładnikowego jako priorytetu zabezpieczeń i przygotuj się na pomoc użytkownikom, którzy tego potrzebują.

Zastosowanie tych zasad potrwa tylko kilka minut, ale będzie przygotowane do obsługi użytkowników w ciągu najbliższych kilku dni.

****

|Plan|Zalecenie|
|---|---|
|Plany platformy Microsoft 365 (bez Azure AD P1 lub P2)|[Włącz wartości domyślne zabezpieczeń w Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Ustawienia domyślne zabezpieczeń w Azure AD obejmują uwierzytelnianie wieloskładnikowe dla użytkowników i administratorów.|
|Microsoft 365 E3 (z Azure AD P1)|Użyj [typowych zasad dostępu warunkowego](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) , aby skonfigurować następujące zasady: <br/>- [Wymagaj uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [Wymagaj uwierzytelniania wieloskładnikowego dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [Blokowanie starszego uwierzytelniania](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (z Azure AD P2)|Korzystając z usługi Azure AD Identity Protection, rozpocznij implementowanie [zalecanego przez firmę Microsoft zestawu dostępu warunkowego i powiązanych zasad](./office-365-security/identity-access-policies.md), tworząc następujące zasady:<br/> - [Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest średnie lub wysokie](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [Blokuj klientów, którzy nie obsługują nowoczesnego uwierzytelniania](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [Użytkownicy wysokiego ryzyka muszą zmienić hasło](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|

## <a name="2-protect-against-threats"></a>2: Ochrona przed zagrożeniami

Wszystkie plany platformy Microsoft 365 obejmują różne funkcje ochrony przed zagrożeniami. Wzbożanie ochrony tych funkcji zajmuje zaledwie kilka minut.

- Ochrona przed złośliwym oprogramowaniem
- Ochrona przed złośliwymi adresami URL i plikami
- Ochrona przed wyłudzaniem informacji
- Ochrona przed spamem

Aby uzyskać wskazówki, których można użyć jako punktu początkowego, zobacz [Ochrona przed zagrożeniami w Office 365](office-365-security/protect-against-threats.md).

## <a name="3-configure-microsoft-defender-for-office-365"></a>3: Konfigurowanie Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender, dołączone do Microsoft 365 E5 i Office 365 E5, chroni organizację przed złośliwymi zagrożeniami, jakie stwarzają wiadomości e-mail, linki (adresy URL) i narzędzia do współpracy. Konfiguracja może potrwać kilka godzin.

Ochrona usługi Office 365 w usłudze Microsoft Defender:

- Chroni organizację przed nieznanymi zagrożeniami poczty e-mail w czasie rzeczywistym przy użyciu inteligentnych systemów, które sprawdzają załączniki i linki pod kątem złośliwej zawartości. Te zautomatyzowane systemy obejmują niezawodną platformę detonacji, heurystykę i modele uczenia maszynowego.
- Chroni organizację, gdy użytkownicy współpracują i udostępniają pliki, identyfikując i blokując złośliwe pliki w witrynach zespołu i bibliotekach dokumentów.
- Stosuje modele uczenia maszynowego i zaawansowane algorytmy wykrywania personifikacji, aby zapobiec atakom wyłudzającym informacje.

Aby zapoznać się z omówieniem, w tym podsumowaniem planów, zobacz [Ochrona usługi Office 365 w usłudze Defender](./office-365-security/defender-for-office-365.md).

Administrator globalny może skonfigurować następujące zabezpieczenia:

- [Konfigurowanie zasad bezpiecznych łączy](office-365-security/set-up-safe-links-policies.md)
- [Konfigurowanie ustawień globalnych dla bezpiecznych linków](office-365-security/configure-global-settings-for-safe-links.md)
- [Konfigurowanie zasad bezpiecznych załączników](office-365-security/set-up-safe-attachments-policies.md)

Aby skonfigurować Ochrona usługi Office 365 w usłudze Defender dla tych obciążeń, musisz współpracować z administratorem Exchange Online i administratorem usługi SharePoint Online:

- [Ochrona punktu końcowego w usłudze Microsoft Defender dla programów SharePoint, OneDrive i Microsoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4: Konfigurowanie Microsoft Defender for Identity

[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) to oparte na chmurze rozwiązanie zabezpieczeń, które wykorzystuje sygnały lokalna usługa Active Directory do identyfikowania, wykrywania i badania zaawansowanych zagrożeń, tożsamości z naruszeniem zabezpieczeń i złośliwych akcji wewnętrznych skierowanych do organizacji. Skoncentruj się na tym następnym, ponieważ chroni on twoją infrastrukturę lokalną i infrastrukturę chmury, nie ma zależności ani wymagań wstępnych i może zapewnić natychmiastowe korzyści.

- Zobacz [Microsoft Defender for Identity Przewodniki Szybki start,](/azure-advanced-threat-protection/install-atp-step1) aby szybko skonfigurować
- Obejrzyj [wideo: Wprowadzenie do Microsoft Defender for Identity](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- Przejrzyj [trzy fazy wdrażania Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5: Włącz Microsoft 365 Defender

Po skonfigurowaniu Ochrona usługi Office 365 w usłudze Microsoft Defender i Microsoft Defender for Identity możesz wyświetlić połączone sygnały z tych funkcji na jednym pulpicie nawigacyjnym. [Microsoft 365 Defender](./defender/microsoft-365-defender.md) łączy alerty, zdarzenia, zautomatyzowane badanie i reagowanie oraz zaawansowane wyszukiwanie zagrożeń w różnych obciążeniach (Microsoft Defender for Identity, Ochrona usługi Office 365 w usłudze Defender, Microsoft Defender dla punktu końcowego i Microsoft Defender for Cloud Apps) w jednym okienku w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.

:::image type="content" source="../media/top-ten-security-remote-work-mtp-dashboard.png" alt-text="Pulpit nawigacyjny Microsoft 365 Defender" lightbox="../media/top-ten-security-remote-work-mtp-dashboard.png":::

Po skonfigurowaniu co najmniej jednej usługi Ochrona usługi Office 365 w usłudze Defender włącz usługę MTP. Nowe funkcje są stale dodawane do protokołu MTP; rozważ zgodę na otrzymywanie funkcji w wersji zapoznawczej.

- [Dowiedz się więcej o usłudze MTP](./defender/microsoft-365-defender.md)
- [Włączanie protokołu MTP](./defender/m365d-enable.md)
- [Zgoda na funkcje w wersji zapoznawczej](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6: Konfigurowanie ochrony aplikacji mobilnych Intune dla telefonów i tabletów

Microsoft Intune Zarządzanie aplikacjami mobilnymi (MAM) umożliwia zarządzanie danymi organizacji i ochronę ich na telefonach i tabletach bez zarządzania tymi urządzeniami. Oto jak to działa:

- Tworzysz zasady ochrony aplikacji (APP), które określają, które aplikacje na urządzeniu są zarządzane i jakie zachowania są dozwolone (na przykład uniemożliwiające kopiowanie danych z aplikacji zarządzanej do niezarządzanej aplikacji). Tworzysz jedną zasadę dla każdej platformy (iOS, Android).
- Po utworzeniu zasad ochrony aplikacji wymuszasz je, tworząc regułę dostępu warunkowego w Azure AD, aby wymagać zatwierdzonych aplikacji i ochrony danych aplikacji.

Zasady ochrony aplikacji zawierają wiele ustawień. Na szczęście nie musisz uczyć się o każdym ustawieniu i ważyć opcji. Firma Microsoft ułatwia stosowanie konfiguracji ustawień, zalecając punkty początkowe. [Struktura ochrony danych korzystająca z zasad ochrony aplikacji](/mem/intune/apps/app-protection-framework) obejmuje trzy poziomy, z które można wybrać.

Co więcej, firma Microsoft koordynuje tę strukturę ochrony aplikacji za pomocą zestawu dostępu warunkowego i powiązanych zasad, których zalecamy wszystkim organizacjom jako punkt wyjścia. Jeśli zaimplementowaliśmy uwierzytelnianie wieloskładnikowe, korzystając ze wskazówek przedstawionych w tym artykule, jesteś w połowie drogi.

Aby skonfigurować ochronę aplikacji mobilnych, skorzystaj ze wskazówek w temacie [Typowe zasady dostępu do tożsamości i urządzeń](./office-365-security/identity-access-policies.md):

 1. Skorzystaj ze wskazówek dotyczących [stosowania zasad ochrony danych aplikacji](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) , aby utworzyć zasady dla systemów iOS i Android. Poziom 2 (rozszerzona ochrona danych) jest zalecany do ochrony punktu odniesienia.
 2. Utwórz regułę dostępu warunkowego w obszarze [Wymagaj zatwierdzonych aplikacji i ochrony aplikacji](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7: Konfigurowanie uwierzytelniania wieloskładnikowego i dostępu warunkowego dla gości, w tym Intune ochrony aplikacji mobilnych

Następnie upewnijmy się, że możesz kontynuować współpracę i pracować z gośćmi. Jeśli używasz planu Microsoft 365 E3 i zaimplementowano uwierzytelnianie wieloskładnikowe dla wszystkich użytkowników, zostanie ustawiona.

Jeśli używasz planu Microsoft 365 E5 i korzystasz z usługi Azure Identity Protection na potrzeby uwierzytelniania wieloskładnikowego opartego na ryzyku, musisz wprowadzić kilka korekt (ponieważ Azure AD Ochrona tożsamości nie obejmuje gości):

- Utwórz nową regułę dostępu warunkowego, aby zawsze wymagać uwierzytelniania wieloskładnikowego dla gości i użytkowników zewnętrznych.
- Zaktualizuj regułę dostępu warunkowego uwierzytelniania wieloskładnikowego opartą na ryzyku, aby wykluczyć gości i użytkowników zewnętrznych.

Skorzystaj ze wskazówek w [temacie Aktualizowanie typowych zasad, aby umożliwić i chronić dostęp gościa i dostępu zewnętrznego](./office-365-security/identity-access-policies-guest-access.md), aby zrozumieć, jak dostęp gościa działa z Azure AD i zaktualizować zasady, których dotyczy problem.

Utworzone zasady ochrony aplikacji mobilnych Intune wraz z regułą dostępu warunkowego w celu wymagania zatwierdzonych aplikacji i ochrony aplikacji mają zastosowanie do kont gości i ułatwiają ochronę danych organizacji.

> [!NOTE]
> Jeśli komputery zostały już zarejestrowane w usłudze zarządzania urządzeniami w celu wymagania zgodnych komputerów, należy również wykluczyć konta gościa z reguły dostępu warunkowego, która wymusza zgodność urządzeń.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8: Rejestrowanie komputerów w zarządzaniu urządzeniami i wymaganie zgodnych komputerów

Istnieje kilka metod rejestrowania urządzeń pracowników. Każda metoda zależy od własności urządzenia (osobistej lub firmowej), typu urządzenia (iOS, Windows, Android) i wymagań dotyczących zarządzania (resetowania, koligacji, blokowania). Może to zająć trochę czasu, aby uporządkować. Zobacz: [Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/enrollment/).

Najszybszym sposobem rozpoczęcia pracy jest [skonfigurowanie automatycznej rejestracji dla urządzeń Windows 10](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

Możesz również skorzystać z następujących samouczków:

- [Rejestrowanie urządzeń z systemem Windows w Intune przy użyciu rozwiązania Autopilot](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [Rejestrowanie urządzeń z systemem iOS/iPadOS w Intune przy użyciu funkcji rejestracji urządzeń firmowych firmy Apple w programie Apple Business Manager (ABM)](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Po zarejestrowaniu urządzeń skorzystaj ze wskazówek w temacie [Typowe zasady dostępu do tożsamości i urządzeń](./office-365-security/identity-access-policies.md) , aby utworzyć następujące zasady:

- [Definiowanie zasad zgodności urządzeń](./office-365-security/identity-access-policies.md#define-device-compliance-policies) — zalecane ustawienia dla Windows 10 obejmują wymaganie ochrony antywirusowej. Jeśli masz Microsoft 365 E5, użyj Ochrona punktu końcowego w usłudze Microsoft Defender, aby monitorować kondycję urządzeń pracowników. Upewnij się, że zasady zgodności dla innych systemów operacyjnych obejmują ochronę antywirusową i oprogramowanie do ochrony punktu końcowego.
- [Wymagaj zgodnych komputerów](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) — jest to reguła dostępu warunkowego w Azure AD, która wymusza zasady zgodności urządzeń.

Tylko jedna organizacja może zarządzać urządzeniem, dlatego należy wykluczyć konta gościa z reguły dostępu warunkowego w Azure AD. Jeśli nie wykluczysz gościa i użytkowników zewnętrznych z zasad wymagających zgodności urządzeń, te zasady zablokują tych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktualizowanie typowych zasad w celu zezwolenia i ochrony dostępu gościa i dostępu zewnętrznego](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9: Optymalizowanie sieci pod kątem łączności w chmurze

Jeśli szybko włączasz większość pracowników do pracy z domu, to nagłe przełączenie wzorców łączności może mieć znaczący wpływ na infrastrukturę sieci firmowej. Wiele sieci zostało skalowanych i zaprojektowanych przed wdrożeniem usług w chmurze. W wielu przypadkach sieci są odporne na zdalne procesy robocze, ale nie zostały zaprojektowane tak, aby były używane zdalnie przez wszystkich użytkowników jednocześnie.

Elementy sieciowe, takie jak koncentratory sieci VPN, centralne urządzenia wychodzące sieci (takie jak serwery proxy i urządzenia zapobiegające utracie danych), centralna przepustowość Internetu, obwody MPLS typu backhaul, możliwość translatora adresów sieciowych i tak dalej są nagle obciążane ze względu na obciążenie całej firmy korzystającej z nich. Efektem końcowym jest niska wydajność i produktywność w połączeniu ze słabym środowiskiem użytkownika dla użytkowników, którzy dostosowują się do pracy z domu.

Niektóre zabezpieczenia, które tradycyjnie były zapewniane przez kierowanie ruchu z powrotem przez sieć firmową, są udostępniane przez aplikacje w chmurze, do których uzyskują dostęp użytkownicy. Jeśli ten krok został osiągnięty w tym artykule, zaimplementowano zestaw zaawansowanych mechanizmów kontroli zabezpieczeń w chmurze dla usług i danych platformy Microsoft 365. Dzięki tym kontrolom możesz być gotowy do kierowania ruchu użytkowników zdalnych bezpośrednio do Office 365. Jeśli nadal potrzebujesz linku sieci VPN w celu uzyskania dostępu do innych aplikacji, możesz znacznie poprawić wydajność i środowisko użytkownika, implementując tunelowanie podzielone. Po osiągnięciu porozumienia w organizacji może to osiągnąć w ciągu dnia dobrze skoordynowany zespół ds. sieci.

Aby uzyskać więcej informacji, zobacz te zasoby w witrynie Docs:

- [Omówienie: Optymalizowanie łączności dla użytkowników zdalnych przy użyciu tunelowania podzielonego sieci VPN](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [Implementowanie tunelowania podzielonego sieci VPN dla Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Ostatnie artykuły w blogu dotyczące tego tematu:

- [Jak szybko zoptymalizować ruch dla zdalnego personelu, & zmniejszyć obciążenie infrastruktury](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Alternatywne sposoby zapewniania przez specjalistów ds. zabezpieczeń i it nowoczesnych mechanizmów kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10: Szkolenie użytkowników

Użytkownicy szkolący mogą zaoszczędzić dużo czasu i frustracji swoim użytkownikom i zespołowi ds. operacji zabezpieczeń. Doświadczeni użytkownicy są mniej skłonni do otwierania załączników lub klikania linków w wątpliwych wiadomościach e-mail i są bardziej skłonni do unikania podejrzanych witryn internetowych.

[Podręcznik kampanii cyberbezpieczeństwa](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) Harvard Kennedy School zawiera doskonałe wskazówki dotyczące ustanawiania silnej kultury świadomości bezpieczeństwa w organizacji, w tym szkolenia użytkowników w celu identyfikowania ataków wyłudzających informacje.

Platforma Microsoft 365 udostępnia następujące zasoby ułatwiające informowanie użytkowników w organizacji:

****

|Koncepcja|Zasoby|
|---|---|
|Microsoft 365|[Dostosowywalne ścieżki szkoleniowe](/office365/customlearning/) <p>Te zasoby mogą pomóc w zebraniu szkoleń dla użytkowników końcowych w organizacji|
|Zabezpieczenia platformy Microsoft 365|[Moduł szkoleniowy: Zabezpieczanie organizacji za pomocą wbudowanych, inteligentnych zabezpieczeń z platformy Microsoft 365](/learn/modules/security-with-microsoft-365) <p>Ten moduł umożliwia opisanie współpracy funkcji zabezpieczeń platformy Microsoft 365 oraz przedstawienie korzyści wynikających z tych funkcji zabezpieczeń.|
|Uwierzytelnianie wieloskładnikowe|[Weryfikacja dwuetapowa: Jaka jest dodatkowa strona weryfikacji?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Ten artykuł pomaga użytkownikom końcowym zrozumieć, czym jest uwierzytelnianie wieloskładnikowe i dlaczego jest używane w organizacji.|

Oprócz tych wskazówek firma Microsoft zaleca użytkownikom podjęcie działań opisanych w tym artykule: [Ochrona konta i urządzeń przed hakerami i złośliwym oprogramowaniem](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Te akcje obejmują:

- Używanie silnych haseł
- Ochrona urządzeń
- Włączanie funkcji zabezpieczeń na komputerach Windows 10 i Mac (w przypadku urządzeń niezarządzanych)

Firma Microsoft zaleca również, aby użytkownicy chronili swoje osobiste konta e-mail, wykonując akcje zalecane w następujących artykułach:

- [Ochrona konta e-mail Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Ochrona konta Gmail za pomocą weryfikacji dwuetapowej](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: Rozpoczynanie pracy z Microsoft Defender for Cloud Apps

[Microsoft Defender for Cloud Apps](/cloud-app-security) zapewnia bogaty wgląd, kontrolę nad przenoszeniem danych i zaawansowane analizy umożliwiające identyfikowanie i zwalczanie cyberoszertw we wszystkich usługach w chmurze. Po rozpoczęciu pracy z usługą Defender for Cloud Apps zasady wykrywania anomalii są automatycznie włączone, ale usługa Defender for Cloud Apps ma początkowy okres nauki wynoszący siedem dni, podczas którego nie są zgłaszane wszystkie alerty wykrywania anomalii.

Rozpocznij pracę z usługą Defender for Cloud Apps. Później można skonfigurować bardziej zaawansowane monitorowanie i kontrolki.

- [Szybki start: rozpoczynanie pracy z usługą Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Uzyskiwanie natychmiastowej analizy behawioralnej i wykrywania anomalii](/cloud-app-security/anomaly-detection-policy)
- [Dowiedz się więcej o Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Przejrzyj nowe funkcje i możliwości](/cloud-app-security/release-notes)
- [Zobacz podstawowe instrukcje dotyczące konfiguracji](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: Monitorowanie zagrożeń i podjęcie działań

Platforma Microsoft 365 obejmuje kilka sposobów monitorowania stanu i podejmowania odpowiednich działań. Najlepszym punktem wyjścia jest <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portal Microsoft 365 Defender</a>, w którym można wyświetlić [wskaźnik Microsoft Secure Score](./defender/microsoft-secure-score.md) organizacji oraz wszelkie alerty lub jednostki, które wymagają uwagi.

- [Wprowadzenie do portalu Microsoft 365 Defender](./defender/microsoft-365-defender-portal.md)
- [Zobacz portale zabezpieczeń na platformie Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>Następne kroki

Gratulacje! Szybko zaimplementowano niektóre z najważniejszych zabezpieczeń, a Twoja organizacja jest znacznie bezpieczniejsza. Teraz możesz przejść jeszcze dalej dzięki funkcjom ochrony przed zagrożeniami (w tym Ochrona punktu końcowego w usłudze Microsoft Defender), możliwościom klasyfikacji i ochrony danych oraz zabezpieczaniu kont administracyjnych. Aby uzyskać dokładniejszy, metodyczny zestaw zaleceń dotyczących zabezpieczeń dla platformy Microsoft 365, zobacz [Microsoft 365 Security for Business Decision Makers (BDMs)](Microsoft-365-security-for-bdm.md).

Odwiedź również nową usługę Defender for Cloud firmy Microsoft na [docs.microsoft.com/security](/security).
