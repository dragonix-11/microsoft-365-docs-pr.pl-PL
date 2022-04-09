---
title: Role niestandardowe kontroli dostępu opartej na rolach
description: Dowiedz się, jak zarządzać rolami niestandardowymi w portalu Microsoft 365 Defender
keywords: dostęp, uprawnienia, Microsoft 365 Defender, M365, zabezpieczenia, MCAS, Cloud App Security, Ochrona punktu końcowego w usłudze Microsoft Defender , zakres, określanie zakresu, kontrola dostępu oparta na rolach, dostęp oparty na rolach, dostęp oparty na rolach, uwierzytelnianie oparte na rolach, kontrola dostępu oparta na rolach w usłudze MDO, role, grupy ról, dziedziczenie uprawnień, uprawnienia szczegółowe
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 94330e319eeb44618c1e11b27da7b3d63c08d203
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731356"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>Role niestandardowe w kontroli dostępu opartej na rolach dla Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Dotyczy:**

- Microsoft 365 Defender
 
Istnieją dwa typy ról, które mogą służyć do uzyskiwania dostępu do Microsoft 365 Defender:
- **Role Azure Active Directory globalnych (AD)**
- **Role niestandardowe**

Dostępem do Microsoft 365 Defender można zarządzać zbiorczo przy użyciu [ról globalnych w Azure Active Directory (AAD)](m365d-permissions.md)

Jeśli potrzebujesz większej elastyczności i kontroli nad dostępem do określonych danych produktów, Microsoft 365 Defender dostępem można zarządzać przy użyciu tworzenia ról niestandardowych za pośrednictwem każdego odpowiedniego portalu zabezpieczeń.  

Na przykład rola niestandardowa utworzona za pośrednictwem Ochrona punktu końcowego w usłudze Microsoft Defender umożliwi dostęp do odpowiednich danych produktu, w tym danych punktu końcowego w portalu Microsoft 365 Defender. Podobnie rola niestandardowa utworzona za pośrednictwem Ochrona usługi Office 365 w usłudze Microsoft Defender umożliwiłaby dostęp do odpowiednich danych produktu, w tym danych współpracy & poczty e-mail w portalu Microsoft 365 Defender.

Użytkownicy z istniejącymi rolami niestandardowymi mogą uzyskiwać dostęp do danych w portalu Microsoft 365 Defender zgodnie z istniejącymi uprawnieniami obciążenia bez konieczności dodatkowej konfiguracji.

## <a name="create-and-manage-custom-roles"></a>Tworzenie ról niestandardowych i zarządzanie nimi
Niestandardowe role i uprawnienia można tworzyć i zarządzać osobno za pośrednictwem każdego z następujących portali zabezpieczeń: 

- Ochrona punktu końcowego w usłudze Microsoft Defender — [edytowanie ról w Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/user-roles.md)
- Ochrona usługi Office 365 w usłudze Microsoft Defender — [uprawnienia w Centrum zgodności & zabezpieczeń](../office-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide)
- Microsoft Defender for Cloud Apps — [zarządzanie dostępem administratora](/cloud-app-security/manage-admins)

Każda rola niestandardowa utworzona za pośrednictwem pojedynczego portalu umożliwia dostęp do danych odpowiedniego portalu produktu. Na przykład rola niestandardowa utworzona za pośrednictwem Ochrona punktu końcowego w usłudze Microsoft Defender będzie zezwalać tylko na dostęp do danych punktu końcowego w usłudze Defender.

> [!TIP]
> Uprawnienia i role można również uzyskać za pośrednictwem portalu Microsoft 365 Defender, wybierając pozycję Uprawnienia & ról w okienku nawigacji. Dostęp do Microsoft Defender for Cloud Apps jest zarządzany za pośrednictwem portalu Defender dla Chmury Apps i kontroluje również dostęp do Microsoft Defender for Identity.  Zobacz [Microsoft Defender for Cloud Apps](/cloud-app-security/manage-admins)

> [!NOTE]
> Role niestandardowe utworzone w Microsoft Defender for Cloud Apps również mają dostęp do danych Microsoft Defender for Identity. Użytkownicy z rolami administratora grupy użytkowników lub administratora aplikacji/wystąpienia Microsoft Defender for Cloud Apps nie mogą uzyskiwać dostępu do danych Microsoft Defender for Cloud Apps za pośrednictwem portalu Microsoft 365 Defender.

## <a name="manage-permissions-and-roles-in-the-microsoft-365-defender-portal"></a>Zarządzanie uprawnieniami i rolami w portalu Microsoft 365 Defender
Uprawnieniami i rolami można również zarządzać w portalu Microsoft 365 Defender:

1. Zaloguj się do portalu Microsoft 365 Defender pod adresem security.microsoft.com.
2. W okienku nawigacji wybierz pozycję **Uprawnienia & ról**.
3. W nagłówku **Uprawnienia** wybierz pozycję **Role**.

> [!NOTE]
> Dotyczy to tylko Ochrona usługi Office 365 w usłudze Defender i usługi Defender dla punktu końcowego. Dostęp do innych obciążeń musi odbywać się w odpowiednich portalach.


