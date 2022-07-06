---
title: Migrowanie zasad Exchange Online DLP do Centrum zgodności
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Dowiedz się, jak planować i migrować zasady ochrony przed utratą danych online programu Exchange do usługi DLP.
ms.openlocfilehash: 371dfafbbf6acf31587b0786a5b5594fb83571d9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638284"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-microsoft-purview-compliance-portal"></a>Migrowanie zasad ochrony przed utratą danych Exchange Online do portal zgodności Microsoft Purview

[Exchange Online zasady ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) są przestarzałe. [Znacznie bogatsze funkcje DLP](dlp-learn-about-dlp.md), w tym Exchange Online DLP, są oferowane w [portal zgodności Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies). Kreator migracji zasad DLP ułatwia przenoszenie Exchange Online zasad DLP do Centrum zgodności, w którym będziesz nimi zarządzać.

Kreator migracji działa, czytając konfigurację zasad DLP w programie Exchange, a następnie tworząc zduplikowane zasady w Centrum zgodności. Domyślnie kreator tworzy nowe wersje zasad w trybie **testowym** , dzięki czemu można zobaczyć, jaki wpływ miałyby one na środowisko bez wymuszania żadnej z akcji. Gdy wszystko będzie gotowe do pełnego przejścia do wersji Centrum zgodności, musisz wykonać następujące **_czynności_**:

1. Dezaktywuj lub usuń zasady źródłowe w Programie Exchange Administracja Center (EAC).
1. Edytuj wersję centrum zgodności zasad i zmień jej stan z **Test** na **Wymuś**.

> [!WARNING]
> Jeśli nie usuniesz lub nie zdezaktywujesz zasad źródłowych w usłudze EAC przed ustawieniem wersji Centrum zgodności na **wartość Wymuszaj** oba zestawy zasad, spróbujesz wymusić akcje, a otrzymasz zduplikowane zdarzenia. **_Jest to nieobsługiwana konfiguracja._**

Kreator migracji migruje tylko zasady EXO i skojarzone reguły przepływu poczty. Autonomiczne reguły przepływu poczty programu Exchange nie są migrowane.

## <a name="migration-workflow"></a>Przepływ pracy migracji

Istnieją cztery fazy migracji zasad DLP z programu Exchange do konsoli zarządzania Unified DLP w Centrum zgodności.

1. Przygotowanie do migracji
    1. Oceń i porównaj zasady DLP Exchange Online (EXO) i zasady DLP Centrum zgodności pod kątem zduplikowanych funkcji.
    1. Zdecyduj, które zasady EXO DLP mają zostać przeniesione dokładnie tak, jak są, możesz użyć kreatora, aby je zmigrować.
    1. Zdecyduj, które zasady EXO DLP mają zostać skonsolidowane i skonsolidowane w centrum administracyjnym programu Exchange, a następnie użyj kreatora migracji, aby przenieść je do Centrum zgodności.
1. Przeprowadzanie migracji — użyj kreatora
1. Testowanie i walidacja — sprawdzanie wyników
1. Aktywowanie zmigrowanych zasad

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="licensing-and-versions"></a>Licencjonowanie i wersje

