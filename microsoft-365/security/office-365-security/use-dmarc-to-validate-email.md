---
title: Weryfikowanie poczty e-mail, konfigurowanie kroków przy użyciu funkcji DMARC
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
description: Dowiedz się, jak skonfigurować oparte na domenie uwierzytelnianie komunikatów, raportowanie i zgodność (DMARC) w celu weryfikowania komunikatów wysyłanych z organizacji.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c10b1cc94f23e96d11a495b9b176d605cb2f3183
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972854"
---
# <a name="use-dmarc-to-validate-email"></a>Sprawdzanie poprawności poczty e-mail przy użyciu usługi DMARC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Uwierzytelnianie komunikatów oparte na domenie, raportowanie i zgodność ([DMARC](https://dmarc.org)) współdziała z platformami SPF (Sender Policy Framework) i DomainKeys Identified Mail (DKIM) w celu uwierzytelniania nadawców poczty i zapewnienia, że docelowe systemy poczty e-mail ufają wiadomościom wysyłanym z domeny. Implementacja DMARC za pomocą SPF i DKIM zapewnia dodatkową ochronę przed fałszowaniem i wyłudzaniem informacji za pomocą poczty e-mail. Usługa DMARC pomaga odbierać systemy poczty, aby określić, co zrobić z wiadomościami wysyłanymi z domeny, które nie sprawdzają SPF lub DKIM.

