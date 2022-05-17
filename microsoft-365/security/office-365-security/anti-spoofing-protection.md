---
title: Ochrona przed spoofingiem
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
description: Administratorzy mogą dowiedzieć się więcej o funkcjach ochrony przed fałszowaniem dostępnych w Exchange Online Protection (EOP), które mogą pomóc w wyeliminowaniu ataków phishingowych ze strony sfałszowanych nadawców i domen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 446b82d668041a476d748956008002c42a92a7f3
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435462"
---
# <a name="anti-spoofing-protection-in-eop"></a>Ochrona przed fałszowaniem w ramach EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacji Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, EOP zawiera funkcje ułatwiające ochronę organizacji przed fałszowaniem (sfałszowanych) nadawców.

Jeśli chodzi o ochronę użytkowników, firma Microsoft poważnie traktuje zagrożenie wyłudzaniem informacji. Fałszowanie jest powszechną techniką używaną przez osoby atakujące. **Fałszywe wiadomości wydają się pochodzić od kogoś lub innego miejsca niż rzeczywiste źródło**. Ta technika jest często używana w kampaniach wyłudzania informacji, które są przeznaczone do uzyskiwania poświadczeń użytkownika. Technologia ochrony przed fałszowaniem w ramach operacji EOP sprawdza w szczególności fałszerość nagłówka From w treści wiadomości (używanego do wyświetlania nadawcy wiadomości w klientach poczty e-mail). Gdy funkcja EOP ma dużą pewność, że nagłówek From jest sfałszowany, komunikat jest identyfikowany jako sfałszowany.

W ramach EOP dostępne są następujące technologie ochrony przed fałszowaniem:

- **Uwierzytelnianie poczty e-mail**: integralną częścią wszelkich działań chroniących przed fałszowaniem jest użycie uwierzytelniania poczty e-mail (znanego również jako weryfikacja poczty e-mail) przez rekordy SPF, DKIM i DMARC w systemie DNS. Te rekordy można skonfigurować dla domen, aby docelowe systemy poczty e-mail mogły sprawdzać poprawność komunikatów, które twierdzą, że pochodzą od nadawców w domenach. W przypadku komunikatów przychodzących Microsoft 365 wymaga uwierzytelniania poczty e-mail dla domen nadawcy. Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie za pomocą poczty e-mail w Microsoft 365](email-validation-and-authentication.md).

  Funkcja EOP analizuje i blokuje komunikaty, których nie można uwierzytelnić za pomocą kombinacji standardowych metod uwierzytelniania poczty e-mail i technik reputacji nadawcy.

  :::image type="content" source="../../media/eop-anti-spoofing-protection.png" alt-text="Testy ochrony przed fałszowaniem EOP" lightbox="../../media/eop-anti-spoofing-protection.png":::

- **Szczegółowe informacje na temat fałszowania analizy**: przejrzyj sfałszowane komunikaty od nadawców w domenach wewnętrznych i zewnętrznych w ciągu ostatnich 7 dni oraz zezwalaj na te nadawcy lub blokuj ich. Aby uzyskać więcej informacji, zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach EOP](learn-about-spoof-intelligence.md)).

- **Zezwalaj lub blokuj sfałszowanych nadawców na liście dozwolonych/blokowych dzierżawy**: Po zastąpieniu werdyktu w analizie analizy fałszowania sfałszowany nadawca staje się ręcznym wpisem zezwalającym lub blokowym, który pojawia się tylko na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców. Możesz również ręcznie utworzyć wpisy zezwalania lub blokowania dla nadawców podszywania się, zanim zostaną wykryte przez analizę fałszowania. Aby uzyskać więcej informacji, zobacz [Manage the Tenant Allow/Block List in EOP (Zarządzanie listą dozwolonych/zablokowanych dzierżaw w ramach operacji EOP](tenant-allow-block-list.md)).

