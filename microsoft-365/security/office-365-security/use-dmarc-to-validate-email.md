---
title: Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail, kroków konfiguracji
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/10/2021
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 4a05898c-b8e4-4eab-bd70-ee912e349737
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Dowiedz się, jak skonfigurować DMARC (Domain-based Message Authentication, Reporting, and Conformance) do sprawdzania poprawności wiadomości wysłanych z Twojej organizacji.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7b166a481bf503ce2d46e79f2cb674861935f4ff
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006564"
---
# <a name="use-dmarc-to-validate-email"></a>Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[DMARC](https://dmarc.org) (Domain-based Message Authentication, Reporting, and Conformance) działa z mechanizmami SPF (Sender Policy Framework) i DKIM (DomainKeys Identified Mail) w celu uwierzytelniania nadawców poczty i upewnienia się, że docelowe systemy poczty e-mail zaufają wiadomościom wysyłanym z Twojej domeny. Wdrożenie DMARC za pomocą SPF i DKIM zapewnia dodatkową ochronę przed fałszowaniem i wyłudzaniem informacji e-mail. DMARC ułatwia odbieranie systemów poczty w określaniu, co należy zrobić z wiadomościami wysyłanymi z Twojej domeny, w przypadku których nie są sprawdzane SPF lub DKIM.

