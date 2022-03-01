---
title: Co nowego w programie Microsoft Defender dla punktu końcowego w systemie iOS
description: Dowiedz się więcej o głównych zmianach dotyczących poprzednich wersji programu Microsoft Defender dla punktu końcowego w systemie iOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: sunasing
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 503ae29fd371948f68b0c25aafe34f02f7bb8f1d
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015368"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>Co nowego w programie Microsoft Defender dla punktu końcowego w systemie iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="improved-experience-on-supervised-ios-devices"></a>Ulepszone środowisko pracy na urządzeniach z systemem iOS nadzorowanych

Program Microsoft Defender for Endpoint dla systemu iOS oferuje obecnie wyspecjalizowaną możliwość pracy na urządzeniach z systemem iOS/iPadOS nadzorowanych ze względu na zwiększone możliwości zarządzania zapewniane przez platformę na tych typach urządzeń. Może również zapewniać ochronę sieci Web **bez konfigurowania lokalnego połączenia VPN na urządzeniu**. Zapewnia to użytkownikom konieczną ochronę przed wyłudzaniem informacji i innymi atakami internetowymi. Aby uzyskać szczegółowe informacje, odwiedź [tę dokumentację](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Program Microsoft Defender for Endpoint jest teraz programem Microsoft Defender w sklepie z aplikacjami

Program Microsoft Defender for Endpoint jest teraz dostępny jako **program Microsoft Defender** w sklepie z aplikacjami. W tej aktualizacji aplikacja będzie dostępna w wersji Preview dla **klientów w USA**. W zależności od tego, jak logujesz się do aplikacji za pomocą konta służbowego lub osobistego, będziesz mieć dostęp do funkcji programu Microsoft Defender dla punktu końcowego lub funkcji programu Microsoft Defender dla poszczególnych osób. Aby uzyskać więcej informacji, zobacz [ten blog](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals).

## <a name="threat-and-vulnerability-management"></a>Zarządzanie zagrożeniami i lukami w zabezpieczeniach

25 stycznia 2022 r. ogłosiliśmy ogólną dostępność funkcji zarządzania zagrożeniami i lukami w zabezpieczeniach w systemach Android i iOS. Aby uzyskać więcej szczegółowych informacji, [zobacz wpis w witrynie TechCommunity tutaj](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="1124210103"></a>1.1.24210103

- Rozwiązano problemy z łącznością z Internetem na urządzeniach nadzorowanych. Aby uzyskać więcej informacji, zobacz [Wdrażanie programu Defender dla punktu końcowego na zarejestrowanych urządzeniach z systemem iOS](ios-install.md).
- Poprawki błędów.

## <a name="1123250104"></a>1.1.23250104

- Optymalizacje wydajności — przetestuj wydajność baterii w tej wersji i daj nam znać swoją opinię.
- **Zero-touch onboard for enrolled iOS devices** - With this version, the preview of Zero-touch onboard for devicesenrolled through Microsoft Endpoint Manager (Intune) has been added. Aby uzyskać więcej informacji, zobacz tę dokumentację [,](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) aby uzyskać więcej informacji na temat konfiguracji i konfiguracji.
- **Mechanizmy kontroli prywatności** — konfigurowanie kontrolek prywatności dla raportów alertów wyłudowych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie funkcji systemu iOS](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Poprawki błędów i ulepszenia wydajności 
  - W tej wersji w tej wersji w zoptymalizowano wydajność. Przetestuj wydajność baterii w tej wersji i pomów nas o swojej opinii.

## <a name="1120240103"></a>1.1.20240103
- Karta Kondycja urządzenia — karta Kondycja urządzenia powiadamia użytkowników końcowych o wszelkich oczekujących aktualizacjach oprogramowania.
- Ulepszenia dotyczące użyteczności — użytkownicy końcowi mogą teraz wyłączyć usługę Defender for Endpoint VPN z samej aplikacji MSDefender. Przed tą aktualizacją użytkownicy końcowi musieli wyłączyć połączenia VPN tylko z Ustawienia sieci.
- Poprawki błędów.

## <a name="1120020101"></a>1.1.20020101
- Ulepszenia środowiska UX — program Microsoft Defender for Endpoint ma nowy wygląd.
- Poprawki błędów.

## <a name="1117240101"></a>1.1.17240101
- Obsługa zarządzania aplikacjami mobilnymi (MAM) za pośrednictwem usługi Intune jest ogólnie dostępna w tej wersji. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender for Endpoint risk signals available for your App protection policies](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **Na ogół jest** dostępne wykrywanie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad dostępu warunkowego na podstawie sygnałów ryzyka urządzenia](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatyczna konfiguracja profilu VPN dla** zarejestrowanych urządzeń za pośrednictwem Microsoft Endpoint Manager (Intune) jest ogólnie dostępna. Aby uzyskać więcej informacji, [zobacz Automatyczne konfigurowanie profilu VPN dla zarejestrowanych urządzeń z systemem iOS](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Poprawki błędów.

## <a name="1115140101"></a>1.1.15140101

- **Funkcja wykrywania** błędów jest w podglądzie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad dostępu warunkowego na podstawie sygnałów ryzyka urządzenia](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatyczna konfiguracja profilu VPN jest w wersji** Preview dla zarejestrowanych urządzeń za pośrednictwem Microsoft Endpoint Manager (Intune). Aby uzyskać więcej informacji, [zobacz Automatyczne konfigurowanie profilu VPN dla zarejestrowanych urządzeń z systemem iOS](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Nazwa produktu Microsoft Defender ATP została teraz zaktualizowana do programu Microsoft Defender for Endpoint w sklepie z aplikacjami.
- Ulepszone środowisko logowania.
- Poprawki błędów.

## <a name="1115010101"></a>1.1.15010101

- W tej wersji zapowiadamy obsługę urządzeń z systemem iPadOS/iPad urządzeniach.
- Poprawki błędów.
