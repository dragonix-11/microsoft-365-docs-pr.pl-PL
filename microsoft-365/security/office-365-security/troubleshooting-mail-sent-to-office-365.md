---
title: Rozwiązywanie problemów z pocztą wysłaną do Microsoft 365
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
description: Ten artykuł zawiera informacje dotyczące rozwiązywania problemów z wysyłaniem wiadomości e-mail do skrzynek odbiorczych w Microsoft 365 & najlepszych rozwiązań dotyczących wysyłania zbiorczego do klientów Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 37703ccb0ffb37163033bb2fdca24566a33bb275
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128439"
---
# <a name="troubleshooting-mail-sent-to-microsoft-365"></a>Rozwiązywanie problemów z pocztą wysłaną do Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)

Ten artykuł zawiera informacje dotyczące rozwiązywania problemów dla nadawców, którzy napotykają problemy podczas próby wysyłania wiadomości e-mail do skrzynek odbiorczych w Microsoft 365 oraz najlepsze rozwiązania dotyczące zbiorczego wysyłania wiadomości do klientów.

## <a name="are-you-managing-your-ip-and-domains-sending-reputation"></a>Czy zarządzasz adresem IP i reputacją wysyłania domeny?

Technologie filtrowania EOP mają na celu zapewnienie ochrony przed spamem dla Microsoft 365 i innych produktów firmy Microsoft, takich jak Exchange Server. Używamy również SPF, DKIM i DMARC; technologie uwierzytelniania poczty e-mail, które pomagają rozwiązać problem fałszowania i wyłudzania informacji, sprawdzając, czy domena wysyłająca wiadomość e-mail jest do tego upoważniona. Na filtrowanie operacji EOP ma wpływ wiele czynników związanych z wysyłaniem adresu IP, domeną, uwierzytelnianiem, dokładnością listy, stawkami skarg, zawartością i nie tylko. Spośród nich jednym z głównych czynników w obniżaniu reputacji nadawcy i ich zdolności do dostarczania wiadomości e-mail jest ich wskaźnik skarg na wiadomości-śmieci.

## <a name="are-you-sending-email-from-new-ip-addresses"></a>Czy wysyłasz wiadomości e-mail z nowych adresów IP?

Adresy IP, które nie były wcześniej używane do wysyłania wiadomości e-mail, zazwyczaj nie mają żadnej reputacji utworzonej w naszych systemach. W związku z tym wiadomości e-mail od nowych adresów IP są bardziej narażone na problemy z dostarczaniem. Po utworzeniu reputacji adresu IP w przypadku niesyłania spamu funkcja EOP zwykle zapewnia lepsze środowisko dostarczania wiadomości e-mail.

Nowe adresy IP dodawane do domen uwierzytelnionych w istniejących rekordach SPF zwykle mają dodatkową korzyść z dziedziczenia niektórych domen wysyłających reputację. Jeśli Twoja domena ma dobrą reputację wysyłania nowych adresów IP, mogą wystąpić szybsze zwiększanie czasu. Nowy adres IP może zostać w pełni zwiększony w ciągu kilku tygodni lub wcześniej w zależności od ilości, dokładności listy i stawek skarg dotyczących wiadomości-śmieci.

## <a name="confirm-that-your-dns-is-set-up-correctly"></a>Upewnij się, że system DNS został poprawnie skonfigurowany

Aby uzyskać instrukcje dotyczące tworzenia i obsługi rekordów DNS, w tym rekordu MX wymaganego do routingu poczty, należy skontaktować się z dostawcą hostingu DNS.

## <a name="ensure-that-you-do-not-advertise-yourself-as-a-non-routable-ip"></a>Upewnij się, że nie anonsujesz się jako adres IP bez routingu

Możemy nie akceptować wiadomości e-mail od nadawców, którzy nie mogą wyszukiwać wstecznego systemu DNS. W niektórych przypadkach legalni nadawcy anonsują się niepoprawnie jako adres IP z routingiem innym niż Internet podczas próby otwarcia połączenia z usługą EOP. Adresy IP zarezerwowane dla sieci prywatnej (bez routingu) obejmują:

- 192.168.0.0/16 (lub 192.168.0.0 - 192.168.255.255)
- 10.0.0.0/8 (lub 10.0.0.0 - 10.255.255.255)
- 172.16.0.0/11 (lub 172.16.0.0 - 172.31.255.255)

## <a name="you-received-a-non-delivery-report-ndr-when-sending-email-to-a-user-in-office-365"></a>Podczas wysyłania wiadomości e-mail do użytkownika w Office 365 otrzymano raport o braku dostarczania (NDR)

