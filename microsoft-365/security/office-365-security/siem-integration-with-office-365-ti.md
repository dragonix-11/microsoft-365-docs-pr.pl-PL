---
title: Integracja usług SIEM z programem Microsoft Defender dla Office 365
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
description: Zintegruj serwer SIEM organizacji z programem Microsoft Defender Office 365 i powiązanymi zdarzeniami związanymi z zagrożeniami w interfejsie API Office 365 Zarządzanie aktywnością.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3dbb175ba169c9bb8f4d7240d59d9886391167c3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984369"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>Integracja usług SIEM z programem Microsoft Defender dla Office 365

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Jeśli Twoja organizacja korzysta z serwera zarządzania informacjami i zdarzeniami zabezpieczeń, możesz zintegrować program Microsoft Defender dla Office 365 z serwerem SIEM. Tę integrację można skonfigurować przy użyciu [interfejsu API Office 365 Zarządzanie aktywnością](/office/office-365-management-api/office-365-management-activity-api-reference).

Integracja SIEM umożliwia wyświetlanie w raportach serwera SIEM informacji, takich jak złośliwe oprogramowanie lub wyłudzy informacji wykryte przez usługę Microsoft Defender for Office 365.

- Aby zobaczyć przykład integracji SIEM z programem Microsoft Defender dla programu Office 365, zobacz blog poświęcony technologii Community: Poprawa skuteczności soc za pomocą programu Defender dla programu Office 365 i interfejsu [API zarządzania usługi O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- Aby dowiedzieć się więcej o interfejsach API zarządzania Office 365, zobacz omówienie Office 365 [interfejsów API zarządzania](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>Jak działa integracja SIEM

Interfejs API Office 365 Zarządzanie aktywnością pobiera informacje o działaniach i zdarzeniach użytkownika, administratora, systemu oraz zasad z dzienników aktywności Microsoft 365 i Azure Active Directory organizacji. Jeśli Twoja organizacja ma program Microsoft Defender for Office 365 Plan 1 lub 2 albo Office 365 E5, możesz użyć programu [Microsoft Defender dla Office 365 schematu](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

Ostatnio do interfejsu API działań zarządzania zarządzaniem w programie [Microsoft Defender](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) dla systemu Office 365 dodano zdarzenia z automatycznego badania i odpowiedzi z planu Office 365 2. Oprócz danych dotyczących podstawowych szczegółów badania, takich jak identyfikator, nazwa i stan, interfejs API zawiera również szczegółowe informacje o akcjach badania i jednostkach.

Serwer SIEM lub inny podobny system sonduje obciążenie **audit.general** w celu uzyskania dostępu do zdarzeń wykrywania. Aby dowiedzieć się więcej, zobacz [Rozpoczynanie pracy z interfejsami API Office 365 zarządzania](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Wylima: AuditLogRecordType — typ: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

W poniższej tabeli podsumowano wartości **typu AuditLogRecordType**, które są istotne dla programu Microsoft Defender w przypadku Office 365 zdarzeń:<br/><br/>

| Value | Nazwa członka | Opis |
|---|---|---|
| 28| ThreatIntelligence | Wyłudzanie informacji i zdarzenia złośliwego oprogramowania z Exchange Online Protection i programu Microsoft Defender dla Office 365. |
| 41| ThreatIntelligenceUrl | Sejf Linki do zdarzeń blokowania i blokowania zastępowania zdarzeń z programu Microsoft Defender dla Office 365. |
| 47| ThreatIntelligenceAtpContent | Wyłudzanie informacji i zdarzenia złośliwego oprogramowania dla plików w SharePoint Online, OneDrive dla Firm i Microsoft Teams, z usługi Microsoft Defender dla Office 365. |
| 64| AirInvestigation | Zautomatyzowane badania i zdarzenia reakcji, takie jak szczegóły badania i istotne artefakty, z usługi Microsoft Defender Office 365 Plan 2. |

> [!IMPORTANT]
> Aby skonfigurować integrację usług SIEM z usługą Microsoft Defender for Office 365, musisz mieć przypisaną rolę administratora globalnego lub administratora zabezpieczeń w portalu Microsoft 365 Defender. Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender użytkowników](permissions-microsoft-365-security-center.md).
>
> Rejestrowanie inspekcji musi być włączone dla Microsoft 365 użytkownika. Aby uzyskać pomoc w tym związku, zobacz Włączanie lub wyłączanie wyszukiwania [w dzienniku inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Zobacz też

[Office 365 i reagowanie na zagrożenia](office-365-ti.md)

[Zautomatyzowane badania i odpowiedzi (AIR) w programie Office 365](automated-investigation-response-office.md)