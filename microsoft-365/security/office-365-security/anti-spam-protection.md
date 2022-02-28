---
title: Ochrona przed spamem
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o ustawieniach ochrony przed spamem i filtrach, które pomagają zapobiegać spamowi w u Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1bc5d81b1221b73bcb701345b8db2f160380ba37
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989660"
---
# <a name="anti-spam-protection-in-eop"></a>Ochrona przed spamem w uciekaniu poczty eop

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

> [!NOTE]
> Ten temat jest przeznaczony dla administratorów. Aby uzyskać informacje dla użytkowników końcowych, zobacz Omówienie filtru wiadomości-śmieci [i](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) Informacje [o wiadomościach-śmieciach i wyłudzaniu informacji](https://support.microsoft.com/office/86c1d76f-4d5a-4967-9647-35665dc17c31).

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online wiadomości e-mail są automatycznie chronione przed spamem (wiadomościami-śmieciami) przez usługę EOP.

Plan firmy Microsoft dotyczący bezpieczeństwa poczty e-mail obejmuje niepasowane podejście między produktami. Technologia ochrony przed spamem i wyłudzaniem informacji EOP jest stosowana na platformach poczty e-mail w celu zapewnienia użytkownikom najnowszych narzędzi do ochrony przed spamem i wyłudzania informacji oraz innowacyjnych rozwiązań w całej sieci. Celem usługi EOP jest oferuje pełną i użytecznych usługę poczty e-mail, która pomaga wykrywać i chronić użytkowników przed wiadomościami-śmieciami, nieuczciwymi zagrożeniami w wiadomościach e-mail (wyłudzaniem informacji) i złośliwym oprogramowaniem.

W związku z tym, że korzystanie z poczty e-mail się rozrosło, dlatego jest nadużyciem poczty e-mail. Niemonitorowane wiadomości-śmieci mogą zapychać skrzynki pocztowe i sieci, wpływać na zadowolenie użytkowników i ująć skuteczność prawdziwej komunikacji za pośrednictwem poczty e-mail. Dlatego firma Microsoft kontynuuje inwestycje w technologie ochrony przed spamem. Mówiąc w prosty sposób, zaczyna się od tego, że zawiera i filtruje wiadomości-śmieci.

> [!TIP]
> Poniższe technologie ochrony przed spamem są przydatne, gdy chcesz zezwolić na wiadomości lub zablokować je na podstawie koperty wiadomości (na przykład domeny nadawcy lub źródłowego adresu IP wiadomości). Aby zezwolić na wiadomości lub zablokować je na podstawie ładu (na przykład adresów URL w wiadomości lub dołączonych plikach), należy użyć portalu Listy [zablokowanych/zezwalania na dzierżawę](tenant-allow-block-list.md).

## <a name="anti-spam-technologies-in-eop"></a>Technologie ochrony przed spamem w uchcie EOP

Aby ograniczyć liczbę wiadomości-śmieci, program EOP obejmuje ochronę przed wiadomościami-śmieciami, które wykorzystują technologie ochrony przed spamem do identyfikowania i oddzielania wiadomości od legalnych wiadomości e-mail. Filtrowanie spamu eOP uczy się od znanych zagrożeń związanych ze spamem i wyłudzaniem informacji oraz opinii użytkowników z naszej platformy dla klientów Outlook.com. Bieżące opinie od użytkowników usługi EOP w programie klasyfikacji wiadomości-śmieci pomagają zapewnić ciągłe przeszkolone i udoskonalone technologie usługi EOP.

Ustawienia ochrony przed spamem w uciekowoniu EOP są następujące technologie:

- **Filtrowanie** połączeń: Identyfikuje dobre i złe serwery źródeł poczty e-mail w wczesnym okresie przychodzącego połączenia poczty e-mail za pośrednictwem listy adresów IP, listy zablokowanych adresów IP i listy bezpiecznych *adresów IP* (dynamicznej, ale nieedytowalnej listy zaufanych nadawców utrzymywanej przez firmę Microsoft). Te ustawienia konfigurujesz w zasadach filtru połączenia. Aby uzyskać więcej informacji [, zobacz Konfigurowanie filtrowania połączeń](configure-the-connection-filter-policy.md).

- **Filtrowanie spamu (filtrowanie zawartości)**: program EOP używa werdyktów filtrowania spamu **Spam****, Spam** o dużej **pewności, Masowa** poczta e-mail **, Wiadomości** e-mail służące do wyłudzania informacji o wysokiej pewności w celu klasyfikowania wiadomości. Na podstawie tych werdyktów można skonfigurować akcje do podjęcia, a także określić, co użytkownicy mogą robić w kwarantannie wiadomości i czy użytkownicy otrzymują powiadomienia kwarantanny za pomocą zasad [kwarantanny](quarantine-policies.md). Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad ochrony przed spamem w programie Microsoft 365](configure-your-spam-filter-policies.md).

  > [!NOTE]
  > Domyślnie filtrowanie spamu jest skonfigurowane do wysyłania do folderu wiadomości-śmieci adresata wiadomości oznaczonych jako spam. Jednak w środowiskach hybrydowych, w których firma EOP chroni lokalne skrzynki pocztowe usługi Exchange, musisz skonfigurować dwie reguły przepływu poczty (nazywane także regułami transportu) w lokalnej organizacji programu Exchange w celu rozpoznania nagłówków spamu usługi EOP dodawanych do wiadomości. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usługi EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- **Filtrowanie spamu** ruchu wychodzącego: Usługa EOP sprawdza również, czy użytkownicy nie wysyłają spamu ani w treści wiadomości wychodzących, ani przez przekroczenie limitów wiadomości wychodzących. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania spamu ruchu wychodzącego w programie Microsoft 365](configure-the-outbound-spam-policy.md).

