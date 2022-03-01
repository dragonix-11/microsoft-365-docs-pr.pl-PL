---
title: Ograniczenia dotyczące podstawowej sprawy zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: W tym artykule opisano ograniczenia dotyczące podstawowej sprawy zbierania elektronicznych materiałów dowodowych w Microsoft 365.
ms.openlocfilehash: 28db179aea27bfff2520199d89b93c8260b7f089
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033005"
---
# <a name="limits-in-core-ediscovery"></a>Ograniczenia podstawowe zbierania elektronicznych materiałów dowodowych

W poniższej tabeli wymieniono limity podstawowych spraw zbierania elektronicznych materiałów dowodowych oraz blokady skojarzone z podstawową sprawą zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji na temat core eDiscovery, zobacz [Omówienie podstawowych zbierania elektronicznych materiałów dowodowych](./get-started-core-ediscovery.md).
    
  | Opis limitu | Limit |
  |:-----|:-----|
  |Maksymalna liczba spraw w organizacji.  <br/> |Bez limitu  <br/> |
  |Maksymalna liczba przypadków przechowań sprawy w organizacji.  <br/> |10,000  <br/> |
  |Maksymalna liczba skrzynek pocztowych z pojedynczymi skrzynkami pocztowymi. Ten limit obejmuje łączną liczbę skrzynek pocztowych użytkowników oraz skrzynek pocztowych skojarzonych Microsoft 365, grup Microsoft Teams i Yammer grupy.  <br/> |1,000  <br/> |
  |Maksymalna liczba witryn w pojedynczym przypadku. Ten limit obejmuje łączną liczbę OneDrive dla Firm, witryn SharePoint oraz witryn skojarzonych z grupami Microsoft 365, witrynami Microsoft Teams i Yammer grupy.  <br/> |100  <br/> |
  |Maksymalna liczba spraw wyświetlanych na głównej stronie głównej zbierania elektronicznych materiałów dowodowych oraz maksymalna liczba elementów wyświetlanych na kartach Zarchiwnia, Wyszukiwania i Eksportowanie w ramach sprawy. <sup>1</sup> |1,000|
  |||

   > [!NOTE]
   > <sup>1</sup> Aby wyświetlić listę ponad 1000 spraw, blokady, wyszukiwania lub eksporty, można użyć odpowiednich poleceń cmdlet programu Office 365 Security & Compliance programu PowerShell:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Aby uzyskać więcej informacji na temat limitów związanych z wyszukiwaniami i eksportami skojarzonymi z podstawową sprawą zbierania elektronicznych materiałów dowodowych, zobacz Limity dotyczące wyszukiwania zawartości i podstawowego [zbierania elektronicznych materiałów dowodowych](limits-for-content-search.md).