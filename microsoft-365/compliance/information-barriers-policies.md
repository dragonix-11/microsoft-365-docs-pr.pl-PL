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
ms.openlocfilehash: 1a9b6a4000b6d96fa8fe60b3abc60ff01676073e
ms.sourcegitcommit: 7b83e2605895fee5c73cd1d01f4cd16e1457a69f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2021
ms.locfileid: "62990534"
---
# <a name="get-started-with-information-barriers"></a>Wprowadzenie do barier informacyjnych

Bariery informacyjne pozwalają definiować zasady tak, aby określone segmenty użytkowników nie komunikują się ze sobą, lub zezwalać określonym segmentom na komunikowanie się tylko z określonymi segmentami. Zasady barier informacyjnej mogą ułatwić organizacji zachowanie zgodności z odpowiednimi standardami i przepisami branżowymi oraz uniknąć potencjalnych konfliktów zainteresowania. Aby uzyskać więcej informacji, zobacz [Informacje o barierach informacyjnych](information-barriers.md).

W tym artykule opisano sposób konfigurowania zasad bariery informacyjnej. W tym celu należy wykonać kilka kroków, dlatego przed rozpoczęciem konfigurowania zasad barier informacyjnych należy zapoznać się z całym procesem.

> [!TIP]
> Ten artykuł zawiera [przykładowy scenariusz ułatwiający](#example-scenario-contosos-departments-segments-and-policies) planowanie i definiowanie zasad barier informacyjnych.

## <a name="concepts"></a>Koncepcje

Definiując zasady dla barier informacyjnych, należy pracować z atrybutami konta użytkownika, segmentami, zasadami "blokowania" i/lub "zezwalania" i aplikacją zasad.

- Atrybuty konta użytkownika są definiowane w programie Azure Active Directory (lub Exchange Online). Te atrybuty mogą obejmować dział, stanowisko, lokalizację, nazwę zespołu i inne szczegóły profilu stanowiska.
- Segmenty to zestawy użytkowników zdefiniowane w Centrum zgodności platformy Microsoft 365 przy użyciu wybranego **atrybutu konta użytkownika**. (Zobacz [listę obsługiwanych atrybutów](information-barriers-attributes.md)).
- Zasady barier informacyjnej określają ograniczenia lub limity komunikacji. Definiując zasady bariery informacyjnej, wybierasz spośród dwóch rodzajów zasad:
  - *Zasady* blokowania uniemożliwiają komunikację jednego segmentu z innym segmentem.
  - *Zasady* zezwalają na komunikację jednego segmentu tylko z określonymi innymi segmentami.
- Aplikacja zasad jest wykonywana po zdefiniowanych wszystkich zasadach bariery informacyjnej i możesz je zastosować w swojej organizacji.

## <a name="configuration-at-a-glance"></a>Rzut oka na konfigurację

| **Kroki** | **Co należy zrobić** |
|:------|:----------------|
| **Krok 1**. [Upewninie się, że są spełnione wymagania wstępne](#step-1-make-sure-prerequisites-are-met) | — Sprawdzanie, czy są wymagane [licencje i uprawnienia](information-barriers.md#required-licenses-and-permissions)<br/>— Sprawdzanie, czy katalog zawiera dane dla użytkowników segmentowania<br/>- Włączanie wyszukiwania w katalogu o ograniczonych zakresach dla Microsoft Teams<br/>— Upewnij się, że rejestrowanie inspekcji jest włączone<br/>- Upewnij się, Exchange są w miejscu zasady książki adresowej<br/>— Użyj programu PowerShell (podano przykłady)<br/>- Udzielić zgody administratora na Microsoft Teams (kroki są uwzględnione) |
| **Krok 2**. [Segmentować użytkowników w organizacji](#step-2-segment-users-in-your-organization) | — Określanie wymaganych zasad<br/>— Lista segmentów w celu zdefiniowania<br/>— Określanie atrybutów, których należy użyć<br/>- Definiowanie segmentów w zakresie filtrów zasad |
| **Krok 3**. [Definiowanie zasad bariery informacyjnej](#step-3-define-information-barrier-policies) | - Zdefiniuj zasady (jeszcze nie mają zastosowania)<br/>— Do wyboru są dwa rodzaje (bloku lub zezwalania) |
| **Krok 4**. [Stosowanie zasad bariery informacyjnej](#step-4-apply-information-barrier-policies) | — Ustawianie stanu aktywnego zasad<br/>- Uruchamianie aplikacji zasad<br/>- Wyświetl stan zasad |
| **Krok 5**. [Konfiguracja barier informacyjnych na komputerach SharePoint i OneDrive (opcjonalnie)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - Konfigurowanie barier informacyjnych na SharePoint i OneDrive |
| **Krok 6**. [Tryby informacyjne (opcjonalne)](#step-6-information-barriers-modes) | - Zaktualizowanie trybów bariery informacyjnej, jeśli ma zastosowanie |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Krok 1. Upewninie się, że są spełnione wymagania wstępne

Oprócz wymaganych licencji [i](information-barriers.md#required-licenses-and-permissions) uprawnień przed skonfigurowaniem barier informacyjnych upewnij się, że są spełnione następujące wymagania:

- **Dane katalogowe**: upewnij się, że struktura organizacji jest odzwierciedlana w danych katalogu. Aby wykonać tę czynność, upewnij się, że atrybuty konta użytkownika, takie jak członkostwo w grupie, nazwa działu itp., są poprawnie wypełnione w programie Azure Active Directory (lub Exchange Online). Aby dowiedzieć się więcej, zobacz następujące zasoby:
  - [Atrybuty zasad bariery informacyjnej](information-barriers-attributes.md)
  - [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Konfigurowanie właściwości konta użytkownika za pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Wyszukiwanie w katalogu z zakresem**: przed zdefiniowaniem pierwszej bariery informacyjnej w organizacji należy włączyć funkcję wyszukiwania w [Microsoft Teams.](/MicrosoftTeams/teams-scoped-directory-search) Przed skonfigurowaniem lub zdefiniowaniem zasad bariery informacyjnej poczekaj co najmniej 24 godziny po włączeniu wyszukiwania w katalogu z zakresami.

- **Exchange Online licencji**: Zasady barier informacyjnych działają tylko wtedy, gdy użytkownikom docelowym przypisano licencję Exchange Online licencji.

- **Sprawdzanie, czy jest włączone** rejestrowanie inspekcji: aby można było sprawdzać stan aplikacji zasad, należy włączyć rejestrowanie inspekcji. Inspekcja jest domyślnie włączona Microsoft 365 organizacji. Niektóre organizacje mogą wyłączyć inspekcję z określonych powodów. Jeśli w Twojej organizacji inspekcja jest wyłączona, może to być spowodowane tym, że inny administrator wyłączył ją. Zalecamy potwierdzenie, że po wykonaniu tego kroku można ponownie włączyć inspekcję. Aby uzyskać więcej informacji, zobacz Włączanie lub wyłączanie [przeszukiwania dziennika inspekcji](turn-audit-log-search-on-or-off.md).

- **Brak zasad książki adresowej**. Przed zdefiniowaniem i zastosowaniem zasad bariery informacyjnej upewnij się, Exchange, że zasady książki adresowej nie są stosowane. Bariery informacyjne są oparte na zasadach książki adresowej, ale oba rodzaje zasad nie są ze sobą zgodne. Jeśli masz takie zasady, najpierw usuń zasady książki [adresowej](/exchange/address-books/address-book-policies/remove-an-address-book-policy) . Po włączeniu zasad bariery informacyjnej i włączeniu hierarchicznej książki adresowej wszyscy użytkownicy, **** którzy nie znajdują się w [segmencie bariery](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) informacyjnej, zobaczą hierarchiczną książkę adresową w Exchange online.

- **Zarządzanie przy użyciu programu PowerShell**: Obecnie zasady barier informacyjnej są definiowane i zarządzane w centrum & zgodności w programie PowerShell. Chociaż w tym artykule podano kilka przykładów, konieczne będzie zapoznanie się z poleceniami cmdlet i parametrami programu PowerShell. Potrzebny będzie również moduł Azure Active Directory PowerShell.
  - [Połączenie do centrum & zabezpieczeń w programie PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [Instalowanie Azure Active Directory PowerShell dla Graph](/powershell/azure/active-directory/install-adv2)

- **Administrator wyraża zgodę** na stosowanie barier informacyjnych w programie Microsoft Teams: Gdy Zasady usługi IB są takie, mogą oni usuwać użytkowników korzystających z zasad innych niż IB z grup (czyli Teams kanałów opartych na grupach). Ta konfiguracja gwarantuje, że Twoja organizacja będzie zachować zgodność z zasadami i przepisami. Skorzystaj z poniższej procedury, aby umożliwić stosowanie zasad barier informacyjnych zgodnie z oczekiwaniami Microsoft Teams.

   1. Wymagania wstępne: [Zainstaluj Azure Active Directory PowerShell dla Graph](/powershell/azure/active-directory/install-adv2).

   1. Uruchom następujące polecenia cmdlet programu PowerShell:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. Gdy zostanie wyświetlony monit, zaloguj się za pomocą konta służbowego lub szkolnego w celu Office 365.

   1. W **oknie dialogowym Żądane** uprawnienia przejrzyj informacje, a następnie wybierz pozycję **Zaakceptuj**. Uprawnienia żądane przez aplikację podano poniżej.

      > [!div class="mx-imgBorder"]
      > ![obraz.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

Gdy wszystkie wymagania wstępne zostaną spełnione, przejdź do następnego kroku.

> [!TIP]
> Aby ułatwić Ci przygotowanie planu, w tym artykule został uwzględniony przykładowy scenariusz. [Zobacz działy, segmenty i zasady firmy Contoso](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>Krok 2. Segmentować użytkowników w organizacji

W tym kroku określisz, jakie zasady informacyjne są potrzebne, określisz listę segmentów do zdefiniowania, a następnie zdefiniujesz segmenty.

### <a name="determine-what-policies-are-needed"></a>Określanie wymaganych zasad

Rozważasz przepisy prawne i branżowe, które są grupami w Twojej organizacji, które będą potrzebować zasad bariery informacyjnej? Schowaj listę. Czy istnieją grupy, których komunikowanie się z inną grupą powinno być niemożliwe? Czy istnieją grupy, które powinny mieć możliwość komunikowania się tylko z jedną lub dwiema innymi grupami? Zastanów się nad zasadami potrzebnymi jako należące do jednej z dwóch grup:

- Zasady "Blokuj" uniemożliwiają jednej grupie komunikowanie się z inną grupą.
- Zasady "Zezwalaj" umożliwiają grupie komunikowanie się tylko z niektórymi innymi, określonymi grupami.

Po wstępnej liście grup i zasad przejdź do segmentów, których potrzebujesz.

### <a name="identify-segments"></a>Identyfikowanie segmentów

Oprócz początkowej listy zasad możesz też wyświetlić listę segmentów w organizacji. Użytkownicy, którzy zostaną uwzględnione w zasadach bariery informacyjnej, powinni należeć do segmentu. Starannie planuj segmenty, ponieważ użytkownik może ująć się tylko w jeden segment. Do każdego segmentu może być stosowana tylko jedna zasada bariery informacyjnej.

> [!IMPORTANT]
> Użytkownik może mieć tylko jeden segment.

Określ atrybuty w danych katalogowych organizacji, których będziesz używać do definiowania segmentów. Możesz użyć *atrybutu Department (Dział*), *MemberOf (Członek*) lub dowolnego z obsługiwanych atrybutów. Upewnij się, że w atrybutach wybranych dla użytkowników są wartości. [Aby uzyskać informacje na temat barier informacyjnych, zapoznaj się z listą obsługiwanych atrybutów](information-barriers-attributes.md).

> [!IMPORTANT]
> **Zanim przejdziesz do następnej sekcji,** upewnij się, że dane katalogu mają wartości atrybutów, których można użyć do zdefiniowania segmentów. Jeśli dane katalogowe nie zawierają wartości atrybutów, których chcesz użyć, przed zastosowaniem barier informacyjnych należy zaktualizować konta użytkowników, aby uwzględnić te informacje. Aby uzyskać pomoc w tym związku, zobacz następujące zasoby:<br/>- [Konfigurowanie właściwości konta użytkownika za pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>Definiowanie segmentów przy użyciu programu PowerShell

Definiowanie segmentów nie wpływa na użytkowników; Stanowi ona jedynie etap definicji zasad bariery informacyjnej, a następnie ich zastosowania.

1. Użyj polecenia cmdlet **New-OrganizationSegment** z parametrem **UserGroupFilter** odpowiadającym atrybutowi [, którego chcesz](information-barriers-attributes.md) użyć.

    | Składnia | Przykład |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>W tym przykładzie segment o nazwie *KADR* jest zdefiniowany przy użyciu *funkcji KADR*, która jest wartością *atrybutu* Department. Część **-eq** polecenia cmdlet odwołuje się do "równa się". (Alternatywnie można użyć - **ne** , aby oznaczać "nie równa się". Zobacz [Używanie wartości "równa się" i "nie równa się" w definicjach segmentu](#using-equals-and-not-equals-in-segment-definitions)). |

    Po uruchomieniu każdego polecenia cmdlet powinna zostać wyświetlona lista szczegółów dotyczących nowego segmentu. Szczegóły obejmują typ segmentu, kto go utworzył lub ostatnio zmodyfikował, i tak dalej. 

2. Powtórz tę procedurę dla każdego segmentu, który chcesz zdefiniować.

    > [!IMPORTANT]
    > **Upewnij się, że segmenty nie nakładają się**. Każdy użytkownik, do którego będą mieć dostęp bariery informacyjne, powinien należeć do jednego (i tylko jednego) segmentu. Żaden użytkownik nie powinien należeć do dwóch lub większej liczby segmentów. (Zobacz [przykład: Segmenty zdefiniowane przez Contoso](#contosos-defined-segments) w tym artykule).

Po zdefiniowaniu segmentów przejdź do [definiowania zasad bariery informacyjnej](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Używanie wartości "równa się" i "nie równa się" w definicjach segmentów

W poniższym przykładzie definiujemy segment o wartości "Dział równa się DZIAŁ". 

| Przykład | Uwaga |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Zauważ, że w tym przykładzie definicja segmentu zawiera parametr "równa się" oznaczony jako **-eq**. |

Segmenty można również definiować przy użyciu parametru "nie równa się" oznaczonego jako **-ne**, jak pokazano w poniższej tabeli:

| Składnia | Przykład |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | W tym przykładzie zdefiniowano segment o nazwie  SprzedażRzeczywający, który obejmuje wszystkich użytkowników, którzy nie należą do działu *Sprzedaż*. Część **-ne** polecenia cmdlet odwołuje się do wartości "not equals". |

Oprócz segmentów definiujących segmenty przy użyciu wartości "równa się" lub "nie równa się" można zdefiniować segment, używając parametrów "równa się" i "nie równa się". Możesz również zdefiniować filtry złożonej grupy przy użyciu *operatorów logicznych AND* *i OR* .

| Składnia | Przykład |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | W tym przykładzie zdefiniowano segment o nazwie *LocalFTE* , który uwzględnia osoby zlokalizowane lokalnie, których stanowiska nie są wymienione jako *tymczasowe*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| W tym przykładzie zdefiniowano segment o nazwie *Segment1* , który obejmuje osoby, które są członkami group1@contoso.com, a nie członkami group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | W tym przykładzie zdefiniowano segment o nazwie *Segment2* , który obejmuje osoby, które są członkami group2@contoso.com, a nie członkami group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| W tym przykładzie zdefiniowano segment o nazwie *Segment1i2* , który obejmuje członków zespołu group1@contoso.com i group2@contoso.com, a nie członków group3@contoso.com. |

> [!TIP]
> Jeśli to możliwe, użyj definicji segmentów, które zawierają "-eq" lub "-ne". Nie wolno definiować definicji złożonych segmentów.

## <a name="step-3-define-information-barrier-policies"></a>Krok 3. Definiowanie zasad bariery informacyjnej

Określ, czy chcesz zapobiec komunikacji między określonymi segmentami, czy ograniczyć komunikację do określonych segmentów. Najlepiej, jeśli użyjesz minimalnej liczby zasad, aby upewnić się, że Twoja organizacja jest zgodna z wymaganiami prawnymi i branżowymi.

W przypadku listy segmentów użytkowników i zasady bariery informacyjnej, które chcesz zdefiniować, wybierz scenariusz, a następnie postępuj zgodnie z instrukcjami.

- [Scenariusz 1. Blokowanie komunikacji między segmentami](#scenario-1-block-communications-between-segments)
- [Scenariusz 2. Zezwalanie segmentowi na komunikowanie się tylko z jednym innym segmentem](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Podczas definiowania zasad upewnij się,** że do segmentu nie są przypisywane więcej niż jedna zasada. Na przykład w przypadku zdefiniowania jednej zasady dla segmentu *o nazwie* Sprzedaż nie zdefiniuj dodatkowych *zasad dla sprzedaży*.<p> Ponadto w przypadku definiowania zasad bariery informacyjnej należy określić, że zasady te są nieaktywne, dopóki nie będą gotowe do ich zastosowania. Definiowanie zasad (lub edytowanie) nie ma wpływu na użytkowników, dopóki nie zostaną one ustawione jako aktywne i zastosowane.

(Zobacz [przykład: Zasady firmy Contoso dotyczące bariery](#contosos-information-barrier-policies) informacyjnej w tym artykule).

### <a name="scenario-1-block-communications-between-segments"></a>Scenariusz 1. Blokowanie komunikacji między segmentami

Jeśli chcesz blokować segmenty w celu komunikowania się ze sobą, możesz zdefiniować dwie zasady: jedną dla każdego kierunku. Każda zasada blokuje komunikację tylko w jeden sposób.

Załóżmy na przykład, że chcesz zablokować komunikację między segmentami A i B. W takim przypadku zdefiniowano jedną zasady uniemożliwiające segmentowi A komunikowanie się z segmentem B, a następnie zdefiniowano drugą zasady uniemożliwiające segmentowi B komunikowanie się z segmentem A.

1. Aby zdefiniować pierwszą politykę blokowania, użyj polecenia cmdlet **New-InformationBarrierPolicy** z **parametrem SegmentsBlocked** .

    | Składnia | Przykład |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady o nazwie *Badanie Sprzedaży* dla segmentu o nazwie *Sprzedaż*. Gdy są aktywne i stosowane, te zasady uniemożliwiają osobom  z działu sprzedaży komunikowanie się z osobami w segmencie o nazwie *Badanie*. |

2. Aby zdefiniować drugi segment blokowania, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsBlocked** ponownie, tym razem z segmentami odwrotnie.

    | Przykład | Uwaga |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | W tym przykładzie zdefiniowaliśmy zasady o nazwie *Badania i* sprzedaż, aby uniemożliwić *komunikację firmy Badania* z *sprzedażą*. |

3. Przejdź do jednej z następujących akcji:

   - (W razie potrzeby) [Definiowanie zasad, aby umożliwić komunikację segmentu tylko z jednym innym segmentem](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Po zakończeniu definicji wszystkich zasad) [Stosowanie zasad bariery informacyjnej](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scenariusz 2. Zezwalanie segmentowi na komunikowanie się tylko z jednym innym segmentem

1. Aby umożliwić komunikację jednego segmentu tylko z jednym innym segmentem, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsAllowed** .

    | Składnia | Przykład |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> W tym przykładzie zdefiniowano zasady o nazwie *Produkcja-KADR* dla segmentu o nazwie *Produkcja*. Te zasady, gdy są aktywne i stosowane, pozwalają  osobom z produkcji komunikować się tylko z osobami z segmentu o nazwie *Kadry*. (W tym przypadku Produkcja *nie może* komunikować się z użytkownikami, którzy nie są częścią *działu kadr*). |

    **W razie potrzeby możesz określić wiele segmentów za pomocą tego polecenia cmdlet, jak pokazano w poniższym przykładzie.**

    | Składnia | Przykład |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady, które umożliwią *segmentowi* badań komunikowanie się tylko z *kadrami* i *produkcją*. |

    Powtórz ten krok dla każdej zasady, którą chcesz zdefiniować, aby umożliwić określonym segmentom komunikowanie się tylko z określonymi określonymi segmentami.

2. Przejdź do jednej z następujących akcji:

   - (W razie potrzeby) [Definiowanie zasad w celu blokowania komunikacji między segmentami](#scenario-1-block-communications-between-segments) 
   - (Po zakończeniu definicji wszystkich zasad) [Stosowanie zasad bariery informacyjnej](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>Krok 4. Stosowanie zasad bariery informacyjnej

Zasady barier informacyjnej nie obowiązują, dopóki nie ustawisz dla nich stanu aktywnego i nie zastosujemy tych zasad.

1. Aby wyświetlić listę zdefiniowanych zasad, użyj polecenia cmdlet **Get-InformationBarrierPolicy** . Zanotuj stan i tożsamość (GUID) poszczególnych zasad.

    Składnia: `Get-InformationBarrierPolicy`

2. Aby ustawić dla zasad stan aktywny, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem **Identity** i parametru **State** ustawionego na wartość **Aktywny**. 

    | Składnia | Przykład |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> W tym przykładzie ustawiono zasady bariery informacyjnej, które mają dla stanu aktywnego identyfikator GUID *43c37853-ea10-4b90-a23d-ab8c93772471* . |

    Powtórz ten krok odpowiednio do potrzeb dla każdej zasady.

3. Po ustawieniu stanu aktywnego zasad bariery informacyjnej użyj polecenia **cmdlet Start-InformationBarrierPoliciesApplication** w Centrum & zabezpieczeń.

    Składnia: `Start-InformationBarrierPoliciesApplication`

    Po uruchomieniu `Start-InformationBarrierPoliciesApplication`system może przez 30 minut rozpocząć stosowanie zasad. System stosuje zasady dla  użytkowników. System przetwarza około 5000 kont użytkowników na godzinę.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Wyświetlanie stanu kont użytkowników, segmentów, zasad lub aplikacji zasad

W programie PowerShell można wyświetlać stan kont użytkowników, segmentów, zasad i aplikacji zasad, jak podano w poniższej tabeli.

| Aby wyświetlić te informacje | Czynności do podjęcia |
|:---------------|:----------|
| Konta użytkowników | Używanie **polecenia cmdlet Get-InformationBarrierRecipientStatus** z parametrami tożsamości. <p> Składnia: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, na przykład nazwy, aliasu, nazwy odróżnianej, kanonicznego nazwy domeny, adresu e-mail lub identyfikatora GUID. <p> Przykład: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> W tym przykładzie używamy dwóch kont użytkowników w programie Office 365: *meganb* dla *Megan* i *alexa dla* *Alexa*. <p> (Możesz też użyć tego polecenia cmdlet dla jednego użytkownika: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> To polecenie cmdlet zwraca informacje o użytkownikach, takie jak wartości atrybutów i wszelkie stosowane zasady informacyjne.|
| Segmenty | Użyj **polecenia cmdlet Get-OrganizationSegment** .<p> Składnia: `Get-OrganizationSegment` <p> To polecenie cmdlet spowoduje wyświetlenie listy wszystkich segmentów zdefiniowanych w organizacji. |
| Zasady bariery informacyjnej | Użyj polecenia **cmdlet Get-InformationBarrierPolicy** . <p> Składnia: `Get-InformationBarrierPolicy` <p> To polecenie cmdlet wyświetli listę zdefiniowanych zasad bariery informacyjnej oraz ich stan. |
| Najnowsza aplikacja do stosowania zasad barier informacyjnych | Użyj **polecenia cmdlet Get-InformationBarrierPoliciesApplicationStatus** . <p> Składnia: `Get-InformationBarrierPoliciesApplicationStatus`<p> To polecenie cmdlet spowoduje wyświetlenie informacji o tym, czy aplikacja zasad została ukończona, nie powiodła się, czy jest w toku. |
| Wszystkie aplikacje z zasadami barier informacyjnych|Zastosowanie `Get-InformationBarrierPoliciesApplicationStatus -All`<p> To polecenie cmdlet spowoduje wyświetlenie informacji o tym, czy aplikacja zasad została ukończona, nie powiodła się, czy jest w toku.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Co zrobić, jeśli muszę usunąć lub zmienić zasady?

Dostępne są zasoby pomocne w zarządzaniu zasadami bariery informacyjnej.

- Jeśli coś nie działa z barierami informacyjnymi, zobacz [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- Aby zatrzymać stosowanie zasad, zobacz [Zatrzymywanie aplikacji zasad](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- Aby usunąć zasady bariery informacyjnej, [zobacz Usuwanie zasad](information-barriers-edit-segments-policies.md#remove-a-policy).
- Aby wprowadzić zmiany w segmentach lub zasadach, zobacz [Zasady edytowania (lub usuwania) informacji.](information-barriers-edit-segments-policies.md)

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Krok 5. Konfigurowanie barier informacyjnych na SharePoint i OneDrive

Jeśli konfigurujesz bariery informacyjne dla usług SharePoint i OneDrive, musisz włączyć bariery informacyjne na tych usługach. Musisz również włączyć bariery informacyjne w tych usługach, jeśli konfigurujesz bariery informacyjne dla Microsoft Teams. Po utworzeniu Microsoft Teams witryny zespołu jest automatycznie tworzona SharePoint skojarzona z Microsoft Teams środowisko plików. Zasady barier informacyjnej nie są domyślnie SharePoint tej witrynie i plikach.

Aby włączyć bariery informacyjne SharePoint i OneDrive, postępuj zgodnie z instrukcjami w artykule Stosowanie barier informacyjnych [SharePoint](/sharepoint/information-barriers) informacji.

## <a name="step-6-information-barriers-modes"></a>Krok 6. Tryby informacyjne

Tryby mogą ułatwić wzmacnianie dostępu, udostępniania i członkostwa Microsoft 365 zasobów w zależności od trybu IB zasobu. Tryby są obsługiwane Microsoft 365 grup, Microsoft Teams, OneDrive i SharePoint internetowych oraz są automatycznie włączane w nowej lub istniejącej konfiguracji IB.

Następujące tryby IB są obsługiwane Microsoft 365 zasobów:

| **Tryb** | **Opis** | **Przykład** |
|:-----|:------------|:--------|
| **Otwórz** | Z zasobem nie są skojarzone żadne zasady ani segmenty wiadomości Microsoft 365 wiadomości. Każdy może zostać zaproszony, aby zostać członkiem tego zasobu. | Witryna zespołu utworzona na wydarzenia piknikowe dla Twojej organizacji. |
| **Właściciel moderowany (wersja Preview)** | Zasady IB zasobu Microsoft 365 są określane na podstawie zasad IB właściciela zasobu. Właściciele zasobów mogą zaprosić do zasobu dowolnego użytkownika na podstawie ich zasad IB. Ten tryb jest przydatny, gdy firma chce zezwolić na współpracę między niezgodnymi użytkownikami segmentu, którzy są moderowane przez właściciela. Tylko właściciel zasobu może dodawać nowych członków według swoich zasad IB. | Wiceprezes działu kadr chce współpracować z specjalistami VPS ds. sprzedaży i badań. A new SharePoint site that is set with IB *mode Owner Moderated to add* both Sales and Research segment users to the same site. Odpowiedzialność właściciela za to, aby zapewnić, że do zasobu zostaną dodani właściwi członkowie. |
| **Niejawny** | Zasady IB lub segmenty zasobu Microsoft 365 są dziedziczone po zasadach IB członków zasobów. Właściciel może dodawać członków, o ile są zgodni z istniejącymi członkami zasobu. Jest to domyślny tryb dla przeglądarki IB dla Microsoft Teams. | Użytkownik segmentu Sprzedaż tworzy zespół Microsoft Teams do współpracy z innymi zgodnymi segmentami w organizacji. |
| **Jawny** | Zasady IB zasobu Microsoft 365 segmentów skojarzonych z zasobem. Właściciel zasobu lub SharePoint może zarządzać segmentami tego zasobu.  | Witryna utworzona wyłącznie dla członków segmentu Sprzedaż do współpracy przez skojarzenie segmentu Sprzedaż z witryną.   |

Aby uzyskać więcej informacji na temat bariery informacyjnej i sposobu ich konfiguracji w różnych usługach, zobacz następujące artykuły:

- [Tryby informacji i Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Tryby informacji i OneDrive](/onedrive/information-barriers)
- [Tryby informacji i SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Przykładowy scenariusz: działy, segmenty i zasady firmy Contoso

Aby zobaczyć, jak organizacja może podchodzić do definiowania segmentów i zasad, rozważ poniższy przykładowy scenariusz.

### <a name="contosos-departments-and-plan"></a>Działy i plan firmy Contoso

Firma Contoso ma pięć działów: Kadry, Sprzedaż, Marketing, Badania i Produkcja. Aby zachować zgodność z przepisami branżowymi, osoby z niektórych działów nie powinny komunikować się z innymi działami, jak podano w poniższej tabeli:

| Segment | Może rozmawiać | Nie można porozmawiać |
|:----------|:--------------|:-----------------|
| Kadry | Wszyscy | (bez ograniczeń) |
| Sprzedaż | Kadry, marketing, produkcja | Poszukiwanie |
| Marketing | Wszyscy | (bez ograniczeń) |
| Poszukiwanie | Kadry, marketing, produkcja | Sprzedaż |
| Produkcja | Kadry, marketing | Każda osoba inna niż kadrowa lub marketingowa |

W przypadku tej struktury plan firmy Contoso obejmuje trzy zasady barier informacyjnej:

1. Zasady mające na celu uniemożliwianie sprzedaży komunikowania się z badaniami (oraz inna zasada zapobiegająca komunikacji działu badań z sprzedażą).

2. Zasady zaprojektowane tak, aby umożliwić produkcji komunikowanie się tylko z kadrami i marketingami.

W tym scenariuszu nie trzeba definiować zasad dla kadr i marketingu.

### <a name="contosos-defined-segments"></a>Segmenty zdefiniowane przez Contoso

W celu zdefiniowania segmentów firma Contoso użyje atrybutu Department Azure Active Directory w następujący sposób:

| Department | Definicja segmentu |
|:-------------|:---------------------|
| Kadry | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Sprzedaż | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Poszukiwanie | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Produkcja | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Po zdefiniowaniu segmentów firma Contoso przechodzi do definiowania zasad.

### <a name="contosos-information-barrier-policies"></a>Zasady bariery informacyjnej firmy Contoso

Firma Contoso definiuje trzy zasady zgodnie z opisem w poniższej tabeli:

| Zasady | Definicja zasad |
|:---------|:--------------------|
| **Zasady 1. Uniemożliwianie sprzedaży komunikowania się z badaniami** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> W tym przykładzie zasady bariery informacyjnej są nazywane *badaniem sprzedaży*. Gdy te zasady są aktywne i stosowane, pomagają zapobiec komunikowaniu się użytkowników z segmentu Sprzedaż z użytkownikami w segmencie Badań. Te zasady są jednokierunkowe. nie zapobiegnie komunikowaniu się firmy Research z  sprzedażą. W tym celu potrzebne są zasady 2. |
| **Zasady 2. Zapobieganie komunikowaniu się z  sprzedażą przez badania** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> W tym przykładzie zasady bariery informacyjnej są nazywane *badaniem i sprzedażą*. Gdy te zasady są aktywne i zastosowane, pomagają one zapobiegać komunikowaniu się użytkowników w segmencie Badań z użytkownikami w segmencie Sprzedaż. |
| **Zasady 3. Zezwalanie produkcji na komunikowanie się tylko z kadrami i marketingami** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> W tym przypadku zasady bariery informacyjnej mają nazwę *Produkcja-HRMarketing*. Gdy te zasady są aktywne i zastosowane, produkcja może komunikować się tylko z kadrami i marketingami. Kadry i marketing nie są ograniczone do komunikowania się z innymi segmentami. |

W przypadku segmentów i zasad firma Contoso stosuje zasady, uruchamiając polecenie cmdlet **Start-InformationBarrierPoliciesApplication** .

Po zakończeniu polecenia cmdlet firma Contoso jest zgodna z wymaganiami prawnymi i branżowymi.

## <a name="resources"></a>Zasoby

- [Omówienie barier informacyjnych](information-barriers.md)
- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w programie OneDrive](/onedrive/information-barriers)
