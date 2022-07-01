---
title: Włącz reguły zmniejszania obszaru podatnego na ataki
description: Zawiera wskazówki dotyczące wdrażania reguł zmniejszania obszaru ataków.
keywords: Wdrażanie reguł zmniejszania obszaru ataków, wdrażanie usługi ASR, włączanie reguł asr, konfigurowanie usługi ASR, system zapobiegania włamaniom do hostów, reguły ochrony, reguły ochrony przed lukami w zabezpieczeniach, reguły antyeksploatowania, reguły wykorzystujące luki w zabezpieczeniach, reguły zapobiegania zakażeniom, Ochrona punktu końcowego w usłudze Microsoft Defender, konfigurowanie reguł usługi ASR
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: c3c693a46c3c22749a4e8ff2d572cef56bc06d9b
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603753"
---
# <a name="enable-attack-surface-reduction-asr-rules"></a>Włącz reguły zmniejszania obszaru podatnego na ataki

Implementowanie reguł zmniejszania obszaru ataków (ASR) powoduje przeniesienie pierwszego pierścienia testowego w włączony stan funkcjonalny.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-implementation-steps.png" alt-text="Procedura implementowania reguł usługi ASR" lightbox="images/asr-rules-implementation-steps.png":::
  

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Krok 1. Przenoszenie reguł usługi ASR z inspekcji do bloku

