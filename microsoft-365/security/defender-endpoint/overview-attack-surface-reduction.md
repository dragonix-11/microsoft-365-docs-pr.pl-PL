---
title: Omówienie i używanie zmniejszania obszaru ataków (ASR)
ms.reviewer: ''
description: Dowiedz się więcej o możliwościach zmniejszania obszaru ataków Ochrona punktu końcowego w usłudze Microsoft Defender.
keywords: asr, attack surface reduction, attack surface reduction rules, Ochrona punktu końcowego w usłudze Microsoft Defender, microsoft defender, antivirus, av, windows defender
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
ms.openlocfilehash: 5b71134f9a7d33880e9762701e825c3fbf708f6b
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705094"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>Omówienie możliwości zmniejszania obszaru ataków i korzystanie z nich

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Powierzchnie ataków to wszystkie miejsca, w których organizacja jest narażona na ataki cybernetyczne i ataki. Usługa Defender for Endpoint oferuje kilka możliwości, które ułatwiają zmniejszenie obszarów ataków. Obejrzyj poniższy film wideo, aby dowiedzieć się więcej na temat zmniejszania obszaru podatnego na ataki.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>Konfigurowanie możliwości zmniejszania obszaru ataków

Aby skonfigurować redukcję obszaru ataków w środowisku, wykonaj następujące kroki:

