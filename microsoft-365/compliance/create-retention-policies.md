---
title: Automatyczne zachowywanie lub usuwanie zawartości przy użyciu zasad przechowywania
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
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Użyj zasad przechowywania, aby efektywnie kontrolować zawartość generowaną przez użytkowników za pomocą poczty e-mail, dokumentów i konwersacji. Zachowaj to, czego chcesz, i pozbądź się tego, czego nie chcesz.
ms.openlocfilehash: 22373fddf6a4ccac718f9fede9d1bbc40b92681d
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "65145322"
---
# <a name="create-and-configure-retention-policies"></a>Tworzenie i konfigurowanie zasad przechowywania

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Użyj zasad przechowywania, aby zarządzać danymi organizacji, aktywnie podejmując decyzję, czy zachować zawartość, usunąć zawartość, czy zachować, a następnie usunąć zawartość.

Zasady przechowywania pozwalają to zrobić bardzo wydajnie, przypisując te same ustawienia przechowywania na poziomie kontenera, które mają być automatycznie dziedziczone przez zawartość w tym kontenerze. Na przykład wszystkie elementy w witrynach SharePoint, wszystkie wiadomości e-mail w skrzynkach pocztowych Exchange użytkowników, wszystkie wiadomości kanałowe dla zespołów, które są używane z Microsoft Teams. Jeśli nie masz pewności, czy używać zasad przechowywania na poziomie kontenera, czy etykiety przechowywania na poziomie elementu, zobacz [Zasady przechowywania i etykiety przechowywania](retention.md#retention-policies-and-retention-labels).

Aby uzyskać więcej informacji na temat zasad przechowywania i sposobu przechowywania w Microsoft 365, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).

