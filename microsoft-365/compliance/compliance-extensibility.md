---
title: Rozszerzalność usługi Microsoft Purview
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Dowiedz się więcej o rozszerzaniu rozwiązań usługi Microsoft Purview przy użyciu łączników danych innych firm i interfejsów API usługi Microsoft Graph.
ms.openlocfilehash: e61cd2dfa8121a0925cc89fd5373569d9697936a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942760"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>Rozszerzalność usługi Microsoft Purview i Microsoft Priva

Rozwiązania Usługi Microsoft Purview pomagają organizacjom inteligentnie oceniać ryzyko związane ze zgodnością, zarządzać danymi poufnymi i chronić je oraz skutecznie reagować na wymagania prawne. Usługa Microsoft Purview jest bogata w scenariusze rozszerzalności i umożliwia organizacjom dostosowywanie, rozszerzanie, integrowanie, przyspieszanie i obsługę rozwiązań do zapewniania zgodności.

Istnieją dwa kluczowe bloki konstrukcyjne rozszerzalności zgodności:

- **Łączniki danych**. Służy do importowania i archiwizowania danych innych firm, dzięki czemu można zastosować funkcje ochrony Microsoft 365 i ładu do danych innych firm.

- **Interfejsy API**. Umożliwia programowy dostęp do możliwości usługi Microsoft Purview.

## <a name="data-connectors"></a>Łączniki danych

