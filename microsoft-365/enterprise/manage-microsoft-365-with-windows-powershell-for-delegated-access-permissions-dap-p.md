---
title: Zarządzanie Microsoft 365 przy użyciu Windows PowerShell dla partnerów dap
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: landing-page
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
description: Jak partnerzy syndykacji i Dostawca rozwiązań w chmurze (CSP) mogą używać Windows PowerShell do zarządzania Microsoft 365 dzierżawami klientów.
ms.openlocfilehash: 9eb1b37f89f7850fe0680bbc43d39abfb68e9954
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091594"
---
# <a name="how-to-manage-microsoft-365-with-windows-powershell-for-delegated-access-permissions-partners"></a>Jak zarządzać Microsoft 365 przy użyciu Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Partnerami z uprawnieniami dostępu delegowanego (DAP) są partnerzy syndykacji i dostawcy rozwiązań w chmurze (CSP). Wiele z nich to dostawcy sieci lub telekomunikacyjni. Łączą Microsoft 365 subskrypcje w swoje oferty usług. Gdy sprzedają subskrypcję Microsoft 365, automatycznie otrzymują uprawnienia Administrowanie w imieniu (AOBO) do dzierżaw klienta, aby mógł administrować tymi dzierżawami i raportować je. Te zadania są trudne do wykonania w Centrum administracyjne platformy Microsoft 365. Znacznie łatwiej jest używać programu PowerShell do Microsoft 365 wykonywania zadań administracyjnych, takich jak:
- Wyświetl listę wszystkich **identyfikatorów dzierżawy** klienta i ich domen 
- Identyfikowanie wszystkich użytkowników dzierżawy klienta i przypisanych do nich licencji
> [!NOTE]
> Niektóre zadania administracyjne można wykonywać tylko w programie PowerShell.

W poniższych artykułach pokazano, jak partnerzy syndykacji i dostawcy CSP używają programu PowerShell do administrowania dzierżawami klientów:
  
- [Zarządzanie dzierżawami Microsoft 365 przy użyciu Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego (DAP)](manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissio.md)
    
- [Dodawanie domeny do dzierżawy klienta za pomocą Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego (DAP)](add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-pe.md)
    
- [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
- [Pobieranie danych raportowania dzierżawy klienta za pomocą Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego (DAP)](retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-ac.md)
