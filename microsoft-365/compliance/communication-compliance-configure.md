---
title: Wprowadzenie do zgodności w komunikacji
description: Skonfiguruj zasady zgodności komunikacji, aby skonfigurować komunikację użytkowników do przeglądu.
keywords: Microsoft 365, Microsoft Purview, zgodność, zgodność z komunikacją
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
ms.openlocfilehash: c4e28c91cc7e7fe441d000553e9099ad39420991
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317079"
---
# <a name="get-started-with-communication-compliance"></a>Wprowadzenie do zgodności w komunikacji

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Użyj zasad zgodności komunikacji, aby zidentyfikować komunikację użytkowników do zbadania przez wewnętrznych lub zewnętrznych recenzentów. Aby uzyskać więcej informacji na temat sposobu, w jaki zasady zgodności komunikacji mogą pomóc w monitorowaniu komunikacji w organizacji, zobacz [zasady zgodności komunikacji](communication-compliance.md). Jeśli chcesz sprawdzić, jak firma Contoso szybko skonfigurowała zasady zgodności komunikacji w celu monitorowania nieodpowiedniej zawartości w Microsoft Teams, Exchange Online i Yammer komunikacji, zapoznaj się z tą [analizą przypadku](communication-compliance-case-study.md).

## <a name="subscriptions-and-licensing"></a>Subskrypcje i licencjonowanie

Przed rozpoczęciem komunikacji należy potwierdzić [swoją subskrypcję Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) i wszelkie dodatki. Aby uzyskać dostęp do zgodności z komunikacją i korzystać z niej, organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- subskrypcja Microsoft 365 E5/A5/F5/G5 (wersja płatna lub próbna)
- subskrypcja Microsoft 365 E3/A3/F3/G5 + dodatek zgodności Microsoft 365 E5/A5/F5/G5
- subskrypcja Microsoft 365 E3/A3/F3/G5 + dodatek Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- subskrypcja Office 365 Enterprise E5 (wersja płatna lub próbna)
- subskrypcja Office 365 A5 (wersja płatna lub próbna)
- Office 365 Enterprise subskrypcję E3 + dodatek Office 365 Advanced Compliance (nie jest już dostępny dla nowych subskrypcji, zobacz uwaga)

