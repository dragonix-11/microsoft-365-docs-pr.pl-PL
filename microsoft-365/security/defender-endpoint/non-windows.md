---
title: Program Microsoft Defender for Endpoint dla platform Windows innych niż platformy
description: Dowiedz się więcej o możliwościach programu Microsoft Defender dla punktów końcowych dla Windows platform
keywords: non windows, mac, macos, linux, android
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c8887f9e26c53d57aa49ec6fb65733cac6e562a9
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033767"
---
# <a name="microsoft-defender-for-endpoint-for-non-windows-platforms"></a>Program Microsoft Defender for Endpoint dla platform Windows innych niż platformy

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Firma Microsoft od dawna chciała rozszerzyć swoje wiodące w branży funkcje zabezpieczeń punktów końcowych poza program Windows i Windows Server do systemów macOS, Linux, Android i iOS.

Organizacje mierzą się z zagrożeniami na różnych platformach i urządzeniach. Nasze zespoły dokładały starań, aby budować rozwiązania zabezpieczające nie tylko dla *firmy Microsoft,* ale również *firmy Microsoft,* aby umożliwić naszym klientom ochronę i zabezpieczanie ich niejednorodnych środowisk. Uważnie słuchamy opinii klientów i ściśle współpracujemy z naszymi klientami, aby tworzyć rozwiązania spełniające ich potrzeby.

Dzięki programowi Microsoft Defender for Endpoint klienci mogą korzystać z ujednoliconego widoku wszystkich zagrożeń i alertów w portalu Microsoft 365 Defender na platformach Windows i innych niż Windows, dzięki czemu mogą uzyskać pełny obraz tego, co dzieje się w ich środowisku, dzięki czemu mogą szybciej oceniać zagrożenia i odpowiadać na nie.

## <a name="microsoft-defender-for-endpoint-on-macos"></a>Program Microsoft Defender for Endpoint w systemie macOS

Program Microsoft Defender for Endpoint w systemie macOS oferuje funkcje oprogramowania antywirusowego, wykrywanie i reagowanie w punktach końcowych (EDR) i zarządzanie lukami w zabezpieczeniach dla trzech najnowszych wersji systemu macOS. Klienci mogą wdrażać rozwiązanie i zarządzać nimi za pośrednictwem usług Microsoft Endpoint Manager i Jamf. Podobnie jak w Microsoft Office w systemie macOS, do zarządzania aktualizacjami programu Microsoft Defender for Endpoint na komputerach Mac jest używana usługa Microsoft Auto Update. Aby uzyskać informacje na temat kluczowych funkcji i korzyści, przeczytaj nasze [ogłoszenia](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/macOS).

