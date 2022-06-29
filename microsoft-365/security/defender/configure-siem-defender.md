---
title: Integrowanie narzędzi SIEM z usługą Microsoft 365 Defender
description: Dowiedz się, jak używać interfejsu API REST i konfigurować obsługiwane narzędzia do zarządzania informacjami i zdarzeniami zabezpieczeń w celu odbierania i wykrywania ściągnięcia.
keywords: konfigurowanie narzędzi do zarządzania informacjami o zabezpieczeniach i zdarzeniami, splunk, arcsight, niestandardowe wskaźniki, interfejs API rest, definicje alertów, wskaźniki naruszenia zabezpieczeń
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
ms.openlocfilehash: 3e2772fd458c60e48f78c0d4b816cdac8ca25940
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530324"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>Integrowanie narzędzi SIEM z usługą Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>Ściąganie zdarzeń Microsoft 365 Defender i przesyłanie strumieniowe danych zdarzeń przy użyciu narzędzi do zarządzania informacjami i zdarzeniami zabezpieczeń (SIEM)

> [!NOTE]
>
> - [Microsoft 365 Defender Zdarzenia](incident-queue.md) składa się z kolekcji skorelowanych alertów i ich dowodów.
> - [Microsoft 365 Defender interfejs API przesyłania strumieniowego](streaming-api.md) przesyła strumieniowo dane zdarzeń z Microsoft 365 Defender do centrów zdarzeń lub kont usługi Azure Storage.

Microsoft 365 Defender obsługuje narzędzia do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM) pozyskujące informacje z dzierżawy przedsiębiorstwa w usłudze Azure Active Directory (AAD) przy użyciu protokołu uwierzytelniania OAuth 2.0 dla zarejestrowanej aplikacji usługi AAD reprezentującej określone rozwiązanie SIEM lub łącznik zainstalowany w środowisku. 

Więcej informacji można znaleźć w następujących artykułach:

- [Microsoft 365 Defender licencji interfejsów API i warunków użytkowania](api-terms.md)
- [Uzyskiwanie dostępu do interfejsów API Microsoft 365 Defender](api-access.md)
- [Hello World — przykład](api-hello-world.md)
- [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](api-create-app-web.md)

Istnieją dwa podstawowe modele do pozyskiwania informacji o zabezpieczeniach: 

1.  Pozyskiwanie zdarzeń Microsoft 365 Defender i zawartych w nich alertów z interfejsu API REST na platformie Azure. 

2.  Pozyskiwanie danych zdarzeń przesyłania strumieniowego za pośrednictwem kont usługi Azure Event Hubs lub konta usługi Azure Storage. 

Microsoft 365 Defender obecnie obsługuje następujące integracje rozwiązań SIEM: 

- [Pozyskiwanie zdarzeń z interfejsu API REST zdarzeń](#ingesting-incidents-from-the-incidents-rest-api)
- [Pozyskiwanie danych zdarzeń przesyłania strumieniowego za pośrednictwem centrum zdarzeń](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>Pozyskiwanie zdarzeń z interfejsu API REST zdarzeń

### <a name="incident-schema"></a>Schemat zdarzeń
Aby uzyskać więcej informacji na temat Microsoft 365 Defender właściwości zdarzenia, w tym zawartych metadanych jednostek alertów i dowodów, zobacz [Mapowanie schematu](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

Korzystanie z nowego, w pełni obsługiwanego dodatku Splunk dla usługi Microsoft Security, który obsługuje:

- Pozyskiwanie zdarzeń zawierających alerty z następujących produktów, które są mapowane na model Common Information Model (CIM) firmy Splunk:

  - Microsoft 365 Defender
  - Ochrona punktu końcowego w usłudze Microsoft Defender
  - Microsoft Defender for Identity i azure Active Directory Identity Protection
  - Microsoft Defender for Cloud Apps

- Pozyskiwanie alertów usługi Defender for Endpoint (z punktu końcowego platformy Azure w usłudze Defender for Endpoint) i aktualizowanie tych alertów

- Obsługa aktualizowania Microsoft 365 Defender zdarzeń i/lub alertów Ochrona punktu końcowego w usłudze Microsoft Defender i odpowiednich pulpitów nawigacyjnych została przeniesiona do aplikacji Microsoft 365 for Splunk. 

Aby uzyskać więcej informacji na temat:

- Dodatek Splunk dla usługi Microsoft Security można znaleźć w dodatku [Microsoft Security Na platformie Splunkbase](https://splunkbase.splunk.com/app/6207/#/overview)

- Aplikacja Platformy Microsoft 365 dla rozwiązania Splunk— zobacz [Aplikację platformy Microsoft 365 na platformie Splunkbase](https://splunkbase.splunk.com/app/3786/)

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Nowy program SmartConnector do Microsoft 365 Defender pozyskuje zdarzenia do usługi ArcSight i mapuje je na platformę Common Event Framework (CEF).

Aby uzyskać więcej informacji na temat nowego programu ArcSight SmartConnector for Microsoft 365 Defender, zobacz [Dokumentacja produktu ArcSight](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

Funkcja SmartConnector zastępuje poprzednią funkcję FlexConnector dla Ochrona punktu końcowego w usłudze Microsoft Defender, która została przestarzała.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>Pozyskiwanie danych zdarzeń przesyłania strumieniowego za pośrednictwem usługi Event Hubs

Najpierw musisz przesyłać strumieniowo zdarzenia z dzierżawy usługi AAD do usługi Event Hubs lub konta usługi Azure Storage. Aby uzyskać więcej informacji, zobacz [Interfejs API przesyłania strumieniowego](../defender/streaming-api.md).

Aby uzyskać więcej informacji na temat typów zdarzeń obsługiwanych przez interfejs API przesyłania [strumieniowego, zobacz Obsługiwane typy zdarzeń przesyłania strumieniowego](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk

Użyj dodatku Splunk dla Cloud Services firmy Microsoft, aby pozyskiwać zdarzenia z Azure Event Hubs.  

Aby uzyskać więcej informacji na temat dodatku Splunk dla usługi Microsoft Cloud Services, zobacz [dodatek Microsoft Cloud Services Splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>Użyj nowego modułu obsługi urządzeń IBM QRadar Microsoft 365 Defender Device Support Module (DSM), który wywołuje [interfejs API przesyłania strumieniowego Microsoft 365 Defender](streaming-api.md), który umożliwia pozyskiwanie danych zdarzeń przesyłania strumieniowego z produktów Microsoft 365 Defender za pośrednictwem usługi Event Hubs lub konta usługi Azure Storage. Aby uzyskać więcej informacji na temat obsługiwanych typów zdarzeń, zobacz [Obsługiwane typy zdarzeń](supported-event-types.md).
