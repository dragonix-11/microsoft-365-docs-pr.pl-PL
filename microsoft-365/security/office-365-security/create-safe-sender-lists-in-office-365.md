---
title: Tworzenie list bezpiecznych nadawców
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.assetid: 9721b46d-cbea-4121-be51-542395e6fd21
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o dostępnych i preferowanych opcjach zezwalania na komunikaty przychodzące w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 898f04826f89e3a33c0cfcca01b717523e7c6122
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974218"
---
# <a name="create-safe-sender-lists-in-eop"></a>Tworzenie list bezpiecznych nadawców w ramach EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jeśli jesteś klientem Microsoft 365 ze skrzynkami pocztowymi w Exchange Online lub autonomicznym klientem Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, usługa EOP oferuje wiele sposobów zapewnienia, że użytkownicy będą otrzymywać wiadomości e-mail od zaufanych nadawców. Te opcje obejmują Exchange reguły przepływu poczty (nazywane również regułami transportu), Outlook Sejf nadawców, listę dozwolonych adresów IP (filtrowanie połączeń) oraz listy dozwolonych nadawców lub listy dozwolonych domen w zasadach ochrony przed spamem. Łącznie można traktować te opcje jako _listy bezpiecznych nadawców_.

Dostępne listy bezpiecznych nadawców są opisane na poniższej liście w kolejności od najbardziej zalecanych do najmniej zalecanych:

1. Reguły przepływu poczty
2. nadawcy Outlook Sejf
3. Lista dozwolonych adresów IP (filtrowanie połączeń)
4. Listy dozwolonych nadawców lub listy dozwolonych domen (zasady ochrony przed spamem)

Reguły przepływu poczty zapewniają największą elastyczność w celu zapewnienia, że dozwolone są tylko odpowiednie wiadomości. Listy dozwolonych nadawców i dozwolonych domen w zasadach ochrony przed spamem nie są tak bezpieczne jak lista dozwolonych adresów IP, ponieważ domena poczty e-mail nadawcy jest łatwo sfałszowana. Jednak lista dozwolonych adresów IP również stanowi zagrożenie, ponieważ wiadomości e-mail z _dowolnej_ domeny wysyłanej z tego adresu IP pomijają filtrowanie spamu.

