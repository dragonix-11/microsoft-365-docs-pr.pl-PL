---
title: Konfigurowanie ustawień przechowywania w celu automatycznego zachowywania lub usuwania zawartości
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Opis ustawień, które można skonfigurować w zasadach przechowywania lub zasadach etykiet przechowywania, aby zachować to, co chcesz, i usunąć to, co nie chcesz.
ms.openlocfilehash: 3b2833b2b6293845379f9f5aeffd3bd46610e2a8
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63713080"
---
# <a name="common-settings-for-retention-policies-and-retention-label-policies"></a>Typowe ustawienia zasad przechowywania i zasad etykiet przechowywania

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](https://aka.ms/ComplianceSD).*

Wiele ustawień przechowywania jest wspólnych zarówno dla zasad przechowywania, jak i zasad etykiet przechowywania. Poniższe informacje ułatwiają skonfigurowanie tych ustawień w taki sposób, aby aktywnie zachowywać zawartość, usuwać ją lub zachowywać, a następnie usuwać.

Aby uzyskać scenariusze obsługi tych zasad przechowywania, zobacz:

- [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md).
- [Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)

Ustawienia scenariuszy zostały opisane w odpowiedniej dokumentacji.

Aby uzyskać ogólne informacje na temat zasad przechowywania i sposobu działania przechowywania w aplikacji Microsoft 365, zobacz Informacje o zasadach przechowywania [i etykietach przechowywania](retention.md).

## <a name="scopes---adaptive-and-static"></a>Zakresy — adaptacyjne i statyczne

Jeśli nie wiesz, jakie zakresy są adaptacyjne i statyczne, i aby ułatwić Ci wybranie, którego z nich będziesz używać podczas konfigurowania zasad przechowywania, zobacz Adaptacyjne lub statyczne zakresy zasad [przechowywania.](retention.md#adaptive-or-static-policy-scopes-for-retention) 

Jeśli zdecydowasz, czy użyć adaptacyjnego, czy statycznego zakresu, skorzystaj z następujących informacji, aby go skonfigurować:
- [Informacje o konfiguracji dla adaptacyjnych zakresów](#configuration-information-for-adaptive-scopes)
- [Informacje o konfiguracji dla zakresów statycznych](#configuration-information-for-static-scopes)

> [!TIP]
> Jeśli masz zasady, które używają zakresów statycznych i chcesz przekonwertować je na adaptacyjne zakresy, pozostaw istniejące zasady na miejscu podczas tworzenia nowych zasad, które używają adaptacyjnych zakresów z tych samych ustawień przechowywania. Sprawdź, czy te nowe zasady są przeznaczone dla poprawnych użytkowników, witryn i grup, zanim wyłączysz lub usuniesz stare zasady ze statycznym zakresem.

### <a name="configuration-information-for-adaptive-scopes"></a>Informacje o konfiguracji dla adaptacyjnych zakresów

Gdy wybierzesz zakresy adaptacyjne, zostanie wyświetlony monit o wybranie odpowiedniego typu adaptacyjnego zakresu. Istnieją trzy różne typy adaptacyjnych zakresów i każdy z nich obsługuje inne atrybuty lub właściwości:

| Adaptacyjny typ zakresu | Obsługiwane są następujące atrybuty lub właściwości |
|:-----|:-----|
|**Użytkownicy** — dotyczy:  <br/> — Exchange-mail <br/> — OneDrive konta <br/> — Teams czatów <br/> — Teams wiadomości z kanału prywatnego <br/> — Yammer wiadomości od użytkowników| Imię <br/> Nazwisko <br/>Nazwa wyświetlana <br/> Stanowisko <br/> Department <br/> Pakiet Office <br/>Ulica <br/> Miasto <br/>Województwo <br/>Kod pocztowy <br/> Kraj lub region <br/> Adresy e-mail <br/> Alias <br/> Exchange atrybuty niestandardowe: CustomAttribute1 — CustomAttribute15|
|**SharePoint witryn —** dotyczy:  <br/> — SharePoint witryn <br/> — OneDrive konta |Adres URL witryny <br/>Nazwa witryny <br/> SharePoint właściwości niestandardowe: RefinableString00 - RefinableString99 |
|**Microsoft 365 grupy —** dotyczy:  <br/> — Microsoft 365 grupy <br/> - Teams wiadomości kanału (standardowe i udostępnione) <br/> — Yammer wiadomości od społeczności |Name (Nazwa) <br/> Nazwa wyświetlana <br/> Opis <br/> Adresy e-mail <br/> Alias <br/> Exchange atrybuty niestandardowe: CustomAttribute1 — CustomAttribute15 |

Nazwy właściwości witryn są oparte na SharePoint właściwościach zarządzanych witryny. Aby uzyskać informacje na temat atrybutów niestandardowych, zobacz Stosowanie SharePoint właściwości witryny niestandardowej w Microsoft 365 [z adaptacyjnym zakresem zasad](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

Nazwy atrybutów użytkowników i grup są oparte na filtrowanych właściwościach [adresatów](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties) mapowanych na atrybuty usługi Azure AD. Przykład:

- **Alias** mapuje nazwę LDAP **mailNickname**, która jest wyświetlana jako **Wiadomość e-mail** w centrum administracyjnym usługi Azure AD.
- **Adresy e-mail** są mapowane na adres **proxyAddresses** nazwy LDAP, który jest wyświetlany jako **adres serwera proxy** w centrum administracyjnym usługi Azure AD.

Atrybuty i właściwości wymienione w tabeli można łatwo określić podczas konfigurowania adaptacyjnego zakresu za pomocą prostego konstruktora zapytań. Dodatkowe atrybuty i właściwości są obsługiwane przez zaawansowanego konstruktora zapytań, zgodnie z opisem w następnej sekcji.

> [!TIP]
> Aby uzyskać dodatkowe informacje na temat używania zaawansowanego konstruktora zapytań, zobacz następujące seminaria w sieci Web: 
> - [Tworzenie zaawansowanych zapytań dla użytkowników i grup za pomocą adaptacyjnych zakresów zasad](https://mipc.eventbuilder.com/event/52683/occurrence/49452/recording?rauth=853.3181650.1f2b6e8b4a05b4441f19b890dfeadcec24c4325e90ac492b7a58eb3045c546ea)
> - [Tworzenie zaawansowanych zapytań dla witryn SharePoint za pomocą adaptacyjnych zakresów zasad](https://aka.ms/AdaptivePolicyScopes-AdvancedSharePoint)

Jedna zasada przechowywania może mieć jeden lub wiele adaptacyjnych zakresów.

#### <a name="to-configure-an-adaptive-scope"></a>Aby skonfigurować adaptacyjny zakres

Przed skonfigurowaniem adaptacyjnego zakresu skorzystaj z poprzedniej sekcji, aby zidentyfikować typ zakresu do utworzenia oraz atrybuty i wartości, których będziesz używać. Może być konieczne potwierdzenie tych informacji we współpracy z innymi administratorami. 

W szczególności SharePoint witryny internetowe mogą wymagać dodatkowej SharePoint, jeśli planujesz użyć [niestandardowych właściwości witryny](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com/) do jednej z następujących lokalizacji:
    
    - Jeśli używasz rozwiązania do zarządzania rekordami:
        - **Rozwiązania** >  **Zarządzanie rekordami** >  **Karta Zakresy adaptacyjne** > + **Tworzenie zakresu**
        
    - W przypadku korzystania z rozwiązania do zarządzania informacjami:
       - **Rozwiązania** >  **Zarządzanie informacjami** >  **Karta Zakresy adaptacyjne** > + **Tworzenie zakresu**
    
    Nie widzisz swojego rozwiązania od razu w okienku nawigacji? Najpierw wybierz pozycję **Pokaż wszystko**. 

2. Postępuj zgodnie z monitami w konfiguracji, aby najpierw wybrać typ zakresu, a następnie wybrać atrybuty lub właściwości, za pomocą których chcesz utworzyć członkostwo dynamiczne, i wpisz wartości atrybutów lub właściwości.
    
    Aby na przykład skonfigurować adaptacyjny zakres, który będzie używany do identyfikowania użytkowników w Europie, najpierw wybierz pozycję  Użytkownicy jako typ zakresu, a następnie wybierz atrybut Kraj lub **region** i **wpisz w Europie**:
    
    ![Przykład adaptacyjnej konfiguracji zakresu.](../media/example-adaptive-scope.png)
    
    Raz dziennie to zapytanie będzie uruchamiane w usłudze Azure AD i zidentyfikuje wszystkich użytkowników, którzy mają wartość Europa określoną na koncie dla **atrybutu Country lub region**.
    
    > [!IMPORTANT]
    > Ponieważ zapytanie nie zostanie uruchomione natychmiast, nie będzie sprawdzania poprawności wpisania wartości.
    
    Wybierz **pozycję Dodaj atrybut** (dla użytkowników i grup) lub Dodaj **właściwość (dla** witryn), aby użyć dowolnej kombinacji atrybutów lub właściwości, które są obsługiwane dla ich typu zakresu, wraz z operatorami logicznymi do tworzenia zapytań. Obsługiwane operatory **są równe****, nie** są **równe, zaczynają** się od i nie są rozpoczynane **oraz można** grupować wybrane atrybuty lub właściwości. Przykład:
    
    ![Przykład adaptacyjnej konfiguracji zakresu z grupami atrybutów.](../media/example-adaptive-scope-grouping.png)
    
    Alternatywnie możesz wybrać pozycję **Zaawansowany konstruktor zapytań** , aby określić własne zapytania:
    
    - W **przypadku** **zakresów Microsoft 365** użytkowników i grup należy użyć składni [filtrowania OPATH](/powershell/exchange/recipient-filters). Aby na przykład utworzyć zakres użytkowników definiujący jego członkostwo według działu, kraju i stanu:
    
        ![Przykład adaptacyjnego zakresu za pomocą zapytania zaawansowanego.](../media/example-adaptive-scope-advanced-query.png)
        
        Jedną z zalet używania zaawansowanego konstruktora zapytań w tych zakresach jest szerszy wybór operatorów zapytań:
        - **i**
        - **lub**
        - **nie**
        - **eq** (równa się)
        - **ne** (nie równa się)
        - **lt** (mniej niż)
        - **gt** (większe niż)
        - **like** (porównanie ciągów)
        - **notlike** (porównanie ciągów)
    
    - Aby **SharePoint zakresów** witryn, użyj języka Keyword Query Language (KQL). Być może wiesz już, jak używać KQL do SharePoint przy użyciu właściwości witryny indeksowanych. Aby ułatwić ci określenie tych zapytań KQL, zobacz Informacje dotyczące składni w języku [KQL (Keyword Query Language](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)).
        
        Ponieważ na przykład zakresy witryn SharePoint automatycznie obejmują wszystkie typy witryn sieci SharePoint, takie jak witryny Microsoft 365 połączone z grupą i witryny typu OneDrive, można użyć zindeksowanych właściwości **siteTemplate**, aby uwzględnić lub wykluczyć określone typy witryn. Szablony, które można określić:
        - SITEPAGEPUBLISHING dla witryn nowoczesnej komunikacji
        - GROUP for Microsoft 365 group-connected sites
        - TEAMCHANNEL dla Microsoft Teams kanałów prywatnych
        - StS (StS) dla SharePoint zespołu
        - SPSPERS dla witryn OneDrive witryn
        
        Aby zatem utworzyć adaptacyjny zakres, który obejmuje tylko nowoczesne witryny do komunikacji i z wyłączeniem Microsoft 365 połączonych ze stronami połączonymi ze stronami OneDrive, określ następujące zapytanie KQL:
        ````console
        SiteTemplate=SITEPAGEPUBLISHING
        ````
    
    Zapytania zaawansowane [można sprawdzać niezależnie](#validating-advanced-queries) od konfiguracji zakresu.
    
    > [!TIP]
    > Aby wykluczyć nieaktywne skrzynki pocztowe, należy użyć zaawansowanego konstruktora zapytań. I odwrotnie, do docelowych są po prostu nieaktywne skrzynki pocztowe. W przypadku tej konfiguracji użyj właściwości OPATH *IsInactiveMailbox*:
    > 
    > - Aby wykluczyć nieaktywne skrzynki pocztowe, upewnij się, że zapytanie zawiera: `(IsInactiveMailbox -eq "False")`
    > - Aby kierować tylko nieaktywne skrzynki pocztowe, określ: `(IsInactiveMailbox -eq "True")`

3. Utwórz tyle adaptacyjnych zakresów, ile potrzebujesz. Możesz wybrać co najmniej jeden adaptacyjny zakres podczas tworzenia zasad przechowywania.

> [!NOTE]
> Pełne wypełnienie zapytań może potrwać do pięciu dni, a zmiany nie zostaną natychmiast wprowadzone. Czynnik tego opóźnienia należy odczekać kilka dni przed dodaniem nowo utworzonego zakresu do zasad przechowywania.

Aby potwierdzić bieżące zmiany członkostwa i członkostwa w zakresie adaptacyjnym:

1. Kliknij dwukrotnie (lub wybierz i naciśnij klawisz Enter) zakres na stronie **Zakresy adaptacyjne**

2. W okienku **Szczegóły wysuwu** wybierz pozycję **Szczegóły zakresu**. 
    
    Przejrzyj informacje identyfikujące wszystkich użytkowników, witryn lub grup obecnie w zakresie, jeśli zostali oni automatycznie dodani lub usunięci, oraz datę i godzina zmiany członkostwa.

> [!TIP]
> Opcja [odnośnika zasad pomoże](retention.md#policy-lookup) Ci w zidentyfikowaniu zasad obecnie przypisanych do określonych użytkowników, witryn i Microsoft 365 grupy.

#### <a name="validating-advanced-queries"></a>Sprawdzania poprawności zapytań zaawansowanych

Zapytania zaawansowane można ręcznie sprawdzać za pomocą programu PowerShell SharePoint wyszukiwania:
- Typy zakresów Użytkownicy i Grupy  Microsoft 365 **programu PowerShell**
- Używanie SharePoint wyszukiwania typów zakresów **SharePoint witryn**

Aby uruchomić zapytanie przy użyciu programu PowerShell:

1. [Połączenie użyć Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) przy użyciu konta z odpowiednimi uprawnieniami [Exchange Online administratora](/powershell/exchange/find-exchange-cmdlet-permissions#use-powershell-to-find-the-permissions-required-to-run-a-cmdlet).

2. Użyj [get-recipient lub](/powershell/module/exchange/get-recipient) [Get-Mailbox](/powershell/module/exchange/get-mailbox) z *parametrem -Filter* i [zapytaniem OPATH](/powershell/exchange/filter-properties) , aby ująć zakres adaptacyjny w nawiasy klamrowe (`{`,`}`). Jeśli wartości atrybutów są ciągami, należy je ująć w podwójny lub pojedynczy cudzysłów.  

    Możesz określić, czy `Get-Mailbox` `Get-Recipient` chcesz użyć polecenia cmdlet, czy sprawdzić jego poprawność, przez określenie, które polecenie cmdlet jest obsługiwane przez właściwość [OPATH](/powershell/exchange/filter-properties) wybieraną dla zapytania.

    > [!IMPORTANT]
    > `Get-Mailbox` nie obsługuje typu adresata *MailUser* , dlatego `Get-Recipient` należy go używać do sprawdzania poprawności zapytań, które zawierają lokalne skrzynki pocztowe w środowisku hybrydowym.

    Aby sprawdzić **poprawność zakresu** użytkownika, użyj jednej z tych funkcji:
    - `Get-Mailbox`z lub `-RecipientTypeDetails UserMailbox`
    - `Get-Recipient` z `-RecipientTypeDetails UserMailbox,MailUser`
    
    Aby sprawdzić poprawność **Microsoft 365 zakresu** grupy, użyj:
    - `Get-Mailbox`lub z `Get-Recipient``-RecipientTypeDetails GroupMailbox`

    Aby na przykład sprawdzić poprawność **zakresu** użytkownika, możesz użyć:
    
    ````PowerShell
    Get-Recipient -RecipientTypeDetails UserMailbox,MailUser -Filter {Department -eq "Marketing"} -ResultSize Unlimited
    ````
    
    Aby sprawdzić **poprawność Microsoft 365 zakresu** grupy, możesz użyć:
    
    ```PowerShell
    Get-Mailbox -RecipientTypeDetails GroupMailbox -Filter {CustomAttribute15 -eq "Marketing"} -ResultSize Unlimited
    ```

3. Sprawdź, czy dane wyjściowe są takie, jak oczekiwani użytkownicy lub grupy w ramach adaptacyjnego zakresu. Jeśli tak się nie stanie, sprawdź zapytanie i wartości u odpowiedniego administratora usługi Azure AD lub Exchange.
 
Aby uruchomić zapytanie przy użyciu SharePoint wyszukiwania:

1. Używając konta administratora globalnego lub konta z SharePoint administratora globalnego, przejdź do pozycji `https://<your_tenant>.sharepoint.com/search`.

2. Użyj paska wyszukiwania, aby określić zapytanie KQL.

3. Sprawdź, czy wyniki wyszukiwania są zgodne z oczekiwanymi adresami URL witryny dla adaptacyjnego zakresu. Jeśli tak się nie stanie, sprawdź zapytanie i adresy URL u odpowiedniego administratora, aby uzyskać więcej SharePoint.

### <a name="configuration-information-for-static-scopes"></a>Informacje o konfiguracji dla zakresów statycznych

Gdy zdecydujesz się używać zakresów statycznych, musisz zdecydować, czy zasady mają być stosowane do wszystkich wystąpień dla wybranej lokalizacji (całej lokalizacji), czy do uwzględnienia bądź wykluczenia określonych wystąpień (określonych dołączeń lub wykluczeń).

#### <a name="a-policy-that-applies-to-entire-locations"></a>Zasady dotyczące całych lokalizacji

Z wyjątkiem Skype dla firm domyślnie wszystkie wystąpienia wybranych lokalizacji są automatycznie uwzględniane w zasadach bez konieczności ich określania jako uwzględnionych.

Na przykład: **Wszyscy adresaci** w Exchange **e-mail**. Po ustawieniu domyślnym wszystkie istniejące skrzynki pocztowe użytkowników będą uwzględniane w zasadach, a wszystkie nowe skrzynki pocztowe utworzone po zastosowaniu zasad automatycznie odziedziczą zasady.

#### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Zasady z określonymi dołączeniami lub wykluczeniami

Jeśli korzystasz z opcjonalnej konfiguracji w celu ograniczenia ustawień przechowywania do konkretnych użytkowników, konkretnych grup Microsoft 365 lub konkretnych witryn, istnieją pewne ograniczenia dotyczące zasad, o których należy pamiętać. Aby uzyskać więcej informacji, [zobacz Limity dotyczące zasad przechowywania i zasad etykiet przechowywania](retention-limits.md). 

Aby użyć opcjonalnej konfiguracji w celu ustawienia zakresu ustawień przechowywania, upewnij się, że stan tej lokalizacji jest Wł **., a** następnie użyj linków, aby uwzględnić lub wykluczyć określonych użytkowników, Microsoft 365 grupy lub witryny.

> [!WARNING]
> Jeśli skonfigurujesz wystąpienia tak, aby uwzględniały i usuwały ostatnie, dla lokalizacji zostanie przywrócona  opcja Wszystkie.  Przed zapisaniem zasad upewnij się, że jest to konfiguracja, która ma być przez Ciebie zamierzana.
>
> Jeśli na przykład określisz jedną witrynę programu SharePoint, która ma zostać dołączona do zasad przechowywania skonfigurowanych do usuwania danych, SharePoint następnie usuniesz pojedynczą witrynę, domyślnie wszystkie witryny programu SharePoint będą podlegały zasadom przechowywania, które trwale usuwają dane. To samo dotyczy także adresatów Exchange, OneDrive, użytkowników Teams czatów itp.
>
> W tym scenariuszu wyłącz lokalizację, jeśli nie chcesz, aby ustawienie Wszystkie dla  lokalizacji podlegało zasadom przechowywania. Możesz również określić wykluczanie wystąpień wykluczania z zasad.

## <a name="locations"></a>Lokalizacje

Lokalizacje w zasadach przechowywania identyfikują określone usługi Microsoft 365, które obsługują ustawienia przechowywania, takie jak poczta e-mail Exchange i witryny SharePoint sieci Web. W poniższej sekcji znajdziesz lokalizacje ze szczegółami konfiguracji i możliwymi wyjątkami, o których musisz pamiętać podczas wybierania ich do zasad.

### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a>Informacje o konfiguracji poczty Exchange e-mail Exchange folderach publicznych

Lokalizacja **Exchange-mail** obsługuje przechowywanie wiadomości e-mail, kalendarza i innych elementów skrzynki pocztowej użytkowników, stosując ustawienia przechowywania na poziomie skrzynki pocztowej. Udostępnione skrzynki pocztowe są również obsługiwane.

Skrzynki pocztowe zasobów, kontakty i skrzynki Microsoft 365 grupy nie są obsługiwane w przypadku Exchange e-mail. Aby Microsoft 365 skrzynki pocztowe grup, wybierz zamiast **Microsoft 365 grupy.** Mimo że lokalizacja Exchange początkowo pozwala na wybór skrzynki pocztowej grupy w zakresie statycznym, podczas próby zapisania zasad przechowywania jest wyświetlany komunikat o błędzie, że "RemoteGroupMailbox" nie jest prawidłową wartością wyboru dla tej lokalizacji.

W zależności od konfiguracji [zasad mogą być](inactive-mailboxes-in-office-365.md) uwzględniane nieaktywne skrzynki pocztowe:

- Zakresy statycznych zasad obejmują nieaktywne skrzynki pocztowe,  jeśli używasz domyślnej konfiguracji Wszyscy adresaci, ale nie są obsługiwani w przypadku określonych dołączeń [lub wykluczeń](#a-policy-with-specific-inclusions-or-exclusions). Jeśli jednak uwzględnisz lub wykluczysz adresata, który ma aktywną skrzynkę pocztową w momencie stosowania zasad, a skrzynka pocztowa zostanie później nieaktywna, ustawienia przechowywania będą nadal stosowane lub wykluczane.

- Zakresy adaptacyjnych zasad domyślnie obejmują nieaktywne skrzynki pocztowe, gdy spełniają one zapytanie zakresu. Można je wykluczyć przy użyciu zaawansowanego konstruktora zapytań i właściwości OPATH *IsInactiveMailbox*:
    
    ```console
    (IsInactiveMailbox -eq "False")
    ```

Jeśli użyjesz statycznego zakresu zasad i wybierzesz adresatów, którzy będą dołączać lub wykluczać, możesz wybrać grupy dystrybucyjne i grupy zabezpieczeń z obsługą poczty e-mail jako wydajny sposób wybierania wielu adresatów zamiast wybierania ich jeden po jeden. Gdy użyjesz tej opcji, te grupy są automatycznie rozszerzane w tle w czasie konfiguracji w celu wybrania skrzynek pocztowych użytkowników w grupie. W przypadku późniejszej zmiany członkostwa w tych grupach istniejące zasady przechowywania nie są automatycznie aktualizowane, w przeciwieństwie do adaptacyjnych zakresów zasad.

Aby uzyskać szczegółowe informacje o tym, które elementy skrzynki pocztowej są uwzględniane i wykluczane podczas konfigurowania ustawień przechowywania Exchange, zobacz Co zawiera [przechowywanie i usuwanie](retention-policies-exchange.md#whats-included-for-retention-and-deletion).

Lokalizacja **Exchange folderów** publicznych powoduje zastosowanie ustawień przechowywania do wszystkich folderów publicznych i nie można jej stosować na poziomie folderu lub skrzynki pocztowej.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Wyjątki dotyczące zasad automatycznego stosowania skonfigurowanych dla typów informacji poufnych

Po skonfigurowaniu zasad automatycznego stosowania, które mają typy informacji poufnych, i wybierz lokalizację Exchange **e-mail**:

- Microsoft 365 skrzynek pocztowych grupy.

- Wszystkie skrzynki pocztowe są uwzględniane automatycznie, nawet jeśli konfigurowane są adaptacyjne zakresy w celu identyfikowania konkretnych skrzynek pocztowych. Jeśli został wybrany statyczny zakres zasad, nie będzie można określić adresatów, których chcesz uwzględnić lub wykluczyć.

### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a>Informacje o konfiguracji witryn SharePoint i kont OneDrive sieci Web

Po wybraniu lokalizacji witryn **SharePoint** zasady przechowywania mogą zachowywać i usuwać dokumenty w witrynach do komunikacji usługi SharePoint, witrynach zespołu, które nie są połączone przez grupy usługi Microsoft 365 i witryny klasyczne. Jeśli nie korzystasz z adaptacyjnych zakresów [zasad, witryny](#exceptions-for-adaptive-policy-scopes) zespołu połączone za pomocą grup usługi Microsoft 365 nie są obsługiwane w przypadku tej opcji i zamiast tego używaj lokalizacji grup usługi **Microsoft 365**, która dotyczy zawartości w skrzynce pocztowej, witrynie i plikach grupy.

Aby uzyskać szczegółowe informacje o tym, co jest uwzględniane i wykluczane podczas konfigurowania ustawień przechowywania dla aplikacji SharePoint i OneDrive, zobacz Co zawiera przechowywanie i [usuwanie](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion).

Po określeniu lokalizacji dla witryn SharePoint lub kont OneDrive nie są potrzebne uprawnienia dostępu do witryn. W przypadku zakresów statycznych sprawdzanie poprawności nie jest wykonywane podczas określania adresu URL na **stronie Edytowanie** lokalizacji. Jednak określone SharePoint są sprawdzane, czy istnieją na ostatniej stronie konfiguracji. Jeśli to sprawdzanie zakończy się niepowodzeniem, zostanie wyświetlony komunikat informujący o tym, że sprawdzanie poprawności wprowadzonego adresu URL nie powiodło się i nie można utworzyć zasad przechowywania, dopóki sprawdzanie poprawności nie przejdzie. Jeśli zostanie wyświetlony ten komunikat, wróć do procesu konfiguracji, aby zmienić adres URL lub usunąć witrynę z zasad przechowywania.

Aby określić poszczególne OneDrive, zobacz Uzyskiwanie listy wszystkich adresów [URL OneDrive UŻYTKOWNIKÓW w organizacji](/onedrive/list-onedrive-urls).

> [!NOTE]
> Podczas określania poszczególnych kont OneDrive należy pamiętać, że jeśli nie utworzono wstępnie obsługi administracyjnej kont usługi [OneDrive, adres](/onedrive/pre-provision-accounts) URL nie zostanie utworzony, dopóki użytkownik nie OneDrive dostępu do swojego konta po raz pierwszy.
>
> Ponadto adres URL OneDrive zostanie [automatycznie](/onedrive/upn-changes) zmienić w przypadku zmiany głównej nazwy użytkownika. Może to być na przykład zdarzenie, w przypadku które ma zostać zmienione nazwy, takie jak chłonienie, lub zmiana nazwy domeny w celu obsługi zmiany nazwy organizacji lub  wywłasniania nazwy firmy. Jeśli zmieni się upn, należy zaktualizować adresy URL usługi OneDrive określone dla ustawień przechowywania.
>
> Ze względu na wyzwania związane z niezawodnym określaniem adresów URL dla poszczególnych użytkowników, które powinny być dołączane lub wykluczane w zakresach statycznych[, adaptacyjne](retention.md#adaptive-or-static-policy-scopes-for-retention) zakresy z typem zakresu Użytkownik lepiej nadają się do tego celu.

#### <a name="exceptions-for-adaptive-policy-scopes"></a>Wyjątki dla adaptacyjnych zakresów zasad

Po skonfigurowaniu zasad przechowywania, które mają zakresy adaptacyjnych zasad, i wybierz lokalizację **SharePoint witryn:**

- OneDrive i witryny Microsoft 365 połączone z grupą są uwzględniane nie tylko w witrynach komunikacji SharePoint, witrynach  zespołu, które nie są połączone przez grupy Microsoft 365 i witryny klasyczne.

### <a name="configuration-information-for-microsoft-365-groups"></a>Informacje o konfiguracji dla Microsoft 365 grupy

Aby zachować lub usunąć zawartość grupy Microsoft 365 grupy (dawniej Office 365), użyj lokalizacji grupy Microsoft 365 **grupy**. W przypadku zasad przechowywania ta lokalizacja obejmuje skrzynkę pocztową grupy i SharePoint zespołów. W przypadku etykiet przechowywania ta lokalizacja obejmuje tylko SharePoint zespołu.

> [!NOTE]
> Mimo że grupa Microsoft 365 ma skrzynkę pocztową usługi Exchange, zasady przechowywania dla lokalizacji poczty e Exchange-mail nie będą uwzględniać zawartości w skrzynkach pocztowych Microsoft 365 grupy.

W przypadku użycia zakresów statycznych: Chociaż lokalizacja poczty **e-mail** w zakresie statycznym Exchange początkowo pozwala określić skrzynkę pocztową grupy, która ma być uwzględniana lub wykluczona, podczas próby zapisania zasad przechowywania będzie wyświetlany komunikat o błędzie, że wartość "RemoteGroupMailbox" nie jest prawidłową wartością dla lokalizacji usługi Exchange.

Domyślnie zasady przechowywania stosowane do grupy Microsoft 365 obejmują skrzynkę pocztową grupy i witrynę SharePoint zespołów. Pliki przechowywane w witrynie SharePoint zespołu są objęte tą lokalizacją, ale nie Teams czatów ani wiadomości Teams kanałów, które mają własne lokalizacje zasad przechowywania.

Aby zmienić domyślne ustawienie, ponieważ zasady przechowywania mają być stosowane tylko do skrzynek pocztowych programu Microsoft 365 lub tylko połączonych witryn zespołów programu SharePoint, użyj polecenia cmdlet [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell z parametrem *Applications* (Aplikacje) z jedną z następujących wartości:

- `Group:Exchange`tylko Microsoft 365, które są połączone z grupą.
- `Group:SharePoint`tylko SharePoint witryn połączonych z grupą.

Aby przywrócić domyślną wartość zarówno skrzynki pocztowej, jak i witryny SharePoint dla wybranych grup Microsoft 365, określ .`Group:Exchange,SharePoint`

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Wyjątki dotyczące zasad automatycznego stosowania skonfigurowanych dla typów informacji poufnych

Po skonfigurowaniu zasad automatycznego stosowania, które mają typy informacji poufnych, i wybierz lokalizację grupy **Microsoft 365 grupy:**

- Microsoft 365 skrzynek pocztowych grupy nie są uwzględniane. Aby uwzględnić te skrzynki pocztowe w zasadach, wybierz zamiast tego **Exchange poczty e-mail**.

#### <a name="what-happens-if-a-microsoft-365-group-is-deleted-after-a-policy-is-applied"></a>Co się stanie, Microsoft 365 grupa zostanie usunięta po zastosowaniu zasad

Gdy zasady przechowywania (statyczny zakres zasad lub adaptacyjne) są stosowane do grupy zasad Microsoft 365, a następnie ta grupa jest usuwana z Azure Active Directory:

- Witryna grupy połączonej SharePoint jest zachowywana i nadal jest zarządzana przez zasady przechowywania z Microsoft 365 **grupy**. Witryna będzie nadal dostępna dla osób, które miały do niego dostęp przed usunięciem grupy, a wszelkie nowe uprawnienia muszą być teraz zarządzane za pośrednictwem SharePoint.
    
    W tym momencie nie można wykluczyć witryny z Microsoft 365 Grupy, ponieważ usuniętej grupy nie można określić. Jeśli chcesz zwolnić zasady przechowywania z tej witryny, skontaktuj się z pomocą techniczną firmy Microsoft. Na przykład otwórz żądanie [usługi w Centrum Administracja Microsoft 365 sieci.](https://admin.microsoft.com/Adminportal/Home#/support)

- Skrzynka pocztowa usuniętej grupy staje się nieaktywna i podobnie SharePoint, podlega ustawień przechowywania. Aby uzyskać więcej informacji, zobacz [Nieaktywne skrzynki pocztowe w Exchange Online](inactive-mailboxes-in-office-365.md).

### <a name="configuration-information-for-skype-for-business"></a>Informacje o konfiguracji dla Skype dla firm

> [!NOTE]
> Skype dla firm [wycofano 31 lipca 2021](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/skype-for-business-online-to-be-retired-in-2021/ba-p/777833) r. i zachęcamy klientów do migracji do Microsoft Teams. Jednak zasady przechowywania dla Skype dla firm będą nadal obsługiwane dla istniejących klientów.

W przeciwieństwie do poczty e-mail usługi Exchange, nie można włączyć stanu lokalizacji usługi Skype, aby automatycznie uwzględniać wszystkich użytkowników, ale po włączeniu tej lokalizacji musisz ręcznie wybrać użytkowników, których konwersacje chcesz zachować:

![Wybierz Skype lokalizacji zasad przechowywania.](../media/skype-location-retention-policies.png)

Po wybraniu tej **opcji edytuj** w okienku **Skype dla firm możesz szybko** dołączyć wszystkich użytkowników, zaznaczając ukryte pole przed **kolumną** Nazwa. Należy jednak pamiętać, że każdy użytkownik jest liczony jako określone uwzględnienie w zasadach. Jeśli więc uwzględnisz 1000 użytkowników, zaznaczenie tego pola będzie takie samo, jak w przypadku ręcznego wybrania 1000 użytkowników, co jest maksymalnym obsługiwanym poziomem Skype dla firm.

Historia **konwersacji**, folder w folderze Outlook, to funkcja, która nie ma nic wspólnego z Skype archiwizacją. **Historię konwersacji** może wyłączyć użytkownik końcowy, ale archiwizowanie w programie Skype odbywa się przez przechowywanie kopii konwersacji programu Skype w ukrytym folderze, który jest niedostępny dla użytkownika, ale dostępny na potrzeby zbierania elektronicznych materiałów dowodowych.

## <a name="settings-for-retaining-and-deleting-content"></a>Ustawienia zachowywania i usuwania zawartości

Po wybraniu ustawień zachowywania i usuwania zawartości zasady przechowywania będą mieć jedną z następujących konfiguracji przez określony czas:

- Tylko do zachowania

    W przypadku tej konfiguracji wybierz pozycję **Zachowaj elementy przez określony okres** i Na koniec okresu **przechowywania: Nie robisz nic**. Możesz też wybrać pozycję **Zachowaj elementy na zawsze**.

- Zachowywanie, a następnie usuwanie

    W tej konfiguracji wybierz pozycję **Zachowaj elementy przez określony okres** i Na koniec okresu **przechowywania: Automatyczne usuwanie elementów**.

- Delete-only

    W tej konfiguracji wybierz pozycję **Usuń elementy tylko wtedy, gdy osiągną określony wiek**.

### <a name="retaining-content-for-a-specific-period-of-time"></a>Zachowywanie zawartości przez określony czas

Konfigurując etykietę przechowywania lub zasady przechowywania zawartości, możesz określić, czy elementy mają być zachowywane przez określoną liczbę dni, miesięcy lub lat. Ewentualnie zachowaj te elementy na zawsze. Okres przechowywania nie jest obliczany na podstawie czasu przydzielenia zasad, ale zgodnie z okresem rozpoczęcia okresu przechowywania.

Po rozpoczęciu okresu przechowywania można określić, kiedy utworzono zawartość lub kiedy ostatnia modyfikacja zawartości była obsługiwana tylko w przypadku plików oraz grup SharePoint, OneDrive i Microsoft 365. W przypadku etykiet przechowywania można rozpocząć okres przechowywania od zawartości, która została oznaczona etykietą, oraz kiedy nastąpi zdarzenie.

Przykłady:

- SharePoint: Jeśli chcesz zachować elementy w zbiorze witryn przez siedem lat od ostatniej modyfikacji tej zawartości, a dokument w tym zbiorze witryn nie został zmodyfikowany przez sześć lat, dokument zostanie zachowany tylko przez kolejny rok, jeśli nie zostanie zmodyfikowany. Jeśli dokument będzie edytowany ponownie, wiek dokumentu jest obliczany na podstawie nowej daty ostatniej modyfikacji i będzie zachowywany przez kolejne siedem lat.

- Exchange: Jeśli chcesz zachować elementy w skrzynce pocztowej przez siedem lat, a wiadomość została wysłana sześć lat temu, wiadomość zostanie zachowana tylko przez jeden rok. W Exchange wiadomości e-mail wiek jest oparty na dacie odebranej dla przychodzącej wiadomości e-mail lub na dacie wysłania wychodzącej wiadomości e-mail. Zachowywanie elementów na podstawie daty ostatniej modyfikacji dotyczy tylko zawartości witryny w witrynach OneDrive i SharePoint.

Po zakończeniu okresu przechowywania możesz określić, czy zawartość ma zostać trwale usunięta:

![Stronie Ustawień przechowywania.](../media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)

Zanim skonfigurujesz przechowywanie, najpierw zapoznaj się z limitami pojemności i przestrzeni dyskowej dla odpowiednich obciążeń:

- Na SharePoint i OneDrive przechowywane elementy są przechowywane w bibliotece zachowywania witryny, która jest uwzględniana w przydomowym magazynie witryny. Aby uzyskać więcej informacji, zobacz [Zarządzanie limitami miejsca w witrynie](/sharepoint/manage-site-collection-storage-limits) z SharePoint przechowywania.

- Aby Exchange, Teams i Yammer, gdzie przechowywane wiadomości są przechowywane w skrzynkach pocztowych, zobacz limity Exchange Online i włącz automatyczne rozszerzanie [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) [archiwizacji](autoexpanding-archiving.md).
    
    W skrajnych przypadkach, gdy w krótkim czasie duża liczba wiadomości e-mail jest usuwana przez użytkowników albo automatycznie z ustawień zasad, konieczne może być również skonfigurowanie w programie Exchange częściej przenoszenia elementów z folderu Elementy do odzyskania w podstawowej skrzynce pocztowej użytkownika do folderu Elementy do odzyskania w jego archiwaowej skrzynce pocztowej. Aby uzyskać instrukcje krok po kroku, zobacz Zwiększanie przydziału elementów odzyskiwalnych dla skrzynek pocztowych w [hold](increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="deleting-content-thats-older-than-a-specific-age"></a>Usuwanie zawartości starszej niż określony wiek

Zasady przechowywania mogą zachowywać, a następnie usuwać elementy lub usuwać stare elementy bez ich zachowywania.

W obu przypadkach, jeśli zasady usuwają elementy, należy pamiętać, że podany okres nie jest obliczany na podstawie czasu przydzielenia zasad, ale zgodnie z rozpoczęciem określonego okresu przechowywania. Na przykład od czasu utworzenia, modyfikacji lub etykiety elementu.

Dlatego najpierw weź pod uwagę wiek istniejącej zawartości i wpływ zasad na tę zawartość. Możesz także przed przydzieleniem użytkowników przekazać użytkownikom nowe zasady w celu przydzielenia im czasu na ocenę możliwego wpływu.

### <a name="a-policy-that-applies-to-entire-locations"></a>Zasady dotyczące całych lokalizacji

Po wybraniu lokalizacji, z wyjątkiem Skype dla firm, ustawieniem domyślnym jest Wszystkie, gdy stan lokalizacji jest  **Wł**.

Jeśli zasady przechowywania mają zastosowanie do dowolnej kombinacji całych lokalizacji, nie ma ograniczenia liczby adresatów, witryn, kont, grup itp., które mogą obejmować zasady.

Jeśli na przykład zasady obejmują wszystkie wiadomości Exchange e-mail i wszystkie witryny SharePoint, zostaną uwzględnione wszystkie witryny i adresaci, niezależnie od ich liczby. Z drugiej Exchange nowa skrzynka pocztowa utworzona po zastosowaniu zasad automatycznie odziedziczy zasady.

### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Zasady z określonymi dołączeniami lub wykluczeniami

Jeśli korzystasz z opcjonalnej konfiguracji w celu ograniczenia ustawień przechowywania do konkretnych użytkowników, konkretnych grup Microsoft 365 lub konkretnych witryn, istnieją pewne ograniczenia dotyczące zasad, o których należy pamiętać. Aby uzyskać więcej informacji, [zobacz Limity dotyczące zasad przechowywania i zasad etykiet przechowywania](retention-limits.md). 

Aby użyć opcjonalnej konfiguracji w celu ustawienia zakresu ustawień przechowywania, upewnij się, że stan tej lokalizacji jest Wł **., a** następnie użyj linków, aby uwzględnić lub wykluczyć określonych użytkowników, Microsoft 365 grupy lub witryny.

> [!WARNING]
> Jeśli skonfigurujesz uwzględnia, a następnie usuniesz ostatni, dla lokalizacji zostanie przywrócona konfiguracja **Wszystkie** .  Przed zapisaniem zasad upewnij się, że jest to konfiguracja, która ma być przez Ciebie zamierzana.
>
> Jeśli na przykład określisz jedną witrynę programu SharePoint, która ma zostać dołączona do zasad przechowywania skonfigurowanych do usuwania danych, SharePoint następnie usuniesz pojedynczą witrynę, domyślnie wszystkie witryny programu SharePoint będą podlegały zasadom przechowywania, które trwale usuwają dane. To samo dotyczy także adresatów Exchange, OneDrive, użytkowników Teams czatów itp.
>
> W tym scenariuszu wyłącz lokalizację, jeśli nie chcesz, aby ustawienie Wszystkie dla  lokalizacji podlegało zasadom przechowywania. Ewentualnie określ wykluczenia z zasad.

## <a name="updating-policies-for-retention"></a>Aktualizowanie zasad przechowywania

Po utworzeniu i zapisaniu zasad przechowywania nie można zmieniać niektórych ustawień, takich jak:
- Nazwa zasad i ustawienia przechowywania z wyjątkiem okresu przechowywania i czasu rozpoczęcia okresu przechowywania.

Jeśli edytujesz zasady przechowywania, a elementy będą już podlegać pierwotnym ustawień w twoich zasadach przechowywania, zaktualizowane ustawienia zostaną automatycznie zastosowane do tych elementów oprócz elementów, które zostały nowo zidentyfikowane.

Zazwyczaj ta aktualizacja jest dość szybka, ale może potrwać kilka dni. Po zakończeniu replikacji zasad Microsoft 365 lokalizacji przechowywania stan zasad przechowywania zostanie wyświetlony w Centrum zgodności platformy Microsoft 365 z **Wł. (** oczekiwanie) na Wł **. (Powodzenie)** .

## <a name="locking-the-policy-to-prevent-changes"></a>Blokowanie zasad w celu uniemożliwinia zmian

Jeśli chcesz się upewnić, że nikt nie będzie miał możliwości wyłączenia zasad, usunięcia zasad lub ich mniej restrykcyjnych, zobacz Używanie blokady zachowywania do ograniczania zmian zasad przechowywania i zasad etykiet [przechowywania](retention-preservation-lock.md).
