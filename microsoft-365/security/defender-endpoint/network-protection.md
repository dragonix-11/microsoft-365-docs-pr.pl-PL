---
title: Używanie ochrony sieci w celu zapobiegania połączeniom z nieprawidłowymi lokacjami
description: Ochrona sieci przez uniemożliwienie użytkownikom uzyskiwania dostępu do znanych złośliwych i podejrzanych adresów sieciowych
keywords: Ochrona sieci, luki w zabezpieczeniach, złośliwa witryna internetowa, adres IP, domena, domeny, polecenie i kontrola, Filtr SmartScreen, powiadomienie wyskakujące
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 604938426dfd8818647a5fa7b71069b4527ec877
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636452"
---
# <a name="protect-your-network"></a>Chroń sieć

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows
- macOS
- Linux

Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Omówienie ochrony sieci

Ochrona sieci pomaga chronić urządzenia przed zdarzeniami internetowymi. Ochrona sieci to możliwość zmniejszania obszaru podatnego na ataki. Pomaga to uniemożliwić pracownikom dostęp do niebezpiecznych domen za pośrednictwem aplikacji. Domeny hostujące wyłudzanie informacji, luki w zabezpieczeniach i inne złośliwe treści w Internecie są uważane za niebezpieczne. Ochrona sieci rozszerza zakres filtru [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) , aby zablokować cały wychodzący ruch HTTP,który próbuje nawiązać połączenie ze źródłami o niskiej reputacji (na podstawie domeny lub nazwy hosta).

Ochrona sieci rozszerza ochronę w [sieci Web](web-protection-overview.md) na poziom systemu operacyjnego. Udostępnia ona funkcje ochrony sieci Web znajdujące się w przeglądarce Microsoft Edge innym obsługiwanym przeglądarom i aplikacjom innym niż przeglądarki. Ochrona sieci zapewnia również widoczność i blokowanie wskaźników naruszenia zabezpieczeń (IOC) w przypadku użycia z [wykrywaniem punktów końcowych i reagowaniem na nie](overview-endpoint-detection-response.md). Na przykład ochrona sieci działa z [niestandardowymi wskaźnikami](manage-indicators.md) , których można użyć do blokowania określonych domen lub nazw hostów.

Obejrzyj ten film wideo, aby dowiedzieć się, w jaki sposób ochrona sieci pomaga ograniczyć obszar ataków urządzeń przed oszustwami wyłudzania informacji, lukami w zabezpieczeniach i inną złośliwą zawartością.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4yZ]

## <a name="requirements-for-network-protection"></a>Wymagania dotyczące ochrony sieci

Ochrona sieci wymaga Windows 10 lub 11 (Pro lub Enterprise), systemu Windows Server w wersji 1803 lub nowszej, systemu macOS w wersji 11 lub nowszej albo obsługiwanych przez usługę Defender wersji systemu Linux oraz ochrony antywirusowej Microsoft Defender w czasie rzeczywistym.

| Wersje systemu Windows | Program antywirusowy Microsoft Defender |
|:---|:---|
| Windows 10 wersji 1709 lub nowszej <br> Windows 11 <br> Windows Server 1803 lub nowszy | [Ochrona antywirusowa Microsoft Defender w czasie rzeczywistym](configure-real-time-protection-microsoft-defender-antivirus.md) <br> ochrona [dostarczana przez chmurę musi być włączona](enable-cloud-protection-microsoft-defender-antivirus.md) (aktywna)|

## <a name="why-network-protection-is-important"></a>Dlaczego ochrona sieci jest ważna

Ochrona sieci jest częścią grupy redukcji obszaru ataków rozwiązań w Ochrona punktu końcowego w usłudze Microsoft Defender. Ochrona sieci umożliwia warstwę warstwy sieciowej blokujących adresów URL i adresów IP. Ochrona sieci może blokować dostęp do adresów URL przy użyciu niektórych przeglądarek i standardowych połączeń sieciowych.

