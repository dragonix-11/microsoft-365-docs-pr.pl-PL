---
title: dołączanie pliku
description: dołączanie pliku
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 2d48c4066cc1cde102fc395d7c532d26ea2a4db0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63331547"
---
## <a name="prerequisites"></a>Wymagania wstępne

Zapoznaj się z następującymi sekcjami, aby uzyskać informacje o wymaganiach dotyczących zarządzania zabezpieczeniami dla programu Microsoft Defender for Endpoint Scenario:

### <a name="environment"></a>Środowisko

Gdy urządzenie jest dołączane do programu Microsoft Defender dla punktu końcowego:


- Urządzenie jest ankietowane pod kątem istniejącej obecności Endpoint Manager, czyli rejestracji funkcji zarządzania urządzeniami przenośnymi (MDM) w usłudze Intune
- Urządzenia bez Endpoint Manager obecności włączyć funkcję zarządzania zabezpieczeniami
- Zaufanie jest tworzone za pomocą Azure Active Directory, jeśli jeszcze nie istnieje
- Azure Active Directory zaufania jest używany do komunikowania się z usługą Endpoint Manager (Intune) i pobierania zasad
- Zasady pobierania z Endpoint Manager są wymuszane na urządzeniu przez usługę Microsoft Defender for Endpoint

### <a name="active-directory-requirements"></a>Wymagania usługi Active Directory

Jeśli urządzenie przyłączone do domeny tworzy zaufanie dla Azure Active Directory, ten scenariusz jest określany jako scenariusz dołączania do Azure Active Directory *hybrydowego*. Zarządzanie zabezpieczeniami dla programu Microsoft Defender for Endpoint w pełni obsługuje ten scenariusz z następującymi wymaganiami:

- Azure Active Directory Połączenie (AAD Połączenie) muszą być zsynchronizowane z dzierżawą używaną z usługi Microsoft Defender for Endpoint
- Dołączanie Azure Active Directory hybrydowe musi być skonfigurowane w środowisku (za pośrednictwem federacji lub AAD Połączenie synchronizacji)
- AAD Połączenie synchronizacji musi uwzględniać obiekty urządzeń w zakresie synchronizacji  z programem Azure Active Directory (gdy jest to potrzebne w celu sprzężenia)
- AAD Połączenie synchronizacji muszą zostać zmodyfikowane dla serwera Server 2012 R2 (gdy jest potrzebna obsługa programu Server 2012 R2)
- Wszystkie urządzenia muszą rejestrować się w Azure Active Directory dzierżawy hostowej programu Microsoft Defender for Endpoint. Scenariusze dla różnych dzierżaw nie są obsługiwane. 

### <a name="connectivity-requirements"></a>Wymagania dotyczące połączenia

Urządzenia muszą mieć dostęp do następujących punktów końcowych:

- `enterpriseregistration.windows.net` — W przypadku rejestracji w usłudze Azure AD.
- `login.microsoftonline.com` — W przypadku rejestracji w usłudze Azure AD.
- `*.dm.microsoft.com` — Użycie symbolu wieloznacznego obsługuje punkty końcowe usługi w chmurze, które są używane do rejestrowania, zaewidencjonowania i raportowania, które mogą się zmieniać jako skale usługi.

### <a name="supported-platforms"></a>Obsługiwane platformy

Zasady zarządzania zabezpieczeniami programu Microsoft Defender for Endpoint są obsługiwane dla następujących platform urządzeń:

