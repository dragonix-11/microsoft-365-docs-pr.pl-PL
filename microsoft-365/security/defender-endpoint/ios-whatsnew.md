---
title: Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender na iOS
description: Dowiedz się więcej o najważniejszych zmianach w poprzednich wersjach Ochrona punktu końcowego w usłudze Microsoft Defender na iOS.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, instalacja, macos, whatsnew
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
ms.openlocfilehash: 3f05c819e5390504bca9c1f5aaa7f85d1e7edc2a
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090481"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-ios"></a>Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender na iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="network-protection"></a>Ochrona sieci
Ochrona sieci w Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz dostępna w publicznej wersji zapoznawczej. Ochrona sieci zapewnia ochronę przed nieautoryzowanymi zagrożeniami związanymi z Wi-Fi, nieautoryzowanym sprzętem, takim jak urządzenia ananasowe, i powiadamia użytkownika o wykryciu powiązanego zagrożenia. Użytkownicy zobaczą również środowisko z przewodnikiem umożliwiające nawiązywanie połączeń z bezpiecznymi sieciami i zmienianie sieci po nawiązaniu połączenia z niezabezpieczonym połączeniem.

Obejmuje ona kilka kontrolek administratora zapewniających elastyczność, na przykład możliwość konfigurowania funkcji z poziomu centrum Microsoft Endpoint Manager Administracja. Administratorzy mogą również włączyć mechanizmy kontroli prywatności, aby skonfigurować dane wysyłane przez usługę Defender for Endpoint z urządzeń iOS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ochrony sieci]().

Ochrona sieci dla iOS jest już włączona dla dzierżawy. Użytkownicy końcowi, którzy testują funkcję ochrony sieci, mogą zainstalować wersję zapoznawczą aplikacji za pośrednictwem TestFlight. Przejdź do https://aka.ms/mdeiospp obszaru na urządzeniu iOS. Spowoduje to wyświetlenie monitu o zainstalowanie aplikacji TestFlight na urządzeniu lub otwarcie TestFlight w przypadku, gdy jest już zainstalowana. W aplikacji TestFlight postępuj zgodnie z instrukcjami wyświetlanymi na ekranie, aby zainstalować punkt końcowy usługi Microsoft Defender. Sprawdź, czy numer wersji mde to 1.1.29270104.

## <a name="integration-with-tunnel"></a>Integracja z Tunnel
Ochrona punktu końcowego w usłudze Microsoft Defender na iOS można teraz zintegrować z usługą Microsoft Tunnel, rozwiązaniem bramy sieci VPN w celu zapewnienia bezpieczeństwa i łączności w jednej aplikacji.  Integracja z Tunnel zapewnia prostsze, bezpieczne środowisko sieci VPN na iOS przy użyciu tylko jednej aplikacji. Ta funkcja była wcześniej dostępna tylko w Android. Aby uzyskać więcej informacji, [zobacz wpis techcommunity tutaj](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/what-s-new-in-microsoft-endpoint-manager-2204-april-edition/ba-p/3297995)

## <a name="improved-experience-on-supervised-ios-devices"></a>Ulepszone środowisko na nadzorowanych urządzeniach iOS

