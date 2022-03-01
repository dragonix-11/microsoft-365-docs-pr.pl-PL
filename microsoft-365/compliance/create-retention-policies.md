---
title: Tworzenie i konfigurowanie zasad przechowywania w celu automatycznego zachowywania lub usuwania zawartości
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
description: Zasady przechowywania skutecznie kontrolują zawartość generną przez użytkowników za pomocą wiadomości e-mail, dokumentów i konwersacji. Zachowaj to, co chcesz, i pozbądź się tego, czego nie chcesz.
ms.openlocfilehash: 115dcce1e99583ab0c3345da683be0b826b24ff7
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027139"
---
# <a name="create-and-configure-retention-policies"></a>Tworzenie i konfigurowanie zasad przechowywania

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Przy użyciu zasad przechowywania możesz zarządzać danymi w organizacji, aktywnie podejmując decyzję o zachowaniu zawartości, usunięciu jej lub zachowaniu, a następnie jej usunięciu.

Zasady przechowywania pozwalają zrobić to bardzo wydajnie, przypisując te same ustawienia przechowywania na poziomie kontenera, które będą automatycznie dziedziczone przez zawartość w tym kontenerze. Na przykład wszystkie elementy w witrynach SharePoint, wszystkie wiadomości e-mail w skrzynkach pocztowych Exchange użytkowników, wszystkie wiadomości kanałów dla zespołów używanych z usługą Microsoft Teams. Jeśli nie masz pewności, czy użyć zasad przechowywania na poziomie kontenera, czy etykiety przechowywania na poziomie elementów, zobacz Zasady przechowywania [i etykiety przechowywania](retention.md#retention-policies-and-retention-labels).

Aby uzyskać więcej informacji na temat zasad przechowywania i sposobu działania Microsoft 365 przechowywania, zobacz Informacje [o zasadach przechowywania i etykietach przechowywania](retention.md).

> [!NOTE]
> Informacje na tej stronie są dla administratorów zgodności. Jeśli nie jesteś administratorem i chcesz dowiedzieć się, jak skonfigurowano zasady przechowywania dla aplikacji, z których korzystasz, skontaktuj się z działem pomocy technicznej, działem IT lub z administratorem. Jeśli widzisz wiadomości dotyczące zasad przechowywania w czatach Teams i wiadomościach kanałów, pomocne może okazać się przejrzenie wiadomości Teams [dotyczących zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny organizacji ma pełne uprawnienia do tworzenia i edytowania zasad przechowywania. Jeśli nie logujesz się jako administrator globalny, zobacz informacje o uprawnieniach do [zarządzania informacjami](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels).

Przed utworzeniem zasad przechowywania zdecyduj, czy będą one **adaptacyjne** , czy **statyczne**. Aby uzyskać więcej informacji, zobacz [Adaptacyjne lub statyczne zakresy zasad przechowywania](retention.md#adaptive-or-static-policy-scopes-for-retention). Jeśli zdecydujesz się używać adaptacyjnych zasad, musisz utworzyć co najmniej jeden adaptacyjny zakres przed utworzeniem zasad przechowywania, a następnie wybrać je podczas tworzenia zasad przechowywania. Aby uzyskać instrukcje, [zobacz Informacje o konfiguracji dotyczące adaptacyjnych zakresów](retention-settings.md#configuration-information-for-adaptive-scopes).

## <a name="create-and-configure-a-retention-policy"></a>Tworzenie i konfigurowanie zasad przechowywania

Mimo że zasady przechowywania mogą obsługiwać wiele usług, które są określone jako "lokalizacje" w zasadach przechowywania, nie można utworzyć jednej zasady przechowywania, która będzie zawierała wszystkie obsługiwane lokalizacje:

- Exchange-mail
- SharePoint witryny
- OneDrive konta
- Microsoft 365 grupy
- Skype dla firm
- Exchange folderów publicznych
- Teams wiadomości na kanale
- Teams czatów
- Teams wiadomości z kanału prywatnego
- Yammer wiadomości od społeczności
- Yammer wiadomości od użytkowników

Jeśli podczas tworzenia zasad przechowywania Teams lub Yammer wybierzesz lokalizacje przechowywania, pozostałe lokalizacje zostaną automatycznie wykluczone. Oznacza to, że instrukcje, które należy wykonać, zależą od tego, czy musisz uwzględnić Teams czy Yammer lokalizacji:

- [Instrukcje dotyczące zasad przechowywania Teams lokalizacji](#retention-policy-for-teams-locations)
- [Instrukcje dotyczące zasad przechowywania Yammer lokalizacji](#retention-policy-for-yammer-locations)
- [Instrukcje dotyczące zasad przechowywania dla lokalizacji innych niż Teams i Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

> [!NOTE]
> Gdy używasz adaptacyjnych zasad zamiast zasad statycznych, możesz skonfigurować pojedyncze zasady przechowywania tak, aby uwzględniały zarówno Teams, jak i Yammer lokalizacje. Nie jest tak w przypadku statycznych zasad, w których Teams i Yammer wymagają własnych zasad przechowywania.

Jeśli masz więcej niż jedno zasady przechowywania, a także używasz etykiet przechowywania, zobacz Zasady przechowywania lub co ma pierwszeństwo [?,](retention.md#the-principles-of-retention-or-what-takes-precedence) aby zrozumieć wynik, gdy wiele ustawień przechowywania jest dotyczących tej samej zawartości.

### <a name="retention-policy-for-teams-locations"></a>Zasady przechowywania dla Teams lokalizacji

1. Na stronie [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/) pozycję **Zasady zarządzania informacjami** > **.**

2. Wybierz **pozycję Nowe zasady przechowywania** , aby uruchomić **konfigurację Tworzenie zasad przechowywania** i nazwać nowe zasady przechowywania.

3. W przypadku **strony Wybierz typ zasad przechowywania** do utworzenia wybierz pozycję **Adaptacyjny** lub Statyczny **, w** zależności od wyboru dokonanego w [instrukcjach Przed rozpoczęciem](#before-you-begin) . Jeśli nie masz jeszcze utworzonych zakresów adaptacyjnych, możesz wybrać pozycję  Adaptacyjny, ale ponieważ nie będzie żadnych adaptacyjnych zakresów do wyboru, nie możesz ukończyć konfiguracji za pomocą tej opcji.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano **adaptacyjny**: Na  stronie Wybieranie zakresów i lokalizacji adaptacyjnych zasad wybierz pozycję  Dodaj zakresy i wybierz co najmniej jeden z utworzonych adaptacyjnych zakresów. Następnie wybierz jedną lub więcej lokalizacji. Lokalizacje, które można wybrać, zależą od [dodanych typów](retention-settings.md#configuration-information-for-adaptive-scopes) zakresów. Jeśli na przykład dodano tylko typ zakresu **użytkownika, będzie** można wybrać czaty Teams, ale nie  Teams **wiadomości w kanałach**. 
    
    - Jeśli wybrano **pozycję Statyczny**: Na **stronie Wybierz** lokalizacje do zastosowania zasad wybierz jedną lub więcej lokalizacji dla Teams:
        - **Teams wiadomości na kanale**: Wiadomości ze standardowych czatów kanałów i standardowych spotkań w kanale, ale nie z [](/microsoftteams/private-channels) kanałów prywatnych, które mają własną lokalizację zasad.
        - **Teams czatów**: Wiadomości z prywatnych czatów prywatnych (1:1), czatów grupowych i czatów na spotkaniach.
        - **Teams wiadomości z kanału prywatnego**: Wiadomości z czatów w kanale prywatnym i spotkań w kanale prywatnym.
        
       Domyślnie są [zaznaczone wszystkie zespoły i wszyscy](retention-settings.md#a-policy-that-applies-to-entire-locations) użytkownicy, ale można to uściślić, wybierając [**opcje** Wybierz i **Wyklucz**](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).

5. W **przypadku opcji Zdecyduj, czy** chcesz zachować zawartość, usunąć ją, czy obie strony, określ opcje konfiguracji zachowywania i usuwania zawartości.

   Można utworzyć zasady przechowywania, które tylko zachowują zawartość bez usuwania, zachowują i usuwają po upływie określonego czasu lub tylko usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, [Ustawienia dotyczące zachowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Ukończ konfigurację i zapisz ustawienia.

Aby uzyskać wskazówki dotyczące korzystania z zasad przechowywania w Teams i zrozumienia środowiska użytkownika końcowego, zobacz Zarządzanie zasadami przechowywania dla użytkowników [Microsoft Teams z Teams](/microsoftteams/retention-policies) dokumentacji.

Aby uzyskać szczegółowe informacje techniczne dotyczące sposobu przechowywania w aplikacji Teams, w tym informacje dotyczące przechowywania i chronometrażu wiadomości, w tym informacje dotyczące przechowywania i chronometrażu, zobacz Informacje na temat przechowywania w celu przechowywania [Microsoft Teams.](retention-policies-teams.md)

#### <a name="known-configuration-issues"></a>Znane problemy z konfiguracją

- Mimo że możesz wybrać opcję, aby rozpocząć okres przechowywania po ostatniej modyfikacji elementów, wartość Gdy elementy **zostały** utworzone jest zawsze używana. W przypadku edytowanych wiadomości jest zapisywana kopia oryginalnej wiadomości z oryginalną sygnaturą czasową, która pozwala określić, kiedy utworzono tę wstępnie edytowaną wiadomość, a wiadomość po edycji ma nowszą sygnaturę czasową.

- Po wybraniu pozycji **Edytuj** dla lokalizacji **Teams wiadomości** w kanale mogą być Microsoft 365 grupy, które nie są również zespołami. Nie zaznaczaj tych grup.

- Po wybraniu pozycji **Edytuj** dla lokalizacji Teams czatów mogą być widziani goście i użytkownicy spoza skrzynki pocztowej. Zasady przechowywania nie są przeznaczone dla tych użytkowników, więc ich nie wybieraj.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Dodatkowe zasady przechowywania wymagane do obsługi Teams

Teams to nie tylko czaty i wiadomości na kanałach. Jeśli masz zespoły utworzone w grupie programu Microsoft 365 (dawniej Office 365), musisz dodatkowo skonfigurować zasady przechowywania, które obejmują grupę Microsoft 365 przy użyciu lokalizacji grupy usługi Microsoft 365. Te zasady przechowywania mają zastosowanie do zawartości w skrzynce pocztowej, witrynie i plikach grupy.

Jeśli masz witryny zespołu, które nie są połączone z grupą programu Microsoft 365, potrzebujesz zasad przechowywania, które obejmują witryny SharePoint lub lokalizacje  kont programu **OneDrive**, aby przechowywać i usuwać pliki w Teams:

- Pliki udostępniane na czacie są przechowywane OneDrive konta użytkownika, który udostępnił plik.

- Pliki przekazane do kanałów są przechowywane w SharePoint zespołu.

> [!TIP]
> Zasady przechowywania można stosować do plików konkretnego zespołu, gdy nie jest on połączony z grupą programu Microsoft 365, wybierając witrynę SharePoint zespołu i konta OneDrive użytkowników w zespole.

Zasady przechowywania stosowane do grup usługi Microsoft 365, witryn usługi SharePoint lub kont programu OneDrive mogą usunąć plik, do których odwołuje się wiadomość na czacie lub w kanale programu Teams, zanim te wiadomości zostaną usunięte. W tym scenariuszu plik będzie nadal wyświetlany w komunikacie Teams pliku, ale po wybraniu pliku jest wyświetlany błąd "Nie można odnaleźć pliku". To zachowanie nie jest specyficzne dla zasad przechowywania i może się również zdarzyć, jeśli użytkownik ręcznie usunie plik z SharePoint lub OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Zasady przechowywania Yammer lokalizacji

> [!NOTE]
> Zasady przechowywania Yammer są w wersji Preview i obecnie nie informują użytkowników o usunięciu wiadomości w wyniku zasad przechowywania.
>
> Aby można było korzystać z tej funkcji, Yammer musi być [trybem natywnym](/yammer/configure-your-yammer-network/overview-native-mode), a nie trybem hybrydowym.

1. Na stronie [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/) pozycję **Zasady zarządzania informacjami** > **.**

2. Wybierz **pozycję Nowe zasady przechowywania** , aby utworzyć nowe zasady przechowywania.

3. W przypadku **strony Wybierz typ zasad przechowywania** do utworzenia wybierz pozycję **Adaptacyjny** lub Statyczny **, w** zależności od wyboru dokonanego w [instrukcjach Przed rozpoczęciem](#before-you-begin) . Jeśli nie masz jeszcze utworzonych zakresów adaptacyjnych, możesz wybrać pozycję  Adaptacyjny, ale ponieważ nie będzie żadnych adaptacyjnych zakresów do wyboru, nie możesz ukończyć konfiguracji za pomocą tej opcji.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano **adaptacyjny**: Na  stronie Wybieranie zakresów i lokalizacji adaptacyjnych zasad wybierz pozycję  Dodaj zakresy i wybierz co najmniej jeden z utworzonych adaptacyjnych zakresów. Następnie wybierz jedną lub więcej lokalizacji. Lokalizacje, które można wybrać, zależą od [dodanych typów](retention-settings.md#configuration-information-for-adaptive-scopes) zakresów. Jeśli na przykład dodano tylko typ zakresu **użytkownika, można** wybrać wiadomości Yammer, ale nie Yammer **wiadomości społeczności**. 
    
    - Jeśli wybrano pozycję **Statyczny**:  Na stronie Wybierz lokalizacje do zastosowania zasad włącz jedną lub obie lokalizacje dla ustawienia Yammer: **Yammer** i wiadomości Yammer **użytkowników**.
        
        > [!IMPORTANT]
        > Mimo że możesz utworzyć zasady przechowywania tylko dla Yammer wiadomości od użytkowników, zasady przechowywania dla tej lokalizacji mogą usuwać wiadomości społeczności z aplikacji Yammer dla wszystkich członków społeczności.
        > 
        > Jeśli wybierzesz tę opcję, a zasady przechowywania zostaną skonfigurowane do usuwania wiadomości od użytkowników, upewnij się, że rozumiesz ten wpływ. Aby uzyskać więcej informacji, zobacz [Jak działa przechowywanie w Yammer](retention-policies-yammer.md#how-retention-works-with-yammer).
        
        Domyślnie są zaznaczone wszystkie społeczności i użytkownicy, ale można to uściślić, określając społeczności i użytkowników do uwzględniania lub wykluczania.
        
        Aby Yammer wiadomości od użytkowników: 
        - Jeśli pozostawisz wartość domyślną **Wszyscy użytkownicy**, nie są uwzględniani użytkownicy goście usługi Azure B2B. 
        - Jeśli wybierzesz **pozycję Edytuj** dla **wszystkich użytkowników**, możesz zastosować zasady przechowywania do użytkowników zewnętrznych, jeśli znasz ich konta.

5. W **przypadku opcji Zdecyduj, czy** chcesz zachować zawartość, usunąć ją, czy obie strony, określ opcje konfiguracji zachowywania i usuwania zawartości. 
    
    Można utworzyć zasady przechowywania, które tylko zachowują zawartość bez usuwania, zachowują i usuwają po upływie określonego czasu lub tylko usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, [Ustawienia dotyczące zachowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Ukończ konfigurację i zapisz ustawienia.

Aby uzyskać więcej informacji o tym, jak działają zasady przechowywania Yammer, zobacz [Informacje na](retention-policies-yammer.md) temat przechowywania w Yammer.

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Dodatkowe zasady przechowywania potrzebne do obsługi Yammer

Yammer to nie tylko wiadomości od społeczności i wiadomości prywatnych. Aby zachowywać i usuwać wiadomości e-mail w sieci Yammer, skonfiguruj dodatkowe zasady przechowywania, które będą zawierały wszystkie grupy Microsoft 365 używane dla sieci Yammer, używając lokalizacji grupy usługi Microsoft 365. 

Aby zachować i usunąć pliki przechowywane w Yammer, potrzebne są zasady przechowywania, które obejmują lokalizację grupy Microsoft 365 lub lokalizacje kont OneDrive konta: 

- Pliki udostępniane w wiadomościach prywatnych są przechowywane OneDrive konta użytkownika, który udostępnił plik. 

- Pliki przekazane do społeczności są przechowywane w połączonej z SharePoint sieci Web społeczności użytkowników Yammer grupy.

Zasady przechowywania stosowane do witryn programu SharePoint lub kont programu OneDrive mogą przed usunięciem tych wiadomości usunąć plik, do których odwołuje się wiadomość Yammer. W tym scenariuszu plik nadal jest wyświetlany w komunikacie Yammer pliku, ale po wybraniu pliku jest wyświetlany błąd "Nie można odnaleźć pliku". To zachowanie nie jest specyficzne dla zasad przechowywania i może się również zdarzyć, jeśli użytkownik ręcznie usunie plik z SharePoint lub OneDrive.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Zasady przechowywania dla lokalizacji innych niż Teams i Yammer

Skorzystaj z następujących instrukcji dotyczących zasad przechowywania, które mają zastosowanie do dowolnej z tych usług:

- Exchange: Poczta e-mail i foldery publiczne
- SharePoint: Witryny
- OneDrive: Konta
- Microsoft 365 grupy
- Skype dla firm

1. Na stronie [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/) pozycję **Zasady zarządzania informacjami** > **.**

2. Wybierz **pozycję Nowe zasady przechowywania** , aby uruchomić **konfigurację Tworzenie zasad przechowywania** i nazwać nowe zasady przechowywania.

3. W przypadku **strony Wybierz typ zasad przechowywania** do utworzenia wybierz pozycję **Adaptacyjny** lub Statyczny **, w** zależności od wyboru dokonanego w [instrukcjach Przed rozpoczęciem](#before-you-begin) . Jeśli nie masz jeszcze utworzonych zakresów adaptacyjnych, możesz wybrać pozycję  Adaptacyjny, ale ponieważ nie będzie żadnych adaptacyjnych zakresów do wyboru, nie możesz ukończyć konfiguracji za pomocą tej opcji. Zasady adaptacyjne nie obsługują lokalizacji folderów Exchange lub folderów Skype dla firm.

4. W zależności od wybranego zakresu:
    
    - Jeśli wybrano **adaptacyjny**: Na  stronie Wybieranie zakresów i lokalizacji adaptacyjnych zasad wybierz pozycję  Dodaj zakresy i wybierz co najmniej jeden z utworzonych adaptacyjnych zakresów. Następnie wybierz jedną lub więcej lokalizacji. Lokalizacje, które można wybrać, zależą od [dodanych typów](retention-settings.md#configuration-information-for-adaptive-scopes) zakresów. Jeśli na przykład dodano tylko typ zakresu **użytkownika, będzie** można wybrać adres e-mail Exchange ale  nie SharePoint **witryn.** 
    
    - Jeśli wybrano pozycję **Statyczny**:  Na stronie Wybieranie lokalizacji włącz lub wyłącz dowolną lokalizację z wyjątkiem lokalizacji dla lokalizacji Teams i Yammer. Dla każdej lokalizacji możesz pozostawić ją domyślną, aby zastosować zasady do całej [lokalizacji, lub](retention-settings.md#a-policy-that-applies-to-entire-locations) określić [uwzględniania i wykluczania](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).
    
    Informacje specyficzne dla lokalizacji:
    - [Exchange e-mail i Exchange foldery publiczne](retention-settings.md#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [SharePoint witryny i konta OneDrive](retention-settings.md#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Microsoft 365 grupy](retention-settings.md#configuration-information-for-microsoft-365-groups)
    - [Skype dla firm](retention-settings.md#configuration-information-for-skype-for-business)

5. W **przypadku opcji Zdecyduj, czy** chcesz zachować zawartość, usunąć ją, czy obie strony, określ opcje konfiguracji zachowywania i usuwania zawartości.
    
    Można utworzyć zasady przechowywania, które tylko zachowują zawartość bez usuwania, zachowują i usuwają po upływie określonego czasu lub tylko usuwają zawartość po określonym czasie. Aby uzyskać więcej informacji, [Ustawienia na temat zachowywania i usuwania zawartości](retention-settings.md#settings-for-retaining-and-deleting-content) na tej stronie.

6. Ukończ konfigurację i zapisz ustawienia.

## <a name="how-long-it-takes-for-retention-policies-to-take-effect"></a>Jak długo trwa okres, w jakim mają obowiązywać zasady przechowywania

Gdy tworzysz i przesyłasz zasady przechowywania, zastosowanie tych zasad może potrwać do siedmiu dni:
  
![Diagram przedstawiający okres, w którym zasady przechowywania są skuteczne.](../media/retention-policy-timings.png)

Najpierw zasady przechowywania muszą zostać rozpowszechnione do wybranych lokalizacji, a następnie zastosowane do zawartości. Zawsze możesz sprawdzić stan dystrybucji zasad przechowywania, wybierając je na stronie Zasady **przechowywania** w Centrum zgodności. W wysuwanej okienku, jeśli zobaczysz stan Wyłączone **(błąd)** i w szczegółach lokalizacji zostanie wyświetlony komunikat informujący, że wdrożenie zasad (w przypadku programu SharePoint) lub podjęcie próby ponownego wdrożenia zasad (dla programu OneDrive) trwa dłużej, niż oczekiwano, spróbuj ponownie uruchomić polecenie [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell, aby ponownie sprawdzić rozkład zasad:

1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom następujące polecenie:
    
    ```PowerShell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

## <a name="updating-retention-policies"></a>Aktualizowanie zasad przechowywania

Gdy ustawienia zasad przechowywania zostaną już zastosowane do zawartości, zmiana konfiguracji zasad zostanie automatycznie zastosowana do tej zawartości oprócz nowo zidentyfikowanej zawartości.

Po utworzeniu i zapisaniu zasad nie można zmieniać niektórych ustawień, takich jak nazwa zasad przechowywania, typ zakresu (adaptacyjny lub statyczny) i ustawienia przechowywania z wyjątkiem okresu przechowywania.

## <a name="next-steps"></a>Następne kroki

Jeśli niektóre elementy dla grup usługi Exchange, SharePoint, OneDrive lub Microsoft 365 wymagają innych ustawień przechowywania niż skonfigurowane ustawienia zasad przechowywania, utwórz etykiety przechowywania dla tych [wyjątków](create-retention-labels-information-governance.md).

Jeśli jednak szukasz zarządzania cyklem życia dokumentów o wysokiej wartości w przypadku wymogów przechowywania dokumentacji biznesowej, prawnych lub prawnych, użyj planu ewidencji, aby utworzyć etykiety przechowywania i zarządzać [nimi](file-plan-manager.md).
