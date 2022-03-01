---
title: Tworzenie wskaźników adresów IP oraz adresów URL/domen
ms.reviewer: ''
description: Tworzenie wskaźników adresów IP oraz adresów URL/domen definiujące wykrywanie, zapobieganie i wykluczenie jednostek.
keywords: ip, url, domain, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8865bf2138947238980b533b8b47ee9663fd5448
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013278"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>Tworzenie wskaźników adresów IP oraz adresów URL/domen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Program Defender for Endpoint może zablokować to, co firma Microsoft może określić jako złośliwe adresy IP/adresy URL, za pośrednictwem filtru Windows Defender SmartScreen dla przeglądarek firmy Microsoft oraz za pośrednictwem filtru Network Protection dla przeglądarek innych niż firma Microsoft lub połączeń wykonanych poza przeglądarką.

Zestaw danych analizy zagrożeń dla tego tematu jest zarządzany przez firmę Microsoft.

Tworząc wskaźniki adresów IP i adresów URL lub domen, można teraz zezwalać na adresy IP, adresy URL lub domeny lub blokować je na podstawie własnej analizy zagrożeń. Możesz również ostrzegać użytkowników z monitem, jeśli otwierają oni ryzykowną aplikację. Monit nie spowoduje zatrzymania korzystania z aplikacji, ale możesz podać niestandardowy komunikat i linki do strony firmy opisujące odpowiednie użycie aplikacji. Użytkownicy nadal mogą pominąć ostrzeżenie i w razie potrzeby nadal korzystać z aplikacji.

Możesz to zrobić za pośrednictwem strony ustawień lub grup komputerowych, jeśli określone grupy są bardziej lub mniej ryzykowne od innych.

> [!NOTE]
> Notacja CIDR (Classless Inter-Domain routingu adresów IP) nie jest obsługiwana.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed utworzeniem wskaźników dla adresów IP, adresów URL lub domen należy poznać następujące wymagania wstępne:

- Zezwalanie na adresy URL/IP i blokowanie opiera się na składniku Ochrona sieci defender for Endpoint w celu umożliwienia dostępu w trybie blokowania. Aby uzyskać więcej informacji na temat ochrony sieci i instrukcji dotyczących konfiguracji, zobacz [Włączanie ochrony sieci](enable-network-protection.md).
- Wersja klienta ochrony przed złośliwym oprogramowaniem musi mieć wersję 4.18.1906.x lub nowszą. 
- Obsługiwane na komputerach z Windows 10, wersja 1709 lub nowsza, Windows 11, Windows Server 2016, Windows Server 2012 R2, Windows Server 2019 i Windows Server 2022.

    > [!NOTE]
    > Windows Server 2016 i Windows Server 2012 R2 muszą zostać naniesone zgodnie z instrukcjami podanymi w te sposób: Windows [onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała.

- Upewnij się **, że w funkcjach zaawansowanych** włączono  \> niestandardowe Microsoft 365 Defender **Ustawienia** \> **sieci**. Aby uzyskać więcej informacji, zobacz [Funkcje zaawansowane](advanced-features.md).
- Aby uzyskać informacje na temat obsługi wskaźników w systemie iOS, [zobacz Konfigurowanie wskaźników niestandardowych](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).

> [!IMPORTANT]
> Do listy wskaźników można dodawać tylko zewnętrzne wiadomości IP. Nie można tworzyć wskaźników dla wewnętrznych ip.
> W przypadku scenariuszy ochrony sieci Web zalecamy używanie wbudowanych funkcji w programie Microsoft Edge. Microsoft Edge usługi [Network Protection do sprawdzania](network-protection.md) ruchu w sieci i umożliwia blokowanie protokołów TCP, HTTP i HTTPS (TLS).
> W przypadku konfliktu zasad wskaźników adresu URL stosowana jest dłuższa ścieżka. Na przykład zasady wskaźnika adresu `https://support.microsoft.com/office` URL mają pierwszeństwo przed zasadami wskaźnika adresu URL `https://support.microsoft.com`.

> [!NOTE]
> W przypadku wszystkich innych procesów scenariusze ochrony sieci Web wykorzystują ochronę sieci do inspekcji i wymuszania:
>
> - Protokół IP jest obsługiwany dla wszystkich trzech protokołów
> - Obsługiwane są tylko pojedyncze adresy IP (nie są obsługiwane bloki CIDR ani zakresy adresów IP)
> - Zaszyfrowane adresy URL (pełna ścieżka) można blokować tylko w przeglądarkach innych firm (Internet Explorer, Microsoft Edge)
> - Zaszyfrowane adresy URL (tylko nazwa FQDN) mogą być blokowane poza przeglądarkami innych firm (Internet Explorer, Microsoft Edge)
> - Pełne bloki ścieżki adresu URL można stosować na poziomie domeny i wszystkich nieszyfrowanych adresów URL
>
> Czas oczekiwania może być do 2 godzin (zazwyczaj krótszy) między czasem działań a zablokowaniem adresu URL i IP.

W trybie ostrzegania można skonfigurować następujące kontrolki:

**Możliwość obejścia**:

- Przycisk Zezwalaj w programie Edge
- Przycisk Zezwalaj w menu toastu (przeglądarki inne niż firmy Microsoft)
- Parametr czasu trwania obejścia na wskaźniku
- Pomijanie wymuszania w przeglądarkach firmy Microsoft i innych niż firma Microsoft

**Przekieruj adres URL**:

- Redirect URL parameter on the indicator
- Redirect URL in Edge
- Przekierowanie adresu URL w wyskakującej witrynie (przeglądarki inne niż firmy Microsoft)

Aby uzyskać więcej informacji, zobacz [Reguluj aplikacje odkryte przez program Microsoft Defender for Endpoint](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Tworzenie wskaźnika adresów IP, adresów URL lub domen na stronie ustawień

1. W okienku nawigacji wybierz pozycję Wskaźnik **Ustawienia** \> **punktów** \> **końcowych** (w obszarze **Reguły**).

2. Wybierz **kartę Adresy IP lub adresy URL/domeny** .

3. Wybierz **pozycję Dodaj element**.

4. Określ następujące szczegóły:
   - Wskaźnik — określ szczegóły jednostki i zdefiniuj wygasanie wskaźnika.
   - Akcja — określ akcję, która ma zostać wykonane, i podaj opis.
   - Zakres — definiowanie zakresu grupy maszyn.

5. Przejrzyj szczegóły na karcie Podsumowanie, a następnie kliknij przycisk **Zapisz**.

## <a name="related-topics"></a>Tematy pokrewne

- [Tworzenie wskaźników](manage-indicators.md)
- [Tworzenie wskaźników dla plików](indicator-file.md)
- [Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md)
- [Zarządzanie wskaźnikami](indicator-manage.md)
