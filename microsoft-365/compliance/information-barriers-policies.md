---
title: Wprowadzenie do barier informacyjnych
description: Dowiedz się, jak rozpocząć pracę z barierami informacyjnymi w Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, zgodność, bariery informacyjne
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
ms.openlocfilehash: 74da3ee1c2b3339a66ff205989dd978fdd00a530
ms.sourcegitcommit: 99494a5530ad64802f341573ad42796134190296
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2022
ms.locfileid: "65396250"
---
# <a name="get-started-with-information-barriers"></a>Wprowadzenie do barier informacyjnych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

W tym artykule opisano sposób konfigurowania zasad barier informacyjnych (IB) w organizacji. Jest zaangażowanych kilka kroków, dlatego przed rozpoczęciem konfigurowania zasad IB upewnij się, że przejrzyj cały proces.

W organizacji skonfigurujesz protokół IB przy użyciu [portal zgodności Microsoft Purview](https://compliance.microsoft.com) lub przy użyciu [programu PowerShell Office 365 Security and Compliance](/powershell/exchange/scc-powershell). W przypadku organizacji konfigurujących usługę IB po raz pierwszy zalecamy korzystanie z rozwiązania **Bariery informacyjne** w portalu zgodności. Jeśli zarządzasz istniejącą konfiguracją IB i dobrze korzystasz z programu PowerShell, nadal masz tę opcję.

Aby uzyskać więcej informacji na temat scenariuszy i funkcji IB, zobacz [Dowiedz się więcej o barierach informacyjnych](information-barriers.md).

> [!TIP]
> Aby ułatwić przygotowanie planu, w tym artykule znajduje się [przykładowy scenariusz](#example-scenario-contosos-departments-segments-and-policies) .

## <a name="required-subscriptions-and-permissions"></a>Wymagane subskrypcje i uprawnienia

Przed rozpoczęciem pracy z usługą IB należy potwierdzić subskrypcję Microsoft 365 i wszelkie dodatki. Aby uzyskać dostęp do usługi IB i korzystać z niej, organizacja musi mieć jedną z następujących subskrypcji lub dodatków:

- subskrypcja Microsoft 365 E5/A5 (wersja płatna lub próbna)
- subskrypcja Office 365 E5/A5/A3/A1 (wersja płatna lub próbna)
- Office 365 Advanced Compliance dodatku (nie jest już dostępny dla nowych subskrypcji)
- subskrypcja Microsoft 365 E3/A3/A1 + dodatek zgodności Microsoft 365 E5/A5
- subskrypcja Microsoft 365 E3/A3/A1 + dodatek Microsoft 365 E5/A5 Insider Risk Management

Aby uzyskać więcej informacji, zobacz [Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Aby [zarządzać zasadami IB](information-barriers-policies.md), musisz mieć przypisaną jedną z następujących ról:

- administrator globalny Microsoft 365
- administrator globalny Office 365
- Administrator zgodności
- Zarządzanie zgodnością IB

Aby dowiedzieć się więcej na temat ról i uprawnień, zobacz [Uprawnienia w centrum Office 365 Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="configuration-concepts"></a>Pojęcia dotyczące konfiguracji

Podczas konfigurowania usługi IB będziesz pracować z kilkoma obiektami i pojęciami.

- **Atrybuty konta użytkownika** są definiowane w Azure Active Directory (lub Exchange Online). Te atrybuty mogą obejmować dział, stanowisko, lokalizację, nazwę zespołu i inne szczegóły profilu zadania. Przypiszesz użytkowników lub grupy do segmentów z tymi atrybutami.
- **Segmenty to zestawy** grup lub użytkowników, które są zdefiniowane w portalu zgodności lub przy użyciu programu PowerShell używającego wybranych atrybutów grupy lub konta użytkownika. Aby uzyskać szczegółowe informacje, zobacz [listę obsługiwanych atrybutów IB](information-barriers-attributes.md) .
- **Zasady IB** określają limity lub ograniczenia komunikacji. Podczas definiowania zasad IB wybierasz spośród dwóch rodzajów zasad:
  - *Zasady blokowe* uniemożliwiają komunikację jednego segmentu z innym segmentem.
  - *Zezwalaj zasadom* na komunikowanie się z jednym segmentem tylko z niektórymi innymi segmentami.

    > [!NOTE]
    > W przypadku zasad *zezwalania* grupy i użytkownicy spoza IB nie będą widoczni dla użytkowników uwzględnionych w segmentach IB i zasadach. Jeśli potrzebujesz grup i użytkowników innych niż IB, aby byli widoczni dla użytkowników uwzględnionych w segmentach i zasadach IB, musisz użyć zasad *blokowych* .

- **Aplikacja zasad** jest wykonywana po zdefiniowaniu wszystkich zasad IB i możesz je zastosować w organizacji.
- **Widoczność użytkowników i grup innych niż IB**. Użytkownicy i grupy inne niż IB są użytkownikami i grupami wykluczonymi z segmentów i zasad IB. W zależności od typu zasad IB (blokuj lub zezwalaj) zachowanie tych użytkowników i grupy będzie się różnić w Microsoft Teams, SharePoint, OneDrive i na globalnej liście adresów. W przypadku użytkowników zdefiniowanych w *zasadach zezwalania* grupy inne niż IB i użytkownicy nie będą widoczni dla użytkowników uwzględnionych w segmentach IB i zasadach. W przypadku użytkowników zdefiniowanych w zasadach *blokowych* grupy inne niż IB i użytkownicy będą widoczni dla użytkowników uwzględnionych w segmentach IB i zasadach.
- **Obsługa grup**. Tylko nowoczesne grupy są obecnie obsługiwane na listach IB, a listy dystrybucyjne/grupy zabezpieczeń są traktowane jako grupy inne niż grupy IB.
- **Ukryte/wyłączone konta użytkowników**. W przypadku kont ukrytych/wyłączonych w organizacji parametr *HiddenFromAddressListEnabled jest automatycznie ustawiany* na *wartość True* , gdy konta użytkowników są ukryte lub wyłączone. W organizacjach z obsługą IB te konta nie mogą komunikować się ze wszystkimi innymi kontami użytkowników. W Microsoft Teams wszystkie czaty, w tym te konta, są zablokowane lub użytkownicy są automatycznie usuwane z konwersacji.

## <a name="configuration-overview"></a>Omówienie konfiguracji 

| **Kroki** | **Co się dzieje** |
|:------|:----------------|
| **Krok 1**. [Upewnij się, że zostały spełnione wymagania wstępne](#step-1-make-sure-prerequisites-are-met) | — Sprawdź, czy masz wymagane subskrypcje i uprawnienia <br/>— Sprawdź, czy katalog zawiera dane dotyczące segmentowania użytkowników<br/>— Włącz [wyszukiwanie według nazwy dla Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>— Upewnij się, że rejestrowanie inspekcji jest włączone<br/>- Upewnij się, że nie obowiązują żadne zasady Exchange książki adresowej <br/>— Udzielanie zgody administratora na Microsoft Teams (kroki są uwzględnione) |
| **Krok 2**. [Segmentuj użytkowników w organizacji](#step-2-segment-users-in-your-organization) | — Określanie, jakie zasady są potrzebne<br/>— Tworzenie listy segmentów do zdefiniowania<br/>— Określanie atrybutów do użycia<br/>— Definiowanie segmentów pod względem filtrów zasad |
| **Krok 3**. [Tworzenie zasad barier informacyjnych](#step-3-create-ib-policies) | — Tworzenie zasad (nie są jeszcze stosowane)<br/>- Wybierz jeden z dwóch rodzajów (blokuj lub zezwalaj) |
| **Krok 4**. [Stosowanie zasad barier informacyjnych](#step-4-apply-ib-policies) | — Ustawianie stanu aktywnego zasad<br/>— Uruchamianie aplikacji zasad<br/>— Wyświetlanie stanu zasad |
| **Krok 5**. [Konfiguracja barier informacyjnych na SharePoint i OneDrive (opcjonalnie)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | — Konfigurowanie protokołu IB dla SharePoint i OneDrive |
| **Krok 6**. [Tryby barier informacyjnych (opcjonalnie)](#step-6-information-barriers-modes) | - Zaktualizuj tryby IB, jeśli ma to zastosowanie |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Krok 1. Upewnij się, że zostały spełnione wymagania wstępne

Oprócz wymaganych subskrypcji i uprawnień przed skonfigurowaniem usługi IB upewnij się, że spełnione są następujące wymagania:

- **Dane katalogu**: upewnij się, że struktura organizacji jest odzwierciedlona w danych katalogu. Aby wykonać tę akcję, upewnij się, że atrybuty konta użytkownika (takie jak członkostwo w grupie, nazwa działu itp.) są poprawnie wypełniane w Azure Active Directory (lub Exchange Online). Aby dowiedzieć się więcej, zobacz następujące zasoby:
  - [Atrybuty zasad barier informacyjnych](information-barriers-attributes.md)
  - [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Konfigurowanie właściwości konta użytkownika za pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Wyszukiwanie w katalogu o określonym zakresie**: przed zdefiniowaniem pierwszych zasad IB organizacji należy [włączyć wyszukiwanie katalogów o określonym zakresie w Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). Odczekaj co najmniej 24 godziny po włączeniu wyszukiwania w katalogu o określonym zakresie, zanim skonfigurujesz lub zdefiniujesz zasady IB.

- **Sprawdź, czy rejestrowanie inspekcji jest włączone**: aby wyszukać stan aplikacji zasad IB, należy włączyć rejestrowanie inspekcji. Inspekcja jest domyślnie włączona dla organizacji Microsoft 365. Niektóre organizacje mogły wyłączyć inspekcję z określonych powodów. Jeśli inspekcja jest wyłączona dla Twojej organizacji, może to być spowodowane tym, że inny administrator wyłączył tę inspekcję. Zalecamy potwierdzenie, że podczas wykonywania tego kroku można ponownie włączyć inspekcję. Aby uzyskać więcej informacji, zobacz [Włączanie lub wyłączanie wyszukiwania dziennika inspekcji](turn-audit-log-search-on-or-off.md).

- **Usuń istniejące zasady Exchange Online książki adresowej**: przed zdefiniowaniem i zastosowaniem zasad IB musisz usunąć wszystkie istniejące zasady Exchange Online książki adresowej w organizacji. Zasady IB są oparte na zasadach książki adresowej, a istniejące zasady abp nie są zgodne z usługami ABP utworzonymi przez IB. Aby usunąć istniejące zasady książki adresowej, zobacz [Usuwanie zasad książki adresowej w Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). Aby uzyskać więcej informacji na temat zasad IB i Exchange Online, zobacz [Bariery informacyjne i Exchange Online](information-barriers.md#information-barriers-and-exchange-online).

- **Zarządzanie przy użyciu programu PowerShell (opcjonalnie)**: segmenty i zasady IB można definiować i zarządzać nimi w programie PowerShell Office 365 Security & Compliance. Chociaż w tym artykule przedstawiono kilka przykładów, musisz zapoznać się z poleceniami cmdlet i parametrami programu PowerShell, jeśli zdecydujesz się na konfigurowanie segmentów i zasad IB oraz zarządzanie nimi za pomocą programu PowerShell. Jeśli wybierzesz tę opcję konfiguracji, będziesz również potrzebować modułu Azure Active Directory programu PowerShell.
  - [Połączenie do programu PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell)
  - [Instalowanie programu Azure Active Directory PowerShell dla Graph](/powershell/azure/active-directory/install-adv2)

- **Zgoda administratora dla usługi IB w Microsoft Teams**: gdy obowiązują zasady IB, mogą usuwać użytkowników niezgodnych z IB z grup (na przykład Teams kanałów opartych na grupach). Ta konfiguracja pomaga zapewnić zgodność organizacji z zasadami i przepisami. Użyj poniższej procedury, aby umożliwić działanie zasad IB zgodnie z oczekiwaniami w Microsoft Teams.

   1. Wymagania wstępne: [zainstaluj Azure Active Directory programu PowerShell dla Graph](/powershell/azure/active-directory/install-adv2).

   2. Uruchom następujące polecenia cmdlet programu PowerShell:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   3. Po wyświetleniu monitu zaloguj się przy użyciu konta służbowego w celu Office 365.

   4. W **żądanym** oknie dialogowym Uprawnienia przejrzyj informacje, a następnie wybierz pozycję **Akceptuj**.

Po spełnieniu wszystkich wymagań wstępnych przejdź do następnego kroku.

## <a name="step-2-segment-users-in-your-organization"></a>Krok 2. Segmentuj użytkowników w organizacji

W tym kroku określisz, jakie zasady IB są potrzebne, utworzysz listę segmentów do zdefiniowania i zdefiniujesz segmenty. Definiowanie segmentów nie ma wpływu na użytkowników, tylko ustawia etap definiowania zasad IB, a następnie stosowania.

### <a name="determine-what-policies-are-needed"></a>Określanie, jakie zasady są potrzebne

Biorąc pod uwagę potrzeby organizacji, określ grupy w organizacji, które będą potrzebować zasad IB. Zadaj sobie następujące pytania:

- Czy istnieją wewnętrzne, prawne lub branżowe przepisy, które wymagają ograniczenia komunikacji i współpracy między grupami i użytkownikami w organizacji?
- Czy istnieją grupy lub użytkownicy, którym należy uniemożliwić komunikowanie się z inną grupą użytkowników?
- Czy istnieją grupy lub użytkownicy, którzy powinni mieć możliwość komunikowania się tylko z jedną lub dwiema innymi grupami użytkowników?

Pomyśl o zasadach, których potrzebujesz, jako należących do jednego z dwóch typów:

- *Zasady blokowe* uniemożliwiają jednej grupie komunikowanie się z inną grupą.
- *Zezwalaj,* aby zasady zezwalają grupie na komunikowanie się tylko z określonymi grupami.

Jeśli masz początkową listę wymaganych grup i zasad, przejdź do identyfikowania segmentów, które będą potrzebne dla zasad IB.

### <a name="identify-segments"></a>Identyfikowanie segmentów

Oprócz początkowej listy zasad utwórz listę segmentów dla swojej organizacji. Użytkownicy, którzy zostaną uwzględnieni w zasadach IB, powinni należeć do segmentu. Starannie zaplanuj segmenty, ponieważ użytkownik może znajdować się tylko w jednym segmencie. Każdy segment może mieć zastosowane tylko jedną zasadę IB.

> [!IMPORTANT]
> Użytkownik może znajdować się tylko w jednym segmencie.

Określ atrybuty w danych katalogu organizacji, których użyjesz do definiowania segmentów. Możesz użyć *działu*, *elementu członkowskiego* lub dowolnego z obsługiwanych atrybutów IB. Upewnij się, że masz wartości w atrybutze wybranym dla użytkowników. Aby uzyskać więcej informacji, zobacz [obsługiwane atrybuty dla IB](information-barriers-attributes.md).

> [!IMPORTANT]
> **Przed przejściem do następnej sekcji upewnij się, że dane katalogu zawierają wartości atrybutów, których można użyć do definiowania segmentów**. Jeśli dane katalogu nie mają wartości atrybutów, których chcesz użyć, konta użytkowników muszą zostać zaktualizowane w celu uwzględnienia tych informacji przed kontynuowaniem konfigurowania usługi IB. Aby uzyskać pomoc w tej kwestii, zobacz następujące zasoby:<br/>- [Konfigurowanie właściwości konta użytkownika za pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-the-compliance-portal"></a>Definiowanie segmentów przy użyciu portalu zgodności

Aby zdefiniować segmenty w portalu zgodności, wykonaj następujące kroki:

1. Zaloguj się do [portalu zgodności](https://compliance.microsoft.com) przy użyciu poświadczeń dla konta administratora w organizacji.
2. W portalu zgodności wybierz pozycję **Bariery** >  **informacyjneSegmenty**.
3. Na stronie **Segmenty** wybierz pozycję **Nowy segment** , aby utworzyć i skonfigurować nowy segment.
4. Na stronie **Nazwa** wprowadź nazwę segmentu. Nie można zmienić nazwy segmentu po jego utworzeniu.
5. Wybierz pozycję **Dalej**.
6. Na stronie **Filtr grupy użytkowników** wybierz pozycję **Dodaj** , aby skonfigurować atrybuty grupy i użytkownika dla segmentu. Wybierz atrybut dla segmentu z listy dostępnych atrybutów.
7. Dla wybranego atrybutu wybierz pozycję *Równe* lub *Nie równe* , a następnie wprowadź wartość atrybutu. Jeśli na przykład wybrano pozycję *Dział* jako atrybut i *Równa się*, możesz wprowadzić wartość *Marketing* jako zdefiniowany *dział* dla tego warunku segmentu. Dodatkowe warunki dla atrybutu można dodać, wybierając pozycję **Dodaj warunek**. Jeśli musisz usunąć atrybut lub warunek atrybutu, wybierz ikonę usuwania atrybutu lub warunku.
8. Dodaj dodatkowe atrybuty zgodnie z potrzebami na stronie **filtru Grupy użytkowników** , a następnie wybierz pozycję **Dalej**.
9. Na stronie **Przeglądanie ustawień przejrzyj** ustawienia wybrane dla segmentu oraz wszelkie sugestie lub ostrzeżenia dotyczące wybranych opcji. Wybierz pozycję **Edytuj** , aby zmienić dowolny z atrybutów i warunków segmentu, lub wybierz pozycję **Prześlij** , aby utworzyć segment.

    > [!IMPORTANT]
    > **Upewnij się, że segmenty nie nakładają się na siebie**. Każdy użytkownik, którego dotyczą zasady IB, powinien należeć do jednego (i tylko jednego) segmentu. Żaden użytkownik nie powinien należeć do co najmniej dwóch segmentów. Zobacz [przykład: Zdefiniowane segmenty firmy Contoso](#contosos-defined-segments) w tym artykule, aby zapoznać się z przykładowym scenariuszem.

### <a name="define-segments-using-powershell"></a>Definiowanie segmentów przy użyciu programu PowerShell

Aby zdefiniować segmenty za pomocą programu PowerShell, wykonaj następujące kroki:

1. Użyj polecenia cmdlet **New-OrganizationSegment** z parametrem **UserGroupFilter** , który odpowiada [atrybutowi](information-barriers-attributes.md) , którego chcesz użyć.

    | Składni | Przykład |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>W tym przykładzie segment o nazwie *HR* jest definiowany przy użyciu *działu kadr*, wartości w atrybucie *Dział* . Część **-eq** polecenia cmdlet odnosi się do wartości "equals". (Alternatywnie, można użyć **-ne** oznacza "nie równa się". Zobacz [Using "equals" and "not equals" in segment definitions (Używanie wartości "equals" i "not equals" w definicjach segmentów](#using-equals-and-not-equals-in-powershell-segment-definitions)). |

    Po uruchomieniu każdego polecenia cmdlet powinna zostać wyświetlona lista szczegółów dotyczących nowego segmentu. Szczegóły obejmują typ segmentu, który go utworzył lub ostatnio zmodyfikował itd. 

2. Powtórz ten proces dla każdego segmentu, który chcesz zdefiniować.

    > [!IMPORTANT]
    > **Upewnij się, że segmenty nie nakładają się na siebie**. Każdy użytkownik, którego dotyczą zasady IB, powinien należeć do jednego (i tylko jednego) segmentu. Żaden użytkownik nie powinien należeć do co najmniej dwóch segmentów. Zobacz [przykład: Zdefiniowane segmenty firmy Contoso](#contosos-defined-segments) w tym artykule, aby zapoznać się z przykładowym scenariuszem.

Po zdefiniowaniu segmentów przejdź do [kroku 3. Tworzenie zasad IB](#step-3-create-ib-policies).

### <a name="using-equals-and-not-equals-in-powershell-segment-definitions"></a>Używanie wartości "equals" i "not equals" w definicjach segmentu programu PowerShell

W poniższym przykładzie konfigurujemy segmenty IB przy użyciu programu PowerShell i definiujemy segment w taki sposób, aby "Dział był równy kadrze".

| Przykład | Uwaga |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Zwróć uwagę, że w tym przykładzie definicja segmentu zawiera parametr "equals" o wartości **-eq**. |

Segmenty można również zdefiniować przy użyciu parametru "nie równa się", oznaczonego jako **-ne**, jak pokazano w poniższej tabeli:

| Składni | Przykład |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | W tym przykładzie zdefiniowaliśmy segment o nazwie *NotSales* , który obejmuje wszystkich, którzy nie są w *sprzedaży*. - **ne** część polecenia cmdlet odnosi się do "nie równa się". |

Oprócz definiowania segmentów przy użyciu parametrów "equals" lub "not equals" można zdefiniować segment przy użyciu parametrów "equals" i "not equals". Można również zdefiniować złożone filtry grup przy użyciu operatorów logicznych *AND* i *OR* .

| Składni | Przykład |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | W tym przykładzie zdefiniowaliśmy segment o nazwie *LocalFTE* , który obejmuje użytkowników, którzy znajdują się lokalnie i których pozycje nie są wymienione jako *tymczasowe*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| W tym przykładzie zdefiniowaliśmy segment o nazwie *Segment1* , który obejmuje użytkowników będących członkami group1@contoso.com, a nie członków group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | W tym przykładzie zdefiniowaliśmy segment o nazwie *Segment2* , który obejmuje użytkowników będących członkami group2@contoso.com, a nie członków group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| W tym przykładzie zdefiniowaliśmy segment o nazwie *Segment1and2* , który obejmuje użytkowników w group1@contoso.com i group2@contoso.com, a nie członków group3@contoso.com. |

> [!TIP]
> Jeśli to możliwe, użyj definicji segmentów, które obejmują "-eq" lub "-ne". Staraj się nie definiować złożonych definicji segmentów.

## <a name="step-3-create-ib-policies"></a>Krok 3. Tworzenie zasad IB

Podczas tworzenia zasad IB określisz, czy musisz uniemożliwić komunikację między niektórymi segmentami, czy ograniczyć komunikację do niektórych segmentów. W idealnym przypadku użyjesz minimalnej liczby zasad IB, aby upewnić się, że twoja organizacja jest zgodna z wymaganiami wewnętrznymi, prawnymi i branżowymi. Za pomocą portalu zgodności lub programu PowerShell można tworzyć i stosować zasady IB.

> [!TIP]
> Aby zapewnić spójność środowiska użytkownika, zalecamy używanie zasad bloku dla większości scenariuszy, jeśli jest to możliwe.

Z listą segmentów użytkowników i zasadami IB, które chcesz zdefiniować, wybierz scenariusz, a następnie wykonaj kroki.

- [Scenariusz 1. Blokowanie komunikacji między segmentami](#scenario-1-block-communications-between-segments)
- [Scenariusz 2. Zezwalanie segmentowi na komunikowanie się tylko z jednym innym segmentem](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Upewnij się, że podczas definiowania zasad nie przypisujesz do segmentu więcej niż jednej zasady**. Jeśli na przykład zdefiniujesz jedną zasadę dla segmentu o nazwie *Sales*, nie zdefiniuj dodatkowych zasad dla segmentu *Sales* .<br> Ponadto podczas definiowania zasad IB upewnij się, że te zasady mają stan nieaktywny, dopóki nie będziesz gotowy do ich zastosowania. Definiowanie (lub edytowanie) zasad nie ma wpływu na użytkowników, dopóki te zasady nie zostaną ustawione na stan aktywny, a następnie zostaną zastosowane.

### <a name="scenario-1-block-communications-between-segments"></a>Scenariusz 1. Blokowanie komunikacji między segmentami

Jeśli chcesz zablokować komunikację między segmentami, zdefiniuj dwie zasady: jedną dla każdego kierunku. Każda zasada blokuje komunikację tylko w jednym kierunku.

Załóżmy na przykład, że chcesz zablokować komunikację między segmentem A a segmentem B. W tym przypadku należy zdefiniować dwie zasady:

- Jedna zasada uniemożliwia komunikację segmentu A z segmentem B
- Druga zasada uniemożliwia komunikację segmentu B z segmentem A

#### <a name="create-policies-using-the-compliance-portal-for-scenario-1"></a>Tworzenie zasad przy użyciu portalu zgodności dla scenariusza 1

Aby zdefiniować zasady w portalu zgodności, wykonaj następujące kroki:

1. Zaloguj się do [portalu zgodności](https://compliance.microsoft.com) przy użyciu poświadczeń dla konta administratora w organizacji.
2. W portalu zgodności wybierz pozycję **Bariery** >  **informacyjneZasady**.
3. Na stronie **Zasady** wybierz pozycję **Utwórz zasady** , aby utworzyć i skonfigurować nowe zasady IB.
4. Na stronie **Nazwa** wprowadź nazwę zasad, a następnie wybierz pozycję **Dalej**.
5. Na stronie **Przypisany segment** wybierz pozycję **Wybierz segment**. Użyj pola wyszukiwania, aby wyszukać segment według nazwy lub przewiń, aby wybrać segment z wyświetlonej listy. Wybierz pozycję **Dodaj** , aby dodać wybrany segment do zasad. Możesz wybrać tylko jeden segment.
6. Wybierz pozycję **Dalej**.
7. Na stronie **Komunikacja i współpraca** wybierz typ zasad w polu **Komunikacja i współpraca** . Opcje zasad są *dozwolone* lub *zablokowane*. W tym przykładowym scenariuszu dla pierwszych zasad zostanie *wybrana opcja Zablokowane* .

    >[!IMPORTANT]
    >Po utworzeniu zasad nie można zmienić stanu Dozwolone i Zablokowane dla segmentów. Aby zmienić stan po utworzeniu zasad, należy usunąć zasady i utworzyć nowe.

8. Wybierz pozycję **Wybierz segment** , aby zdefiniować akcje dla segmentu docelowego. W tym kroku można przypisać więcej niż jeden segment. Jeśli na przykład chcesz zablokować użytkownikom w segmencie o nazwie *Sales* komunikację z użytkownikami w segmencie o nazwie *Badania*, zdefiniowalibyśmy segment *Sales* w kroku 5 i przypiszesz opcję *Badania* w opcji **Wybierz segment** w tym kroku.
9. Wybierz pozycję **Dalej**.
10. Na stronie **Stan zasad** przełącz stan aktywnych zasad na **Wł**. Wybierz przycisk **Dalej**, aby kontynuować.
11. Na stronie **Przeglądanie ustawień przejrzyj** ustawienia wybrane dla zasad oraz wszelkie sugestie lub ostrzeżenia dotyczące wybranych opcji. Wybierz pozycję **Edytuj** , aby zmienić dowolny z segmentów zasad i stanu, lub wybierz pozycję **Prześlij** , aby utworzyć zasady.

W tym przykładzie należy powtórzyć poprzednie kroki, aby utworzyć drugą zasadę *bloku w* celu ograniczenia komunikacji użytkowników w segmencie o nazwie *Research* z użytkownikami w segmencie o nazwie *Sales*. Segment *Badania* zostałby zdefiniowany w kroku 5 i przypiszesz wartość *Sales* (lub wiele segmentów) w opcji **Wybierz segment** .

#### <a name="create-policies-using-powershell-for-scenario-1"></a>Tworzenie zasad przy użyciu programu PowerShell dla scenariusza 1

Aby zdefiniować zasady za pomocą programu PowerShell, wykonaj następujące kroki:

1. Aby zdefiniować pierwsze zasady blokowania, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsBlocked** .

    | Składni | Przykład |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady o nazwie *Sales-Research* dla segmentu o nazwie *Sales*. Gdy są aktywne i stosowane, te zasady uniemożliwiają użytkownikom w *usłudze Sales* komunikowanie się z użytkownikami w segmencie o nazwie *Badania*. |

2. Aby zdefiniować drugi segment blokowania, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsBlocked** ponownie, tym razem z odwróconymi segmentami.

    | Przykład | Uwaga |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | W tym przykładzie zdefiniowaliśmy zasady o nazwie *Research-Sales* , aby uniemożliwić programowi *Research* komunikowanie się z usługą *Sales*. |

3. Przejdź do jednej z następujących akcji:

   - (W razie potrzeby) [Definiowanie zasad umożliwiających segmentowi komunikowanie się tylko z jednym innym segmentem](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Po zdefiniowaniu wszystkich zasad) [Stosowanie zasad IB](#step-4-apply-ib-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scenariusz 2. Zezwalanie segmentowi na komunikowanie się tylko z jednym innym segmentem

Jeśli chcesz zezwolić segmentowi na komunikowanie się tylko z jednym innym segmentem, należy zdefiniować tylko jedną zasadę dla tego segmentu. Segment, z którym komunikuje się komunikacja, nie wymaga podobnych zasad kierunkowych (ponieważ domyślnie mogą komunikować się ze wszystkimi użytkownikami i współpracować z nimi).

#### <a name="create-a-policy-using-the-compliance-portal-for-scenario-2"></a>Tworzenie zasad przy użyciu portalu zgodności dla scenariusza 2

Aby zdefiniować zasady w portalu zgodności, wykonaj następujące kroki:

1. Zaloguj się do [portalu zgodności](https://compliance.microsoft.com) przy użyciu poświadczeń dla konta administratora w organizacji.
2. W portalu zgodności wybierz pozycję **Bariery** >  **informacyjneZasady**.
3. Na stronie **Zasady** wybierz pozycję **Utwórz zasady** , aby utworzyć i skonfigurować nowe zasady IB.
4. Na stronie **Nazwa** wprowadź nazwę zasad, a następnie wybierz pozycję **Dalej**.
5. Na stronie **Przypisany segment** wybierz pozycję **Wybierz segment**. Użyj pola wyszukiwania, aby wyszukać segment według nazwy lub przewiń, aby wybrać segment z wyświetlonej listy. Wybierz pozycję **Dodaj** , aby dodać wybrany segment do zasad. Możesz wybrać tylko jeden segment.
6. Wybierz pozycję **Dalej**.
7. Na stronie **Komunikacja i współpraca** wybierz typ zasad w polu **Komunikacja i współpraca** . Opcje zasad są *dozwolone* lub *zablokowane*. W tym przykładowym scenariuszu dla zasad wybrano opcję *Dozwolone* .

    >[!IMPORTANT]
    >Po utworzeniu zasad nie można zmienić stanu Dozwolone i Zablokowane dla segmentów. Aby zmienić stan po utworzeniu zasad, należy usunąć zasady i utworzyć nowe.

8. Wybierz pozycję **Wybierz segment** , aby zdefiniować akcje dla segmentu docelowego. W tym kroku można przypisać więcej niż jeden segment. Jeśli na przykład chcesz zezwolić użytkownikom w segmencie o nazwie *Manufacturing* na komunikowanie się z użytkownikami w segmencie o nazwie *HR*, zdefiniowalibyśmy segment *Produkcja* w kroku 5 i przypiszesz dział *kadr* w opcji **Wybierz segment** w tym kroku.
9. Wybierz pozycję **Dalej**.
10. Na stronie **Stan zasad** przełącz stan aktywnych zasad na **Wł**. Wybierz przycisk **Dalej**, aby kontynuować.
11. Na stronie **Przeglądanie ustawień przejrzyj** ustawienia wybrane dla zasad oraz wszelkie sugestie lub ostrzeżenia dotyczące wybranych opcji. Wybierz pozycję **Edytuj** , aby zmienić dowolny z segmentów zasad i stanu, lub wybierz pozycję **Prześlij** , aby utworzyć zasady.

#### <a name="create-a-policy-using-powershell-for-scenario-2"></a>Tworzenie zasad przy użyciu programu PowerShell dla scenariusza 2

Aby zdefiniować zasady za pomocą programu PowerShell, wykonaj następujące kroki:

1. Aby zezwolić jedneemu segmentowi na komunikowanie się tylko z jednym innym segmentem, użyj polecenia cmdlet **New-InformationBarrierPolicy** z parametrem **SegmentsAllowed** .

    | Składni | Przykład |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady o nazwie *Manufacturing-HR* dla segmentu o nazwie *Manufacturing*. Gdy są aktywne i stosowane, te zasady umożliwiają użytkownikom w *usłudze Manufacturing komunikowanie* się tylko z użytkownikami w segmencie o nazwie *HR*. W takim przypadku *usługa Manufacturing* nie może komunikować się z użytkownikami, którzy nie są częścią *działu kadr*. |

    **W razie potrzeby można określić wiele segmentów za pomocą tego polecenia cmdlet, jak pokazano w poniższym przykładzie.**

    | Składni | Przykład |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> W tym przykładzie zdefiniowaliśmy zasady, które umożliwiają segmentowi *Research* komunikowanie się tylko z *działem kadr* i *produkcją*. |

    Powtórz ten krok dla każdej zasady, którą chcesz zdefiniować, aby umożliwić określonym segmentom komunikowanie się tylko z niektórymi innymi określonymi segmentami.

2. Przejdź do jednej z następujących akcji:

   - (W razie potrzeby) [Definiowanie zasad blokujących komunikację między segmentami](#scenario-1-block-communications-between-segments) 
   - (Po zdefiniowaniu wszystkich zasad) [Stosowanie zasad IB](#step-4-apply-ib-policies)

## <a name="step-4-apply-ib-policies"></a>Krok 4. Stosowanie zasad IB

Zasady IB nie są stosowane, dopóki nie ustawisz ich na stan aktywny i nie zastosujesz zasad.

### <a name="apply-policies-using-the-compliance-portal"></a>Stosowanie zasad przy użyciu portalu zgodności

Aby zastosować zasady w portalu zgodności, wykonaj następujące kroki:

1. Zaloguj się do [portalu zgodności](https://compliance.microsoft.com) przy użyciu poświadczeń dla konta administratora w organizacji.
2. W portalu zgodności wybierz pozycję **Bariery informacyjneZasady** >  **aplikacji**.
3. Na stronie **Aplikacja zasady** wybierz pozycję **Zastosuj wszystkie zasady** , aby zastosować wszystkie zasady IB w organizacji.

    >[!NOTE]
    >Zaczekaj 30 minut na rozpoczęcie stosowania zasad przez system. System stosuje zasady użytkownika według użytkownika. System przetwarza około 5000 kont użytkowników na godzinę.

### <a name="apply-policies-using-powershell"></a>Stosowanie zasad przy użyciu programu PowerShell

Aby zastosować zasady przy użyciu programu PowerShell, wykonaj następujące kroki:

1. Użyj polecenia cmdlet **Get-InformationBarrierPolicy** , aby wyświetlić listę zdefiniowanych zasad. Zwróć uwagę na stan i tożsamość (GUID) poszczególnych zasad.

    Składni: `Get-InformationBarrierPolicy`

2. Aby ustawić stan aktywny zasad, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem **Identity** i parametru **State** ustawionego na **Aktywny**. 

    | Składni | Przykład |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> W tym przykładzie ustawiliśmy zasady IB o identyfikatorze GUID *43c37853-ea10-4b90-a23d-ab8c93772471* jako stan aktywny. |

    Powtórz ten krok zgodnie z potrzebami dla poszczególnych zasad.

3. Po zakończeniu ustawiania stanu aktywnego zasad IB użyj polecenia cmdlet **Start-InformationBarrierPoliciesApplication** w programie PowerShell Security & Compliance.

    Składni: `Start-InformationBarrierPoliciesApplication`

    Po uruchomieniu `Start-InformationBarrierPoliciesApplication`programu zaczekaj 30 minut na rozpoczęcie stosowania zasad przez system. System stosuje zasady użytkownika według użytkownika. System przetwarza około 5000 kont użytkowników na godzinę.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Wyświetlanie stanu kont użytkowników, segmentów, zasad lub aplikacji zasad

Za pomocą programu PowerShell można wyświetlić stan kont użytkowników, segmentów, zasad i aplikacji zasad, jak pokazano w poniższej tabeli.

| Aby wyświetlić te informacje | Wykonaj tę akcję |
|:---------------|:----------|
| Konta użytkowników | Użyj polecenia cmdlet **Get-InformationBarrierRecipientStatus** z parametrami tożsamości. <p> Składni: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, takiej jak nazwa, alias, nazwa wyróżniająca, nazwa domeny kanonicznej, adres e-mail lub identyfikator GUID. <p> Przykład: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> W tym przykładzie odwołujemy się do dwóch kont użytkowników w Office 365: *meganb* dla *Megan* i *alexw* dla *Alex*. <p> (Możesz również użyć tego polecenia cmdlet dla jednego użytkownika: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> To polecenie cmdlet zwraca informacje o użytkownikach, takie jak wartości atrybutów i zastosowane zasady IB.|
| Segmenty | Użyj polecenia cmdlet **Get-OrganizationSegment** .<p> Składni: `Get-OrganizationSegment` <p> To polecenie cmdlet wyświetli listę wszystkich segmentów zdefiniowanych dla twojej organizacji. |
| Zasady IB | Użyj polecenia cmdlet **Get-InformationBarrierPolicy** . <p> Składni: `Get-InformationBarrierPolicy` <p> To polecenie cmdlet wyświetli listę zdefiniowanych zasad IB oraz ich stan. |
| Najnowsza aplikacja zasad IB | Użyj polecenia cmdlet **Get-InformationBarrierPoliciesApplicationStatus** . <p> Składni: `Get-InformationBarrierPoliciesApplicationStatus`<p> To polecenie cmdlet wyświetli informacje o tym, czy aplikacja zasad została ukończona, zakończona niepowodzeniem, czy jest w toku. |
| Wszystkie aplikacje zasad IB|Używać `Get-InformationBarrierPoliciesApplicationStatus -All`<p> To polecenie cmdlet wyświetli informacje o tym, czy aplikacja zasad została ukończona, zakończona niepowodzeniem, czy jest w toku.|

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Co zrobić, jeśli muszę usunąć lub zmienić zasady?

Dostępne są zasoby ułatwiające zarządzanie zasadami IB.

- Aby edytować, zatrzymać lub usunąć zasady IB, zobacz [Zarządzanie zasadami barier informacyjnych](information-barriers-edit-segments-policies.md).
- Jeśli coś pójdzie nie tak z usługą IB, zobacz [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Krok 5. Konfiguracja barier informacyjnych na SharePoint i OneDrive

Jeśli konfigurujesz protokół IB dla SharePoint i OneDrive, musisz włączyć usługę IB w tych usługach. Jeśli konfigurujesz protokół IB pod kątem Microsoft Teams, musisz również włączyć funkcję IB w tych usługach. Po utworzeniu zespołu w zespole Microsoft Teams witryna SharePoint jest automatycznie tworzona i skojarzona z Microsoft Teams dla środowiska plików. Zasady IB nie są domyślnie przestrzegane w tej nowej witrynie SharePoint i plikach.

Aby włączyć funkcję IB w SharePoint i OneDrive, postępuj zgodnie ze wskazówkami i [krokami w artykule Korzystanie z barier informacyjnych z SharePoint](/sharepoint/information-barriers).

## <a name="step-6-information-barriers-modes"></a>Krok 6. Tryby barier informacyjnych

Tryby mogą pomóc wzmocnić dostęp, udostępnianie i członkostwo w zasobie Microsoft 365 w oparciu o tryb IB zasobu. Tryby są obsługiwane w lokacjach Grupy Microsoft 365, Microsoft Teams, OneDrive i SharePoint i są automatycznie włączane w nowej lub istniejącej konfiguracji IB.

Następujące tryby IB są obsługiwane w zasobach Microsoft 365:

| **Tryb** | **Opis** | **Przykład** |
|:-----|:------------|:--------|
| **Otwórz** | Nie ma żadnych zasad IB ani segmentów skojarzonych z zasobem Microsoft 365. Każdy może zostać zaproszony do udziału w zasobie. | Witryna zespołu utworzona na potrzeby imprezy piknikowej dla Twojej organizacji. |
| **Moderowany przez właściciela (wersja zapoznawcza)** | Zasady IB zasobu Microsoft 365 są określane na podstawie zasad IB właściciela zasobu. Właściciele zasobów mogą zapraszać dowolnego użytkownika do zasobu na podstawie zasad IB. Ten tryb jest przydatny, gdy firma chce zezwolić na współpracę między niezgodnych użytkowników segmentu, które są moderowane przez właściciela. Tylko właściciel zasobu może dodawać nowych członków według zasad IB. | Wirtualny przedstawiciel działu kadr chce współpracować z wirtualnymi przedstawicielami ds. sprzedaży i badań. Nowa witryna SharePoint, która jest ustawiona z *moderem właściciela* trybu IB, aby dodać użytkowników segmentu Sprzedaż i badania do tej samej witryny. Właściciel jest odpowiedzialny za zapewnienie, że do zasobu zostaną dodane odpowiednie elementy członkowskie. |
| **Niejawne** | Zasady IB lub segmenty zasobu Microsoft 365 są dziedziczone z zasad IB elementów członkowskich zasobów. Właściciel może dodawać członków, o ile są one zgodne z istniejącymi członkami zasobu. Ten tryb jest domyślnym trybem IB dla Microsoft Teams. | Użytkownik segmentu Sales tworzy zespół Microsoft Teams do współpracy z innymi zgodnymi segmentami w organizacji. |
| **Jawne** | Zasady IB zasobu Microsoft 365 są według segmentów skojarzonych z zasobem. Właściciel zasobu lub administrator SharePoint może zarządzać segmentami zasobu.  | Witryna utworzona tylko dla członków segmentu Sales w celu współpracy przez skojarzenie segmentu Sales z witryną.   |

Aby uzyskać więcej informacji na temat trybów IB i sposobu ich konfigurowania w usługach, zobacz następujące artykuły:

- [Tryby i Microsoft Teams barier informacyjnych](/microsoftteams/information-barriers-in-teams)
- [Tryby i OneDrive barier informacyjnych](/onedrive/information-barriers)
- [Tryby i SharePoint barier informacyjnych](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Przykładowy scenariusz: działy, segmenty i zasady firmy Contoso

Aby zobaczyć, jak organizacja może podejść do definiowania segmentów i zasad, rozważ poniższy przykładowy scenariusz.

### <a name="contosos-departments-and-plan"></a>Działy i plan firmy Contoso

Firma Contoso ma pięć działów: *HR*, *Sales*, *Marketing*, *Research* i *Manufacturing*. Aby zachować zgodność z przepisami branżowymi, użytkownicy w niektórych działach nie powinni komunikować się z innymi działami, jak wymieniono w poniższej tabeli:

| Segmentu | Może komunikować się z | Nie można komunikować się z |
|:----------|:--------------|:-----------------|
| HR | Wszyscy | (bez ograniczeń) |
| Sprzedaży | HR, Marketing, Manufacturing | Poszukiwanie |
| Marketing | Wszyscy | (bez ograniczeń) |
| Poszukiwanie | HR, Marketing, Manufacturing | Sprzedaży |
| Produkcji | HR, Marketing | Każda osoba inna niż hr lub marketing |

W przypadku tej struktury plan firmy Contoso obejmuje trzy zasady IB:

1. Zasady IB mające na celu uniemożliwienie komunikacji sprzedaży z programem Research
2. Inne zasady IB uniemożliwiające programowi Research komunikowanie się z usługą Sales.
3. Zasady IB mające na celu umożliwienie usłudze Manufacturing komunikowania się tylko z działem kadr i marketingiem.

W tym scenariuszu nie trzeba definiować zasad IB dla *kadr* lub *marketingu*.

### <a name="contosos-defined-segments"></a>Zdefiniowane segmenty firmy Contoso

Firma Contoso użyje atrybutu Dział w Azure Active Directory, aby zdefiniować segmenty w następujący sposób:

| Department | Definicja segmentu |
|:-------------|:---------------------|
| HR | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Sprzedaży | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Poszukiwanie | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Produkcji | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Po zdefiniowaniu segmentów firma Contoso definiuje zasady IB.

### <a name="contosos-ib-policies"></a>Zasady IB firmy Contoso

Firma Contoso definiuje trzy zasady IB zgodnie z opisem w poniższej tabeli:

| Zasad | Definicja zasad |
|:---------|:--------------------|
| **Zasady 1: Uniemożliwianie komunikacji sprzedaży z programem Research** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> W tym przykładzie zasady IB są nazywane *Sales-Research*. Gdy te zasady są aktywne i stosowane, pomogą uniemożliwić użytkownikom należącym do segmentu Sales komunikowanie się z użytkownikami w segmencie Badania. Te zasady są zasadami jednokierunkowymi; Nie uniemożliwi to badaniu komunikowania się z usługą Sales. W tym celu wymagana jest zasada 2. |
| **Zasady 2: Uniemożliwiaj badaniu komunikowanie się ze sprzedażą** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> W tym przykładzie zasady IB są nazywane *Research-Sales*. Gdy te zasady są aktywne i stosowane, pomogą uniemożliwić użytkownikom należącym do segmentu Badania komunikowanie się z użytkownikami w segmencie Sprzedaż. |
| **Zasady 3: Zezwalaj produkcji na komunikowanie się tylko z działem kadr i marketingiem** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> W tym przypadku zasady IB są *nazywane Manufacturing-HRMarketing*. Gdy te zasady są aktywne i stosowane, usługa Manufacturing może komunikować się tylko z działem kadr i marketingiem. Dział kadr i marketing nie są ograniczone do komunikowania się z innymi segmentami. |

Po zdefiniowaniu segmentów i zasad firma Contoso stosuje zasady, uruchamiając polecenie cmdlet **Start-InformationBarrierPoliciesApplication** .

Po zakończeniu polecenia cmdlet firma Contoso jest zgodna z wymaganiami branżowymi.

## <a name="resources"></a>Zasoby

- [Dowiedz się więcej o barierach informacyjnych](information-barriers.md)
- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w usłudze SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w OneDrive](/onedrive/information-barriers)
