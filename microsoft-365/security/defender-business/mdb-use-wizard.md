---
title: Konfigurowanie programu Microsoft Defender dla firm przy użyciu kreatora
description: Program Defender dla firm obejmuje proces konfiguracji i konfiguracji podobny do kreatora. Użyj kreatora, aby zaoszczędzić czas i nakład pracy.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
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
ms.openlocfilehash: b55af496881489279a7a6f96ed386ab2a26c2fa5
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512604"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business"></a>Konfigurowanie programu Microsoft Defender dla firm przy użyciu kreatora

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, [](https://aka.ms/mdb-preview) którzy zarejestrują się tutaj, aby poprosić o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
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

1. **Przypisywanie uprawnień użytkownika**. W tym kroku należy udzielić zespołowi zabezpieczeń dostępu do portalu Microsoft 365 Defender sieci ([https://security.microsoft.com](https://security.microsoft.com)). Dostęp do portalu jest udzielany za pośrednictwem ról sugerujące pewne uprawnienia. [Dowiedz się więcej o rolach i uprawnieniach](mdb-roles-permissions.md).

   - Administrator globalny może wyświetlać i edytować wszystkie ustawienia w całej Microsoft 365 dzierżawie. 
   - Administrator zabezpieczeń może wyświetlać i edytować ustawienia zabezpieczeń. 
   - Czytnik zabezpieczeń może wyświetlać informacje tylko w raportach. 

2. **Wdowaj i konfiguruj Windows urządzenia**. W tym kroku możesz szybko dodać firmowe urządzenia mobilne do Windows Defender dla firm. Urządzenia dołączające od razu pomagają chronić je od pierwszego dnia. Aby [uzyskać więcej szczegółowych informacji, zobacz Urządzenia w programie Microsoft Defender dla](mdb-onboard-devices.md) firm.

   - Jeśli korzystasz już z usługi Microsoft Intune (część usługi Microsoft Endpoint Manager), a Twoja firma ma urządzenia zarejestrowane w usłudze Endpoint Manager, zostaniesz poproszony(-a) o zastosowanie automatycznego dołączania dla niektórych lub wszystkich zarejestrowanych Windows urządzeniach.[](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) Automatyczne wniesienie konfiguruje połączenie między usługami Endpoint Manager i Defender dla Firm, a następnie bezproblemowo dołącza Windows z usługą Defender dla firm.

   - Jeśli jeszcze nie korzystasz z usługi Endpoint Manager lub masz urządzenia inne niż Windows zarejestrowane w programie Endpoint Manager, możesz ręcznie włączyć je do usługi [Defender dla firm](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
3. **Skonfiguruj zasady zabezpieczeń**. Program Defender dla firm zawiera domyślne zasady zabezpieczeń dla ochrony następnej generacji i ochrony zapory, które mogą być stosowane do urządzeń firmy. Te zasady domyślne używają zalecanych ustawień i zostały zaprojektowane tak, aby zapewnić silną ochronę Twoich urządzeń. 

   Jeśli chcesz, możesz również utworzyć własne zasady zabezpieczeń. Jeśli korzystasz już z usługi Endpoint Manager, możesz nadal używać jej do zarządzania zasadami zabezpieczeń. 

   Aby dowiedzieć się więcej, [zobacz Wyświetlanie i edytowanie zasad i ustawień zabezpieczeń](mdb-configure-security-settings.md).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Co się stanie, jeśli nie użyję kreatora?

Jeśli nie chcesz korzystać z kreatora lub jeśli kreator zostanie zamknięty przed ukończeniem procesu konfiguracji, nadal możesz samodzielnie ukończyć proces konfiguracji i konfiguracji. 

Zobacz [Konfigurowanie i konfigurowanie programu Microsoft Defender dla firm](mdb-setup-configuration.md) , aby wykonać następujące czynności:

1. [Przypisz role i uprawnienia,](mdb-roles-permissions.md) aby Twój zespół zabezpieczeńł dostęp do portalu Microsoft 365 Defender i korzystać z niego ([https://security.microsoft.com](https://security.microsoft.com)).

2. [Skonfiguruj powiadomienia e-mail dla zespołu zabezpieczeń](mdb-email-notifications.md) , aby były na bieżąco dotyczące nowych alertów i luk w zabezpieczeniach.

3. [Urządzenia mobilne,](mdb-onboard-devices.md) dzięki czemu są chronione przez usługę Defender dla firm.

4. [Zarządzaj zasadami zabezpieczeń](mdb-configure-security-settings.md), które obejmują ochronę następnej generacji, ochronę zapory i filtrowanie zawartości sieci Web.

## <a name="next-steps"></a>Następne kroki

- [Konfigurowanie powiadomień e-mail dla zespołu zabezpieczeń](mdb-email-notifications.md)

- [Rozpoczynanie korzystania z portalu Microsoft 365 Defender-](mdb-get-started.md)

- [Używanie pulpitu nawigacyjnego zarządzania & zagrożeniami](mdb-view-tvm-dashboard.md)