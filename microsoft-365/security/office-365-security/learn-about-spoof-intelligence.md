---
title: Szczegółowe informacje o analizie spoofingu
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
description: Administratorzy mogą dowiedzieć się więcej na temat analizy fałszowania w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9455ddf17d26e33ed5b2669a27ee93cf5f56b8f9
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016059"
---
# <a name="spoof-intelligence-insight-in-eop"></a>Fałszowanie szczegółowych informacji wywiadowczych w ramach EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych przychodzące wiadomości e-mail są automatycznie chronione przed fałszowaniem. W ramach ogólnej ochrony organizacji przed wyłudzaniem informacji EOP używa **analizy fałszowania** . Aby uzyskać więcej informacji, zobacz [Ochrona przed fałszowaniem w ramach EOP](anti-spoofing-protection.md).

Gdy nadawca podszywa się pod adres e-mail, wydaje się być użytkownikiem w jednej z domen organizacji lub użytkownikiem w domenie zewnętrznej, który wysyła wiadomość e-mail do organizacji. Osoby atakujące, które podszywają się pod nadawców w celu wysyłania spamu lub wiadomości e-mail wyłudzających informacje, muszą zostać zablokowane. Istnieją jednak scenariusze, w których legalni nadawcy podszywają się pod tych nadawców. Przykład:

- Uzasadnione scenariusze fałszowania domen wewnętrznych:
  - Nadawcy innych firm używają Twojej domeny do wysyłania wiadomości e-mail zbiorczych do własnych pracowników na potrzeby ankiet firmowych.
  - Zewnętrzna firma generuje i wysyła w Twoim imieniu reklamy lub aktualizacje produktów.
  - Asystent regularnie musi wysyłać wiadomości e-mail do innej osoby w organizacji.
  - Aplikacja wewnętrzna wysyła powiadomienia e-mail.

- Uzasadnione scenariusze fałszowania domen zewnętrznych:
  - Nadawca znajduje się na liście adresowej (znanej również jako lista dyskusyjna), a lista adresowa przekazuje wiadomość e-mail od oryginalnego nadawcy do wszystkich uczestników na liście adresowej.
  - Firma zewnętrzna wysyła wiadomość e-mail w imieniu innej firmy (na przykład zautomatyzowanego raportu lub firmy zajmującej się oprogramowaniem jako usługą).

W portalu Microsoft 365 Defender  można szybko zidentyfikować sfałszowanych nadawców, którzy legalnie wysyłają Ci nieuwierzytelnioną wiadomość e-mail (wiadomości z domen, które nie przechodzą testów SPF, DKIM lub DMARC), i ręcznie zezwolić na tych nadawców.

Zezwalając znanym nadawcom na wysyłanie fałszywych wiadomości ze znanych lokalizacji, można zmniejszyć liczbę wyników fałszywie dodatnich (dobra wiadomość e-mail oznaczona jako zła). Monitorując dozwolonych sfałszowanych nadawców, zapewniasz dodatkową warstwę zabezpieczeń, aby zapobiec napływowi niebezpiecznych komunikatów do organizacji.

Podobnie możesz przejrzeć sfałszowanych nadawców, którzy byli dozwoloni przez fałszowanie inteligencji, i ręcznie zablokować tych nadawców przed fałszowaniem analizy wywiadowczej.

W pozostałej części tego artykułu wyjaśniono, jak korzystać ze szczegółowych informacji na temat fałszowania analizy w portalu Microsoft 365 Defender i w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomiczny program PowerShell EOP dla organizacji bez Exchange Online skrzynki pocztowe).

