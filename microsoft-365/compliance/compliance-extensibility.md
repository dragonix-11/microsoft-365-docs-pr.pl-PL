---
title: Rozszerzalność usługi Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się więcej o rozszerzaniu rozwiązań usługi Microsoft Purview przy użyciu łączników danych innych firm i interfejsów API programu Microsoft Graph.
ms.openlocfilehash: 8cda9ea3a5ef69af69ab802ca21aa8c4c0e716b9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621188"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>Microsoft Purview i rozszerzalność Microsoft Priva

Rozwiązania Usługi Microsoft Purview pomagają organizacjom inteligentnie oceniać ryzyko związane ze zgodnością, zarządzać danymi poufnymi i chronić je oraz skutecznie reagować na wymagania prawne. Usługa Microsoft Purview jest bogata w scenariusze rozszerzalności i umożliwia organizacjom dostosowywanie, rozszerzanie, integrowanie, przyspieszanie i obsługę rozwiązań do zapewniania zgodności.

Istnieją dwa kluczowe bloki konstrukcyjne rozszerzalności zgodności:

- **Łączniki danych**. Służy do importowania i archiwizowania danych innych firm, dzięki czemu można zastosować funkcje ochrony i ładu platformy Microsoft 365 do danych innych firm.

- **Interfejsy API**. Umożliwia programowy dostęp do możliwości usługi Microsoft Purview.

## <a name="data-connectors"></a>Łączniki danych

