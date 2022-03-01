---
title: Migrowanie Exchange Online zasad ochrony przed utratą danych do Centrum zgodności
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
description: Dowiedz się, jak zaplanować i przeprowadzić migrację twoich Exchange ochrony przed utratą danych online do usługi Microsoft 365 DLP.
ms.openlocfilehash: 07d0eb19155a7f91b30feb8d7938ea574b0e75f9
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019335"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-compliance-center"></a>Migrowanie Exchange Online zasad ochrony przed utratą danych do Centrum zgodności

[Exchange Online ochrony przed utratą danych (DLP, data loss prevention)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) są przestarzałe. [Znacznie bogatsza funkcja ochrony przed dlp](dlp-learn-about-dlp.md), w tym funkcja Exchange Online DLP, jest dostępna w centrum zgodności usługi [Microsoft 365 zgodności](https://compliance.microsoft.com/datalossprevention?viewid=policies). Kreator migracji zasad DLP pomoże Ci przejść do Exchange Online zasad DLP do centrum zgodności, w którym będziesz nimi zarządzać.

Kreator migracji działa, odczytując konfigurację zasad DLP w programie Exchange a następnie tworząc zduplikowane zasady w Centrum zgodności. Domyślnie kreator tworzy nowe wersje zasad w trybie testowania, aby  można było zobaczyć, jaki wpływ będą miały te zasady na środowisko bez wymuszania żadnych akcji. Gdy wszystko będzie gotowe do pełnego przejścia do wersji Centrum zgodności, **_musisz_**:

1. Dezaktywuj lub usuń zasady źródłowe w Centrum Exchange administracyjnego usługi .
1. Edytuj wersję zasad w Centrum zgodności i zmień jej stan z **Test na** **Wymuszanie**. 

> [!WARNING]
> Jeśli zasady źródłowe nie zostaną usunięte lub dezaktywowane w Centrum zgodności przed ustawieniem w Centrum zgodności ustawienia Wymuszaj oba zestawy zasad będą próbować wymusić akcje i otrzymasz zduplikowane zdarzenia. **_To nieobsługiwana konfiguracja._**


Kreator migracji migruje tylko zasady EXO i skojarzone reguły przepływu poczty. Autonomiczne Exchange przepływu poczty e-mail nie są migrowane.

## <a name="migration-workflow"></a>Przepływ pracy migracji

Istnieją cztery fazy migracji zasad DLP z usługi Exchange do ujednoliconej konsoli zarządzania DLP w Centrum zgodności.  

1. Przygotowywanie do migracji
    1. Oceń i porównaj zasady DLP Exchange Online (EXO) i zasady DLP Centrum zgodności pod celu zapewnienia zduplikowanych funkcji.
    1. Zdecyduj, które zasady DLP serwera EXO chcesz przenieść dokładnie tak, jak są, możesz przeprowadzić migrację tych zasad za pomocą kreatora.
    1. Zdecyduj, które zasady DLP usługi EXO chcesz skonsolidować i skonsolidować w centrum administracyjnym usługi Exchange, a następnie przenios je do Centrum zgodności za pomocą kreatora migracji.
1. Przeprowadzanie migracji — korzystanie z kreatora
1. Testowanie i sprawdzanie poprawności — sprawdzenie wyników
1. Aktywowanie migrowanych zasad

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="licensing-and-versions"></a>Licencjonowanie i wersje

Przed rozpoczęciem migracji zasad DLP należy potwierdzić [Microsoft 365 subskrypcję](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) i dodatki. 

Aby uzyskać dostęp do kreatora migracji zasad i korzystać z niego, musisz mieć jedną z tych subskrypcji lub dodatków

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 zgodności
- Microsoft 365 A5 zgodności
- Microsoft 365 E5 i zarządzanie informacjami
- Microsoft 365 A5 i zarządzanie informacjami

Aby uzyskać szczegółową listę wymagań licencjonowania dotyczących ochrony przed utratą danych, zobacz Microsoft 365 licencjonowania w celu zapewnienia zgodności z & [i ochrony przed utratą danych.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)


### <a name="permissions"></a>Uprawnienia

Konto służące do uruchamiania kreatora migracji musi mieć dostęp zarówno do strony DLP konsoli administracyjnej usługi Exchange, jak i do ujednoliconej konsoli DLP w Centrum zgodności.

## <a name="prepare-for-migration"></a>Przygotowywanie do migracji

1. Jeśli nie wiesz, jak stosować zasady DLP, konsolę DLP centrum zgodności lub konsolę DLP centrum administracyjnego programu Exchange, zapoznaj się z tym programem przed podjęciem próby migracji zasad.
    1. [Exchange Online ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Dowiedz się więcej Microsoft 365 ochrony przed utratą danych w punktach końcowych](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
    1. [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
1. Oceń swoje Exchange zasad DLP i Centrum zgodności, zadając następujące pytania:


|Pytanie  |Akcja  | Procedura migracji|
|---------|---------|---------|
|Czy zasady są nadal potrzebne?    |Jeśli nie jest, usuń ją lub dezaktywuj |nie przeprowadzaj migracji|
|Czy pokrywa się ono z innymi zasadami DLP Exchange centrum zgodności?     |Jeśli tak, czy można skonsolidować nakładające się zasady?         |— Jeśli te zasady nakładają się Exchange, ręcznie utwórz skonsolidowane zasady DLP w centrum administracyjnym usługi Exchange, a następnie użyj kreatora migracji. </br> — Jeśli zasady te nakładają się na istniejące zasady Centrum zgodności, możesz zmodyfikować istniejące zasady Centrum zgodności, aby je dopasować, nie migrować Exchange wersji|
|Czy zasady Exchange DLP są ściśle określone i czy mają dobrze zdefiniowane warunki, działania, dołączenia i wykluczenia?     |Jeśli tak, dobrym rozwiązaniem jest przeprowadzenie migracji za pomocą kreatora, zanotuj zasady, aby pamiętać o ich późniejszym usunięciu.         | migrowanie przy użyciu kreatora|

## <a name="migration"></a>Migracja

Po zakończeniu oceny potrzeb i zgodności wszystkich zasad DLP Exchange Centrum zgodności można użyć kreatora migracji.

1. Otwórz [konsolę DLP Microsoft 365 Centrum](https://compliance.microsoft.com/datalossprevention?viewid=policies) zgodności.
2. Jeśli istnieją Exchange DLP, które można migrować, u góry strony zostanie wyświetlony transparent z powiadomieniem.
3. Wybierz **pozycję Migracja** zasad w banerze, aby otworzyć kreatora migracji. Zostaną wyświetlone Exchange zasad DLP. Nie można wybrać wcześniej migrowanych zasad.
4. Wybierz zasady, które chcesz zmigrować. Można je migrować pojedynczo lub w grupach, stosując podejście etapowe lub wszystkie jednocześnie. Wybierz pozycję **Dalej**.
5. Przejrzyj okienko wysuwu dla wszystkich ostrzeżeń i wiadomości. Przed przystąpieniem do tej procedury rozwiąż wszelkie problemy.
6. Wybierz tryb, w którym chcesz tworzyć nowe zasady Centrum **zgodności, Aktywne**, **Testowe** lub **Wyłączone**.  Wartość domyślna to **Test**. Wybierz pozycję **Dalej**.
7. W razie potrzeby możesz utworzyć więcej zasad, które są oparte na Exchange DLP dla innych ujednoliconych lokalizacji zasad DLP. Spowoduje to jeden nowy, ujednolicony zasady DLP dla migrowanych zasad ochrony przed Exchange i jedną nową, ujednoliconą politykę DLP dla innych lokalizacji, które wybierzemy tutaj.

> [!IMPORTANT]
> Wszelkie Exchange zasad DLP, które nie są obsługiwane przez inne lokalizacje ochrony przed DLP, takie jak Urządzenia, SharePoint, OneDrive, Lokalne, MCAS lub Teams czaty i wiadomości kanałów zostaną usunięte z dodatkowych zasad. Ponadto są dostępne wstępne prace, które należy wykonać w innych lokalizacjach. Zobacz:
>- [Dowiedz się więcej Microsoft 365 ochrony przed utratą danych w punktach końcowych](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
>- [Wprowadzenie do ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)
>- [Korzystanie z ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
>- [Dowiedz się więcej Microsoft 365 ochrony przed utratą danych w środowisku lokalnym](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Wprowadzenie do lokalnego skanera ochrony przed utratą danych](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)
>- [Używanie skanera Microsoft 365 ochrony przed utratą danych](dlp-on-premises-scanner-use.md#use-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Korzystanie z zasad ochrony przed utratą danych dla aplikacji w chmurze innych niż firmy Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)
 
8. Przejrzyj ustawienia sesji kreatora migracji. Wybierz pozycję **Dalej**.
9. Przejrzyj raport o migracji. Zwróć uwagę na wszelkie błędy obejmujące Exchange przepływu poczty. Możesz je naprawić i ponownie zmigrować skojarzone zasady.

Zmigrowane zasady pojawią się teraz na liście zasad DLP w konsoli DLP centrum zgodności. 

## <a name="common-errors-and-mitigation"></a>Typowe błędy i środki zaradcze
|Komunikat o błędzie  |Przyczyna  | Środki zaradcze/zalecane kroki|
|---------|---------|---------|
|Zasady zgodności o nazwie już `<Name of the policy>` istnieją w scenariuszach `Dlp`.    |Prawdopodobnie ta migracja zasad została wykonana wcześniej, a następnie ponownie opanowana w tej samej sesji |Odśwież sesję, aby zaktualizować listę zasad dostępnych do migracji. Wszystkie wcześniej migrowane zasady powinny mieć stan `Already migrated` .|
|Zasady zgodności o nazwie już `<Name of the policy>` istnieją w scenariuszach `Hold`.     |Zasady przechowywania o tej samej nazwie istnieją w tej samej dzierżawie.       |— Zmienić nazwę zasad DLP w Aplikacji EAC na inną. </br> — Ponów próbę migracji w przypadku tych zasad. |
|`DLP-group@contoso.com` nie można użyć jako wartości warunku Udostępnione przez, ponieważ jest to grupa dystrybucyjna lub grupa zabezpieczeń z obsługą poczty. Użyj funkcji Udostępnione przez członka predykatu, aby wykryć działania członków pewnych grup.     |Reguły transportu umożliwiają zastosowanie grup w `sender is` tym warunku, ale ujednolicone zasady DLP na to nie zezwalają.         | Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail `sender is` `sender is a member of` grupy z warunku i w razie potrzeby dodać grupę do warunku. Ponowna próby migracji dla zasad, których migracja może wpłynąć|
|Nie można odnaleźć adresata `DLP-group@contoso.com`. Jeśli zostanie nowo utworzony, spróbuj ponownie później. Jeśli pliki zostały usunięte lub wygasły, zresetuj je z prawidłowymi wartościami i spróbuj ponownie.     |Prawdopodobnie adres grupy `sender is a member of` `recipient is a member of` użyty w tym warunku wygasł lub jest nieprawidłowy.         | — Usunąć/zamienić wszystkie nieprawidłowe adresy e-mail grupy w  regułę transportu w Exchange administracyjnego. </br> — Ponów próbę migracji w przypadku tych zasad.|
|Wartość określona w o `FromMemberOf` predykatu musi być grupą zabezpieczeń z włączoną obsługą poczty.     |Reguły transportu umożliwiają zastosowanie poszczególnych użytkowników `sender is a member of` w warunku, ale ujednolicone zasady DLP nie zezwalają na to.         | — Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail poszczególnych `sender is a member of` `sender is` użytkowników z warunku i w razie potrzeby dodać użytkowników do warunku. </br> — Ponów próbę migracji w przypadku tych zasad.|
|Wartość określona w o `SentToMemberOf` predykatu musi być grupą zabezpieczeń z włączoną obsługą poczty.    |Reguły transportu umożliwiają zastosowanie poszczególnych użytkowników pod `recipient is a member of` warunkiem, ale ujednolicone zasady DLP na to nie zezwalają.         | — Zaktualizuj regułę transportu, aby usunąć wszystkie adresy e-mail poszczególnych `recipient is a member of` `recipient is` użytkowników z warunku i w razie potrzeby dodać użytkowników do warunku. </br> — Ponów próbę migracji w przypadku tych zasad.|
|Używanie parametru `<Name of condition>` jest obsługiwane tylko w przypadku Exchange. Usuń ten parametr lub włącz tylko Exchange lokalizacji.         | Prawdopodobnie w Centrum zgodności istnieją inne zasady o tej samej nazwie z innymi lokalizacjami, na przykład SPO/ODB/Teams, dla których wymieniony warunek nie jest obsługiwany. | Zmień nazwę zasad DLP Exchange centrum administracyjnym i ponów próbę migracji.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Testowanie i sprawdzanie poprawności <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

Przetestuj i przejrzyj zasady.

1. Postępuj zgodnie [z procedurami Test zasad DLP](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. Przejrzyj zdarzenia utworzone przez zasady w [Eksploratorze aktywności](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-365-unified-dlp"></a>Przejrzyj dopasowania zasad między centrum Exchange administracyjnym DLP a ujednoliconą zasadą DLP Microsoft 365 ujednoliconym

Aby upewnić się, że zmigrowane zasady działają zgodnie z oczekiwaniami, możesz wyeksportować raporty zarówno z centrów a administracji, jak i porównać dopasowania zasad.

1. Połączenie do [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. [Wyeksportuj raport zasad DLP EAC](/powershell/module/exchange/get-maildetaildlppolicyreport). Możesz skopiować to polecenie cmdlet i wstawić odpowiednie wartości:

```powershell
Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv"> 
```

3. [Wyeksportuj raport funkcji Unified DLP](/powershell/module/exchange/get-dlpdetailreport). Możesz skopiować to polecenie cmdlet i wstawić odpowiednie wartości:

```powershell
Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">  
```

## <a name="activate-your-migrated-policies"></a>Aktywowanie migrowanych zasad

Po zakończeniu działania zmigrowanych zasad możesz ustawić ich **wymuszanie**.

1. Otwórz konsolę DLP centrum Exchange administracyjnego.
2. Dezaktywuj lub usuń zasady źródłowe.
3. Otwórz [konsolę DLP](https://compliance.microsoft.com/datalossprevention?viewid=policies) centrum zgodności usługi Microsoft 365 i wybierz zasady, które chcesz aktywnie edytować.
4. Zmień stan na **Włącz**.

## <a name="related-articles"></a>Artykuły pokrewne

- [Exchange Online ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
- [Exchange Online ochrony przed utratą danych (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
