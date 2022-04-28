---
title: Monitorowanie łączności platformy Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: W tym artykule dowiesz się więcej o narzędziach i technikach, których można użyć do monitorowania i utrzymywania łączności Microsoft 365.
ms.openlocfilehash: 0e7c18a10dc851596af6a652fb80c9c72852ee0d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093312"
---
# <a name="monitor-microsoft-365-connectivity"></a>Monitorowanie łączności platformy Microsoft 365

Po wdrożeniu Microsoft 365 można zachować łączność Microsoft 365 przy użyciu niektórych poniższych narzędzi i technik. Warto zapoznać się z oficjalnymi wytycznymi dotyczącymi [kondycji i ciągłości usługi,](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) a także [naszymi najlepszymi rozwiązaniami dotyczącymi używania Microsoft 365 w powolnej sieci](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Warto również pobrać [aplikację administratora Microsoft 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) i dodać zakładkę do naszej [Microsoft 365 dla firm — Pomoc dla administratorów](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Monitorowanie łączności Microsoft 365

|Typ monitorowania |Opis |
|:-----|:-----|
|**Otrzymywanie powiadomień o nowych punktach końcowych Microsoft 365** <br/> |Jeśli [zarządzasz punktami końcowymi Microsoft 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), chcesz otrzymywać powiadomienia podczas publikowania nowych punktów końcowych, możesz subskrybować nasz kanał informacyjny RSS przy użyciu ulubionego czytnika RSS. Oto jak [subskrybować za pośrednictwem Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) lub możesz [wysłać do Ciebie wiadomość e-mail z aktualizacjami kanału informacyjnego RSS](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Monitorowanie Microsoft 365 przy użyciu System Center** <br/> |Jeśli używasz usługi Microsoft System Center, możesz pobrać [pakiet administracyjny programu Microsoft System Center Operations Manager, aby Microsoft 365](https://www.microsoft.com/download/details.aspx?id=103379) rozpocząć monitorowanie Microsoft 365 dzisiaj. Aby uzyskać bardziej szczegółowe wskazówki, zobacz przewodnik po operacjach pakietu administracyjnego. <br/> |
|**Monitorowanie kondycji usługi Azure ExpressRoute** <br/> |Jeśli nawiązujesz połączenie z usługą Microsoft 365 przy użyciu usługi Azure ExpressRoute dla Microsoft 365, upewnij się, że używasz zarówno pulpitu nawigacyjnego usługi Microsoft 365 Service Health, jak i [czasu rozwiązywania problemów z usługą Azure Redukowanie czasu rozwiązywania problemów z usługą Azure Resource Health](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**Korzystanie z usługi Azure AD Połączenie Health z usługami AD FS** <br/> |Jeśli używasz usług AD FS dla pojedynczego Sign-On z Microsoft 365, warto zacząć [używać usługi Azure AD Połączenie Health do monitorowania infrastruktury usług AD FS](/azure/active-directory/hybrid/how-to-connect-health-adfs).  <br/> |
|**Programowe monitorowanie Microsoft 365** <br/> |Zapoznaj się z naszymi wskazówkami dotyczącymi [interfejsu API zarządzania Microsoft 365](/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Konfigurowanie usług i aplikacji Microsoft 365 Enterprise](configure-services-and-applications.md)
  
[Przygotowanie organizacji do Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Planowanie sieci i dostrajanie wydajności dla Microsoft 365](network-planning-and-performance.md)
  
[Microsoft 365 integracji ze środowiskami lokalnymi](microsoft-365-integration.md)
  
[Zarządzanie punktami końcowymi Microsoft 365](managing-office-365-endpoints.md)
