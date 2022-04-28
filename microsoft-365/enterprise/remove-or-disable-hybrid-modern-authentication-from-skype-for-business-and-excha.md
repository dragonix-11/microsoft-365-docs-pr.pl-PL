---
title: Usuwanie lub wyłączanie nowoczesnego uwierzytelniania hybrydowego z Skype dla firm i Exchange
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: W tym artykule wyjaśniono, jak usunąć lub wyłączyć nowoczesne uwierzytelnianie hybrydowe z Skype dla firm i Exchange.
ms.openlocfilehash: 27768d5f2ee1a2d223d0979a80d3fff003ed65ec
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097343"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Usuwanie lub wyłączanie nowoczesnego uwierzytelniania hybrydowego z Skype dla firm i Exchange

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli włączono hybrydowe nowoczesne uwierzytelnianie (HMA) tylko w celu znalezienia, że nie jest ono odpowiednie dla bieżącego środowiska, możesz wyłączyć usługę HMA. W tym artykule wyjaśniono, jak to zrobić.
  
## <a name="who-is-this-article-for"></a>KtoTo jest ten artykuł?

Jeśli włączono nowoczesne uwierzytelnianie w usłudze Skype dla firm Online lub lokalnie i/lub Exchange Online lub lokalnie i okazało się, że musisz wyłączyć usługę HMA, te kroki są dla Ciebie.

> [!IMPORTANT]
> Zapoznaj się [z artykułem "topologie Skype dla firm obsługiwane przy użyciu nowoczesnego uwierzytelniania](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)", jeśli pracujesz w usłudze Skype dla firm Online lub lokalnie, masz środowisko HMA z topologią mieszaną i przed rozpoczęciem musisz przyjrzeć się obsługiwanym topologiom.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Jak wyłączyć nowoczesne uwierzytelnianie hybrydowe (Exchange)

1. **Exchange lokalnie**: otwórz powłokę zarządzania Exchange i uruchom następujące polecenia: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Połączenie do Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) za pomocą zdalnego programu PowerShell. Uruchom następujące polecenie, aby zmienić flagę  *OAuth2ClientProfileEnabled*  na "false":

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Jak wyłączyć nowoczesne uwierzytelnianie hybrydowe (Skype dla firm)

1. **Skype dla firm lokalnie**: uruchom następujące polecenia w powłoce zarządzania Skype dla firm:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype dla firm Online**: [Połączenie do Skype dla firm Online](manage-skype-for-business-online-with-microsoft-365-powershell.md) za pomocą zdalnego programu PowerShell. Uruchom następujące polecenie, aby wyłączyć nowoczesne uwierzytelnianie:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Link z powrotem do przeglądu nowoczesnego uwierzytelniania](hybrid-modern-auth-overview.md) . 