Aby uzyskać więcej szczegółowych informacji na temat rozpoczynania pracy, odwiedź dokumentację programu Defender for Endpoint w systemie [macOS.](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Następujące funkcje nie są obecnie obsługiwane w punktach końcowych systemu macOS:
>
> - Ochrona przed utratą danych
> - Odpowiedź na żywo
> - Zarządzanie zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego

## <a name="microsoft-defender-for-endpoint-on-linux"></a>Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie

Program Microsoft Defender for Endpoint dla systemu Linux oferuje funkcje zapobiegania dostępom antywirusowym (AV), wykrywanie i reagowanie w punktach końcowych (EDR) i zarządzanie lukami w zabezpieczeniach dla serwerów Linux. Obejmuje to pełne środowisko wiersza polecenia służące do konfigurowania agenta i zarządzania jego agentem, inicjowania skanów i zarządzania zagrożeniami. Obsługujemy najnowsze wersje sześciu najpopularniejszych dystrybucji Linux Server: R CZĘSTO spotykane wersje R CZĘSTO spotykane: R CZĘSTO spotykane wersje, R CZĘSTO ZADAWANE 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS lub wyżej LTS, SLES 12+, Debian 9+, Oraz Oracle Linux 7.2. Program Microsoft Defender for Endpoint w systemie Linux można wdrożyć i skonfigurować przy użyciu oprogramowania 99, Ansible lub za pomocą istniejącego narzędzia do zarządzania konfiguracją systemu Linux. Aby uzyskać informacje na temat kluczowych funkcji i korzyści, przeczytaj nasze [ogłoszenia](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Linux).

Aby uzyskać więcej szczegółowych informacji na temat rozpoczynania pracy, odwiedź dokumentację programu Microsoft Defender for Endpoint dla systemu [Linux](microsoft-defender-endpoint-linux.md).


> [!NOTE]
> Następujące funkcje nie są obecnie obsługiwane w punktach końcowych systemu Linux:
>
> - Ochrona przed utratą danych
> - Odpowiedź na żywo
> - Zarządzanie zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego

## <a name="microsoft-defender-for-endpoint-on-android"></a>Program Microsoft Defender for Endpoint w systemie Android

Program Microsoft Defender dla punktu końcowego w systemie Android to nasze rozwiązanie do ochrony przed zagrożeniami na urządzeniach z systemem Android 6.0 lub wyższym. Obsługiwane są Enterprise systemu Android (profil służbowy) i tryb administratora urządzenia. W systemie Android oferujemy ochronę sieci Web, która obejmuje ochronę przed wyłudzaniem informacji, blokowanie niebezpiecznych połączeń i ustawianie wskaźników niestandardowych. Rozwiązanie skanuje w poszukiwaniu złośliwego oprogramowania i potencjalnie niepożądanych aplikacji (PUA) i oferuje dodatkowe funkcje ochrony przed naruszeniem za pośrednictwem integracji z programem Microsoft Endpoint Manager dostępem warunkowym. Aby uzyskać informacje na temat kluczowych funkcji i korzyści, przeczytaj nasze [ogłoszenia](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Android).

Aby uzyskać więcej szczegółowych informacji na temat rozpoczynania pracy, odwiedź dokumentację programu Microsoft Defender for Endpoint [w systemie Android](microsoft-defender-endpoint-android.md).

## <a name="microsoft-defender-for-endpoint-on-ios"></a>Program Microsoft Defender for Endpoint w systemie iOS

Program Microsoft Defender for Endpoint w systemie iOS to nasze rozwiązanie do ochrony przed zagrożeniami na urządzeniach z systemem iOS 11.0 lub wyższym. Urządzenia zarejestrowane w dzierżawie klienta (zarejestrowane lub nierejestrowane) są obsługiwane. Obsługiwane są zarówno urządzenia nadzorowane, jak i niezadzorowane zarejestrowane urządzenia. W systemie iOS oferujemy ochronę sieci Web, która obejmuje ochronę przed wyłudzaniem informacji, blokowanie niebezpiecznych połączeń i ustawianie wskaźników niestandardowych oraz wykrywanie błędów. Aby uzyskać więcej informacji na temat kluczowych funkcji i korzyści, przeczytaj nasze [ogłoszenia](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

Aby uzyskać więcej szczegółowych informacji na temat rozpoczynania pracy, odwiedź dokumentację programu Microsoft Defender for Endpoint w systemie [iOS.](microsoft-defender-endpoint-ios.md)

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Uprawnieni licencjonowani użytkownicy mogą używać programu Microsoft Defender dla punktu końcowego na maksymalnie pięciu jednoczesnych urządzeniach. Program Microsoft Defender for Endpoint jest również dostępny do zakupu w sklepie Dostawca rozwiązań w chmurze (CSP).

Klienci mogą uzyskać program Microsoft Defender for Endpoint w systemie macOS za pośrednictwem autonomicznej licencji programu Microsoft Defender for Endpoint w ramach usługi Microsoft 365 A5/E5 lub Microsoft 365 Security.

Ostatnio zapowiadane funkcje programu Microsoft Defender dla punktu końcowego w systemach Android i iOS są zawarte w powyższych powyższych ofertach w ramach pięciu kwalifikujących się urządzeń dla uprawnionych licencjonowanych użytkowników.

Program Defender for Endpoint dla systemu Linux jest dostępny za pośrednictwem wersji SKU Defender for Endpoint Server, która jest dostępna zarówno dla klientów komercyjnych, jak i edukacyjnych.

Skontaktuj się ze swoim zespołem ds. kont lub zespołem CSP, aby uzyskać ceny i dodatkowe wymagania dotyczące uprawnień.