1. Po określeniu wszystkich wykluczeń w trybie inspekcji rozpocznij ustawianie niektórych reguł usługi ASR na tryb "blokuj", zaczynając od reguły, która ma najmniejszą liczba wyzwalanych zdarzeń. Zobacz" [Włączanie reguł zmniejszania obszaru podatnego na ataki](enable-attack-surface-reduction.md).
2. Przejrzyj stronę raportowania w portalu Microsoft 365 Defender. Zobacz [Raport dotyczący ochrony przed zagrożeniami w Ochrona punktu końcowego w usłudze Microsoft Defender](threat-protection-reports.md). Przejrzyj również opinie mistrzów usługi ASR.
3. Uściślij wykluczenia lub utwórz nowe wykluczenia zgodnie z potrzebami.
4. Przełącz problematyczne reguły z powrotem na inspekcję.

  >[!Note]
  >W przypadku problematycznych reguł (reguł tworzących zbyt dużo szumu) lepiej jest tworzyć wykluczenia niż wyłączać reguły lub przełączać się z powrotem na inspekcję. Musisz określić, co jest najlepsze dla Twojego środowiska.

  >[!Tip]
  >Jeśli jest dostępna, skorzystaj z ustawienia Tryb ostrzeżenia w regułach, aby ograniczyć zakłócenia. Włączenie reguł usługi ASR w trybie ostrzeżenia umożliwia przechwytywanie wyzwalanych zdarzeń i wyświetlanie ich potencjalnych zakłóceń bez faktycznego blokowania dostępu użytkowników końcowych. Dowiedz się więcej: [Tryb ostrzegania dla użytkowników](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Jak działa tryb ostrzeżenia?

Tryb ostrzeżenia jest faktycznie instrukcją bloku, ale z opcją "Odblokuj" kolejne wykonania danego przepływu lub aplikacji. Tryb ostrzeżenia odblokowuje na poszczególnych urządzeniach, użytkownikach, plikach i kombinacjach procesów. Informacje o trybie ostrzegania są przechowywane lokalnie i mają czas trwania 24 godzin.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Krok 2. Rozwiń wdrożenie, aby utworzyć pierścień n + 1

Jeśli masz pewność, że poprawnie skonfigurowano reguły asr dla pierścienia 1, możesz poszerzyć zakres wdrożenia do następnego pierścienia (pierścień n + 1).

Proces wdrażania, kroki 1–3, jest zasadniczo taki sam dla każdego kolejnego pierścienia:

1. Reguły testów w obszarze Inspekcja
2. Przejrzyj zdarzenia inspekcji wyzwalane przez usługę ASR w portalu Microsoft 365 Defender
3. Tworzenie wykluczeń
4. Przegląd: uściślaj, dodaj lub usuń wykluczenia w razie potrzeby
5. Ustaw reguły na "blokuj"
6. Przejrzyj stronę raportowania w portalu Microsoft 365 Defender.
7. Tworzenie wykluczeń.
8. Wyłącz problematyczne reguły lub przełącz je z powrotem na inspekcję.

#### <a name="customize-attack-surface-reduction-rules"></a>Dostosowywanie reguł zmniejszania obszaru ataków

W miarę rozszerzania wdrożenia reguł zmniejszania obszaru ataków może okazać się konieczne lub korzystne dostosowanie włączonych reguł zmniejszania obszaru ataków.

##### <a name="exclude-files-and-folders"></a>Wykluczanie plików i folderów

Można wykluczyć pliki i foldery z oceny przez reguły zmniejszania obszaru ataków. Jeśli plik zostanie wykluczony, nie zostanie zablokowany, nawet jeśli reguła zmniejszania obszaru ataków wykryje, że plik zawiera złośliwe zachowanie.

Rozważmy na przykład regułę wymuszania okupu:

Reguła wymuszania okupu ma na celu pomoc klientom korporacyjnym w zmniejszeniu ryzyka ataków wymuszających okup przy jednoczesnym zapewnieniu ciągłości działania. Domyślnie błędy reguły wymuszania okupu po stronie ostrożności i ochrony przed plikami, które nie osiągnęły jeszcze wystarczającej reputacji i zaufania. Aby ponownie zaimponować, reguła wymuszania okupu wyzwala tylko pliki, które nie zyskały wystarczającej pozytywnej reputacji i rozpowszechnienia na podstawie metryk użycia milionów naszych klientów. Zazwyczaj bloki są rozwiązywane samodzielnie, ponieważ wartości "reputacji i zaufania" poszczególnych plików są przyrostowo uaktualniane w miarę wzrostu użycia bez problemów.

W przypadkach, w których bloki nie są rozwiązywane samodzielnie w odpowiednim czasie, klienci mogą - _na własne ryzyko_ - korzystać z mechanizmu samoobsługowego lub funkcji "listy dozwolonych" opartej na wskaźniku kompromisu (MKOl) w celu odblokowania samych plików.

> [!WARNING]
> Wykluczenie lub odblokowanie plików lub folderów może potencjalnie umożliwić uruchamianie niebezpiecznych plików i infekowanie urządzeń. Wykluczenie plików lub folderów może znacznie zmniejszyć ochronę zapewnianą przez reguły zmniejszania obszaru podatnego na ataki. Pliki, które zostałyby zablokowane przez regułę, będą mogły być uruchamiane i nie będą rejestrowane żadne raporty ani zdarzenia.

Wykluczenie dotyczy wszystkich reguł, które zezwalają na wykluczenia. Możesz określić pojedynczy plik, ścieżkę folderu lub w pełni kwalifikowaną nazwę domeny zasobu. Nie można jednak ograniczyć wykluczenia do określonej reguły.

Wykluczenie jest stosowane tylko wtedy, gdy zostanie uruchomiona wykluczona aplikacja lub usługa. Jeśli na przykład dodasz wykluczenie dla usługi aktualizacji, która jest już uruchomiona, usługa aktualizacji będzie nadal wyzwalać zdarzenia, dopóki usługa nie zostanie zatrzymana i ponownie uruchomiona.

Redukcja obszaru ataków obsługuje zmienne środowiskowe i symbole wieloznaczne. Aby uzyskać informacje na temat korzystania z symboli wieloznacznych, zobacz [używanie symboli wieloznacznych na liście wykluczeń nazwy pliku i folderu lub rozszerzenia](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).
Jeśli występują problemy z regułami wykrywania plików, które uważasz, że nie powinny zostać wykryte, [użyj trybu inspekcji, aby przetestować regułę](evaluate-attack-surface-reduction.md).

Aby uzyskać szczegółowe informacje na temat każdej reguły, zobacz temat [dotyczący reguł zmniejszania obszaru ataków](attack-surface-reduction-rules-reference.md) .

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Używanie zasady grupy do wykluczania plików i folderów

1. Na komputerze zarządzania zasady grupy otwórz [konsolę zarządzania zasady grupy](https://technet.microsoft.com/library/cc731212.aspx), kliknij prawym przyciskiem myszy obiekt zasady grupy, który chcesz skonfigurować, i wybierz pozycję **Edytuj**.

2. W **edytorze zarządzania zasady grupy** przejdź do pozycji **Konfiguracja komputera** i kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo do **składników** \> systemu Windows **Program antywirusowy** \> **Microsoft Defender Microsoft Defender Exploit Guard** \> **— redukcja obszaru ataków**.

4. Kliknij dwukrotnie ustawienie **Wyklucz pliki i ścieżki z reguł zmniejszania obszaru ataków** i ustaw opcję **Włączone**. Wybierz pozycję **Pokaż** i wprowadź każdy plik lub folder w kolumnie **Nazwa wartości** . Wprowadź **wartość 0** w kolumnie **Wartość** dla każdego elementu.

> [!WARNING]
> Nie używaj cudzysłowów, ponieważ nie są one obsługiwane w kolumnie **Nazwa wartości** ani w kolumnie **Wartość** .

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Wykluczanie plików i folderów przy użyciu programu PowerShell

1. Wpisz **program PowerShell** w menu Start, kliknij prawym przyciskiem myszy **Windows PowerShell** i wybierz pozycję **Uruchom jako administrator**.

2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Nadal używaj polecenia `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` , aby dodać więcej folderów do listy.

    > [!IMPORTANT]
    > Służy `Add-MpPreference` do dołączania lub dodawania aplikacji do listy. `Set-MpPreference` Użycie polecenia cmdlet spowoduje zastąpienie istniejącej listy.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Używanie dostawców CSP mdm do wykluczania plików i folderów

Aby dodać wykluczenia, użyj dostawcy usługi konfiguracji [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) .

##### <a name="customize-the-notification"></a>Dostosuj powiadomienie

Powiadomienie można dostosować w przypadku wyzwolenia reguły i zablokowania aplikacji lub pliku. Zobacz [artykuł Zabezpieczenia Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center).

## <a name="additional-topics-in-this-deployment-collection"></a>Dodatkowe tematy w tej kolekcji wdrożeń

[Omówienie wdrażania reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment.md)

[Zaplanuj wdrażanie reguł zmniejszania powierzchni podatnej na ataki (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Przetestuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-test.md)

[Operacjonalizuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-deployment-operationalize.md)

[Odwołuj reguły zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md)