> [!TIP]
> Odwiedź katalog [Microsoft Intelligent Security Association (MISA),](https://www.microsoft.com/misapartnercatalog) aby wyświetlić informacje o dostawcach innych firm, którzy oferują raporty DMARC dla Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>Jak SPF i DMARC współpracują w celu ochrony poczty e-mail w Microsoft 365?

 Wiadomość e-mail może zawierać wiele adresów nadawcy lub nadawcy. Te adresy są używane do różnych celów. Rozważ na przykład następujące adresy:

- **Adres "Poczta od"**. Identyfikuje nadawcę i określa, gdzie mają być wysłane powiadomienia o dostarczeniu, jeśli występują problemy z dostarczaniem wiadomości, takie jak powiadomienia o niedo dostarczenia. Ta informacja pojawi się w części koperty wiadomości e-mail i nie będzie wyświetlana w aplikacji poczty e-mail. Jest to czasami nazywane adresem 5321.MailFrom lub adresem odwrotnej ścieżki.

- **Adres "Od"**: adres wyświetlany w aplikacji poczty jako adres Od. Ten adres wskazuje autora wiadomości e-mail. Oznacza to skrzynkę pocztową osoby lub systemu odpowiedzialnego za napisanie wiadomości. Jest to czasami nazywane adresem 5322.From.

Spf używa rekordu DNS TXT w celu zapewnienia listy autoryzowanych wysyłających adresów IP dla danej domeny. Zwykle testy SPF są wykonywane tylko względem adresu 5321.MailFrom. Oznacza to, że adres 5322.From nie jest uwierzytelniany, gdy jest sam spf. Pozwala to na scenariusz, w którym użytkownik może odebrać wiadomość, który przekazuje sprawdzanie SPF, ale ma sfałszowaną wartość 5322.From sender address (Z adresu nadawcy). Przejmij na przykład ten zapis SMTP:

```console
S: Helo woodgrovebank.com
S: Mail from: phish@phishing.contoso.com
S: Rcpt to: astobes@tailspintoys.com
S: data
S: To: "Andrew Stobes" <astobes@tailspintoys.com>
S: From: "Woodgrove Bank Security" <security@woodgrovebank.com>
S: Subject: Woodgrove Bank - Action required
S:
S: Greetings User,
S:
S: We need to verify your banking details.
S: Please click the following link to verify that Microsoft has the right information for your account.
S:
S: https://short.url/woodgrovebank/updateaccount/12-121.aspx
S:
S: Thank you,
S: Woodgrove Bank
S: .
```

W tej transkrypcie adresy nadawców są następujące:

- Poczta z adresu (5321.MailFrom): phish@phishing.contoso.com

- Od adresu (5322.From): security@woodgrovebank.com

Jeśli skonfigurowano SPF, serwer odbierający przeprowadza sprawdzanie względem pola adresu Mail od phish@phishing.contoso.com. Jeśli wiadomość pochodzi z prawidłowego źródła dla domeny phishing.contoso.com, oznacza to, że pomyślnie przejdzie sprawdzanie SPF. Ponieważ klient poczty e-mail wyświetla tylko adres Od, użytkownik widzi, że ta wiadomość pochodzi od security@woodgrovebank.com. Sam rekord SPF oznacza, że poprawność woodgrovebank.com nigdy nie została uwierzytelniona.

W przypadku korzystania z funkcji DMARC serwer odbierający również przeprowadza sprawdzanie pod adresem Od. W powyższym przykładzie, jeśli istnieje rekord TXT DMARC na woodgrovebank.com, sprawdzanie adresu Od kończy się niepowodzeniem.

## <a name="what-is-a-dmarc-txt-record"></a>Co to jest rekord TXT DMARC?

Rekord DMARC, podobnie jak rekordy DNS dla spf, jest rekordem tekstowym DNS (TXT), który pomaga zapobiegać fałszingowi i wyłudzaniu informacji. Publikujesz rekordy TXT DMARC w systemie DNS. Rekordy TXT DMARC sprawdzają pochodzenie wiadomości e-mail, weryfikując adres IP autora wiadomości e-mail na domniemanego właściciela domeny wysyłającej. Rekord TXT DMARC identyfikuje autoryzowane serwery poczty e-mail ruchu wychodzącego. Docelowe systemy poczty e-mail mogą następnie sprawdzić, czy o odbieranie wiadomości pochodzą one z autoryzowanych wychodzących serwerów poczty e-mail.

Rekord TXT DMARC firmy Microsoft wygląda następująco:

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"
```

Aby uzyskać informacje o innych dostawcach, którzy oferują raporty DMARC dla Microsoft 365, odwiedź [katalog MISA](https://www.microsoft.com/misapartnercatalog?IntegratedProducts=DMARCReportingforOffice365).

## <a name="set-up-dmarc-for-inbound-mail"></a>Konfigurowanie usługi DMARC dla poczty przychodzącej

Nie musisz nic robić, aby skonfigurować DMARC dla poczty obierania w Microsoft 365. To wszystko jest zajmą się tym. Jeśli chcesz dowiedzieć się, co się stanie z pocztą, która nie przejdzie naszych testów DMARC, zobacz Jak Microsoft 365 poczty przychodzącej, która kończy się niepowodzeniem [DMARC](#how-microsoft-365-handles-inbound-email-that-fails-dmarc).

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Konfigurowanie usługi DMARC dla poczty wychodzącej z usługi Microsoft 365

Jeśli używasz Microsoft 365, ale nie używasz domeny niestandardowej, to znaczy używasz programu onmicrosoft.com, nie musisz robić nic innego, aby skonfigurować lub zaimplementować DMARC dla swojej organizacji. Spf jest już automatycznie ustawiony i Microsoft 365 automatycznie generuje podpis DKIM dla poczty wychodzącej. Aby uzyskać więcej informacji na temat tego podpisu, zobacz [Zachowanie domyślne dla DKIM i Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 Jeśli masz domenę niestandardową lub oprócz programu Microsoft 365 używasz lokalnych serwerów poczty Exchange, musisz ręcznie zaimplementować DMARC dla poczty wychodzącej. Implementowanie DMARC dla domeny niestandardowej obejmuje następujące kroki:

- [Krok 1. Identyfikowanie prawidłowych źródeł poczty dla domeny](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [Krok 2. Konfigurowanie spf dla domeny](#step-2-set-up-spf-for-your-domain)

- [Krok 3. Konfigurowanie usługi DKIM dla domeny niestandardowej](#step-3-set-up-dkim-for-your-custom-domain)

- [Krok 4. Formularz rekordu TXT DMARC domeny](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>Krok 1. Identyfikowanie prawidłowych źródeł poczty dla domeny

Jeśli masz już ustawioną spf, to zostało już wykonywane to ćwiczenie. Jednak w przypadku DMARC istnieją dodatkowe zagadnienia. Podczas identyfikowania źródeł poczty dla domeny należy odpowiedzieć na dwa pytania:

- Jakie adresy IP wysyłają wiadomości z mojej domeny?

- W przypadku poczty wysłanej przez inne firmy w moim imieniu będą dopasowane domeny 5321.MailFrom i 5322.From domains?

### <a name="step-2-set-up-spf-for-your-domain"></a>Krok 2. Konfigurowanie spf dla domeny

Teraz, gdy masz listę wszystkich swoich prawidłowych nadawców, możesz wykonać czynności opisane w te sposób: Konfigurowanie SPF w celu zapobiegania [fałszersce](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Załóżmy na przykład, że program contoso.com wysyła pocztę z programu Exchange Online — lokalnego serwera Exchange, którego adres IP to 192.168.0.1, oraz aplikacji sieci Web o adresie IP 192.168.100.100, rekord TXT SPF będzie wyglądał tak:

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

Jako najlepsze rozwiązanie należy się upewnić, że rekord TXT SPF uwzględnia nadawców z innych firm.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>Krok 3. Konfigurowanie usługi DKIM dla domeny niestandardowej

Po skonfigurowaniu spf musisz skonfigurować DKIM. Funkcja DKIM umożliwia dodawanie podpisu cyfrowego do wiadomości e-mail w nagłówku wiadomości. Jeśli nie skonfigurujemy funkcji DKIM i Microsoft 365 używanie domyślnej konfiguracji DKIM dla domeny, DMARC może nie powieść się. Jest tak, ponieważ domyślna konfiguracja usługi DKIM używa domeny onmicrosoft.com domeny jako adresu 5322.From, a nie domeny niestandardowej. Wymusza to niezgodność między wartościami 5321.MailFrom i 5322.From (Od) we wszystkich wiadomościach e-mail wysyłanych z Twojej domeny.

Jeśli nadawcy z innych firm wysyłają wiadomości w Twoim imieniu i wysyłana przez nich wiadomość e-mail nie ma wartości 5321.MailFrom i 5322.From adresy, DMARC nie powiedzie się dla tej wiadomości e-mail. Aby tego uniknąć, musisz skonfigurować DKIM dla swojej domeny, a konkretnie u tego nadawcy innej firmy. Umożliwia to Microsoft 365 e-mail z tej usługi innych firm. Jednak inne osoby, na przykład Yahoo, Gmail i Comcast, mogą zweryfikować wiadomości e-mail wysłane do nich przez inne firmy tak, jakby były wysyłane przez Ciebie. Jest Microsoft 365 korzystne, ponieważ pozwala klientom na tworzenie zaufania z Twoją domeną bez względu na miejsce, w którym znajdują się ich skrzynki pocztowe, a jednocześnie program Microsoft 365 nie oznacza wiadomości jako spamu z powodu fałszowania, ponieważ przejdzie testy uwierzytelniania dla Twojej domeny.

Aby uzyskać instrukcje dotyczące konfigurowania funkcji DKIM dla twojej domeny, w tym sposobu konfigurowania funkcji DKIM dla nadawców innych firm, aby nadawcy podszywali się pod Twoją domenę, zobacz Używanie funkcji [DKIM](use-dkim-to-validate-outbound-email.md) do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych z domeny niestandardowej.

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>Krok 4. Formularz rekordu TXT DMARC domeny

Chociaż istnieją inne opcje składni, o których nie wspomniano, są to najczęściej używane opcje używane w programach Microsoft 365. Form the DMARC TXT record for your domain in the format:

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

Gdzie:

- *domena* to domena, którą chcesz chronić. Domyślnie rekord chroni pocztę przed domeną i wszystkimi poddomenami. Jeśli na przykład określisz typ dmarc.contoso.com \_, program DMARC będzie chronić pocztę przed domeną i wszystkimi poddomenami, takimi jak housewares.contoso.com lub plumbing.contoso.com.

- *Czas wygaśnięcia* zawsze powinien być odpowiednikiem jednej godziny. Jednostka używana w przypadku czasu wygaśnięcia: godziny (1 godzina), minuty (60 minut) lub sekund (3600 sekund) będzie się różnić w zależności od rejestratora Twojej domeny.

- *Pct=100 wskazuje* , że ta reguła powinna być używana w 100% wiadomości e-mail.

- *zasady* określają zasady, które mają być zgodne z zasadami, które mają być zgodne z zasadami dla serwera odbieracego w przypadku niepowodzenia działania DMARC. Zasady można ustawić jako brak, kwarantannę lub odrzucenie.

Aby uzyskać informacje na temat opcji, których można użyć, zapoznaj się z pojęciami w tematach Najlepsze rozwiązania dotyczące implementowania [funkcji DMARC w programie Microsoft 365](#best-practices-for-implementing-dmarc-in-microsoft-365).

Przykłady:

- Zasady ustawione na brak

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- Zasady ustawione do kwarantanny

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- Zestaw zasad do odrzucenia

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Po formularzu rekordu musisz zaktualizować rekord u rejestratora domen.

## <a name="dmarc-mail-public-preview-feature"></a>DMARC Mail (funkcja publicznej wersji zapoznawczej)

> [!CAUTION]
> Wiadomości e-mail mogą nie być wysyłane codziennie, a sam raport może ulec zmianie podczas publicznego podglądu. Można oczekiwać, że zagregowane wiadomości e-mail raportu DMARC będą wysyłane z kont klientów hotmail.com (na przykład kont klientów hotmail.com, outlook.com lub live.com klientów).

W tym przykładowym rekordzie TXT DMARC: `dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"`, możesz zobaczyć adres *rua* , w tym przypadku przetworzony przez firmę Agari z innej firmy. Ten adres służy do wysyłania zagregowanych opinii do analizy, która jest używana do generowania raportu.

> [!TIP]
> Odwiedź katalog [MISA,](https://www.microsoft.com/misapartnercatalog) aby wyświetlić więcej dostawców zewnętrznych oferujących raporty DMARC dla Microsoft 365. Zobacz [temat DMARC (Domain-based Message Authentication, Reporting, and Conformance) organizacji IETF.org](https://datatracker.ietf.org/doc/html/rfc7489) , aby uzyskać więcej informacji na temat adresów DMARC "rua".


## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Najlepsze rozwiązania dotyczące implementowania DMARC w programie Microsoft 365

Program DMARC można wdrożyć stopniowo bez wpływu na pozostałą część przepływu poczty. Utwórz i implementuj plan wdrażania, który jest następujący po tych krokach. Przed przejściem do następnego kroku wykonaj wszystkie te czynności najpierw dla poddomeny, a następnie innych poddomen, a na koniec domeny najwyższego poziomu w organizacji.

1. Monitorowanie wpływu wdrożenia DMARC

    Zacznij od prostego rekordu trybu monitorowania dla poddomeny lub domeny, który żąda, aby odbiorcy DMARC wysyłali do Ciebie statystykę wiadomości widzianych przy użyciu tej domeny. Rekord trybu monitorowania to rekord TXT DMARC, dla który jego zasady mają ustawioną wartość brak (p=none). Wiele firm publikuje rekord TXT DMARC z p=none, ponieważ nie ma pewności, ile poczty e-mail może utracić, publikując bardziej restrykcyjne zasady DMARC.

    Możesz to zrobić jeszcze przed zaimplementowaniem funkcji SPF lub DKIM w infrastrukturze obsługi wiadomości. Jednak nie będzie można skutecznie poddać kwarantannie ani odrzucić poczty przy użyciu funkcji DMARC, dopóki nie zaimplementowano również funkcji SPF i DKIM. W związku z wprowadzeniem spf i DKIM raporty wygenerowane za pomocą DMARC będą źródłem liczb i źródeł wiadomości, które przechodzą te testy, a te nie. Możesz łatwo sprawdzić, ile Twojego wiarygodnego ruchu jest lub nie jest przez nie objęte, i rozwiązywać wszelkie problemy. Zaczniesz również widzieć, ile nieuprawnianych wiadomości jest wysyłanych i skąd są wysyłane.

2. Żądanie, aby zewnętrzne systemy poczty poddały poczty kwarantannie, która kończy się niepowodzeniem DMARC

    Jeśli uważasz, że cały lub większość Twojego ruchu jest chroniony za pomocą spf i DKIM, i rozumiesz wpływ wdrożenia DMARC, możesz zaimplementować zasady kwarantanny. Zasady kwarantanny to rekord TXT DMARC, dla których ustawiono kwarantannę (p=kwarantanna). W ten sposób prosi się odbiorców DMARC, aby umieszczali wiadomości z Twojej domeny, w przypadku których nie powiodło się DMARC, w lokalnym odpowiedniku folderu spamu, a nie w skrzynkach odbiorczych klientów.

3. Żądanie, aby zewnętrzne systemy poczty nie akceptowały wiadomości, których błędem jest DMARC

    Ostatnim krokiem jest zaimplementowanie zasad odrzucania. Zasady odrzucania to rekord TXT DMARC, dla których ustawiono zasady odrzucania (p=odrzuć). W takim przypadku należy poprosić odbiorców DMARC, aby nie akceptowali wiadomości, które zakończyły się niepowodzeniem sprawdzania DMARC.

4. Jak skonfigurować DMARC dla poddomeny?

   DMARC jest implementowany przez publikowanie zasad jako rekordu TXT w systemie DNS i jest hierarchiczny (na przykład zasady opublikowane dla usługi contoso.com będą stosowane do usługi sub.domain.contonos.com, chyba że dla tej poddomeny nie zostały jawnie zdefiniowane inne zasady). Jest to przydatne, ponieważ organizacje mogą mieć możliwość określenia mniejszej liczby rekordów DMARC wysokiego poziomu w celu szerszego zasięgu. Należy zadbać o to, aby konfigurować jawne rekordy DMARC poddomen w miejscach, w których poddomeny nie powinny dziedziczyć rekordu DMARC domeny najwyższego poziomu.

   Ponadto możesz dodać zasady typu symbolu wieloznacznego dla funkcji DMARC, gdy poddomeny nie powinny wysyłać wiadomości e-mail, dodając wartość `sp=reject` . Przykład:

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Jak Microsoft 365 wychodzącej poczty e-mail, która kończy się niepowodzeniem DMARC

Jeśli wiadomość wychodząca z usługi Microsoft 365 kończy się niepowodzeniem przez DMARC i ustawiono zasady p=kwarantanny lub p=odrzuć, wiadomość jest przekierowywać wiadomości wychodzące przez pulę dostarczania wiadomości wysokiego [ryzyka.](high-risk-delivery-pool-for-outbound-messages.md) Nie ma możliwości zastępowania wychodzących wiadomości e-mail.

Jeśli opublikujesz zasady odrzuć DMARC (p=reject), żaden inny klient w usłudze Microsoft 365 nie będzie mógł podszyć się pod Twoją domenę, ponieważ wiadomości nie będą mogły przekazać SPF ani DKIM dla Twojej domeny podczas przekazywania wiadomości wychodzących przez usługę. Jeśli jednak opublikujesz DMARC, ale nie uwierzytelnisz wszystkich wiadomości e-mail za pośrednictwem programu Microsoft 365, niektóre z nich mogą zostać oznaczone jako spam dla przychodzącej poczty e-mail (jak opisano powyżej) lub zostaną odrzucone, jeśli nie opublikujesz spf i spróbujesz go przekazywanie przez usługę. Dzieje się tak, jeśli na przykład zapomnisz dołączyć niektóre adresy IP serwerów i aplikacji, które wysyłają pocztę w imieniu Twojej domeny podczas formować rekord TXT DMARC.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Jak Microsoft 365 przychodzącej poczty e-mail, która kończy się niepowodzeniem DMARC

Jeśli zasady DMARC `p=reject`serwera wysyłającego to , program [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) oznacza wiadomość jako sfałszowaną, zamiast odrzucać ją. Innymi słowy: w przypadku przychodzącej poczty e-mail Microsoft 365 traktować `p=reject` ją `p=quarantine` tak samo i tak samo. Administratorzy mogą zdefiniować akcję, która ma na celu ataki na wiadomości sklasyfikowane jako sfałszowane w ramach zasad [ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md).

Microsoft 365 został skonfigurowany w ten sposób, ponieważ niektóre wiarygodne wiadomości e-mail mogą nie powieść się dMARC. Na przykład wiadomość może nie zostać wysłana do listy adresowej przez DMARC, która następnie przekazuje tę wiadomość wszystkim uczestnikom listy. Jeśli Microsoft 365 odrzucone, inne osoby mogą utracić legalną pocztę e-mail i nie mogą jej odzyskać. Zamiast tego te wiadomości nadal nie będą się dMARC, ale będą oznaczane jako spam i nie będą odrzucane. W razie potrzeby użytkownicy nadal mogą odbierać te wiadomości w swoich skrzynkach odbiorczych za pomocą tych metod:

- Użytkownicy dodają bezpiecznych nadawców pojedynczo przy użyciu swojego klienta poczty e-mail.

- Administratorzy mogą używać szczegółowych informacji o analizie dotyczącej [fałszowania](learn-about-spoof-intelligence.md) lub listy zezwalania [na blokowanie dzierżawy](tenant-allow-block-list.md) , aby zezwolić na wiadomości od sfałszowanych nadawców.

- Administratorzy tworzą regułę przepływu Exchange poczty e-mail (z znaną także regułą transportu) dla wszystkich użytkowników, która zezwala na wiadomości od tych określonych nadawców.

Aby uzyskać więcej informacji, zobacz [Tworzenie bezpiecznych list nadawców](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Sposób Microsoft 365 funkcji uwierzytelnionego łańcucha odbieranych (ARC)

Wszystkie hostowane skrzynki pocztowe w Microsoft 365 teraz skorzystają z funkcji ŁUK, dzięki ulepszonej dostarczności wiadomości i ulepszonej ochrony przed fałszerością. Łuk zachowuje wyniki uwierzytelniania poczty e-mail od wszystkich uczestniczących w nim pośredników, czyli przeskoków, gdy wiadomość e-mail jest przekierowyowana z serwera pochodzących do skrzynki pocztowej adresata. Przed wprowadzeniem funkcji ARC modyfikacje wykonywane przez pośredniczące w routingu poczty e-mail, takie jak reguły przesyłania dalej lub podpisy automatyczne, mogą powodować błędy DMARC przed dotarciem wiadomości e-mail do skrzynki pocztowej adresata. Dzięki funkcji ARC zachowanie kryptograficzne wyników uwierzytelniania umożliwia Microsoft 365 autentyczności nadawcy wiadomości e-mail.

Microsoft 365 obecnie używa funkcji ARC w celu zweryfikowania wyników uwierzytelniania, gdy firma Microsoft jest zaklejaczem ARC, ale planuje w przyszłości dodać obsługę zaklejek ARC innych firm.

## <a name="troubleshooting-your-dmarc-implementation"></a>Rozwiązywanie problemów z implementacją DMARC

Jeśli skonfigurowano rekordy MX domeny, w których program EOP nie jest pierwszym wpisem, błędy DMARC nie zostaną wymuszone dla domeny.

Jeśli jesteś klientem, a podstawowy rekord MX domeny nie wskaże usługi EOP, nie otrzymasz korzyści z usługi DMARC. Na przykład funkcja DMARC nie będzie działać, jeśli wskażesz rekord MX lokalnym serwerem poczty, a następnie przekierujesz pocztę e-mail do usługi EOP za pomocą łącznika. W tym scenariuszu domena odbierana jest jedną z domen, ale Accepted-Domains EOP nie jest podstawowym rekordem MX. Załóżmy na przykład, contoso.com sam rekord MX i używa usługi EOP jako pomocniczego rekordu MX, rekord MX domeny contoso.com wygląda następująco:

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

Wszystkie lub większość poczty e-mail będą najpierw kierowane mail.contoso.com, ponieważ jest to podstawowy rekord MX, a następnie poczta zostanie przekierowyowana do usługi EOP. W niektórych przypadkach możesz nawet nie wyświetlić usługi EOP jako rekordu MX i po prostu podłączyć łączniki w celu rozsyłania wiadomości e-mail. Program EOP nie musi być pierwszym wpisem do weryfikacji DMARC. Zapewnia jedynie sprawdzenie poprawności, aby mieć pewność, że wszystkie serwery lokalne/inne niż O365 będą przeprowadzać testy DMARC.  Podczas konfiguracji rekordu TXT DMARC dMARC można wymuszać na domenie klienta (nie na serwerze), ale w rzeczywistości to serwer odbierający musi wykonać wymuszenie.  Jeśli usługę EOP skonfigurujesz jako serwer odbierający, wówczas program EOP będzie wymuszał DMARC.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="Grafika rozwiązywania problemów dMARC dzięki uprzejmości Daniela Mande" lightbox="../../media/Tp_DMARCTroublehoot.png":::

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

Chcesz uzyskać więcej informacji na temat DMARC? Te zasoby mogą  pomóc.

- [Nagłówki wiadomości niezamówień spamu](anti-spam-message-headers.md) zawierają składnię i pola nagłówków używane przez program Microsoft 365 do sprawdzania funkcji DMARC.

- Skorzystaj z [serii szkoleń DMARC](https://www.m3aawg.org/activities/training/dmarc-training-series) z <sup>M3AAWG</sup> (Wiadomości, złośliwe oprogramowanie, grupa robocza ds. ochrony przed nadużyciami na urządzeniach przenośnych).

- Użyj listy kontrolnej w miejscu [dmarcian](https://space.dmarcian.com/deployment/).

- Przejdź bezpośrednio do [źródła w DMARC.org](https://dmarc.org).

## <a name="see-also"></a>Zobacz też

[Jak Microsoft 365 spf (Sender Policy Framework) w celu zapobiegania fałszowania](how-office-365-uses-spf-to-prevent-spoofing.md)

[**Konfigurowanie spf in Microsoft 365 to prevent spoofing**](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[**Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych z domeny niestandardowej w Microsoft 365**](use-dkim-to-validate-outbound-email.md)
