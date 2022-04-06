---
title: Application Guard dla Office dla administratorów
keywords: application guard, protection, isolation, isolated container, hardware isolation
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Uzyskaj najnowszą wersję izolacji sprzętowej. Zapobieganie bieżącym i pojawiającym się atakom, na przykład wykorzystaniom lub złośliwym linkom, w celu zakłócania wydajności pracowników i zabezpieczeń przedsiębiorstwa.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: da61ee2f5e29501e033ad44bc3fdb04ee2c042f0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473326"
---
# <a name="application-guard-for-office-for-admins"></a>Application Guard dla Office dla administratorów

**Dotyczy:** Word, Excel, PowerPoint dla Microsoft 365, Windows 10 Enterprise, Windows 11 Enterprise

Microsoft Defender Application Guard for Office (Application Guard for Office) pomaga zapobiec uzyskiwaniu dostępu do zaufanych zasobów przez niezaufane pliki, zabezpieczając przedsiębiorstwa przed nowymi i pojawiającymi się atakami. W tym artykule administratorzy mogą skonfigurować urządzenia w celu wyświetlania podglądu z programu Application Guard dla Office. Zawiera informacje o wymaganiach systemowych i krokach instalacji w celu włączenia funkcji Application Guard Office na urządzeniu.

## <a name="prerequisites"></a>Wymagania wstępne

### <a name="minimum-hardware-requirements"></a>Minimalne wymagania sprzętowe

* **Procesor**: 64-bitowy, 4-rdzeniowy (fizyczny lub wirtualny), rozszerzenia wirtualizacji (Intel VT-x LUB AMD-V), odpowiednik core i5 lub wyższy zalecany
* **Pamięć fizyczna**: 8 GB pamięci RAM
* **Dysk twardy**: 10 GB wolnego miejsca na dysku systemowym (zalecane dyski SSD)

### <a name="minimum-software-requirements"></a>Minimalne wymagania dotyczące oprogramowania

