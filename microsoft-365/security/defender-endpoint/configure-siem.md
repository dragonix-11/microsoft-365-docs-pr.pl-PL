---
title: Integrowanie narzędzi SIEM z Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak pozyskiwać zdarzenia i alerty oraz integrować narzędzia SIEM.
keywords: konfigurowanie narzędzi do zarządzania informacjami o zabezpieczeniach i zdarzeniami, splunk, arcsight, niestandardowe wskaźniki, interfejs API rest, definicje alertów, wskaźniki naruszenia zabezpieczeń
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
ms.openlocfilehash: d679ac0d01a7e922e49b72b574a43e6f684179f9
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664507"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>Integrowanie narzędzi SIEM z Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>Pozyskiwanie alertów przy użyciu narzędzi do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM)

> [!NOTE]
>
> [Ochrona punktu końcowego w usłudze Microsoft Defender Alert](alerts.md) składa się z jednego lub kilku podejrzanych lub złośliwych zdarzeń, które wystąpiły na urządzeniu, oraz powiązanych z nimi szczegółów. Interfejs API alertów Ochrona punktu końcowego w usłudze Microsoft Defender jest najnowszym interfejsem API do użycia alertów i zawiera szczegółową listę powiązanych dowodów dla każdego alertu. Aby uzyskać więcej informacji, zobacz [Metody alertów i właściwości](alerts.md) oraz [Lista alertów](get-alerts.md).

Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje narzędzia do zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM) pozyskujące informacje z dzierżawy przedsiębiorstwa w Azure Active Directory (AAD) przy użyciu protokołu uwierzytelniania OAuth 2.0 dla zarejestrowanego AAD  aplikacja reprezentująca określone rozwiązanie SIEM lub łącznik zainstalowany w środowisku.

Więcej informacji można znaleźć w następujących artykułach:

- [licencja i warunki użytkowania interfejsów API Ochrona punktu końcowego w usłudze Microsoft Defender](api-terms-of-use.md) 
- [Uzyskaj dostęp do interfejsów API usługi ochrony punktu końcowego w usłudze Microsoft Defender](apis-intro.md)
- [Hello world przykład (opisuje sposób rejestrowania aplikacji w Azure Active Directory)](api-hello-world.md)
- [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](exposed-apis-create-app-webapp.md)


Ochrona punktu końcowego w usłudze Microsoft Defender obecnie obsługuje następujące integracje rozwiązań SIEM: 

- [Pozyskiwanie zdarzeń i alertów z Microsoft 365 Defender i Ochrona punktu końcowego w usłudze Microsoft Defender zdarzeń i alertów interfejsów API REST](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [Pozyskiwanie zdarzeń Ochrona punktu końcowego w usłudze Microsoft Defender z interfejsu API przesyłania strumieniowego zdarzeń Microsoft 365 Defender](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>Pozyskiwanie zdarzeń i alertów z Microsoft 365 Defender i Ochrona punktu końcowego w usłudze Microsoft Defender zdarzeń i alertów interfejsów API REST

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>Pozyskiwanie zdarzeń z interfejsu API REST zdarzeń Microsoft 365 Defender

Aby uzyskać więcej informacji na temat interfejsu API zdarzeń Microsoft 365 Defender, zobacz [metody i właściwości zdarzeń](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>Pozyskiwanie alertów z interfejsu API REST alertów Ochrona punktu końcowego w usłudze Microsoft Defender

Aby uzyskać więcej informacji na temat interfejsu API alertów Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [metody alertów i właściwości](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>Integracja narzędzi SIEM z Ochrona punktu końcowego w usłudze Microsoft Defender

### <a name="splunk"></a>Splunk

Korzystanie z dodatku Microsoft 365 Defender dla aplikacji Splunk, który obsługuje:

- Pozyskiwanie alertów Ochrona punktu końcowego w usłudze Microsoft Defender
- Aktualizowanie alertów w Ochrona punktu końcowego w usłudze Microsoft Defender z poziomu programu Splunk

Aby uzyskać więcej informacji na temat dodatku Microsoft 365 Defender dla aplikacji Splunk, zobacz [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

Nowy program SmartConnector do Microsoft 365 Defender pozyskuje zdarzenia zawierające alerty ze wszystkich produktów Microsoft 365 Defender — w tym z Ochrona punktu końcowego w usłudze Microsoft Defender — do usługi ArcSight i mapuje je na swoje wspólne zdarzenie Framework (CEF).

Aby uzyskać więcej informacji na temat nowego programu ArcSight SmartConnector for Microsoft 365 Defender, zobacz [dokumentację produktu ArcSight](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

Funkcja SmartConnector zastępuje poprzednią funkcję FlexConnector dla Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>Integracja rozwiązania IBM QRadar z usługą Microsoft 365 Defender obejmująca Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz obsługiwana przez nowy moduł Microsoft 365 Defender Device Support Module (DSM), który wywołuje [ Microsoft 365 Defender interfejs API przesyłania strumieniowego](../defender/streaming-api.md), który umożliwia pozyskiwanie danych zdarzeń przesyłania strumieniowego z produktów Microsoft 365 Defender, w tym Ochrona punktu końcowego w usłudze Microsoft Defender. Aby uzyskać więcej informacji na temat nowego modułu DSM Microsoft 365 Defender QRadar, zobacz [Dokumentacja produktu IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender), a aby uzyskać więcej informacji na temat obsługiwanych typów zdarzeń interfejsu API przesyłania strumieniowego, zobacz [Obsługiwane typy zdarzeń](../defender/supported-event-types.md).

Nowi klienci nie są już dołączani przy użyciu poprzedniego modułu DSM (QRadar Microsoft Defender ATP Device Support Module), a istniejący klienci są zachęcani do przyjęcia nowej Microsoft 365 Defender DSM jako jednego punktu integracji ze wszystkimi produktami Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>Pozyskiwanie zdarzeń Ochrona punktu końcowego w usłudze Microsoft Defender z interfejsu API przesyłania strumieniowego zdarzeń Microsoft 365 Defender

Microsoft 365 Defender dane zdarzeń przesyłania strumieniowego obejmują alerty i inne zdarzenia z Ochrona punktu końcowego w usłudze Microsoft Defender i innych produktów usługi Microsoft Defender. Te zdarzenia mogą być przesyłane strumieniowo do konta Storage platformy Azure lub do Azure Event Hubs. Model integracji za pośrednictwem centrów zdarzeń jest obecnie obsługiwany przez firmy Splunk i IBM QRadar.

Aby uzyskać więcej informacji, zobacz [integrację Microsoft 365 Defender SIEM](../defender/configure-siem-defender.md).