Domyślnie ochrona sieci chroni komputery przed znanymi złośliwymi adresami URL przy użyciu kanału informacyjnego SmartScreen, który blokuje złośliwe adresy URL w sposób podobny do filtru SmartScreen w przeglądarce Microsoft Edge. Funkcje ochrony sieci można rozszerzyć na:

- Blokuj adresy IP/adresy URL z własnej analizy [zagrożeń (wskaźniki](indicator-ip-domain.md))
- Blokuj niesankcjonowane usługi z [Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps) (wcześniej znanej jako Microsoft Cloud App Security)
- Blokowanie witryn na podstawie kategorii ([filtrowanie zawartości sieci Web](web-content-filtering.md))

Ochrona sieci jest kluczową częścią stosu ochrony i odpowiedzi firmy Microsoft.

> [!TIP]
> Aby uzyskać szczegółowe informacje na temat ochrony sieci dla systemów Windows Server, Linux, MacOS i Mobile Threat Defense (MTD), zobacz [Proaktywne wyszukiwanie zagrożeń z zaawansowanym wyszukiwaniem zagrożeń](advanced-hunting-overview.md).

### <a name="block-command-and-control-c2-attacks"></a>Blokuj ataki na polecenia i kontrolę (C2)

Komputery serwera poleceń i kontroli (C2) są używane przez złośliwych użytkowników do wysyłania poleceń do systemów zagrożonych złośliwym oprogramowaniem, a następnie wywierają pewnego rodzaju kontrolę nad systemami, których zabezpieczenia zostały naruszone. Ataki C2 zwykle ukrywają się w usługach opartych na chmurze, takich jak udostępnianie plików i usługi poczty internetowej, co umożliwia serwerom C2 uniknięcie wykrycia przez połączenie się z typowym ruchem.

Serwerów C2 można używać do inicjowania poleceń, które mogą:

- Kradzież danych (na przykład w drodze wyłudzania informacji)
- Kontrolowanie komputerów z naruszonymi zabezpieczeniami w sieci botnet
- Zakłócanie legalnych aplikacji
- Rozprzestrzenianie złośliwego oprogramowania, takiego jak oprogramowanie wymuszające okup

Składnik ochrony sieci w usłudze Defender for Endpoint identyfikuje i blokuje połączenia z infrastrukturami C2 używanymi w atakach wymuszania okupu obsługiwanych przez człowieka przy użyciu technik takich jak uczenie maszynowe i inteligentna identyfikacja wskaźnika naruszenia zabezpieczeń (IoC).

#### <a name="network-protection-new-toast-notifications"></a>Ochrona sieci: nowe powiadomienia wyskakujące

| Nowe mapowanie  | Kategoria odpowiedzi  | Źródeł |
| :--- | :--- | :--- |
| Phishing | Wyłudzanie informacji | Filtr smartscreen |
| Złośliwy | Złośliwy | Filtr smartscreen |
| polecenie i kontrolka | C2 | Filtr smartscreen |
| polecenie i kontrolka | COCO | Filtr smartscreen |
| Złośliwy | Niezaufanych | Filtr smartscreen |
| przez administratora IT | CustomBlockList |   |
| przez administratora IT | CustomPolicy |   |

> [!NOTE]
> **customAllowList** nie generuje powiadomień w punktach końcowych.

### <a name="new-notifications-for-network-protection-determination"></a>Nowe powiadomienia dotyczące określania ochrony sieci

Nowa, publicznie dostępna funkcja ochrony sieci wykorzystuje funkcje w filtrze SmartScreen do blokowania działań wyłudzających informacje ze złośliwych witryn poleceń i kontroli.

Gdy użytkownik końcowy próbuje odwiedzić witrynę internetową w środowisku, w którym włączono ochronę sieci, możliwe są trzy scenariusze:

