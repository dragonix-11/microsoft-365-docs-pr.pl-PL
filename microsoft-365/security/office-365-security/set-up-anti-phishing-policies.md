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
description: Administratorzy mogą dowiedzieć się więcej o zasadach ochrony przed wyłudzaniem informacji dostępnych w Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Microsoft Defender.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1a1265e70c0d22182e8ee4db865eeb53ac8168b7
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115900"
---
# <a name="anti-phishing-policies-in-microsoft-365"></a>Zasady ochrony przed wyłudzaniem informacji w Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Zasady konfigurowania ustawień ochrony przed wyłudzaniem informacji są dostępne w organizacjach Microsoft 365 z Exchange Online skrzynkami pocztowymi, autonomicznymi organizacjami Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych oraz Ochrona usługi Office 365 w usłudze Microsoft Defender organizacji.

Przykłady organizacji Ochrona usługi Office 365 w usłudze Microsoft Defender to:

- Microsoft 365 Enterprise E5, Microsoft 365 Education A5 itp.
- [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise/home)
- [Microsoft 365 Business](https://www.microsoft.com/microsoft-365/business)
- [Ochrona usługi Office 365 w usłudze Microsoft Defender jako dodatek](https://products.office.com/exchange/advance-threat-protection)

Ogólne różnice między zasadami ochrony przed wyłudzaniem informacji w ramach EOP i zasadami ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender opisano w poniższej tabeli:

|Funkcja|Zasady ochrony przed wyłudzaniem informacji w ramach EOP|Zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender|
|---|:---:|:---:|
|Automatycznie utworzone zasady domyślne|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Tworzenie zasad niestandardowych|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Typowe ustawienia zasad<sup>\*</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Ustawienia fałszowania|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru.](../../media/checkmark.png)|
|Pierwszy kontakt porada dotycząca bezpieczeństwa|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|
|Ustawienia personifikacji||![Znacznik wyboru](../../media/checkmark.png)|
|Zaawansowane progi wyłudzania informacji||![Znacznik wyboru](../../media/checkmark.png)|

<sup>\*</sup> W zasadach domyślnych nazwa zasad i opis są tylko do odczytu (opis jest pusty) i nie można określić, do kogo mają zastosowanie zasady (zasady domyślne dotyczą wszystkich adresatów).

Aby skonfigurować zasady ochrony przed wyłudzaniem informacji, zobacz następujące artykuły:

- [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w usłudze EOP](configure-anti-phishing-policies-eop.md)
- [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md)

W pozostałej części tego artykułu opisano ustawienia, które są dostępne w zasadach ochrony przed wyłudzaniem informacji w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Defender.

## <a name="common-policy-settings"></a>Typowe ustawienia zasad

Następujące ustawienia zasad są dostępne w zasadach ochrony przed wyłudzaniem informacji na platformie EOP i Ochrona usługi Office 365 w usłudze Defender:

- **Nazwa**: nie można zmienić nazwy domyślnych zasad ochrony przed wyłudzaniem informacji. Po utworzeniu niestandardowych zasad ochrony przed wyłudzaniem informacji nie można zmienić nazwy zasad w portalu Microsoft 365 Defender.

- **Opis** Nie można dodać opisu do domyślnych zasad ochrony przed wyłudzaniem informacji, ale możesz dodać i zmienić opis utworzonych zasad niestandardowych.

- **Użytkownicy, grupy i domeny**: identyfikuje wewnętrznych adresatów, których dotyczą zasady ochrony przed wyłudzaniem informacji. Ta wartość jest wymagana w zasadach niestandardowych i nie jest dostępna w zasadach domyślnych (zasady domyślne dotyczą wszystkich adresatów).

  Warunek lub wyjątek można użyć tylko raz, ale można określić wiele wartości dla warunku lub wyjątku. Wiele wartości tego samego warunku lub wyjątku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki lub wyjątki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

  - **Użytkownicy**: co najmniej jedna skrzynka pocztowa, użytkownicy poczty lub kontakty pocztowe w organizacji.
  - **Grupy**: co najmniej jedna grupa w organizacji.
  - **Domeny**: co najmniej jedna ze skonfigurowanych [zaakceptowanych domen](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w Microsoft 365.

  - **Wyklucz tych użytkowników, grupy i domeny**: wyjątki dla zasad. Ustawienia i zachowanie są dokładnie takie same jak w następujących warunkach:
    - **Użytkownicy**
    - **Grupy**
    - **Domeny**

  > [!NOTE]
  > Co najmniej jeden wybór w **ustawieniach Użytkownicy, grupy i domeny** jest wymagany w niestandardowych zasadach ochrony przed wyłudzaniem informacji, aby zidentyfikować **adresatów** wiadomości <u>, których dotyczą zasady</u>. Zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender mają również [ustawienia personifikacji](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365), w których można określić poszczególne adresy e-mail nadawcy lub domeny nadawcy<u>, które otrzymają ochronę przed personifikacją</u> zgodnie z opisem w dalszej części tego artykułu.
  >
  > Wiele różnych warunków lub wyjątków nie są addytywne; są inkluzywne. Zasady są stosowane _tylko_ do tych adresatów, którzy pasują do _wszystkich_ filtrów określonych adresatów. Na przykład należy skonfigurować warunek filtru adresata w zasadach z następującymi wartościami:
  >
  > - Adresatem jest: romain@contoso.com
  > - Odbiorca jest członkiem: Kierownictwo
  >
  > Zasady są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, zasady nie są do niego stosowane.
  >
  > Podobnie, jeśli używasz tego samego filtru adresata co wyjątek od zasad, zasady nie są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, polityka nadal ma do niego zastosowanie.

## <a name="spoof-settings"></a>Ustawienia fałszowania

Fałszowanie polega na tym, że adres Od w wiadomości e-mail (adres nadawcy wyświetlany w klientach poczty e-mail) nie jest zgodny z domeną źródła wiadomości e-mail. Aby uzyskać więcej informacji na temat fałszowania, zobacz [Ochrona przed fałszowaniem w Microsoft 365](anti-spoofing-protection.md).

Następujące ustawienia fałszowania są dostępne w zasadach ochrony przed wyłudzaniem informacji na platformie EOP i Ochrona usługi Office 365 w usłudze Defender:

- **Włączanie analizy fałszowania**: włącza lub wyłącza analizę fałszowania. Zalecamy pozostawienie jej włączonej.

  Po włączeniu analizy fałszowania szczegółowe **informacje o fałszowaniu analizy** pokazują sfałszowanych nadawców, którzy zostali automatycznie wykryci i dozwoloni lub zablokowani przez fałszowanie inteligencji. Możesz ręcznie zastąpić werdykt analizy fałszowania, aby umożliwić lub zablokować wykrytych sfałszowanych nadawców z poziomu szczegółowych informacji. Jednak gdy to zrobisz, sfałszowany nadawca znika ze szczegółowych informacji o fałszowaniu analizy i jest teraz widoczny tylko na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżaw. Możesz również ręcznie utworzyć wpisy zezwalania lub blokowania dla sfałszowanych nadawców na liście dozwolonych/zablokowanych dzierżaw. Aby uzyskać więcej informacji, zapoznaj się z następującymi artykułami:

  - [Fałszowanie szczegółowych informacji wywiadowczych w ramach EOP](learn-about-spoof-intelligence.md)
  - [Zarządzanie listą dozwolonych/zablokowanych dzierżaw w funkcji EOP](tenant-allow-block-list.md)

  > [!NOTE]
  >
  > - Ochrona przed fałszowaniem jest domyślnie włączona w domyślnych zasadach ochrony przed wyłudzaniem informacji i we wszystkich nowych niestandardowych zasadach ochrony przed wyłudzaniem informacji, które tworzysz.
  > - Nie musisz wyłączać ochrony przed fałszowaniem, jeśli rekord MX nie wskazuje na Microsoft 365; zamiast tego włączysz rozszerzone filtrowanie dla łączników. Aby uzyskać instrukcje, zobacz [Rozszerzone filtrowanie łączników w Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
  > - Wyłączenie ochrony przed fałszowaniem wyłącza tylko _niejawną_ ochronę przed fałszowaniem z testów [uwierzytelniania złożonego](email-validation-and-authentication.md#composite-authentication) . Jeśli nadawca nie _powiedzie się jawnie_ [DMARC](use-dmarc-to-validate-email.md) sprawdza, czy zasady są ustawione na kwarantannę lub odrzucenie, komunikat jest nadal poddawany kwarantannie lub odrzucany.

- **Nieuwierzytelnione wskaźniki nadawcy**: dostępne w sekcji **Wskazówki dotyczące bezpieczeństwa & wskaźniki** tylko wtedy, gdy jest włączona inteligencja fałszowania. Zobacz szczegóły w następnej sekcji.
- **Akcje**: W przypadku komunikatów od zablokowanych sfałszowanych nadawców (automatycznie zablokowanych przez fałszowanie analizy lub ręcznie zablokowanych na liście Zezwalaj/blokuj dzierżawę) można również określić akcję do wykonania w przypadku komunikatów:
  - **Przenieś wiadomości do folderów wiadomości-śmieci adresatów**: jest to wartość domyślna. Wiadomość jest dostarczana do skrzynki pocztowej i przenoszona do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych w Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Kwarantanna komunikatu**: wysyła komunikat do kwarantanny zamiast zamierzonych adresatów. Aby uzyskać informacje o kwarantannie, zobacz następujące artykuły:
    - [Kwarantanna w Microsoft 365](quarantine-email-messages.md)
    - [Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Znajdowanie i zwalnianie komunikatów poddanych kwarantannie jako użytkownik w Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Jeśli **wybierzesz pozycję Kwarantanna komunikatu**, możesz również wybrać zasady kwarantanny, które mają zastosowanie do komunikatów, które zostały poddane kwarantannie przez ochronę przed fałszowaniem danych wywiadowczych. Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

### <a name="unauthenticated-sender-indicators"></a>Nieuwierzytelnione wskaźniki nadawcy

Nieuwierzytelnione wskaźniki nadawcy są częścią [ustawień fałszowania](#spoof-settings), które są dostępne w sekcji **Wskazówki dotyczące bezpieczeństwa & wskaźników** w zasadach ochrony przed wyłudzaniem informacji zarówno na platformie EOP, jak i w Ochrona usługi Office 365 w usłudze Defender. Następujące ustawienia są dostępne tylko po włączeniu analizy fałszowania:

- **Pokaż (?) dla nieuwierzytelnionych nadawców pod kątem fałszowania**: dodaje znak zapytania do zdjęcia nadawcy w polu Od, jeśli komunikat nie przechodzi testów SPF lub DKIM **, a** komunikat nie przekazuje [uwierzytelniania DMARC lub uwierzytelniania złożonego](email-validation-and-authentication.md#composite-authentication). Gdy to ustawienie jest wyłączone, znak zapytania nie jest dodawany do zdjęcia nadawcy.

- **Pokaż tag "via"**: dodaje tag via (chris@contoso.com <u>za pośrednictwem</u> fabrikam.com) w polu Od, jeśli domena w polu Adres od (nadawca wiadomości wyświetlany w klientach poczty e-mail) różni się od domeny w sygnaturze DKIM lub **adresie MAIL FROM** . Aby uzyskać więcej informacji na temat tych adresów, zobacz [Omówienie standardów wiadomości e-mail](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

Aby zapobiec dodawaniu znaku zapytania lub tagu za pośrednictwem tagu do wiadomości od określonych nadawców, dostępne są następujące opcje:

- Zezwalaj na sfałszowanego nadawcę w szczegółowych [informacjach analizy fałszowania](learn-about-spoof-intelligence.md) lub ręcznie na [liście zezwalania/blokowania dzierżawy](tenant-allow-block-list.md). Zezwolenie na sfałszowanego nadawcę uniemożliwi wyświetlanie tagu via w komunikatach od nadawcy, nawet jeśli ustawienie **tagu Pokaż "za pośrednictwem"** jest włączone w zasadach.
- [Skonfiguruj uwierzytelnianie poczty e-mail](email-validation-and-authentication.md#configure-email-authentication-for-domains-you-own) dla domeny nadawcy.
  - Dla znaku zapytania na zdjęciu nadawcy najważniejszy jest SPF lub DKIM.
  - W przypadku tagu via potwierdź, że domena w podpisie DKIM lub adres **MAIL FROM** jest zgodna (lub jest poddomeną) domeny w adresie Od.

Aby uzyskać więcej informacji, zobacz [Identyfikowanie podejrzanych wiadomości w witrynie Outlook.com i Outlook w sieci Web](https://support.microsoft.com/office/3d44102b-6ce3-4f7c-a359-b623bec82206)

## <a name="first-contact-safety-tip"></a>Pierwszy kontakt porada dotycząca bezpieczeństwa

Ustawienia **porada dotycząca bezpieczeństwa Pokaż pierwszy kontakt** są dostępne w organizacjach EOP i Ochrona usługi Office 365 w usłudze Defender i nie są zależne od ustawień ochrony przed fałszowaniem lub personifikacją. Porada dotycząca bezpieczeństwa jest wyświetlany adresatom w następujących scenariuszach:

- Przy pierwszym pobraniu wiadomości od nadawcy
- Często nie pobierają wiadomości od nadawcy.

:::image type="content" source="../../media/safety-tip-first-contact-one-recipient.png" alt-text="Pierwszy kontakt porada dotycząca bezpieczeństwa wiadomości z jednym adresatem" lightbox="../../media/safety-tip-first-contact-one-recipient.png":::

:::image type="content" source="../../media/safety-tip-first-contact-multiple-recipients.png" alt-text="Pierwszy kontakt porada dotycząca bezpieczeństwa wiadomości z wieloma adresatami" lightbox="../../media/safety-tip-first-contact-multiple-recipients.png":::

Ta funkcja dodaje dodatkową warstwę ochrony przed potencjalnymi atakami personifikacji, dlatego zalecamy jej włączenie.

Pierwszy kontakt porada dotycząca bezpieczeństwa zastępuje również konieczność tworzenia reguł przepływu poczty (znanych również jako reguły transportu), które dodają nagłówek o nazwie **X-MS-Exchange-EnableFirstContactSafetyTip** **wartością Włącz** dla komunikatów (chociaż ta funkcja jest nadal dostępna).

> [!NOTE]
> Jeśli komunikat ma wielu adresatów, czy porada jest wyświetlana i dla kogo jest oparta na modelu większości. Jeśli większość adresatów nigdy nie odbiera lub nie odbiera wiadomości od nadawcy, adresaci, których dotyczy problem, otrzymają poradę **Niektóre osoby, które otrzymały tę wiadomość...** Jeśli obawiasz się, że to zachowanie uwidacznia nawyki komunikacyjne jednego adresata, nie należy włączać pierwszego kontaktu porada dotycząca bezpieczeństwa i nadal używać reguł przepływu poczty.

## <a name="exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia wyłączne w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

W tej sekcji opisano ustawienia zasad, które są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender.

> [!NOTE]
> Domyślne zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender zapewniają [ochronę przed fałszowaniem](set-up-anti-phishing-policies.md#spoof-settings) i analizę skrzynek pocztowych dla wszystkich adresatów. Jednak inne dostępne funkcje [ochrony przed personifikacją](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i [ustawienia zaawansowane](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) nie są skonfigurowane ani włączone w zasadach domyślnych. Aby włączyć wszystkie funkcje ochrony, zmodyfikuj domyślne zasady ochrony przed wyłudzaniem informacji lub utwórz dodatkowe zasady ochrony przed wyłudzaniem informacji.

### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Personifikacja to miejsce, w którym domena poczty e-mail nadawcy lub nadawcy w wiadomości wygląda podobnie do rzeczywistego nadawcy lub domeny:

- Przykładowa personifikacja contoso.com domeny jest ćóntoso.com.
- Personifikacja użytkownika jest kombinacją nazwy wyświetlanej użytkownika i adresu e-mail. Na przykład Valeria Barrios (vbarrios@contoso.com) może być personifikowana jako Valeria Barrios, ale z zupełnie innym adresem e-mail.

> [!NOTE]
> Ochrona przed personifikacją wyszukuje podobne domeny. Jeśli na przykład domena jest contoso.com, sprawdzamy różne domeny najwyższego poziomu (.com, biz itp.) jako próby personifikacji, ale także domeny, które są nawet nieco podobne. Na przykład contosososo.com lub contoabcdef.com mogą być postrzegane jako próby personifikacji contoso.com.

Domena personifikowana może w przeciwnym razie zostać uznana za uzasadnioną (zarejestrowana domena, skonfigurowane rekordy uwierzytelniania poczty e-mail itp.), z wyjątkiem tego, że jej celem jest oszukanie adresatów.

Następujące ustawienia personifikacji są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender:

- **Włącz ochronę użytkowników**: zapobiega personifikacji określonych wewnętrznych lub zewnętrznych adresów e-mail **jako nadawców wiadomości**. Na przykład otrzymasz wiadomość e-mail od wiceprezesa twojej firmy z prośbą o wysłanie jej wewnętrznych informacji o firmie. Czy to zrobisz? Wiele osób wysyłałoby odpowiedź bez zastanowienia.

  Chronionych użytkowników można używać do dodawania wewnętrznych i zewnętrznych adresów e-mail nadawcy w celu ochrony przed personifikacją. Ta lista **nadawców** , którzy są chronieni przed personifikacją użytkowników, różni się od listy **adresatów** , których dotyczą zasady (wszyscy adresaci zasad domyślnych; określonych adresatów skonfigurowanych w ustawieniu **Użytkownicy, grupy i domeny** w sekcji [Typowe ustawienia zasad](#common-policy-settings) ).

  > [!NOTE]
  >
  > - W poszczególnych zasadach ochrony przed wyłudzaniem informacji można określić maksymalnie 350 chronionych użytkowników (adresy e-mail nadawcy). Nie można określić tego samego chronionego użytkownika w wielu zasadach. Dlatego bez względu na to, ile zasad dotyczy adresata, maksymalna liczba chronionych użytkowników (adresów e-mail nadawcy) dla każdego pojedynczego adresata wynosi 350. Aby uzyskać więcej informacji na temat priorytetu zasad i sposobu zatrzymywania przetwarzania zasad po zastosowaniu pierwszych zasad, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).
  > - Ochrona przed personifikacją użytkownika nie działa, jeśli nadawca i adresat wcześniej komunikowali się za pośrednictwem poczty e-mail. Jeśli nadawca i adresat nigdy nie komunikowali się za pośrednictwem poczty e-mail, wiadomość zostanie zidentyfikowana jako próba personifikacji.

  Domyślnie żadne adresy e-mail nadawcy nie są skonfigurowane do ochrony przed personifikacją w **obszarze Użytkownicy w celu ochrony**. W związku z tym domyślnie żadne adresy e-mail nadawcy nie są objęte ochroną przed personifikacją w zasadach domyślnych lub zasadach niestandardowych.

  Po dodaniu wewnętrznych lub zewnętrznych adresów e-mail do listy **Użytkownicy w celu ochrony** wiadomości od tych **nadawców** podlegają kontroli ochrony przed personifikacją. Wiadomość jest sprawdzana pod kątem personifikacji, **jeśli** wiadomość jest wysyłana do **adresata** , do których mają zastosowanie zasady (wszyscy adresaci domyślnych zasad; **Użytkownicy, grupy i adresaci domen** w zasadach niestandardowych). Jeśli na adres e-mail nadawcy zostanie wykryta personifikacja, do wiadomości zostaną zastosowane akcje ochrony przed personifikacją dla użytkowników (co zrobić z komunikatem, czy wyświetlić wskazówki dotyczące bezpieczeństwa personifikowanych użytkowników itp.).

- **Włącz ochronę domen**: zapobiega personifikacji określonych domen **w domenie nadawcy wiadomości**. Na przykład wszystkie domeny, których jesteś właścicielem ([akceptowane domeny](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)) lub określonych domen niestandardowych (domen, których jesteś właścicielem lub domen partnerskich). Ta lista **domen nadawców** , które są chronione przed personifikacją, różni się od listy **adresatów** , których dotyczą zasady (wszyscy adresaci domyślnych zasad; określonych adresatów skonfigurowanych w ustawieniu **Użytkownicy, grupy i domeny** w sekcji [Typowe ustawienia zasad](#common-policy-settings) ).

  > [!NOTE]
  > W każdej z zasad ochrony przed wyłudzaniem informacji można określić maksymalnie 50 domen niestandardowych.

  Domyślnie żadne domeny nadawcy nie są skonfigurowane do ochrony przed personifikacją w **sekcji Włączanie ochrony domen**. W związku z tym domyślnie żadne domeny nadawcy nie są objęte ochroną przed personifikacją w zasadach domyślnych lub zasadach niestandardowych.

  Po dodaniu domen do listy **Włącz domeny w celu ochrony** komunikaty od **nadawców w tych domenach** podlegają kontroli ochrony przed personifikacją. Wiadomość jest sprawdzana pod kątem personifikacji, **jeśli** wiadomość jest wysyłana do **adresata** , do których mają zastosowanie zasady (wszyscy adresaci domyślnych zasad; **Użytkownicy, grupy i adresaci domen** w zasadach niestandardowych). Jeśli w domenie nadawcy zostanie wykryta personifikacja, do komunikatu zostaną zastosowane akcje ochrony przed personifikacją domen (co zrobić z komunikatem, czy wyświetlić wskazówki dotyczące bezpieczeństwa personifikowanych użytkowników itp.).

- **Akcje**: wybierz akcję do wykonania w przypadku komunikatów przychodzących zawierających próby personifikacji wobec chronionych użytkowników i chronionych domen w zasadach. Możesz określić różne akcje personifikacji chronionych użytkowników a personifikację chronionych domen:
  - **Nie stosuj żadnej akcji**
  - **Przekieruj wiadomość na inne adresy e-mail**: wysyła wiadomość do określonych adresatów zamiast do zamierzonych adresatów.
  - **Przenieś wiadomości do folderów wiadomości-śmieci adresatów**: wiadomość jest dostarczana do skrzynki pocztowej i przenoszona do folderu Wiadomości-śmieci. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych w Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).
  - **Kwarantanna komunikatu**: wysyła komunikat do kwarantanny zamiast zamierzonych adresatów. Aby uzyskać informacje o kwarantannie, zobacz następujące artykuły:
    - [Kwarantanna w Microsoft 365](quarantine-email-messages.md)
    - [Zarządzanie komunikatami i plikami poddanymi kwarantannie jako administrator w Microsoft 365](manage-quarantined-messages-and-files.md)
    - [Znajdowanie i zwalnianie komunikatów poddanych kwarantannie jako użytkownik w Microsoft 365](find-and-release-quarantined-messages-as-a-user.md)

    Jeśli **wybierzesz pozycję Kwarantanna komunikatu**, możesz również wybrać zasady kwarantanny, które mają zastosowanie do komunikatów poddawanych kwarantannie przez personifikację użytkownika lub ochronę przed personifikacją domeny. Zasady kwarantanny definiują, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

  - **Dostarczenie wiadomości i dodanie innych adresów do wiersza Bcc**: dostarczenie wiadomości do zamierzonych adresatów i dyskretne dostarczenie wiadomości do określonych adresatów.
  - **Usuń wiadomość przed jej dostarczeniem**: w trybie dyskretnym usuwa całą wiadomość, w tym wszystkie załączniki.

- **Wskazówki dotyczące bezpieczeństwa personifikacji**: włącz lub wyłącz następujące wskazówki dotyczące bezpieczeństwa personifikacji, które będą wyświetlane komunikaty, które nie sprawdzają personifikacji:
  - **Pokaż poradę dla personifikowanych użytkowników**: adres Od zawiera opcję **Włącz użytkownikom ochronę** użytkownika. Opcja dostępna tylko wtedy, gdy opcja **Włącz ochronę użytkowników** jest włączona i skonfigurowana.
  - **Pokaż poradę dotyczącą domen personifikowanych**: adres Od zawiera domenę **Włączanie ochrony** domeny. Dostępne tylko wtedy, gdy włączono i skonfigurowano opcję **Włącz domeny do ochrony** .
  - **Pokaż poradę dotyczącą nietypowych znaków**: adres From zawiera nietypowe zestawy znaków (na przykład symbole matematyczne i tekst lub kombinację wielkich i małych liter) w obszarze **Włącz użytkownikom ochronę** **nadawcy lub domenom Włączanie ochrony domeny nadawcy** .  Dostępne tylko wtedy, gdy włączono i skonfigurowano opcję **Włącz dla użytkowników ochronę** _lub_ **Włącz ochronę domen** .

- **Włączanie analizy skrzynek pocztowych**: włącza lub wyłącza sztuczną inteligencję (AI), która określa wzorce poczty e-mail użytkowników z ich częstymi kontaktami. To ustawienie pomaga sztucznej inteligencji odróżnić komunikaty od legalnych i personifikowanych nadawców.

  Na przykład Gabriela Laureano (glaureano@contoso.com) jest dyrektorem generalnym twojej firmy, dlatego należy dodać ją jako chronionego nadawcę w obszarze **Włączanie użytkownikom ochrony** ustawień zasad. Ale niektórzy adresaci, których dotyczą zasady, regularnie komunikują się z dostawcą o nazwie Gabriela Laureano (glaureano@fabrikam.com). Ponieważ adresaci mają historię komunikacji z glaureano@fabrikam.com, analiza skrzynek pocztowych nie będzie identyfikować wiadomości z glaureano@fabrikam.com jako próby personifikacji glaureano@contoso.com dla tych adresatów.

  Aby używać częstych kontaktów poznanych przez analizę skrzynki pocztowej (i ich brak) w celu ochrony użytkowników przed atakami personifikacji, możesz włączyć opcję **Włącz ochronę przed personifikacją inteligencji** po **włączeniu funkcji Włączanie analizy skrzynek pocztowych**.

- **Włącz ochronę przed personifikacją analizy**: włącz to ustawienie, aby określić akcję do wykonania w przypadku wykrywania personifikacji z wyników analizy skrzynki pocztowej:
  - **Nie stosuj żadnych akcji**: zwróć uwagę, że ta wartość ma taki sam wynik jak włączenie **analizy skrzynki pocztowej** , ale **wyłączenie opcji Włącz ochronę przed personifikacją inteligencji**.
  - **Przekierowywanie wiadomości na inne adresy e-mail**
  - **Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**
  - **Kwarantanna komunikatu**: Jeśli wybierzesz tę akcję, możesz również wybrać zasady kwarantanny, które mają zastosowanie do wiadomości poddawanych kwarantannie przez ochronę przed inteligencją skrzynki pocztowej. Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).
  - **Dostarczanie komunikatu i dodawanie innych adresów do wiersza Bcc**
  - **Usuń wiadomość przed jej dostarczeniem**

- **Dodawanie zaufanych nadawców i domen**: wyjątki od ustawień ochrony przed personifikacją. Komunikaty z określonych domen nadawców i nadawców nigdy nie są klasyfikowane jako ataki oparte na personifikacji przez zasady. Innymi słowy, akcja dla chronionych nadawców, domen chronionych ani ochrony inteligencji skrzynki pocztowej nie jest stosowana do tych zaufanych nadawców ani domen nadawców. Maksymalny limit dla tych list to 1024 wpisy.

### <a name="advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Zaawansowane progi wyłudzania informacji w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender

Następujące zaawansowane progi wyłudzania informacji są dostępne tylko w zasadach ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender. Te progi kontrolują czułość stosowania modeli uczenia maszynowego do komunikatów w celu określenia werdyktu wyłudzania informacji:

- **1 — Standardowa**: jest to wartość domyślna. Ważność akcji wykonywanej w wiadomości zależy od stopnia pewności, że wiadomość jest wyłudzająca informacje (niska, średnia, wysoka lub bardzo wysoka pewność). Na przykład komunikaty, które są identyfikowane jako wyłudzanie informacji z bardzo wysokim poziomem zaufania, mają najsurowsze działania, podczas gdy komunikaty, które są identyfikowane jako wyłudzanie informacji z niskim stopniem ufności, mają mniej poważne działania.
- **2 — Agresywne**: Komunikaty, które są identyfikowane jako wyłudzanie informacji z wysokim stopniem ufności, są traktowane tak, jakby były identyfikowane z bardzo wysokim poziomem zaufania.
- **3 — Bardziej agresywne**: Komunikaty, które są identyfikowane jako wyłudzanie informacji ze średnim lub wysokim poziomem ufności, są traktowane tak, jakby były identyfikowane z bardzo wysokim poziomem zaufania.
- **4 — Najbardziej agresywne**: Komunikaty, które są identyfikowane jako wyłudzanie informacji z niskim, średnim lub wysokim stopniem ufności, są traktowane tak, jakby zostały zidentyfikowane z bardzo wysokim poziomem zaufania.

Prawdopodobieństwo fałszywie dodatnich (dobrych komunikatów oznaczonych jako złe) zwiększa się w miarę zwiększania tego ustawienia. Aby uzyskać informacje o zalecanych ustawieniach, zobacz [zasady ochrony przed wyłudzaniem informacji w ustawieniach Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).
