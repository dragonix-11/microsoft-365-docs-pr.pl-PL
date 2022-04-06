---
title: Wprowadzenie do zgodności w komunikacji
description: Skonfiguruj zasady zgodności komunikacji, aby skonfigurować komunikację użytkowników do przeglądu.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d9d418cee35976e621c173b3563b04ee8bdce7ca
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595309"
---
# <a name="get-started-with-communication-compliance"></a>Wprowadzenie do zgodności w komunikacji

Za pomocą zasad zgodności komunikacji możesz identyfikować komunikację użytkowników w celu weryfikacji przez wewnętrznych lub zewnętrznych recenzentów. Aby uzyskać więcej informacji na temat tego, jak zasady zgodności komunikacji mogą ułatwić monitorowanie komunikacji w organizacji[, zobacz Zasady](communication-compliance.md) zgodności komunikacji w Microsoft 365. Jeśli chcesz sprawdzić, jak firma Contoso szybko skonfigurowała zasady zgodności komunikacji w celu monitorowania nieodpowiedniej zawartości w korespondencji Microsoft Teams, Exchange Online i Yammer, zapoznaj się z analizą [przypadku.](communication-compliance-case-study.md)

## <a name="subscriptions-and-licensing"></a>Subskrypcje i licencjonowanie

Przed rozpoczęciem pracy ze zgodnością komunikacji należy potwierdzić Microsoft 365 [subskrypcji](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) usługi i wszelkich dodatków. Aby uzyskać dostęp do zgodności komunikacji i korzystać z nich, twoja organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- Microsoft 365 E5/A5/F5/G5 (wersja płatna lub próbna)
- Microsoft 365 E3/A3/F3/G5 + Microsoft 365 E5 zgodności ze standardem Microsoft 365 E5/A5/F5/G5
- Microsoft 365 E3/A3/F3/G5 + Microsoft 365 E5/A5/F5/G5 Zarządzanie ryzykiem w ramach niejawnego programu testów
- Office 365 Enterprise E5 (płatna lub próbna)
- Office 365 A5 (płatna lub próbna)
- Office 365 Enterprise E3 + Office 365 Advanced Compliance (nie jest już dostępna dla nowych subskrypcji, zobacz uwagę)

