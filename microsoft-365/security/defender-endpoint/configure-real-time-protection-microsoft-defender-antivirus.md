---
title: Włączanie i konfigurowanie Program antywirusowy Microsoft Defender ochrony
description: Włączanie i konfigurowanie Program antywirusowy Microsoft Defender funkcji ochrony w czasie rzeczywistym, takich jak monitorowanie zachowania, heuristics i uczenie maszynowe
keywords: oprogramowanie antywirusowe, ochrona w czasie rzeczywistym, rtp, uczenie maszynowe, monitorowanie zachowania, heuristics
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.date: 10/22/2021
manager: dansimp
ms.custom: nextgen
ms.collection: M365-security-compliance
ms.openlocfilehash: 245aad5498793d951de68e5bf4c3e91510c7d774
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019382"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Włączanie i konfigurowanie Program antywirusowy Microsoft Defender w aplikacji zasady grupy


**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Ochrona zawsze w czasie rzeczywistym składa się z ochrony w czasie rzeczywistym, monitorowania zachowania i heuristics w celu identyfikowania złośliwego oprogramowania na podstawie znanych podejrzanych i złośliwych działań.

Te działania obejmują zdarzenia, takie jak procesy służące do dokonywania nietypowych zmian w istniejących plikach, modyfikowanie lub tworzenie automatycznych kluczy rejestru uruchamiania i lokalizacji uruchamiania (nazywanych również punktami rozszerzalności automatycznego lub edytorami ASEP) oraz innymi zmianami w systemie plików lub strukturze plików.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Włączanie i konfigurowanie zawsze najbędszej ochrony w zasady grupy

Za pomocą **edytora lokalnego zasady grupy włączyć** i skonfigurować Program antywirusowy Microsoft Defender zawsze wł. ustawień ochrony.

Aby włączyć i skonfigurować zawsze włączoną ochronę:

1. Otwórz **Edytor zasady grupy lokalnego** w następujący sposób:

    1. W polu Windows 10 Windows 11 na pasku zadań wpisz **gpedit**.

    2. W **obszarze Najlepsze dopasowanie** wybierz pozycję **Edytuj zasady grupy** , aby **uruchomić Edytor zasady grupy grupy**.
    
       ![GpEdit taskbar search result.](images/gpedit-search.png)

2. W lewym okienku Edytora folderów **zasady grupy rozwiń** drzewo do grupy **Szablony** \>  \> administracyjne konfiguracji komputera i Windows **składniki** \> **Program antywirusowy Microsoft Defender**.

3. Skonfiguruj ustawienie Program antywirusowy Microsoft Defender ochrony przed złośliwym oprogramowaniem.

   W **okienku Program antywirusowy Microsoft Defender** po prawej stronie kliknij dwukrotnie pozycję Zezwalaj usłudze ochrony przed złośliwym oprogramowaniem na uruchomienie z normalnym **priorytetem i ustaw** dla tej usługi wartość **Włączone**.

   Następnie wybierz przycisk **OK**.

