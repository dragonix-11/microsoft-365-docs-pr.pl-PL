---
title: Uwierzytelnianie poczty e-mail w Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- Strat_O365_IP
ms.custom: TopSMBIssues
ms.localizationpriority: high
description: Administratorzy mogą dowiedzieć się, jak usługa EOP używa uwierzytelniania poczty e-mail (SPF, DKIM i DMARC), aby zapobiec fałszowaniu, wyłudzaniu informacji i spamowi.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2b0a1f1bec76a8dd22bc04502ea7ca09f2c7af66
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772779"
---
# <a name="email-authentication-in-eop"></a>Uwierzytelnianie za pomocą poczty e-mail w ramach EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Uwierzytelnianie poczty e-mail (nazywane również weryfikacją poczty e-mail) to grupa standardów, która próbuje zatrzymać fałszowanie (wiadomości e-mail od sfałszowanych nadawców). We wszystkich organizacjach Microsoft 365 EOP używa tych standardów do weryfikowania przychodzącej poczty e-mail:

- [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)
- [DKIM](use-dkim-to-validate-outbound-email.md)
- [DMARC](use-dmarc-to-validate-email.md)

Uwierzytelnianie poczty e-mail sprawdza, czy wiadomości e-mail od nadawcy (na przykład laura@contoso.com) są uzasadnione i pochodzą z oczekiwanych źródeł dla tej domeny poczty e-mail (na przykład contoso.com).

W pozostałej części tego artykułu wyjaśniono, jak działają te technologie i jak EOP używa ich do sprawdzania przychodzącej poczty e-mail.

## <a name="use-email-authentication-to-help-prevent-spoofing"></a>Używanie uwierzytelniania za pomocą poczty e-mail w celu zapobiegania fałszowaniu

Funkcja DMARC uniemożliwia fałszowanie, sprawdzając adres **Od** w komunikatach. Adres **Od** to adres e-mail nadawcy, który użytkownicy widzą w kliencie poczty e-mail. Docelowe organizacje poczty e-mail mogą również sprawdzić, czy domena poczty e-mail przeszła przez protokół SPF lub DKIM. Innymi słowy, domena została uwierzytelniona i dlatego adres e-mail nadawcy nie jest sfałszowany.

Jednak rekordy DNS dla SPF, DKIM i DMARC (łącznie znane jako zasady uwierzytelniania poczty e-mail) są opcjonalne. Domeny z silnymi zasadami uwierzytelniania poczty e-mail, takimi jak microsoft.com i skype.com, są chronione przed fałszowaniem. Jednak domeny ze słabszymi zasadami uwierzytelniania poczty e-mail lub bez żadnych zasad są głównymi celami fałszowania.

Od marca 2018 r. tylko 9% domen firm z listy Fortune 500 publikuje zasady silnego uwierzytelniania poczty e-mail. Pozostałe 91% firm może zostać sfałszowanych przez osobę atakującą. Jeśli inny mechanizm filtrowania poczty e-mail nie jest w miejscu, wiadomości e-mail od sfałszowanych nadawców w tych domenach mogą być dostarczane do użytkowników.

![Zasady DMARC firm z listy Fortune 500.](../../media/84e77d34-2073-4a8e-9f39-f109b32d06df.jpg)

Odsetek małych i średnich firm, które publikują zasady silnego uwierzytelniania poczty e-mail, jest mniejszy. A liczba ta jest jeszcze mniejsza w przypadku domen poczty e-mail spoza Ameryka Północna i Europy Zachodniej.

Brak silnych zasad uwierzytelniania poczty e-mail to duży problem. Chociaż organizacje mogą nie zrozumieć, jak działa uwierzytelnianie poczty e-mail, osoby atakujące w pełni rozumieją i korzystają z tej możliwości. Ze względu na problemy z wyłudzaniem informacji i ograniczone wdrożenie zasad silnego uwierzytelniania poczty *e-mail firma Microsoft używa niejawnego uwierzytelniania poczty e-mail* do sprawdzania przychodzącej poczty e-mail.

Niejawne uwierzytelnianie poczty e-mail jest rozszerzeniem zasad regularnego uwierzytelniania poczty e-mail. Te rozszerzenia obejmują: reputację nadawcy, historię nadawcy, historię adresata, analizę behawioralną i inne zaawansowane techniki. W przypadku braku innych sygnałów z tych rozszerzeń komunikaty wysyłane z domen, które nie korzystają z zasad uwierzytelniania poczty e-mail, zostaną oznaczone jako fałszywe.