- **Fałszywa inteligencja**: Aby uzyskać więcej informacji, zobacz [Ochrona przed fałszerami w uciekaniu poczty eOP](anti-spoofing-protection.md).

## <a name="manage-errors-in-spam-filtering"></a>Zarządzanie błędami podczas filtrowania spamu

Możliwe jest, że dobre wiadomości można określić jako spam (nazywany też wynikami fałszywie dodatnimi) lub że spam może być dostarczany do Skrzynki odbiorczej (znani także jako wynik fałszywie ujemny). Możesz skorzystać z sugestii w poniższych sekcjach, aby dowiedzieć się, co się stało, i zapobiec temu w przyszłości.

Oto kilka najlepszych rozwiązań, które dotyczą obu scenariuszy:

- Zawsze zgłaszaj błędnie sklasyfikowane wiadomości do firmy Microsoft. Aby uzyskać więcej informacji, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

- **Sprawdź nagłówki wiadomości przed spamem**: Te wartości będą zawierały informacje o tym, dlaczego wiadomość została oznaczona jako spam lub dlaczego została pominięta w filtrowaniu spamu. Aby uzyskać więcej informacji, zobacz [Nagłówki wiadomości przed spamem](anti-spam-message-headers.md).

- **Wskaż rekord MX tak, Microsoft 365**: aby program EOP zapewniał najlepszą ochronę, zawsze zalecamy, aby wiadomości e-mail były dostarczane Microsoft 365 e-mail. Aby uzyskać instrukcje, [zobacz Tworzenie rekordów DNS dla Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

  Jeśli rekord MX wskazuje inną lokalizację (na przykład urządzenie lub rozwiązanie do ochrony przed spamem innej firmy), usługi EOP trudno jest zapewnić dokładne filtrowanie spamu. W tym scenariuszu należy skonfigurować ulepszone filtrowanie łączników (nazywane również _pomijanie listy_). Aby uzyskać instrukcje, [zobacz Ulepszone filtrowanie łączników w programie Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- **Korzystanie z uwierzytelniania** wiadomości e-mail: Jeśli jesteś właścicielem domeny poczty e-mail, możesz użyć systemu DNS, aby mieć potwierdzenie, że wiadomości od nadawców w tej domenie są prawdziwe. Aby chronić usługę EOP przed spamem i niechcianym fałszerszem, użyj wszystkich następujących metod uwierzytelniania pocztą e-mail:

  - **SPF**: Program Sender Policy Framework sprawdza źródłowy adres IP wiadomości przed właścicielem domeny wysyłającej. Aby uzyskać krótkie wprowadzenie do SPF i skonfigurować go szybko, zobacz Konfigurowanie spf w celu zapobiegania [fałszersprowadzeniu](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Aby uzyskać bardziej szczegółowe informacje na temat sposobu, w jaki program Microsoft 365 korzysta z SPF, lub na potrzeby rozwiązywania problemów lub wdrożeń niestandardowych, takich jak wdrożenia hybrydowe, zacznij od tematu Jak program Microsoft 365 używa struktury zasad dotyczących nadawców [(SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) w celu zapobiegania fałszowania.

  - **DKIM**: Identyfikowana poczta kluczami domen (DomainKeys) dodaje podpis cyfrowy do nagłówka wiadomości w wiadomościach wysyłanych z Twojej domeny. Aby uzyskać więcej informacji, zobacz Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych z domeny [niestandardowej w Microsoft 365](use-dkim-to-validate-outbound-email.md).

  - **DMARC**: Uwierzytelnianie, raportowanie i zgodność wiadomości opartych na domenie ułatwia docelowym systemom poczty e-mail określenie, co należy zrobić z wiadomościami, które nie spełniają wymagań dotyczących mechanizmu SPF lub DKIM, i zapewnia innym poziom zaufania partnerom poczty e-mail. Aby uzyskać więcej informacji, zobacz [Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail Microsoft 365](use-dmarc-to-validate-email.md).

- **Sprawdź ustawienia masowej** poczty e-mail: Próg zbiorczych skarg skonfigurowanych w zasadach ochrony przed spamem określa, czy masowa poczta _e-mail_ (znana również jako szara poczta) jest oznaczana jako spam. Ustawienie tylko w programie PowerShell _MarkAsSpamBulkMail_ , które jest domyślnie włączone, również wpływa na wyniki. Aby uzyskać więcej informacji, [zobacz Konfigurowanie zasad ochrony przed spamem w programie Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="prevent-the-delivery-of-spam-to-the-inbox"></a>Zapobieganie dostarczaniu spamu do Skrzynki odbiorczej

- **Sprawdź ustawienia** swojej organizacji. Uwaga na ustawienia umożliwiające pomijanie filtrowania spamu przez wiadomości (na przykład jeśli dodasz własną domenę do listy dozwolonych domen w zasadach ochrony przed spamem). Aby uzyskać informacje o naszych zalecanych ustawieniach, zobacz Zalecane ustawienia usług [EOP i Microsoft Defender](recommended-settings-for-eop-and-office365.md) w Office 365 zabezpieczeń i [Tworzenie list bezpiecznych nadawców](create-safe-sender-lists-in-office-365.md).

- **Użyj dostępnych list zablokowanych nadawców**: Aby uzyskać informacje, zobacz [Tworzenie list zablokowanych nadawców](create-block-sender-lists-in-office-365.md).

- **Anulowanie subskrypcji zbiorczej wiadomości e-mail** Jeśli wiadomość zawierała treści, w których użytkownik się załozył (biuletyny, ogłoszenia o produktach itp.) i zawiera link anulowania subskrypcji wiarygodnego źródła, rozważ po prostu anulowanie ich subskrypcji.

- Autonomiczna **program EOP:** twórz reguły przepływu poczty e-mail w lokalnym programie Exchange na potrzeby werdyktów filtrowania spamu usługi EOP: W środowiskach hybrydowych, w których firma EOP chroni lokalne skrzynki pocztowe programu Exchange, musisz skonfigurować reguły przepływu poczty e-mail (nazywane także regułami transportu) w lokalnym programie Exchange. Te reguły przepływu poczty tłumaczą werdykt filtrowania spamu usługi EOP, dzięki czemu reguła wiadomości-śmieci w skrzynce pocztowej może przenieść wiadomość do folderu Wiadomości-śmieci. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usługi EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

### <a name="prevent-good-email-from-being-identified-as-spam"></a>Zapobieganie identyfikowaniu dobrych wiadomości e-mail jako spamu

Oto kilka czynności, które można wykonać, aby zapobiec wynikom fałszywie dodatnim:

- **Sprawdź ustawienia filtru wiadomości Outlook-śmieci**:

  - Sprawdź **,** **czy Outlook** Filtr wiadomości-śmieci jest wyłączony: Gdy filtr wiadomości-śmieci usługi Outlook jest ustawiony na wartość domyślną Bez filtrowania automatycznego, program Outlook nie próbuje klasyfikować wiadomości jako spamu.  Gdy jest ustawiona wartość Niski  lub **Wysoki, filtr** wiadomości-śmieci filtru wiadomości-śmieci filtru Outlook używa własnej technologii filtru SmartScreen do identyfikowania i przenoszenia spamu do folderu Wiadomości-śmieci w celu uzyskania wyników fałszywie dodatnich. W listopadzie 2016 r. firma Microsoft zaprzestała tworzenia aktualizacji definicji spamu dla filtrów SmartScreen Exchange i Outlook filtrach. Istniejące definicje spamu w filtrze SmartScreen zostały pozostawione, ale ich skuteczność prawdopodobnie będzie się pogarszać z czasem.

  - Sprawdź, czy ustawienie **Outlook** "Tylko listy Sejf" jest wyłączone: Gdy to ustawienie jest włączone, do Skrzynki odbiorczej są dostarczane tylko wiadomości od nadawców z listy nadawców lub listy adresatów programu Sejf użytkownika Sejf wiadomości e-mail od innych osób są automatycznie przenoszone do folderu Wiadomości-śmieci.

  Aby uzyskać więcej informacji o tych ustawieniach, zobacz [Konfigurowanie ustawień wiadomości-śmieci na Exchange Online pocztowych w Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Użyj dostępnych list bezpiecznych nadawców**: Aby uzyskać informacje, zobacz [Tworzenie list bezpiecznych nadawców](create-safe-sender-lists-in-office-365.md).

- **Sprawdź, czy użytkownicy są w granicach** wysyłania i odbierania [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) zgodnie z opisem w opisie usługi Exchange Online i wysyłania.

- **Autonomiczna usługa EOP:** użyj synchronizacji katalogów: Jeśli korzystasz z autonomicznej usługi EOP w celu ochrony lokalnej organizacji usługi Exchange, synchronizuj ustawienia użytkownika z usługą przy użyciu synchronizacji katalogów. W ten sposób zapewnisz, że listy Sejf nadawców użytkowników będą szanujene przez firmę EOP. Aby uzyskać więcej informacji, zobacz [Zarządzanie użytkownikami poczty przy użyciu synchronizacji katalogów](/exchange/standalone-eop/manage-mail-users-in-eop#synchronize-directories-with-azure-active-directory-connect-aad-connect).

## <a name="anti-spam-legislation"></a>Ustawa antyspamowa

W firmie Microsoft uważamy, że rozwój nowych technologii i samoregulacji wymaga wsparcia dla skutecznych zasad rządowych i ram prawnych. Cały świat spamu zachęcił wiele osób do ujednorzenia komercyjnych wiadomości e-mail. W wielu krajach są obecnie obowiązujące przepisy dotyczące rozsyłania spamu. Stany Zjednoczone mają prawo federalne i państwowe, którym podlega spam, a to uzupełnienie pozwala na ograniczanie spamu przy jednoczesnym włączaniu legalnego handlu elektronicznego do używania spamu. Działanie CAN-SPAM rozszerza dostępne narzędzia do blokowania nieuprawniających i zniechęcających wiadomości e-mail.
