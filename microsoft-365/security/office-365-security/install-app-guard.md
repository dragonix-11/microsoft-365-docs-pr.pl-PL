---
title: Application Guard dla pakietu Office dla administratorów
keywords: ochrona aplikacji, ochrona, izolacja, izolowany kontener, izolacja sprzętowa
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
description: Uzyskaj najnowsze informacje na temat izolacji opartej na sprzęcie. Zapobiegaj obecnym i pojawiającym się atakom, takim jak luki w zabezpieczeniach lub złośliwe linki, zakłócając produktywność pracowników i bezpieczeństwo przedsiębiorstwa.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9a7e820a4aedb4338111ef0fc76a35de480ea1f8
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530931"
---
# <a name="application-guard-for-office-for-admins"></a>Application Guard dla pakietu Office dla administratorów

**Dotyczy:** Word, Excel i PowerPoint dla Microsoft 365 Apps, Windows 10 Enterprise, Windows 11 Enterprise

Microsoft Defender Application Guard for Office (Application Guard for Office) pomaga zapobiegać uzyskiwaniu przez niezaufane pliki dostępu do zaufanych zasobów, zapewniając przedsiębiorstwu bezpieczeństwo przed nowymi i pojawiającym się atakami. W tym artykule przedstawiono instrukcje dla administratorów dotyczące konfigurowania urządzeń na potrzeby wersji zapoznawczej funkcji Application Guard dla pakietu Office. Zawiera informacje o wymaganiach systemowych i krokach instalacji, aby włączyć funkcję Application Guard dla pakietu Office na urządzeniu.

## <a name="prerequisites"></a>Wymagania wstępne

### <a name="minimum-hardware-requirements"></a>Minimalne wymagania sprzętowe

* **Procesor CPU**: 64-bitowe, 4 rdzenie (fizyczne lub wirtualne), rozszerzenia wirtualizacji (Intel VT-x LUB AMD-V), core i5 równoważne lub wyższe zalecane
* **Pamięć fizyczna**: 8 GB pamięci RAM
* **Dysk twardy**: 10 GB wolnego miejsca na dysku systemowym (zalecane dyski SSD)

### <a name="minimum-software-requirements"></a>Minimalne wymagania dotyczące oprogramowania

