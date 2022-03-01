---
title: Program Microsoft Defender dla punktu końcowego na komputerze Mac
ms.reviewer: ''
description: Dowiedz się, jak instalować, konfigurować, aktualizować i używać programu Microsoft Defender dla punktu końcowego na komputerze Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, dezinstalacja, intune, jamf, macos, monterey, big sur, catalina, mojave, mde for mac
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 504bed69cb8380d685abfc78abe9c579313c3963
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63026627"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Program Microsoft Defender dla punktu końcowego na komputerze Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W tym temacie opisano, jak zainstalować, skonfigurować, zaktualizować i używać programu Defender dla punktu końcowego na komputerze Mac.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych innych firm wraz z programem Microsoft Defender for Endpoint na komputerze Mac może prowadzić do problemów z wydajnością i nieprzewidywalnych efektów ubocznych. Jeśli ochrona punktu końcowego firmy innym niż Microsoft jest bezwzględnym wymaganiem w Twoim środowisku, nadal możesz bezpiecznie korzystać z usługi Defender for Endpoint na komputerze Mac EDR po skonfigurowaniu funkcji oprogramowania antywirusowego do uruchamiania w trybie [pasywnym](mac-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="whats-new-in-the-latest-release"></a>Co nowego w najnowszej wersji

[Co nowego w programie Microsoft Defender dla punktu końcowego](whats-new-in-microsoft-defender-endpoint.md)

[Co nowego w programie Microsoft Defender dla punktu końcowego na komputerze Mac](mac-whatsnew.md)

> [!TIP]
> Jeśli masz opinię, która chcesz udostępnić, prześlij ją, otwierając program Microsoft Defender for Endpoint na komputerze Mac  \> na urządzeniu i przechodząc do pomocy w wysyłaniu **opinii**.

Aby uzyskać najnowsze funkcje, w tym funkcje wersji Preview (na przykład wykrywanie i reagowanie w punktach końcowych dla urządzeń z systemem Mac), skonfiguruj urządzenie z systemem macOS z programem Microsoft Defender for Endpoint, aby było urządzeniem "Niejawny program testów".

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>Jak zainstalować program Microsoft Defender for Endpoint na komputerze Mac

### <a name="prerequisites"></a>Wymagania wstępne

- Subskrypcja usługi Defender for Endpoint i dostęp do portalu Microsoft 365 Defender sieci Web
- Środowisko początkujących w skryptach macOS i BASH
- Uprawnienia administracyjne na urządzeniu (w przypadku wdrożenia ręcznego)

### <a name="installation-instructions"></a>Instrukcje instalacji

Istnieje kilka metod i narzędzi wdrożeniowych, których można użyć do zainstalowania i skonfigurowania programu Defender dla punktu końcowego na komputerze Mac.

- Narzędzia do zarządzania przez inne firmy:
    - [Microsoft Intune oparte na programie](mac-install-with-intune.md)
    - [Wdrażanie oparte na programie JAMF](mac-install-with-jamf.md)
    - [Inne produkty MDM](mac-install-with-other-mdm.md)

- Narzędzie wiersza polecenia:
    - [Wdrażanie ręczne](mac-install-manually.md)

### <a name="system-requirements"></a>Wymagania systemowe

Obsługiwane są trzy najnowsze wersje główne systemu macOS.

> [!IMPORTANT]
> W systemie macOS 11 (Big Sur) i wyżej program Microsoft Defender for Endpoint wymaga dodatkowych profilów konfiguracji. Jeśli jesteś klientem uaktualniacym z wcześniejszych wersji systemu macOS, upewnij się, że wdrożono dodatkowe profile konfiguracji wymienione w tece Nowe profile konfiguracji systemu [macOS Catalina i nowsze wersje systemu macOS](mac-sysext-policies.md).

- 12 (Monterey), 11 (Big Sur), 10.15 (Catalina)
- Miejsce na dysku: 1 GB

Wersje beta systemu macOS nie są obsługiwane.

Obsługa urządzeń macOS z procesorami opartymi na mikroukładzie M1 została oficjalnie obsługiwana od wersji 101.40.84 agenta.

Po włączeniu usługi może być konieczne skonfigurowanie sieci lub zapory w celu umożliwienia połączeń wychodzących między usługą a punktami końcowymi.

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Program Microsoft Defender for Endpoint na komputerze Mac wymaga jednej z następujących ofert licencjonowania zbiorowego firmy Microsoft:

- Microsoft 365 E5 (M365 E5)
- Zabezpieczenia platformy Microsoft 365 E5
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Ochrona punktu końcowego w usłudze Microsoft Defender

