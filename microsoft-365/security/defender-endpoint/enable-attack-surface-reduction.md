---
title: Włączanie reguł zmniejszania obszaru ataków
description: Włącz reguły zmniejszania obszaru ataków (ASR), aby chronić urządzenia przed atakami korzystającymi z makr, skryptów i typowych technik iniekcji.
keywords: Zmniejszanie powierzchni ataku, biodra, system zapobiegania włamaniom hostów, zasady ochrony, antyeksploatacja, antyeksploatacja, luki w zabezpieczeniach, zapobieganie zakażeniom, włączanie, włączanie
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.date: 1/18/2022
ms.openlocfilehash: 90244050b9fd8e5714ba28f7ac9850091d368da7
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601229"
---
# <a name="enable-attack-surface-reduction-rules"></a>Włączanie reguł zmniejszania obszaru ataków

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

> [!TIP]
> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Reguły zmniejszania obszaru ataków](attack-surface-reduction.md) (reguły ASR) pomagają zapobiegać działaniom, które złośliwe oprogramowanie często nadużywa w celu naruszenia zabezpieczeń urządzeń i sieci.

## <a name="requirements"></a>Wymagania

Funkcje zmniejszania obszaru ataków w wersjach systemu Windows

Możesz ustawić reguły zmniejszania obszaru podatnego na ataki dla urządzeń, na których działa dowolna z następujących wersji i wersji systemu Windows:

- [System Windows 11 Pro](/windows/whats-new/windows-11-overview)
- [System Windows 11 dla firm](https://www.microsoft.com/microsoft-365/windows/windows-11-enterprise)
- Windows 10 Pro, [wersja 1709 lub nowsza](/windows/whats-new/whats-new-windows-10-version-1709)
- Windows 10 Enterprise, [wersja 1709 lub nowsza](/windows/whats-new/whats-new-windows-10-version-1709)
- Windows Server, [wersja 1803 (półroczny kanał)](/windows-server/get-started/whats-new-in-windows-server-1803) lub nowszy
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2022](/windows-server/get-started/whats-new-in-windows-server-2022)

Aby użyć całego zestawu funkcji reguł zmniejszania obszaru podatnego na ataki, potrzebne są:

- Program antywirusowy Windows Defender jako podstawowa usługa AV (włączona ochrona w czasie rzeczywistym)
- [Ochrona przed dostarczaniem w chmurze](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) (niektóre reguły tego wymagają)
- licencja Windows 10 Enterprise E5 lub E3

Mimo że reguły zmniejszania obszaru podatnego na ataki nie wymagają [licencji systemu Windows E5](/windows/deployment/deploy-enterprise-licenses), z licencją systemu Windows E5 można uzyskać zaawansowane możliwości zarządzania, w tym monitorowanie, analizę i przepływy pracy dostępne w usłudze Defender for Endpoint, a także możliwości raportowania i konfiguracji w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>. Te zaawansowane możliwości nie są dostępne z licencją E3, ale nadal możesz używać Podgląd zdarzeń do przeglądania zdarzeń reguł zmniejszania obszaru podatnego na ataki.

Każda reguła usługi ASR zawiera jedno z czterech ustawień:

- **Nie skonfigurowano** |  **Wyłączone**: wyłącz regułę usługi ASR
- **Blokuj**: Włączanie reguły usługi ASR
- **Inspekcja**: oceń, jak reguła usługi ASR wpłynie na organizację, jeśli zostanie włączona
- **Ostrzegaj**: Włącz regułę usługi ASR, ale zezwalaj użytkownikowi końcowemu na obejście bloku

Zalecamy używanie reguł usługi ASR z licencją systemu Windows E5 (lub podobną jednostką SKU licencjonowania), aby korzystać z zaawansowanych funkcji monitorowania i raportowania dostępnych w [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md) (Defender for Endpoint). Jeśli jednak masz inną licencję, taką jak Windows Professional lub Windows E3, które nie obejmują zaawansowanych funkcji monitorowania i raportowania, możesz opracować własne narzędzia do monitorowania i raportowania oprócz zdarzeń generowanych w każdym punkcie końcowym po wyzwoleniu reguł usługi ASR (na przykład przekazywania zdarzeń).

