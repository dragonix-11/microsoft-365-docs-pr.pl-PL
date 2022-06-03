---
title: Ochrona punktu końcowego w usłudze Microsoft Defender — Mobile Threat Defense
ms.reviewer: ''
description: Omówienie usługi Mobile Threat Defense w Ochrona punktu końcowego w usłudze Microsoft Defender
keywords: mobile, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, ios, mtd, android, security
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
ms.openlocfilehash: 6df00016658ee8afb703c15b95a969169ab80b41
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872341"
---
# <a name="microsoft-defender-for-endpoint---mobile-threat-defense"></a>Ochrona punktu końcowego w usłudze Microsoft Defender — Mobile Threat Defense

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ochrona punktu końcowego w usłudze Microsoft Defender na Android i iOS jest naszym **rozwiązaniem do ochrony przed zagrożeniami mobilnymi (MTD).** Zazwyczaj firmy aktywnie chronią komputery przed lukami w zabezpieczeniach i atakami, podczas gdy urządzenia przenośne często nie sąmonitorowane i niechronione. W przypadku, gdy platformy mobilne mają wbudowaną ochronę, taką jak izolacja aplikacji i sprawdzone sklepy z aplikacjami konsumenckimi, platformy te pozostają narażone na ataki internetowe lub inne zaawansowane ataki. Ponieważ coraz więcej pracowników korzysta z urządzeń do pracy i uzyskuje dostęp do poufnych informacji, konieczne jest, aby firmy wdrażały rozwiązanie MTD, aby chronić urządzenia i zasoby przed coraz bardziej zaawansowanymi atakami na urządzenia przenośne.

## <a name="key-capabilities"></a>Kluczowe możliwości

Ochrona punktu końcowego w usłudze Microsoft Defender na temat Android i iOS zapewnia poniższe kluczowe możliwości. Aby uzyskać informacje o najnowszych [funkcjach i korzyściach](https://aka.ms/mdeblog), przeczytaj nasze ogłoszenia.

<br>

|Możliwości|Opis|
|---|---|
|Ochrona w Sieci Web|Ochrona przed wyłudzaniem informacji, blokowanie niebezpiecznych połączeń sieciowych i obsługa niestandardowych wskaźników.|
|Ochrona przed złośliwym oprogramowaniem (tylko Android)|Skanowanie w poszukiwaniu złośliwych aplikacji.|
|Wykrywanie jailbreaka (tylko iOS)|Wykrywanie urządzeń ze zdjętymi zabezpieczeniami systemu.|
|Zarządzanie zagrożeniami i lukami w zabezpieczeniach (TVM) |Ocena luk w zabezpieczeniach dołączonych urządzeń przenośnych. Odwiedź tę [stronę](next-gen-threat-and-vuln-mgt.md), aby dowiedzieć się więcej o Zarządzanie zagrożeniami i lukami w Ochrona punktu końcowego w usłudze Microsoft Defender. *Należy pamiętać, że w iOS w tej wersji zapoznawczej są obsługiwane tylko luki w zabezpieczeniach systemu operacyjnego.*|
|Ujednolicone alerty|Alerty ze wszystkich platform w ujednoliconej konsoli zabezpieczeń M365|
|Dostęp warunkowy, uruchamianie warunkowe|Blokowanie uzyskiwania dostępu do zasobów firmowych przez ryzykowne urządzenia. Sygnały o ryzyku usługi Defender for Endpoint można również dodać do zasad ochrony aplikacji (MAM)|
|Mechanizmy kontroli prywatności. W wersji zapoznawczej (patrz uwaga poniżej)|Skonfiguruj prywatność w raportach o zagrożeniach, kontrolując dane wysyłane przez Ochrona punktu końcowego w usłudze Microsoft Defender. *Należy pamiętać, że mechanizmy kontroli prywatności są obecnie dostępne tylko dla zarejestrowanych urządzeń. Kontrolki dla niezarejestrowanych urządzeń zostaną dodane później*|
|Integracja z Microsoft Tunnel|Można zintegrować z Microsoft Tunnel, rozwiązaniem bramy sieci VPN w celu włączenia zabezpieczeń i łączności w jednej aplikacji. Dostępne w Android i jest teraz ogólnie dostępne również w iOS.|

Wszystkie te możliwości są dostępne dla Ochrona punktu końcowego w usłudze Microsoft Defender posiadaczy licencji. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące licencjonowania](minimum-requirements.md#licensing-requirements).


## <a name="overview-and-deploy"></a>Omówienie i wdrażanie

Wdrażanie Ochrona punktu końcowego w usłudze Microsoft Defender na urządzeniach przenośnych można wykonać za pośrednictwem Microsoft Endpoint Manager (MEM). Obejrzyj to wideo, aby zapoznać się z krótkim omówieniem możliwości i wdrożenia usługi MTD:

<br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMpiC]

### <a name="deploy"></a>Wdrażanie

Poniższa tabela zawiera podsumowanie sposobu wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender na Android i iOS. Aby uzyskać szczegółową dokumentację, zobacz 
- [Omówienie Ochrona punktu końcowego w usłudze Microsoft Defender na Android](microsoft-defender-endpoint-android.md) i
- [Omówienie usługi ochrony punktu końcowego w usłudze Microsoft Defender w systemie iOS](microsoft-defender-endpoint-ios.md)

**Android**

