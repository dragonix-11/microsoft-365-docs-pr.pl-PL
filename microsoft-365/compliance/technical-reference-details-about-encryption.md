---
title: Informacje techniczne dotyczące szyfrowania
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
- Strat_O365_IP
search.appverid:
- MET150
- MOE150
ms.assetid: 862cbe93-4268-4ef9-ba79-277545ecf221
description: Poznaj różne certyfikaty, technologie i pakiety szyfrowania TLS (Transport Layer Security) używane do szyfrowania w usługach Office 365 i Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6b5df1f9e983ab2e8add09b50c2dfbd30dc1243e
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2021
ms.locfileid: "62996399"
---
# <a name="technical-reference-details-about-encryption"></a>Informacje techniczne dotyczące szyfrowania

Zapoznaj się z tym artykułem, aby dowiedzieć się więcej o certyfikatach, technologiach i kluczach szyfrowania TLS używanych do szyfrowania w [Office 365](encryption.md). Ten artykuł zawiera również szczegółowe informacje na temat planowanych dezpedywacji.
  
- Jeśli szukasz informacji przeglądowych, zobacz Szyfrowanie w [programie Office 365](encryption.md).
- Jeśli szukasz informacji o konfiguracji, zobacz [Konfigurowanie szyfrowania w programie Office 365 Enterprise](set-up-encryption.md).
- Aby uzyskać informacje na temat pakietów szyfrowania obsługiwanych w określonych wersjach programu Windows, zobacz [Pakiety Cipher Suites w protokołach TLS/SSL (Dolowe SSP).](/windows/desktop/SecAuthN/cipher-suites-in-schannel)

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Microsoft Office 365 i zarządzanie certyfikatem

Nie musisz kupować ani konserwować certyfikatów dla Office 365. Zamiast tego Office 365 z własnych certyfikatów.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>Bieżące standardy szyfrowania i planowane czasy planowanego dezpretowania

Aby zapewnić najlepsze w swojej klasie szyfrowanie, Office 365 regularnie sprawdza obsługiwane standardy szyfrowania. Czasami stare standardy są przestarzałe, gdy stają się nieaktualne i mniej bezpieczne. W tym artykule opisano obecnie obsługiwane pakiety szyfrowania oraz inne standardy i szczegóły dotyczące planowanych dezpekwacji.

## <a name="fips-compliance-for-office-365"></a>Zgodność FIPS dla sieci Office 365

Wszystkie pakiety szyfrowania obsługiwane przez Office 365 algorytmów akceptowanych przez fips 140-2. Office 365 dziedziczy sprawdzanie poprawności FIPS po Windows (za pośrednictwem Oprogramowaniannel). Aby uzyskać informacje na temat Oprogramowaniannel, zobacz [Pakiety Cipher Suites w protokołach TLS/SSL (Oprogramowaniannel SSP)](/windows/desktop/SecAuthN/cipher-suites-in-schannel).
  
## <a name="versions-of-tls-supported-by-office-365"></a>Wersje TLS obsługiwane przez Office 365

TLS i SSL (wcześniej TLS) to protokoły kryptograficzne, które zabezpieczają komunikację przez sieć przy użyciu certyfikatów zabezpieczeń w celu zaszyfrowania połączenia między komputerami. Office 365 obsługuje TLS w wersji 1.2 (TLS 1.2).

Niektóre usługi są obsługiwane przez usługę TLS w wersji 1.3 (TLS 1.3).

> [!IMPORTANT]
> Należy pamiętać, że wersje TLS przestarzałe i że przestarzałe wersje  nie powinny być używane, gdy są dostępne nowsze wersje. Jeśli starsze usługi nie wymagają usługi TLS 1.0 lub 1.1, należy je wyłączyć.
  
## <a name="support-for-tls-10-and-11-deprecation"></a>Obsługa cofania 1.0 i 1.1 TLS

Office 365 31 października 2018 r. przestała obsługiwać TLS 1.0 i 1.1. Zakończyliśmy wyłączanie TLS 1.0 i 1.1 w GCC środowiskach Wysokie i DoD. Od 15 października 2020 r. zaczęliśmy wyłączać środowiska TLS 1.0 i 1.1 dla środowisk worldwide i GCC, a następnie będą one nadal będą pojawiać się w następnych tygodniach i miesiącach.