1. [Włącz izolację sprzętową dla Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. Włącz kontrolę aplikacji.

   1. Przejrzyj zasady podstawowe w Windows. Zobacz [przykładowe zasady podstawowe](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. Zobacz [przewodnik projektowania Windows Defender Application Control](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. Zapoznaj się z [tematem Wdrażanie zasad Windows Defender kontroli aplikacji (WDAC](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)).

3. [Włącz kontrolowany dostęp do folderu](enable-controlled-folders.md).

4. [Włącz ochronę sieci](enable-network-protection.md).

5. [Włącz ochronę przed lukami w zabezpieczeniach](enable-exploit-protection.md).

6. [Wdrażanie reguł zmniejszania obszaru ataków](attack-surface-reduction-rules-deployment.md).

7. Skonfiguruj zaporę sieciową.

   1. Zapoznaj się z omówieniem [zapory Windows Defender z zaawansowanymi zabezpieczeniami](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. Skorzystaj z [przewodnika projektowania zapory Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide), aby zdecydować, jak chcesz zaprojektować zasady zapory.
   3. Użyj [przewodnika wdrażania zapory Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide), aby skonfigurować zaporę organizacji z zaawansowanymi zabezpieczeniami.

> [!TIP]
> W większości przypadków podczas konfigurowania możliwości zmniejszania obszaru podatnego na ataki można wybrać jedną z kilku metod:
>
> - Microsoft Endpoint Manager (w tym Microsoft Intune i Microsoft Endpoint Configuration Manager)
> - Zasady grupy
> - Polecenia cmdlet programu PowerShell

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Zmniejszanie obszaru ataków testowych w Ochrona punktu końcowego w usłudze Microsoft Defender

W ramach zespołu ds. zabezpieczeń w organizacji możesz skonfigurować możliwości zmniejszania obszaru ataków, aby uruchamiać je w trybie inspekcji, aby zobaczyć, jak będą one działać. W trybie inspekcji można włączyć następujące funkcje zabezpieczeń usługi ASR:

- Reguły zmniejszania obszaru podatnego na ataki
- Ochrona przed wykorzystywaniem
- Ochrona sieci
- I kontrolowany dostęp do folderu

Tryb inspekcji umożliwia wyświetlenie rekordu, co *by* się stało, gdyby włączono tę funkcję.

Tryb inspekcji można włączyć podczas testowania działania funkcji. Włączenie trybu inspekcji tylko na potrzeby testowania pomaga zapobiegać wpływowi trybu inspekcji na aplikacje biznesowe. Możesz również poznać liczbę podejrzanych prób modyfikacji plików w określonym okresie.

Funkcje nie blokują ani nie uniemożliwiają modyfikowania aplikacji, skryptów ani plików. Jednak dziennik zdarzeń Windows będzie rejestrować zdarzenia tak, jakby funkcje były w pełni włączone. W trybie inspekcji możesz przejrzeć dziennik zdarzeń, aby zobaczyć, jaki wpływ miałaby funkcja, gdyby została włączona.

Aby znaleźć inspekcję wpisów, przejdź do **obszaru Aplikacje i usługi** \> **Microsoft** \> **Windows** \> **Windows Defender** \> **Operational**.

Użyj usługi Defender for Endpoint, aby uzyskać więcej szczegółów dotyczących każdego zdarzenia. Te szczegóły są szczególnie przydatne w badaniu reguł zmniejszania obszaru podatnego na ataki. Korzystanie z konsoli usługi Defender for Endpoint umożliwia [badanie problemów w ramach osi czasu alertów i scenariuszy badania](investigate-alerts.md).

Tryb inspekcji można włączyć przy użyciu dostawców usług zasady grupy, PowerShell i konfiguracji.

> [!TIP]
> Możesz również odwiedzić witrynę internetową Windows Defender Testground pod adresem [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground), aby potwierdzić, że funkcje działają i zobaczyć, jak działają.

> [!NOTE]
> Witryna demonstracyjna usługi Defender for Endpoint w demo.wd.microsoft.com jest przestarzała i zostanie usunięta w przyszłości.

| Opcje inspekcji | Jak włączyć tryb inspekcji | Jak wyświetlać zdarzenia |
|---|---|---|
| Inspekcja dotyczy wszystkich zdarzeń | [Włącz kontrolowany dostępu do folderu](enable-controlled-folders.md) | [Zdarzenia dostępu do kontrolowanych folderów](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| Inspekcja ma zastosowanie do poszczególnych reguł | [Krok 1. Testowanie reguł usługi ASR przy użyciu trybu inspekcji](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [Krok 2. Omówienie strony raportowania reguł zmniejszania obszaru ataków](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| Inspekcja dotyczy wszystkich zdarzeń | [Włączanie ochrony sieci](enable-network-protection.md) | [Zdarzenia ochrony sieci](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| Inspekcja ma zastosowanie do poszczególnych środków zaradczych | [Włącz ochronę przed wykorzystaniem](enable-exploit-protection.md) | [Zdarzenia ochrony przed lukami w zabezpieczeniach](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

### <a name="attack-surface-reduction-asr-rules"></a>Reguły zmniejszania obszaru podatnego na ataki

Reguły zmniejszania obszaru ataków (ASR) są wstępnie zdefiniowane w celu wzmacniania typowych, znanych obszarów ataków. Istnieje kilka metod, za pomocą których można zaimplementować reguły zmniejszania obszaru podatnego na ataki. Preferowana metoda jest udokumentowana w następujących tematach wdrażania reguł zmniejszania obszaru ataków (ASR):

- [Omówienie wdrażania reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment.md)
- [Planowanie wdrożenia reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-plan.md)
- [Reguły zmniejszania obszaru ataków testowych (ASR)](attack-surface-reduction-rules-deployment-test.md)
- [Włączanie reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-implement.md)
- [Operacjonalizowanie reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="view-attack-surface-reduction-events"></a>Wyświetlanie zdarzeń redukcji obszaru ataków

Przejrzyj zdarzenia zmniejszania obszaru ataków w Podgląd zdarzeń, aby monitorować, jakie reguły lub ustawienia działają. Możesz również określić, czy jakiekolwiek ustawienia są zbyt "hałaśliwe" lub mają wpływ na przepływ pracy z dnia na dzień.

Przeglądanie zdarzeń jest przydatne podczas oceny funkcji. Możesz włączyć tryb inspekcji dla funkcji lub ustawień, a następnie sprawdzić, co by się stało, gdyby były w pełni włączone.

W tej sekcji wymieniono wszystkie zdarzenia, skojarzoną z nimi funkcję lub ustawienie oraz opisano sposób tworzenia widoków niestandardowych w celu filtrowania do określonych zdarzeń.

Uzyskaj szczegółowe raporty dotyczące zdarzeń, bloków i ostrzeżeń w ramach Zabezpieczenia Windows, jeśli masz subskrypcję E5 i używasz [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>Przeglądanie możliwości zmniejszania obszaru podatnego na ataki przy użyciu widoków niestandardowych

Utwórz widoki niestandardowe w Windows Podgląd zdarzeń, aby wyświetlać zdarzenia tylko dla określonych możliwości i ustawień. Najprostszym sposobem jest zaimportowanie widoku niestandardowego jako pliku XML. Kod XML można skopiować bezpośrednio z tej strony.

Możesz również ręcznie przejść do obszaru zdarzeń, który odpowiada funkcji.

#### <a name="import-an-existing-xml-custom-view"></a>Importowanie istniejącego widoku niestandardowego XML

1. Utwórz pusty plik .txt i skopiuj plik XML dla widoku niestandardowego, którego chcesz użyć, do pliku .txt. Zrób to dla każdego z widoków niestandardowych, których chcesz użyć. Zmień nazwę plików w następujący sposób (upewnij się, że typ został zmieniony z .txt na .xml):
    - Widok niestandardowy zdarzeń dostępu do folderów kontrolowanych: *cfa-events.xml*
    - Widok niestandardowy zdarzeń ochrony przed lukami w zabezpieczeniach: *ep-events.xml*
    - Niestandardowy widok zdarzeń zmniejszania obszaru ataków: *asr-events.xml*
    - Widok niestandardowy zdarzeń sieci/ochrony: *np-events.xml*

2. Wpisz **podgląd zdarzeń** w menu Start i otwórz **Podgląd zdarzeń**.

3. Wybierz pozycję **Akcja** \> **Importuj widok niestandardowy...**

   > [!div class="mx-imgBorder"]
   > ![Animacja wyróżniająca widok niestandardowy Importuj po lewej stronie okna Podgląd parzystych.](images/events-import.gif)

4. Przejdź do miejsca wyodrębnienia pliku XML dla żądanego widoku niestandardowego i wybierz go.

5. Wybierz opcję **Otwórz**.

6. Utworzy on niestandardowy widok, który filtruje tylko zdarzenia związane z tą funkcją.

#### <a name="copy-the-xml-directly"></a>Bezpośrednie kopiowanie kodu XML

1. Wpisz **podgląd zdarzeń** w menu Start i otwórz **Podgląd zdarzeń Windows**.

2. Na panelu po lewej stronie w obszarze **Akcje** wybierz pozycję **Utwórz widok niestandardowy...**

   > [!div class="mx-imgBorder"]
   > ![Animacja wyróżniająca opcję utwórz widok niestandardowy w oknie Podgląd zdarzeń.](images/events-create.gif)

3. Przejdź do karty XML i ręcznie wybierz pozycję **Edytuj zapytanie**. Zobaczysz ostrzeżenie, że nie możesz edytować zapytania przy użyciu karty **Filtr** , jeśli używasz opcji XML. Wybierz opcję **Tak**.

4. Wklej kod XML funkcji, z której chcesz filtrować zdarzenia, do sekcji XML.

5. Wybierz przycisk **OK**. Określ nazwę filtru. Spowoduje to utworzenie widoku niestandardowego, który filtruje tylko zdarzenia związane z tą funkcją.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>XML dla zdarzeń reguły zmniejszania obszaru ataków

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>XML dla zdarzeń dostępu do folderów kontrolowanych

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-exploit-protection-events"></a>KOD XML dla zdarzeń ochrony przed lukami w zabezpieczeniach

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

#### <a name="xml-for-network-protection-events"></a>XML dla zdarzeń ochrony sieci

```xml
<QueryList>
 <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
  <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
  <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
 </Query>
</QueryList>
```

### <a name="list-of-attack-surface-reduction-events"></a>Lista zdarzeń zmniejszania obszaru ataków

Wszystkie zdarzenia zmniejszania obszaru ataków znajdują się w obszarze **Dzienniki aplikacji i usług > microsoft > Windows**, a następnie folder lub dostawca, jak wymieniono w poniższej tabeli.

Dostęp do tych zdarzeń można uzyskać w przeglądarce zdarzeń Windows:

1. Otwórz menu **Start** i wpisz **podgląd zdarzeń**, a następnie wybierz **wynik Podgląd zdarzeń**.
2. Rozwiń węzeł **Dzienniki aplikacji i usług > microsoft > Windows**, a następnie przejdź do folderu wymienionego w obszarze **Dostawca/źródło** w poniższej tabeli.
3. Kliknij dwukrotnie element podrzędny, aby wyświetlić zdarzenia. Przewiń zdarzenia, aby znaleźć ten, którego szukasz.

   ![Animacja przedstawiająca użycie Podgląd zdarzeń.](images/event-viewer.gif)

<br>

****

|Funkcja|Dostawca/źródło|Identyfikator zdarzenia|Opis|
|---|---|:---:|---|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|1|Inspekcja acg|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|2|Wymuszanie acg|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|3|Nie zezwalaj na inspekcję procesów podrzędnych|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|4|Nie zezwalaj na blok procesów podrzędnych|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|5|Blokuj inspekcję obrazów o niskiej integralności|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|6|Blokuj blok obrazów o niskiej integralności|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|7|Blokuj inspekcję obrazów zdalnych|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|8|Blokuj zdalny blok obrazów|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|9|Wyłączanie inspekcji wywołań systemowych win32k|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|10|Wyłącz blok wywołań systemowych win32k|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|11|Inspekcja ochrony integralności kodu|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|12|Blok ochrony integralności kodu|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|13|Inspekcja zapory aplikacji internetowej|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|14|Wymuszanie zapory aplikacji internetowej|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|15|Inspekcja EAF+|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|16|Wymuszanie aplikacji EAF+|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|17|Inspekcja zapory aplikacji internetowej|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|18|Wymuszanie zapory aplikacji internetowej|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|19|Inspekcja ROP StackPivot|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|20|Wymuszanie ROP StackPivot|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|21|Inspekcja kontroli wywołań ROP|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|22|Wymuszanie wywołania ROP|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|23|Inspekcja ROP SimExec|
|Ochrona przed wykorzystywaniem|Security-Mitigations (tryb jądra/tryb użytkownika)|24|Wymuszanie ROP SimExec|
|Ochrona przed wykorzystywaniem|WER-Diagnostics|5|Blok CFG|
|Ochrona przed wykorzystywaniem|Win32K (operacyjny)|260|Niezaufane czcionki|
|Ochrona sieci|Windows Defender (operacyjne)|5007|Zdarzenie po zmianie ustawień|
|Ochrona sieci|Windows Defender (operacyjne)|1125|Zdarzenie, gdy ochrona sieci jest uruchamiana w trybie inspekcji|
|Ochrona sieci|Windows Defender (operacyjne)|1126|Zdarzenie, gdy ochrona sieci jest uruchamiana w trybie bloku|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|5007|Zdarzenie po zmianie ustawień|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1124|Zdarzenie inspekcji dostępu do folderów kontrolowanych|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1123|Zablokowane zdarzenie dostępu do folderu kontrolowanego|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1127|Zablokowane zdarzenie bloku zapisu w sektorze dostępu do folderów kontrolowanych|
|Kontrolowany dostęp do folderu|Windows Defender (operacyjne)|1128|Zdarzenie bloku zapisu w sektorze inspekcji dostępu do folderów kontrolowanych|
|Zmniejszanie obszaru podatnego na ataki|Windows Defender (operacyjne)|5007|Zdarzenie po zmianie ustawień|
|Zmniejszanie obszaru podatnego na ataki|Windows Defender (operacyjne)|1122|Zdarzenie, gdy reguła jest uruchamiana w trybie inspekcji|
|Zmniejszanie obszaru podatnego na ataki|Windows Defender (operacyjne)|1121|Zdarzenie, gdy reguła jest uruchamiana w trybie bloku|

>[!NOTE]
> Z perspektywy użytkownika powiadomienia w trybie ostrzeżenia usługi ASR są tworzone jako Windows powiadomienia wyskakujące dla reguł zmniejszania obszaru ataków.
>
> W usłudze ASR usługa Network Protection udostępnia tylko tryby inspekcji i bloku.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>Zasoby, aby dowiedzieć się więcej na temat zmniejszania obszaru ataków

Jak wspomniano w filmie wideo, usługa Defender for Endpoint oferuje kilka możliwości zmniejszania obszaru ataków. Aby dowiedzieć się więcej, skorzystaj z następujących zasobów:

| Artykułu | Opis |
|:---|:---|
| [Izolacja sprzętowa](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | Chroń i zachowaj integralność systemu podczas uruchamiania i podczas jego działania. Weryfikowanie integralności systemu za pomocą lokalnego i zdalnego zaświadczania. Użyj izolacji kontenera dla Microsoft Edge, aby chronić przed złośliwymi witrynami internetowymi. |
| [Kontrola aplikacji](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | Użyj kontroli aplikacji, aby aplikacje mogły uzyskiwać zaufanie do uruchamiania. |
| [Kontrolowany dostęp do folderu](controlled-folders.md) | Zapobieganie złośliwym lub podejrzanym aplikacjom (w tym złośliwemu oprogramowaniu wymuszającemu szyfrowanie plików) przed wprowadzaniem zmian w plikach w kluczowych folderach systemowych (wymaga Program antywirusowy Microsoft Defender) |
| [Ochrona sieci](network-protection.md) | Rozszerzanie ochrony ruchu sieciowego i łączności na urządzeniach organizacji. (Wymaga Program antywirusowy Microsoft Defender) |
| [Ochrona przed wykorzystywaniem](exploit-protection.md) | Ochrona systemów operacyjnych i aplikacji używanych przez organizację przed wykorzystywaniem. Ochrona przed lukami w zabezpieczeniach działa również z rozwiązaniami antywirusowymi innych firm. |
| [Sterowanie urządzeniem](device-control-report.md) | Chroni przed utratą danych przez monitorowanie i kontrolowanie nośników używanych na urządzeniach, takich jak magazyn wymienny i dyski USB, w organizacji. |
| [Przewodnik wdrażania reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment.md) | Przedstawia informacje o przeglądzie i wymagania wstępne dotyczące wdrażania reguł zmniejszania obszaru podatnego na ataki |
| [Planowanie wdrożenia reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-plan.md) | Wyświetla listę zalecanych kroków wdrażania reguł zmniejszania obszaru ataków |
| [Reguły zmniejszania obszaru ataków testowych (ASR)](attack-surface-reduction-rules-deployment-test.md) | Zawiera instrukcje dotyczące używania trybu inspekcji do testowania reguł zmniejszania obszaru podatnego na ataki. |
| [Włączanie reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-implement.md) | Przedstawia kroki przejścia reguł zmniejszania obszaru ataków z trybu testowego (inspekcji) do aktywnego, włączonego trybu (blokuj) |
| [Operacjonalizowanie reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-operationalize.md) | Zawiera informacje o codziennych działaniach związanych z przeglądem i konserwacją. |
| [Dokumentacja reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-reference.md) | Zawiera szczegółowe informacje o każdej regule zmniejszania obszaru ataków. |
| [Reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction.md) | Zmniejsz luki w zabezpieczeniach (powierzchnie ataków) w aplikacjach dzięki inteligentnym regułom, które pomagają zatrzymać złośliwe oprogramowanie. (Wymaga Program antywirusowy Microsoft Defender). |
