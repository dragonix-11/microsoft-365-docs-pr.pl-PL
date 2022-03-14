---
title: Program Microsoft Defender dla punktu końcowego — obrona przed zagrożeniami na urządzeniach przenośnych
ms.reviewer: ''
description: Omówienie ochrony przed zagrożeniami na urządzeniach przenośnych w programie Microsoft Defender dla punktu końcowego
keywords: mobile, defender, Microsoft Defender for Endpoint, ios, mtd, android, security
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 07cd42d1ab1c6b945525b1e9ed4b463ee76376e1
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2022
ms.locfileid: "63468938"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Program Microsoft Defender dla punktu końcowego — obrona przed zagrożeniami na urządzeniach przenośnych

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Program Microsoft Defender for Endpoint w systemach Android i iOS to nasze rozwiązanie do ochrony przed **zagrożeniami mobilnymi (MTD).** Zazwyczaj firmy aktywnie chronią komputery przed luki w zabezpieczeniach i atakami, podczas gdy urządzenia przenośne często są niemonitorowane i niechronione. Platformy mobilne, które mają wbudowaną ochronę, taką jak izolacji aplikacji i magazyny aplikacji dla klientów stacjonarnych, są narażona na ataki oparte na sieci Web lub na innych zaawansowanych atakach. Ponieważ więcej pracowników korzysta z urządzeń do pracy i uzyskiwania dostępu do informacji poufnych, konieczne jest wdrożenie przez firmy rozwiązania MTD w celu ochrony urządzeń i zasobów przed coraz bardziej zaawansowanymi atakami na urządzenia przenośne.

## <a name="key-capabilities"></a>Najważniejsze funkcje