- Adres URL ma **znaną dobrą reputację** — w tym przypadku użytkownik ma dozwolony dostęp bez przeszkód i w punkcie końcowym nie jest wyświetlane wyskakujące powiadomienie. W efekcie domena lub adres URL jest ustawiona na _wartość Dozwolone_.
- Adres URL ma **nieznaną lub niepewną reputację** — dostęp użytkownika jest zablokowany, ale z możliwością obejścia (odblokowania) bloku. W efekcie domena lub adres URL jest ustawiona na _Inspekcja_.
- Adres URL ma **znaną złą (złośliwą) reputację** — użytkownik nie może uzyskać dostępu. W efekcie domena lub adres URL jest ustawiona na _wartość Blokuj_.

#### <a name="warn-experience"></a>Ostrzeżenie o środowisku

Użytkownik odwiedza witrynę internetową:

- Jeśli adres URL ma nieznaną lub niepewną reputację, wyskakujące powiadomienie wyświetli użytkownikowi następujące opcje:

  - **Ok** — powiadomienie wyskakujące jest zwalniane (usuwane), a próba uzyskania dostępu do witryny została zakończona.
  - **Odblokuj** — aby uzyskać dostęp do witryny, użytkownik nie będzie musiał uzyskiwać dostępu do portalu Windows Defender Security Intelligence (WDSI). Użytkownik będzie miał dostęp do witryny przez 24 godziny. w którym momencie blok jest ponownie włączany przez kolejne 24 godziny. Użytkownik może nadal używać funkcji **Odblokuj** , aby uzyskać dostęp do witryny do czasu, gdy administrator zabroni (blokuje) witryny, usuwając w ten sposób opcję **Odblokuj**.
  - **Opinia** — wyskakujące powiadomienie przedstawia użytkownikowi link do przesłania biletu, którego użytkownik może użyć do przesłania opinii do administratora w celu uzasadnienia dostępu do witryny.

  > [!div class="mx-imgBorder"]
  > ![Wyświetla powiadomienie o wyłudzaniu informacji o zawartości ochrony sieci](images/network-protection-phishing-warn-2.png)

  > [UWAGA!] Obrazy wyświetlane tutaj w celu ostrzeżenia środowiska i blokowania (poniżej) zawierają listę **"zablokowany adres URL"** jako przykładowy tekst zastępczy; W środowisku funkcjonującym zostanie wyświetlony rzeczywisty adres URL lub domena.  

#### <a name="block-experience"></a>Zablokuj środowisko

Użytkownik odwiedza witrynę internetową:

- Jeśli adres URL ma złą reputację, wyskakujące powiadomienie wyświetli użytkownikowi następujące opcje:
  - **Ok** Powiadomienie wyskakujące jest zwalniane (usuwane), a próba uzyskania dostępu do witryny została zakończona.
  - **Opinie** Wyskakujące powiadomienie przedstawia użytkownikowi link do przesłania biletu, którego użytkownik może użyć do przesłania opinii do administratora, próbując uzasadnić dostęp do witryny.
  
  > [!div class="mx-imgBorder"]
  > ![ Pokazuje powiadomienie o blokadzie znanej zawartości wyłudzającej informacje o ochronie sieci](images/network-protection-phishing-blocked.png)

### <a name="network-protection-c2-detection-and-remediation"></a>Ochrona sieci: wykrywanie i korygowanie C2

W początkowej formie oprogramowanie wymuszające okup jest zagrożeniem towarowym, wstępnie zaprogramowanym i skoncentrowanym na ograniczonych, konkretnych wynikach (na przykład szyfrowaniu komputera). Jednak oprogramowanie wymuszające okup przekształciło się w zaawansowane zagrożenie oparte na człowieku, adaptacyjne i skoncentrowane na większej skali i bardziej rozpowszechnionych wynikach; takich jak przechowywanie zasobów lub danych całej organizacji dla okupu.

Obsługa serwerów poleceń i kontroli (C2) jest kluczowym elementem tej ewolucji oprogramowania wymuszającego okup i umożliwia tym atakom dostosowanie się do środowiska, do którego są przeznaczone. Przerwanie linku do infrastruktury dowodzenia i kontroli zatrzymuje postęp ataku do następnego etapu.

