---
title: Uzyskiwanie dostępu do interfejsów API programu Microsoft Defender dla punktów końcowych
ms.reviewer: ''
description: Dowiedz się, jak za pomocą interfejsów API automatyzować przepływy pracy i wprowadzać w nich innowacje w oparciu o program Microsoft Defender w zakresie funkcji punktu końcowego
keywords: apis, api, wdatp, open api, microsoft defender for endpoint api, microsoft defender atp, public api, supported api, alerts, device, user, domain, ip, file, advanced hunting, query
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
ms.openlocfilehash: a73df39c6d26bdfd44a7f4f629e148e7f0afabb2
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996879"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Uzyskiwanie dostępu do interfejsów API programu Microsoft Defender dla punktów końcowych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Program Defender for Endpoint udostępnia większość danych i akcji za pośrednictwem zestawu programistycznych interfejsów API. Te interfejsy API umożliwią Automatyzowanie przepływów pracy i wprowadzanie innowacji w oparciu o funkcje usługi Defender for Endpoint. Dostęp do interfejsu API wymaga uwierzytelniania OAuth2.0. Aby uzyskać więcej informacji, zobacz [Kod autoryzacji protokołu OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Obejrzyj ten klip wideo, aby szybko oomówić interfejsy API usługi Defender dla punktu końcowego.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

Aby korzystać z interfejsów API, musisz wykonać następujące czynności:

- Tworzenie AAD [aplikacji](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Uzyskiwanie tokenu dostępu przy użyciu tej aplikacji
- Korzystanie z tokenu w celu uzyskania dostępu do usługi Defender for Endpoint API

Dostęp do interfejsu API punktu końcowego programu Defender można uzyskać z **kontekstem aplikacji** **lub kontekstem użytkownika**.

- **Kontekst aplikacji: (zalecane)**

  Używane przez aplikacje uruchamiane bez zalogowania się użytkownika. na przykład aplikacje, które działają jako usługi w tle lub jako daemony.

  Kroki, które należy wykonać, aby uzyskać dostęp do usługi Defender dla interfejsu API punktu końcowego w kontekście aplikacji:

  1. Utwórz nową AAD web-Application.
  2. Przypisz żądane uprawnienie do aplikacji, na przykład "Odczyt alertów", "Izoluj komputery".
  3. Utwórz klucz dla tej aplikacji.
  4. Pobierz token przy użyciu aplikacji wraz z jej kluczem.
  5. Używanie tokenu w celu uzyskania dostępu do interfejsu API programu Microsoft Defender dla punktu końcowego

     Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu za pomocą kontekstu aplikacji](exposed-apis-create-app-webapp.md).

- **Kontekst użytkownika:**

  Służy do wykonywania akcji w interfejsie API w imieniu użytkownika.

  Czynności, które należy wykonać, aby uzyskać dostęp do usługi Defender for Endpoint API z kontekstem użytkownika:

  1. Tworzenie AAD natywnej.
  2. Przypisz żądane uprawnienie do aplikacji, np. "Odczyt alertów", "Izoluj komputery" itd.
  3. Uzyskaj token przy użyciu aplikacji z poświadczeniami użytkownika.
  4. Używanie tokenu w celu uzyskania dostępu do interfejsu API programu Microsoft Defender dla punktu końcowego

     Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu z kontekstem użytkownika](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Interfejsy API programu Microsoft Defender dla punktów końcowych](exposed-apis-list.md)
- [Uzyskiwanie dostępu do programu Microsoft Defender dla punktu końcowego w kontekście aplikacji](exposed-apis-create-app-webapp.md)
- [Dostęp do programu Microsoft Defender dla punktu końcowego z kontekstem użytkownika](exposed-apis-create-app-nativeapp.md)