> [!TIP]
> Aby dowiedzieć się więcej na temat licencjonowania systemu Windows, zobacz [licencjonowanie Windows 10](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) i zapoznaj się z [przewodnikiem licencjonowania zbiorowego dla Windows 10](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf).

Reguły zmniejszania obszaru ataków można włączyć przy użyciu dowolnej z następujących metod:

- [Microsoft Intune](#intune)
- [Zarządzanie urządzeniami przenośnymi (MDM)](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Zasady grupy](#group-policy)
- [PowerShell](#powershell)

Zalecane jest zarządzanie na poziomie przedsiębiorstwa, takie jak Intune lub Microsoft Endpoint Manager. Zarządzanie na poziomie przedsiębiorstwa spowoduje zastąpienie wszelkich powodujących konflikt ustawień zasady grupy lub programu PowerShell podczas uruchamiania.

## <a name="exclude-files-and-folders-from-asr-rules"></a>Wykluczanie plików i folderów z reguł usługi ASR

Można wykluczyć pliki i foldery z oceny przez większość reguł zmniejszania obszaru ataków. Oznacza to, że nawet jeśli reguła usługi ASR określa, że plik lub folder zawiera złośliwe zachowanie, nie będzie blokować uruchamiania pliku. Może to potencjalnie umożliwić uruchamianie i infekowanie urządzeń przez niebezpieczne pliki.

Można również wykluczyć reguły usługi ASR z wyzwalania na podstawie skrótów certyfikatów i plików, zezwalając na określone wskaźniki plików i certyfikatów usługi Defender for Endpoint. (Zobacz [Zarządzanie wskaźnikami](manage-indicators.md)).

> [!IMPORTANT]
> Wyłączenie plików lub folderów może znacznie zmniejszyć ochronę zapewnianą przez reguły usługi ASR. Wykluczone pliki będą mogły być uruchamiane i nie będzie rejestrowany żaden raport ani zdarzenie.
> Jeśli reguły usługi ASR wykrywają pliki, które prawdopodobnie nie powinny zostać wykryte, należy [najpierw użyć trybu inspekcji, aby przetestować regułę](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit).

Możesz określić poszczególne pliki lub foldery (przy użyciu ścieżek folderów lub w pełni kwalifikowanych nazw zasobów), ale nie możesz określić reguł, do których mają zastosowanie wykluczenia. Wykluczenie jest stosowane tylko wtedy, gdy zostanie uruchomiona wykluczona aplikacja lub usługa. Jeśli na przykład dodasz wykluczenie dla usługi aktualizacji, która jest już uruchomiona, usługa aktualizacji będzie nadal wyzwalać zdarzenia, dopóki usługa nie zostanie zatrzymana i ponownie uruchomiona.

Reguły usługi ASR obsługują zmienne środowiskowe i symbole wieloznaczne. Aby uzyskać informacje na temat używania symboli wieloznacznych, zobacz [Używanie symboli wieloznacznych na liście wykluczeń nazwy pliku i folderu lub rozszerzenia](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>Konflikt zasad

1. Jeśli zasady powodujące konflikt są stosowane za pośrednictwem zarządzania urządzeniami przenośnymi i zasadami grupy, pierwszeństwo będzie mieć ustawienie zastosowane z rozwiązania MDM.

2. Reguły zmniejszania obszaru ataków dla urządzeń zarządzanych przez MEM obsługują teraz zachowanie łączenia ustawień z różnych zasad w celu utworzenia nadzbioru zasad dla każdego urządzenia. Tylko ustawienia, które nie są w konflikcie, są scalane, podczas gdy te, które są w konflikcie, nie są dodawane do nadzbioru reguł. Wcześniej, jeśli dwie zasady zawierały konflikty dla jednego ustawienia, obie zasady były oflagowane jako będące w konflikcie i żadne ustawienia z żadnego z profilów nie były wdrażane. Zachowanie scalania reguł zmniejszania obszaru podatnego na ataki jest następujące:
   - Reguły zmniejszania obszaru podatnego na ataki z następujących profilów są oceniane dla każdego urządzenia, do którego mają zastosowanie reguły:
     - Urządzenia > zasady konfiguracji > profilu ochrony punktu końcowego >[zmniejszanie obszaru podatnego na ataki](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules) w usłudze **Microsoft Defender Exploit Guard** > .
     - Zabezpieczenia punktu końcowego > **zasady zmniejszania obszaru ataków Reguły** > [zmniejszania obszaru podatnego na ataki](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - Zabezpieczenia punktu końcowego > punkty odniesienia zabezpieczeń >[reguły zmniejszania obszaru podatnego na ataki](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules) **wg planu bazowego** >  usługi Microsoft Defender ATP.
   - Ustawienia, które nie mają konfliktów, są dodawane do nadzbioru zasad dla urządzenia.
   - Jeśli co najmniej dwie zasady mają ustawienia powodujące konflikt, ustawienia powodujące konflikt nie są dodawane do połączonych zasad, a ustawienia, które nie powodują konfliktu, są dodawane do zasad nadzbioru, które mają zastosowanie do urządzenia.
   - Tylko konfiguracje ustawień powodujących konflikt są wstrzymywane.

## <a name="configuration-methods"></a>Metody konfiguracji

Ta sekcja zawiera szczegółowe informacje o konfiguracji następujących metod konfiguracji:

- [Intune](#intune)
- [MEM](#mem)
- [MDM](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Zasady grupy](#group-policy)
- [PowerShell](#powershell)

Poniższe procedury włączania reguł usługi ASR zawierają instrukcje dotyczące wykluczania plików i folderów.

### <a name="intune"></a>Intune

#### <a name="device-configuration-profiles"></a>Profile konfiguracji urządzeń

1. Wybierz pozycję **Profile konfiguracji** \> urządzenia. Wybierz istniejący profil ochrony punktu końcowego lub utwórz nowy. Aby utworzyć nowy, wybierz pozycję **Utwórz profil** i wprowadź informacje dotyczące tego profilu. W polu **Typ profilu** wybierz pozycję **Ochrona punktu końcowego**. Jeśli wybrano istniejący profil, wybierz pozycję **Właściwości** , a następnie wybierz pozycję **Ustawienia**.

2. W okienku **Ochrona punktu końcowego** wybierz pozycję **Windows Defender Exploit Guard**, a następnie wybierz pozycję **Zmniejszanie obszaru podatnego na ataki**. Wybierz odpowiednie ustawienie dla każdej reguły usługi ASR.

3. W obszarze **Wyjątki zmniejszania obszaru podatnego na ataki** wprowadź poszczególne pliki i foldery. Możesz również wybrać pozycję **Importuj** , aby zaimportować plik CSV zawierający pliki i foldery do wykluczenia z reguł usługi ASR. Każdy wiersz w pliku CSV powinien być sformatowany w następujący sposób:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Wybierz przycisk **OK** w trzech okienkach konfiguracji. Następnie wybierz pozycję **Utwórz** , jeśli tworzysz nowy plik ochrony punktu końcowego, lub **zapisz** , jeśli edytujesz istniejący plik.

#### <a name="endpoint-security-policy"></a>Zasady zabezpieczeń punktu końcowego

1. Wybierz pozycję **Redukcja obszaru ataków** zabezpieczeń \> **punktu końcowego**. Wybierz istniejącą regułę usługi ASR lub utwórz nową. Aby utworzyć nowy, wybierz pozycję **Utwórz zasady** i wprowadź informacje dotyczące tego profilu. W polu **Typ profilu** wybierz pozycję **Reguły zmniejszania obszaru ataków**. Jeśli wybrano istniejący profil, wybierz pozycję **Właściwości** , a następnie wybierz pozycję **Ustawienia**.

2. W okienku **Ustawienia konfiguracji** wybierz pozycję **Zmniejszanie obszaru podatnego na ataki** , a następnie wybierz odpowiednie ustawienie dla każdej reguły usługi ASR.

3. W obszarze **Lista dodatkowych folderów, które muszą być chronione**, **lista aplikacji, które mają dostęp do folderów chronionych**, oraz **Wyklucz pliki i ścieżki z reguł zmniejszania obszaru ataków** wprowadź poszczególne pliki i foldery. Możesz również wybrać pozycję **Importuj** , aby zaimportować plik CSV zawierający pliki i foldery do wykluczenia z reguł usługi ASR. Każdy wiersz w pliku CSV powinien być sformatowany w następujący sposób:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Wybierz pozycję **Dalej** w trzech okienkach konfiguracji, a następnie wybierz pozycję **Utwórz** , jeśli tworzysz nowe zasady, lub **Zapisz** , jeśli edytujesz istniejące zasady.

### <a name="mem"></a>MEM

Aby skonfigurować niestandardowe reguły usługi ASR, możesz użyć identyfikatora OMA-URI firmy Microsoft Endpoint Manager (MEM). W poniższej procedurze użyto reguły [Blokuj wykorzystywanie wykorzystywanych, narażonych na zagrożenia podpisanych sterowników](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) .

1. Otwórz centrum administracyjne usługi Microsoft Endpoint Manager (MEM). W menu **Narzędzia główne** kliknij pozycję  **Urządzenia**, wybierz pozycję **Profile konfiguracji**, a następnie kliknij pozycję **Utwórz profil**.

   > [!div class="mx-imgBorder"]
   >  :::image type="content" source="images/mem01-create-profile.png" alt-text="Strona Tworzenie profilu w portalu centrum administracyjnego firmy Microsoft Endpoint Manager" lightbox="images/mem01-create-profile.png":::

2. W **obszarze Tworzenie profilu** na następujących dwóch listach rozwijanych wybierz następujące pozycje:

   - W **obszarze Platforma** wybierz **pozycję Windows 10 i nowsze**
   - W **obszarze Typ profilu** wybierz pozycję **Szablony**
   - Jeśli reguły usługi ASR są już ustawione za pomocą zabezpieczeń punktu końcowego, w **polu Typ profilu** wybierz pozycję **Katalog ustawień**.

   Wybierz pozycję **Niestandardowe**, a następnie wybierz pozycję **Utwórz**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem02-profile-attributes.png" alt-text="Atrybuty profilu reguły w portalu centrum administracyjnego firmy Microsoft Endpoint Manager" lightbox="images/mem02-profile-attributes.png":::

3. Zostanie otwarte narzędzie Szablon **niestandardowy w kroku 1 Podstawy**. W **obszarze 1 Podstawy** w polu **Nazwa** wpisz nazwę szablonu, a w **polu Opis** możesz wpisać opis (opcjonalnie).

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem03-1-basics.png" alt-text="Podstawowe atrybuty w portalu centrum administracyjnego Endpoint Manager firmy Microsoft" lightbox="images/mem03-1-basics.png":::

4. Kliknij **Dalej**. Zostanie otwarty krok **2. Ustawienia konfiguracji** . W obszarze Ustawienia OMA-URI kliknij pozycję **Dodaj**. Zostaną wyświetlone dwie opcje: **Dodaj** i **eksportuj**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem04-2-configuration-settings.png" alt-text="Ustawienia konfiguracji w portalu centrum administracyjnego usługi Microsoft Endpoint Manager" lightbox="images/mem04-2-configuration-settings.png":::

5. Kliknij ponownie **pozycję Dodaj** . Zostanie otwarte **okno Dodawanie ustawień OMA-URI wiersza** . W **obszarze Dodaj wiersz** wykonaj następujące czynności:

   - W **polu Nazwa** wpisz nazwę reguły.
   - W **polu Opis** wpisz krótki opis.
   - W **polu OMA-URI** wpisz lub wklej określony link OMA-URI dla dodawanej reguły. Zapoznaj się z sekcją MDM w tym artykule, aby uzyskać identyfikator OMA-URI, aby użyć tej przykładowej reguły. Aby uzyskać identyfikatory GUID reguły zmniejszania obszaru [ataków, zobacz Opisy reguł w temacie: Reguły](attack-surface-reduction-rules-reference.md#per-rule-descriptions) zmniejszania obszaru podatnego na ataki.
   - W **obszarze Typ danych** wybierz pozycję **Ciąg**.
   - W **polu Wartość** wpisz lub wklej wartość identyfikatora GUID, \= znak i wartość State bez spacji (_GUID=StateValue_). Gdzie:

     - 0: Wyłącz (Wyłącz regułę USŁUGI ASR)
     - 1: Blokuj (włącz regułę ASR)
     - 2: Inspekcja (oceń wpływ reguły ASR na organizację, jeśli zostanie włączona)
     - 6: Ostrzegaj (włącz regułę usługi ASR, ale zezwala użytkownikowi końcowemu na obejście bloku)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem05-add-row-oma-uri.png" alt-text="Konfiguracja identyfikatora URI OMA w portalu centrum administracyjnego firmy Microsoft Endpoint Manager" lightbox="images/mem05-add-row-oma-uri.png":::

6. Wybierz **Zapisz**. **Dodaj zamknięcie wiersza** . W **obszarze Niestandardowe** wybierz pozycję **Dalej**. W kroku **3 Tagi zakresu** tagi zakresu są opcjonalne. Wykonaj jeden z następujących kroków:

   - Wybierz **pozycję Wybierz tagi zakresu**, wybierz tag zakresu (opcjonalnie), a następnie wybierz pozycję **Dalej**.
   - Możesz też wybrać pozycję **Dalej**

7. W kroku **4 Przypisania** w **obszarze Dołączone grupy** dla grup, które mają być stosowane przez tę regułę, wybierz jedną z następujących opcji:

   - **Dodawanie grup**
   - **Dodawanie wszystkich użytkowników**
   - **Dodawanie wszystkich urządzeń**

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem06-4-assignments.png" alt-text="Przypisania w portalu centrum administracyjnego firmy Microsoft Endpoint Manager" lightbox="images/mem06-4-assignments.png":::

8. W **obszarze Wykluczone grupy** wybierz wszystkie grupy, które chcesz wykluczyć z tej reguły, a następnie wybierz pozycję **Dalej**.

9. W kroku **5 Reguły stosowania** dla następujących ustawień wykonaj następujące czynności:

   - W **obszarze Reguła** wybierz pozycję **Przypisz profil, jeśli** lub **Nie przypisuj profilu, jeśli**
   - W **obszarze Właściwość** wybierz właściwość, do której ma zostać zastosowana ta reguła
   - W **polu Wartość** wprowadź odpowiednią wartość lub zakres wartości

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem07-5-applicability-rules.png" alt-text="Reguły stosowania w portalu centrum administracyjnego firmy Microsoft Endpoint Manager" lightbox="images/mem07-5-applicability-rules.png":::

10. Wybierz pozycję **Dalej**. W kroku **6 Przejrzyj i utwórz** przejrzyj wybrane i wprowadzone ustawienia oraz informacje, a następnie wybierz pozycję **Utwórz**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mem08-6-review-create.png" alt-text="Opcja Przeglądanie i tworzenie w portalu centrum administracyjnego firmy Microsoft Endpoint Manager" lightbox="images/mem08-6-review-create.png":::

    > [!NOTE]
    > Reguły są aktywne i działają w ciągu kilku minut.

> [!NOTE]
> Obsługa konfliktów:
>
> Jeśli przypiszesz urządzeniu dwie różne zasady usługi ASR, sposób obsługi konfliktu to reguły, do których przypisano różne stany, nie istnieje żadne zarządzanie konfliktami, a wynik jest błędem.
>
> Reguły nie powodujące konfliktu nie spowodują błędu, a reguła zostanie zastosowana poprawnie. W rezultacie zostanie zastosowana pierwsza reguła, a kolejne reguły nie powodujące konfliktu zostaną scalone z zasadami.

### <a name="mdm"></a>MDM

Użyj dostawcy [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) configuration service provider (CSP), aby indywidualnie włączyć i ustawić tryb dla każdej reguły.

Poniżej przedstawiono przykład do celów referencyjnych z użyciem wartości GUID dla [odwołania do reguł zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

Wartości, które należy włączyć (blokuj), wyłączyć, ostrzec lub włączyć w trybie inspekcji, to:

- 0: Wyłącz (Wyłącz regułę USŁUGI ASR)
- 1: Blokuj (włącz regułę ASR)
- 2: Inspekcja (oceń wpływ reguły ASR na organizację, jeśli zostanie włączona)
- 6: Ostrzegaj (włącz regułę usługi ASR, ale zezwala użytkownikowi końcowemu na obejście bloku). Tryb ostrzeżenia jest dostępny dla większości reguł usługi ASR.

Aby dodać wykluczenia, użyj dostawcy usługi konfiguracji [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) .

Przykład:

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> Pamiętaj, aby wprowadzić wartości OMA-URI bez spacji.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. W programie Microsoft Endpoint Configuration Manager przejdź do pozycji **Zasoby i zgodność**\>**Ochrona punktu końcowego**\>**Windows Defender Exploit Guard**.

2. Wybierz pozycję **Narzędzia główne** \> **Utwórz zasady Exploit Guard Policy**.

3. Wprowadź nazwę i opis, wybierz pozycję **Zmniejszanie obszaru podatnego na ataki**, a następnie wybierz pozycję **Dalej**.

4. Wybierz reguły, które będą blokować lub przeprowadzać inspekcję akcji, a następnie wybierz pozycję **Dalej**.

5. Przejrzyj ustawienia i wybierz pozycję **Dalej** , aby utworzyć zasady.

6. Po utworzeniu zasad wybierz pozycję **Zamknij**.

### <a name="group-policy"></a>Zasady grupy

> [!WARNING]
> Jeśli zarządzasz komputerami i urządzeniami przy użyciu Intune, Configuration Manager lub innej platformy zarządzania na poziomie przedsiębiorstwa, oprogramowanie do zarządzania zastąpi wszelkie powodujące konflikt ustawienia zasady grupy podczas uruchamiania.

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](https://technet.microsoft.com/library/cc731212.aspx), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i wybierz pozycję **Szablony administracyjne**.

3. Rozwiń drzewo do **składników** \> systemu Windows **Program antywirusowy** \> **Microsoft Defender Microsoft Defender Exploit Guard** \> **— redukcja obszaru ataków**.

4. Wybierz pozycję **Konfiguruj reguły zmniejszania obszaru podatnego na ataki** i wybierz pozycję **Włączone**. Następnie możesz ustawić indywidualny stan dla każdej reguły w sekcji opcje. Wybierz pozycję **Pokaż...** i wprowadź identyfikator reguły w kolumnie **Nazwa wartości** i wybrany stan w kolumnie **Value** w następujący sposób:

   - 0: Wyłącz (Wyłącz regułę USŁUGI ASR)
   - 1: Blokuj (włącz regułę ASR)
   - 2: Inspekcja (oceń wpływ reguły ASR na organizację, jeśli zostanie włączona)
   - 6: Ostrzegaj (włącz regułę usługi ASR, ale zezwala użytkownikowi końcowemu na obejście bloku)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="Reguły usługi ASR w zasady grupy" lightbox="images/asr-rules-gp.png":::

5. Aby wykluczyć pliki i foldery z reguł usługi ASR, wybierz ustawienie **Wyklucz pliki i ścieżki z reguł zmniejszania obszaru ataków** i ustaw opcję **Włączone**. Wybierz pozycję **Pokaż** i wprowadź każdy plik lub folder w kolumnie **Nazwa wartości** . Wprowadź **wartość 0** w kolumnie **Wartość** dla każdego elementu.

   > [!WARNING]
   > Nie używaj cudzysłowów, ponieważ nie są one obsługiwane w kolumnie **Nazwa wartości** ani w kolumnie **Wartość** .

### <a name="powershell"></a>PowerShell

> [!WARNING]
> Jeśli zarządzasz komputerami i urządzeniami przy użyciu Intune, Configuration Manager lub innej platformy zarządzania na poziomie przedsiębiorstwa, oprogramowanie do zarządzania zastąpi wszelkie sprzeczne ustawienia programu PowerShell podczas uruchamiania. Aby umożliwić użytkownikom definiowanie wartości przy użyciu programu PowerShell, użyj opcji "Zdefiniowane przez użytkownika" dla reguły na platformie zarządzania.
> "Zdefiniowane przez użytkownika" umożliwia administratorowi lokalnemu skonfigurowanie reguły.
> Ustawienie opcji Zdefiniowane przez użytkownika jest wyświetlane na poniższej ilustracji.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-user-defined.png" alt-text="Opcja Włącz dla zabezpieczeń poświadczeń" lightbox="images/asr-user-defined.png":::

1. Wpisz **program PowerShell** w menu Start, kliknij prawym przyciskiem myszy **Windows PowerShell** i wybierz pozycję **Uruchom jako administrator**.

2. Wpisz jedno z następujących poleceń cmdlet. (Aby uzyskać więcej szczegółów, takich jak identyfikator reguły, zapoznaj się z [dokumentacją reguł zmniejszania obszaru](attack-surface-reduction-rules-reference.md) ataków).

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    Aby włączyć reguły usługi ASR w trybie inspekcji, użyj następującego polecenia cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    Aby włączyć reguły usługi ASR w trybie ostrzeżenia, użyj następującego polecenia cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Warn
    ```

    Aby włączyć blokowanie przez usługę ASR nadużywania wykorzystywanych, narażonych na zagrożenia podpisanych sterowników, użyj następującego polecenia cmdlet:

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    Aby wyłączyć reguły usługi ASR, użyj następującego polecenia cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > Należy określić stan indywidualnie dla każdej reguły, ale można łączyć reguły i stany na liście rozdzielonej przecinkami.
    >
    > W poniższym przykładzie zostaną włączone dwie pierwsze reguły, trzecia reguła zostanie wyłączona, a czwarta reguła zostanie włączona w trybie inspekcji:
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    Możesz również użyć czasownika `Add-MpPreference` programu PowerShell, aby dodać nowe reguły do istniejącej listy.

    > [!WARNING]
    > `Set-MpPreference` Zawsze zastąpi istniejący zestaw reguł. Jeśli chcesz dodać do istniejącego zestawu, użyj zamiast tego.`Add-MpPreference`
    > Listę reguł i ich bieżącego stanu można uzyskać za pomocą polecenia `Get-MpPreference`.

3. Aby wykluczyć pliki i foldery z reguł usługi ASR, użyj następującego polecenia cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Nadal używaj polecenia `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` , aby dodać więcej plików i folderów do listy.

    > [!IMPORTANT]
    > Służy `Add-MpPreference` do dołączania lub dodawania aplikacji do listy. `Set-MpPreference` Użycie polecenia cmdlet spowoduje zastąpienie istniejącej listy.

## <a name="related-articles"></a>Powiązane artykuły:

- [Dokumentacja reguł zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md)
- [Ocena redukcji obszaru ataków](evaluate-attack-surface-reduction.md)
- [Zmniejszanie obszaru podatnego na ataki — często zadawane pytania](attack-surface-reduction.md)
