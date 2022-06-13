---
title: Microsoft Compliance Configuration Analyzer for Compliance Manager
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
description: Dowiedz się, jak za pomocą analizatora konfiguracji zgodności firmy Microsoft szybko rozpocząć korzystanie z programu Microsoft Purview Compliance Manager.
ms.openlocfilehash: a973412c2d40993b47343273675cee3922b57cdf
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012819"
---
# <a name="microsoft-compliance-configuration-analyzer-for-compliance-manager-preview"></a>Microsoft Compliance Configuration Analyzer for Compliance Manager (wersja zapoznawcza)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**W tym artykule:** Dowiedz się, jak zainstalować i uruchomić narzędzie Microsoft Compliance Configure Analyzer, aby szybko rozpocząć pracę z rozwiązaniem Microsoft Compliance Manger.

## <a name="microsoft-compliance-configuration-analyzer-mcca-preview-overview"></a>Omówienie programu Microsoft Compliance Configuration Analyzer (MCCA) (wersja zapoznawcza)

Microsoft Compliance Configuration Analyzer (MCCA) to narzędzie w wersji zapoznawczej, które może ułatwić rozpoczęcie pracy z [programem Microsoft Purview Compliance Manager](compliance-manager.md). MCCA to narzędzie oparte na programie PowerShell, które pobiera bieżące konfiguracje organizacji i weryfikuje je pod kątem Microsoft 365 zalecanych najlepszych rozwiązań. Te najlepsze rozwiązania są oparte na zestawie mechanizmów kontroli, które obejmują kluczowe przepisy i standardy dotyczące ochrony danych i zarządzania danymi.

McCA może pomóc szybko zobaczyć, które akcje poprawy w Menedżerze zgodności mają zastosowanie do bieżącego środowiska Microsoft 365. Każda akcja zidentyfikowana przez mcca będzie udostępniać zalecenia dotyczące implementacji, z bezpośrednimi linkami do Menedżera zgodności i odpowiednim rozwiązaniem, aby rozpocząć podejmowanie działań naprawczych.

