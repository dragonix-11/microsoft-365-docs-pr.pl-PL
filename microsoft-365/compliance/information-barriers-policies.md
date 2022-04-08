---
title: Wprowadzenie do barier informacyjnych
description: Dowiedz się, jak rozpocząć pracę z barierami informacyjnymi.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fb6de09c0c020631f42d8f2f09cb236affb94417
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713542"
---
# <a name="get-started-with-information-barriers"></a>Wprowadzenie do barier informacyjnych

Dzięki barierom informacyjnym można zdefiniować zasady, które mają uniemożliwiać niektórym segmentom użytkowników komunikowanie się ze sobą lub zezwalać określonym segmentom na komunikowanie się tylko z niektórymi innymi segmentami. Zasady barier informacyjnych mogą pomóc organizacji w zachowaniu zgodności z odpowiednimi standardami i przepisami branżowymi oraz uniknąć potencjalnych konfliktów interesów. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o barierach informacyjnych](information-barriers.md).

W tym artykule opisano sposób konfigurowania zasad barier informacyjnych. Jest zaangażowanych kilka kroków, dlatego przed rozpoczęciem konfigurowania zasad bariery informacyjnej należy zapoznać się z całym procesem.

> [!TIP]
> Ten artykuł zawiera [przykładowy scenariusz](#example-scenario-contosos-departments-segments-and-policies) ułatwiający planowanie i definiowanie zasad barier informacyjnych.

## <a name="concepts"></a>Pojęcia

Podczas definiowania zasad dla barier informacyjnych będziesz pracować z atrybutami konta użytkownika, segmentami, zasadami "blokuj" i/lub "zezwalaj" oraz aplikacją zasad.

- Atrybuty konta użytkownika są definiowane w Azure Active Directory (lub Exchange Online). Te atrybuty mogą obejmować dział, stanowisko, lokalizację, nazwę zespołu i inne szczegóły profilu zadania.
- Segmenty to zestawy użytkowników zdefiniowanych w Centrum zgodności platformy Microsoft 365 przy użyciu wybranego **atrybutu konta użytkownika**. (Zobacz [listę obsługiwanych atrybutów](information-barriers-attributes.md)).
- Zasady barier informacyjnych określają limity lub ograniczenia komunikacji. Podczas definiowania zasad bariery informacyjnej wybierasz spośród dwóch rodzajów zasad:
  - *Zasady blokowe* uniemożliwiają komunikację jednego segmentu z innym segmentem.
  - *Zezwalaj zasadom* na komunikowanie się z jednym segmentem tylko z niektórymi innymi segmentami.
- Aplikacja zasad jest wykonywana po zdefiniowaniu wszystkich zasad barier informacyjnych i możesz je zastosować w organizacji.

## <a name="configuration-at-a-glance"></a>Konfiguracja w skrócie

| **Kroki** | **Co się dzieje** |
|:------|:----------------|
| **Krok 1**. [Upewnij się, że zostały spełnione wymagania wstępne](#step-1-make-sure-prerequisites-are-met) | — Sprawdź, czy masz [wymagane licencje i uprawnienia](information-barriers.md#required-licenses-and-permissions)<br/>— Sprawdź, czy katalog zawiera dane dotyczące segmentowania użytkowników<br/>— Włącz [wyszukiwanie według nazwy dla Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>— Upewnij się, że rejestrowanie inspekcji jest włączone<br/>- Upewnij się, że nie obowiązują żadne zasady Exchange książki adresowej<br/>— Korzystanie z programu PowerShell (podano przykłady)<br/>— Udzielanie zgody administratora na Microsoft Teams (kroki są uwzględnione) |
| **Krok 2**. [Segmentuj użytkowników w organizacji](#step-2-segment-users-in-your-organization) | — Określanie, jakie zasady są potrzebne<br/>— Tworzenie listy segmentów do zdefiniowania<br/>— Określanie atrybutów do użycia<br/>— Definiowanie segmentów pod względem filtrów zasad |
| **Krok 3**. [Definiowanie zasad barier informacyjnych](#step-3-define-information-barrier-policies) | — Definiowanie zasad (nie są jeszcze stosowane)<br/>- Wybierz jeden z dwóch rodzajów (blokuj lub zezwalaj) |
| **Krok 4**. [Stosowanie zasad barier informacyjnych](#step-4-apply-information-barrier-policies) | — Ustawianie stanu aktywnego zasad<br/>— Uruchamianie aplikacji zasad<br/>— Wyświetlanie stanu zasad |
| **Krok 5**. [Konfiguracja barier informacyjnych na SharePoint i OneDrive (opcjonalnie)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | — Konfigurowanie barier informacyjnych dla SharePoint i OneDrive |
| **Krok 6**. [Tryby barier informacyjnych (opcjonalnie)](#step-6-information-barriers-modes) | - Zaktualizuj tryby bariery informacyjnej, jeśli ma to zastosowanie |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Krok 1. Upewnij się, że zostały spełnione wymagania wstępne

Oprócz [wymaganych licencji i uprawnień](information-barriers.md#required-licenses-and-permissions) przed skonfigurowaniem barier informacyjnych upewnij się, że spełnione są następujące wymagania:

- **Dane katalogu**: upewnij się, że struktura organizacji jest odzwierciedlona w danych katalogu. Aby wykonać tę akcję, upewnij się, że atrybuty konta użytkownika, takie jak członkostwo w grupie, nazwa działu itp., są poprawnie wypełniane w Azure Active Directory (lub Exchange Online). Aby dowiedzieć się więcej, zobacz następujące zasoby:
  - [Atrybuty zasad bariery informacyjnej](information-barriers-attributes.md)
  - [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Konfigurowanie właściwości konta użytkownika za pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Wyszukiwanie w katalogu o określonym zakresie**: przed zdefiniowaniem pierwszych zasad bariery informacyjnej w organizacji należy [włączyć wyszukiwanie katalogów o określonym zakresie w Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). Poczekaj co najmniej 24 godziny po włączeniu wyszukiwania w katalogu o określonym zakresie, zanim skonfigurujesz lub zdefiniujesz zasady bariery informacyjnej.

- **licencje Exchange Online**: zasady barier informacyjnych działają tylko wtedy, gdy użytkownikom docelowym przypisano licencję Exchange Online.

- **Sprawdź, czy rejestrowanie inspekcji jest włączone**: aby wyszukać stan aplikacji zasad, należy włączyć rejestrowanie inspekcji. Inspekcja jest domyślnie włączona dla organizacji Microsoft 365. Niektóre organizacje mogły wyłączyć inspekcję z określonych powodów. Jeśli inspekcja jest wyłączona dla Twojej organizacji, może to być spowodowane tym, że inny administrator wyłączył tę inspekcję. Zalecamy potwierdzenie, że podczas wykonywania tego kroku można ponownie włączyć inspekcję. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania dziennika inspekcji](turn-audit-log-search-on-or-off.md).

- **Brak zasad książki adresowej**: Przed zdefiniowaniem i zastosowaniem zasad barier informacyjnych upewnij się, że nie obowiązują żadne zasady Exchange książki adresowej. Bariery informacyjne są oparte na zasadach książki adresowej, ale te dwa rodzaje zasad nie są zgodne. Jeśli masz takie zasady, najpierw [usuń zasady książki adresowej](/exchange/address-books/address-book-policies/remove-an-address-book-policy) . Po włączeniu zasad bariery informacyjnej i włączeniu hierarchicznej książki adresowej wszyscy użytkownicy **_, którzy nie znajdują się_** w segmencie barier informacyjnych, zobaczą [hierarchiczną książkę adresową](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) w Exchange online.

- **Zarządzanie przy użyciu programu PowerShell**: obecnie zasady bariery informacyjnej są definiowane i zarządzane w programie PowerShell Centrum zgodności usługi Security &. Chociaż w tym artykule podano kilka przykładów, musisz znać polecenia cmdlet i parametry programu PowerShell. Potrzebny będzie również moduł Azure Active Directory programu PowerShell.
  - [Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell)
  - [Instalowanie programu Azure Active Directory PowerShell dla Graph](/powershell/azure/active-directory/install-adv2)

- **Zgoda administratora na bariery informacyjne w Microsoft Teams**: po wprowadzeniu zasad IB mogą oni usuwać użytkowników niezgodnych z usługą IB z grup (tj. Teams kanałów opartych na grupach). Ta konfiguracja pomaga zapewnić zgodność organizacji z zasadami i przepisami. Użyj poniższej procedury, aby umożliwić działanie zasad barier informacyjnych zgodnie z oczekiwaniami w Microsoft Teams.

   1. Wymagania wstępne: [zainstaluj Azure Active Directory programu PowerShell dla Graph](/powershell/azure/active-directory/install-adv2).

   1. Uruchom następujące polecenia cmdlet programu PowerShell:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. Po wyświetleniu monitu zaloguj się przy użyciu konta służbowego w celu Office 365.

   1. W **żądanym** oknie dialogowym Uprawnienia przejrzyj informacje, a następnie wybierz pozycję **Akceptuj**. Uprawnienia wymagane przez aplikację są podane poniżej.

      > [!div class="mx-imgBorder"]
      > ![Obrazu.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

Po spełnieniu wszystkich wymagań wstępnych przejdź do następnego kroku.

> [!TIP]
> Aby ułatwić przygotowanie planu, w tym artykule znajduje się przykładowy scenariusz. [Zobacz działy, segmenty i zasady firmy Contoso](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>Krok 2. Segmentuj użytkowników w organizacji

W tym kroku określisz, jakie zasady barier informacyjnych są potrzebne, utworzysz listę segmentów do zdefiniowania, a następnie zdefiniujesz segmenty.

### <a name="determine-what-policies-are-needed"></a>Określanie, jakie zasady są potrzebne

Biorąc pod uwagę przepisy prawne i branżowe, kim są grupy w organizacji, które będą potrzebować zasad barier informacyjnych? Utwórz listę. Czy istnieją grupy, które powinny nie komunikować się z inną grupą? Czy istnieją grupy, które powinny mieć możliwość komunikowania się tylko z jedną lub dwiema innymi grupami? Pomyśl o zasadach, których potrzebujesz, jako należących do jednej z dwóch grup:

- Zasady "Blokuj" uniemożliwiają jednej grupie komunikowanie się z inną grupą.
- Zasady "Zezwalaj" umożliwiają grupie komunikowanie się tylko z niektórymi innymi, określonymi grupami.

Jeśli masz początkową listę grup i zasad, przejdź do identyfikowania potrzebnych segmentów.

### <a name="identify-segments"></a>Identyfikowanie segmentów

Oprócz początkowej listy zasad utwórz listę segmentów dla swojej organizacji. Użytkownicy, którzy zostaną uwzględnieni w zasadach barier informacyjnych, powinni należeć do segmentu. Starannie zaplanuj segmenty, ponieważ użytkownik może znajdować się tylko w jednym segmencie. Każdy segment może mieć zastosowane tylko jedną zasadę bariery informacyjnej.

> [!IMPORTANT]
> Użytkownik może znajdować się tylko w jednym segmencie.

Określ atrybuty w danych katalogu organizacji, których użyjesz do definiowania segmentów. Możesz użyć *działu*, *elementu członkowskiego* lub dowolnego z obsługiwanych atrybutów. Upewnij się, że masz wartości w atrybutze wybranym dla użytkowników. [Zobacz listę obsługiwanych atrybutów, aby uzyskać informacje o barierach](information-barriers-attributes.md).

> [!IMPORTANT]
> **Przed przejściem do następnej sekcji upewnij się, że dane katalogu zawierają wartości atrybutów, których można użyć do definiowania segmentów**. Jeśli dane katalogu nie mają wartości atrybutów, których chcesz użyć, konta użytkowników muszą zostać zaktualizowane w celu uwzględnienia tych informacji przed przejściem do barier informacyjnych. Aby uzyskać pomoc w tej kwestii, zobacz następujące zasoby:<br/>- [Konfigurowanie właściwości konta użytkownika za pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>Definiowanie segmentów przy użyciu programu PowerShell

Definiowanie segmentów nie ma wpływu na użytkowników; Po prostu ustawia scenę dla zasad barier informacyjnych, które mają być zdefiniowane, a następnie stosowane.

1. Użyj polecenia cmdlet **New-OrganizationSegment** z parametrem **UserGroupFilter** , który odpowiada [atrybutowi](information-barriers-attributes.md) , którego chcesz użyć.

    | Składni | Przykład |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>W tym przykładzie segment o nazwie *HR* jest definiowany przy użyciu *działu kadr*, wartości w atrybucie *Dział* . Część **-eq** polecenia cmdlet odnosi się do wartości "equals". (Alternatywnie, można użyć **-ne** oznacza "nie równa się". Zobacz [Using "equals" and "not equals" in segment definitions (Używanie wartości "equals" i "not equals" w definicjach segmentów](#using-equals-and-not-equals-in-segment-definitions)). |

    Po uruchomieniu każdego polecenia cmdlet powinna zostać wyświetlona lista szczegółów dotyczących nowego segmentu. Szczegóły obejmują typ segmentu, który go utworzył lub ostatnio zmodyfikował itd. 

2. Powtórz ten proces dla każdego segmentu, który chcesz zdefiniować.

    > [!IMPORTANT]
    > **Upewnij się, że segmenty nie nakładają się na siebie**. Każdy użytkownik, którego będą dotyczyć bariery informacyjne, powinien należeć do jednego (i tylko jednego) segmentu. Żaden użytkownik nie powinien należeć do co najmniej dwóch segmentów. (Zobacz [przykład: zdefiniowane segmenty firmy Contoso](#contosos-defined-segments) w tym artykule).

Po zdefiniowaniu segmentów przejdź do [definiowania zasad barier informacyjnych](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Używanie wartości "equals" i "not equals" w definicjach segmentów

W poniższym przykładzie definiujemy segment w taki sposób, że "Dział równa się hr". 

| Przykład | Uwaga |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Zwróć uwagę, że w tym przykładzie definicja segmentu zawiera parametr "equals" o wartości **-eq**. |

Segmenty można również zdefiniować przy użyciu parametru "nie równa się", oznaczonego jako **-ne**, jak pokazano w poniższej tabeli:

| Składni | Przykład |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | W tym przykładzie zdefiniowaliśmy segment o nazwie *NotSales* , który obejmuje wszystkich użytkowników, którzy nie znajdują się w *obszarze Sprzedaż*. - **ne** część polecenia cmdlet odnosi się do "nie równa się". |

Oprócz definiowania segmentów przy użyciu parametrów "equals" lub "not equals" można zdefiniować segment przy użyciu parametrów "equals" i "not equals". Można również zdefiniować złożone filtry grup przy użyciu operatorów logicznych *AND* i *OR* .

| Składni | Przykład |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | W tym przykładzie zdefiniowaliśmy segment o nazwie *LocalFTE* , który obejmuje osoby, które znajdują się lokalnie i których stanowiska nie są wymienione jako *tymczasowe*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| W tym przykładzie zdefiniowaliśmy segment o nazwie *Segment1* , który obejmuje osoby będące członkami group1@contoso.com, a nie członków group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | W tym przykładzie zdefiniowaliśmy segment o nazwie *Segment2* , który obejmuje osoby będące członkami group2@contoso.com, a nie członków group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| W tym przykładzie zdefiniowaliśmy segment o nazwie *Segment1and2* , który obejmuje członków osób group1@contoso.com i group2@contoso.com, a nie członków group3@contoso.com. |

> [!TIP]
> Jeśli to możliwe, użyj definicji segmentów, które obejmują "-eq" lub "-ne". Staraj się nie definiować złożonych definicji segmentów.

## <a name="step-3-define-information-barrier-policies"></a>Krok 3. Definiowanie zasad barier informacyjnych

Określ, czy musisz uniemożliwić komunikację między niektórymi segmentami, czy ograniczyć komunikację do niektórych segmentów. W idealnym przypadku użyjesz minimalnej liczby zasad, aby zapewnić zgodność organizacji z wymaganiami prawnymi i branżowymi.

Z listą segmentów użytkowników i zasadami bariery informacyjnej, które chcesz zdefiniować, wybierz scenariusz, a następnie wykonaj kroki.

- [Scenariusz 1. Blokowanie komunikacji między segmentami](#scenario-1-block-communications-between-segments)
- [Scenariusz 2. Zezwalanie segmentowi na komunikowanie się tylko z jednym innym segmentem](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Upewnij się, że podczas definiowania zasad nie przypisujesz do segmentu więcej niż jednej zasady**. Jeśli na przykład zdefiniujesz jedną zasadę dla segmentu o nazwie *Sales*, nie zdefiniuj dodatkowych zasad dla *pozycji Sprzedaż*.<p> Ponadto podczas definiowania zasad barier informacyjnych należy ustawić te zasady na stan nieaktywny, dopóki nie będziesz gotowy do ich zastosowania. Definiowanie (lub edytowanie) zasad nie ma wpływu na użytkowników, dopóki te zasady nie zostaną ustawione na stan aktywny, a następnie zostaną zastosowane.

(Zobacz [przykład: zasady bariery informacyjnej firmy Contoso](#contosos-information-barrier-policies) w tym artykule).

### <a name="scenario-1-block-communications-between-segments"></a>Scenariusz 1. Blokowanie komunikacji między segmentami

Jeśli chcesz zablokować komunikację między segmentami, zdefiniuj dwie zasady: jedną dla każdego kierunku. Każda zasada blokuje komunikację tylko w jedną stronę.

Załóżmy na przykład, że chcesz zablokować komunikację między segmentem A a segmentem B. W tym przypadku zdefiniujesz jedną zasadę uniemożliwiającą segmentowi A komunikowanie się z segmentem B, a następnie zdefiniuj drugą zasadę, aby uniemożliwić segmentowi B komunikowanie się z segmentem A.

1. Aby zdefiniować pierwsze zasady blokowania, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsBlocked** .

    | Składni | Przykład |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady o nazwie *Sales-Research* dla segmentu o nazwie *Sales*. Gdy są aktywne i stosowane, te zasady uniemożliwiają użytkownikom w *sprzedaży* komunikowanie się z osobami w segmencie o nazwie *Badania*. |

2. Aby zdefiniować drugi segment blokowania, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsBlocked** ponownie, tym razem z odwróconymi segmentami.

    | Przykład | Uwaga |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | W tym przykładzie zdefiniowaliśmy zasady o nazwie *Research-Sales* , aby uniemożliwić programowi *Research* komunikowanie się z usługą *Sales*. |

3. Przejdź do jednej z następujących akcji:

   - (W razie potrzeby) [Definiowanie zasad umożliwiających segmentowi komunikowanie się tylko z jednym innym segmentem](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Po zdefiniowaniu wszystkich zasad) [Stosowanie zasad barier informacyjnych](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scenariusz 2. Zezwalanie segmentowi na komunikowanie się tylko z jednym innym segmentem

1. Aby zezwolić jedneemu segmentowi na komunikowanie się tylko z jednym innym segmentem, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsAllowed** .

    | Składni | Przykład |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady o nazwie *Manufacturing-HR* dla segmentu o nazwie *Manufacturing*. Gdy są aktywne i stosowane, te zasady umożliwiają osobom w *środowisku produkcyjnym komunikowanie* się tylko z osobami w segmencie o nazwie *HR*. (W tym przypadku *produkcja* nie może komunikować się z użytkownikami, którzy nie są częścią *kadry*). |

    **W razie potrzeby można określić wiele segmentów za pomocą tego polecenia cmdlet, jak pokazano w poniższym przykładzie.**

    | Składni | Przykład |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady, które umożliwiają segmentowi *Research* komunikowanie się tylko z *działem kadr* i *produkcją*. |

    Powtórz ten krok dla każdej zasady, którą chcesz zdefiniować, aby umożliwić określonym segmentom komunikowanie się tylko z niektórymi innymi określonymi segmentami.

2. Przejdź do jednej z następujących akcji:

   - (W razie potrzeby) [Definiowanie zasad blokujących komunikację między segmentami](#scenario-1-block-communications-between-segments) 
   - (Po zdefiniowaniu wszystkich zasad) [Stosowanie zasad barier informacyjnych](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>Krok 4. Stosowanie zasad barier informacyjnych

Zasady bariery informacyjnej nie są stosowane, dopóki nie ustawisz ich na stan aktywny, a następnie zastosujesz zasady.

1. Użyj polecenia cmdlet **Get-InformationBarrierPolicy** , aby wyświetlić listę zdefiniowanych zasad. Zwróć uwagę na stan i tożsamość (GUID) poszczególnych zasad.

    Składni: `Get-InformationBarrierPolicy`

2. Aby ustawić stan aktywny zasad, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem **Identity** i parametru **State** ustawionego na **Aktywny**. 

    | Składni | Przykład |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> W tym przykładzie ustawiliśmy zasady bariery informacyjnej z identyfikatorem GUID *43c37853-ea10-4b90-a23d-ab8c93772471* jako stan aktywny. |

    Powtórz ten krok zgodnie z potrzebami dla poszczególnych zasad.

3. Po zakończeniu ustawiania stanu aktywnego zasad bariery informacji użyj polecenia cmdlet **Start-InformationBarrierPoliciesApplication** w Centrum zgodności & zabezpieczeń.

    Składni: `Start-InformationBarrierPoliciesApplication`

    Po uruchomieniu `Start-InformationBarrierPoliciesApplication`programu zaczekaj 30 minut na rozpoczęcie stosowania zasad przez system. System stosuje zasady użytkownika według użytkownika. System przetwarza około 5000 kont użytkowników na godzinę.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Wyświetlanie stanu kont użytkowników, segmentów, zasad lub aplikacji zasad

Za pomocą programu PowerShell można wyświetlić stan kont użytkowników, segmentów, zasad i aplikacji zasad, jak pokazano w poniższej tabeli.

| Aby wyświetlić te informacje | Wykonaj tę akcję |
|:---------------|:----------|
| Konta użytkowników | Użyj polecenia cmdlet **Get-InformationBarrierRecipientStatus** z parametrami tożsamości. <p> Składni: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, takiej jak nazwa, alias, nazwa wyróżniająca, nazwa domeny kanonicznej, adres e-mail lub identyfikator GUID. <p> Przykład: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> W tym przykładzie odwołujemy się do dwóch kont użytkowników w Office 365: *meganb* dla *Megan* i *alexw* dla *Alex*. <p> (Możesz również użyć tego polecenia cmdlet dla jednego użytkownika: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> To polecenie cmdlet zwraca informacje o użytkownikach, takie jak wartości atrybutów i wszelkie zastosowane zasady bariery informacyjnej.|
| Segmenty | Użyj polecenia cmdlet **Get-OrganizationSegment** .<p> Składni: `Get-OrganizationSegment` <p> To polecenie cmdlet wyświetli listę wszystkich segmentów zdefiniowanych dla twojej organizacji. |
| Zasady barier informacyjnych | Użyj polecenia cmdlet **Get-InformationBarrierPolicy** . <p> Składni: `Get-InformationBarrierPolicy` <p> To polecenie cmdlet wyświetli listę zdefiniowanych zasad barier informacyjnych oraz ich stan. |
| Najnowsza aplikacja zasad bariery informacyjnej | Użyj polecenia cmdlet **Get-InformationBarrierPoliciesApplicationStatus** . <p> Składni: `Get-InformationBarrierPoliciesApplicationStatus`<p> To polecenie cmdlet wyświetli informacje o tym, czy aplikacja zasad została ukończona, zakończona niepowodzeniem, czy jest w toku. |
| Wszystkie aplikacje zasad bariery informacyjnej|Używać `Get-InformationBarrierPoliciesApplicationStatus -All`<p> To polecenie cmdlet wyświetli informacje o tym, czy aplikacja zasad została ukończona, zakończona niepowodzeniem, czy jest w toku.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Co zrobić, jeśli muszę usunąć lub zmienić zasady?

Dostępne są zasoby ułatwiające zarządzanie zasadami barier informacyjnych.

- Jeśli coś pójdzie nie tak z barierami informacyjnymi, zobacz [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- Aby zatrzymać stosowanie zasad, zobacz [Zatrzymywanie aplikacji zasad](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- Aby usunąć zasady bariery informacyjnej, zobacz [Usuwanie zasad](information-barriers-edit-segments-policies.md#remove-a-policy).
- Aby wprowadzić zmiany w segmentach lub zasadach, zobacz [Edytowanie (lub usuwanie) zasad barier informacyjnych](information-barriers-edit-segments-policies.md).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Krok 5. Konfiguracja barier informacyjnych na SharePoint i OneDrive

Jeśli konfigurujesz bariery informacyjne dla SharePoint i OneDrive, musisz włączyć bariery informacyjne w tych usługach. Należy również włączyć bariery informacyjne dla tych usług, jeśli konfigurujesz bariery informacyjne dla Microsoft Teams. Po utworzeniu zespołu Microsoft Teams witryna SharePoint jest automatycznie tworzona i skojarzona z Microsoft Teams dla środowiska plików. Zasady bariery informacyjnej nie są domyślnie przestrzegane w tej witrynie SharePoint i plikach.

Aby włączyć bariery informacyjne w SharePoint i OneDrive, postępuj zgodnie ze wskazówkami i krokami w artykule [Korzystanie z barier informacyjnych z SharePoint](/sharepoint/information-barriers).

## <a name="step-6-information-barriers-modes"></a>Krok 6. Tryby barier informacyjnych

Tryby mogą pomóc wzmocnić dostęp, udostępnianie i członkostwo w zasobie Microsoft 365 w oparciu o tryb IB zasobu. Tryby są obsługiwane w lokacjach Grupy Microsoft 365, Microsoft Teams, OneDrive i SharePoint i są automatycznie włączane w nowej lub istniejącej konfiguracji IB.

Następujące tryby IB są obsługiwane w zasobach Microsoft 365:

| **Tryb** | **Opis** | **Przykład** |
|:-----|:------------|:--------|
| **Otwórz** | Nie ma żadnych zasad IB ani segmentów skojarzonych z zasobem Microsoft 365. Każdy może zostać zaproszony do udziału w zasobie. | Witryna zespołu utworzona na potrzeby imprezy piknikowej dla Twojej organizacji. |
| **Moderowany przez właściciela (wersja zapoznawcza)** | Zasady IB zasobu Microsoft 365 są określane na podstawie zasad IB właściciela zasobu. Właściciele zasobów mogą zapraszać dowolnego użytkownika do zasobu na podstawie zasad IB. Ten tryb jest przydatny, gdy firma chce zezwolić na współpracę między niezgodnych użytkowników segmentu, które są moderowane przez właściciela. Tylko właściciel zasobu może dodawać nowych członków według zasad IB. | Wirtualny przedstawiciel działu kadr chce współpracować z wirtualnymi przedstawicielami ds. sprzedaży i badań. Nowa witryna SharePoint, która jest ustawiona z *moderem właściciela* trybu IB, aby dodać użytkowników segmentu Sprzedaż i badania do tej samej witryny. Właściciel jest odpowiedzialny za zapewnienie, że do zasobu zostaną dodane odpowiednie elementy członkowskie. |
| **Niejawne** | Zasady IB lub segmenty zasobu Microsoft 365 są dziedziczone z zasad IB elementów członkowskich zasobów. Właściciel może dodawać członków, o ile są one zgodne z istniejącymi elementami członkowskimi zasobu. Jest to domyślny tryb IB dla Microsoft Teams. | Użytkownik segmentu Sales tworzy zespół Microsoft Teams do współpracy z innymi zgodnymi segmentami w organizacji. |
| **Jawne** | Zasady IB zasobu Microsoft 365 są według segmentów skojarzonych z zasobem. Właściciel zasobu lub administrator SharePoint może zarządzać segmentami zasobu.  | Witryna utworzona tylko dla członków segmentu Sales w celu współpracy przez skojarzenie segmentu Sales z witryną.   |

Aby uzyskać więcej informacji na temat trybu bariery informacyjnej i sposobu ich konfigurowania w usługach, zobacz następujące artykuły:

- [Tryby i Microsoft Teams barier informacyjnych](/microsoftteams/information-barriers-in-teams)
- [Tryby i OneDrive barier informacyjnych](/onedrive/information-barriers)
- [Tryby i SharePoint barier informacyjnych](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Przykładowy scenariusz: działy, segmenty i zasady firmy Contoso

Aby zobaczyć, jak organizacja może podejść do definiowania segmentów i zasad, rozważ poniższy przykładowy scenariusz.

### <a name="contosos-departments-and-plan"></a>Działy i plan firmy Contoso

Firma Contoso ma pięć działów: HR, Sales, Marketing, Research i Manufacturing. Aby zachować zgodność z przepisami branżowymi, osoby w niektórych działach nie powinny komunikować się z innymi działami, jak wymieniono w poniższej tabeli:

| Segmentu | Może rozmawiać z | Nie można rozmawiać z |
|:----------|:--------------|:-----------------|
| HR | Wszyscy | (bez ograniczeń) |
| Sprzedaży | HR, Marketing, Manufacturing | Poszukiwanie |
| Marketing | Wszyscy | (bez ograniczeń) |
| Poszukiwanie | HR, Marketing, Manufacturing | Sprzedaży |
| Produkcji | HR, Marketing | Każda osoba inna niż hr lub marketing |

W przypadku tej struktury plan firmy Contoso obejmuje trzy zasady barier informacyjnych:

1. Zasady mające na celu uniemożliwienie sprzedaży komunikowania się z programem Research (oraz inne zasady uniemożliwiające programowi Research komunikowanie się z usługą Sales).

2. Zasady mające na celu umożliwienie usłudze Manufacturing komunikowania się tylko z działem kadr i marketingiem.

W tym scenariuszu nie trzeba definiować zasad dotyczących działu kadr ani marketingu.

### <a name="contosos-defined-segments"></a>Zdefiniowane segmenty firmy Contoso

Firma Contoso użyje atrybutu Dział w Azure Active Directory, aby zdefiniować segmenty w następujący sposób:

| Department | Definicja segmentu |
|:-------------|:---------------------|
| HR | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Sprzedaży | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Poszukiwanie | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Produkcji | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Po zdefiniowaniu segmentów firma Contoso kontynuuje definiowanie zasad.

### <a name="contosos-information-barrier-policies"></a>Zasady barier informacyjnych firmy Contoso

Firma Contoso definiuje trzy zasady zgodnie z opisem w poniższej tabeli:

| Zasad | Definicja zasad |
|:---------|:--------------------|
| **Zasady 1: Uniemożliwianie komunikacji sprzedaży z programem Research** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> W tym przykładzie zasady bariery informacyjnej są nazywane *Sales-Research*. Gdy te zasady są aktywne i stosowane, pomogą uniemożliwić użytkownikom należącym do segmentu Sales komunikowanie się z użytkownikami w segmencie Badania. Te zasady są zasadami jednokierunkowymi; Nie uniemożliwi to badaniu komunikowania się z usługą Sales. W tym celu wymagana jest zasada 2. |
| **Zasady 2: Uniemożliwiaj badaniu komunikowanie się ze sprzedażą** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> W tym przykładzie zasady bariery informacyjnej są nazywane *Research-Sales*. Gdy te zasady są aktywne i stosowane, pomogą uniemożliwić użytkownikom należącym do segmentu Badania komunikowanie się z użytkownikami w segmencie Sprzedaż. |
| **Zasady 3: Zezwalaj produkcji na komunikowanie się tylko z działem kadr i marketingiem** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> W tym przypadku zasady bariery informacyjnej są *nazywane Manufacturing-HRMarketing*. Gdy te zasady są aktywne i stosowane, usługa Manufacturing może komunikować się tylko z działem kadr i marketingiem. Dział kadr i marketing nie są ograniczone do komunikowania się z innymi segmentami. |

Po zdefiniowaniu segmentów i zasad firma Contoso stosuje zasady, uruchamiając polecenie cmdlet **Start-InformationBarrierPoliciesApplication** .

Po zakończeniu polecenia cmdlet firma Contoso jest zgodna z wymaganiami prawnymi i branżowymi.

## <a name="resources"></a>Zasoby

- [Omówienie barier informacyjnych](information-barriers.md)
- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w usłudze SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w OneDrive](/onedrive/information-barriers)