Firma Microsoft udostępnia łączniki danych innych firm, które można skonfigurować w portal zgodności Microsoft Purview. Aby uzyskać listę łączników danych dostarczonych przez firmę Microsoft, zobacz tabelę [Łączniki danych innych firm](archiving-third-party-data.md#third-party-data-connectors) . Tabela łączników danych innych firm zawiera również podsumowanie rozwiązań zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizowaniu danych w usłudze Microsoft 365, oraz linki do instrukcji krok po kroku dla każdego łącznika.

Aby dowiedzieć się więcej na temat łączników danych platformy Microsoft 365, zobacz [Archiwizowanie danych innych firm](archiving-third-party-data.md). Jeśli typ danych innej firmy nie jest obsługiwany przez łączniki danych dostępne w portalu zgodności, możesz współpracować z partnerem, który może udostępnić Ci łącznik niestandardowy. Aby uzyskać listę partnerów, z którą możesz pracować, oraz proces krok po kroku dla tej metody, zobacz [Praca z partnerem w celu archiwizowania danych innych firm](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Wymagania wstępne dotyczące łączników danych

Wiele łączników danych dostępnych w portalu zgodności do importowania i archiwizowania danych innych firm wymaga przygotowania i wykonania zadań konfiguracji w źródle danych innych firm. Te wymagania wstępne są szczegółowo udokumentowane dla każdego łącznika danych innej firmy.

W przypadku łączników danych w portalu zgodności udostępnianym przez jednego z partnerów firmy Microsoft twoja organizacja będzie potrzebować relacji biznesowych z partnerem przed wdrożeniem łącznika.

Aby uzyskać wskazówki i wymagania dotyczące łączników danych innych firm, zobacz sekcję "Łączniki danych" w [przewodniku Microsoft 365 dotyczącymi zgodności & zabezpieczeń — opisy usług | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>Interfejsów api

Interfejsy API usługi Microsoft Purview i Microsoft Priva są dostępne w Microsoft Information Protection SDK, microsoft interfejs Graph API i interfejsie API działań zarządzania Office 365. Niektóre interfejsy API zgodności są częścią nowego zestawu interfejsów API zabezpieczeń i zgodności, które umożliwiają deweloperom dla klientów platformy Microsoft 365, niezależnych dostawców oprogramowania, integratorów systemów i zarządzanych dostawców usług zabezpieczeń tworzenie rozwiązań w zakresie zabezpieczeń i zgodności o wysokiej wartości.

Aby dowiedzieć się więcej na temat uzyskiwania dostępu do interfejsów API programu Graph, zobacz [Omówienie programu Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Interfejsy API programu Microsoft Graph dla żądań praw podmiotu

Zgodnie z pewnymi przepisami dotyczącymi ochrony prywatności na całym świecie osoby fizyczne mogą zgłaszać żądania przeglądania danych osobowych o sobie lub zarządzania nimi, które zebrały firmy. Żądania te są określane jako *żądania praw podmiotu* w rozwiązaniu żądania praw podmiotów Microsoft Priva. Żądania praw podmiotów są również nazywane *żądaniami podmiotów danych* (DSR) lub *żądaniami dostępu podmiotów danych* . Interfejsy API programu Microsoft Graph dla żądań praw podmiotów umożliwiają deweloperom integrowanie żądań praw podmiotów związanych z platformą Microsoft 365 z szerszym ekosystemem prywatności. Ta rozszerzalność oparta na interfejsie API umożliwia organizacjom reagowanie na żądania praw podmiotów w ujednolicony sposób w całej ich infrastrukturze danych obejmującej zarówno środowiska firmy Microsoft, jak i inne firmy. Ta funkcja pomaga również w automatyzacji na dużą skalę i pomaga organizacjom w wydajniejszym spełnianiu przepisów branżowych bez polegania na procesach ręcznych.

Aby dowiedzieć się więcej, zobacz [Microsoft Graph APIs for subject rights request (Interfejsy API programu Microsoft Graph dotyczące żądania praw podmiotu](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview)).

### <a name="microsoft-information-protection-mip-sdk"></a>zestaw SDK Microsoft Information Protection (MIP)

Zestaw MIP SDK uwidacznia usługi etykietowania i ochrony z centrów zabezpieczeń i zgodności platformy Microsoft 365 na aplikacje i usługi innych firm. Deweloperzy mogą używać zestawu SDK do tworzenia natywnej obsługi stosowania etykiet i ochrony plików. Deweloperzy mogą określić, które akcje należy wykonać w przypadku wykrycia określonych etykiet, oraz przyczyny związane z informacjami zaszyfrowanymi przez program MIP.

Przypadki użycia zestawu MIP SDK wysokiego poziomu obejmują:

- Aplikacja biznesowa, która stosuje etykiety klasyfikacji do plików w eksporcie.

- Aplikacja projektowa CAD/CAM, która zapewnia natywną obsługę etykiet poufności.

- Broker zabezpieczeń dostępu do chmury lub rozwiązanie do ochrony przed utratą danych, które może szyfrować dane za pomocą usługi Azure Information Protection.

Aby dowiedzieć się więcej na temat zestawu MIP SDK, wymagań wstępnych, dodatkowych scenariuszy i przykładów, zobacz [Omówienie zestawu MIP SDK](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft interfejs Graph API for Teams DLP

Możliwości [ochrony przed utratą danych (DLP)](dlp-microsoft-teams.md) są szeroko stosowane w usłudze Microsoft Teams, zwłaszcza że organizacje przesunęły się do pracy zdalnej. Niedawno [ogłosiliśmy ogólną dostępność](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) interfejsu API powiadomień o zmianie programu Microsoft Graph dla komunikatów w usłudze Teams. Ten interfejs API umożliwia deweloperom tworzenie aplikacji, które mogą nasłuchiwać komunikatów usługi Microsoft Teams niemal w czasie rzeczywistym, a następnie implementować scenariusze DLP zarówno dla klientów, jak i partnerów. Ponadto interfejs API poprawek programu Microsoft Graph umożliwia stosowanie akcji DLP do komunikatów usługi Teams.

Te dwa interfejsy API tworzą usługę Microsoft interfejs Graph API for Teams DLP. Możesz rozpocząć od wypróbowania [przykładowej aplikacji](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Aby uzyskać więcej informacji na temat elementów webhook wiadomości w usłudze Microsoft Teams, zobacz [dokumentację](/graph/api/subscription-post-subscriptions).

Aby zapoznać się z wymaganiami licencyjnymi dotyczącymi usługi Teams DLP, zobacz [Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft interfejs Graph API for eDiscovery (wersja zapoznawcza)

Dzięki [funkcji zbierania elektronicznych materiałów dowodowych (Premium)](overview-ediscovery-20.md) organizacje mogą odnajdywać dane, w których się znajdują, i zarządzać bardziej kompleksowymi przepływami pracy zbierania elektronicznych elektronicznych materiałów dowodowych przy użyciu inteligentnych możliwości uczenia maszynowego i analizy, aby ograniczyć dane do odpowiedniego zestawu — wszystko to, gdy dane pozostają w granicach zabezpieczeń i zgodności usługi Microsoft 365.

Interfejsy API programu Graph dla zbierania elektronicznych materiałów dowodowych (Premium) mogą służyć do tworzenia przypadków i zarządzania nimi, przeglądania zestawów i przeglądania zapytań zestawów w skalowalny i powtarzalny sposób. Dzięki temu klienci i partnerzy mogą tworzyć aplikacje i przepływy pracy w celu automatyzowania typowych i powtarzających się procesów, takich jak tworzenie spraw i zarządzanie opiekunami i blokadami prawnymi.

Pierwszy zestaw interfejsów API programu Graph dla zbierania elektronicznych materiałów dowodowych jest dostępny w publicznej wersji zapoznawczej. Planujemy dodać więcej możliwości do końca roku kalendarzowego. Aby dowiedzieć się więcej na temat tych interfejsów API i innych aktualizacji zbierania elektronicznych materiałów dowodowych (Premium), zobacz ten [blog](https://aka.ms/Ignite2020AeDAA).

Aby zapoznać się z wymaganiami licencyjnymi dotyczącymi zbierania elektronicznych materiałów dowodowych (Premium) i interfejsu API, zobacz sekcję "eDiscovery" w [wytycznych dotyczących licencjonowania platformy Microsoft 365 dotyczących zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Eksportowanie usługi Microsoft interfejs Graph API for Teams

Archiwizowanie informacji o przedsiębiorstwie (EIA) dla usługi Microsoft Teams jest kluczowym scenariuszem dla naszych klientów, ponieważ pozwala im rozwiązywać wymagania prawne. Oprócz wbudowanych możliwości archiwizowania zawartości w usłudze Microsoft Teams klienci i partnerzy mogą teraz używać interfejsów API eksportu aplikacji Teams do rozwiązywania problemów dotyczących niestandardowych scenariuszy aplikacji i integracji. Interfejsy API eksportu aplikacji Teams obsługują eksport zbiorczy (maksymalnie 200 żądań na sekundę/na aplikację/dzierżawę) komunikatów i załączników komunikatów usługi Teams. Usunięte komunikaty są również dostępne dla interfejsu API przez maksymalnie 30 dni po ich usunięciu. Aby uzyskać więcej informacji na temat tych interfejsów API eksportu usługi Teams i sposobu ich używania w aplikacjach, zobacz [Eksportowanie zawartości za pomocą interfejsów API eksportu usługi Microsoft Teams](/microsoftteams/export-teams-content).

Aby zapoznać się z wymaganiami licencyjnymi dotyczącymi korzystania z interfejsów API eksportu usługi Teams, zobacz [Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>Interfejsy API łącznika programu Microsoft Graph (wersja zapoznawcza)

Za pomocą [łączników programu Microsoft Graph](/microsoftsearch/connectors-overview) organizacje mogą indeksować dane innych firm, aby były wyświetlane w wynikach usługi Microsoft Search. Ta funkcja rozszerza typy źródeł zawartości, które można przeszukiwać w aplikacjach zwiększających produktywność platformy Microsoft 365 i w szerszym ekosystemie firmy Microsoft. Dane innych firm mogą być hostowane lokalnie lub w chmurach publicznych lub prywatnych. Począwszy od eDiscovery (Premium), włączamy wersję zapoznawczą dla deweloperów wbudowanej wartości zgodności połączonych aplikacji platformy Microsoft 365. Umożliwia to zgodność aplikacji integrujących się z ekosystemem platformy Microsoft 365 w celu umożliwienia użytkownikom bezproblemowego zapewniania zgodności. Aby dowiedzieć się więcej na temat dołączania interfejsów API łącznika programu Microsoft Graph do widoku aplikacji, zobacz [Tworzenie, aktualizowanie i usuwanie połączeń w programie Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).

### <a name="microsoft-graph-api-for-records-management-preview"></a>Microsoft interfejs Graph API do zarządzania rekordami (wersja zapoznawcza)

Organizacje wszystkich typów wymagają rozwiązania do zarządzania rekordami w celu zarządzania rekordami krytycznymi w danych. [Zarządzanie rekordami w Microsoft Purview](records-management.md) pomaga organizacji zarządzać swoimi zobowiązaniami prawnymi, umożliwia demonstrowanie zgodności z przepisami i zwiększa wydajność przy regularnym rozporządzaniu elementami, które nie są już wymagane.

Rozwiązanie do zarządzania rekordami jest używane przez organizacje w dużych ilościach do wykorzystania różnych możliwości w zakresie ochrony, etykietowania, przechowywania lub usuwania danych. Interfejsy API programu Microsoft Graph do zarządzania rekordami umożliwiają organizacjom wydajniejsze zarządzanie etykietami przechowywania i skojarzonymi z nimi akcjami, automatyzowanie powtarzających się zadań i zapewnianie klientom elastyczności w opcjach.

Teraz jest wdrażana pierwsza wersja interfejsów API programu Graph do zarządzania rekordami obsługuje zarządzanie etykietami przechowywania i przechowywanie oparte na zdarzeniach. Przykładowe scenariusze:

- **Zarządzanie etykietami przechowywania**
    
    Administratorzy zarządzania rekordami i deweloperzy muszą utrzymywać swoje systemy zarządzania rekordami z etykietami, które są okresowo tworzone, aktualizowane i usuwane.
    
    Deweloperzy i administratorzy zgodności używają interfejsów API programu Graph do zarządzania rekordami do wykonywania operacji CRUD w jednostce etykiety w celu utrzymania swoich systemów.

- **Wyzwalanie zdarzenia dla istniejącej etykiety**
    
    Gdy pracownik opuszcza organizację, informacje są aktualizowane w systemie zarządzania kadrami. Od daty wyjazdu poufne dokumenty muszą być przechowywane przez siedem lat. W tych dokumentach zastosowano już etykietę przechowywania "Employee_departure".
    
    Deweloperzy i administratorzy zgodności używają interfejsów API programu Graph do zarządzania rekordami, aby odczytać etykietę "Employee_departure" i wyszukać skojarzony typ zdarzenia "Event-employee_departure".
    
    Następnie używają interfejsów API programu Graph do zarządzania rekordami, aby utworzyć zdarzenie dla skojarzonego typu zdarzenia. Okres przechowywania poufnych dokumentów rozpoczyna się po utworzeniu tego zdarzenia.

Aby uzyskać więcej informacji na temat interfejsów API programu Graph do zarządzania rekordami, zobacz [Korzystanie z interfejsu API zarządzania rekordami programu Microsoft Graph](/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-beta&preserve-view=true).

Aby uzyskać wymagania licencyjne dotyczące korzystania z tych interfejsów API, zobacz sekcję zarządzania rekordami w [temacie Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).
