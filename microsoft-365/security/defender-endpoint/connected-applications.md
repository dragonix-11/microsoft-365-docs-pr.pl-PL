---
title: Połączone aplikacje w aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender
ms.reviewer: ''
description: Wyświetlanie połączonych aplikacji partnerów, które używają standardowego protokołu OAuth 2.0 do uwierzytelniania i zapewnienia tokenów do używania z Ochrona punktu końcowego w usłudze Microsoft Defender API.
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
ms.openlocfilehash: 9e15103f4366d0717af9cec44d516b4b16a7160a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475570"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Połączone aplikacje w aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Połączone aplikacje są zintegrowane z platformą Defender for Endpoint przy użyciu interfejsów API.

Aplikacje używają standardowego protokołu OAuth 2.0 do uwierzytelniania i uwierzytelniania tokenów do używania z Ochrona punktu końcowego w usłudze Microsoft Defender API. Ponadto aplikacje usługi Azure Active Directory (Azure AD) umożliwiają administratorom dzierżawy ustawienie jawnej kontroli nad tym, do których interfejsów API można uzyskiwać dostęp przy użyciu odpowiedniej aplikacji.

Aby korzystać [z interfejsów](/microsoft-365/security/defender-endpoint/apis-intro) API z połączenią aplikacją, należy wykonać poniższe czynności.

W menu nawigacji po lewej stronie wybierz pozycję **Partnerzy & INTERFEJSY API** (w obszarze **Punkty** końcowe) > **połączone aplikacje**.

## <a name="view-connected-application-details"></a>Wyświetlanie szczegółów połączonej aplikacji

Strona Połączone aplikacje zawiera informacje o aplikacjach usługi Azure AD połączonych Ochrona punktu końcowego w usłudze Microsoft Defender Twojej organizacji. Możesz przejrzeć użycie połączonych aplikacji: ostatnio widziane, liczbę żądań w ciągu ostatnich 24 godzin i zażądać trendów w ciągu ostatnich 30 dni.

:::image type="content" source="images/connected-apps.png" alt-text="Połączone aplikacje" lightbox="images/connected-apps.png":::
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Edytowanie, ponowne konfigurowanie lub usuwanie połączonej aplikacji

Link **Otwórz ustawienia aplikacji powoduje** otwarcie odpowiedniej strony zarządzania aplikacją usługi Azure AD w Azure Portal. Z poziomu Azure Portal możesz zarządzać uprawnieniami, ponownie skonfigurować lub usunąć połączone aplikacje.
