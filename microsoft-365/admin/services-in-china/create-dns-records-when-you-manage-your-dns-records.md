---
title: Tworzenie rekordów DNS dla Office 365 w przypadku zarządzania rekordami DNS
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEA150
ms.assetid: 0669bf14-414d-4f51-8231-6b710ce7980b
ROBOTS: NOINDEX
description: 'Dowiedz się, jak tworzyć rekordy DNS dla Office 365 obsługiwanych przez firmę 21Vianet w przypadku Twojego zarządzania rekordami DNS. '
monikerRange: o365-21vianet
ms.openlocfilehash: 0b84926dbedf90752c994e76695c2d18d92fb9c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984950"
---
# <a name="create-dns-records-for-office-365-when-you-manage-your-dns-records"></a>Tworzenie rekordów DNS dla Office 365 w przypadku zarządzania rekordami DNS

Aby uzyskać szczegółowe instrukcje dotyczące tworzenia rekordów DNS dla usługi Office 365 obsługiwanej przez firmę 21Vianet, w tym rekordu MX wymaganego do routingu poczty, zobacz Tworzenie rekordów [DNS](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) dla usługi Office 365. 
  
  
Więcej opcji i kilka rzeczy, o których należy pamiętać:
      
-  Jeśli nie znasz dostawcy hostingu DNS lub rejestratora domen dla swojej domeny, zobacz [Znajdowanie rejestratora domen lub dostawcy hostingu DNS](../get-help-with-domains/find-your-domain-registrar.md). Aby uzyskać opisy rekordów DNS, zobacz [Podstawowe informacje o systemie DNS](../get-help-with-domains/dns-basics.md).
    
-  Niektórzy dostawcy hostingu DNS nie umożliwiają tworzenia wszystkich wymaganych typów rekordów, co powoduje ograniczenia usługi, gdy twój [dostawca hostingu nie obsługuje rekordów SRV, CNAME, TXT lub przekierowywania](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77). Jeśli Twój dostawca nie obsługuje rekordów SRV, TXT lub CNAME, zalecamy przeniesienie domeny do dostawcy obsługującego [](../get-help-with-domains/buy-a-domain-name.md) wszystkie [wymagane typy rekordów](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77). 
    
- Aby sprawdzić, które rekordy DNS są wymagane, i znaleźć wartości do użycia dla poszczególnych rekordów, w tym rekord MX dla poczty [e-mail](../get-help-with-domains/information-for-dns-records.md), zobacz Zbieranie informacji potrzebnych do utworzenia Office 365 DNS. Aby uzyskać opisy rekordów DNS, zobacz [Podstawowe informacje o systemie DNS](../get-help-with-domains/dns-basics.md).