Aby zobaczyć ogólne ogłoszenie firmy Microsoft, zobacz [A Sea of Phish Part 2 — Enhanced Anti-spoofing in Microsoft 365 (Morze Phish— część 2 — ulepszone fałszowanie w Microsoft 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Schooling-A-Sea-of-Phish-Part-2-Enhanced-Anti-spoofing/ba-p/176209)).

## <a name="composite-authentication"></a>Uwierzytelnianie złożone

Jeśli domena nie ma tradycyjnych rekordów SPF, DKIM i DMARC, te kontrole rekordów nie komunikują wystarczającej ilości informacji o stanie uwierzytelniania. W związku z tym firma Microsoft opracowała algorytm niejawnego uwierzytelniania poczty e-mail. Ten algorytm łączy wiele sygnałów w pojedynczą wartość nazywaną _uwierzytelnianiem złożonym_ lub `compauth` w skrócie. Wartość `compauth` jest ostemplowana w nagłówku **Authentication-Results** w nagłówkach wiadomości.

```text
Authentication-Results:
   compauth=<fail | pass | softpass | none> reason=<yyy>
```

Te wartości zostały wyjaśnione w [nagłówku komunikatu Authentication-results](anti-spam-message-headers.md#authentication-results-message-header).

Sprawdzając nagłówki komunikatów, administratorzy, a nawet użytkownicy końcowi mogą określić, w jaki sposób Microsoft 365 ustalić, że nadawca jest sfałszowany.

## <a name="why-email-authentication-is-not-always-enough-to-stop-spoofing"></a>Dlaczego uwierzytelnianie za pomocą poczty e-mail nie zawsze wystarczy, aby zatrzymać fałszowanie

Poleganie tylko na rekordach uwierzytelniania poczty e-mail w celu określenia, czy wiadomość przychodząca jest sfałszowana, ma następujące ograniczenia:

- Domena wysyłająca może nie mieć wymaganych rekordów DNS lub rekordy są niepoprawnie skonfigurowane.

- Domena źródłowa prawidłowo skonfigurowała rekordy DNS, ale ta domena nie jest zgodna z domeną w polu Adres od. SPF i DKIM nie wymagają, aby domena była używana w polu Adres od. Osoby atakujące lub uprawnione usługi mogą zarejestrować domenę, skonfigurować SPF i DKIM dla domeny i użyć zupełnie innej domeny w polu Adres od. Komunikaty od nadawców w tej domenie będą przekazywane przez SPF i DKIM.

Uwierzytelnianie złożone może rozwiązać te ograniczenia, przekazując komunikaty, które w przeciwnym razie nie będą sprawdzać uwierzytelniania poczty e-mail.

Dla uproszczenia poniższe przykłady koncentrują się na wynikach uwierzytelniania poczty e-mail. Inne czynniki analizy zaplecza mogą identyfikować wiadomości, które przekazują uwierzytelnianie poczty e-mail jako sfałszowane, lub wiadomości, które nie uwierzytelniania poczty e-mail są uzasadnione.

Na przykład domena fabrikam.com nie ma rekordów SPF, DKIM ani DMARC. Komunikaty od nadawców w domenie fabrikam.com mogą zakończyć się niepowodzeniem uwierzytelniania złożonego (zanotuj wartość i przyczynę `compauth` ):

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=none
  action=none header.from=fabrikam.com; compauth=fail reason=001
From: chris@fabrikam.com
To: michelle@contoso.com
```

Jeśli fabrikam.com konfiguruje SPF bez rekordu DKIM, komunikat może przekazać uwierzytelnianie złożone. Domena, która przeszła testy SPF, jest zgodna z domeną w polu Adres od:

```text
Authentication-Results: spf=pass (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=bestguesspass
  action=none header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Jeśli fabrikam.com konfiguruje rekord DKIM bez rekordu SPF, komunikat może przekazać uwierzytelnianie złożone. Domena w sygnaturze DKIM jest zgodna z domeną w polu Adres od:

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=pass
  (signature was verified) header.d=outbound.fabrikam.com;
  contoso.com; dmarc=bestguesspass action=none
  header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Jeśli domena w SPF lub podpis DKIM nie jest zgodna z domeną w adresie Od, komunikat może zakończyć się niepowodzeniem uwierzytelniania złożonego:

```text
Authentication-Results: spf=none (sender IP is 192.168.1.8)
  smtp.mailfrom=maliciousdomain.com; contoso.com; dkim=pass
  (signature was verified) header.d=maliciousdomain.com;
  contoso.com; dmarc=none action=none header.from=contoso.com;
  compauth=fail reason=001
From: chris@contoso.com
To: michelle@fabrikam.com
```

## <a name="solutions-for-legitimate-senders-who-are-sending-unauthenticated-email"></a>Rozwiązania dla legalnych nadawców, którzy wysyłają nieuwierzytelnioną wiadomość e-mail

Microsoft 365 śledzi, kto wysyła nieuwierzytelnioną wiadomość e-mail do organizacji. Jeśli usługa uważa, że nadawca nie jest zgodny z prawem, oznacza komunikaty od tego nadawcy jako błąd uwierzytelniania złożonego. Aby uniknąć tego werdyktu, możesz użyć zaleceń w tej sekcji.

### <a name="configure-email-authentication-for-domains-you-own"></a>Konfigurowanie uwierzytelniania poczty e-mail dla domen, których jesteś właścicielem

Ta metoda umożliwia rozwiązywanie problemów z fałszowaniem wewnątrz organizacji i fałszowaniem między domenami w przypadkach, gdy jesteś właścicielem wielu dzierżaw lub wchodzisz w interakcje z wieloma dzierżawami. Pomaga również rozwiązać problem fałszowania między domenami, w którym wysyła się do innych klientów w ramach Microsoft 365 lub innych firm hostowanych przez innych dostawców.

- [Skonfiguruj rekordy SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md) dla domen.
- [Skonfiguruj rekordy DKIM](use-dkim-to-validate-outbound-email.md) dla domen podstawowych.
- [Rozważ skonfigurowanie rekordów DMARC](use-dmarc-to-validate-email.md) dla domeny w celu określenia legalnych nadawców.

Firma Microsoft nie udostępnia szczegółowych wytycznych dotyczących implementacji rekordów SPF, DKIM i DMARC. Istnieje jednak wiele informacji dostępnych online. Istnieją również firmy innych firm, które ułatwiają organizacji konfigurowanie rekordów uwierzytelniania poczty e-mail.

#### <a name="you-dont-know-all-sources-for-your-email"></a>Nie znasz wszystkich źródeł wiadomości e-mail

Wiele domen nie publikuje rekordów SPF, ponieważ nie znają wszystkich źródeł wiadomości e-mail dla wiadomości w swojej domenie. Rozpocznij od opublikowania rekordu SPF zawierającego wszystkie znane źródła poczty e-mail (szczególnie w przypadku lokalizacji ruchu firmowego) i opublikowania neutralnych zasad `?all`SPF. Przykład:

```text
fabrikam.com IN TXT "v=spf1 include:spf.fabrikam.com ?all"
```

Ten przykład oznacza, że poczta e-mail z infrastruktury firmowej będzie przekazywać uwierzytelnianie za pośrednictwem poczty e-mail, ale poczta e-mail z nieznanych źródeł powróci do neutralnego poziomu.

Microsoft 365 będzie traktować przychodzące wiadomości e-mail z infrastruktury firmowej jako uwierzytelnione. Wiadomość e-mail z niezidentyfikowanych źródeł może nadal być oznaczona jako sfałszowana, jeśli nie powiedzie się uwierzytelnianie niejawne. Jednak nadal jest to poprawa w stosunku do wszystkich wiadomości e-mail oznaczonych jako fałszywe przez Microsoft 365.

Po rozpoczęciu pracy z rezerwowymi zasadami `?all`SPF programu można stopniowo odnajdywać i dołączać więcej źródeł wiadomości e-mail, a następnie aktualizować rekord SPF przy użyciu bardziej rygorystycznych zasad.

### <a name="configure-permitted-senders-of-unauthenticated-email"></a>Konfigurowanie dozwolonych nadawców nieuwierzytelnionych wiadomości e-mail

Możesz również użyć [analizy fałszowania](learn-about-spoof-intelligence.md) i [listy dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md) , aby umożliwić nadawcom przesyłanie nieuwierzytelnionych komunikatów do organizacji.

W przypadku domen zewnętrznych sfałszowany użytkownik jest domeną w polu Adres od, a infrastruktura wysyłania jest jedną z następujących wartości:

- Źródłowy adres IP (podzielony na zakresy CIDR /24)
- Domena organizacyjna odwrotnego rekordu DNS (PTR).
- Zweryfikowana domena DKIM.

### <a name="create-an-allow-entry-for-the-senderrecipient-pair"></a>Tworzenie wpisu zezwalania dla pary nadawcy/odbiorcy

Aby pominąć filtrowanie spamu, niektóre części filtrowania pod kątem wyłudzania informacji, ale nie filtrowania złośliwego oprogramowania dla określonych nadawców, zobacz [Tworzenie list bezpiecznych nadawców w Microsoft 365](create-safe-sender-lists-in-office-365.md).

### <a name="ask-the-sender-to-configure-email-authentication-for-domains-you-dont-own"></a>Poproś nadawcę o skonfigurowanie uwierzytelniania poczty e-mail dla domen, których nie jesteś właścicielem

Ze względu na problem ze spamem i wyłudzaniem informacji firma Microsoft zaleca uwierzytelnianie poczty e-mail dla wszystkich organizacji poczty e-mail. Zamiast konfigurować ręczne przesłonięcia w organizacji, możesz poprosić administratora w domenie wysyłającej o skonfigurowanie rekordów uwierzytelniania poczty e-mail.

- Nawet jeśli w przeszłości nie musieli publikować rekordów uwierzytelniania poczty e-mail, powinni to zrobić, jeśli wysyłają wiadomość e-mail do firmy Microsoft.

- Skonfiguruj SPF, aby opublikować adresy IP wysyłające domenę, i skonfiguruj usługę DKIM (jeśli jest dostępna), aby cyfrowo podpisywać komunikaty. Należy również rozważyć skonfigurowanie rekordów DMARC.

- Jeśli używają nadawców zbiorczych do wysyłania wiadomości e-mail w ich imieniu, sprawdź, czy domena w adresie Od (jeśli należy do nich) jest zgodna z domeną, która przekazuje protokół SPF lub DMARC.

- Sprawdź, czy następujące lokalizacje (jeśli ich używają) są uwzględnione w rekordzie SPF:

  - Lokalne serwery poczty e-mail.
  - Wiadomość e-mail wysłana od dostawcy oprogramowania jako usługi (SaaS).
  - Wiadomość e-mail wysłana z usługi hostingu w chmurze (Microsoft Azure, GoDaddy, Rackspace, Amazon Web Services itp.).

- W przypadku małych domen hostowanych przez usługodawcę sieciowego skonfiguruj rekord SPF zgodnie z instrukcjami usługodawcy isp.

Chociaż na początku może być trudno uzyskać wysyłanie domen w celu uwierzytelnienia, ponieważ coraz więcej filtrów poczty e-mail zaczyna usuwać wiadomości e-mail, a nawet odrzucać ich pocztę e-mail, spowoduje to skonfigurowanie odpowiednich rekordów w celu zapewnienia lepszego dostarczania. Ponadto ich udział może pomóc w walce z wyłudzaniem informacji i może zmniejszyć możliwość wyłudzania informacji w organizacji lub organizacjach, do których wysyła wiadomości e-mail.

#### <a name="information-for-infrastructure-providers-isps-esps-or-cloud-hosting-services"></a>Informacje dla dostawców infrastruktury (usługodawców internetowych, dostawców usług internetowych lub usług hostingu w chmurze)

Jeśli hostujesz adres e-mail domeny lub udostępniasz infrastrukturę hostingu, która może wysyłać wiadomości e-mail, wykonaj następujące czynności:

- Upewnij się, że klienci mają dokumentację wyjaśniającą, jak klienci powinni konfigurować rekordy SPF

- Rozważ podpisanie podpisywania podpisów DKIM w wychodzącej wiadomości e-mail, nawet jeśli klient nie jawnie go skonfigurował (zaloguj się przy użyciu domeny domyślnej). Możesz nawet dwukrotnie podpisać wiadomość e-mail przy użyciu podpisów DKIM (raz z domeną klienta, jeśli została skonfigurowana, i po raz drugi z podpisem DKIM firmy)

Dostarczenie do firmy Microsoft nie jest gwarantowane nawet w przypadku uwierzytelniania poczty e-mail pochodzącej z platformy, ale przynajmniej gwarantuje, że firma Microsoft nie wysyła wiadomości e-mail, ponieważ nie jest uwierzytelniona.

## <a name="related-links"></a>Linki pokrewne

Aby uzyskać więcej informacji na temat najlepszych rozwiązań dla dostawców usług, zobacz [M3AAWG Mobile Messaging Best Practices for Service Providers (Najlepsze rozwiązania dotyczące obsługi komunikatów mobilnych M3AAWG dla dostawców usług](https://www.m3aawg.org/sites/default/files/m3aawg-mobile-messaging-best-practices-service-providers-2015-08_0.pdf)).

Dowiedz się, jak Office 365 używa SPF i obsługuje walidację DKIM:

- [Więcej informacji o platformie SPF](how-office-365-uses-spf-to-prevent-spoofing.md)

- [Więcej informacji o infrastrukturze DKIM](support-for-validation-of-dkim-signed-messages.md)