> [!IMPORTANT]
>
> - Komunikaty, które są identyfikowane jako złośliwe oprogramowanie lub wyłudzanie informacji o wysokim poziomie zaufania, są zawsze poddawane kwarantannie, niezależnie od używanej opcji listy bezpiecznych nadawców. Aby uzyskać więcej informacji, zobacz [Domyślne zabezpieczanie w Office 365](secure-by-default.md).
>
> - Należy zachować ostrożność, aby ściśle monitorować _wszelkie_ wyjątki występujące w przypadku filtrowania spamu przy użyciu list bezpiecznych nadawców.
>
> - List bezpiecznych nadawców można używać do pomocy w przypadku wyników fałszywie dodatnich (dobra wiadomość e-mail oznaczona jako zła), ale należy rozważyć użycie list bezpiecznych nadawców jako tymczasowego rozwiązania, którego należy unikać, jeśli to możliwe. Nie zalecamy zarządzania wynikami fałszywie dodatnimi przy użyciu bezpiecznych list nadawców, ponieważ wyjątki od filtrowania spamu mogą otworzyć organizację na fałszowanie i inne ataki. Jeśli nalegasz na używanie list bezpiecznych nadawców do zarządzania wynikami fałszywie dodatnimi, musisz zachować czujność i zachować ostrożność w [temacie Zgłaszanie komunikatów i plików firmie Microsoft](report-junk-email-messages-to-microsoft.md) w gotowości.
>
> - Aby zezwolić domenie na wysyłanie nieuwierzytelnionych wiadomości e-mail (pomiń ochronę przed fałszowaniem), ale nie pomijaj ochrony przed spamem i innymi zabezpieczeniami, możesz użyć [analizy fałszowania](learn-about-spoof-intelligence.md) i [listy dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md).
>
> - Metodyka EOP i Outlook sprawdzają różne właściwości komunikatów, aby określić nadawcę wiadomości. Aby uzyskać więcej informacji, zobacz sekcję [Zagadnienia dotyczące zbiorczej poczty e-mail](#considerations-for-bulk-email) w dalszej części tego artykułu.
>

Z kolei istnieje kilka opcji blokowania poczty e-mail z określonych źródeł przy użyciu _zablokowanych list nadawców_. Aby uzyskać więcej informacji, zobacz [Create block sender lists in EOP (Tworzenie list nadawców blokowych w ramach EOP](create-block-sender-lists-in-office-365.md)).

## <a name="recommended-use-mail-flow-rules"></a>(Zalecane) Używanie reguł przepływu poczty

> [!NOTE]
> Nie można użyć nagłówków wiadomości i reguł przepływu poczty, aby wyznaczyć wewnętrznego nadawcę jako bezpiecznego nadawcę. Procedury w tej sekcji działają tylko dla nadawców zewnętrznych.

Reguły przepływu poczty w Exchange Online i autonomicznej operacji EOP używają warunków i wyjątków do identyfikowania komunikatów oraz akcji określających, co należy zrobić z tymi wiadomościami. Aby uzyskać więcej informacji, zobacz [Reguły przepływu poczty (reguły transportu) w Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

W poniższym przykładzie założono, że potrzebujesz wiadomości e-mail z contoso.com, aby pominąć filtrowanie spamu. W tym celu skonfiguruj następujące ustawienia:

1. **Warunek**: **Domena nadawcy** \> **jest** \> contoso.com.

2. Skonfiguruj jedno z następujących ustawień:

   - **Warunek reguły przepływu** **poczty: Nagłówek** \> wiadomości **zawiera dowolną z następujących słów** \> **Nazwa nagłówka**: `Authentication-Results` \> **wartość nagłówka**: `dmarc=pass` lub `dmarc=bestguesspass`.

     Ten warunek sprawdza stan uwierzytelniania poczty e-mail wysyłanej domeny poczty e-mail, aby upewnić się, że domena wysyłająca nie jest sfałszowana. Aby uzyskać więcej informacji na temat uwierzytelniania poczty e-mail, zobacz [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md).

   - **Lista dozwolonych adresów IP**: określ źródłowy adres IP lub zakres adresów w zasadach filtru połączeń.

     Użyj tego ustawienia, jeśli domena wysyłająca nie używa uwierzytelniania poczty e-mail. Być tak restrykcyjne, jak to możliwe, jeśli chodzi o źródłowe adresy IP na liście dozwolonych adresów IP. Zalecamy użycie zakresu adresów IP o wartości /24 lub mniejszej (mniej jest lepsze). Nie używaj zakresów adresów IP należących do usług konsumenckich (na przykład outlook.com) ani infrastruktur udostępnionych.

   > [!IMPORTANT]
   >
   > - Nigdy nie konfiguruj reguł przepływu poczty _tylko_ z domeną nadawcy jako warunkiem pominięcia filtrowania spamu. Spowoduje to _znaczne_ zwiększenie prawdopodobieństwa, że osoby atakujące będą mogły podszywać się pod domenę wysyłającą (lub personifikować pełny adres e-mail), pominąć filtrowanie spamu i pominąć sprawdzanie uwierzytelniania nadawcy, aby wiadomość dotarła do skrzynki odbiorczej odbiorcy.
   >
   > - Nie używaj domen, których jesteś właścicielem (nazywanych również akceptowanymi domenami) ani popularnych domen (na przykład microsoft.com) jako warunków w regułach przepływu poczty. Jest to uznawane za wysokie ryzyko, ponieważ stwarza możliwość wysyłania wiadomości e-mail przez osoby atakujące, które w przeciwnym razie byłyby filtrowane.
   >
   > - Jeśli zezwolisz na adres IP, który znajduje się za bramą translatora adresów sieciowych (NAT), musisz znać serwery, które są zaangażowane w pulę translatora adresów sieciowych, aby poznać zakres listy dozwolonych adresów IP. Adresy IP i uczestnicy translatora adresów sieciowych mogą ulec zmianie. Należy okresowo sprawdzać wpisy listy dozwolonych adresów IP w ramach standardowych procedur konserwacji.

3. **Warunki opcjonalne**:
   - **Nadawca** \> **jest wewnętrzny/zewnętrzny** \> **Poza organizacją**: ten warunek jest niejawny, ale można go używać do obsługi kont lokalnych serwerów poczty e-mail, które mogą nie być poprawnie skonfigurowane.
   - **Temat lub treść** \> **temat lub treść zawiera dowolny z tych wyrazów** \> \<keywords\>: Jeśli możesz dodatkowo ograniczyć komunikaty według słów kluczowych lub fraz w wierszu tematu lub treści wiadomości, możesz użyć tych słów jako warunku.

4. **Akcja**: skonfiguruj obie te akcje w regule:
   1. **Modyfikowanie właściwości** \> komunikatu **ustawianie poziomu ufności spamu (SCL)** \> **Pomijanie filtrowania spamu**.
   2. **Modyfikowanie właściwości** \> komunikatu **ustaw nagłówek komunikatu**: **ustaw nagłówek** \<CustomHeaderName\> **komunikatu na wartość** \<CustomHeaderValue\>.

      Na przykład `X-ETR: Bypass spam filtering for authenticated sender 'contoso.com'`. Jeśli w regule znajduje się więcej niż jedna domena, możesz odpowiednio dostosować tekst nagłówka.

      Gdy wiadomość pomija filtrowanie spamu z powodu reguły przepływu poczty, wartość `SFV:SKN` jest ostemplowana w nagłówku **X-Forefront-Antispam-Report** . Jeśli komunikat pochodzi ze źródła, które znajduje się na liście dozwolonych adresów IP, wartość `IPV:CAL` zostanie również dodana. Te wartości mogą pomóc w rozwiązywaniu problemów.

      :::image type="content" source="../../media/1-AllowList-SkipFilteringFromContoso.png" alt-text="Ustawienia reguły przepływu poczty w usłudze EAC dotyczące pomijania filtrowania spamu" lightbox="../../media/1-AllowList-SkipFilteringFromContoso.png":::

## <a name="use-outlook-safe-senders"></a>Używanie nadawców Outlook Sejf

> [!CAUTION]
> Ta metoda stwarza wysokie ryzyko, że osoby atakujące pomyślnie dostarczają wiadomość e-mail do skrzynki odbiorczej, która w przeciwnym razie zostałaby przefiltrowana. Jednak listy Sejf nadawców lub domen Sejf użytkownika nie uniemożliwiają filtrowania złośliwego oprogramowania ani wiadomości wyłudzających informacje o wysokim poziomie ufności.

Zamiast ustawienia organizacyjnego użytkownicy lub administratorzy mogą dodać adresy e-mail nadawcy do listy nadawców Sejf w skrzynce pocztowej. Aby uzyskać instrukcje, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych w Office 365](configure-junk-email-settings-on-exo-mailboxes.md). Nie jest to pożądane w większości sytuacji, ponieważ nadawcy omijają części stosu filtrowania. Mimo że nadawca jest zaufany, nadal można naruszyć bezpieczeństwo nadawcy i wysłać złośliwą zawartość. Najlepiej, aby nasze filtry robiły to, co jest potrzebne do sprawdzenia każdej wiadomości, a następnie [zgłaszały fałszywe wyniki dodatnie/ujemne firmie Microsoft](report-junk-email-messages-to-microsoft.md) , jeśli nasze filtry pomyliły się. Pomijanie stosu filtrowania zakłóca również [zap](zero-hour-auto-purge.md).

Gdy wiadomości pomijają filtrowanie spamu z powodu listy nadawców Sejf użytkownika, pole nagłówka **X-Forefront-Antispam-Report** będzie zawierać wartość `SFV:SFE`, która wskazuje, że filtrowanie pod kątem spamu, fałszowania i wyłudzania informacji zostało pominięte.

## <a name="use-the-ip-allow-list"></a>Używanie listy dozwolonych adresów IP

Jeśli nie możesz użyć reguł przepływu poczty zgodnie z wcześniejszym opisem, następną najlepszą opcją jest dodanie źródłowego serwera lub serwerów poczty e-mail do listy dozwolonych adresów IP w zasadach filtru połączeń. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie filtrowania połączeń w ramach EOP](configure-the-connection-filter-policy.md).

