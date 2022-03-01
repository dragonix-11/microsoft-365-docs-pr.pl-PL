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
description: Administratorzy mogą dowiedzieć się, jak program EOP używa uwierzytelniania poczty e-mail (SPF, DKIM i DMARC) w celu zapobiegania fałszaniu, wyłudzaniu informacji i spamowi.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c0e7bc2ddd620b454979418735fb6982b71501c3
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021310"
---
# <a name="email-authentication-in-eop"></a>Uwierzytelnianie poczty e-mail w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


Uwierzytelnianie wiadomości e-mail (nazywane także sprawdzaniem poprawności poczty e-mail) to grupa standardów, która próbuje zatrzymać fałszowanie (wiadomości e-mail od sfałszowanych nadawców). We wszystkich Microsoft 365 e-mail usługi EOP są weryfikowane za pomocą tych standardów:

- [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)
- [DKIM](use-dkim-to-validate-outbound-email.md)
- [DMARC](use-dmarc-to-validate-email.md)

Uwierzytelnianie wiadomości e-mail sprawdza, czy wiadomości e-mail od nadawcy (na przykład laura@contoso.com) są wiarygodne i pochodzą z oczekiwanych źródeł dla tej domeny poczty e-mail (na przykład contoso.com).

W dalszej części tego artykułu wyjaśniono, jak te technologie działają i jak są one używane przez usługę EOP do sprawdzania przychodzącej poczty e-mail.

## <a name="use-email-authentication-to-help-prevent-spoofing"></a>Używanie uwierzytelniania poczty e-mail w celu zapobiegania fałszersce

DMARC zapobiega fałszersce, analizując **adres Od** w wiadomościach. Adres **Od** to adres e-mail nadawcy, który jest wyświetlony w jego kliencie poczty e-mail. Docelowe organizacje poczty e-mail mogą również zweryfikować, czy domena poczty e-mail przeszła spf lub DKIM. Innymi słowy domena została uwierzytelniona, dlatego adres e-mail nadawcy nie jest fałszywy.

Rekordy DNS dla rekordów SPF, DKIM i DMARC (zbiorczo nazywane zasadami uwierzytelniania wiadomości e-mail) są opcjonalne. Domeny z silnymi zasadami uwierzytelniania poczty e-mail microsoft.com i skype.com są chronione przed fałszerstwom. Jednak domeny z słabymi zasadami uwierzytelniania poczty e-mail lub w ogóle nie mają żadnych zasad, są głównymi celami spoofed.

Od marca 2018 r. tylko 9% domen firm w rankingu Fortune 500 publikuje silne zasady uwierzytelniania poczty e-mail. Pozostałe 91% firm może być sfałszowanych przez atakującego. O ile nie istnieje inny mechanizm filtrowania poczty e-mail, wiadomości e-mail od sfałszowanych nadawców w tych domenach mogą być dostarczane do użytkowników.

![Zasady DMARC firm z listy Fortune 500.](../../media/84e77d34-2073-4a8e-9f39-f109b32d06df.jpg)

Proporcje małych i średnich firm, które publikują silne zasady uwierzytelniania poczty e-mail, są mniejsze. A w przypadku domen poczty e-mail poza Ameryką Północną i Europa Zachodnią liczba jest jeszcze mniejsza.

Brak silnych zasad uwierzytelniania poczty e-mail to duży problem. Mimo że organizacje mogą nie zrozumieć, jak działa uwierzytelnianie wiadomości e-mail, atakujący są w pełni zrozumiałi i mogą z nich korzystać. Ze względu na problemy związane z wyłudzaniem informacji i ograniczone wdrożenie silnych zasad uwierzytelniania wiadomości e-mail firma Microsoft używa niejawnego uwierzytelniania wiadomości e-mail *do sprawdzania* przychodzącej poczty e-mail.

Niejawne uwierzytelnianie wiadomości e-mail to rozszerzenie zasad zwykłego uwierzytelniania wiadomości e-mail. Rozszerzenia te obejmują: reputację nadawcy, historię nadawców, historię adresatów, analizę zachowania i inne zaawansowane techniki. W przypadku braku innych sygnałów z tych rozszerzeń wiadomości wysyłane z domen, które nie używają zasad uwierzytelniania poczty e-mail, będą oznaczane jako sfałszowane.

Aby zobaczyć ogólne ogłoszenie firmy Microsoft, zobacz [Sea of Phish Part 2 — Enhanced Anti-spoofing in Microsoft 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Schooling-A-Sea-of-Phish-Part-2-Enhanced-Anti-spoofing/ba-p/176209).

