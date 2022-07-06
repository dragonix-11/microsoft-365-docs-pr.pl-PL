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
ms.openlocfilehash: 0f0fa2da9c41700216b0142827897980870f006d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627674"
---
# <a name="create-and-configure-retention-policies"></a>Tworzenie i konfigurowanie zasad przechowywania

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Użyj zasad przechowywania, aby zarządzać danymi organizacji, aktywnie podejmując decyzję, czy zachować zawartość, usunąć zawartość, czy zachować, a następnie usunąć zawartość.

Zasady przechowywania pozwalają to zrobić bardzo wydajnie, przypisując te same ustawienia przechowywania na poziomie kontenera, które mają być automatycznie dziedziczone przez zawartość w tym kontenerze. Na przykład wszystkie elementy w witrynach programu SharePoint, wszystkie wiadomości e-mail w skrzynkach pocztowych programu Exchange użytkowników, wszystkie wiadomości kanałowe dla zespołów, które są używane w usłudze Microsoft Teams. Jeśli nie masz pewności, czy używać zasad przechowywania na poziomie kontenera, czy etykiety przechowywania na poziomie elementu, zobacz [Zasady przechowywania i etykiety przechowywania](retention.md#retention-policies-and-retention-labels).

Aby uzyskać więcej informacji na temat zasad przechowywania i sposobu działania przechowywania w usłudze Microsoft 365, zobacz [Informacje o zasadach przechowywania i etykietach przechowywania](retention.md).

> [!NOTE]
> Informacje na tej stronie są przeznaczone dla administratorów zgodności. Jeśli nie jesteś administratorem i chcesz zrozumieć, w jaki sposób zasady przechowywania zostały skonfigurowane dla używanych aplikacji, skontaktuj się z pomocą techniczną, działem IT lub administratorem. Jeśli widzisz komunikaty dotyczące zasad przechowywania w czatach i komunikatach kanałów w usłudze Teams, warto przejrzeć [komunikaty usługi Teams dotyczące zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny organizacji ma pełne uprawnienia do tworzenia i edytowania zasad przechowywania. Jeśli nie logujesz się jako administrator globalny, zapoznaj się z [informacjami o uprawnieniach do zarządzania cyklem życia danych](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels).

Przed utworzeniem zasad przechowywania zdecyduj, czy będą **to zasady adaptacyjne** , czy **statyczne**. Aby uzyskać więcej informacji, zobacz [Adaptacyjne lub statyczne zakresy zasad przechowywania](retention.md#adaptive-or-static-policy-scopes-for-retention). Jeśli zdecydujesz się na korzystanie z zasad adaptacyjnych, musisz utworzyć co najmniej jeden zakres adaptacyjny przed utworzeniem zasad przechowywania, a następnie wybrać je podczas procesu tworzenia zasad przechowywania. Aby uzyskać instrukcje, zobacz [Informacje o konfiguracji dla zakresów adaptacyjnych](retention-settings.md#configuration-information-for-adaptive-scopes).

## <a name="create-and-configure-a-retention-policy"></a>Tworzenie i konfigurowanie zasad przechowywania

Mimo że zasady przechowywania mogą obsługiwać wiele usług, które są identyfikowane jako "lokalizacje" w zasadach przechowywania, nie można utworzyć jednej zasady przechowywania, która zawiera wszystkie obsługiwane lokalizacje:

- Poczta e-mail programu Exchange
- Witryna programu SharePoint
- Konta usługi OneDrive
- Grupy platformy Microsoft 365
- Skype dla firm
- Foldery publiczne programu Exchange
- Komunikaty kanału usługi Teams
- Czaty w usłudze Teams
- Komunikaty kanału prywatnego usługi Teams
- Komunikaty społeczności usługi Yammer
- Komunikaty użytkowników usługi Yammer

Jeśli podczas tworzenia zasad przechowywania wybierzesz lokalizacje usługi Teams lub Yammer, pozostałe lokalizacje zostaną automatycznie wykluczone. Oznacza to, że instrukcje, które należy wykonać, zależą od tego, czy należy uwzględnić lokalizacje usługi Teams, czy Yammer:

- [Instrukcje dotyczące zasad przechowywania dla lokalizacji usługi Teams](#retention-policy-for-teams-locations)
- [Instrukcje dotyczące zasad przechowywania dla lokalizacji usługi Yammer](#retention-policy-for-yammer-locations)
- [Instrukcje dotyczące zasad przechowywania dla lokalizacji innych niż Teams i Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

> [!NOTE]
> W przypadku korzystania z zasad adaptacyjnych zamiast zasad statycznych można skonfigurować pojedyncze zasady przechowywania w taki sposób, aby uwzględniały lokalizacje usługi Teams i Yammer. Nie dotyczy to zasad statycznych, w których lokalizacje usługi Teams i Yammer wymagają własnych zasad przechowywania.

Jeśli masz więcej niż jedną zasadę przechowywania, a także używasz etykiet przechowywania, zobacz [Zasady przechowywania lub co ma pierwszeństwo?](retention.md#the-principles-of-retention-or-what-takes-precedence) aby zrozumieć wynik, gdy wiele ustawień przechowywania ma zastosowanie do tej samej zawartości.

### <a name="retention-policy-for-teams-locations"></a>Zasady przechowywania lokalizacji usługi Teams

> [!NOTE]
> Zasady przechowywania obsługują teraz [kanały udostępnione](/MicrosoftTeams/shared-channels) w wersji zapoznawczej. Po skonfigurowaniu ustawień przechowywania dla lokalizacji **komunikatów kanału usługi Teams** , jeśli zespół ma jakiekolwiek kanały udostępnione, dziedziczy ustawienia przechowywania po swoim zespole nadrzędnym.

1. Z [portal zgodności Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **Zasady przechowywania** **zarządzania cyklem** >  życia danych.

2. Wybierz pozycję **Nowe zasady przechowywania** , aby rozpocząć **konfigurowanie zasad przechowywania** i nadać nazwę nowym zasadom przechowywania.

3. Na stronie **Wybierz typ zasad przechowywania do utworzenia** wybierz pozycję **Adaptacyjne** lub **Statyczne**, w zależności od wyboru dokonanego z instrukcji [Przed rozpoczęciem](#before-you-begin) . Jeśli nie utworzono jeszcze zakresów adaptacyjnych, możesz wybrać opcję **Adaptacyjne** , ale ponieważ nie będzie żadnych zakresów adaptacyjnych do wybrania, nie będzie można ukończyć konfiguracji przy użyciu tej opcji.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano pozycję **Adaptacyjne**: na stronie **Wybieranie zakresów i lokalizacji zasad adaptacyjnych** wybierz pozycję **Dodaj zakresy** i wybierz co najmniej jeden utworzony zakres adaptacyjny. Następnie wybierz co najmniej jedną lokalizację. Lokalizacje, które można wybrać, zależą od [dodanych typów zakresów](retention-settings.md#configuration-information-for-adaptive-scopes) . Jeśli na przykład dodano tylko typ zakresu **Użytkownika**, będzie można wybrać opcję **Czaty w usłudze Teams** , ale nie **komunikaty kanału usługi Teams**. 
    
    - Jeśli **wybrano pozycję Statyczne**: na stronie **Wybieranie lokalizacji do zastosowania zasad** wybierz co najmniej jedną lokalizację dla usługi Teams:
        - **Komunikat kanału usługi Teams**: komunikaty ze standardowych i udostępnionych czatów kanałów oraz standardowe i udostępnione spotkania kanałów, ale nie z [kanałów prywatnych](/microsoftteams/private-channels) , które mają własną lokalizację zasad.
        - **Czaty w usłudze Teams**: wiadomości z prywatnych czatów 1:1, czatów grupowych i czatów na spotkaniach.
        - **Komunikaty kanału prywatnego usługi Teams**: wiadomości z czatów kanału prywatnego i spotkań kanału prywatnego.
        
       Domyślnie [wybierane są wszystkie zespoły i wszyscy użytkownicy](retention-settings.md#a-policy-that-applies-to-entire-locations), ale możesz to uściślić, wybierając [opcje **Wybierz** i **Wyklucz**](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).

5. W polu **Zdecyduj, czy chcesz zachować zawartość, usuń ją lub obie** strony, określ opcje konfiguracji przechowywania i usuwania zawartości.

   Możesz utworzyć zasady przechowywania, które po prostu zachowują zawartość bez usuwania, zachowywania, a następnie usuwania po określonym czasie lub po prostu usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, zobacz [Ustawienia dotyczące przechowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Zakończ konfigurację i zapisz ustawienia.

Aby uzyskać wskazówki dotyczące korzystania z zasad przechowywania w usłudze Teams i poznania środowiska użytkownika końcowego, zobacz [Zarządzanie zasadami przechowywania w usłudze Microsoft Teams](/microsoftteams/retention-policies) w dokumentacji usługi Teams.

Aby uzyskać szczegółowe informacje techniczne dotyczące sposobu działania przechowywania w usłudze Teams, w tym elementów komunikatów obsługiwanych na potrzeby przechowywania i informacji o chronometrażu z przykładowymi przewodnikami, zobacz [Learn about retention for Microsoft Teams (Informacje na temat przechowywania w usłudze Microsoft Teams](retention-policies-teams.md)).

#### <a name="known-configuration-issues"></a>Znane problemy z konfiguracją

- Mimo że można wybrać opcję rozpoczęcia okresu przechowywania, gdy elementy zostały ostatnio zmodyfikowane, zawsze jest używana wartość **Kiedy elementy zostały utworzone** . W przypadku edytowanych komunikatów kopia oryginalnej wiadomości jest zapisywana z oryginalną sygnaturą czasową w celu określenia, kiedy został utworzony wstępnie edytowany komunikat, a wiadomość po edycji ma nowszą sygnaturę czasową.

- Po wybraniu pozycji **Edytuj** dla lokalizacji czatów w usłudze Teams mogą być widoczni goście i użytkownicy bez skrzynki pocztowej. Zasady przechowywania nie są przeznaczone dla tych użytkowników, więc nie wybieraj ich.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Dodatkowe zasady przechowywania potrzebne do obsługi usługi Teams

Teams to coś więcej niż tylko czaty i wiadomości kanałów. Jeśli masz zespoły utworzone na podstawie grupy platformy Microsoft 365 (wcześniej Office 365), należy dodatkowo skonfigurować zasady przechowywania, które obejmują tę grupę platformy Microsoft 365 przy użyciu lokalizacji **Grupy Microsoft 365**. Te zasady przechowywania mają zastosowanie do zawartości w skrzynce pocztowej, witrynie i plikach grupy.

Jeśli masz witryny zespołu, które nie są połączone z grupą platformy Microsoft 365, potrzebne są zasady przechowywania zawierające **witryny programu SharePoint** lub lokalizacje **kont usługi OneDrive** do przechowywania i usuwania plików w usłudze Teams:

- Pliki udostępnione na czacie są przechowywane na koncie usługi OneDrive użytkownika, który udostępnił plik.

- Pliki przekazywane do kanałów są przechowywane w witrynie programu SharePoint dla zespołu.

> [!TIP]
> Zasady przechowywania można zastosować do plików tylko określonego zespołu, gdy nie jest on połączony z grupą platformy Microsoft 365, wybierając witrynę programu SharePoint dla zespołu oraz konta użytkowników usługi OneDrive w zespole.

Istnieje możliwość, że zasady przechowywania stosowane do grup platformy Microsoft 365, witryn programu SharePoint lub kont usługi OneDrive mogą usunąć plik, do którego odwołuje się czat lub komunikat kanału usługi Teams, zanim te wiadomości zostaną usunięte. W tym scenariuszu plik nadal jest wyświetlany w komunikacie usługi Teams, ale po wybraniu pliku przez użytkowników występuje błąd "Nie znaleziono pliku". To zachowanie nie jest specyficzne dla zasad przechowywania i może również wystąpić, jeśli użytkownik ręcznie usunie plik z programu SharePoint lub OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Zasady przechowywania lokalizacji usługi Yammer

> [!NOTE]
> Zasady przechowywania usługi Yammer obecnie nie informują użytkowników o usunięciu komunikatów w wyniku zasad przechowywania.
>
> Aby korzystać z tej funkcji, sieć usługi Yammer musi być [trybem natywnym](/yammer/configure-your-yammer-network/overview-native-mode), a nie trybem hybrydowym.

1. Z [portal zgodności Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **Zasady przechowywania** **zarządzania cyklem** >  życia danych.

2. Wybierz pozycję **Nowe zasady przechowywania** , aby utworzyć nowe zasady przechowywania.

3. Na stronie **Wybierz typ zasad przechowywania do utworzenia** wybierz pozycję **Adaptacyjne** lub **Statyczne**, w zależności od wyboru dokonanego z instrukcji [Przed rozpoczęciem](#before-you-begin) . Jeśli nie utworzono jeszcze zakresów adaptacyjnych, możesz wybrać opcję **Adaptacyjne** , ale ponieważ nie będzie żadnych zakresów adaptacyjnych do wybrania, nie będzie można ukończyć konfiguracji przy użyciu tej opcji.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano pozycję **Adaptacyjne**: na stronie **Wybieranie zakresów i lokalizacji zasad adaptacyjnych** wybierz pozycję **Dodaj zakresy** i wybierz co najmniej jeden utworzony zakres adaptacyjny. Następnie wybierz co najmniej jedną lokalizację. Lokalizacje, które można wybrać, zależą od [dodanych typów zakresów](retention-settings.md#configuration-information-for-adaptive-scopes) . Jeśli na przykład dodano tylko typ zakresu **Użytkownika**, będzie można wybrać **komunikaty użytkowników usługi Yammer** , ale nie **komunikaty społeczności usługi Yammer**. 
    
    - Jeśli **wybrano pozycję Statyczne**: na stronie **Wybieranie lokalizacji do zastosowania zasad** przełącz jedną lub obie lokalizacje dla usługi **Yammer: komunikat społeczności usługi Yammer** i **komunikaty użytkowników usługi Yammer**.
        
        Domyślnie wybierane są wszystkie społeczności i użytkownicy, ale można to uściślić, określając społeczności i użytkowników, które mają zostać uwzględnione lub wykluczone.
        
        W przypadku komunikatów użytkownika usługi Yammer: 
        - Jeśli pozostawisz wartość domyślną **Dla wszystkich użytkowników**, użytkownicy-goście usługi Azure B2B nie zostaną uwzględnieni. 
        - Jeśli **wybierzesz pozycję Edytuj** dla **wszystkich użytkowników**, możesz zastosować zasady przechowywania do użytkowników zewnętrznych, jeśli znasz ich konto.

5. W polu **Zdecyduj, czy chcesz zachować zawartość, usuń ją lub obie** strony, określ opcje konfiguracji przechowywania i usuwania zawartości. 
    
    Możesz utworzyć zasady przechowywania, które po prostu zachowują zawartość bez usuwania, zachowywania, a następnie usuwania po określonym czasie lub po prostu usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, zobacz [Ustawienia dotyczące przechowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Zakończ konfigurację i zapisz ustawienia.

Aby uzyskać więcej informacji na temat sposobu działania zasad przechowywania dla usługi Yammer, zobacz [Dowiedz się więcej na temat przechowywania usługi Yammer](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Dodatkowe zasady przechowywania potrzebne do obsługi usługi Yammer

Usługa Yammer to coś więcej niż tylko wiadomości społeczności i wiadomości prywatne. Aby zachować i usunąć wiadomości e-mail dla sieci usługi Yammer, skonfiguruj dodatkowe zasady przechowywania zawierające wszystkie grupy platformy Microsoft 365 używane w usłudze Yammer przy użyciu lokalizacji **Grupy Microsoft 365**.

Ta lokalizacja będzie również zawierać pliki przekazywane do społeczności usługi Yammer. Te pliki są przechowywane w witrynie programu SharePoint połączonej z grupą dla społeczności usługi Yammer.

Istnieje możliwość, że zasady przechowywania stosowane do witryn programu SharePoint mogą usunąć plik, do którego odwołuje się komunikat usługi Yammer, zanim te komunikaty zostaną usunięte. W tym scenariuszu plik nadal jest wyświetlany w komunikacie usługi Yammer, ale po wybraniu pliku przez użytkowników występuje błąd "Nie znaleziono pliku". To zachowanie nie jest specyficzne dla zasad przechowywania i może również wystąpić, jeśli użytkownik ręcznie usunie plik z programu SharePoint.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Zasady przechowywania dla lokalizacji innych niż Teams i Yammer

Użyj następujących instrukcji dotyczących zasad przechowywania, które mają zastosowanie do dowolnej z tych usług:

- Exchange: Wiadomości e-mail i foldery publiczne
- SharePoint: witryny
- OneDrive: konta
- Grupy platformy Microsoft 365
- Skype dla firm

1. Z [portal zgodności Microsoft Purview](https://compliance.microsoft.com/) wybierz pozycję **Zasady przechowywania** **zarządzania cyklem** >  życia danych.

2. Wybierz pozycję **Nowe zasady przechowywania** , aby rozpocząć **konfigurowanie zasad przechowywania** i nadać nazwę nowym zasadom przechowywania.

3. Na stronie **Wybierz typ zasad przechowywania do utworzenia** wybierz pozycję **Adaptacyjne** lub **Statyczne**, w zależności od wyboru dokonanego z instrukcji [Przed rozpoczęciem](#before-you-begin) . Jeśli nie utworzono jeszcze zakresów adaptacyjnych, możesz wybrać opcję **Adaptacyjne** , ale ponieważ nie będzie żadnych zakresów adaptacyjnych do wybrania, nie będzie można ukończyć konfiguracji przy użyciu tej opcji. Zasady adaptacyjne nie obsługują lokalizacji dla folderów publicznych programu Exchange ani Skype dla firm.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano pozycję **Adaptacyjne**: na stronie **Wybieranie zakresów i lokalizacji zasad adaptacyjnych** wybierz pozycję **Dodaj zakresy** i wybierz co najmniej jeden utworzony zakres adaptacyjny. Następnie wybierz co najmniej jedną lokalizację. Lokalizacje, które można wybrać, zależą od [dodanych typów zakresów](retention-settings.md#configuration-information-for-adaptive-scopes) . Jeśli na przykład dodano tylko typ zakresu **Użytkownika**, będzie można wybrać pozycję **Poczta e-mail programu Exchange** , ale nie **witryny programu SharePoint**. 
    
    - Jeśli wybierzesz pozycję **Statyczne**: na stronie **Wybieranie lokalizacji** włącz lub wyłącz dowolną lokalizację z wyjątkiem lokalizacji dla aplikacji Teams i Yammer. Dla każdej lokalizacji można pozostawić ją domyślnie, aby [zastosować zasady do całej lokalizacji](retention-settings.md#a-policy-that-applies-to-entire-locations) lub [określić opcje dołączania i wykluczania](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).
    
    Informacje specyficzne dla lokalizacji:
    - [Wiadomości e-mail programu Exchange i foldery publiczne programu Exchange](retention-settings.md#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [Witryny programu SharePoint i konta usługi OneDrive](retention-settings.md#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Grupy Microsoft 365](retention-settings.md#configuration-information-for-microsoft-365-groups)
    - [Skype dla firm](retention-settings.md#configuration-information-for-skype-for-business)

5. W polu **Zdecyduj, czy chcesz zachować zawartość, usuń ją lub obie** strony, określ opcje konfiguracji przechowywania i usuwania zawartości.
    
    Możesz utworzyć zasady przechowywania, które po prostu zachowują zawartość bez usuwania, zachowywania, a następnie usuwania po określonym czasie lub po prostu usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, zobacz [Ustawienia przechowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content) na tej stronie.

6. Zakończ konfigurację i zapisz ustawienia.

## <a name="how-long-it-takes-for-retention-policies-to-take-effect"></a>Jak długo trwa obowiązywanie zasad przechowywania

Po utworzeniu i przesłaniu zasad przechowywania zastosowanie zasad przechowywania może potrwać do siedmiu dni:
  
![Diagram przedstawiający, kiedy zasady przechowywania wchodzą w życie.](../media/retention-policy-timings.png)

Najpierw zasady przechowywania muszą być dystrybuowane do wybranych lokalizacji, a następnie stosowane do zawartości. Zawsze możesz sprawdzić stan dystrybucji zasad przechowywania, wybierając ją na stronie **Zasady przechowywania** w portal zgodności Microsoft Purview. Jeśli w okienku wysuwanym zostanie wyświetlony komunikat **(Błąd)** uwzględniony w stanie, a w szczegółach lokalizacji zostanie wyświetlony komunikat, że wdrażanie zasad trwa dłużej niż oczekiwano lub spróbuj ponownie wdrożyć zasady, spróbuj uruchomić polecenie [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/set-appretentioncompliancepolicy) lub [Set-RetentionCompliancePolicy,](/powershell/module/exchange/set-retentioncompliancepolicy) aby ponowić próbę dystrybucji zasad:

1. [Połącz się z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom jedno z następujących poleceń:
    
    - W przypadku lokalizacji zasad **komunikaty kanału prywatnego usługi Teams**, **komunikaty użytkowników usługi Yammer** i **komunikaty społeczności usługi Yammer**:
    
        ```PowerShell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
    
    - Dla wszystkich innych lokalizacji zasad, takich jak **wiadomości e-mail programu Exchange**, **witryny programu SharePoint** i **wiadomości kanału usługi Teams**:
    
        ```PowerShell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

## <a name="updating-retention-policies"></a>Aktualizowanie zasad przechowywania

Gdy ustawienia zasad przechowywania są już stosowane do zawartości, zmiana konfiguracji zasad zostanie automatycznie zastosowana do tej zawartości oprócz nowo zidentyfikowanej zawartości.

Niektórych ustawień nie można zmienić po utworzeniu i zapisaniu zasad, które obejmują nazwę zasad przechowywania, typ zakresu (adaptacyjny lub statyczny) oraz ustawienia przechowywania z wyjątkiem okresu przechowywania.

## <a name="next-steps"></a>Następne kroki

Jeśli niektóre elementy programu Exchange, SharePoint, OneDrive lub Grupy Microsoft 365 wymagają innych ustawień przechowywania niż skonfigurowane ustawienia zasad przechowywania, [utwórz etykiety przechowywania dla tych wyjątków](create-retention-labels-data-lifecycle-management.md).

Jeśli jednak chcesz zarządzać elementami o wysokiej wartości dla wymagań dotyczących przechowywania rekordów biznesowych, prawnych lub regulacyjnych, [użyj planu plików, aby utworzyć etykiety przechowywania i zarządzać nimi](file-plan-manager.md).