## <a name="smartscreen-unblock"></a>Odblokuj filtr SmartScreen

Nowa funkcja w wskaźnikach punktu końcowego w usłudze Defender umożliwia administratorom zezwalanie użytkownikom końcowym na pomijanie ostrzeżeń generowanych dla niektórych adresów URL i adresów IP. W zależności od tego, dlaczego adres URL został zablokowany, napotkany blok SmartScreen może zaoferować administratorom możliwość odblokowania witryny przez maksymalnie 24 godziny. W takich przypadkach zostanie wyświetlone powiadomienie Zabezpieczenia Windows wyskakujące, co umożliwi użytkownikowi końcowemu **odblokowanie** adresu URL lub adresu IP przez zdefiniowany okres.  

 > [!div class="mx-imgBorder"]
 > ![Zabezpieczenia Windows powiadomienia o ochronie sieci](images/network-protection-smart-screen-block-notification.png)

Ochrona punktu końcowego w usłudze Microsoft Defender Administratorzy mogą skonfigurować funkcję Odblokuj filtr SmartScreen w [Microsoft 365 Defender](https://security.microsoft.com/) przy użyciu następującego narzędzia konfiguracji. W portalu Microsoft 365 Defender przejdź do ścieżki do nazwy ConfigToolName.

<!-- Hide {this intro with no subsequent list items}
[Line 171: Delete the colon and the right angle-brackets. The resulting sentence will be "From the [MS365 Defender] portal, navigate to path to ConfigToolName." Delete "to" and add "the" before path unless a specific description is available. Would a screenshot help? Normally angle brackets or arrows are used in place of certain text rather than in addition.]
-->

 > [!div class="mx-imgBorder"]
 > ![Konfiguracja bloku smartscreen ochrony sieci ulr i formularz adresu IP](images/network-protection-smart-screen-block-configuration.png)

## <a name="using-network-protection"></a>Korzystanie z ochrony sieci

Ochrona sieci jest włączona dla każdego urządzenia, co zwykle odbywa się przy użyciu infrastruktury zarządzania. Aby uzyskać obsługiwane metody, zobacz [Włączanie ochrony sieci](enable-network-protection.md).

> [!NOTE]
> Program antywirusowy Microsoft Defender musi być aktywny, aby włączyć ochronę sieci.

Ochronę sieci można włączyć w trybie **inspekcji** lub w trybie **bloku** . Jeśli chcesz ocenić wpływ włączenia ochrony sieci przed faktycznym zablokowaniem adresów IP lub adresów URL, możesz włączyć ochronę sieci w trybie inspekcji przez pewien czas, aby zebrać dane dotyczące tego, co zostałoby zablokowane. Dzienniki trybu inspekcji, gdy użytkownicy końcowi nawiązali połączenie z adresem lub lokacją, która w przeciwnym razie zostałaby zablokowana przez ochronę sieci.

## <a name="advanced-hunting"></a>Zaawansowane wyszukiwanie zagrożeń

Jeśli używasz zaawansowanego wyszukiwania zagrożeń do identyfikowania zdarzeń inspekcji, będziesz mieć do 30-dniową historię dostępną w konsoli programu . Zobacz [Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md).

Dane inspekcji można znaleźć w obszarze **Zaawansowane wyszukiwanie zagrożeń** w portalu usługi Defender for Endpoint ([https://security.microsoft.com](https://security.microsoft.com)).  

Zdarzenia są w obszarze DeviceEvents z wartością ActionType z wartością `ExploitGuardNetworkProtectionAudited`. Bloki są wyświetlane przez `ExploitGuardNetworkProtectionBlocked`.  

Poniższy przykład obejmuje zablokowane akcje:

```kusto

DeviceEvents

- Where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')

```

 > [!div class="mx-imgBorder"]
 > ![Zaawansowane wyszukiwanie zagrożeń dotyczących inspekcji i identyfikowania zdarzeń](images/network-protection-advanced-hunting.png)

> [!TIP]
> Te wpisy zawierają dane w kolumnie **AdditionalFields** , które zawierają doskonałe informacje dotyczące akcji, jeśli rozwiniesz pole **Dodatkowe,** możesz również uzyskać pola: **IsAudit**, **ResponseCategory** i **DisplayName**.

Oto kolejny przykład:

```kusto

DeviceEvents:

- where ActionType contains "ExploitGuardNetworkProtection"
- extend ParsedFields=parse_json(AdditionalFields)
- project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, IsAudit=tostring(ParsedFields.IsAudit), ResponseCategory=tostring(ParsedFields.ResponseCategory), DisplayName=tostring(ParsedFields.DisplayName)
- sort by Timestamp desc

```
Kategoria Odpowiedź informuje o przyczynach zdarzenia, na przykład:

| Kategoria odpowiedzi | Funkcja odpowiedzialna za zdarzenie |
|:---|:---|
| CustomPolicy |  WCF  |
| CustomBlockList  |   Wskaźniki niestandardowe   |
| CasbPolicy   |   Defender for Cloud Apps   |
| Złośliwy   |   Zagrożenia internetowe  |
| Wyłudzanie informacji  |   Zagrożenia internetowe  |

Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z blokami punktów końcowych](web-protection-overview.md#troubleshoot-endpoint-blocks).

Możesz użyć wynikowej listy adresów URL i adresów IP, aby określić, co zostałoby zablokowane, gdyby urządzenie było w trybie bloku i która funkcja je zablokowała. Przejrzyj każdy element na liście, aby zidentyfikować adresy URL lub adresy IP, niezależnie od tego, czy są niezbędne dla danego środowiska. Jeśli znajdziesz wszystkie wpisy, które zostały poddane inspekcji, które mają kluczowe znaczenie dla środowiska, utwórz wskaźnik zezwalający na nie w sieci. Wskaźniki zezwalania na adres URL/ADRES IP mają pierwszeństwo przed dowolnym blokiem.

Po utworzeniu wskaźnika możesz przyjrzeć się rozwiązaniu podstawowego problemu:

- SmartScreen — przegląd żądań
- Wskaźnik — modyfikowanie istniejącego wskaźnika
- MCA — przeglądanie nieusankcjonowanych aplikacji
- WCF — ponowna kategoryzacja żądania

Korzystając z tych danych, możesz podjąć świadomą decyzję o włączeniu ochrony sieci w trybie bloku. Zobacz [Kolejność pierwszeństwa dla bloków ochrony sieci](web-protection-overview.md#order-of-precedence).

> [!NOTE]
> Ponieważ jest to ustawienie dla poszczególnych urządzeń, jeśli istnieją urządzenia, które nie mogą przejść do trybu bloku, możesz po prostu pozostawić je w inspekcji, dopóki nie będzie można rozwiązać problemu i nadal będą otrzymywać zdarzenia inspekcji.

Aby uzyskać informacje o sposobie zgłaszania wyników fałszywie dodatnich, zobacz [Zgłaszanie wyników fałszywie dodatnich](web-protection-overview.md#report-false-positives).

Aby uzyskać szczegółowe informacje na temat tworzenia własnych raportów usługi Power BI, zobacz [Tworzenie raportów niestandardowych przy użyciu usługi Power BI](api-power-bi.md).

## <a name="configuring-network-protection"></a>Konfigurowanie ochrony sieci

Aby uzyskać więcej informacji na temat włączania ochrony sieci, zobacz **[Włączanie ochrony sieci](enable-network-protection.md)**. Użyj zasady grupy, programu PowerShell lub dostawców CSP mdm, aby włączyć ochronę sieci w sieci i zarządzać nią.

Po włączeniu usług może być konieczne skonfigurowanie sieci lub zapory w celu zezwolenia na połączenia między usługami i urządzeniami (nazywane również punktami końcowymi).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="viewing-network-protection-events"></a>Wyświetlanie zdarzeń ochrony sieci

Ochrona sieci działa najlepiej z [Ochrona punktu końcowego w usłudze Microsoft Defender](microsoft-defender-endpoint.md), co zapewnia szczegółowe raportowanie zdarzeń i bloków ochrony przed lukami w zabezpieczeniach w ramach [scenariuszy badania alertów](investigate-alerts.md).

Gdy ochrona sieci blokuje połączenie, z Centrum akcji jest wyświetlane powiadomienie. Twój zespół ds. operacji zabezpieczeń może [dostosować powiadomienie](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) przy użyciu szczegółów i informacji kontaktowych organizacji. Ponadto można włączyć i dostosować poszczególne reguły zmniejszania obszaru podatnego na ataki, aby dostosować je do określonych technik monitorowania.

Możesz również użyć [trybu inspekcji](audit-windows-defender.md) , aby ocenić, w jaki sposób ochrona sieci wpłynie na organizację, jeśli zostałaby włączona.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Przeglądanie zdarzeń ochrony sieci w portalu Microsoft 365 Defender

Usługa Defender for Endpoint udostępnia szczegółowe raporty dotyczące zdarzeń i bloków w ramach [scenariuszy badania alertów](investigate-alerts.md). Te szczegóły można wyświetlić w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) w [kolejce alertów](review-alerts.md) lub przy użyciu [zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md). Jeśli używasz [trybu inspekcji](audit-windows-defender.md), możesz użyć zaawansowanego wyszukiwania zagrożeń, aby zobaczyć, jak ustawienia ochrony sieci wpłyną na środowisko, jeśli zostaną włączone.

Oto przykładowe zapytanie dotyczące zaawansowanego wyszukiwania zagrożeń:

```kusto

DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')

```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Przejrzyj zdarzenia ochrony sieci w systemie Windows Podgląd zdarzeń

Możesz przejrzeć dziennik zdarzeń systemu Windows, aby wyświetlić zdarzenia, które są tworzone, gdy ochrona sieci blokuje (lub przeprowadza inspekcje) dostęp do złośliwego adresu IP lub domeny:

1. [Skopiuj plik XML bezpośrednio](event-views.md).

2. Wybierz przycisk **OK**.

Ta procedura tworzy widok niestandardowy, który filtruje tylko następujące zdarzenia związane z ochroną sieci:

|Identyfikator zdarzenia|Opis|
|---|---|
|5007|Zdarzenie po zmianie ustawień|
|1125|Zdarzenie, gdy ochrona sieci jest uruchamiana w trybie inspekcji|
|1126|Zdarzenie, gdy ochrona sieci jest uruchamiana w trybie bloku|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Ochrona sieci i trójstopnie uzgadnianie protokołu TCP

W przypadku ochrony sieci określenie, czy zezwolić na dostęp do lokacji lub zablokować go, jest wykonywane po zakończeniu [uzgadniania trójstopnienego za pośrednictwem protokołu TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). W związku z tym, gdy lokacja jest zablokowana przez ochronę sieci, w portalu Microsoft 365 Defender może zostać wyświetlony typ `ConnectionSuccess` `NetworkConnectionEvents` akcji poniżej, mimo że witryna została zablokowana. `NetworkConnectionEvents` są zgłaszane z warstwy TCP, a nie z ochrony sieci. Po zakończeniu uzgadniania trójstopnienia dostęp do witryny jest dozwolony lub blokowany przez ochronę sieci.

Oto przykład tego, jak to działa:

1. Załóżmy, że użytkownik próbuje uzyskać dostęp do witryny internetowej na swoim urządzeniu. Lokacja jest hostowana w niebezpiecznej domenie i powinna zostać zablokowana przez ochronę sieci.  

2. Rozpoczyna się uzgadnianie trójstopnie za pośrednictwem protokołu TCP/IP. Przed zakończeniem `NetworkConnectionEvents` jest rejestrowana akcja, a jej `ActionType` nazwa jest wyświetlana jako `ConnectionSuccess`. Jednak po zakończeniu trójstopnienego procesu uzgadniania ochrona sieci blokuje dostęp do lokacji. Wszystko to dzieje się szybko. Podobny proces występuje w przypadku [filtru Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview); jest to, gdy uzgadnianie trójstopnie kończy się, że determinacja jest dokonywana, a dostęp do witryny jest zablokowany lub dozwolony.

3. W portalu Microsoft 365 Defender alert jest wyświetlany w [kolejce alertów](alerts-queue.md). Szczegóły tego alertu obejmują zarówno `NetworkConnectionEvents` i `AlertEvents`. Widać, że witryna została zablokowana, mimo że masz `NetworkConnectionEvents` również element o typie ActionType .`ConnectionSuccess`

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Zagadnienia dotyczące pulpitu wirtualnego systemu Windows uruchomionego Windows 10 Enterprise wielu sesjach

Ze względu na charakter wielu użytkowników Windows 10 Enterprise należy pamiętać o następujących kwestiach:

1. Ochrona sieci jest funkcją dla całego urządzenia i nie może być przeznaczona dla określonych sesji użytkowników.

2. Zasady filtrowania zawartości sieci Web są również na całym urządzeniu.

3. Jeśli musisz rozróżnić grupy użytkowników, rozważ utworzenie oddzielnych pul hostów i przypisań usługi Windows Virtual Desktop.

4. Przetestuj ochronę sieci w trybie inspekcji, aby ocenić jej zachowanie przed wdrożeniem.

5. Rozważ zmiany rozmiaru wdrożenia, jeśli masz dużą liczbę użytkowników lub dużą liczbę sesji z wieloma użytkownikami.

### <a name="alternative-option-for-network-protection"></a>Alternatywna opcja ochrony sieci

W przypadku Windows 10 Enterprise z wieloma sesjami 1909 i nowszymi, używanymi w programie Windows Virtual Desktop na platformie Azure, ochronę sieci dla przeglądarki Microsoft Edge można włączyć przy użyciu następującej metody:

1. Użyj opcji [Włącz ochronę sieci](enable-network-protection.md) i postępuj zgodnie z instrukcjami, aby zastosować zasady.

2. Wykonaj następujące polecenia programu PowerShell:

   - `Set-MpPreference -EnableNetworkProtection Enabled`
   - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
   - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
   - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Rozwiązywanie problemów z ochroną sieci

Ze względu na środowisko, w którym działa ochrona sieci, firma Microsoft może nie być w stanie wykryć ustawień serwera proxy systemu operacyjnego. W niektórych przypadkach klienci ochrony sieci nie mogą uzyskać dostępu do usługi w chmurze. Aby rozwiązać problem z [łącznością, skonfiguruj statyczny serwer proxy dla programu antywirusowego Microsoft Defender](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus).

## <a name="optimizing-network-protection-performance"></a>Optymalizowanie wydajności ochrony sieci

Ochrona sieci ma teraz optymalizację wydajności, która umożliwia trybowi bloku rozpoczęcie asynchronicznej inspekcji długich połączeń po ich zweryfikowaniu i zezwoleniu przez filtr SmartScreen, co może zapewnić potencjalne zmniejszenie kosztów inspekcji przepustowości i może również pomóc w rozwiązywaniu problemów ze zgodnością aplikacji. Ta funkcja optymalizacji jest domyślnie włączona. Tę funkcję można wyłączyć przy użyciu następującego polecenia cmdlet programu PowerShell:

`Set-MpPreference -AllowSwitchToAsyncInspection $false`

## <a name="see-also"></a>Zobacz też

- [Ocena | ochrony sieci](evaluate-network-protection.md) Podejmij się szybkiego scenariusza, który pokazuje, jak działa funkcja i jakie zdarzenia są zwykle tworzone.
- [Włączanie | ochrony sieci](enable-network-protection.md) Użyj zasady grupy, programu PowerShell lub dostawców CSP mdm, aby włączyć ochronę sieci w sieci i zarządzać nią.
- [Konfigurowanie możliwości zmniejszania obszaru ataków w Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