- **Zasady ochrony przed wyłudzaniem informacji**: W ramach EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender zasady ochrony przed wyłudzaniem informacji zawierają następujące ustawienia ochrony przed fałszowaniem:
  - Włącz lub wyłącz analizę fałszowania.
  - Włącz lub wyłącz nieuwierzytelnione wskaźniki nadawcy w Outlook.
  - Określ akcję dla zablokowanych sfałszowanych nadawców.

  Aby uzyskać więcej informacji, zobacz [Ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings).

  **Uwaga**: zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender zawierają dodatkowe zabezpieczenia, w tym ochronę **przed personifikacją**. Aby uzyskać więcej informacji, zobacz [Ustawienia wyłączności w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- **Raport dotyczący wykrywania podróbek**: Aby uzyskać więcej informacji, zobacz [Raport wykrywania fałszowania](view-email-security-reports.md#spoof-detections-report).

  **Uwaga**: Ochrona usługi Office 365 w usłudze Defender organizacje mogą również używać wykrywania w czasie rzeczywistym (plan 1) lub Eksploratora zagrożeń (plan 2) do wyświetlania informacji o próbach wyłudzania informacji. Aby uzyskać więcej informacji, zobacz [Microsoft 365 badanie zagrożeń i reagowanie.](office-365-ti.md)

## <a name="how-spoofing-is-used-in-phishing-attacks"></a>Jak fałszowanie jest używane w atakach wyłudzania informacji

Fałszowanie wiadomości ma następujące negatywne konsekwencje dla użytkowników:

- **Sfałszowane wiadomości oszukują użytkowników**: sfałszowana wiadomość może skłonić odbiorcę do kliknięcia linku i rezygnacji z poświadczeń, pobrania złośliwego oprogramowania lub odpowiedzi na wiadomość z poufną zawartością (znaną jako naruszenie zabezpieczeń poczty e-mail lub BEC).

  Poniższy komunikat jest przykładem wyłudzania informacji, który używa sfałszowanego nadawcy msoutlook94@service.outlook.com:

  ![Service.outlook.com podszywanie się pod wiadomość wyłudzającą informacje.](../../media/1a441f21-8ef7-41c7-90c0-847272dc5350.jpg)

  Ta wiadomość nie pochodzi z service.outlook.com, ale osoba atakująca sfałszowała pole **Nagłówka Od** , aby wyglądało to tak, jak miało to miejsce. Była to próba nakłonienia adresata do kliknięcia linku **zmiany hasła** i rezygnacji z poświadczeń.

  Poniższy komunikat jest przykładem usługi BEC, która używa sfałszowanej domeny poczty e-mail contoso.com:

  ![Wiadomość wyłudzająca informacje — naruszenie zabezpieczeń poczty e-mail w firmie.](../../media/da15adaa-708b-4e73-8165-482fc9182090.jpg)

  Wiadomość wygląda legalnie, ale nadawca jest sfałszowany.

- **Użytkownicy mylą prawdziwe wiadomości dla fałszywych**: Nawet użytkownicy, którzy wiedzą o wyłudzaniu informacji, mogą mieć trudności z zobaczeniem różnic między rzeczywistymi wiadomościami a sfałszowanymi wiadomościami.

  Poniższy komunikat jest przykładem prawdziwego komunikatu resetowania hasła z konta Microsoft Security:

  ![Prawidłowe resetowanie hasła przez firmę Microsoft.](../../media/58a3154f-e83d-4f86-bcfe-ae9e8c87bd37.jpg)

  Wiadomość naprawdę pochodzi od firmy Microsoft, ale użytkownicy zostali warunkowi podejrzani. Ponieważ różnica między prawdziwą wiadomością resetowania hasła a fałszywą jest trudna, użytkownicy mogą ignorować tę wiadomość, zgłaszać ją jako spam lub niepotrzebnie zgłaszać wiadomość firmie Microsoft jako wyłudzanie informacji.

## <a name="different-types-of-spoofing"></a>Różne typy fałszowania

Firma Microsoft rozróżnia dwa różne typy sfałszowanych komunikatów:

- **Fałszowanie wewnątrz organizacji**: znane _również jako_ samoobsługowe fałszowanie. Przykład:

  - Nadawca i adresat znajdują się w tej samej domenie:
    > Od: chris@contoso.com <br> Do: michelle@contoso.com

  - Nadawca i adresat znajdują się w poddomenach tej samej domeny:
    > Od: laura@marketing.fabrikam.com <br> Do: julia@engineering.fabrikam.com

  - Nadawca i adresat znajdują się w różnych domenach należących do tej samej organizacji (oznacza to, że obie domeny są skonfigurowane jako [akceptowane domeny](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w tej samej organizacji):
    > Od: nadawca @ microsoft.com <br> Do: adresat @ bing.com

    Spacje są używane na adresach e-mail, aby zapobiec zbieraniu spambotów.

  Komunikaty, które nie obsługują [uwierzytelniania złożonego](email-validation-and-authentication.md#composite-authentication) z powodu fałszowania wewnątrz organizacji, zawierają następujące wartości nagłówka:

  `Authentication-Results: ... compauth=fail reason=6xx`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11`

  - `reason=6xx` oznacza fałszowanie wewnątrz organizacji.

  - SFTY to poziom bezpieczeństwa komunikatu. 9 wskazuje na wyłudzanie informacji. 11 wskazuje fałszowanie wewnątrz organizacji.

- **Fałszowanie między domenami**: domeny nadawcy i adresata są różne i nie mają ze sobą żadnych relacji (znanych również jako domeny zewnętrzne). Przykład:
    > Od: chris@contoso.com <br> Do: michelle@tailspintoys.com

  Komunikaty, które nie obsługują [uwierzytelniania złożonego](email-validation-and-authentication.md#composite-authentication) z powodu fałszowania między domenami, zawierają następujące wartości nagłówków:

  `Authentication-Results: ... compauth=fail reason=000/001`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22`

  - `reason=000` wskazuje, że wiadomość nie powiodła się jawne uwierzytelnianie poczty e-mail. `reason=001` wskazuje, że wiadomość nie powiodła się niejawne uwierzytelnianie poczty e-mail.

  - `SFTY` to poziom bezpieczeństwa komunikatu. 9 wskazuje na wyłudzanie informacji, 0,22 wskazuje fałszowanie między domenami.

> [!NOTE]
> Jeśli otrzymasz komunikat taki jak ***compauth=fail reason=###** _ i musisz wiedzieć o uwierzytelnianiu złożonym (compauth) i wartościach związanych z fałszowaniem, zobacz [nagłówki wiadomości _Anti-spam w Microsoft 365*](anti-spam-message-headers.md). Możesz też przejść bezpośrednio do kodów [*przyczyn*](anti-spam-message-headers.md) .

Aby uzyskać więcej informacji na temat usługi DMARC, zobacz [Używanie funkcji DMARC do weryfikowania poczty e-mail w Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="problems-with-anti-spoofing-protection"></a>Problemy z ochroną przed fałszowaniem

Wiadomo, że listy mailingowe (nazywane również listami dyskusyjnymi) mają problemy z przeciwdziałaniem fałszowaniu ze względu na sposób przesyłania dalej i modyfikowania wiadomości.

Na przykład Gabriela Laureano (glaureano@contoso.com) jest zainteresowana obserwacją ptaków, dołącza do listy adresowej birdwatchers@fabrikam.com i wysyła na listę następującą wiadomość:

> **Z:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Do:** Lista dyskusyjna obserwatora ptaków \<birdwatchers@fabrikam.com\> <br> **Temat:** Świetne oglądanie niebieskich sójek na szczycie Mt. Rainier w tym tygodniu <p> Każdy, kto chce sprawdzić oglądania w tym tygodniu z Mt. Rainier?

Serwer listy adresowej odbiera wiadomość, modyfikuje jej zawartość i odtwarza ją do członków listy. Odtworzony komunikat ma ten sam adres od (glaureano@contoso.com), ale tag jest dodawany do wiersza tematu, a stopka jest dodawana do dołu komunikatu. Ten typ modyfikacji jest typowy na listach wysyłkowych i może powodować fałszywie dodatnie pod kątem fałszowania.

> **Z:** "Gabriela Laureano" \<glaureano@contoso.com\> <br> **Do:** Lista dyskusyjna obserwatora ptaków \<birdwatchers@fabrikam.com\> <br> **Temat:** [BIRDWATCHERS] Świetne oglądanie niebieskich sójek na szczycie Mt. Rainier w tym tygodniu <p> Każdy, kto chce sprawdzić oglądania w tym tygodniu z Mt. Rainier? <p> Ta wiadomość została wysłana do listy dyskusyjnej birdwatchers. Subskrypcję można anulować w dowolnym momencie.

Aby ułatwić wysyłanie wiadomości z listy pocztowej, wykonaj następujące czynności w zależności od tego, czy kontrolujesz listę adresową:

- Twoja organizacja jest właścicielem listy adresowej:

  - Sprawdź często zadawane pytania na stronie DMARC.org: [Mam obsługiwać listę adresową i chcę współdziałać z usługą DMARC, co mam zrobić?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F).

  - Przeczytaj instrukcje podane w tym wpisie w blogu: [Porada dotycząca operatorów list pocztowych w celu współdziałania z usługą DMARC w celu uniknięcia błędów](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures).

  - Rozważ zainstalowanie aktualizacji na serwerze listy adresowej w celu obsługi usługi ARC, zobacz <http://arc-spec.org>.

- Twoja organizacja nie jest właścicielem listy adresowej:

  - Poproś opiekuna listy adresowej o skonfigurowanie uwierzytelniania poczty e-mail dla domeny, z którą jest przekazywana lista adresów.

    Gdy wystarczająco dużo nadawców odpowiada właścicielom domeny, że powinni skonfigurować rekordy uwierzytelniania poczty e-mail, skłania ich to do podjęcia działań. Firma Microsoft współpracuje również z właścicielami domen w celu publikowania wymaganych rekordów, ale pomaga jeszcze bardziej, gdy żądają tego poszczególni użytkownicy.

  - Utwórz reguły skrzynki odbiorczej w kliencie poczty e-mail, aby przenieść wiadomości do skrzynki odbiorczej. Możesz również poprosić administratorów o skonfigurowanie przesłonięć zgodnie z opisem w artykule Spoof intelligence insight in EOP and Manage the Tenant Allow/Block List ( [Fałszowanie analizy w ramach operacji EOP](learn-about-spoof-intelligence.md) i [zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md)).

  - Użyj listy dozwolonych/zablokowanych dzierżaw, aby utworzyć przesłonięcia listy adresowej, aby traktować ją jako zgodną z prawem. Aby uzyskać więcej informacji, zobacz [Dodawanie opcji zezwala na korzystanie z listy dozwolonych/zablokowanych dzierżaw](manage-tenant-allows.md).

Jeśli wszystko inne nie powiedzie się, możesz zgłosić wiadomość jako fałszywie dodatnią firmie Microsoft. Aby uzyskać więcej informacji, zobacz [Zgłaszanie komunikatów i plików do firmy Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="considerations-for-anti-spoofing-protection"></a>Zagadnienia dotyczące ochrony przed fałszowaniem

Jeśli jesteś administratorem, który obecnie wysyła wiadomości do Microsoft 365, musisz upewnić się, że wiadomość e-mail jest prawidłowo uwierzytelniona. W przeciwnym razie może zostać oznaczony jako spam lub wyłudzanie informacji. Aby uzyskać więcej informacji, zobacz [Solutions for legalnych nadawców, którzy wysyłają nieuwierzytelnioną wiadomość e-mail](email-validation-and-authentication.md#solutions-for-legitimate-senders-who-are-sending-unauthenticated-email).

Nadawcy na liście Sejf nadawców poszczególnych użytkowników (lub administratorów) pomijają części stosu filtrowania, w tym ochronę przed fałszowaniem. Aby uzyskać więcej informacji, zobacz [Outlook Sejf Nadawcy](create-safe-sender-lists-in-office-365.md#use-outlook-safe-senders).

Administratorzy powinni unikać (jeśli to możliwe) używania list dozwolonych nadawców lub list dozwolonych domen. Ci nadawcy pomijają wszystkie spam, fałszowanie i ochronę przed wyłudzaniem informacji, a także uwierzytelnianie nadawcy (SPF, DKIM, DMARC). Aby uzyskać więcej informacji, zobacz [Używanie list dozwolonych nadawców lub list dozwolonych domen](create-safe-sender-lists-in-office-365.md#use-allowed-sender-lists-or-allowed-domain-lists).
