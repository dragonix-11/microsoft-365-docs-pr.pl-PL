---
title: Opis i używanie zmniejszania powierzchni ataków (ASR)
ms.reviewer: ''
description: Dowiedz się więcej o możliwościach zmniejszenia powierzchni ataków usługi Microsoft Defender dla punktu końcowego.
keywords: asr, zmniejszenie powierzchni ataków, Microsoft Defender for Endpoint, microsoft defender, antivirus, av, windows defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.custom: asr
ms.topic: conceptual
ms.technology: mde
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 9c489d28467582e0f95f3fde7440ff43022c44e1
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682047"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>Opis funkcji ograniczania powierzchni ataków i korzystanie z nich

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Powierzchnie ataków to wszystkie miejsca, w których Twoja organizacja jest narażona na cyberataki i ataki. Program Defender for Endpoint zawiera kilka możliwości pomagania w zmniejszania powierzchni ataków. Obejrzyj poniższy klip wideo, aby dowiedzieć się więcej o zmniejszaniu powierzchni ataków.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>Konfigurowanie możliwości zmniejszania powierzchni ataków

Aby skonfigurować zmniejszenie powierzchni ataków w środowisku, wykonaj następujące czynności:

1. [Włącz izolacji sprzętowej dla Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. Włącz kontrolkę aplikacji.

   1. Przejrzyj zasady podstawowe w programie Windows. Zobacz [Przykładowe zasady podstawowe](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. Zobacz Windows Defender [projektu kontrolki aplikacji](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. Zobacz [Wdrażanie zasad Windows Defender (WDAC](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)).

3. [Włączanie kontrolowanego dostępu do folderu](enable-controlled-folders.md).

4. [Włącz ochronę sieci](enable-network-protection.md).

5. [Włączanie ochrony przed lukami w zabezpieczeniach](enable-exploit-protection.md).

6. [Wdrażanie reguł ograniczania powierzchni ataków](attack-surface-reduction-rules-deployment.md).

7. Skonfiguruj zaporę sieciową.

   1. Poznaj omówienie zapory [Windows Defender z zaawansowanymi zabezpieczeniami](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. Skorzystaj z [przewodnika Windows Defender projektu](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) zapory, aby określić sposób projektowania zasad zapory.
   3. Skorzystaj z [Windows Defender wdrażania](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) zapory sieciowej, aby skonfigurować zaporę organizacji z zaawansowanymi zabezpieczeniami.

> [!TIP]
> W większości przypadków po skonfigurowaniu funkcji zmniejszania powierzchni ataków można wybrać jedną z kilku metod:
>
> - Microsoft Endpoint Manager (która obejmuje teraz Microsoft Intune i Microsoft Endpoint Configuration Manager)
> - zasady grupy
> - Polecenia cmdlet programu PowerShell

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Zmniejszanie powierzchni ataków w programie Microsoft Defender dla punktu końcowego

W ramach zespołu zabezpieczeń organizacji możesz skonfigurować funkcje zmniejszania powierzchni ataków, aby uruchamiać się w trybie inspekcji, aby zobaczyć, jak będą działać. W trybie inspekcji można włączyć:

- Reguły zmniejszania obszaru podatnego na ataki
- Exploit Protection
- Ochrona sieci
- Kontrolowany dostęp do folderu w trybie inspekcji

Tryb inspekcji umożliwia wyświetlanie informacji o tym, co  się stało, jeśli włączono tę funkcję.

Możesz włączyć tryb inspekcji podczas testowania działania funkcji. Włączenie trybu inspekcji tylko na potrzeby testowania pomaga zapobiec wpływaniu trybu inspekcji na aplikacje firmowe. Możesz również dowiedzieć się, ile podejrzanych prób modyfikacji pliku ma miejsce w określonym czasie.

Te funkcje nie blokują ani nie zapobiegają modyfikacji aplikacji, skryptów ani plików. Jednak dziennik Windows zdarzeń będzie rejestrować zdarzenia tak, jakby funkcje były w pełni włączone. W trybie inspekcji możesz przejrzeć dziennik zdarzeń, aby sprawdzić, jaki wpływ ma na tę funkcję, gdyby została włączona.

Aby znaleźć wpisy, które są pod kontrolą, przejdź do **pozycji** \> Aplikacje i usługi firmy **Microsoft** \>  \> Windows **Windows Defender** \> **operacyjne**.

Użyj usługi Defender for Endpoint, aby uzyskać bardziej szczegółowe informacje na temat poszczególnych wydarzeń. Te szczegóły są szczególnie przydatne w przypadku badania reguł ograniczania powierzchni ataków. Korzystanie z konsoli programu Defender dla punktu końcowego umożliwia [badanie problemów w ramach osi czasu alertu i scenariuszy badania](investigate-alerts.md).

Tryb inspekcji można włączyć przy zasady grupy, programu PowerShell i dostawców usług konfiguracji.

> [!TIP]
> Możesz również odwiedzić witrynę Windows Defender Testground w witrynie demo.wd.microsoft.com, aby [](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) sprawdzić, czy funkcje działają i jak działają.

> [!NOTE]
> Witryna pokazowa usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

| Opcje inspekcji | Jak włączyć tryb inspekcji | Jak wyświetlić zdarzenia |
|---|---|---|
| Inspekcja dotyczy wszystkich zdarzeń | [Włączanie kontrolowanego dostępu do folderu](enable-controlled-folders.md) | [Zdarzenia kontrolowanego dostępu do folderu](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| Inspekcja dotyczy poszczególnych reguł | [Krok 1. Testowanie reguł asr przy użyciu inspekcji](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [Krok 2. Opis strony raportowania reguł ograniczania powierzchni ataków](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| Inspekcja dotyczy wszystkich zdarzeń | [Włączanie ochrony sieci](enable-network-protection.md) | [Zdarzenia ochrony sieci](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| Inspekcja dotyczy pojedynczych środków zaradczych | [Włączanie ochrony przed lukami w zabezpieczeniach](enable-exploit-protection.md) | [Exploit Protection events](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

## <a name="view-attack-surface-reduction-events"></a>Wyświetlanie zdarzeń zmniejszenia powierzchni ataków

Przejrzyj zdarzenia zmniejszenia powierzchni ataków w Podglądzie zdarzeń, aby monitorować, jakie reguły lub ustawienia działają. Można także określić, czy jakiekolwiek ustawienia są zbyt "głośne" lub mają wpływ na przebieg twojego dnia pracy.

Recenzowanie zdarzeń jest przydatne podczas oceny funkcji. Możesz włączyć tryb inspekcji dla funkcji lub ustawień, a następnie sprawdzić, co się stało, gdyby były w pełni włączone.

W tej sekcji wymieniono wszystkie zdarzenia, skojarzone z nimi funkcje lub ustawienia oraz opisano sposób tworzenia widoków niestandardowych w celu filtrowania w celu filtrowania w celu określonych zdarzeń.

Uzyskaj szczegółowe raportowanie zdarzeń, bloków i ostrzeżeń w ramach usługi Zabezpieczenia Windows jeśli masz subskrypcję E5 i używasz programu [Microsoft Defender dla punktu końcowego](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>Przeglądanie możliwości ograniczania powierzchni ataków za pomocą widoków niestandardowych

Tworzenie niestandardowych widoków w przeglądarce Windows zdarzeń, aby wyświetlać tylko zdarzenia pod określonymi możliwościami i ustawieniami. Najłatwiejszym sposobem jest zaimportowanie widoku niestandardowego jako pliku XML. Kod XML można skopiować bezpośrednio z tej strony.

Możesz także ręcznie przejść do obszaru zdarzenia odpowiadającego tej funkcji.

#### <a name="import-an-existing-xml-custom-view"></a>Importowanie istniejącego widoku niestandardowego XML

1. Utwórz pusty .txt pliku i skopiuj plik XML do widoku niestandardowego, którego chcesz użyć, do .txt pliku. Zrób to dla każdego z widoków niestandardowych, którego chcesz użyć. Zmień nazwy plików w następujący sposób (upewnij się, że zmieniasz typ z .txt na .xml):
    - Widok niestandardowy zdarzeń o kontrolowanym dostępie do *folderu:cfa-events.xml*
    - Widok niestandardowy zdarzeń ochrony przed wykorzystywaniem luk: *ep-events.xml*
    - Niestandardowy widok wydarzeń zmniejszania powierzchni ataków: *asr-events.xml*
    - Widok niestandardowy zdarzeń sieci/ochrony: *np-events.xml*

2. Wpisz **nazwę podglądu zdarzeń** w menu Start i otwórz **podgląd zdarzeń**.

3. Wybierz **pozycję Akcja importu** \> **widoku niestandardowego...**

   > [!div class="mx-imgBorder"]
   > ![Wyróżnienie animacji Importuj widok niestandardowy po lewej stronie okna podglądu Nawet.](images/events-import.gif)

4. Przejdź do wybranego miejsca wyodrębnienia pliku XML dla odpowiedniego widoku niestandardowego i wybierz go.

5. Wybierz opcję **Otwórz**.

6. Spowoduje to utworzenie widoku niestandardowego, który filtruje w celu pokazania tylko zdarzeń związanych z tę funkcją.

#### <a name="copy-the-xml-directly"></a>Bezpośrednie kopiowanie pliku XML

1. Wpisz **podgląd zdarzeń** w menu Start i otwórz okno Windows **Podgląd zdarzeń**.

2. W panelu po lewej stronie w **obszarze Akcje** wybierz **pozycję Utwórz widok niestandardowy...**

   > [!div class="mx-imgBorder"]
   > ![Animacja z wyróżniona opcją utwórz widok niestandardowy w oknie podglądu zdarzeń.](images/events-create.gif)

3. Przejdź do karty XML i wybierz **pozycję Edytuj zapytanie ręcznie**. Jeśli używasz opcji XML, zobaczysz ostrzeżenie, że nie możesz edytować zapytania za pomocą karty  Filtr. Wybierz opcję **Tak**.

4. Wklej kod XML funkcji, z której chcesz filtrować zdarzenia, w sekcji XML.

5. Wybierz przycisk **OK**. Określ nazwę filtru. Powoduje to utworzenie widoku niestandardowego, który filtruje w celu pokazania tylko zdarzeń związanych z tą funkcją.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>Kod XML do zmniejszania powierzchni ataków ze zdarzeniami reguły

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>Kod XML na zdarzenia kontrolowanego dostępu do folderu

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-exploit-protection-events"></a>Plik XML na przykład w celu ochrony przed lukami

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Security-Mitigations/KernelMode">
   <Select Path="Microsoft-Windows-Security-Mitigations/KernelMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Concurrency">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Contention">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Messages">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Operational">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Power">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Render">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Tracing">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/UIPI">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="System">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Security-Mitigations/UserMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-network-protection-events"></a>Kod XML na zdarzenia ochrony sieci

```xml
<QueryList>
 <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
  <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
  <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
 </Query>
</QueryList>
```

### <a name="list-of-attack-surface-reduction-events"></a>Lista zdarzeń zmniejszenia powierzchni ataków

Wszystkie zdarzenia zmniejszenia powierzchni ataków znajdują się w obszarze Dzienniki aplikacji i usług **> microsoft > Windows** a następnie folder lub dostawca wymienione w poniższej tabeli.

Dostęp do tych zdarzeń można uzyskać w przeglądarce Windows zdarzeń:

1. Otwórz menu **Start** i wpisz **podgląd zdarzeń**, a następnie wybierz wynik **podglądu** zdarzeń.
2. **Rozwiń pozycję Dzienniki aplikacji i usług > microsoft > Windows**, a następnie przejdź do folderu na liście w obszarze Dostawca **/** źródło w poniższej tabeli.
3. Kliknij dwukrotnie podmenu, aby wyświetlić zdarzenia. Przewiń zdarzenia, aby znaleźć to, którego szukasz.

   ![Animacja pokazywana za pomocą Podglądu zdarzeń.](images/event-viewer.gif)

<br>

****

|Funkcja|Dostawca/źródło|Identyfikator zdarzenia|Opis|
|---|---|:---:|---|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|1|Inspekcja ACG|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|2|Wymuszanie ACG|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|3|Nie zezwalaj na inspekcję procesów podrzędnych|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|4|Nie zezwalaj na blokowanie procesów podrzędnych|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|5|Blokowanie inspekcji obrazów o niskiej integralności|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|6|Blokowanie bloku obrazów o niskiej integralności|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|7|Blokowanie inspekcji obrazów zdalnych|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|8|Blokowanie bloku obrazów zdalnych|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|9|Wyłączanie inspekcji połączeń systemowych win32k|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|10|Wyłączanie blokowania połączeń systemowych win32k|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|11|Inspekcja ochrony integralności kodu|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|12|Blok ochrony integralności kodu|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|13|Inspekcja EAF|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|14|Wymuszanie EAF|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|15|Inspekcja + EAF|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|16|EAF+ wymuszanie|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|17|Inspekcja IAF|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|18|Wymuszanie IAF|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|19|INSPEKCJA STACKPivot|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|20|WYMUSZANIE STACK StackPivot|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|21|AUDIT CallerCheck audit|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|22|WYMUSZANIE PRZEZ CALLerCheck|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|23|INSPEKCJA SIMExec|
|Exploit Protection|Security-Mitigations (tryb kernel/tryb użytkownika)|24|WYMUSZANIE KARTY SimExec|
|Exploit Protection|WER-Diagnostics|5|Blok CFG|
|Exploit Protection|Win32K (operacyjny)|260|Czcionka niezaufana|
|Ochrona sieci|Windows Defender (operacyjne)|5007|Zdarzenie w przypadku zmiany ustawień|
|Ochrona sieci|Windows Defender (operacyjne)|1125|Zdarzenie, gdy ochrona sieci jest w trybie inspekcji|
|Ochrona sieci|Windows Defender (operacyjne)|1126|Zdarzenie, gdy ochrona sieci jest wyzb. w trybie blokowania|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|5007|Zdarzenie w przypadku zmiany ustawień|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1124|Zdarzenie kontrolowanego dostępu do folderu|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1123|Zdarzenie zablokowanego dostępu do folderu sterowanego|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1127|Zdarzenie bloków zapisu zablokowanego dostępu do folderu kontrolowanego przez sektora|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1128|Zdarzenie blokady zapisu dla kontrolowanego folderu dostępu z sektora kontrolowanego|
|Zmniejszenie powierzchni ataków|Windows Defender (operacyjne)|5007|Zdarzenie w przypadku zmiany ustawień|
|Zmniejszenie powierzchni ataków|Windows Defender (operacyjne)|1122|Zdarzenie, gdy reguła jest w trybie inspekcji|
|Zmniejszenie powierzchni ataków|Windows Defender (operacyjne)|1121|Zdarzenie, gdy reguła zostanie wyzb. w trybie blokowania|

>[!NOTE]
> Z perspektywy użytkownika powiadomienia w trybie ostrzegania ASR są wyświetlane jako wyskakujące powiadomienie Windows do zasad zmniejszania powierzchni ataków.
>
> W trybie ASR ochrona sieci zapewnia tylko tryby inspekcji i blokowania.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>Zasoby, aby dowiedzieć się więcej o zmniejszeniu powierzchni ataków

Jak wspomniano w tym klipie wideo, program Defender for Endpoint zawiera kilka możliwości ograniczania powierzchni ataków. Skorzystaj z następujących zasobów, aby dowiedzieć się więcej:

| Artykuł | Opis |
|:---|:---|
| [Izolacji na podstawie sprzętu](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | Ochrona i zachowywanie integralności systemu podczas jego uruchamiania i działania. Sprawdzaj integralność systemu za pośrednictwem lokalnych i zdalnych poświadczenia. Użyj izolacji kontenera na Microsoft Edge, aby chronić przed złośliwymi witrynami internetowymi. |
| [Kontrolka aplikacji](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | Użyj kontrolki aplikacji, aby aplikacje zdobywały zaufanie, aby można było je uruchomić. |
| [Kontrolowany dostęp do folderu](controlled-folders.md) | Ochrona przed złośliwymi lub podejrzanymi aplikacjami (w tym złośliwym oprogramowaniem wymuszającym okup szyfrującym pliki) przed wprowadzeniem zmian w plikach w kluczowych folderach systemowych (wymaga ochrony przed Program antywirusowy Microsoft Defender) |
| [Ochrona sieci](network-protection.md) | Rozszerzanie ochrony ruchu sieciowego i łączności na urządzeniach organizacji. (Wymaga Program antywirusowy Microsoft Defender) |
| [Exploit Protection](exploit-protection.md) | Pomóż chronić systemy operacyjne i aplikacje używane przez Twoją organizację przed wykorzystywaniem ich. Exploit Protection działa również z rozwiązaniami antywirusowymi innych firm. |
| [Reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction.md) | Ogranicz luki w zabezpieczeniach (powierzchnie ataków) w aplikacjach za pomocą inteligentnych reguł, które pomagają w zatrzymaniu złośliwego oprogramowania. (Wymaga Program antywirusowy Microsoft Defender). |
| [Sterowanie urządzeniem](device-control-report.md) | Zapewnia ochronę przed utratą danych, monitorując i kontrolując nośniki używane na urządzeniach, takich jak magazyn wymienny i dyski USB, w organizacji. |
