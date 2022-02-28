---
title: Rozszerzanie zaawansowanego zakresu wyszukiwania o odpowiednie ustawienia
description: Sprawdzanie ustawień inspekcji na Windows urządzeniach i innych ustawieniach w celu zapewnienia, że będziesz mieć dostęp do najbardziej kompleksowych danych podczas zaawansowanego wyszukiwania
keywords: zaawansowane szukanie, zdarzenie, przestaw, jednostka, ustawienia inspekcji, zarządzanie kontami użytkowników, zarządzanie grupą zabezpieczeń, szukanie zagrożeń, szukanie przed cyberzagrożeniami, wyszukiwanie, zapytanie, telemetria, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dd61fa434eaf2130f0fcb0f28df9a20d696e04ec
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989710"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Rozszerzanie zaawansowanego zakresu wyszukiwania o odpowiednie ustawienia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

[Zaawansowane wyszukiwania](advanced-hunting-overview.md) są wykorzystywane na podstawie danych pochodzących z różnych źródeł, takich jak urządzenia, Office 365 obszarów roboczych, usługi Azure AD i programu Microsoft Defender dla tożsamości. Aby uzyskać jak naj obszerne dane, upewnij się, że w odpowiadających im źródłach danych są odpowiednie ustawienia.

## <a name="advanced-security-auditing-on-windows-devices"></a>Zaawansowana inspekcja zabezpieczeń na Windows urządzeniach
Włącz te zaawansowane ustawienia inspekcji, aby mieć pewność, że będziesz mieć dostęp do danych o działaniach na Twoich urządzeniach, takich jak zarządzanie kontem lokalnym, zarządzanie lokalną grupą zabezpieczeń i tworzenie usług.

| Data (Dane) | Opis | Tabela schematu | Jak skonfigurować |
| --- | --- | --- | --- |
| Zarządzanie kontem | Zdarzenia przechwytywane jako różne wartości `ActionType` wskazujące lokalne tworzenie, usuwanie i inne działania związane z kontem | [DeviceEvents](advanced-hunting-deviceevents-table.md) | — Wdrażanie zaawansowanych zasad inspekcji zabezpieczeń: [Inspekcja zarządzania kontami użytkowników](/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [Informacje o zaawansowanych zasadach inspekcji zabezpieczeń](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Zarządzanie grupą zabezpieczeń | Zdarzenia przechwytywane jako różne wartości `ActionType` wskazujące na tworzenie lokalnej grupy zabezpieczeń i inne działania związane z zarządzaniem grupą lokalną | [DeviceEvents](advanced-hunting-deviceevents-table.md) | — Wdrażanie zaawansowanych zasad inspekcji zabezpieczeń: [Zarządzanie grupą zabezpieczeń inspekcji](/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [Informacje o zaawansowanych zasadach inspekcji zabezpieczeń](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Instalacja usługi | Zdarzenia zarejestrowane za pomocą wartości `ActionType` `ServiceInstalled`, wskazującej, że usługa została utworzona | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Wdrażanie zaawansowanych zasad inspekcji zabezpieczeń: [Rozszerzenie systemu zabezpieczeń inspekcji](/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [Informacje o zaawansowanych zasadach inspekcji zabezpieczeń](/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>Czujnik usługi Microsoft Defender for Identity na kontrolerze domeny
Jeśli używasz usługi Active Directory w środowisku lokalnym, musisz zainstalować czujnik usługi Microsoft Defender for Identity na kontrolerze domeny, aby pobrać dane do usługi Microsoft Defender for Identity. Po zainstalowaniu i prawidłowym skonfigurowaniu te dane są również wykorzystywane do zaawansowanego wyszukiwania w programie Microsoft Defender dla tożsamości i zapewniają bardziej obraz obrazowy informacji o tożsamości i zdarzeń w Twojej sieci. Te dane zwiększają także możliwości programu Microsoft Defender dla tożsamości w celu generowania odpowiednich alertów, które są również objęte zaawansowanymi wyszukiwaniami. 

| Data (Dane) | Opis | Tabela schematu | Jak skonfigurować |
| --- | --- | --- | --- |
| Kontroler domeny | Dane z lokalnej usługi Active Directory wysyłane do usługi Microsoft Defender for Identity, wzbogacając informacje związane z tożsamością, takie jak szczegóły konta, aktywność logowania i zapytania usługi Active Directory | Wiele tabel, w [tym IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) i [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)  | - [Zainstaluj czujnik usługi Microsoft Defender for Identity](/azure-advanced-threat-protection/install-atp-step4)<br>- [Włączanie odpowiednich zdarzeń Windows zdarzenia](/azure-advanced-threat-protection/configure-event-collection) |

>[!NOTE]
>Niektóre tabele w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Tematy pokrewne
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Opis schematu](advanced-hunting-schema-tables.md)