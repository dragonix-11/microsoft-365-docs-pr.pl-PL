---
title: Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac
ms.reviewer: ''
description: Dowiedz się, jak instalować, konfigurować, aktualizować i używać Ochrona punktu końcowego w usłudze Microsoft Defender na komputerach Mac.
keywords: microsoft, defender, Ochrona punktu końcowego w usłudze Microsoft Defender, mac, installation, deploy, uninstallation, intune, jamf, macos, monterey, big sur, catalina, mojave, mde for mac
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
ms.openlocfilehash: d6438c7af3d3dbb8f4b2c19fdfdd04640cc8b4d2
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174974"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

W tym temacie opisano sposób instalowania, konfigurowania, aktualizowania i używania usługi Defender for Endpoint na komputerach Mac.

> [!CAUTION]
> Uruchamianie innych produktów ochrony punktów końcowych innych firm wraz z Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac może prowadzić do problemów z wydajnością i nieprzewidywalnych skutków ubocznych. Jeśli ochrona punktów końcowych innych niż Microsoft jest absolutnym wymaganiem w twoim środowisku, nadal możesz bezpiecznie korzystać z funkcji usługi Defender for Endpoint na komputerach Mac EDR po skonfigurowaniu funkcji antywirusowej do uruchamiania w [trybie pasywnym](mac-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="whats-new-in-the-latest-release"></a>Co nowego w najnowszej wersji

[Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender](whats-new-in-microsoft-defender-endpoint.md)

[Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](mac-whatsnew.md)

> [!TIP]
> Jeśli masz opinię, którą chcesz udostępnić, prześlij ją, otwierając Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac na urządzeniu i przechodząc do **pozycji Pomoc** \> **w wysyłaniu opinii**.

Aby uzyskać najnowsze funkcje, w tym funkcje w wersji zapoznawczej (takie jak wykrywanie i reagowanie w punktach końcowych dla urządzeń z systemem Mac), skonfiguruj urządzenie z systemem macOS z systemem Ochrona punktu końcowego w usłudze Microsoft Defender urządzeniem "Niejawnym testerem".

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>Jak zainstalować Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac

### <a name="prerequisites"></a>Wymagania wstępne

- Subskrypcja usługi Defender for Endpoint i dostęp do portalu Microsoft 365 Defender
- Doświadczenie na poziomie początkującym w skryptach dla systemów macOS i BASH
- Uprawnienia administracyjne na urządzeniu (w przypadku wdrożenia ręcznego)

### <a name="installation-instructions"></a>Instrukcje instalacji

Istnieje kilka metod i narzędzi wdrażania, których można użyć do instalowania i konfigurowania usługi Defender for Endpoint na komputerze Mac.

- Narzędzia do zarządzania innych firm:
    - [Wdrożenie oparte na usłudze Microsoft Intune](mac-install-with-intune.md)
    - [Wdrażanie oparte na narzędziu JAMF](mac-install-with-jamf.md)
    - [Inne produkty MDM](mac-install-with-other-mdm.md)

- Narzędzie wiersza polecenia:
    - [Wdrażanie ręczne](mac-install-manually.md)

### <a name="system-requirements"></a>Wymagania systemowe

Obsługiwane są trzy najnowsze główne wersje systemu macOS.

> [!IMPORTANT]
> W systemie macOS 11 (Big Sur) lub nowszym Ochrona punktu końcowego w usłudze Microsoft Defender wymaga dodatkowych profilów konfiguracji. Jeśli jesteś istniejącym klientem uaktualniającym z wcześniejszych wersji systemu macOS, pamiętaj o wdrożeniu dodatkowych profilów konfiguracji wymienionych w [temacie Nowe profile konfiguracji dla systemu macOS Catalina i nowszych wersji systemu macOS](mac-sysext-policies.md).

- 12 (Monterey), 11 (Big Sur), 10.15 (Catalina)
- Miejsce na dysku: 1 GB

Wersje beta systemu macOS nie są obsługiwane.

Obsługa urządzeń z systemem macOS z procesorami opartymi na mikroukładach M1 jest oficjalnie obsługiwana od wersji 101.40.84 agenta.

Po włączeniu usługi może być konieczne skonfigurowanie sieci lub zapory w celu zezwolenia na połączenia wychodzące między nią a punktami końcowymi.

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac wymaga jednej z następujących ofert licencjonowania zbiorowego firmy Microsoft:

- Microsoft 365 E5 (M365 E5)
- Zabezpieczenia platformy Microsoft 365 E5
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Ochrona punktu końcowego w usłudze Microsoft Defender

> [!NOTE]
> Uprawnieni użytkownicy licencjonowani mogą używać Ochrona punktu końcowego w usłudze Microsoft Defender na maksymalnie pięciu równoczesnych urządzeniach.
> Ochrona punktu końcowego w usłudze Microsoft Defender jest również dostępny do zakupu w Dostawca rozwiązań w chmurze (CSP). Zakupiony za pośrednictwem dostawcy CSP nie wymaga ofert licencjonowania zbiorowego firmy Microsoft wymienionych na liście.

### <a name="configuring-exclusions"></a>Konfigurowanie wykluczeń

Podczas dodawania wykluczeń należy pamiętać o [typowych błędach wykluczania dla Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>Połączenia sieciowe

Poniższy arkusz kalkulacyjny do pobrania zawiera listę usług i skojarzonych z nimi adresów URL, z którymi sieć musi mieć możliwość nawiązania połączenia. Upewnij się, że nie ma reguł filtrowania zapory ani sieci, które odmawiałyby dostępu do tych adresów URL, lub może być konieczne utworzenie reguły *zezwalania* specjalnie dla nich.


|Arkusz kalkulacyjny listy domen| Opis|
|---|---|
|lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender dla klientów komercyjnych| Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów komercyjnych. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| lista adresów URL Ochrona punktu końcowego w usłudze Microsoft Defender gov/GCC/doD | Arkusz kalkulacyjny z określonymi rekordami DNS dla lokalizacji usług, lokalizacji geograficznych i systemu operacyjnego dla klientów Gov/GCC/DoD. <p> [Pobierz arkusz kalkulacyjny tutaj.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Ochrona punktu końcowego w usłudze Microsoft Defender może odnajdywać serwer proxy przy użyciu następujących metod odnajdywania:

- Autokonfigurowanie serwera proxy (PAC)
- Protokół WPAD (Web Proxy Autodiscovery Protocol)
- Ręczna konfiguracja statycznego serwera proxy

Jeśli serwer proxy lub zapora blokuje ruch anonimowy, upewnij się, że ruch anonimowy jest dozwolony we wcześniej wymienionych adresach URL.

> [!WARNING]
> Uwierzytelnione serwery proxy nie są obsługiwane. Upewnij się, że jest używany tylko serwer PAC, WPAD lub statyczny serwer proxy.
>
> Inspekcja protokołu SSL i przechwytywanie serwerów proxy również nie są obsługiwane ze względów bezpieczeństwa. Skonfiguruj wyjątek inspekcji protokołu SSL i serwera proxy w celu bezpośredniego przekazywania danych z Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS do odpowiednich adresów URL bez przechwytywania. Dodanie certyfikatu przechwytywania do magazynu globalnego nie pozwoli na przechwycenie.

Aby sprawdzić, czy połączenie nie jest zablokowane, otwórz <https://x.cp.wd.microsoft.com/api/report> i <https://cdn.x.cp.wd.microsoft.com/ping> w przeglądarce.

Jeśli wolisz wiersz polecenia, możesz również sprawdzić połączenie, uruchamiając następujące polecenie w terminalu:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Dane wyjściowe tego polecenia powinny być podobne do następujących:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> Zalecamy włączenie [ochrony integralności systemu](https://support.apple.com/HT204899) (SIP) na urządzeniach klienckich. SIP to wbudowana funkcja zabezpieczeń systemu macOS, która zapobiega naruszeniom systemu operacyjnego na niskim poziomie i jest domyślnie włączona.

Po zainstalowaniu Ochrona punktu końcowego w usłudze Microsoft Defender łączność można zweryfikować, uruchamiając następujące polecenie w terminalu:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>Jak zaktualizować Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac

Firma Microsoft regularnie publikuje aktualizacje oprogramowania w celu zwiększenia wydajności, bezpieczeństwa i dostarczania nowych funkcji. Aby zaktualizować Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac, jest używany program o nazwie Microsoft AutoUpdate (MAU). Aby dowiedzieć się więcej, zobacz [Wdrażanie aktualizacji dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>Jak skonfigurować Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac

Wskazówki dotyczące konfigurowania produktu w środowiskach przedsiębiorstwa są dostępne w [temacie Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerach Mac](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>Jądro systemu macOS i rozszerzenia systemowe

Począwszy od systemu macOS 11 (Big Sur), Ochrona punktu końcowego w usłudze Microsoft Defender została w pełni zmigrowana z rozszerzenia jądra do rozszerzeń systemu. Rozszerzenie jądra jest nadal używane w systemie macOS 10.15 (Catalina).

## <a name="resources"></a>Zasoby

- Aby uzyskać więcej informacji na temat rejestrowania, odinstalowywania lub innych tematów, zobacz [Zasoby dla Ochrona punktu końcowego w usłudze Microsoft Defender na komputerach Mac](mac-resources.md).
- [Prywatność Ochrona punktu końcowego w usłudze Microsoft Defender na komputerach Mac](mac-privacy.md).
