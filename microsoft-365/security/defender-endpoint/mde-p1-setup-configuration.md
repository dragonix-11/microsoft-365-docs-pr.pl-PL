---
title: Konfigurowanie i konfigurowanie usługi Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1
description: Dowiedz się, jak skonfigurować usługę Defender dla punktu końcowego (plan 1). Przejrzyj wymagania, zaplanuj swój projekt i skonfiguruj środowisko.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/14/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: e2a8f7166e1fa3a05b95b1a48dbf91b30ef34224
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470378"
---
# <a name="set-up-and-configure-microsoft-defender-for-endpoint-plan-1"></a>Konfigurowanie i konfigurowanie usługi Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

W tym artykule opisano, jak skonfigurować usługę Defender dla punktu końcowego (plan 1). Niezależnie od tego, czy korzystasz z pomocy, czy też samodzielnie to robisz, możesz użyć tego artykułu jako przewodnika podczas wdrażania.  

## <a name="the-setup-and-configuration-process"></a>Proces konfiguracji

:::image type="content" source="images/mde-p1-deploymentflow.png" alt-text="Konfigurowanie i przepływ wdrażania dla Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1" lightbox="images/mde-p1-deploymentflow.png":::

Proces konfiguracji ogólnej dla programu Defender dla punktu końcowego (plan 1) jest następujący: <br/><br/>


