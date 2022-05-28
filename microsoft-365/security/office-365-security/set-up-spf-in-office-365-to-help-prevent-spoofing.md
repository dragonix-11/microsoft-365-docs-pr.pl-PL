---
title: Konfigurowanie platformy SPF w celu zapobiegania spoofingowi
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
description: Dowiedz się, jak zaktualizować rekord usługi nazw domen (DNS) w celu używania struktury zasad nadawcy (SPF) z domeną niestandardową w Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 33e4a6d3644f7a3aab8992130b2b92e09dd665af
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772407"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Konfigurowanie platformy SPF w celu zapobiegania spoofingowi

- [Wymagania wstępne](#prerequisites)
- [Tworzenie lub aktualizowanie rekordu SPF TXT](#create-or-update-your-spf-txt-record)
- [Jak obsługiwać poddomeny?](#how-to-handle-subdomains)
- [Rozwiązywanie problemów z platformą SPF](#troubleshooting-spf)

<!--
[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

W tym artykule opisano sposób aktualizowania rekordu usługi nazw domen (DNS), aby można było używać uwierzytelniania poczty e-mail programu Sender Policy Framework (SPF) z domeną niestandardową w Office 365.

SPF pomaga *zweryfikować wychodzące wiadomości e-mail* wysyłane z domeny niestandardowej (pochodzi od tego, kto to mówi). Jest to pierwszy krok w konfigurowaniu pełnych zalecanych metod uwierzytelniania poczty e-mail usług SPF, [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md).

- [Wymagania wstępne](#prerequisites)
- [Tworzenie lub aktualizowanie rekordu SPF TXT](#create-or-update-your-spf-txt-record)
  - [Jak obsługiwać poddomeny?](#how-to-handle-subdomains)
- [Co faktycznie robi uwierzytelnianie poczty e-mail SPF?](#what-does-spf-email-authentication-actually-do)
  - [Rozwiązywanie problemów z platformą SPF](#troubleshooting-spf)
- [Więcej informacji o platformie SPF](#more-information-about-spf)

## <a name="prerequisites"></a>Wymagania wstępne

> [!IMPORTANT]
> Jeśli jesteś **małą firmą** lub nie znasz adresów IP lub konfiguracji DNS, zadzwoń do rejestratora domen internetowych (np. GoDaddy, Bluehost, web.com) & poprosić o pomoc w *konfiguracji DNS SPF* (i innej metody uwierzytelniania poczty e-mail). <p> **Jeśli nie używasz niestandardowego adresu URL** (a adres URL używany do Office 365 kończy się **onmicrosoft.com**), SPF został już skonfigurowany w usłudze Office 365.

Zatem do dzieła.

Rekord SPF TXT dla Office 365 zostanie wprowadzony w zewnętrznym systemie DNS dla dowolnych domen niestandardowych lub domen podrzędnych. Potrzebujesz pewnych informacji, aby utworzyć rekord. Zbierz następujące informacje:

- Rekord SPF TXT dla domeny niestandardowej, jeśli istnieje. Aby uzyskać instrukcje, zobacz [Zbieranie informacji potrzebnych do utworzenia Office 365 rekordów DNS](../../admin/get-help-with-domains/information-for-dns-records.md).

- Przejdź do serwerów obsługi komunikatów i znajdź zewnętrzne adresy IP (potrzebne ze wszystkich lokalnych serwerów obsługi komunikatów). Na przykład **131.107.2.200**.

- Nazwy domen do użycia dla wszystkich domen innych firm, które należy uwzględnić w rekordzie SPF TXT. Niektórzy dostawcy poczty zbiorczej skonfigurowali poddomeny do użycia dla swoich klientów. Na przykład firma MailChimp skonfigurowała **servers.mcsv.net**.

- Dowiedz się, jakiej reguły wymuszania chcesz użyć dla rekordu SPF TXT. Zalecana jest reguła **-all** . Aby uzyskać szczegółowe informacje o innych opcjach składni, zobacz [Składnia rekordu SPF TXT dla Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> Aby można było użyć domeny niestandardowej, Office 365 wymaga dodania rekordu TXT struktury zasad nadawcy (SPF) do rekordu DNS, aby zapobiec fałszowaniu.

## <a name="create-or-update-your-spf-txt-record"></a>Tworzenie lub aktualizowanie rekordu SPF TXT

1. Upewnij się, że znasz składnię SPF w poniższej tabeli.

    |Element|Jeśli używasz...|Typowe dla klientów?|Dodaj to...|
    |---|---|---|---|
    |1|Dowolny system poczty e-mail (wymagany)|Wspólne. Wszystkie rekordy SPF TXT zaczynają się od tej wartości|`v=spf1`|
    |2|Exchange Online|Wspólne|`include:spf.protection.outlook.com`|
    |3|Exchange Online tylko dedykowane|Nie jest to typowe|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 Niemczech, tylko Microsoft Cloud Germany|Nie jest to typowe|`include:spf.protection.outlook.de`|
    |5|System poczty e-mail innej firmy|Nie jest to typowe|`include:<domain_name>` <p> \<domain_name\> jest domeną systemu poczty e-mail innej firmy.|
    |6|Lokalny system poczty e-mail. Na przykład Exchange Online Protection plus inny system poczty e-mail|Nie jest to typowe|Użyj jednego z nich dla każdego dodatkowego systemu poczty: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> i \<domain_name\> to adres IP i domena innego systemu poczty e-mail, który wysyła pocztę w imieniu twojej domeny.|
    |7|Dowolny system poczty e-mail (wymagany)|Wspólne. Wszystkie rekordy SPF TXT kończą się tą wartością|`<enforcement rule>` <p> Może to być jedna z kilku wartości. Zalecamy wartość `-all`.|

2. Jeśli jeszcze tego nie zrobiono, należy utworzyć rekord SPF TXT przy użyciu składni z tabeli.

   Jeśli na przykład jesteś hostowany w całości w Office 365, oznacza to, że nie masz lokalnych serwerów poczty, rekord SPF TXT będzie zawierać wiersze 1, 2 i 7 i będzie wyglądać następująco:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **Powyższy przykład jest najczęstszym rekordem SPF TXT**. Ten rekord działa dla prawie wszystkich, niezależnie od tego, czy centrum danych firmy Microsoft znajduje się w Stany Zjednoczone, czy w Europie (w tym w Niemczech), czy w innej lokalizacji.

   Jeśli jednak zakupiono Office 365 Niemczech, część usługi Microsoft Cloud Germany, należy użyć instrukcji include z wiersza 4 zamiast wiersza 2. Jeśli na przykład jesteś hostowany w całości w Office 365 Niemczech, oznacza to, że nie masz lokalnych serwerów poczty, rekord SPF TXT będzie zawierać wiersze 1, 4 i 7 i będzie wyglądać następująco:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Jeśli masz już wdrożone Office 365 i skonfigurowano rekordy SPF TXT dla domeny niestandardowej i przeprowadzasz migrację do Office 365 Niemczech, musisz zaktualizować rekord SPF TXT. Aby to zrobić, zmień wartość `include:spf.protection.outlook.com` na `include:spf.protection.outlook.de`.

3. Po utworzeniu rekordu SPF TXT należy zaktualizować rekord w systemie DNS. **Możesz mieć tylko jeden rekord TXT SPF dla domeny.** Jeśli istnieje rekord SPF TXT, zamiast dodawać nowy rekord, musisz zaktualizować istniejący rekord. Przejdź do pozycji [Tworzenie rekordów DNS dla Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md), a następnie wybierz link dla hosta DNS.

4. Przetestuj rekord SPF TXT.

## <a name="how-to-handle-subdomains"></a>Jak obsługiwać poddomeny?

Należy pamiętać, że *należy utworzyć oddzielny rekord dla każdej poddomeny, ponieważ poddomeny nie dziedziczą rekordu SPF domeny najwyższego poziomu*.

Rekord SPF z symbolami wieloznacznymi (`*.`) jest wymagany dla każdej domeny i poddomeny, aby zapobiec wysyłaniu wiadomości e-mail przez osoby atakujące z nieistniejącymi domenami podrzędnymi. Przykład:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>Rozwiązywanie problemów z platformą SPF

Masz problemy z rekordem SPF TXT? [Rozwiązywanie problemów z odczytem: najlepsze rozwiązania dotyczące SPF w Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>Co faktycznie robi uwierzytelnianie poczty e-mail SPF?

SPF określa, które serwery poczty mogą wysyłać wiadomości e-mail w Twoim imieniu. Zasadniczo SPF, wraz z DKIM, DMARC i innymi technologiami obsługiwanymi przez Office 365, pomagają zapobiegać fałszowaniu i wyłudzaniu informacji. SPF jest dodawany jako rekord TXT używany przez usługę DNS do identyfikowania serwerów poczty, które mogą wysyłać wiadomości e-mail w imieniu domeny niestandardowej. Systemy poczty adresatów odwołują się do rekordu SPF TXT, aby ustalić, czy wiadomość z domeny niestandardowej pochodzi z autoryzowanego serwera obsługi komunikatów.

Załóżmy na przykład, że domena niestandardowa contoso.com używa Office 365. Dodajesz rekord SPF TXT, który wyświetla listę serwerów Office 365 komunikatów jako prawidłowe serwery poczty dla twojej domeny. Gdy serwer odbierający komunikaty otrzymuje komunikat z joe@contoso.com, serwer wyszukuje rekord SPF TXT dla contoso.com i sprawdza, czy komunikat jest prawidłowy. Jeśli serwer odbierający dowie się, że wiadomość pochodzi z serwera innego niż serwery Office 365 komunikatów wymienione w rekordzie SPF, serwer poczty odbiorczej może odrzucić wiadomość jako spam.

Ponadto jeśli domena niestandardowa nie ma rekordu SPF TXT, niektóre serwery odbierające mogą odrzucić komunikat wprost. Dzieje się tak, ponieważ serwer odbierający nie może sprawdzić, czy komunikat pochodzi z autoryzowanego serwera obsługi komunikatów.

Jeśli poczta została już skonfigurowana dla Office 365, serwery obsługi komunikatów firmy Microsoft zostały już uwzględnione w systemie DNS jako rekord SPF TXT. Jednak w niektórych przypadkach może być konieczne zaktualizowanie rekordu SPF TXT w systemie DNS. Przykład:

- Wcześniej trzeba było dodać inny rekord SPF TXT do domeny niestandardowej, jeśli używasz usługi SharePoint Online. Nie jest to już wymagane. Ta zmiana powinna zmniejszyć ryzyko SharePoint wiadomości powiadomień online znajdujących się w folderze Wiadomości-śmieci. Zaktualizuj rekord TXT SPF, jeśli osiągasz limit 10 odnośników i otrzymujesz błędy, takie jak "przekroczono limit wyszukiwania" i "zbyt wiele przeskoków".

- Jeśli masz środowisko hybrydowe z Office 365 i Exchange lokalnie.

- Zamierzasz skonfigurować DKIM i DMARC (zalecane).

## <a name="more-information-about-spf"></a>Więcej informacji o platformie SPF

Aby uzyskać zaawansowane przykłady, bardziej szczegółową dyskusję na temat obsługiwanej składni SPF, fałszowania, rozwiązywania problemów i sposobu, w jaki Office 365 obsługuje SPF, zobacz [Jak działa SPF, aby zapobiec fałszowaniu i wyłudzaniu informacji w Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>Następne kroki: DKIM i DMARC

 SPF ma na celu zapobieganie fałszowaniu, ale istnieją techniki fałszowania, przed których SPF nie może się chronić. Aby się przed tym bronić, po skonfigurowaniu SPF należy skonfigurować DKIM i DMARC dla Office 365.

Celem uwierzytelniania poczty e-mail [**DKIM**](use-dkim-to-validate-outbound-email.md) jest udowodnienie, że zawartość wiadomości e-mail nie została naruszona.

Celem uwierzytelniania poczty e-mail [**DMARC**](use-dmarc-to-validate-email.md) jest upewnienie się, że informacje SPF i DKIM są zgodne z adresem Od.

 Aby uzyskać zaawansowane przykłady i bardziej szczegółową dyskusję na temat obsługiwanej składni SPF, zobacz [Jak działa SPF, aby zapobiec fałszowaniu i wyłudzaniu informacji w Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

[Używanie zaufanych nadawców usługi ARC na potrzeby legalnych przepływów poczty](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)

*Wybierz pozycję "Ta strona" w obszarze "Opinia", jeśli masz opinię na temat tej dokumentacji.*
