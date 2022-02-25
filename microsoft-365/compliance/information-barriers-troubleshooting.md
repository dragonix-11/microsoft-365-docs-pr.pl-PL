---
title: Rozwiązywanie problemów z barierami informacyjnymi
description: Ten artykuł jest przewodnikiem po rozwiązywaniu problemów z barierami informacyjnymi.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: None
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: de415ba7b68df786ead038bb72465c445a86ba5a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2021
ms.locfileid: "62959548"
---
# <a name="troubleshooting-information-barriers"></a>Rozwiązywanie problemów z barierami informacyjnymi

[Bariery informacyjne mogą](information-barriers.md) pomóc Twojej organizacji zachować zgodność z wymaganiami prawnymi i przepisami branżowymi. Z barierami informacyjnymi można na przykład ograniczyć komunikację między określonymi grupami użytkowników, aby uniknąć konfliktu zainteresowań lub innych problemów. (Aby dowiedzieć się więcej na temat sposobu określania barier informacyjnych, zobacz Definiowanie [zasad dla barier informacyjnych](information-barriers-policies.md)).

W przypadku wystąpienia nieoczekiwanych problemów po wtargeniu barier informacyjnych można podjąć pewne kroki, aby rozwiązać te problemy. Skorzystaj z tego artykułu jako przewodnika.

