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
description: W tym artykule opisano limity w przypadku zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) na platformie Microsoft 365.
ms.openlocfilehash: fe564bfb26bf586ba6ff6567dae057ecb1065296
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634142"
---
# <a name="limits-in-ediscovery-standard"></a>Limity w zakresie zbierania elektronicznych materiałów dowodowych (Standardowa)

W poniższej tabeli wymieniono limity dla przypadków zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) i blokad skojarzonych ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa). Aby uzyskać więcej informacji na temat Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview (Standard), zobacz [Omówienie zbierania elektronicznych materiałów dowodowych (Standard)](./get-started-core-ediscovery.md).
    
  | Opis limitu | Limit |
  |:-----|:-----|
  |Maksymalna liczba przypadków dla organizacji.  <br/> |Brak limitu  <br/> |
  |Maksymalna liczba spraw w organizacji.  <br/> |10,000  <br/> |
  |Maksymalna liczba skrzynek pocztowych w jednym przypadku blokady. Ten limit obejmuje łączną liczbę skrzynek pocztowych użytkowników oraz skrzynki pocztowe skojarzone z grupami Grupy Microsoft 365, Microsoft Teams i Yammer.  <br/> |1,000  <br/> |
  |Maksymalna liczba witryn w jednym przypadku blokady. Ten limit obejmuje łączną sumę witryn OneDrive dla Firm, witryn programu SharePoint oraz witryn skojarzonych z grupami Grupy Microsoft 365, Microsoft Teams i Yammer.  <br/> |100  <br/> |
  |Maksymalna liczba przypadków wyświetlanych na stronie głównej zbierania elektronicznych materiałów dowodowych (standardowa) oraz maksymalna liczba elementów wyświetlanych na kartach Blokady, Wyszukiwania i Eksport w danym przypadku. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup>1</sup> Aby wyświetlić listę ponad 1000 spraw, blokad, wyszukiwań lub eksportów, możesz użyć odpowiednich poleceń cmdlet programu PowerShell Office 365 Security & Compliance:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Aby uzyskać więcej informacji na temat limitów związanych z wyszukiwaniami i eksportami skojarzonymi ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa), zobacz [Limity dotyczące wyszukiwania zawartości i zbierania elektronicznych materiałów dowodowych (Standard)](limits-for-content-search.md).