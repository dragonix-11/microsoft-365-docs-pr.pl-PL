---
title: Uzyskaj dostęp do interfejsów API usługi ochrony punktu końcowego w usłudze Microsoft Defender
ms.reviewer: ''
description: Dowiedz się, jak za pomocą interfejsów API automatyzować przepływy pracy i wprowadzać innowacje w oparciu o możliwości Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: apis, api, wdatp, open api, microsoft defender for endpoint api, microsoft defender atp, public api, supported apis, alerts, device, user, domain, ip, file, advanced hunting, query
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3638357d2c1440604858fabfa42e5df32569aed3
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172270"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Uzyskaj dostęp do interfejsów API usługi ochrony punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender dla Firm](../defender-business/index.yml)

> [!IMPORTANT]
> Zaawansowane możliwości wyszukiwania zagrożeń nie są uwzględniane w usłudze Defender dla firm. Zobacz [Porównanie Microsoft Defender dla Firm z planami Ochrona punktu końcowego w usłudze Microsoft Defender 1 i 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Usługa Defender for Endpoint uwidacznia wiele swoich danych i akcji za pośrednictwem zestawu programowych interfejsów API. Te interfejsy API umożliwiają automatyzację przepływów pracy i wprowadzanie innowacji w oparciu o możliwości usługi Defender for Endpoint. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Obejrzyj to wideo, aby zapoznać się z krótkim omówieniem interfejsów API usługi Defender for Endpoint.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

Ogólnie rzecz biorąc, należy wykonać następujące kroki, aby korzystać z interfejsów API:

- Tworzenie [aplikacji AAD](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Uzyskiwanie tokenu dostępu przy użyciu tej aplikacji
- Uzyskiwanie dostępu do interfejsu API usługi Defender for Endpoint przy użyciu tokenu

Dostęp do interfejsu API usługi Defender for Endpoint można uzyskać za pomocą **kontekstu aplikacji** lub **kontekstu użytkownika**.

- **Kontekst aplikacji: (zalecane)**

  Używane przez aplikacje uruchamiane bez zalogowanego użytkownika. na przykład aplikacje działające jako usługi w tle lub demony.

  Kroki, które należy wykonać w celu uzyskania dostępu do interfejsu API usługi Defender for Endpoint z kontekstem aplikacji:

  1. Utwórz aplikację internetową AAD.
  2. Przypisz żądane uprawnienie do aplikacji, na przykład "Odczyt alertów", "Izoluj maszyny".
  3. Utwórz klucz dla tej aplikacji.
  4. Pobierz token przy użyciu aplikacji z jej kluczem.
  5. Uzyskiwanie dostępu do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu tokenu

     Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](exposed-apis-create-app-webapp.md).

- **Kontekst użytkownika:**

  Służy do wykonywania akcji w interfejsie API w imieniu użytkownika.

  Kroki, które należy wykonać, aby uzyskać dostęp do interfejsu API usługi Defender for Endpoint z kontekstem użytkownika:

  1. Utwórz AAD aplikację natywną.
  2. Przypisz żądane uprawnienie do aplikacji, np. "Odczyt alertów", "Izolowanie maszyn" itp.
  3. Pobierz token przy użyciu aplikacji z poświadczeniami użytkownika.
  4. Uzyskiwanie dostępu do interfejsu API Ochrona punktu końcowego w usłudze Microsoft Defender przy użyciu tokenu

     Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu za pomocą kontekstu użytkownika](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>Tematy pokrewne

- [interfejsy API Ochrona punktu końcowego w usłudze Microsoft Defender](exposed-apis-list.md)
- [Dostęp Ochrona punktu końcowego w usłudze Microsoft Defender z kontekstem aplikacji](exposed-apis-create-app-webapp.md)
- [Dostęp Ochrona punktu końcowego w usłudze Microsoft Defender z kontekstem użytkownika](exposed-apis-create-app-nativeapp.md)