## <a name="required-roles-and-permissions"></a>Wymagane role i uprawnienia
W poniższej tabeli przedstawiono role i uprawnienia wymagane do uzyskania dostępu do każdego ujednoliconego środowiska w każdym obciążeniu. Role zdefiniowane w poniższej tabeli odnoszą się do ról niestandardowych w poszczególnych portalach i nie są połączone z rolami globalnymi w usłudze Azure AD, nawet jeśli mają podobną nazwę.

> [!NOTE]
> Zarządzanie zdarzeniami wymaga uprawnień do zarządzania dla wszystkich produktów, które są częścią zdarzenia.
 
| **Jedna z następujących ról jest wymagana do Microsoft 365 Defender**  | **Jedna z następujących ról jest wymagana dla usługi Defender for Endpoint**  | **Jedna z następujących ról jest wymagana dla Ochrona usługi Office 365 w usłudze Defender** | **Jedna z następujących ról jest wymagana w przypadku aplikacji Defender dla Chmury** | 
|---------|---------|---------|---------|
| Wyświetlanie danych badania: <ul><li>Strona alertu</li> <li>Kolejka alertów</li> <li>Zdarzenia</li>  <li>Kolejka zdarzeń</li> <li>Centrum akcji</li></ul>| Wyświetlanie danych — operacje zabezpieczeń | <ul><li>Zarządzanie alertami tylko w widoku </li> <li>Konfiguracja organizacji</li><li>Dzienniki inspekcji</li> <li>Dzienniki inspekcji tylko do wyświetlania</li> <li>Czytelnik zabezpieczeń</li> <li>Administrator zabezpieczeń</li><li>Adresaci tylko do wyświetlania</li></ul>  | <ul><li>Administrator globalny</li> <li>Administrator zabezpieczeń</li> <li>Administrator zgodności</li> <li>Operator zabezpieczeń</li> <li>Czytelnik zabezpieczeń</li> <li>Czytelnik globalny</li></ul> |
| Wyświetlanie danych wyszukiwania zagrożeń | Wyświetlanie danych — operacje zabezpieczeń | <ul><li>Czytelnik zabezpieczeń</li> <li>Administrator zabezpieczeń</li> <li>Adresaci tylko do wyświetlania</li> | <ul><li>Administrator globalny</li> <li>Administrator zabezpieczeń</li> <li>Administrator zgodności</li> <li>Operator zabezpieczeń</li> <li>Czytelnik zabezpieczeń</li> <li>Czytelnik globalny</li></ul> |
| Zarządzanie alertami i zdarzeniami | Badanie alertów | <ul><li>Zarządzaj alertami</li> <li>Administrator zabezpieczeń</li> | <ul><li>Administrator globalny</li> <li>Administrator zabezpieczeń</li> <li>Administrator zgodności</li> <li>Operator zabezpieczeń</li> <li>Czytelnik zabezpieczeń</li></ul> |
| Korygowanie centrum akcji | Aktywne akcje korygowania — operacje zabezpieczeń | Wyszukiwanie i przeczyszczanie | |
| Ustawianie wykrywania niestandardowego | Zarządzanie ustawieniami zabezpieczeń |<ul><li>Zarządzaj alertami</li> <li>Administrator zabezpieczeń</li></ul> | <ul><li>Administrator globalny</li> <li>Administrator zabezpieczeń</li> <li>Administrator zgodności</li> <li>Operator zabezpieczeń</li> <li>Czytelnik zabezpieczeń</li> <li>Czytelnik globalny</li></ul> |
| Analiza zagrożeń | Dane alertów i zdarzeń: <ul><li>Wyświetlanie danych — operacje zabezpieczeń</li></ul>Środki zaradcze tvm:<ul><li>Wyświetlanie danych — zagrożenia i zarządzanie lukami w zabezpieczeniach</li></ul> | Dane alertów i zdarzeń:<ul> <li>Zarządzanie alertami tylko w widoku</li> <li>Zarządzaj alertami</li> <li>Konfiguracja organizacji</li><li>Dzienniki inspekcji</li> <li>Dzienniki inspekcji tylko do wyświetlania</li><li>Czytelnik zabezpieczeń</li> <li>Administrator zabezpieczeń</li><li>Adresaci tylko do wyświetlania</li> </ul> Uniemożliwiono próby wysłania wiadomości e-mail: <ul><li>Czytelnik zabezpieczeń</li> <li>Administrator zabezpieczeń</li><li>Adresaci tylko do wyświetlania</li> | Niedostępne dla użytkowników Defender dla Chmury Apps lub MDI |

Aby na przykład wyświetlić dane wyszukiwania zagrożeń z Ochrona punktu końcowego w usłudze Microsoft Defender, wymagane są uprawnienia Do wyświetlania operacji zabezpieczeń danych.  

Podobnie, aby wyświetlić dane wyszukiwania zagrożeń z Ochrona usługi Office 365 w usłudze Microsoft Defender, użytkownicy będą wymagać jednej z następujących ról:  

- Wyświetlanie operacji zabezpieczeń danych
- Czytelnik zabezpieczeń
- Administrator zabezpieczeń
- Adresaci tylko do wyświetlania

## <a name="related-topics"></a>Tematy pokrewne
- [Role RBAC](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Zarządzanie dostępem do Microsoft 365 Defender](m365d-permissions.md)
- [Zarządzanie dostępem administratora do aplikacji Defender dla Chmury](/cloud-app-security/manage-admins)
