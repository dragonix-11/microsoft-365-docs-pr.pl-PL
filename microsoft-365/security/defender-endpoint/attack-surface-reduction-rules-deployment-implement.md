---
title: Wdrażanie wdrożenia reguł ograniczania powierzchni ataków (ASR, Attack Surface Reduction)
description: Zapewnia wskazówki dotyczące wdrażania reguł ograniczania powierzchni ataków.
keywords: Wdrażanie reguł ograniczania powierzchni ataków, wdrażanie ASR, włączanie reguł asr, konfigurowanie funkcji asr, systemu ochrony przed nieuprawnianiem hosta, reguł ochrony, reguł ochrony przed wykorzystywaniem luk, ochrony przed wykorzystywaniem, regułami wykorzystania luk, regułami zapobiegania powstawaniu przed wirusami, program Microsoft Defender for Endpoint, konfigurowanie reguł asr
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
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 2ca83735eab465e3a5ec6b25156143fde1719c0a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683126"
---
# <a name="step-3-implement-asr-rules"></a>Krok 3. Implementowanie reguł asr

Implementowanie reguł zmniejszania powierzchni ataków (ASR) powoduje przeniesienie pierwszego pierścienia testowego do stanu włączonego i funkcjonalnego.

> [!div class="mx-imgBorder"]
> ![Kroki implementacji reguł ASR](images/asr-rules-implementation-steps.png)

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Krok 1. Przejście reguł asr z inspekcji do bloku

