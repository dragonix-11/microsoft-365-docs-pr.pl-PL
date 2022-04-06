---
title: 12 najlepszych zadań dla zespołów ds. zabezpieczeń na rzecz obsługi pracy z domu
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
description: Chroń służbową pocztę e-mail i dane przed zagrożeniami cyberzagrożeniami, w tym oprogramowaniem wymuszającym okup, wyłudzaniem informacji i złośliwymi załącznikami.
ms.openlocfilehash: 7f5c52eb0768adc4c64251ed7c3f34cccdf9cd57
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469454"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>12 najlepszych zadań dla zespołów ds. zabezpieczeń na rzecz obsługi pracy z domu

Jeśli podoba Ci się [firma Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) , ale nagle okazało się, że obsługujesz głównie pracowników domowych, chcemy pomóc Ci zapewnić, że Twoja organizacja pracuje tak bezpiecznie, jak to możliwe. W tym artykule priorytetyzują zadania, aby ułatwić zespołom zabezpieczeń jak najszybciej zaimplementowanie najważniejszych funkcji zabezpieczeń.

:::image type="content" source="../media/security/security-support-remote-work.png" alt-text="Najważniejsze zadania do wykonania na rzecz obsługi pracy w domu" lightbox="../media/security/security-support-remote-work.png":::


Jeśli korzystasz z jednego z planów firmy Microsoft dla firm w małej lub średniej organizacji, zamiast tego zobacz następujące zasoby:

- [10 najlepszych sposobów zabezpieczania Office 365 i Microsoft 365 dla firm](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 kampanii](../business-premium/index.md) (zawiera zalecaną konfigurację zabezpieczeń dla usługi Microsoft 365 Firm)

W przypadku klientów korzystających z planów dla przedsiębiorstw firma Microsoft zaleca wykonywanie zadań wymienionych w poniższej tabeli dotyczące Twojego planu usług. Jeśli zamiast wykupić plan dla przedsiębiorstwa Microsoft 365, łączysz subskrypcje, zwróć uwagę na następujące kwestie:

- Microsoft 365 E3 obejmuje Enterprise Mobility + Security (EMS) E3 i Azure AD P1
- Microsoft 365 E5 obejmuje usługi EMS E5 i Azure AD P2

****

