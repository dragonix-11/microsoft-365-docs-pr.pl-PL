---
title: Monitorowanie Microsoft 365 sieci
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: W tym artykule dowiesz się więcej o narzędziach i technikach, za pomocą których można monitorować i konserwować Microsoft 365 sieciową.
ms.openlocfilehash: 783278ad69fbe47afd6ea85fdb70c8bb0057005c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985479"
---
# <a name="monitor-microsoft-365-connectivity"></a>Monitorowanie Microsoft 365 sieci

Po wdrożeniu programu Microsoft 365 możesz zachować łączność Microsoft 365, używając niektórych narzędzi i technik dostępnych poniżej. Należy zrozumieć oficjalne wytyczne dotyczące kondycji i [](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) ciągłości usług, a także nasze najlepsze rozwiązania dotyczące korzystania Microsoft 365 [w wolno powolnej sieci](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). Warto również chcieć pobrać aplikację Microsoft 365 [i](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) dodać zakładkę do Microsoft 365 dla firm [— Pomoc dla administratorów](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>Monitorowanie Microsoft 365 sieci

|Typ monitorowania |Opis |
|:-----|:-----|
|**Uzyskiwanie powiadomień o nowych Microsoft 365 końcowych** <br/> |Jeśli zarządzasz [punktami końcowymi](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) Microsoft 365, zalecamy otrzymywanie powiadomień, gdy publikujemy nowe punkty końcowe, możesz zasubskrybować nasz kanał informacyjny RSS przy użyciu ulubionego czytnika RSS. Poniżej opisano, jak zasubskrybować kanał [Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) lub wysłać do Ciebie pocztą e-mail aktualizacje kanału [informacyjnego RSS](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**Monitorowanie System Center za pomocą Microsoft 365** <br/> |Jeśli korzystasz z programu Microsoft System Center, możesz pobrać pakiet administracyjny dodatku [Microsoft System Center Operations Manager](https://www.microsoft.com/download/details.aspx?id=103379) dla programu Microsoft 365 rozpocząć monitorowanie Microsoft 365 dzisiaj. Aby uzyskać bardziej szczegółowe wskazówki, zobacz podręcznik operacyjny pakietu zarządzania. <br/> |
|**Monitorowanie kondycji usługi Azure ExpressRoute** <br/> |Jeśli łączysz się z usługą Microsoft 365 za pomocą usługi Azure ExpressRoute dla usługi Microsoft 365, należy upewnić się, że używasz zarówno pulpitu nawigacyjnego kondycji usługi Microsoft 365, jak i platformy Azure (Skracanie czasu rozwiązywania problemów z kondycją zasobów platformy [Azure](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/)) <br/> |
|**Korzystanie z usługi Azure AD Połączenie Health z usługami AD FS** <br/> |Jeśli używasz usług AD FS do pracy Sign-On z usługą Microsoft 365, zacznij używać usługi [Azure AD Połączenie Health](/azure/active-directory/hybrid/how-to-connect-health-adfs) do monitorowania infrastruktury usług AD FS.  <br/> |
|**Programowo monitoruj Microsoft 365** <br/> |Skorzystaj z naszych wskazówek dotyczących [interfejsu API Microsoft 365 zarządzania](/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>Tematy pokrewne

[Konfigurowanie Microsoft 365 Enterprise i aplikacji](configure-services-and-applications.md)
  
[Przygotuj swoją organizację do Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[Planowanie sieci i dostosowywanie wydajności dla Microsoft 365](network-planning-and-performance.md)
  
[Microsoft 365 integracji ze środowiskami lokalnymi](microsoft-365-integration.md)
  
[Zarządzanie Microsoft 365 punktami końcowymi](managing-office-365-endpoints.md)
