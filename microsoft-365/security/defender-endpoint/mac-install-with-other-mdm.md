---
title: Wdrażanie przy użyciu innego systemu Zarządzanie urządzeniami mobilnego (MDM) dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac
description: Zainstaluj Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac w innych rozwiązaniach do zarządzania.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, instalacja, wdrażanie, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: mavel
author: maximvelichko
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2fa64ee9822fe1f784788e2d1ead79e66eb200ef
ms.sourcegitcommit: 2d870e06e87b10d9e8ec7a7a8381353bc3bc59c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65349740"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>Wdrażanie przy użyciu innego systemu Zarządzanie urządzeniami mobilnego (MDM) dla Ochrona punktu końcowego w usłudze Microsoft Defender na macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zapoznaj się z [głównym Ochrona punktu końcowego w usłudze Microsoft Defender na stronie macOS](microsoft-defender-endpoint-mac.md), aby zapoznać się z opisem wymagań wstępnych i wymagań systemowych dotyczących bieżącej wersji oprogramowania.


## <a name="approach"></a>Podejście

> [!CAUTION]

> Obecnie firma Microsoft oficjalnie obsługuje tylko Intune i JAMF na potrzeby wdrażania Ochrona punktu końcowego w usłudze Microsoft Defender i zarządzania nimi na macOS. Firma Microsoft nie udziela żadnych gwarancji, wyraźnych ani dorozumianych, w odniesieniu do informacji podanych poniżej.

Jeśli Twoja organizacja korzysta z rozwiązania mobile Zarządzanie urządzeniami (MDM), które nie jest oficjalnie obsługiwane, nie oznacza to, że nie możesz wdrożyć ani uruchomić Ochrona punktu końcowego w usłudze Microsoft Defender na macOS.

Ochrona punktu końcowego w usłudze Microsoft Defender na macOS nie zależy od żadnych funkcji specyficznych dla dostawcy. Może być używany z dowolnym rozwiązaniem MDM, które obsługuje następujące funkcje:

- Wdrażanie macOS .pkg na zarządzanych urządzeniach.
- Wdrażanie profilów konfiguracji systemu macOS na urządzeniach zarządzanych.
- Uruchamianie dowolnego narzędzia/skryptu skonfigurowanego przez administratora na urządzeniach zarządzanych.

Większość nowoczesnych rozwiązań MDM obejmuje te funkcje, jednak mogą one wywoływać je inaczej.

Można jednak wdrożyć usługę Defender for Endpoint bez ostatniego wymagania z poprzedniej listy:

- Nie będzie można zbierać stanu w scentralizowany sposób.
- Jeśli zdecydujesz się odinstalować usługę Defender for Endpoint, musisz zalogować się lokalnie na urządzeniu klienckim jako administrator.

## <a name="deployment"></a>Wdrożenie

Większość rozwiązań MDM używa tego samego modelu do zarządzania urządzeniami macOS z podobną terminologią. Użyj [wdrożenia opartego na narzędziu JAMF](mac-install-with-jamf.md) jako szablonu.

### <a name="package"></a>Pakiet

Skonfiguruj wdrożenie [wymaganego pakietu aplikacji](mac-install-with-jamf.md) z pakietem instalacyjnym (wdav.pkg) pobranym z [portalu Microsoft 365 Defender](mac-install-with-jamf.md).

Aby wdrożyć pakiet w przedsiębiorstwie, skorzystaj z instrukcji skojarzonych z rozwiązaniem MDM.

### <a name="license-settings"></a>Ustawienia licencji

[Skonfiguruj profil konfiguracji systemu](mac-install-with-jamf.md). 

Rozwiązanie MDM może nazywać je "profilem niestandardowym Ustawienia", ponieważ Ochrona punktu końcowego w usłudze Microsoft Defender na macOS nie jest częścią macOS.

Użyj listy właściwości jamf/WindowsDefenderATPOnboarding.plist, którą można wyodrębnić z pakietu dołączania pobranego z [portalu Microsoft 365 Defender](mac-install-with-jamf.md).
System może obsługiwać dowolną listę właściwości w formacie XML. Plik jamf/WindowsDefenderATPOnboarding.plist można przekazać w takim przypadku.
Alternatywnie może wymagać najpierw przekonwertowania listy właściwości na inny format.

Zazwyczaj profil niestandardowy ma identyfikator, nazwę lub atrybut domeny. Dla tej wartości należy użyć dokładnie "com.microsoft.wdav.atp".
Rozwiązanie MDM używa go do wdrożenia pliku ustawień w **pliku /Library/Managed Preferences/com.microsoft.wdav.atp.plist** na urządzeniu klienckim, a usługa Defender for Endpoint używa tego pliku do ładowania informacji o dołączaniu.

### <a name="kernel-extension-policy"></a>Zasady rozszerzenia jądra

Skonfiguruj zasady rozszerzenia KEXT lub jądra. Użyj identyfikatora zespołu **UBF8T346G9** , aby zezwolić na rozszerzenia jądra udostępniane przez firmę Microsoft.

> [!CAUTION]
> Jeśli środowisko składa się z urządzeń z systemem Apple Silicon (M1), te maszyny nie powinny otrzymywać profilów konfiguracji z zasadami KEXT.
> Firma Apple nie obsługuje rozwiązania KEXT na tych maszynach. Wdrożenie takiego profilu nie powiedzie się na maszynach M1.

### <a name="system-extension-policy"></a>Zasady rozszerzenia systemu

Skonfiguruj zasady rozszerzenia systemu. Użyj identyfikatora zespołu **UBF8T346G9** i zatwierdź następujące identyfikatory pakietów:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Zasady dostępu do pełnego dysku

Udziel pełnego dostępu do dysku następującym składnikom:

- Ochrona punktu końcowego w usłudze Microsoft Defender
    - Identyfikator: `com.microsoft.wdav`
    - Typ identyfikatora: identyfikator pakietu
    - Wymaganie dotyczące kodu: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- rozszerzenie zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender
    - Identyfikator: `com.microsoft.wdav.epsext`
    - Typ identyfikatora: identyfikator pakietu
    - Wymaganie dotyczące kodu: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Zasady rozszerzenia sieci

W ramach funkcji wykrywania punktów końcowych i reagowania Ochrona punktu końcowego w usłudze Microsoft Defender na macOS sprawdza ruch gniazd i zgłasza te informacje do portalu Microsoft 365 Defender. Poniższe zasady umożliwiają rozszerzeniu sieci wykonywanie tej funkcji.

- Typ filtru: wtyczka
- Identyfikator pakietu wtyczki: `com.microsoft.wdav`
- Identyfikator pakietu dostawcy danych filtru: `com.microsoft.wdav.netext`
- Wymaganie wyznaczone przez dostawcę danych filtrowania: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Gniazda filtru: `true`

## <a name="check-installation-status"></a>Sprawdzanie stanu instalacji

Uruchom [Ochrona punktu końcowego w usłudze Microsoft Defender](mac-install-with-jamf.md) na urządzeniu klienckim, aby sprawdzić stan dołączania.
