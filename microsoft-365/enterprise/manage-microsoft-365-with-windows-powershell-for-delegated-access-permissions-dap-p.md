---
title: Zarządzanie Microsoft 365 pomocą Windows PowerShell daP
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: be497751-596f-431d-b256-0a89d36a47ce
description: W jaki sposób partnerzy usług Syndication i Dostawca rozwiązań w chmurze (CSP) mogą Windows PowerShell zarządzać Microsoft 365 dzierżawami klientów.
ms.openlocfilehash: 2678489d1e281a60d230c65e29b358dff5f1a8ad
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959565"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>Jak zarządzać Microsoft 365 z Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Partnerzy w programie DaP (Delegated Access Permission) to partnerzy usług Syndication i Dostawcy rozwiązań w chmurze (CSP). Wielu z nich to dostawcy sieci lub telekomunikacyjni. Oferują pakiety Microsoft 365 do swoich ofert usług. Gdy sprzeda on subskrypcję usługi Microsoft 365, automatycznie udziela mu uprawnień administrowania w imieniu klienta (AOBO) w celu administrowania tymi dziesiątami i zgłaszania na ich temat. Te zadania są trudne do wykonania w centrum administracyjne platformy Microsoft 365. Znacznie łatwiej jest używać programu PowerShell do Microsoft 365 zadań administracyjnych, takich jak:
- Lista wszystkich **dzierżawców** i ich domen 
- Zidentyfikuj wszystkich użytkowników w przypadku umowy klienta i przypisanych im licencji
> [!NOTE]
> Niektóre zadania administracyjne można wykonywać tylko w programie PowerShell.

W poniższych artykułach podano, jak partnerzy programu Syndication i programu CSP zarządzają swoimi dziesiątami klientów za pomocą programu PowerShell:
  
- [Zarządzanie Microsoft 365 dostępu za pomocą Windows PowerShell dla partnerów daP (Delegated Access Permissions)](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [Dodawanie domeny do licencji klienta z usługą Windows PowerShell dla partnerów dap (Delegated Access Permission)](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [Połączenie do Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
- [Pobieranie danych raportowania dzierżawy klienta Windows PowerShell partnerom dap (Delegated Access Permissions)](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
