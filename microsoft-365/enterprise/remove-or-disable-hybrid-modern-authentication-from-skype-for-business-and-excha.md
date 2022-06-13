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
ms.openlocfilehash: 6456873f7338b97b3255f3976e7520580ac2a142
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017796"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Usuwanie lub wyłączanie nowoczesnego uwierzytelniania hybrydowego z Skype dla firm i Exchange

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Jeśli włączono hybrydowe nowoczesne uwierzytelnianie (HMA) tylko w celu znalezienia, że nie jest ono odpowiednie dla bieżącego środowiska, możesz wyłączyć usługę HMA. W tym artykule wyjaśniono, jak to zrobić.

## <a name="who-is-this-article-for"></a>KtoTo jest ten artykuł?

Jeśli włączono nowoczesne uwierzytelnianie w usłudze Skype dla firm Online lub lokalnie i/lub Exchange Online lub lokalnie i okazało się, że musisz wyłączyć usługę HMA, te kroki są dla Ciebie.

> [!IMPORTANT]
> Zapoznaj się [z artykułem "topologie Skype dla firm obsługiwane przy użyciu nowoczesnego uwierzytelniania](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)", jeśli pracujesz w usłudze Skype dla firm Online lub lokalnie, masz środowisko HMA z topologią mieszaną i przed rozpoczęciem musisz przyjrzeć się obsługiwanym topologiom.

## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Jak wyłączyć nowoczesne uwierzytelnianie hybrydowe (Exchange)

1. **Exchange lokalnie**: [otwórz powłokę zarządzania Exchange](/powershell/exchange/open-the-exchange-management-shell) i uruchom następujące polecenia:

   ```powershell
   Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
   Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
   ```

2. **Exchange Online**: [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Uruchom następujące polecenie, aby wyłączyć nowoczesne uwierzytelnianie:

   ```powershell
   Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
   ```

## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Jak wyłączyć nowoczesne uwierzytelnianie hybrydowe (Skype dla firm)

1. **Skype dla firm lokalnie**: uruchom następujące polecenia w powłoce zarządzania Skype dla firm:

   ```powershell
   Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
   ```

2. **Skype dla firm Online**: [Połączenie do programu PowerShell Skype dla firm Online](manage-skype-for-business-online-with-microsoft-365-powershell.md). Uruchom następujące polecenie, aby wyłączyć nowoczesne uwierzytelnianie:

   ```powershell
   Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
   ```

[Link z powrotem do przeglądu nowoczesnego uwierzytelniania](hybrid-modern-auth-overview.md).
