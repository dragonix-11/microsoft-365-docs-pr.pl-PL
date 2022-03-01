---
title: Integracja narzędzi SIEM z programem Microsoft Defender for Endpoint
description: Dowiedz się, jak cytować alerty i zdarzenia oraz zintegrować narzędzia SIEM.
keywords: konfigurowanie siem, narzędzi do zarządzania informacjami i zdarzeniami zabezpieczeń, splunku, arcusight, niestandardowych wskaźników, interfejsu API rest, definicji alertów, wskaźników naruszenia bezpieczeństwa
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4c0462bcfae77677fca05132aaf0895b897bf788
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010369"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Integracja narzędzi SIEM z programem Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Alerty dotyczące alertów przy użyciu narzędzi do zarządzania informacjami i zdarzeniami zabezpieczeń

> [!NOTE]
>
> [Alert programu Microsoft Defender dla punktu końcowego](alerts.md) składa się z co najmniej jednego podejrzanego lub złośliwego zdarzenia, które wystąpiło na urządzeniu, i powiązanych ze nim informacji. Interfejs API alertów programu Microsoft Defender for Endpoint To najnowszy interfejs API do użycia alertów, który zawiera szczegółową listę powiązanych dowodów dla poszczególnych alertów. Aby uzyskać więcej informacji, zobacz [Metody i właściwości alertów oraz](alerts.md) [Alerty listy](get-alerts.md).

Program Microsoft Defender for Endpoint obsługuje narzędzia do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), które pozwalają na korzystanie z informacji z dzierżawy przedsiębiorstwa w programie Azure Active Directory (AAD) przy użyciu protokołu uwierzytelniania OAuth 2.0 dla zarejestrowanej aplikacji programu AAD reprezentującej określone rozwiązanie SIEM lub łącznik zainstalowany w Twoim środowisku.

Więcej informacji można znaleźć w następujących artykułach:

- [Licencja i warunki użytkowania interfejsów API programu Microsoft Defender dla punktów końcowych](api-terms-of-use.md) 
- [Uzyskiwanie dostępu do interfejsów API programu Microsoft Defender dla punktów końcowych](apis-intro.md)
- [Przykład "Witaj świecie" (w tym artykule opisano, jak zarejestrować aplikację w Azure Active Directory)](api-hello-world.md)
- [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](exposed-apis-create-app-webapp.md)


Program Microsoft Defender for Endpoint obsługuje obecnie następujące integracje rozwiązań SIEM: 

- [Powiadomienia i zdarzenia związane z usługą Microsoft 365 Defender programu Microsoft Defender dla zdarzeń dotyczących punktu końcowego oraz alerty interfejsów API usługi REST](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Ingesting Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Powiadomienia i zdarzenia związane z usługą Microsoft 365 Defender programu Microsoft Defender dla zdarzeń dotyczących punktu końcowego oraz alerty interfejsów API usługi REST

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Insesting incidents from the Microsoft 365 Defender incidents REST API

Aby uzyskać więcej informacji na temat interfejsu API Microsoft 365 Defender zdarzeń, zobacz Metody [i właściwości zdarzeń](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Alerty dotyczące obsługi z interfejsu API rest alertów programu Microsoft Defender dla punktów końcowych

Aby uzyskać więcej informacji na temat interfejsu API alertów programu Microsoft Defender for Endpoint, zobacz Metody [i właściwości alertów](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Integracja narzędzi SIEM z programem Microsoft Defender for Endpoint

### <a name="splunk"></a>Splunk

Za pomocą Microsoft 365 Defender Splunk, który obsługuje:

- Alerty dotyczące programu Microsoft Defender dla punktu końcowego
- Aktualizowanie alertów w programie Microsoft Defender dla punktu końcowego z poziomu splunk

Aby uzyskać więcej informacji na temat dodatku Microsoft 365 Defender splunk, zobacz [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Arcsight z mikro fokusem

Nowy program SmartConnector Microsoft 365 Defender zdarzeń, które zawierają alerty ze wszystkich produktów firmy Microsoft 365 Defender — w tym z programu Microsoft Defender for Endpoint — do usługi ArcSight i mapuje je na swoją wspólną platformę zdarzeń (CEF).

Aby uzyskać więcej informacji na temat nowego programu ArcSight SmartConnector dla Microsoft 365 Defender, zobacz [dokumentację produktu ArcSight](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

Program SmartConnector zastępuje poprzednią usługę FlexConnector dla Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>Integracja oprogramowania IBM QRadar z usługą Microsoft 365 Defender, która zawiera program Microsoft Defender for Endpoint, jest teraz obsługiwana przez nowy moduł obsługi urządzeń firmy Microsoft 365 Defender, który nazywa interfejs [API usługi Microsoft 365 Defender Streaming](../defender/streaming-api.md), który umożliwia przesyłanie strumieniowe danych zdarzeń z Microsoft 365 Defender, w tym program Microsoft Defender for Endpoint. Aby uzyskać więcej informacji na temat nowego serwera dsM usługi QRadar Microsoft 365 Defender, zobacz Dokumentacja produktu [firmy IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender), a aby uzyskać więcej informacji na temat typów zdarzeń obsługiwanych przez interfejs API przesyłania strumieniowego, zobacz Obsługiwane [typy zdarzeń](../defender/supported-event-types.md).

Nowi klienci nie są już dołączani przy użyciu poprzedniego modułu obsługi urządzeń ATP (DSM, QRadar Microsoft Defender) i zachęcamy istniejących klientów do przyjęcia nowej usługi dsM usługi Microsoft 365 Defender jako pojedynczego punktu integracji ze wszystkimi produktami firmy Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Ingesting Microsoft Defender for Endpoint events from the Microsoft 365 Defender event streaming API

Microsoft 365 Defender strumieniowe dane zdarzeń obejmują alerty i inne zdarzenia z usługi Microsoft Defender dla punktu końcowego i innych produktów Microsoft Defender. Te zdarzenia mogą być przesyłane strumieniowo do konta usługi Azure Storage lub do Centrum zdarzeń Azure. Model integracji za pośrednictwem centrów zdarzeń jest obecnie obsługiwany przez firmę Splunk i ibm QRadar.

Aby uzyskać więcej informacji, [zobacz integracja Microsoft 365 Defender SIEM](../defender/configure-siem-defender.md).