> [!TIP]
> Odwiedź katalog [Microsoft Intelligent Security Association (MISA),](https://www.microsoft.com/misapartnercatalog) aby wyświetlić dostawców innych firm oferujących raportowanie DMARC dla Microsoft 365.

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-microsoft-365"></a>Jak SPF i DMARC współpracują ze sobą w celu ochrony poczty e-mail w Microsoft 365?

 Wiadomość e-mail może zawierać wiele adresów inicjalatora lub nadawcy. Te adresy są używane do różnych celów. Rozważmy na przykład następujące adresy:

- **Adres "Mail From"**: identyfikuje nadawcę i określa, gdzie wysyłać powiadomienia zwrotne, jeśli wystąpią jakiekolwiek problemy z dostarczeniem wiadomości, takie jak powiadomienia o braku dostawy. Jest ona wyświetlana w części koperty wiadomości e-mail i nie jest wyświetlana przez aplikację poczty e-mail. Jest to czasami nazywane adresem 5321.MailFrom lub adresem odwrotnej ścieżki.

- **Adres "Od"**: adres wyświetlany jako adres od aplikacji poczty. Ten adres identyfikuje autora wiadomości e-mail. Oznacza to, że skrzynka pocztowa osoby lub systemu odpowiedzialnego za napisanie wiadomości. Jest to czasami nazywane adresem 5322.From.

SPF używa rekordu TXT DNS, aby podać listę autoryzowanych adresów IP wysyłania dla danej domeny. Zwykle kontrole SPF są wykonywane tylko względem adresu 5321.MailFrom. Oznacza to, że adres 5322.From nie jest uwierzytelniony, gdy używasz samego SPF. Umożliwia to scenariusz, w którym użytkownik może odbierać komunikat, który przekazuje test SPF, ale ma sfałszowany adres 5322.Z adresu nadawcy. Rozważmy na przykład tę transkrypcję SMTP:

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

W tej transkrypcji adresy nadawcy są następujące:

- Poczta z adresu (5321.MailFrom): phish@phishing.contoso.com

- Z adresu (5322.From): security@woodgrovebank.com

Jeśli skonfigurowano SPF, serwer odbierający wykonuje sprawdzanie poczty z adresu phish@phishing.contoso.com. Jeśli komunikat pochodzi z prawidłowego źródła phishing.contoso.com domeny, test SPF jest przekazywany. Ponieważ klient poczty e-mail wyświetla tylko adres Od, użytkownik widzi, że ta wiadomość pochodzi z security@woodgrovebank.com. W przypadku samego SPF ważność woodgrovebank.com nigdy nie została uwierzytelniona.

W przypadku korzystania z usługi DMARC serwer odbierający wykonuje również sprawdzanie adresu Od. Jeśli w powyższym przykładzie istnieje rekord DMARC TXT dla woodgrovebank.com, sprawdzanie adresu From kończy się niepowodzeniem.

## <a name="what-is-a-dmarc-txt-record"></a>Co to jest rekord DMARC TXT?

Podobnie jak rekordy DNS dla SPF, rekord DMARC jest rekordem tekstowym DNS (TXT), który pomaga zapobiegać fałszowaniu i wyłudzaniu informacji. Rekordy DMARC TXT są publikowane w systemie DNS. Rekordy TXT DMARC weryfikują pochodzenie wiadomości e-mail, sprawdzając adres IP autora wiadomości e-mail względem domniemanego właściciela domeny wysyłającej. Rekord DMARC TXT identyfikuje autoryzowane wychodzące serwery poczty e-mail. Docelowe systemy poczty e-mail mogą następnie sprawdzić, czy odbierane wiadomości pochodzą z autoryzowanych wychodzących serwerów poczty e-mail.

Rekord DMARC TXT firmy Microsoft wygląda mniej więcej tak:

```console
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.contoso.com; ruf=mailto:d@ruf.contoso.com; fo=1"
```

Aby uzyskać więcej dostawców innych firm, którzy oferują raportowanie DMARC dla Microsoft 365, odwiedź [katalog MISA](https://www.microsoft.com/misapartnercatalog?IntegratedProducts=DMARCReportingforOffice365).

## <a name="set-up-dmarc-for-inbound-mail"></a>Konfigurowanie usługi DMARC dla poczty przychodzącej

Nie musisz wykonywać żadnych czynności, aby skonfigurować usługę DMARC dla poczty otrzymanej w Microsoft 365. To wszystko jest pod opieką. Jeśli chcesz dowiedzieć się, co się stanie z pocztą, która nie przejdzie testów DMARC, zobacz [Jak Microsoft 365 obsługuje przychodzącą wiadomość e-mail, która kończy się niepowodzeniem DMARC.If](#how-microsoft-365-handles-inbound-email-that-fails-dmarc) you want to learn what happens to mail that fail to pass our DMARC checks, see How Microsoft 365 handles inbound email that fail DMARC.

## <a name="set-up-dmarc-for-outbound-mail-from-microsoft-365"></a>Konfigurowanie usługi DMARC dla poczty wychodzącej z Microsoft 365

Jeśli używasz Microsoft 365, ale nie używasz domeny niestandardowej, oznacza to, że używasz onmicrosoft.com, nie musisz wykonywać żadnych innych czynności, aby skonfigurować lub zaimplementować usługę DMARC dla swojej organizacji. SPF jest już skonfigurowany dla Ciebie i Microsoft 365 automatycznie generuje podpis DKIM dla poczty wychodzącej. Aby uzyskać więcej informacji na temat tego podpisu, zobacz [Domyślne zachowanie DKIM i Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

 Jeśli masz domenę niestandardową lub używasz lokalnych serwerów Exchange oprócz Microsoft 365, musisz ręcznie zaimplementować funkcję DMARC dla poczty wychodzącej. Implementacja usługi DMARC dla domeny niestandardowej obejmuje następujące kroki:

- [Krok 1. Identyfikowanie prawidłowych źródeł poczty dla domeny](#step-1-identify-valid-sources-of-mail-for-your-domain)

- [Krok 2. Konfigurowanie filtru SPF dla domeny](#step-2-set-up-spf-for-your-domain)

- [Krok 3. Konfigurowanie usługi DKIM dla domeny niestandardowej](#step-3-set-up-dkim-for-your-custom-domain)

- [Krok 4. Tworzenie rekordu DMARC TXT dla domeny](#step-4-form-the-dmarc-txt-record-for-your-domain)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>Krok 1. Identyfikowanie prawidłowych źródeł poczty dla domeny

Jeśli masz już skonfigurowaną platformę SPF, to już przeszło to ćwiczenie. Jednak w przypadku DMARC należy wziąć pod uwagę dodatkowe kwestie. Podczas identyfikowania źródeł poczty dla domeny należy odpowiedzieć na dwa pytania:

- Jakie adresy IP wysyłają komunikaty z mojej domeny?

- Czy adresy 5321.MailFrom i 5322.From są zgodne w przypadku wiadomości wysłanych od osób trzecich w moim imieniu?

### <a name="step-2-set-up-spf-for-your-domain"></a>Krok 2. Konfigurowanie filtru SPF dla domeny

Teraz, gdy masz listę wszystkich prawidłowych nadawców, możesz wykonać kroki opisane w [temacie Konfigurowanie filtru SPF, aby zapobiec fałszowaniu](set-up-spf-in-office-365-to-help-prevent-spoofing.md).

Na przykład przy założeniu, że contoso.com wysyła pocztę z Exchange Online, lokalnego serwera Exchange, którego adres IP to 192.168.0.1, oraz aplikacji internetowej, której adres IP to 192.168.100.100, rekord TXT SPF będzie wyglądać następująco:

```console
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

Najlepszym rozwiązaniem jest upewnienie się, że rekord SPF TXT uwzględnia nadawców innych firm.

### <a name="step-3-set-up-dkim-for-your-custom-domain"></a>Krok 3. Konfigurowanie usługi DKIM dla domeny niestandardowej

Po skonfigurowaniu SPF należy skonfigurować infrastrukturę DKIM. Program DKIM umożliwia dodanie podpisu cyfrowego do wiadomości e-mail w nagłówku wiadomości. Jeśli nie skonfigurujesz infrastruktury DKIM i zamiast tego zezwolisz Microsoft 365 na używanie domyślnej konfiguracji DKIM dla domeny, funkcja DMARC może zakończyć się niepowodzeniem. Dzieje się tak, ponieważ domyślna konfiguracja DKIM używa początkowej domeny onmicrosoft.com jako adresu 5322.From, a nie domeny niestandardowej. Wymusza to niezgodność między 5321.MailFrom i 5322.Z adresów we wszystkich wiadomościach e-mail wysłanych z domeny.

Jeśli masz nadawców innych firm, którzy wysyłają wiadomość e-mail w Twoim imieniu i wysyłaną przez nich wiadomość e-mail, niezgodnie z adresami 5321.MailFrom i 5322.From, DMARC zakończy się niepowodzeniem dla tej wiadomości e-mail. Aby tego uniknąć, należy skonfigurować usługę DKIM dla domeny specjalnie z tym nadawcą innej firmy. Umożliwia to Microsoft 365 uwierzytelnianie poczty e-mail z tej usługi innej firmy. Jednak umożliwia również innym, na przykład Yahoo, Gmail i Comcast, zweryfikowanie wiadomości e-mail wysłanych do nich przez inną firmę tak, jakby była wysyłana przez Ciebie pocztą e-mail. Jest to korzystne, ponieważ pozwala klientom na budowanie zaufania z domeną bez względu na to, gdzie znajduje się ich skrzynka pocztowa, a jednocześnie Microsoft 365 nie oznaczy wiadomości jako spamu z powodu fałszowania, ponieważ przekazuje testy uwierzytelniania dla twojej domeny.

Aby uzyskać instrukcje dotyczące konfigurowania modułu DKIM dla domeny, w tym sposobu konfigurowania modułu DKIM dla nadawców innych firm, aby mogli podszywać się pod twoją domenę, zobacz [Używanie modułu DKIM do weryfikowania wychodzących wiadomości e-mail wysyłanych z domeny niestandardowej](use-dkim-to-validate-outbound-email.md).

### <a name="step-4-form-the-dmarc-txt-record-for-your-domain"></a>Krok 4. Tworzenie rekordu DMARC TXT dla domeny

Chociaż istnieją inne opcje składni, które nie są wymienione tutaj, są to najczęściej używane opcje Microsoft 365. Sformatuj rekord DMARC TXT dla domeny w formacie:

```console
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

Gdzie:

- *domena* to domena, którą chcesz chronić. Domyślnie rekord chroni pocztę z domeny i wszystkich domen podrzędnych. Jeśli na przykład określisz \_dmarc.contoso.com, usługa DMARC chroni pocztę z domeny i wszystkich poddomen, takich jak housewares.contoso.com lub plumbing.contoso.com.

- *Czas wygaśnięcia* powinien zawsze odpowiadać jednej godzinie. Jednostka używana dla czasu wygaśnięcia(1 godzina), minut (60 minut) lub sekund (3600 sekund) będzie się różnić w zależności od rejestratora domeny.

- *pct=100* wskazuje, że ta reguła powinna być używana dla 100% wiadomości e-mail.

- *Zasady* określają zasady, które mają być przestrzegane przez serwer odbierający w przypadku niepowodzenia DMARC. Możesz ustawić zasady na brak, kwarantannę lub odrzucenie.

Aby uzyskać informacje na temat opcji do użycia, zapoznaj się z pojęciami w [temacie Najlepsze rozwiązania dotyczące implementowania DMARC w Microsoft 365](#best-practices-for-implementing-dmarc-in-microsoft-365).

Przykłady:

- Zasady ustawione na brak

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- Ustawienie zasad na kwarantannę

    ```console
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- Zasady ustawione na odrzucenie

    ```console
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

Po utworzeniu rekordu należy zaktualizować rekord u rejestratora domen.

## <a name="dmarc-mail-public-preview-feature"></a>Poczta DMARC (funkcja publicznej wersji zapoznawczej)

> [!CAUTION]
> Wiadomości e-mail mogą nie być wysyłane codziennie, a sam raport może ulec zmianie podczas publicznej wersji zapoznawczej. Zagregowane wiadomości e-mail raportu DMARC można oczekiwać od kont konsumentów (takich jak konta hotmail.com, outlook.com lub live.com).

W tym przykładzie rekord TXT DMARC: `dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1"`, możesz zobaczyć adres *rua* , w tym przypadku przetworzony przez firmę innej firmy Agari. Ten adres służy do wysyłania "zagregowanej opinii" do analizy i służy do generowania raportu.

> [!TIP]
> Odwiedź [katalog MISA,](https://www.microsoft.com/misapartnercatalog) aby wyświetlić więcej dostawców innych firm oferujących raportowanie DMARC dla Microsoft 365. Aby uzyskać więcej informacji na temat adresów "rua" DMARC, zobacz " [Domain-based Message Authentication, Reporting, and Conformance (DMARC) firmy IETF.org"](https://datatracker.ietf.org/doc/html/rfc7489) .

## <a name="best-practices-for-implementing-dmarc-in-microsoft-365"></a>Najlepsze rozwiązania dotyczące implementowania DMARC w Microsoft 365

Program DMARC można wdrażać stopniowo bez wpływu na pozostałą część przepływu poczty. Utwórz i zaimplementuj plan wdrożenia, który jest zgodny z tymi krokami. Przed przejściem do następnego kroku wykonaj każdy z tych kroków najpierw z domeną podrzędną, a następnie innymi domenami podrzędnymi, a na koniec z domeną najwyższego poziomu w organizacji.

1. Monitorowanie wpływu implementacji DMARC

    Zacznij od prostego rekordu trybu monitorowania dla domeny podrzędnej lub domeny, która żąda, aby odbiorcy DMARC wysyłali ci statystyki dotyczące komunikatów, które widzą przy użyciu tej domeny. Rekord trybu monitorowania jest rekordem TXT DMARC, który ma swoje zasady ustawione na brak (p=none). Wiele firm publikuje rekord DMARC TXT z p =none, ponieważ nie są pewni, ile wiadomości e-mail mogą stracić, publikując bardziej restrykcyjne zasady DMARC.

    Można to zrobić jeszcze przed zaimplementowaniem SPF lub DKIM w infrastrukturze obsługi komunikatów. Jednak nie będzie można skutecznie poddać kwarantannie ani odrzucać poczty przy użyciu funkcji DMARC, dopóki nie zaimplementujesz również SPF i DKIM. W miarę wprowadzania SPF i DKIM raporty generowane za pośrednictwem usługi DMARC udostępniają liczby i źródła komunikatów, które przechodzą te testy, oraz te, które tego nie zrobią. Możesz łatwo zobaczyć, jaka część legalnego ruchu jest lub nie jest przez nich objęta, i rozwiązać wszelkie problemy. Zaczniesz również widzieć, ile fałszywych wiadomości jest wysyłanych i skąd są wysyłane.

2. Żądanie, aby zewnętrzne systemy poczty zostały poddane kwarantannie pocztą, która kończy się niepowodzeniem DMARC

    Jeśli uważasz, że cały lub większość legalnego ruchu jest chroniony przez SPF i DKIM i rozumiesz wpływ implementacji DMARC, możesz zaimplementować zasady kwarantanny. Zasady kwarantanny to rekord TXT DMARC, który ma swoje zasady ustawione na kwarantannę (p=kwarantanna). W ten sposób prosisz odbiorców DMARC o umieszczenie komunikatów z domeny, które kończą się niepowodzeniem DMARC, do lokalnego odpowiednika folderu spamu zamiast skrzynek odbiorczych klientów.

3. Żądanie, aby zewnętrzne systemy poczty nie akceptować wiadomości, które nie DMARC

    Ostatnim krokiem jest zaimplementowanie zasad odrzucania. Zasady odrzucania to rekord TXT DMARC, który ma swoje zasady ustawione na odrzucenie (p=reject). Gdy to zrobisz, prosisz odbiorników DMARC, aby nie akceptowali komunikatów, które nie sprawdzają DMARC.

4. Jak skonfigurować DMARC dla poddomeny?

   Usługa DMARC jest implementowana przez opublikowanie zasad jako rekordu TXT w systemie DNS i jest hierarchiczna (na przykład zasady opublikowane dla contoso.com będą miały zastosowanie do sub.domain.contonos.com chyba że dla poddomeny jawnie zdefiniowano inne zasady). Jest to przydatne, ponieważ organizacje mogą być w stanie określić mniejszą liczbę rekordów DMARC wysokiego poziomu w celu szerszego pokrycia. Należy zadbać o skonfigurowanie jawnych rekordów DMARC poddomeny, w których domeny podrzędne nie mają dziedziczyć rekordu DMARC domeny najwyższego poziomu.

   Ponadto można dodać zasady typu symbolu wieloznacznego dla DMARC, gdy poddomeny nie powinny wysyłać wiadomości e-mail, dodając `sp=reject` wartość. Przykład:

   ```text
   _dmarc.contoso.com. TXT "v=DMARC1; p=reject; sp=reject; ruf=mailto:authfail@contoso.com; rua=mailto:aggrep@contoso.com"
   ```

## <a name="how-microsoft-365-handles-outbound-email-that-fails-dmarc"></a>Jak Microsoft 365 obsługuje wychodzącą wiadomość e-mail, która kończy się niepowodzeniem DMARC

Jeśli komunikat jest wychodzący z Microsoft 365 i kończy się niepowodzeniem DMARC, a zasady zostały ustawione na p=kwarantanna lub p=reject, komunikat jest kierowany przez [pulę dostarczania wysokiego ryzyka dla komunikatów wychodzących](high-risk-delivery-pool-for-outbound-messages.md). Wychodząca wiadomość e-mail nie jest zastępowana.

Jeśli opublikujesz zasady odrzucenia DMARC (p=reject), żaden inny klient w Microsoft 365 nie może podszyć się pod twoją domenę, ponieważ komunikaty nie będą mogły przekazać SPF lub DKIM dla twojej domeny podczas przekazywania komunikatu wychodzącego za pośrednictwem usługi. Jeśli jednak opublikujesz zasady odrzucania DMARC, ale nie masz wszystkich wiadomości e-mail uwierzytelnionych za pośrednictwem Microsoft 365, niektóre z nich mogą być oznaczone jako spam dla przychodzącej wiadomości e-mail (zgodnie z powyższym opisem) lub zostaną odrzucone, jeśli nie opublikujesz protokołu SPF i spróbujesz przekazać go wychodzącego za pośrednictwem usługi. Dzieje się tak na przykład w przypadku zapomnienia o uwzględnieniu niektórych adresów IP dla serwerów i aplikacji, które wysyłają pocztę w imieniu domeny podczas tworzenia rekordu DMARC TXT.

## <a name="how-microsoft-365-handles-inbound-email-that-fails-dmarc"></a>Jak Microsoft 365 obsługuje przychodzącą wiadomość e-mail, która kończy się niepowodzeniem DMARC

Jeśli zasady DMARC serwera wysyłającego to `p=reject`, [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) oznacza komunikat jako fałszywy zamiast odrzucać. Innymi słowy, w przypadku przychodzącej poczty e-mail Microsoft 365 traktuje `p=reject` i `p=quarantine` w ten sam sposób. Administratorzy mogą zdefiniować akcję do wykonania w przypadku komunikatów sklasyfikowanych jako fałszywe w ramach [zasad ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md).

Microsoft 365 jest skonfigurowany w ten sposób, ponieważ niektóre uzasadnione wiadomości e-mail mogą zakończyć się niepowodzeniem DMARC. Na przykład komunikat może zakończyć się niepowodzeniem DMARC, jeśli zostanie wysłany do listy adresowej, która następnie przekazuje wiadomość wszystkim uczestnikom listy. Jeśli Microsoft 365 odrzuci te wiadomości, użytkownicy mogą utracić legalną wiadomość e-mail i nie mieć możliwości jej pobrania. Zamiast tego te komunikaty nadal będą kończyć się niepowodzeniem DMARC, ale zostaną oznaczone jako spam i nie zostaną odrzucone. W razie potrzeby użytkownicy mogą nadal pobierać te komunikaty w skrzynce odbiorczej za pomocą następujących metod:

- Użytkownicy dodają bezpiecznych nadawców indywidualnie przy użyciu klienta poczty e-mail.

- Administratorzy mogą używać [analizy fałszowania](learn-about-spoof-intelligence.md) lub [listy dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md) , aby zezwalać na komunikaty od sfałszowanego nadawcy.

- Administratorzy tworzą regułę przepływu poczty Exchange (znaną również jako reguła transportu) dla wszystkich użytkowników, która zezwala na wiadomości dla tych konkretnych nadawców.

Aby uzyskać więcej informacji, zobacz [Tworzenie list bezpiecznych nadawców](create-safe-sender-lists-in-office-365.md).

## <a name="how-microsoft-365-utilizes-authenticated-received-chain-arc"></a>Jak Microsoft 365 korzysta z uwierzytelnionego odebranego łańcucha (ARC)

Wszystkie hostowane skrzynki pocztowe w Microsoft 365 będą teraz korzystać z usługi ARC z lepszą dostarczaniem wiadomości i ulepszoną ochroną przed fałszowaniem. Usługa ARC zachowuje wyniki uwierzytelniania poczty e-mail od wszystkich uczestniczących pośredników lub przeskoków, gdy wiadomość e-mail jest kierowana z serwera źródłowego do skrzynki pocztowej adresata. Przed użyciem usługi ARC modyfikacje wykonywane przez pośredników w routingu poczty e-mail, takie jak reguły przekazywania lub podpisy automatyczne, mogą powodować błędy DMARC do czasu, gdy wiadomość e-mail dotarła do skrzynki pocztowej adresata. Dzięki usłudze ARC kryptograficzne zachowanie wyników uwierzytelniania umożliwia Microsoft 365 zweryfikowanie autentyczności nadawcy wiadomości e-mail.

Microsoft 365 obecnie używa usługi ARC do weryfikowania wyników uwierzytelniania, gdy firma Microsoft jest uszczelniaczem ARC, ale planuje dodać obsługę uszczelniaczy ARC innych firm w przyszłości.

## <a name="troubleshooting-your-dmarc-implementation"></a>Rozwiązywanie problemów z implementacją DMARC

Jeśli skonfigurowano rekordy MX domeny, w których EOP nie jest pierwszym wpisem, błędy DMARC nie będą wymuszane dla twojej domeny.

Jeśli jesteś klientem, a podstawowy rekord MX domeny nie wskazuje na EOP, nie uzyskasz korzyści wynikających z funkcji DMARC. Na przykład funkcja DMARC nie będzie działać, jeśli wskażesz rekord MX do lokalnego serwera poczty, a następnie przekierujesz wiadomość e-mail do EOP przy użyciu łącznika. W tym scenariuszu domena odbierania jest jedną z twoich Accepted-Domains ale EOP nie jest podstawowym serwerem MX. Załóżmy na przykład, że contoso.com wskazuje swój MX na siebie i używa operacji EOP jako pomocniczego rekordu MX, rekord MX contoso.com wygląda następująco:

```console
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

Wszystkie lub większość wiadomości e-mail będą najpierw kierowane do mail.contoso.com, ponieważ jest to podstawowy serwer MX, a następnie poczta zostanie przekierowana do EOP. W niektórych przypadkach może nawet nie wyświetlać listy EOP jako rekordu MX w ogóle i po prostu podłączyć łączniki do kierowania wiadomości e-mail. EOP nie musi być pierwszym wpisem do weryfikacji DMARC do wykonania. Zapewnia tylko walidację, aby mieć pewność, że wszystkie serwery lokalne/inne niż O365 będą wykonywać testy DMARC.  Usługa DMARC kwalifikuje się do wymuszania dla domeny klienta (nie serwera) podczas konfigurowania rekordu DMARC TXT, ale faktyczne wykonanie wymuszania należy do serwera odbierającego.  Jeśli skonfigurowano funkcję EOP jako serwer odbierający, funkcja EOP wykonuje wymuszanie DMARC.

:::image type="content" source="../../media/Tp_DMARCTroublehoot.png" alt-text="Grafika rozwiązywania problemów dla usługi DMARC" lightbox="../../media/Tp_DMARCTroublehoot.png":::

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

Chcesz uzyskać więcej informacji na temat usługi DMARC? Te zasoby mogą pomóc.

- [Nagłówki wiadomości antyspamowych](anti-spam-message-headers.md) zawierają pola składni i nagłówków używane przez Microsoft 365 do sprawdzania DMARC.

- Weź udział w [serii szkoleń DMARC](https://www.m3aawg.org/activities/training/dmarc-training-series) od <sup>M3AAWG</sup> (Messaging, Malware, Mobile Anti-Abuse Working Group).

- Użyj listy kontrolnej w [dmarcian](https://space.dmarcian.com/deployment/).

- Przejdź bezpośrednio do źródła w [DMARC.org](https://dmarc.org).

## <a name="see-also"></a>Zobacz też

[Jak Microsoft 365 używa struktury zasad nadawcy (SPF), aby zapobiec fałszowaniu](how-office-365-uses-spf-to-prevent-spoofing.md)

[**Konfigurowanie SPF w Microsoft 365, aby zapobiec fałszowaniu**](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

[**Weryfikowanie wychodzących wiadomości e-mail wysyłanych z domeny niestandardowej w Microsoft 365 za pomocą modułu DKIM**](use-dkim-to-validate-outbound-email.md)