Dodatkowym zasobem umożliwiającym zrozumienie mcca jest [odwiedzenie instrukcji README dotyczących GitHub](https://github.com/OfficeDev/MCCA#overview). Ta strona zawiera szczegółowe informacje o wymaganiach wstępnych i zawiera pełne instrukcje instalacji. Nie potrzebujesz konta GitHub, aby uzyskać dostęp do tej strony.

**Dostępność**: mcca jest dostępna dla wszystkich organizacji z licencjami Office 365 i Microsoft 365 i us Government Community (GCC) Moderate, GCC High i Department of Defense (DoD).

## <a name="install-mcca-and-run-a-report"></a>Instalowanie mcca i uruchamianie raportu

Narzędzie MCCA można zainstalować przy użyciu Windows PowerShell. Po pobraniu i zainstalowaniu narzędzia nie trzeba powtarzać tych kroków, aby uruchamiać raporty. Za każdym razem, gdy otworzysz mcca, będzie monitować o poświadczenia logowania i wygeneruje nowy, zaktualizowany raport.

### <a name="step-1-install-the-exchange-online-powershell-v2-module"></a>Krok 1. Instalowanie modułu Exchange Online programu PowerShell w wersji 2

Aby rozpocząć, potrzebny jest moduł Exchange Online programu PowerShell (wersja 2.0.3 lub nowsza), który jest dostępny w galerii programu PowerShell. Aby uzyskać instrukcje instalacji, zobacz [Instalowanie i obsługa modułu EXO v2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

### <a name="step-2-install-mcca"></a>Krok 2. Instalowanie mcca

Aby zainstalować usługę MCCA, rozpocznij od użycia programu PowerShell w trybie administratora. Wykonaj poniższe kroki:

1. Wybierz przycisk Windows **Start**.
1. Wpisz **program PowerShell**, kliknij prawym przyciskiem myszy **Windows PowerShell**, a następnie wybierz pozycję **Uruchom jako administrator**.
1. W wierszu polecenia wpisz:

    ```powershell
    Install-Module -Name MCCAPreview
    ```

### <a name="step-3-run-a-report"></a>Krok 3. Uruchamianie raportu

Po zainstalowaniu mcca, można uruchomić mcca i wygenerować raport. Aby uruchomić raport:

1. Otwórz program PowerShell
2. Uruchom polecenie cmdlet:

    ```powershell
    Get-MCCAReport
    ```

    Jeśli jesteś klientem GCC High, musisz podać dodatkowy parametr wejściowy, aby uruchomić raport:

    ```powershell
    Get-MCCAReport -ExchangeEnvironmentName O365USGovGCCHigh
    ```

3. Po uruchomieniu mcca wykonuje wstępne sprawdzanie wersji i poprosić o poświadczenia. W wierszu polecenia Wprowadź nazwę użytkownika zaloguj się przy użyciu adresu e-mail Microsoft 365 konta ([wyświetl role kwalifikujące się do tworzenia raportów](#role-based-reporting)). Następnie wprowadź hasło w wierszu polecenia hasła.

Wygenerowanie raportu potrwa około 2–5 minut. Po zakończeniu zostanie otwarte okno przeglądarki i zostanie wyświetlony raport HTML. Za każdym razem, gdy uruchamiasz narzędzie, będzie ono monitować o poświadczenia i generować nowy raport. Ten raport jest przechowywany lokalnie w katalogu C: \ Users \ *username* \ AppData \ Local \ Microsoft \ MCCA.

Dostęp do wcześniej wygenerowanych raportów można uzyskać z tego katalogu.

## <a name="understanding-your-report"></a>Informacje o raporcie

Raport odzwierciedla dane na podstawie daty i godziny, o której został wygenerowany. Górna sekcja zawiera szczegółowe informacje o tym, kiedy został wygenerowany, nazwa organizacji i identyfikator dzierżawy.

### <a name="geolocation-based-reporting"></a>Raportowanie oparte na geolokalizacji

Sekcja **Uwaga** pokazuje, że raport jest dostosowany na podstawie lokalizacji geograficznej dzierżawy. Rekomendacje wymienione w narzędziu będą specyficzne dla Twojego kraju lub regionu.

Wybór geolokalizacji służy do oceny poufnych typów informacji (SIC), które są istotne dla tej geolokalizacji, i generowania raportu zgodnego z twoim krajem lub regionem. Wybierz lokalizacje geograficzne na podstawie danych znajdujących się w dzierżawie.

Aby zmienić informacje o lokalizacji raportu, musisz podać parametr wejściowy geolokalizacji (-Geo). Możesz wybrać jedną lub wiele geolokalizacji mających zastosowanie do dzierżawy.

Postępuj zgodnie z tymi instrukcjami, aby uruchomić raport na podstawie określonej lokalizacji:

1. Otwórz program PowerShell
2. Aby określić określony region, uruchomisz polecenie cmdlet przy użyciu liczb z poniższej tabeli, które odpowiadają krajowi lub regionowi. Wprowadź wiele liczb, oddzielając je przecinkami. Na przykład poniższe polecenie cmdlet uruchomi dostosowany raport dla Asia-Pacific i Japonii:

    ```powershell
    Get-MCCAReport -Geo @(1,7)
    ```

  | Wejście |  Kraj lub region |
  | :------------- | :------------: |
  | 1 | Asia-Pacific |
  | 2 | Australia |
  | 3 | Kanada |
  | 4 | Europa (z wyłączeniem Francji) / Bliski Wschód / Afryka |
  | 5 | Francja |
  | 6 | Indie |
  | 7 | Japonia |
  | 8 | Korea |
  | 9 | Ameryka Północna (z wyłączeniem Kanady) |
  | 10 | Ameryka Południowa |
  | 11 | Republika Południowej Afryki |
  | 12 | Szwajcaria |
  | 13 | Zjednoczone Emiraty Arabskie |
  | 14 | Zjednoczone Królestwo |

  > [!NOTE]
  > Raport będzie zawsze zawierać międzynarodowe typy informacji poufnych obsługiwane przez mcca, takie jak kod SWIFT, numer karty kredytowej itp.

### <a name="role-based-reporting"></a>Raportowanie oparte na rolach

Raport zostanie również dostosowany na podstawie Twojej roli.

W poniższej tabeli przedstawiono role, do których sekcji raportu masz dostęp. Inne role w organizacji (niewymienne w poniższej tabeli) mogą nie być w stanie uruchomić narzędzia lub mogą uruchomić narzędzie i mieć ograniczony dostęp do informacji w raporcie końcowym.

![MCCA — role.](../media/compliance-manager-mcca-roles.png "Role MCCA")

Wyjątki:

1. Użytkownicy nie będą mogli generować raportu dla adresu IP oprócz sekcji "Używanie usługi IRM dla Exchange Online".
2. Użytkownicy będą mogli generować raporty dla adresu IP oprócz sekcji "Używanie usługi IRM dla Exchange Online".
3. Użytkownicy będą mogli generować raporty dla adresu IP oprócz sekcji "Włącz zgodność komunikacji w usłudze O365".
4. Użytkownicy nie będą mogli generować raportu dla adresu IP poza sekcją "Włącz inspekcję w Office 365".
5. Użytkownicy będą mogli generować raporty dla adresu IP oprócz sekcji "Włącz inspekcję w Office 365".

### <a name="solutions-summary-section"></a>Sekcja Podsumowanie rozwiązań

Sekcja **Podsumowanie rozwiązań** raportu zawiera omówienie akcji poprawy, które organizacja może podjąć w Menedżerze zgodności, aby poprawić stan zgodności.

![MCCA — podsumowanie rozwiązań.](../media/compliance-manager-mcca-solutions.png "Ekran podsumowania rozwiązań MCCA")

Usługa MCCA ocenia bieżące konfiguracje pod kątem zalecanych akcji poprawy w menedżerze zgodności. Każda akcja poprawy określona przez narzędzie MCCA jako wymagająca uwagi zostanie wymieniona w tej sekcji.

Obok każdego rozwiązania firmy Microsoft znajdują się kolorowe pola wskazujące liczbę elementów odpowiadających akcjom poprawy w Menedżerze zgodności. Akcje są podzielone na trzy stany stanu:

- **OK**: akcje, które spełniają zalecane warunki i nie wymagają obecnie uwagi
- **Ulepszenie**: akcje wymagające uwagi
- **Zalecenie**: akcje, które nie wymagają uwagi, ale dla których zalecamy najlepsze rozwiązania

Wybierz pole, aby wyświetlić ulepszenia i zalecenia.

#### <a name="items-with-the-improvement-status"></a>Elementy ze stanem poprawy

Wybierz listę rozwijaną obok etykiety **Ulepszenie** po prawej stronie akcji poprawy. Zobaczysz krótkie podsumowanie i szczegółowe informacje o bieżących ustawieniach oraz zalecanych akcjach poprawy. Podsumowanie zawiera bezpośrednie linki do Menedżera zgodności, odpowiedniego rozwiązania w portalu zgodności usługi Microsoft Purview oraz odpowiedniej dokumentacji.

Kliknięcie linku Menedżer zgodności spowoduje przejście do filtrowanego widoku wszystkich akcji poprawy w ramach tego rozwiązania, które nie zostały jeszcze zaimplementowane. W tym miejscu można zobaczyć liczbę punktów, które można osiągnąć, aby zwiększyć [wskaźnik zgodności](compliance-score-calculation.md), a także oceny, do których mają zastosowanie, oraz odpowiednie przepisy i certyfikaty.

W przypadku programu DLP znajduje się przycisk **Skrypt korygowania** , który udostępnia wstępnie wygenerowany skrypt programu PowerShell w oparciu o to, co jest zalecane. Możesz skopiować i wkleić go bezpośrednio w konsoli programu PowerShell. Spowoduje to utworzenie zasad DLP w trybie testowym

#### <a name="items-with-recommendation-status"></a>Elementy ze stanem zalecenia

Wybierz listę rozwijaną obok etykiety **Zalecenie** po prawej stronie akcji poprawy. Zobaczysz podsumowanie bieżącego środowiska Microsoft 365 organizacji związane z akcją poprawy wraz z zalecanymi najlepszymi rozwiązaniami.

## <a name="resources"></a>Zasoby

Aby uzyskać bardziej szczegółowe informacje na temat instalowania, konfigurowania i używania usługi MCCA, zobacz [instrukcje README dotyczące GitHub](https://github.com/OfficeDev/MCCA#overview) (nie jest wymagane żadne konto GitHub).

Aby uzyskać więcej informacji na temat Windows PowerShell, zacznij od [tematu How to use the PowerShell documentation (Jak korzystać z dokumentacji programu PowerShell](/powershell/scripting/how-to-use-docs)). Zobacz również [Uruchamianie Windows PowerShell](/powershell/scripting/windows-powershell/starting-windows-powershell).
