---
title: Analizator konfiguracji zgodności firmy Microsoft dla Menedżera zgodności
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak korzystać z Analizatora konfiguracji zgodności firmy Microsoft, aby szybko rozpocząć korzystanie z Menedżera zgodności firmy Microsoft.
ms.openlocfilehash: a679f0483431313672ac0dfa1101eb9909b6c060
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525157"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Analizator konfiguracji zgodności firmy Microsoft dla Menedżera zgodności (wersja zapoznawcza)

**W tym artykule:** Dowiedz się, jak zainstalować i uruchomić narzędzie Microsoft Compliance Configure Analyzer, aby szybko rozpocząć pracę z narzędziem Microsoft Compliance Manger.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Omówienie analizatora konfiguracji zgodności firmy Microsoft (MCCA, Compliance Configuration Analyzer) (wersja zapoznawcza)

Analizator konfiguracji zgodności firmy Microsoft (MCCA, Microsoft Compliance Analyzer) to narzędzie w wersji Preview, które może ułatwić Ci wprowadzenie do [Menedżera zgodności firmy Microsoft](compliance-manager.md). MCCA to narzędzie oparte na programie PowerShell, które pobiera bieżące konfiguracje Twojej organizacji i sprawdza je pod Microsoft 365 zalecanymi najlepszymi rozwiązaniami. Te najważniejsze wskazówki są oparte na zestawie kontrolek, które obejmują kluczowe przepisy i standardy w zakresie ochrony danych i zarządzania danymi.

Firma MCCA pomoże Ci szybko sprawdzić, które działania ulepszeń w Menedżerze zgodności mają zastosowanie do Twojego bieżącego Microsoft 365 zgodności. Każde działanie zidentyfikowane przez firmę MCCA będzie zawierało zalecenia dotyczące wdrożenia z bezpośrednimi linkami do Menedżera zgodności i odpowiedniego rozwiązania w celu rozpoczęcia działań naprawczych.

