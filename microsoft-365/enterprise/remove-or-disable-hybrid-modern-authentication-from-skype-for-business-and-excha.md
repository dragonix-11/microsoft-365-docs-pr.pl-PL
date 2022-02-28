---
title: Usuwanie lub wyłączanie nowoczesnego uwierzytelniania hybrydowego Skype dla firm i Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: W tym artykule wyjaśniono, jak usunąć lub wyłączyć nowoczesne uwierzytelnianie hybrydowe na Skype dla firm i Exchange.
ms.openlocfilehash: efc84ead5ea8219e77391f2a8ebe51e5fa23da8c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988010"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Usuwanie lub wyłączanie nowoczesnego uwierzytelniania hybrydowego Skype dla firm i Exchange

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli włączono nowoczesne uwierzytelnianie hybrydowe (HMA, Hybrid Modern Authentication) tylko w celu znalezienia tego, że nie jest ono nieodpowiednie dla Twojego bieżącego środowiska, możesz wyłączyć usługę HMA. W tym artykule wyjaśniono, jak to zrobić.
  
## <a name="who-is-this-article-for"></a>KtoTo temat tego artykułu?

Jeśli włączysz nowoczesne uwierzytelnianie w trybie Skype dla firm Online lub lokalnym i/lub lokalnym i Exchange Online/lub lokalnym i okazało się, że musisz wyłączyć funkcję HMA, te kroki są dla Ciebie.

> [!IMPORTANT]
> Zobacz [artykuł Skype dla firm](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) topologii obsługiwanych za pomocą nowoczesnego uwierzytelniania, jeśli używasz usługi Skype dla firm Online lub lokalnej, masz topologię mieszaną, a przed rozpoczęciem musisz przyjrzeć się obsługiwanym topologiom.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Jak wyłączyć nowoczesne uwierzytelnianie hybrydowe (Exchange)

1. **Exchange lokalne**: Otwórz powłokę Exchange zarządzania danymi i uruchom następujące polecenia: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Połączenie do Exchange Online przy użyciu](/powershell/exchange/connect-to-exchange-online-powershell) zdalnej pracy z programem PowerShell. Uruchom następujące polecenie, aby przekształcić flagę  *OAuth2ClientProfileEnabled*  na "false":

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Jak wyłączyć nowoczesne uwierzytelnianie hybrydowe (Skype dla firm)

1. **Skype dla firm lokalne**: Uruchom następujące polecenia w Skype dla firm zarządzania:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype dla firm Online**: Połączenie [do Skype dla firm Online za](manage-skype-for-business-online-with-microsoft-365-powershell.md) pomocą zdalnej pracy w programie PowerShell. Uruchom następujące polecenie, aby wyłączyć nowoczesne uwierzytelnianie:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Wróć do przeglądu nowoczesnego uwierzytelniania](hybrid-modern-auth-overview.md) . 
