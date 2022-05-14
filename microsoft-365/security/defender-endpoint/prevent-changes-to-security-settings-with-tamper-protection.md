---
title: Chroń ustawienia zabezpieczeń z ochroną przed naruszeniami
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Użyj ochrony przed naruszeniami, aby zapobiec zmianie ważnych ustawień zabezpieczeń przez złośliwe aplikacje.
keywords: malware, defender, antivirus, ochrona przed naruszeniami
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
ms.date: 04/07/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 6bd334802319b897de7a8fd8fbb61a490dddcffe
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416315"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Chroń ustawienia zabezpieczeń z ochroną przed naruszeniami

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Ochrona przed naruszeniami jest dostępna dla urządzeń z uruchomioną jedną z następujących wersji Windows:

- Windows 11
- Windows 11 Enterprise wielu sesjach 
- Windows 10
- Windows 10 Enterprise wielu sesjach
- Windows Server 2022
- Windows Server 2019
- Windows Server, wersja 1803 lub nowsza
- System Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> Ochrona przed naruszeniami w Windows Server 2012 R2 jest dostępna dla urządzeń dołączonych przy użyciu nowoczesnego ujednoliconego pakietu rozwiązań. Aby uzyskać więcej informacji, zobacz [Dołączanie serwerów Windows do usługi Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-server-endpoints).


## <a name="overview"></a>Omówienie

Podczas pewnego rodzaju cyberataków źle aktorzy próbują wyłączyć funkcje zabezpieczeń, takie jak ochrona antywirusowa, na maszynach. Źle aktorzy lubią wyłączać funkcje zabezpieczeń, aby uzyskać łatwiejszy dostęp do danych, zainstalować złośliwe oprogramowanie lub w inny sposób wykorzystać dane, tożsamość i urządzenia. Ochrona przed naruszeniami pomaga zapobiegać występowaniu tego rodzaju rzeczy. Dzięki ochronie przed naruszeniami złośliwe aplikacje nie mogą podejmować akcji, takich jak:

- Wyłączanie ochrony przed wirusami i zagrożeniami
- Wyłączanie ochrony w czasie rzeczywistym
- Wyłączanie monitorowania zachowania
- Wyłączanie programu antywirusowego (na przykład IOfficeAntivirus (IOAV))
- Wyłączanie ochrony dostarczanej w chmurze
- Usuwanie aktualizacji analizy zabezpieczeń
- Wyłączanie automatycznych akcji w wykrytych zagrożeniach

### <a name="how-it-works"></a>Jak to działa

Ochrona przed naruszeniami zasadniczo blokuje Program antywirusowy Microsoft Defender do jej bezpiecznych, domyślnych wartości i uniemożliwia zmianę ustawień zabezpieczeń za pośrednictwem aplikacji i metod, takich jak:

- Konfigurowanie ustawień w Edytorze rejestru na urządzeniu Windows
- Zmienianie ustawień za pomocą poleceń cmdlet programu PowerShell
- Edytowanie lub usuwanie ustawień zabezpieczeń za pośrednictwem zasady grupy

