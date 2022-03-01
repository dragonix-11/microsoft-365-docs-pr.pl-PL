---
title: Ochrona ustawień zabezpieczeń za pomocą ochrony przed naruszeniami
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Ochrona przed naruszeniami zapobiega zmienianiu ważnych ustawień zabezpieczeń przez złośliwe aplikacje.
keywords: złośliwe oprogramowanie, defender, oprogramowanie antywirusowe, ochrona przed naruszeniami
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.technology: mde
ms.date: 01/18/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: ef9db769811c3848646c0bf7b8f7755941918362
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2022
ms.locfileid: "63009738"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Ochrona ustawień zabezpieczeń za pomocą ochrony przed naruszeniami

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ochrona przed naruszeniami jest dostępna dla urządzeń z jedną z następujących wersji programu Windows:

- Windows 10
- Windows 11
- Windows 10 Enterprise wielu sesji
- Windows 11 Enterprise wielu sesji 
- Windows Server 2019
- Windows Server 2022
- Windows Server w wersji 1803 lub nowszej
- System Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> Ochrona przed naruszeniami Windows Server 2012 R2 jest dostępna dla urządzeń dołączanych przy użyciu nowoczesnego, ujednoliconego pakietu rozwiązań. Aby uzyskać więcej informacji, zobacz Nowe funkcje w nowoczesnym, ujednoliconym rozwiązaniu dla wersji [Windows Server 2012 R2 i 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

## <a name="overview"></a>Omówienie

W przypadku niektórych rodzajów cyberataków złe szybki próbują wyłączyć na komputerach funkcje zabezpieczeń, takie jak ochrona przed wirusami. Bad  na przykład w celu wyłączenia funkcji zabezpieczeń, aby uzyskać łatwiejszy dostęp do danych, zainstalować złośliwe oprogramowanie lub w inny sposób wykorzystać dane, tożsamość i urządzenia. Ochrona przed naruszeniami pomaga zapobiec występowaniu tego typu zdarzeń.

Ochrona przed naruszeniami uniemożliwia złośliwym aplikacjom podejmowanie takich czynności, jak:

- Wyłączanie ochrony przed wirusami i zagrożeniami
- Wyłączanie ochrony w czasie rzeczywistym
- Wyłączanie monitorowania zachowania
- Wyłączanie oprogramowania antywirusowego (na przykład IOfficeAntiwirus (IOAV))
- Wyłączanie ochrony w chmurze
- Usuwanie aktualizacji analizy zabezpieczeń
- Wyłączanie automatycznych akcji na wykrytych zagrożeniach

### <a name="how-it-works"></a>Jak to działa

Ochrona przed naruszeniami jest w zasadzie blokowana Program antywirusowy Microsoft Defender na bezpieczne, wartości domyślne i zapobiega zmienianiu ustawień zabezpieczeń za pomocą aplikacji i metod, takich jak:

- Konfigurowanie ustawień w Edytorze rejestru na Windows urządzeniu
- Zmienianie ustawień za pomocą poleceń cmdlet programu PowerShell
- Edytowanie lub usuwanie ustawień zabezpieczeń za pośrednictwem zasady grupy

Ochrona przed naruszeniami nie uniemożliwia wyświetlania ustawień zabezpieczeń. Ochrona przed naruszeniami nie ma wpływu na sposób rejestrowania się aplikacji antywirusowych innych niż firma Microsoft Zabezpieczenia Windows aplikacji. Jeśli Twoja organizacja używa sieci Windows 10 Enterprise E5, poszczegoni użytkownicy nie mogą zmienić ustawienia ochrony przed naruszeniami. W takich przypadkach ochrona przed naruszeniami jest zarządzana przez Twój zespół zabezpieczeń.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

<br/><br/>

|Aby wykonać to zadanie...|Zobacz tę sekcję...|
|---|---|
|Zarządzanie ochroną przed naruszeniami w dzierżawie <p> Włączanie lub Microsoft 365 Defender ochrony przed naruszeniami za pomocą portalu ochrony przed naruszeniami|[Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu narzędzia Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Dostosowywanie ustawień ochrony przed naruszeniami w organizacji <p> Aby włączyć lub wyłączyć ochronę przed Microsoft Endpoint Manager, użyj usługi Intune (Microsoft Endpoint Manager). Tę metodę można skonfigurować ochronę przed naruszeniami dla niektórych lub wszystkich użytkowników.|[Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Włączanie lub wyłączanie ochrony przed naruszeniami w organizacji za pomocą aplikacji Menedżer konfiguracji|[Zarządzanie ochroną przed naruszeniami w organizacji za pomocą dołączania dzierżawy Menedżer konfiguracji wersji 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Włączanie lub wyłączanie ochrony przed naruszeniami na poszczególnych urządzeniach|[Zarządzanie ochroną przed naruszeniami na poszczególnych urządzeniach](#manage-tamper-protection-on-an-individual-device)|
|Wyświetlanie szczegółów prób naruszenia na urządzeniach|[Wyświetlanie informacji o próbach naruszenia](#view-information-about-tampering-attempts)|
|Przejrzyj zalecenia dotyczące zabezpieczeń|[Przejrzyj zalecenia dotyczące zabezpieczeń](#review-your-security-recommendations)|
|Przejrzyj listę często zadawanych pytań (często zadawane pytania)|[Przeglądanie często zadawanych pytania](#view-information-about-tampering-attempts)|

W zależności od metody lub narzędzia do zarządzania, za pomocą których włączyć ochronę przed naruszeniami, może być zależność od ochrony w chmurze.

W poniższej tabeli przedstawiono szczegółowe informacje o metodach, narzędziach i zależnościach.

<br/><br/>

|Jak włączono ochronę przed naruszeniami|Zależność od ochrony w chmurze (MAPS)|
|---|---|
|Microsoft Intune|Nie|
|Microsoft Endpoint Configuration Manager + Dołącz dzierżawę|Nie|
|Microsoft 365 Defender portalu ([https://security.microsoft.com](https://security.microsoft.com))|Tak|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Zarządzanie ochroną przed naruszeniami w organizacji za pomocą portalu Microsoft 365 Defender sieci

Ochronę przed naruszeniami można włączać i wyłączać dla dzierżawy za Microsoft 365 Defender portal internetowy ([https://security.microsoft.com](https://security.microsoft.com)). Należy pamiętać o kilku kwestiach:

- Obecnie opcja zarządzania zabezpieczeniami przed naruszeniami w portalu Microsoft 365 Defender jest domyślnie włączona dla nowych wdrożeń. W przypadku istniejących wdrożeń ochrona przed naruszeniami jest dostępna z określoną zgodyą. Aby się w tym programie wybrać, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">w portalu Microsoft 365 Defender wybierz</a> pozycję **Zaawansowane** \> funkcje ochrony przed Ustawienia **punktami** \> **końcowymi**\>.

- Gdy używasz portalu Microsoft 365 Defender do zarządzania zabezpieczeniami przed naruszeniami, nie musisz używać usługi Intune ani metody dołączania dzierżawy.

- Jeśli zarządzasz ochroną przed naruszeniami w portalu usługi Microsoft 365 Defender, ustawienie to jest stosowane w całej dzierżawie, co ma wpływ na wszystkie urządzenia z systemem Windows 10, Windows 10 Enterprise w wielu sesjach, Windows 11 Windows 11 Enterprise  wiele sesji, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 lub Windows Server 2022. Aby dostosować ochronę przed naruszeniami (na przykład ochrony przed naruszeniami na niektórych urządzeniach, ale wyłączoną dla [](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) innych), używaj aplikacji sieci Microsoft Endpoint Manager lub Menedżer konfiguracji dołączania [dzierżawy](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006).

- Jeśli masz środowisko hybrydowe, ustawienia ochrony przed naruszeniami skonfigurowane w usłudze Intune mają pierwszeństwo przed ustawieniami skonfigurowanymi w portalu Microsoft 365 Defender sieci.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Wymagania dotyczące zarządzania zabezpieczeniami przed naruszeniami w Microsoft 365 Defender zabezpieczeń

- Musisz mieć [przypisane odpowiednie uprawnienia](/microsoft-365/security/defender-endpoint/assign-portal-access) , takie jak administrator globalny, administrator zabezpieczeń lub operacje zabezpieczeń.

- Na Windows musi być uruchomiona jedna z następujących wersji programu Windows:
  
  - Windows 10
  - Windows 11
  - Windows 10 Enterprise wielu sesji
  - Windows 11 Enterprise wielu sesji 
  - Windows Server 2019
  - Windows Server 2022
  - Windows Server w wersji 1803 lub nowszej
  - System Windows Server 2016
  - Windows Server 2012 R2

Aby uzyskać więcej informacji o wersjach, [zobacz Windows 10 informacje o wersji](/windows/release-health/release-information).

- Twoje urządzenia muszą być [podłączone do programu Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/onboarding).

- Urządzenia muszą być w wersji na platformie `4.18.2010.7` chroniącej przed złośliwym oprogramowaniem (lub wspomniano) i wersji aparatu ochrony przed `1.1.17600.5` złośliwym oprogramowaniem (lub wspomniano wyżej). ([Zarządzaj Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md)).

- [Ochrona w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md) musi być włączona.

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Włączanie lub wyłączanie ochrony przed naruszeniami w portalu Microsoft 365 Defender użytkowników

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Włącz ochronę przed naruszeniami w portalu Microsoft 365 Defender użytkowników.":::

1. Przejdź do Microsoft 365 Defender konta ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Wybierz **Ustawienia** \> **punkty końcowe**.

3. Przejdź do **opcji Ogólne** \> **funkcje zaawansowane**, a następnie włącz ochronę przed naruszeniami.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu Microsoft Endpoint Manager

Jeśli Twoja organizacja używa programu Microsoft Endpoint Manager (MEM), możesz włączyć lub wyłączyć ochronę przed naruszeniami w organizacji w centrum administracyjnym usługi Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Usługa Intune umożliwia dostosowanie ustawień ochrony przed naruszeniami. Jeśli na przykład chcesz włączyć ochronę przed naruszeniami na niektórych urządzeniach, ale nie wszystkich, użyj usługi Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Wymagania dotyczące zarządzania zabezpieczeniami przed naruszeniami w Endpoint Manager

- Twoje urządzenia muszą być [podłączone do programu Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/onboarding).

- Musisz mieć [przypisane odpowiednie uprawnienia](/microsoft-365/security/defender-endpoint/assign-portal-access) , takie jak administrator globalny, administrator zabezpieczeń lub operacje zabezpieczeń.

- Twoja organizacja korzysta [Microsoft Endpoint Manager do zarządzania urządzeniami](/mem/endpoint-manager-getting-started). (Microsoft Endpoint Manager (MEM) są wymagane; MEM jest dołączony do Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3, Microsoft 365  G3/G5 dla instytucji rządowych i odpowiadające im licencje dla instytucji edukacyjnych).

- Na Windows muszą być uruchomione Windows 11 lub Windows 10 [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) lub nowsze. (Aby uzyskać więcej informacji o wersjach, [zobacz Windows 10 informacje o wersji](/windows/release-health/release-information)).

- Musisz korzystać z zabezpieczeń [Windows przy aktualizacji](https://www.microsoft.com/wdsi/definitions) zabezpieczeń do wersji 1.287.60.0 (lub powyższej).

- Urządzenia muszą korzystać z platformy chroniącej przed złośliwym oprogramowaniem w wersji 4.18.1906.3 (lub powyższej) `1.1.15500.X` oraz wersji aparatu ochrony przed złośliwym oprogramowaniem (lub wspomniano wyżej). ([Zarządzaj Program antywirusowy Microsoft Defender i stosowanie planu bazowego](manage-updates-baselines-microsoft-defender-antivirus.md)).

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Włączanie (lub wyłączanie) ochrony przed naruszeniami w Microsoft Endpoint Manager

![Włącz ochronę przed naruszeniami za pomocą Endpoint Manager.](images/turnontamperprotectinmem.png)

1. W centrum [Microsoft Endpoint Manager przejdź](https://go.microsoft.com/fwlink/?linkid=2109431) do pozycji Zabezpieczenia punktu **końcowego** \> oprogramowania antywirusowego **, a** następnie wybierz pozycję **+ Utwórz zasady**.

   - Na liście **Platforma** wybierz pozycję Windows 10 **lub nowsze.**
   - Na liście **Profil** wybierz pozycję **Zabezpieczenia Windows środowisko.**

2. Utwórz profil, który zawiera następujące ustawienie:

    - **Włącz ochronę przed naruszeniami, aby zapobiec wyłączeniu programu Microsoft Defender: Włącz**

3. Przypisz profil do jednej lub większej liczby grup.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Zarządzanie ochroną przed naruszeniami w organizacji za Menedżer konfiguracji 2006

Jeśli korzystasz z programu Menedżer konfiguracji w wersji [2006](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006), możesz zarządzać ustawieniami ochrony przed naruszeniami w usługach Windows 10, Windows 10 Enterprise multi-session, Windows 11, Windows 11 Enterprise multi-session, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 i Windows Server 2022 przy użyciu metody o nazwie *dołączanie dzierżawy*. Dołączanie dzierżawy umożliwia synchronizowanie urządzeń lokalnych z Menedżer konfiguracji Microsoft Endpoint Manager centrum administracyjnego programu Microsoft Endpoint Manager, a następnie dostarczanie zasad konfiguracji zabezpieczeń punktów końcowych do lokalnych kolekcji & urządzeniach.

> [!NOTE]
> Procedura ta może zostać użyta do rozszerzenia ochrony przed naruszeniami na urządzeniach z systemem Windows 10, Windows 10 Enterprise w wielu sesjach, Windows 11, Windows 11 Enterprise, Windows Server 2019 i Windows Server 2022. Upewnij się, że wymagania wstępne i inne informacje są dostępne w zasobach wymienionych w tej procedurze.

1. Konfigurowanie dołączania dzierżawy. Aby dowiedzieć się więcej, zobacz [Wprowadzenie: Tworzenie i wdrażanie zasad zabezpieczeń punktów końcowych w centrum administracyjnym](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. W centrum [Microsoft Endpoint Manager przejdź](https://go.microsoft.com/fwlink/?linkid=2109431) do pozycji Zabezpieczenia punktu **końcowego** \> oprogramowania antywirusowego **, a** następnie wybierz pozycję **+ Utwórz zasady**.

   - Na liście **Platforma** wybierz pozycję **Windows 10, Windows 11 i Windows Server (ConfigMgr)**.
   - Na liście **Profil** wybierz pozycję Zabezpieczenia Windows **(podgląd)**.

3. Wdeksuj zasady w kolekcji urządzeń.

#### <a name="need-help-with-this-method"></a>Potrzebujesz pomocy przy tej metodzie?

Zobacz następujące zasoby:

- [Ustawienia profilu Zabezpieczenia Windows w programie Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Blog Community: ogłaszanie ochrony przed naruszeniami dla klientów dołączania Menedżer konfiguracji dzierżawy](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Zarządzanie ochroną przed naruszeniami na poszczególnych urządzeniach

> [!NOTE]
> Ochrona przed naruszeniami blokuje próby Program antywirusowy Microsoft Defender ustawień za pośrednictwem rejestru.
>
> Aby mieć pewność, że ochrona przed naruszeniami nie zakłóci działania produktów zabezpieczających innych niż firma Microsoft ani skryptów instalacji przedsiębiorstwa, które modyfikują te ustawienia, przejdź do strony **Zabezpieczenia Windows** i zaktualizuj zabezpieczenia do wersji 1.287.60.0 lub nowszej. (Zobacz [Aktualizacje analizy zabezpieczeń](https://www.microsoft.com/wdsi/definitions)).
>
> Po wróceniu tej aktualizacji ochrona przed naruszeniami będzie nadal chronić ustawienia rejestru i dzienniki będą próbować je modyfikować bez konieczności zwracania błędów.

Jeśli jesteś użytkownikiem domowym lub nie podlegasz ustawień zarządzanych przez zespół zabezpieczeń, możesz użyć aplikacji Zabezpieczenia Windows do zarządzania zabezpieczeniami. Aby zmienić ustawienia zabezpieczeń, takie jak ochrona przed naruszeniami, musisz mieć odpowiednie uprawnienia administratora na urządzeniu.

W aplikacji usługi Zabezpieczenia Windows jest Zabezpieczenia Windows:

![Ochrona przed naruszeniami włączona w Windows 10 Home.](images/tamperprotectionturnedon.png)

1. Wybierz **przycisk Start** i zacznij pisać *Zabezpieczenia*. W wynikach wyszukiwania wybierz pozycję **Zabezpieczenia Windows**.

2. Wybierz **pozycję Ochrona przed & przed wirusami** \> **i & ustawieniami ochrony przed zagrożeniami**.

3. Ustaw **ochronę przed naruszeniami** **na wartość Wł** lub **Wył**.

## <a name="are-you-using-windows-server-2016-or-windows-version-1709-1803-or-1809"></a>Korzystasz z Windows Server 2016 lub Windows wersji 1709, 1803 lub 1809?

Jeśli korzystasz z pakietu Windows Server 2016, Windows 10 1709, 1803 lub [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019), ochrona przed naruszeniami nie będzie dostępna w aplikacji Zabezpieczenia Windows. Aby ustalić, czy ochrona przed naruszeniami jest włączona, możesz użyć programu PowerShell.

Na Windows Server 2016 ta Ustawienia dokładnie odzwierciedla stan ochrony w czasie rzeczywistym, gdy jest włączona ochrona przed naruszeniami.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Używanie programu PowerShell do określania, czy ochrona przed naruszeniami i ochrona w czasie rzeczywistym są włączone

1. Otwórz Windows PowerShell aplikacji.

2. Użyj polecenia [cmdlet Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) programu PowerShell.

3. Na liście wyników odszukaj lub `IsTamperProtected` `RealTimeProtectionEnabled`. (Wartość True oznacza *,* że włączono ochronę przed naruszeniami).

## <a name="view-information-about-tampering-attempts"></a>Wyświetlanie informacji o próbach naruszenia

Próby naruszenia zwykle oznaczają większe cyberataki. Bad  przekonspewuje próbę zmiany ustawień zabezpieczeń, aby zachować nie dosuwaną wiadomość. Jeśli należysz do zespołu zabezpieczeń organizacji, możesz wyświetlać informacje o takich próbach, a następnie podejmować odpowiednie działania w celu zmniejszenia zagrożeń.

W przypadku wykrycia próby naruszenia w portalu sieci Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) jest [Microsoft 365 Defender alert](/microsoft-365/security/defender-endpoint/portal-overview).

![Microsoft 365 Defender.](images/tamperattemptalert.png)

Za [wykrywanie i reagowanie w punktach końcowych](overview-endpoint-detection-response.md) i [zaawansowane funkcje](advanced-hunting-overview.md) wyszukiwania w programie Microsoft Defender for Endpoint Twój zespół operacyjny bezpieczeństwa może zbadać te próby i rozwiązać je.

## <a name="review-your-security-recommendations"></a>Przejrzyj zalecenia dotyczące zabezpieczeń

Ochrona przed naruszeniami jest [zintegrowana z możliwościami & zarządzania lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md) . [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md) obejmują upewnioną, że ochrona przed naruszeniami jest włączona. Możesz na przykład wyszukiwać informacje dotyczące *manipulowania*. W wynikach wyszukiwania możesz wybrać pozycję **Włącz ochronę** przed naruszeniami, aby dowiedzieć się więcej i włączyć tę opcję.

![Włącz ochronę przed naruszeniami.](images/tamperprotectsecurityrecos.png)

Aby dowiedzieć się więcej o zarządzaniu & zagrożeniami, zobacz Informacje o pulpicie nawigacyjnym — informacje [Zarządzanie zagrożeniami i lukami](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>W jakich wersjach programu Windows skonfigurować ochronę przed naruszeniami?

Windows 10 systemu operacyjnego [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) lub nowszego wraz z [programem Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint).
  
Windows 10 Enterprise wielu sesji

Windows 11

Windows 11 Enterprise wielu sesji
  
Jeśli korzystasz z programu Menedżer konfiguracji w wersji 2006 z dołączoną dzierżawą, ochronę przed naruszeniami można wydłużyć do wersji Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 i Windows Server 2022. Zobacz [Dołączanie dzierżawy: Tworzenie i wdrażanie zasad ochrony punktu końcowego Oprogramowania antywirusowego w centrum administracyjnym (wersja Preview)](/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>Czy ochrona przed naruszeniami będzie mieć wpływ na rejestrację oprogramowania antywirusowego niebędące przez firmę Microsoft w Zabezpieczenia Windows aplikacji?

L.p. Produkty antywirusowe innych niż firmy Microsoft będą nadal rejestrować się w Zabezpieczenia Windows programie.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Co się stanie, Program antywirusowy Microsoft Defender nie jest aktywne na urządzeniu?

Urządzenia, które są podłączone do programu Microsoft Defender dla punktu końcowego, Program antywirusowy Microsoft Defender działają w trybie pasywnym. W takich przypadkach ochrona przed naruszeniami będzie nadal chronić usługę i jej funkcje.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Jak włączyć lub wyłączyć ochronę przed naruszeniami?

Jeśli jesteś użytkownikiem domowym, zobacz Zarządzanie ochroną przed naruszeniami [na poszczególnych urządzeniach](#manage-tamper-protection-on-an-individual-device).

Jeśli jesteś organizacją korzystającą z programu [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint), powinno być możliwe zarządzanie ochroną przed naruszeniami w usłudze Intune podobnie jak zarządzanie innymi funkcjami ochrony punktu końcowego. Zobacz następujące sekcje tego artykułu:

- [Zarządzanie zabezpieczeniami przed naruszeniami przy użyciu Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Zarządzanie zabezpieczeniami przed naruszeniami przy użyciu Microsoft 365 Defender zabezpieczeń](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Jak skonfigurowanie ochrony przed naruszeniami w usłudze Intune wpływa na sposób zarządzania Program antywirusowy Microsoft Defender za pomocą usługi zasady grupy?

Zasady grupy nie dotyczą ochrony przed naruszeniami. Zmiany wprowadzone w ustawieniach Program antywirusowy Microsoft Defender są ignorowane w przypadku korzystania z ochrony przed naruszeniami.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Jeśli używamy Microsoft Intune do konfigurowania ochrony przed naruszeniami, czy ma ona zastosowanie tylko do całej organizacji?

Masz elastyczność w konfigurowaniu ochrony przed naruszeniami w usłudze Intune. Możesz kierować zawartość do całej organizacji lub wybierać konkretne urządzenia i grupy użytkowników.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Czy mogę skonfigurować ochronę przed naruszeniami za pomocą Microsoft Endpoint Configuration Manager?

Jeśli używasz dołączania dzierżawy, możesz użyć Microsoft Endpoint Configuration Manager. Zobacz następujące zasoby:

- [Zarządzanie ochroną przed naruszeniami w organizacji za Menedżer konfiguracji 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Blog Community: Ogłaszanie ochrony przed naruszeniami dla klientów dołączania Menedżer konfiguracji dzierżawy](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>Mam Windows E3. Czy mogę używać konfigurowania ochrony przed naruszeniami w usłudze Intune?

Obecnie konfigurowanie ochrony przed naruszeniami w usłudze Intune jest dostępne tylko dla klientów korzystających z programu [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Co się stanie, jeśli spróbuję zmienić ustawienia programu Microsoft Defender dla punktu końcowego w usłudze Intune, Microsoft Endpoint Configuration Manager i Windows Management Instrumentation po włączeniu ochrony przed naruszeniami na urządzeniu?

Nie będzie można zmieniać funkcji chronionych za pomocą ochrony przed naruszeniami. takie żądania zmiany są ignorowane.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Jestem klientem korporacyjnym. Czy administratorzy lokalni mogą zmienić ochronę przed naruszeniami na swoich urządzeniach?

L.p. Administratorzy lokalni nie mogą zmieniać ani modyfikować ustawień ochrony przed naruszeniami.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Co się stanie, jeśli urządzenie jest w nim dołoowane do usługi Microsoft Defender for Endpoint, a następnie przechodzi w stan poza tablicą?

Jeśli urządzenie jest odłączone od programu Microsoft Defender for Endpoint, ochrona przed naruszeniami jest włączona, co jest stanem domyślnym dla urządzeń niezakierowanych.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Jeśli stan ochrony przed naruszeniami jest inny, czy alerty są wyświetlane w Microsoft 365 Defender zabezpieczeń?

Tak. Alert jest wyświetlany w obszarze [https://security.microsoft.com](https://security.microsoft.com) **Alerty**.

Zespół operacyjny ds. zabezpieczeń może również korzystać z zapytań łowiecki, takich jak na przykład:

`AlertInfo|where Title == "Tamper Protection bypass"`

[Wyświetlanie informacji o próbach naruszenia.](#view-information-about-tampering-attempts)

## <a name="see-also"></a>Zobacz też

[Pomóż zabezpieczyć Windows PC za pomocą Endpoint Protection dla Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Omówienie programu Microsoft Defender dla punktu końcowego](/microsoft-365/security/defender-endpoint)

[Razem lepiej: program Program antywirusowy Microsoft Defender i program Microsoft Defender dla punktu końcowego](why-use-microsoft-defender-antivirus.md)
