---
title: Zasady ochrony przed wyłudzaniem informacji
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: 5a6f2d7f-d998-4f31-b4f5-f7cbf6f38578
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o zasadach ochrony przed wyłudzaniem informacji dostępnych w programach Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5389e83634bc92dd01908b16e8ca0a76dd76c765
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475702"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Zasady ochrony przed wyłudzaniem informacji w programie Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Zasady konfigurowania ustawień ochrony przed wyłudzaniem informacji są dostępne w organizacjach Microsoft 365 ze skrzynkami pocztowymi firmy Exchange Online, w autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych oraz Ochrona usługi Office 365 w usłudze Microsoft Defender organizacji.

Oto przykłady Ochrona usługi Office 365 w usłudze Microsoft Defender organizacji:

- Microsoft 365 Enterprise E5, Microsoft 365 Education A5 itp.
- [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender jako dodatek](https://products.office.com/exchange/advance-threat-protection)

W poniższej tabeli przedstawiono różnice między zasadami ochrony przed wyłudzaniem informacji w UAD a zasadami ochrony przed Ochrona usługi Office 365 w usłudze Defender wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Defender:

|Funkcja|Zasady ochrony przed wyłudzaniem informacji w uchcie EOP|Zasady ochrony przed wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Defender|
|---|:---:|:---:|
|Zasady domyślne utworzone automatycznie|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Tworzenie zasad niestandardowych|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Ustawienia wspólnych zasad<sup>\*</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Spoof settings|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Pierwszy kontakt porada dotycząca bezpieczeństwa|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|
|Ustawienia personifikacji||![Znacznik wyboru](../../media/checkmark.png)|
|Zaawansowane progi wyłudzania informacji||![Znacznik wyboru](../../media/checkmark.png)|

<sup>\*</sup> W zasadach domyślnych nazwa i opis zasad są tylko do odczytu (opis jest pusty) i nie można określić, kogo dotyczą zasady (zasady domyślne dotyczą wszystkich adresatów).

Aby skonfigurować zasady ochrony przed wyłudzaniem informacji, zobacz następujące artykuły:

- [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP](configure-anti-phishing-policies-eop.md)
- [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md)

W dalszej części tego artykułu opisano ustawienia dostępne w zasadach ochrony przed wyłudzaniem informacji w umacie EOP i Ochrona usługi Office 365 w usłudze Defender.

## <a name="common-policy-settings"></a>Ustawienia wspólnych zasad

Poniższe ustawienia zasad są dostępne w zasadach ochrony przed wyłudzaniem informacji w u Ochrona usługi Office 365 w usłudze Defender:

- **Nazwa**: Nie można zmienić nazwy domyślnych zasad ochrony przed wyłudzaniem informacji. Po utworzeniu niestandardowych zasad ochrony przed wyłudzaniem informacji nie można zmienić ich nazw w portalu Microsoft 365 Defender informacje.

- **Opis** Nie można dodawać opisu do domyślnych zasad ochrony przed wyłudzaniem informacji, ale można dodawać i zmieniać opisy niestandardowych zasad niestandardowych tworzyć.

- **Użytkownicy, grupy i domeny**: Identyfikuje adresatów wewnętrznych, do których mają zastosowanie zasady ochrony przed wyłudzaniem informacji. Ta wartość jest wymagana w zasadach niestandardowych i nie jest dostępna w zasadach domyślnych (zasady domyślne są stosowane do wszystkich adresatów).

  Możesz użyć tylko raz warunku lub wyjątku, ale możesz określić wiele wartości dla warunku lub wyjątku. Wiele wartości takich samych warunków lub wyjątków używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). W różnych warunkach lub wyjątkach jest używanie logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

  - **Użytkownicy**: co najmniej jedna skrzynka pocztowa, użytkownicy poczty lub kontakty poczty w organizacji.
  - **Grupy**: Co najmniej jedna grupa w organizacji.
  - **Domeny**: Co najmniej jedna ze skonfigurowanych [zaakceptowanych domen](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w Microsoft 365.

  - **Wyklucz tych użytkowników, grupy i domeny**: Wyjątki dla zasad. Ustawienia i zachowanie są dokładnie takie, jak warunki:
    - **Użytkownicy**
    - **Grupy**
    - **Domeny**

  > [!NOTE]
  > W niestandardowych zasadach ochrony przed wyłudzaniem informacji w celu zidentyfikowania adresatów wiadomości, których dotyczą te zasady, wymagane jest  co najmniej jedno zaznaczenie ustawień Użytkownicy **,** grupy i <u>domeny</u>. Zasady ochrony przed wyłudzaniem informacji w programie [](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) Ochrona usługi Office 365 w usłudze Defender także ustawienia personifikacji, gdzie można określić adresy e-mail poszczególnych nadawców lub domeny nadawców, które będą otrzymywać ochronę przed personifikacji zgodnie z opisem w dalszej części tego artykułu.<u></u>

## <a name="spoof-settings"></a>Spoof settings

Spoofing (Fałszowanie) jest wyświetlany w sytuacji, gdy adres Nadawca w wiadomości e-mail (adres nadawcy wyświetlany w klientach poczty e-mail) nie jest taki, jak domena źródła poczty e-mail. Aby uzyskać więcej informacji na temat fałszowania, zobacz Ochrona [przed fałszowaniem w programie Microsoft 365](anti-spoofing-protection.md).

Poniższe ustawienia fałszowania są dostępne w zasadach ochrony przed wyłudzaniem informacji w u Ochrona usługi Office 365 w usłudze Defender:

- **Włącz analizę fałszowania**: Pozwala włączać lub wyłączać funkcję fałszowania. Zalecamy pozostawienie jej włączonej.

  Gdy jest włączona analiza fałszerska, analiza fałszerska pokazuje sfałszowanych nadawców, którzy zostali automatycznie wykryci i zachęceni lub zablokowani przez fałszywą inteligencję. Możesz ręcznie zastąpić werdykt analizy fałszowania, aby zezwolić na dostęp do informacji wykrytych fałszywych nadawców lub zablokować ich. Jednak gdy to zrobisz, fałszywy nadawca zniknie z szczegółowych informacji o analizie fałszowania i będzie teraz widoczny tylko na  karcie Fałsz na liście zezwalania/blokowania dzierżawy. Na liście zezwalania/blokowania dzierżawy można też ręcznie tworzyć wpisy zezwalające lub blokowane dla sfałszowanych nadawców. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

  - [Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md)
  - [Zarządzanie listą zezwalania/blokowania dzierżawy w uciekaniu usługi EOP](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - Ochrona przed fałszerskami jest domyślnie włączona w domyślnych zasadach ochrony przed wyłudzaniem informacji i we wszystkich nowych niestandardowych zasadach ochrony przed wyłudzaniem informacji, które są przez Ciebie tworzyć.
  > - Nie musisz wyłączać ochrony przed fałszeringem, jeśli rekord MX nie Microsoft 365; zamiast tego włącz funkcję rozszerzonego filtrowania dla łączników. Aby uzyskać instrukcje, [zobacz Ulepszone filtrowanie łączników w programie Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  > - Wyłączenie ochrony przed fałszeringem powoduje tylko  wyłączenie niejawnej ochrony przed fałszowaniem na podstawie [testów uwierzytelniania złożonego](email-validation-and-authentication.md#composite-authentication). Jeśli nadawca nie sprawdzi _jawnego_ [ciągu DMARC](use-dmarc-to-validate-email.md) w miejscu, w którym ustawiono zasady do kwarantanny lub odrzucenia, wiadomość jest nadal poddana kwarantannie lub odrzucana.

- **Powiadomienia nieuwierzytanych nadawców**: Te powiadomienia są dostępne tylko wtedy, gdy jest włączona sfałszowana inteligencja. Zapoznaj się z informacjami w następnej sekcji.
- Akcje **: W** przypadku wiadomości od zablokowanych sfałszowanych nadawców (automatycznie zablokowanych przez fałszywą inteligencję lub ręcznie zablokowanych na liście Zezwalaj/Zablokuj dzierżawy) możesz także określić akcję, która ma być podejmowane w porównaniu z wiadomościami:
  - **Przenoszenie wiadomości do folderów wiadomości-śmieci** adresatów: jest to wartość domyślna. Wiadomość zostanie dostarczona do skrzynki pocztowej i przeniesiona do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci Exchange Online pocztowych w programie Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Poddaj wiadomość kwarantannie**: Wysyła wiadomość do kwarantanny zamiast do zamierzonych adresatów. Aby uzyskać informacje na temat kwarantanny, zobacz następujące artykuły:
    - [Kwarantanna w Microsoft 365](quarantine-email-messages.md)
    - [Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator w Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Znajdowanie i zwalnianie wiadomości poddanych kwarantannie jako użytkownik w programie Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Jeśli wybierzesz pozycję Poddaj wiadomość kwarantannie, możesz także wybrać zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę przed fałszerami. Zasady kwarantanny określają, co użytkownicy mogą robić w kwarantannie wiadomości i czy użytkownicy otrzymują powiadomienia kwarantanny. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

### <a name="unauthenticated-sender"></a>Nieuwierzyta nadawca

Powiadomienia nieuwierzytanych nadawców są częścią ustawień [](#spoof-settings) fałszowania dostępnych w zasadach ochrony przed wyłudzaniem informacji w uchcie EOP i w Ochrona usługi Office 365 w usłudze Defender zgodnie z opisem w poprzedniej sekcji. Następujące ustawienia są dostępne tylko wtedy, gdy jest włączona sfałszowana inteligencja:

- **Pokaż (?)** dla nieuwierzytanych nadawców w celu fałszowania: To powiadomienie powoduje dodanie znaku zapytania do zdjęcia nadawcy w polu Od, jeśli wiadomość nie przejdzie testów SPF lub DKIM i wiadomość nie przejdzie uwierzytelniania DMARC lub [złożonego](email-validation-and-authentication.md#composite-authentication). Gdy to ustawienie jest wyłączone, znak zapytania nie jest dodawany do fotografii nadawcy.

- Czy jest wyświetlany tag **"** za pośrednictwem"? To powiadomienie dodaje tag za pośrednictwem <u>(chris@contoso.com za</u> pośrednictwem usługi fabrikam.com) w polu Od, jeśli domena w polu adresu Od (nadawca wiadomości wyświetlana w klientach poczty e-mail) różni się od domeny w podpisie DKIM lub adresu **MAIL FROM**. Aby uzyskać więcej informacji o tych adresach, zobacz [Omówienie standardów wiadomości e-mail](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

Aby zapobiec dodaniu znaku zapytania lub tagu za pośrednictwem do wiadomości od określonych nadawców, dostępne są następujące opcje:

- Zezwalaj fałszywym nadawcom na wgląd w analizę [fałszowania](learn-about-spoof-intelligence.md) lub ręcznie na liście [zezwalania/blokowania dzierżawy](tenant-allow-block-list.md). Zezwolenie nadawcy na spoofed sender will prevent the via tag from the messages from the sender when unauthenticated sender identification is disabled (Identyfikacja nieuwierzytanego nadawcy) nie będzie wyświetlana w wiadomościach od tego nadawcy.
- [Konfigurowanie uwierzytelniania poczty e-mail](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) dla domeny nadawcy.
  - Dla znaku zapytania na zdjęciu nadawcy najważniejsze są SPF lub DKIM.
  - W przypadku tagu za pośrednictwem potwierdź w podpisie DKIM lub w adresie **MAIL FROM** dopasowania (lub jest poddomeną) domeny w adresie Od.

Aby uzyskać więcej informacji, zobacz [Identyfikowanie podejrzanych wiadomości Outlook.com i Outlook w sieci Web](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="first-contact-safety-tip"></a>Pierwszy kontakt porada dotycząca bezpieczeństwa

Ustawienia **Pokaż pierwszy kontakt porada dotycząca bezpieczeństwa** są dostępne w usługach EOP i Ochrona usługi Office 365 w usłudze Defender organizacji i nie są zależne od ustawień ochrony przed fałszerami i personifikacji. Przedstawione porada dotycząca bezpieczeństwa są wyświetlane adresatom w następujących scenariuszach:

- Gdy po raz pierwszy otrzyma wiadomość od nadawcy
- Nie są one często wysyłane do nadawcy.

:::image type="content" source="../../media/safety-tip-first-contact-one-recipient.png" alt-text="Pierwszy kontakt porada dotycząca bezpieczeństwa wiadomości z jednym adresatem" lightbox="../../media/safety-tip-first-contact-one-recipient.png":::

:::image type="content" source="../../media/safety-tip-first-contact-multiple-recipients.png" alt-text="Pierwszy kontakt porada dotycząca bezpieczeństwa wiadomości z wieloma adresatami" lightbox="../../media/safety-tip-first-contact-multiple-recipients.png":::

Ta funkcja zapewnia dodatkową warstwę ochrony przed potencjalnymi atakami personifikacji, dlatego zalecamy jej włączenie.

Pierwszy kontakt porada dotycząca bezpieczeństwa zastępuje również konieczność utworzenia reguł przepływu poczty e-mail (nazywanych również regułami transportu), które dodają nagłówek o nazwie **X-MS-Exchange-EnableFirstContactSafetyTip** z wartością **Włącz** do wiadomości (chociaż ta funkcja jest nadal dostępna).

> [!NOTE]
> Jeśli wiadomość ma wielu adresatów, to czy porada jest wyświetlana i dla kogo jest oparty model dla większości. Jeśli większość adresatów nigdy lub nie otrzymuje wiadomości od tego nadawcy, adresaci, których to dotyczy, otrzymają poradę Niektórzy adresaci, którzy otrzymali **tę wiadomość.** Jeśli obawiasz się, że takie zachowanie ujawnia nawyki dotyczące komunikacji jednego adresata drugiemu, nie włączaj pierwszego kontaktu porada dotycząca bezpieczeństwa i zamiast tego używaj reguł przepływu poczty e-mail.

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia wyłączności w zasadach ochrony przed wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Microsoft Defender

W tej sekcji opisano ustawienia zasad, które są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender.

> [!NOTE]
> Domyślne zasady ochrony przed wyłudzaniem informacji w programie Ochrona usługi Office 365 w usłudze Defender zapewniają ochronę przed [fałszerami](set-up-anti-phishing-policies.md#spoof-settings) i analizą skrzynek pocztowych dla wszystkich adresatów. Jednak inne dostępne funkcje ochrony [personifikacji](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i ustawienia [zaawansowane](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) nie są konfigurowane ani włączone w zasadach domyślnych. Aby włączyć wszystkie funkcje ochrony, zmodyfikuj domyślne zasady ochrony przed wyłudzaniem informacji lub utwórz dodatkowe zasady ochrony przed wyłudzaniem informacji.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Personifikacja to miejsce, w którym nadawca lub domena poczty e-mail nadawcy w wiadomości wygląda podobnie do rzeczywistego nadawcy lub domeny:

- Przykład personifikacji domeny, contoso.com to ćóntoso.com.
- Personifikacja użytkownika to połączenie nazwy wyświetlanej i adresu e-mail użytkownika. Na przykład valeria Barrios (vbarrios@contoso.com) może zostać personifikowana jako Valeria Barrios, ale ma zupełnie inny adres e-mail.

> [!NOTE]
> Ochrona personifikacji wyszukuje podobne domeny. Jeśli na przykład domena jest contoso.com, jako próby personifikacji sprawdzamy inne domeny najwyższego poziomu (.com, .biz itp.), ale także domeny, które są dosyć podobne. Na przykład contosososo.com lub contoabcdef.com mogą być widoczne jako próby personifikacji contoso.com.

Spersonifikowana domena może być w inny sposób uznawana za legalną (zarejestrowaną domenę, skonfigurowane rekordy uwierzytelniania poczty e-mail itp.), z wyjątkiem sytuacji, gdy jej celem jest nakłonienie adresatów.

Następujące ustawienia personifikacji są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender:

- **Włączanie ochrony dla użytkowników**: zapobiega personifikacji określonych wewnętrznych lub zewnętrznych adresów e-mail **jako nadawców wiadomości**. Na przykład otrzymasz wiadomość e-mail od wiceprezesa ds. firmy z prośbą o wysłanie jej pewnych wewnętrznych informacji o firmie. Czy możesz to zrobić? Wiele osób przysłało odpowiedź bez przemyślenia.

  Możesz użyć chronionych użytkowników, aby dodać wewnętrzne i zewnętrzne adresy e-mail nadawcy w celu ochrony przed personifikacji. Ta lista nadawców, którzy są chronieni przed personifikacji użytkownika, różni się  od listy adresatów, do których mają zastosowanie zasady (wszyscy adresaci zasad domyślnych, określonymi adresatami skonfigurowanymi w ustawieniu Użytkownicy **,** grupy i domeny w [](#common-policy-settings) sekcji Ustawienia wspólnych zasad).

  > [!NOTE]
  >
  > - W każdej z zasad ochrony przed wyłudzaniem informacji możesz określić maksymalnie 350 chronionych użytkowników (adresy e-mail nadawców). Nie można określić tego samego chronionego użytkownika w wielu zasadach. Z tego względu niezależnie od liczby zasad, które mają zastosowanie do adresata, maksymalna liczba chronionych użytkowników (adresów e-mail nadawców) dla każdego adresata wynosi 350. Aby uzyskać więcej informacji na temat priorytetu zasad i sposobu zatrzymania przetwarzania zasad po zastosowaniu pierwszej zasady, zobacz Kolejność i [pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).
  > - Ochrona personifikacji użytkownika nie działa, jeśli nadawca i adresat wcześniej komunikowali się za pośrednictwem poczty e-mail. Jeśli nadawca i adresat nigdy nie komunikowali się za pośrednictwem poczty e-mail, wiadomość zostanie zidentyfikowany jako próba personifikacji.

  Domyślnie w celu ochrony użytkowników nie są konfigurowane żadne adresy e-mail **nadawców na potrzeby ochrony personifikacji**. Dlatego domyślnie żadne adresy e-mail nadawców nie są objęte ochroną personifikacji, zarówno w zasadach domyślnych, jak i w zasadach niestandardowych.

  Gdy dodasz wewnętrzne lub zewnętrzne adresy e-mail  do listy Użytkownicy w celu ochrony, wiadomości  od tych nadawców będą podlegały testom ochrony przed personifikacjami. Wiadomość jest sprawdzana pod kątem personifikacji, jeśli wiadomość jest  wysyłana do adresata, do których mają zastosowanie zasady (wszyscy adresaci zasad domyślnych; **Użytkownicy, grupy i adresaci domen** w zasadach niestandardowych). W przypadku wykrycia personifikacji w adresie e-mail nadawcy do wiadomości są stosowane akcje ochrony personifikacji dla użytkowników (co zrobić z wiadomością, czy wyświetlić porady dotyczące bezpieczeństwa personifikacji użytkowników itp.).

- **Włączanie ochrony domen**: zapobiega personifikacji określonych domen **w domenie nadawcy wiadomości**. Na przykład wszystkie posiadane [domeny (](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)zaakceptowane domeny) lub określone domeny niestandardowe (domeny, których jesteś właścicielem lub domenami partnerów). Ta lista domen  nadawców, które są chronione za pomocą personifikacji, różni  się od listy adresatów, do których mają zastosowanie zasady (wszyscy adresaci zasad domyślnych, określonymi adresatami skonfigurowanymi w ustawieniu Użytkownicy **,** grupy i domeny [](#common-policy-settings) w sekcji Ustawienia wspólnych zasad).

  > [!NOTE]
  > Maksymalna liczba chronionych domen, które można zdefiniować we wszystkich zasadach ochrony przed wyłudzaniem informacji, wynosi 50.

  Domyślnie żadna domena nadawcy nie jest skonfigurowana do ochrony personifikacji w **opcjach Włącz ochronę domen**. Dlatego domyślnie żadna domena nadawcy nie jest objęta ochroną personifikacji, zarówno w zasadach domyślnych, jak i w zasadach niestandardowych.

  Po dodaniu domen do listy **Włącz** ochronę domen wiadomości od nadawców w  tych domenach podlegają testom ochrony przed personifikacjami. Wiadomość jest sprawdzana pod kątem personifikacji, jeśli wiadomość jest  wysyłana do adresata, do których mają zastosowanie zasady (wszyscy adresaci zasad domyślnych; **Użytkownicy, grupy i adresaci domen** w zasadach niestandardowych). W przypadku wykrycia personifikacji w domenie nadawcy do wiadomości są stosowane akcje ochrony przed personifikacji dla domen (co zrobić z wiadomością, czy wyświetlić porady dotyczące bezpieczeństwa personifikacji użytkowników itp.).

- **Akcje**: Wybierz akcję, która ma być podejmowana względem wiadomości przychodzących, które zawierają próby personifikacji wobec chronionych użytkowników i chronionych domen w zasadach. Dla personifikacji chronionych użytkowników i personifikacji chronionych domen można określić różne akcje:
  - **Nie zastosuj żadnej akcji**
  - **Przekierowywanie wiadomości na inne** adresy e-mail: wysyła wiadomość do określonych adresatów zamiast do określonych adresatów.
  - **Przenoszenie wiadomości do folderów wiadomości-śmieci** adresatów: Wiadomość jest dostarczana do skrzynki pocztowej i przenoszony do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci Exchange Online pocztowych w programie Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Poddaj wiadomość kwarantannie**: Wysyła wiadomość do kwarantanny zamiast do zamierzonych adresatów. Aby uzyskać informacje na temat kwarantanny, zobacz następujące artykuły:
    - [Kwarantanna w Microsoft 365](quarantine-email-messages.md)
    - [Zarządzanie wiadomościami i plikami poddanymi kwarantannie jako administrator w Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Znajdowanie i zwalnianie wiadomości poddanych kwarantannie jako użytkownik w programie Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Jeśli wybierzesz pozycję Poddaj wiadomość kwarantannie, możesz również wybrać zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę personifikacji użytkownika lub personifikacji domeny. Zasady kwarantanny określają, co użytkownicy mogą robić w kwarantannie wiadomości. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

  - **Dostarczanie wiadomości i dodawanie innych adresów** do wiersza UDW: Dostarczanie wiadomości do określonych adresatów i dyskretne dostarczanie wiadomości do określonych adresatów.
  - **Usunąć wiadomość przed jej dostarczenia**: w trybie dyskretnym usuwa całą wiadomość wraz ze wszystkimi załącznikami.

- **Porady dotyczące bezpieczeństwa personifikacji**: Włącz lub wyłącz następujące porady dotyczące bezpieczeństwa personifikacji, które będą wyświetlane wiadomości, które nie będą sprawdzać personifikacji:
  - **Pokaż poradę dla personifikowanych użytkowników**: Adres Od zawiera pole **Umożliwiaj użytkownikom ochronę** użytkownika. Dostępne tylko wtedy **, gdy jest włączone** i skonfigurowane ustawienie Włącz ochronę dla użytkowników.
  - **Pokaż poradę dla spersonifikowanych domen**: Adres Od zawiera pole **Włącz domeny w celu ochrony** domeny. Dostępne tylko wtedy **, gdy jest** włączona i skonfigurowana włączanie ochrony domen.
  - **Pokaż** poradę dla nietypowych znaków: Adres Od zawiera nietypowe zestawy znaków (na przykład symbole matematyczne i tekst lub kombinację wielkich i małych liter) w  polu Umożliwiaj użytkownikom ochronę nadawcy lub Włącz domeny w celu ochrony domeny nadawcy.  Dostępne tylko wtedy **, gdy jest włączone i**   skonfigurowane ustawienie Włącz ochronę dla użytkowników lub Włącz ochronę domen.

- **Włączanie analizy skrzynek pocztowych**: Włączenie lub wyłączenie sztucznej inteligencji, która określa wzorce obsługi poczty e-mail użytkowników z częstymi kontaktami. To ustawienie ułatwia AI odróżnianie wiadomości od legalnych i personifikowanych nadawców.

  Na przykład Laureano Laureano (glaureano@contoso.com) jest dyrektorem generalną Twojej firmy, dlatego dodajesz ją jako chronionego nadawcę w ustawieniach  Zasad umożliwiania użytkownikom ochrony ustawień. Jednak niektórzy adresaci, do których mają zastosowanie zasady, regularnie komunikują się z dostawcą o imieniu Laureano (glaureano@fabrikam.com). Ponieważ w przypadku tych adresatów historia komunikacji jest glaureano@fabrikam.com, inteligencja skrzynek pocztowych nie będzie identyfikować wiadomości od usługi glaureano@fabrikam.com jako próby personifikacji glaureano@contoso.com dla tych adresatów.

  Aby korzystać z częstych kontaktów, które były poznane przez funkcje analizy skrzynek pocztowych (i których nie ma) w celu ochrony użytkowników przed atakami  personifikacji, możesz włączyć ochronę personifikacji analizy po włączeniu włączoną analizę skrzynki **pocztowej.**

- **Włączanie ochrony personifikacji** personifikacji: Włącz to ustawienie, aby określić akcję, która ma być wytyczysz wiadomości na podstawie wykrywania personifikacji z wyników analizy skrzynki pocztowej:
  - **Nie zastosuj żadnej akcji**: Zwróć uwagę, że ta wartość ma taki sam skutek jak włączenie analizy skrzynki **pocztowej, ale** wyłączenie ochrony przed personifikacjami włączoną **analizę**.
  - **Przekierowywanie wiadomości na inne adresy e-mail**
  - **Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**
  - **Poddaj kwarantannie** wiadomość: Jeśli wybierzesz tę akcję, możesz również wybrać zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę skrzynki pocztowej. Zasady kwarantanny określają, co użytkownicy mogą robić w kwarantannie wiadomości i czy użytkownicy otrzymują powiadomienia kwarantanny. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).
  - **Dostarczanie wiadomości i dodawanie innych adresów do wiersza UDW**
  - **Usunięcie wiadomości przed jej dostarczeniaą**

- **Dodaj zaufanych nadawców i domeny**: Wyjątki od ustawień ochrony personifikacji. Wiadomości od określonych nadawców i domen nadawcy nigdy nie są klasyfikowane przez zasady jako ataki oparte na personifikacji. Innymi słowy, akcja dla chronionych nadawców, chronionych domen lub ochrony skrzynki pocztowej nie jest stosowana do tych zaufanych nadawców ani domen nadawców. Maksymalne ograniczenie dla tych list to 1024 wpisy.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Zaawansowane progi wyłudzania informacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Poniższe zaawansowane progi wyłudzania informacji są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender. Te progi sterują wrażliwością na stosowanie modeli uczenia maszynowego do wiadomości w celu określenia werdyktu wyłudzania informacji:

- **1 — Standardowe**: jest to wartość domyślna. Ważność akcji podejmowanej w  związku z wiadomością zależy od stopnia pewności, że wiadomość jest próbą wyłudzenia informacji (niska, średnia, wysoka lub bardzo wysoka pewność). Na przykład w wiadomościach zidentyfikowanych jako próby wyłudzenia informacji o bardzo wysokim stopniu ufności stosowane są najbardziej poważne akcje, natomiast w wiadomościach oznaczonych jako próby wyłudzenia informacji o niskim stopniu pewności stosowane są mniej poważne akcje.
- **2 . Agresywne**: Wiadomości zidentyfikowane jako próby wyłudzenia informacji z dużą pewnością są traktowane tak, jakby zostały zidentyfikowane z bardzo dużą pewnością siebie.
- **3 — Bardziej** agresywne: Wiadomości zidentyfikowane jako próby wyłudzenia informacji z średnią lub wysokim stopniem ufności są traktowane tak, jakby zostały zidentyfikowane z bardzo wysokim stopniem ufności.
- **4 —** Najbardziej agresywne: Wiadomości zidentyfikowane jako próby wyłudzenia informacji z niskim, średnim lub wysokim stopniem ufności są traktowane tak, jakby zostały zidentyfikowane z bardzo dużą pewnością.

W przypadku zwiększenia tego ustawienia prawdopodobieństwo wyników fałszywie dodatnich (oznaczanych jako złe) wzrasta. Aby uzyskać informacje na temat zalecanych ustawień, zobacz zasady [ochrony przed wyłudzaniem informacji Ochrona usługi Office 365 w usłudze Microsoft Defender sieci.](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)
