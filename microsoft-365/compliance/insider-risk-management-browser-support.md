---
title: Informacje na temat wykrywania sygnału w przeglądarce zarządzania ryzykiem w niejawnym programie testów i konfiguracji
description: Dowiedz się więcej o wykrywaniu sygnału przeglądarki zarządzania ryzykiem w niejawnym programie testów w programie Microsoft 365
keywords: Microsoft 365, zarządzanie ryzykiem w niejawnym programie testów, zarządzanie ryzykiem, zgodność
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: c3cb9e432f3ea94f88c63cfad928ba577471b420
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014821"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Informacje na temat wykrywania sygnału w przeglądarce zarządzania ryzykiem w niejawnym programie testów i konfiguracji

Przeglądarki sieci Web są często używane przez użytkowników w celu uzyskania dostępu zarówno do plików poufnych, jak i nie poufnych w organizacji. Zarządzanie ryzykiem w niejawnym programie testów pozwala Twojej organizacji wykrywać i działać na sygnały ex ex rozsyłania w przeglądarce dla wszystkich plików nie wykonywalnych przeglądanych w przeglądarkach [Microsoft Edge](https://www.microsoft.com/edge) [i Google Chrome](https://www.google.com/chrome). Sygnalizuje to, że analitycy i wrównanie mogą szybko działać, gdy użytkownicy zasad w zakresie wykonywanych przez użytkowników zasad w zakresie mogą szybko działać w następujących przeglądarkach:

- Pliki skopiowane do osobistego magazynu w chmurze
- Pliki drukowane na urządzenia lokalne lub sieciowe
- Pliki przeniesione lub skopiowane do udziału sieciowego
- Pliki skopiowane na urządzenia USB

Sygnały sygnalizują te zdarzenia w Microsoft Edge za pomocą wbudowanych funkcji przeglądarki i przy użyciu dodatku *Microsoft Compliance* Extension. W przeglądarce Google Chrome klienci używają rozszerzenia *zgodności firmy Microsoft do* wykrywania sygnału.

W poniższej tabeli podsumowano wykryte działania i obsługę rozszerzeń dla poszczególnych przeglądarek:

| **Wykryte działania**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Pliki skopiowane do osobistego magazynu w chmurze         | Natywne             | Rozszerzenie         |
| Pliki drukowane na urządzenia lokalne lub sieciowe      | Natywne             | Rozszerzenie         |
| Pliki przeniesione lub skopiowane do udziału sieciowego | Rozszerzenie          | Rozszerzenie         |
| Pliki skopiowane na urządzenia USB                    | Rozszerzenie          | Rozszerzenie         |

## <a name="common-requirements"></a>Typowe wymagania

Przed zainstalowaniem Microsoft Edge lub rozszerzenia Google Chrome klienci muszą upewnić się, że urządzenia dla użytkowników zasad dotyczących zakresu spełniają następujące wymagania:

- Zalecana jest Windows 10 kompilacja x64, minimalna Windows 10 x64 kompilacja 1809 do obsługi wykrywania sygnału. Wykrywanie sygnału przeglądarki nie jest obecnie obsługiwane na urządzeniach innych Windows urządzeniach.
- [Bieżąca Microsoft 365 z pomocą](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) techniczną w zakresie zarządzania ryzykiem w ramach niejawnego programu testów.
- Urządzenia muszą [być podłączone do](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) portalu zgodności Microsoft 365 zgodności.

Aby uzyskać szczegółowe wymagania dotyczące konfiguracji przeglądarki, zobacz sekcje Microsoft Edge i Google Chrome w dalszej części tego artykułu.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Konfigurowanie wykrywania sygnału przeglądarki na Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>Microsoft Edge wymagań dotyczących przeglądarki

- Spełnia typowe wymagania
- Microsoft Edge x64, 91.0.864.41 lub nowsza
- *Dodatek z rozszerzeniem* zgodności firmy Microsoft w wersji 1.0.0.44 lub wyższej
- Edge.exe nie jest skonfigurowana jako przeglądarka niedozwolone

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Opcja 1: Konfiguracja podstawowa (zalecana do testowania w programie Edge)

Użyj tej opcji, aby skonfigurować selfhost pojedynczy komputer dla każdego urządzenia w organizacji podczas testowania wykrywania sygnału przeglądarki.

Aby wybrać opcję konfiguracji podstawowej, wykonaj następujące czynności:

1. Przejdź do rozszerzenia [zgodności firmy Microsoft](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Zainstaluj rozszerzenie.

### <a name="option-2-intune-setup-for-edge"></a>Opcja 2: Konfiguracja usługi Intune dla programu Edge

Ta opcja umożliwia skonfigurowanie rozszerzenia i wymagań organizacji przy użyciu usługi Intune.

Aby wybrać opcję konfiguracji usługi Intune, wykonaj następujące czynności:

1. Zaloguj się do centrum [administracyjnego Microsoft Endpoint Manager przy](https://endpoint.microsoft.com) użyciu uprawnień administratora.
2. Przejdź do **profilów konfiguracji**.
3. Wybierz **pozycję Utwórz profil**.
4. Wybierz **Windows 10** jako platformę.
5. Wybierz **pozycję Szablony administracyjne** jako *typ profilu, a* następnie wybierz **pozycję Utwórz.**
6. Wybierz **kartę Ustawienia** zaawansowanej.
7. Wybierz **pozycję Edge w wersji 77 lub nowszej.**
8. Wyszukaj rozszerzenia **, które** zawierają przegląd wszystkich ustawień związanych z rozszerzeniami.
9. Wybierz ustawienie **Kontroluj, które rozszerzenia są instalowane dyskretnie.**
10. Wybierz **pozycję Włączone.**
11. Po wyświetleniu monitu dodaj identyfikator rozszerzenia: *lcmcgbabdcbcbcfabdncmoppkajglo***.**
12. Wybierz **przycisk OK.**

### <a name="option-3-group-policy-setup-for-edge"></a>Opcja 3. zasady grupy konfiguracji dla programu Edge

Użyj tej opcji, aby skonfigurować rozszerzenie i wymagania dla całej organizacji przy użyciu zasady grupy.

Aby uzyskać zasady grupy konfiguracji, wykonaj następujące czynności:

**Krok 1. Zaimportuj najnowszy Microsoft Edge szablonu administracyjnego (admx).**

Urządzeniami należy zarządzać przy użyciu zasad grupy, [Microsoft Edge wszystkie](https://www.microsoft.com/edge/business/download) szablony administracyjne muszą zostać zaimportowane do zasady grupy centralnej. Aby uzyskać więcej informacji, zobacz Jak utworzyć magazyn centralny dla [zasady grupy administracyjnych i zarządzać nimi w Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Krok 2. Dodaj dodatek *Microsoft Compliance Extension* do listy *Wymuszaj instalację* .**

Wykonaj następujące czynności, aby dodać rozszerzenie:

1. W **edytorze zasady grupy zarządzaniem** przejdź do jednostki organizacyjnej.
2. Rozwiń następującą **ścieżkę Zasady konfiguracji komputera/użytkownika** \>  \> **Szablony administracyjne** \>  \> Klasyczne szablony **administracyjne Microsoft Edge** \> **rozszerzenia.** Ta ścieżka może się różnić w zależności od konfiguracji dla organizacji.
3. Wybierz **pozycję Konfigurowanie rozszerzeń instalowanych dyskretnie.**
4. Kliknij prawym przyciskiem myszy i wybierz polecenie **Edytuj**.
5. Zaznacz przycisk **radiowy** Włączone.
6. Wybierz **pozycję Pokaż**.
7. W **przypadku wartości** dodaj następujący wpis: *lcmcgbabdcbcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. Wybierz **przycisk OK** i wybierz pozycję **Zastosuj**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Konfigurowanie wykrywania sygnału przeglądarki dla przeglądarki Google Chrome

Obsługa wykrywania sygnału wykrywania sygnału w niejawnym programie testów dla przeglądarki Google Chrome jest włączona za pośrednictwem rozszerzenia *zgodności firmy Microsoft*. To rozszerzenie obsługuje również funkcję DLP punktu końcowego w przeglądarce Chrome. Aby uzyskać więcej informacji na temat obsługi ochrony przed dLP dla punktów końcowych, zobacz [Wprowadzenie do rozszerzenia zgodności firmy Microsoft (wersja Preview).](/microsoft-365/compliance/dlp-chrome-get-started)

### <a name="google-chrome-browser-requirements"></a>Wymagania przeglądarki Google Chrome

- Spełnia typowe wymagania
- Najnowsza wersja przeglądarki Google Chrome x64
- *Rozszerzenie zgodności firmy Microsoft* 2.0.0.183 lub nowsza
- Chrome.exe nie jest skonfigurowana jako przeglądarka niedozwolone

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>Opcja 1: Konfiguracja podstawowa (zalecana do testowania w przeglądarce Chrome)

Użyj tej opcji, aby skonfigurować selfhost pojedynczy komputer dla każdego urządzenia w organizacji podczas testowania wykrywania sygnału przeglądarki.

Aby wybrać opcję konfiguracji podstawowej, wykonaj następujące czynności:

**Krok 1. Włączanie wymaganych kluczy rejestru za pomocą programu PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Te klucze rejestru są wymagane do zapewnienia prawidłowego działania rozszerzenia. Przed testowaniem sygnałów należy włączyć te klucze rejestru.*

**Krok 2. Instalowanie rozszerzenia *zgodności firmy Microsoft***

1. Przejdź do rozszerzenia [zgodności firmy Microsoft](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Zainstaluj rozszerzenie.

### <a name="option-2-intune-setup-for-chrome"></a>Opcja 2: Konfiguracja usługi Intune dla przeglądarki Chrome

Ta opcja umożliwia skonfigurowanie rozszerzenia i wymagań organizacji przy użyciu usługi Intune.

Aby wybrać opcję konfiguracji usługi Intune, wykonaj następujące czynności:

**Krok 1. Włączanie wymaganego klucza rejestru za pomocą usługi Intune**

1. Uruchom następujący skrypt programu PowerShell:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Zaloguj się do centrum [Microsoft Endpoint Manager administracyjnego](https://endpoint.microsoft.com).
3. Przejdź do **opcji Skrypty** \> **urządzeń** i wybierz pozycję **Dodaj.**
4. Przejdź do lokalizacji skryptu utworzonego po wyświetleniu monitu.
5. Wybierz następujące ustawienia:

    - Uruchom ten skrypt przy użyciu zalogowanych poświadczeń: *Tak*
    - Wymuszanie sprawdzania podpisu skryptu: *Nie*
    - Uruchom skrypt na 64-bitowym hoście programu PowerShell: *Tak*

6. Wybierz odpowiednie grupy urządzeń i zastosuj zasady.

**Krok 2. Konfigurowanie usługi Intune Force Install**

Przed dodaniem rozszerzenia Microsoft DLP Chrome do listy wymuszania zainstalowanych rozszerzeń musisz zainstalować plik szablonu administracyjnego Chrome (admx) do zarządzania usługą Intune. Aby uzyskać szczegółowe instrukcje, zobacz [Zarządzanie przeglądarką Chrome za pomocą Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). Po zainstalowaniu pliku szablonu administracyjnego wykonaj następujące czynności:

1. Zaloguj się do centrum [Microsoft Endpoint Manager administracyjnego](https://endpoint.microsoft.com).
2. Przejdź do **profilów konfiguracji**.
3. Wybierz **pozycję Utwórz profil**.
4. Wybierz **Windows 10** jako *platformę*.
5. Wybierz **pozycję** Niestandardowe jako *typ* profilu.
6. Wybierz **kartę Ustawienia** zaawansowanej.
7. Wybierz **pozycję Dodaj.**
8. Wprowadź następujące informacje o zasadach:

    - OMA-URI: *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Typ danych: *Ciąg*
    - Wartość: *\<enabled/\>\<data id=”ExtensionInstallForcelistDesc” value=”1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx″/\>*

9. Wybierz pozycję **Utwórz**.

### <a name="option-3-group-policy-setup-for-chrome"></a>Opcja 3. zasady grupy dla przeglądarki Chrome

Użyj tej opcji, aby skonfigurować rozszerzenie i wymagania dla całej organizacji przy użyciu zasady grupy.

Aby uzyskać zasady grupy konfiguracji, wykonaj następujące czynności:

**Krok 1. Importowanie pliku szablonu administracyjnego przeglądarki Chrome**

Urządzeniami należy zarządzać przy użyciu programu zasady grupy, a wszystkie szablony administracyjne przeglądarki [Chrome](https://chromeenterprise.google/browser/download/) muszą zostać zaimportowane do zasady grupy Centralnej. Aby uzyskać więcej informacji, zobacz Jak utworzyć magazyn centralny dla [zasady grupy administracyjnych i zarządzać nimi w Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**Krok 2. Włączanie wymaganego klucza rejestru za pomocą programu PowerShell**

1. Utwórz skrypt programu PowerShell o następującej zawartości:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Otwórz **konsolę zasady grupy zarządzania i** przejdź do jednostki organizacyjnej.
3. Kliknij prawym przyciskiem myszy i wybierz **pozycję Utwórz zasadę grupy w tej domenie i połącz ją tutaj**. Po wyświetleniu monitu przypisz opisową nazwę do tego obiektu zasady grupy (GPO). Na przykład natychmiastowy skrypt *programu PowerShell dla programu DLP dla przeglądarki Chrome*.
4. Po utworzeniu grupy kliknij prawym przyciskiem myszy i wybierz polecenie **Edytuj**. Zaznaczenie tej opcji przenosi do zasady grupy obiekt.
5. Przejdź do **preferencji Konfiguracja komputera** \> **Ustawienia** \> **panelu sterowania** \> **Zaplanowane zadania**.
6. Kliknij prawym przyciskiem myszy pusty obszar **w obszarze Zaplanowane** zadania i **wybierz pozycję** \> Nowe zadanie **natychmiastowe (co najmniej Windows 7).**
7. Wprowadź nazwę *i* opis *zadania*.
8. Wybierz odpowiednie konto, aby uruchomić natychmiastowe zadanie. Na przykład urząd *NT*.
9. Wybierz **pozycję Uruchom z najwyższymi uprawnieniami**.
10. Skonfiguruj zasady dla Windows 10.
11. Na karcie **Akcje** wybierz pozycję **Uruchom program**.
12. Wprowadź ścieżkę do programu/skryptu utworzonego w **kroku 1**.
13. Wybierz **pozycję Zastosuj**.

**Krok 3. Dodanie rozszerzenia przeglądarki Chrome do listy Wymuszaj instalację**

1. W **edytorze zasady grupy zarządzaniem** przejdź do jednostki organizacyjnej.
2. Rozwiń następującą **ścieżkę Zasady konfiguracji komputera/użytkownika** \>  \> **Szablony administracyjne** \> Klasyczne **szablony administracyjne programu** \> **Google** \> **Chrome** \> **.** Ta ścieżka może się różnić w zależności od konfiguracji dla organizacji.
3. Wybierz **pozycję Konfiguruj listę wymuszania zainstalowanych rozszerzeń**.
4. Kliknij prawym przyciskiem myszy i wybierz polecenie **Edytuj**.
5. Wybierz przycisk **radiowy** Włączone.
6. Wybierz **pozycję Pokaż**.
7. W **przypadku** wartości dodaj następujący *wpis: echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. Wybierz **przycisk OK** i wybierz pozycję **Zastosuj**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Testowanie i weryfikowanie wykrywanie sygnału przeglądarki zarządzania ryzykiem w niejawnym programie testów

1. Utwórz zasady zarządzania ryzykiem w niejawnym programie testów z włączonymi wskaźnikami urządzeń.
2. Aby przetestować wykrywanie sygnału dla plików skopiowanych do magazynu osobistego w chmurze, wykonaj następujące czynności z obsługiwanego Windows urządzenia:

    - Otwórz witrynę internetową udostępniania plików (Microsoft OneDrive, Dysk Google itp.) przy użyciu typu przeglądarki skonfigurowanego do wykrywania sygnału.
    - Za pomocą przeglądarki przekaż plik, który nie jest wykonywalny, do witryny sieci Web.
3. Aby przetestować wykrywanie sygnału dla plików drukowanych na urządzeniach lokalnych lub sieciowych, plików przeniesionych lub skopiowanych do udziału sieciowego oraz plików skopiowanych na urządzenia USB, wykonaj następujące czynności z obsługiwanego Windows urządzenia:

    - Otwórz plik nie wykonywalny bezpośrednio w przeglądarce. Aby można było przeglądać plik, trzeba otworzyć go bezpośrednio w Eksploratorze plików lub otworzyć go na nowej karcie przeglądarki zamiast na stronie internetowej.
    - Wydrukuj plik.
    - Zapisz plik na urządzeniu USB.
    - Zapisz plik na dysku sieciowym.
  
4. Po utworzeniu pierwszych zasad zarządzania ryzykiem w niejawnym programie testów zaczniesz otrzymywać alerty ze wskaźników aktywności po upływie około 24 godzin. Na [pulpicie nawigacyjnym alertów](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) są sprawdzane alerty zarządzania ryzykiem niejawnego programu testów dotyczące testowanych działań.
