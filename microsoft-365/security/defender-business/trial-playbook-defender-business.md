---
title: podręcznik wersji próbnej Microsoft Defender dla Firm
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.collection: m365-security-compliance
ms.localizationpriority: high
ms.prod: m365-security
ms.technology: mdb
search.appverid:
- MOE150
- MET150
description: W tym podręczniku najlepiej wykorzystać wersję próbną usługi Defender for Business. Szybko skonfiguruj i rozpocznij korzystanie z nowych funkcji zabezpieczeń.
ms.openlocfilehash: 4f239a08e46e8c8bede5c2e972c3daed2af8b550
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418988"
---
# <a name="trial-playbook-microsoft-defender-for-business"></a>Podręcznik wersji próbnej: Microsoft Defender dla Firm

**Witamy w podręczniku wersji próbnej usługi Defender for Business!** 

Ten podręcznik to prosty przewodnik, który pomoże Ci w maksymalnym maksymalnym użyciu 30-dniowej bezpłatnej wersji próbnej. Korzystając z zaleceń zawartych w tym artykule zespołu usługi Microsoft Defender, dowiesz się, w jaki sposób usługa Defender dla Firm może pomóc w podniesieniu poziomu zabezpieczeń od tradycyjnej ochrony antywirusowej do ochrony nowej generacji, wykrywanie i reagowanie w punktach końcowych i Zarządzanie zagrożeniami i lukami. 

## <a name="what-is-defender-for-business"></a>Co to jest usługa Defender dla Firm? 

Defender for Business to nowe rozwiązanie zabezpieczeń punktów końcowych, które zostało zaprojektowane specjalnie dla małych i średnich firm (do 300 pracowników). Dzięki temu rozwiązaniu zabezpieczeń punktu końcowego urządzenia organizacji są lepiej chronione przed oprogramowaniem wymuszającym okup, złośliwym oprogramowaniem, wyłudzaniem informacji i innymi zagrożeniami. 

:::image type="content" source="media/mdb-offering-overview.png" alt-text="Microsoft Defender dla Firm funkcje i możliwości.":::

**Zaczynajmy!**

## <a name="set-up-your-trial"></a>Konfigurowanie wersji próbnej

Poniżej przedstawiono sposób konfigurowania subskrypcji wersji próbnej:

