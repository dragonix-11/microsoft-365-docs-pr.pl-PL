---
title: Limity w przypadku zbierania elektronicznych materiałów dowodowych (standardowa)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: W tym artykule opisano limity w przypadku zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) w Microsoft 365.
ms.openlocfilehash: 6cc058bee09563d6a9914b9602b2fc6a3bfdf7f6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093048"
---
# <a name="limits-in-ediscovery-standard"></a>Limity w zakresie zbierania elektronicznych materiałów dowodowych (Standardowa)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W poniższej tabeli wymieniono limity dla przypadków zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) i blokad skojarzonych ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa). Aby uzyskać więcej informacji o usłudze Microsoft Purview eDiscovery (Standard), zobacz [Omówienie zbierania elektronicznych materiałów dowodowych (Standard)](./get-started-core-ediscovery.md).
    
  | Opis limitu | Limit |
  |:-----|:-----|
  |Maksymalna liczba przypadków dla organizacji.  <br/> |Brak limitu  <br/> |
  |Maksymalna liczba spraw w organizacji.  <br/> |10,000  <br/> |
  |Maksymalna liczba skrzynek pocztowych w jednym przypadku blokady. Ten limit obejmuje łączną sumę skrzynek pocztowych użytkowników oraz skrzynki pocztowe skojarzone z grupami Grupy Microsoft 365, Microsoft Teams i Yammer.  <br/> |1,000  <br/> |
  |Maksymalna liczba witryn w jednym przypadku blokady. Ten limit obejmuje łączną sumę witryn OneDrive dla Firm, witryn SharePoint oraz witryn skojarzonych z grupami Grupy Microsoft 365, Microsoft Teams i Yammer.  <br/> |100  <br/> |
  |Maksymalna liczba przypadków wyświetlanych na stronie głównej zbierania elektronicznych materiałów dowodowych (standardowa) oraz maksymalna liczba elementów wyświetlanych na kartach Blokady, Wyszukiwania i Eksport w danym przypadku. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup>1</sup> Aby wyświetlić listę ponad 1000 spraw, blokad, wyszukiwań lub eksportów, możesz użyć odpowiednich poleceń cmdlet programu PowerShell Office 365 Security & Compliance:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Aby uzyskać więcej informacji na temat limitów związanych z wyszukiwaniami i eksportami skojarzonymi ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa), zobacz [Limity dotyczące wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (Standard)](limits-for-content-search.md).