---
title: Konfigurowanie symulowania wyłudzania informacji innych firm do użytkowników i niefiltrowanych wiadomości do skrzynek pocztowych usługi SecOps
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak za pomocą zaawansowanych zasad dostarczania w programie Exchange Online Protection (EOP) identyfikować wiadomości, które nie powinny być filtrowane w określonych obsługiwanych scenariuszach (symulowanie wyłudzania informacji innych firm i wiadomości dostarczane do skrzynek pocztowych operacji zabezpieczeń (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bf564765b9bb896fcfcdac01961d414139199603
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021314"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Konfigurowanie symulowania wyłudzania informacji innych firm do użytkowników i niefiltrowanych wiadomości do skrzynek pocztowych usługi SecOps

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Aby twoja organizacja domyślnie zapewniała [bezpieczeństwo, program](secure-by-default.md) Exchange Online Protection (EOP) nie zezwala na bezpieczne listy ani na obejście filtrowania w przypadku wiadomości zidentyfikowanych jako złośliwe oprogramowanie lub jako próby wyłudzenia informacji o wysokiej pewności. Istnieją jednak określone scenariusze, które wymagają dostarczenia niefiltrowanych wiadomości. Przykład:

- **Symulacyjne próby wyłudzania** informacji od innych firm: Symulowane ataki mogą ułatwić zidentyfikowanie użytkowników, którzy mogą być podatni na ataki, zanim prawdziwe ataki będą mieć wpływ na organizację.
- **Operacje zabezpieczeń (SecOps)** skrzynki pocztowe: dedykowane skrzynki pocztowe, które są używane przez zespoły zabezpieczeń do zbierania i analizowania niefiltrowanych wiadomości (zarówno tych dobrych, jak i złych).

Za pomocą zaawansowanych zasad _dostarczania w aplikacji_ Microsoft 365 można zapobiec filtrowaniu wiadomości przychodzących w _tych konkretnych_ scenariuszach.<sup>\*</sup> Zaawansowane zasady dostarczania zapewniają, że wiadomości w tych scenariuszach osiągną następujące wyniki:

- Filtry w usługach EOP i Microsoft Defender Office 365 nie mają żadnych działań w przypadku tych wiadomości.<sup>\*</sup>
- [Czyszczenie zerowej godziny w przypadku](zero-hour-auto-purge.md) spamu i wyłudzania informacji nie podejmie żadnych działań w przypadku tych wiadomości.<sup>\*</sup>
- [W tych scenariuszach](/microsoft-365/compliance/alert-policies#default-alert-policies) domyślne alerty systemowe nie są wyzwalane.
- [Program AIR i klastrowanie w programie Defender dla Office 365](office-365-air.md) ignoruje te wiadomości.
- Przeznaczone specjalnie do przykładów wyłudzania informacji innych firm:
  - [Zgłoszenia administratorów](admin-submission.md) generują automatyczną odpowiedź informjącą, że wiadomość jest częścią kampanii symulacyjnej wyłudzania informacji i nie jest prawdziwym zagrożeniem. Alerty i air nie zostaną wyzwolone. Środowisko przesyłania administratora będzie wyświetlać te wiadomości jako symulowane zagrożenie.
  - Gdy użytkownik zgłasza wiadomość symulacyjna wyłudzania informacji przy użyciu dodatków Report Message (Wiadomość raportu wyłudzająca informacje) lub [Report Phishing](enable-the-report-message-add-in.md) (Wyłudzanie informacji), system nie generuje alertu, badania ani zdarzenia. Linki ani pliki nie zostaną detonowane, ale wiadomość pojawi się również na karcie Użytkownik zgłosił wiadomości na  **stronie** Materiały.
  - [Sejf Linki w programie Defender Office 365](safe-links.md) wiadomości nie blokują ani nie detonują adresów URL zidentyfikowanych w tych wiadomościach w momencie kliknięcia. Adresy URL są nadal zawijane, ale nie są blokowane.
  - [Sejf załączników w programie Defender Office 365](safe-attachments.md) nie detonuje załączników w tych wiadomościach.

<sup>\*</sup> Nie można pominąć filtrowania złośliwego oprogramowania ani zap w przypadku złośliwego oprogramowania.

Wiadomości zidentyfikowane za pomocą zaawansowanych zasad dostarczania nie są zagrożeniami bezpieczeństwa, dlatego są one oznaczone jako zastępowanie systemu. W środowiskoch administratora te komunikaty są wyświetlane ze względu na zastępowanie systemu symulacyjnego wyłudzania informacji lub zastępowanie systemu skrzynek pocztowych programu **SecOps**. Administratorzy mogą filtrować i analizować zmiany w tych systemach zastępować w następujących środowiskoch:

- [Wykrywanie w Eksploratorze zagrożeń/](threat-explorer.md)czasie rzeczywistym w programie Defender Office 365 plan 2: Administrator może filtrować według źródła  zastępowania systemu i wybrać symulowanie **wyłudzania** informacji lub pozycję **Skrzynka pocztowa usługi SecOps**.
- Strona jednostki poczty [e-mail](mdo-email-entity-page.md) w wykrywaniu w Eksploratorze zagrożeń/w czasie rzeczywistym: administrator może wyświetlać wiadomość, na co zezwoliły zasady organizacji,  za pomocą skrzynki pocztowej **usługi SecOps** lub symulacyjnej wyłudzania informacji w obszarze Zastępowanie dzierżawy w sekcji Zastępowanie. 
- Raport [o stanie ochrony](view-email-security-reports.md#threat-protection-status-report) przed zagrożeniami: Administrator może  filtrować według danych przez zastępowanie systemu w menu rozwijanych i wybrać wyświetlanie dozwolonych wiadomości ze względu na zastępowanie systemu symulacyjnego wyłudzania informacji. Aby wyświetlić wiadomości dozwolone przez zastępowanie skrzynki pocztowej usługi SecOps,  możesz wybrać podział wykresu według lokalizacji dostarczania w menu rozwijanym z **powodu** podziału wykresu.
- [Zaawansowane wyszukiwanie w programie Microsoft Defender dla](../defender-endpoint/advanced-hunting-overview.md) punktu końcowego: Zastąpienia systemu skrzynek pocztowych programu SecOps i symulacja wyłudzania informacji są wyświetlane jako opcje w ramach usługi OrgLevelPolicy w narzędziu EmailEvents.
- [Widoki kampanii](campaigns.md): Administrator może filtrować według źródła **zastępowania systemu** i wybrać **symulacyjne wyłudzanie** informacji lub **pozycję Skrzynka pocztowa usługi SecOps**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zaawansowane dostarczanie** , otwórz stronę <https://security.microsoft.com/advanceddelivery>.

- Aby nawiązać połączenie z programem PowerShell & zabezpieczeń lub zgodności, zobacz Połączenie się z centrum & [zabezpieczeń w programie PowerShell](/powershell/exchange/connect-to-scc-powershell).

- Aby można było wykonać procedury z tego artykułu, musisz mieć przypisane uprawnienia:
  - Aby tworzyć, modyfikować lub usuwać skonfigurowane ustawienia w zaawansowanych zasadach dostarczania, musisz być członkiem grupy ról **Administrator** zabezpieczeń w **portalu Microsoft 365 Defender** i członkiem grupy ról Zarządzanie organizacją w **programie Exchange Online**.
  - Aby mieć dostęp tylko do odczytu do zaawansowanych zasad dostarczania, musisz być członkiem grup ról Czytnik globalny  lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender i](permissions-microsoft-365-security-center.md) [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > Dodanie użytkowników do odpowiedniej roli Azure Active Directory zapewnia użytkownikom wymagane uprawnienia w portalu usługi Microsoft 365 Defender oraz uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Konfigurowanie skrzynek Microsoft 365 Defender SecOps w zaawansowanych zasadach dostarczania za pomocą portalu wiadomości

1.  W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Reguły &-mail i zasad & **zasad** \>  \> zagrożeń **Zaawansowane dostarczanie.** Aby przejść bezpośrednio do strony **Zaawansowane dostarczanie** , użyj opcji <https://security.microsoft.com/advanceddelivery>.

2. Na stronie **Zaawansowane dostarczanie sprawdź** , czy jest zaznaczona karta skrzynki pocztowej usługi **SecOps** , a następnie wykonaj jedną z następujących czynności:
   - Kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**.
   - Jeśli nie ma skonfigurowanych symulowań wyłudzania informacji, kliknij przycisk **Dodaj**.

3. W oknie wysuwanym Edytowanie skrzynek pocztowych usługi **SecOps**, które zostanie otwarte, wprowadź istniejącą skrzynkę pocztową programu Exchange Online, którą chcesz wyznaczyć na skrzynkę pocztową usługi SecOps, wykonując jedną z następujących czynności:
   - Kliknij w polu, poczekaj na rozwiązanie listy skrzynek pocztowych, a następnie wybierz skrzynkę pocztową.
   - Kliknij w polu zacznij wpisywać identyfikator skrzynki pocztowej (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), a następnie wybierz skrzynkę pocztową (nazwę wyświetlaną) z wyników.

     Powtarzaj ten krok tyle razy, ile to konieczne. Grupy dystrybucyjne są niedozwolone.

     Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

4. Po zakończeniu kliknij przycisk **Zapisz**.

Konfigurowane wpisy skrzynek pocztowych usługi SecOps są wyświetlane na karcie **Skrzynka pocztowa usługi SecOps** . Aby wprowadzić zmiany, kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** na karcie.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Korzystanie z portalu Microsoft 365 Defender do konfigurowania symulacyjnych wyłudzania informacji innych firm w zaawansowanych zasadach dostarczania

1.  W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Reguły &-mail i zasad & **zasad** \>  \> zagrożeń **Zaawansowane dostarczanie.** Aby przejść bezpośrednio do strony **Zaawansowane dostarczanie** , użyj opcji <https://security.microsoft.com/advanceddelivery>.

2. Na stronie **Zaawansowane dostarczanie** wybierz kartę symulowania **wyłudzania** informacji, a następnie wykonaj jedną z następujących czynności:
   - Kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**.
   - Jeśli nie ma skonfigurowanych symulowań wyłudzania informacji, kliknij przycisk **Dodaj**.

3. W **oknie wysuwana** Edycja innej firmy podczas próby wyłudzania informacji skonfiguruj następujące ustawienia:

   - **Domena**: Rozwiń to ustawienie i wprowadź co najmniej jedną domenę adresu e-mail (na przykład contoso.com), klikając pole, wprowadzając wartość, a następnie naciskając klawisz Enter lub wybierając wartość wyświetlaną poniżej tego pola. Powtarzaj ten krok tyle razy, ile to konieczne. Możesz dodać maksymalnie 20 wpisów.

     > [!NOTE]
     > Użyj domeny z adresu (znanego również jako **adres MAIL FROM**, nadawcy P1 lub nadawcy koperty) używanej do transmisji SMTP wiadomości lub domeny DKIM  (DomainKeys Identified Mail) określonej przez dostawcę symulowania wyłudzania informacji.`5321.MailFrom` 

   - **Wysyłanie adresu IP**: Rozwiń to ustawienie i wprowadź co najmniej jeden prawidłowy adres IPv4, klikając pole, wprowadzając wartość, a następnie naciskając klawisz Enter lub wybierając wartość, która jest wyświetlana poniżej tego pola. Powtarzaj ten krok tyle razy, ile to konieczne. Możesz dodać maksymalnie 10 wpisów. Prawidłowe wartości to:
     - Pojedynczy adres IP: Na przykład 192.168.1.1.
     - Zakres adresów IP: Na przykład: 192.168.0.1-192.168.0.254.
     - IP CIDR: Na przykład 192.168.0.1/25.
   - **Adresy URL** symulacji, aby zezwolić. Rozwiń to ustawienie i opcjonalnie wprowadź określone adresy URL, które są częścią kampanii symulacyjnej wyłudzania informacji, które nie powinny być blokowane ani detonowane, klikając pole, wprowadzając wartość, a następnie naciskając klawisz Enter lub wybierając wartość wyświetlaną poniżej tego pola. Możesz dodać maksymalnie 10 wpisów. Aby uzyskać informacje na temat formatu składni adresu URL, zobacz [Składnia adresu URL dla listy adresów zezwalania/blokowania dzierżawy](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). Te adresy URL są zawijane w momencie kliknięcia, ale nie są blokowane.

   Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   > [!NOTE]
   > Aby skonfigurować symulację wyłudzania informacji innej firmy w dostarczaniu zaawansowanym, należy odpowiednio skonfigurować następujące informacje:
   > 
   > - Co najmniej jedna **domena** pochodzi z jednego z następujących źródeł:
   >   - Adres `5321.MailFrom` (znany także jako adres MAIL FROM, nadawca P1 lub nadawca koperty).
   >   - Domena DKIM.
   > - Co najmniej jeden **wysyłający adres IP**.
   > 
   > Opcjonalnie możesz dołączyć adresy **URL symulowania** , aby zapewnić, że adresy URL w wiadomościach symulacyjnych nie będą blokowane.
   > Dla każdego pola możesz określić maksymalnie 10 wpisów.
   > Musi być zgodne co najmniej jedna domena i jeden  wysyłający adres **IP**, ale nie jest zachowywane żadne skojarzenie między wartościami.

4. Po zakończeniu wykonaj jedną z następujących czynności:
   - **Za pierwszym razem**: Kliknij **przycisk Dodaj**, a następnie kliknij przycisk **Zamknij**.
   - **Edytuj istniejące**: Kliknij **pozycję Zapisz,** a następnie kliknij **przycisk Zamknij**.

Konfigurowane przez Ciebie wpisy symulacyjne wyłudzania informacji są wyświetlane na karcie **symulacyjnej wyłudzania** informacji. Aby wprowadzić zmiany, kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** na karcie.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Dodatkowe scenariusze wymagające obejścia filtrowania

Oprócz dwóch scenariuszy, w których mogą pomóc zaawansowane zasady dostarczania, istnieją inne scenariusze, które mogą wymagać obejścia filtrowania:

- **Filtry innych firm**: Jeśli rekord MX domeny nie Office 365 (wiadomości  są najpierw kierowane w inne [miejsce), domyślnie](secure-by-default.md) bezpieczne nie *jest dostępne*. Jeśli chcesz zwiększyć ochronę, musisz włączyć funkcję rozszerzonego filtrowania dla łączników (ta *pomiń na liście*). Aby uzyskać więcej informacji, zobacz [Zarządzanie przepływem poczty e-mail za pomocą usługi w chmurze innej firmy z usługą Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud). Jeśli nie chcesz korzystać z funkcji rozszerzonego filtrowania dla łączników, użyj reguł przepływu poczty e-mail (nazywanych również regułami transportu), aby pominąć filtrowanie firmy Microsoft w przypadku wiadomości, które zostały już ocenione przez filtrowanie innych firm. Aby uzyskać więcej informacji, zobacz Ustawianie listy SCL w wiadomościach przy użyciu [reguł przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- Wyniki fałszywie dodatnie w trakcie przeglądania **: Warto** tymczasowo zezwolić na zgłaszanie znanych dobrych wiadomości, które są niepoprawnie oznaczane jako niepoprawne dla firmy Microsoft (wyników fałszywie dodatnich), które są nadal analizowane przez firmę Microsoft za pośrednictwem przesyłania przez administratora.[](admin-submission.md) Podobnie jak w przypadku wszystkich zastępować ****, zalecane jest, aby przydziały te były tymczasowe.

## <a name="security--compliance-center-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Procedury & zabezpieczeń centrum zgodności programu PowerShell dla skrzynek pocztowych usługi SecOps w zaawansowanych zasadach dostarczania

W centrum & zabezpieczeń w programie PowerShell podstawowe elementy skrzynek pocztowych usługi SecOps w zaawansowanych zasadach dostarczania są następujące:

- **Zasady zastępowania secops**: sterowane **\*przez polecenia cmdlet -SecOpsOverridePolicy** .
- **Reguła zastępowania secOps**: kontrolowana **\*przez polecenia cmdlet -SecOpsOverrideRule** .

Ma to następujące wyniki:

- Najpierw tworzysz zasady, a następnie tworzysz regułę identyfikującą zasady, których ta reguła dotyczy.
- Usunięcie zasad z programu PowerShell powoduje również usunięcie odpowiadającej jej reguły.
- Usunięcie reguły z programu PowerShell nie powoduje usunięcia odpowiednich zasad. Należy ręcznie usunąć odpowiednie zasady.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>Konfigurowanie skrzynek pocztowych usługi SecOps przy użyciu programu PowerShell

Konfigurowanie skrzynki pocztowej usługi SecOps w zaawansowanych zasadach dostarczania w programie PowerShell jest procesem dwuetapowym:

1. Utwórz zasady zastępowania zabezpieczeń.
2. Utwórz regułę zastępowania zabezpieczeń określającą zasady, których ta reguła dotyczy.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>Krok 1. Tworzenie zasad zastępowania zabezpieczeń przy użyciu programu PowerShell

Aby utworzyć zasady zastępowania zabezpieczeń, użyj następującej składni:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> Niezależnie od wartości Name (Nazwa) zostanie nadana nazwa zasad _SecOpsOverridePolicy_, dlatego warto użyć tej wartości.

W tym przykładzie są  tworzyne zasady skrzynki pocztowej usługi SecOps.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>Krok 2. Tworzenie reguły zastępowania secops za pomocą programu PowerShell

W tym przykładzie jest określonej reguły skrzynki pocztowej usługi SecOps z określonymi ustawieniami.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> Niezależnie od wartości Name (Nazwa) nazwa reguły będzie określana jako _SecOpsOverrideRule_\<GUID\>\<GUID\>, która ma unikatowy identyfikator GUID (na przykład 6fed4b63-3563-495d-a481-b24a311f8329).

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>Wyświetlanie zasad zastępowania zabezpieczeń za pomocą programu PowerShell

W tym przykładzie są zwracane szczegółowe informacje o zasadach skrzynki pocztowej usługi SecOps i tylko o nich.

```powershell
Get-SecOpsOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>Wyświetlanie reguł zastępowania secops za pomocą programu PowerShell

W tym przykładzie są zwracane szczegółowe informacje na temat zastępowania reguł w programie SecOps.

```powershell
Get-SecOpsOverrideRule
```

Mimo że poprzednie polecenie powinno zwrócić tylko jedną regułę, wszystkie reguły oczekujące na usunięcie także mogą zostać uwzględnione w wynikach.

W tym przykładzie identyfikuje się prawidłową regułę (jedną) i wszelkie nieprawidłowe reguły.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Nieprawidłowe reguły można usunąć, używając polecenia cmdlet **Remove-SecOpsOverrideRule** w sposób opisany w dalszej części [tego artykułu](#use-powershell-to-remove-secops-override-rules).

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>Modyfikowanie zasad zastępowania zabezpieczeń za pomocą programu PowerShell

Aby zmodyfikować zasady zastępowania zabezpieczeń, użyj następującej składni:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

W tym przykładzie `secops2@contoso.com` dodano zasady zastępowania zabezpieczeń.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> Jeśli istnieje skojarzona, prawidłowa reguła zastępująca secOps, adresy e-mail w tej  reguła również zostaną zaktualizowane.

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>Modyfikowanie reguły zastępowania secops za pomocą programu PowerShell

Polecenie **cmdlet Set-SecOpsOverrideRule nie modyfikuje adresów e-mail** w regułę zastępowania secops. Aby zmodyfikować adresy e-mail w regułę zastępowania secops, użyj polecenia cmdlet **Set-SecOpsOverridePolicy** .

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>Usuwanie zasad zastępowania zabezpieczeń za pomocą programu PowerShell

W tym przykładzie zasady skrzynki pocztowej usługi SecOps oraz odpowiadająca jej reguła są usuwane.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>Usuwanie reguł zastępowania secops za pomocą programu PowerShell

Aby usunąć regułę zastępowania secops, użyj następującej składni:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

W tym przykładzie usuwana jest określona reguła zastępowania secops.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-center-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Procedury & zabezpieczeń w programie PowerShell dla przykładów wyłudzania informacji innych firm w zaawansowanych zasadach dostarczania

W centrum & zabezpieczeń w programie PowerShell podstawowe elementy innych symulowań wyłudzania informacji w zaawansowanych zasadach dostarczania to:

- **Zasady zastępowania podczas wyłudzania** informacji: Sterowane **\*przez polecenia cmdlet -PhishSimOverridePolicy** .
- **Reguła zastępowania symulowania wyłudzania** informacji: kontrolowana przez **\*polecenia cmdlet -PhishSimOverrideRule** .
- **Adresy URL dozwolonych (odblokowanych)** prób wyłudzania informacji: Sterowane **\*przez polecenia cmdlet -TenantAllowBlockListItems** .

Ma to następujące wyniki:

- Najpierw tworzysz zasady, a następnie tworzysz regułę identyfikującą zasady, których ta reguła dotyczy.
- Ustawienia zasad i reguły można modyfikować osobno.
- Usunięcie zasad z programu PowerShell powoduje również usunięcie odpowiadającej jej reguły.
- Usunięcie reguły z programu PowerShell nie powoduje usunięcia odpowiednich zasad. Należy ręcznie usunąć odpowiednie zasady.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Konfigurowanie symulacyjnych wyłudzania informacji innych firm przy użyciu programu PowerShell

Konfigurowanie symulacji wyłudzania informacji innej firmy w programie PowerShell jest wieloetapowym procesem:

1. Utwórz zasady zastępowania wyłudzania informacji.
2. Utwórz regułę zastępowania przez symulowanie wyłudzania informacji, która określa:
   - Zasady, których ta reguła dotyczy.
   - Źródłowy adres IP wiadomości symulacyjnych wyłudzania informacji.
3. Opcjonalnie możesz tożsamościąć adresy URL symulowania wyłudzania informacji, które powinny być dozwolone (czyli nie są blokowane ani skanowane).

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>Krok 1. Tworzenie zasady zastępowania symulowania wyłudzania informacji za pomocą programu PowerShell

W tym przykładzie są  tworzyne zasady zastępowania podczas wyłudzania informacji.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Uwaga**: Niezależnie od wartości Name (Nazwa) określisz nazwę zasad _PhishSimOverridePolicy_, więc możesz również użyć tej wartości.

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>Krok 2. Tworzenie reguły zastępowania symulowania wyłudzania informacji za pomocą programu PowerShell

Należy stosować następującą składnię:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

Niezależnie od wartości Name (Nazwa), nazwą reguły będzie _PhishSimOverrideRule_\<GUID\>\<GUID\>, gdzie jest unikatowa wartość GUID (na przykład a0eae53e-d755-4a42-9320-b9c6b55c5011).

Prawidłowy wpis adresu IP to jedna z następujących wartości:

- Pojedynczy adres IP: Na przykład 192.168.1.1.
- Zakres adresów IP: Na przykład: 192.168.0.1-192.168.0.254.
- IP CIDR: Na przykład 192.168.0.1/25.

W tym przykładzie tworzy się symulacyjne zastępowanie reguły przez wyłudzanie informacji przy użyciu określonych ustawień.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>Krok 3. (Opcjonalnie) Używanie programu PowerShell do identyfikowania adresów URL symulacyjnych wyłudzania informacji, które są na to zezwalane

Należy stosować następującą składnię:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

Aby uzyskać szczegółowe informacje na temat składni adresu URL, zobacz [składnię adresu URL dla listy zablokowanych/zezwalanych na dzierżawę](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

W tym przykładzie dodano adres URL zezwalania na wpis dla określonego adresu URL symulacyjnego wyłudzania informacji innej firmy bez wygasania.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Wyświetlanie zasad zastępowania wyłudzania informacji za pomocą programu PowerShell

W tym przykładzie są zwracane szczegółowe informacje dotyczące zasady zastępowania tylko jednej i tylko symulacyjnej metody wyłudzania informacji.

```powershell
Get-PhishSimOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Wyświetlanie reguł zastępowania reguł za pomocą programu PowerShell

W tym przykładzie są zwracane szczegółowe informacje dotyczące reguł zastępowania reguł wyłudzania informacji.

```powershell
Get-PhishSimOverrideRule
```

Mimo że poprzednie polecenie powinno zwrócić tylko jedną regułę, wszystkie reguły oczekujące na usunięcie także mogą zostać uwzględnione w wynikach.

W tym przykładzie identyfikuje się prawidłową regułę (jedną) i wszelkie nieprawidłowe reguły.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Po zidentyfikowaniu nieprawidłowych reguł można je usunąć przy użyciu polecenia cmdlet **Remove-PhishSimOverrideRule** zgodnie z opisem w dalszej części [tego artykułu](#use-powershell-to-remove-phishing-simulation-override-rules).

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>Wyświetlanie dozwolonych wpisów adresu URL dla próbek wyłudzania informacji przy użyciu programu PowerShell

Aby wyświetlić adresy URL dozwolonych symeranów wyłudzania informacji, uruchom następujące polecenie:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Modyfikowanie zasad zastępowania wyłudzania informacji za pomocą programu PowerShell

Aby zmodyfikować zasady zastępowania symulowania wyłudzania informacji, użyj następującej składni:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

W tym przykładzie zasady zastępowania są wyłączane podczas wyłudzania informacji.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>Modyfikowanie reguł zastępowania reguł wyłudzania informacji za pomocą programu PowerShell

Aby zmodyfikować regułę zastępowania reguły wyłudzania informacji, użyj następującej składni:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

W tym przykładzie zmodyfikuje określoną regułę wyłudzania informacji zastępującą regułę następującymi ustawieniami:

- Dodaj wpis domeny blueyonderairlines.com.
- Usuń wpis adresu IP 192.168.1.55.

Zwróć uwagę, że te zmiany nie wpływają na istniejące wpisy.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>Modyfikowanie dozwolonych wpisów adresu URL dla próbek wyłudzania informacji przy użyciu programu PowerShell

Nie można bezpośrednio modyfikować wartości adresu URL. Możesz usunąć [istniejące wpisy adresu URL i](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) [dodać nowe wpisy adresu URL](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) zgodnie z opisem w tym artykule.

Aby zmodyfikować inne właściwości wpisu adresu URL dla próby wyłudzenia informacji (na przykład datę wygaśnięcia lub komentarze), użyj następującej składni:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

Należy zidentyfikować wpis do zmodyfikowania za pomocą wartości adresu URL (parametr _Entries_ ) lub wartości Identity z wyników polecenia cmdlet **Get-TenantAllowBlockListItems** ( _parametru Ids_ ).

W tym przykładzie zmodyfikował datę wygaśnięcia określonej pozycji.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery –Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Usuwanie zasad zastępowania wyłudzania informacji za pomocą programu PowerShell

Ten przykład usuwa zasady zastępowania zasad wyłudzania informacji i odpowiadające im reguły.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Usuwanie reguł zastępowania reguł za pomocą programu PowerShell

Aby usunąć regułę zastępowania reguły podczas wyłudzania informacji, użyj następującej składni:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

W tym przykładzie reguła zastępująca wyłudzanie informacji jest usuwana z określonej reguły wyłudzania informacji.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>Usuwanie dozwolonych wpisów adresu URL dla prób wyłudzania informacji przy użyciu programu PowerShell

Aby usunąć istniejący wpis adresu URL dla próby wyłudzenia informacji, użyj następującej składni:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

Należy zidentyfikować wpis do zmodyfikowania za pomocą wartości adresu URL (parametr _Entries_ ) lub wartości Identity z wyników polecenia cmdlet **Get-TenantAllowBlockListItems** ( _parametru Ids_ ).

W tym przykładzie zmodyfikował datę wygaśnięcia określonej pozycji.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery –Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