> [!NOTE]
>
> - Tylko sfałszowani nadawcy, którzy zostali wykryci przez fałszywą inteligencję, pojawiają się w szczegółowej analizie dotyczącej fałszowania. Po zastąpieniu werdyktu zezwalania lub blokowania w analizie fałszywy nadawca staje się ręcznym wpisem zezwalającym lub blokowym wyświetlanym tylko na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców. Możesz również ręcznie utworzyć wpisy zezwalania lub blokować dla sfałszowanych nadawców, zanim zostaną wykryte przez analizę fałszowania. Aby uzyskać więcej informacji, zobacz [Manage the Tenant Allow/Block List in EOP (Zarządzanie listą dozwolonych/zablokowanych dzierżaw w ramach operacji EOP](tenant-allow-block-list.md)).
>
> - Szczegółowe informacje o fałszowaniu analizy i karta **Fałszowanie** na liście Zezwalanie/blokowanie dzierżawy zastępują funkcje zasad analizy fałszowania, które były dostępne na stronie zasad ochrony przed spamem w Centrum zgodności & zabezpieczeń.
>
>- Szczegółowe informacje o analizie fałszowania pokazują dane warte 7 dni. Polecenie cmdlet **Get-SpoofIntelligenceInsight** pokazuje dane o wartości 30 dni.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do karty **Fałszowanie** na stronie **Lista dozwolonych/zablokowanych dzierżaw** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>. Aby przejść bezpośrednio do strony **szczegółowej analizy fałszowania** , użyj polecenia <https://security.microsoft.com/spoofintelligence>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby zmodyfikować zasady analizy fałszowania lub włączyć lub wyłączyć analizę fałszowania, musisz być członkiem 
    -   **Zarządzanie organizacją**
    -   **Administrator zabezpieczeń** <u>i</u> **konfiguracja tylko do wyświetlania** lub **zarządzanie organizacją tylko do wyświetlania**.
  - Aby uzyskać dostęp tylko do odczytu do zasad analizy fałszowania, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  > - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Włączasz i wyłączasz analizę fałszowania w zasadach ochrony przed wyłudzaniem informacji w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender. Analiza fałszowania jest domyślnie włączona. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w ramach EOP](configure-anti-phishing-policies-eop.md) lub [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

- Aby zapoznać się z naszymi zalecanymi ustawieniami analizy podróbek, zobacz [Ustawienia zasad ochrony przed wyłudzaniem informacji](recommended-settings-for-eop-and-office365-atp.md#eop-anti-phishing-policy-settings) w usłudze EOP.

## <a name="open-the-spoof-intelligence-insight-in-the-microsoft-365-defender-portal"></a>Otwieranie szczegółowych informacji na temat fałszowania analizy w portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Zasady współpracy** \> & poczty e-mail **& Reguły** \> **zasad** \> zagrożeń **Listy dozwolonych/blokowych dzierżawy** w sekcji **Reguły**. Aby przejść bezpośrednio do karty **Fałszowanie** na stronie **Lista dozwolonych/zablokowanych dzierżaw** , użyj polecenia <https://security.microsoft.com/tenantAllowBlockList?viewid=SpoofItem>.

2. Na stronie **Zezwalaj/blokuj listy dzierżawy** szczegółowy wgląd w analizę podróbek wygląda następująco:

   :::image type="content" source="../../media/m365-sc-spoof-intelligence-insight.png" alt-text="Szczegółowe informacje o analizie dotyczącej fałszowania na stronie zasad ochrony przed wyłudzaniem informacji" lightbox="../../media/m365-sc-spoof-intelligence-insight.png":::

   Szczegółowe informacje mają dwa tryby:

   - **Tryb szczegółowych informacji**: jeśli włączono analizę fałszowania, szczegółowe informacje pokazują, ile komunikatów zostało wykrytych przez analizę fałszowania w ciągu ostatnich siedmiu dni.
   - **Co zrobić, jeśli tryb**: Jeśli analiza fałszowania jest wyłączona, szczegółowe informacje pokazują, ile komunikatów *zostałoby* wykrytych przez analizę fałszowania w ciągu ostatnich siedmiu dni.

Aby wyświetlić informacje na temat wykrywania fałszywych danych wywiadowczych, kliknij pozycję **Wyświetl działanie fałszowania** w szczegółowych informacjach na temat fałszowania analizy.

### <a name="view-information-about-spoofed-messages"></a>Wyświetlanie informacji o sfałszowanych komunikatach

> [!NOTE]
> Pamiętaj, że na tej stronie pojawiają się tylko sfałszowani nadawcy, którzy zostali wykryci przez fałszywą inteligencję. Po zastąpieniu werdyktu zezwalania lub blokowania w analizie fałszywy nadawca staje się ręcznym wpisem zezwalającym lub blokowym wyświetlanym tylko na karcie **Fałszowanie** na liście dozwolonych/zablokowanych dzierżawców.

Na stronie **Szczegółowe informacje o fałszowaniu analizy** wyświetlanej po kliknięciu pozycji **Wyświetl działanie fałszowania** w analizie analizy fałszowania strona zawiera następujące informacje:

- **Sfałszowany użytkownik**: **domena** sfałszowanego użytkownika wyświetlana w polu **Od** w klientach poczty e-mail. Adres Od jest również znany jako `5322.From` adres.
- **Wysyłanie infrastruktury**: znana również jako _infrastruktura_. Infrastruktura wysyłania będzie jedną z następujących wartości:
  - Domena znaleziona w odwrotnym wyszukiwaniu DNS (rekord PTR) adresu IP źródłowego serwera poczty e-mail.
  - Jeśli źródłowy adres IP nie ma rekordu PTR, infrastruktura wysyłania jest identyfikowana jako \<source IP\>/24 (na przykład 192.168.100.100/24).
- **Liczba komunikatów**: liczba komunikatów z kombinacji sfałszowanej domeny _i_ infrastruktury wysyłania do organizacji w ciągu ostatnich 7 dni.
- **Ostatnio widziano**: ostatnia data odebrania komunikatu z infrastruktury wysyłania zawierającej sfałszowaną domenę.
- **Typ fałszowania**: Jedna z następujących wartości:
  - **Wewnętrzne**: sfałszowany nadawca znajduje się w domenie należącej do Organizacji ( [akceptowana domena](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
  - **Zewnętrzne**: sfałszowany nadawca znajduje się w domenie zewnętrznej.
- **Akcja**: Ta wartość to **Dozwolone** lub **Zablokowane**:
  - **Dozwolone**: Domena nie powiodła się jawne uwierzytelnianie poczty e-mail sprawdza [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) i [DMARC](use-dmarc-to-validate-email.md). Jednak domena przeszła nasze niejawne testy uwierzytelniania poczty e-mail ([uwierzytelnianie złożone](email-validation-and-authentication.md#composite-authentication)). W związku z tym nie podjęto żadnych działań chroniących przed fałszowaniem wiadomości.
  - **Zablokowane**: komunikaty z kombinacji sfałszowanej domeny _i_ infrastruktury wysyłania są oznaczone jako złe przez fałszowanie inteligencji. Akcja wykonywana w przypadku sfałszowanych wiadomości jest kontrolowana przez domyślne zasady ochrony przed wyłudzaniem informacji lub niestandardowe zasady ochrony przed wyłudzaniem informacji (wartość domyślna to **Przenieś wiadomość do folderu Wiadomości-śmieci**). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender](configure-mdo-anti-phishing-policies.md).

Możesz kliknąć wybrane nagłówki kolumn, aby posortować wyniki.

Aby filtrować wyniki, dostępne są następujące opcje:

- Kliknij przycisk **Filtruj** . W wyświetlonym okienku wysuwu **Filtr** możesz filtrować wyniki według:
  - **Typ fałszowania**
  - **Akcja**
- Użyj pola **Wyszukiwania** , aby wprowadzić rozdzielaną przecinkami listę sfałszowanych wartości domeny lub wysłać wartości infrastruktury w celu filtrowania wyników.

### <a name="view-details-about-spoofed-messages"></a>Wyświetlanie szczegółów dotyczących sfałszowanych komunikatów

Po wybraniu wpisu z listy zostanie wyświetlony wysuwany szczegół zawierający następujące informacje i funkcje:

- **Zezwalaj na fałszowanie** lub **blokowanie fałszowania**: wybierz jedną z tych wartości, aby zastąpić oryginalny werdykt analizy fałszowania i przenieść wpis ze szczegółowych informacji wywiadowczych na fałszywe dane wywiadowcze do listy dozwolonych/zablokowanych dzierżaw jako wpis dozwolony lub blokowy na potrzeby fałszowania.
- Dlaczego to złapaliśmy.
- Co musisz zrobić.
- Podsumowanie domeny, które zawiera większość tych samych informacji z głównej strony analizy fałszowania.
- WhoIs data about the sender (WhoIs data about the sender).
- Link do otwierania [Eksploratora zagrożeń](threat-explorer.md) w celu wyświetlenia dodatkowych szczegółów dotyczących nadawcy w obszarze **Wyświetl** \> **język phish** w Ochrona usługi Office 365 w usłudze Microsoft Defender.
- Podobne komunikaty, które widzieliśmy w twojej dzierżawie od tego samego nadawcy.

### <a name="about-allowed-spoofed-senders"></a>Informacje o dozwolonych sfałszowanych nadawcach

Dozwolony sfałszowany nadawca w analizie analizy fałszowania lub zablokowany sfałszowany nadawca, który został ręcznie zmieniony na **Zezwalaj na fałszowanie** , zezwala tylko na komunikaty z kombinacji sfałszowanej domeny _i_ infrastruktury wysyłania. Nie zezwala na wysyłanie wiadomości e-mail z sfałszowanej domeny z dowolnego źródła ani nie zezwala na wysyłanie wiadomości e-mail z infrastruktury wysyłania dla dowolnej domeny.

Na przykład następujący sfałszowany nadawca może podszywać się pod:

- **Domena**: gmail.com
- **Infrastruktura**: tms.mx.com

Tylko wiadomości e-mail z tej pary infrastruktury/wysyłania będą mogły zostać sfałszowane. Inni nadawcy próbujący podszyć gmail.com nie są automatycznie dozwoloni. Komunikaty od nadawców w innych domenach, które pochodzą z tms.mx.com, są nadal sprawdzane przez analizę fałszowania i mogą być blokowane.

## <a name="use-the-spoof-intelligence-insight-in-exchange-online-powershell-or-standalone-eop-powershell"></a>Korzystanie z analizy fałszowania w programie Exchange Online programie PowerShell lub autonomicznym programie PowerShell EOP

W programie PowerShell polecenie cmdlet **Get-SpoofIntelligenceInsight** służy do **wyświetlania** dozwolonych i zablokowanych sfałszowanych nadawców wykrytych przez analizę fałszowania. Aby ręcznie zezwolić lub zablokować sfałszowanych nadawców, należy użyć polecenia cmdlet **New-TenantAllowBlockListSpoofItems** . Aby uzyskać więcej informacji, zobacz [Używanie programu PowerShell do zarządzania fałszywymi wpisami nadawcy na liście dozwolonych/zablokowanych dzierżawców](tenant-allow-block-list.md).

Aby wyświetlić informacje w analizie analizy fałszowania, uruchom następujące polecenie:

```powershell
Get-SpoofIntelligenceInsight
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SpoofIntelligenceInsight](/powershell/module/exchange/get-spoofintelligenceinsight).

## <a name="other-ways-to-manage-spoofing-and-phishing"></a>Inne sposoby zarządzania fałszowaniem i wyłudzaniem informacji

Należy zachować staranność w zakresie fałszowania i wyłudzania informacji. Poniżej przedstawiono powiązane sposoby sprawdzania nadawców, którzy podszywają się pod Twoją domenę, i zapobiegania ich uszkodzeniu organizacji:

- Sprawdź **raport dotyczący fałszowania poczty**. Ten raport często służy do wyświetlania sfałszowanych nadawców i ułatwiania zarządzania nimi. Aby uzyskać informacje, zobacz [Raport wykrywania fałszowania](view-email-security-reports.md#spoof-detections-report).

- Przejrzyj konfigurację struktury zasad nadawcy (SPF). Aby uzyskać krótkie wprowadzenie do SPF i szybko skonfigurować go, zobacz [Konfigurowanie SPF w Microsoft 365, aby zapobiec fałszowaniu](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Aby uzyskać bardziej szczegółowe informacje na temat sposobu, w jaki Office 365 używa SPF, rozwiązywania problemów lub wdrożeń niestandardowych, takich jak wdrożenia hybrydowe, zacznij od tego, [jak Office 365 używa struktury zasad nadawcy (SPF), aby zapobiec fałszowaniu](how-office-365-uses-spf-to-prevent-spoofing.md).

- Przejrzyj konfigurację usługi DomainKeys Identified Mail (DKIM). Oprócz funkcji SPF i DMARC należy użyć modułu DKIM, aby uniemożliwić osobom atakującym wysyłanie komunikatów, które wyglądają tak, jakby pochodziły z Twojej domeny. Program DKIM umożliwia dodanie podpisu cyfrowego do wiadomości e-mail w nagłówku wiadomości. Aby uzyskać informacje, zobacz [Używanie modułu DKIM do weryfikowania wychodzących wiadomości e-mail wysyłanych z domeny niestandardowej w Office 365](use-dkim-to-validate-outbound-email.md).

- Przejrzyj konfigurację uwierzytelniania, raportowania i zgodności (DMARC) opartej na domenie. Implementacja DMARC za pomocą SPF i DKIM zapewnia dodatkową ochronę przed fałszowaniem i wyłudzaniem informacji za pomocą poczty e-mail. Usługa DMARC pomaga odbierać systemy poczty, aby określić, co zrobić z wiadomościami wysyłanymi z domeny, które nie sprawdzają SPF lub DKIM. Aby uzyskać informacje, zobacz [Używanie funkcji DMARC do weryfikowania poczty e-mail w Office 365](use-dmarc-to-validate-email.md).
