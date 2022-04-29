---
title: Integracja rozwiązania SIEM z Ochrona usługi Office 365 w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: ''
search.appverid:
- MET150
- MOE150
ms.assetid: eb56b69b-3170-4086-82cf-ba40a530fa1b
ms.date: 08/21/2020
ms.collection:
- M365-security-compliance
description: Zintegruj serwer SIEM organizacji z Ochrona usługi Office 365 w usłudze Microsoft Defender i powiązanymi zdarzeniami zagrożeń w interfejsie API zarządzania działaniami Office 365.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2ffa1e59f368af4b3e99cee9939ed0ead0cc686e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131003"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>Integracja rozwiązania SIEM z Ochrona usługi Office 365 w usłudze Microsoft Defender

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Jeśli Organizacja korzysta z serwera zarządzania informacjami o zabezpieczeniach i zdarzeniami (SIEM), możesz zintegrować Ochrona usługi Office 365 w usłudze Microsoft Defender z serwerem SIEM. Tę integrację można skonfigurować przy użyciu [interfejsu API zarządzania działaniami Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

Integracja rozwiązania SIEM umożliwia wyświetlanie informacji, takich jak złośliwe oprogramowanie lub phish wykryte przez Ochrona usługi Office 365 w usłudze Microsoft Defender, w raportach serwera SIEM.

- Aby zobaczyć przykład integracji rozwiązania SIEM z usługą Ochrona usługi Office 365 w usłudze Microsoft Defender, zobacz [blog Tech Community: Ulepszanie skuteczności soc za pomocą Ochrona usługi Office 365 w usłudze Defender i interfejsu API zarządzania O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- Aby dowiedzieć się więcej na temat interfejsów API zarządzania Office 365, zobacz [omówienie interfejsów API zarządzania Office 365](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>Jak działa integracja rozwiązania SIEM

Interfejs API zarządzania działaniami Office 365 pobiera informacje o użytkownikach, administratorach, systemach i akcjach zasad oraz zdarzeniach z dzienników aktywności Microsoft 365 i Azure Active Directory organizacji. Jeśli Twoja organizacja ma Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 lub 2 lub Office 365 E5, możesz użyć [schematu Ochrona usługi Office 365 w usłudze Microsoft Defender](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

Ostatnio zdarzenia z funkcji zautomatyzowanego badania i reagowania w [planie Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) zostały dodane do interfejsu API działania zarządzania Office 365. Oprócz uwzględnienia danych dotyczących podstawowych szczegółów badania, takich jak identyfikator, nazwa i stan, interfejs API zawiera również ogólne informacje o akcjach badania i jednostkach.

Serwer SIEM lub inny podobny system sonduje obciążenie **audit.general** w celu uzyskania dostępu do zdarzeń wykrywania. Aby dowiedzieć się więcej, zobacz [Wprowadzenie z interfejsami API zarządzania Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Wyliczenie: AuditLogRecordType — typ: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

W poniższej tabeli podsumowano wartości **parametru AuditLogRecordType**, które są istotne dla zdarzeń Ochrona usługi Office 365 w usłudze Microsoft Defender:<br/><br/>

| Value | Nazwa elementu członkowskiego | Opis |
|---|---|---|
| 28| ThreatIntelligence | Zdarzenia wyłudzania informacji i złośliwego oprogramowania z Exchange Online Protection i Ochrona usługi Office 365 w usłudze Microsoft Defender. |
| 41| ThreatIntelligenceUrl | Sejf Łączy zdarzenia przesłonięcia bloku i bloku z Ochrona usługi Office 365 w usłudze Microsoft Defender. |
| 47| ThreatIntelligenceAtpContent | Zdarzenia wyłudzania informacji i złośliwego oprogramowania dla plików w usłudze SharePoint Online, OneDrive dla Firm i Microsoft Teams z Ochrona usługi Office 365 w usłudze Microsoft Defender. |
| 64| AirInvestigation | Zdarzenia zautomatyzowanego badania i reagowania, takie jak szczegóły badania i odpowiednie artefakty, z planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2. |

> [!IMPORTANT]
> Aby skonfigurować integrację rozwiązania SIEM z usługą Ochrona usługi Office 365 w usłudze Microsoft Defender, musisz mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md).
>
> Rejestrowanie inspekcji musi być włączone dla środowiska Microsoft 365. Aby uzyskać pomoc w tej sprawie, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Zobacz też

[Office 365 badania zagrożeń i reagowania na nie](office-365-ti.md)

[Zautomatyzowane badanie i reagowanie (AIR) w Office 365](automated-investigation-response-office.md)