* **Windows**: Windows 10 Enterprise, kompilacja klienta w wersji 2004 (20H1) 19041 lub nowsza. Wszystkie wersje Windows 11 są obsługiwane. 
* **Office**: Office i Miesięczny kanał Enterprise, kompilacja 2011 16.0.13530.10000 lub nowsza. Office Semi-Annual Enterprise, kompilacja 2108 lub nowsza. Obsługiwane są wersje 32-bitowe i 64-bitowe Office.
* **Pakiet aktualizacji**: skumulowana Windows 10 aktualizacji zabezpieczeń [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Aby uzyskać szczegółowe wymagania systemowe, zobacz [Wymagania systemowe Microsoft Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). Należy również zapoznać się z przewodnikami producenta komputera na temat włączania technologii wirtualizacji.
Aby dowiedzieć się więcej o Office kanałach aktualizacji, zobacz [Omówienie kanałów](/deployoffice/overview-update-channels) aktualizacji dla Microsoft 365.

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

* Microsoft 365 E5 lub Zabezpieczenia platformy Microsoft 365 E5

> [!NOTE]
> Aplikacje Microsoft 365 dla przedsiębiorstw z licencją opartą na urządzeniu nie mają dostępu do do aplikacji Application Guard dla Office.

## <a name="deploy-application-guard-for-office"></a>Wdrażanie do guard aplikacji dla Office

### <a name="enable-application-guard-for-office"></a>Włączanie funkcji Application Guard dla Office

1. Pobierz i zainstaluj **Windows 10 comiesięcznych aktualizacji zabezpieczeń KB4571756**.

2. Wybierz **Microsoft Defender Application Guard** w Windows Funkcje i wybierz przycisk **OK**. Włączenie funkcji Application Guard spowoduje monit o ponowne uruchomienie systemu. Możesz zdecydować się na ponowne uruchomienie teraz lub po kroku 3.

   :::image type="content" source="../../media/ag03-deploy.png" alt-text="Okno Windows funkcje ag" lightbox="../../media/ag03-deploy.png":::

   Tę funkcję można również włączyć, uruchamiając następujące polecenie programu PowerShell jako administrator:

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Wyszukaj Microsoft Defender Application Guard **w** trybie zarządzanym zasady grupy **\\\\w grupie Szablony administracyjne Windows składniki\\ Microsoft Defender Application Guard**. Włącz te zasady, ustawiając wartość w obszarze Opcje jako **2** lub **3**, a następnie wybierając przycisk **OK** lub **Zastosuj**.

   :::image type="content" source="../../media/ag04-deploy.png" alt-text="Opcja włącz ag w trybie zarządzanym" lightbox="../../media/ag04-deploy.png":::

   Zamiast tego możesz ustawić odpowiednie zasady CSP:

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Ustawienia/AllowWindowsDefenderApplicationGuard** <br> Typ danych: **Liczba całkowita** <br> Wartość: **2**

4. Uruchom ponownie system.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Ustaw opinię & diagnostyki, aby wysyłać pełne dane

> [!NOTE]
> Nie jest to jednak wymagane, jednak skonfigurowanie opcjonalnych danych diagnostycznych pomoże zdiagnozować zgłoszone problemy.

Ten krok gwarantuje, że do firmy Microsoft trafiają dane niezbędne do zidentyfikowania i rozwiązania problemów. Wykonaj poniższe czynności, aby włączyć diagnostykę na Windows urządzenia:

1. Otwórz **Ustawienia** z menu Start.

   :::image type="content" source="../../media/ag05-diagnostic.png" alt-text="The menu Start" lightbox="../../media/ag05-diagnostic.png":::

2. Na **Windows Ustawienia** wybierz pozycję **Prywatność**.

   :::image type="content" source="../../media/ag06-diagnostic.png" alt-text="Menu Windows Ustawienia" lightbox="../../media/ag06-diagnostic.png":::

3. W obszarze Prywatność wybierz pozycję **Diagnostyka & opinie i** wybierz pozycję **Opcjonalne dane diagnostyczne**.

   :::image type="content" source="../../media/ag07a-diagnostic.png" alt-text="Menu Diagnostyka i opinia" lightbox="../../media/ag07a-diagnostic.png":::

Aby uzyskać więcej informacji na temat Windows diagnostycznych, zobacz Konfigurowanie Windows [diagnostycznych w organizacji](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Upewnij się, że funkcja Application Guard Office jest włączona i działa

Przed potwierdzeniem działania funkcji Application Guard dla programu Office uruchom program Word, Excel lub PowerPoint na urządzeniu, na którym wdrożono zasady. Upewnij się, Office został aktywowany. Może być konieczne użycie Tożsamości służbowej w celu aktywowania Office produktu.

Aby potwierdzić, że funkcja Application Guard Office jest włączona, uruchom program Word, Excel lub PowerPoint, a następnie otwórz niezaufany dokument. Na przykład możesz otworzyć dokument pobrany z Internetu lub załącznik wiadomości e-mail od osoby spoza Twojej organizacji.

Przy pierwszym otwarciu niezaufanego pliku może zostać wyświetlony Office powitalny, taki jak w poniższym przykładzie. Może on być wyświetlany przez jakiś czas, gdy jest Office application Guard for Office i plik jest otwierany. Kolejne otwarcie niezaufanych plików powinno być szybsze.

:::image type="content" source="../../media/ag08-confirm.png" alt-text="Strona aplikacja pakietu Office powitalnego" lightbox="../../media/ag08-confirm.png":::

Po otwarciu pliku powinien być wyświetlanych kilka wskaźników wizualnych, że plik został otwarty w programie Application Guard dla aplikacji Office:

* Objaśnienie na wstążce

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Plik doc przedstawiający małą notatkę z rozszerzeniem App Guard" lightbox="../../media/ag09-confirm.png":::

* Ikona aplikacji z tarczą na pasku zadań

  ![Ikona na pasku zadań.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Konfigurowanie dorównania aplikacji dla Office

Office obsługuje następujące zasady, aby umożliwić skonfigurowanie funkcji Application Guard dla Office. Te zasady można konfigurować za pośrednictwem zasad grupy lub za [pośrednictwem Office zasad w chmurze](/DeployOffice/overview-office-cloud-policy-service).


> [!NOTE]
> Skonfigurowanie tych zasad może wyłączyć niektóre funkcje plików otwieranych w funkcji Application Guard dla Office.

|Zasady|Opis|
|---|---|
|Nie używaj funkcji Application Guard do Office|Włączenie tych zasad spowoduje, że program Word, Excel i PowerPoint będzie używać kontenera izolacji widoku chronionego zamiast do ochrony przed Office. Za pomocą tych zasad można tymczasowo wyłączyć funkcję Application Guard dla Office, gdy występują problemy podczas jej opuszczania na Microsoft Edge.|
|Konfigurowanie application Guard Office wstępnego tworzenia kontenera|Te zasady określają, czy kontener funkcji Application Guard Office, który umożliwia odizolowanie niezaufanych plików, jest wstępnie utworzony w celu poprawy wydajności wykonywania. Po włączeniu tego ustawienia można określić liczbę dni, przez które kontener będzie nadal przed utworzeniem, lub pozwolić, Office wbudowany heuristic wstępnie utworzyć kontener.
|Nie zezwalaj na kopiowanie/wklejanie w przypadku Office otwieranych w aplikacji Application Guard dla Office|Włączenie tych zasad uniemożliwi użytkownikowi kopiowanie i wklejanie zawartości z dokumentu otwartego w aplikacji Application Guard w celu Office do dokumentu otwartego poza nim.|
|Wyłączanie przyspieszenia sprzętowego w funkcji Application Guard dla Office|Te zasady sterują tym, czy funkcja Application Guard dla Office używa przyspieszenia sprzętowego do renderowania grafiki. Po włączeniu tego ustawienia ochrona Application Guard dla systemu Office będzie korzystać z renderowania opartego na oprogramowaniu (CPU) i nie będzie ładować sterowników graficznych innych firm ani korzystać z podłączonego sprzętu graficznego.
|Wyłączanie ochrony nieobsługiwanych typów plików w funkcji Application Guard dla Office|Te zasady sterują tym, czy rozszerzenie Application Guard dla programu Office zablokuje otwarcie nieobsługiwanych typów plików, czy też umożliwi przekierowywanie do widoku chronionego.
|Wyłączanie dostępu do kamery i mikrofonu dla dokumentów otwieranych w aplikacji Application Guard dla Office|Włączenie tych zasad Office dostępu do kamery i mikrofonu w funkcji Application Guard dla Office.|
|Ograniczanie drukowania z dokumentów otwieranych w aplikacji Application Guard dla Office|Włączenie tych zasad ograniczy liczbę drukarek, na których użytkownik może drukować z pliku otwartego w funkcji Application Guard dla systemu Office. Za pomocą tych zasad można na przykład ograniczyć drukowanie tylko do pliku PDF użytkownikom.|
|Uniemożliwianie użytkownikom usuwania do guard aplikacji w Office ochrony plików|Włączenie tych zasad spowoduje usunięcie opcji (w ramach środowiska aplikacji Office) wyłączenia funkcji Application Guard na Office ochrony lub otwarcia pliku poza rozszerzeniem Application Guard dla systemu Office. <p> **Uwaga:** Użytkownicy nadal mogą pominąć te zasady, ręcznie usuwając właściwość mark-of-the-web z pliku lub przenosząc dokument do zaufanej lokalizacji.|

> [!NOTE]
> Poniższe zasady będą wymagały wylogowania użytkownika i ponownego zalogowania się w celu Windows w życie:
>
> * Wyłączanie funkcji kopiowania/wklejania dla dokumentów otwieranych w funkcji Application Guard dla Office
> * Ograniczanie drukowania dokumentów otwieranych w aplikacji Application Guard dla Office
> * Wyłączanie dostępu z aparatu i mikrofonu do dokumentów otwieranych w aplikacji Application Guard dla Office

## <a name="submit-feedback"></a>Prześlij opinię

### <a name="submit-feedback-via-feedback-hub"></a>Prześlij opinię za pośrednictwem Centrum opinii

Jeśli podczas uruchamiania programu Application Guard dla aplikacji Office wystąpią problemy, zachęcamy do przesyłania opinii za pośrednictwem Centrum opinii:

1. Otwórz aplikację **Centrum opinii i** zaloguj się.

2. Jeśli podczas uruchamiania programu Application Guard zostanie wyświetlone okno dialogowe błędu, wybierz pozycję Zgłoś firmie **Microsoft** w oknie dialogowym błędu, aby rozpocząć przesyłanie nowej opinii. W przeciwnym razie przejdź do odpowiedniej <https://aka.ms/mdagoffice-fb> kategorii dla application Guard, a następnie wybierz **+&nbsp;pozycję Dodaj nową opinię** w prawym górnym rogu.

3. Wprowadź podsumowanie w polu **Podsumuj opinię** , jeśli nie zostało ono jeszcze wypełnione.

4. Wprowadź szczegółowy opis wystąpiłego problemu i czynności, które miały miejsce, w polu Wyjaśnij **bardziej szczegółowo** , a następnie wybierz pozycję **Dalej**.

5. Wybierz dymek obok przycisku **Problem**. Upewnij się, że wybrana kategoria to **Zabezpieczenia \> i prywatność Microsoft Defender Application Guard — Office**, a następnie wybierz pozycję **Dalej**.

6. Wybierz **pozycję Nowa opinia**, a następnie **przycisk Dalej**.

7. Zbieranie danych śledzenia dotyczących problemu:

   1. Rozwiń **kafelek Odtwórz mój problem** .

   2. Jeśli problem, który występuje, występuje, gdy jest uruchomiony program Application Guard, otwórz wystąpienie programu Application Guard. Otwarcie wystąpienia umożliwia zbieranie dodatkowych danych śledzenia z kontenera application Guard.

   3. Wybierz **pozycję Rozpocznij nagrywanie** i poczekaj, aż kafelek przestanie obracać się, a następnie powiedz *Zatrzymaj nagrywanie*.

   4. W pełni odtąd odtąd odtąd odtąd występuje problem z application Guard. Kopiowanie może obejmować próbę uruchomienia wystąpienia programu Application Guard i oczekiwania na niepowodzenie lub ponowne przedstawienie problemu w uruchomionym wystąpieniu programu Application Guard.

   5. Wybierz **kafelek Zatrzymaj nagrywanie** .

   6. Nie otwieraj żadnych uruchomionych wystąpień funkcji Application Guard nawet przez kilka minut po ich przesłanie, aby można było również zbierać diagnostykę kontenerów.

8. Dołącz wszelkie odpowiednie zrzuty ekranu lub pliki związane z problemem.

9. Wybierz **pozycję Prześlij**.

### <a name="submit-feedback-via-office-customer-voice"></a>Przesyłanie opinii za pośrednictwem Office Customer Voice

Możesz również przesłać opinię z programu Office, jeśli problem występuje po otwarciu Office w aplikacji Application Guard. Informacje na temat [przesyłania Office niejawnego](https://insider.office.com/handbook) programu testów znajdziesz w podręczniku niejawnego programu testów.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Integracja z Ochrona punktu końcowego w usłudze Microsoft Defender i Ochrona usługi Office 365 w usłudze Microsoft Defender

Application Guard for Office is integrated with Ochrona punktu końcowego w usłudze Microsoft Defender to provide monitoring and alerting on malicious activity that happens in the isolated environment.

[Sejf dokumenty na platformie Microsoft E365 E5](/microsoft-365/security/office-365-security/safe-docs) to funkcja, która używa programu Ochrona punktu końcowego w usłudze Microsoft Defender do skanowania dokumentów otwieranych w aplikacji Application Guard dla systemu Office. Aby uzyskać dodatkową warstwę ochrony, użytkownicy nie mogą opuszczać do Office do czasu ustalenia wyników skanowania.

Ochrona punktu końcowego w usłudze Microsoft Defender to platforma zabezpieczeń, która ma pomóc sieciom przedsiębiorstwa zapobiegać zaawansowanym zagrożeniam, wykrywać i badać je oraz odpowiadać na nie. Aby uzyskać więcej informacji na temat tej platformy, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). Aby dowiedzieć się więcej o dołączaniu urządzeń do tej platformy, zobacz [Urządzenia](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure) na urządzeniach w Ochrona punktu końcowego w usłudze Microsoft Defender usługi.

Możesz również skonfigurować program Ochrona usługi Office 365 w usłudze Microsoft Defender do pracy z usługą Defender dla punktu końcowego. Aby uzyskać więcej informacji, zobacz [Integracja Ochrona usługi Office 365 w usłudze Defender z Ochrona punktu końcowego w usłudze Microsoft Defender](integrate-office-365-ti-with-mde.md).

## <a name="limitations-and-considerations"></a>Ograniczenia i zagadnienia

* Application Guard for Office is a protected mode that isolates untrusted documents so so that they cannot access trusted corporate resources, an intranet, the user's identity, and arbitrary files on the computer. W wyniku tego, jeśli użytkownik spróbuje uzyskać dostęp do funkcji, która ma zależność od takiego dostępu, na przykład wstawienie obrazu z pliku lokalnego na dysku, dostęp zakończy się niepowodzeniem i wyświetli monit podobny do poniższego przykładu. Aby włączyć niezaufany dokument w celu uzyskiwania dostępu do zaufanych zasobów, użytkownicy muszą usunąć z dokumentu ochronę funkcji Application Guard. 

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Okno dialogowe z komunikatem o zabezpieczeniach i stanem funkcji" lightbox="../../media/ag09-confirm.png":::

  > [!NOTE]
  > Porada użytkownikom, aby usuwali ochronę tylko wtedy, gdy ufają plikowi i jego źródle lub miejscu, z którego pochodzi.

* Jeśli niezaufany dokument jest przechowywany w zaufanej lokalizacji, zaufanie po tej lokalizacji jest dziedziczone przez ten dokument. Zazwyczaj magazyn w chmurze organizacji jest identyfikowany jako zaufana lokalizacja.
  
* Zawartość aktywna w dokumentach, takich jak makra i kontrolki ActiveX, jest wyłączona w aplikacji Application Guard for Office. Użytkownicy muszą usunąć ochronę funkcji Application Guard, aby włączyć zawartość aktywną.

* Niezaufane pliki z udziałów sieciowych lub plików udostępnionych z OneDrive, OneDrive dla Firm lub SharePoint Online z innej organizacji są otwierane w trybie tylko do odczytu w programie Application Guard. Użytkownicy mogą zapisać lokalną kopię takich plików, aby kontynuować pracę w kontenerze, lub usunąć ochronę, aby bezpośrednio pracować z oryginalnym plikiem.

* Pliki chronione przez usługę Zarządzanie prawami do informacji (IRM) są domyślnie blokowane. Jeśli użytkownicy chcą otwierać takie pliki w widoku chronionym, administrator musi skonfigurować ustawienia zasad dla nieobsługiwanych typów plików w organizacji.

* Wszelkie dostosowania do Office w funkcji Application Guard dla systemu Office nie będą zachowywane, gdy użytkownik się wyczyszczy i ponownie się uruchomi lub po ponownym uruchomieniu urządzenia.

* Tylko narzędzia ułatwień dostępu, które korzystają z struktury INTERFEJSU UŻYTKOWNIKA, mogą zapewnić ułatwienia dostępu dla plików otwieranych w funkcji Application Guard dla Office.

* Łączność sieciowa jest wymagana przy pierwszym uruchomieniu programu Application Guard po instalacji. Do weryfikacji licencji jest wymagana łączność z programem Application Guard.

* W sekcji informacji o dokumencie właściwość *Ostatnio zmodyfikowane przez* może wyświetlać **wartość WDAGUtilityAccount** jako użytkownik. WDAGUtilityAccount to użytkownik anonimowy skonfigurowany w aplikacji Application Guard. Tożsamość użytkownika klasycznego nie jest udostępniana w kontenerze application Guard.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Optymalizacja wydajności dla programu Application Guard dla Office

Ta sekcja zawiera omówienie optymalizacji wydajności używanej w funkcji Application Guard na Office. Te informacje mogą ułatwić administratorom diagnozowanie raportów od użytkowników związanych z wydajnością programu Office lub ogólnym systemem, gdy jest włączona funkcja Application Guard.

Aplikacja Application Guard używa zwirtualizowanego kontenera do odizolowania niezaufanych dokumentów od systemu. Proces tworzenia kontenera i konfigurowania kontenera Application Guard w celu otwierania dokumentów programu Office ma dodatkowe obciążenie związane z wydajnością, które może mieć negatywny wpływ na środowisko użytkownika, gdy użytkownicy otwierają niezaufany dokument.

Aby zapewnić użytkownikom oczekiwane środowisko otwierania plików, w aplikacji Application Guard jest używana logika do wstępnego tworzenia kontenera, gdy w systemie zostanie spełniony następujący heuristic: W ciągu ostatnich 28 dni użytkownik otworzył plik w widoku chronionym lub w doborze aplikacji Application Guard.

Gdy ta heuristic zostanie spełniony, Office wstępnie utworzy kontener Application Guard dla użytkownika po zalogowaniu się w celu Windows. Podczas tej operacji wstępnej tworzenia mogą wystąpić wolne działanie systemu, ale efekt ten zostanie rozwiązany zaraz po ukończeniu operacji.

> [!NOTE]
> Wskazówki potrzebne do heuristic do wstępnego utworzenia kontenera są generowane przez Office, gdy użytkownik korzysta z nich. Jeśli użytkownik zainstaluje Office w nowym systemie, w którym jest włączona funkcja Application Guard, program Office nie utworzy wstępnie kontenera do momentu, gdy użytkownik po raz pierwszy otworzy w systemie niezaufany dokument. Użytkownik zauważy, że otwieranie tego pierwszego pliku w aplikacji Application Guard trwa dłużej.

## <a name="known-issues"></a>Znane problemy

* Wybranie linków internetowych (`http` lub `https`) nie spowoduje otwarcia przeglądarki.
* Domyślnym ustawieniem zasad ochrony przed kopiowaniem i wklejaniem jest włączenie dostępu tylko do schowka do tekstu.
* Domyślnym ustawieniem zasad ochrony nieobsługiwanych typów plików jest blokowanie otwierania niezaufanych nieobsługiwanych typów plików, które są szyfrowane lub mają ustawione zarządzanie prawami do informacji (IRM). Dotyczy to plików, które Microsoft Information Protection etykiety wrażliwości przy użyciu szyfrowania (poufne lub wysoce poufne).
* Pliki CSV i HTML nie są obecnie obsługiwane.
* Program Application Guard Office obecnie nie działa z skompresowanym woluminami plików NTFS. Jeśli jest wyświetlany komunikat o błędzie "ERROR_VIRTUAL_DISK_LIMITATION", spróbuj dekompresowanie głośności.
* Aktualizacje programu .NET mogą powodować niepowodzenie otwierania plików w funkcji Application Guard. Aby obejść ten problem, użytkownicy mogą ponownie uruchomić swoje urządzenie, gdy dotkną tego błędu. Dowiedz się więcej o tym problemie w tece Komunikat o błędzie wyświetlany podczas próby otwarcia Windows Defender Application Guard [lub Piaskownica systemu Windows](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* Aby uzyskać [więcej informacji, zobacz Często Microsoft Defender Application Guard — informacje.](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard) 