**Uwagi**:

- Ważne jest, aby zachować minimalną liczbę dozwolonych adresów IP, więc unikaj używania całych zakresów adresów IP zawsze, gdy jest to możliwe.
- Nie używaj zakresów adresów IP należących do usług konsumenckich (na przykład outlook.com) ani infrastruktur udostępnionych.
- Regularnie przeglądaj wpisy na liście dozwolonych adresów IP i usuwaj wpisy, których już nie potrzebujesz.

> [!CAUTION]
> Bez dodatkowej weryfikacji, takiej jak reguły przepływu poczty, poczta e-mail ze źródeł na liście dozwolonych adresów IP pomija filtrowanie spamu i uwierzytelnianie nadawcy (SPF, DKIM, DMARC). Powoduje to wysokie ryzyko, że osoby atakujące pomyślnie dostarczają wiadomość e-mail do skrzynki odbiorczej, która w przeciwnym razie zostałaby przefiltrowana. Jednak lista dozwolonych adresów IP nie uniemożliwia filtrowania złośliwego oprogramowania ani wiadomości wyłudzających informacje o wysokim poziomie ufności.

## <a name="use-allowed-sender-lists-or-allowed-domain-lists"></a>Używanie list dozwolonych nadawców lub list dozwolonych domen

Najmniej pożądaną opcją jest użycie listy dozwolonych nadawców lub listy dozwolonych domen w zasadach ochrony przed spamem. Należy unikać tej opcji, _jeśli jest to możliwe_ , ponieważ nadawcy pomijają całą ochronę przed spamem, fałszowaniem i wyłudzaniem informacji oraz uwierzytelnianie nadawcy (SPF, DKIM, DMARC). Ta metoda jest najlepiej używana tylko do testowania tymczasowego. Szczegółowe kroki można znaleźć w [temacie Konfigurowanie zasad ochrony przed spamem w temacie EOP](configure-your-spam-filter-policies.md) .

