---
title: Ochrona przed fałszerami
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
search.appverid:
- MET150
ms.assetid: d24bb387-c65d-486e-93e7-06a4f1a436c0
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
ms.localizationpriority: high
description: Administratorzy mogą dowiedzieć się więcej o funkcjach ochrony przed fałszerzami dostępnych w programie Exchange Online Protection (EOP), które mogą pomóc w zminimalizowaniu ataków na wyłudzanie informacji ze strony sfałszowanych nadawców i domen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b93f2e1543a70ca7b5dde8ab5e83d48fba5f5a5e
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2021
ms.locfileid: "63012510"
---
# <a name="anti-spoofing-protection-in-eop"></a>Ochrona przed fałszeringem w uciekaniu poczty eop

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online program EOP zawiera funkcje chroniące organizację przed fałszywymi (sfałszowaymi) nadawcami.

Jeśli chodzi o ochronę swoich użytkowników, firma Microsoft poważnie grozi wyłudzaniem informacji. Spoofing jest wspólną techniką używaną przez atakujących. **Spoofed messages appear to originate from someone or somewhere other than the actual source**. Ta technika jest często używana w kampaniach wyłudzających informacje, które służą do uzyskiwania poświadczeń użytkowników. Technologia ochrony przed fałszerskami w u żebyjmości EOP dokładnie sprawdza podszywanie się nagłówka Od w treści wiadomości (służy do wyświetlania nadawcy wiadomości w klientach poczty e-mail). Jeśli usługa EOP ma dużą pewność, że nagłówek Od jest sfałszowany, wiadomość jest identyfikowana jako sfałszowana.

W umiędzy EOP są dostępne następujące technologie ochrony przed fałszerami:

- **Uwierzytelnianie wiadomości** e-mail: Integralną częścią jakiegokolwiek nakładu pracy w zakresie ochrony przed fałszerskimi informacjami jest użycie uwierzytelniania poczty e-mail (nazywanego także sprawdzaniem poprawności poczty e-mail) przez rekordy SPF, DKIM i DMARC w systemie DNS. Te rekordy można skonfigurować dla swoich domen, aby docelowe systemy poczty e-mail sprawdzały poprawność wiadomości, które mają pochodzić od nadawców z Twoich domen. W przypadku wiadomości przychodzących Microsoft 365 wymaga uwierzytelniania poczty e-mail dla domen nadawcy. Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie pocztą e-mail w programie Microsoft 365](email-validation-and-authentication.md).

  Program EOP analizuje i blokuje wiadomości, których nie można uwierzytelnić za pomocą kombinacji standardowych metod uwierzytelniania poczty e-mail i technik reputacji nadawcy.

  ![Testy ochrony przed fałszer kontrolą EOP.](../../media/eop-anti-spoofing-protection.png)

- **Szczegółowe informacje o analizie** fałszowania: Przeglądanie fałszywych wiadomości od nadawców w domenach wewnętrznych i zewnętrznych w ciągu ostatnich 7 dni oraz zezwalanie na tych nadawców lub blokowanie ich. Aby uzyskać więcej informacji, zobacz [Spoof intelligence insight in EOP (Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md)).

