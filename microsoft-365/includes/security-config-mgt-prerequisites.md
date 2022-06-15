---
title: uwzględnij plik
description: uwzględnij plik
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 61d7b5f00a42789a2d4f46aa41eb3f8865fb6e03
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66091459"
---
## <a name="prerequisites"></a>Wymagania wstępne

Zapoznaj się z następującymi sekcjami, aby zapoznać się z wymaganiami dotyczącymi zarządzania zabezpieczeniami dla scenariusza Ochrona punktu końcowego w usłudze Microsoft Defender:

### <a name="environment"></a>Środowiska

Gdy urządzenie zostanie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender:


- Urządzenie jest badane pod kątem istniejącej obecności Endpoint Manager, czyli rejestracji zarządzania urządzeniami przenośnymi (MDM) w celu Intune
- Urządzenia bez obecności Endpoint Manager będą włączać funkcję zarządzania zabezpieczeniami
- Jeśli relacja zaufania jeszcze nie istnieje, zostanie utworzona relacja zaufania z Azure Active Directory
- Azure Active Directory zaufanie jest używane do komunikowania się z Endpoint Manager (Intune) i pobierania zasad
- Pobieranie zasad z Endpoint Manager jest wymuszane na urządzeniu przez Ochrona punktu końcowego w usłudze Microsoft Defender

### <a name="active-directory-requirements"></a>Wymagania usługi Active Directory

Gdy urządzenie przyłączone do domeny tworzy relację zaufania z Azure Active Directory, ten scenariusz jest określany jako scenariusz *dołączania* hybrydowego Azure Active Directory. Usługa Security Management for Ochrona punktu końcowego w usłudze Microsoft Defender w pełni obsługuje ten scenariusz z następującymi wymaganiami:

- Azure Active Directory Połączenie (AAD Połączenie) należy zsynchronizować z dzierżawą używaną z Ochrona punktu końcowego w usłudze Microsoft Defender
- Przyłączanie hybrydowe Azure Active Directory musi być skonfigurowane w środowisku (za pośrednictwem federacji lub usługi AAD Połączenie Sync)
- Usługa AAD Połączenie Sync musi zawierać obiekty urządzenia *w zakresie* synchronizacji z Azure Active Directory (w razie potrzeby w celu dołączenia)
- Reguły Połączenie usługi AAD dotyczące synchronizacji muszą zostać zmodyfikowane dla serwera 2012 R2 (gdy wymagana jest obsługa serwera 2012 R2)
- Wszystkie urządzenia muszą zarejestrować się w Azure Active Directory dzierżawy hostującej Ochrona punktu końcowego w usłudze Microsoft Defender. Scenariusze obejmujące wiele dzierżaw nie są obsługiwane. 

### <a name="connectivity-requirements"></a>Wymagania dotyczące połączenia

Urządzenia muszą mieć dostęp do następujących punktów końcowych:

- `enterpriseregistration.windows.net`- Na potrzeby rejestracji Azure AD.
- `login.microsoftonline.com`- Na potrzeby rejestracji Azure AD.
- `*.dm.microsoft.com` — Użycie symbolu wieloznacznego obsługuje punkty końcowe usługi w chmurze używane do rejestracji, ewidencjonowania i raportowania, które mogą ulec zmianie w miarę skalowania usługi.

> [!Note]
> Jeśli użytkownicy organizacji przeprowadzają inspekcję protokołu Secure Socket Layer (SSL), punkty końcowe powinny zostać wykluczone z inspekcji.

### <a name="supported-platforms"></a>Obsługiwane platformy

Zasady zarządzania zabezpieczeniami Ochrona punktu końcowego w usłudze Microsoft Defender są obsługiwane dla następujących platform urządzeń:

