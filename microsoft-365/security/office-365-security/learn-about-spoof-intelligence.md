---
title: Analiza fałszerów
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 978c3173-3578-4286-aaf4-8a10951978bf
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o analizie fałszer Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5bf0ed143f5bfb78ff1d6af4005a4b5ec64fd90e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021308"
---
# <a name="spoof-intelligence-insight-in-eop"></a>Spoof intelligence insight in EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Funkcje opisane w tym artykule są w wersji Preview, mogą ulec zmianie i nie są dostępne we wszystkich organizacjach. Jeśli w Twojej organizacji nie ma funkcji opisanych w tym artykule, zobacz starsze środowisko zarządzania fałszerami w artykule Zarządzanie fałszywymi nadawcami przy użyciu zasad ochrony przed fałszerami i wglądu w analizę fałszowania w [uciekinie usługi EOP](walkthrough-spoof-intelligence-insight.md).

W Microsoft 365 z skrzynkami pocztowymi w Exchange Online lub autonomicznej organizacji usługi Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych przychodzące wiadomości e-mail są automatycznie chronione przed fałszowaniem. Firma EOP **korzysta z ochrony** przed wyłudzaniem informacji fałszerczych w organizacji. Aby uzyskać więcej informacji, zobacz [Ochrona przed fałszerko-fałszergami w uciekaniu poczty eOP](anti-spoofing-protection.md).

Gdy nadawca fałszuje adres e-mail, wydaje się, że jest użytkownikiem w jednej z domen organizacji lub użytkownikiem w domenie zewnętrznej, który wysyła wiadomości e-mail do Twojej organizacji. Atakujący, którzy podszywają się pod nadawców w celu wysyłania spamu lub wyłudzania informacji, muszą być zablokowani. Jednak istnieją sytuacje, w których fałszywi nadawcy podszywają się pod innych nadawców. Przykład:

- Wiarygodne scenariusze spoofingu domen wewnętrznych:
  - Nadawcy z innych firm używają Twojej domeny do wysyłania poczty masowej do własnych pracowników na ankiety w firmie.
  - Firma zewnętrzna generuje i wysyła w Twoim imieniu reklamy lub aktualizacje produktów.
  - Asystent musi regularnie wysyłać wiadomości e-mail do innej osoby w Twojej organizacji.
  - Aplikacja wewnętrzna wysyła powiadomienia e-mail.

- Uzasadnione scenariusze spoofingu domen zewnętrznych:
  - Nadawca znajduje się na liście adresowej (nazywanej również listą dyskusyjną), a lista adresowa przekazuje wiadomości e-mail od pierwotnego nadawcy do wszystkich uczestników na liście adresowej.
  - Firma zewnętrzna wysyła wiadomość e-mail w imieniu innej firmy (na przykład raport zautomatyzowany lub firma software-as-a-service).

Za pomocą szczegółowych informacji  o fałszerce w portalu usługi Microsoft 365 Defender można szybko zidentyfikować fałszywych nadawców, którzy w uzasadniony sposób wysyłają do Ciebie nieuwierzytane wiadomości e-mail (wiadomości z domen, które nie przechodzą testów SPF, DKIM lub DMARC) i ręcznie zezwalają tym nadawcom.

Zezwalając znanym nadawcom na wysyłanie fałszywych wiadomości ze znanych lokalizacji, możesz zmniejszyć liczbę wyników fałszywie dodatnich (dobra wiadomość e-mail oznaczona jako zła). Monitorując dozwolonych sfałszowanych nadawców, zapewniasz dodatkową warstwę zabezpieczeń, aby zapobiec dostarczaniu niebezpiecznych wiadomości do organizacji.

Podobnie możesz przeglądać fałszywych nadawców, którzy zostali dozwoloni przez fałszywą inteligencję, i ręcznie blokować tych nadawców na podstawie informacji o fałszerce.

W dalszej części tego artykułu wyjaśniono, jak korzystać z analiz fałszerskich w portalu usługi Microsoft 365 Defender i w programie Power Microsoft 365 Shell (Exchange Online PowerShell dla organizacji z skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online skrzynki pocztowe).