> [!NOTE]
> Uprawnieni licencjonowani użytkownicy mogą używać programu Microsoft Defender for Endpoint na maksymalnie pięciu jednoczesnych urządzeniach.
> Program Microsoft Defender for Endpoint jest również dostępny do zakupu w sklepie Dostawca rozwiązań w chmurze (CSP). W przypadku zakupu za pośrednictwem programu CSP nie wymaga on wymienionych ofert licencjonowania zbiorowego firmy Microsoft.

### <a name="configuring-exclusions"></a>Konfigurowanie wykluczeń

Podczas dodawania wykluczeń warto pamiętać o typowych błędach wykluczeń, które [mogą Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>Połączenia sieciowe

Poniższy arkusz kalkulacyjny zawiera listę usług i skojarzonych z nimi adresów URL, z których sieć musi nawiązać połączenie. Należy upewnić się, że nie ma żadnych reguł zapory lub filtrowania sieci, które odmówią dostępu do tych adresów URL, lub może  być konieczne utworzenie reguły zezwalania przeznaczonej specjalnie dla tych adresów URL.


|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|Lista adresów URL punktu końcowego programu Microsoft Defender dla klientów komercyjnych | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Lista adresów URL programu Microsoft Defender dla punktów końcowych dla klientów GCC/DoD| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|




Program Microsoft Defender for Endpoint może wykryć serwer proxy przy użyciu następujących metod odnajdowania:

- Automatyczne konfiguracja serwera proxy (PAC)
- Protokół automatycznego wykrywania proxy sieci Web (WPAD)
- Ręczna statyczna konfiguracja serwera proxy

Jeśli ruch anonimowy jest blokowany przez serwer proxy lub zaporę, upewnij się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL.

> [!WARNING]
> Uwierzytelnione proxy nie są obsługiwane. Upewnij się, że używany jest tylko PAC, WPAD lub statyczny serwer proxy.
>
> Inspekcja SSL i przechwytywanie serwerów proxy nie są również obsługiwane ze względów bezpieczeństwa. Skonfiguruj wyjątek dla inspekcji SSL i serwera proxy, aby bezpośrednio przekazać dane z programu Microsoft Defender dla punktu końcowego w systemie macOS do odpowiednich adresów URL bez przecięcia. Dodanie certyfikatu odcięcia do magazynu globalnego nie umożliwi przecięcia.

Aby sprawdzić, czy połączenie nie jest zablokowane, otwórz <https://x.cp.wd.microsoft.com/api/report> je i otwórz <https://cdn.x.cp.wd.microsoft.com/ping> w przeglądarce.

Jeśli wolisz wiersz polecenia, możesz również sprawdzić połączenie, uruchamiając następujące polecenie w programie Terminal:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Dane wyjściowe tego polecenia powinny przypominać następujące:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> Zalecamy zachowanie włączonej ochrony [integralności](https://support.apple.com/HT204899) systemu (SIP) na urządzeniach klienckich. SIP to wbudowana funkcja zabezpieczeń systemu macOS, która zapobiega manipulowaniu na niskim poziomie systemu operacyjnego i jest domyślnie włączona.

Po zainstalowaniu programu Microsoft Defender for Endpoint można sprawdzić łączność, uruchamiając następujące polecenie w programie Terminal:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>Jak zaktualizować program Microsoft Defender dla punktu końcowego na komputerze Mac

Firma Microsoft regularnie publikuje aktualizacje oprogramowania w celu zwiększenia wydajności, zabezpieczeń i dostarczania nowych funkcji. Aby zaktualizować program Microsoft Defender for Endpoint na komputerze Mac, używany jest program o nazwie Microsoft AutoUpdate (MAU). Aby dowiedzieć się więcej, zobacz [Wdrażanie aktualizacji programu Microsoft Defender dla punktu końcowego na komputerze Mac](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>Jak skonfigurować program Microsoft Defender dla punktu końcowego na komputerze Mac

Wskazówki dotyczące konfigurowania produktu w środowiskach przedsiębiorstwa można uzyskać w tece Ustawianie preferencji programu [Microsoft Defender dla punktu końcowego na komputerze Mac](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>rozszerzenia systemu i kernel systemu macOS

Razem z rozwojem systemu macOS przygotowujemy program Microsoft Defender for Endpoint w aktualizacji dla komputerów Mac, która korzysta z rozszerzeń systemowych, a nie rozszerzeń kernel. Aby uzyskać odpowiednie szczegóły, [zobacz Co nowego w programie Microsoft Defender dla punktu końcowego na komputerze Mac](mac-whatsnew.md).

## <a name="resources"></a>Zasoby

- Aby uzyskać więcej informacji na temat rejestrowania, odinstalowywania lub innych tematów, zobacz Zasoby dotyczące programu [Microsoft Defender dla punktu końcowego na komputerze Mac](mac-resources.md).
- [Prywatność dla programu Microsoft Defender dla punktu końcowego na komputerze Mac](mac-privacy.md).
