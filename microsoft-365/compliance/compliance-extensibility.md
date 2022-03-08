---
title: Microsoft 365 rozszerzalność zgodności
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
description: Dowiedz się więcej o rozszerzaniu Microsoft 365 zgodności przy użyciu łączników danych i interfejsów API usługi Microsoft Graph firmy Microsoft.
ms.openlocfilehash: 0632de40141b86e6dfdebf3f5c3a97ca50219357
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330541"
---
# <a name="microsoft-365-compliance-and-microsoft-priva-extensibility"></a>Microsoft 365 zgodności i rozszerzalność usługi Microsoft Priva

Microsoft 365 rozwiązania dotyczące zgodności pomagają organizacjom inteligentnie oceniać swoje zagrożenia zgodności z przepisami, określać zasady ochrony poufnych danych i skutecznie odpowiadać na wymagania prawne. Microsoft 365 rozwiązania dotyczące zgodności są rozbudowane w scenariuszach rozszerzalności i pozwalają organizacjom dostosowywać, rozszerzać, integrować, przyspieszyć i obsługiwać swoje rozwiązania zgodności.

Istnieją dwa kluczowe bloki konstrukcyjne rozszerzalności zgodności:

- **Łączniki danych**. Umożliwia importowanie i archiwizowanie danych innych niż firmy Microsoft w celu zastosowania Microsoft 365 ochrony i zarządzania danymi innych firm.

- **INTERFEJSY API**. Umożliwia programowy dostęp do Microsoft 365 funkcji zgodności.

## <a name="data-connectors"></a>Łączniki danych