Firma Microsoft udostępnia łączniki danych innych firm, które można skonfigurować w portalu zgodności usługi Microsoft Purview. Aby uzyskać listę łączników danych dostarczonych przez firmę Microsoft, zobacz tabelę [Łączniki danych innych firm](archiving-third-party-data.md#third-party-data-connectors) . Tabela łączników danych innych firm zawiera również podsumowanie rozwiązań zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizowaniu danych w Microsoft 365 oraz linki do instrukcji krok po kroku dla każdego łącznika.

Aby dowiedzieć się więcej na temat łączników Microsoft 365 danych, zobacz [Archiwizowanie danych innych firm](archiving-third-party-data.md). Jeśli typ danych innej firmy nie jest obsługiwany przez łączniki danych dostępne w portalu zgodności, możesz współpracować z partnerem, który może udostępnić Ci łącznik niestandardowy. Aby uzyskać listę partnerów, z którą możesz pracować, oraz proces krok po kroku dla tej metody, zobacz [Praca z partnerem w celu archiwizowania danych innych firm](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Wymagania wstępne dotyczące łączników danych

Wiele łączników danych dostępnych w portalu zgodności do importowania i archiwizowania danych innych firm wymaga przygotowania i wykonania zadań konfiguracji w źródle danych innych firm. Te wymagania wstępne są szczegółowo udokumentowane dla każdego łącznika danych innej firmy.

W przypadku łączników danych w portalu zgodności udostępnianym przez jednego z partnerów firmy Microsoft twoja organizacja będzie potrzebować relacji biznesowych z partnerem przed wdrożeniem łącznika.

Aby uzyskać wskazówki i wymagania dotyczące łączników danych innych firm, zobacz sekcję "Łączniki danych" w [Microsoft 365 wskazówki dotyczące zgodności & zabezpieczeń — opisy usług | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>Interfejsów api

Interfejsy API Microsoft Purview i Microsoft Priva są dostępne w zestawach SDK Microsoft Information Protection, microsoft interfejs Graph API i interfejsie API działań zarządzania Office 365. Niektóre interfejsy API zgodności są częścią nowego zestawu interfejsów API zabezpieczeń i zgodności, które umożliwiają deweloperom Microsoft 365 klientom, niezależnym dostawcom oprogramowania, integratorom systemu i zarządzanym dostawcom usług zabezpieczeń tworzenie rozwiązań w zakresie zabezpieczeń i zgodności o wysokiej wartości.

Aby dowiedzieć się więcej na temat uzyskiwania dostępu do interfejsów API Graph, zobacz [Omówienie usługi Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Interfejsy API Graph firmy Microsoft dla żądań praw podmiotu

Zgodnie z pewnymi przepisami dotyczącymi ochrony prywatności na całym świecie osoby fizyczne mogą zgłaszać żądania przeglądania danych osobowych o sobie lub zarządzania nimi, które zebrały firmy. Te żądania są określane jako *żądania praw podmiotu* w rozwiązaniu Microsoft Priva Subject Rights Requests. Żądania praw podmiotów są również nazywane *żądaniami podmiotów danych* (DSR) lub *żądaniami dostępu podmiotów danych* . Interfejsy API usługi Microsoft Graph dla żądań praw podmiotów umożliwiają deweloperom integrację żądań praw podmiotów związanych z Microsoft 365 z szerszym ekosystemem prywatności. Ta rozszerzalność oparta na interfejsie API umożliwia organizacjom reagowanie na żądania praw podmiotów w ujednolicony sposób w całej ich infrastrukturze danych obejmującej zarówno środowiska firmy Microsoft, jak i inne firmy. Ta funkcja pomaga również w automatyzacji na dużą skalę i pomaga organizacjom w wydajniejszym spełnianiu przepisów branżowych bez polegania na procesach ręcznych.

Aby dowiedzieć się więcej, zobacz [Microsoft Graph APIs for subject rights request (Microsoft Graph APIs for subject rights request(Microsoft Graph APIs for subject rights request](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview)).

### <a name="microsoft-information-protection-mip-sdk"></a>zestaw SDK Microsoft Information Protection (MIP)

Zestaw MIP SDK uwidacznia usługi etykietowania i ochrony od Microsoft 365 centrów zabezpieczeń i zgodności do aplikacji i usług innych firm. Deweloperzy mogą używać zestawu SDK do tworzenia natywnej obsługi stosowania etykiet i ochrony plików. Deweloperzy mogą określić, które akcje należy wykonać w przypadku wykrycia określonych etykiet, oraz przyczyny związane z informacjami zaszyfrowanymi przez program MIP.

Przypadki użycia zestawu MIP SDK wysokiego poziomu obejmują:

- Aplikacja biznesowa, która stosuje etykiety klasyfikacji do plików w eksporcie.

- Aplikacja projektowa CAD/CAM, która zapewnia natywną obsługę etykiet poufności.

- Broker zabezpieczeń dostępu do chmury lub rozwiązanie do ochrony przed utratą danych, które może szyfrować dane za pomocą usługi Azure Information Protection.

Aby dowiedzieć się więcej na temat zestawu MIP SDK, wymagań wstępnych, dodatkowych scenariuszy i przykładów, zobacz [Omówienie zestawu MIP SDK](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft interfejs Graph API for Teams DLP

Możliwości [ochrony przed utratą danych (DLP)](dlp-microsoft-teams.md) są szeroko stosowane w Microsoft Teams zwłaszcza, że organizacje przesunęły się do pracy zdalnej. Niedawno [ogłosiliśmy ogólną dostępność](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) interfejsu API powiadomień o zmianie Graph firmy Microsoft dla komunikatów w Teams. Ten interfejs API umożliwia deweloperom tworzenie aplikacji, które mogą nasłuchiwać komunikatów Microsoft Teams niemal w czasie rzeczywistym, a następnie implementować scenariusze DLP zarówno dla klientów, jak i partnerów. Ponadto interfejs API poprawek usługi Microsoft Graph umożliwia stosowanie akcji DLP do Teams komunikatów.

Te dwa interfejsy API tworzą interfejs Graph API firmy Microsoft dla Teams DLP. Możesz rozpocząć od wypróbowania [przykładowej aplikacji](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Aby uzyskać więcej informacji na temat elementów webhook Microsoft Teams wiadomości, zapoznaj się z [dokumentacją](/graph/api/subscription-post-subscriptions).

Aby zapoznać się z wymaganiami licencyjnymi dotyczącymi Teams DLP, zobacz [Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft interfejs Graph API for eDiscovery (wersja zapoznawcza)

Dzięki [funkcji zbierania elektronicznych materiałów dowodowych (Premium)](overview-ediscovery-20.md) organizacje mogą odnajdywać dane tam, gdzie się znajdują, i zarządzać większą ilością kompleksowych przepływów pracy zbierania elektronicznych elektronicznych materiałów dowodowych przy użyciu inteligentnych możliwości uczenia maszynowego i analizy, aby ograniczyć dane do odpowiedniego zestawu — wszystko to, gdy dane pozostają w granicach Microsoft 365 zabezpieczeń i zgodności.

Graph interfejsów API zbierania elektronicznych materiałów dowodowych (Premium) można używać do tworzenia przypadków, przeglądania zestawów i przeglądania zapytań zestawów oraz zarządzania nimi w sposób skalowalny i powtarzalny. Dzięki temu klienci i partnerzy mogą tworzyć aplikacje i przepływy pracy w celu automatyzowania typowych i powtarzających się procesów, takich jak tworzenie spraw i zarządzanie opiekunami i blokadami prawnymi.

Pierwszy zestaw interfejsów API Graph dla zbierania elektronicznych materiałów dowodowych jest dostępny w publicznej wersji zapoznawczej. Planujemy dodać więcej możliwości do końca roku kalendarzowego. Aby dowiedzieć się więcej na temat tych interfejsów API i innych aktualizacji zbierania elektronicznych materiałów dowodowych (Premium), zobacz ten [blog](https://aka.ms/Ignite2020AeDAA).

Aby zapoznać się z wymaganiami licencyjnymi dotyczącymi zbierania elektronicznych materiałów dowodowych (Premium) i interfejsu API, zobacz sekcję "Zbierania elektronicznych materiałów dowodowych" w [Microsoft 365 wytycznych dotyczących licencjonowania dotyczących zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft interfejs Graph API for Teams Export

Enterprise Archiwizowanie informacji (EIA) dla Microsoft Teams jest kluczowym scenariuszem dla naszych klientów, ponieważ pozwala im rozwiązywać wymagania prawne. Oprócz wbudowanych możliwości archiwizowania zawartości w Microsoft Teams klienci i partnerzy mogą teraz używać interfejsów API Teams Export do rozwiązywania problemów w przypadku niestandardowych scenariuszy aplikacji i integracji. Interfejsy API eksportu Teams obsługują eksport zbiorczy (maksymalnie 200 żądań na sekundę/na aplikację/dzierżawę) Teams komunikatów i załączników komunikatów. Usunięte komunikaty są również dostępne dla interfejsu API przez maksymalnie 30 dni po ich usunięciu. Aby uzyskać więcej informacji na temat tych Teams eksportowania interfejsów API i sposobu ich używania w aplikacjach, zobacz [Export content with the Microsoft Teams Export APIs (Eksportowanie zawartości za pomocą interfejsów API eksportu Microsoft Teams](/microsoftteams/export-teams-content)).

Aby zapoznać się z wymaganiami licencyjnymi dotyczącymi używania interfejsów API eksportu Teams, zobacz [Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>Interfejsy API łącznika usługi Microsoft Graph (wersja zapoznawcza)

Dzięki [łącznikom Graph firmy Microsoft](/microsoftsearch/connectors-overview) organizacje mogą indeksować dane innych firm, aby były wyświetlane w Microsoft Search wynikach. Ta funkcja rozszerza typy źródeł zawartości, które można przeszukiwać w Microsoft 365 aplikacji zwiększających produktywność i w szerszym ekosystemie firmy Microsoft. Dane innych firm mogą być hostowane lokalnie lub w chmurach publicznych lub prywatnych. Począwszy od eDiscovery (Premium), włączamy dla deweloperów wersję zapoznawczą wbudowanej wartości zgodności Microsoft 365 połączonych aplikacji. Umożliwia to zgodność aplikacji integrujących się z ekosystemem Microsoft 365 w celu umożliwienia użytkownikom bezproblemowego zapewniania zgodności. Aby dowiedzieć się więcej na temat włączania interfejsów API łącznika usługi Microsoft Graph w widoku aplikacji, zobacz [Tworzenie, aktualizowanie i usuwanie połączeń w usłudze Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).
