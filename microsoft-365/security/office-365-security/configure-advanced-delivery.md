---
title: Konfigurowanie dostarczania symulacji wyłudzania informacji innych firm użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych SecOps
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
description: Administratorzy mogą dowiedzieć się, jak używać zaawansowanych zasad dostarczania w Exchange Online Protection (EOP) do identyfikowania komunikatów, które nie powinny być filtrowane w określonych obsługiwanych scenariuszach (symulacje wyłudzania informacji i wiadomości dostarczane do skrzynek pocztowych operacji zabezpieczeń (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 109d711623d2a0355851414af3ef0cb1beadf6af
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490448"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Konfigurowanie dostarczania symulacji wyłudzania informacji innych firm użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych SecOps

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Aby zapewnić bezpieczeństwo organizacji [domyślnie](secure-by-default.md), Exchange Online Protection (EOP) nie zezwala na bezpieczne listy ani filtrowanie pomijania komunikatów, które są identyfikowane jako złośliwe oprogramowanie lub wyłudzanie informacji o wysokim poziomie zaufania. Istnieją jednak konkretne scenariusze, które wymagają dostarczania niefiltrowanych komunikatów. Przykład:

- **Symulacje wyłudzania informacji innych firm**: symulowane ataki mogą pomóc zidentyfikować narażonych użytkowników, zanim rzeczywisty atak wpłynie na Organizację.
- **Skrzynki pocztowe operacji zabezpieczeń (SecOps):** dedykowane skrzynki pocztowe używane przez zespoły zabezpieczeń do zbierania i analizowania niefiltrowanych wiadomości (zarówno dobrych, jak i złych).

Zaawansowane _zasady dostarczania_ w usłudze Microsoft 365 uniemożliwiają _filtrowanie komunikatów przychodzących w tych konkretnych scenariuszach_ .<sup>\*</sup> Zaawansowane zasady dostarczania zapewniają, że komunikaty w tych scenariuszach osiągną następujące wyniki:

- Filtry w modelu EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender nie podejmują żadnych działań w przypadku tych komunikatów.<sup>\*</sup>
- [Bezgodzinne przeczyszczanie (ZAP)](zero-hour-auto-purge.md) w przypadku spamu i wyłudzania informacji nie podejmuje żadnych działań w przypadku tych wiadomości.<sup>\*\*</sup>
- [Domyślne alerty systemowe](/microsoft-365/compliance/alert-policies#default-alert-policies) nie są wyzwalane dla tych scenariuszy.
- [Funkcja AIR i klastrowanie w Ochrona usługi Office 365 w usłudze Defender](office-365-air.md) ignoruje te komunikaty.
- W szczególności w przypadku symulacji wyłudzania informacji innych firm:
  - [Administracja przesyłania](admin-submission.md) generuje automatyczną odpowiedź z informacją, że wiadomość jest częścią kampanii symulacji wyłudzania informacji i nie stanowi rzeczywistego zagrożenia. Alerty i air nie zostaną wyzwolone. Środowisko przesyłania przez administratora będzie pokazywać te komunikaty jako symulowane zagrożenie.
  - Gdy użytkownik zgłosi komunikat symulacji wyłudzania informacji przy użyciu [komunikatu raportu lub dodatków Wyłudzanie informacji o raporcie](enable-the-report-message-add-in.md), system nie wygeneruje alertu, badania ani zdarzenia. Linki lub pliki nie zostaną zdetonowane, ale komunikat zostanie również wyświetlony na karcie **Komunikaty zgłaszane przez użytkownika** na stronie **Przesłane** .
  - [Bezpieczne linki w Ochrona usługi Office 365 w usłudze Defender](safe-links.md) nie blokują ani nie detonują określonych adresów URL w tych komunikatach w momencie kliknięcia. Adresy URL są nadal opakowane, ale nie są blokowane.
  - [Bezpieczne załączniki w Ochrona usługi Office 365 w usłudze Defender](safe-attachments.md) nie detonują załączników w tych komunikatach.

<sup>\*</sup> Nie można pominąć filtrowania złośliwego oprogramowania.

<sup>\*\*</sup> Możesz pominąć zap dla złośliwego oprogramowania, tworząc zasady ochrony przed złośliwym oprogramowaniem dla skrzynki pocztowej SecOps, gdzie zap dla złośliwego oprogramowania jest wyłączony. Aby uzyskać instrukcje, zobacz [Konfigurowanie zasad ochrony przed złośliwym oprogramowaniem w ramach EOP](configure-anti-malware-policies.md).

Komunikaty identyfikowane przez zaawansowane zasady dostarczania nie są zagrożeniami bezpieczeństwa, dlatego komunikaty są oznaczone przesłonięciami systemu. Administracja środowiska będą pokazywać te komunikaty z powodu zastąpienia systemu **symulacji wyłudzania informacji** lub zastąpienia systemu **skrzynki pocztowej SecOps**. Administratorzy mogą filtrować i analizować te przesłonięcia systemu w następujących środowiskach:

- [Wykrywanie zagrożeń/wykrywanie w czasie rzeczywistym w Ochrona usługi Office 365 w usłudze Defender planie 2](threat-explorer.md): Administracja może filtrować **źródło zastąpienia systemu** i wybierać **symulację wyłudzania informacji** lub **skrzynkę pocztową SecOps**.
- [Strona jednostki Poczty e-mail w Eksploratorze zagrożeń/Wykrywanie w czasie rzeczywistym](mdo-email-entity-page.md): Administracja może wyświetlić komunikat dozwolony przez zasady organizacji przez **skrzynkę pocztową SecOps** lub **symulację wyłudzania informacji** w obszarze **Zastępowanie dzierżawy** w sekcji **Przesłonięcia**.
- [Raport o stanie ochrony przed zagrożeniami](view-email-security-reports.md#threat-protection-status-report): Administracja może filtrować według **wyświetlania danych według zastąpienia systemu** w menu rozwijanym i wybrać opcję wyświetlania komunikatów dozwolonych z powodu zastąpienia systemu symulacji wyłudzania informacji. Aby wyświetlić komunikaty dozwolone przez zastąpienie skrzynki pocztowej SecOps, możesz wybrać **podział wykresu według lokalizacji dostarczania** w menu rozwijanym **Podział wykresu według przyczyny** .
- [Zaawansowane wyszukiwanie zagrożeń w Ochrona punktu końcowego w usłudze Microsoft Defender](../defender-endpoint/advanced-hunting-overview.md): symulacja wyłudzania informacji i przesłonięcia systemu skrzynek pocztowych SecOps będą wyświetlane jako opcje w obszarze OrgLevelPolicy w usłudze EmailEvents.
- [Widoki kampanii](campaigns.md): Administracja może filtrować **źródło zastąpienia systemu** i wybierać **symulację wyłudzania informacji** lub **skrzynkę pocztową SecOps**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zaawansowane dostarczanie** , otwórz pozycję <https://security.microsoft.com/advanceddelivery>.

- Aby nawiązać połączenie z programem PowerShell security & Compliance, zobacz [Connect to Security & Compliance PowerShell (Łączenie z programem PowerShell & zgodności z zabezpieczeniami](/powershell/exchange/connect-to-scc-powershell)).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia:
  - Aby tworzyć, modyfikować lub usuwać skonfigurowane ustawienia w zaawansowanych zasadach dostarczania, musisz być członkiem grupy ról **administratora zabezpieczeń** w **portalu Microsoft 365 Defender** i członkiem grupy ról **Zarządzanie organizacją** w **Exchange Online**.
  - Aby uzyskać dostęp tylko do odczytu do zaawansowanych zasad dostarczania, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md) i [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > Dodanie użytkowników do odpowiedniej roli usługi Azure Active Directory zapewnia użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender _i_ uprawnienia do innych funkcji w usłudze Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Konfigurowanie skrzynek pocztowych Usługi SecOps w zaawansowanych zasadach dostarczania przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  pozycji Zasady współpracy \> **& poczty e-mail** **& Reguły** \> **— zaawansowane** \> dostarczanie zasad zagrożeń w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zaawansowane dostarczanie** , użyj polecenia <https://security.microsoft.com/advanceddelivery>.

2. Na stronie **Zaawansowane dostarczanie** sprawdź, czy wybrano kartę **Skrzynka pocztowa SecOps** , a następnie wykonaj jedną z następujących czynności:
   - Kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**.
   - Jeśli nie ma skonfigurowanych symulacji wyłudzania informacji, kliknij przycisk **Dodaj**.

3. W wyświetlonym wysuwu **Edytuj skrzynki pocztowe SecOps** wprowadź istniejącą skrzynkę pocztową Exchange Online, którą chcesz wyznaczyć jako skrzynkę pocztową SecOps, wykonując jedną z następujących czynności:
   - Kliknij w polu, niech lista skrzynek pocztowych rozpoznać, a następnie wybierz skrzynkę pocztową.
   - Kliknij w polu, aby rozpocząć wpisywanie identyfikatora skrzynki pocztowej (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), a następnie wybierz skrzynkę pocztową (nazwę wyświetlaną) z wyników.

     Powtórz ten krok tyle razy, ile jest to konieczne. Grupy dystrybucyjne są niedozwolone.

     Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

4. Po zakończeniu kliknij przycisk **Zapisz**.

Skonfigurowane wpisy skrzynki pocztowej SecOps są wyświetlane na karcie **Skrzynka pocztowa SecOps** . Aby wprowadzić zmiany, kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** na karcie.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Konfigurowanie symulacji wyłudzania informacji innych firm w zaawansowanych zasadach dostarczania przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  pozycji Zasady współpracy \> **& poczty e-mail** **& Reguły** \> **— zaawansowane** \> dostarczanie zasad zagrożeń w sekcji **Reguły**. Aby przejść bezpośrednio do strony **Zaawansowane dostarczanie** , użyj polecenia <https://security.microsoft.com/advanceddelivery>.

2. Na stronie **Zaawansowane dostarczanie** wybierz kartę **Symulacja wyłudzania informacji** , a następnie wykonaj jedną z następujących czynności:
   - Kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**.
   - Jeśli nie ma skonfigurowanych symulacji wyłudzania informacji, kliknij przycisk **Dodaj**.

3. W wyświetlonym oknie wysuwnym **Edytowanie symulacji wyłudzania informacji innych firm** skonfiguruj następujące ustawienia:

   - **Domena**: rozwiń to ustawienie i wprowadź co najmniej jedną domenę adresu e-mail (na przykład contoso.com), klikając pole, wprowadzając wartość, a następnie naciskając klawisz Enter lub wybierając wartość wyświetlaną poniżej pola. Powtórz ten krok tyle razy, ile jest to konieczne. Możesz dodać maksymalnie 20 wpisów.

     > [!NOTE]
     > Użyj domeny z `5321.MailFrom` adresu (znanego również jako adres **MAIL FROM** , nadawca P1 lub nadawca koperty), która jest używana w transmisji SMTP wiadomości **lub** domenie DomainKeys Identified Mail (DKIM) określonej przez dostawcę symulacji wyłudzania informacji.

   - **Wysyłanie adresu IP**: rozwiń to ustawienie i wprowadź co najmniej jeden prawidłowy adres IPv4, klikając pole, wprowadzając wartość, a następnie naciskając klawisz Enter lub wybierając wartość wyświetlaną poniżej pola. Powtórz ten krok tyle razy, ile jest to konieczne. Możesz dodać maksymalnie 10 wpisów. Prawidłowe wartości to:
     - Pojedynczy adres IP: na przykład 192.168.1.1.
     - Zakres adresów IP: na przykład 192.168.0.1-192.168.0.254.
     - Adres IP CIDR: na przykład 192.168.0.1/25.
   - **Adresy URL symulacji umożliwiające**: rozwiń to ustawienie i opcjonalnie wprowadź określone adresy URL będące częścią kampanii symulacji wyłudzania informacji, których nie należy blokować ani detonować, klikając pole, wprowadzając wartość, a następnie naciskając klawisz Enter lub wybierając wartość wyświetlaną poniżej pola. Możesz dodać maksymalnie 10 wpisów. Aby uzyskać format składni adresu URL, zobacz [Składnia adresu URL listy dozwolonych/zablokowanych dzierżawców](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). Te adresy URL są opakowane w momencie kliknięcia, ale nie są blokowane.

   Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   > [!NOTE]
   > Aby skonfigurować symulację wyłudzania informacji innej firmy w usłudze Advanced Delivery, należy podać następujące informacje:
   >
   > - Co najmniej jedna **domena** z jednego z następujących źródeł:
   >   - Adres `5321.MailFrom` (znany również jako adres MAIL FROM, nadawca P1 lub nadawca koperty).
   >   - Domena DKIM.
   > - Co najmniej jeden **adres IP wysyłania**.
   >
   > Opcjonalnie możesz dołączyć **adresy URL symulacji, aby** upewnić się, że adresy URL w komunikatach symulacji nie są blokowane.
   > Dla każdego pola można określić maksymalnie 10 wpisów.
   > Musi istnieć dopasowanie co najmniej jednej **domeny** i jednego **wysyłającego adresu IP**, ale nie jest utrzymywane żadne skojarzenie między wartościami.

4. Po zakończeniu wykonaj jedną z następujących czynności:
   - **Pierwszy raz**: kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Zamknij**.
   - **Edytuj istniejące**: kliknij przycisk **Zapisz** , a następnie kliknij przycisk **Zamknij**.

Skonfigurowane wpisy symulacji wyłudzania informacji innych firm są wyświetlane na karcie **Symulacja wyłudzania informacji** . Aby wprowadzić zmiany, kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** na karcie.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Dodatkowe scenariusze wymagające obejścia filtrowania

Oprócz dwóch scenariuszy, w których mogą pomóc zaawansowane zasady dostarczania, istnieją inne scenariusze, które mogą wymagać pominięcia filtrowania:

- **Filtry innych firm**: jeśli rekord MX twojej domeny _nie_ wskazuje na Office 365 (komunikaty są najpierw kierowane gdzie indziej), [zabezpieczenia domyślnie](secure-by-default.md) _nie są dostępne_. Jeśli chcesz dodać ochronę, musisz włączyć rozszerzone filtrowanie dla łączników (nazywane również _pomijaniem listy_). Aby uzyskać więcej informacji, zobacz [Manage mail flow using a third-party cloud service with Exchange Online (Zarządzanie przepływem poczty przy użyciu usługi w chmurze innej firmy z Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud)). Jeśli nie chcesz rozszerzonego filtrowania dla łączników, użyj reguł przepływu poczty (znanych również jako reguły transportu), aby pominąć filtrowanie przez firmę Microsoft wiadomości, które zostały już ocenione przez filtrowanie innych firm. Aby uzyskać więcej informacji, zobacz [Używanie reguł przepływu poczty do ustawiania listy SCL w wiadomościach](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **Wyniki fałszywie dodatnie w trakcie przeglądu**: możesz tymczasowo zezwolić niektórym komunikatom, które są nadal analizowane przez firmę Microsoft za pośrednictwem [przesłanych przez administratorów](admin-submission.md) , na zgłaszanie znanych dobrych wiadomości, które są niepoprawnie oznaczone jako złe dla firmy Microsoft (wyniki fałszywie dodatnie). Podobnie jak w przypadku wszystkich zastąpień, _**zdecydowanie zalecamy, aby**_ te dodatki były tymczasowe.

## <a name="security--compliance-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Procedury programu PowerShell dotyczące zgodności & zabezpieczeń dla skrzynek pocztowych SecOps w zaawansowanych zasadach dostarczania

W programie PowerShell security & Compliance podstawowe elementy skrzynek pocztowych SecOps w zaawansowanych zasadach dostarczania to:

- **Zasady zastępowania secops**: kontrolowane przez **\*polecenia cmdlet -SecOpsOverridePolicy** .
- **Reguła zastąpienia SecOps**: kontrolowana przez **\*polecenia cmdlet -SecOpsOverrideRule** .

To zachowanie ma następujące wyniki:

- Najpierw tworzysz zasady, a następnie tworzysz regułę identyfikującą zasady, do których ma zastosowanie reguła.
- Po usunięciu zasad z programu PowerShell zostanie również usunięta odpowiednia reguła.
- Po usunięciu reguły z programu PowerShell odpowiednie zasady nie zostaną usunięte. Odpowiednie zasady należy usunąć ręcznie.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>Konfigurowanie skrzynek pocztowych Usługi SecOps przy użyciu programu PowerShell

Konfigurowanie skrzynki pocztowej SecOps w zaawansowanych zasadach dostarczania w programie PowerShell jest procesem dwuetapowym:

1. Utwórz zasady zastępowania usługi SecOps.
2. Utwórz regułę zastąpienia SecOps określającą zasady, do których ma zastosowanie reguła.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>Krok 1. Tworzenie zasad zastępowania usługi SecOps przy użyciu programu PowerShell

Aby utworzyć zasady zastępowania usługi SecOps, użyj następującej składni:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> Bez względu na określoną wartość Nazwa nazwa zasad będzie mieć wartość _SecOpsOverridePolicy_, więc możesz również użyć tej wartości.

W tym przykładzie są tworzone zasady skrzynki pocztowej SecOps.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>Krok 2. Tworzenie reguły zastąpienia secops przy użyciu programu PowerShell

W tym przykładzie zostanie utworzona reguła skrzynki pocztowej SecOps z określonymi ustawieniami.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> Niezależnie od określonej wartości Nazwa nazwa reguły będzie _secOpsOverrideRule_\<GUID\> , gdzie \<GUID\> jest unikatową wartością identyfikatora GUID (na przykład 6fed4b63-3563-495d-a481-b24a311f8329).

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>Wyświetlanie zasad zastępowania secops przy użyciu programu PowerShell

W tym przykładzie są zwracane szczegółowe informacje o zasadach jednej i tylko skrzynki pocztowej SecOps.

```powershell
Get-SecOpsOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>Wyświetlanie reguł zastępowania secops przy użyciu programu PowerShell

Ten przykład zwraca szczegółowe informacje o regułach zastępowania usługi SecOps.

```powershell
Get-SecOpsOverrideRule
```

Mimo że poprzednie polecenie powinno zwracać tylko jedną regułę, wszystkie reguły oczekujące na usunięcie mogą również zostać uwzględnione w wynikach.

W tym przykładzie zidentyfikowano prawidłową regułę (jedną) i wszystkie nieprawidłowe reguły.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Po zidentyfikowaniu nieprawidłowych reguł można je usunąć za pomocą polecenia cmdlet **Remove-SecOpsOverrideRule** zgodnie z opisem [w dalszej części tego artykułu](#use-powershell-to-remove-secops-override-rules).

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>Modyfikowanie zasad zastępowania usługi SecOps przy użyciu programu PowerShell

Aby zmodyfikować zasady zastępowania secops, użyj następującej składni:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

W tym przykładzie `secops2@contoso.com` dodano zasady zastępowania usługi SecOps.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> Jeśli istnieje skojarzona prawidłowa reguła zastąpienia secops, adresy e-mail w regule również zostaną zaktualizowane.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>Modyfikowanie reguły zastępowania secops przy użyciu programu PowerShell

Polecenie cmdlet **Set-SecOpsOverrideRule** nie modyfikuje adresów e-mail w regule zastępowania SecOps. Aby zmodyfikować adresy e-mail w regule zastępowania secops, użyj polecenia cmdlet **Set-SecOpsOverridePolicy** .

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>Usuwanie zasad zastępowania secops przy użyciu programu PowerShell

W tym przykładzie usunięto zasady skrzynki pocztowej SecOps i odpowiednią regułę.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>Usuwanie reguł zastępowania secops przy użyciu programu PowerShell

Aby usunąć regułę zastąpienia SecOps, użyj następującej składni:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

W tym przykładzie usunięto określoną regułę zastąpienia SecOps.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Procedury programu PowerShell dotyczące zgodności & zabezpieczeń dla symulacji wyłudzania informacji innych firm w zaawansowanych zasadach dostarczania

W programie PowerShell security & Compliance podstawowe elementy symulacji wyłudzania informacji innych firm w zaawansowanych zasadach dostarczania to:

- **Zasady zastępowania symulacji wyłudzania informacji**: kontrolowane przez **\*polecenia cmdlet -PhishSimOverridePolicy** .
- **Reguła zastępowania symulacji wyłudzania informacji**: kontrolowana przez **\*polecenia cmdlet -PhishSimOverrideRule** .
- **Dozwolone (odblokowane) adresy URL symulacji wyłudzania informacji**: kontrolowane przez **\*polecenia cmdlet -TenantAllowBlockListItems** .

To zachowanie ma następujące wyniki:

- Najpierw tworzysz zasady, a następnie tworzysz regułę identyfikującą zasady, do których ma zastosowanie reguła.
- Ustawienia zasad i reguły są modyfikowane oddzielnie.
- Po usunięciu zasad z programu PowerShell zostanie również usunięta odpowiednia reguła.
- Po usunięciu reguły z programu PowerShell odpowiednie zasady nie zostaną usunięte. Odpowiednie zasady należy usunąć ręcznie.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Konfigurowanie symulacji wyłudzania informacji innych firm przy użyciu programu PowerShell

Konfigurowanie symulacji wyłudzania informacji innych firm w programie PowerShell jest procesem wieloetapowym:

1. Utwórz zasady zastępowania symulacji wyłudzania informacji.
2. Utwórz regułę zastąpienia symulacji wyłudzania informacji, która określa:
   - Zasady, do których ma zastosowanie reguła.
   - Źródłowy adres IP komunikatów symulacji wyłudzania informacji.
3. Opcjonalnie należy przypisać tożsamość adresów URL symulacji wyłudzania informacji, które powinny być dozwolone (czyli nie są blokowane ani skanowane).

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>Krok 1. Tworzenie zasad zastępowania symulacji wyłudzania informacji przy użyciu programu PowerShell

Ten przykład tworzy zasady zastępowania symulacji wyłudzania informacji.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Uwaga**: niezależnie od określonej wartości Nazwa nazwa zasad będzie mieć wartość _PhishSimOverridePolicy_, więc równie dobrze możesz użyć tej wartości.

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>Krok 2. Tworzenie reguły zastąpienia symulacji wyłudzania informacji przy użyciu programu PowerShell

Należy stosować następującą składnię:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

Niezależnie od określonej wartości Nazwa nazwa reguły będzie mieć wartość _PhishSimOverrideRule_\<GUID\> , gdzie \<GUID\> jest unikatową wartością identyfikatora GUID (na przykład a0eae53e-d755-4a42-9320-b9c6b55c5011).

Prawidłowy wpis adresu IP to jedna z następujących wartości:

- Pojedynczy adres IP: na przykład 192.168.1.1.
- Zakres adresów IP: na przykład 192.168.0.1-192.168.0.254.
- Adres IP CIDR: na przykład 192.168.0.1/25.

W tym przykładzie zostanie utworzona reguła zastąpienia symulacji wyłudzania informacji z określonymi ustawieniami.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>Krok 3. (Opcjonalnie) Używanie programu PowerShell do identyfikowania adresów URL symulacji wyłudzania informacji w celu zezwolenia

Należy stosować następującą składnię:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

Aby uzyskać szczegółowe informacje na temat składni adresu URL, zobacz [Składnia adresu URL listy dozwolonych/zablokowanych dzierżawców](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

W tym przykładzie dodano adres URL zezwalania na wpis dla określonego adresu URL symulacji wyłudzania informacji innej firmy bez wygaśnięcia.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Wyświetlanie zasad zastępowania symulacji wyłudzania informacji przy użyciu programu PowerShell

Ten przykład zwraca szczegółowe informacje o zasadach zastępowania jedynej symulacji wyłudzania informacji.

```powershell
Get-PhishSimOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Wyświetlanie reguł zastępowania symulacji wyłudzania informacji przy użyciu programu PowerShell

Ten przykład zwraca szczegółowe informacje o regułach zastępowania symulacji wyłudzania informacji.

```powershell
Get-PhishSimOverrideRule
```

Mimo że poprzednie polecenie powinno zwracać tylko jedną regułę, wszystkie reguły oczekujące na usunięcie mogą również zostać uwzględnione w wynikach.

W tym przykładzie zidentyfikowano prawidłową regułę (jedną) i wszystkie nieprawidłowe reguły.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Po zidentyfikowaniu nieprawidłowych reguł można je usunąć za pomocą polecenia cmdlet **Remove-PhishSimOverrideRule** zgodnie z opisem [w dalszej części tego artykułu](#use-powershell-to-remove-phishing-simulation-override-rules).

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>Wyświetlanie dozwolonych wpisów adresu URL symulacji wyłudzania informacji przy użyciu programu PowerShell

Aby wyświetlić dozwolone adresy URL symulacji wyłudzania informacji, uruchom następujące polecenie:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Modyfikowanie zasad zastępowania symulacji wyłudzania informacji przy użyciu programu PowerShell

Aby zmodyfikować zasady zastępowania symulacji wyłudzania informacji, użyj następującej składni:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

Ten przykład wyłącza zasady zastępowania symulacji wyłudzania informacji.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>Modyfikowanie reguł zastępowania symulacji wyłudzania informacji przy użyciu programu PowerShell

Aby zmodyfikować regułę zastępowania symulacji wyłudzania informacji, użyj następującej składni:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

Ten przykład modyfikuje określoną regułę zastępowania symulacji wyłudzania informacji przy użyciu następujących ustawień:

- Dodaj wpis domeny blueyonderairlines.com.
- Usuń wpis adresu IP 192.168.1.55.

Należy pamiętać, że te zmiany nie mają wpływu na istniejące wpisy.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>Modyfikowanie dozwolonych wpisów adresu URL symulacji wyłudzania informacji przy użyciu programu PowerShell

Nie można bezpośrednio modyfikować wartości adresu URL. Możesz [usunąć istniejące wpisy adresu URL](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) i [dodać nowe wpisy adresu URL](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) zgodnie z opisem w tym artykule.

Aby zmodyfikować inne właściwości dozwolonego wpisu adresu URL symulacji wyłudzania informacji (na przykład datę wygaśnięcia lub komentarze), użyj następującej składni:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

Można zidentyfikować wpis, który ma zostać zmodyfikowany przez jego wartości adresu URL (parametr _Wpisy_ ) lub wartość Identity z danych wyjściowych polecenia cmdlet **Get-TenantAllowBlockListItems** ( _parametrUidentyfikatora identyfikatorów_ ).

W tym przykładzie zmodyfikowano datę wygaśnięcia określonego wpisu.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Usuwanie zasad zastępowania symulacji wyłudzania informacji przy użyciu programu PowerShell

W tym przykładzie usunięto zasady zastępowania symulacji wyłudzania informacji i odpowiednią regułę.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Usuwanie reguł zastępowania symulacji wyłudzania informacji przy użyciu programu PowerShell

Aby usunąć regułę zastępowania symulacji wyłudzania informacji, użyj następującej składni:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

W tym przykładzie usunięto określoną regułę zastępowania symulacji wyłudzania informacji.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>Usuwanie dozwolonych wpisów adresu URL symulacji wyłudzania informacji przy użyciu programu PowerShell

Aby usunąć istniejący wpis adresu URL symulacji wyłudzania informacji, użyj następującej składni:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

Można zidentyfikować wpis, który ma zostać zmodyfikowany przez jego wartości adresu URL (parametr _Wpisy_ ) lub wartość Identity z danych wyjściowych polecenia cmdlet **Get-TenantAllowBlockListItems** ( _parametrUidentyfikatora identyfikatorów_ ).

W tym przykładzie zmodyfikowano datę wygaśnięcia określonego wpisu.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