Aby zapewnić bezpieczne połączenie z usługami Office 365 i Microsoft 365, wszystkie kombinacje klient-serwer i serwer przeglądarki używają szyfrowania TLS 1.2 i nowoczesnych pakietów szyfrowania. Należy zaktualizować określone kombinacje typu klient-serwer i przeglądarka-serwer. Aby uzyskać informacje o tym, jaki wpływ na Ciebie ma ta zmiana, zobacz Przygotowanie do obowiązkowego użycia [TLS 1.2 w Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
  
## <a name="deprecating-support-for-3des"></a>Zaniechanie obsługi 3DES

Od 31 października 2018 r. Office 365 nie obsługuje już pakietów szyfrowania 3DES do komunikacji z Office 365. Dokładniej mówiąc, Office 365 już nie obsługuje pakietu TLS_RSA_WITH_3DES_EDE_CBC_SHA cipher suite. Od 28 lutego 2019 r. ten pakiet szyfrowania został wyłączony w Office 365. Klienci i serwery komunikują się z Office 365 muszą obsługiwać co najmniej jeden z obsługiwanych szyfrów. Aby uzyskać listę obsługiwanych szyfrowania, zobacz Pakiety szyfrowania [TLS obsługiwane przez Office 365](#tls-cipher-suites-supported-by-office-365).
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>Zaniechanie obsługi certyfikatu SHA-1 w programie Office 365

Od czerwca 2016 r. Office 365 nie przyjmuje już certyfikatu SHA-1 dla połączeń wychodzących i przychodzących. Użyj algorytmu SHA-2 (Secure Hash Algorithm 2) lub silniejszego algorytmu skrótów w łańcuchu certyfikatów.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>Pakiety szyfrowania TLS obsługiwane przez Office 365

Szyfrowanie TLS *używa pakietów szyfrowania*, kolekcji algorytmów szyfrowania, do ustanawiania bezpiecznych połączeń. Office 365 obsługuje pakiety szyfrowania wymienione w poniższej tabeli. W tabeli znajduje się lista pakietów cipher w kolejności siły z najsilniejszym pakietem cipher na liście jako pierwsza.

Office 365 odpowie na żądanie połączenia, próbując nawiązać połączenie przy użyciu najbezpieczniejszego pakietu cipher. Jeśli połączenie nie działa, spróbuje Office 365 drugiego najbezpieczniejszego pakietu cipher na liście i tak dalej. Usługa będzie kontynuować listę do momentu zaakceptowania połączenia. Podobnie, Office 365 żąda połączenia, usługa odbieraca wybiera, czy ma być używany szyfrowanie TLS i który pakiet szyfrowania ma być używany.

| Nazwa pakietu Cipher | Algorytm/siłę wymiany klucza | Przesyłanie dalej secrecy | Cipher/strength | Algorytm/siłę uwierzytelniania |
|:-----|:-----|:-----|:-----|:-----|
| TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384  <br/> | ECDH/192  <br/> | Tak  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256  <br/> | ECDH/128  <br/> | Tak  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384  <br/> | ECDH/192  <br/> | Tak  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256  <br/> | ECDH/128  <br/> | Tak  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA     <br/> | ECDH/192  <br/> | Tak  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA     <br/> | ECDH/128  <br/> | Tak  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_256_GCM_SHA384        <br/> | RSA/112   <br/> | Nie   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_128_GCM_SHA256        <br/> | RSA/112   <br/> | Nie   <br/> | AES/256  <br/> | RSA/112  <br/> |

Następujące pakiety szyfrowania obsługiwane są przez protokoły TLS 1.0 i 1.1 do momentu ich zakończenia. W GCC do aplikacji High and DoD, w których data zakończenia to 15 stycznia 2020 r. W przypadku środowisk GCC środowiskach danych data to 15 października 2020 r.

| Protokoły | Nazwa pakietu Cipher | Algorytm/siłę wymiany klucza | Przesyłanie dalej secrecy | Cipher/strength | Algorytm/siłę uwierzytelniania | 
|:-----|:-----|:-----|:-----|:-----|:-----|
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA  <br/> | ECDH/192  <br/> | Tak  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA  <br/> | ECDH/128  <br/> | Tak  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA        <br/> | RSA/112   <br/> | Nie   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA        <br/> | RSA/112   <br/> | Nie   <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA256     <br/> | RSA/112   <br/> | Nie   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA256     <br/> | RSA/112   <br/> | Nie   <br/> | AES/256  <br/> | RSA/112  <br/> |

Niektóre Office 365 (w tym Microsoft Teams) korzystają z systemu [Azure Front Door](/azure/frontdoor/front-door-overview), aby zamykać połączenia TLS i wydajnie rozsyłać ruch sieciowy. Aby można było pomyślnie łączyć się z tymi produktami, musi być włączony co najmniej jeden z pakietów szyfrowania obsługiwanych przez system [Azure Front Door przez TLS 1.2](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-) . W Windows 10 i w powyższych przypadkach zalecamy włączenie jednego lub obu pakietów cipher ECDHE w celu lepszej zabezpieczeń. Windows 7, 8 i 8.1 nie są zgodne z pakietami do szyfrowania ECDHE bramy Azure Front Door, a pakiety ciphere DHE zostały dostarczone w celu zapewnienia zgodności z tymi systemami operacyjnymi.

## <a name="related-articles"></a>Artykuły pokrewne

[Pakiety TLS Cipher Suites Windows 10 wersji 1903](/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[Szyfrowanie w Office 365](encryption.md)
  
[Konfigurowanie szyfrowania w Office 365 Enterprise](set-up-encryption.md)
  
[Implementacja oprogramowania TLS 1.0 w Windows aktualizacji stanu zabezpieczeń: 24 listopada 2015 r.](https://support.microsoft.com/kb/3117336)
  
[Udoskonalenia kryptograficzne protokołu TLS/SSL (Windows centrum IT)](/previous-versions/windows/it-pro/windows-vista/cc766285(v=ws.10))
  
[Przygotowanie do protokołu TLS 1.2 w usłudze Office 365 i usłudze Office 365 GCC](/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)

[Jakie są bieżące pakiety szyfrowania obsługiwane przez system Azure Front Door?](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-)