> [!NOTE]
>
> - W analizie fałszowanych informacji są wyświetlani tylko fałszywi nadawcy, którzy zostali wykryci w przypadku fałszywych informacji. Gdy zastąpisz zezwalanie lub blokowanie werdyktu w szczegółowych informacjach, fałszywy nadawca stanie się ręcznym wpisem zezwalania lub  blokowania, który jest wyświetlany tylko na karcie Fałsz na liście zezwalania/blokowania dzierżawy. Możesz również ręcznie utworzyć zezwalanie na fałszywych nadawców lub blokować ich wpisy, zanim zostaną one wykryte przez fałszywą inteligencję. Aby uzyskać więcej informacji, zobacz [Zarządzanie listą zezwalania/blokowania dzierżawy w u usługi EOP](tenant-allow-block-list.md).
>
> - Szczegółowe informacje dotyczące fałszowania  i karta Fałsz na liście Zezwalaj/Zablokuj dzierżawy zastępują funkcje zasad ochrony przed fałszerami, które były dostępne na stronie zasad ochrony przed spamem w Centrum zgodności usługi & zabezpieczeń.
>
>- Szczegółowe informacje o analizie fałszerzy to dane 7-dniowe. Polecenie **cmdlet Get-SpoofIntgenceInsight** wyświetla dane warte 30 dni.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do karty **Fałszowanie** na stronie **Lista zezwalania/blokowania dzierżawy** , użyj klawisza <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>. Aby przejść bezpośrednio do strony Szczegółowe **informacje o fałszerce**, użyj .<https://security.microsoft.com/spoofintelligence>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby zmodyfikować zasady ochrony przed fałszerami albo włączyć lub wyłączyć analizę fałszowania,  musisz być członkiem grup ról Zarządzanie organizacją lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do zasad ochrony przed fałszerami, musisz być członkiem  grup ról Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  > - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Zasady ochrony przed wyłudzaniem informacji są włączane i wyłączane w usługach EOP i Microsoft Defender for Office 365. Funkcja analizy fałszowania jest domyślnie włączona. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed](configure-anti-phishing-policies-eop.md) wyłudzaniem informacji w uwitrynie EOP lub Konfigurowanie zasad [ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla systemu Office 365](configure-mdo-anti-phishing-policies.md).

- Aby uzyskać informacje o naszych zalecanych ustawieniach ochrony przed fałszerami, zobacz Ustawienia zasad ochrony przed wyłudzaniem informacji [eOP](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings).

## <a name="open-the-spoof-intelligence-insight-in-the-microsoft-365-defender-portal"></a>Otwieranie szczegółowych informacji o analizie fałszer Microsoft 365 Defender portalu

1. W portalu Microsoft 365 Defender <https://security.microsoft.com> pod adresem przejdź do sekcji **&** \> e-mail i zasad & **zasad** \> \> zagrożeń dotyczących dzierżawy zezwalania na dostęp **do** list zablokowanych i zezwalania **na** nie. Aby przejść bezpośrednio do karty **Fałszowanie** na stronie **Lista zezwalania/blokowania dzierżawy** , użyj klawisza <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>.

2. Na stronie **Listy zezwalania/blokowania dzierżawy** informacje o analizie dotyczącej fałszowania wyglądają następująco:

   ![Szczegółowe informacje dotyczące ochrony przed fałszerami na stronie zasad ochrony przed wyłudzaniem informacji.](../../media/m365-sc-spoof-intelligence-insight.png)

   Szczegółowe informacje są dostępne w dwóch trybach:

   - **Tryb analizy**: Jeśli jest włączona analiza fałszowania, możesz sprawdzić, ile wiadomości zostało wykrytych przez sfałszowaną analizę w ciągu ostatnich siedmiu dni.
   - **Co zrobić, jeśli** tryb: Jeśli jest wyłączona analiza fałszerska, pozwala uzyskać informacje  o tym, ile wiadomości zostałoby wykrytych przez fałszerkę w ciągu ostatnich siedmiu dni.

Aby wyświetlić informacje o wykryciu fałszowania informacji, kliknij pozycję Wyświetl aktywność podszywania się **w** analizie fałszowania.

### <a name="view-information-about-spoofed-messages"></a>Wyświetlanie informacji o sfałszowanych wiadomościach

> [!NOTE]
> Pamiętaj, że na tej stronie są wyświetlani tylko fałszywi nadawcy, którzy zostali wykryci przez fałszywą inteligencję. Gdy zastąpisz zezwalanie lub blokowanie werdyktu w szczegółowych informacjach, fałszywy nadawca stanie się ręcznym wpisem zezwalania lub  blokowania, który jest wyświetlany tylko na karcie Fałsz na liście zezwalania/blokowania dzierżawy.

