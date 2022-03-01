---
title: Omówienie zarządzania i interfejsów API
ms.reviewer: ''
description: Informacje o narzędziach do zarządzania i kategoriach interfejsu API w programie Microsoft Defender for Endpoint
keywords: onboarding, api, siem, rbac, access, portal, integration, investigation, response, entitys, entity, user context, application context, streaming
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
ms.openlocfilehash: 36975b55d8f26ae7788495543ae42922ea404c66
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010432"
---
# <a name="overview-of-management-and-apis"></a>Omówienie zarządzania i interfejsów API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mgt-apis-abovefoldlink)


Program Defender for Endpoint obsługuje wiele różnych opcji zapewniających, że klienci mogą łatwo zaadoptować tę platformę.

Potwierdzając, że środowiska i struktury klientów mogą się różnić, program Defender for Endpoint został utworzony z elastyczność i szczegółową kontrolą w celu dopasowania do różnych wymagań klientów.

## <a name="endpoint-onboarding-and-portal-access"></a>Dołączanie punktów końcowych i dostęp do portalu

Dołączanie urządzeń jest w pełni zintegrowane z usługami Microsoft Endpoint Manager i Microsoft Intune dla urządzeń klienckich oraz z programem Microsoft Defender dla urządzeń serwerowych, co zapewnia kompleksowe środowisko konfiguracji, wdrażania i monitorowania. Ponadto program Microsoft Defender for Endpoint zasady grupy narzędzia innych firm używane do zarządzania urządzeniami.

Program Defender for Endpoint zapewnia szczegółowe sterowanie tym, co użytkownicy z dostępem do portalu mogą widzieć i robić przez elastyczność kontroli dostępu opartej na rolach (RBAC, role based access control). Model RBAC obsługuje wszystkie odmiany struktury zespołów ds. zabezpieczeń:

- Globalnie rozpowszechniane organizacje i zespoły zabezpieczeń
- Zespoły ds. operacji zabezpieczeń modelu warstwowego
- W pełni podzielone działy z pojedynczymi scentralizowanymi zespołami ds. globalnej operacji zabezpieczeń

## <a name="available-apis"></a>Dostępne interfejsy API

Rozwiązanie Microsoft Defender for Endpoint jest zbudowane na platformie gotowej do integracji.

Program Defender for Endpoint udostępnia większość danych i akcji za pośrednictwem zestawu programistycznych interfejsów API. Te interfejsy API umożliwią Automatyzowanie przepływów pracy i wprowadzanie innowacji w oparciu o funkcje usługi Defender for Endpoint.

![Obraz dostępnych interfejsów API i integracji w programie Microsoft Defender for Endpoint.](images/mdatp-apis.png)

Interfejsy API usługi Defender dla punktu końcowego można pogrupowane w trzy grupy:

- Interfejsy API programu Microsoft Defender dla punktów końcowych
- Interfejs API przesyłania strumieniowego danych nieprzetworzonego
- Integracja usług SIEM

## <a name="microsoft-defender-for-endpoint-apis"></a>Interfejsy API programu Microsoft Defender dla punktów końcowych

Usługa Defender for Endpoint oferuje model warstwowego interfejsu API uwzględniający dane i możliwości w modelu ustrukturyzowanym, przejrzystym i łatwym w użyciu, który jest ujawniony za pomocą standardowego modelu uwierzytelniania i autoryzacji opartego na usłudze Azure AD, który umożliwia dostęp w kontekście użytkowników lub aplikacji SaaS. Model interfejsu API został zaprojektowany w celu udostępnienia jednostek i możliwości w spójnej formie.

Obejrzyj ten klip wideo, aby szybko oomówić interfejsy API usługi Defender dla punktu końcowego.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

Interfejs **API** badania udostępnia rozbudowę usługi Defender for Endpoint — eksponowanie jednostek obliczeniowych lub "profilowych" (na przykład urządzeń, użytkowników i plików) i chętnych zdarzeń (na przykład tworzenia procesów i tworzenia plików), które zazwyczaj opisują zachowanie związane z jednostką, umożliwiając dostęp do danych za pośrednictwem interfejsów badania umożliwiających dostęp do danych opartych na zapytaniach. Aby uzyskać więcej informacji, zobacz [Obsługiwane interfejsy API](exposed-apis-list.md).

Interfejs **API odpowiedzi** udostępnia możliwość wykonywania działań w usłudze i na urządzeniach, umożliwiając klientom dostęp do wskaźników, zarządzanie ustawieniami, stanem alertów, a także programowe działania na urządzeniach, takie jak odizolowanie urządzeń od sieci, pliki kwarantanny itp.

## <a name="raw-data-streaming-api"></a>Interfejs API przesyłania strumieniowego danych nieprzetworzonego

Interfejs API przesyłania strumieniowego nieprzetworzonych danych w programie Defender for Endpoint umożliwia klientom przesyłanie zdarzeń w czasie rzeczywistym i alertów z ich wystąpień w momencie wystąpienia w pojedynczym strumieniu danych, co zapewnia mechanizm dostarczania o małych opóźnieniach i wysokiej przepływności.

Informacje o zdarzeniach usługi Defender for Endpoint są wypychane bezpośrednio do magazynu platformy Azure w celu przechowywania danych przez dłuższy czas lub do centrum zdarzeń platformy Azure w celu ich użycia przez usługi wizualizacji lub dodatkowe aparaty przetwarzania danych.

Aby uzyskać więcej informacji, zobacz [Nieprzetworzone interfejs API przesyłania strumieniowego danych](raw-data-export.md).

Nowy interfejs API usługi Microsoft 365 Defender Streaming zawiera nie tylko zdarzenia urządzenia, ale również pocztę e-mail i zdarzenia alertów.
Aby uzyskać więcej informacji, zobacz [Microsoft 365 Defender interfejs API przesyłania strumieniowego](../defender/streaming-api.md).

## <a name="siem-api"></a>SIEM API

Włączenie integracji informacji zabezpieczeń i zarządzania zdarzeniami (SIEM) umożliwia wykrywanie z programu Microsoft 365 Defender przy użyciu rozwiązania SIEM lub przez bezpośrednie połączenie z interfejsem API REST wykrywania. Aktywuje to sekcję szczegółów dostępu łącznika SIEM z wstępnie wypełnionymi wartościami, a aplikacja jest tworzona w ramach Twojej dzierżawy usługi Azure Active Directory (Azure AD). 

## <a name="related-topics"></a>Tematy pokrewne

- [Uzyskiwanie dostępu do interfejsów API programu Microsoft Defender dla punktów końcowych](apis-intro.md)
- [Obsługiwane interfejsy API](exposed-apis-list.md)
- [Szanse partnerów technicznych](partner-integration.md)
