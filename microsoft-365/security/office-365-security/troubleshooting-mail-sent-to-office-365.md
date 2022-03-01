---
title: Rozwiązywanie problemów z wiadomościami wysyłanymi na Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: f4caa4e1-e414-4b21-8822-31c08064c059
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Ten artykuł zawiera informacje dotyczące rozwiązywania problemów z wysyłaniem wiadomości e-mail do skrzynek Microsoft 365 & i najlepsze rozwiązania dotyczące zbiorczej wysyłki do Microsoft 365 klientów.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f5fe128989b66f110899e6af08180e830319b739
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006579"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Rozwiązywanie problemów z wiadomościami wysyłanymi na Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów nadawców, którzy mają problemy podczas próby wysłania wiadomości e-mail do skrzynek pocztowych w programie Microsoft 365, oraz najlepsze rozwiązania dotyczące zbiorczej wysyłki poczty do klientów.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>Zarządzasz swoją reputacją wysyłania adresu IP i domeny?

Technologie filtrowania EOP są zaprojektowane w taki sposób, aby zapewnić ochronę przed spamem Microsoft 365 innych produktów firmy Microsoft, takich jak Exchange Server. Używamy również funkcji SPF, DKIM i DMARC. technologie uwierzytelniania poczty e-mail, które pomagają rozwiązać problem fałszowania i wyłudzania informacji przez sprawdzenie, czy domena wysyłająca wiadomości e-mail jest do tego upoważniona. Filtrowanie usługi EOP ma wpływ na wiele czynników związanych z wysyłającym adresem IP, domeną, uwierzytelnianiem, dokładnością list, stawkami za skargi, zawartością i nie tylko. Jeden z nich to jeden z głównych czynników wpływa na wpływanie na reputację nadawcy oraz na możliwość dostarczania wiadomości e-mail przez jego nadawcę.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Wysyłasz wiadomości e-mail z nowych adresów IP?

Adresy IP, które nie były wcześniej używane do wysyłania wiadomości e-mail, zwykle nie mają żadnej reputacji wbudowanej w nasze systemy. W efekcie wiadomości e-mail z nowych adresów IP najprawdopodobniej doświadczą problemów z dostarczaniem. Gdy adres IP sbuduje reputację, która nie wysyła spamu, usługi EOP zwykle pozwalają na lepsze dostarczanie wiadomości e-mail.

Nowe rekordy IP dodawane dla domen uwierzytelnionych w ramach istniejących rekordów SPF zwykle mają dodatkową zaletę dziedziczenia części reputacji wysyłania domeny. Jeśli Twoja domena ma dobrą reputację wysyłania nowych ip, może to przyspieszyć twoją pracę. Nowe adresy IP mogą być w pełni objęte w ciągu kilku tygodni lub szybciej, w zależności od ilości liczby adresów IP, dokładności list i stawek za skargi przed wiadomościami-śmieciami.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>Potwierdzanie, że system DNS jest poprawnie skonfigurowany

Aby uzyskać instrukcje dotyczące tworzenia i utrzymywania rekordów DNS, w tym rekordu MX wymaganego do routingu poczty, musisz skontaktować się z dostawcą hostingu DNS.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Upewnij się, że nie ogłaszasz się jako nie routowalnych adresów IP

Nie możemy akceptować wiadomości e-mail od nadawców, którzy nie przejdą wyszukiwania odwrotnego DNS. W niektórych przypadkach legalni nadawcy ogłaszają się niepoprawnie jako nieistniejące internetowe adresy IP routowalne podczas próby otwarcia połączenia z usługą EOP. Adresy IP, które są zarezerwowane dla sieci prywatnych (nie routowalnych), to:

- 192.168.0.0/16 (lub 192.168.0.0 – 192.168.255.255)
- 10.0.0.0/8 (lub 10.0.0.0 – 10.255.255.255)
- 172.16.0.0/11 (lub 172.16.0.0 – 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Raport o niedostarczeniu (NDR, non-delivery report) został odebrany podczas wysyłania wiadomości e-mail do użytkownika w Office 365

Niektóre problemy z dostarczaniem są wynikiem zablokowania adresu IP nadawcy przez firmę Microsoft lub ze względu na to, że konto użytkownika zostało zidentyfikowane jako zablokowane z powodu poprzedniej aktywności dotyczącej spamu. Jeśli uważasz, że raport o niedostarczeniu został wyświetlony w błędzie, najpierw postępuj zgodnie z instrukcjami podanymi w komunikacie o niedostarczeniu, aby rozwiązać ten problem.

Aby uzyskać więcej informacji o otrzymanym błędzie, zobacz listę kodów błędów w tece Raporty o [niedotrzymywaniu poczty e-mail w programie Exchange Online](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

 Jeśli na przykład otrzymasz następujący komunikat o niedostarczeniu, oznacza to, że wysyłający adres IP został zablokowany przez firmę Microsoft:

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Aby zażądać usunięcia z tej listy, możesz użyć [portalu delist, aby usunąć siebie z listy zablokowanych nadawców](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>Wiadomości e-mail trafione do folderu wiadomości-śmieci adresata

Jeśli wiadomość została niepoprawnie zidentyfikowany przez usługę EOP jako spam, możesz we współpracy z adresatem przesłać tę wiadomość fałszywie dodatnią do zespołu analizy spamu firmy Microsoft, który będzie oceniać i analizować wiadomość. Aby uzyskać więcej informacji, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>Ruch z mojego adresu IP jest ograniczany przez usługę EOP

Jeśli otrzymasz powiadomienie o niedostarczeniu od usługi EOP wskazujące, że twój adres IP jest ograniczany przez usługę EOP, na przykład:

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

Otrzymano zgłoszenie o niedostarczeniu, ponieważ podejrzana aktywność została wykryta z adresu IP i została tymczasowo ograniczona do czasu jego dalszej oceny. Jeśli podejrzenie jest wyczyszczyszona w ramach oceny, wkrótce to ograniczenie zostanie podniesione.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Nie mogę odbierać wiadomości e-mail od nadawców w Microsoft 365

 Aby otrzymywać wiadomości od naszych użytkowników, upewnij się, że Twoja sieć zezwala na połączenia z adresów IP, z których korzysta program EOP w naszych centrach danych. Aby uzyskać więcej informacji, [zobacz Exchange Online Protection IP](../../enterprise/urls-and-ip-address-ranges.md).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Najlepsze rozwiązania dotyczące zbiorczego wysyłanie wiadomości e-mail do Microsoft 365 użytkowników

Jeśli często przeprowadzasz zbiorcze kampanie dotyczące poczty e-mail Microsoft 365 użytkowników i chcesz mieć pewność, że Twoje wiadomości e-mail będą przychodzić w bezpieczny i terminowy sposób, postępuj zgodnie z poradami w tej sekcji.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Upewnij się, że nazwa Od odzwierciedla nadawcę wiadomości

Temat powinien być krótkim podsumowaniem tematu wiadomości, a treść wiadomości powinna jasno i zwięźle wskazywać, czego dotyczy oferta, usługa lub produkt. Przykład:

Poprawne:

> Od: marketing@shoppershandbag.com <br> Temat: Zaktualizowano katalog bożonarodzeniowy!

Niepoprawnie:

> Od: someone@outlook.com <br> Temat: Katalogi

Im łatwiej będzie wiadomo, kim jesteś i co robisz, tym mniej trudności będziesz mieć w przypadku większości filtrów spamu.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Zawsze dołączaj opcję anulowania subskrypcji w wiadomościach e-mail kampanii

Marketingowe wiadomości e-mail, zwłaszcza biuletyny, zawsze powinny zawierać sposób na odsubskrybowanie przyszłych wiadomości e-mail. Przykład:

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Niektórzy nadawcy dołączają tę opcję, wymagając od adresatów wysłania wiadomości e-mail na określony alias z treścią "Anuluj subskrypcję" w temacie. Nie jest to preferowane w przypadku powyższego przykładu jednym kliknięciem. Jeśli zdecydujesz się na wymaganie od adresatów wysłania wiadomości, upewnij się, że po kliknięciu linku wszystkie wymagane pola są wstępnie wypełnione.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Użyj opcji podwójnej zgody na rejestrację marketingowej poczty e-mail lub biuletynu

To najlepsze rozwiązanie z branży jest zalecane, jeśli Twoja firma wymaga lub zachęca użytkowników do zarejestrowania ich informacji kontaktowych w celu uzyskania dostępu do Twoich produktów lub usług. W niektórych firmach praktyką jest automatyczne zarejestrowanie użytkowników w celu otrzymywania marketingowych wiadomości e-mail lub biuletynów e-mail w trakcie procesu rejestracji, ale w przypadku niektórych rozwiązań marketingowych można je traktować jako kwestionowane w świecie filtrowania wiadomości e-mail.

Jeśli podczas procesu rejestracji zaznaczono pole wyboru "Tak, wyślij mi swój biuletyn" lub "Tak, proszę o wysyłanie ofert specjalnych", użytkownicy, którzy nie przyciągną uwagi, mogą niechcący zarejestrować się w marketingowych wiadomościach e-mail lub biuletynach, których nie chcą otrzymywać.

 Firma Microsoft zaleca użycie opcji podwójnej zgody, co oznacza, że pole wyboru dla marketingowych wiadomości e-mail lub biuletynów nie jest domyślnie zaznaczone. Ponadto po przesłaniu formularza rejestracji do użytkownika jest wysyłana weryfikacyjna wiadomość e-mail z adresem URL umożliwiającym potwierdzenie decyzji o otrzymywaniu marketingowych wiadomości e-mail.

 Dzięki temu tylko użytkownicy, którzy chcą otrzymywać marketingowe wiadomości e-mail, zostaną usunięci w tych wiadomościach e-mail, a następnie czyszcząc firmę wysyłającą wszelkie wątpliwości dotyczące działań marketingowych w wiadomościach e-mail.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>Zapewnianie przezroczystości i możliwości śledzenia zawartości wiadomości e-mail

Równie ważna jest to, jak sposób wysłania wiadomości e-mail to zawartość, która je zawiera. Podczas tworzenia zawartości wiadomości e-mail korzystaj z następujących najlepszych rozwiązań, aby upewnić się, że wiadomości e-mail nie będą oflagowyane przez usługi filtrowania wiadomości e-mail:

- Gdy wiadomość e-mail żąda, aby adresaci dodali nadawcę do książki adresowej, należy wyraźnie o tym pamiętać, że takie działanie nie jest gwarancją dostarczenia.

- Przekierowania zawarte w treści wiadomości powinny być podobne i spójne, a także nie powinny być wielokrotne i zróżnicowane. Przekierowanie w tym kontekście to wszystko, co wskazuje wiadomość, na przykład linki i dokumenty. Jeśli masz wiele reklam lub anuluj subskrypcję linków lub Aktualizuj linki profilu, powinny one wskazać tę samą domenę. Przykład:

  Poprawna (wszystkie domeny są takie same):

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Niepoprawne (wszystkie domeny są różne):

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Unikaj zawartości z dużymi obrazami i załącznikami lub wiadomości składających się wyłącznie na obraz.

- Ustawienia prywatności publicznej (prywatności) lub P3P powinny jasno pouczać o obecności pikseli śledzenia (błędów sieci Web lub sygnałów nawigacyjnych).

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Usuwanie nieprawidłowych aliasów e-mail z baz danych

Każdy alias e-mail w bazie danych, który tworzy wiadomość typu "bounce-back", nie jest niepotrzebny i stwarza zagrożenie dla dokładniejszej kontroli wiadomości wychodzących przez usługi filtrowania wiadomości e-mail. Upewnij się, że baza danych poczty e-mail jest aktualne.