Ochrona punktu końcowego w usłudze Microsoft Defender na iOS ma teraz wyspecjalizowane możliwości na nadzorowanych urządzeniach z systemem iOS/iPadOS, biorąc pod uwagę zwiększone możliwości zarządzania zapewniane przez platformę na tego typu urządzeniach. Może również zapewnić ochronę sieci Web **bez konfigurowania lokalnej sieci VPN na urządzeniu**. Zapewnia to użytkownikom końcowym bezproblemowe środowisko, a jednocześnie jest chronione przed wyłudzaniem informacji i innymi atakami internetowymi. Aby uzyskać szczegółowe informacje, odwiedź [tę dokumentację](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-app-store"></a>Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz usługą Microsoft Defender w sklepie App Store

Ochrona punktu końcowego w usłudze Microsoft Defender jest teraz dostępna jako **usługa Microsoft Defender** w sklepie z aplikacjami. Dzięki tej aktualizacji aplikacja będzie dostępna w wersji zapoznawczej dla **użytkowników w regionie USA**. W zależności od sposobu logowania się do aplikacji przy użyciu konta służbowego lub osobistego będziesz mieć dostęp do funkcji dla Ochrona punktu końcowego w usłudze Microsoft Defender lub funkcji usługi Microsoft Defender dla użytkowników indywidualnych. Aby uzyskać więcej informacji, zobacz [ten blog](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals).

## <a name="threat-and-vulnerability-management"></a>Zarządzanie zagrożeniami i lukami w zabezpieczeniach

25 stycznia 2022 r. ogłosiliśmy ogólną dostępność zarządzania zagrożeniami i lukami w zabezpieczeniach w Android i iOS. Aby uzyskać więcej informacji, zobacz [wpis techcommunity tutaj](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="1128250101"></a>1.1.28250101
- **Integracja z usługą Tunnel** — Ochrona punktu końcowego w usłudze Microsoft Defender na iOS można teraz zintegrować z Microsoft Tunnel, rozwiązaniem bramy sieci VPN w celu włączenia zabezpieczeń i łączności w jednej aplikacji. Aby uzyskać więcej informacji, zobacz [omówienie Microsoft Tunnel](/mem/intune/protect/microsoft-tunnel-overview).
- **Dołączenie bezdotyku dla zarejestrowanych urządzeń iOS** zarejestrowanych za pośrednictwem Microsoft Endpoint Manager (Intune) jest ogólnie dostępne. Aby uzyskać więcej informacji, zobacz [Zero touch onboarding of Ochrona punktu końcowego w usłudze Microsoft Defender (Zero touch onboarding of Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/ios-install#zero-touch-onboarding-of-microsoft-defender-for-endpoint)).
- Poprawki.


## <a name="1124210103"></a>1.1.24210103

- Rozwiązano problemy z łącznością z Internetem na urządzeniach nadzorowanych. Aby uzyskać więcej informacji, zobacz [Deploy Defender for Endpoint on enrolled iOS devices (Wdrażanie usługi Defender for Endpoint na zarejestrowanych urządzeniach iOS](ios-install.md)).
- Poprawki.

## <a name="1123250104"></a>1.1.23250104

- Optymalizacje wydajności — przetestuj wydajność baterii w tej wersji i poinformuj nas o swojej opinii.
- **Dołączanie bezdotyku dla zarejestrowanych urządzeń iOS** — w tej wersji dodano wersję zapoznawczą dołączania bezdotyku dla urządzeń zarejestrowanych za pośrednictwem Microsoft Endpoint Manager (Intune). Aby uzyskać więcej informacji, zobacz tę [dokumentację](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint) , aby uzyskać więcej informacji na temat konfiguracji i konfiguracji.
- **Mechanizmy kontroli prywatności** — skonfiguruj mechanizmy kontroli prywatności dla raportu alertów phish. Aby uzyskać więcej informacji, zobacz [Konfigurowanie funkcji iOS](ios-configure-features.md).

## <a name="1123010101"></a>1.1.23010101

- Poprawki błędów i ulepszenia wydajności 
  - W tej wersji dokonano optymalizacji wydajności. Przetestuj wydajność baterii w tej wersji i poinformuj nas o swojej opinii.

## <a name="1120240103"></a>1.1.20240103
- Karta Kondycja urządzenia — karta Kondycja urządzenia powiadamia użytkowników końcowych o wszelkich oczekujących aktualizacjach oprogramowania.
- Ulepszenia użyteczności — użytkownicy końcowi mogą teraz wyłączyć sieć VPN usługi Defender for Endpoint z samej aplikacji Microsoft Defender. Przed tą aktualizacją użytkownicy końcowi musieli wyłączyć sieć VPN tylko z aplikacji Ustawienia.
- Poprawki.

## <a name="1120020101"></a>1.1.20020101
- Ulepszenia środowiska użytkownika — Ochrona punktu końcowego w usłudze Microsoft Defender ma nowy wygląd.
- Poprawki.

## <a name="1117240101"></a>1.1.17240101
- Obsługa zarządzania aplikacjami mobilnymi (MAM) za pośrednictwem Intune jest ogólnie dostępna w tej wersji. Aby uzyskać więcej informacji, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender sygnały ryzyka dostępne dla zasad Ochrona aplikacji](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-defender-for-endpoint-risk-signals-available-for-your/ba-p/2186322)
- **Wykrywanie jailbreak** jest ogólnie dostępne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad dostępu warunkowego na podstawie sygnałów ryzyka urządzenia](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatyczna konfiguracja profilu sieci VPN** dla zarejestrowanych urządzeń za pośrednictwem Microsoft Endpoint Manager (Intune) jest ogólnie dostępna. Aby uzyskać więcej informacji, zobacz [Automatyczne konfigurowanie profilu sieci VPN dla zarejestrowanych urządzeń iOS](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Poprawki.

## <a name="1115140101"></a>1.1.15140101

- **Wykrywanie jailbreak** jest w wersji zapoznawczej. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad dostępu warunkowego na podstawie sygnałów ryzyka urządzenia](ios-configure-features.md#conditional-access-with-defender-for-endpoint-on-ios).
- **Automatyczna konfiguracja profilu sieci VPN** jest dostępna w wersji zapoznawczej dla zarejestrowanych urządzeń za pośrednictwem Microsoft Endpoint Manager (Intune). Aby uzyskać więcej informacji, zobacz [Automatyczne konfigurowanie profilu sieci VPN dla zarejestrowanych urządzeń iOS](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding).
- Nazwa produktu usługi Microsoft Defender ATP została zaktualizowana do Ochrona punktu końcowego w usłudze Microsoft Defender w sklepie z aplikacjami.
- Ulepszone środowisko logowania.
- Poprawki.

## <a name="1115010101"></a>1.1.15010101

- W tej wersji ogłaszamy obsługę urządzeń z systemem iPadOS/iPad.
- Poprawki.