Przed rozpoczęciem migracji zasad DLP należy potwierdzić [subskrypcję platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i wszelkie dodatki.

Aby uzyskać dostęp do kreatora migracji zasad i korzystać z niego, musisz mieć jedną z tych subskrypcji lub dodatków

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- zgodność Microsoft 365 E5
- zgodność Microsoft 365 A5
- Microsoft 365 E5 ochrona informacji i ład
- Microsoft 365 A5 ochrony informacji i ładu

Aby uzyskać szczegółową listę wymagań dotyczących licencjonowania DLP, zobacz [Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń, ochrony przed utratą danych](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

### <a name="permissions"></a>Uprawnienia

Konto używane do uruchamiania kreatora migracji musi mieć dostęp zarówno do strony DLP konsoli programu Exchange Administracja, jak i do konsoli Unified DLP w Centrum zgodności.

## <a name="prepare-for-migration"></a>Przygotowanie do migracji

1. Jeśli nie znasz DLP, konsoli DLP Centrum zgodności lub konsoli DLP centrum programu Exchange Administracja, przed podjęciem próby migracji zasad należy się zapoznać.
    1. [Exchange Online zasad ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
    1. [Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md)
1. Oceń zasady programu Exchange DLP i Centrum zgodności, zadając następujące pytania:

|Pytanie|Akcja|Procedura migracji|
|---|---|---|
|Czy zasady są nadal potrzebne?|Jeśli nie, usuń lub dezaktywuj|nie migruj|
|Czy nakłada się ona na inne zasady DLP programu Exchange lub Centrum zgodności?|Jeśli tak, czy można skonsolidować nakładające się zasady?|— Jeśli nakładają się na inne zasady programu Exchange, ręcznie utwórz skonsolidowane zasady DLP w centrum programu Exchange Administracja, a następnie użyj kreatora migracji. </br> — Jeśli pokrywają się one z istniejącymi zasadami Centrum zgodności, możesz zmodyfikować istniejące zasady Centrum zgodności tak, aby były zgodne, nie migrować wersji programu Exchange|
|Czy zasady DLP programu Exchange są ściśle ograniczone i czy mają dobrze zdefiniowane warunki, akcje, dołączenia i wykluczenia?|Jeśli tak, jest dobrym kandydatem do migracji za pomocą kreatora, zanotuj zasady, aby pamiętać, aby wrócić, aby usunąć je później|migrowanie za pomocą kreatora|

## <a name="migration"></a>Migracja

Po dokonaniu oceny wszystkich zasad DLP programu Exchange i Centrum zgodności pod kątem potrzeb i zgodności możesz użyć kreatora migracji.

1. Otwórz konsolę [portal zgodności Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP.
2. Jeśli istnieją zasady DLP programu Exchange, które można migrować, w górnej części strony zostanie wyświetlony baner informujący o tym.
3. Wybierz **pozycję Migruj zasady** na banerze, aby otworzyć kreatora migracji. Na liście znajdują się wszystkie zasady DLP programu Exchange. Nie można wybrać wcześniej zmigrowanych zasad.
4. Wybierz zasady, które chcesz migrować. Można je migrować pojedynczo lub w grupach przy użyciu podejścia etapowego lub wszystkich jednocześnie. Wybierz pozycję **Dalej**.
5. Przejrzyj okienko wysuwane pod kątem ostrzeżeń lub komunikatów. Rozwiąż wszelkie problemy przed kontynuowaniem.
6. Wybierz tryb, w który mają zostać utworzone nowe zasady Centrum zgodności, **Aktywne**, **Testowe** lub **Wyłączone**.  Wartość domyślna to **Test**. Wybierz pozycję **Dalej**.
7. W razie potrzeby można utworzyć więcej zasad opartych na zasadach DLP programu Exchange dla innych ujednoliconych lokalizacji DLP. Spowoduje to powstanie jednej nowej ujednoliconej zasady DLP dla zmigrowanych zasad programu Exchange i jednej nowej ujednoliconej zasady DLP dla innych lokalizacji, które wybierzesz tutaj.

> [!IMPORTANT]
> Wszelkie warunki i akcje zasad DLP programu Exchange, które nie są obsługiwane przez inne lokalizacje DLP, takie jak Urządzenia, SharePoint, OneDrive, Lokalna, USŁUGA MCAS lub komunikaty kanału i czatu usługi Teams, zostaną usunięte z dodatkowych zasad. Ponadto istnieje praca wstępna, którą należy wykonać dla innych lokalizacji. Zobacz:
>- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
>- [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md)
>- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md)
>- [Dowiedz się więcej o lokalnym skanerze zapobiegania utracie danych](dlp-on-premises-scanner-learn.md)
>- [Wprowadzenie do lokalnego skanera zapobiegania utracie danych](dlp-on-premises-scanner-get-started.md)
>- [Używanie lokalnego skanera ochrony przed utratą danych w usłudze Microsoft Purview](dlp-on-premises-scanner-use.md)
>- [Używanie zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md)
 
8. Przejrzyj ustawienia sesji kreatora migracji. Wybierz pozycję **Dalej**.
9. Przejrzyj raport migracji. Zwróć uwagę na wszelkie błędy związane z regułami przepływu poczty programu Exchange. Można je naprawić i ponownie tworzyć skojarzone zasady.

Zmigrowane zasady będą teraz wyświetlane na liście zasad DLP w konsoli DLP Centrum zgodności.

## <a name="common-errors-and-mitigation"></a>Typowe błędy i środki zaradcze

|Komunikat o błędzie|Powodu|Środki zaradcze/zalecane kroki|
|---|---|---|
|Zasady zgodności o nazwie `<Name of the policy>` już istnieją w scenariuszach `Dlp`.|Prawdopodobnie ta migracja zasad została przeprowadzona wcześniej, a następnie ponownie zrekomplektowana w tej samej sesji|Odśwież sesję, aby zaktualizować listę zasad dostępnych do migracji. Wszystkie wcześniej zmigrowane zasady powinny być w `Already migrated` stanie.|
|Zasady zgodności o nazwie `<Name of the policy>` już istnieją w scenariuszach `Hold`.|Zasady przechowywania o tej samej nazwie istnieją w tej samej dzierżawie.|— Zmień nazwę zasad DLP w eac na inną nazwę. </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|`DLP-group@contoso.com` nie można użyć jako wartości warunku Udostępnione według, ponieważ jest to grupa dystrybucyjna lub grupa zabezpieczeń z obsługą poczty. Użyj opcji Udostępnione przez członka predykatu, aby wykrywać działania członków niektórych grup.|Reguły transportu zezwalają na użycie grup w warunku `sender is` , ale ujednolicony protokół DLP nie zezwala na to.|Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail grupy z warunku `sender is` i w razie potrzeby dodać grupę do warunku `sender is a member of` . Ponów próbę migracji dla zasad, których dotyczy problem|
|Nie można odnaleźć adresata `DLP-group@contoso.com`. Jeśli nowo utworzono, ponów próbę wykonania operacji po pewnym czasie. Jeśli usunięto lub wygasło, zresetuj prawidłowe wartości i spróbuj ponownie.|Prawdopodobnie adres grupy używany w `sender is a member of` warunku lub `recipient is a member of` wygasł lub jest nieprawidłowy.|— Usuń/zastąp wszystkie nieprawidłowe adresy e-mail grupy w regule transportu w centrum administracyjnym programu Exchange. </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|Wartością określoną w `FromMemberOf` predykatze musi być grupa zabezpieczeń z włączoną obsługą poczty e-mail.|Reguły transportu zezwalają na używanie poszczególnych użytkowników w warunku `sender is a member of` , ale ujednolicony protokół DLP na to nie zezwala.|— Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail poszczególnych użytkowników z warunku `sender is a member of` i w razie potrzeby dodać użytkowników do warunku `sender is` . </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|Wartością określoną w `SentToMemberOf` predykatze musi być grupa zabezpieczeń z włączoną obsługą poczty e-mail.|Reguły transportu zezwalają na używanie poszczególnych użytkowników pod warunkiem `recipient is a member of` , ale ujednolicone DLP nie zezwala na to.|— Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail poszczególnych użytkowników z warunku `recipient is a member of` i w razie potrzeby dodać użytkowników do warunku `recipient is` . </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|Używanie parametru `<Name of condition>` jest obsługiwane tylko w przypadku programu Exchange. Usuń ten parametr lub włącz tylko lokalizację programu Exchange.|Prawdopodobnie w Centrum zgodności istnieją inne zasady o tej samej nazwie z innymi lokalizacjami, takimi jak SPO/ODB/Teams, dla których wspomniany warunek nie jest obsługiwany.|Zmień nazwę zasad DLP w centrum administracyjnym programu Exchange i ponów próbę migracji.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Testowanie i walidacja <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

Testowanie i przeglądanie zasad.

1. Postępuj zgodnie z [procedurami testowania zasad DLP](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. Przejrzyj zdarzenia utworzone przez zasady w [Eksploratorze działań](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-purview-unified-dlp"></a>Przejrzyj dopasowania zasad między programami Exchange Administracja Center DLP i Microsoft Purview Unified DLP

Aby upewnić się, że zmigrowane zasady zachowują się zgodnie z oczekiwaniami, możesz wyeksportować raporty z obu centrów administracyjnych i porównać dopasowania zasad.

1. Połącz się z [usługą Exchange Online w programie PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Wyeksportuj [raport EAC DLP](/powershell/module/exchange/get-maildetaildlppolicyreport). Możesz skopiować to polecenie cmdlet i wstawić odpowiednie wartości:

   ```powershell
   Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

3. Wyeksportuj [raport Unified DLP](/powershell/module/exchange/get-dlpdetailreport). Możesz skopiować to polecenie cmdlet i wstawić odpowiednie wartości:

   ```powershell
   Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

## <a name="activate-your-migrated-policies"></a>Aktywowanie zmigrowanych zasad

Gdy będziesz zadowolony ze sposobu działania zmigrowanych zasad, możesz ustawić je na **wymuszanie**.

1. Otwórz konsolę DLP programu Exchange Administracja Center.
2. Dezaktywuj lub usuń zasady źródłowe.
3. Otwórz [konsolę portal zgodności Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP i wybierz zasady, które chcesz uaktywnić, aby je edytować.
4. Zmień stan na **Włącz**.

## <a name="related-articles"></a>Powiązane artykuły:

- [Exchange Online zasad ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
- [Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
- [Exchange Online zasad ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
