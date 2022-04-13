---
title: Limity w podstawowym przypadku zbierania elektronicznych materiałów dowodowych
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
description: W tym artykule opisano limity w podstawowym przypadku zbierania elektronicznych materiałów dowodowych w Microsoft 365.
ms.openlocfilehash: 2d920fbe5973d07b7da656d6247038ab785bbe5c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822655"
---
# <a name="limits-in-core-ediscovery"></a>Limity w podstawowym zbierania elektronicznych materiałów dowodowych

W poniższej tabeli wymieniono limity dotyczące podstawowych przypadków zbierania elektronicznych materiałów dowodowych i blokad skojarzonych z podstawowym przypadkiem zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji na temat podstawowych zbierania elektronicznych materiałów dowodowych, zobacz [Omówienie podstawowego zbierania elektronicznych materiałów dowodowych](./get-started-core-ediscovery.md).
    
  | Opis limitu | Limit |
  |:-----|:-----|
  |Maksymalna liczba przypadków dla organizacji.  <br/> |Brak limitu  <br/> |
  |Maksymalna liczba spraw w organizacji.  <br/> |10,000  <br/> |
  |Maksymalna liczba skrzynek pocztowych w jednym przypadku blokady. Ten limit obejmuje łączną sumę skrzynek pocztowych użytkowników oraz skrzynki pocztowe skojarzone z grupami Grupy Microsoft 365, Microsoft Teams i Yammer.  <br/> |1,000  <br/> |
  |Maksymalna liczba witryn w jednym przypadku blokady. Ten limit obejmuje łączną sumę witryn OneDrive dla Firm, witryn SharePoint oraz witryn skojarzonych z grupami Grupy Microsoft 365, Microsoft Teams i Yammer.  <br/> |100  <br/> |
  |Maksymalna liczba przypadków wyświetlanych na podstawowej stronie głównej zbierania elektronicznych materiałów dowodowych oraz maksymalna liczba elementów wyświetlanych na kartach Blokady, Wyszukiwania i Eksport w ramach sprawy. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup>1</sup> Aby wyświetlić listę ponad 1000 spraw, blokad, wyszukiwań lub eksportów, możesz użyć odpowiednich poleceń cmdlet programu PowerShell Office 365 Security & Compliance:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Aby uzyskać więcej informacji na temat limitów związanych z wyszukiwaniami i eksportami skojarzonymi z podstawowym przypadkiem zbierania elektronicznych materiałów dowodowych, zobacz [Limity dotyczące wyszukiwania zawartości i podstawowego zbierania elektronicznych materiałów dowodowych](limits-for-content-search.md).