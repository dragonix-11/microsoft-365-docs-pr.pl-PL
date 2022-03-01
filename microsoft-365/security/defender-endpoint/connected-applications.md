---
title: Połączone aplikacje w programie Microsoft Defender for Endpoint
ms.reviewer: ''
description: Wyświetl połączone aplikacje partnerskie, które używają standardowego protokołu OAuth 2.0 do uwierzytelniania i zapewnienia tokenów do używania z interfejsami API programu Microsoft Defender dla punktów końcowych.
keywords: partners, applications, third-party, connections, sentinelone, lookout, bitdefender, corrata, morphisec, paloalto, ziften, better mobile
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4dd630dd2b35c2fedc0340cd873ff065b2685b41
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996272"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Połączone aplikacje w programie Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Połączone aplikacje są zintegrowane z platformą Defender for Endpoint przy użyciu interfejsów API.

Aplikacje używają standardowego protokołu OAuth 2.0 do uwierzytelniania i uwierzytelniania tokenów do używania z interfejsami API programu Microsoft Defender dla punktów końcowych. Ponadto aplikacje usługi Azure Active Directory (Azure AD) umożliwiają administratorom dzierżawy ustawienie jawnej kontroli nad tym, do których interfejsów API można uzyskiwać dostęp przy użyciu odpowiedniej aplikacji.

Aby korzystać [z interfejsów](/microsoft-365/security/defender-endpoint/apis-intro) API z połączenią aplikacją, należy wykonać poniższe czynności.

W menu nawigacji po lewej stronie wybierz pozycję **Partnerzy & INTERFEJSY API** (w obszarze **Punkty** końcowe) > **połączone aplikacje**.

## <a name="view-connected-application-details"></a>Wyświetlanie szczegółów połączonej aplikacji

Strona Połączone aplikacje zawiera informacje o aplikacjach usługi Azure AD połączonych z programem Microsoft Defender for Endpoint w organizacji. Możesz przejrzeć użycie połączonych aplikacji: ostatnio widziane, liczbę żądań w ciągu ostatnich 24 godzin i zażądać trendów w ciągu ostatnich 30 dni.

![Obraz połączonych aplikacji.](images/connected-apps.png)
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Edytowanie, ponowne konfigurowanie lub usuwanie połączonej aplikacji

Link **Otwórz ustawienia aplikacji powoduje** otwarcie odpowiedniej strony zarządzania aplikacją usługi Azure AD w portalu Azure Portal. W portalu Azure Portal możesz zarządzać uprawnieniami, ponownie skonfigurować lub usunąć połączone aplikacje.
