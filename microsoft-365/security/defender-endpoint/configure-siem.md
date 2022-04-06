---
title: Integrowanie narzędzi SIEM z Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.openlocfilehash: ed88048b506ecfcddb8394667e7d800927fc1d83
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634916"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Integrowanie narzędzi SIEM z Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Alerty dotyczące alertów przy użyciu narzędzi do zarządzania informacjami i zdarzeniami zabezpieczeń

> [!NOTE]
>
> [Ochrona punktu końcowego w usłudze Microsoft Defender alert](alerts.md) pochodzi z co najmniej jednego podejrzanego lub złośliwego zdarzenia, które wystąpiło na urządzeniu, i powiązanych ze nim informacji. Interfejs API Ochrona punktu końcowego w usłudze Microsoft Defender alertów to najnowszy interfejs API do użycia alertów i zawiera szczegółową listę powiązanych dowodów dla każdego alertu. Aby uzyskać więcej informacji, zobacz [Metody i właściwości alertów oraz](alerts.md) [Alerty listy](get-alerts.md).

Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje narzędzia do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM, Security Information And Event Management), które pozwalają na korzystanie z informacji z dzierżawy przedsiębiorstwa w programie Azure Active Directory (AAD) przy użyciu protokołu uwierzytelniania OAuth 2.0 dla zarejestrowanego AAD  aplikacja reprezentująca określone rozwiązanie SIEM lub łącznik zainstalowany w Twoim środowisku.

Więcej informacji można znaleźć w następujących artykułach:

- [Ochrona punktu końcowego w usłudze Microsoft Defender licencji i warunków użytkowania interfejsów API](api-terms-of-use.md) 
- [Uzyskaj dostęp do interfejsów API usługi ochrony punktu końcowego w usłudze Microsoft Defender](apis-intro.md)
- [Hello world przykład (w tym artykule opisano, jak zarejestrować aplikację w aplikacji Azure Active Directory)](api-hello-world.md)
- [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](exposed-apis-create-app-webapp.md)


Ochrona punktu końcowego w usłudze Microsoft Defender obecnie obsługuje następujące integracje rozwiązań SIEM: 

- [Instytucyjanie zdarzeń i alertów z Microsoft 365 Defender i Ochrona punktu końcowego w usłudze Microsoft Defender i alertów interfejsów API rest](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Inesting Ochrona punktu końcowego w usłudze Microsoft Defender events from the Microsoft 365 Defender event streaming API](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Instytucyjanie zdarzeń i alertów z Microsoft 365 Defender i Ochrona punktu końcowego w usłudze Microsoft Defender i alertów interfejsów API rest

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Insesting incidents from the Microsoft 365 Defender incidents REST API

Aby uzyskać więcej informacji na temat interfejsu API Microsoft 365 Defender zdarzeń, zobacz Metody [i właściwości zdarzeń](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Alerty dotyczące alertów z interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender REST

Aby uzyskać więcej informacji na temat interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender alertów, zobacz Metody [i właściwości alertów](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Integracja narzędzi SIEM z programem Ochrona punktu końcowego w usłudze Microsoft Defender

### <a name="splunk"></a>Splunk

Za pomocą Microsoft 365 Defender Splunk, który obsługuje:

- Alerty dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender użytkownika
- Aktualizowanie alertów w programie Ochrona punktu końcowego w usłudze Microsoft Defender z poziomu splunk

Aby uzyskać więcej informacji na temat dodatku Microsoft 365 Defender splunk, zobacz [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Arcsight z mikro fokusem

Nowy program SmartConnector do obsługi Microsoft 365 Defender zdarzeń, które zawierają alerty ze wszystkich produktów firmy Microsoft 365 Defender — w tym z programu Ochrona punktu końcowego w usłudze Microsoft Defender — do usługi ArcSight i mapuje je na wspólne wydarzenie (CEF).

Aby uzyskać więcej informacji na temat nowego programu ArcSight SmartConnector dla Microsoft 365 Defender, zobacz [dokumentację produktu ArcSight](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

Program SmartConnector zastępuje poprzednią usługę FlexConnector dla Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>Integracja oprogramowania IBM QRadar z usługą Microsoft 365 Defender, która zawiera Ochrona punktu końcowego w usłudze Microsoft Defender, jest teraz obsługiwana przez nowy moduł obsługi Microsoft 365 Defender (DSM, Device Support Module), [który Microsoft 365 Defender interfejsu API przesyłania](../defender/streaming-api.md) strumieniowego, który umożliwia korzystanie z danych zdarzeń przesyłania strumieniowego z Microsoft 365 Defender produktów, w tym Ochrona punktu końcowego w usłudze Microsoft Defender. Aby uzyskać więcej informacji na temat nowego serwera dsM usługi QRadar Microsoft 365 Defender, zobacz Dokumentacja produktu [firmy IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender), a aby uzyskać więcej informacji na temat typów zdarzeń obsługiwanych przez interfejs API przesyłania strumieniowego, zobacz Obsługiwane [typy zdarzeń](../defender/supported-event-types.md).

Nowi klienci nie są już dołączani przy użyciu poprzedniego modułu obsługi urządzeń ATP (DSM, QRadar Microsoft Defender) i zachęcamy istniejących klientów do przyjęcia nowej usługi dsM usługi Microsoft 365 Defender jako pojedynczego punktu integracji ze wszystkimi produktami firmy Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Inesting Ochrona punktu końcowego w usłudze Microsoft Defender events from the Microsoft 365 Defender event streaming API

Microsoft 365 Defender strumieniowe dane zdarzeń obejmują alerty i inne zdarzenia z usługi Ochrona punktu końcowego w usłudze Microsoft Defender i innych produktów Microsoft Defender. Te zdarzenia mogą być przesyłane strumieniowo do konta usługi Azure Storage lub do Azure Event Hubs. Model integracji za pośrednictwem centrów zdarzeń jest obecnie obsługiwany przez firmę Splunk i ibm QRadar.

Aby uzyskać więcej informacji, [zobacz integracja Microsoft 365 Defender SIEM](../defender/configure-siem-defender.md).