|Typ rejestracji     |Szczegóły      |
|--------------------|-------------|
|Android Enterprise z Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|[Wdrażanie na Android Enterprise zarejestrowanych urządzeniach](android-intune.md#deploy-on-android-enterprise-enrolled-devices)|
|Administrator urządzeń z Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|[Wdrażanie na urządzeniach zarejestrowanych przez administratora urządzeń](android-intune.md#deploy-on-device-administrator-enrolled-devices)|
|Niezarządzane urządzenia BYOD LUB zarządzane przez innych menedżerów ujednoliconych punktów końcowych / Konfigurowanie zasad ochrony aplikacji (MAM)|[Konfigurowanie sygnałów ryzyka usługi Defender w zasadach ochrony aplikacji (MAM)](android-configure-mam.md)|

**iOS**

|Typ rejestracji     |Szczegóły      |
|--------------------|-------------|
|Nadzorowane urządzenia z Intune Unified Endpoint Manager (Microsoft Endpoint Manager)|1. [Wdrażanie jako aplikacja ze sklepu iOS](ios-install.md)<br/>2. [Konfigurowanie ochrony sieci Web bez sieci VPN dla urządzeń nadzorowanych iOS](ios-install.md#complete-deployment-for-supervised-devices)|
|Urządzenia nienadzorowane (BYOD) zarejestrowane w Intune UEM (Microsoft Endpoint Manager)|[Wdrażanie jako aplikacja ze sklepu iOS](ios-install.md)|
|Niezarządzane urządzenia BYOD LUB zarządzane przez inne moduły UEM / Konfigurowanie zasad ochrony aplikacji (MAM)|[Konfigurowanie sygnałów ryzyka usługi Defender w zasadach ochrony aplikacji (MAM)](ios-install-unmanaged.md)|

### <a name="end-user-onboarding"></a>Dołączanie użytkowników końcowych

- [Konfigurowanie dołączania zero-touch dla iOS zarejestrowanych urządzeń](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint): administratorzy mogą skonfigurować instalację bezobsługową do dyskretnego dołączania Ochrona punktu końcowego w usłudze Microsoft Defender na zarejestrowanych urządzeniach iOS bez konieczności otwierania aplikacji przez użytkownika. 

- [Skonfiguruj dostęp warunkowy, aby wymusić dołączanie użytkowników](android-configure.md#conditional-access-with-defender-for-endpoint-on-android): można to zastosować w celu zapewnienia, że użytkownicy końcowi dołączą do aplikacji Ochrona punktu końcowego w usłudze Microsoft Defender po wdrożeniu. Obejrzyj ten film wideo, aby zapoznać się z krótkim pokazem konfigurowania dostępu warunkowego przy użyciu sygnałów ryzyka usługi Defender for Endpoint. 

  <br/>

  > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMwR1]

### <a name="simplify-onboarding"></a>Uproszczenie dołączania

- [iOS — dołączanie Zero-Touch](ios-install.md#zero-touch-onboarding-of-microsoft-defender-for-endpoint)
- [Android Enterprise — konfigurowanie zawsze włączonej sieci VPN](android-intune.md#auto-setup-of-always-on-vpn).
- [iOS — automatyczna konfiguracja profilu sieci VPN](ios-install.md#auto-onboarding-of-vpn-profile-simplified-onboarding)

## <a name="pilot-evaluation"></a>Ocena pilotażowa

Podczas oceny ochrony przed zagrożeniami mobilnymi za pomocą Ochrona punktu końcowego w usłudze Microsoft Defender można sprawdzić, czy zostały spełnione określone kryteria przed kontynuowaniem wdrażania usługi na większych urządzeniach. Możesz zdefiniować kryteria zakończenia i upewnić się, że są one spełnione przed szerokim wdrożeniem.

Pomaga to zmniejszyć potencjalne problemy, które mogą wystąpić podczas wdrażania usługi. Oto niektóre testy i kryteria zakończenia, które mogą pomóc:

- Urządzenia są wyświetlane na liście spisu urządzeń: po pomyślnym dołączeniu usługi Defender for Endpoint na urządzeniu przenośnym sprawdź, czy urządzenie znajduje się na liście Spis urządzeń w [konsoli zabezpieczeń](https://security.microsoft.com).

- Uruchom test wykrywania złośliwego oprogramowania na urządzeniu Android: zainstaluj dowolną testową aplikację antywirusową ze sklepu Google Play i sprawdź, czy zostanie wykryta przez Ochrona punktu końcowego w usłudze Microsoft Defender. Oto przykładowa aplikacja, która może być używana do tego testu: [test wirusa](https://play.google.com/store/apps/details?id=com.antivirus&hl=en_US&gl=US). Należy pamiętać, że na Android Enterprise z profilem służbowym obsługiwany jest tylko profil służbowy.

- Uruchom test wyłudzania informacji: przejdź do https://smartscreentestratings2.net strony i sprawdź, czy zostanie on zablokowany przez Ochrona punktu końcowego w usłudze Microsoft Defender. Należy pamiętać, że na Android Enterprise z profilem służbowym obsługiwany jest tylko profil służbowy.

- Alerty są wyświetlane na pulpicie nawigacyjnym: sprawdź, czy alerty dla powyższych testów wykrywania są wyświetlane w [konsoli zabezpieczeń](https://security.microsoft.com).

## <a name="configure"></a>Konfiguruj

- [Konfigurowanie funkcji Android](android-configure.md)
- [Skonfiguruj funkcje systemu iOS](ios-configure-features.md)
- [Konfigurowanie ochrony sieci Web bez sieci VPN dla nadzorowanych urządzeń iOS](ios-install.md#complete-deployment-for-supervised-devices)

## <a name="resources"></a>Zasoby

- [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Android](microsoft-defender-endpoint-android.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender w systemie iOS](microsoft-defender-endpoint-ios.md)
- Bądź na bieżąco z nadchodzącymi wydaniami, czytając nasze [ogłoszenia](https://aka.ms/mdeblog).