1. [Dodawanie użytkowników i przypisywanie licencji](#step-1-add-users-and-assign-licenses).
2. [Odwiedź portal Microsoft 365 Defender](#step-2-visit-the-microsoft-365-defender-portal).
3. [Użyj kreatora konfiguracji](#step-3-use-the-setup-wizard-in-defender-for-business-recommended).
4. [Skonfiguruj i skonfiguruj usługę Defender dla Firm](#step-4-set-up-and-configure-defender-for-business).

### <a name="step-1-add-users-and-assign-licenses"></a>Krok 1. Dodawanie użytkowników i przypisywanie licencji

Po zarejestrowaniu się w usłudze Defender dla Firm pierwszym krokiem jest **[dodanie użytkowników i przypisanie licencji](mdb-add-users.md)**.

> [!NOTE]
> Aby wykonać to zadanie, musisz być administratorem globalnym. Osoba, która zarejestrowała firmę w Microsoft 365 lub Defender for Business, jest domyślnie administratorem globalnym. [Dowiedz się więcej o rolach i uprawnieniach](mdb-roles-permissions.md).

### <a name="step-2-visit-the-microsoft-365-defender-portal"></a>Krok 2. Odwiedź portal Microsoft 365 Defender
 
Portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) to punkt, w który można korzystać z usługi Defender for Business i zarządzać nią. Zawiera baner powitalny i objaśnienia ułatwiające rozpoczęcie pracy, karty, które udostępniają odpowiednie informacje, oraz pasek nawigacyjny, który zapewnia łatwy dostęp do różnych funkcji i możliwości. 

- **[Odwiedź portal Microsoft 365 Defender](mdb-get-started.md)**.
- **[Zapoznaj się z paskiem nawigacyjnym](mdb-get-started.md#the-navigation-bar)** po lewej stronie ekranu, aby uzyskać dostęp do zdarzeń, wyświetlić raporty i zarządzać zasadami i ustawieniami zabezpieczeń. 

### <a name="step-3-use-the-setup-wizard-in-defender-for-business-recommended"></a>Krok 3. Korzystanie z kreatora konfiguracji w usłudze Defender dla Firm (zalecane)

Usługa Defender for Business została zaprojektowana w celu zaoszczędzenia czasu i wysiłku małych i średnich firm. Początkową konfigurację i konfigurację można wykonać za pomocą kreatora konfiguracji. Kreator konfiguracji przeprowadzi Cię przez udzielanie dostępu zespołowi ds. zabezpieczeń, konfigurowanie powiadomień e-mail dla zespołu ds. zabezpieczeń i dołączanie urządzeń Windows firmy. **[Użyj kreatora konfiguracji](mdb-use-wizard.md)**.

> [!NOTE]
> Kreatora konfiguracji można używać tylko raz. 

#### <a name="setup-wizard-flow-what-to-expect"></a>Przepływ kreatora instalacji: czego się spodziewać

> [!TIP]
> **Korzystanie z kreatora konfiguracji jest opcjonalne** (zobacz [Co się stanie, jeśli nie używam kreatora?](mdb-use-wizard.md#what-happens-if-i-dont-use-the-wizard)). Jeśli nie chcesz korzystać z kreatora lub kreator jest zamknięty przed zakończeniem procesu konfiguracji, możesz samodzielnie ukończyć proces konfiguracji i konfiguracji. Zobacz [Krok 4](#step-4-set-up-and-configure-defender-for-business). 

1. **[Przypisz uprawnienia użytkownika](mdb-roles-permissions.md#view-or-edit-role-assignments)**. Udziel zespołowi ds. zabezpieczeń dostępu do portalu Microsoft 365 Defender.

2. **[Konfigurowanie powiadomień e-mail](mdb-email-notifications.md#view-and-edit-email-notifications)** dla zespołu ds. zabezpieczeń.

3. **[Dołączanie i konfigurowanie urządzeń Windows](mdb-onboard-devices.md)**. Od razu dołączanie urządzeń pomaga chronić te urządzenia od pierwszego dnia.

   > [!NOTE]
   > Podczas korzystania z kreatora konfiguracji system wykryje, czy masz Windows urządzenia, które zostały już zarejestrowane w Intune. Zostanie wyświetlone pytanie, czy chcesz używać automatycznego dołączania dla wszystkich lub niektórych z tych urządzeń. Możesz dołączyć wszystkie urządzenia Windows jednocześnie lub wybrać określone urządzenia do rozpoczęcia, a następnie dodać więcej urządzeń później. [Dowiedz się więcej o automatycznym dołączaniu](mdb-use-wizard.md#what-is-automatic-onboarding).
   
   Aby dołączyć inne urządzenia, zobacz [krok 4](#step-4-set-up-and-configure-defender-for-business).

4.  **[Wyświetl i w razie potrzeby edytuj zasady zabezpieczeń](mdb-configure-security-settings.md)**. Usługa Defender dla firm obejmuje domyślne zasady zabezpieczeń dla ochrony następnej generacji i ochrony zapory, które można zastosować do urządzeń firmy. Te wstępnie skonfigurowane zasady zabezpieczeń używają zalecanych ustawień, dzięki czemu będziesz chroniony zaraz po dołączeniu urządzeń do usługi Defender dla Firm. I nadal masz możliwość edytowania zasad lub tworzenia nowych. 

### <a name="step-4-set-up-and-configure-defender-for-business"></a>Krok 4. Konfigurowanie i konfigurowanie usługi Defender dla Firm

Jeśli nie chcesz korzystać z kreatora konfiguracji, na poniższym diagramie przedstawiono [ogólny proces konfiguracji i konfiguracji](mdb-setup-configuration.md#the-setup-and-configuration-process) usługi Defender dla firm. 

[:::image type="content" source="media/mdb-setup-process-2.png" alt-text="Proces konfiguracji i konfiguracji dla Microsoft Defender dla Firm.":::](mdb-setup-configuration.md)

Jeśli używasz kreatora instalacji, ale musisz dołączyć więcej urządzeń, takich jak urządzenia inne niż Windows, przejdź bezpośrednio do kroku 4 w poniższej procedurze: 

1. **[Zapoznaj się z wymaganiami dotyczącymi](mdb-requirements.md)** konfigurowania i używania usługi Defender dla Firm. 

2. **[Przypisz role i uprawnienia](mdb-roles-permissions.md)** w portalu Microsoft 365 Defender.

   - [Dowiedz się więcej o rolach w usłudze Defender dla Firm](mdb-roles-permissions.md#roles-in-defender-for-business). 
   - [Wyświetlanie lub edytowanie przypisań ról dla zespołu ds. zabezpieczeń](mdb-roles-permissions.md#view-or-edit-role-assignments).

3. **[Konfigurowanie powiadomień e-mail](mdb-email-notifications.md)** dla zespołu ds. zabezpieczeń.

   - [Dowiedz się więcej o typach powiadomień e-mail](mdb-email-notifications.md#types-of-email-notifications).
   - [Wyświetlanie i edytowanie ustawień powiadomień e-mail](mdb-email-notifications.md#view-and-edit-email-notifications).

4. **[Dołączanie urządzeń](mdb-onboard-devices.md)**. W usłudze Defender dla firm masz do wyboru kilka opcji dołączania urządzeń firmy. Zacznij od wybrania systemu operacyjnego, który chcesz dołączyć. 

   | Urządzeń | Metody dołączania |
   |:---|:---|
   | [klienci Windows](mdb-onboard-devices.md) | Wybierz jedną z następujących opcji dołączania Windows urządzeń klienckich do usługi Defender dla Firm:<br/>— Skrypt lokalny (do ręcznego dołączania urządzeń w portalu Microsoft 365 Defender)<br/>- zasady grupy (jeśli już używasz zasady grupy i wolisz tę metodę)<br/>- Microsoft Intune (*zalecane*; zawarte w [Microsoft 365 Business Premium](../../business-premium/index.md)) |
   | [komputery macOS](mdb-onboard-devices.md) | Wybierz jedną z następujących opcji dołączania urządzeń macOS:<br/>— Skrypt lokalny dla macOS (*zalecane*) <br/>- Microsoft Intune dla macOS (Intune jest uwzględniony w [Microsoft 365 Business Premium](../../business-premium/index.md))<br/><br/>Zalecamy dołączenie macOS urządzeń przy użyciu skryptu lokalnego. Chociaż [rejestrację dla urządzeń macOS można skonfigurować w Intune](/mem/intune/enrollment/macos-enroll), skrypt lokalny jest najprostszą metodą dołączania urządzeń macOS do usługi Defender for Business. |
   | serwery Windows Server i Linux | *serwery Windows Server i Linux nie są obecnie obsługiwane. Funkcje dołączania serwera i zabezpieczeń wkrótce zostaną wyświetlone w usłudze Defender dla Firm*. |
   | [Urządzenia przenośne](mdb-onboard-devices.md) | Musisz Microsoft Intune do dołączania urządzeń przenośnych, takich jak urządzenia Android i iOS/iPadOS. Jeśli masz [Microsoft 365 Business Premium](../../business-premium/index.md), Intune w ramach subskrypcji. Intune można również kupić oddzielnie. Zobacz następujące zasoby, aby uzyskać pomoc dotyczącą rejestrowania tych urządzeń w Intune:<br/>- [Rejestrowanie urządzeń Android](/mem/intune/enrollment/android-enroll)<br/>- [Rejestrowanie urządzeń z systemem iOS lub iPadOS](/mem/intune/enrollment/ios-enroll) |

5. **[Wyświetl i w razie potrzeby skonfiguruj zasady zabezpieczeń](mdb-configure-security-settings.md)**. Po dołączeniu urządzeń firmy do Microsoft Defender dla Firm następnym krokiem jest wyświetlenie i w razie potrzeby edytowanie zasad i ustawień zabezpieczeń. Usługa Defender dla firm zawiera wstępnie skonfigurowane zasady zabezpieczeń, które używają zalecanych ustawień. Można jednak edytować ustawienia zgodnie z potrzebami biznesowymi.

   | Akcja | Opis |
   |:---|:---|
   | [Wybierz miejsce zarządzania zasadami zabezpieczeń i urządzeniami](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices). | Jeśli wybierzesz [uproszczony proces konfiguracji](mdb-simplified-configuration.md), możesz wyświetlić zasady zabezpieczeń i zarządzać nimi w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Nie ograniczasz się jednak do tej opcji. Jeśli używasz [Intune](/mem/intune/protect/), możesz nadal używać centrum administracyjnego Microsoft Endpoint Manager do zarządzania zasadami zabezpieczeń i urządzeniami. |
   | [Wyświetlanie lub edytowanie zasad ochrony nowej generacji](mdb-configure-security-settings.md#view-or-edit-your-next-generation-protection-policies). | Ustawienia ochrony nowej generacji obejmują ochronę w czasie rzeczywistym, blokowanie od pierwszego wejrzenia, ochronę sieci, akcje do wykonania w przypadku potencjalnie niechcianych aplikacji i zaplanowane skanowanie antywirusowe.  |
   | [Wyświetlanie lub edytowanie zasad zapory](mdb-configure-security-settings.md#view-or-edit-your-firewall-policies-and-custom-rules). | Ochrona zapory określa, jaki ruch sieciowy może przepływać do lub z urządzeń firmy. [Reguły niestandardowe](mdb-custom-rules-firewall.md) mogą służyć do definiowania wyjątków od zasad zapory. |
   | [Skonfiguruj filtrowanie zawartości internetowej](mdb-configure-security-settings.md#set-up-web-content-filtering). | Filtrowanie zawartości internetowej umożliwia zespołowi ds. zabezpieczeń śledzenie i regulowanie dostępu do witryn internetowych na podstawie kategorii zawartości, takich jak zawartość dla dorosłych, wysoka przepustowość, odpowiedzialność prawna, wypoczynek lub bez kategorii. |
   | [Przejrzyj ustawienia funkcji zaawansowanych](mdb-configure-security-settings.md#review-settings-for-advanced-features). | W usłudze Defender dla firm funkcje zabezpieczeń są wstępnie konfigurowane przy użyciu zalecanych ustawień. Można je jednak przejrzeć i w razie potrzeby edytować ustawienia zgodnie z potrzebami biznesowymi. <br/><br/>Aby uzyskać dostęp do ustawień zaawansowanych funkcji, w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) przejdź do **obszaru Ustawienia** EndpointsGeneralAdvanced features(Ustawienia  >  EndpointsGeneralAdvanced >  >  **features**). |
   | [Wyświetl i edytuj inne ustawienia](mdb-configure-security-settings.md#access-your-settings-in-the-microsoft-365-defender-portal) w portalu Microsoft 365 Defender. | Oprócz zasad zabezpieczeń stosowanych do urządzeń istnieją inne ustawienia, które można wyświetlać i edytować w usłudze Defender dla firm. Na przykład należy określić strefę czasową do użycia i można dołączyć (lub odłączyć) urządzenia. |

## <a name="start-using-defender-for-business"></a>Rozpoczynanie korzystania z usługi Defender dla Firm

W ciągu następnych 30 dni zalecamy wypróbowanie nowych możliwości zabezpieczeń, zgodnie z opisem w następujących sekcjach:

- [Korzystanie z pulpitu nawigacyjnego zarządzania lukami w zabezpieczeniach & zagrożeń](#use-your-threat--vulnerability-management-dashboard) 
- [Wyświetlanie zagrożeń i reagowanie na nie](#view-and-respond-to-detected-threats)
- [Przeglądanie zasad zabezpieczeń](#review-security-policies)
- [Przygotowanie do bieżącego zarządzania zabezpieczeniami](#prepare-for-ongoing-security-management)

### <a name="use-your-threat--vulnerability-management-dashboard"></a>Korzystanie z pulpitu nawigacyjnego zarządzania lukami w zabezpieczeniach & zagrożeń

Usługa Defender dla firm zawiera pulpit nawigacyjny zarządzania lukami w zabezpieczeniach &, który został zaprojektowany w celu zaoszczędzenia czasu i nakładu pracy zespołu ds. zabezpieczeń. [Użyj pulpitu nawigacyjnego zarządzania lukami w zabezpieczeniach & zagrożeń](mdb-view-tvm-dashboard.md).

- Wyświetl wskaźnik ekspozycji skojarzony z urządzeniami w organizacji.   
- Wyświetlanie najważniejszych zaleceń dotyczących zabezpieczeń, takich jak rozwiązywanie problemów z upośledzoną komunikacją z urządzeniami, włączanie ochrony zapory lub aktualizowanie definicji Program antywirusowy Microsoft Defender.   
- Wyświetlanie działań korygowania, takich jak wszystkie pliki, które zostały wysłane do kwarantanny, lub luki w zabezpieczeniach znalezione na urządzeniach.

### <a name="view-and-respond-to-detected-threats"></a>Wyświetlanie zagrożeń i reagowanie na nie

W miarę wykrywania zagrożeń i wyzwalania alertów tworzone są zdarzenia. Zespół ds. zabezpieczeń organizacji może wyświetlać zdarzenia i zarządzać nimi w portalu Microsoft 365 Defender. [Wyświetlanie wykrytych zagrożeń i reagowanie na](mdb-view-manage-incidents.md) nie. 

- [Wyświetlanie zdarzeń i zarządzanie nimi](mdb-view-manage-incidents.md).
- [Reagowanie na zagrożenia i ich eliminowanie](mdb-respond-mitigate-threats.md).
- [Przejrzyj akcje mediacji w Centrum akcji](mdb-review-remediation-actions.md).
- [Wyświetlanie i używanie raportów](mdb-reports.md).

### <a name="review-security-policies"></a>Przeglądanie zasad zabezpieczeń

W usłudze Defender dla firm ustawienia zabezpieczeń są konfigurowane za pomocą zasad stosowanych do urządzeń. Usługa Defender dla firm zawiera wstępnie skonfigurowane zasady, które ułatwiają ochronę urządzeń firmy zaraz po ich dołączeniu, chroniąc organizację przed zagrożeniami bezpieczeństwa tożsamości, urządzeń, aplikacji i dokumentów. [Przejrzyj zasady zabezpieczeń](mdb-view-edit-create-policies.md).

- [Dowiedz się więcej o domyślnych zasadach](mdb-view-edit-create-policies.md#default-policies-in-defender-for-business).
- [Wyświetl istniejące zasady](mdb-view-edit-create-policies.md#view-your-existing-policies).
- [Omówienie kolejności zasad](mdb-policy-order.md). 
- [Omówienie ustawień konfiguracji nowej generacji](mdb-next-gen-configuration-settings.md).
- [Przejrzyj domyślne ustawienia zapory](mdb-firewall.md#default-firewall-settings-in-defender-for-business).
- [Omówienie ustawień zapory, które można skonfigurować](mdb-firewall.md#firewall-settings-you-can-configure-in-defender-for-business).
- [Skonfiguruj filtrowanie zawartości internetowej](mdb-configure-security-settings.md#set-up-web-content-filtering). Filtrowanie zawartości internetowej umożliwia zespołowi ds. zabezpieczeń śledzenie i regulowanie dostępu do witryn internetowych na podstawie ich kategorii zawartości. Nie jest ona domyślnie włączona, więc musisz ją skonfigurować, jeśli chcesz, aby ta funkcja była dostępna dla twojej organizacji.
  
### <a name="prepare-for-ongoing-security-management"></a>Przygotowanie do bieżącego zarządzania zabezpieczeniami

Nowe zdarzenia zabezpieczeń, takie jak wykrywanie zagrożeń na urządzeniu, dodawanie nowych urządzeń, a pracownicy dołączający lub opuszczający organizację będą wymagać zarządzania zabezpieczeniami. W Microsoft Defender dla Firm istnieje wiele sposobów zarządzania zabezpieczeniami urządzeń. 

- [Wyświetl listę dołączonych urządzeń](mdb-manage-devices.md#view-the-list-of-onboarded-devices) , aby zobaczyć ich poziom ryzyka, poziom narażenia i stan kondycji.
- [Podejmij akcję na urządzeniu](mdb-manage-devices.md#take-action-on-a-device-that-has-threat-detections) , które ma wykrywanie zagrożeń.
- [Dołączanie urządzenia do usługi Defender dla Firm](mdb-manage-devices.md#onboard-a-device).
- [Odłącz urządzenie od usługi Defender dla Firm](mdb-manage-devices.md#offboard-a-device).

## <a name="additional-resources"></a>Dodatkowe materiały

- [Omówienie usługi Microsoft Defender dla Firm](mdb-overview.md)
- [Samouczki i symulacje w Microsoft Defender dla Firm](mdb-tutorials.md)
- [Wideo: ochrona Enterprise-Grade dla małych & średnich firm](https://youtu.be/umhUNzMqZto)
- [Uzyskiwanie Microsoft Defender dla Firm](get-defender-business.md)
