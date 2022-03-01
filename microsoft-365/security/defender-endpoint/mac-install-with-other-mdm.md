---
title: Wdrożenie z innym systemem zarządzania urządzeniami przenośnymi dla programu Microsoft Defender dla punktu końcowego na komputerze Mac
description: Zainstaluj program Microsoft Defender for Endpoint na komputerze Mac na innych rozwiązaniach zarządzania.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: c8ffab850302967b9e36e841bf035cef07ad2775
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011935"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>Wdrożenie z innym systemem zarządzania urządzeniami przenośnymi (MDM) dla programu Microsoft Defender for Endpoint w systemie macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Wymagania wstępne i wymagania systemowe

Przed rozpoczęciem zapoznaj się z główną stroną programu [Microsoft Defender for Endpoint na stronie macOS](microsoft-defender-endpoint-mac.md) , aby uzyskać opis wymagań wstępnych i wymagań systemowych bieżącej wersji oprogramowania.


## <a name="approach"></a>Podejście

> [!CAUTION]

> Obecnie firma Microsoft oficjalnie obsługuje tylko usługi Intune i JAMF w zakresie wdrażania i zarządzania programem Microsoft Defender for Endpoint w systemie macOS. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, w odniesieniu do podanych poniżej informacji.

Jeśli Twoja organizacja korzysta z rozwiązania MDM (Mobile Device Management), które nie jest oficjalnie obsługiwane, nie oznacza to, że nie możesz wdrożyć ani uruchomić programu Microsoft Defender for Endpoint w systemie macOS.

Program Microsoft Defender for Endpoint w systemie macOS nie zależy od jakichkolwiek funkcji specyficznych dla dostawcy. Można go używać z dowolnym rozwiązaniem MDM, które obsługuje następujące funkcje:

- Wdąż na urządzenia zarządzane w systemie macOS .pkg.
- Wdeksuj profile konfiguracji systemu macOS na urządzeniach zarządzanych.
- Na zarządzanych urządzeniach uruchom dowolnego narzędzia lub skrypty skonfigurowane przez administratora.

Większość nowoczesnych rozwiązań MDM zawiera te funkcje, jednak mogą one nazywać je inaczej.

Usługę Defender dla punktu końcowego można wdrożyć bez ostatniego wymagania z powyższej listy, jednak:

- Nie będzie można zbierać stanu w scentralizowany sposób.
- Jeśli zdecydujesz się odinstalować usługę Defender for Endpoint, musisz zalogować się na urządzeniu klienckim lokalnie jako administrator.

## <a name="deployment"></a>Wdrożenie

Większość rozwiązań MDM używa tego samego modelu do zarządzania urządzeniami z systemem macOS i jest w nim stosowana podobna terminologia. Używanie [wdrożenia opartego na pliku JAMF](mac-install-with-jamf.md) jako szablonu.

### <a name="package"></a>Pakiet

Skonfiguruj wdrożenie [wymaganego pakietu aplikacji](mac-install-with-jamf.md) przy użyciu pakietu instalacyjnego (wdav.pkg) pobranego [z Microsoft 365 Defender sieci Web](mac-install-with-jamf.md).

Aby wdrożyć pakiet w przedsiębiorstwie, skorzystaj z instrukcji skojarzonych z rozwiązaniem MDM.

### <a name="license-settings"></a>Ustawienia licencji

Konfigurowanie [profilu konfiguracji systemu](mac-install-with-jamf.md). 

Rozwiązanie MDM może przypominać "Niestandardowy profil Ustawienia", ponieważ program Microsoft Defender for Endpoint w systemie macOS nie jest częścią systemu macOS.

Użyj listy właściwości, jamf/WindowsDefenderATPOnboarding.plist, która może zostać wyodrębniona z pakietu dołączania pobranego z Microsoft 365 Defender [portal.](mac-install-with-jamf.md)
Twój system może obsługiwać dowolną listę właściwości w formacie XML. W takim przypadku możesz przekazać plik jamf/WindowsDefenderATPOnboarding.plist bez użycia.
Ewentualnie może być konieczne najpierw przekonwertowanie listy właściwości na inny format.

Zazwyczaj profil niestandardowy ma identyfikator, nazwę lub atrybut domeny. Dla tej wartości należy dokładnie użyć wartości "com.microsoft.wdav.atp".
Mdm używa go do wdrażania pliku ustawień w bibliotece/preferencjach zarządzanych **/com.microsoft.wdav.atp.plist** na urządzeniu klienckim, a program Defender for Endpoint używa tego pliku do ładowania informacji o dołączaniu.

### <a name="kernel-extension-policy"></a>Zasady rozszerzenia Kernel

Skonfiguruj zasady rozszerzenia KEXT lub kernel. Użyj identyfikatora **zespołu UBF8T346G9** , aby zezwolić na rozszerzenia kernelów udostępniane przez firmę Microsoft.

> [!CAUTION]
> Jeśli Twoje środowisko składa się z urządzeń firmy Apple Silicon (M1), te komputery nie powinny otrzymywać profilów konfiguracji za pomocą zasad KEXT.
> Firma Apple nie obsługuje programu KEXT na tych komputerach, wdrożenie takiego profilu może się nie powieść na komputerach M1.

### <a name="system-extension-policy"></a>Zasady rozszerzenia systemu

Skonfiguruj zasady rozszerzenia systemu. Użyj identyfikatora **zespołu UBF8T346G9** i zatwierdź następujące identyfikatory pakietów:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Zasady pełnego dostępu do dysku

Przyznaj pełny dostęp dyskowy do następujących składników:

- Ochrona punktu końcowego w usłudze Microsoft Defender
    - Identyfikator: `com.microsoft.wdav`
    - Typ identyfikatora: Identyfikator pakietu
    - Wymaganie kodu: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- Microsoft Defender for Endpoint Security Extension
    - Identyfikator: `com.microsoft.wdav.epsext`
    - Typ identyfikatora: Identyfikator pakietu
    - Wymaganie kodu: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Zasady rozszerzenia sieci

W ramach funkcji wykrywania punktu końcowego i odpowiedzi usługa Microsoft Defender for Endpoint w systemie macOS sprawdza ruch sieciowy i raportuje te informacje w portalu usługi Microsoft 365 Defender sieci. Poniższe zasady pozwalają na korzystanie z tej funkcji przez rozszerzenie sieci.

- Typ filtru: Wtyczka
- Identyfikator pakietu wtyczki: `com.microsoft.wdav`
- Identyfikator pakietu dostawcy danych filtru: `com.microsoft.wdav.netext`
- Filtruj dostawcę danych, który ma być wymagany: `identifier "com.microsoft.wdav.tunnelext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Filtruj sockets. `true`

## <a name="check-installation-status"></a>Sprawdzanie stanu instalacji

Uruchom [program Microsoft Defender for Endpoint](mac-install-with-jamf.md) na urządzeniu klienckim, aby sprawdzić stan dołączania.