Firma Microsoft udostępnia łączniki danych innych firm, które można skonfigurować w Centrum zgodności platformy Microsoft 365. Aby uzyskać listę łączników danych dostarczanych przez firmę Microsoft, zobacz tabelę [Łączniki danych innych](archiving-third-party-data.md#third-party-data-connectors) firm. Tabela łączników danych innych firm zawiera również podsumowanie rozwiązań zgodności, które można zastosować do danych innych firm po zaimportowaniu i zarchiwizować dane w programie Microsoft 365, oraz linki do instrukcji krok po kroku dotyczących poszczególnych łączników.

Aby dowiedzieć się więcej Microsoft 365 łączników danych, zobacz [Archiwizowanie danych innych firm](archiving-third-party-data.md). Jeśli typ danych innej firmy nie jest obsługiwany przez łączniki danych dostępne w p Centrum zgodności platformy Microsoft 365, możesz współpracować z partnerem, który może udostępnić łącznik niestandardowy. Aby uzyskać listę partnerów, z których możesz współpracować, oraz proces krok po kroku dla tej metody, zobacz Współpraca z partnerem w celu archiwizacji danych [innych firm](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Wymagania wstępne łączników danych

Wiele łączników danych dostępnych w p Centrum zgodności platformy Microsoft 365 do importowania i archiwizowania danych innych firm wymaga przygotowania i wykonania zadań konfiguracyjnych w źródle danych innych firm. Te wymagania wstępne są szczegółowo udokumentowane dla każdego łącznika danych innej firmy.

W przypadku łączników danych w Centrum zgodności platformy Microsoft 365 dostarczonych przez jednego z partnerów firmy Microsoft Twoja organizacja będzie potrzebować relacji biznesowej z tym partnerem, aby można było wdrożyć łącznik.

Aby uzyskać wskazówki i wymagania dotyczące łączników danych innych firm, zobacz sekcję "Łączniki danych" w te Microsoft 365 wskazówki dotyczące zgodności & zabezpieczeń — opisy [| Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>Interfejsy API

Microsoft 365 zgodnością i interfejsami API Microsoft Priva są dostępne w zestawie SDK pakietu Microsoft Information Protection, interfejsie API microsoft Graph i interfejsie API działań zarządzania Office 365 zarządzaniem. Niektóre interfejsy API zgodności są częścią nowego zestawu interfejsów API zabezpieczeń i zgodności, które umożliwiają deweloperom dla klientów usługi Microsoft 365, niezależnych dostawców oprogramowania, integratorów systemu i zarządzanych dostawców usług zabezpieczeń tworzenie cennych rozwiązań zabezpieczeń i zgodności.

Aby dowiedzieć się więcej na temat uzyskiwania dostępu do Graph API, zobacz [Omówienie interfejsów API Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Interfejsy API Graph Microsoft dla żądań praw podmiotu

Zgodnie z niektórymi przepisami dotyczącymi prywatności na całym świecie osoby mogą wnioskować o przejrzenie danych osobowych o sobie zbieranych przez firmy lub zarządzanie nimi. Takie żądania są określane jako żądania praw *podstawowych w ramach* rozwiązania Microsoft Priva Subject Rights Requests. Żądania praw osób, których dane dotyczą, są również *określane jako żądania* dostępu osób, których  dane dotyczą, lub żądania dostępu osób, których dane dotyczą. Interfejsy API Graph Microsoft dla żądań praw podmiotu umożliwiają deweloperom integrowanie Microsoft 365 powiązanych z tematem żądań praw z szerszego ekosystemu prywatności. To rozszerzanie oparte na interfejsie API umożliwia organizacjom odpowiadanie na żądania praw podstawowych w ujednolicony sposób w obrębie całego rynku danych, obejmującego zarówno środowiska firmy Microsoft, jak i środowiska innych niż firmy Microsoft. Funkcja ta pomaga również w automatyzacji na skalę i pomaga organizacjom w wydajniejszym spełnianiu przepisów branżowych bez konieczności obsługi procesów ręcznych.

Aby dowiedzieć się więcej, zobacz [Interfejsy API usługi Microsoft Graph, aby uzyskać informacje na temat żądania praw podmiotu](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>Microsoft Information Protection SDK (MIP)

Zestaw SDK ochrony przed zagrożeniami miP udostępnia usługi etykiet i ochrony z Microsoft 365 zabezpieczeń i zgodności na aplikacje i usługi innych firm. Deweloperzy mogą używać zestawu SDK do tworzenia natywnej obsługi stosowania etykiet i ochrony plików. Deweloperzy mogą określać, jakie akcje należy podjąć po wykryciu określonych etykiet, oraz powody, dla których informacje zaszyfrowane za pomocą szyfrowania MIP.

Zestaw SDK miP wysokiego poziomu to między innymi:

- Etykieta aplikacja LOB, która stosuje etykiety klasyfikacji do plików podczas eksportowania.

- Aplikacja do projektowania programów CAD/CAM, która zapewnia natywną obsługę etykiet MIP.

- Broker dostępu w chmurze lub rozwiązanie do ochrony przed utratą danych, które może szyfrować dane za pomocą usługi Azure Information Protection.

Aby dowiedzieć się więcej o zestawie MIP SDK, wymaganiach wstępnych, dodatkowych scenariuszach i przykładach, zobacz Omówienie [zestawu SDK miP](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Interfejs API Graph Microsoft dla aplikacji Teams DLP

[Funkcje ochrony przed utratą danych (DLP, Data loss prevention)](dlp-microsoft-teams.md) są powszechnie używane w Microsoft Teams, zwłaszcza gdy organizacje przeszły do pracy zdalnej. Niedawno [ogłosiliśmy ogólną dostępność](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) interfejsu API powiadomień usługi Microsoft Graph dla wiadomości w aplikacji Teams. Ten interfejs API umożliwia deweloperom tworzenie aplikacji, które mogą odsłuchiwać wiadomości Microsoft Teams w czasie rzeczywistym, a następnie wdrażać scenariusze dotyczące funkcji DLP zarówno dla klientów, jak i partnerów. Ponadto interfejs API poprawek Microsoft Graph umożliwia stosowanie akcji DLP do Teams wiadomości.

Te dwa interfejsy API tworzą interfejs API platformy Microsoft Graph dla Teams DLP. Możesz zacząć od wypróbowania [przykładowej aplikacji](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Aby uzyskać więcej informacji Microsoft Teams wiadomości w sieci Web, zapoznaj się z [dokumentacją](/graph/api/subscription-post-subscriptions).

Aby uzyskać informacje na temat wymagań licencjonowania dotyczących ochrony przed Teams DLP, zobacz Microsoft 365 [licencjonowania w celu zapewnienia zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Interfejs API Graph Microsoft dla zbierania elektronicznych materiałów dowodowych (wersja Preview)

Dzięki programowi [Advanced eDiscovery](overview-ediscovery-20.md) organizacje mogą odnajdować dane w miejscu, w którym się on znajduje, i zarządzać bardziej całymi przepływami pracy zbierania elektronicznych materiałów dowodowych dzięki inteligentnym możliwościom uczenia maszynowego i analizy w celu zmniejszenia ilości danych do odpowiedniego zestawu — Microsoft 365 dane pozostają w granicach zabezpieczeń i zgodności usługi Microsoft 365.

Graph interfejsów API dla Advanced eDiscovery mogą być używane do tworzenia spraw i zarządzania nimi, przeglądania zestawów i reenzowania zestawów zapytań w sposób skalowalny i powtarzalny. Umożliwia to klientom i partnerom tworzenie aplikacji i przepływów pracy w celu zautomatyzowania typowych i powtarzających się procesów, takich jak tworzenie spraw i zarządzanie opiekunami oraz zamiejscami  prawne.

Pierwszy zestaw interfejsów API zbierania Graph eDiscovery jest dostępny w publicznej wersji zapoznawczej. Planujemy dodać więcej funkcji do końca roku kalendarzowego. Aby dowiedzieć się więcej o tych interfejsach API i innych aktualizacjach Advanced eDiscovery, zobacz [ten blog](https://aka.ms/Ignite2020AeDAA).

Aby uzyskać informacje na temat wymagań licencjonowania Advanced eDiscovery interfejsu API, zobacz sekcję "Zbierania elektronicznych materiałów dowodowych" w sekcji wskazówki dotyczące licencjonowania Microsoft 365 dotyczące zabezpieczeń & [zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Interfejs API Graph Microsoft dla Teams Eksportuj

Enterprise archiwizacji informacji (EIA, Information Archiving) dla systemu Microsoft Teams to kluczowy scenariusz dla klientów, ponieważ pozwala im na rozwiązanie wymogów prawnych. Oprócz naszych wbudowanych funkcji archiwizowania zawartości w programie Microsoft Teams klienci i partnerzy mogą teraz używać interfejsów API eksportu do rozwiązywania niestandardowych scenariuszy integracji i aplikacji za pomocą programu Teams. Interfejsy API Teams obsługują eksport zbiorczy (maksymalnie 200 żądań na sekundę/na aplikację/dzierżawę) Teams wiadomości i załączników wiadomości. Usunięte wiadomości są również dostępne przez interfejs API w ciągu 30 dni od ich usunięcia. Aby uzyskać więcej informacji na temat tych Teams API eksportowania i używania ich w aplikacjach, zobacz Eksportowanie zawartości za pomocą interfejsów API eksportu Microsoft Teams [eksportowania](/microsoftteams/export-teams-content).

Aby uzyskać informacje na temat wymagań licencjonowania dotyczących używania interfejsów API eksportu Teams, zobacz Microsoft 365 licencjonowania w celu zapewnienia zgodności [& zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>Interfejsy API programu Microsoft Graph Connector (wersja zapoznawcza)

Za [pomocą łączników programu Microsoft Graph](/microsoftsearch/connectors-overview) organizacje mogą indeksować dane innych firm, aby były wyświetlane w Microsoft Search danych. Ta funkcja rozszerza typy źródeł zawartości, które można przeszukiwać Microsoft 365 aplikacjach zwiększających produktywność i szerszego ekosystemu firmy Microsoft. Dane innych firm mogą być hostowane lokalnie lub w chmurach publicznych lub prywatnych. Rozpoczynając od Advanced eDiscovery, umożliwiamy deweloperowi podgląd wbudowanej wartości zgodności dla Microsoft 365 połączonych aplikacji. Dzięki temu aplikacje integrują się z całym Microsoft 365, umożliwiając użytkownikom zapewnienie bezproblemowej zgodności. Aby dowiedzieć się więcej na temat dołączania interfejsów API programu Microsoft Graph Connector w widoku aplikacji, zobacz Tworzenie, aktualizowanie i usuwanie połączeń w aplikacji [Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).