|Krok|Zadanie|Wszystkie Office 365 Enterprise planów|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[Włączanie uwierzytelniania wieloskładnikowego usługi Azure AD](#1-enable-azure-ad-multi-factor-authentication-mfa)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[Ochrona przed zagrożeniami](#2-protect-against-threats)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Konfigurowanie Ochrona usługi Office 365 w usłudze Microsoft Defender](#3-configure-microsoft-defender-for-office-365)|||![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[Konfigurowanie Microsoft Defender for Identity](#4-configure-microsoft-defender-for-identity)|||![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[Włączanie usługi Microsoft 365 Defender](#5-turn-on-microsoft-365-defender)|||![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[Konfigurowanie Intune aplikacji mobilnej dla telefonów i tabletów](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[Konfigurowanie uwierzytelniania wieloskładnikowego i dostępu warunkowego dla gości, w tym Intune aplikacji](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[Rejestrowanie komputerów do zarządzania urządzeniami i wymaganie zgodnych komputerów](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[Optymalizowanie sieci pod kątem łączności z chmurą](#9-optimize-your-network-for-cloud-connectivity)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Uwzględnione](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[Szkolenie użytkowników](#10-train-users)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[Wprowadzenie do usługi Microsoft Defender for Cloud Apps](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[Monitorowanie zagrożeń i działania](#12-monitor-for-threats-and-take-action)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Dołączona.](../media/d238e041-6854-4a78-9141-049224df0795.png)|

Przed rozpoczęciem należy sprawdzić wynik [Microsoft 365 w portalu Microsoft 365 Defender](./defender/microsoft-secure-score.md) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">sieci.</a> Za pomocą scentralizowanego pulpitu nawigacyjnego możesz monitorować i ulepszać zabezpieczenia tożsamości, Microsoft 365, danych, aplikacji, urządzeń i infrastruktury. Masz punkty za skonfigurowanie zalecanych funkcji zabezpieczeń, wykonywanie zadań związanych z zabezpieczeniami (takich jak wyświetlanie raportów) lub adresowanie rekomendacji za pomocą aplikacji lub oprogramowania innej firmy. Zadania zalecane w tym artykule podniesie Twój wynik.

:::image type="content" source="../media/secure-score.png" alt-text="Ekran bezpiecznego wyniku firmy Microsoft w portalu Microsoft 365 Defender sieci Microsoft 365 Defender" lightbox="../media/secure-score.png":::

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1. Włączanie uwierzytelniania wieloskładnikowego usługi Azure AD

Najlepszą rzeczą, jaką można zrobić, aby zwiększyć bezpieczeństwo pracowników pracujących z domu, jest włączenie uwierzytelniania wieloskładnikowego. Jeśli nie masz jeszcze procesów, potraktuj go jako pilotażu alarmowego i upewnij się, że pracownicy pomocy technicznej są gotowi pomagać pracownikom, którzy utknęli. Jak prawdopodobnie nie możesz rozpowszechniać urządzeń zabezpieczających sprzętowych, używaj biometrycznych Windows Hello aplikacji do uwierzytelniania smartfonów, takich jak Microsoft Authenticator.

Zwykle firma Microsoft zaleca, aby przed wymaganiem uwierzytelniania wieloskładnikowego dać użytkownikom 14 dni na zarejestrowanie urządzenia na potrzeby uwierzytelniania wieloskładnikowego. Jeśli jednak twój pracownik nagle pracuje w domu, możesz wymagać uwierzytelniania wieloskładnikowego jako priorytetu zabezpieczeń i przygotować się do pomagania użytkownikom, którzy go potrzebują.

Zastosowanie tych zasad zajmie tylko kilka minut, ale należy przygotować się do obsługi użytkowników w ciągu następnych kilku dni.

****

|Plan|Zalecenie|
|---|---|
|Microsoft 365 (bez planu Azure AD P1 lub P2)|[Włącz domyślne ustawienia zabezpieczeń w usłudze Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Wartości domyślne zabezpieczeń w usłudze Azure AD obejmują uwierzytelniania wieloskładnikowe dla użytkowników i administratorów.|
|Microsoft 365 E3 (z usługą Azure AD P1)|Użyj [typowych zasad dostępu warunkowego,](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) aby skonfigurować następujące zasady: <br/>- [Wymaganie uwierzytelniania wieloskładnikowego dla administratorów](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [Wymaganie uwierzytelniania WIELOSKŁADNIKOWEGO dla wszystkich użytkowników](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [Blokowanie starszego uwierzytelniania](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (z usługą Azure AD P2)|Korzystając z usługi Azure AD Identity Protection, zacznij implementować zalecany przez firmę Microsoft [zestaw](./office-365-security/identity-access-policies.md) dostępu warunkowego i pokrewnych zasad, tworząc te zasady:<br/> - [Wymagaj uwierzytelniania wieloskładnikowego, gdy ryzyko logowania jest średnie lub wysokie](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [Blokowanie klientów, którzy nie obsługują nowoczesnego uwierzytelniania](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [Zmiana hasła przez użytkowników o wysokim poziomie ryzyka](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|

## <a name="2-protect-against-threats"></a>2. Ochrona przed zagrożeniami

Wszystkie Microsoft 365 zawierają szereg funkcji ochrony przed zagrożeniami. Ochrona w sposób nierówny dla tych funkcji trwa zaledwie kilka minut.

- Ochrona przed złośliwym oprogramowaniem
- Ochrona przed złośliwymi adresami URL i plikami
- Ochrona przed wyłudzaniem informacji
- Ochrona przed spamem

Zobacz [Ochrona przed zagrożeniami Office 365](office-365-security/protect-against-threats.md), aby uzyskać wskazówki, których możesz użyć jako punktu wyjścia.

## <a name="3-configure-microsoft-defender-for-office-365"></a>3. Konfigurowanie Ochrona usługi Office 365 w usłudze Microsoft Defender

Ochrona usługi Office 365 w usłudze Microsoft Defender, dostępne w p Microsoft 365 E5 i Office 365 E5, chroni organizację przed złośliwymi zagrożeniami ze strony wiadomości e-mail, linków (adresów URL) i narzędzi do współpracy. Konfigurowanie tej opcji może potrwać kilka godzin.

Ochrona usługi Office 365 w usłudze Microsoft Defender:

- Zapewnia ochronę organizacji przed nieznanymi zagrożeniami dla poczty e-mail w czasie rzeczywistym za pomocą inteligentnych systemów sprawdzanych załączniki i linki w celu zabezpieczenia złośliwej zawartości. Te automatyczne systemy obejmują solidną platformę detonacji, heuristics i modele uczenia maszynowego.
- Chroni organizację, gdy użytkownicy współpracują i udostępniają pliki, identyfikując i blokując złośliwe pliki w witrynach  zespołowych i bibliotekach dokumentów.
- Stosuje modele uczenia maszynowego i algorytmy zaawansowanego wykrywania personifikacji w celu odwrócić ataki służące do wyłudzania informacji.

Aby uzyskać omówienie, w tym podsumowanie planów[, zobacz Ochrona usługi Office 365 w usłudze Defender](./office-365-security/defender-for-office-365.md).

Administrator globalny może skonfigurować następujące zabezpieczenia:

- [Konfigurowanie zasad Sejf linków](office-365-security/set-up-safe-links-policies.md)
- [Konfigurowanie ustawień globalnych dla linków Sejf sieci](office-365-security/configure-global-settings-for-safe-links.md)
- [Konfigurowanie zasad Sejf załączników](office-365-security/set-up-safe-attachments-policies.md)

Musisz współpracować z administratorem usługi Exchange Online i administratorem usługi SharePoint Online, aby Ochrona usługi Office 365 w usłudze Defender tych obciążeń:

- [Ochrona punktu końcowego w usłudze Microsoft Defender dla SharePoint, OneDrive i Microsoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4. Konfigurowanie Microsoft Defender for Identity

[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) to oparte na chmurze rozwiązanie zabezpieczeń, które wykorzystuje sygnały lokalna usługa Active Directory do identyfikowania, wykrywania i badanie zaawansowanych zagrożeń, naruszonych tożsamości i złośliwych działań niejawnych testerów skierowanych do organizacji. Skoncentruj się na tym w następnej sprawie, ponieważ chroni on infrastrukturę w infrastrukturze hybrydowej i chmurę, nie ma żadnych zależności ani wymagań wstępnych i może zapewnić natychmiastową korzyść.

- Zobacz [Microsoft Defender for Identity Szybki start, aby](/azure-advanced-threat-protection/install-atp-step1) szybko rozpocząć konfigurację
- Obejrzyj [klip wideo: wprowadzenie do Microsoft Defender for Identity](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- Przejrzyj trzy [fazy wdrożenia Microsoft Defender for Identity projektu](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5. Włączanie Microsoft 365 Defender

Po skonfigurowaniu Ochrona usługi Office 365 w usłudze Microsoft Defender i Microsoft Defender for Identity możesz wyświetlać połączone sygnały z tych funkcji na jednym pulpicie nawigacyjnym. [Microsoft 365 Defender](./defender/microsoft-365-defender.md) zawiera alerty, zdarzenia, zautomatyzowane badania i odpowiedzi oraz zaawansowane szukanie pracy (Microsoft Defender for Identity, Ochrona usługi Office 365 w usłudze Defender, Microsoft Defender dla Endpoint (Punkt Microsoft Defender for Cloud Apps) do jednego okienka w Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">sieci Web</a>.

:::image type="content" source="../media/top-ten-security-remote-work-mtp-dashboard.png" alt-text="Pulpit Microsoft 365 Defender nawigacyjny" lightbox="../media/top-ten-security-remote-work-mtp-dashboard.png":::

Po skonfigurowaniu co najmniej jednej z usług Ochrona usługi Office 365 w usłudze Defender mtp włącz usługę MTP. Nowe funkcje są stale dodawane do mtp; rozważ zgodę na otrzymywanie funkcji wersji Preview.

- [Dowiedz się więcej o MTP](./defender/microsoft-365-defender.md)
- [Włącz MTP](./defender/m365d-enable.md)
- [Opt in for preview features](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6. Konfigurowanie ochrony Intune aplikacji mobilnej dla telefonów i tabletów

Microsoft Intune zarządzanie aplikacjami mobilnymi (MAM) umożliwia zarządzanie danymi organizacji i ich ochronę na telefonach i tabletach bez zarządzania tymi urządzeniami. Oto jak to działa:

- Tworzysz zasady ochrony aplikacji (APP), które określają, które aplikacje na urządzeniu są zarządzane i jakie zachowania są dozwolone (na przykład uniemożliwianie kopiowania danych z aplikacji zarządzanej do aplikacji nieza zarządzaniem). Tworzysz jedną zasady dla każdej platformy (dla systemu iOS, Android).
- Po utworzeniu zasad ochrony aplikacji można je wymusić, tworząc regułę dostępu warunkowego w usłudze Azure AD, aby wymagać zatwierdzonych aplikacji i ochrony danych aplikacji.

Zasady ochrony aplikacji zawierają wiele ustawień. Na szczęście nie musisz uczyć się każdego ustawienia i ważyć opcje. Firma Microsoft ułatwia stosowanie konfiguracji ustawień, polecając punkty początkowe. W [ramach struktury ochrony danych, w ramach których są zbierane zasady ochrony](/mem/intune/apps/app-protection-framework) aplikacji, można wybrać trzy poziomy.

Co więcej, firma Microsoft koordynuje tę ramę ochrony aplikacji za pomocą zestawu dostępu warunkowego i powiązanych zasad, zalecamy, aby wszystkie organizacje używać jako punktu wyjścia. Jeśli uwierzytelniania wieloskładnikowego wdrożono, korzystając z wskazówek w tym artykule, możesz to zrobić w połowie tego artykułu.

Aby skonfigurować ochronę aplikacji dla urządzeń przenośnych, skorzystaj z wskazówek w tece Wspólne [zasady dostępu do](./office-365-security/identity-access-policies.md) urządzeń i tożsamości:

 1. Aby utworzyć [zasady dla systemów](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) iOS i Android, skorzystaj ze wskazówek dotyczących stosowania zasad ochrony danych aplikacji. Poziom 2 (rozszerzona ochrona danych) jest zalecany w przypadku ochrony według planu bazowego.
 2. Utwórz regułę dostępu warunkowego [wymagaj zatwierdzonych aplikacji i ochrony aplikacji](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7. Konfigurowanie uwierzytelniania wieloskładnikowego i dostępu warunkowego dla gości, w tym Intune ochrony aplikacji dla urządzeń przenośnych

Następnie upewnijmy się, że możesz kontynuować współpracę z gośćmi. Jeśli używasz planu usługi Microsoft 365 E3 uwierzytelniania wieloskładnikowego dla wszystkich użytkowników, wszystko jest już tak ustawione.

Jeśli korzystasz z planu usługi Microsoft 365 E5 i korzystasz z usługi Azure Identity Protection na potrzeby uwierzytelniania wieloskładnikowego opartego na czynnikach ryzyka, musisz wprowadzić kilka zmian (ponieważ ochrona tożsamości usługi Azure AD nie obejmuje gości):

- Utwórz nową regułę dostępu warunkowego, aby wymagać uwierzytelniania MFA zawsze dla gości i użytkowników zewnętrznych.
- Zaktualizuj regułę dostępu warunkowego opartego na czynniku ryzyka, aby wykluczyć gości i użytkowników zewnętrznych.

Skorzystaj ze wskazówek [](./office-365-security/identity-access-policies-guest-access.md) w tece Aktualizowanie wspólnych zasad, aby zezwolić na dostęp gościa i dostęp zewnętrzny oraz chronić go, aby zrozumieć sposób działania dostępu gościa z usługą Azure AD oraz zaktualizować zasady, których to dotyczy.

Utworzone Intune ochrony aplikacji dla urządzeń przenośnych wraz z regułą dostępu warunkowego w celu wymagania zatwierdzonych aplikacji i ochrony aplikacji, dotyczą kont gości i pomagają chronić dane Twojej organizacji.

> [!NOTE]
> Jeśli masz już zarejestrowane komputery do zarządzania urządzeniami, aby wymagać zgodnych komputerów, musisz również wykluczyć konta gości z reguły dostępu warunkowego wymuszającego zgodność urządzenia.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8. Zarejestruj komputery do zarządzania urządzeniami i wymagaj zgodnych komputerów

Istnieje kilka metod zarejestrowania urządzeń pracowników. Każda metoda zależy od własności urządzenia (osobistego lub firmowego), typu urządzenia (iOS, Windows, Android) i wymagań dotyczących zarządzania (resetowanie,  koligacja, blokowanie). Jej posortowanie może zająć trochę czasu. Zobacz: [Rejestrowanie urządzeń w u Microsoft Intune](/mem/intune/enrollment/).

Najszybszym sposobem jest skonfigurowanie rejestracji automatycznej dla Windows 10 [urządzeniach](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

Możesz również skorzystać z tych samouczków:

- [Funkcja Autopilot zarejestruje Windows urządzenia w Intune](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [Skorzystaj z funkcji rejestracji firmowych urządzeń firmy Apple w apple Business Manager (ABM), aby zarejestrować urządzenia z systemem iOS/iPadOS w aplikacji Intune](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Po zarejestrowaniu urządzeń skorzystaj z wskazówek w tece Wspólne zasady dostępu do urządzeń i tożsamości [,](./office-365-security/identity-access-policies.md) aby utworzyć te zasady:

- [Definiowanie zasad zgodności urządzeń —](./office-365-security/identity-access-policies.md#define-device-compliance-policies) zalecane ustawienia dotyczące ochrony Windows 10 ochrony antywirusowej. Jeśli masz Microsoft 365 E5, użyj Ochrona punktu końcowego w usłudze Microsoft Defender do monitorowania kondycji urządzeń pracowników. Upewnij się, że zasady zgodności dla innych systemów operacyjnych obejmują ochronę antywirusową i oprogramowanie ochrony punktu końcowego.
- [Wymagaj zgodności komputerów —](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) jest to reguła dostępu warunkowego w usłudze Azure AD, która wymusza zasady zgodności urządzeń.

Urządzeniem może zarządzać tylko jedna organizacja, dlatego upewnij się, że konta gości są wykluczone z reguły dostępu warunkowego w usłudze Azure AD. Jeśli nie wykluczasz gości i użytkowników zewnętrznych z zasad wymagających zgodności urządzeń, te zasady będą blokować tych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktualizowanie typowych zasad w celu umożliwienia i ochrony dostępu gościa i dostępu zewnętrznego](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9. Optymalizowanie sieci pod kątem łączności z chmurą

Jeśli błyskawicznie włączasz pracę z domu przez większość pracowników, ten nagle przełączenie wzorców łączności może mieć istotny wpływ na firmową infrastrukturę sieciową. Wiele sieci zostało przeskalowane i zaprojektowanych przed podjęciem decyzji o usługach w chmurze. W wielu przypadkach sieci tolerują pracowników zdalnych, ale nie są zaprojektowane do jednoczesnego użycia przez wszystkich użytkowników zdalnie.

Elementy sieciowe, takie jak urządzenia sieci VPN, centralny sprzęt do ruchu wychodzącego (takie jak serwery proxy i urządzenia do ochrony przed utratą danych), centralna przepustowość internetowa, obwody BACKHAul MPLS, funkcja NAT i tak dalej są nagle obciążane olbrzymim obciążeniem ze względu na obciążenie całej firmy, z których korzysta ta firma. Wynikiem końcowy jest niska wydajność i produktywność w połączeniu z niską wydajnością środowiska użytkownika dla użytkowników, którzy dostosowują się do pracy w domu.

Niektóre z zabezpieczeń, które zazwyczaj były zapewniane przez kierowanie ruchu za pośrednictwem sieci firmowej, są zapewniane przez aplikacje w chmurze, do których mają dostęp użytkownicy. Jeśli został osiągnięty ten krok w tym artykule, wdrożono zestaw zaawansowanych kontrolek zabezpieczeń w chmurze dla Microsoft 365 i danych. Te kontrolki mogą być gotowe do bezpośredniego rozsyłania ruchu użytkowników zdalnych do Office 365. Jeśli nadal potrzebujesz linku VPN w celu uzyskiwania dostępu do innych aplikacji, możesz znacznie poprawić wydajność i usprawnić działanie użytkownika, implementując rozdzielanie połączeń rozdzielanych. Po osiągnięciu porozumienia w organizacji można to osiągnąć w ciągu jednego dnia przez dobrze skoordynowany zespół sieci.

Aby uzyskać więcej informacji, zobacz następujące zasoby dotyczące dokumentów:

- [Omówienie: Optymalizowanie łączności dla użytkowników zdalnych przy użyciu rozdzielania sieci VPN](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [Implementowanie rozdzielania sieci VPN na Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Najnowsze artykuły na ten temat:

- [Jak szybko zoptymalizować ruch pod kątem zdalnego obciążenia personelu & zmniejszyć obciążenie infrastruktury](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Nowoczesne mechanizmy kontroli zabezpieczeń w dzisiejszych unikatowych scenariuszach pracy zdalnej mogą zapewnić specjaliści ds. zabezpieczeń i informatycy.](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10. Szkolenie użytkowników

Użytkownicy szkoleń mogą zaoszczędzić dużo czasu i frustrację zespołu szkoleniowego związanego z operacjami bezpieczeństwa. Tego użytkownika jest mniej prawdopodobne, że otwierają załączniki lub klikają linki w podejrzanych wiadomościach e-mail i unikają podejrzanych witryn internetowych.

Podręcznik kampanii kampanii na [harvardzie dla](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) szkół podstawowych zapewnia doskonałe wskazówki na temat ustanawiania silnej kultury informacji na temat bezpieczeństwa w organizacji, w tym dla użytkowników szkoleniowych w zakresie identyfikowania ataków na wyłudzanie informacji.

Microsoft 365 udostępnia następujące zasoby, które ułatwiają informowanie użytkowników w organizacji:

****

|Pojęcie|Zasoby|
|---|---|
|Microsoft 365|[Dostosowywane ścieżki edukacyjne](/office365/customlearning/) <p>Te zasoby mogą ułatwić ci zskładanie szkoleń dla użytkowników końcowych w organizacji|
|Centrum zabezpieczeń platformy Microsoft 365|[Edukacja: Zabezpieczanie organizacji za pomocą wbudowanych, inteligentnych zabezpieczeń przed Microsoft 365](/learn/modules/security-with-microsoft-365) <p>Ten moduł umożliwia opisanie Microsoft 365 współpracy funkcji zabezpieczeń i wyartykułować zalety tych funkcji zabezpieczeń.|
|Uwierzytelnianie wieloskładnikowe|[Weryfikacja dwuetapowa: Co to jest dodatkowa strona weryfikacji?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Ten artykuł ułatwia użytkownikom końcowych zrozumienie, co to jest uwierzytelnianie wieloskładnikowe i dlaczego jest ono używane w Twojej organizacji.|

Oprócz tych wskazówek firma Microsoft zaleca użytkownikom korzystanie z akcji opisanych w tym artykule: Ochrona konta i urządzeń przed [hakerami i złośliwym oprogramowaniem](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Są to między innymi:

- Używanie silnych haseł
- Ochrona urządzeń
- Włączanie funkcji zabezpieczeń na Windows 10 komputerach PC i Mac (na urządzeniach niezamenu)

Firma Microsoft zaleca również użytkownikom ochronę osobistych kont e-mail, korzystając z akcji zalecanych w następujących artykułach:

- [Ochrona konta e Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Ochrona konta Gmail za pomocą weryfikacji dwuetapowej](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: Wprowadzenie pomocą Microsoft Defender for Cloud Apps

[Microsoft Defender for Cloud Apps](/cloud-app-security) zapewnia zaawansowaną widoczność, kontrolę nad podróżami danych oraz zaawansowane analizy w celu identyfikowania i zwalczania cyberataków we wszystkich usługach w chmurze. Po rozpoczęcia pracy z aplikacjami pakietu Defender dla Chmury zasady wykrywania anomaly są automatycznie włączone, ale Defender dla Chmury Apps ma początkowy siedmiodniowy okres nauki, podczas którego nie wszystkie alerty wykrywania anomaly są podwyższone.

Wprowadzenie teraz Defender dla Chmury aplikacje. Później możesz skonfigurować bardziej zaawansowane monitorowanie i kontrolki.

- [Szybki start: Wprowadzenie z Defender dla Chmury aplikacji](/cloud-app-security/getting-started-with-cloud-app-security)
- [Uzyskiwanie natychmiastowej analizy zachowania i wykrywania anomalii](/cloud-app-security/anomaly-detection-policy)
- [Dowiedz się więcej o Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Przeglądanie nowych funkcji i możliwości](/cloud-app-security/release-notes)
- [Zobacz podstawowe instrukcje konfiguracji](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: Monitorowanie zagrożeń i działanie

Microsoft 365 kilka sposobów monitorowania stanu i podjęcia odpowiednich działań. Najlepszym punktem startowym jest <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portal Microsoft 365 Defender</a>, w którym można wyświetlać wyniki bezpiecznego dostępu firmy [Microsoft](./defender/microsoft-secure-score.md) oraz alerty i jednostki, które wymagają Twojej uwagi.

- [Wprowadzenie z portalem Microsoft 365 Defender-](./defender/microsoft-365-defender.md#the-microsoft-365-defender-portal)
- [Zobacz portale zabezpieczeń w programie Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>Następne kroki

Gratulacje! Niektóre z najważniejszych zabezpieczeń zostały szybko zaimplementowane, a Twoja organizacja jest znacznie bezpieczniejsza. Teraz możesz jeszcze bardziej pójść o krok dalej dzięki możliwościom ochrony przed zagrożeniami (w tym Ochrona punktu końcowego w usłudze Microsoft Defender), klasyfikacji i ochrony danych oraz zabezpieczania kont administracyjnych. Aby uzyskać bardziej szczegółowe i metodyczne zalecenia dotyczące zabezpieczeń dla Microsoft 365, zobacz Microsoft 365 dla osób decyzyjnych w biznesie[.](Microsoft-365-security-for-bdm.md)

Odwiedź też nową stronę firmy Microsoft, Defender dla Chmury on [docs.microsoft.com/security](/security).