Na stronie **Spoof intelligence insight** (Analiza fałszowania) wyświetlanej po kliknięciu przycisku **Wyświetl aktywność spoofingu** w szczegółowych informacjach dotyczących fałszowania ta strona zawiera następujące informacje:

- **Sfałszowany użytkownik**: **domena** fałszywego użytkownika wyświetlana w polu **Od w** klientach poczty e-mail. Adres Od jest również nazywany adresem `5322.From` .
- **Infrastruktura wysyłania**: ta infrastruktura _jest także znana jako infrastruktura_. Infrastruktura wysyłania będzie mieć jedną z następujących wartości:
  - Domena znaleziona w odwrotnym odnośniku DNS (rekord PTR) adresu IP źródłowego serwera poczty e-mail.
  - Jeśli źródłowy adres IP nie ma rekordu PTR, \<source IP\>wówczas infrastruktura wysyłania jest identyfikowana jako /24 (na przykład 192.168.100.100/24).
- **Liczba wiadomości**: Liczba wiadomości z połączenia sfałszowanej domeny i infrastruktury wysyłania do Twojej  organizacji w ciągu ostatnich 7 dni.
- **Ostatnio widziane**: Ostatnia data, kiedy wiadomość została odebrana z infrastruktury wysyłania zawierającej fałszywą domenę.
- **Fałsz typ**: Jedna z następujących wartości:
  - **Wewnętrzny**: sfałszowany nadawca należy do Twojej organizacji ( [zaakceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
  - **Zewnętrzne**: sfałszowany nadawca znajduje się w domenie zewnętrznej.
- **Akcja**: Ta wartość jest **dozwolona lub** **zablokowana**:
  - **Dozwolone**: Domena nie sprawdza jawnego uwierzytelniania wiadomości e-mail [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md). Jednak ta domena przeszła niejawne testy uwierzytelniania wiadomości e-mail ([uwierzytelnianie złożone](email-validation-and-authentication.md#composite-authentication)). W wyniku tego nie zostały podjęte żadne działania zapobiegające podszywce się nad wiadomością.
  - **Zablokowane**: Wiadomości z połączenia domeny sfałszowanej i infrastruktury wysyłania są  oznaczane jako złe przez spoof intelligence. Akcja przejmowana przez sfałszowane wiadomości jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji (wartość domyślna to Przenoszenie wiadomości do folderu **Wiadomości-śmieci**). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

Możesz kliknąć wybrane nagłówki kolumn, aby posortować wyniki.

Aby przefiltrować wyniki, dostępne są następujące opcje:

- Kliknij **przycisk Filtruj** . W **wyświetlonym** wysuwanych czacie Filtr możesz filtrować wyniki według:
  - **Typ fałsz**
  - **Akcja**
- Za pomocą **pola wyszukiwania** wprowadź rozdzieloną przecinkami listę sfałszowanych wartości domeny lub wysyłając wartości infrastruktury w celu filtrowania wyników.

### <a name="view-details-about-spoofed-messages"></a>Wyświetlanie szczegółów sfałszowanych wiadomości

Po wybraniu pozycji z listy zostanie wyświetlone wysuwne okno wysuwu szczegółów zawierające następujące informacje i funkcje:

- **Zezwalaj** na fałszowanie lub Blokowanie podszywania **się: Wybierz** jedną z tych wartości, aby zastąpić oryginalny werdykt analizy fałszowania i przenieść wpis z informacji o fałszerce do listy zezwalania na dostęp do dzierżawy/blokowania jej jako wpisu zezwalania na fałszowanie lub blokowania go.
- Dlaczego go przygotowaliśmy.
- Co należy zrobić.
- Podsumowanie domeny, które zawiera większość tych samych informacji ze strony głównej analizy fałszowania.
- WhoIs data about the sender.
- Link do otwierania [Eksploratora zagrożeń w](threat-explorer.md) celu wyświetlenia dodatkowych szczegółów dotyczących nadawcy  \> w obszarze **Wyświetlanie informacji o wiadomościach phish** w programie Microsoft Defender dla Office 365.
- Podobne wiadomości, które zobaczyliśmy w Twojej dzierżawie od tego samego nadawcy.

### <a name="about-allowed-spoofed-senders"></a>Informacje o dozwolonych sfałszowanych nadawcach

Dozwolony sfałszowany nadawca w szczegółowych informacjach na temat fałszowania lub zablokowany sfałszowany nadawca, który został ręcznie zmieniony  na Zezwalaj na fałsz, zezwala tylko na wiadomości z kombinacji sfałszowanej  domeny i infrastruktury wysyłania. Nie zezwala na pocztę e-mail z domeny sfałszowanej z żadnego źródła, ani nie zezwala na pocztę e-mail z infrastruktury wysyłania dla żadnej domeny.

Na przykład następujący fałszywy nadawca może fałszować:

- **Domena**: gmail.com
- **Infrastruktura**: tms.mx.com

Tylko wiadomości e-mail z tej pary domena/infrastruktura wysyłania mogą być fałszowane. Inni nadawcy próbujący fałszować gmail.com nie są automatycznie dozwolone. Wiadomości od nadawców z innych domen pochodzących z tms.mx.com są nadal sprawdzane przez analizę fałszowania i mogą być blokowane.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>Korzystanie z informacji o analizie fałszerów w programie Exchange Online PowerShell lub autonomicznym programie PowerShell usługi EOP

W programie PowerShell polecenie cmdlet **Get-SpoofIntgenceInsight** umożliwia wyświetlanie dozwolonych i zablokowanych sfałszowanych nadawców wykrytych przez fałszywą inteligencję. Aby ręcznie zezwolić lub zablokować fałszywych nadawców, musisz użyć polecenia cmdlet **New-TenantAllowBlockListSpoofItems** . Aby uzyskać więcej informacji, zobacz Zarządzanie fałszywymi wpisami nadawców na liście zezwalania/blokowania dzierżawy za pomocą [programu PowerShell](tenant-allow-block-list.md).

Aby wyświetlić informacje w analizie fałszerów, uruchom następujące polecenie:

```powershell
Get-SpoofIntelligenceInsight
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SpoofIntelligenceInsight](/powershell/module/exchange/get-spoofintelligenceinsight).

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Inne sposoby zarządzania fałszowaniem i wyłudzaniem informacji

Schowaj się przed fałszowaniem i wyłudzaniem informacji. Oto powiązane sposoby sprawdzania nadawców, którzy podszywają się pod Twoją domenę, i pomagają zapobiec uszkodniom twojej organizacji:

- Sprawdź raport **fałszowania poczty**. Tego raportu można często używać do wyświetlania fałszywych nadawców i zarządzania nimi. Aby uzyskać więcej informacji, zobacz [Raport Fałsz wykrywanie](view-email-security-reports.md#spoof-detections-report).

- Przejrzyj konfigurację struktury zasad dotyczących nadawców (SPF). Aby uzyskać krótkie wprowadzenie do SPF i skonfigurować go szybko, zobacz Konfigurowanie spf w programie [Microsoft 365 zapobiegania fałszersprowadzeniu](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Aby uzyskać bardziej szczegółowe informacje na temat sposobu, w jaki program Office 365 korzysta z SPF, lub na potrzeby rozwiązywania problemów bądź wdrożeń niestandardowych, takich jak wdrożenia hybrydowe, zacznij od tego, jak program Office 365 używa struktury zasad dotyczących nadawców [(SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) w celu zapobiegania fałszersce.

- Przejrzyj konfigurację DKIM (DomainKeys Identified Mail). Oprócz funkcji SPF i DMARC należy używać funkcji DKIM w celu zapobiegania wysyłaniu przez atakujących wiadomości wyglądających tak, jakby pochodziły z Twojej domeny. Funkcja DKIM umożliwia dodawanie podpisu cyfrowego do wiadomości e-mail w nagłówku wiadomości. Aby uzyskać informacje, zobacz Używanie funkcji DKIM do sprawdzania poprawności wychodzących wiadomości e-mail wysłanych z domeny [niestandardowej w Office 365](use-dkim-to-validate-outbound-email.md).

- Sprawdź konfigurację DMARC (Domain-based Message Authentication, Reporting, and Conformance). Wdrożenie DMARC za pomocą SPF i DKIM zapewnia dodatkową ochronę przed fałszowaniem i wyłudzaniem informacji e-mail. DMARC ułatwia odbieranie systemów poczty w określaniu, co należy zrobić z wiadomościami wysyłanymi z Twojej domeny, w przypadku których nie są sprawdzane SPF lub DKIM. Aby uzyskać informacje, zobacz [Używanie funkcji DMARC do sprawdzania poprawności wiadomości e-mail Office 365](use-dmarc-to-validate-email.md).