- Zezwalanie na spoofed nadawców lub blokowanie ich na liście zezwalania **/** blokowania dzierżawy: Gdy zastąpisz werdykt w analizie fałszowania, fałszywy nadawca stanie się ręcznym wpisem zezwalania lub blokowania, który pojawia się tylko na karcie Fałsz na liście zezwalania/blokowania dzierżawy. Możesz również ręcznie utworzyć zezwalanie na nadawców lub blokować ich wpisy podszywają się pod nadawców, zanim zostaną one wykryte przez sfałszowaną inteligencję. Aby uzyskać więcej informacji, zobacz [Zarządzanie listą zezwalania/blokowania dzierżawy w u usługi EOP](tenant-allow-block-list.md).

- **Zasady ochrony przed wyłudzaniem** informacji: W usługach EOP i Microsoft Defender dla systemu Office 365 zasady ochrony przed wyłudzaniem informacji zawierają następujące ustawienia ochrony przed fałszerniem:
  - Włącz lub wyłącz analizę fałszowania.
  - Włączanie lub wyłączanie identyfikacji nieuwierzytanych Outlook nadawców.
  - Określ akcję dla zablokowanych sfałszowanych nadawców.

  Aby uzyskać więcej informacji, zobacz [Ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings).

  **Uwaga**: Zasady ochrony przed wyłudzaniem informacji w programie Defender Office 365 ochrony przed dodawaniem, w tym ochrony **przed personifikacji**. Aby uzyskać więcej informacji, zobacz [Ustawienia wyłączności w zasadach ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- **Raport Fałsz wykrywanie**: Aby uzyskać więcej informacji, zobacz [Raport Fałsz wykrywanie](view-email-security-reports.md#spoof-detections-report).

  **Uwaga**: Program Defender dla Office 365 organizacji może też wyświetlać informacje o próbach wyłudzania informacji za pomocą wykrywania w czasie rzeczywistym (plan 1) lub Eksploratora zagrożeń (plan 2). Aby uzyskać więcej informacji, [zobacz Microsoft 365 i reagowanie na zagrożenia](office-365-ti.md).

## <a name="how-spoofing-is-used-in-phishing-attacks"></a>Jak spoofing jest używany w atakach wyłudzających informacje

Spoofing wiadomości ma następujące negatywne skutki dla użytkowników:

- **Sfałszowane** wiadomości podszywają się pod użytkowników: Sfałszowana wiadomość może nakłaniać adresata do kliknięcia linku i podania poświadczeń, pobrania złośliwego oprogramowania lub odpowiadania na wiadomość z poufnej zawartości (nazywanej firmową wiadomością e-mail, która jest naruszona).

  Poniższy komunikat jest przykładem wyłudzania informacji, w przypadku których używany jest fałszywy nadawca msoutlook94@service.outlook.com:

  ![Personifikacja wiadomości wyłudzającej informacje service.outlook.com.](../../media/1a441f21-8ef7-41c7-90c0-847272dc5350.jpg)

  Ta wiadomość nie pochodzi od service.outlook.com, ale atakujący podszył się pod pole nagłówka Od, wyglądając tak, jak on. Była to próba nakłoowania adresata do **kliknięcia linku** zmiany hasła i podania poświadczeń.

  Poniższy komunikat zawiera przykład usługi BEC, która używa sfałszowanych domen poczty e-mail w contoso.com:

  ![Wiadomość wyłudzająca informacje — służbowe konto e-mail.](../../media/da15adaa-708b-4e73-8165-482fc9182090.jpg)

  Wiadomość wygląda na legalną, ale nadawca jest fałszywy.

- **Użytkownicy mylą prawdziwe wiadomości** z fałszywymi: Nawet użytkownicy, którzy wiedzą o wyłudzaniu informacji, mogą mieć trudności ze zobaczeniem różnic między rzeczywistymi wiadomościami a fałszywymi wiadomościami.

  Poniższy komunikat jest przykładem prawdziwej wiadomości resetowania hasła z konta zabezpieczeń Microsoft:

  ![Resetowanie legalnych haseł firmy Microsoft.](../../media/58a3154f-e83d-4f86-bcfe-ae9e8c87bd37.jpg)

  Wiadomość rzeczywiście pochodzi od firmy Microsoft, ale użytkownikom została narzu przesłana warunek podejrzana. Ponieważ różnica między rzeczywistą wiadomością z resetowaniem hasła a fałszywą wiadomością jest trudna, użytkownicy mogą zignorować tę wiadomość, zgłosić ją jako spam lub niepotrzebnie zgłosić tę wiadomość do firmy Microsoft jako próbną wyłudzanie informacji.

## <a name="different-types-of-spoofing"></a>Różne typy fałszowania

Firma Microsoft rozróżnia dwa różne typy wiadomości sfałszowanych:

- **Fałszowanie** wewnątrz organizacji: nazywane _także samodzielnym_ fałszowaniem. Przykład:

  - Nadawca i adresat znajdują się w tej samej domenie:
    > Od: chris@contoso.com <br> Do: michelle@contoso.com

  - Nadawca i adresat znajdują się w poddomenach tej samej domeny:
    > Od: laura@marketing.fabrikam.com <br> Do: julia@engineering.fabrikam.com

  - Nadawca i adresat znajdują się w różnych domenach należących do tej samej organizacji (co oznacza, że obie domeny są skonfigurowane jako zaakceptowane [domeny](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w tej samej organizacji):
    > Od: nadawca @ microsoft.com <br> Do: adresat @ bing.com

    W adresach e-mail są używane spacje, aby zapobiec zbieraniu spambotów.

  Wiadomości, których uwierzytelnianie [złożone nie powiodło](email-validation-and-authentication.md#composite-authentication) się ze względu na spoofing wewnątrz organizacji, zawierają następujące wartości nagłówka:

  `Authentication-Results: ... compauth=fail reason=6xx`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11`

  - `reason=6xx` oznacza spoofing wewnątrz organizacji.

  - SFTY to poziom bezpieczeństwa wiadomości. 9 oznacza wyłudzanie informacji, a 0,11 oznacza spoofing wewnątrz organizacji.

- **Fałszowanie między domenami**: Domeny nadawcy i adresata różnią się i nie są ze sobą relacjami (nazywanymi również domenami zewnętrznymi). Przykład:
    > Od: chris@contoso.com <br> Do: michelle@tailspintoys.com

  Wiadomości, których uwierzytelnianie [złożone nie powiedzie](email-validation-and-authentication.md#composite-authentication) się z powodu fałszowania między domenami, zawierają następujące wartości nagłówków:

  `Authentication-Results: ... compauth=fail reason=000/001`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22`

  - `reason=000` oznacza komunikat o błędzie jawnego uwierzytelniania wiadomości e-mail. `reason=001` wskazuje, że w wiadomości nie powiodło się niejawne uwierzytelnianie poczty e-mail.

  - `SFTY` to poziom bezpieczeństwa wiadomości. 9 oznacza wyłudzanie informacji, 0,22 wskazuje na fałszowanie między domenami.

> [!NOTE]
> Jeśli masz komunikat, taki jak ***compauth=fail reason=###** _ i chcesz wiedzieć o uwierzytelnieniu złożonym (współtworzenie) oraz o wartościach związanych z fałszowaniem, zobacz nagłówki wiadomości spamu _Anti w programie [Microsoft 365*](anti-spam-message-headers.md). Lub przejdź bezpośrednio do [*kodów przyczyn*](anti-spam-message-headers.md) .

Aby uzyskać więcej informacji na temat funkcji DMARC, zobacz Używanie [funkcji DMARC do sprawdzania poprawności wiadomości e-mail w programie Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="problems-with-anti-spoofing-protection"></a>Problemy z ochroną przed fałszerami

Wiadomo, że listy adresowe (nazywane również listami dyskusyjnymi) mają problemy z podszywniem się ze względu na sposób przesyłania dalej i modyfikowania wiadomości.

Na przykład Beata Laureano (glaureano@contoso.com) jest obserwowana ptaka, dołącza do listy adresowej birdwatchers@fabrikam.com i wysyła do tej listy następujący komunikat:

> **Od:** "Laureano" \<glaureano@contoso.com\> <br> **Do:** Lista dyskusyjna programu Birdwatcher \<birdwatchers@fabrikam.com\> <br> **Temat:** Doskonałe wyświetlanie niebieskich jays na górze Góry. Rainier w tym tygodniu <p> Każdy, kto chciałby sprawdzić widok w tym tygodniu z góry. Rainier?

Serwer listy adresowej odbiera wiadomość, modyfikuje jej zawartość i odtwarza ją dla członków listy. Odtworzona wiadomość ma taki sam adres od (glaureano@contoso.com), ale w wierszu tematu jest dodawany tag, a u dołu wiadomości jest dodawana stopka. Tego typu modyfikacje są częste w listach adresowych i mogą powodować fałszywie dodatnie wyniki fałszowania.

> **Od:** "Laureano" \<glaureano@contoso.com\> <br> **Do:** Lista dyskusyjna programu Birdwatcher \<birdwatchers@fabrikam.com\> <br> **Temat:** [BIRDWATCHERS] Doskonałe wyświetlanie niebieskich jays na górze Góry. Rainier w tym tygodniu <p> Każdy, kto chciałby sprawdzić widok w tym tygodniu z góry. Rainier? <p> Ta wiadomość została wysłana do listy dyskusyjnej birdwatchers. W każdej chwili możesz anulować subskrypcję.

Aby ułatwić wiadomościom listy adresowej przejście kontroli przed fałszowaniem, wykonaj następujące czynności w zależności od tego, czy masz kontrolę nad listą adresową:

- Twoja organizacja jest właścicielem listy adresowej:

  - Zapoznaj się z często zadawanymi pytaniami w DMARC.org: Działam listą adresową i chcę współdziałać z [DMARC, co mam zrobić?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F).

  - Przeczytaj instrukcje z tego wpisu w blogu: Porada dla operatorów listy adresowej współdziałających z [DMARC w celu uniknięcia niepowodzeń](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures).

  - Rozważ zainstalowanie aktualizacji na serwerze listy adresowej w celu obsługi funkcji ARC, zobacz <http://arc-spec.org>.

- Twoja organizacja nie jest właścicielem listy adresowej:

  - Poproś opiekuna listy adresowej o skonfigurowanie uwierzytelniania poczty e-mail dla domeny, z których jest przekazywanie na listę adresową.

    Gdy nadawcy odpowiedzą z powrotem do właścicieli domen, że powinni skonfigurować rekordy uwierzytelniania poczty e-mail, spowodują oni podjęcie działania. Firma Microsoft współpracuje również z właścicielami domen w celu publikowania wymaganych rekordów, ale pomaga jeszcze bardziej, gdy poszczegótni użytkownicy o to poprosili.

  - Utwórz reguły skrzynki odbiorczej w kliencie poczty e-mail, aby przenosić wiadomości do skrzynki odbiorczej. Możesz również poprosić administratorów o skonfigurowanie zastępować zgodnie z opisem w analizie fałszerów w u usługi [EOP](learn-about-spoof-intelligence.md) i zarządzaniu listą zezwalania [/blokowania dzierżawy](tenant-allow-block-list.md).

  - Użyj listy zezwalania/blokowania dzierżawy, aby utworzyć zastępowanie listy adresowej, aby traktować ją jak legalną. Aby uzyskać więcej informacji, zobacz [Zezwalanie na dodawanie na liście zezwalania/blokowania dzierżawy](manage-tenant-allows.md).

Jeśli wszystko inne zawiedzie, możesz zgłosić tę wiadomość firmie Microsoft jako fałszywie dodatnią. Aby uzyskać więcej informacji, zobacz [Zgłaszanie wiadomości i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="considerations-for-anti-spoofing-protection"></a>Zagadnienia dotyczące ochrony przed fałszerkami

Jeśli jesteś administratorem, który obecnie wysyła wiadomości do firmy Microsoft 365, musisz się upewnić, że poczta e-mail jest poprawnie uwierzytelniona. W przeciwnym razie może zostać oznaczona jako spam lub wyłudzanie informacji. Aby uzyskać więcej informacji, zobacz [Rozwiązania dla nadawców, którzy wysyłają nieuwierzytane wiadomości e-mail](email-validation-and-authentication.md#solutions-for-legitimate-senders-who-are-sending-unauthenticated-email).

Nadawcy z listy nadawców indywidualnych użytkowników (lub administratorów) w Sejf nadawców pomijają części stosu filtrowania, w tym ochronę przed fałszerami. Aby uzyskać więcej informacji, [zobacz Outlook Sejf nadawców](create-safe-sender-lists-in-office-365.md#use-outlook-safe-senders).

Administratorzy powinni unikać (jeśli to możliwe) używania dozwolonych list nadawców lub dozwolonych list domen. Ci nadawcy pomijają całą ochronę przed spamem, fałszowaniem i wyłudzaniem informacji, a także uwierzytelnianie nadawcy (SPF, DKIM, DMARC). Aby uzyskać więcej informacji, zobacz [Używanie dozwolonych list nadawców lub dozwolonych list domen](create-safe-sender-lists-in-office-365.md#use-allowed-sender-lists-or-allowed-domain-lists).
