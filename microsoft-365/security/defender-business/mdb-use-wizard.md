---
title: Konfigurowanie programu Microsoft Defender dla firm (wersja Preview) za pomocą kreatora
description: Program Defender dla firm obejmuje proces konfiguracji i konfiguracji podobny do kreatora. Użyj kreatora, aby zaoszczędzić czas i nakład pracy.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/16/2022
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
ms.openlocfilehash: 26bf8e46ba79094f74fe542f932921d4f1c2a50d
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014817"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business-preview"></a>Konfigurowanie programu Microsoft Defender dla firm (wersja Preview) za pomocą kreatora

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Usługa Microsoft Defender dla firm (w wersji Preview) została zaprojektowana tak, aby zaoszczędzić czas i nakład pracy małych i średnich firm przy użyciu interfejsu kreatora na potrzeby konfiguracji początkowej. W tym artykule opisano kroki kreatora oraz opcje ręcznego konfigurowania i konfigurowania programu Defender dla firm.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Zrzut ekranu głównego kreatora do skonfigurowania usługi Defender dla firm.":::

## <a name="overview-of-the-wizard"></a>Omówienie kreatora

Kreator pomoże Ci szybko i wydajnie skonfigurować usługę Defender dla firm. Kreator przeprowadzi Cię przez następujące etapy:

1. **Przypisywanie uprawnień użytkownika**. W tym kroku należy udzielić zespołowi zabezpieczeń dostępu do portalu Microsoft 365 Defender sieci ([https://security.microsoft.com](https://security.microsoft.com)). Dostęp do portalu jest udzielany za pośrednictwem ról sugerujące pewne uprawnienia. [Dowiedz się więcej o rolach i uprawnieniach](mdb-roles-permissions.md).

   - Administrator globalny może wyświetlać i edytować wszystkie ustawienia w całej Microsoft 365 dzierżawie. 
   - Administrator zabezpieczeń może wyświetlać i edytować ustawienia zabezpieczeń. 
   - Czytnik zabezpieczeń może wyświetlać informacje tylko w raportach. 

2. **Konfigurowanie powiadomień e-mail**. W tym kroku określisz, kto powinien otrzymywać powiadomienia e-mail w przypadku wykrytej luki w zabezpieczeniach lub nowego alertu. Powiadomienia e-mail pomagają informować zespół zabezpieczeń, nawet jeśli nie ma go przy biurku. [Dowiedz się więcej o powiadomieniach e-mail](mdb-email-notifications.md). 

3. **Wdowaj i konfiguruj Windows urządzenia**. W tym kroku możesz szybko dodać urządzenia mobilne organizacji do Windows Defender dla firm. Urządzenia dołączające od razu pomagają chronić je od pierwszego dnia. 

   - Jeśli korzystasz już z usługi Microsoft Intune (część usługi Microsoft Endpoint Manager), a Twoja organizacja ma urządzenia zarejestrowane w programie Endpoint Manager, zostaniesz poproszony o określenie, czy chcesz korzystać z automatycznego dołączania dla niektórych lub wszystkich zarejestrowanych Windows urządzeniach. Automatyczne wniesienie konfiguruje połączenie między usługami Endpoint Manager i Defender dla Firm, a następnie bezproblemowo dołącza Windows z usługą Defender dla firm.

   - Jeśli jeszcze nie korzystasz z usługi Endpoint Manager lub masz urządzenia inne niż Windows zarejestrowane w programie Endpoint Manager, możesz ręcznie włączyć urządzenia do programu Defender dla firm (wersja Preview). 

   - Zobacz [Urządzenia w programie Microsoft Defender dla firm (wersja Preview).](mdb-onboard-devices.md)
   
4. **Skonfiguruj zasady zabezpieczeń**. Program Defender dla firm zawiera domyślne zasady zabezpieczeń, które mogą być stosowane do urządzeń organizacji. Te zasady domyślne używają zalecanych ustawień i zostały zaprojektowane tak, aby zapewnić silną ochronę Twoich urządzeń. Jeśli jednak chcesz, możesz również utworzyć własne zasady zabezpieczeń. Jeśli korzystasz już z usługi Endpoint Manager, możesz nadal używać jej do zarządzania zasadami zabezpieczeń. 

   - [Dowiedz się więcej o uproszczonej konfiguracji](mdb-simplified-configuration.md).
   - [Wybierz miejsce zarządzania zasadami zabezpieczeń i urządzeniami](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Co się stanie, jeśli nie użyję kreatora?

Jeśli nie chcesz używać kreatora lub jeśli go opuścisz przed zakończeniem procesu konfiguracji, nadal możesz samodzielnie ukończyć proces konfiguracji i konfiguracji. Aby [uzyskać instrukcje, zobacz Konfigurowanie i konfigurowanie programu Microsoft Defender dla firm (](mdb-setup-configuration.md) w wersji Preview).

## <a name="next-steps"></a>Następne kroki

- [Rozpoczynanie korzystania z portalu Microsoft 365 Defender-](mdb-get-started.md)

- [Używanie pulpitu nawigacyjnego zarządzania & zagrożeniami](mdb-view-tvm-dashboard.md)