Użytkownikom uwzględnionym w zasadach zgodności komunikacji należy przypisać jedną z powyższych licencji. Aby uzyskać więcej informacji na temat subskrypcji i licencjonowania, [Microsoft 365 wskazówki dotyczące zabezpieczeń & zgodnością](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Zgodność komunikacji jest obecnie dostępna w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi Azure. Aby sprawdzić, czy zgodność komunikacji jest obsługiwana przez Twoją organizację, zobacz Dostępność usługi [Azure dependency według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

Jeśli nie masz jeszcze planu Office 365 Enterprise E5 i chcesz wypróbować zgodność komunikacji, możesz dodać usługę [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji lub utworzyć konto w celu wypróbowania usługi Office 365 Enterprise [](https://www.microsoft.com/microsoft-365/enterprise) E5.

> [!NOTE]
> Office 365 Advanced Compliance jest już sprzedawana jako subskrypcja autonomiczna. Gdy wygasają bieżące subskrypcje, klienci powinni przejść do jednej z powyższych subskrypcji, która zawiera takie same lub dodatkowe funkcje zgodności.

## <a name="recommended-actions-preview"></a>Zalecane akcje (wersja zapoznawcza)

Zalecane działania mogą ułatwić Twojej organizacji rozpoczynanie pracy z możliwościami zgodności komunikacji i wyekspować istniejące zasady. Na stronie **Zasady znajdują się zalecane** akcje, które dostarczają szczegółowych informacji i podsumowują typy informacji poufnych oraz nieodpowiednie działania dotyczące zawartości w komunikacji w organizacji. Szczegółowe informacje klasyfikacja [danych](data-classification-overview.md) i stosowanie etykiet wrażliwości, etykiet przechowywania oraz klasyfikacja typów informacji poufnych. Te szczegółowe informacje nie obejmują żadnych danych umożliwiających identyfikację użytkownika (PII) dla użytkowników w organizacji.

![Zalecane działania dotyczące zgodności komunikacji.](../media/communication-compliance-recommended-actions.png)

Aktywność w wiadomościach zawierających nieodpowiednią zawartość jest agregowana przez typ klasyfikatora z istniejących zasad, które używają nieodpowiedniego szablonu zawartości lub zasad niestandardowych, które używają klasyfikatorów dla nieodpowiedniej zawartości.[](/microsoft-365/compliance/communication-compliance-policies#classifiers) Badanie alertów dla tych wiadomości na pulpicie nawigacyjnym alertów dotyczących zasad.

Działania dotyczące [typów informacji poufnych](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) są wykrywane w wiadomościach objętych istniejącymi zasadami i w przypadku wiadomości, które nie są objęte istniejącymi zasadami. Szczegółowe informacje są agregowane dla wszystkich typów informacji poufnych, w tym tych, które nie zostały wcześniej zdefiniowane przez organizację w istniejących zasadach zgodności komunikacji. Skorzystaj z tych informacji, aby utworzyć nowe zasady zgodności komunikacji lub zaktualizować istniejące zasady.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Krok 1 (wymagany): Włączanie uprawnień do zgodności komunikacji

> [!IMPORTANT]
> Po skonfigurowaniu grup ról może upłynąć do 30 minut, aby uprawnienia grupy ról dotyczyły przypisanych użytkowników w organizacji.

Do konfigurowania początkowych uprawnień w celu zarządzania funkcjami zgodności komunikacji jest używanych sześć grup ról. Aby zapewnić **zgodność komunikacji** jako opcję menu w programie Centrum zgodności platformy Microsoft 365 i kontynuować te kroki konfiguracji, musisz mieć przypisaną jedną z następujących ról lub grup ról:

- Azure Active Directory [*administrator globalny*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*administratora*](/azure/active-directory/roles/permissions-reference#compliance-administrator) zgodności
- Centrum zgodności platformy Microsoft 365 [*ról Zarządzanie*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) organizacją
- Centrum zgodności platformy Microsoft 365 [*ról Administrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) zgodności
- *Communication Compliance* role group
- *Grupa ról Administrator zgodności komunikacji*

Członkowie następujących ról mają te same uprawnienia rozwiązania zawarte w grupie ról Administrator *zgodności* komunikacji:

- Azure Active Directory *administrator globalny*
- Azure Active Directory *administratora zgodności*
- Centrum zgodności platformy Microsoft 365 *zarządzanie organizacją*
- Centrum zgodności platformy Microsoft 365 *zgodności*

> [!IMPORTANT]
> Upewnij się, że w grupach ról Zgodność z komunikacją lub Administrator  zgodności komunikacji (w zależności od wybranej opcji) zawsze jest co najmniej jeden użytkownik, aby konfiguracja zgodności komunikacji nie była dostępna w scenariuszu "zero administratora", jeśli określone osoby opuszczają Twoją organizację.

W zależności od tego, jak chcesz zarządzać zasadami i alertami zgodności komunikacji, konieczne będzie przypisanie użytkowników do określonych grup ról w celu zarządzania różnymi zestawami funkcji zgodności komunikacji. Użytkownikom z różnymi zakresami obowiązków w zakresie zgodności można przypisać określone grupy ról w celu zarządzania różnymi obszarami funkcji zgodności komunikacji. Możesz także przypisać wszystkie konta użytkowników dla wyznaczonych administratorów, analityków, osób oglądających i osoby przeglądowe do grupy ról *Zgodność* z komunikacją. Korzystaj z jednej lub wielu grup ról, aby jak najlepiej dopasować się do wymagań zarządzania zgodnością.

Podczas konfigurowania zgodności komunikacji i zarządzania zgodnością wybierz jedną z tych opcji grupy ról rozwiązania:

| Rola | Uprawnienia roli |
|:-----|:-----------------|
| **Zgodność komunikacji** | Ta grupa ról pozwala zarządzać zgodnością komunikacji dla organizacji w jednej grupie. Dodając wszystkie konta użytkowników przeznaczone dla wyznaczonych administratorów, analityków, osób oglądających i wyeks odpowiednie osoby, możesz skonfigurować uprawnienia do zgodności komunikacji w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień zgodności komunikacji. Ta konfiguracja jest najprostszym sposobem szybkiego rozpoczęcia pracy ze zgodnością komunikacji i dobrze pasuje do organizacji, które nie potrzebują osobnych uprawnień zdefiniowanych dla osobnych grup użytkowników. Użytkownicy, którzy tworzą zasady jako administrator zgodności komunikacji, muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online.|
| **Administrator zgodności komunikacji** | Ta grupa ról umożliwia wstępne skonfigurowanie zgodności komunikacji, a później podział administratorów zgodności komunikacji na zdefiniowaną grupę. Użytkownicy przypisani do tej grupy ról mogą tworzyć, odczytywać, aktualizować i usuwać zasady zgodności komunikacji, ustawienia globalne i przypisania grup ról. Użytkownicy przypisani do tej grupy ról nie mogą wyświetlać alertów o wiadomościach. Użytkownicy, którzy tworzą zasady jako administrator zgodności komunikacji, muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online.|
| **Analityk zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak analitycy zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać zasady, do których są przypisywani jako recenzenty, wyświetlać metadane wiadomości (a nie zawartość wiadomości), eskalacji do dodatkowych recenzentów lub wysyłać powiadomienia do użytkowników. Analitycy nie mogą rozstrzygić oczekujących alertów. |
| **Działania w zakresie zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak uprawnienia do zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać metadane i zawartość wiadomości, eskalacji do dodatkowych recenzentów, eskalować do sprawy Advanced eDiscovery, wysyłać powiadomienia do użytkowników i rozwiązywać alert. |
| **Przeglądarka zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą zarządzać raportami do komunikacji. Użytkownicy przypisani do tej grupy ról mają dostęp do wszystkich widżetów raportowania na stronie głównej zgodności komunikacji i mogą wyświetlać wszystkie raporty zgodności komunikacji. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Opcja 1. Przypisanie wszystkich użytkowników zgodności do grupy ról Zgodności komunikacji

1. Zaloguj się [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) przy użyciu poświadczeń dla konta administratora w Microsoft 365 organizacji.

2. W Centrum zgodności &amp; zabezpieczeń przejdź **do uprawnień.** Wybierz link, aby wyświetlić role i zarządzać nimi w Office 365.

3. Wybierz *grupę ról Zgodność komunikacji* , a następnie wybierz **pozycję Edytuj grupę ról**.

4. Wybierz **pozycję Wybierz członków** w lewym okienku nawigacji, a następnie wybierz pozycję **Edytuj**.

5. Wybierz **pozycję** Dodaj, a następnie zaznacz pole wyboru dla wszystkich użytkowników, których chcesz dodać do grupy ról *Zgodność* komunikacji.

6. Wybierz **pozycję Dodaj**, a następnie pozycję **Gotowe**.

7. Wybierz **pozycję Zapisz** , aby dodać użytkowników do grupy ról. Wybierz **pozycję Zamknij** , aby ukończyć procedurę

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Opcja 2. Przypisywanie użytkowników do konkretnych grup ról zgodności komunikacji

Użyj tej opcji, aby przypisać użytkowników do określonych grup ról w celu segmentowania zakresu dostępu do zgodności komunikacji i obowiązków między różnymi użytkownikami w organizacji.

1. Zaloguj się do [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w Twojej organizacji usługi Microsoft 365, a następnie przejdź do strony **Uprawnienia**</a>.

2. Wybierz link, aby wyświetlić role i zarządzać nimi w Office 365.

3. Wybierz jedną z grup ról zgodności komunikacji, a następnie wybierz pozycję **Edytuj grupę ról**.

4. Wybierz **pozycję Wybierz członków** w lewym okienku nawigacji, a następnie wybierz pozycję **Edytuj**.

5. Wybierz **pozycję** Dodaj, a następnie zaznacz pole wyboru dla wszystkich użytkowników, których chcesz dodać do grupy ról.

6. Wybierz **pozycję Dodaj**, a następnie pozycję **Gotowe**.

7. Wybierz **pozycję Zapisz** , aby dodać użytkowników do grupy ról.

8. Wybierz następną grupę ról zgodności komunikacji, a następnie powtórz kroki od 4 do 7 dla każdej wymaganej grupy ról.

9. Wybierz **pozycję Zamknij** , aby ukończyć procedurę.

Aby uzyskać więcej informacji o grupach ról i uprawnieniach, zobacz [Uprawnienia w Centrum zgodności](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Krok 2 (wymagany): Włączanie dziennika inspekcji

Zgodność komunikacji wymaga dzienników inspekcji w celu pokazania alertów i śledzenia działań naprawczych realizowanych przez recenzentów. Dzienniki inspekcji są podsumowaniem wszystkich działań skojarzonych ze zdefiniowanymi zasadami organizacji lub w dowolnym momencie, gdy zmienią się zasady zgodności komunikacji.

Inspekcja jest domyślnie włączona Microsoft 365 organizacji. Niektóre organizacje mogą wyłączyć inspekcję z określonych powodów. Jeśli w Twojej organizacji inspekcja jest wyłączona, może to być spowodowane tym, że inny administrator wyłączył ją. Zalecamy potwierdzenie, że po wykonaniu tego kroku można ponownie włączyć inspekcję.

Aby uzyskać instrukcje krok po kroku dotyczące dotyczące włączanie inspekcji, zobacz Włączanie lub wyłączanie przeszukiwania [dziennika inspekcji](turn-audit-log-search-on-or-off.md). Po włączeniu inspekcji jest wyświetlany komunikat informujący, że dziennik inspekcji jest przygotowywany i że po upływie kilku godzin od zakończenia przygotowywania można uruchomić wyszukiwanie. Wystarczy wykonać tę czynność tylko raz. Aby uzyskać więcej informacji na temat korzystania z dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Krok 3 (opcjonalnie): Konfigurowanie grup na celu zapewnienie zgodności z komunikacją

 Podczas tworzenia zasad zgodności komunikacji określa się, kto przegląda komunikację i kto go przegląda. Te zasady będą używać adresów e-mail do identyfikowania osób lub grup osób. Aby uprościć konfigurację, możesz utworzyć grupy dla osób przeglądających komunikację i grupy dla osób przeglądających te wiadomości. Jeśli korzystasz z grup, może być ich kilka. Może to być na przykład w sytuacji, gdy chcesz monitorować komunikację między dwiema różnymi grupami osób lub określić grupę, która nie będzie nadzorowana.

Skorzystaj z poniższego wykresu, aby ułatwić konfigurowanie grup w organizacji pod celu stosowania zasad zgodności komunikacji:

| **Członek zasad** | **Obsługiwane grupy** | **Nieobsługiwane grupy** |
|:-----|:-----|:-----|
|Nadzór nad użytkownikami <br> Wykluczeni użytkownicy | Grupy dystrybucyjne <br> Grupy Microsoft 365 | Dynamiczne grupy dystrybucyjne <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty <br> Microsoft 365 grup z członkostwem dynamicznym |
| Recenzentzy | Brak | Grupy dystrybucyjne <br> Dynamiczne grupy dystrybucyjne <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty |

Po przypisaniu grupy *dystrybucyjnej* do zasad zasady monitoruje wszystkie wiadomości e-mail i czaty Teams wiadomości od poszczególnych użytkowników *w grupie dystrybucyjnej*. Po przypisaniu grupy *Microsoft 365* w zasadach zasady monitoruje wszystkie wiadomości e-mail i czaty Teams wysyłane do grupy Microsoft 365*, *a* nie poszczególne wiadomości e-mail i czaty otrzymane przez poszczególnych członków grupy. Korzystanie z grup dystrybucyjnych w zasadach zgodności komunikacji jest zalecane, aby poszczególne wiadomości e-mail i Teams czaty od poszczególnych użytkowników są automatycznie monitorowane.

Jeśli jesteś organizacją z wdrożeniem lokalnym programu Exchange lub zewnętrznym dostawcą poczty e-mail i chcesz monitorować czaty programu Microsoft Teams dla użytkowników, musisz utworzyć grupę dystrybucyjną dla użytkowników z lokalnymi lub zewnętrznymi skrzynkami pocztowymi do monitorowania. W dalszej części tych kroków przypiszesz tę grupę dystrybucyjną jako wybór **Użytkownicy** i grupy nadzorowane w kreatorze zasad. Aby uzyskać więcej informacji o wymaganiach i ograniczeniach dotyczących włączania magazynu opartego na chmurze i obsługi Teams użytkowników lokalnych, zobacz Wyszukiwanie danych czatu Teams użytkowników [lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

Aby zarządzać nadzorowanych użytkowników w dużych organizacjach przedsiębiorstwa, może być konieczne monitorowanie wszystkich użytkowników w dużych grupach. Za pomocą programu PowerShell możesz skonfigurować grupę dystrybucyjną dla globalnych zasad zgodności komunikacji dla przypisanej grupy. Dzięki temu możesz monitorować tysiące użytkowników za pomocą jednej zasady i aktualizować zasady zgodności komunikacji, gdy nowi pracownicy dołączają do organizacji.

1. Utwórz [dedykowaną](/powershell/module/exchange/new-distributiongroup) grupę dystrybucyjną dla globalnych zasad zgodności komunikacji o następujących właściwościach: Upewnij się, że ta grupa dystrybucyjna nie jest używana do innych celów ani do Office 365 usług firmy Microsoft.

    - **MemberDepartRestriction = Closed**. Zapewnia, że użytkownicy nie mogą sami usuwać się z grupy dystrybucyjnej.
    - **MemberJoinRestriction = Closed**. Zapewnia, że użytkownicy nie mogą dodawać siebie do grupy dystrybucyjnej.
    - **ModerationEnabled = True**. Zapewnia, że wszystkie wiadomości wysłane do tej grupy podlegają zatwierdzaniu i że grupa nie jest używana do komunikacji poza konfiguracją zasad zgodności komunikacji.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Wybierz nieużywany atrybut [Exchange niestandardowego](/Exchange/recipients/mailbox-custom-attributes), aby śledzić użytkowników dodawanych do zasad zgodności komunikacji w organizacji.

3. Uruchom następujący skrypt programu PowerShell w harmonogramie cyklicznym, aby dodać użytkowników do zasad zgodności komunikacji:

    ```PowerShell
    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
      Write-Host "Adding" $M.DisplayName
      Add-DistributionGroupMember -Identity <your group name> -Member $M.DistinguishedName -ErrorAction SilentlyContinue
      Set-Mailbox -Identity $M.Alias -<your custom attribute name> SRAdded
      $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."
    ```

Aby uzyskać więcej informacji na temat konfigurowania grup, zobacz:

- [Tworzenie grup dystrybucyjnych i zarządzanie nimi](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Omówienie Grupy Microsoft 365](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Krok 4 (opcjonalnie): sprawdzanie, czy Yammer jest w trybie natywnym

W trybie natywnym Yammer użytkownicy znajdują się w usłudze Azure Active Directory (Azure AD), wszystkie grupy są Office 365 grupy, a wszystkie pliki są przechowywane w usłudze SharePoint Online. Dzierżawa Yammer musi być w trybie natywnym, aby zasady zgodności komunikacji były skanowane i identyfikowane ryzykownych konwersacji w wiadomościach prywatnych i konwersacjach społeczności w Yammer.

Aby uzyskać więcej informacji na temat konfigurowania Yammer w trybie natywnym, zobacz:

- [Omówienie Yammer natywnego w programie Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Konfigurowanie sieci Yammer w trybie natywnym dla Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Krok 5 (wymagany). Tworzenie zasad zgodności komunikacji

>[!IMPORTANT]
>Tworzenie zasad zgodności komunikacji i zarządzanie nimi za pomocą programu PowerShell nie jest obsługiwane. Aby utworzyć te zasady i zarządzać nimi, musisz użyć kontrolek zarządzania zasadami w Microsoft 365 [rozwiązania do zgodności komunikacji](https://compliance.microsoft.com/supervisoryreview).

>[!TIP]  
>Chcesz uzyskać szczegółowe informacje dotyczące konfigurowania nowych zasad zgodności komunikacji i rozwiązywania problemów z alertem? Obejrzyj ten [15-minutowy](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) klip wideo, aby zobaczyć, jak zasady zgodności komunikacji mogą ułatwić wykrywanie nieodpowiednich wiadomości, badanie potencjalnych naruszeń i rozwiązywanie problemów ze zgodnością.

1. Zaloguj się do [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w Twojej Microsoft 365 organizacji.

2. W Centrum zgodności platformy Microsoft 365 wybierz pozycję **Zgodność komunikacji**.

3. Wybierz **kartę** Zasady.

4. Wybierz **pozycję Utwórz zasady** , aby utworzyć i skonfigurować nowe zasady na podstawie szablonu lub aby utworzyć i skonfigurować zasady niestandardowe.

    Jeśli wybierzesz szablon zasad w celu utworzenia zasad, możesz:

    - Potwierdź lub zaktualizuj nazwę zasad. Po utworzeniu zasad nie można zmienić nazw zasad.

    - Wybierz użytkowników lub grupy nadzorowane, w tym wybieranie użytkowników lub grup, które chcesz wykluczyć. W przypadku używania szablonu konfliktu zainteresowań należy wybrać dwóch grup lub dwóch użytkowników do monitorowania komunikacji wewnętrznej.

    - Wybierz recenzentów zasad. Recenzentzy to poszczegrzy użytkownicy, a wszyscy recenzenty muszą mieć skrzynki pocztowe hostowane w Exchange Online. Recenzenty dodani tutaj to recenzentzy, których możesz wybrać podczas eskalowania alertu w przepływie pracy badania i rozwiązywania problemów. Po dodaniu recenzentów do zasad automatycznie otrzymuje on wiadomość e-mail z powiadomieniem o przypisaniu do zasad i linkami do informacji o procesie sprawdzania.

    - Wybierz pole ograniczonego warunku, zazwyczaj słownik informacji poufnych lub słownik słów kluczowych do zastosowania do zasad.

    > [!NOTE]
    > Jeśli chcesz włączyć optyczne rozpoznawanie znaków [(OCR, Optical Character Recognition)](communication-compliance-policies.md#optical-character-recognition-ocr) w celu skanowania osadzonych lub dołączonych obrazów w wiadomościach pod poszukiwaniu drukowanego lub napisanego ręcznie tekstu zgodnego z warunkami zasad,  >  wybierz pozycję Dostosuj zasadyKodowania i wartości procentowe, a następnie włącz opcję Wyodrębnij drukowany lub odręczny tekst z obrazów do **oceny.**

    Jeśli zdecydujesz się utworzyć zasady niestandardowe za pomocą kreatora zasad, możesz:

    - Nadaj zasadom nazwę i opis. Po utworzeniu zasad nie można zmienić nazw zasad.

    - Wybierz użytkowników lub grupy nadzorowane, w tym wszystkich użytkowników w organizacji, konkretnych użytkowników i grup lub innych użytkowników i grup, które chcesz wykluczyć.

    - Wybierz recenzentów zasad. Recenzentzy to poszczegrzy użytkownicy, a wszyscy recenzenty muszą mieć skrzynki pocztowe hostowane w Exchange Online. Recenzenty dodani tutaj to recenzentzy, których możesz wybrać podczas eskalowania alertu w przepływie pracy badania i rozwiązywania problemów. Po dodaniu recenzentów do zasad automatycznie otrzymuje on wiadomość e-mail z powiadomieniem o przypisaniu do zasad i linkami do informacji o procesie sprawdzania.

    - Wybierz kanały komunikacji do zeskanowania, w tym kanały Exchange, Microsoft Teams, Yammer lub Skype dla firm. Możesz również skanować źródła innych firm, jeśli w programie Microsoft 365.

    - Wybierz kierunek komunikacji, który chcesz monitorować, w tym komunikację przychodzący, wychodzącą lub wewnętrzną.

    - Definiowanie warunków zasad zgodności [komunikacji](communication-compliance-policies.md#ConditionalSettings). Możesz wybrać adres wiadomości, słowo kluczowe, typy plików i rozmiar zgodne warunki.

    - Wybierz, czy chcesz uwzględnić typy informacji poufnych. W tym kroku możesz wybrać domyślne i niestandardowe typy informacji poufnych. Wybierz z istniejących niestandardowych typów informacji poufnych lub niestandardowe słowniki słów kluczowych w kreatorze zasad zgodności komunikacji. W razie potrzeby możesz utworzyć te elementy przed uruchomieniem kreatora. Za pomocą kreatora zasad zgodności komunikacji możesz również tworzyć nowe typy informacji poufnych.

    - Wybierz, czy chcesz włączyć klasyfikatory. Klasyfikatory mogą wykrywać nieodpowiedni język i obrazy wysyłane lub odbierane w treści wiadomości e-mail lub innych typów tekstu. Możesz wybrać następujące wbudowane klasyfikatory *: Zagrożenia*, *Profanity**,* Molestowanie *kierowane,* Obrazy dorosłego, *Obrazy* Ciesieli i *Obrazy wąsów*.

    - Włącz [optyczne rozpoznawanie znaków (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) w celu skanowania osadzonych lub dołączonych obrazów w wiadomościach pod poszukiwaniu drukowanego lub napisanego ręcznie tekstu, które są zgodne z warunkami zasad. W przypadku zasad niestandardowych w zasadach należy skonfigurować co najmniej jedno lub więcej ustawień warunkowych skojarzonych z tekstem, słowami kluczowymi, klasyfikatorami lub typami informacji poufnych, aby umożliwić wybór optycznego skanowania znaków.

    - Zdefiniuj procent wiadomości do przejrzenia.

    - Przejrzyj wybrane zasady i utwórz zasady.

5. Wybierz **pozycję Utwórz zasady** podczas korzystania z szablonów lub **Prześlij** w przypadku korzystania z kreatora zasad niestandardowych.

6. Strona **Twoje zasady zostały utworzone,** zawiera wskazówki dotyczące tego, kiedy zasady zostaną aktywowane i która komunikacja zostanie przechwycona.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>Krok 6 (opcjonalnie): Aktualizowanie granic zgodności w celu zapewnienia zgodności z zasadami zgodności komunikacji

[](/microsoft-365/compliance/set-up-compliance-boundaries) Granice zgodności tworzą logiczne granice w organizacji, które kontrolują lokalizacje zawartości użytkowników (takie jak skrzynki pocztowe, konta OneDrive i witryny SharePoint), które menedżerowie zbierania elektronicznych materiałów dowodowych mogą wyszukiwać.

Jeśli skonfigurowano granice zgodności w organizacji, należy zaktualizować granice zgodności, aby umożliwić określonym użytkownikom dostęp do skrzynek pocztowych, które obsługują zasady zgodności komunikacji. Aby działania w zakresie zarządzania zasadami oraz działań w zakresie badań i rozwiązywania problemów działały poprawnie, musisz zezwolić na dostęp administratorom zgodności komunikacji i recenzentom zgodności komunikacji.

Aby zezwolić na dostęp administratorom zgodności komunikacji i recenzentom, uruchom następujące polecenia programu PowerShell. Te polecenia trzeba uruchomić tylko raz, nawet jeśli w przyszłości dodasz nowe zasady zgodności komunikacji:

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

Aby uzyskać więcej informacji na temat składni polecenia cmdlet, zobacz [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>Krok 7 (opcjonalnie): tworzenie szablonów z powiadomieniami i konfigurowanie anonimizacji użytkowników

Jeśli chcesz mieć możliwość odpowiadania na alert zasad przez wysłanie powiadomienia z przypomnieniem do skojarzonego użytkownika, musisz utworzyć w organizacji co najmniej jeden szablon powiadomienia. Pola szablonu powiadomień można edytować przed ich wysłaniem w ramach procesu rozwiązywania problemów z alertami i zaleca się utworzenie niestandardowego szablonu powiadomienia dla poszczególnych zasad zgodności komunikacji.

Możesz również włączyć anonimizowanie wyświetlanych nazw użytkowników podczas badania dopasowania zasad i podejmowania działań na wiadomościach.

1. Zaloguj się do [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w Twojej Microsoft 365 organizacji.

2. Na stronie Centrum zgodności platformy Microsoft 365 do tematu **Zgodność komunikacji**.

3. Aby skonfigurować anonimizacja nazw użytkowników, wybierz **kartę Prywatność** .

4. Aby włączyć anonimizację, wybierz **pozycję Pokaż wersje zanonimizowanych nazw użytkowników**.

5. Wybierz **Zapisz**.

6. Przejdź do karty **Szablony z powiadomieniami** , a następnie wybierz **pozycję Utwórz szablon powiadomienia**.

7. Na stronie **Modyfikowanie szablonu powiadomienia** wypełnij następujące pola:

    - Nazwa szablonu (wymagany)
    - Wyślij z (wymagane)
    - DW i UDW (opcjonalne)
    - Temat (wymagany)
    - Treść wiadomości (wymagany)

8. Wybierz **pozycję Zapisz** , aby utworzyć i zapisać szablon powiadomienia.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>Krok 8 (opcjonalnie): Testowanie zasad zgodności komunikacji

Po utworzeniu zasad zgodności komunikacji warto je przetestować, aby upewnić się, że zdefiniowane warunki są poprawnie wymuszane przez zasady. Warto również przetestować zasady ochrony przed [utratą danych (DLP](create-test-tune-dlp-policy.md) ), jeśli zasady zgodności komunikacji zawierają typy informacji poufnych. Upewnij się, że masz czas na aktywowanie zasad, aby przechwycić informacje, które chcesz przetestować.

Wykonaj poniższe czynności, aby przetestować swoje zasady zgodności komunikacji:

1. Otwórz klienta poczty e-mail, Microsoft Teams lub Yammer po zalogowaniu się jako nadzorowany użytkownik zdefiniowany w zasadach, które chcesz przetestować.

2. Wyślij wiadomość e-mail, Microsoft Teams czat lub Yammer wiadomość, która spełnia kryteria określone w zasadach zgodności komunikacji. Ten test może być słowem kluczowym, rozmiarem załącznika, domeną itp. Upewnij się, że skonfigurowane w zasadach ustawienia warunkowe są zbyt restrykcyjne, czy zbyt lenisz.

    > [!NOTE]
    > Pełne przetwarzanie zasad w wiadomościach e-mail może potrwać do 24 godzin. Pełne przetwarzanie komunikacji na Microsoft Teams platformach Microsoft Teams, Yammer i innych firm może potrwać do 48 godzin.

3. Zaloguj się Microsoft 365 jako recenzent wskazany w zasadach zgodności komunikacji. Przejdź do **complianceAlerts**  >  komunikacji, aby wyświetlić alerty dotyczące zasad.

4. Zaradcze działania alertu za pomocą kontrolek zaradczych i sprawdzanie, czy alert został poprawnie rozwiązany.

## <a name="next-steps"></a>Następne kroki

Po zakończeniu tych czynności w celu utworzenia pierwszych zasad zgodności komunikacji zaczniesz otrzymywać alerty ze wskaźników aktywności po 24–48 godzinach. Skonfiguruj dodatkowe zasady zgodnie z potrzebami, używając wskazówek w kroku 5 tego artykułu.

Aby dowiedzieć się więcej o badanie alertów zgodności komunikacji, zobacz [Badanie i rozwiązywanie problemów z alertami zgodności komunikacji](communication-compliance-investigate-remediate.md).

Aby być na bieżąco z najnowszymi aktualizacjami zgodności komunikacji, **wybierz pozycję Co** nowego [](https://compliance.microsoft.com/) w zgodności komunikacyjnej dla organizacji.