> [!IMPORTANT]
> Aby wykonać zadania opisane w tym artykule, musisz mieć przypisaną odpowiednią rolę, taką jak jedna z następujących czynności:<br/>— Microsoft 365 Enterprise administrator globalny<br/>— administrator globalny<br/>- Administrator zgodności<br/>- Zarządzanie zgodnością IB (jest to nowa rola!)<p>Aby dowiedzieć się więcej o wymaganiach wstępnych dla barier informacyjnych, zobacz Wymagania wstępne (aby poznać zasady barier [informacyjnej).](information-barriers-policies.md#prerequisites)<p>Upewnij się, [że łączysz się z programem PowerShell & w Centrum zgodności](/powershell/exchange/connect-to-scc-powershell).

## <a name="issue-users-are-unexpectedly-blocked-from-communicating-with-others-in-microsoft-teams"></a>Problem: Użytkownicy mają nieoczekiwane zablokowanie komunikacji z innymi osobami w programie Microsoft Teams 

W takim przypadku osoby zgłaszają nieoczekiwane problemy dotyczące komunikowania się z innymi osobami w Microsoft Teams. Oto kilka przykładów:

- Użytkownik wyszukuje, ale nie może odnaleźć innego użytkownika w Microsoft Teams.
- Użytkownik może znaleźć innego użytkownika w programie Microsoft Teams, ale nie może go Microsoft Teams.
- Użytkownik może zobaczyć innego użytkownika, ale nie może wysyłać wiadomości do tego innego użytkownika w Microsoft Teams.

### <a name="what-to-do"></a>Co należy zrobić

Określ, czy na użytkowników mają wpływ zasady bariery informacyjnej. W zależności od konfiguracji zasad bariery informacyjne mogą działać zgodnie z oczekiwaniami. Może też być konieczne uściślinie zasad organizacji.

1. Użyj polecenia **cmdlet Get-InformationBarrierRecipientStatus** z parametrem Identity. 

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity` <p> Możesz użyć dowolnej wartości tożsamości, która jednoznacznie identyfikuje każdego adresata, takiego jak Nazwa, Alias, Nazwa wyróżniająca (DN), Kanonic DN, Adres e-mail lub Identyfikator GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb` <p> W tym przykładzie używamy aliasu (*meganb*) dla parametru Identity. To polecenie cmdlet zwróci informacje wskazujące, czy na użytkownika mają wpływ zasady bariery informacyjnej. (Poszukaj *ExoPolicyId: \<GUID>.) |

    **Jeśli użytkownicy nie są uwzględniani w zasadach bariery informacyjnej, skontaktuj się z pomocą techniczną**. W przeciwnym razie przejdź do następnego kroku.

2. Dowiedz się, jakie segmenty uwzględniono w zasadach bariery informacyjnej. W tym celu użyj polecenia `Get-InformationBarrierPolicy` cmdlet z parametrem Identity. 

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Get-InformationBarrierPolicy` <p> Użyj szczegółów, takich jak identyfikator GUID zasad (ExoPolicyId), który otrzymano w poprzednim kroku, jako wartość tożsamości. | `Get-InformationBarrierPolicy -Identity b42c3d0f-49e9-4506-a0a5-bf2853b5df6f` <p> W tym przykładzie są dostępne szczegółowe informacje dotyczące zasad bariery informacyjnej dotyczących usługi ExoPolicyId *b42c3d0f-49e9-4506-a0a5-bf2853b5df6f*. |

    Po uruchomieniu polecenia cmdlet w wynikach odszukaj wartości **AssignedSegment**, **SegmentsAllowed** i **SegmentsBlocked** .

    Na przykład po uruchomieniu polecenia `Get-InformationBarrierPolicy` cmdlet na liście wyników przedstawiono następujące informacje:

    ```powershell
    AssignedSegment : Sales
    SegmentsAllowed : {}
    SegmentsBlocked : {Research}
    ```

    W tym przypadku widać, że zasady bariery informacyjnej wpływają na ludzi, którzy znajdują się w segmentach Sprzedaż i Badania. W tym przypadku osoby z działu sprzedaży nie mogą komunikować się z osobami w zakresie badań.

    Jeśli wydaje się to poprawne, bariery informacyjne działają zgodnie z oczekiwaniami. W przeciwnym wypadku przejdź do następnego kroku.

3. Upewnij się, że segmenty zostały poprawnie zdefiniowane. W tym celu użyj polecenia `Get-OrganizationSegment` cmdlet i przejrzyj listę wyników.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Get-OrganizationSegment`<p> Użyj tego polecenia cmdlet z parametrem Identity. | `Get-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <p> W tym przykładzie są dostępne informacje dotyczące segmentu o identyfikatorze GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

    Przejrzyj szczegóły segmentu. W razie potrzeby [edytuj segment, a](information-barriers-edit-segments-policies.md#edit-a-segment) następnie ponownie użyj polecenia `Start-InformationBarrierPoliciesApplication` cmdlet.

    **Jeśli nadal masz problemy z zasadami bariery informacyjnej, skontaktuj się z pomocą techniczną**.

## <a name="issue-communications-are-allowed-between-users-who-should-be-blocked-in-microsoft-teams"></a>Problem: Dozwolone jest komunikacja między użytkownikami, którzy powinni zostać zablokowani w Microsoft Teams

W tym przypadku, chociaż bariery informacyjne są określone, aktywne i stosowane, osoby, które nie powinny się ze sobą komunikować, są w jakiś sposób w stanie rozmawiać ze sobą i do siebie dzwonić Microsoft Teams.

### <a name="what-to-do"></a>Co należy zrobić

Sprawdź, czy dane użytkownicy są dostępni do zasad bariery informacyjnej. 

1. Używanie **polecenia cmdlet Get-InformationBarrierRecipientStatus** z parametrami tożsamości.

    |**Składnia** _|_ *Example**|
    |:----------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, na przykład nazwy, aliasu, nazwy odróżnianej, kanonicznego nazwy domeny, adresu e-mail lub identyfikatora GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> W tym przykładzie używamy dwóch kont użytkowników w aplikacji Office 365: *meganb* dla *Megan* i *alexy dla* *Alexy*. |

    > [!TIP]
    > Możesz także użyć tego polecenia cmdlet dla jednego użytkownika: `Get-InformationBarrierRecipientStatus -Identity <value>`

2. Przejrzyj ustalenia. Polecenie **cmdlet Get-InformationBarrierRecipientStatus** zwraca informacje o użytkownikach, takie jak wartości atrybutów i wszelkie stosowane zasady bariery informacyjnej.

    Przejrzyj wyniki, a następnie zrób tak, jak to opisano w poniższej tabeli:

    |**Wyniki**|**Co zrobić dalej**|
    |:----------|:------------------|
    | Nie wymieniono żadnych segmentów dla wybranych użytkowników. | Wykonaj jeden z następujących kroków:<br/>— Przypisać użytkowników do istniejącego segmentu, edytując ich profile w Azure Active Directory. (Zobacz [Konfigurowanie właściwości konta użytkownika za pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)).<br/>— Zdefiniowanie segmentu przy użyciu [obsługiwanego atrybutu dla barier informacyjnych](information-barriers-attributes.md). Następnie [zdefiniuj nowe zasady](information-barriers-policies.md#part-2-define-information-barrier-policies) lub [edytuj istniejące zasady, aby](information-barriers-edit-segments-policies.md#edit-a-policy) uwzględnić ten segment. |
    | Segmenty są wymienione, ale do tych segmentów nie są przypisywane żadne zasady informacyjne | Wykonaj jeden z następujących kroków:<br/>- [Definiowanie nowych zasad bariery informacyjnej](information-barriers-policies.md#part-2-define-information-barrier-policies) dla każdego segmentu <br/>- [Edytowanie istniejących zasad bariery informacyjnej](information-barriers-edit-segments-policies.md#edit-a-policy) w celu przypisania ich do właściwego segmentu |
    | Segmenty są wymienione na liście, a każdy z nich jest uwzględniany w zasadach bariery informacyjnej | - Uruchom polecenie `Get-InformationBarrierPolicy` cmdlet, aby sprawdzić, czy zasady bariery informacyjnej są aktywne<br/>- Uruchom polecenie `Get-InformationBarrierPoliciesApplicationStatus` cmdlet, aby potwierdzić zastosowanie zasad<br/>- Uruchom polecenie `Start-InformationBarrierPoliciesApplication` cmdlet, aby zastosować wszystkie zasady bariery informacyjnej aktywnej |

## <a name="issue-i-need-to-remove-a-single-user-from-an-information-barrier-policy"></a>Problem: muszę usunąć jednego użytkownika z zasad bariery informacyjnej

W takim przypadku zasady barier informacyjnej są już obowiązywać i jeden lub więcej użytkowników ma nieoczekiwane zablokowanie komunikacji z innymi osobami w Microsoft Teams. Zamiast całkowicie usuwać zasady barier informacyjnej, możesz usunąć jednego lub wielu użytkowników z zasad bariery informacyjnej.

### <a name="what-to-do"></a>Co należy zrobić

Zasady barier informacyjnej przypisywane są segmentom użytkowników. Segmenty są definiowane za pomocą określonych [atrybutów w profilach kont użytkowników](information-barriers-attributes.md). Jeśli musisz usunąć zasady od jednego użytkownika, rozważ edytowanie profilu tego użytkownika w programie Azure Active Directory tak, aby ten użytkownik nie był już uwzględniony w segmentze, na który mają wpływ bariery informacyjne.

1. Używanie **polecenia cmdlet Get-InformationBarrierRecipientStatus** z parametrami tożsamości. To polecenie cmdlet zwraca informacje o użytkownikach, takie jak wartości atrybutów i wszelkie stosowane zasady informacyjne.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, na przykład nazwy, aliasu, nazwy odróżnianej, kanonicznego nazwy domeny, adresu e-mail lub identyfikatora GUID. | `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> W tym przykładzie używamy dwóch kont użytkowników w aplikacji Office 365: *meganb* dla *Megan* i *alexy dla* *Alexy*.          |
    | `Get-InformationBarrierRecipientStatus -Identity <value>` <p> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje użytkownika, na przykład nazwy, aliasu, nazwy odróżnianej, kanonicznego nazwy domeny, adresu e-mail lub identyfikatora GUID.|`Get-InformationBarrierRecipientStatus -Identity jeanp`<p> W tym przykładzie używamy jednego konta w programie Office 365: *marcin*. |

2. Przejrzyj wyniki, aby sprawdzić, czy są przypisane zasady bariery informacyjnej i do jakich segmentów należy użytkownik.

3. Aby usunąć użytkownika z segmentu, na który mają wpływ bariery [informacyjne, zaktualizuj](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) informacje o profilu użytkownika w Azure Active Directory.

4. Poczekaj około 30 minut na wystąpień protokołu FwdSync. Możesz też uruchomić polecenie `Start-InformationBarrierPoliciesApplication` cmdlet, aby zastosować wszystkie zasady bariery informacyjnej aktywnej.

## <a name="issue-the-information-barrier-application-process-is-taking-too-long"></a>Problem: proces tworzenia aplikacji z barierą informacyjną trwa zbyt długo

Po **uruchomieniu polecenia cmdlet Start-InformationBarrierPoliciesApplication** proces ten trwa bardzo długo.

### <a name="what-to-do"></a>Co należy zrobić

Pamiętaj, że po uruchomieniu polecenia cmdlet aplikacji zasad stosowane (lub usuwane) zasady barier informacyjnej są stosowane przez użytkowników do wszystkich kont w organizacji. Jeśli masz wielu użytkowników, ich przetwarzanie zajmie trochę czasu. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

1. Aby sprawdzić stan najnowszej aplikacji zasad, użyj polecenia cmdlet **Get-InformationBarrierPoliciesApplicationStatus** .

    |**Aby wyświetlić najnowszą aplikację zasad**|**Aby wyświetlić stan wszystkich aplikacji zasad**|
    |:---------------------------------------------|:---------------------------------------------|
    | `Get-InformationBarrierPoliciesApplicationStatus` | `Get-InformationBarrierPoliciesApplicationStatus -All $true` |

    Spowoduje to wyświetlenie informacji o tym, czy aplikacja zasad została ukończona, nie powiodła się, czy jest w toku.

2. W zależności od wyników poprzedniego kroku, zrób tak:
  
    |**Stan**|**Następny krok**|
    |:---------|:------------|
    | **Nie rozpoczęto** | Jeśli od czasu uruchomienia polecenia cmdlet **Start-InformationBarrierPoliciesApplication** mi zostało uruchomione więcej niż 45 minut, przejrzyj dziennik inspekcji, aby sprawdzić, czy w definicjach zasad występują błędy lub z innego powodu, dla którego aplikacja nie została uruchomiona. |
    | **Zakończone niepowodzeniem** | Jeśli aplikacja nie powiodła się, przejrzyj dziennik inspekcji. Przejrzyj też segmenty i zasady. Czy jakichkolwiek użytkowników przypisano do więcej niż jednego segmentu? Czy jakieś segmenty mają przypisaną więcej niż jedną polikość? W razie potrzeby edytuj [segmenty](information-barriers-edit-segments-policies.md#edit-a-segment) i [/lub edytuj](information-barriers-edit-segments-policies.md#edit-a-policy) zasady, a następnie ponownie uruchom polecenie cmdlet **Start-InformationBarrierPoliciesApplication** . |
    | **W toku** | Jeśli aplikacja jest nadal w toku, miej więcej czasu na jej ukończenie. Jeśli mi było kilka dni, zbierz dzienniki inspekcji, a następnie skontaktuj się z pomocą techniczną. |

## <a name="issue-information-barrier-policies-are-not-being-applied-at-all"></a>Problem: zasady barier informacyjnej w ogóle nie są stosowane

W tym przypadku zdefiniowano segmenty, zasady bariery informacyjnej i próbowano je zastosować. Jednak po uruchomieniu polecenia `Get-InformationBarrierPoliciesApplicationStatus` cmdlet można zobaczyć, że aplikacja zasad nie powiodła się.

### <a name="what-to-do"></a>Co należy zrobić

Upewnij się, że w Twojej organizacji nie są [Exchange zasady książki adresowej](/exchange/address-books/address-book-policies/address-book-policies). Takie zasady uniemożliwiają zastosowanie zasad bariery informacyjnej.

1. Połączenie do [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie [cmdlet Get-AddressBookPolicy](/powershell/module/exchange/get-addressbookpolicy) i przejrzyj wyniki.

    |**Wyniki**|**Następny krok**|
    |:----------|:------------|
    | Exchange są wymienione zasady książki adresowej | [Usuwanie zasad książki adresowej](/exchange/address-books/address-book-policies/remove-an-address-book-policy) |
    | Nie istnieją żadne zasady książki adresowej |Przejrzyj dzienniki inspekcji, aby dowiedzieć się, dlaczego aplikacja zasad nie może się pomylić |

3. [Wyświetlanie stanu kont użytkowników, segmentów, zasad lub aplikacji zasad](information-barriers-policies.md#view-status-of-user-accounts-segments-policies-or-policy-application).

## <a name="issue-information-barrier-policy-not-applied-to-all-designated-users"></a>Problem: zasady barier informacyjnej nie mają zastosowania do wszystkich wyznaczonych użytkowników

Po zdefiniowanych segmentach, zdefiniowanych zasadach barier informacyjnych i próbie zastosowania tych zasad może się okazać, że zasady te mają zastosowanie do niektórych adresatów, ale nie do innych.
Po uruchomieniu polecenia `Get-InformationBarrierPoliciesApplicationStatus` cmdlet wyszukaj w wyniku tekst w ten sposób.

> Tożsamość: `<application guid>`
>
> Łączna liczba adresatów: 81527
>
> Adresaci, których nie powiodło się: 2
>
> Kategoria niepowodzenia: Brak
>
> Stan: Ukończone

### <a name="what-to-do"></a>Co należy zrobić

1. Wyszukaj w dzienniku inspekcji .`<application guid>` Możesz skopiować ten kod programu PowerShell i zmodyfikować zmienne.

```powershell
$DetailedLogs = Search-UnifiedAuditLog -EndDate <yyyy-mm-ddThh:mm:ss>  -StartDate <yyyy-mm-ddThh:mm:ss> -RecordType InformationBarrierPolicyApplication -ResultSize 1000 |?{$_.AuditData.Contains(<application guid>)} 
```

2. Sprawdź w szczegółowych danych wyjściowych dziennika inspekcji wartości pól `"UserId"` i `"ErrorDetails"` . W ten sposób możesz podać przyczynę niepowodzenia. Możesz skopiować ten kod programu PowerShell i zmodyfikować zmienne.

```powershell
   $DetailedLogs[1] |fl
```

Przykład:

> "UserId": Użytkownik1
>
>"ErrorDetails":"Status: IBPolicyConflict. Błąd: W przypadku segmentu IB "identyfikator1" i segment IB "identyfikator segmentu 2" występuje konflikt i nie można go przypisać do adresata.

3. Zazwyczaj użytkownik został uwzględniony w więcej niż jednym segmencie. Ten problem można rozwiązać, aktualizując wartość w `-UserGroupFilter` `OrganizationSegments`.

4. Ponowne stosowanie zasad barier informacyjnych przy użyciu tych procedur — zasad [barier informacyjnych](information-barriers-policies.md#part-3-apply-information-barrier-policies).

## <a name="resources"></a>Zasoby

- [Definiowanie zasad dla barier informacyjnych w Microsoft Teams](information-barriers-policies.md)
- [Bariery informacyjne](information-barriers.md)