## <a name="composite-authentication"></a>Uwierzytelnianie złożone

Jeśli domena nie ma tradycyjnych rekordów SPF, DKIM i DMARC, te testy rekordu nie przekazują wystarczającej ilości informacji o stanie uwierzytelniania. Dlatego firma Microsoft opracowała algorytm do niejawnego uwierzytelniania wiadomości e-mail. Ten algorytm łączy wiele sygnałów w jedną wartość nazywaną _uwierzytelnianiem złożonym_ lub `compauth` krótko. Wartość `compauth` jest stemplowana w **nagłówku Authentication-Results (Wyniki** uwierzytelniania) w nagłówkach wiadomości.

```text
Authentication-Results:
   compauth=<fail | pass | softpass | none> reason=<yyy>
```

Te wartości wyjaśniono w [nagłówku wiadomości wyników uwierzytelniania](anti-spam-message-headers.md#authentication-results-message-header).

Aby ustalić, w jaki sposób nadawca jest sfałszowany, można też po jego Microsoft 365 nawet ustalić, że nadawca jest fałszywy.

## <a name="why-email-authentication-is-not-always-enough-to-stop-spoofing"></a>Dlaczego uwierzytelnianie pocztą e-mail nie zawsze wystarcza do zatrzymania fałszowania

Poleganie tylko na rekordach uwierzytelniania poczty e-mail w celu określenia, czy wiadomość przychodząca jest sfałszowana, ma następujące ograniczenia:

- Domena wysyłająca może nie zawierać wymaganych rekordów DNS lub rekordy są niepoprawnie skonfigurowane.

- Domena źródłowa prawidłowo skonfigurowała rekordy DNS, ale ta domena nie jest taka, jak domena w adresie Od. Spf i DKIM nie wymagają, aby domena używana w adresie Od. Rejestratorzy lub legalne usługi mogą zarejestrować domenę, skonfigurować SPF i DKIM dla tej domeny oraz użyć zupełnie innej domeny w adresie Od. Wiadomości od nadawców w tej domenie będą przekazywać dane SPF i DKIM.

Uwierzytelnianie złożone może rozwiązać te ograniczenia, przekazując wiadomości, które w przeciwnym razie nie będą sprawdzać uwierzytelniania wiadomości e-mail.

Poniższe przykłady skoncentrają się na wynikach uwierzytelniania wiadomości e-mail, na przykładach. Inne czynniki analizy back-end mogą identyfikować wiadomości, które przechodzą uwierzytelnianie poczty e-mail jako fałszywe, lub wiadomości, które nie uwierzytelniają poczty e-mail jako prawdziwe.

Na przykład domena fabrikam.com nie ma rekordów SPF, DKIM ani DMARC. Wiadomości od nadawców w domenie fabrikam.com mogą nie powieść uwierzytelniania złożonego (zwróć uwagę na `compauth` wartość i przyczynę):

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=none
  action=none header.from=fabrikam.com; compauth=fail reason=001
From: chris@fabrikam.com
To: michelle@contoso.com
```

Jeśli fabrikam.com rekord SPF bez rekordu DKIM, wiadomość może przejść uwierzytelnianie złożone. Domena, która przeszła testy SPF, jest wyrównana z domeną w adresie Od:

```text
Authentication-Results: spf=pass (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=bestguesspass
  action=none header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Jeśli fabrikam.com rekord DKIM bez rekordu SPF, wiadomość może przejść uwierzytelnianie złożone. Domena w podpisie DKIM jest wyrównana do domeny w adresie Od:

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=pass
  (signature was verified) header.d=outbound.fabrikam.com;
  contoso.com; dmarc=bestguesspass action=none
  header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Jeśli domena w mechanizmie SPF lub podpisie DKIM nie jest wyrównana z domeną w adresie Od, w komunikacie może się nie powieść uwierzytelnianie złożone:

```text
Authentication-Results: spf=none (sender IP is 192.168.1.8)
  smtp.mailfrom=maliciousdomain.com; contoso.com; dkim=pass
  (signature was verified) header.d=maliciousdomain.com;
  contoso.com; dmarc=none action=none header.from=contoso.com;
  compauth=fail reason=001
From: chris@contoso.com
To: michelle@fabrikam.com
```

## <a name="solutions-for-legitimate-senders-who-are-sending-unauthenticated-email"></a>Rozwiązania dla nadawców, którzy wysyłają nieuwierzytane wiadomości e-mail

Microsoft 365 informacji o tym, kto wysyła nieuwierzytowane wiadomości e-mail do Twojej organizacji. Jeśli usługa uważa, że nadawca nie jest legalny, oznaczy wiadomości od tego nadawcy jako złożony błąd uwierzytelniania. Aby uniknąć tego werdyktu, możesz skorzystać z zaleceń z tej sekcji.

### <a name="configure-email-authentication-for-domains-you-own"></a>Konfigurowanie uwierzytelniania poczty e-mail dla posiadanych domen

Ta metoda umożliwia rozwiązywanie problemów z spoofingiem wewnątrz organizacji i spoofingiem między domenami w przypadkach, gdy jesteś właścicielem wielu dzierżaw lub wchodzisz w interakcje z wieloma dzierżawami. Ułatwia to także rozwiązywanie fałszowania między domenami w przypadku wysyłania wiadomości do innych klientów w ramach usługi Microsoft 365 lub innych firm hostowanych przez innych dostawców.

- [Konfigurowanie rekordów SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md) dla swoich domen.
- [Konfigurowanie rekordów DKIM](use-dkim-to-validate-outbound-email.md) dla domen podstawowych.
- [Rozważ skonfigurowanie rekordów DMARC dla](use-dmarc-to-validate-email.md) swojej domeny w celu określenia legalnych nadawców.

Firma Microsoft nie dostarcza szczegółowych wytycznych dotyczących implementacji rekordów SPF, DKIM i DMARC. Dostępnych jest jednak wiele informacji w trybie online. Istnieją również inne firmy, które pomagają Twojej organizacji w skonfigurowaniu rekordów uwierzytelniania poczty e-mail.

#### <a name="you-dont-know-all-sources-for-your-email"></a>Nie znasz wszystkich źródeł wiadomości e-mail

Wiele domen nie publikuje rekordów SPF, ponieważ nie zna wszystkich źródeł poczty e-mail dla wiadomości w swojej domenie. Zacznij od opublikowania rekordu SPF zawierającego wszystkie źródła poczty e-mail, które znasz (zwłaszcza tam, gdzie znajduje się ruch firmowy `?all`), i opublikuj neutralne zasady SPF. Przykład:

```text
fabrikam.com IN TXT "v=spf1 include:spf.fabrikam.com ?all"
```

Ten przykład oznacza, że wiadomości e-mail z infrastruktury firmowej będą przechodzić przez uwierzytelnianie wiadomości e-mail, ale wiadomości e-mail z nieznanych źródeł wrócą do neutralności.

Microsoft 365 poczty przychodzącej z infrastruktury firmowej będą traktować jako uwierzytelnione. Wiadomości e-mail z niezidentyfikowanych źródeł mogą być nadal oznaczane jako fałsz, jeśli uwierzytelnianie niejawne nie powiedzie się. Jednak nadal jest to ulepszenie w przypadku wszystkich wiadomości e-mail oznaczanych jako fałszowane przez Microsoft 365.

Po zaczynaniu od zasad rezerwowych SPF `?all`usługi , możesz stopniowo wykrywać i dołączać więcej źródeł poczty e-mail dla wiadomości, a następnie aktualizować rekord SPF przy użyciu bardziej rygorystycznych zasad.

### <a name="configure-permitted-senders-of-unauthenticated-email"></a>Konfigurowanie dozwolonych nadawców nieuwierzytanych wiadomości e-mail

Aby umożliwić nadawcom przesyłanie [](learn-about-spoof-intelligence.md) nieuwierzytanych wiadomości do organizacji, możesz również użyć szczegółowych informacji o analizie fałszowania oraz listy zezwalania [na blokowanie/](tenant-allow-block-list.md)zezwalanie nadawcom na przesyłanie nieuwierzytanych wiadomości.

W przypadku domen zewnętrznych sfałszowany użytkownik to domena w adresie Od, a infrastruktura wysyłania to źródłowy adres IP (podzielony na zakresy CIDR /24) lub domena organizacji odwrotnego rekordu DNS (PTR).

### <a name="create-an-allow-entry-for-the-senderrecipient-pair"></a>Tworzenie wpisu zezwalania dla pary nadawca/adresat

Aby pominąć filtrowanie spamu, niektóre części filtrowania w celu wyłudzania informacji, ale bez filtrowania złośliwego oprogramowania u określonych nadawców, zobacz Tworzenie list bezpiecznych nadawców w [programie Microsoft 365](create-safe-sender-lists-in-office-365.md).

### <a name="ask-the-sender-to-configure-email-authentication-for-domains-you-dont-own"></a>Poproś nadawcę o skonfigurowanie uwierzytelniania poczty e-mail dla domen, które nie są Właścicielami

Ze względu na problem ze spamem i wyłudzaniem informacji firma Microsoft zaleca uwierzytelnianie wiadomości e-mail dla wszystkich organizacji poczty e-mail. Zamiast konfigurować ręczne zastępowanie w organizacji, możesz poprosić administratora w domenie wysyłającej o skonfigurowanie rekordów uwierzytelniania poczty e-mail.

- Nawet jeśli w przeszłości nie musieli oni publikować rekordów uwierzytelniania poczty e-mail, powinni to zrobić, jeśli wysyłają wiadomości e-mail do firmy Microsoft.

- Skonfiguruj spf (SPF) w celu publikowania wysyłających adresów IP domeny i skonfiguruj DKIM (jeśli jest dostępny) do cyfrowego podpisywania wiadomości. Powinni również rozważyć skonfigurowanie rekordów DMARC.

- Jeśli wysyłają wiadomości e-mail w ich imieniu za pomocą nadawców zbiorczych, upewnij się, że domena w adresie Od (jeśli należy do nich) jest wyrównana z domeną, która przekazuje rekord SPF lub DMARC.

- Sprawdź, czy następujące lokalizacje (jeśli je używają) są uwzględnione w rekordzie SPF:

  - Lokalne serwery poczty e-mail.
  - Wiadomość e-mail wysłana od dostawcy oprogramowania jako usługi (SaaS).
  - Wiadomości e-mail wysyłane z usługi hostingu w chmurze (Microsoft Azure, GoDaddy, Rackspace, Amazon Web Services itp.).

- W przypadku małych domen hostowanych przez isp skonfiguruj rekord SPF zgodnie z instrukcjami podanymi przez tego isp.

Chociaż na początku wysyłanie domen może być trudne w celu uwierzytelnienia, ponieważ coraz więcej filtrów wiadomości e-mail zaczyna wiadomości-śmieci, a nawet odrzuca ich wiadomości e-mail, jednak w ich przypadku należy skonfigurować odpowiednie rekordy, aby zapewnić lepsze dostarczanie. Ich uczestnictwo może także pomóc w zwalczaniu wyłudzania informacji i ograniczać możliwość wyłudzania informacji w organizacji lub organizacjach, do których wysyłają wiadomości e-mail.

#### <a name="information-for-infrastructure-providers-isps-esps-or-cloud-hosting-services"></a>Informacje dla dostawców infrastruktury (usługodawców internetowych usług internetowych lub usług hostingu w chmurze)

Jeśli hostowasz pocztę e-mail domeny lub zapewniasz infrastrukturę hostingu, która może wysyłać wiadomości e-mail, wykonaj następujące czynności:

- Zapewnij klientom dokumentację wyjaśniającą sposób konfigurowania rekordów SPF przez klientów

- Rozważ podpisywanie podpisów DKIM w wychodzących wiadomościach e-mail, nawet jeśli klient nie ustawi jej jawnie (zaloguj się przy użyciu domeny domyślnej). Możesz nawet podpisać dwukrotnie wiadomość e-mail przy użyciu podpisów DKIM (raz z domeną klienta, jeśli został on przez niego ustawiony, i drugi raz przy użyciu podpisu DKIM Twojej firmy)

Dostarczanie wiadomości do firmy Microsoft nie jest gwarantowane, nawet jeśli uwierzytelniasz wiadomości e-mail pochodzące z Twojej platformy, ale przynajmniej zapewnia, że firma Microsoft nie będzie wiadomości-śmieciem, ponieważ nie została uwierzytelniona.

## <a name="related-links"></a>Linki pokrewne

Aby uzyskać więcej informacji o najlepszych rozwiązaniach dotyczących dostawców usług, zobacz Najlepsze rozwiązania dotyczące wiadomości mobilnych [M3AAWG dla dostawców usług](https://www.m3aawg.org/sites/default/files/m3aawg-mobile-messaging-best-practices-service-providers-2015-08_0.pdf).

Dowiedz się, Office 365 spf i obsługuje sprawdzanie poprawności DKIM:

- [Więcej informacji o SPF](how-office-365-uses-spf-to-prevent-spoofing.md)

- [Więcej informacji na temat DKIM](support-for-validation-of-dkim-signed-messages.md)
