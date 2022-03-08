---
title: Konfigurowanie programu Microsoft Defender dla firm przy użyciu kreatora
description: Program Defender dla firm obejmuje proces konfiguracji i konfiguracji podobny do kreatora. Użyj kreatora, aby zaoszczędzić czas i nakład pracy.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/02/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 98660e437463a79ce263edd29f2cd01725d19762
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322929"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business"></a>Konfigurowanie programu Microsoft Defender dla firm przy użyciu kreatora

> [!IMPORTANT]
> Od 1 marca 2022 r. usługa Microsoft Defender dla firm jest wprowadzana u klientów usługi Microsoft 365 Business Premium. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Usługa Microsoft Defender dla firm została zaprojektowana tak, aby zaoszczędzić czas i wysiłku małych i średnich firm przy użyciu interfejsu kreatora na potrzeby konfiguracji początkowej. W tym artykule opisano kroki kreatora oraz opcje ręcznego konfigurowania i konfigurowania programu Defender dla firm.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Zrzut ekranu głównego kreatora do skonfigurowania usługi Defender dla firm.":::

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

## <a name="overview-of-the-wizard"></a>Omówienie kreatora

Kreator pomoże Ci szybko i wydajnie skonfigurować usługę Defender dla firm. Kreator przeprowadzi Cię przez następujące etapy:

1. **Przypisywanie uprawnień użytkownika**. W tym kroku udzielisz zespołowi zabezpieczeń dostępu do portalu Usługi Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Dostęp do portalu jest udzielany za pośrednictwem ról sugerujące pewne uprawnienia. [Dowiedz się więcej o rolach i uprawnieniach](mdb-roles-permissions.md).

   - Administrator globalny może wyświetlać i edytować wszystkie ustawienia w dzierżawie platformy Microsoft 365. 
   - Administrator zabezpieczeń może wyświetlać i edytować ustawienia zabezpieczeń. 
   - Czytnik zabezpieczeń może wyświetlać informacje tylko w raportach. 

2. **Wdowy i konfigurowanie urządzeń z systemem Windows**. W tym kroku możesz szybko dodać urządzenia organizacji z systemem Windows do programu Defender dla firm. Urządzenia dołączające od razu pomagają chronić je od pierwszego dnia. Aby [uzyskać więcej szczegółowych informacji, zobacz Urządzenia w programie Microsoft Defender dla](mdb-onboard-devices.md) firm.

   - Jeśli korzystasz już z usługi Microsoft Intune (część do menedżera punktów końcowych firmy Microsoft) i Twoja organizacja ma urządzenia zarejestrowane w Menedżerze punktów końcowych, zostaniesz poproszony o określenie, czy chcesz korzystać z automatycznego dołączania dla niektórych, czy wszystkich zarejestrowanych urządzeń z systemem Windows. Automatyczne wniesienie konfiguruje połączenie między menedżerem punktów końcowych i usługą Defender dla firm, a następnie bezproblemowo dołącza urządzenia z systemem Windows do programu Defender dla firm.

   - Jeśli jeszcze nie korzystasz z menedżera punktów końcowych lub masz urządzenia innego niż Windows zarejestrowane w Menedżerze punktów końcowych, możesz ręcznie dodać urządzenia do usługi Defender dla firm. 
   
3. **Skonfiguruj zasady zabezpieczeń**. Program Defender dla firm zawiera domyślne zasady zabezpieczeń dla ochrony następnej generacji i ochrony zapory, które można stosować do urządzeń organizacji. Te zasady domyślne używają zalecanych ustawień i zostały zaprojektowane tak, aby zapewnić silną ochronę Twoich urządzeń. 

   Jeśli chcesz, możesz również utworzyć własne zasady zabezpieczeń. Jeśli już korzystasz z menedżera punktów końcowych, możesz nadal używać go do zarządzania zasadami zabezpieczeń. 

   Aby dowiedzieć się więcej, [zobacz Wyświetlanie i edytowanie zasad i ustawień zabezpieczeń](mdb-configure-security-settings.md).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Co się stanie, jeśli nie użyję kreatora?

Jeśli nie chcesz korzystać z kreatora lub jeśli kreator zostanie zamknięty przed ukończeniem procesu konfiguracji, nadal możesz samodzielnie ukończyć proces konfiguracji i konfiguracji. 

Zobacz [Konfigurowanie i konfigurowanie programu Microsoft Defender dla firm](mdb-setup-configuration.md) , aby wykonać następujące czynności:

1. [Przypisz role i uprawnienia,](mdb-roles-permissions.md) aby Twój zespół zabezpieczeń mieć dostęp do portalu Usługi Microsoft 365 Defender i korzystać z niego ([https://security.microsoft.com](https://security.microsoft.com)).

2. [Skonfiguruj powiadomienia e-mail dla zespołu zabezpieczeń](mdb-email-notifications.md) , aby były na bieżąco dotyczące nowych alertów i luk w zabezpieczeniach.

3. [Urządzenia mobilne,](mdb-onboard-devices.md) dzięki czemu są chronione przez usługę Defender dla firm.

4. [Zarządzaj zasadami zabezpieczeń](mdb-configure-security-settings.md), które obejmują ochronę następnej generacji, ochronę zapory i filtrowanie zawartości sieci Web.

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie powiadomień e-mail dla zespołu zabezpieczeń](mdb-email-notifications.md)

- [Rozpoczynanie korzystania z portalu usługi Microsoft 365 Defender](mdb-get-started.md)

- [Używanie pulpitu nawigacyjnego zarządzania & zagrożeniami](mdb-view-tvm-dashboard.md)