Program Microsoft Defender for Endpoint dla systemów Android i iOS oferuje poniższe kluczowe funkcje. Aby uzyskać informacje o najnowszych funkcjach i zaletach, przeczytaj [nasze ogłoszenia](https://aka.ms/mdeblog).

<br>

|Funkcja|Opis|
|---|---|
|Ochrona sieci Web|Ochrona przed wyłudzaniem informacji, blokowanie niebezpiecznych połączeń sieciowych i obsługa wskaźników niestandardowych.|
|Ochrona przed złośliwym oprogramowaniem (tylko system Android)|Skanowanie w celu skanowania w celu wymiany złośliwych aplikacji.|
|Detection (tylko system iOS)|Wykrywanie urządzeń o jailbroken.|
|Zarządzanie zagrożeniami i lukami (TVM) |Ocena luk w zabezpieczeniach podłączonych urządzeń przenośnych. Odwiedź tę [stronę,](next-gen-threat-and-vuln-mgt.md) aby dowiedzieć się więcej o tym, Zarządzanie zagrożeniami i lukami programie Microsoft Defender for Endpoint. *W systemie iOS są obsługiwane tylko luki w zabezpieczeniach systemu operacyjnego.*|
|Ujednolicone alerty|Alerty ze wszystkich platform w ujednoliconej konsoli zabezpieczeń M365|
|Dostęp warunkowy, Uruchamianie warunkowe|Blokuje to ryzykowne urządzenia w celu uzyskiwania dostępu do zasobów firmy. Do zasad ochrony aplikacji (MAM) można również dodawać sygnały ryzyka związane z programem Defender for Endpoint|
|Mechanizmy kontroli prywatności. Na podglądzie (patrz uwaga poniżej)|Skonfiguruj prywatność w raportach o zagrożeniach, kontrolując dane wysyłane przez usługę Microsoft Defender for Endpoint. *Pamiętaj, że mechanizmy kontroli prywatności są obecnie dostępne tylko dla zarejestrowanych urządzeń. Kontrolki dla nie zarejestrowanych urządzeń zostaną dodane później*|
|Integracja z Microsoft Tunnel|Może zintegrować Microsoft Tunnel z bramą VPN, aby zapewnić bezpieczeństwo i łączność w jednej aplikacji. Obecnie dostępne tylko w systemie Android|

Wszystkie te funkcje są dostępne dla posiadaczy licencji programu Microsoft Defender dla punktów końcowych. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące licencjonowania](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>Omówienie i wdrażanie

Wdrażanie programu Microsoft Defender dla punktu końcowego na urządzeniach przenośnych można wykonać za pośrednictwem Microsoft Endpoint Manager (MEM). Obejrzyj ten klip wideo, aby szybko oomów możliwości i wdrożenie technologii MTD:

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>Wdrażanie

W poniższej tabeli podsumowano sposób wdrażania programu Microsoft Defender dla punktu końcowego w systemach Android i iOS. Aby uzyskać szczegółową dokumentację, zobacz 
- [Omówienie programu Microsoft Defender dla punktu końcowego w systemie Android](microsoft-defender-endpoint-android.md) oraz
- [Omówienie programu Microsoft Defender dla punktu końcowego w systemie iOS](microsoft-defender-endpoint-ios.md)

**Android**

|Typ rejestracji     |Szczegóły      |
|--------------------|-------------|
|System Android Enterprise z ujednoliconą Endpoint Manager Intune (Microsoft Endpoint Manager)|[Wdrażanie na zarejestrowanych Enterprise Android](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|Administrator urządzenia z ujednoliconą usługą Intune Endpoint Manager (Microsoft Endpoint Manager)|[Wdrażanie na urządzeniach zarejestrowanych przez administratora urządzeń](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|Nieza zarządzanie urządzeniami BYOD OR zarządzanymi przez innych ujednoliconych menedżerów punktów końcowych/ Zasady ochrony aplikacji instalatora (MAM)|[Konfigurowanie sygnałów ryzyka usługi Defender w zasadach ochrony aplikacji (MAM)](android-configure-mam.md)|

**iOS**

|Typ rejestracji     |Szczegóły      |
|--------------------|-------------|
|Urządzenia nadzorowane przy użyciu ujednoliconej Endpoint Manager Intune (Microsoft Endpoint Manager)|1. [Wdrażanie jako aplikacji ze sklepu iOS](ios-install.md)<br/>2. [Konfigurowanie ochrony sieci Web bez połączenia VPN pod nadzorem urządzeń z systemem iOS](ios-install.md#complete-deployment-for-supervised-devices)|
|Niesupervised (BYOD) devices enrolled with Intune UEM (Microsoft Endpoint Manager)|[Wdrażanie jako aplikacji ze sklepu iOS](ios-install.md)|
|Nieza zarządzanie urządzeniami BYOD LUB zarządzanymi przez inne uems/ zasady ochrony aplikacji instalatora (MAM)|[Konfigurowanie sygnałów ryzyka usługi Defender w zasadach ochrony aplikacji (MAM)](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>Dołączanie użytkowników końcowych

- Konfigurowanie tablicy zerowej dotyku dla zarejestrowanych urządzeń z systemem iOS: Administratorzy mogą skonfigurować instalację z zerowej obsługi dotykowej w celu dyskretnego wnosze usługi Microsoft Defender dla punktu końcowego na zarejestrowanych urządzeniach z systemem [iOS](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview) bez konieczności otwierania aplikacji przez użytkownika. 

- [Konfigurowanie dostępu warunkowego](android-configure.md#conditional-access-with-defender-for-endpoint-on-android) w celu wymuszania dołączania użytkowników: Można to zastosować, aby zapewnić użytkownikom końcowym dołączanie do aplikacji Microsoft Defender for Endpoint po wdrożeniu. Obejrzyj ten klip wideo, aby szybko obejrzeć pokaz konfigurowania dostępu warunkowego za pomocą programu Defender do sygnalizowania ryzyka związanego z punktem końcowym. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>Upraszczanie dołączania

- [iOS — Zero-Touch Onboard](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview)
- [System Android Enterprise — konfiguracja zawsze w sieci VPN](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS — automatyczna konfiguracja profilu VPN](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>Ocena pilotażowa

Oceniając obronę przed zagrożeniami na urządzeniach przenośnych za pomocą programu Microsoft Defender dla punktu końcowego, możesz przed przystąpieniem do wdrażania usługi na większym zestawie urządzeń sprawdzić, czy są spełnione określone kryteria. Możesz zdefiniować kryteria wyjścia i upewnić się, że są one odpowiednie przed rozpoczęciem szerokiego wdrażania.

Pomaga to ograniczyć potencjalne problemy, które mogą się pojawić podczas świadczenia usługi. Oto kilka testów i kryteriów wyjścia, które mogą okazać się pomocne:

- Urządzenia są wyświetlane na liście zasobów w spisie urządzeń: Po pomyślnym wkładzie programu Defender for Endpoint na urządzeniu przenośnym sprawdź, czy urządzenie jest wymienione w spisie urządzeń w [konsoli zabezpieczeń](https://security.microsoft.com).

- Uruchom test wykrywania złośliwego oprogramowania na urządzeniu z systemem Android: zainstaluj dowolną aplikację testowa wirusów ze sklepu Google Play i sprawdź, czy jest wykrywana przez program Microsoft Defender for Endpoint. Oto przykładowa aplikacja, która może zostać użyta do tego testu: [Test wirusa](https://play.google.com/store/apps/details?id=com.androidantivirus.testvirus). Pamiętaj, że na Enterprise Android z profilem służbowym jest obsługiwany tylko profil służbowy.

- Uruchom test wyłudzania informacji: Przejdź do tej https://smartscreentestratings2.net usługi i sprawdź, czy jest blokowana przez usługę Microsoft Defender for Endpoint. Pamiętaj, że na Enterprise Android z profilem służbowym jest obsługiwany tylko profil służbowy.

- Alerty są wyświetlane na pulpicie nawigacyjnym. Sprawdź, czy na konsoli zabezpieczeń są wyświetlane alerty dotyczące powyższych [testów wykrywania](https://security.microsoft.com).

## <a name="configure"></a>Konfigurowanie

- [Konfigurowanie funkcji systemu Android](android-configure.md)
- [Konfigurowanie funkcji systemu iOS](ios-configure-features.md)
- [Konfigurowanie ochrony sieci Web bez połączenia VPN pod nadzorowane urządzenia z systemem iOS](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>Zasoby

- [Program Microsoft Defender for Endpoint w systemie Android](microsoft-defender-endpoint-android.md)
- [Program Microsoft Defender for Endpoint w systemie iOS](microsoft-defender-endpoint-ios.md)
- Bądź na bieżąco z informacjami o nadchodzących wersjach, czytając [nasze ogłoszenia](https://aka.ms/mdeblog).