| Numer  | Krok  | Opis  |
|:---------:|:---------|:---------|
| 1 | [Przejrzyj wymagania](#review-the-requirements)  | Lista wymagań dotyczących licencjonowania, przeglądarki, systemu operacyjnego i centrum danych   |
| 2 | [Planowanie wdrożenia](#plan-your-deployment) | Lista kilku metod wdrażania do rozważenia oraz linki do większej liczby zasobów, które ułatwiają podjęcie decyzji, której metody użyć.  |
| 3 | [Konfigurowanie środowiska dzierżawy](#set-up-your-tenant-environment) | Lista zadań związanych z konfigurowaniem środowiska dzierżawcy |
| 4 | [Przypisywanie ról i uprawnień](#assign-roles-and-permissions) | Lista ról i uprawnień do rozważenia dla zespołu zabezpieczeń. <br/><br/>**PORADA**: Po przypisaniu ról i uprawnień Twój zespół zabezpieczeń może rozpocząć korzystanie z portalu Microsoft 365 Defender sieci. Aby dowiedzieć się więcej, zobacz [Wprowadzenie](mde-plan1-getting-started.md). |
| 5 | [Onboard to Defender for Endpoint](#onboard-to-defender-for-endpoint) | Lista kilku metod dołączanych przez system operacyjny do programu Defender dla punktu końcowego (plan 1) oraz linki do bardziej szczegółowych informacji dotyczących poszczególnych metod  |
| 6 | [Konfigurowanie ochrony następnej generacji](#configure-next-generation-protection) | W tym artykule opisano, jak skonfigurować ustawienia ochrony następnej generacji w programie Microsoft Endpoint Manager  |
| 7 | [Konfigurowanie możliwości zmniejszania powierzchni ataków](#configure-your-attack-surface-reduction-capabilities)        | Lista typów funkcji zmniejszania powierzchni ataków, które można skonfigurować i zawiera procedury z linkami do większej liczby zasobów.  |
 
## <a name="review-the-requirements"></a>Przejrzyj wymagania

W poniższej tabeli wymieniono podstawowe wymagania dotyczące usługi Defender dla punktu końcowego (plan 1):<br/><br/>

| Wymaganie | Opis |
|:---|:---|
| Wymagania dotyczące licencjonowania | Defender for Endpoint Plan 1 (dawniej nazywany Ochrona punktu końcowego w usłudze Microsoft Defender Lite)|
| Wymagania dotyczące przeglądarki | Microsoft Edge <br/> Internet Explorer w wersji 11 <br/> Google Chrome |
| Systemy operacyjne | Windows 10, wersja 1709 lub nowsza <br/>macOS: 11.5 (Big Sur), 10.15.7 (Catalina) lub 10.14.6 (Mojave) <br/>iOS <br/>System operacyjny Android  |
| Datacenter | Jedna z następujących lokalizacji centrów danych: <br/>- Unia Europejska <br/>— Zjednoczone Królestwo <br/>— Stany Zjednoczone |


## <a name="plan-your-deployment"></a>Planowanie wdrożenia

Podczas planowania wdrożenia możesz wybrać jedną z kilku różnych architektur i metod wdrażania. Każda organizacja jest unikatowa, więc masz kilka opcji do rozważenia, jak podano w poniższej tabeli: <br/><br/>

| Metoda | Opis |
|:---|:---|
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (zawarte w p Microsoft Endpoint Manager) | Zarządzanie Intune punktami końcowymi w środowisku natywnym chmury |
| [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Configuration Manager](/mem/configmgr/core/understand/introduction) (zawarte w p Microsoft Endpoint Manager) | Zarządzanie Intune i Configuration Manager i obciążeniami, które obejmują lokalne i chmurowe środowisko |
| [Menedżer konfiguracji](/mem/configmgr/core/understand/introduction) | Ochrona Configuration Manager punktów końcowych za pomocą opartego na chmurze rozwiązania Defender for Endpoint |
| Skrypt lokalny pobrany z portalu Microsoft 365 Defender sieci Microsoft 365 Defender | Używanie skryptów lokalnych w punktach końcowych w celu uruchomienia pilotażu lub uruchomienia tylko kilku urządzeń |

Aby dowiedzieć się więcej o opcjach wdrażania, zobacz [Planowanie wdrożenia usługi Defender na punktu końcowego](deployment-strategy.md). Następnie pobierz następujący plakat: 

[:::image type="content" source="../../media/defender-endpoint/mde-deployment-strategy.png" alt-text="Miniatura plakatu strategii wdrażania":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)

**[Pobierz plakat wdrażania](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)**

> [!TIP]
> Aby uzyskać bardziej szczegółowe informacje na temat planowania wdrożenia, zobacz [Planowanie Ochrona punktu końcowego w usłudze Microsoft Defender wdrażania](deployment-strategy.md).

## <a name="set-up-your-tenant-environment"></a>Konfigurowanie środowiska dzierżawy

Konfigurowanie środowiska dzierżawy obejmuje zadania, takie jak:

- Weryfikowanie licencji
- Konfigurowanie dzierżawy
- Konfigurowanie ustawień serwera proxy (tylko w razie potrzeby)
- Upewniamy się, że czujniki działają poprawnie, i raportowanie danych do usługi Defender for Endpoint 

Te zadania są uwzględnione w fazie konfiguracji programu Defender dla punktu końcowego. Zobacz [Konfigurowanie usługi Defender dla punktu końcowego](production-deployment.md).

## <a name="assign-roles-and-permissions"></a>Przypisywanie ról i uprawnień

Aby uzyskać dostęp do portalu Microsoft 365 Defender, skonfiguruj ustawienia usługi Defender for Endpoint lub wykonaj zadania, takie jak podejmowanie działań dotyczących wykrytych zagrożeń, muszą zostać przypisane odpowiednie uprawnienia. Program Defender for Endpoint [używa wbudowanych ról w Azure Active Directory](/azure/active-directory/roles/permissions-reference). 

Firma Microsoft zaleca przypisywanie użytkownikom tylko poziomu uprawnień potrzebnych do wykonywania swoich zadań. Uprawnienia można przypisywać przy użyciu podstawowego zarządzania uprawnieniami lub za pomocą kontroli dostępu opartej na rolach (RBAC, role [based access control](rbac.md) ). 

- Podstawowe zarządzanie uprawnieniami umożliwia administratorom globalnym i administratorom zabezpieczeń pełny dostęp, natomiast czytnikom zabezpieczeń dostęp tylko do odczytu.
- Przy użyciu RBAC możesz ustawić bardziej szczegółowe uprawnienia za pośrednictwem większej liczby ról. Na przykład możesz mieć czytniki zabezpieczeń, operatorów zabezpieczeń, administratorów zabezpieczeń, administratorów punktów końcowych i nie tylko.


W poniższej tabeli opisano kluczowe role, które należy rozważyć dla usługi Defender dla punktu końcowego w organizacji: <br/><br/>

| Rola | Opis |
|:---|:---|
| Administratorzy globalni (nazywani również administratorami globalnymi) <br/><br/> *Najlepszym rozwiązaniem jest ograniczenie liczby administratorów globalnych.* | Administratorzy globalni mogą wykonywać wszelkiego rodzaju zadania. Osoba, która załozyła konto w firmie w Microsoft 365 lub u Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1, jest domyślnie administratorem globalnym. <br/><br/> Administratorzy globalni mogą uzyskać dostęp do ustawień oraz zmieniać je we wszystkich Microsoft 365 portalach, takich jak: <br/>- Centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portalu ([https://security.microsoft.com](https://security.microsoft.com)) <br/>- Microsoft Endpoint Manager administracyjne ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  |
| Administratorzy zabezpieczeń (nazywani również administratorami zabezpieczeń) | Administratorzy zabezpieczeń mogą wykonywać zadania operatorów zabezpieczeń oraz następujące zadania: <br/>- Monitorowanie zasad związanych z zabezpieczeniami <br/>- Zarządzanie zagrożeniami zabezpieczeń i alertami <br/>— Wyświetlanie raportów |
| Operator zabezpieczeń | Operatory zabezpieczeń mogą wykonywać zadania czytnika zabezpieczeń oraz następujące zadania: <br/>— Wyświetlać informacje o wykrytych zagrożeniach <br/>- Badanie wykrytych zagrożeń i reagowanie na nie  |
| Czytelnik zabezpieczeń | Czytniki zabezpieczeń mogą wykonywać następujące zadania: <br/>- Wyświetlanie zasad związanych z zabezpieczeniami w Microsoft 365 usługach <br/>- Wyświetlanie zagrożeń bezpieczeństwa i alertów <br/>— Wyświetlanie raportów  |


> [!TIP]
> Aby dowiedzieć się więcej o rolach w Azure Active Directory, zobacz Przypisywanie ról administratora i innych użytkowników, którzy nie [są administratorami, użytkownikom](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal) z Azure Active Directory. Aby uzyskać więcej informacji o rolach w programie Defender dla punktu końcowego, zobacz [Kontrola dostępu oparta na rolach](prepare-deployment.md#role-based-access-control).

## <a name="onboard-to-defender-for-endpoint"></a>Onboard to Defender for Endpoint

Gdy wszystko będzie gotowe do korzystania z punktów końcowych organizacji, możesz wybrać jedną z kilku metod wymienionych w poniższej tabeli: <br/><br/>

|System operacyjny punktu końcowego | Metody dołączania|
|---|---|
| Windows 10 | [Skrypt lokalny (do 10 urządzeń)](configure-endpoints-script.md) <br>  [Zasady grupy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Urządzenie Menedżer urządzeń](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Skrypty VDI](configure-endpoints-vdi.md)  |
| macOS | [Skrypty lokalne](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [Jamf Pro](mac-install-with-jamf.md) <br> [Urządzenia Zarządzanie urządzeniami](mac-install-with-other-mdm.md) |
| iOS |[Oparte na aplikacji](ios-install.md) |
| Android | [Microsoft Endpoint Manager](android-intune.md) |

Następnie przejdź do konfigurowania funkcji ograniczania powierzchni ataków następnej generacji i ochrony.

## <a name="configure-next-generation-protection"></a>Konfigurowanie ochrony następnej generacji

Zalecamy [używanie Microsoft Endpoint Manager do](/mem) zarządzania urządzeniami i ustawieniami zabezpieczeń organizacji, jak pokazano na poniższej ilustracji:
 
:::image type="content" source="../../media/mde-p1/endpoint-policies.png" alt-text="Zasady zabezpieczeń punktów końcowych w portalu Endpoint Manager Micorosft" lightbox="../../media/mde-p1/endpoint-policies.png":::

Aby skonfigurować ochronę następnej generacji w programie Microsoft Endpoint Manager, wykonaj następujące czynności:

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz **pozycję Endpoint** **securityAntiwirus** > , a następnie wybierz istniejące zasady. (Jeśli nie masz istniejących zasad, utwórz nowe zasady).

3. Ustaw lub zmień ustawienia konfiguracji oprogramowania antywirusowego. Potrzebujesz pomocy? Skorzystaj z następujących zasobów: <br/>

   - [Ustawienia dla Windows 10 Program antywirusowy Microsoft Defender w programie Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)
   - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu iOS](ios-configure-features.md)

4. Po zakończeniu określania ustawień wybierz pozycję **Recenzja + zapisywanie**.

## <a name="configure-your-attack-surface-reduction-capabilities"></a>Konfigurowanie możliwości zmniejszania powierzchni ataków

Zmniejszenie powierzchni ataków ma na celu zmniejszenie liczby miejsc i sposobów, w jakie Twoja organizacja jest otwarta do ataków. Program Defender for Endpoint Plan 1 zawiera kilka funkcji i możliwości, które ułatwiają zmniejszanie powierzchni ataków w Twoich punktach końcowych. Te funkcje i funkcje są wymienione w poniższej tabeli: <br/><br/>

| Funkcja/funkcja | Opis |
|:---|:---|
| [Reguły zmniejszania obszaru podatnego na ataki](#attack-surface-reduction-rules) | Skonfiguruj reguły ograniczania powierzchni ataków, aby ograniczyć ryzykowne zachowania oparte na oprogramowaniu i zapewnić bezpieczeństwo Twojej organizacji. Reguły zmniejszania powierzchni ataków mają na celu określone zachowania oprogramowania, takie jak<br/>- Uruchamianie plików wykonywalnych i skryptów próbujących pobierać lub uruchamiać pliki <br/>- Uruchamianie skryptów w źródle danych lub w inny sposób podejrzanych skryptów <br/>- Wykonywanie zachowań, których aplikacje zwykle nie inicjują podczas normalnej pracy <br/><br/>Takie zachowania oprogramowania są czasami widoczne w aplikacji o zgodnej z prawem wersji. Takie zachowania są często uznawane za ryzykowne, ponieważ są często wykorzystywane przez atakujących za pośrednictwem złośliwego oprogramowania.  |
| [Ograniczanie oprogramowania wymuszającego okup](#ransomware-mitigation) | Skonfiguruj środki zaradcze dla oprogramowania wymuszającego okup, konfigurując kontrolowany dostęp do folderu, który pomaga chronić cenne dane Twojej organizacji przed złośliwymi aplikacjami i zagrożeniami, takimi jak oprogramowanie wymuszające okup. | 
| [Sterowanie urządzeniem](#device-control) | Konfigurowanie ustawień sterowania urządzeniami w organizacji w celu zezwalania na urządzenia wymienne lub blokowania ich (takich jak dyski USB). | 
| [Ochrona sieci](#network-protection) | Skonfiguruj ochronę sieci, aby zapobiec używaniu przez osoby w organizacji aplikacji, które mają dostęp do niebezpiecznych domen lub złośliwej zawartości w Internecie. |
| [Ochrona sieci Web](#web-protection) | Skonfiguruj ochronę przed zagrożeniami internetowymi, aby chronić urządzenia organizacji przed witrynami wyłudzających informacje, witrynami wykorzystującmi luki i innymi witrynami niezaufanymi lub o niskiej reputacji. Skonfiguruj filtrowanie zawartości sieci Web, aby śledzić i regulować dostęp do witryn internetowych na podstawie ich kategorii zawartości (takich jak rozrywka, wysoka przepustowość, zawartość dla dorosłych lub odpowiedzialność). |
| [Zapora sieciowa](#network-firewall) | Skonfiguruj zaporę sieciową za pomocą reguł, które określają dozwolony ruch sieciowy do połączeń z urządzeniami organizacji lub wychodzący z nich. |
| [Kontrolka aplikacji](#application-control)  | Skonfiguruj reguły kontroli aplikacji, jeśli chcesz zezwolić na uruchamianie tylko zaufanych aplikacji i procesów na Windows urządzeniach.    |

### <a name="attack-surface-reduction-rules"></a>Reguły zmniejszania obszaru podatnego na ataki

Reguły zmniejszania powierzchni ataków są dostępne na urządzeniach z systemem Windows. Zalecamy używanie Microsoft Endpoint Manager, jak pokazano na poniższej ilustracji:

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Reguły zmniejszania powierzchni ataków w portalu Microsoft Endpoint Manager użytkowników" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz **pozycję Zabezpieczenia punktu** **końcowegoWłącz** >  zmniejszenie **powierzchni** >  + Utwórz zasady.

3. W **przypadku opcji Platforma** wybierz **Windows 10 lub nowsze.**

4. W **przypadku profilu** wybierz pozycję **Reguły zmniejszania powierzchni ataków**, a następnie wybierz pozycję **Utwórz**.

5. Na karcie **Podstawy** określ nazwę i opis zasad, a następnie wybierz przycisk **Dalej**.

6. Na karcie **Ustawienia konfiguracji** rozwiń pozycję **Reguły zmniejszania powierzchni w przypadku ataków**.

7. Określ ustawienia dla każdej reguły, a następnie wybierz przycisk **Dalej**. (Aby uzyskać więcej informacji na temat tego, do czego mają zastosowanie poszczególne reguły, zobacz [Reguły ograniczania powierzchni ataków](attack-surface-reduction.md)). 

8. Jeśli w **organizacji na karcie Zakres** są używane tagi zakresów, wybierz pozycję **+ Wybierz** tagi zakresów, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz przycisk **Dalej**. 
   
   Aby dowiedzieć się więcej o tagach zakresów, zobacz Używanie kontroli dostępu opartej na rolach [(RBAC, role based access control) i tagów zakresów dla rozpowszechnianych informacji IT](/mem/intune/fundamentals/scope-tags).

9. Na **karcie Zadania określ** użytkowników i grupy, do których mają być stosowane zasady, a następnie wybierz pozycję **Dalej**. (Aby dowiedzieć się więcej o zadaniach, zobacz [Przypisywanie profilów użytkowników i urządzeń Microsoft Intune](/mem/intune/configuration/device-profile-assign)).

10. Na karcie **Recenzja + tworzenie** przejrzyj ustawienia, a następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Aby dowiedzieć się więcej o zasadach ograniczania powierzchni ataków, zobacz następujące zasoby:
> - [Stosowanie reguł zmniejszania powierzchni ataków w celu zapobiegania zainfekowaniu złośliwym oprogramowaniem](attack-surface-reduction.md)
> - [Wyświetlanie listy reguł zmniejszania powierzchni ataków](attack-surface-reduction-rules-reference.md)
> - [Wdrażanie reguł ograniczania powierzchni ataków Krok 3. Implementowanie reguł asr](attack-surface-reduction-rules-deployment-implement.md)

### <a name="ransomware-mitigation"></a>Ograniczanie oprogramowania wymuszającego okup

Uzyskujesz środki zaradcze przed oprogramowaniem wymuszającym okup przez kontrolowany [dostęp do folderu](controlled-folders.md#what-is-controlled-folder-access), który umożliwia tylko zaufanym aplikacjom dostęp do chronionych folderów w twoich punktach końcowych. 

Zalecamy używanie programu Microsoft Endpoint Manager w celu skonfigurowania kontrolowanego dostępu do folderu.

:::image type="content" source="../../media/mde-p1/mem-asrpolicies.png" alt-text="Zasady asr w portalu Microsoft Endpoint Manager użytkowników" lightbox="../../media/mde-p1/mem-asrpolicies.png":::

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się. 

2. Wybierz **pozycję Zabezpieczenia punktu końcowego**, a następnie **wybierz pozycję Zmniejszenie powierzchni ataków**.

3. Wybierz **pozycję + Utwórz zasady**. 

4. W **przypadku opcji Platforma** wybierz **pozycję Windows 10 później**, a następnie dla opcji **Profil** wybierz pozycję **Reguły ograniczania powierzchni ataków**. Następnie wybierz **pozycję Utwórz**. 

5. Na karcie **Podstawy** nazwij zasady i dodaj opis. Wybierz pozycję **Dalej**. 

6. Na karcie **Ustawienia konfiguracji** w sekcji **Reguły** zmniejszania powierzchni ataków przewiń w dół. Z listy **rozwijanej Włączanie ochrony** folderu wybierz pozycję **Włącz**. Opcjonalnie możesz określić inne następujące ustawienia:

   - Obok **pozycji Lista dodatkowych folderów**, które muszą być chronione, wybierz menu rozwijane, a następnie dodaj foldery, które muszą być chronione.
   - Obok pozycji **Lista aplikacji, które mają** dostęp do chronionych folderów wybierz menu rozwijane, a następnie dodaj aplikacje, które powinny mieć dostęp do chronionych folderów.
   - Obok **pozycji** Wyklucz pliki i ścieżki z reguł zmniejszania powierzchni ataków wybierz menu rozwijane, a następnie dodaj pliki i ścieżki, które muszą być wykluczone z reguł zmniejszania powierzchni ataków.

   Następnie wybierz przycisk **Dalej**.

7. Jeśli w **organizacji na karcie Zakres** są używane tagi zakresów, wybierz pozycję **+ Wybierz** tagi zakresów, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz przycisk **Dalej**. 
   
   Aby dowiedzieć się więcej o tagach zakresów, zobacz Używanie kontroli dostępu opartej na rolach [(RBAC, role based access control) i tagów zakresów dla rozpowszechnianych informacji IT](/mem/intune/fundamentals/scope-tags).

8. Na karcie **Zadania wybierz** pozycję **Dodaj** wszystkich użytkowników i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz też określić określone grupy użytkowników lub urządzeń).

9. Na karcie **Recenzja + tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**. Zasady zostaną zastosowane do wszystkich punktów końcowych, które wkrótce zostały zastosowane do usługi Defender for Endpoint.

### <a name="device-control"></a>Sterowanie urządzeniem

Możesz skonfigurować usługę Defender for Endpoint, aby blokować lub zezwalać na urządzenia przenośne i pliki na urządzeniach wymiennych. Zalecamy skonfigurowanie Microsoft Endpoint Manager sterowania urządzeniem przy użyciu przeglądarki.

:::image type="content" source="../../media/mde-p1/mem-admintemplates.png" alt-text="Microsoft Endpoint Manager szablonów administracyjnych" lightbox="../../media/mde-p1/mem-admintemplates.png":::

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się. 

2. Wybierz pozycję **Urządzenia** > **Profile konfiguracji** > **Utwórz profil**.

3. W **przypadku opcji** Platforma wybierz **Windows 10 lub** nowsze, a dla **opcji Typ profilu** wybierz pozycję **Szablony**. 

   W **obszarze Nazwa szablonu** wybierz pozycję **Szablony administracyjne**, a następnie wybierz pozycję **Utwórz**. 

4. Na karcie **Podstawy** nazwij zasady i dodaj opis. Wybierz pozycję **Dalej**. 

5. Na karcie **Ustawienia konfiguracji** wybierz pozycję **Wszystkie Ustawienia**. Następnie w polu wyszukiwania wpisz `Removable` , aby wyświetlić wszystkie ustawienia dotyczące urządzeń wymiennych.

6. Zaznacz element na liście, na przykład Wszystkie wymienne **Storage klas:** Odmów dostępu, aby otworzyć jego okienko wysuwu. Wysuw w przypadku każdego ustawienia wyjaśnia, co się dzieje, gdy jest włączone, wyłączone lub nieskonfigurowane. Wybierz ustawienie, a następnie wybierz przycisk **OK**. 

7. Powtórz krok 6 dla każdego ustawienia, które chcesz skonfigurować. Następnie wybierz przycisk **Dalej**.

8. Jeśli w **organizacji na karcie Zakres** są używane tagi zakresów, wybierz pozycję **+ Wybierz** tagi zakresów, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz przycisk **Dalej**. 
   
   Aby dowiedzieć się więcej o tagach zakresów, zobacz Używanie kontroli dostępu opartej na rolach [(RBAC, role based access control) i tagów zakresów dla rozpowszechnianych informacji IT](/mem/intune/fundamentals/scope-tags).

9. Na karcie **Zadania wybierz** pozycję **Dodaj** wszystkich użytkowników i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz też określić określone grupy użytkowników lub urządzeń).

10. Na karcie **Recenzja + tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**. Zasady zostaną zastosowane do wszystkich punktów końcowych, które wkrótce zostały zastosowane do usługi Defender for Endpoint.

> [!TIP]
> Aby uzyskać więcej informacji, zobacz Jak sterować [urządzeniami USB i innymi nośnikami wymiennymi przy użyciu Ochrona punktu końcowego w usłudze Microsoft Defender](control-usb-devices-using-intune.md).

### <a name="network-protection"></a>Ochrona sieci

Dzięki ochronie sieci można chronić organizację przed niebezpiecznymi domenami, które mogą czynami wyłudzania informacji, oszustwami i złośliwą zawartością w Internecie. Zalecamy włączenie Microsoft Endpoint Manager sieci za pomocą programu Microsoft Microsoft Endpoint Manager.

:::image type="content" source="../../media/mde-p1/mem-endpointprotectionprofile.png" alt-text="Profil ochrony punktu końcowego w Microsoft Endpoint Manager sieci Web" lightbox="../../media/mde-p1/mem-endpointprotectionprofile.png":::

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się. 

2. Wybierz pozycję **Urządzenia** > **Profile konfiguracji** > **Utwórz profil**.

3. W **przypadku opcji** Platforma wybierz **Windows 10 lub** nowsze, a dla **opcji Typ profilu** wybierz pozycję **Szablony**. 

   W **obszarze Nazwa szablonu** wybierz pozycję **Ochrona punktu końcowego**, a następnie wybierz pozycję **Utwórz**. 

4. Na karcie **Podstawy** nazwij zasady i dodaj opis. Wybierz pozycję **Dalej**. 

5. Na karcie **Ustawienia konfiguracji** rozwiń pozycję **Microsoft Defender Exploit Guard**, a następnie rozwiń **pozycję Filtrowanie sieci**.

   Ustaw **ochronę sieci na** **wartość Włącz**. (Możesz również wybrać pozycję **Inspekcja,** aby zobaczyć, jak będzie działać ochrona sieci w Twoim środowisku).

   Następnie wybierz przycisk **Dalej**.

6. Na karcie **Zadania wybierz** pozycję **Dodaj** wszystkich użytkowników i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz też określić określone grupy użytkowników lub urządzeń).

7. Na **karcie Reguły stosowania** skonfiguruj regułę. Konfigurowalny profil zostanie zastosowany tylko do urządzeń spełniających określone kryteria. 

   Na przykład możesz przypisać zasady do punktów końcowych, dla których jest uruchomiona tylko jedna wersja systemu operacyjnego.

   Następnie wybierz przycisk **Dalej**. 

8. Na karcie **Recenzja + tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**. Zasady zostaną zastosowane do wszystkich punktów końcowych, które wkrótce zostały zastosowane do usługi Defender for Endpoint.

> [!TIP]
> Możesz użyć innych metod, takich jak Windows PowerShell lub zasady grupy, aby włączyć ochronę sieci. Aby dowiedzieć się więcej, [zobacz Włączanie ochrony sieci](enable-network-protection.md).

### <a name="web-protection"></a>Ochrona sieci Web

Dzięki ochronie sieci Web możesz chronić urządzenia organizacji przed zagrożeniami internetowymi i niepożądaną zawartością. Ochrona sieci Web obejmuje [ochronę przed zagrożeniami internetowymi](#configure-web-threat-protection) i [filtrowanie zawartości sieci Web](#configure-web-content-filtering). Skonfiguruj oba zestawy funkcji. Zalecamy skonfigurowanie Microsoft Endpoint Manager ochrony sieci Web za pomocą przeglądarki.

#### <a name="configure-web-threat-protection"></a>Konfigurowanie ochrony przed zagrożeniami internetowymi

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.
 
2. Wybierz **pozycję Zabezpieczenia punktu** **końcowegoWłącz** >  zmniejszenie powierzchni, a następnie wybierz **pozycję + Utwórz zasady**.

3. Wybierz platformę, na przykład Windows 10 **lub nowszą**, wybierz profil **ochrony sieci Web**, a następnie wybierz pozycję **Utwórz**. 

4. Na karcie **Podstawy** określ nazwę i opis, a następnie wybierz przycisk **Dalej**.

5. Na karcie **Ustawienia konfiguracji** rozwiń pozycję **Ochrona sieci Web**, określ ustawienia w poniższej tabeli, a następnie wybierz przycisk **Dalej**. <br/><br/>

   | Ustawienie | Zalecenie |
   |:---|:---|
   | **Włączanie ochrony sieci** | Ustaw na wartość **Włączone**. Uniemożliwia użytkownikom odwiedzanie złośliwych witryn lub domen. <br/><br/>Ewentualnie możesz ustawić ochronę sieci na wartość **Tryb inspekcji** , aby zobaczyć, jak będzie działać w Twoim środowisku. W trybie inspekcji ochrona sieci nie uniemożliwia użytkownikom odwiedzania witryn ani domen, ale śledzi wykrywanie jako zdarzenia. |
   | **Wymaganie filtru SmartScreen dla Starsza wersja Microsoft Edge** | Ustaw wartość **Tak**. Pomaga chronić użytkowników przed potencjalnymi wyłudzaniem informacji i złośliwym oprogramowaniem. |
   | **Blokowanie złośliwego dostępu do witryny** | Ustaw wartość **Tak**. Zapobiega pomijaniu ostrzeżeń o potencjalnie złośliwych witrynach przez użytkowników. |
   | **Blokowanie pobierania niesweryfikowanego pliku** | Ustaw wartość **Tak**. Uniemożliwia użytkownikom pomijanie ostrzeżeń i pobieranie niesprawdzonych plików. |

6. Jeśli w **organizacji na karcie Zakres** są używane tagi zakresów, wybierz pozycję **+ Wybierz** tagi zakresów, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz przycisk **Dalej**. 
   
   Aby dowiedzieć się więcej o tagach zakresów, zobacz Używanie kontroli dostępu opartej na rolach [(RBAC, role based access control) i tagów zakresów dla rozpowszechnianych informacji IT](/mem/intune/fundamentals/scope-tags).

7. Na karcie **Zadania określ** użytkowników i urządzenia, na których mają być odbierane zasady ochrony sieci Web, a następnie wybierz pozycję **Dalej**.

8. Na karcie **Recenzja + tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Aby dowiedzieć się więcej o ochronie przed zagrożeniami internetowymi, zobacz [Ochrona organizacji przed zagrożeniami internetowymi](web-threat-protection.md).

#### <a name="configure-web-content-filtering"></a>Konfigurowanie filtrowania zawartości sieci Web

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com/](https://security.microsoft.com/)) i zaloguj się.

2. Wybierz **Ustawienia** >  **Endpoints**.

3. W **obszarze Reguły** wybierz **pozycję Filtrowanie zawartości sieci Web**, a następnie wybierz pozycję **+ Dodaj zasady**.

4. W **wysuwanych polach** Dodaj zasady na **karcie Ogólne określ** nazwę zasad, a następnie wybierz pozycję **Dalej**.

5. W kategorii **Zablokowane wybierz** jedną lub więcej kategorii, które chcesz zablokować, a następnie wybierz pozycję **Dalej**.

6. Na karcie **Zakres** wybierz grupy urządzeń, do których chcesz otrzymywać te zasady, a następnie wybierz pozycję **Dalej**.

7. Na karcie **Podsumowanie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Zapisz**.

> [!TIP]
> Aby dowiedzieć się więcej o konfigurowaniu filtrowania zawartości sieci Web, zobacz [Filtrowanie zawartości sieci Web](web-content-filtering.md).

### <a name="network-firewall"></a>Zapora sieciowa

Zapora sieciowa pomaga zmniejszyć ryzyko zagrożenia bezpieczeństwa sieci. Zespół zabezpieczeń może ustawić reguły, które określają dozwolony ruch do lub z urządzeń organizacji. Zalecamy skonfigurowanie Microsoft Endpoint Manager sieciowej za pomocą Microsoft Endpoint Manager sieci. 

:::image type="content" source="../../media/mde-p1/mem-firewallpolicy.png" alt-text="Zasady zapory w portalu Microsoft Endpoint Manager sieci" lightbox="../../media/mde-p1/mem-firewallpolicy.png":::

Aby skonfigurować podstawowe ustawienia zapory, wykonaj następujące czynności:

1. Przejdź do Microsoft Endpoint Manager administracyjnego ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) i zaloguj się.

2. Wybierz **pozycję Zabezpieczenia punktu** **końcowegoFirewall** > , a następnie wybierz **pozycję + Utwórz zasady**.

3. Wybierz platformę, na przykład Windows 10 **lub nowszą**, wybierz profil **Zapory usługi Microsoft Defender**, a następnie wybierz pozycję **Utwórz**. 

4. Na karcie **Podstawy** określ nazwę i opis, a następnie wybierz przycisk **Dalej**.

5. **Rozwiń Zaporę Microsoft Defender**, a następnie przewiń listę w dół.

6. Ustaw dla każdego z następujących ustawień wartość **Tak**:

   - **Włączanie Zapory programu Microsoft Defender dla sieci domen** 
   - **Włączanie Zapory usługi Microsoft Defender dla sieci prywatnych**
   - **Włączanie Zapory programu Microsoft Defender dla sieci publicznych**
   
   Przejrzyj listę ustawień dla poszczególnych sieci domen, sieci prywatnych i sieci publicznych. Możesz pozostawić je skonfigurowane jako **Nieskonfigurowane** lub zmienić je odpowiednio do potrzeb Twojej organizacji.

   Następnie wybierz przycisk **Dalej**.

7. Jeśli w **organizacji na karcie Zakres** są używane tagi zakresów, wybierz pozycję **+ Wybierz** tagi zakresów, a następnie wybierz tagi, których chcesz użyć. Następnie wybierz przycisk **Dalej**. 
   
   Aby dowiedzieć się więcej o tagach zakresów, zobacz Używanie kontroli dostępu opartej na rolach [(RBAC, role based access control) i tagów zakresów dla rozpowszechnianych informacji IT](/mem/intune/fundamentals/scope-tags).

8. Na karcie **Zadania wybierz** pozycję **Dodaj** wszystkich użytkowników i **+ Dodaj wszystkie urządzenia**, a następnie wybierz pozycję **Dalej**. (Możesz też określić określone grupy użytkowników lub urządzeń).

9. Na karcie **Recenzja + tworzenie** przejrzyj ustawienia zasad, a następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Ustawienia zapory są szczegółowe i mogą wydawać się skomplikowane. Zobacz [Najlepsze rozwiązania dotyczące konfigurowania zapory Windows Defender sieciowej](/windows/security/threat-protection/windows-firewall/best-practices-configuring).

### <a name="application-control"></a>Kontrolka aplikacji

Windows Defender (WDAC, Application Control) pomaga chronić punkty Windows, zezwalając na uruchamianie tylko zaufanych aplikacji i procesów. Większość organizacji używa wdrażania etapowego pakietu WDAC. Oznacza to, że w większości organizacji nie jest najpierw WDAC we wszystkich Windows końcowych. W zależności od tego, czy punkty końcowe programu Windows Twojej organizacji są w pełni zarządzane, lekko zarządzane czy "Przynieś własne urządzenie", możesz wdrożyć WDAC we wszystkich lub niektórych punktach końcowych.

Aby uzyskać pomoc w planowaniu wdrożenia WDAC, zobacz następujące zasoby:

- [Application Control for Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Windows Defender decyzji dotyczących projektu zasad kontroli aplikacji](/windows/security/threat-protection/windows-defender-application-control/understand-windows-defender-application-control-policy-design-decisions)

- [Windows Defender wdrażania kontroli aplikacji w różnych scenariuszach: typy urządzeń](/windows/security/threat-protection/windows-defender-application-control/types-of-devices)

## <a name="next-steps"></a>Następne kroki

Po zakończeniu procesu konfiguracji kolejnym krokiem jest wprowadzenie usługi Defender dla punktu końcowego. 

- [Wprowadzenie z programem Defender dla punktu końcowego (plan 1)](mde-plan1-getting-started.md)