* **Windows**: wersja Windows 10 Enterprise, kompilacja klienta 2004 (20H1) kompilacja 19041 lub nowsza. Obsługiwane są wszystkie wersje Windows 11.
* **Office**: Aplikacje Microsoft 365 z kompilacją 16.0.13530.10000 lub nowszą. W przypadku instalacji bieżącego kanału i miesięcznego kanału Enterprise Channel jest to wersja 2011. W przypadku Semi-Annual Enterprise Channel i Semi-Annual Enterprise Channel (wersja zapoznawcza) minimalna wersja to 2108 lub nowsza. Obsługiwane są wersje 32-bitowe i 64-bitowe.
* **Pakiet aktualizacji**: Windows 10 skumulowana miesięczna aktualizacja zabezpieczeń [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

Aby uzyskać szczegółowe wymagania systemowe, zobacz [Wymagania systemowe dotyczące Microsoft Defender Application Guard](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). Zapoznaj się również z przewodnikami producenta komputera dotyczącymi włączania technologii wirtualizacji.
Aby dowiedzieć się więcej o Aplikacje Microsoft 365 kanałach aktualizacji, zobacz [Omówienie kanałów aktualizacji dla Aplikacje Microsoft 365](/deployoffice/overview-update-channels).

### <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

* Zabezpieczenia platformy Microsoft 365 E5
* Microsoft 365 A5 dla wykładowców
* Microsoft 365 A5 for Students

> [!NOTE]
> Aplikacje Microsoft 365 dla przedsiębiorstw z aktywacją komputera udostępnionego lub licencjonowaniem opartym na urządzeniach nie mają dostępu do funkcji Application Guard dla pakietu Office.
>
> Plany licencjonowania bezpiecznych dokumentów umożliwiają dostęp do funkcji Application Guard dla pakietu Office. Aby uzyskać więcej informacji, zobacz [Safe Documents in Microsoft 365 E5/A5 (Bezpieczne dokumenty w Microsoft 365 E5/A5](/microsoft-365/security/office-365-security/safe-docs)).

## <a name="deploy-application-guard-for-office"></a>Wdrażanie funkcji Application Guard dla pakietu Office

### <a name="enable-application-guard-for-office"></a>Włączanie funkcji Application Guard dla pakietu Office

1. Pobierz i zainstaluj **Windows 10 zbiorcze miesięczne aktualizacje zabezpieczeń KB4571756**.

2. Wybierz **pozycję Microsoft Defender Application Guard** w obszarze Funkcje systemu Windows i wybierz przycisk **OK**. Włączenie funkcji Application Guard spowoduje wyświetlenie monitu o ponowne uruchomienie systemu. Możesz wybrać ponowne uruchomienie teraz lub po kroku 3.

   :::image type="content" source="../../media/ag03-deploy.png" alt-text="Okno dialogowe Funkcje systemu Windows z wyświetloną grupą dostępności" lightbox="../../media/ag03-deploy.png":::

   Tę funkcję można również włączyć, uruchamiając następujące polecenie programu PowerShell jako administrator:

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. Wyszukaj **Microsoft Defender Application Guard w trybie zarządzanym**, zasady grupy w **konfiguracji\\komputera Szablony\\administracyjne Składniki\\ systemu Windows Microsoft Defender Application Guard**. Włącz te zasady, ustawiając wartość w obszarze Opcje jako **2** lub **3**, a następnie wybierając przycisk **OK** lub **Zastosuj**.

   :::image type="content" source="../../media/ag04-deploy.png" alt-text="Opcja włączenia grupy dostępności w trybie zarządzanym" lightbox="../../media/ag04-deploy.png":::

   Zamiast tego można ustawić odpowiednie zasady CSP:

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/Settings/AllowWindowsDefenderApplicationGuard** <br> Typ danych: **Liczba całkowita** <br> Wartość: **2**

4. Uruchom ponownie system.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>Ustawianie opinii & diagnostycznej w celu wysyłania pełnych danych

> [!NOTE]
> Nie jest to jednak wymagane, dlatego skonfigurowanie opcjonalnych danych diagnostycznych pomoże zdiagnozować zgłoszone problemy.

Ten krok gwarantuje, że dane niezbędne do identyfikowania i rozwiązywania problemów docierają do firmy Microsoft. Wykonaj następujące kroki, aby włączyć diagnostykę na urządzeniu z systemem Windows:

1. Otwórz **pozycję Ustawienia** z menu Start.

   :::image type="content" source="../../media/ag05-diagnostic.png" alt-text="Menu Start" lightbox="../../media/ag05-diagnostic.png":::

2. W **obszarze Ustawienia systemu Windows** wybierz pozycję **Prywatność**.

   :::image type="content" source="../../media/ag06-diagnostic.png" alt-text="Menu Ustawienia systemu Windows" lightbox="../../media/ag06-diagnostic.png":::

3. W obszarze Prywatność wybierz pozycję **Diagnostyka & opinii** i wybierz pozycję **Opcjonalne dane diagnostyczne**.

   :::image type="content" source="../../media/ag07a-diagnostic.png" alt-text="Menu Diagnostyka i opinie" lightbox="../../media/ag07a-diagnostic.png":::

Aby uzyskać więcej informacji na temat konfigurowania ustawień diagnostycznych systemu Windows, zobacz [Konfigurowanie danych diagnostycznych systemu Windows w organizacji](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>Upewnij się, że funkcja Application Guard dla pakietu Office jest włączona i działa

Przed potwierdzeniem włączenia funkcji Application Guard dla pakietu Office uruchom program Word, Excel lub PowerPoint na urządzeniu, na którym wdrożono zasady. Upewnij się, że pakiet Office jest aktywowany. Aby aktywować produkt pakietu Office, może być konieczne użycie tożsamości służbowej.

Aby potwierdzić, że funkcja Application Guard dla pakietu Office jest włączona, uruchom program Word, Excel lub PowerPoint, a następnie otwórz niezaufany dokument. Możesz na przykład otworzyć dokument pobrany z Internetu lub załącznik wiadomości e-mail od osoby spoza organizacji.

Po pierwszym otwarciu niezaufanego pliku może zostać wyświetlony ekran powitalny pakietu Office, taki jak w poniższym przykładzie. Może być wyświetlany przez jakiś czas, gdy funkcja Application Guard dla pakietu Office jest aktywowana i plik jest otwierany. Kolejne otwory niezaufanych plików powinny być szybsze.

:::image type="content" source="../../media/ag08-confirm.png" alt-text="Strona powitalna aplikacji pakietu Office" lightbox="../../media/ag08-confirm.png":::

Po otwarciu pliku powinno zostać wyświetlonych kilka wizualnych wskaźników, że plik został otwarty w usłudze Application Guard dla pakietu Office:

* Objaśnienie na wstążce

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Plik dokumentu z małą notatką funkcji App Guard" lightbox="../../media/ag09-confirm.png":::

* Ikona aplikacji z osłoną na pasku zadań

  ![Ikona na pasku zadań.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>Konfigurowanie funkcji Application Guard dla pakietu Office

Pakiet Office obsługuje następujące zasady, aby umożliwić konfigurowanie możliwości funkcji funkcji Application Guard dla pakietu Office. Te zasady można skonfigurować za pomocą zasad grupy lub za pośrednictwem [usługi zasad w chmurze pakietu Office](/DeployOffice/overview-office-cloud-policy-service).

> [!NOTE]
> Skonfigurowanie tych zasad może wyłączyć niektóre funkcje plików otwartych w usłudze Application Guard dla pakietu Office.

|Zasad|Opis|
|---|---|
|Nie używaj funkcji Application Guard dla pakietu Office|Włączenie tych zasad spowoduje, że program Word, Excel i PowerPoint będą używać kontenera izolacji Widoku chronionego zamiast funkcji Application Guard dla pakietu Office. Te zasady mogą służyć do tymczasowego wyłączania funkcji Application Guard dla pakietu Office, gdy występują problemy z pozostawieniem jej włączonej dla przeglądarki Microsoft Edge.|
|Konfigurowanie funkcji Application Guard dla kontenera pakietu Office przed utworzeniem|Te zasady określają, czy kontener Application Guard for Office do izolowania niezaufanych plików jest wstępnie tworzony w celu zwiększenia wydajności w czasie wykonywania. Jeśli to ustawienie zostanie włączone, możesz określić liczbę dni, przez które będzie można kontynuować wstępne tworzenie kontenera, lub zezwolić wbudowanemu pakietowi Office na wstępne utworzenie kontenera.
|Nie zezwalaj na kopiowanie/wklejanie dokumentów pakietu Office otwartych w usłudze Application Guard dla pakietu Office|Włączenie tych zasad uniemożliwi użytkownikowi kopiowanie i wklejanie zawartości z dokumentu otwartego w usłudze Application Guard dla pakietu Office do dokumentu otwartego poza nim.|
|Wyłączanie przyspieszania sprzętowego w funkcji Application Guard dla pakietu Office|Te zasady określają, czy funkcja Application Guard dla pakietu Office używa przyspieszania sprzętowego do renderowania grafiki. Jeśli to ustawienie zostanie włączone, usługa Application Guard dla pakietu Office korzysta z renderowania opartego na oprogramowaniu (CPU) i nie ładuje żadnych sterowników graficznych innych firm ani nie wchodzi w interakcje z żadnym połączonym sprzętem graficznym.
|Wyłączanie ochrony nieobsługiwanych typów plików w usłudze Application Guard dla pakietu Office|Te zasady określają, czy usługa Application Guard dla pakietu Office zablokuje otwarcie nieobsługiwanych typów plików lub czy umożliwi przekierowanie do widoku chronionego.
|Wyłączanie dostępu do kamery i mikrofonu dla dokumentów otwartych w usłudze Application Guard dla pakietu Office|Włączenie tych zasad spowoduje usunięcie dostępu pakietu Office do aparatu i mikrofonu wewnątrz funkcji Application Guard dla pakietu Office.|
|Ograniczanie drukowania z dokumentów otwartych w usłudze Application Guard dla pakietu Office|Włączenie tych zasad spowoduje ograniczenie drukarek, do których użytkownik może drukować z pliku otwartego w usłudze Application Guard dla pakietu Office. Można na przykład użyć tych zasad, aby ograniczyć użytkownikom możliwość drukowania tylko w formacie PDF.|
|Uniemożliwianie użytkownikom usuwania funkcji Application Guard na potrzeby ochrony pakietu Office w plikach|Włączenie tych zasad spowoduje usunięcie opcji (w środowisku aplikacji pakietu Office), aby wyłączyć funkcję Application Guard dla ochrony pakietu Office lub otworzyć plik poza usługą Application Guard dla pakietu Office. <p> **Uwaga:** Użytkownicy mogą nadal pomijać te zasady, ręcznie usuwając właściwość mark-of-the-web z pliku lub przenosząc dokument do zaufanej lokalizacji.|

> [!NOTE]
> Następujące zasady będą wymagać od użytkownika wylogowywania się i ponownego zalogowania się do systemu Windows, aby obowiązywać:
>
> * Wyłączanie kopiowania/wklejania dokumentów otwartych w usłudze Application Guard dla pakietu Office
> * Ograniczanie drukowania dokumentów otwartych w usłudze Application Guard dla pakietu Office
> * Wyłączanie dostępu kamery i mikrofonu do dokumentów otwartych w usłudze Application Guard dla pakietu Office

## <a name="submit-feedback"></a>Prześlij opinię

### <a name="submit-feedback-via-feedback-hub"></a>Przesyłanie opinii za pośrednictwem Centrum opinii

Jeśli podczas uruchamiania usługi Application Guard dla pakietu Office wystąpią jakiekolwiek problemy, zachęcamy do przesyłania opinii za pośrednictwem Centrum opinii:

1. Otwórz **aplikację Centrum opinii** i zaloguj się.

2. Jeśli podczas uruchamiania funkcji Application Guard zostanie wyświetlone okno dialogowe błędu, wybierz pozycję **Zgłoś firmie Microsoft** w oknie dialogowym błędu, aby rozpocząć przesyłanie nowej opinii. W przeciwnym razie przejdź do <https://aka.ms/mdagoffice-fb> pozycji , aby wybrać odpowiednią kategorię dla funkcji Application Guard, a następnie wybierz pozycję **Dodaj nową opinię+&nbsp;** w prawym górnym rogu.

3. Wprowadź podsumowanie w polu **Podsumowanie opinii** , jeśli nie zostało ono jeszcze wypełnione.

4. Wprowadź szczegółowy opis napotkanego problemu i czynności, które zostały opisane **w polu Objaśnienie bardziej szczegółowo** , a następnie wybierz pozycję **Dalej**.

5. Wybierz bąbelek obok pozycji **Problem**. Upewnij się, że wybrana kategoria to **Zabezpieczenia i prywatność \> Microsoft Defender Application Guard — pakiet Office**, a następnie wybierz pozycję **Dalej**.

6. Wybierz pozycję **Nowa opinia**, a następnie **pozycję Dalej**.

7. Zbierz ślady dotyczące problemu:

   1. Rozwiń kafelek **Utwórz ponownie mój problem** .

   2. Jeśli napotkany problem występuje podczas działania funkcji Application Guard, otwórz wystąpienie usługi Application Guard. Otwarcie wystąpienia umożliwia zbieranie dodatkowych śladów z kontenera usługi Application Guard.

   3. Wybierz pozycję **Rozpocznij nagrywanie** i poczekaj, aż kafelek przestanie się obracać, a następnie zaczekaj na zatrzymanie *nagrywania*.

   4. W pełni odtwórz problem z funkcją Application Guard. Reprodukcja może obejmować próbę uruchomienia wystąpienia funkcji Application Guard i oczekiwanie na niepowodzenie lub odtworzenie problemu w uruchomionym wystąpieniu funkcji Application Guard.

   5. Wybierz kafelek **Zatrzymaj nagrywanie** .

   6. Pozostaw otwarte wszystkie uruchomione wystąpienia usługi Application Guard, nawet przez kilka minut po przesłaniu, aby można było również zebrać diagnostykę kontenera.

8. Dołącz wszelkie odpowiednie zrzuty ekranu lub pliki związane z problemem.

9. Wybierz pozycję **Prześlij**.

### <a name="submit-feedback-via-office-customer-voice"></a>Przesyłanie opinii za pośrednictwem usługi Office Customer Voice

Możesz również przesłać opinię z pakietu Office, jeśli problem występuje, gdy dokumenty pakietu Office są otwierane w usłudze Application Guard. Zapoznaj się z [podręcznikiem niejawnych testerów pakietu Office](https://insider.office.com/handbook) , aby przesłać opinię.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>Integracja z Ochrona punktu końcowego w usłudze Microsoft Defender i Ochrona usługi Office 365 w usłudze Microsoft Defender

Funkcja Application Guard dla pakietu Office jest zintegrowana z usługą Ochrona punktu końcowego w usłudze Microsoft Defender w celu zapewnienia monitorowania i zgłaszania alertów dotyczących złośliwych działań wykonywanych w środowisku izolowanym.

[Bezpieczne dokumenty w usłudze Microsoft E365 E5](/microsoft-365/security/office-365-security/safe-docs) to funkcja, która używa Ochrona punktu końcowego w usłudze Microsoft Defender do skanowania dokumentów otwartych w usłudze Application Guard dla pakietu Office. Aby uzyskać dodatkową warstwę ochrony, użytkownicy nie mogą opuścić funkcji Application Guard dla pakietu Office, dopóki nie zostaną określone wyniki skanowania.

Ochrona punktu końcowego w usłudze Microsoft Defender to platforma zabezpieczeń, która pomaga sieciom przedsiębiorstw zapobiegać zaawansowanym zagrożeniom, wykrywać je, badać je i reagować na nie. Aby uzyskać więcej informacji na temat tej platformy, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). Aby dowiedzieć się więcej na temat dołączania urządzeń do tej platformy, zobacz [Dołączanie urządzeń do usługi Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure).

Możesz również skonfigurować Ochrona usługi Office 365 w usłudze Microsoft Defender do pracy z usługą Defender for Endpoint. Aby uzyskać więcej informacji, zobacz [Integrowanie Ochrona usługi Office 365 w usłudze Defender z Ochrona punktu końcowego w usłudze Microsoft Defender](integrate-office-365-ti-with-mde.md).

## <a name="limitations-and-considerations"></a>Ograniczenia i zagadnienia

* Funkcja Application Guard dla pakietu Office to tryb chroniony, który izoluje niezaufane dokumenty, aby nie mogły uzyskać dostępu do zaufanych zasobów firmowych, intranetu, tożsamości użytkownika i dowolnych plików na komputerze. W związku z tym, jeśli użytkownik próbuje uzyskać dostęp do funkcji, która ma zależność od takiego dostępu, na przykład wstawianie obrazu z pliku lokalnego na dysku, dostęp kończy się niepowodzeniem i generuje monit podobny do poniższego przykładu. Aby umożliwić niezaufanemu dokumentowi dostęp do zaufanych zasobów, użytkownicy muszą usunąć ochronę funkcji Application Guard z dokumentu.

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="Okno dialogowe z komunikatem o bezpieczeństwie i stanem funkcji" lightbox="../../media/ag09-confirm.png":::

  > [!NOTE]
  > Poinformuj użytkowników, aby usunęli ochronę tylko wtedy, gdy ufają plikowi i jego źródle lub skąd pochodzą.

* Gdy niezaufany dokument jest przechowywany w zaufanej lokalizacji, zaufanie z lokalizacji jest dziedziczone przez dokument. Zazwyczaj magazyn w chmurze organizacji jest identyfikowany jako zaufana lokalizacja.

* Aktywna zawartość w dokumentach, takich jak makra i kontrolki ActiveX, jest wyłączona w funkcji Application Guard dla pakietu Office. Użytkownicy muszą usunąć ochronę funkcji Application Guard, aby włączyć aktywną zawartość.

* Niezaufane pliki z udziałów sieciowych lub plików udostępnionych z usługi OneDrive, OneDrive dla Firm lub SharePoint Online z innej organizacji otwarte jako tylko do odczytu w usłudze Application Guard. Użytkownicy mogą zapisać lokalną kopię takich plików, aby kontynuować pracę w kontenerze lub usunąć ochronę, aby bezpośrednio pracować z oryginalnym plikiem.

* Pliki chronione przez usługę Information Rights Management (IRM) są domyślnie blokowane. Jeśli użytkownicy chcą otwierać takie pliki w widoku chronionym, administrator musi skonfigurować ustawienia zasad dla nieobsługiwanych typów plików dla organizacji.

* Wszelkie dostosowania aplikacji pakietu Office w usłudze Application Guard dla pakietu Office nie będą utrwalane po wylogowaniu się użytkownika i ponownym zalogowaniu się lub po ponownym uruchomieniu urządzenia.

* Tylko narzędzia ułatwień dostępu korzystające z platformy UIA mogą zapewnić dostępne środowisko dla plików otwartych w usłudze Application Guard dla pakietu Office.

* Łączność sieciowa jest wymagana do pierwszego uruchomienia funkcji Application Guard po instalacji. Do zweryfikowania licencji wymagana jest łączność z usługą Application Guard.

* W sekcji informacji dokumentu właściwość *Last Modified By* może wyświetlać konto **WDAGUtilityAccount** jako użytkownik. WDAGUtilityAccount to użytkownik anonimowy skonfigurowany w usłudze Application Guard. Tożsamość użytkownika pulpitu nie jest współużytkowana w kontenerze usługi Application Guard.

## <a name="performance-optimizations-for-application-guard-for-office"></a>Optymalizacje wydajności dla funkcji Application Guard dla pakietu Office

Ta sekcja zawiera omówienie optymalizacji wydajności używanych w funkcji Application Guard dla pakietu Office. Te informacje mogą pomóc administratorom w diagnozowaniu raportów od użytkowników związanych z wydajnością pakietu Office lub ogólnego systemu po włączeniu funkcji Application Guard.

Funkcja Application Guard używa zwirtualizowanego kontenera do izolowania niezaufanych dokumentów z dala od systemu. Proces tworzenia kontenera i konfigurowania kontenera usługi Application Guard w celu otwierania dokumentów pakietu Office ma obciążenie wydajnością, które może negatywnie wpłynąć na środowisko użytkownika, gdy użytkownicy otwierają niezaufany dokument.

Aby zapewnić użytkownikom oczekiwane środowisko otwierania plików, usługa Application Guard używa logiki do wstępnego utworzenia kontenera, gdy w systemie zostanie spełniony następujący heurystyczny element: Użytkownik otworzył plik w widoku chronionym lub funkcji Application Guard w ciągu ostatnich 28 dni.

Po spełnieniu tego heurystycznego pakietu Office utworzy wstępnie kontener usługi Application Guard dla użytkownika po zalogowaniu się do systemu Windows. Mimo że ta operacja przed utworzeniem jest w toku, system może mieć niską wydajność, ale efekt zostanie rozwiązany natychmiast po zakończeniu operacji.

> [!NOTE]
> Wskazówki potrzebne do utworzenia kontenera w języku heurystycznym są generowane przez aplikacje pakietu Office, gdy użytkownik z nich korzysta. Jeśli użytkownik zainstaluje pakiet Office w nowym systemie, w którym włączono funkcję Application Guard, pakiet Office nie utworzy wstępnie kontenera dopiero po pierwszym otwarciu niezaufanego dokumentu w systemie. Użytkownik zauważy, że otwieranie pierwszego pliku w usłudze Application Guard trwa dłużej.

## <a name="known-issues"></a>Znane problemy

* Wybranie linków internetowych (`http` lub `https`) nie powoduje otwarcia przeglądarki.
* Domyślnym ustawieniem zasad ochrony przed kopiowaniem i wklejaniem jest włączenie dostępu schowka tylko do tekstu.
* Domyślnym ustawieniem zasad ochrony nieobsługiwanych typów plików jest zablokowanie otwierania niezaufanych nieobsługiwanych typów plików, które są szyfrowane lub mają ustawioną usługę Zarządzanie prawami do informacji (IRM). Obejmuje to pliki zaszyfrowane przy użyciu etykiet poufności z Microsoft Purview Information Protection.
* Pliki CSV i HTML nie są obecnie obsługiwane.
* Funkcja Application Guard dla pakietu Office obecnie nie współpracuje ze skompresowanymi woluminami NTFS. Jeśli występuje błąd "ERROR_VIRTUAL_DISK_LIMITATION", spróbuj usunąć skompresowanie woluminu.
* Aktualizacje do platformy .NET może spowodować niepowodzenie otwierania plików w usłudze Application Guard. Aby obejść ten problem, użytkownicy mogą ponownie uruchomić swoje urządzenie po wystąpieniu tego błędu. Dowiedz się więcej o problemie w oknie [Otrzymywanie komunikatu o błędzie podczas próby otwarcia Windows Defender Application Guard lub Piaskownica systemu Windows](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* Aby uzyskać [dodatkowe informacje, zobacz Często zadawane pytania — Microsoft Defender Application Guard.](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard)
