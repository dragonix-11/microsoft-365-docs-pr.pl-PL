---
title: Dowiedz się więcej o wykrywaniu sygnałów w przeglądarce zarządzania ryzykiem wewnętrznym i konfigurowaniu go
description: Dowiedz się więcej o wykrywaniu sygnałów w przeglądarce zarządzania ryzykiem wewnętrznym w Microsoft 365
keywords: Microsoft 365, zarządzanie ryzykiem wewnętrznym, zarządzanie ryzykiem, zgodność
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
ms.openlocfilehash: e904c4576081cd459ca905a56e3dd6cec5b1af31
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758734"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>Dowiedz się więcej o wykrywaniu sygnałów w przeglądarce zarządzania ryzykiem wewnętrznym i konfigurowaniu go

Przeglądarki internetowe są często używane przez użytkowników do uzyskiwania dostępu do poufnych i niewrażliwych plików w organizacji. Zarządzanie ryzykiem wewnętrznym umożliwia organizacji wykrywanie i działanie na sygnałach eksfiltracji przeglądarki dla wszystkich plików wykonywalnych wyświetlanych w przeglądarkach [Microsoft Edge](https://www.microsoft.com/edge) i [Google Chrome](https://www.google.com/chrome). Dzięki tym sygnałom analitycy i badacze mogą szybko działać, gdy dowolne z następujących działań jest wykonywane przez użytkowników zasad w zakresie podczas korzystania z tych przeglądarek:

- Pliki skopiowane do osobistego magazynu w chmurze
- Pliki drukowane na urządzeniach lokalnych lub sieciowych
- Pliki przesyłane lub kopiowane do udziału sieciowego
- Pliki skopiowane na urządzenia USB

Sygnały dotyczące tych zdarzeń są wykrywane w Microsoft Edge przy użyciu wbudowanych funkcji przeglądarki i przy użyciu dodatku *Rozszerzenie zgodności firmy Microsoft*. W przeglądarce Google Chrome klienci używają *rozszerzenia zgodności firmy Microsoft* do wykrywania sygnałów.

Poniższa tabela zawiera podsumowanie wykrytych działań i obsługi rozszerzeń dla każdej przeglądarki:

| **Wykryte działania**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| Pliki skopiowane do osobistego magazynu w chmurze         | Macierzystego             | Rozszerzenie         |
| Pliki drukowane na urządzeniach lokalnych lub sieciowych      | Macierzystego             | Rozszerzenie         |
| Pliki przesyłane lub kopiowane do udziału sieciowego | Rozszerzenie          | Rozszerzenie         |
| Pliki skopiowane na urządzenia USB                    | Rozszerzenie          | Rozszerzenie         |

## <a name="common-requirements"></a>Typowe wymagania

Przed zainstalowaniem dodatku Microsoft Edge lub rozszerzenia Google Chrome klienci muszą upewnić się, że urządzenia dla użytkowników zasad w zakresie spełniają następujące wymagania:

- Zalecana jest najnowsza kompilacja Windows 10 x64, minimalna Windows 10 kompilacji x64 1809 w celu obsługi wykrywania sygnałów. Wykrywanie sygnału przeglądarki nie jest obecnie obsługiwane na urządzeniach innych niż Windows.
- [Bieżąca subskrypcja Microsoft 365](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) z pomocą techniczną dotyczącą zarządzania ryzykiem wewnętrznym.
- Urządzenia muszą zostać [dołączone](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) do portalu Microsoft 365 Compliance.

Aby uzyskać szczegółowe wymagania dotyczące konfiguracji przeglądarki, zobacz sekcje Microsoft Edge i Google Chrome w dalszej części tego artykułu.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>Konfigurowanie wykrywania sygnału przeglądarki dla Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>wymagania przeglądarki Microsoft Edge

- Spełnianie typowych wymagań
- Microsoft Edge wersji x64, 91.0.864.41 lub nowszej
- *Dodatek Microsoft Compliance Extension* w wersji 1.0.0.44 lub nowszej
- Edge.exe nie jest skonfigurowana jako niezamówiona przeglądarka

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>Opcja 1. Konfiguracja podstawowa (zalecana do testowania przy użyciu przeglądarki Edge)

Użyj tej opcji, aby skonfigurować samoobsługowe hostowanie pojedynczej maszyny dla każdego urządzenia w organizacji podczas testowania wykrywania sygnału przeglądarki.

Aby uzyskać podstawową opcję konfiguracji, wykonaj następujące kroki:

1. Przejdź do obszaru [Rozszerzenie zgodności firmy Microsoft](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. Zainstaluj rozszerzenie.

### <a name="option-2-intune-setup-for-edge"></a>Opcja 2: konfiguracja Intune dla przeglądarki Edge

Użyj tej opcji, aby skonfigurować rozszerzenie i wymagania dla organizacji przy użyciu Intune.

Aby uzyskać opcję konfiguracji Intune, wykonaj następujące kroki:

1. Zaloguj się do [centrum administracyjnego Microsoft Endpoint Manager](https://endpoint.microsoft.com) przy użyciu uprawnień administratora.
2. Przejdź do pozycji **Profile konfiguracji**.
3. Wybierz pozycję **Utwórz profil**.
4. Wybierz **Windows 10** jako platformę.
5. Wybierz pozycję **Szablony administracyjne** jako *typ profilu* i wybierz pozycję **Utwórz.**
6. Wybierz kartę **Ustawienia**.
7. Wybierz **pozycję Edge w wersji 77 lub nowszej.**
8. Wyszukaj **rozszerzenia** , które zawierają omówienie wszystkich ustawień związanych z rozszerzeniem.
9. Wybierz ustawienie **Kontroluj, które rozszerzenia są instalowane w trybie dyskretnym.**
10. Wybierz pozycję **Włączone.**
11. Dodaj identyfikator rozszerzenia po wyświetleniu monitu: *lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. Wybierz przycisk **OK.**

### <a name="option-3-group-policy-setup-for-edge"></a>Opcja 3: konfiguracja zasady grupy dla przeglądarki Edge

Użyj tej opcji, aby skonfigurować rozszerzenie i wymagania dla całej organizacji przy użyciu zasady grupy.

Aby uzyskać opcję konfiguracji zasady grupy, wykonaj następujące kroki:

**Krok 1. Zaimportuj najnowszy plik szablonu administracyjnego Microsoft Edge (admx).**

Urządzenia muszą być zarządzane przy użyciu zasad grupy, a wszystkie [Microsoft Edge szablony administracyjne](https://www.microsoft.com/edge/business/download) muszą zostać zaimportowane do sklepu zasady grupy Central Store. Aby uzyskać więcej informacji, zobacz [How to create and manage the Central Store for zasady grupy Administrative Templates in Windows (Jak utworzyć magazyn centralny dla szablonów administracyjnych zasady grupy i zarządzać nimi w Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store)).

**Krok 2. Dodaj do listy *Force Install* do dodatku *Rozszerzenie zgodności firmy Microsoft*.**

Wykonaj następujące kroki, aby dodać rozszerzenie:

1. W **edytorze zarządzania zasady grupy** przejdź do jednostki organizacyjnej (OU).
2. Rozwiń następującą ścieżkę **Zasady** \> **konfiguracji** \> komputera/użytkownika **Szablony administracyjne Klasyczne szablony** \> \> **administracyjne** **Microsoft Edge** \> **rozszerzenia**. Ta ścieżka może się różnić w zależności od konfiguracji organizacji.
3. Wybierz pozycję **Konfiguruj, które rozszerzenia są instalowane w trybie dyskretnym.**
4. Kliknij prawym przyciskiem myszy i wybierz pozycję **Edytuj**.
5. Sprawdź przycisk Radiowy **włączone** .
6. Wybierz pozycję **Pokaż**.
7. W polu **Wartość** dodaj następujący wpis: *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. Wybierz przycisk **OK** i wybierz pozycję **Zastosuj**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>Konfigurowanie wykrywania sygnału przeglądarki dla przeglądarki Google Chrome

Obsługa wykrywania sygnałów w przeglądarce zarządzania ryzykiem wewnętrznym dla przeglądarki Google Chrome jest włączona za pośrednictwem *rozszerzenia zgodności firmy Microsoft*. To rozszerzenie obsługuje również protokół DLP punktu końcowego w przeglądarce Chrome. Aby uzyskać więcej informacji na temat obsługi DLP punktu końcowego, zobacz [Wprowadzenie z rozszerzeniem zgodności firmy Microsoft (wersja zapoznawcza).](/microsoft-365/compliance/dlp-chrome-get-started)

### <a name="google-chrome-browser-requirements"></a>Wymagania przeglądarki Google Chrome

- Spełnianie typowych wymagań
- Najnowsza wersja przeglądarki Google Chrome x64
- *Rozszerzenie zgodności firmy Microsoft* w wersji 2.0.0.183 lub nowszej
- Chrome.exe nie jest skonfigurowana jako niezamówiona przeglądarka

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>Opcja 1. Konfiguracja podstawowa (zalecana do testowania w przeglądarce Chrome)

Użyj tej opcji, aby skonfigurować samoobsługowe hostowanie pojedynczej maszyny dla każdego urządzenia w organizacji podczas testowania wykrywania sygnału przeglądarki.

Aby uzyskać podstawową opcję konfiguracji, wykonaj następujące kroki:

**Krok 1. Włączanie wymaganych kluczy rejestru przy użyciu programu PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>Te klucze rejestru są wymagane w celu zapewnienia prawidłowej funkcjonalności rozszerzenia. Te klucze rejestru należy włączyć przed przetestowaniem jakichkolwiek sygnałów.*

**Krok 2. Instalowanie *rozszerzenia zgodności firmy Microsoft***

1. Przejdź do obszaru [Rozszerzenie zgodności firmy Microsoft](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. Zainstaluj rozszerzenie.

### <a name="option-2-intune-setup-for-chrome"></a>Opcja 2: konfiguracja Intune dla przeglądarki Chrome

Użyj tej opcji, aby skonfigurować rozszerzenie i wymagania dla organizacji przy użyciu Intune.

Aby uzyskać opcję konfiguracji Intune, wykonaj następujące kroki:

**Krok 1. Włączanie wymaganego klucza rejestru przy użyciu Intune**

1. Uruchom następujący skrypt programu PowerShell:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. Zaloguj się do [centrum administracyjnego Microsoft Endpoint Manager](https://endpoint.microsoft.com).
3. Przejdź do pozycji **Skrypty urządzeń** \> i wybierz pozycję **Dodaj.** 
4. Przejdź do lokalizacji skryptu utworzonego po wyświetleniu monitu.
5. Wybierz następujące ustawienia:

    - Uruchom ten skrypt przy użyciu poświadczeń logowania: *Tak*
    - Wymuszanie sprawdzania podpisu skryptu: *Nie*
    - Uruchamianie skryptu na 64-bitowym hoście programu PowerShell: *Tak*

6. Wybierz odpowiednie grupy urządzeń i zastosuj zasady.

**Krok 2. Konfigurowanie Intune wymuszania instalacji**

Przed dodaniem rozszerzenia Microsoft DLP Chrome do listy wymuszonych zainstalowanych rozszerzeń należy zainstalować plik szablonu administracyjnego chrome (admx) na potrzeby zarządzania Intune. Aby uzyskać szczegółowe wskazówki, zobacz [Manage Chrome Browser with Microsoft Intune (Zarządzanie przeglądarką Chrome przy użyciu Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune)). Po zainstalowaniu pliku szablonu administracyjnego wykonaj następujące kroki:

1. Zaloguj się do [centrum administracyjnego Microsoft Endpoint Manager](https://endpoint.microsoft.com).
2. Przejdź do pozycji **Profile konfiguracji**.
3. Wybierz pozycję **Utwórz profil**.
4. Wybierz **Windows 10** jako *platformę*.
5. Wybierz pozycję **Niestandardowe** jako typ *profilu* .
6. Wybierz kartę **Ustawienia**.
7. Wybierz pozycję **Dodaj.**
8. Wprowadź następujące informacje o zasadach:

    - OMA-URI: *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - Typ danych: *Ciąg*
    - Wartość: *\<enabled/\>\<data id="ExtensionInstallForcelistDesc" value="1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/\>*

9. Wybierz pozycję **Utwórz**.

### <a name="option-3-group-policy-setup-for-chrome"></a>Opcja 3: konfiguracja zasady grupy dla przeglądarki Chrome

Użyj tej opcji, aby skonfigurować rozszerzenie i wymagania dla całej organizacji przy użyciu zasady grupy.

Aby uzyskać opcję konfiguracji zasady grupy, wykonaj następujące kroki:

**Krok 1. Importowanie pliku szablonu administracyjnego chrome**

Urządzenia muszą być zarządzane przy użyciu zasady grupy, a wszystkie [szablony administracyjne programu Chrome](https://chromeenterprise.google/browser/download/) muszą zostać zaimportowane do sklepu zasady grupy Central Store. Aby uzyskać więcej informacji, zobacz [How to create and manage the Central Store for zasady grupy Administrative Templates in Windows (Jak utworzyć magazyn centralny dla szablonów administracyjnych zasady grupy i zarządzać nimi w Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store)).

**Krok 2. Włączanie wymaganego klucza rejestru przy użyciu programu PowerShell**

1. Utwórz skrypt programu PowerShell z następującą zawartością:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Otwórz **konsolę zarządzania zasady grupy** i przejdź do jednostki organizacyjnej .
3. Kliknij prawym przyciskiem myszy i wybierz **pozycję Utwórz obiekt zasad grupy w tej domenie i połącz go tutaj**. Po wyświetleniu monitu przypisz opisową nazwę do tego obiektu zasady grupy (GPO). Na przykład *natychmiastowy skrypt programu PowerShell dla programu DLP Chrome*.
4. Po utworzeniu obiektu zasad grupy kliknij prawym przyciskiem myszy i wybierz pozycję **Edytuj**. To zaznaczenie spowoduje przejście do obiektu zasady grupy.
5. Przejdź do **obszaru Ustawienia panelu** \> **sterowania Preferencje** \> **konfiguracji** \> komputera **Zaplanowane zadania**.
6. Kliknij prawym przyciskiem myszy pusty obszar w obszarze **Zaplanowane zadania** i wybierz pozycję **Nowe** \> **zadanie natychmiastowe (co najmniej Windows 7).**
7. Wprowadź *nazwę* zadania i *opis*.
8. Wybierz odpowiednie konto, aby uruchomić zadanie natychmiastowe. Na przykład *nt urzędu*.
9. Wybierz pozycję **Uruchom z najwyższymi uprawnieniami**.
10. Skonfiguruj zasady dla Windows 10.
11. Na karcie **Akcje** wybierz **pozycję Uruchom program**.
12. Wprowadź ścieżkę do programu/skryptu utworzonego w **kroku 1**.
13. Wybierz pozycję **Zastosuj**.

**Krok 3. Dodawanie rozszerzenia Chrome do listy Wymuszanie instalacji**

1. W **edytorze zarządzania zasady grupy** przejdź do jednostki organizacyjnej (OU).
2.  Rozwiń następującą ścieżkę **Zasady** \> **konfiguracji** \> komputera/użytkownika **Szablony administracyjne Klasyczne szablony** \> administracyjne Google **Chrome** \> **Extensions** \> \>. Ta ścieżka może się różnić w zależności od konfiguracji organizacji.
3. Wybierz **pozycję Skonfiguruj listę wymuszonych zainstalowanych rozszerzeń**.
4. Kliknij prawym przyciskiem myszy i wybierz pozycję **Edytuj**.
5. Wybierz przycisk radiowy **Włączone** .
6. Wybierz pozycję **Pokaż**.
7. W polu **Wartość** dodaj następujący wpis: *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. Wybierz przycisk **OK** i wybierz pozycję **Zastosuj**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>Testowanie i weryfikowanie wykrywania sygnałów w przeglądarce zarządzania ryzykiem wewnętrznym

1. Utwórz zasady zarządzania ryzykiem wewnętrznym z włączonymi wskaźnikami urządzeń.
2. Aby przetestować wykrywanie sygnału dla plików skopiowanych do osobistego magazynu w chmurze, wykonaj następujące kroki z obsługiwanego urządzenia Windows:

    - Otwórz witrynę internetową do udostępniania plików (Microsoft OneDrive, Dysk Google itp.) przy użyciu typu przeglądarki skonfigurowanego do wykrywania sygnału.
    - W przeglądarce przekaż plik wykonywalny do witryny internetowej.
3. Aby przetestować wykrywanie sygnału dla plików wydrukowanych na urządzeniach lokalnych lub sieciowych, plików przesłanych lub skopiowanych do udziału sieciowego oraz plików skopiowanych na urządzenia USB, wykonaj następujące kroki z obsługiwanego urządzenia Windows:

    - Otwórz plik wykonywalny bezpośrednio w przeglądarce. Plik należy otworzyć bezpośrednio za pośrednictwem Eksplorator plików lub otworzyć na nowej karcie przeglądarki do wyświetlania, a nie na stronie internetowej.
    - Wydrukuj plik.
    - Zapisz plik na urządzeniu USB.
    - Zapisz plik na dysku sieciowym.
  
4. Po utworzeniu pierwszych zasad zarządzania ryzykiem wewnętrznym zaczniesz otrzymywać alerty ze wskaźników aktywności po około 24 godzinach. Sprawdź [pulpit nawigacyjny Alerty](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) , aby uzyskać alerty dotyczące zarządzania ryzykiem wewnętrznym dla przetestowanych działań.