Użytkownikom uwzględnionym w zasadach zgodności komunikacji należy przypisać jedną z powyższych licencji. Aby uzyskać więcej informacji na temat subskrypcji i licencjonowania, zobacz [Microsoft 365 wskazówki dotyczące zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Zgodność z komunikacją jest obecnie dostępna w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi platformy Azure. Aby sprawdzić, czy zgodność komunikacji jest obsługiwana w organizacji, zobacz [Dostępność zależności platformy Azure według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

Jeśli nie masz istniejącego planu Office 365 Enterprise E5 i chcesz wypróbować zgodność z komunikacją, możesz [dodać Microsoft 365](/office365/admin/try-or-buy-microsoft-365) do istniejącej subskrypcji lub [zarejestrować się w wersji próbnej](https://www.microsoft.com/microsoft-365/enterprise) Office 365 Enterprise E5.

> [!NOTE]
> Office 365 Advanced Compliance nie jest już sprzedawana jako subskrypcja autonomiczna. Po wygaśnięciu bieżących subskrypcji klienci powinni przejść do jednej z powyższych subskrypcji, która zawiera te same lub dodatkowe funkcje zgodności.

## <a name="recommended-actions-preview"></a>Zalecane akcje (wersja zapoznawcza)

Zalecane akcje mogą pomóc organizacji rozpocząć pracę z funkcjami zgodności komunikacji i jak najlepiej wykorzystać istniejące zasady. Zalecane akcje zawarte na stronie **Zasady** zawierają szczegółowe informacje i podsumowują typy informacji poufnych oraz nieodpowiednie działania związane z zawartością w komunikacji w organizacji. Szczegółowe informacje są obsługiwane przez [klasyfikację danych](data-classification-overview.md) i stosowanie etykiet poufności, etykiet przechowywania i klasyfikacji typów informacji poufnych. Te szczegółowe informacje nie obejmują żadnych danych osobowych (PII) dla użytkowników w organizacji.

![Zalecane akcje dotyczące zgodności z komunikacją.](../media/communication-compliance-recommended-actions.png)

Działanie w komunikatach zawierających nieodpowiednią zawartość jest agregowane według [typu klasyfikatora](/microsoft-365/compliance/communication-compliance-policies#classifiers) z istniejących zasad, które używają nieodpowiedniego szablonu zawartości lub zasad niestandardowych, które używają klasyfikatorów do nieodpowiedniej zawartości. Zbadaj alerty dla tych komunikatów na pulpicie nawigacyjnym alertów dla zasad.

Działanie obejmujące [typy informacji poufnych](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) jest wykrywane w komunikatach omówionych w istniejących zasadach i komunikatach, które nie są objęte istniejącymi zasadami. Szczegółowe informacje są agregowane dla wszystkich typów informacji poufnych, w tym tych, które organizacja nie została wcześniej zdefiniowana w istniejących zasadach zgodności komunikacji. Skorzystaj z tych szczegółowych informacji, aby utworzyć nowe zasady zgodności komunikacji lub zaktualizować istniejące zasady.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Krok 1 (wymagany): Włączanie uprawnień do zgodności z komunikacją

> [!IMPORTANT]
> Po skonfigurowaniu grup ról stosowanie uprawnień grupy ról do przypisanych użytkowników w całej organizacji może potrwać do 30 minut.

Istnieje sześć grup ról używanych do konfigurowania początkowych uprawnień do zarządzania funkcjami zgodności komunikacji. Aby zapewnić **zgodność z komunikacją** jako opcję menu w portal zgodności Microsoft Purview i kontynuować wykonywanie tych kroków konfiguracji, musisz zostać przypisany do jednej z następujących ról lub grup ról:

- rola [*administratora globalnego*](/azure/active-directory/roles/permissions-reference#global-administrator) Azure Active Directory
- rola [*administratora zgodności*](/azure/active-directory/roles/permissions-reference#compliance-administrator) Azure Active Directory
- grupa ról [*zarządzania organizacją*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portal zgodności Microsoft Purview
- grupa ról [*administratora zgodności*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portal zgodności Microsoft Purview
- *Grupa ról Zgodność z komunikacją*
- *Grupa ról administratora zgodności komunikacji*

Członkowie następujących ról mają te same uprawnienia rozwiązania dołączone do grupy ról *Administrator zgodności komunikacji* :

- *administrator globalny* Azure Active Directory
- *administrator zgodności* Azure Active Directory
- *zarządzanie organizacją* portal zgodności Microsoft Purview
- *administrator zgodności* portal zgodności Microsoft Purview

> [!IMPORTANT]
> Upewnij się, że zawsze masz co najmniej jednego użytkownika w grupach ról *Zgodność z komunikacją* lub *Zgodność z komunikacją Administrator* (w zależności od wybranej opcji), aby konfiguracja zgodności komunikacji nie wchodziła do scenariusza "zero administratora", jeśli określoni użytkownicy opuszczają organizację.

W zależności od sposobu zarządzania zasadami zgodności komunikacji i alertami należy przypisać użytkowników do określonych grup ról, aby zarządzać różnymi zestawami funkcji zgodności komunikacji. Możesz przypisać użytkowników z różnymi obowiązkami zgodności do określonych grup ról w celu zarządzania różnymi obszarami funkcji zgodności komunikacji. Możesz też zdecydować się na przypisanie wszystkich kont użytkowników wyznaczonym administratorom, analitykom, badaczom i widzom do grupy ról *Zgodność z komunikacją* . Użyj jednej grupy ról lub wielu grup ról, aby najlepiej dopasować wymagania dotyczące zarządzania zgodnością.

Wybierz spośród tych opcji grupy ról rozwiązania podczas konfigurowania zgodności z komunikacją i zarządzania nimi:

| Rola | Uprawnienia roli |
|:-----|:-----------------|
| **Zgodność z komunikacją** | Ta grupa ról służy do zarządzania zgodnością komunikacji dla organizacji w jednej grupie. Dodając wszystkie konta użytkowników dla wyznaczonych administratorów, analityków, badaczy i osób przeglądających, możesz skonfigurować uprawnienia do zgodności komunikacji w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień zgodności komunikacji. Ta konfiguracja jest najprostszym sposobem szybkiego rozpoczęcia pracy ze zgodnością z komunikacją i jest dobrym rozwiązaniem dla organizacji, które nie potrzebują oddzielnych uprawnień zdefiniowanych dla oddzielnych grup użytkowników. Użytkownicy tworzący zasady jako administrator zgodności komunikacji muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online.|
| **Administrator zgodności komunikacji** | Użyj tej grupy ról, aby początkowo skonfigurować zgodność z komunikacją, a później segregować administratorów zgodności komunikacji do zdefiniowanej grupy. Użytkownicy przypisani do tej grupy ról mogą tworzyć, odczytywać, aktualizować i usuwać zasady zgodności komunikacji, ustawienia globalne i przypisania grup ról. Użytkownicy przypisani do tej grupy ról nie mogą wyświetlać alertów komunikatów. Użytkownicy tworzący zasady jako administrator zgodności komunikacji muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online.|
| **Analityk zgodności komunikacji** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą pełnić rolę analityków zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać zasady, w których są przypisani jako recenzenci, wyświetlać metadane komunikatów (nie zawartość komunikatów), eskalować do dodatkowych recenzentów lub wysyłać powiadomienia do użytkowników. Analitycy nie mogą rozwiązywać oczekujących alertów. |
| **Badacz zgodności z komunikacją** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą pełnić rolę badaczy zgodności z komunikacją. Użytkownicy przypisani do tej grupy ról mogą wyświetlać metadane komunikatów i zawartość, eskalować do dodatkowych recenzentów, eskalować do sprawy zbierania elektronicznych materiałów dowodowych (Premium), wysyłać powiadomienia do użytkowników i rozwiązywać alert. |
| **Podgląd zgodności komunikacji** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą zarządzać raportami komunikacji. Użytkownicy przypisani do tej grupy ról mogą uzyskiwać dostęp do wszystkich widżetów raportowania na stronie głównej zgodności komunikacji i mogą wyświetlać wszystkie raporty zgodności komunikacji. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Opcja 1. Przypisywanie wszystkich użytkowników zgodności do grupy ról Zgodność z komunikacją

1. Zaloguj się przy [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) użyciu poświadczeń dla konta administratora w organizacji Microsoft 365.

2. W Centrum zgodności zabezpieczeń &amp; przejdź do pozycji **Uprawnienia**. Wybierz link, aby wyświetlić role i zarządzać nimi w Office 365.

3. Wybierz grupę ról *Zgodność z komunikacją* , a następnie wybierz pozycję **Edytuj grupę ról**.

4. Wybierz pozycję **Wybierz członków** w okienku nawigacji po lewej stronie, a następnie wybierz pozycję **Edytuj**.

5. Wybierz pozycję **Dodaj,** a następnie zaznacz pole wyboru dla wszystkich użytkowników, którzy chcesz dodać do grupy ról *Zgodność z komunikacją* .

6. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Gotowe**.

7. Wybierz pozycję **Zapisz** , aby dodać użytkowników do grupy ról. Wybierz pozycję **Zamknij** , aby wykonać kroki

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Opcja 2. Przypisywanie użytkowników do określonych grup ról zgodności komunikacji

Ta opcja służy do przypisywania użytkowników do określonych grup ról w celu segmentowania dostępu do zgodności komunikacji i obowiązków między różnymi użytkownikami w organizacji.

1. Zaloguj się do [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji Microsoft 365, a następnie przejdź do obszaru **Uprawnienia**</a>.

2. Wybierz link, aby wyświetlić role i zarządzać nimi w Office 365.

3. Wybierz jedną z grup ról zgodności komunikacji, a następnie wybierz pozycję **Edytuj grupę ról**.

4. Wybierz pozycję **Wybierz członków** w okienku nawigacji po lewej stronie, a następnie wybierz pozycję **Edytuj**.

5. Wybierz pozycję **Dodaj** , a następnie zaznacz pole wyboru dla wszystkich użytkowników, którzy chcesz dodać do grupy ról.

6. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Gotowe**.

7. Wybierz pozycję **Zapisz** , aby dodać użytkowników do grupy ról.

8. Wybierz następną grupę ról zgodności komunikacji, a następnie powtórz kroki 4–7 dla każdej wymaganej grupy ról.

9. Wybierz pozycję **Zamknij** , aby wykonać kroki.

Aby uzyskać więcej informacji na temat grup ról i uprawnień, zobacz [Uprawnienia w Centrum zgodności](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Krok 2 (wymagane): Włączanie dziennika inspekcji

Zgodność z komunikacją wymaga dzienników inspekcji w celu wyświetlania alertów i śledzenia akcji korygowania podejmowanych przez recenzentów. Dzienniki inspekcji są podsumowaniem wszystkich działań skojarzonych ze zdefiniowanymi zasadami organizacyjnymi lub w dowolnym momencie zmiany zasad zgodności komunikacji.

Inspekcja jest domyślnie włączona dla organizacji Microsoft 365. Niektóre organizacje mogły wyłączyć inspekcję z określonych powodów. Jeśli inspekcja jest wyłączona dla Twojej organizacji, może to być spowodowane tym, że inny administrator wyłączył tę inspekcję. Zalecamy potwierdzenie, że podczas wykonywania tego kroku można ponownie włączyć inspekcję.

Aby uzyskać instrukcje krok po kroku dotyczące włączania inspekcji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](turn-audit-log-search-on-or-off.md). Po włączeniu inspekcji zostanie wyświetlony komunikat informujący, że dziennik inspekcji jest przygotowywany i że wyszukiwanie można uruchomić w ciągu kilku godzin po zakończeniu przygotowywania. Tę akcję trzeba wykonać tylko raz. Aby uzyskać więcej informacji na temat korzystania z dziennika inspekcji, zobacz [Przeszukiwanie dziennika inspekcji](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Krok 3 (opcjonalnie): Konfigurowanie grup pod kątem zgodności z komunikacją

 Podczas tworzenia zasad zgodności komunikacji określasz, kto ma przeglądaną komunikację i kto wykonuje przeglądy. W zasadach użyjesz adresów e-mail do identyfikowania osób lub grup osób. Aby uprościć konfigurację, możesz tworzyć grupy dla osób, które mają przejrzaną komunikację, oraz grupy dla osób przeglądających te komunikaty. Jeśli używasz grup, może być potrzebnych kilka. Jeśli na przykład chcesz monitorować komunikację między dwiema odrębnymi grupami osób lub chcesz określić grupę, która nie będzie nadzorowana.

Użyj poniższego wykresu, aby ułatwić konfigurowanie grup w organizacji pod kątem zasad zgodności z komunikacją:

| **Członek zasad** | **Obsługiwane grupy** | **Nieobsługiwanych grup** |
|:-----|:-----|:-----|
|Użytkownicy nadzorowane <br> Wykluczeni użytkownicy | Grupy dystrybucyjne <br> Grupy Microsoft 365 | Dynamiczne grupy dystrybucji <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty <br> Microsoft 365 grupy z członkostwem dynamicznym |
| Wszyscy oceniający | Brak | Grupy dystrybucyjne <br> Dynamiczne grupy dystrybucji <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty |

Po przypisaniu *grupy dystrybucyjnej* w zasadach zasady monitorują wszystkie wiadomości e-mail i Teams czaty od każdego użytkownika w *grupie dystrybucyjnej*. Po przypisaniu *grupy Microsoft 365* w zasadach zasady monitorują wszystkie wiadomości e-mail i Teams czaty wysyłane do *grupy Microsoft 365*, a nie poszczególne wiadomości e-mail i czaty odbierane przez każdego członka grupy. Zaleca się używanie grup dystrybucyjnych w zasadach zgodności komunikacji, aby poszczególne wiadomości e-mail i Teams czaty od każdego użytkownika były automatycznie monitorowane.

Jeśli jesteś organizacją z Exchange wdrożeniem lokalnym lub zewnętrznym dostawcą poczty e-mail i chcesz monitorować Microsoft Teams czaty dla użytkowników, musisz utworzyć grupę dystrybucyjną dla użytkowników z lokalnymi lub zewnętrznymi skrzynkami pocztowymi do monitorowania. W dalszej części tych kroków przypiszesz tę grupę dystrybucyjną jako wybór **nadzorowanych użytkowników i grup** w kreatorze zasad. Aby uzyskać więcej informacji na temat wymagań i ograniczeń dotyczących włączania magazynu opartego na chmurze i obsługi Teams dla użytkowników lokalnych, zobacz [Wyszukiwanie Teams danych czatu dla użytkowników lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).

Aby zarządzać nadzorowanymi użytkownikami w dużych organizacjach przedsiębiorstwa, może być konieczne monitorowanie wszystkich użytkowników w dużych grupach. Program PowerShell umożliwia skonfigurowanie grupy dystrybucyjnej dla globalnych zasad zgodności komunikacji dla przypisanej grupy. Dzięki temu można monitorować tysiące użytkowników przy użyciu jednej zasady i aktualizować zasady zgodności komunikacji, gdy nowi pracownicy dołączą do organizacji.

1. Utwórz dedykowaną [grupę dystrybucyjną](/powershell/module/exchange/new-distributiongroup) dla globalnych zasad zgodności komunikacji z następującymi właściwościami: Upewnij się, że ta grupa dystrybucyjna nie jest używana do innych celów ani innych usług Office 365.

    - **MemberDepartRestriction = Zamknięte**. Zapewnia, że użytkownicy nie mogą usunąć się z grupy dystrybucyjnej.
    - **MemberJoinRestriction = Zamknięte**. Zapewnia, że użytkownicy nie mogą dodawać się do grupy dystrybucyjnej.
    - **ModerationEnabled = True**. Zapewnia, że wszystkie komunikaty wysyłane do tej grupy podlegają zatwierdzeniu i że grupa nie jest używana do komunikowania się poza konfiguracją zasad zgodności komunikacji.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Wybierz nieużywany [atrybut niestandardowy Exchange](/Exchange/recipients/mailbox-custom-attributes), aby śledzić użytkowników dodanych do zasad zgodności komunikacji w organizacji.

3. Uruchom następujący skrypt programu PowerShell zgodnie z harmonogramem cyklicznym, aby dodać użytkowników do zasad zgodności komunikacji:

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

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Krok 4 (opcjonalnie): Sprawdź, czy dzierżawa Yammer jest w trybie natywnym

W trybie natywnym wszyscy użytkownicy Yammer znajdują się w Azure Active Directory (Azure AD), wszystkie grupy są Office 365 Grupy, a wszystkie pliki są przechowywane w usłudze SharePoint Online. Dzierżawa Yammer musi być w trybie natywnym, aby zasady zgodności komunikacji skanować i identyfikować ryzykowne konwersacje w prywatnych wiadomościach i konwersacjach społeczności w Yammer.

Aby uzyskać więcej informacji na temat konfigurowania Yammer w trybie natywnym, zobacz:

- [Omówienie trybu natywnego Yammer w Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Konfigurowanie sieci Yammer dla trybu natywnego dla Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Krok 5 (wymagany): Tworzenie zasad zgodności komunikacji

>[!IMPORTANT]
>Używanie programu PowerShell do tworzenia zasad zgodności komunikacji i zarządzania nimi nie jest obsługiwane. Aby utworzyć te zasady i zarządzać nimi, należy użyć mechanizmów kontroli zarządzania zasadami w [rozwiązaniu zgodności z komunikacją](https://compliance.microsoft.com/supervisoryreview).

>[!TIP]  
>Chcesz zapoznać się z szczegółowym przewodnikiem konfigurowania nowych zasad zgodności komunikacji i korygowania alertu? Zapoznaj się z [tym 15-minutowym filmem wideo](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) , aby zobaczyć pokaz sposobu, w jaki zasady zgodności komunikacji mogą pomóc w wykrywaniu nieodpowiednich komunikatów, badaniu potencjalnych naruszeń i korygowaniu problemów ze zgodnością.

1. Zaloguj się do [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji Microsoft 365.

2. W portal zgodności Microsoft Purview wybierz pozycję **Zgodność z komunikacją**.

3. Wybierz kartę **Zasady** .

4. Wybierz pozycję **Utwórz zasady** , aby utworzyć i skonfigurować nowe zasady na podstawie szablonu lub utworzyć i skonfigurować zasady niestandardowe.

    Jeśli wybierzesz szablon zasad do utworzenia zasad, wykonasz:

    - Potwierdź lub zaktualizuj nazwę zasad. Nazw zasad nie można zmienić po utworzeniu zasad.

    - Wybierz użytkowników lub grupy do nadzorowania, w tym wybieranie użytkowników lub grup, których chcesz wykluczyć. W przypadku korzystania z szablonu konfliktu interesów wybierzesz dwie grupy lub dwóch użytkowników do monitorowania pod kątem komunikacji wewnętrznej.

    - Wybierz recenzentów zasad. Recenzenci to użytkownicy indywidualni, a wszyscy recenzenci muszą mieć skrzynki pocztowe hostowane w Exchange Online. Recenzenci dodani tutaj to recenzenci, spośród których możesz wybrać podczas eskalacji alertu w przepływie pracy badania i korygowania. Gdy recenzenci są dodawani do zasad, automatycznie otrzymują wiadomość e-mail z powiadomieniem o przypisaniu do zasad i udostępniają linki do informacji o procesie przeglądu.

    - Wybierz ograniczone pole warunku, zwykle typ informacji poufnych lub słownik słów kluczowych do zastosowania do zasad.

    > [!NOTE]
    > Jeśli chcesz włączyć [optyczne rozpoznawanie znaków (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) do skanowania osadzonych lub dołączonych obrazów w komunikatach pod kątem tekstu drukowanego lub odręcznego zgodnego z warunkami zasad, wybierz pozycję **Dostosuj** **zasadyKondycje** >  i procent oraz włącz **opcję Wyodrębnij tekst drukowany lub odręczny z obrazów do oceny**.

    Jeśli zdecydujesz się utworzyć zasady niestandardowe za pomocą kreatora zasad, wykonaj następujące czynności:

    - Nadaj zasadom nazwę i opis. Nazw zasad nie można zmienić po utworzeniu zasad.

    - Wybierz użytkowników lub grupy do nadzorowania, w tym wszystkich użytkowników w organizacji, określonych użytkowników i grupy lub innych użytkowników i grup, które chcesz wykluczyć.

    - Wybierz recenzentów zasad. Recenzenci to użytkownicy indywidualni, a wszyscy recenzenci muszą mieć skrzynki pocztowe hostowane w Exchange Online. Recenzenci dodani tutaj to recenzenci, spośród których możesz wybrać podczas eskalacji alertu w przepływie pracy badania i korygowania. Gdy recenzenci są dodawani do zasad, automatycznie otrzymują wiadomość e-mail z powiadomieniem o przypisaniu do zasad i udostępniają linki do informacji o procesie przeglądu.

    - Wybierz kanały komunikacyjne do skanowania, w tym Exchange, Microsoft Teams, Yammer lub Skype dla firm. Jeśli łącznik został skonfigurowany w Microsoft 365, wybierzesz również skanowanie źródeł innych firm.

    - Wybierz kierunek komunikacji do monitorowania, w tym komunikację przychodzącą, wychodzącą lub wewnętrzną.

    - Zdefiniuj [warunki](communication-compliance-policies.md#ConditionalSettings) zasad zgodności komunikacji. Możesz wybierać spośród adresów wiadomości, słów kluczowych, typów plików i warunków dopasowania rozmiaru.

    - Wybierz, czy chcesz uwzględnić typy informacji poufnych. W tym kroku można wybrać domyślne i niestandardowe typy informacji poufnych. Wybierz z istniejących niestandardowych typów informacji poufnych lub niestandardowych słowników słów kluczowych w kreatorze zasad zgodności komunikacji. Te elementy można utworzyć przed uruchomieniem kreatora w razie potrzeby. Możesz również utworzyć nowe typy informacji poufnych z poziomu kreatora zasad zgodności komunikacji.

    - Wybierz, czy chcesz włączyć klasyfikatory. Klasyfikatory mogą wykrywać nieodpowiedni język i obrazy wysyłane lub odbierane w treści wiadomości e-mail lub innych typów tekstu. Możesz wybrać następujące wbudowane klasyfikatory: *Threat*, *Profanity*, *Targeted harassment*, *Adult images*, *Racy images* i *Gory images*.

    - Włącz [optyczne rozpoznawanie znaków (OCR),](communication-compliance-policies.md#optical-character-recognition-ocr) aby skanować osadzone lub dołączone obrazy w komunikatach pod kątem tekstu drukowanego lub odręcznego zgodnego z warunkami zasad. W przypadku zasad niestandardowych w zasadach należy skonfigurować co najmniej jedno ustawienie warunkowe skojarzone z tekstem, słowami kluczowymi, klasyfikatorami lub typami informacji poufnych, aby umożliwić wybór skanowania optycznego rozpoznawania znaków.

    - Zdefiniuj procent komunikacji do przejrzenia.

    - Przejrzyj wybrane zasady i utwórz zasady.

5. Wybierz pozycję **Utwórz zasady** podczas korzystania z szablonów lub **Prześlij** podczas korzystania z kreatora zasad niestandardowych.

6. Strona **Twoje zasady została utworzona** jest wyświetlana z wytycznymi dotyczącymi tego, kiedy zasady zostaną aktywowane i które komunikaty zostaną przechwycone.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>Krok 6 (opcjonalnie): Aktualizowanie granic zgodności dla zasad zgodności komunikacji

[Granice zgodności](/microsoft-365/compliance/set-up-compliance-boundaries) tworzą granice logiczne w organizacji kontrolujące lokalizacje zawartości użytkownika (takie jak skrzynki pocztowe, konta OneDrive i witryny SharePoint), które mogą wyszukiwać menedżerowie zbierania elektronicznych materiałów dowodowych.

Jeśli w organizacji skonfigurowano granice zgodności, musisz zaktualizować granice zgodności, aby umożliwić niektórym użytkownikom dostęp do skrzynek pocztowych, które obsługują zasady zgodności komunikacji. Musisz zezwolić na dostęp do administratorów zgodności komunikacji i recenzentów zgodności z komunikacją, aby akcje zarządzania zasadami oraz badania i korygowania działały prawidłowo.

Aby zezwolić na dostęp dla administratorów i recenzentów zgodności komunikacji, uruchom następujące polecenia programu PowerShell. Te polecenia należy uruchomić tylko raz, nawet jeśli w przyszłości dodasz nowe zasady zgodności komunikacji:

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

Aby uzyskać więcej informacji na temat składni poleceń cmdlet, zobacz [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>Krok 7 (opcjonalnie): tworzenie szablonów powiadomień i konfigurowanie anonimizacji użytkowników

Jeśli chcesz mieć możliwość odpowiadania na alert zasad, wysyłając powiadomienie o przypomnieniu do skojarzonego użytkownika, musisz utworzyć co najmniej jeden szablon powiadomienia w organizacji. Pola szablonu powiadomień można edytować przed wysłaniem ich w ramach procesu korygowania alertów, a zalecane jest utworzenie dostosowanego szablonu powiadomień dla każdej zasady zgodności komunikacji.

Możesz również włączyć anonimizację wyświetlanych nazw użytkowników podczas badania dopasowań zasad i podejmowania działań dotyczących komunikatów.

1. Zaloguj się do [portal zgodności Microsoft Purview](https://compliance.microsoft.com) przy użyciu poświadczeń konta administratora w organizacji Microsoft 365.

2. W portal zgodności Microsoft Purview przejdź do pozycji **Zgodność z komunikacją**.

3. Aby skonfigurować anonimizację nazw użytkowników, wybierz kartę **Prywatność** .

4. Aby włączyć anonimizację, wybierz pozycję **Pokaż zanonimizowane wersje nazw użytkowników**.

5. Wybierz **Zapisz**.

6. Przejdź do karty **Szablony powiadomień** , a następnie wybierz pozycję **Utwórz szablon powiadomienia**.

7. Na stronie **Modyfikowanie szablonu powiadomienia** wypełnij następujące pola:

    - Nazwa szablonu (wymagana)
    - Wyślij z (wymagane)
    - Cc i Bcc (opcjonalnie)
    - Temat (wymagany)
    - Treść komunikatu (wymagana)

8. Wybierz pozycję **Zapisz** , aby utworzyć i zapisać szablon powiadomienia.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>Krok 8 (opcjonalnie): Testowanie zasad zgodności komunikacji

Po utworzeniu zasad zgodności komunikacji warto ją przetestować, aby upewnić się, że zdefiniowane warunki są prawidłowo wymuszane przez zasady. Możesz również [przetestować zasady Ochrona przed utratą danych w Microsoft Purview (DLP),](create-test-tune-dlp-policy.md) jeśli zasady zgodności komunikacji obejmują typy informacji poufnych. Upewnij się, że dajesz zasadom czas na aktywowanie, aby komunikacja, którą chcesz przetestować, została przechwycona.

Wykonaj następujące kroki, aby przetestować zasady zgodności komunikacji:

1. Otwórz klienta poczty e-mail, Microsoft Teams lub Yammer podczas logowania jako nadzorowany użytkownik zdefiniowany w zasadach, które chcesz przetestować.

2. Wyślij wiadomość e-mail, Microsoft Teams czat lub Yammer wiadomość spełniającą kryteria zdefiniowane w zasadach zgodności komunikacji. Ten test może być słowem kluczowym, rozmiarem załącznika, domeną itp. Upewnij się, że określono, czy skonfigurowane ustawienia warunkowe w zasadach są zbyt restrykcyjne lub zbyt łagodne.

    > [!NOTE]
    > Pełne przetwarzanie wiadomości e-mail w zasadach może potrwać około 24 godzin. Pełne przetwarzanie komunikacji na platformach Microsoft Teams, Yammer i innych firm może potrwać około 48 godzin.

3. Zaloguj się do Microsoft 365 jako recenzent wyznaczony w zasadach zgodności komunikacji. Przejdź do pozycji **Zgodność** >  **komunikacjiAcertyfikacje**, aby wyświetlić alerty dotyczące zasad.

4. Skoryguj alert przy użyciu kontrolek korygowania i sprawdź, czy alert został prawidłowo rozwiązany.

## <a name="next-steps"></a>Następne kroki

Po wykonaniu tych kroków w celu utworzenia pierwszych zasad zgodności komunikacji zaczniesz otrzymywać alerty ze wskaźników aktywności po 24–48 godzinach. Skonfiguruj dodatkowe zasady zgodnie z potrzebami, korzystając ze wskazówek opisanych w kroku 5 tego artykułu.

Aby dowiedzieć się więcej na temat badania alertów zgodności komunikacji, zobacz [Badanie i korygowanie alertów zgodności komunikacji](communication-compliance-investigate-remediate.md).

Aby być na bieżąco z najnowszymi aktualizacjami zgodności komunikacji, wybierz pozycję **Co nowego** w [zgodności z komunikacją](https://compliance.microsoft.com/) w organizacji.