Dodatkowy zasób do zrozumienia usługi MCCA można znaleźć w instrukcjach [README GitHub](https://github.com/OfficeDev/MCCA#overview). Ta strona zawiera szczegółowe informacje o wymaganiach wstępnych i zawiera pełne instrukcje dotyczące instalacji. Nie potrzebujesz konta programu GitHub, aby uzyskać dostęp do tej strony.

Dostępność **: Firma** MCCA jest dostępna dla wszystkich organizacji z licencjami usług Office 365 i Microsoft 365 oraz dla klientów usługi Government Community (GCC) Moderate, GCC High i Department of Defense (DoD).

## <a name="install-mcca-and-run-a-report"></a>Instalowanie pakietu MCCA i uruchamianie raportu

Narzędzie MCCA można zainstalować przy użyciu Windows PowerShell. Po pobraniu i zainstalowaniu narzędzia nie trzeba powtarzać tych czynności, aby uruchomić raporty. Przy każdym otwarciu usługi MCCA będzie wymagane poświadczenie logowania, co spowoduje wygenerowanie nowego, zaktualizowanego raportu.

### <a name="step-1-install-windows-powershell"></a>Krok 1. Instalowanie Windows PowerShell

Aby rozpocząć, potrzebny będzie moduł Exchange Online PowerShell (w wersji 2.0.3 lub wyższej), który jest dostępny w galerii programu PowerShell. [Uzyskaj instrukcje instalacji](https://www.powershellgallery.com/packages/ExchangeOnlineManagement/2.0.3).

### <a name="step-2-install-mcca"></a>Krok 2. Instalowanie aplikacji MCCA

Aby zainstalować usługę MCCA, zacznij od programu PowerShell w trybie administratora. Wykonaj poniższe czynności:

1. Wybierz przycisk Windows **Start**.
1. Wpisz **PowerShell**, kliknij prawym przyciskiem **myszy pozycję Windows PowerShell**, a następnie wybierz **pozycję Uruchom jako administrator**.
1. W wierszu polecenia wpisz:

    ```powershell
    Install-Module -Name MCCAPreview
    ```

### <a name="step-3-run-a-report"></a>Krok 3. Uruchamianie raportu

Po zainstalowaniu aplikacji MCCA można uruchomić aplikację MCCA i wygenerować raport. Aby uruchomić raport:

1. Otwieranie programu PowerShell
2. Uruchom polecenie cmdlet:

    ```powershell
    Get-MCCAReport
    ```

    Jeśli jesteś klientem usługi GCC, musisz podać dodatkowy parametr wejściowy, aby uruchomić raport:

    ```powershell
    Get-MCCAReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. Po zakończeniu pracy aplikacji MCCA aplikacja sprawdza wersję wstępną i prosi o poświadczenia. W wierszu wprowadzania nazwy użytkownika zaloguj się przy użyciu adresu e Microsoft 365-mail konta (wyświetl role, [które są uprawnione do tworzenia raportów](#role-based-reporting)). Następnie wprowadź hasło w wierszu monitu o hasło.

Wygenerowanie raportu zajmie około 2–5 minut. Gdy to zrobisz, zostanie otwarte okno przeglądarki z wyświetlonym raportem w formacie HTML. Za każdym razem, gdy uruchamiasz narzędzie, będzie ono prosić o poświadczenia i generować nowy raport. Ten raport jest przechowywany lokalnie w katalogu C: \ Użytkownicy \ *nazwa* _użytkownika \ AppData \ Local \ Microsoft \ MCCA.

Można uzyskać dostęp do wcześniej wygenerowanych raportów z tego katalogu.

## <a name="understanding-your-report"></a>Opis raportu

Raport odzwierciedla dane na podstawie daty i czasu, w której został wygenerowany. W górnej sekcji przedstawiono szczegółowe informacje na temat tego, kiedy został wygenerowany, nazwa organizacji i identyfikator dzierżawy.

#### <a name="geolocation-based-reporting"></a>Raportowanie oparte na lokalizacji geograficznej

Sekcja **Uwaga** pokazuje, że raport został dostosowany na podstawie lokalizacji geograficznej dzierżawy. Rekomendacje w narzędziu będą specyficzne dla danego kraju lub regionu.

Wybór lokalizacji geograficznej jest używany do oceny typów informacji poufnych, które są istotne dla tej lokalizacji geograficznej, i do generowania raportu dostosowanego do danego kraju lub regionu. Wybierz lokalizacje geograficzne na podstawie danych, które masz w swojej dzierżawie.

Aby zmienić informacje o lokalizacji raportu, musisz podać parametr wejściowy geolokalizacji (-Geo). Możesz wybrać jedną lub wiele lokalizacji geograficznych mających zastosowanie do Twojej dzierżawy.

Wykonaj poniższe instrukcje, aby uruchomić raport na podstawie konkretnej lokalizacji:

1. Otwieranie programu PowerShell
2. Aby określić określony region, uruchom polecenie cmdlet, używając liczb z poniższej tabeli, które odpowiadają krajowi lub regionowi. Wprowadź wiele numerów, oddzielając je przecinkami. Na przykład poniższe polecenie cmdlet spowoduje uruchomienie dostosowanego raportu dla Asia-Pacific i Japonii:

    ```powershell
    Get-MCCAReport -Geo @(1,7)
    ```
  | Wprowadzanie danych |  Kraj lub region | 
  | :------------- | :------------: |
  | 1 | Asia-Pacific |
  | 2 | Australia |
  | 3 | Kanada |
  | 4 | Europa (z wyjątkiem Francji) / Bliski Wschód/Afryka |
  | 5 | Francja |
  | 6 | Indie |
  | 7 | Japonia |
  | 8 | Korea |
  | 9 | Ameryka Północna (z wyjątkiem Kanady) |
  | 10 | Ameryka Południowa |
  | 11 | Republika Południowej Afryki |
  | 12 | Szwajcaria |
  | 13 | Zjednoczone Emiraty Arabskie |
  | 14 | Zjednoczone Królestwo |


 > [!NOTE]
> Raport zawsze będzie zawierał międzynarodowe typy informacji poufnych, takie jak kod SWIFT, numer karty kredytowej itp.

#### <a name="role-based-reporting"></a>Raportowanie oparte na rolach

Raport zostanie również dostosowany do Twojej roli.

W poniższej tabeli przedstawiono role, które mają dostęp do poszczególnych sekcji raportu. Inne role w organizacji (nie wymienione w poniższej tabeli) mogą nie być w stanie uruchomić tego narzędzia lub mogą uruchamiać to narzędzie i mieć ograniczony dostęp do informacji w ostatnim raporcie.

![MCCA — role.](../media/compliance-manager-mcca-roles.png "Role w u administratorach firmy MCCA")

Wyjątki:
1. Użytkownicy nie będą mogli generować raportu dla adresów IP poza sekcją "Użyj usługi IRM dla sieci Exchange Online".
2. Użytkownicy będą mogli generować raporty dla adresów IP oprócz sekcji "Użyj usługi IRM dla sieci Exchange Online".
3. Użytkownicy będą mogli generować raport dla adresów IP poza sekcją "Włączanie zgodności komunikacji w u usługi O365".
4. Użytkownicy nie będą mogli generować raportów dla adresów IP oprócz sekcji "Włączanie inspekcji w u Office 365".
5. Użytkownicy będą mogli generować raport dla adresów IP oprócz sekcji "Włączanie inspekcji Office 365".

#### <a name="solutions-summary-section"></a>Sekcja Podsumowanie rozwiązań

Sekcja **Podsumowanie rozwiązań** raportu zawiera omówienie działań usprawnień, które Twoja organizacja może podjąć w Menedżerze zgodności w celu poprawy stanu zgodności.

![MCCA — podsumowanie rozwiązań.](../media/compliance-manager-mcca-solutions.png "Ekran podsumowania rozwiązań firmy MCCA")

Firma MCCA ocenia bieżące konfiguracje pod względem zalecanych działań udoskonalania w Menedżerze zgodności. W tej sekcji wymieniono wszelkie działania usprawnień zidentyfikowane przez narzędzie MCCA, które wymagają uwagi.

Obok każdego rozwiązania firmy Microsoft są oznaczane kolorami pola wskazujące liczbę elementów odpowiadających działaniom udoskonalania w Menedżerze zgodności. Akcje są podzielone na trzy stany:

- **OK**: działania, które spełniają zalecane warunki i w tej chwili nie wymagają uwagi
- **Ulepszenie**: działania, które wymagają uwagi
- **Zalecenie**: działania, które nie wymagają uwagi, ale do których zalecamy najlepsze rozwiązania
 
Wybierz pole, aby wyświetlić ulepszenia i zalecenia.

**Elementy ze stanem Ulepszenie**

Wybierz menu rozwijane obok etykiety **Ulepszenie** po prawej stronie akcji udoskonalania. Zobaczysz krótkie podsumowanie i szczegóły dotyczące bieżących ustawień oraz zalecane działania ulepszeń. Podsumowanie zawiera bezpośrednie linki do Menedżera zgodności, odpowiedniego rozwiązania w Centrum zgodności platformy Microsoft 365 i odpowiedniej dokumentacji.

Kliknięcie linku Menedżer zgodności umożliwia wyświetlenie filtrowanych widoków wszystkich działań udoskonalania w ramach tego rozwiązania, które nie zostały jeszcze zaimplementowane. W tym miejscu możesz zobaczyć liczbę punktów, które można osiągnąć, aby zwiększyć ocenę [zgodności, oceny](compliance-score-calculation.md), do których są stosowane, oraz odpowiednie przepisy i certyfikaty.

W przypadku zasad DLP jest przycisk Skrypt  rozwiązywania problemów, który udostępnia wstępnie wygenerowany skrypt programu PowerShell na podstawie zalecanych czynności. Możesz go skopiować i wkleić bezpośrednio w konsoli programu PowerShell. Spowoduje to utworzenie zasad DLP w trybie testowania

**Elementy ze stanem zalecenia**

Wybierz menu rozwijane **obok etykiety** Zalecenie po prawej stronie akcji udoskonalania. Zostanie wyświetlony podsumowanie bieżącego środowiska pracy Microsoft 365 organizacji związane z działaniem udoskonalania oraz zalecane najlepsze rozwiązania.

## <a name="resources"></a>Zasoby

Aby uzyskać bardziej szczegółowe informacje na temat instalowania, konfigurowania i używania usługi MCCA, zobacz instrukcje [dotyczące funkcji README](https://github.com/OfficeDev/MCCA#overview) GitHub (nie jest wymagane GitHub konta).

Aby uzyskać więcej informacji na Windows PowerShell, zobacz Jak [używać dokumentacji programu PowerShell](/powershell/scripting/how-to-use-docs). Zobacz też [Rozpoczynanie Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