Maksymalny limit dla tych list wynosi około 1000 wpisów; chociaż w portalu będzie można wprowadzić tylko 30 wpisów. Aby dodać więcej niż 30 wpisów, należy użyć programu PowerShell.

> [!CAUTION]
>
> - Ta metoda stwarza wysokie ryzyko, że osoby atakujące pomyślnie dostarczają wiadomość e-mail do skrzynki odbiorczej, która w przeciwnym razie zostałaby przefiltrowana. Jednak listy dozwolonych nadawców lub dozwolonych domen nie uniemożliwiają filtrowania złośliwego oprogramowania ani wiadomości wyłudzających informacje o wysokim poziomie ufności.
>
> - Nie używaj domen, których jesteś właścicielem (znanych również jako akceptowane domeny) ani popularnych domen (na przykład microsoft.com) na listach dozwolonych domen.

## <a name="considerations-for-bulk-email"></a>Zagadnienia dotyczące zbiorczej poczty e-mail

Standardowa wiadomość e-mail SMTP składa się z _koperty wiadomości_ i zawartości wiadomości. Koperta wiadomości zawiera informacje wymagane do przesyłania i dostarczania komunikatu między serwerami SMTP. Zawartość wiadomości zawiera pola nagłówka wiadomości (łącznie nazywane _nagłówkiem komunikatu_) i treść komunikatu. Koperta komunikatu jest opisana w dokumencie RFC 5321, a nagłówek komunikatu jest opisany w dokumencie RFC 5322. Adresaci nigdy nie widzą rzeczywistej koperty wiadomości, ponieważ jest ona generowana przez proces transmisji komunikatów i w rzeczywistości nie jest częścią wiadomości.

- Adres `5321.MailFrom` (znany również jako adres **MAIL FROM** , nadawca P1 lub nadawca koperty) to adres e-mail używany podczas transmisji wiadomości przez protokół SMTP. Ten adres e-mail jest zwykle rejestrowany w polu nagłówek **Return-Path** w nagłówku wiadomości (chociaż nadawca może wyznaczyć inny adres **e-mail ze ścieżką powrotną** ). Jeśli nie można dostarczyć wiadomości, jest to adresat raportu o braku dostarczenia (znany również jako komunikat NDR lub bounce).
- Adres `5322.From` (znany również jako adres **od** lub nadawca P2) to adres e-mail w polu **Nagłówek od** i jest adresem e-mail nadawcy wyświetlanym w klientach poczty e-mail.

Często adresy `5321.MailFrom` i `5322.From` są takie same (komunikacja między osobami). Jednak gdy wiadomość e-mail jest wysyłana w imieniu innej osoby, adresy mogą być inne. Dzieje się tak najczęściej w przypadku zbiorczych wiadomości e-mail.

Załóżmy na przykład, że Blue Yonder Airlines zatrudniła Margie's Travel do wysyłania reklam e-mail. Komunikat otrzymywany w skrzynce odbiorczej ma następujące właściwości:

- Adres `5321.MailFrom` jest blueyonder.airlines@margiestravel.com.
- Adres `5322.From` jest blueyonder@news.blueyonderairlines.com, co zobaczysz w Outlook.

Sejf listy nadawców i listy bezpiecznych domen w zasadach ochrony przed spamem w usłudze EOP sprawdzają tylko `5322.From` adresy, jest to podobne do Outlook Sejf nadawców używających `5322.From` tego adresu.

Aby zapobiec filtrowaniu tego komunikatu, możesz wykonać następujące kroki:

- Dodaj blueyonder@news.blueyonderairlines.com (`5322.From`adres) jako nadawcę Outlook Sejf.
- [Użyj reguły przepływu poczty](#recommended-use-mail-flow-rules) z warunkiem, który wyszuka wiadomości z blueyonder@news.blueyonderairlines.com ( `5322.From` adres, blueyonder.airlines@margiestravel.com ( `5321.MailFrom`), lub obu tych elementów.