Niektóre problemy z dostarczaniem są wynikiem zablokowania adresu IP nadawcy przez firmę Microsoft lub zidentyfikowania konta użytkownika jako nadawcy zabronionego z powodu wcześniejszej aktywności spamu. Jeśli uważasz, że błąd NDR został odebrany, najpierw postępuj zgodnie z instrukcjami w komunikacie NDR, aby rozwiązać ten problem.

Aby uzyskać więcej informacji na temat otrzymanego błędu, zobacz listę kodów błędów w [temacie Wysyłanie wiadomości e-mail do raportów o braku dostarczania w Exchange Online](/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

 Jeśli na przykład otrzymasz następujący NDR, oznacza to, że wysyłający adres IP został zablokowany przez firmę Microsoft:

 `550 5.7.606-649 Access denied, banned sending IP [x.x.x.x]; To request removal from this list please visit https://sender.office.com/ and follow the directions.`

Aby zażądać usunięcia z tej listy, możesz [usunąć siebie z listy zablokowanych nadawców za pomocą portalu delist](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="my-email-landed-in-the-recipients-junk-email-folder"></a>Moja wiadomość e-mail trafiła do folderu Wiadomości-śmieci adresata

Jeśli wiadomość została niepoprawnie zidentyfikowana jako spam przez EOP, możesz wraz z odbiorcą przesłać tę fałszywie dodatnią wiadomość do zespołu ds. analizy spamu firmy Microsoft, który oceni i przeanalizuje wiadomość. Aby uzyskać więcej informacji, zobacz [Zgłaszanie komunikatów i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="traffic-from-my-ip-address-is-throttled-by-eop"></a>Ruch z mojego adresu IP jest ograniczany przez EOP

Jeśli otrzymasz NDR z EOP, który wskazuje, że twój adres IP jest ograniczany przez EOP, na przykład:

 `host xxxx.outlook.com [x.x.x.x]: 451 4.7.550 Access denied, please try again later`

Otrzymano NDR, ponieważ wykryto podejrzane działanie z adresu IP i zostało ono tymczasowo ograniczone podczas dalszej oceny. Jeśli podejrzenie zostanie wyczyszczone w drodze oceny, to ograniczenie zostanie wkrótce zniesione.

## <a name="i-cant-receive-email-from-senders-in-microsoft-365"></a>Nie mogę otrzymywać wiadomości e-mail od nadawców w Microsoft 365

 Aby odbierać komunikaty od naszych użytkowników, upewnij się, że sieć zezwala na połączenia z adresów IP używanych przez funkcję EOP w naszych centrach danych. Aby uzyskać więcej informacji, zobacz [Exchange Online Protection adresów IP](../../enterprise/urls-and-ip-address-ranges.md).

## <a name="best-practices-for-bulk-emailing-to-microsoft-365-users"></a>Najlepsze rozwiązania dotyczące zbiorczej poczty e-mail do użytkowników Microsoft 365

Jeśli często prowadzisz zbiorcze kampanie e-mail w celu Microsoft 365 użytkowników i chcesz upewnić się, że wiadomości e-mail docierają w bezpieczny i terminowy sposób, postępuj zgodnie z wskazówkami w tej sekcji.

### <a name="ensure-that-the-from-name-reflects-who-is-sending-the-message"></a>Upewnij się, że nazwa Od odzwierciedla, kto wysyła wiadomość

Temat powinien być krótkim podsumowaniem tego, o co chodzi w komunikacie, a treść komunikatu powinna jasno i zwięźle wskazywać, o co chodzi w ofercie, usłudze lub produkcie. Przykład:

Poprawne:

> Od: marketing@shoppershandbag.com <br> Temat: Zaktualizowano katalog na boże Narodzenie!

Niepoprawne:

> Od: someone@outlook.com <br> Temat: katalogi

Im łatwiej jest ludziom wiedzieć, kim jesteś i co robisz, tym mniej trudności będziesz mieć dostarczanie za pośrednictwem większości filtrów spamu.

### <a name="always-include-an-unsubscribe-option-in-campaign-emails"></a>Zawsze dołączaj opcję anulowania subskrypcji do wiadomości e-mail kampanii

Marketingowe wiadomości e-mail, zwłaszcza biuletyny, powinny zawsze zawierać sposób anulowania subskrypcji z przyszłych wiadomości e-mail. Przykład:

 `This email was sent to example@contoso.com by sender@fabrikam.com.`

 `Update Profile/Email Address | Instant removal with SafeUnsubscribe&trade; | Privacy Policy`

Niektórzy nadawcy obejmują tę opcję, wymagając od adresatów wysłania wiadomości e-mail do określonego aliasu z opcją "Anuluj subskrypcję" w temacie. Nie jest to preferowane w powyższym przykładzie jednym kliknięciem. Jeśli zdecydujesz się wymagać od adresatów wysłania wiadomości e-mail, upewnij się, że po kliknięciu linku wszystkie wymagane pola zostaną wstępnie wypełnione.

### <a name="use-the-double-opt-in-option-for-marketing-email-or-newsletter-registration"></a>Użyj opcji podwójnej zgody na marketingową rejestrację wiadomości e-mail lub biuletynu

To najlepsze rozwiązanie w branży jest zalecane, jeśli firma wymaga lub zachęca użytkowników do rejestrowania swoich informacji kontaktowych w celu uzyskania dostępu do produktu lub usług. Niektóre firmy sprawiają, że jest to praktyka automatycznego rejestrowania swoich użytkowników do marketingowych wiadomości e-mail lub e-biuletynów podczas procesu rejestracji, ale jest to uważane za wątpliwą praktykę marketingową w świecie filtrowania wiadomości e-mail.

Jeśli podczas procesu rejestracji zaznaczono pole wyboru "Tak, wyślij do mnie biuletyn" lub "Tak, wyślij mi oferty specjalne", użytkownicy, którzy nie zwracają szczególnej uwagi, mogą przypadkowo zarejestrować się w celu otrzymywania marketingowych wiadomości e-mail lub biuletynów, których nie chcą otrzymywać.

 Firma Microsoft zaleca zamiast tego opcję podwójnej zgody, co oznacza, że pole wyboru dla marketingowych wiadomości e-mail lub biuletynów jest domyślnie niezaznaczone. Ponadto po przesłaniu formularza rejestracji do użytkownika jest wysyłana wiadomość e-mail weryfikacyjna z adresem URL umożliwiającym potwierdzenie decyzji o otrzymaniu marketingowych wiadomości e-mail.

 Pomaga to zapewnić, że tylko ci użytkownicy, którzy chcą otrzymywać marketingowe wiadomości e-mail, są rejestrowani w celu otrzymywania wiadomości e-mail, a następnie usuwają firmę wysyłającą wszelkie wątpliwe praktyki marketingu poczty e-mail.

### <a name="ensure-that-email-message-content-is-transparent-and-traceable"></a>Upewnij się, że zawartość wiadomości e-mail jest przezroczysta i można jej śledzić

Tak samo ważna jak sposób wysyłania wiadomości e-mail jest zawartość, która zawiera. Podczas tworzenia zawartości wiadomości e-mail użyj następujących najlepszych rozwiązań, aby upewnić się, że wiadomości e-mail nie będą oflagowane przez usługi filtrowania wiadomości e-mail:

- Gdy wiadomość e-mail żąda, aby adresaci dodali nadawcę do książki adresowej, należy wyraźnie stwierdzić, że taka akcja nie jest gwarancją dostarczenia.

- Przekierowania zawarte w treści komunikatu powinny być podobne i spójne, a nie wielokrotne i zróżnicowane. Przekierowanie w tym kontekście to wszystko, co wskazuje na komunikat, na przykład linki i dokumenty. Jeśli masz wiele linków reklamowych, anuluj subskrypcję lub Aktualizuj linki profilu, wszystkie powinny wskazywać tę samą domenę. Przykład:

  Odpowiedź prawidłowa (wszystkie domeny są takie same):

  `unsubscribe.bulkmailer.com`

  `profile.bulkmailer.com`

  `options.bulkmailer.com`

  Nieprawidłowe (wszystkie domeny są różne):

  `unsubscribe.bulkmailer.com`

  `profile.excite.com`

  `options.yahoo.com`

- Unikaj zawartości z dużymi obrazami i załącznikami lub komunikatami, które składają się wyłącznie z obrazu.

- Ustawienia prywatności publicznej lub P3P powinny wyraźnie określać obecność pikseli śledzenia (usterek internetowych lub sygnałów nawigacyjnych).

### <a name="remove-incorrect-email-aliases-from-your-databases"></a>Usuwanie nieprawidłowych aliasów wiadomości e-mail z baz danych

Każdy alias wiadomości e-mail w bazie danych, który tworzy odbicie, jest niepotrzebny i naraża wychodzące wiadomości e-mail na ryzyko dalszej kontroli za pomocą usług filtrowania wiadomości e-mail. Upewnij się, że baza danych poczty e-mail jest aktualna.