1. Gdy wszystkie wykluczenia zostaną określone w trybie inspekcji, zacznij ustawiać tryb "blokowania" niektórych reguł asr, zaczynając od reguły, która ma najmniej zdarzeń wyzwalanych. Zobacz" [Włączanie reguł ograniczania powierzchni ataków](enable-attack-surface-reduction.md).
2. Przejrzyj stronę raportowania w portalu Microsoft 365 Defender; zobacz Raport [o ochronie przed zagrożeniami w programie Microsoft Defender dla punktu końcowego](threat-protection-reports.md). Przejrzyj też opinie od mistrzów ASR.
3. Uściślij wykluczenia lub utwórz nowe wykluczenia określone jako konieczne.
4. Przełączanie reguł sprawiające problemy z powrotem do kontroli.

  >[!Note]
  >W przypadku problematycznych reguł (czyli reguł tworzących zbyt wiele szumów) lepszym rozwiązaniem jest tworzenie wykluczeń niż wyłączenie reguł lub powrót do inspekcji. Musisz określić, co najlepiej jest dla Twojego środowiska.

  >[!Tip]
  >Jeśli jest to możliwe, skorzystaj z ustawienia trybu ostrzegawczych w zasadach, aby ograniczyć przerwy w pracy. Włączenie reguł asr w trybie ostrzegawczym umożliwia przechwytywanie zdarzeń wyzwalanych i wyświetlanie ich potencjalnych zakłóceń bez blokowania dostępu użytkowników końcowych. Dowiedz się więcej: [Tryb ostrzegania dla użytkowników](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Jak działa tryb ostrzegawcy?

Tryb ostrzegania jest w praktyce instrukcjami blokowania, ale z opcją "Odblokowywanie" kolejnych wykonywania danego przepływu lub aplikacji. Tryb ostrzegawczy jest odblokowywany na urządzeniu, w kombinacji użytkowników, plików i procesów. Informacje o trybie ostrzegania są przechowywane lokalnie i mają czas trwania 24 godzin.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Krok 2. Rozwijanie wdrożenia, aby dzwonić n + 1

Jeśli masz pewność, że reguły asr dla pierścienia 1 zostały poprawnie skonfigurowane, możesz zmienić zakres wdrożenia do następnego pierścienia (zadzwoń n + 1).

Proces wdrażania (kroki 1–3) zasadniczo jest taki sam dla każdego kolejnego pierścienia:

1. Testowanie reguł w inspekcji
2. Przeglądanie zdarzeń inspekcji wyzwalanych przez asr w portalu Microsoft 365 Defender użytkowników
3. Tworzenie wykluczeń
4. Przegląd: uściślij, dodaj lub usuń wykluczenia w razie potrzeby
5. Ustawianie reguł jako "bloku"
6. Przejrzyj stronę raportowania w portalu Microsoft 365 Defender sieci Web.
7. Tworzenie wykluczeń.
8. Wyłącz reguły sprawiające problemy lub przełącz je z powrotem na inspekcję.

#### <a name="customize-attack-surface-reduction-rules"></a>Dostosowywanie reguł zmniejszania powierzchni ataków

W miarę rozszerzania wdrażania reguł ograniczania powierzchni ataków może być konieczne lub korzystne dostosowanie włączonych reguł ograniczania powierzchni ataków.

##### <a name="exclude-files-and-folders"></a>Wyklucz pliki i foldery

Możesz wykluczyć pliki i foldery z oceny przez reguły ograniczania powierzchni ataków. Wykluczony plik nie będzie blokowany, nawet jeśli reguła zmniejszania powierzchni ataków wykryje, że plik zawiera złośliwe zachowanie.

Rozważ na przykład regułę oprogramowania wymuszającego okup:

Reguła oprogramowania wymuszającego okup została zaprojektowana tak, aby ułatwić klientom korporacyjnym zmniejszenie ryzyka związanego z atakami oprogramowania wymuszającego okup przy jednoczesnym zapewnieniu ciągłości działania. Domyślnie błędy reguł oprogramowania wymuszającego okup są zbędne i chronią przed plikami, które jeszcze nie osiągnąć odpowiedniej reputacji i zaufania. W celu ponownego przesuńenia danych reguła oprogramowania wymuszającego okup wyzwala tylko pliki, które nie uzyskały wystarczającej reputacji i pozytywnej reputacji, na podstawie metryk użycia milionów klientów. Zazwyczaj bloki są rozwiązywane samodzielnie, ponieważ wartości "reputacji i zaufania" każdego pliku są stopniowo uaktualniane jako wzrost użycia, które nie są problematyczne.

W przypadkach, gdy bloki nie zostaną rozwiązane w terminie, klienci mogą — na własne _ryzyko — skorzystać_ z funkcji mechanizmu samoobsługi lub funkcji opartego na wskaźniku naruszenia zabezpieczeń (IOC, Indicator of Compromise, allow list) w celu odblokowania samych plików.

> [!WARNING]
> Wykluczenie lub odblokowanie plików lub folderów może potencjalnie umożliwić uruchamianie i zainfekowanie urządzeń niebezpiecznymi plikami. Wykluczenie plików lub folderów może znacznie zmniejszyć ochronę zapewnianą przez reguły zmniejszania obszaru podatnego na ataki. Pliki, które zostałyby zablokowane przez regułę, będą mogły być uruchamiane i nie będą rejestrowane żadne raporty ani zdarzenia.

Wykluczenie dotyczy wszystkich reguł, które zezwalają na wykluczenia. Możesz określić pojedynczy plik, ścieżkę folderu lub w pełni kwalifikowaną nazwę domeny zasobu. Nie można jednak ograniczyć wykluczenia do konkretnej reguły.

Wykluczenie jest stosowane tylko w momencie uruchamiania aplikacji lub usługi wykluczonych. Jeśli na przykład dodasz wykluczenie dla usługi aktualizacji, która jest już uruchomiona, usługa aktualizacji będzie nadal wyzwalać zdarzenia do momentu zatrzymania i ponownego uruchomienia usługi.

Zmniejszenie powierzchni ataków obsługuje zmienne środowiskowe i symbole wieloznaczne. Aby uzyskać informacje na temat używania symboli wieloznacznych, zobacz Używanie symboli wieloznacznych w nazwach plików i ścieżkach folderów [lub na listach wykluczeń rozszerzenia](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).
Jeśli występują problemy z regułami wykrywania plików, które uważasz, że nie powinny być wykrywane, przetestuj regułę w [trybie inspekcji](evaluate-attack-surface-reduction.md).

Aby uzyskać [szczegółowe informacje na temat każdej](attack-surface-reduction-rules-reference.md) reguły, zobacz temat z informacjami na temat reguł ograniczania powierzchni ataków.

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Wykluczanie plików zasady grupy folderów za pomocą funkcji plików

1. Na komputerze zasady grupy zarządzania usługami otwórz konsolę zarządzania usługami [zasady grupy, kliknij](https://technet.microsoft.com/library/cc731212.aspx) prawym przyciskiem myszy zasady grupy obiekt, który chcesz skonfigurować, a następnie wybierz pozycję **Edytuj**.

2. W **administracyjnym zasady grupy zarządzania** przejdź do **strony Konfiguracja komputera i** kliknij pozycję **Szablony administracyjne**.

3. Rozwiń drzewo, **aby Windows składniki Program antywirusowy Microsoft Defender** \>  \> **Microsoft Defender Exploit Guard** \> **zmniejszenie powierzchni ataków**.

4. Kliknij dwukrotnie ustawienie **Wyklucz pliki i ścieżki z zasad** zmniejszania powierzchni ataków i ustaw opcję **Włączone**. Wybierz **pozycję** Pokaż i wprowadź każdy plik lub folder w **kolumnie Nazwa** wartości. Wprowadź **wartość 0** w **kolumnie Wartość** dla każdego elementu.

> [!WARNING]
> Cudzysłowów nie należy używać, ponieważ nie są obsługiwane  w przypadku kolumny Nazwa wartości ani **dla kolumny** Wartość.

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Wykluczanie plików i folderów za pomocą programu PowerShell

1. Wpisz **tekst powershell** w menu Start kliknij prawym **przyciskiem myszy Windows PowerShell** a następnie wybierz **pozycję Uruchom jako administrator**.

2. Wprowadź następujące polecenie cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Nadal używaj dodawania `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` kolejnych folderów do listy.

    > [!IMPORTANT]
    > Użyj, `Add-MpPreference` aby dołączyć aplikacje do listy lub dodać je do listy. Użycie polecenia `Set-MpPreference` cmdlet spowoduje zastąpienie istniejącej listy.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Wykluczanie plików i folderów za pomocą csP usługi MDM

Aby dodać wykluczenia, użyj konfiguracji [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) usługodawca (CSP).

##### <a name="customize-the-notification"></a>Dostosowywanie powiadomienia

Możesz dostosować powiadomienie o tym, kiedy reguła zostanie wyzwolona, i blokuje aplikację lub plik. Zobacz [Zabezpieczenia Windows.](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center)

## <a name="additional-topics-in-this-deployment-collection"></a>Dodatkowe tematy w tym zbiorze wdrożeń

[Wymagania wstępne wdrażania reguł asr](attack-surface-reduction-rules-deployment.md)

[Krok 1. Planowanie wdrożenia reguł ASR](attack-surface-reduction-rules-deployment-plan.md)

[Krok 2. Testowanie reguł asr](attack-surface-reduction-rules-deployment-test.md)

[Krok 4. Operacyjne reguły asr](attack-surface-reduction-rules-deployment-operationalize.md)
