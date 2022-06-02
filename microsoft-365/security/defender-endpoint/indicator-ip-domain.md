---
title: Utwórz wskaźniki adresów IP i adresów URL/domen
ms.reviewer: ''
description: Utwórz wskaźniki adresów IP i adresów URL/domen, które definiują wykrywanie, zapobieganie i wykluczanie jednostek.
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
ms.openlocfilehash: 955f11aa44bd0defb867c25124da7c5a3769c98d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840123"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>Utwórz wskaźniki adresów IP i adresów URL/domen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Usługa Defender for Endpoint może blokować to, co firma Microsoft uważa za złośliwe adresy IP/adresy URL, za pośrednictwem Windows Defender filtru SmartScreen dla przeglądarek firmy Microsoft oraz za pośrednictwem ochrony sieci dla przeglądarek lub wywołań innych niż Microsoft wykonanych poza przeglądarką.

Zestaw danych analizy zagrożeń został zarządzany przez firmę Microsoft.

Tworząc wskaźniki dla adresów IP, adresów URL lub domen, możesz teraz zezwalać na adresy IP, adresy URL lub domeny albo blokować je na podstawie własnej analizy zagrożeń. Możesz również ostrzec użytkowników za pomocą monitu, jeśli otworzą ryzykowną aplikację. Monit nie uniemożliwi korzystania z aplikacji, ale możesz podać niestandardowy komunikat i linki do strony firmowej opisującej odpowiednie użycie aplikacji. Użytkownicy nadal mogą pominąć ostrzeżenie i nadal korzystać z aplikacji, jeśli zajdzie taka potrzeba.

Można to zrobić za pośrednictwem strony ustawień lub grup maszyn, jeśli uważasz, że niektóre grupy są bardziej lub mniej zagrożone niż inne.

> [!NOTE]
> Bezklasowa notacja routingu Inter-Domain (CIDR) dla adresów IP nie jest obsługiwana.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed utworzeniem wskaźników dla adresów IP, adresów URL lub domen należy zapoznać się z następującymi wymaganiami wstępnymi:

- Zezwalanie na adres URL/adres IP i blokowanie zależy od włączenia ochrony sieci składnika Defender for Endpoint w trybie bloku. Aby uzyskać więcej informacji na temat ochrony sieci i instrukcji konfiguracji, zobacz [Włączanie ochrony sieci](enable-network-protection.md).
- Wersja klienta ochrony przed złośliwym kodem musi mieć wersję 4.18.1906.x lub nowszą. 
- Obsługiwane na maszynach Windows 10 w wersji 1709 lub nowszej, Windows 11, Windows Server 2016, Windows Server 2012 R2, Windows Server 2019, Windows Server 2022 oraz Android i iOS urządzeń.

    > [!NOTE]
    > Windows Server 2016 i Windows Server 2012 R2 należy dołączyć, korzystając z instrukcji zawartych w temacie [Dołączanie serwerów Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała.

- Upewnij się, że **niestandardowe wskaźniki sieci** są włączone w **Microsoft 365 Defender** \> **Ustawienia** \> **funkcje zaawansowane**. Aby uzyskać więcej informacji, zobacz [Funkcje zaawansowane](advanced-features.md).
- Aby uzyskać pomoc dotyczącą wskaźników dotyczących iOS, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender na temat iOS](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).
- Aby uzyskać obsługę wskaźników dotyczących Android, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender na temat Android](/microsoft-365/security/defender-endpoint/android-configure#configure-custom-indicators).

> [!IMPORTANT]
> Do listy wskaźników można dodawać tylko zewnętrzne adresy IP. Nie można utworzyć wskaźników dla wewnętrznych adresów IP.
> W przypadku scenariuszy ochrony sieci Web zalecamy korzystanie z wbudowanych funkcji w Microsoft Edge. Microsoft Edge korzysta z [usługi Network Protection](network-protection.md) w celu inspekcji ruchu sieciego i umożliwia blokowanie protokołów TCP, HTTP i HTTPS (TLS).
> Jeśli istnieją sprzeczne zasady wskaźnika adresu URL, zostanie zastosowana dłuższa ścieżka. Na przykład zasady `https://support.microsoft.com/office` wskaźnika adresu URL mają pierwszeństwo przed zasadami `https://support.microsoft.com`wskaźnika adresu URL.

> [!NOTE]
> W przypadku wszystkich innych procesów scenariusze ochrony sieci Web wykorzystują ochronę sieci do inspekcji i wymuszania:
>
> - Adres IP jest obsługiwany dla wszystkich trzech protokołów
> - Obsługiwane są tylko pojedyncze adresy IP (brak bloków CIDR ani zakresów adresów IP)
> - Zaszyfrowane adresy URL (pełna ścieżka) mogą być blokowane tylko w przeglądarkach innych firm (Internet Explorer, Edge)
> - Szyfrowane adresy URL (tylko nazwa FQDN) mogą być blokowane poza przeglądarkami innych firm (Internet Explorer, Edge)
> - Bloki pełnej ścieżki adresu URL można zastosować na poziomie domeny i wszystkich niezaszyfrowanych adresów URL
>
> Między czasem wykonania akcji a zablokowaniem adresu URL i adresu IP może wystąpić do 2 godzin opóźnienia (zwykle mniej).

W przypadku korzystania z trybu ostrzegania można skonfigurować następujące kontrolki:

**Możliwość obejścia**:

- Przycisk Zezwalaj w przeglądarce Edge
- Przycisk Zezwalaj na wyskakujące (przeglądarki inne niż Microsoft)
- Obejście parametru czasu trwania wskaźnika
- Pomijanie wymuszania w przeglądarkach firmy Microsoft i innych firm

**Adres URL przekierowania**:

- Parametr przekierowania adresu URL wskaźnika
- Adres URL przekierowania w przeglądarce Edge
- Adres URL przekierowania w wyskakujących (przeglądarki innych niż Microsoft)

Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami odnalezionych przez Ochrona punktu końcowego w usłudze Microsoft Defender](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Tworzenie wskaźnika adresów IP, adresów URL lub domen na stronie ustawień

1. W okienku nawigacji wybierz pozycję **Ustawienia** \> **Wskaźniki** **punktów końcowych** (w obszarze **Reguły**\>).

2. Wybierz kartę **Adresy IP lub adresy URL/domeny** .

3. Wybierz pozycję **Dodaj element**.

4. Określ następujące szczegóły:
   - Wskaźnik — określ szczegóły jednostki i zdefiniuj wygaśnięcie wskaźnika.
   - Akcja — określ akcję do wykonania i podaj opis.
   - Zakres — zdefiniuj zakres grupy maszyn.

5. Przejrzyj szczegóły na karcie Podsumowanie, a następnie kliknij przycisk **Zapisz**.

## <a name="related-topics"></a>Tematy pokrewne

- [Utwórz wskaźniki](manage-indicators.md)
- [Utwórz wskaźniki dla plików](indicator-file.md)
- [Tworzenie wskaźników na podstawie certyfikatów](indicator-certificates.md)
- [Zarządzaj wskaźnikami](indicator-manage.md)
