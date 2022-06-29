---
title: Konfigurowanie i konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender planu 1
description: Dowiedz się, jak skonfigurować i skonfigurować usługę Defender for Endpoint Plan 1. Przejrzyj wymagania, zaplanuj wdrożenie i skonfiguruj środowisko.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e94a0ee04d45e92d5891c73ba3a70ac2f05cd482
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485962"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1"></a>Konfigurowanie i konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender planu 1

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W tym artykule opisano sposób konfigurowania i konfigurowania usługi Defender for Endpoint Plan 1. Niezależnie od tego, czy masz pomoc, czy robisz to samodzielnie, możesz użyć tego artykułu jako przewodnika po całym wdrożeniu.  

## <a name="the-setup-and-configuration-process"></a>Proces konfiguracji i konfiguracji

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Konfigurowanie i wdrażanie przepływu dla planu Ochrona punktu końcowego w usłudze Microsoft Defender 1" lightbox="images/mde-p1-deploymentflow.png":::

Ogólny proces konfiguracji i konfiguracji usługi Defender for Endpoint Plan 1 jest następujący: <br/><br/>


| Numer  | Krok  | Opis  |
|:---------:|:---------|:---------|
| 1 | [Przejrzyj wymagania](#review-the-requirements)  | Wyświetla listę wymagań dotyczących licencjonowania, przeglądarki, systemu operacyjnego i centrum danych   |
| 2 | [Planowanie wdrożenia](#plan-your-deployment) | Wyświetla listę kilku metod wdrażania do rozważenia i zawiera linki do większej liczby zasobów, które pomogą Ci zdecydować, która metoda ma być używana  |
| 3 | [Konfigurowanie środowiska dzierżawy](#set-up-your-tenant-environment) | Wyświetla listę zadań dotyczących konfigurowania środowiska dzierżawy |
| 4 | [Przypisywanie ról i uprawnień](#assign-roles-and-permissions) | Wyświetla listę ról i uprawnień do rozważenia dla zespołu ds. zabezpieczeń <br/><br/>**PORADA**: Po przypisaniu ról i uprawnień zespół ds. zabezpieczeń może rozpocząć pracę przy użyciu portalu Microsoft 365 Defender. Aby dowiedzieć się więcej, zobacz [Wprowadzenie](mde-plan1-getting-started.md). |
| 5 | [Dołączanie do usługi Defender dla punktu końcowego](#onboard-to-defender-for-endpoint) | Wyświetla listę kilku metod dołączania do usługi Defender for Endpoint Plan 1 przez system operacyjny i zawiera linki do bardziej szczegółowych informacji dla każdej metody  |
| 6 | [Konfigurowanie ochrony nowej generacji](#configure-next-generation-protection) | Opis sposobu konfigurowania ustawień ochrony nowej generacji w usłudze Microsoft Endpoint Manager  |
| 7 | [Konfigurowanie możliwości zmniejszania obszaru ataków](#configure-your-attack-surface-reduction-capabilities)        | Zawiera listę typów możliwości zmniejszania obszaru ataków, które można skonfigurować i zawiera procedury z linkami do większej liczby zasobów  |
 
## <a name="review-the-requirements"></a>Przejrzyj wymagania

W poniższej tabeli wymieniono podstawowe wymagania dotyczące usługi Defender for Endpoint Plan 1:<br/><br/>

| Wymóg | Opis |
|:---|:---|
| Wymagania dotyczące licencjonowania | Defender for Endpoint Plan 1 (autonomiczny lub jako część Microsoft 365 E3 lub A3) |
| Wymagania przeglądarki | Microsoft Edge <br/> Internet Explorer w wersji 11 <br/> Google Chrome |
| Systemy operacyjne | Windows 11 lub Windows 10 w wersji 1709 lub nowszej <br/>macOS (obsługiwane są trzy najnowsze wersje) <br/>iOS <br/>System operacyjny Android <br/><br/>Należy pamiętać, że autonomiczna wersja usługi Defender for Endpoint Plan 1 nie zawiera licencji serwera. Aby dołączyć serwery, musisz mieć usługę Defender for Servers Plan 1 lub Plan 2 w ramach [oferty usługi Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . Aby dowiedzieć się więcej. zobacz [Omówienie usługi Microsoft Defender dla serwerów](/azure/defender-for-cloud/defender-for-servers-introduction). |
| Datacenter | Jedna z następujących lokalizacji centrum danych: <br/>- Unia Europejska <br/>- Zjednoczone Królestwo <br/>- Stany Zjednoczone |


## <a name="plan-your-deployment"></a>Planowanie wdrożenia

Podczas planowania wdrożenia można wybrać jedną z kilku różnych architektur i metod wdrażania. Każda organizacja jest unikatowa, więc masz kilka opcji do rozważenia, jak wymieniono w poniższej tabeli: <br/><br/>

| Metoda | Opis |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (zawarte w Endpoint Manager firmy Microsoft) | Zarządzanie punktami końcowymi w środowisku natywnym chmury przy użyciu Intune |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Configuration Manager](/mem/configmgr/core/understand/introduction) (zawarte w usłudze Microsoft Endpoint Manager) | Zarządzanie punktami końcowymi i obciążeniami obejmującymi środowisko lokalne i w chmurze przy użyciu Intune i Configuration Manager |
| [Menedżer konfiguracji](/mem/configmgr/core/understand/introduction) | Używanie Configuration Manager do ochrony lokalnych punktów końcowych przy użyciu opartej na chmurze mocy usługi Defender for Endpoint |
| Skrypt lokalny pobrany z portalu Microsoft 365 Defender | Używanie skryptów lokalnych w punktach końcowych do uruchamiania pilotażu lub dołączania tylko kilku urządzeń |

Aby dowiedzieć się więcej na temat opcji wdrażania, zobacz [Planowanie wdrożenia usługi Defender for Endpoint](deployment-strategy.md). Pobierz następujący plakat: 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Miniatura plakatu strategii wdrażania":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)

**[Pobieranie plakatu wdrożenia](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)**

> [!TIP]
> Aby uzyskać bardziej szczegółowe informacje na temat planowania wdrożenia, zobacz [Planowanie wdrożenia Ochrona punktu końcowego w usłudze Microsoft Defender](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Konfigurowanie środowiska dzierżawy

Konfigurowanie środowiska dzierżawy obejmuje zadania, takie jak:

- Weryfikowanie licencji
- Konfigurowanie dzierżawy
- Konfigurowanie ustawień serwera proxy (tylko w razie potrzeby)
- Upewnianie się, że czujniki działają prawidłowo i raportują dane do usługi Defender for Endpoint 

Te zadania są uwzględniane w fazie konfiguracji usługi Defender dla punktu końcowego. Zobacz [Konfigurowanie usługi Defender dla punktu końcowego](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Przypisywanie ról i uprawnień

Aby uzyskać dostęp do portalu Microsoft 365 Defender, skonfiguruj ustawienia usługi Defender dla punktu końcowego lub wykonaj zadania, takie jak wykonywanie akcji reagowania na wykryte zagrożenia, należy przypisać odpowiednie uprawnienia. Usługa Defender for Endpoint używa [wbudowanych ról w usłudze Azure Active Directory](/azure/active-directory/roles/permissions-reference). 

Firma Microsoft zaleca przypisanie użytkownikom tylko poziomu uprawnień potrzebnych do wykonywania zadań. Uprawnienia można przypisać przy użyciu podstawowego zarządzania uprawnieniami lub przy użyciu [kontroli dostępu opartej na rolach](rbac.md) (RBAC). 

- W przypadku podstawowego zarządzania uprawnieniami administratorzy globalni i administratorzy zabezpieczeń mają pełny dostęp, natomiast czytelnicy zabezpieczeń mają dostęp tylko do odczytu.
- Za pomocą kontroli dostępu opartej na rolach można ustawić bardziej szczegółowe uprawnienia za pomocą większej liczby ról. Na przykład możesz mieć czytniki zabezpieczeń, operatory zabezpieczeń, administratorów zabezpieczeń, administratorów punktów końcowych i nie tylko.


W poniższej tabeli opisano kluczowe role, które należy wziąć pod uwagę w przypadku usługi Defender for Endpoint w organizacji: <br/><br/>

| Rola | Opis |
|:---|:---|
| Administratorzy globalni (nazywani również administratorami globalnymi) <br/><br/> *Najlepszym rozwiązaniem jest ograniczenie liczby administratorów globalnych.* | Administratorzy globalni mogą wykonywać różnego rodzaju zadania. Osoba, która utworzyła firmę na platformie Microsoft 365 lub w Ochrona punktu końcowego w usłudze Microsoft Defender planie 1, jest domyślnie administratorem globalnym. <br/><br/> Administratorzy globalni mogą uzyskiwać dostęp do/zmieniać ustawienia we wszystkich portalach platformy Microsoft 365, takich jak: <br/>- Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>— portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>— Centrum administracyjne usługi Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  |
| Administratorzy zabezpieczeń (nazywani również administratorami zabezpieczeń) | Administratorzy zabezpieczeń mogą wykonywać zadania operatora zabezpieczeń oraz następujące zadania: <br/>— Monitorowanie zasad związanych z zabezpieczeniami <br/>— Zarządzanie zagrożeniami i alertami bezpieczeństwa <br/>— Wyświetlanie raportów |
| Operator zabezpieczeń | Operatory zabezpieczeń mogą wykonywać zadania czytnika zabezpieczeń oraz następujące zadania: <br/>— Wyświetlanie informacji o wykrytych zagrożeniach <br/>- Badanie wykrytych zagrożeń i reagowanie na nie  |
| Czytelnik zabezpieczeń | Czytelnicy zabezpieczeń mogą wykonywać następujące zadania: <br/>— Wyświetlanie zasad związanych z zabezpieczeniami w usługach Microsoft 365 <br/>— Wyświetlanie zagrożeń i alertów związanych z zabezpieczeniami <br/>— Wyświetlanie raportów  |


> [!TIP]
> Aby dowiedzieć się więcej na temat ról w usłudze Azure Active Directory, zobacz [Przypisywanie ról administratora i nieadministratora do użytkowników za pomocą usługi Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Więcej informacji na temat ról usługi Defender for Endpoint można znaleźć w temacie [Kontrola dostępu oparta na rolach](prepare-deployment.md#role-based-access-control).

## <a name="onboard-to-defender-for-endpoint"></a>Dołączanie do usługi Defender dla punktu końcowego

Gdy wszystko będzie gotowe do dołączenia punktów końcowych organizacji, możesz wybrać jedną z kilku metod, jak pokazano w poniższej tabeli: <br/><br/>

|System operacyjny punktu końcowego | Metody dołączania|
|---|---|
| Windows 10 | [Skrypt lokalny (maksymalnie 10 urządzeń)](configure-endpoints-script.md) <br>  [Zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobile Menedżer urządzeń](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md)  |
| macOS | [Skrypty lokalne](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Zarządzanie urządzeniami mobilne](mac-install-with-other-mdm.md) |
| iOS |[Oparte na aplikacji](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Następnie przejdź do konfigurowania funkcji ochrony następnej generacji i zmniejszania obszaru ataków.

## <a name="configure-next-generation-protection"></a>Konfigurowanie ochrony nowej generacji

Zalecamy zarządzanie urządzeniami i ustawieniami zabezpieczeń organizacji przy użyciu usługi [Microsoft Endpoint Manager](/mem), jak pokazano na poniższej ilustracji:
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Zasady zabezpieczeń punktu końcowego w portalu micorosft Endpoint Manager" lightbox="../../media/mde-p1/endpoint-policies.png":::

Aby skonfigurować ochronę nowej generacji w usłudze Microsoft Endpoint Manager, wykonaj następujące kroki:

1. Przejdź do centrum administracyjnego microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Program antywirusowy** zabezpieczeń  > **punktu końcowego**, a następnie wybierz istniejące zasady. (Jeśli nie masz istniejących zasad, utwórz nowe zasady).

3. Ustaw lub zmień ustawienia konfiguracji programu antywirusowego. Potrzebujesz pomocy? Zapoznaj się z następującymi zasobami: <br/>

   - [Ustawienia Windows 10 zasad ochrony antywirusowej Microsoft Defender w Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu iOS](ios-configure-features.md)

4. Po zakończeniu określania ustawień wybierz pozycję **Przejrzyj i zapisz**.

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Konfigurowanie możliwości zmniejszania obszaru ataków

Zmniejszenie obszaru podatnego na ataki polega na zmniejszeniu liczby miejsc i sposobów, w jakie organizacja jest otwarta na ataki. Usługa Defender for Endpoint Plan 1 zawiera kilka funkcji i możliwości, które ułatwiają ograniczenie obszarów ataków w punktach końcowych. Te funkcje i możliwości są wymienione w poniższej tabeli: <br/><br/>

| Funkcja/funkcja | Opis |
|:---|:---|
| [Reguły zmniejszania obszaru podatnego na ataki](#attack-surface-reduction-rules) | Skonfiguruj reguły zmniejszania obszaru ataków, aby ograniczyć ryzykowne zachowania oparte na oprogramowaniu i zapewnić bezpieczeństwo organizacji. Reguły zmniejszania obszaru ataków dotyczą pewnych zachowań oprogramowania, takich jak<br/>— Uruchamianie plików wykonywalnych i skryptów, które próbują pobrać lub uruchomić pliki <br/>— Uruchamianie zaciemnionych lub w inny sposób podejrzanych skryptów <br/>- Wykonywanie zachowań, które aplikacje zwykle nie inicjują podczas normalnej codziennej pracy <br/><br/>Takie zachowania oprogramowania są czasami widoczne w legalnych aplikacjach. Jednak te zachowania są często uważane za ryzykowne, ponieważ są często nadużywane przez osoby atakujące za pośrednictwem złośliwego oprogramowania.  |
| [Ograniczanie ryzyka wymuszania okupu](#ransomware-mitigation) | Skonfiguruj środki zaradcze wymuszające okup, konfigurując kontrolowany dostęp do folderów, co pomaga chronić cenne dane organizacji przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. | 
| [Sterowanie urządzeniem](#device-control) | Skonfiguruj ustawienia sterowania urządzeniami dla organizacji, aby zezwalać na urządzenia wymienne lub blokować je (np. dyski USB). | 
| [Ochrona sieci](#network-protection) | Skonfiguruj ochronę sieci, aby uniemożliwić osobom w organizacji korzystanie z aplikacji uzyskujących dostęp do niebezpiecznych domen lub złośliwej zawartości w Internecie. |
| [Ochrona sieci Web](#web-protection) | Skonfiguruj ochronę przed zagrożeniami internetowymi, aby chronić urządzenia organizacji przed witrynami wyłudzającymi informacje, witrynami wykorzystującymi luki w zabezpieczeniach i innymi niezaufanymi witrynami o niskiej reputacji. Skonfiguruj filtrowanie zawartości internetowej w celu śledzenia i regulowania dostępu do witryn internetowych na podstawie ich kategorii zawartości (takich jak wypoczynek, wysoka przepustowość, zawartość dla dorosłych lub odpowiedzialność prawna). |
| [Zapora sieciowa](#network-firewall) | Skonfiguruj zaporę sieciową przy użyciu reguł określających, który ruch sieciowy może pochodzić z urządzeń organizacji lub z nich wychodzić. |
| [Kontrola aplikacji](#application-control)  | Skonfiguruj reguły kontroli aplikacji, jeśli chcesz zezwolić na uruchamianie tylko zaufanych aplikacji i procesów na urządzeniach z systemem Windows.    |

### <a name="attack-surface-reduction-rules"></a>Reguły zmniejszania obszaru podatnego na ataki

Reguły zmniejszania obszaru ataków są dostępne na urządzeniach z systemem Windows. Zalecamy korzystanie z usługi Microsoft Endpoint Manager, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Reguły zmniejszania obszaru ataków w portalu microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Przejdź do centrum administracyjnego microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz **pozycję Redukcja** >  **obszaru ataków** zabezpieczeń  >  punktu końcowego **+ Utwórz zasady**.

3. W obszarze **Platforma** wybierz **pozycję Windows 10 i nowsze**.

4. W obszarze **Profil** wybierz pozycję **Reguły zmniejszania obszaru podatnego na ataki**, a następnie wybierz pozycję **Utwórz**.

5. Na **karcie Podstawy** określ nazwę i opis zasad, a następnie wybierz pozycję **Dalej**.

6. Na **karcie Ustawienia konfiguracji** rozwiń węzeł **Reguły zmniejszania obszaru podatnego na ataki**.

7. Określ ustawienia dla każdej reguły, a następnie wybierz pozycję **Dalej**. (Aby uzyskać więcej informacji o tym, co robi każda reguła, zobacz [Reguły zmniejszania obszaru ataków](attack-surface-reduction.md)). 

8. Na karcie **Tagi zakresu** , jeśli organizacja używa tagów zakresu, wybierz **pozycję + Wybierz tagi zakresu**, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz pozycję **Dalej**. 
   
   Aby dowiedzieć się więcej na temat tagów zakresu, zobacz [Używanie kontroli dostępu opartej na rolach (RBAC) i tagów zakresu dla rozproszonej infrastruktury IT](/mem/intune/fundamentals/scope-tags).

9. Na **karcie Przypisania** określ użytkowników i grupy, do których mają być stosowane zasady, a następnie wybierz pozycję **Dalej**. (Aby dowiedzieć się więcej na temat przypisań, zobacz [Przypisywanie profilów użytkowników i urządzeń w Microsoft Intune](/mem/intune/configuration/device-profile-assign)).

10. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia, a następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Aby dowiedzieć się więcej na temat reguł zmniejszania obszaru ataków, zobacz następujące zasoby:
> - [Używanie reguł zmniejszania obszaru ataków w celu zapobiegania infekcji złośliwym oprogramowaniem](attack-surface-reduction.md)
> - [Wyświetlanie listy reguł zmniejszania obszaru ataków](attack-surface-reduction-rules-reference.md)
> - [Wdrażanie reguł zmniejszania obszaru ataków — krok 3: implementowanie reguł usługi ASR](attack-surface-reduction-rules-deployment-implement.md)

### <a name="ransomware-mitigation"></a>Ograniczanie ryzyka wymuszania okupu

Ograniczanie ryzyka wymuszania okupu odbywa się za pośrednictwem [kontrolowanego dostępu do folderów](controlled-folders.md#what-is-controlled-folder-access), co umożliwia tylko zaufanym aplikacjom dostęp do chronionych folderów w punktach końcowych. 

Zalecamy skonfigurowanie kontrolowanego dostępu do folderów przy użyciu usługi Microsoft Endpoint Manager.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Zasady usługi ASR w portalu microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Przejdź do centrum administracyjnego microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się. 

2. Wybierz pozycję **Zabezpieczenia punktu końcowego**, a następnie wybierz pozycję **Zmniejszanie obszaru podatnego na ataki**.

3. Wybierz **pozycję + Utwórz zasady**. 

4. W obszarze **Platforma** wybierz pozycję **Windows 10 i nowsze**, a w polu **Profil** wybierz pozycję **Reguły zmniejszania obszaru ataków**. Następnie wybierz pozycję **Utwórz**. 

5. Na **karcie Podstawy** nadaj zasadom nazwę i dodaj opis. Wybierz pozycję **Dalej**. 

6. Na **karcie Ustawienia konfiguracji** w sekcji **Reguły zmniejszania obszaru podatnego na ataki** przewiń w dół do dołu. Na liście rozwijanej **Włącz ochronę folderów** wybierz pozycję **Włącz**. Opcjonalnie można określić następujące inne ustawienia:

   - Obok pozycji **Lista dodatkowych folderów, które muszą być chronione**, wybierz menu rozwijane, a następnie dodaj foldery, które muszą być chronione.
   - Obok pozycji **Lista aplikacji, które mają dostęp do folderów chronionych**, wybierz menu rozwijane, a następnie dodaj aplikacje, które powinny mieć dostęp do chronionych folderów.
   - Obok pozycji **Wyklucz pliki i ścieżki z reguł zmniejszania obszaru ataków** wybierz menu rozwijane, a następnie dodaj pliki i ścieżki, które należy wykluczyć z reguł zmniejszania obszaru ataków.

   Następnie wybierz pozycję **Dalej**.

7. Na karcie **Tagi zakresu** , jeśli organizacja używa tagów zakresu, wybierz **pozycję + Wybierz tagi zakresu**, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz pozycję **Dalej**. 
   
   Aby dowiedzieć się więcej na temat tagów zakresu, zobacz [Używanie kontroli dostępu opartej na rolach (RBAC) i tagów zakresu dla rozproszonej infrastruktury IT](/mem/intune/fundamentals/scope-tags).

8. Na **karcie Przypisania** wybierz pozycję **Dodaj wszystkich użytkowników** i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz alternatywnie określić określone grupy użytkowników lub urządzeń).

9. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**. Zasady zostaną zastosowane do wszystkich punktów końcowych, które zostały wkrótce dołączone do usługi Defender for Endpoint.

### <a name="device-control"></a>Kontrola urządzenia

Usługę Defender for Endpoint można skonfigurować tak, aby blokowała lub zezwalała na wymienne urządzenia i pliki na urządzeniach wymiennych. Zalecamy skonfigurowanie ustawień sterowania urządzeniami przy użyciu usługi Microsoft Endpoint Manager.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Szablony administracyjne Endpoint Manager firmy Microsoft" lightbox="../../media/mde-p1/mem-admintemplates.png":::

1. Przejdź do centrum administracyjnego microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się. 

2. Wybierz pozycję **Urządzenia** > **Profile konfiguracji** > **Utwórz profil**.

3. W obszarze **Platforma** wybierz pozycję **Windows 10 i nowsze**, a w polu **Typ profilu** wybierz pozycję **Szablony**. 

   W obszarze **Nazwa szablonu** wybierz pozycję **Szablony administracyjne**, a następnie wybierz pozycję **Utwórz**. 

4. Na **karcie Podstawy** nadaj zasadom nazwę i dodaj opis. Wybierz pozycję **Dalej**. 

5. Na **karcie Ustawienia konfiguracji** wybierz pozycję **Wszystkie ustawienia**. Następnie w polu wyszukiwania wpisz `Removable` , aby wyświetlić wszystkie ustawienia dotyczące urządzeń wymiennych.

6. Wybierz element z listy, na przykład **Wszystkie klasy magazynu wymiennego: Odmów wszystkim dostępom**, aby otworzyć okienko wysuwane. Wysuwane dla każdego ustawienia wyjaśnia, co się dzieje, gdy jest włączone, wyłączone lub nieskonfigurowane. Wybierz ustawienie, a następnie wybierz przycisk **OK**. 

7. Powtórz krok 6 dla każdego ustawienia, które chcesz skonfigurować. Następnie wybierz pozycję **Dalej**.

8. Na karcie **Tagi zakresu** , jeśli organizacja używa tagów zakresu, wybierz **pozycję + Wybierz tagi zakresu**, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz pozycję **Dalej**. 
   
   Aby dowiedzieć się więcej na temat tagów zakresu, zobacz [Używanie kontroli dostępu opartej na rolach (RBAC) i tagów zakresu dla rozproszonej infrastruktury IT](/mem/intune/fundamentals/scope-tags).

9. Na **karcie Przypisania** wybierz pozycję **Dodaj wszystkich użytkowników** i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz alternatywnie określić określone grupy użytkowników lub urządzeń).

10. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**. Zasady zostaną zastosowane do wszystkich punktów końcowych, które zostały wkrótce dołączone do usługi Defender for Endpoint.

> [!TIP]
> Aby uzyskać więcej informacji, zobacz [Jak kontrolować urządzenia USB i inne nośniki wymienne przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Ochrona sieci

Dzięki ochronie sieci możesz chronić organizację przed niebezpiecznymi domenami, które mogą hostować wyłudzanie informacji, luki w zabezpieczeniach i inną złośliwą zawartość w Internecie. Zalecamy włączenie ochrony sieci przy użyciu usługi Microsoft Endpoint Manager.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Profil programu Endpoint Protection w portalu microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-endpointprotectionprofile.png":::

1. Przejdź do centrum administracyjnego microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się. 

2. Wybierz pozycję **Urządzenia** > **Profile konfiguracji** > **Utwórz profil**.

3. W obszarze **Platforma** wybierz pozycję **Windows 10 i nowsze**, a w polu **Typ profilu** wybierz pozycję **Szablony**. 

   W obszarze **Nazwa szablonu** wybierz pozycję **Ochrona punktu końcowego**, a następnie wybierz pozycję **Utwórz**. 

4. Na **karcie Podstawy** nadaj zasadom nazwę i dodaj opis. Wybierz pozycję **Dalej**. 

5. Na **karcie Ustawienia konfiguracji** rozwiń węzeł **Microsoft Defender Exploit Guard**, a następnie rozwiń węzeł **Filtrowanie sieci**.

   Ustaw **opcję Ochrona sieci** na **Wartość Włącz**. (Możesz też wybrać opcję **Inspekcja** , aby zobaczyć, jak ochrona sieci będzie działać w twoim środowisku na początku).

   Następnie wybierz pozycję **Dalej**.

6. Na **karcie Przypisania** wybierz pozycję **Dodaj wszystkich użytkowników** i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz alternatywnie określić określone grupy użytkowników lub urządzeń).

7. Na karcie **Reguły stosowania** skonfiguruj regułę. Skonfigurowany profil będzie stosowany tylko do urządzeń spełniających określone połączone kryteria. 

   Na przykład można przypisać zasady do punktów końcowych, w których działa tylko określona wersja systemu operacyjnego.

   Następnie wybierz pozycję **Dalej**. 

8. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**. Zasady zostaną zastosowane do wszystkich punktów końcowych, które zostały wkrótce dołączone do usługi Defender for Endpoint.

> [!TIP]
> Aby włączyć ochronę sieci, można użyć innych metod, takich jak Windows PowerShell lub zasady grupy. Aby dowiedzieć się więcej, zobacz [Włączanie ochrony sieci](enable-network-protection.md).

### <a name="web-protection"></a>Ochrona sieci Web

Dzięki ochronie w Internecie można chronić urządzenia organizacji przed zagrożeniami internetowymi i niepożądaną zawartością. Ochrona w Internecie obejmuje [ochronę przed zagrożeniami internetowymi](#configure-web-threat-protection) i [filtrowanie zawartości internetowej](#configure-web-content-filtering). Skonfiguruj oba zestawy możliwości. Zalecamy skonfigurowanie ustawień ochrony sieci Web przy użyciu usługi Microsoft Endpoint Manager.

#### <a name="configure-web-threat-protection"></a>Konfigurowanie ochrony przed zagrożeniami internetowymi

1. Przejdź do centrum administracyjnego microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.
 
2. Wybierz pozycję **Zmniejszanie obszaru ataków** zabezpieczeń  > **punktu końcowego**, a następnie wybierz pozycję **+ Utwórz zasady**.

3. Wybierz platformę, taką jak **Windows 10 i nowsze**, wybierz profil **ochrony sieci Web**, a następnie wybierz pozycję **Utwórz**. 

4. Na **karcie Podstawy** określ nazwę i opis, a następnie wybierz pozycję **Dalej**.

5. Na karcie **Ustawienia konfiguracji** rozwiń węzeł **Web Protection**, określ ustawienia w poniższej tabeli, a następnie wybierz pozycję **Dalej**. <br/><br/>

   | Ustawienie | Zalecenie |
   |:---|:---|
   | **Włączanie ochrony sieci** | Ustaw wartość **Włączone**. Uniemożliwia użytkownikom odwiedzanie złośliwych witryn lub domen. <br/><br/>Alternatywnie można ustawić ochronę sieci na **tryb inspekcji** , aby zobaczyć, jak będzie działać w twoim środowisku. W trybie inspekcji ochrona sieci nie uniemożliwia użytkownikom odwiedzania witryn lub domen, ale śledzi wykrycia jako zdarzenia. |
   | **Wymagaj filtru SmartScreen dla Starsza wersja Microsoft Edge** | Ustaw wartość **Tak**. Pomaga chronić użytkowników przed potencjalnym wyłudzaniem informacji i złośliwym oprogramowaniem. |
   | **Blokuj dostęp do złośliwej witryny** | Ustaw wartość **Tak**. Uniemożliwia użytkownikom pomijanie ostrzeżeń dotyczących potencjalnie złośliwych witryn. |
   | **Blokuj pobieranie niezweryfikowanych plików** | Ustaw wartość **Tak**. Uniemożliwia użytkownikom pomijanie ostrzeżeń i pobieranie niezweryfikowanych plików. |

6. Na karcie **Tagi zakresu** , jeśli organizacja używa tagów zakresu, wybierz **pozycję + Wybierz tagi zakresu**, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz pozycję **Dalej**. 
   
   Aby dowiedzieć się więcej na temat tagów zakresu, zobacz [Używanie kontroli dostępu opartej na rolach (RBAC) i tagów zakresu dla rozproszonej infrastruktury IT](/mem/intune/fundamentals/scope-tags).

7. Na **karcie Przypisania** określ użytkowników i urządzenia, które mają otrzymywać zasady ochrony sieci Web, a następnie wybierz pozycję **Dalej**.

8. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Aby dowiedzieć się więcej na temat ochrony przed zagrożeniami [internetowymi, zobacz Ochrona organizacji przed zagrożeniami internetowymi](web-threat-protection.md).

#### <a name="configure-web-content-filtering"></a>Konfigurowanie filtrowania zawartości internetowej

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) i zaloguj się.

2. Wybierz pozycję **Ustawienia** > **Punkty końcowe**.

3. W obszarze **Reguły** wybierz pozycję **Filtrowanie zawartości sieci Web**, a następnie wybierz pozycję **+ Dodaj zasady**.

4. W menu wysuwnym **Dodawanie zasad** na karcie **Ogólne** określ nazwę zasad, a następnie wybierz pozycję **Dalej**.

5. W **obszarze Zablokowane kategorie** wybierz co najmniej jedną kategorię, którą chcesz zablokować, a następnie wybierz pozycję **Dalej**.

6. Na karcie **Zakres** wybierz grupy urządzeń, które chcesz otrzymać te zasady, a następnie wybierz pozycję **Dalej**.

7. Na karcie **Podsumowanie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Zapisz**.

> [!TIP]
> Aby dowiedzieć się więcej na temat konfigurowania filtrowania zawartości internetowej, zobacz [Filtrowanie zawartości sieci Web](web-content-filtering.md).

### <a name="network-firewall"></a>Zapora sieciowa

Zapora sieciowa pomaga zmniejszyć ryzyko zagrożeń bezpieczeństwa sieci. Twój zespół ds. zabezpieczeń może ustawić reguły określające, który ruch może przepływać do lub z urządzeń organizacji. Zalecamy skonfigurowanie zapory sieciowej przy użyciu usługi Microsoft Endpoint Manager. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Zasady zapory w portalu microsoft Endpoint Manager" lightbox="../../media/mde-p1/mem-firewallpolicy.png":::

Aby skonfigurować podstawowe ustawienia zapory, wykonaj następujące kroki:

1. Przejdź do centrum administracyjnego microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz pozycję **Zapora** zabezpieczeń  > **punktu końcowego**, a następnie wybierz pozycję **+ Utwórz zasady**.

3. Wybierz platformę, taką jak **Windows 10 i nowsze**, wybierz profil **Zapora Microsoft Defender**, a następnie wybierz pozycję **Utwórz**. 

4. Na **karcie Podstawy** określ nazwę i opis, a następnie wybierz pozycję **Dalej**.

5. Rozwiń **Zapora Microsoft Defender**, a następnie przewiń w dół do dołu listy.

6. Dla każdego z następujących ustawień ustaw wartość **Tak**:

   - **Włączanie Zapora Microsoft Defender dla sieci domenowych** 
   - **Włączanie Zapora Microsoft Defender dla sieci prywatnych**
   - **Włączanie Zapora Microsoft Defender dla sieci publicznych**
   
   Przejrzyj listę ustawień w każdej z sieci domenowych, sieci prywatnych i sieci publicznych. Możesz pozostawić dla nich ustawienie **Nieskonfigurowane** lub zmienić je zgodnie z potrzebami organizacji.

   Następnie wybierz pozycję **Dalej**.

7. Na karcie **Tagi zakresu** , jeśli organizacja używa tagów zakresu, wybierz **pozycję + Wybierz tagi zakresu**, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz pozycję **Dalej**. 
   
   Aby dowiedzieć się więcej na temat tagów zakresu, zobacz [Używanie kontroli dostępu opartej na rolach (RBAC) i tagów zakresu dla rozproszonej infrastruktury IT](/mem/intune/fundamentals/scope-tags).

8. Na **karcie Przypisania** wybierz pozycję **Dodaj wszystkich użytkowników** i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz alternatywnie określić określone grupy użytkowników lub urządzeń).

9. Na karcie **Przeglądanie i tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Ustawienia zapory są szczegółowe i mogą wydawać się skomplikowane. Zapoznaj się z [tematem Najlepsze rozwiązania dotyczące konfigurowania Zapora Windows Defender](/windows/security/threat-protection/windows-firewall/best-practices-configuring).

### <a name="application-control"></a>Kontrola aplikacji

Windows Defender Application Control (WDAC) pomaga chronić punkty końcowe systemu Windows, zezwalając tylko na uruchamianie zaufanych aplikacji i procesów. Większość organizacji korzystała z wdrożenia etapowego usługi WDAC. Oznacza to, że większość organizacji na początku nie wdraża funkcji WDAC we wszystkich punktach końcowych systemu Windows. W rzeczywistości w zależności od tego, czy punkty końcowe systemu Windows w organizacji są w pełni zarządzane, lekko zarządzane, czy też punkty końcowe "Przynieś własne urządzenie", możesz wdrożyć usługę WDAC we wszystkich punktach końcowych lub w niektórych punktach końcowych.

Aby pomóc w planowaniu wdrożenia usługi WDAC, zobacz następujące zasoby:

- [Kontrola aplikacji dla systemu Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender decyzje dotyczące projektowania zasad kontroli aplikacji](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Windows Defender wdrożenie usługi Application Control w różnych scenariuszach: typy urządzeń](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Następne kroki

Po zakończeniu procesu konfiguracji i konfiguracji następnym krokiem jest rozpoczęcie korzystania z usługi Defender for Endpoint. 

- [Wprowadzenie do usługi Defender for Endpoint Plan 1](mde-plan1-getting-started.md)