- Windows 10 Professional/Enterprise (z [kb5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows 11 Professional/Enterprise
- Windows Server 2012 R2 z [usługą Microsoft Defender dla urządzeń Down-Level](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 z [usługą Microsoft Defender dla urządzeń Down-Level](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 (z [KB5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 (z [kb5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>Licencjonowanie i subskrypcje

Aby korzystać z zarządzania zabezpieczeniami dla Ochrona punktu końcowego w usłudze Microsoft Defender, potrzebne są:

- Subskrypcja, która udziela licencji na Ochrona punktu końcowego w usłudze Microsoft Defender, na przykład Microsoft 365, lub licencję autonomiczną tylko dla Ochrona punktu końcowego w usłudze Microsoft Defender. Subskrypcja, która udziela licencji Ochrona punktu końcowego w usłudze Microsoft Defender, udziela również dzierżawcy dostępu do węzła zabezpieczeń punktu końcowego centrum administracyjnego Microsoft Endpoint Manager.

  > [!NOTE]  
  > **Wyjątek**: jeśli masz dostęp do Ochrona punktu końcowego w usłudze Microsoft Defender w ramach licencji Microsoft Defender dla Chmury tylko (dawniej Azure Security Center), usługa Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender funkcjonalność nie jest dostępna.

Węzeł Zabezpieczenia punktu końcowego to miejsce, w którym skonfigurujesz i wdrożysz zasady do zarządzania Ochrona punktu końcowego w usłudze Microsoft Defender dla urządzeń i monitorowania stanu urządzenia.

Aby uzyskać bieżące informacje o opcjach, zobacz [Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>Architektura

Na poniższym diagramie przedstawiono koncepcyjną reprezentację rozwiązania do zarządzania konfiguracją zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender.

:::image type="content" alt-text="Koncepcyjna reprezentacja rozwiązania do zarządzania konfiguracją zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender" source="../security/defender-endpoint/images/mde-architecture.png":::

1. Urządzenia dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender.

2. Między każdym urządzeniem a Azure AD ustanawiane jest zaufanie. Jeśli urządzenie ma istniejące zaufanie, jest ono używane. Gdy urządzenia nie zostały zarejestrowane, zostanie utworzone nowe zaufanie.

3. Urządzenia komunikują się z Endpoint Manager przy użyciu tożsamości Azure AD. Ta tożsamość umożliwia Microsoft Endpoint Manager dystrybuowanie zasad przeznaczonych dla urządzeń podczas ich zaewidencjonowania.

4. Usługa Defender dla punktu końcowego zgłasza stan zasad z powrotem do Endpoint Manager.

## <a name="which-solution-should-i-use"></a>Którego rozwiązania należy użyć?

Microsoft Endpoint Manager obejmuje kilka metod i typów zasad do zarządzania konfiguracją usługi Defender for Endpoint na urządzeniach.

Jeśli ochrona urządzenia wymaga rozszerzenia poza zarządzanie usługą Defender for Endpoint, zobacz [Omówienie ochrony urządzeń](/mem/intune/protect/device-protect), aby dowiedzieć się więcej o dodatkowych funkcjach udostępnianych przez Microsoft Endpoint Manager w celu ochrony urządzeń, takich jak *zgodność urządzeń*, *aplikacje zarządzane*, *zasady ochrony aplikacji* oraz integracja z partnerami ds. zgodności i *ochrony przed zagrożeniami mobilnymi*.

Poniższa tabela pomaga zrozumieć, które zasady, które można skonfigurować ustawienia MDE, są obsługiwane przez urządzenia zarządzane przez różne scenariusze. Po wdrożeniu zasad obsługiwanych zarówno w przypadku *konfiguracji zabezpieczeń mde*, jak i *Microsoft Endpoint Manager* pojedyncze wystąpienie tych zasad może być przetwarzane przez urządzenia z systemem Ochrona punktu końcowego w usłudze Microsoft Defender tylko i urządzenia zarządzane przez dowolną z nich Intune lub Configuration Manager.

| Microsoft Endpoint Manager  | Obciążenia |Zasad| Konfiguracja zabezpieczeń mde  |  Microsoft Endpoint Manager |
|----------------|----------------|-------------------|------------|
| Zabezpieczenia punktu końcowego    | Antivirus   |     Antivirus           | ![Obsługiwane](../media/green-check.png)  | ![Obsługiwane](../media/green-check.png)  |
|                      | Antivirus   |   Wykluczenia programu antywirusowego   | ![Obsługiwane](../media/green-check.png)  | ![Obsługiwane](../media/green-check.png)  |
|                      | Antivirus   | środowisko Zabezpieczenia Windows |                        | ![Obsługiwane](../media/green-check.png)  |
|                      | Szyfrowanie dysków   |     Wszystkie |      | ![Obsługiwane](../media/green-check.png)  |
|                      | Zapory   | Zapory              | ![Obsługiwane](../media/green-check.png) | ![Obsługiwane](../media/green-check.png)  |
|                      | Zapory | Reguły zapory                | ![Obsługiwane](../media/green-check.png) | ![Obsługiwane](../media/green-check.png)  |
|                      | Wykrywanie i reagowanie dotyczące punktów końcowych   | Wykrywanie i reagowanie dotyczące punktów końcowych | ![Obsługiwane](../media/green-check.png) | ![Obsługiwane](../media/green-check.png)  |
|                      | Zmniejszanie obszaru podatnego na ataki    |   Wszystkie |          | ![Obsługiwane](../media/green-check.png)  |
|                      | Ochrona konta       |    Wszystkie |     | ![Obsługiwane](../media/green-check.png)  |
|                      | Zgodność urządzenia     |   Wszystkie |  | ![Obsługiwane](../media/green-check.png)  |
|                      | Dostęp warunkowy    |   Wszystkie |  | ![Obsługiwane](../media/green-check.png)  |
|                      | Plan bazowy zabezpieczeń      |  Wszystkie |   | ![Obsługiwane](../media/green-check.png)  |

**Zasady zabezpieczeń punktu końcowego** to odrębne grupy ustawień przeznaczone do użycia przez administratorów zabezpieczeń, którzy koncentrują się na ochronie urządzeń w organizacji.

- **Zasady ochrony antywirusowej** zarządzają konfiguracjami zabezpieczeń znalezionymi w Ochrona punktu końcowego w usłudze Microsoft Defender. Zobacz zasady  [ochrony antywirusowej](/mem/intune/protect/endpoint-security-antivirus-policy) dotyczące zabezpieczeń punktów końcowych.
- Zasady **zmniejszania obszaru ataków** koncentrują się na minimalizowaniu miejsc, w których organizacja jest podatna na ataki cybernetyczne i ataki. Aby uzyskać więcej informacji, zobacz [Omówienie zmniejszania obszaru podatnego na ataki](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) w dokumentacji Windows Ochrona przed zagrożeniami oraz zasady [zmniejszania obszaru ataków](/mem/intune/protect/endpoint-security-asr-policy) dla zabezpieczeń punktu końcowego.
- Zasady **wykrywania i reagowania na punkty końcowe** (EDR) zarządzają możliwościami usługi Defender for Endpoint, które zapewniają zaawansowane wykrywanie ataków niemal w czasie rzeczywistym i możliwość akcji. Na podstawie konfiguracji EDR analitycy zabezpieczeń mogą efektywnie ustalać priorytety alertów, uzyskiwać wgląd w pełny zakres naruszenia i podejmować działania reagowania w celu skorygowania zagrożeń. Zobacz [zasady wykrywanie i reagowanie w punktach końcowych](/mem/intune/protect/endpoint-security-edr-policy) dotyczące zabezpieczeń punktu końcowego.
- Zasady **zapory** koncentrują się na zaporze usługi Defender na urządzeniach. Zobacz zasady [zapory](/mem/intune/protect/endpoint-security-firewall-policy) dotyczące zabezpieczeń punktu końcowego.
- **Reguły zapory** konfigurują szczegółowe reguły dla zapór, w tym określone porty, protokoły, aplikacje i sieci. Zobacz zasady [zapory](/mem/intune/protect/endpoint-security-firewall-policy) dotyczące zabezpieczeń punktu końcowego.
- **Punkty odniesienia zabezpieczeń** obejmują wstępnie skonfigurowane ustawienia zabezpieczeń definiujące zalecaną przez firmę Microsoft postawę zabezpieczeń dla różnych produktów, takich jak Defender, Edge lub Windows. Zalecenia domyślne pochodzą od odpowiednich zespołów ds. produktów i umożliwiają szybkie wdrożenie zalecanej bezpiecznej konfiguracji na urządzeniach. Ustawienia są wstępnie konfigurowane w każdym punkcie odniesienia, ale można tworzyć ich dostosowane wystąpienia w celu ustalenia oczekiwań organizacji w zakresie zabezpieczeń. Zobacz [punkty odniesienia zabezpieczeń](/mem/intune/protect/security-baselines) dla Intune.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Konfigurowanie dzierżawy do obsługi zarządzania konfiguracją zabezpieczeń Ochrona punktu końcowego w usłudze Microsoft Defender

Aby obsługiwać Ochrona punktu końcowego w usłudze Microsoft Defender zarządzania konfiguracją zabezpieczeń za pośrednictwem centrum administracyjnego Microsoft Endpoint Manager, należy włączyć komunikację między nimi z poziomu każdej konsoli.

1. Zaloguj się do [portalu Microsoft 365 Defender](https://security.microsoft.com/) i przejdź do **obszaru Ustawienia** >  **Endpoints** >  Configuration Management **Enforcement Scope (Zakres wymuszania zarządzania** **konfiguracją** >  punktów) i włącz platformy do zarządzania ustawieniami zabezpieczeń:

   :::image type="content" source="../media/security-settings-mgt.png" alt-text="Włącz zarządzanie ustawieniami Ochrona punktu końcowego w usłudze Microsoft Defender w konsoli usługi Defender.":::
    
1. Skonfiguruj tryb pilotażowy i Configuration Manager ustawień urzędu zgodnie z potrzebami organizacji:

   :::image type="content" source="../media/pilot-CMAuthority-mde-settings-management-defender.png" alt-text="Skonfiguruj tryb pilotażowy dla zarządzania ustawieniami punktu końcowego w portalu Microsoft 365 Defender.":::
   
  > [!TIP]
  > Użyj trybu pilotażowego i odpowiednich tagów urządzeń, aby przetestować i zweryfikować wdrożenie na niewielkiej liczbie urządzeń. Bez korzystania z trybu pilotażowego każde urządzenie wchodzące w skonfigurowany zakres zostanie automatycznie zarejestrowane.

1. Upewnij się, że odpowiedni użytkownicy mają uprawnienia do zarządzania ustawieniami zabezpieczeń punktu końcowego w Microsoft Endpoint Manager lub udzielania tych uprawnień, konfigurując rolę w portalu usługi Defender. Przejdź do **pozycji Ustawienia** >  **Role** > **Dodaj element**:

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Utwórz nową rolę w portalu usługi Defender.":::

   > [!TIP]
   > Istniejące role można modyfikować i dodawać niezbędne uprawnienia w porównaniu z tworzeniem dodatkowych ról w Ochrona punktu końcowego w usłudze Microsoft Defender

1. Podczas konfigurowania roli dodaj użytkowników i wybierz pozycję **Zarządzaj ustawieniami zabezpieczeń punktu końcowego w Microsoft Endpoint Manager**:

   :::image type="content" source="../media/add-role.png" alt-text="Przyznaj użytkownikom uprawnienia do zarządzania ustawieniami.":::

1. Zaloguj się do [centrum administracyjnego programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

1. Wybierz pozycję **Zabezpieczenia** >  punktu końcowego Ochrona punktu końcowego w usłudze Microsoft Defender i ustaw opcję **Zezwalaj Ochrona punktu końcowego w usłudze Microsoft Defender na wymuszanie konfiguracji zabezpieczeń punktu końcowego (wersja zapoznawcza)** **na wartość Włączone**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Włącz zarządzanie ustawieniami Ochrona punktu końcowego w usłudze Microsoft Defender w centrum administracyjnym Microsoft Endpoint Manager.":::

   Po ustawieniu tej opcji *na wartość Włączone* wszystkie urządzenia w zakresie platformy w Ochrona punktu końcowego w usłudze Microsoft Defender, które nie są zarządzane przez Microsoft Endpoint Manager, będą kwalifikować się do dołączenia do Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Dołączanie urządzeń do Ochrona punktu końcowego w usłudze Microsoft Defender

Ochrona punktu końcowego w usłudze Microsoft Defender obsługuje kilka opcji dołączania urządzeń. Aby uzyskać bieżące wskazówki, zobacz [Dołączanie narzędzi i metod dla urządzeń Windows](/microsoft-365/security/defender-endpoint/security-config-management) w dokumentacji usługi Defender for Endpoint.



## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>Współistnienie z Microsoft Endpoint Configuration Manager
W niektórych środowiskach może być konieczne użycie usługi Security Management do Ochrona punktu końcowego w usłudze Microsoft Defender z [dołączaniem dzierżawy Configuration Manager](/mem/configmgr/tenant-attach/endpoint-security-get-started). Jeśli używasz obu tych kanałów, musisz kontrolować zasady za pośrednictwem jednego kanału, ponieważ użycie więcej niż jednego kanału stwarza szansę na konflikty i niepożądane wyniki.

Aby to obsłużyć, skonfiguruj *ustawienia Zarządzanie zabezpieczeniami przy użyciu przełącznika Configuration Manager* w pozycji *Wyłączone*.  Zaloguj się do [portalu Microsoft 365 Defender](https://security.microsoft.com/) i przejdź do **obszaru Ustawienia** >  Endpoints Configuration Management **Enforcement Scope (Zakres wymuszania zarządzania** **konfiguracją** >  **punktów końcowych** > ):

:::image type="content" source="../media/manage-security-settings-cfg-mgr.png" alt-text="Zarządzanie ustawieniami zabezpieczeń przy użyciu ustawienia Configuration Manager.":::

>[!NOTE]
>W przypadku korzystania z usługi Security Management dla Ochrona punktu końcowego w usłudze Microsoft Defender z Configuration Manager zasady zabezpieczeń punktu końcowego powinny być izolowane do pojedynczej płaszczyzny sterowania. Kontrolowanie zasad za pośrednictwem obu kanałów może powodować konflikty i niepożądane wyniki.


## <a name="create-azure-ad-groups"></a>Tworzenie grup Azure AD

Po dołączeniu urządzeń do usługi Defender for Endpoint należy utworzyć grupy urządzeń w celu obsługi wdrażania zasad dla Ochrona punktu końcowego w usłudze Microsoft Defender.

Aby zidentyfikować urządzenia zarejestrowane w Ochrona punktu końcowego w usłudze Microsoft Defender, ale nie są zarządzane przez Intune lub Configuration Manager:

1. Zaloguj się do [centrum administracyjnego Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Przejdź do pozycji **Urządzenia** > **Wszystkie urządzenia**, a następnie wybierz kolumnę **Zarządzane przez** , aby posortować widok urządzeń.

   Urządzenia dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender i zarejestrowane, ale nie są zarządzane przez Intune wyświetlają **Ochrona punktu końcowego w usłudze Microsoft Defender** w kolumnie *Zarządzane przez*. Są to urządzenia, które mogą odbierać zasady zarządzania zabezpieczeniami dla Ochrona punktu końcowego w usłudze Microsoft Defender.

   Znajdziesz również dwie etykiety dla urządzeń korzystających z zarządzania zabezpieczeniami dla Ochrona punktu końcowego w usłudze Microsoft Defender:

   - **MDEJoined** — dodano do urządzeń przyłączonych do katalogu w ramach tego scenariusza.
   - **MDEManaged** — dodano do urządzeń, które aktywnie korzystają ze scenariusza zarządzania zabezpieczeniami. Ten tag zostanie usunięty z urządzenia, jeśli usługa Defender for Endpoint przestanie zarządzać konfiguracją zabezpieczeń.

Grupy dla tych urządzeń można tworzyć [w Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) lub [w centrum administracyjnym Microsoft Endpoint Manager](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>Wdrażanie zasad

Po utworzeniu co najmniej jednej grupy Azure AD zawierającej urządzenia zarządzane przez Ochrona punktu końcowego w usłudze Microsoft Defender można utworzyć i wdrożyć następujące zasady dla usługi Security Management Ochrona punktu końcowego w usłudze Microsoft Defender do tych grup:

- Antivirus
- Zapory
- Reguły zapory
- Wykrywanie i reagowanie na punkty końcowe

> [!TIP]
> Unikaj wdrażania wielu zasad, które zarządzają tym samym ustawieniem na urządzeniu.
>
> Microsoft Endpoint Manager obsługuje wdrażanie wielu wystąpień każdego typu zasad zabezpieczeń punktu końcowego na tym samym urządzeniu, przy czym każde wystąpienie zasad jest odbierane przez urządzenie oddzielnie. W związku z tym urządzenie może otrzymać oddzielne konfiguracje dla tego samego ustawienia z różnych zasad, co powoduje konflikt. Niektóre ustawienia (takie jak wykluczenia antywirusowe) zostaną scalone na kliencie i zostaną pomyślnie zastosowane.

1. Zaloguj się do [centrum administracyjnego programu Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Przejdź do **pozycji Zabezpieczenia punktu końcowego** , a następnie wybierz typ zasad, które chcesz skonfigurować, oprogramowanie antywirusowe lub zaporę, a następnie wybierz pozycję **Utwórz zasady**.

3. Wprowadź następujące właściwości lub wybrany typ zasad:

   - W obszarze Zasady ochrony antywirusowej wybierz pozycję:
     - Platforma: **Windows 10, Windows 11 i serwer Windows (wersja zapoznawcza)**
     - Profil: **Program antywirusowy Microsoft Defender (wersja zapoznawcza)**

   - W obszarze Zasady zapory wybierz pozycję:
     - Platforma: **Windows 10, Windows 11 i serwer Windows (wersja zapoznawcza)**
     - Profil: **Zapora Microsoft Defender (wersja zapoznawcza)**

   - W obszarze Zasady zapory wybierz pozycję:
     - Platforma: **Windows 10, Windows 11 i serwer Windows (wersja zapoznawcza)**
     - Profil: **reguły Zapora Microsoft Defender (wersja zapoznawcza)**

   - W obszarze Zasady wykrywania punktów końcowych i reagowania wybierz:
     - Platforma: **Windows 10, Windows 11 i serwer Windows (wersja zapoznawcza)**
     - Profil: **Wykrywanie i reagowanie punktów końcowych (wersja zapoznawcza)**

   >[!Note]
   > Te profile dotyczą zarówno urządzeń komunikujących się za pośrednictwem usługi Mobile Zarządzanie urządzeniami (MDM) z Microsoft Intune, jak i urządzeń komunikujących się przy użyciu klienta Ochrona punktu końcowego w usłudze Microsoft Defender.
   >
   > Upewnij się, że w razie potrzeby przejrzysz wartości docelowe i grupy.

4. Wybierz pozycję **Utwórz**.

5. Na stronie **Podstawowe** wprowadź nazwę i opis dla profilu, a następnie wybierz pozycję **Dalej**.

6. Na stronie **Ustawienia konfiguracji** wybierz ustawienia, które chcesz zarządzać przy użyciu tego profilu. Aby dowiedzieć się więcej na temat ustawienia, rozwiń okno dialogowe informacji i wybierz link *Dowiedz się więcej* , aby wyświetlić informacje o programie CSP dla tego ustawienia w dokumentacji online.

   Po zakończeniu konfigurowania ustawień wybierz pozycję **Dalej**.

7. Na stronie **Przypisania** wybierz grupy Azure AD, które otrzymają ten profil. Aby uzyskać więcej informacji na temat przypisywania profilów, zobacz [Przypisywanie profilów użytkowników i urządzeń](/mem/intune/configuration/device-profile-assign).

   Wybierz przycisk **Dalej**, aby kontynuować.

   > [!TIP]
   >
   > - Filtry przypisań nie są obsługiwane w przypadku profilów zarządzania konfiguracją zabezpieczeń.
   > - Tylko *obiekty urządzenia* mają zastosowanie do zarządzania Ochrona punktu końcowego w usłudze Microsoft Defender. Kierowanie użytkowników nie jest obsługiwane.
   > - Skonfigurowane zasady będą stosowane zarówno do klientów Microsoft Intune, jak i Ochrona punktu końcowego w usłudze Microsoft Defender

8. Ukończ proces tworzenia zasad, a następnie na stronie **Przeglądanie i tworzenie** wybierz pozycję **Utwórz**. Nowy profil zostanie wyświetlony na liście po wybraniu typu zasad dla utworzonego profilu.

9. Poczekaj na przypisanie zasad i wyświetl informację o powodzeniu, że zasady zostały zastosowane.

10. Możesz sprawdzić, czy ustawienia zostały zastosowane lokalnie na kliencie za pomocą narzędzia polecenia [Get-MpPreference](/powershell/module/defender/get-mppreference#examples) .
