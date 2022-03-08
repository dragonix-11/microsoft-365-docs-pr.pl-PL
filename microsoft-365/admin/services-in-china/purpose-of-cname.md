---
title: Jaki jest cel rekordu CNAME Office 365 MSOID?
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NOINDEX
description: Dowiedz się więcej o rekordzie CNAME "MSOID" w programie Office 365, który kieruje Cię do najlepszego serwera procesów uwierzytelniania, dzięki czemu szybciej otrzymasz odpowiedź.
monikerRange: o365-21vianet
ms.openlocfilehash: 1b053ac0df7cd770b5627b688e90641688f94141
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325127"
---
# <a name="whats-the-purpose-of-the-office-365-cname-record-for-msoid"></a>Jaki jest cel rekordu CNAME Office 365 MSOID?

 **[Zajrzyj do często zadawanych pytań dotyczących domen](../setup/domains-faq.yml)**, jeśli nie możesz znaleźć szukanych informacji. 
> [!NOTE]
> Poniższe informacje dotyczą tylko **Office 365 obsługiwanej przez firmę 21Vianet.
  
Być może zastanawiasz się, dlaczego musisz dodać rekord CNAME "MSOID" w programie Office 365. Jest to rekord, który należy dodać dla wszystkich domen niestandardowych, niezależnie od tego, której subskrypcji używasz. Dlaczego jest potrzebny? Jest to nieco techniczne, ale w zasadzie to jest tak, że zostaniesz przekierowywowany do najlepszego serwera dla określonych procesów uwierzytelniania, dzięki czemu szybciej na to zatądnisz.
  
Szczegóły techniczne: Po uruchomieniu aplikacji klienckiej, która działa z usługą Office 365, takiej jak narzędzie do synchronizacji usługi Skype dla firm Online, Outlook, Windows PowerShell lub Microsoft Azure Active Directory, poświadczenia muszą zostać uwierzytelnione. Office 365 korzysta z rekordu CNAME, aby wskazać poprawny punkt końcowy uwierzytelniania dla Twojej lokalizacji, co zapewnia szybki czas odpowiedzi uwierzytelniania.
  
Jeśli brakuje tego rekordu CNAME dla Twojej domeny, te aplikacje będą używać domyślnego punktu końcowego uwierzytelniania w Stanach Zjednoczonych, co oznacza, że uwierzytelnianie może być wolniejsze. Jeśli ten rekord CNAME nie jest prawidłowo skonfigurowany — na przykład w polu Points **to address** (Wskazuje adres) — te aplikacje nie będą mogły się uwierzytelnić.
  
 **Jeśli Office 365 rekordami DNS** Twojej domeny, Office 365 skonfigurować ten rekord CNAME. 
  
 **Jeśli zarządzasz rekordami DNS** dla swojej domeny u swojego hosta DNS, ten rekord tworzysz samodzielnie, korzystając z instrukcji [dotyczących twojego hosta DNS](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
  
Jeśli planujesz wdrożenie usługi Office 365 i chcesz dowiedzieć się więcej o wszystkich rekordach DNS, które mogą być potrzebne do dodania lub zaktualizowania, przeczytaj o nich w te sposób: Reference[: External Domain Name System](../../enterprise/external-domain-name-system-records.md) records for Office 365.
