---
title: Zintegruj narzędzia SIEM z Microsoft 365 Defender
description: Dowiedz się, jak korzystać z interfejsu API usługi REST oraz jak skonfigurować obsługiwane informacje o zabezpieczeniach i narzędzia do zarządzania zdarzeniami w celu odbierania i odbierania wykrywania.
keywords: konfigurowanie siem, narzędzi do zarządzania informacjami i zdarzeniami zabezpieczeń, splunku, arcusight, niestandardowych wskaźników, interfejsu API rest, definicji alertów, wskaźników naruszenia bezpieczeństwa
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 210705bd3392e4aeeadd815ed8c1840e772f6ad9
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005283"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>Zintegruj narzędzia SIEM z Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Przyciąganie Microsoft 365 Defender zdarzeń i przesyłanie strumieniowe danych zdarzeń przy użyciu narzędzi do zarządzania zdarzeniami i informacjami o zabezpieczeniach

> [!NOTE]
>
> - [Microsoft 365 Defender zdarzenia składają](incident-queue.md) się ze zbiorów skorelowanych alertów i ich dowodów.
> - [Microsoft 365 Defender Api przesyłania strumieniowego](streaming-api.md) przesyła dane zdarzeń z Microsoft 365 Defender do centrum zdarzeń lub kont magazynu platformy Azure.

Program Microsoft 365 Defender obsługuje narzędzia do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), które pozwalają na korzystanie z informacji z dzierżawy przedsiębiorstwa w programie Azure Active Directory (AAD) przy użyciu protokołu uwierzytelniania OAuth 2.0 dla zarejestrowanej aplikacji programu AAD reprezentującej określone rozwiązanie SIEM lub łącznik zainstalowany w Twoim w środowisku. 

Więcej informacji można znaleźć w następujących artykułach:

- [Microsoft 365 Defender licencji i warunków użytkowania interfejsów API](api-terms.md)
- [Uzyskiwanie dostępu do Microsoft 365 Defender API](api-access.md)
- [Przykład witaj świecie](api-hello-world.md)
- [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](api-create-app-web.md)

Istnieją dwa podstawowe modele, w których należy uzyskać informacje dotyczące zabezpieczeń: 

1.  Inesting Microsoft 365 Defender i ich zawarte alerty z interfejsu API REST na platformie Azure. 

2.  Ingesting streaming event data through Azure Event Hubs or Azure Storage Accounts. 

Microsoft 365 Defender obecnie obsługuje następujące integracje rozwiązań SIEM: 

- [Insesting incidents from the incidents REST API](#ingesting-incidents-from-the-incidents-rest-api)
- [Ingesting streaming event data via Event Hub](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Insesting incidents from the incidents REST API

### <a name="incident-schema"></a>Schemat zdarzenia
Aby uzyskać więcej informacji na Microsoft 365 Defender zdarzeń, w tym metadanych zawierających alerty i jednostki dowodu, zobacz [Mapowanie schematu](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

Za pomocą Microsoft 365 Defender Splunk, który obsługuje:

- Oznaczanie zdarzeń zawierających alerty z następujących produktów, które są mapowane na model informacji wspólnych (CIM) Splunka:

  - Microsoft 365 Defender
  - Ochrona punktu końcowego w usłudze Microsoft Defender
  - Microsoft Defender for Identity and Azure Active Directory Identity Protection
  - Usługa Microsoft Defender dla aplikacji w chmurze

- Aktualizowanie zdarzeń w programie Microsoft 365 Defender z poziomu splunk

- Ingesting Defender for Endpoint alerts (from the Defender for Endpoint's Azure endpoint) and updating these alerts

Aby uzyskać więcej informacji na temat dodatku Microsoft 365 Defender splunk, zobacz [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Arcsight z mikro fokusem

Nowy program SmartConnector do Microsoft 365 Defender zdarzeń typu ArcSight i mapuje je na swoją wspólną platformę zdarzeń (CEF).

Aby uzyskać więcej informacji na temat nowego programu ArcSight SmartConnector dla Microsoft 365 Defender, zobacz [Dokumentację produktu ArcSight](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

Program SmartConnector zastępuje poprzednią usługę FlexConnector programu Microsoft Defender dla punktu końcowego.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Ingesting streaming event data via Event Hubs

Najpierw musisz przesyłać strumieniowo zdarzenia z dzierżawy usługi AAD do centrum zdarzeń lub konta usługi Azure Storage. Aby uzyskać więcej informacji, zobacz [Interfejs API przesyłania strumieniowego](../defender/streaming-api.md).

Aby uzyskać więcej informacji na temat typów zdarzeń obsługiwanych przez interfejs API przesyłania strumieniowego, zobacz [Obsługiwane typy zdarzeń przesyłania strumieniowego](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk
Używaj dodatku Splunk dla usług firmy Microsoft w chmurze, aby ingest wydarzeń z centrum zdarzeń Azure.  


Aby uzyskać więcej informacji na temat dodatku Splunk dla usług Firmy Microsoft w chmurze, zobacz [Splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>Użyj nowego modułu obsługi urządzeń (DSM) IBM QRadar Microsoft 365 Defender, który nazywa interfejs API usługi [Microsoft 365 Defender Streaming](streaming-api.md), który umożliwia przesyłanie strumieniowe danych zdarzeń z Microsoft 365 Defender produktów. Aby uzyskać więcej informacji na temat obsługiwanych typów zdarzeń, zobacz [Obsługiwane typy zdarzeń](supported-event-types.md).
