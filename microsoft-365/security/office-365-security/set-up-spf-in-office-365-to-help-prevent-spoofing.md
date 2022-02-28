---
title: Konfigurowanie spf w celu zapobiegania fałszerszem
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Dowiedz się, jak zaktualizować rekord usługi nazw domen (DNS) w celu używania struktury zasad dotyczących nadawców (SPF) z domeną niestandardową w usłudze Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab7bd0e579bfe26236eb009dc09689ddb90f2782
ms.sourcegitcommit: 43adb0d91af234c34e22d450a9c1d26aa745c2ca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2021
ms.locfileid: "62988672"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Konfigurowanie spf w celu zapobiegania fałszerszem

- [Wymagania wstępne](#prerequisites)
- [Tworzenie lub aktualizowanie rekordu SPF TXT](#create-or-update-your-spf-txt-record)
- [Jak obsługiwać poddomeny?](#how-to-handle-subdomains)
- [Rozwiązywanie problemów z SPF](#troubleshooting-spf)

<!--
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

W tym artykule opisano, jak zaktualizować rekord usługi nazw domen (DNS) w celu użycia uwierzytelniania poczty e-mail SPF (Sender Policy Framework) z domeną niestandardową w usłudze Office 365.

Spf ułatwia *weryfikację* wychodzących wiadomości e-mail wysłanych z domeny niestandardowej (jest ona pochodzących od osób, do których jest wysyłana wiadomość). Jest to pierwszy krok w konfigurowaniu pełnych zalecanych metod uwierzytelniania poczty e-mail metod SPF, [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md).

- [Wymagania wstępne](#prerequisites)
- [Tworzenie lub aktualizowanie rekordu SPF TXT](#create-or-update-your-spf-txt-record)
  - [Jak obsługiwać poddomeny?](#how-to-handle-subdomains)
- [Do czego w rzeczywistości działa uwierzytelnianie za pomocą poczty e-mail SPF?](#what-does-spf-email-authentication-actually-do)
  - [Rozwiązywanie problemów z SPF](#troubleshooting-spf)
- [Więcej informacji na temat SPF](#more-information-about-spf)

## <a name="prerequisites"></a>Wymagania wstępne

> [!IMPORTANT]
> Jeśli jesteś **małą firmą lub** nie wiesz, jak to zrobić, zadzwoń do rejestratora domen internetowych (np. Firma GoDaddy, Bluehost, web.com) & o pomoc w konfiguracji *DNS SPF* (i dowolnej innej metody uwierzytelniania poczty e-mail). <p> **Jeśli nie używasz** niestandardowego adresu URL (a adres URL używany dla domeny Office 365 kończy się na **onmicrosoft.com**), SPF został już dla Ciebie ustawiony w usłudze Office 365.

Zaczynamy.

Rekord TXT SPF dla Office 365 zostanie wykonany w zewnętrznym systemie DNS dla dowolnych domen niestandardowych lub poddomen. Do nagrania potrzebne są pewne informacje. Zbierz te informacje:

- Rekord TXT SPF domeny niestandardowej (jeśli istnieje). Aby uzyskać instrukcje, [zobacz Zbieranie informacji potrzebnych do utworzenia Office 365 DNS](../../admin/get-help-with-domains/information-for-dns-records.md).

- Przejdź do swoich serwerów wiadomości i sprawdź zewnętrzne adresy IP (wymagane na wszystkich lokalnych serwerach obsługi wiadomości). Na przykład **131.107.2.200**.

- Nazwy domen do użycia dla wszystkich domen innych firm, które należy uwzględnić w rekordzie TXT SPF. Niektórzy dostawcy poczty masowej skon skonfigurować poddomeny do używania dla swoich klientów. Na przykład w firmie MailChimp **servers.mcsv.net.**

- Ustalić, której reguły wymuszania chcesz użyć dla rekordu TXT SPF. Zalecana **jest reguła -all** . Aby uzyskać szczegółowe informacje na temat innych opcji składni, zobacz [Składnia rekordu SPF TXT dla Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> Aby używać domeny niestandardowej, usługa Office 365 wymaga dodania rekordu TXT SPF (Sender Policy Framework) do rekordu DNS w celu zapobiegania fałszowania.

## <a name="create-or-update-your-spf-txt-record"></a>Tworzenie lub aktualizowanie rekordu SPF TXT

1. Upewnij się, że znasz składnię spf w poniższej tabeli.

    <br>

    ****

    |Element|Jeśli używasz...|Czy jest to popularne dla klientów?|Dodaj to...|
    |---|---|---|---|
    |1|Dowolny system poczty e-mail (wymagany)|Wspólne. Wszystkie rekordy TXT SPF zaczynają się od tej wartości|`v=spf1`|
    |2|Exchange Online|Typowe|`include:spf.protection.outlook.com`|
    |3|Exchange Online dedykowane|Nie typowe|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 Germany, tylko Microsoft Cloud Germany|Nie typowe|`include:spf.protection.outlook.de`|
    |5|System poczty e-mail innej firmy|Nie typowe|`include:<domain_name>` <p> \<domain_name\> jest domeną systemu poczty e-mail innej firmy.|
    |6|Lokalnego systemu poczty e-mail. Na przykład Exchange Online Protection i inny system poczty e-mail|Nie typowe|Użyj jednego z tych dla każdego dodatkowego systemu poczty: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> są \<domain_name\> adresem IP i domeną innego systemu poczty e-mail, który wysyła pocztę w imieniu Twojej domeny.|
    |7|Dowolny system poczty e-mail (wymagany)|Wspólne. Wszystkie rekordy TXT SPF kończą się tą wartością|`<enforcement rule>` <p> Może to być jedna z kilku wartości. Zalecamy korzystanie z tej wartości `-all`.|
    |

2. Jeśli jeszcze tego nie zrobiono, stworzymy rekord TXT SPF, używając składni z tabeli.

   Jeśli na przykład hostowane są wyłącznie Office 365, to oznacza to, że nie masz żadnych lokalnych serwerów poczty, Twój rekord SPF TXT będzie zawierać wiersze 1, 2 i 7 i będzie wyglądał tak:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **W powyższym przykładzie jest najczęściej spotykany rekord TXT SPF**. Ten rekord działa tylko dla prawie każdego, niezależnie od tego, czy Twoje centrum danych firmy Microsoft znajduje się w Stanach Zjednoczonych, w Europie (w tym w Niemczech) czy w innej lokalizacji.

   Jeśli jednak zakupiono usługę Office 365 Germany w ramach usługi Microsoft Cloud Germany, zamiast wiersza 2 należy użyć oświadczenia z wiersza 4. Jeśli na przykład hostowane jest całkowicie w Office 365 Germany, to oznacza to, że nie masz lokalnych serwerów poczty, Twój rekord SPF TXT będzie zawierać wiersze 1, 4 i 7 i będzie wyglądał tak:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Jeśli twoja konfiguracja rekordów SPF TXT dla domeny niestandardowej została już wdrożona w programie Office 365 i jest migrowana do usługi Office 365 Germany, musisz zaktualizować rekord TXT SPF. Aby to zrobić, zmień na `include:spf.protection.outlook.com` `include:spf.protection.outlook.de`.

3. Po formularzu rekordu TXT SPF musisz zaktualizować rekord w systemie DNS. **Możesz mieć tylko jeden rekord TXT SPF dla domeny.** Jeśli rekord TXT SPF istnieje, zamiast dodawać nowy rekord, musisz zaktualizować istniejący rekord. Przejdź do [strony Tworzenie rekordów DNS dla Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md), a następnie wybierz link do hosta DNS.

4. Przetestuj rekord TXT SPF.

## <a name="how-to-handle-subdomains"></a>Jak obsługiwać poddomeny?

Należy pamiętać, że musisz utworzyć osobny rekord dla każdej poddomeny, ponieważ poddomeny nie dziedziczą rekordu SPF ich domeny najwyższego *poziomu*.

Dla każdej domeny i poddomeny jest`*.` wymagany rekord SPF z symbolami wieloznaczny, aby zapobiec wysyłaniu przez atakujących wiadomości e-mail poddomen, które poddomeny nie istnieją. Przykład:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>Rozwiązywanie problemów z SPF

Masz problemy z rekordem TXT SPF? Przeczytaj [rozwiązywanie problemów: Najlepsze rozwiązania dotyczące SPF w programie Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>Do czego w rzeczywistości działa uwierzytelnianie za pomocą poczty e-mail SPF?

Spf określa, które serwery poczty mogą wysyłać pocztę w Twoim imieniu. Zasadniczo SPF, wraz z DKIM, DMARC i innymi technologiami obsługiwanymi przez Office 365, pomagają zapobiegać fałszersku i wyłudzaniu informacji. Spf jest dodawany jako rekord TXT, który jest używany przez system DNS do identyfikowania serwerów poczty, które mogą wysyłać pocztę w imieniu Twojej domeny niestandardowej. Systemy poczty adresata odwołują się do rekordu TXT SPF w celu określenia, czy wiadomość z Twojej domeny niestandardowej pochodzi od autoryzowanego serwera wiadomości.

Załóżmy na przykład, że domena niestandardowa, z contoso.com używana przez Office 365. Dodajesz rekord TXT SPF, który wyświetla Office 365 wiadomości jako wiarygodne serwery poczty dla Twojej domeny. Gdy odbierający serwer wiadomości otrzymuje wiadomość z programu joe@contoso.com, wyszukuje rekord TXT SPF dla serwera contoso.com i sprawdza, czy wiadomość jest prawidłowa. Jeśli serwer odbierający stwierdzi, że wiadomość pochodzi z serwera innego niż serwery wiadomości Office 365 wymienione w rekordzie SPF, odbierający serwer poczty może odrzucić wiadomość jako spam.

Ponadto jeśli Twoja domena niestandardowa nie ma rekordu TXT SPF, niektóre serwery odbierające mogą odrzuć tę wiadomość. Jest tak, ponieważ serwer odbierający nie może sprawdzić, czy wiadomość pochodzi z autoryzowanego serwera wiadomości.

Jeśli masz już ustawioną pocztę dla usługi Office 365, serwery wiadomości firmy Microsoft zostały już uwzględnione w systemie DNS jako rekord TXT SPF. Jednak w niektórych przypadkach może być konieczne zaktualizowanie rekordu TXT SPF w systemie DNS. Przykład:

- Wcześniej trzeba było dodać inny rekord TXT SPF do domeny niestandardowej, jeśli używano usługi SharePoint Online. Nie jest to już wymagane. Ta zmiana powinna zmniejszyć ryzyko, że SharePoint wiadomości z powiadomieniami online kończące się w folderze Wiadomości-śmieci. Zaktualizuj rekord TXT SPF, jeśli jest przekroczony limit 10 odnośników i są odbierane błędy, takie jak "przekroczono limit odnośników" i "zbyt wiele przeskoków".

- Jeśli masz środowisko hybrydowe z usługą Office 365 i Exchange lokalnym.

- Zamierzasz skonfigurować DKIM i DMARC (zalecane).

## <a name="more-information-about-spf"></a>Więcej informacji na temat SPF

Aby uzyskać przykłady zaawansowane, bardziej szczegółową dyskusję na temat obsługiwanej składni SPF, fałszowania, rozwiązywania problemów i sposobu, w jaki program Office 365 obsługuje funkcję SPF, zobacz Jak działa funkcja SPF w celu zapobiegania fałszersce i wyłudzaniu informacji w sieci [Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>Następne kroki: DKIM i DMARC

 Spf ma na celu zapobieganie fałszersce, ale istnieją techniki podszywania się, przed które spf nie może się chronić. Aby obronić się przed tymi ustawieniami, po skonfigurowaniu spf musisz skonfigurować ustawienia DKIM i DMARC dla Office 365.

Celem uwierzytelniania poczty e-mail [**DKIM**](use-dkim-to-validate-outbound-email.md) jest udowodnienie, że zawartość wiadomości nie została naruszona.

[**Celem uwierzytelniania poczty e-mail DMARC**](use-dmarc-to-validate-email.md) jest upewnienie się, że informacje SPF i DKIM są takie, jak adres Od.

 Aby uzyskać zaawansowane przykłady i bardziej szczegółową dyskusję na temat obsługiwanej składni SPF, zobacz Jak działa funkcja SPF w celu zapobiegania [fałszowania](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks) i wyłudzania informacji w Office 365.

*Wybierz pozycję "Ta strona" w obszarze "Opinia", jeśli masz opinię na temat tej dokumentacji.*