Ochrona przed naruszeniami nie uniemożliwia wyświetlania ustawień zabezpieczeń. Ochrona przed naruszeniami nie ma wpływu na sposób rejestrowania aplikacji antywirusowych innych niż Microsoft w aplikacji Zabezpieczenia Windows. Jeśli Twoja organizacja korzysta z Windows 10 Enterprise E5, poszczególni użytkownicy nie mogą zmienić ustawienia ochrony przed naruszeniami. W takich przypadkach ochrona przed naruszeniami jest zarządzana przez zespół ds. zabezpieczeń.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|Aby wykonać to zadanie...|Zobacz tę sekcję...|
|---|---|
|Zarządzanie ochroną przed naruszeniami w dzierżawie <p> Użyj portalu Microsoft 365 Defender, aby włączyć lub wyłączyć ochronę przed naruszeniami|[Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Dostosuj ustawienia ochrony przed naruszeniami w organizacji <p> Użyj Intune (Microsoft Endpoint Manager), aby włączyć lub wyłączyć ochronę przed naruszeniami. Za pomocą tej metody można skonfigurować ochronę przed naruszeniami dla niektórych lub wszystkich użytkowników.|[Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Włączanie (lub wyłączanie) ochrony przed naruszeniami w organizacji przy użyciu Configuration Manager|[Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu dołączania dzierżawy do Configuration Manager w wersji 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Włączanie (lub wyłączanie) ochrony przed naruszeniami dla poszczególnych urządzeń|[Zarządzanie ochroną przed naruszeniami na poszczególnych urządzeniach](#manage-tamper-protection-on-an-individual-device)|
|Wyświetlanie szczegółów dotyczących prób naruszenia na urządzeniach|[Wyświetlanie informacji o próbach naruszenia](#view-information-about-tampering-attempts)|
|Przeglądanie zaleceń dotyczących zabezpieczeń|[Pobieranie rekomendacji dotyczących zabezpieczeń](#review-your-security-recommendations)|
|Przejrzyj listę często zadawanych pytań|[Przeglądaj często zadawane pytania](#view-information-about-tampering-attempts)|

## <a name="potential-dependency-on-cloud-protection"></a>Potencjalna zależność od ochrony chmury  
  
W zależności od metody lub narzędzia do zarządzania używanego do włączania ochrony przed naruszeniami może istnieć zależność od [ochrony dostarczanej przez chmurę ochrona dostarczana przez chmurę](cloud-protection-microsoft-defender-antivirus.md) jest również nazywana ochroną w chmurze lub usługą Microsoft Advanced Protection Service (MAPS).

Poniższa tabela zawiera szczegółowe informacje na temat metod, narzędzi i zależności.

| Jak włączono ochronę przed naruszeniami | Zależność od ochrony chmury |
|---|---|
|Microsoft Intune|Nie|
|Microsoft Endpoint Configuration Manager z dołączaniem dzierżawy|Nie|
|portal Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))|Tak|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu portalu Microsoft 365 Defender

Ochronę przed naruszeniami można włączyć lub wyłączyć dla dzierżawy przy użyciu portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Oto kilka kwestii, o których należy pamiętać:

- Obecnie opcja zarządzania ochroną przed naruszeniami w portalu Microsoft 365 Defender jest domyślnie włączona dla nowych wdrożeń. W przypadku istniejących wdrożeń ochrona przed naruszeniami jest dostępna na zasadzie zgody. Aby wyrazić zgodę, w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a> wybierz **pozycję Ustawienia** \> **Punkty końcowe** \> **Funkcje** \> zaawansowane **Ochrona przed naruszeniami**.
- Jeśli używasz portalu Microsoft 365 Defender do zarządzania ochroną przed naruszeniami, nie musisz używać Intune ani metody dołączania dzierżawy.
- W przypadku zarządzania ochroną przed naruszeniami w portalu Microsoft 365 Defender ustawienie jest stosowane w całej dzierżawie, co ma wpływ na wszystkie urządzenia z uruchomionymi Windows 10, Windows 10 Enterprise wielosesyjną, Windows 11, Windows 11 Enterprise  multi-session, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 lub Windows Server 2022. Aby dostroić ochronę przed naruszeniami (na przykład ochronę przed naruszeniami na niektórych urządzeniach, ale poza nimi), użyj [Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) lub [Configuration Manager z dołączaniem dzierżawy](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006).
- Jeśli masz środowisko hybrydowe, ustawienia ochrony przed naruszeniami skonfigurowane w Intune mają pierwszeństwo przed ustawieniami skonfigurowanymi w portalu Microsoft 365 Defender.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Wymagania dotyczące zarządzania ochroną przed naruszeniami w portalu Microsoft 365 Defender

- Musisz mieć [przypisane odpowiednie uprawnienia](/microsoft-365/security/defender-endpoint/assign-portal-access) , takie jak administrator globalny, administrator zabezpieczeń lub operacje zabezpieczeń.

- Na urządzeniach Windows musi działać jedna z następujących wersji Windows:
  
  - Windows 11
  - Windows 11 Enterprise wielu sesjach 
  - Windows 10
  - Windows 10 Enterprise wielu sesjach
  - Windows Server 2022
  - Windows Server 2019
  - Windows Server, wersja 1803 lub nowsza
  - System Windows Server 2016
  - Windows Server 2012 R2

Aby uzyskać więcej informacji na temat wydań, zobacz [Windows 10 informacji o wersji](/windows/release-health/release-information).

- Urządzenia muszą być [dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/onboarding).
- Urządzenia muszą używać wersji `4.18.2010.7` platformy chroniącej przed złośliwym oprogramowaniem (lub nowszej) i wersji aparatu chroniącego przed złośliwym oprogramowaniem (lub nowszej `1.1.17600.5` ). ([Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)).
- Ochrona [dostarczana w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md) musi być włączona.

> [!NOTE]
> Po włączeniu ochrony przed naruszeniami za pośrednictwem portalu Microsoft 365 Defender wymagana jest ochrona dostarczana przez chmurę, dzięki czemu można kontrolować włączony stan ochrony przed naruszeniami.  
> Począwszy od aktualizacji z listopada 2021 r. (wersja `4.18.2111.5`platformy), jeśli ochrona dostarczana w chmurze nie jest włączona dla urządzenia, a ochrona przed naruszeniami jest włączona w portalu Microsoft 365 Defender, ochrona dostarczana w chmurze zostanie automatycznie włączona dla tego urządzenia wraz z ochroną przed naruszeniami.   

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Włączanie (lub wyłączanie) ochrony przed naruszeniami w portalu Microsoft 365 Defender

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Włączanie ochrony przed naruszeniami w portalu Microsoft 365 Defender" lightbox="../../media/mde-turn-tamperprotectionon.png":::

1. Przejdź do portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i zaloguj się.

2. Wybierz **pozycję Ustawienia** \> **punkty końcowe**.

3. Przejdź do pozycji **Ogólne** \> **funkcje zaawansowane**, a następnie włącz ochronę przed naruszeniami.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Zarządzanie ochroną przed naruszeniami w organizacji przy użyciu Microsoft Endpoint Manager

Jeśli Organizacja używa Microsoft Endpoint Manager (MEM), możesz włączyć (lub wyłączyć) ochronę przed naruszeniami w organizacji w centrum administracyjnym Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Użyj Intune, aby dostosować ustawienia ochrony przed naruszeniami. Jeśli na przykład chcesz włączyć ochronę przed naruszeniami na niektórych urządzeniach, ale nie na wszystkich, użyj Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Wymagania dotyczące zarządzania ochroną przed naruszeniami w Endpoint Manager

- Urządzenia muszą być [dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint/onboarding).
- Musisz mieć [przypisane odpowiednie uprawnienia](/microsoft-365/security/defender-endpoint/assign-portal-access) , takie jak administrator globalny, administrator zabezpieczeń lub operacje zabezpieczeń.
- Organizacja używa [Microsoft Endpoint Manager do zarządzania urządzeniami](/mem/endpoint-manager-getting-started). (Microsoft Endpoint Manager licencje (MEM) są wymagane; MEM jest uwzględniony w Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3, Microsoft 365  Instytucje rządowe G3/G5 i odpowiednie licencje edukacyjne).
- Urządzenia Windows muszą działać Windows 11 lub Windows 10 [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) lub nowszym. (Aby uzyskać więcej informacji na temat wydań, zobacz [Windows 10 informacje o wersji](/windows/release-health/release-information)).
- Musisz używać zabezpieczeń Windows z [analizą zabezpieczeń](https://www.microsoft.com/wdsi/definitions) zaktualizowaną do wersji 1.287.60.0 (lub nowszej).
- Urządzenia muszą używać platformy chroniącej przed złośliwym oprogramowaniem w wersji 4.18.1906.3 (lub nowszej) i wersji `1.1.15500.X` aparatu chroniącego przed złośliwym oprogramowaniem (lub nowszym). ([Zarządzanie aktualizacjami Program antywirusowy Microsoft Defender i stosowanie planów bazowych](manage-updates-baselines-microsoft-defender-antivirus.md)).

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Włączanie (lub wyłączanie) ochrony przed naruszeniami w Microsoft Endpoint Manager

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="Włączanie ochrony przed naruszeniami przy użyciu Intune" lightbox="images/turnontamperprotectinmem.png":::

1. W [centrum administracyjnym Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do pozycji **Program antywirusowy** **zabezpieczeń** \> punktu końcowego, a następnie wybierz pozycję **+ Utwórz zasady**.

   - Na liście **Platforma** wybierz pozycję **Windows 10 i nowsze**.
   - Na liście **Profil** wybierz pozycję **Zabezpieczenia Windows środowisko**.

2. Utwórz profil zawierający następujące ustawienie:

    - **Włącz ochronę przed naruszeniami, aby zapobiec wyłączeniu usługi Microsoft Defender: Włącz**

3. Przypisz profil do co najmniej jednej grupy.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Zarządzanie ochroną przed naruszeniami w organizacji za pomocą Configuration Manager w wersji 2006

Jeśli używasz [wersji 2006 Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006), możesz zarządzać ustawieniami ochrony przed naruszeniami w Windows 10, Windows 10 Enterprise wielu sesjach, Windows 11, Windows 11 Enterprise wielu sesjach, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 i Windows Server 2022 przy użyciu metody o nazwie *dołączanie dzierżawy*. Dołączanie dzierżawy umożliwia synchronizowanie lokalnych urządzeń Configuration Manager z centrum administracyjnym Microsoft Endpoint Manager, a następnie dostarczanie zasad konfiguracji zabezpieczeń punktu końcowego do kolekcji lokalnych & urządzeniach.

> [!NOTE]
> Procedura może służyć do rozszerzania ochrony przed naruszeniami na urządzenia z systemem Windows 10, Windows 10 Enterprise wielu sesjach, Windows 11, Windows 11 Enterprise wielu sesjach, Windows Server 2019 i Windows Server 2022. Zapoznaj się z wymaganiami wstępnymi i innymi informacjami w zasobach wymienionych w tej procedurze. Do Windows Server 2012 R2 jest wymagane nowoczesne, ujednolicone rozwiązanie w [wersji 2203 Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2203).

1. Skonfiguruj dołączanie dzierżawy. Aby dowiedzieć się więcej, zobacz [Wprowadzenie: Tworzenie i wdrażanie zasad zabezpieczeń punktu końcowego z poziomu centrum administracyjnego](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. W [centrum administracyjnym Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) przejdź do pozycji **Program antywirusowy** **zabezpieczeń** \> punktu końcowego, a następnie wybierz pozycję **+ Utwórz zasady**.

   - Na liście **Platforma** wybierz pozycje **Windows 10, Windows 11 i Windows Server (ConfigMgr)**.
   - Na liście **Profil** wybierz pozycję **środowisko Zabezpieczenia Windows (wersja zapoznawcza)**.

3. Wdróż zasady w kolekcji urządzeń.

#### <a name="need-help-with-this-method"></a>Potrzebujesz pomocy dotyczącej tej metody?

Zobacz następujące zasoby:

- [Ustawienia profilu środowiska Zabezpieczenia Windows w Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Blog tech Community: ogłoszenie ochrony przed naruszeniami dla klientów dołączania dzierżawy Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Zarządzanie ochroną przed naruszeniami na poszczególnych urządzeniach

> [!NOTE]
> Ochrona przed naruszeniami blokuje próby modyfikowania ustawień Program antywirusowy Microsoft Defender za pośrednictwem rejestru.
>
> Aby zapewnić, że ochrona przed naruszeniami nie koliduje z produktami zabezpieczeń innych niż microsoft ani skryptami instalacji przedsiębiorstwa modyfikuj te ustawienia, przejdź do **Zabezpieczenia Windows** i **zaktualizuj analizę zabezpieczeń** do wersji 1.287.60.0 lub nowszej. (Zobacz [Aktualizacje analizy zabezpieczeń](https://www.microsoft.com/wdsi/definitions)). Po wprowadzeniu tej aktualizacji ochrona przed naruszeniami nadal chroni ustawienia rejestru, a dzienniki próbują je zmodyfikować bez zwracania błędów.

Jeśli jesteś użytkownikiem domowym lub nie podlegasz ustawieniu zarządzanym przez zespół ds. zabezpieczeń, możesz użyć aplikacji Zabezpieczenia Windows do zarządzania ochroną przed naruszeniami. Aby zmienić ustawienia zabezpieczeń, takie jak ochrona przed naruszeniami, musisz mieć odpowiednie uprawnienia administratora na urządzeniu.

Oto, co widzisz w aplikacji Zabezpieczenia Windows:

:::image type="content" source="images/tamperprotectionturnedon.png" alt-text="Włączanie ochrony przed naruszeniami w Windows 10 Home" lightbox="images/tamperprotectionturnedon.png":::

1. Wybierz pozycję **Start** i rozpocznij wpisywanie *pozycji Zabezpieczenia*. W wynikach wyszukiwania wybierz pozycję **Zabezpieczenia Windows**.

2. Wybierz pozycję Ochrona przed \> **zagrożeniami & wirusów** **Ustawienia ochrony przed zagrożeniami & zagrożeń**.

3. Ustaw **opcję Ochrona przed naruszeniami** na **wartość Włączone** lub **Wyłączone**.

## <a name="are-you-using-windows-server-2012-r2-2016-or-windows-version-1709-1803-or-1809"></a>Czy używasz Windows Server 2012 R2, 2016 lub Windows wersji 1709, 1803 lub 1809?

Jeśli używasz Windows Server 2012 R2 przy użyciu nowoczesnego ujednoliconego rozwiązania, Windows Server 2016, Windows 10 wersji 1709, 1803 lub [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019), nie zobaczysz **ochrony przed naruszeniami** w aplikacji Zabezpieczenia Windows. Zamiast tego można użyć programu PowerShell, aby określić, czy ochrona przed naruszeniami jest włączona.

W Windows Server 2016 aplikacja Ustawienia nie będzie dokładnie odzwierciedlać stanu ochrony w czasie rzeczywistym po włączeniu ochrony przed naruszeniami.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Użyj programu PowerShell, aby określić, czy włączono ochronę przed naruszeniami i ochronę w czasie rzeczywistym

1. Otwórz aplikację Windows PowerShell.

2. Użyj polecenia cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) programu PowerShell.

3. Na liście wyników wyszukaj `IsTamperProtected` lub `RealTimeProtectionEnabled`. (Wartość *true* oznacza, że ochrona przed naruszeniami jest włączona).

## <a name="view-information-about-tampering-attempts"></a>Wyświetlanie informacji o próbach naruszenia

Próby manipulacji zazwyczaj wskazują na większe cyberataki. Źli aktorzy próbują zmienić ustawienia zabezpieczeń jako sposób na utrwalanie i pozostawanie niewykrytymi. Jeśli jesteś członkiem zespołu ds. zabezpieczeń w organizacji, możesz wyświetlić informacje o takich próbach, a następnie podjąć odpowiednie działania w celu wyeliminowania zagrożeń.

Po wykryciu próby naruszenia alert jest zgłaszany w [portalu Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/portal-overview) ([https://security.microsoft.com](https://security.microsoft.com)).

:::image type="content" source="images/tamperattemptalert.png" alt-text="Portal Microsoft 365 Defender" lightbox="images/tamperattemptalert.png":::

Korzystając [z wykrywanie i reagowanie w punktach końcowych](overview-endpoint-detection-response.md) i zaawansowanych możliwości [wyszukiwania zagrożeń](advanced-hunting-overview.md) w Ochrona punktu końcowego w usłudze Microsoft Defender, twój zespół ds. operacji zabezpieczeń może badać i rozwiązywać takie próby.

## <a name="review-your-security-recommendations"></a>Przeglądanie zaleceń dotyczących zabezpieczeń

Ochrona przed naruszeniami integruje się z [funkcjami zarządzania lukami w zabezpieczeniach & zagrożeń](next-gen-threat-and-vuln-mgt.md) . [Zalecenia dotyczące zabezpieczeń](tvm-security-recommendation.md) obejmują upewnienie się, że ochrona przed naruszeniami jest włączona. Możesz na przykład wyszukać *manipulację*. W wynikach możesz wybrać pozycję **Włącz ochronę przed naruszeniami** , aby dowiedzieć się więcej i włączyć ją.

:::image type="content" source="images/tamperprotectsecurityrecos.png" alt-text="Włączanie ochrony przed naruszeniami w portalu Centrum zabezpieczeń usługi Microsoft Defender" lightbox="images/tamperprotectsecurityrecos.png":::

Aby dowiedzieć się więcej na temat zarządzania lukami w zabezpieczeniach & zagrożeń, zobacz [Szczegółowe informacje dotyczące pulpitu nawigacyjnego — Zarządzanie zagrożeniami i lukami](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>W jakich wersjach Windows mogę skonfigurować ochronę przed naruszeniami?

- Windows 11
- Windows 11 Enterprise wielu sesjach
- Windows 10 system operacyjny [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) lub nowszy razem z [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint).
- Windows 10 Enterprise wielu sesjach
  
Jeśli używasz Configuration Manager w wersji 2006 z dołączaniem dzierżawy, ochronę przed naruszeniami można rozszerzyć na Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 i Windows Server 2022. Zobacz [Dołączanie dzierżawy: Tworzenie i wdrażanie zasad ochrony antywirusowej zabezpieczeń punktu końcowego z centrum administracyjnego (wersja zapoznawcza).](/mem/configmgr/tenant-attach/deploy-antivirus-policy)

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>Czy ochrona przed naruszeniami wpłynie na rejestrację oprogramowania antywirusowego innej firmy niż Microsoft w aplikacji Zabezpieczenia Windows?

Nie. Oferty programów antywirusowych innych niż Microsoft będą nadal rejestrowane w aplikacji Zabezpieczenia Windows.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Co się stanie, jeśli Program antywirusowy Microsoft Defender nie jest aktywna na urządzeniu?

Urządzenia dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender będą miały Program antywirusowy Microsoft Defender uruchomione w trybie pasywnym. W takich przypadkach ochrona przed naruszeniami będzie nadal chronić usługę i jej funkcje.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Jak mogę włączyć lub wyłączyć ochronę przed naruszeniami?

Jeśli jesteś użytkownikiem domowym, zobacz [Manage tamper protection on an individual device (Zarządzanie ochroną przed naruszeniami na poszczególnych urządzeniach](#manage-tamper-protection-on-an-individual-device)).

Jeśli jesteś organizacją korzystającą z [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint), możesz zarządzać ochroną przed naruszeniami w Intune podobnie jak w przypadku zarządzania innymi funkcjami ochrony punktów końcowych. Zobacz następujące sekcje tego artykułu:

- [Zarządzanie ochroną przed naruszeniami przy użyciu Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Zarządzanie ochroną przed naruszeniami przy użyciu portalu Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Jak konfigurowanie ochrony przed naruszeniami w Intune wpływa na sposób zarządzania Program antywirusowy Microsoft Defender za pomocą zasady grupy?

Zasady grupy nie mają zastosowania do ochrony przed naruszeniami. Zmiany wprowadzone w ustawieniach Program antywirusowy Microsoft Defender są ignorowane, gdy ochrona przed naruszeniami jest włączona.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Jeśli używamy Microsoft Intune do skonfigurowania ochrony przed naruszeniami, czy ma ona zastosowanie tylko do całej organizacji?

Masz elastyczność w konfigurowaniu ochrony przed naruszeniami za pomocą Intune. Możesz kierować dane do całej organizacji lub wybrać określone urządzenia i grupy użytkowników.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Czy mogę skonfigurować ochronę przed naruszeniami przy użyciu Microsoft Endpoint Configuration Manager?

Jeśli używasz dołączania dzierżawy, możesz użyć Microsoft Endpoint Configuration Manager. Zobacz następujące zasoby:

- [Zarządzanie ochroną przed naruszeniami w organizacji za pomocą Configuration Manager w wersji 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Blog tech Community: ogłoszenie ochrony przed naruszeniami dla klientów dołączania dzierżawy Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>Mam rejestrację Windows E3. Czy można skonfigurować ochronę przed naruszeniami w Intune?

Obecnie konfigurowanie ochrony przed naruszeniami w Intune jest dostępne tylko dla klientów, którzy mają [Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Co się stanie, jeśli spróbuję zmienić ustawienia Ochrona punktu końcowego w usłudze Microsoft Defender w Intune, Microsoft Endpoint Configuration Manager i instrumentacji zarządzania Windows podczas ochrony przed naruszeniami jest włączona na urządzeniu?

Nie będzie można zmienić funkcji chronionych przez ochronę przed naruszeniami. takie żądania zmiany są ignorowane.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Jestem klientem korporacyjnym. Czy administratorzy lokalni mogą zmienić ochronę przed naruszeniami na swoich urządzeniach?

Nie. Administratorzy lokalni nie mogą zmieniać ani modyfikować ustawień ochrony przed naruszeniami.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Co się stanie, jeśli moje urządzenie zostanie dołączone do Ochrona punktu końcowego w usłudze Microsoft Defender, a następnie przejdzie w stan off-boarded?

Jeśli urządzenie jest wyłączone z Ochrona punktu końcowego w usłudze Microsoft Defender, jest włączona ochrona przed naruszeniami, co jest stanem domyślnym dla urządzeń niezarządzanych.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Czy w przypadku zmiany stanu ochrony przed naruszeniami alerty są wyświetlane w portalu Microsoft 365 Defender?

Tak. Alert jest wyświetlany w obszarze [https://security.microsoft.com](https://security.microsoft.com) **Alerty**.

Twój zespół ds. operacji zabezpieczeń może również używać zapytań wyszukiwania zagrożeń, takich jak następujący przykład:

`AlertInfo|where Title == "Tamper Protection bypass"`

[Wyświetl informacje o próbach naruszenia](#view-information-about-tampering-attempts).

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie komputerów Windows przy użyciu Endpoint Protection dla Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Omówienie Ochrona punktu końcowego w usłudze Microsoft Defender](/microsoft-365/security/defender-endpoint)
- [Lepiej razem: program antywirusowy Microsoft Defender i usługa ochrony punktu końcowego w usłudze Microsoft Defender](why-use-microsoft-defender-antivirus.md)
- [Włącz tryb rozwiązywania problemów](enable-troubleshooting-mode.md)
- [Scenariusze trybu rozwiązywania problemów](troubleshooting-mode-scenarios.md)
