---
title: Migruj zasady ochrony przed utratą danych w usłudze Exchange Online do centrum zgodności
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
description: Dowiedz się, jak planować i migrować Exchange zasad ochrony przed utratą danych online do Microsoft 365 DLP.
ms.openlocfilehash: c6b941a0dd1f66e2f44494fded9ba47e8c3d7230
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760872"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-compliance-center"></a>Migruj zasady ochrony przed utratą danych w usłudze Exchange Online do centrum zgodności

[Exchange Online zasady ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) są przestarzałe. [Znacznie bogatsze funkcje DLP](dlp-learn-about-dlp.md), w tym Exchange Online DLP, są oferowane w [centrum zgodności Microsoft 365](https://compliance.microsoft.com/datalossprevention?viewid=policies). Kreator migracji zasad DLP ułatwia przenoszenie Exchange Online zasad DLP do Centrum zgodności, w którym będziesz nimi zarządzać.

Kreator migracji działa przez przeczytanie konfiguracji zasad DLP w Exchange, a następnie utworzenie zduplikowanych zasad w Centrum zgodności. Domyślnie kreator tworzy nowe wersje zasad w trybie **testowym** , dzięki czemu można zobaczyć, jaki wpływ miałyby one na środowisko bez wymuszania żadnej z akcji. Gdy wszystko będzie gotowe do pełnego przejścia do wersji Centrum zgodności, musisz wykonać następujące **_czynności_**:

1. Dezaktywuj lub usuń zasady źródłowe w centrum administracyjnym Exchange (EAC).
1. Edytuj wersję centrum zgodności zasad i zmień jej stan z **Test** na **Wymuś**.

> [!WARNING]
> Jeśli nie usuniesz lub nie zdezaktywujesz zasad źródłowych w usłudze EAC przed ustawieniem wersji Centrum zgodności na **wartość Wymuszaj** oba zestawy zasad, spróbujesz wymusić akcje, a otrzymasz zduplikowane zdarzenia. **_Jest to nieobsługiwana konfiguracja._**

Kreator migracji migruje tylko zasady EXO i skojarzone reguły przepływu poczty. Autonomiczne reguły przepływu poczty Exchange nie są migrowane.

## <a name="migration-workflow"></a>Przepływ pracy migracji

Istnieją cztery fazy migracji zasad DLP z Exchange do konsoli zarządzania Unified DLP w Centrum zgodności.

1. Przygotowanie do migracji
    1. Oceń i porównaj zasady DLP Exchange Online (EXO) i zasady DLP Centrum zgodności pod kątem zduplikowanych funkcji.
    1. Zdecyduj, które zasady EXO DLP mają zostać przeniesione dokładnie tak, jak są, możesz użyć kreatora, aby je zmigrować.
    1. Zdecyduj, które zasady EXO DLP mają zostać skonsolidowane i skonsolidowane w centrum administracyjnym Exchange, a następnie użyj kreatora migracji, aby przenieść je do Centrum zgodności.
1. Przeprowadzanie migracji — użyj kreatora
1. Testowanie i walidacja — sprawdzanie wyników
1. Aktywowanie zmigrowanych zasad

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="licensing-and-versions"></a>Licencjonowanie i wersje

Przed rozpoczęciem migracji zasad DLP należy potwierdzić [subskrypcję Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i wszelkie dodatki.

Aby uzyskać dostęp do kreatora migracji zasad i korzystać z niego, musisz mieć jedną z tych subskrypcji lub dodatków

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- zgodność Microsoft 365 E5
- zgodność Microsoft 365 A5
- Microsoft 365 E5 ochrona informacji i ład
- Microsoft 365 A5 ochrony informacji i ładu

Aby uzyskać szczegółową listę wymagań dotyczących licencjonowania DLP, zobacz [Microsoft 365 Wytyczne dotyczące licencjonowania dotyczące zgodności & zabezpieczeń, ochrony przed utratą danych](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

### <a name="permissions"></a>Uprawnienia

Konto używane do uruchamiania kreatora migracji musi mieć dostęp zarówno do strony DLP konsoli administracyjnej Exchange, jak i do konsoli Unified DLP w Centrum zgodności.

## <a name="prepare-for-migration"></a>Przygotowanie do migracji

1. Jeśli nie znasz DLP, konsoli DLP Centrum zgodności lub konsoli DLP centrum administracyjnego Exchange, przed podjęciem próby migracji zasad należy się zapoznać.
    1. [Exchange Online zasad ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Dowiedz się więcej o zapobieganiu utracie danych punktu końcowego Microsoft 365](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
    1. [Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md)
1. Oceń zasady Exchange DLP i Centrum zgodności, zadając następujące pytania:

|Pytanie|Akcja|Procedura migracji|
|---|---|---|
|Czy zasady są nadal potrzebne?|Jeśli nie, usuń lub dezaktywuj|nie migruj|
|Czy nakłada się ona na inne zasady DLP Exchange lub Centrum zgodności?|Jeśli tak, czy można skonsolidować nakładające się zasady?|— Jeśli nakładają się na inne zasady Exchange, ręcznie utwórz skonsolidowane zasady DLP w centrum administracyjnym Exchange, a następnie użyj kreatora migracji. </br> — Jeśli pokrywają się one z istniejącymi zasadami Centrum zgodności, możesz zmodyfikować istniejące zasady Centrum zgodności tak, aby były zgodne, nie migrować Exchange wersji|
|Czy zasady Exchange DLP są ściśle ograniczone i czy mają dobrze zdefiniowane warunki, akcje, dołączenia i wykluczenia?|Jeśli tak, jest dobrym kandydatem do migracji za pomocą kreatora, zanotuj zasady, aby pamiętać, aby wrócić, aby usunąć je później|migrowanie za pomocą kreatora|

## <a name="migration"></a>Migracja

Po ocenie wszystkich zasad DLP centrum Exchange i zgodności pod kątem potrzeb i zgodności można użyć kreatora migracji.

1. Otwórz konsolę [DLP centrum zgodności Microsoft 365](https://compliance.microsoft.com/datalossprevention?viewid=policies).
2. Jeśli istnieją Exchange zasad DLP, które można migrować, w górnej części strony zostanie wyświetlony baner informujący o tym.
3. Wybierz **pozycję Migruj zasady** na banerze, aby otworzyć kreatora migracji. Wszystkie zasady Exchange DLP są wymienione. Nie można wybrać wcześniej zmigrowanych zasad.
4. Wybierz zasady, które chcesz migrować. Można je migrować pojedynczo lub w grupach przy użyciu podejścia etapowego lub wszystkich jednocześnie. Wybierz pozycję **Dalej**.
5. Przejrzyj okienko wysuwane pod kątem ostrzeżeń lub komunikatów. Rozwiąż wszelkie problemy przed kontynuowaniem.
6. Wybierz tryb, w który mają zostać utworzone nowe zasady Centrum zgodności, **Aktywne**, **Testowe** lub **Wyłączone**.  Wartość domyślna to **Test**. Wybierz pozycję **Dalej**.
7. W razie potrzeby można utworzyć więcej zasad opartych na zasadach Exchange DLP dla innych ujednoliconych lokalizacji DLP. Spowoduje to powstanie jednej nowej ujednoliconej zasady DLP dla zmigrowanych zasad Exchange i jednej nowej ujednoliconej zasady DLP dla innych lokalizacji, które wybierzesz tutaj.

   > [!IMPORTANT]
   > Wszelkie Exchange warunki zasad DLP i akcje, które nie są obsługiwane przez inne lokalizacje DLP, takie jak urządzenia, SharePoint, OneDrive, lokalne, MCAS lub Teams wiadomości czatu i kanału, zostaną usunięte z dodatkowych zasad. Ponadto istnieje praca wstępna, którą należy wykonać dla innych lokalizacji. Zobacz:
   >
   > - [Dowiedz się więcej o zapobieganiu utracie danych punktu końcowego Microsoft 365](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
   > - [Wprowadzenie do ochrony przed utratą danych punktu końcowego](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)
   > - [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
   > - [Dowiedz się więcej na temat lokalnego skanera Microsoft 365 zapobiegania utracie danych](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner)
   > - [Wprowadzenie z lokalnym skanerem zapobiegania utracie danych](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)
   > - [Używanie lokalnego skanera Microsoft 365 zapobiegania utracie danych](dlp-on-premises-scanner-use.md#use-the-microsoft-365-data-loss-prevention-on-premises-scanner)
   > - [Używanie zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)

8. Przejrzyj ustawienia sesji kreatora migracji. Wybierz pozycję **Dalej**.
9. Przejrzyj raport migracji. Zwróć uwagę na wszelkie błędy związane z Exchange regułami przepływu poczty. Można je naprawić i ponownie tworzyć skojarzone zasady.

Zmigrowane zasady będą teraz wyświetlane na liście zasad DLP w konsoli DLP Centrum zgodności.

## <a name="common-errors-and-mitigation"></a>Typowe błędy i środki zaradcze

|Komunikat o błędzie|Powodu|Środki zaradcze/zalecane kroki|
|---|---|---|
|Zasady zgodności o nazwie `<Name of the policy>` już istnieją w scenariuszach `Dlp`.|Prawdopodobnie ta migracja zasad została przeprowadzona wcześniej, a następnie ponownie zrekomplektowana w tej samej sesji|Odśwież sesję, aby zaktualizować listę zasad dostępnych do migracji. Wszystkie wcześniej zmigrowane zasady powinny być w `Already migrated` stanie.|
|Zasady zgodności o nazwie `<Name of the policy>` już istnieją w scenariuszach `Hold`.|Zasady przechowywania o tej samej nazwie istnieją w tej samej dzierżawie.|— Zmień nazwę zasad DLP w eac na inną nazwę. </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|`DLP-group@contoso.com` nie można użyć jako wartości warunku Udostępnione według, ponieważ jest to grupa dystrybucyjna lub grupa zabezpieczeń z obsługą poczty. Użyj opcji Udostępnione przez członka predykatu, aby wykrywać działania członków niektórych grup.|Reguły transportu zezwalają na użycie grup w warunku `sender is` , ale ujednolicony protokół DLP nie zezwala na to.|Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail grupy z warunku `sender is` i w razie potrzeby dodać grupę do warunku `sender is a member of` . Ponów próbę migracji dla zasad, których dotyczy problem|
|Nie można odnaleźć adresata `DLP-group@contoso.com`. Jeśli nowo utworzono, ponów próbę wykonania operacji po pewnym czasie. Jeśli usunięto lub wygasło, zresetuj prawidłowe wartości i spróbuj ponownie.|Prawdopodobnie adres grupy używany w `sender is a member of` warunku lub `recipient is a member of` wygasł lub jest nieprawidłowy.|— Usuń/zastąp wszystkie nieprawidłowe adresy e-mail grupy w regule transportu w centrum administracyjnym Exchange. </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|Wartością określoną w `FromMemberOf` predykatze musi być grupa zabezpieczeń z włączoną obsługą poczty e-mail.|Reguły transportu zezwalają na używanie poszczególnych użytkowników w warunku `sender is a member of` , ale ujednolicony protokół DLP na to nie zezwala.|— Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail poszczególnych użytkowników z warunku `sender is a member of` i w razie potrzeby dodać użytkowników do warunku `sender is` . </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|Wartością określoną w `SentToMemberOf` predykatze musi być grupa zabezpieczeń z włączoną obsługą poczty e-mail.|Reguły transportu zezwalają na używanie poszczególnych użytkowników pod warunkiem `recipient is a member of` , ale ujednolicone DLP nie zezwala na to.|— Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail poszczególnych użytkowników z warunku `recipient is a member of` i w razie potrzeby dodać użytkowników do warunku `recipient is` . </br> — Ponów próbę migracji dla zasad, których dotyczy problem.|
|Użycie parametru `<Name of condition>` jest obsługiwane tylko w przypadku Exchange. Usuń ten parametr lub włącz tylko Exchange lokalizacji.|Prawdopodobnie istnieją inne zasady o tej samej nazwie w Centrum zgodności z innymi lokalizacjami, takimi jak SPO/ODB/Teams, dla których wspomniany warunek nie jest obsługiwany.|Zmień nazwę zasad DLP w centrum administracyjnym Exchange i spróbuj ponownie przeprowadzić migrację.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Testowanie i walidacja <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

Testowanie i przeglądanie zasad.

1. Postępuj zgodnie z [procedurami testowania zasad DLP](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. Przejrzyj zdarzenia utworzone przez zasady w [Eksploratorze działań](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-365-unified-dlp"></a>Przejrzyj dopasowania zasad między Exchange DLP Centrum administracyjnego i Microsoft 365 Unified DLP

Aby upewnić się, że zmigrowane zasady zachowują się zgodnie z oczekiwaniami, możesz wyeksportować raporty z obu centrów administracyjnych i porównać dopasowania zasad.

1. Połączenie do [Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
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

1. Otwórz konsolę DLP centrum administracyjnego Exchange.
2. Dezaktywuj lub usuń zasady źródłowe.
3. Otwórz konsolę [DLP centrum zgodności Microsoft 365](https://compliance.microsoft.com/datalossprevention?viewid=policies) i wybierz zasady, które chcesz uaktywnić, aby je edytować.
4. Zmień stan na **Włącz**.

## <a name="related-articles"></a>Artykuły pokrewne

- [Exchange Online zasad ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Wprowadzenie za pomocą Eksploratora działań](data-classification-activity-explorer.md)
- [Tworzenie, testowanie i dostrajanie zasad DLP](create-test-tune-dlp-policy.md)
- [Twórz zasady DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
- [Exchange Online zasad ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