> [!NOTE]
> Informacje na tej stronie są przeznaczone dla administratorów zgodności. Jeśli nie jesteś administratorem i chcesz zrozumieć, w jaki sposób zasady przechowywania zostały skonfigurowane dla używanych aplikacji, skontaktuj się z pomocą techniczną, działem IT lub administratorem. Jeśli widzisz komunikaty dotyczące zasad przechowywania w Teams czatach i komunikatach kanałów, warto przejrzeć [Teams komunikatów dotyczących zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny organizacji ma pełne uprawnienia do tworzenia i edytowania zasad przechowywania. Jeśli nie logujesz się jako administrator globalny, zapoznaj się z [informacjami o uprawnieniach do zarządzania cyklem życia danych](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels).

Przed utworzeniem zasad przechowywania zdecyduj, czy będą **to zasady adaptacyjne** , czy **statyczne**. Aby uzyskać więcej informacji, zobacz [Adaptacyjne lub statyczne zakresy zasad przechowywania](retention.md#adaptive-or-static-policy-scopes-for-retention). Jeśli zdecydujesz się na korzystanie z zasad adaptacyjnych, musisz utworzyć co najmniej jeden zakres adaptacyjny przed utworzeniem zasad przechowywania, a następnie wybrać je podczas procesu tworzenia zasad przechowywania. Aby uzyskać instrukcje, zobacz [Informacje o konfiguracji dla zakresów adaptacyjnych](retention-settings.md#configuration-information-for-adaptive-scopes).

## <a name="create-and-configure-a-retention-policy"></a>Tworzenie i konfigurowanie zasad przechowywania

Mimo że zasady przechowywania mogą obsługiwać wiele usług, które są identyfikowane jako "lokalizacje" w zasadach przechowywania, nie można utworzyć jednej zasady przechowywania, która zawiera wszystkie obsługiwane lokalizacje:

- Exchange e-mail
- witryna SharePoint
- konta OneDrive
- Grupy platformy Microsoft 365
- Skype dla firm
- Exchange folderów publicznych
- komunikaty kanału Teams
- Teams czaty
- Teams wiadomości z kanału prywatnego
- Yammer komunikaty społeczności
- Yammer komunikaty użytkowników

Jeśli podczas tworzenia zasad przechowywania wybierzesz lokalizacje Teams lub Yammer, inne lokalizacje zostaną automatycznie wykluczone. Oznacza to, że instrukcje do wykonania zależą od tego, czy należy uwzględnić lokalizacje Teams, czy Yammer:

- [Instrukcje dotyczące zasad przechowywania dla lokalizacji Teams](#retention-policy-for-teams-locations)
- [Instrukcje dotyczące zasad przechowywania dla lokalizacji Yammer](#retention-policy-for-yammer-locations)
- [Instrukcje dotyczące zasad przechowywania dla lokalizacji innych niż Teams i Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

> [!NOTE]
> W przypadku korzystania z zasad adaptacyjnych zamiast zasad statycznych można skonfigurować pojedyncze zasady przechowywania, aby uwzględniać zarówno lokalizacje Teams, jak i Yammer. Nie dotyczy to zasad statycznych, w których lokalizacje Teams i Yammer wymagają własnych zasad przechowywania.

Jeśli masz więcej niż jedną zasadę przechowywania, a także używasz etykiet przechowywania, zobacz [Zasady przechowywania lub co ma pierwszeństwo?](retention.md#the-principles-of-retention-or-what-takes-precedence) aby zrozumieć wynik, gdy wiele ustawień przechowywania ma zastosowanie do tej samej zawartości.

### <a name="retention-policy-for-teams-locations"></a>Zasady przechowywania dla lokalizacji Teams

> [!NOTE]
> Zasady przechowywania obsługują teraz [kanały udostępnione](/MicrosoftTeams/shared-channels) w wersji zapoznawczej. Po skonfigurowaniu ustawień przechowywania dla lokalizacji **komunikatów kanału Teams**, jeśli zespół ma jakiekolwiek kanały udostępnione, dziedziczy ustawienia przechowywania po swoim zespole nadrzędnym.

1. W [portalu zgodności usługi Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **Zarządzanie cyklem** >  życia **danychZasady ponownego wdrażania**.

2. Wybierz pozycję **Nowe zasady przechowywania** , aby rozpocząć **konfigurowanie zasad przechowywania** i nadać nazwę nowym zasadom przechowywania.

3. Na stronie **Wybierz typ zasad przechowywania do utworzenia** wybierz pozycję **Adaptacyjne** lub **Statyczne**, w zależności od wyboru dokonanego z instrukcji [Przed rozpoczęciem](#before-you-begin) . Jeśli nie utworzono jeszcze zakresów adaptacyjnych, możesz wybrać opcję **Adaptacyjne** , ale ponieważ nie będzie żadnych zakresów adaptacyjnych do wybrania, nie będzie można ukończyć konfiguracji przy użyciu tej opcji.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano pozycję **Adaptacyjne**: na stronie **Wybieranie zakresów i lokalizacji zasad adaptacyjnych** wybierz pozycję **Dodaj zakresy** i wybierz co najmniej jeden utworzony zakres adaptacyjny. Następnie wybierz co najmniej jedną lokalizację. Lokalizacje, które można wybrać, zależą od [dodanych typów zakresów](retention-settings.md#configuration-information-for-adaptive-scopes) . Jeśli na przykład dodano tylko typ zakresu **Użytkownika**, będzie można wybrać **Teams czatów**, ale nie **Teams komunikatów kanału**. 
    
    - Jeśli **wybrano pozycję Statyczne**: na stronie **Wybieranie lokalizacji do zastosowania zasad** wybierz co najmniej jedną lokalizację dla Teams:
        - **Teams komunikat kanału**: wiadomości ze standardowych i udostępnionych czatów kanałów oraz standardowe i udostępnione spotkania kanałów, ale nie z [kanałów prywatnych](/microsoftteams/private-channels), które mają własną lokalizację zasad.
        - **Teams czaty**: wiadomości z prywatnych czatów 1:1, czatów grupowych i czatów na spotkaniach.
        - **Teams wiadomości kanału prywatnego**: wiadomości z czatów kanału prywatnego i spotkań kanału prywatnego.
        
       Domyślnie [wybierane są wszystkie zespoły i wszyscy użytkownicy](retention-settings.md#a-policy-that-applies-to-entire-locations), ale możesz to uściślić, wybierając [opcje **Wybierz** i **Wyklucz**](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).

5. W polu **Zdecyduj, czy chcesz zachować zawartość, usuń ją lub obie** strony, określ opcje konfiguracji przechowywania i usuwania zawartości.

   Możesz utworzyć zasady przechowywania, które po prostu zachowują zawartość bez usuwania, zachowywania, a następnie usuwania po określonym czasie lub po prostu usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, zobacz [Ustawienia do przechowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Zakończ konfigurację i zapisz ustawienia.

Aby uzyskać wskazówki dotyczące używania zasad przechowywania dla Teams i poznania środowiska użytkownika końcowego, zobacz [Zarządzanie zasadami przechowywania dla Microsoft Teams](/microsoftteams/retention-policies) z dokumentacji Teams.

Aby uzyskać szczegółowe informacje techniczne dotyczące sposobu działania przechowywania dla Teams, w tym jakie elementy komunikatów są obsługiwane na potrzeby przechowywania i informacji o chronometrażu z przykładowymi przewodnikami, zobacz [Dowiedz się więcej na temat przechowywania Microsoft Teams](retention-policies-teams.md).

#### <a name="known-configuration-issues"></a>Znane problemy z konfiguracją

- Mimo że można wybrać opcję rozpoczęcia okresu przechowywania, gdy elementy zostały ostatnio zmodyfikowane, zawsze jest używana wartość **Kiedy elementy zostały utworzone** . W przypadku edytowanych komunikatów kopia oryginalnej wiadomości jest zapisywana z oryginalną sygnaturą czasową w celu określenia, kiedy został utworzony wstępnie edytowany komunikat, a wiadomość po edycji ma nowszą sygnaturę czasową.

- Po wybraniu pozycji **Edytuj** dla lokalizacji czatów Teams mogą być widoczni goście i użytkownicy bez skrzynki pocztowej. Zasady przechowywania nie są przeznaczone dla tych użytkowników, więc nie wybieraj ich.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Dodatkowe zasady przechowywania potrzebne do obsługi Teams

Teams to coś więcej niż tylko czaty i wiadomości kanałowe. Jeśli masz zespoły utworzone na podstawie grupy Microsoft 365 (dawniej Office 365), należy dodatkowo skonfigurować zasady przechowywania, które obejmują tę grupę Microsoft 365 przy użyciu lokalizacji **Grupy Microsoft 365**. Te zasady przechowywania mają zastosowanie do zawartości w skrzynce pocztowej, witrynie i plikach grupy.

Jeśli masz witryny zespołu, które nie są połączone z grupą Microsoft 365, potrzebne są zasady przechowywania zawierające **lokalizacje SharePoint witryn** lub **kont OneDrive**, aby przechowywać i usuwać pliki w Teams:

- Pliki udostępnione na czacie są przechowywane na koncie OneDrive użytkownika, który udostępnił plik.

- Pliki przekazywane do kanałów są przechowywane w witrynie SharePoint dla zespołu.

> [!TIP]
> Zasady przechowywania można zastosować do plików tylko określonego zespołu, gdy nie jest on połączony z grupą Microsoft 365, wybierając witrynę SharePoint dla zespołu oraz konta OneDrive użytkowników w zespole.

Istnieje możliwość, że zasady przechowywania stosowane do grup Microsoft 365, SharePoint witryn lub kont OneDrive mogą usunąć plik, do którego odwołuje się Teams czat lub komunikat kanału, zanim te wiadomości zostaną usunięte. W tym scenariuszu plik nadal jest wyświetlany w komunikacie Teams, ale po wybraniu pliku przez użytkowników występuje błąd "Nie znaleziono pliku". To zachowanie nie jest specyficzne dla zasad przechowywania i może również wystąpić, jeśli użytkownik ręcznie usunie plik z SharePoint lub OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Zasady przechowywania dla lokalizacji Yammer

> [!NOTE]
> Zasady przechowywania dla Yammer obecnie nie informują użytkowników o usunięciu komunikatów w wyniku zasad przechowywania.
>
> Aby korzystać z tej funkcji, sieć Yammer musi być [trybem natywnym](/yammer/configure-your-yammer-network/overview-native-mode), a nie trybem hybrydowym.

1. W [portalu zgodności usługi Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **Zarządzanie cyklem** >  życia **danychZasady ponownego wdrażania**.

2. Wybierz pozycję **Nowe zasady przechowywania** , aby utworzyć nowe zasady przechowywania.

3. Na stronie **Wybierz typ zasad przechowywania do utworzenia** wybierz pozycję **Adaptacyjne** lub **Statyczne**, w zależności od wyboru dokonanego z instrukcji [Przed rozpoczęciem](#before-you-begin) . Jeśli nie utworzono jeszcze zakresów adaptacyjnych, możesz wybrać opcję **Adaptacyjne** , ale ponieważ nie będzie żadnych zakresów adaptacyjnych do wybrania, nie będzie można ukończyć konfiguracji przy użyciu tej opcji.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano pozycję **Adaptacyjne**: na stronie **Wybieranie zakresów i lokalizacji zasad adaptacyjnych** wybierz pozycję **Dodaj zakresy** i wybierz co najmniej jeden utworzony zakres adaptacyjny. Następnie wybierz co najmniej jedną lokalizację. Lokalizacje, które można wybrać, zależą od [dodanych typów zakresów](retention-settings.md#configuration-information-for-adaptive-scopes) . Jeśli na przykład dodano tylko typ zakresu **Użytkownika**, będzie można wybrać **Yammer komunikatów użytkowników**, ale nie **Yammer komunikatów społeczności**. 
    
    - Jeśli **wybrano pozycję Statyczne**: na stronie **Wybieranie lokalizacji do zastosowania zasad** przełącz jedną lub obie lokalizacje dla Yammer: **Yammer komunikat społeczności** i **Yammer komunikaty użytkowników**.
        
        Domyślnie wybierane są wszystkie społeczności i użytkownicy, ale można to uściślić, określając społeczności i użytkowników, które mają zostać uwzględnione lub wykluczone.
        
        W przypadku Yammer komunikatów użytkowników: 
        - Jeśli pozostawisz wartość domyślną **Dla wszystkich użytkowników**, użytkownicy-goście usługi Azure B2B nie zostaną uwzględnieni. 
        - Jeśli **wybierzesz pozycję Edytuj** dla **wszystkich użytkowników**, możesz zastosować zasady przechowywania do użytkowników zewnętrznych, jeśli znasz ich konto.

5. W polu **Zdecyduj, czy chcesz zachować zawartość, usuń ją lub obie** strony, określ opcje konfiguracji przechowywania i usuwania zawartości. 
    
    Możesz utworzyć zasady przechowywania, które po prostu zachowują zawartość bez usuwania, zachowywania, a następnie usuwania po określonym czasie lub po prostu usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, zobacz [Ustawienia do przechowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Zakończ konfigurację i zapisz ustawienia.

Aby uzyskać więcej informacji na temat sposobu działania zasad przechowywania dla Yammer, zobacz [Informacje na temat przechowywania Yammer](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Dodatkowe zasady przechowywania potrzebne do obsługi Yammer

Yammer to coś więcej niż tylko wiadomości społeczności i wiadomości prywatne. Aby zachować i usunąć wiadomości e-mail dla sieci Yammer, skonfiguruj dodatkowe zasady przechowywania, które obejmują wszystkie grupy Microsoft 365 używane do Yammer przy użyciu lokalizacji **Grupy Microsoft 365**. 

Aby zachować i usunąć pliki przechowywane w Yammer, potrzebne są zasady przechowywania zawierające **lokalizację Grupy Microsoft 365** lub **lokalizacje kont OneDrive**:

- Pliki udostępnione w wiadomościach prywatnych są przechowywane na koncie OneDrive użytkownika, który udostępnił plik. 

- Pliki przekazywane do społeczności są przechowywane w witrynie SharePoint połączonej z grupą dla społeczności Yammer.

Istnieje możliwość, że zasady przechowywania stosowane do SharePoint witryn lub kont OneDrive mogą usunąć plik, do którego odwołuje się komunikat Yammer przed usunięciem tych komunikatów. W tym scenariuszu plik nadal jest wyświetlany w komunikacie Yammer, ale po wybraniu pliku przez użytkowników występuje błąd "Nie znaleziono pliku". To zachowanie nie jest specyficzne dla zasad przechowywania i może również wystąpić, jeśli użytkownik ręcznie usunie plik z SharePoint lub OneDrive.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Zasady przechowywania dla lokalizacji innych niż Teams i Yammer

Użyj następujących instrukcji dotyczących zasad przechowywania, które mają zastosowanie do dowolnej z tych usług:

- Exchange: wiadomości e-mail i foldery publiczne
- SharePoint: witryny
- OneDrive: konta
- Grupy platformy Microsoft 365
- Skype dla firm

1. W [portalu zgodności usługi Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **Zarządzanie cyklem** >  życia **danychZasady ponownego wdrażania**.

2. Wybierz pozycję **Nowe zasady przechowywania** , aby rozpocząć **konfigurowanie zasad przechowywania** i nadać nazwę nowym zasadom przechowywania.

3. Na stronie **Wybierz typ zasad przechowywania do utworzenia** wybierz pozycję **Adaptacyjne** lub **Statyczne**, w zależności od wyboru dokonanego z instrukcji [Przed rozpoczęciem](#before-you-begin) . Jeśli nie utworzono jeszcze zakresów adaptacyjnych, możesz wybrać opcję **Adaptacyjne** , ale ponieważ nie będzie żadnych zakresów adaptacyjnych do wybrania, nie będzie można ukończyć konfiguracji przy użyciu tej opcji. Zasady adaptacyjne nie obsługują lokalizacji Exchange folderów publicznych ani Skype dla firm.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano pozycję **Adaptacyjne**: na stronie **Wybieranie zakresów i lokalizacji zasad adaptacyjnych** wybierz pozycję **Dodaj zakresy** i wybierz co najmniej jeden utworzony zakres adaptacyjny. Następnie wybierz co najmniej jedną lokalizację. Lokalizacje, które można wybrać, zależą od [dodanych typów zakresów](retention-settings.md#configuration-information-for-adaptive-scopes) . Jeśli na przykład dodano tylko typ zakresu **Użytkownika**, będzie można wybrać **Exchange wiadomości e-mail**, ale nie **SharePoint witryn**. 
    
    - Jeśli **wybrano pozycję Statyczne**: na stronie **Wybieranie lokalizacji** włącz lub wyłącz dowolną lokalizację z wyjątkiem lokalizacji dla Teams i Yammer. Dla każdej lokalizacji można pozostawić ją domyślnie, aby [zastosować zasady do całej lokalizacji](retention-settings.md#a-policy-that-applies-to-entire-locations) lub [określić opcje dołączania i wykluczania](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).
    
    Informacje specyficzne dla lokalizacji:
    - [Exchange wiadomości e-mail i Exchange folderów publicznych](retention-settings.md#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [SharePoint witryn i kont OneDrive](retention-settings.md#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Grupy Microsoft 365](retention-settings.md#configuration-information-for-microsoft-365-groups)
    - [Skype dla firm](retention-settings.md#configuration-information-for-skype-for-business)

5. W polu **Zdecyduj, czy chcesz zachować zawartość, usuń ją lub obie** strony, określ opcje konfiguracji przechowywania i usuwania zawartości.
    
    Możesz utworzyć zasady przechowywania, które po prostu zachowują zawartość bez usuwania, zachowywania, a następnie usuwania po określonym czasie lub po prostu usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, zobacz [Ustawienia do przechowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content) na tej stronie.

6. Zakończ konfigurację i zapisz ustawienia.

## <a name="how-long-it-takes-for-retention-policies-to-take-effect"></a>Jak długo trwa obowiązywanie zasad przechowywania

Po utworzeniu i przesłaniu zasad przechowywania zastosowanie zasad przechowywania może potrwać do siedmiu dni:
  
![Diagram przedstawiający, kiedy zasady przechowywania wchodzą w życie.](../media/retention-policy-timings.png)

Najpierw zasady przechowywania muszą być dystrybuowane do wybranych lokalizacji, a następnie stosowane do zawartości. Zawsze możesz sprawdzić stan dystrybucji zasad przechowywania, wybierając je na stronie **Zasady przechowywania** w portalu zgodności usługi Microsoft Purview. Jeśli w okienku wysuwanym zostanie wyświetlony komunikat **(Błąd)** uwzględniony w stanie, a w szczegółach lokalizacji zostanie wyświetlony komunikat, że wdrażanie zasad trwa dłużej niż oczekiwano lub spróbuj ponownie wdrożyć zasady, spróbuj uruchomić polecenie [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/set-appretentioncompliancepolicy) lub [Set-RetentionCompliancePolicy,](/powershell/module/exchange/set-retentioncompliancepolicy) aby ponowić próbę dystrybucji zasad:

1. [Połączenie do programu PowerShell Centrum zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom jedno z następujących poleceń:
    
    - W przypadku lokalizacji zasad **Teams wiadomości kanału prywatnego** **Yammer komunikaty użytkowników** i **Yammer komunikaty społeczności**:
    
        ```PowerShell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
    
    - W przypadku wszystkich innych lokalizacji zasad, takich jak **wiadomości e-mail Exchange**, **witryny SharePoint** i **wiadomości kanału Teams**:
    
        ```PowerShell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

## <a name="updating-retention-policies"></a>Aktualizowanie zasad przechowywania

Gdy ustawienia zasad przechowywania są już stosowane do zawartości, zmiana konfiguracji zasad zostanie automatycznie zastosowana do tej zawartości oprócz nowo zidentyfikowanej zawartości.

Niektórych ustawień nie można zmienić po utworzeniu i zapisaniu zasad, które obejmują nazwę zasad przechowywania, typ zakresu (adaptacyjny lub statyczny) oraz ustawienia przechowywania z wyjątkiem okresu przechowywania.

## <a name="next-steps"></a>Następne kroki

Jeśli niektóre elementy dla Exchange, SharePoint, OneDrive lub Grupy Microsoft 365 wymagają innych ustawień przechowywania niż skonfigurowane ustawienia zasad przechowywania, [utwórz etykiety przechowywania dla tych wyjątków](create-retention-labels-data-lifecycle-management.md).

Jeśli jednak chcesz zarządzać elementami o wysokiej wartości dla wymagań dotyczących przechowywania rekordów biznesowych, prawnych lub regulacyjnych, [użyj planu plików, aby utworzyć etykiety przechowywania i zarządzać nimi](file-plan-manager.md).