- Windows 10 Pro/Enterprise (z [kb5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows 11 Pro/Enterprise
- Windows Server 2012 R2 z [programem Microsoft Defender dla Down-Level Urządzenia](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 z [programem Microsoft Defender dla Down-Level Urządzeń przenośnych](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 (z [kb5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 (z [kb5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>Licencjonowanie i subskrypcje

Aby korzystać z zarządzania zabezpieczeniami w programie Microsoft Defender for Endpoint, potrzebujesz:

- Subskrypcja, która udziela licencji na usługę Microsoft Defender dla punktu końcowego, na przykład Microsoft 365, lub autonomiczną licencję tylko programu Microsoft Defender dla punktu końcowego. Subskrypcja, która udziela licencji programu Microsoft Defender dla punktów końcowych, udziela również dostępu dzierżawcy do węzła zabezpieczeń punktu Microsoft Endpoint Manager administracyjnego.

  > [!NOTE]  
  > **Wyjątek**: jeśli w ramach licencji Microsoft Defender for Cloud tylko (dawniej Azure Security Center) masz dostęp do programu Microsoft Defender for Endpoint, funkcja zarządzania zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego nie jest dostępna.

Węzeł zabezpieczeń punktu końcowego to miejsce, w którym możesz skonfigurować i wdrożyć zasady zarządzania usługą Microsoft Defender dla punktu końcowego dla swoich urządzeń i monitorowania stanu urządzenia.

Aby uzyskać bieżące informacje na temat opcji, zobacz [Minimalne wymagania programu Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>Architektura

Poniższy diagram przedstawia koncepcyjną reprezentację rozwiązania do zarządzania konfiguracją zabezpieczeń programu Microsoft Defender for Endpoint.

:::image type="content" alt-text="Koncepcyjna reprezentacja rozwiązania do zarządzania konfiguracją zabezpieczeń programu Microsoft Defender for Endpoint" source="../security/defender-endpoint/images/mde-architecture.png":::

1. Urządzenia są dołączane do programu Microsoft Defender dla punktu końcowego.

2. Między każdym urządzeniem a usługą Azure AD jest ustanowione zaufanie. Używane jest istniejące zaufanie dla urządzenia. Jeśli urządzenia nie zostały zarejestrowane, jest tworzone nowe zaufanie.

3. Urządzenia komunikują się z innymi użytkownikami za pomocą tożsamości usługi Azure AD Endpoint Manager. Ta tożsamość umożliwia Microsoft Endpoint Manager zasad, które są kierowane do urządzeń podczas ich zaewidencjonania.

4. Program Defender for Endpoint ponownie informuje o stanie zasad w Endpoint Manager.

## <a name="which-solution-should-i-use"></a>Którego rozwiązania mam użyć?

Microsoft Endpoint Manager metody i typy zasad do zarządzania konfiguracją usługi Defender for Endpoint na urządzeniach.

Jeśli ochrona urządzenia wymaga więcej niż zarządzania programem Defender for Endpoint, [](/mem/intune/protect/device-protect) zobacz Omówienie ochrony urządzeń, aby dowiedzieć się więcej o dodatkowych możliwościach firmy Microsoft Endpoint Manager dotyczących ochrony urządzeń, takich jak zgodność *urządzeń, aplikacje* *zarządzane, zasady* ochrony aplikacji oraz integracja z innymi partnerami w zakresie ochrony przed zagrożeniami i zgodnością z urządzeniami *przenośnymi.*

W poniższej tabeli przedstawiono zasady, które mogą konfigurować ustawienia MDE, są obsługiwane przez urządzenia zarządzane przez różne scenariusze. Po wdrożeniu zasad obsługiwanych zarówno w przypadku konfiguracji zabezpieczeń *MDE*, jak i programu *Microsoft Endpoint Manager* pojedyncze wystąpienie tych zasad może być przetwarzane przez urządzenia, na których działa tylko usługa MDE, oraz urządzenia zarządzane przez usługę Intune lub Menedżer konfiguracji.

| Microsoft Endpoint Manager  | Obciążenie pracą | Konfiguracja zabezpieczeń MDE  |  Microsoft Endpoint Manager |
|----------------|----------------|-------------------|------------|
| Zabezpieczenia punktu końcowego    | Oprogramowanie antywirusowe                   | ![Obsługiwane](../media/green-check.png)  | ![Obsługiwane](../media/green-check.png)  |
|                      | Szyfrowanie dysku   |           | ![Obsługiwane](../media/green-check.png)  |
|                      | Zapora (profil i reguły)                | ![Obsługiwane](../media/green-check.png) | ![Obsługiwane](../media/green-check.png)  |
|                      | Wykrywanie punktu końcowego i odpowiedź        | ![Obsługiwane](../media/green-check.png) | ![Obsługiwane](../media/green-check.png)  |
|                      | Zmniejszenie powierzchni ataków    |           | ![Obsługiwane](../media/green-check.png)  |
|                      | Ochrona konta       |       | ![Obsługiwane](../media/green-check.png)  |
|                      | Zgodność urządzenia     |   | ![Obsługiwane](../media/green-check.png)  |
|                      | Dostęp warunkowy    |   | ![Obsługiwane](../media/green-check.png)  |
|                      | Linie bazowe zabezpieczeń      |   | ![Obsługiwane](../media/green-check.png)  |

**Zasady zabezpieczeń punktów końcowych** to osobne grupy ustawień przeznaczone do używania przez administratorów zabezpieczeń, którzy skupiają się na ochronie urządzeń w Twojej organizacji.

- **Zasady oprogramowania** antywirusowego zarządzają konfiguracjami zabezpieczeń znalezionymi w programie Microsoft Defender dla punktu końcowego. Zobacz  [Zasady oprogramowania antywirusowego](/mem/intune/protect/endpoint-security-antivirus-policy) dotyczące zabezpieczeń punktów końcowych.
- **Zasady ograniczania obszarów** ataków koncentrują się na minimalizowaniu miejsc, w których Twoja organizacja jest narażona na cyberataki i ataki. Aby uzyskać więcej informacji, zobacz [Omówienie](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) ograniczania powierzchni ataków w dokumentacji programu Windows ochrony przed zagrożeniami i zasady [](/mem/intune/protect/endpoint-security-asr-policy) ograniczania powierzchni ataków dla zabezpieczeń punktów końcowych.
- **Zasady wykrywania i odpowiedzi** punktu końcowego (EDR) zarządzają możliwościami usługi Defender for Endpoint, które zapewniają zaawansowane wykrywanie ataków, które są blisko czasu rzeczywistego i które oferują możliwości działania. Na podstawie EDR, analitycy zabezpieczeń mogą efektywnie określać alerty, zyskać wgląd w pełny zakres naruszenia oraz podjąć działania w celu reagowania na zagrożenia. Zobacz [wykrywanie i reagowanie w punktach końcowych](/mem/intune/protect/endpoint-security-edr-policy) zabezpieczeń punktu końcowego.
- **Zasady** zapory koncentrują się na zaporze usługi Defender na Twoich urządzeniach. Zobacz [zasady zapory](/mem/intune/protect/endpoint-security-firewall-policy) dotyczące zabezpieczeń punktów końcowych.
- **Reguły zapory** konfigurują szczegółowe reguły zapory, w tym określone porty, protokoły, aplikacje i sieci. Zobacz [zasady zapory](/mem/intune/protect/endpoint-security-firewall-policy) dotyczące zabezpieczeń punktów końcowych.
- **Linie bazowe zabezpieczeń** zawierają wstępnie skonfigurowane ustawienia zabezpieczeń definiujące zalecane przez firmę Microsoft środki za zabezpieczenia dla różnych produktów, takich jak Defender, Edge i Windows. Domyślne zalecenia znajdują się w odpowiednich zespołach produktu i umożliwiają szybkie wdrożenie zalecanej bezpiecznej konfiguracji na urządzeniach. Mimo że ustawienia są wstępnie skonfigurowane w poszczególnych planach bazowych, możesz utworzyć dostosowane wystąpienia tych wystąpień, aby ustalić oczekiwania dotyczące zabezpieczeń twojej organizacji. Zobacz [informacje o planach bazowych zabezpieczeń](/mem/intune/protect/security-baselines) dla usługi Intune.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Konfigurowanie dzierżawy do obsługi programu Microsoft Defender for Endpoint Security Configuration Management

Aby obsługiwać program Microsoft Defender for Endpoint zarządzanie konfiguracją zabezpieczeń za pośrednictwem centrum administracyjnego programu Microsoft Endpoint Manager, musisz włączyć komunikację między nimi z poziomu każdej konsoli.

1. Zaloguj się [do Microsoft 365 Defender i](https://security.microsoft.com/) przejdź do **strony Ustawienia** >  **EndpointsConfiguration** >  **ManagementEnforcement Zakres** >  i włącz platformy do zarządzania ustawieniami zabezpieczeń:

   :::image type="content" source="../media/enable-mde-settings-management-defender.png" alt-text="Włącz program Microsoft Defender dla zarządzania ustawieniami punktu końcowego w konsoli Defender.":::

2. Upewnij się, że odpowiedni użytkownicy mają uprawnienia do zarządzania ustawieniami zabezpieczeń punktów końcowych w programie Microsoft Endpoint Manager lub udzielaj tych uprawnień, konfigurując rolę w portalu usługi Defender. Przejdź do **Ustawienia** >  **RolesAdd** >  elementu:

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Utwórz nową rolę w portalu usługi Defender.":::

   > [!TIP]
   > Można modyfikować istniejące role i dodawać konieczne uprawnienia w porównaniu z tworzeniem dodatkowych ról w programie Microsoft Defender for Endpoint

3. Podczas konfigurowania roli dodaj użytkowników i wybierz pozycję **Zarządzaj ustawieniami zabezpieczeń punktu końcowego w programie Microsoft Endpoint Manager**:

   :::image type="content" source="../media/add-role.png" alt-text="Udzielanie użytkownikom uprawnień do zarządzania ustawieniami.":::

4. Zaloguj się do [centrum administracyjnego programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Wybierz **pozycję Zabezpieczenia punktu** końcowegoMicrosoft  > **Defender for Endpoint** i ustaw dla opcji **Zezwalaj programowi Microsoft Defender na** punkt końcowy w celu wymuszania konfiguracji zabezpieczeń punktu końcowego (wersja Preview) na **wartość Wł**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Włącz usługę Microsoft Defender dla zarządzania ustawieniami punktu końcowego w centrum Microsoft Endpoint Manager administracyjnego.":::

   Po skonfigurowaniu tej opcji na wartość Wł *., wszystkie* urządzenia w zakresie platformy w programie Microsoft Defender for Endpoint, które nie są zarządzane przez program Microsoft Endpoint Manager będą kwalifikowały się do korzystania z programu Microsoft Defender dla punktu końcowego.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Urządzenia w programie Microsoft Defender dla punktu końcowego

Program Microsoft Defender for Endpoint obsługuje kilka opcji w przypadku urządzeń mobilnych. Aby uzyskać aktualne wskazówki, zobacz Narzędzia i metody dołączania do [Windows w](/microsoft-365/security/defender-endpoint/security-config-management) dokumentacji programu Defender for Endpoint.


> [!IMPORTANT]
> Po dojechi urządzenia z programem Microsoft Defender for Endpoint musi ono zostać oznakowane za pomocą funkcji **MDE-Management** , aby było możliwe zarejestrowanie się w układzie Zarządzanie zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego. Aby uzyskać więcej informacji na temat tagowania urządzeń w aplikacji MDE, zobacz [*Tworzenie tagów urządzeń i zarządzanie nimi*](/microsoft-365/security/defender-endpoint/machine-tags).


## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>Istnienie ze Microsoft Endpoint Configuration Manager
Podczas korzystania Menedżer konfiguracji najlepszą ścieżką do zarządzania zasadami zabezpieczeń jest dołączanie Menedżer konfiguracji [dzierżawy](/mem/configmgr/tenant-attach/endpoint-security-get-started). W niektórych środowiskach pożądane może być korzystanie z zarządzania zabezpieczeniami dla programu Microsoft Defender. Podczas korzystania z zarządzania zabezpieczeniami dla programu Microsoft Defender Menedżer konfiguracji zasady zabezpieczeń punktu końcowego powinny być odizolowane od jednego samolotu kontrolnego. Kontrolowanie zasad za pośrednictwem obu kanałów umożliwia tworzenie konfliktów i niepożądane rezultaty.


## <a name="create-azure-ad-groups"></a>Tworzenie grup usługi Azure AD

Po dojecheniu urządzeń do usługi Defender for Endpoint musisz utworzyć grupy urządzeń w celu obsługi wdrożenia zasad dla programu Microsoft Defender dla punktu końcowego.

Aby zidentyfikować urządzenia, które zarejestrowane za pomocą usługi Microsoft Defender for Endpoint, ale nie są zarządzane przez usługę Intune lub Menedżer konfiguracji:

1. Zaloguj się do [Microsoft Endpoint Manager administracyjnego](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Przejdź do **urządzeniaWszystkie** >  **urządzenia**, a następnie zaznacz kolumnę Zarządzane **przez**, aby posortować widok urządzeń.

   Urządzenia, które są wnosone do usługi Microsoft Defender for Endpoint i zarejestrowane, ale nie są zarządzane przez usługę Intune, wyświetlają usługę **Microsoft Defender for Endpoint** w *kolumnie Zarządzane przez* . To są urządzenia, które mogą otrzymywać zasady zarządzania zabezpieczeniami dla programu Microsoft Defender for Endpoint.

   Znajdziesz też dwie etykiety dla urządzeń korzystających z zarządzania zabezpieczeniami dla programu Microsoft Defender for Endpoint:

   - **MDEJoined** — dodano do urządzeń, które są sprzężeniami z katalogiem w ramach tego scenariusza.
   - **MDEManaged** — dodane do urządzeń aktywnie korzystających ze scenariusza zarządzania zabezpieczeniami. Ten tag zostanie usunięty z urządzenia, jeśli program Defender for Endpoint przestanie zarządzać konfiguracją zabezpieczeń.

Grupy dla tych urządzeń można tworzyć w [usłudze Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) lub w centrum [Microsoft Endpoint Manager administracyjnego](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>Wdrażanie zasad

Po utworzeniu co najmniej jednej grupy usługi Azure AD, które zawierają urządzenia zarządzane przez program Microsoft Defender for Endpoint, możesz utworzyć i wdrożyć następujące zasady zarządzania zabezpieczeniami dla programu Microsoft Defender dla punktu końcowego w tych grupach:

- Oprogramowanie antywirusowe
- Zapora
- Reguły zapory
- Wykrywanie punktu końcowego i odpowiedź

> [!TIP]
> Unikaj wdrażania wielu zasad, które zarządzają tym samym ustawieniem na urządzeniu.
>
> Microsoft Endpoint Manager obsługuje wdrażanie wielu wystąpień każdego typu zasad zabezpieczeń punktu końcowego na tym samym urządzeniu, a każde wystąpienie zasad jest odbierane przez urządzenie oddzielnie. Dlatego urządzenie może otrzymywać osobne konfiguracje dla tego samego ustawienia z różnych zasad, co powoduje konflikt. Niektóre ustawienia (na przykład wykluczenia oprogramowania antywirusowego) zostaną scalone z klientem i zostaną pomyślnie stosowane.

1. Zaloguj się do [centrum administracyjnego programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Przejdź do **zabezpieczeń punktu końcowego** , a następnie wybierz typ zasad, które chcesz skonfigurować : Oprogramowanie antywirusowe lub Zapora, a następnie wybierz **pozycję Utwórz zasady**.

3. Wprowadź następujące właściwości lub wybrany typ zasad:

   - W przypadku zasad oprogramowania antywirusowego wybierz pozycję:
     - Platforma: **Windows 10, Windows 11 i Windows Server (Wersja Preview)**
     - Profil: **Program antywirusowy Microsoft Defender (wersja zapoznawcza)**

   - W przypadku zasad zapory wybierz pozycję:
     - Platforma: **Windows 10, Windows 11 i Windows Server (Wersja Preview)**
     - Profil: **Zapora Microsoft Defender (wersja zapoznawcza)**

   - W przypadku zasad Reguły zapory wybierz pozycję:
     - Platforma: **Windows 10, Windows 11 i Windows Server (Wersja Preview)**
     - Profil: **Reguły zapory programu Microsoft Defender (wersja zapoznawcza)**

   - W przypadku zasad Wykrywanie punktu końcowego i odpowiedzi wybierz pozycję:
     - Platforma: **Windows 10, Windows 11 i Windows Server (Wersja Preview)**
     - Profil: **Wykrywanie punktu końcowego i odpowiedź (wersja Preview)**

   >[!Note]
   > Te profile mają zastosowanie zarówno do urządzeń komunikjących się za pośrednictwem funkcji Zarządzanie urządzeniami przenośnymi (MDM), jak i do urządzeń, Microsoft Intune które komunikują się przy użyciu klienta programu Microsoft Defender for Endpoint.
   >
   > Upewnij się, że w razie potrzeby przeglądasz informacje dotyczące określania docelowych wartości i grup.

4. Wybierz pozycję **Utwórz**.

5. Na stronie **Podstawowe** wprowadź nazwę i opis dla profilu, a następnie wybierz pozycję **Dalej**.

6. Na **stronie Ustawienia konfiguracji** wybierz ustawienia, które chcesz zarządzać za pomocą tego profilu. Aby dowiedzieć się więcej o ustawieniu, rozwiń okno dialogowe z informacjami i *wybierz link Dowiedz* się więcej, aby wyświetlić informacje o programie CSP dla ustawienia w dokumentacji on-line.

   Po zakończeniu konfigurowania ustawień wybierz pozycję **Dalej**.

7. Na stronie **Zadania wybierz** grupy usługi Azure AD, które otrzymają ten profil. Aby uzyskać więcej informacji na temat przypisywania profilów, zobacz [Przypisywanie profilów użytkowników i urządzeń](/mem/intune/configuration/device-profile-assign).

   Wybierz przycisk **Dalej**, aby kontynuować.

   > [!TIP]
   >
   > - Filtry przydziałów nie są obsługiwane w profilach zarządzania konfiguracją zabezpieczeń.
   > - Do *zarządzania punktami* końcowymi programu Microsoft Defender obowiązują tylko obiekty urządzeń. Kierowanie użytkowników nie jest obsługiwane.
   > - Skonfigurowane zasady będą stosowane zarówno do programu Microsoft Intune, jak i programu Microsoft Defender dla klientów końcowych

8. Ukończ proces tworzenia zasad, a następnie na **stronie Recenzja + utwórz** wybierz pozycję **Utwórz**. Nowy profil zostanie wyświetlony na liście po wybraniu typu zasad dla utworzonego profilu.

9. Poczekaj na przypisanie zasady i wyświetl wskaźnik sukcesu, że zasady zostały zastosowane.

10. Aby sprawdzić, czy ustawienia zostały zastosowane lokalnie na kliencie, możesz użyć narzędzia [poleceń Get-MpPreference](/powershell/module/defender/get-mppreference#examples) .