4. Skonfiguruj ustawienia Program antywirusowy Microsoft Defender ochrony w czasie rzeczywistym w następujący sposób:

    1. W **okienku Program antywirusowy Microsoft Defender** szczegółów kliknij dwukrotnie pozycję **Ochrona w czasie rzeczywistym**. Lub w **drzewie Program antywirusowy Microsoft Defender** okienku po lewej stronie wybierz pozycję **Ochrona w czasie rzeczywistym**.

    2. W **okienku szczegółów Ochrona** w czasie rzeczywistym po prawej stronie kliknij dwukrotnie ustawienie zasad określone w ustawieniach zasad ochrony w czasie [rzeczywistym (w](#real-time-protection-policy-settings) dalszej części tego artykułu).

    3. Skonfiguruj odpowiednie ustawienie i wybierz przycisk **OK**.

    4. Powtórz poprzednie kroki dla każdego ustawienia w tabeli.

5. Skonfiguruj ustawienie Program antywirusowy Microsoft Defender skanowania w następujący sposób:

    1. W **drzewie Program antywirusowy Microsoft Defender** okienku po lewej stronie wybierz pozycję **Skanuj**.
    
   2. W **okienku** szczegółów Skanowania po prawej stronie kliknij dwukrotnie pozycję **Włącz heuristics** i ustaw dla niego wartość **Włączone**. 

   3. Wybierz przycisk **OK**.

6. Zamknij **Edytor zasady grupy lokalnego**.

### <a name="real-time-protection-policy-settings"></a>Ustawienia zasad ochrony w czasie rzeczywistym

|Ustawienie|Ustawienie domyślne|
|---|---|
|Włączanie monitorowania zachowania <p> Aparat antywirusowy będzie monitorował procesy plików, zmiany w plikach i rejestrach oraz inne zdarzenia w punktach końcowych pod celu wykrycia podejrzanych i znanych złośliwych działań.|Włączone|
|Skanowanie wszystkich pobranych plików i załączników <p> Pobrane pliki i załączniki są automatycznie skanowane. To skanowanie działa oprócz filtru Windows Defender SmartScreen, który skanuje pliki przed i podczas pobierania.|Włączone|
|Monitorowanie aktywności dotyczącej plików i programów na komputerze <p> Aparat Program antywirusowy Microsoft Defender zanotuje wszelkie zmiany w plikach (takie jak przeniesienie, kopie i modyfikacje) oraz ogólne działania w programie (programy, które są otwierane lub uruchomione i które powodują uruchamianie innych programów).|Włączone|
|Włączanie powiadomień o nieprzetworzonej głośności zapisu <p> Informacje o nieprzetworzonej ilości danych będą analizowane za pomocą monitorowania zachowania.|Włączone|
|Włączanie skanowania w czasie rzeczywistym po włączeniu ochrony w czasie rzeczywistym <p> Możesz niezależnie umożliwić aparatowi Program antywirusowy Microsoft Defender skanowanie uruchomionych procesów w poszukiwaniu podejrzanych zmian lub zachowań. Jest to przydatne, jeśli tymczasowo wyłączono ochronę w czasie rzeczywistym i chcesz automatycznie skanować procesy rozpoczęte w trakcie jej wyłączenia.|Włączone|
|Definiowanie maksymalnego rozmiaru pobranych plików i załączników do skanowania <p> Można zdefiniować rozmiar w kilobajtach.|Włączone|
|Konfigurowanie zastępowania ustawień lokalnych w celu włączeń monitorowania zachowania <p> Skonfiguruj zastępowanie lokalne dla konfiguracji monitorowania zachowania. To ustawienie może być ustawiane tylko przez zasady grupy. Włączenie tego ustawienia spowoduje, że ustawienie preferencji lokalnych będzie mieć pierwszeństwo przed zasady grupy. Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia, zasady grupy będą pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie zastępowania ustawień lokalnych w celu skanowania wszystkich pobranych plików i załączników <p> Skonfiguruj lokalne zastępowanie konfiguracji skanowania dla wszystkich pobranych plików i załączników. To ustawienie może być ustawiane tylko przez zasady grupy. Włączenie tego ustawienia spowoduje, że ustawienie preferencji lokalnych będzie mieć pierwszeństwo przed zasady grupy. Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia, zasady grupy będą pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie zastępowania ustawień lokalnych pod celu monitorowania aktywności plików i programów na komputerze <p> Skonfiguruj lokalne zastępowanie konfiguracji monitorowania aktywności plików i programów na komputerze. To ustawienie może być ustawiane tylko przez zasady grupy. Włączenie tego ustawienia spowoduje, że ustawienie preferencji lokalnych będzie mieć pierwszeństwo przed zasady grupy. Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia, zasady grupy będą pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie zastępowania ustawień lokalnych w celu włączoną ochronę w czasie rzeczywistym <p> Skonfiguruj zastępowanie lokalne dla konfiguracji, aby włączyć ochronę w czasie rzeczywistym. To ustawienie może być ustawiane tylko przez zasady grupy. Włączenie tego ustawienia spowoduje, że ustawienie preferencji lokalnych będzie mieć pierwszeństwo przed zasady grupy. Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia, zasady grupy będą pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie zastępowania ustawień lokalnych w celu monitorowania przychodzącej i wychodzącej aktywności plików <p> Skonfiguruj zastępowanie lokalne na poziomie konfiguracji monitorowania aktywności dotyczącej plików przychodzących i wychodzących. To ustawienie może być ustawiane tylko przez zasady grupy. Włączenie tego ustawienia spowoduje, że ustawienie preferencji lokalnych będzie mieć pierwszeństwo przed zasady grupy. Jeśli wyłączysz lub nie skonfigurujesz tego ustawienia, zasady grupy będą pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie monitorowania przychodzącej i wychodzącej aktywności dotyczącej plików i programów <p> Określenie, czy monitorowanie ma być odbierane w przychodzącym, wychodzącym, w obu kierunkach, czy w żaden sposób. Ta akcja jest istotne dla instalacji programu Windows Server, gdy zdefiniowano określone serwery lub role serwera, w których widać duże ilości zmian plików w jednym kierunku i chcesz zwiększyć wydajność sieci. Pełne zaktualizowane punkty końcowe (i serwery) w sieci będą miały niewielki wpływ na wydajność niezależnie od liczby lub kierunku zmian plików.|Włączony (oba wskazówki)|

## <a name="disable-real-time-protection-in-group-policy"></a>Wyłączanie ochrony w czasie rzeczywistym w programie zasady grupy

> [!WARNING]
> Wyłączenie ochrony w czasie rzeczywistym znacząco zmniejsza ochronę punktów końcowych i nie jest zalecane.

Główna funkcja ochrony w czasie rzeczywistym jest domyślnie włączona, ale można ją wyłączyć przy użyciu Edytora lokalnego **zasady grupy danych**.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Aby wyłączyć ochronę w czasie rzeczywistym w zasadach grupy

1. Otwórz **Edytor zasady grupy lokalnym**.

   1. W polu Windows 10 Windows 11 na pasku zadań wpisz **gpedit**.
   2. W **obszarze Najlepsze dopasowanie** wybierz pozycję **Edytuj zasady grupy** , aby **uruchomić Edytor zasady grupy grupy**.

2. W lewym okienku Edytora folderów **zasady grupy rozwiń** \>  \> drzewo do grupy Szablony administracyjne konfiguracji komputera Windows **składniki** \>  \> Program antywirusowy Microsoft Defender **ochronę w czasie rzeczywistym**.

3. W **okienku szczegółów Ochrona w czasie** rzeczywistym po prawej stronie kliknij dwukrotnie pozycję **Wyłącz ochronę w czasie rzeczywistym**.

4. W **oknie ustawienia Wyłącz ochronę w czasie rzeczywistym** ustaw dla tej opcji wartość **Włączone**.
   
5. wybierz przycisk **OK**.

6. Zamknij **Edytor zasady grupy lokalnego**.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ochrony zachowanie, heuristic i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w programie Windows 10](microsoft-defender-antivirus-in-windows-10.md)
