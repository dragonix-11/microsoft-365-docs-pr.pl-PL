---
title: Włączanie i konfigurowanie funkcji ochrony Program antywirusowy Microsoft Defender
description: Włączanie i konfigurowanie Program antywirusowy Microsoft Defender funkcji ochrony w czasie rzeczywistym, takich jak monitorowanie zachowań, heurystyka i uczenie maszynowe
keywords: oprogramowanie antywirusowe, ochrona w czasie rzeczywistym, rtp, uczenie maszynowe, monitorowanie zachowań, heurystyka
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
ms.openlocfilehash: 744aaa887bfbfafd29b9e3bedb8dc49791b43137
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790179"
---
# <a name="enable-and-configure-microsoft-defender-antivirus-always-on-protection-in-group-policy"></a>Włącz i skonfiguruj zawsze aktywną ochronę programu antywirusowego Microsoft Defender w zasadach grupy

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

Zawsze włączona ochrona składa się z ochrony w czasie rzeczywistym, monitorowania zachowań i heurystyki w celu identyfikowania złośliwego oprogramowania na podstawie znanych podejrzanych i złośliwych działań.

Działania te obejmują zdarzenia, takie jak procesy wprowadzające nietypowe zmiany w istniejących plikach, modyfikowanie lub tworzenie automatycznych kluczy rejestru uruchamiania i lokalizacji uruchamiania (znanych również jako punkty rozszerzalności automatycznego startu lub aseps) oraz inne zmiany w systemie plików lub strukturze plików.

## <a name="enable-and-configure-always-on-protection-in-group-policy"></a>Włączanie i konfigurowanie zawsze włączonej ochrony w zasady grupy

Za pomocą **lokalnego edytora zasady grupy** można włączyć i skonfigurować Program antywirusowy Microsoft Defender zawsze włączonych ustawień ochrony.

Aby włączyć i skonfigurować zawsze włączoną ochronę:

1. Otwórz **lokalny edytor zasady grupy** w następujący sposób:

    1. W polu wyszukiwania Windows 10 lub Windows 11 paska zadań wpisz **gpedit**.

    2. W obszarze **Najlepsze dopasowanie** wybierz pozycję **Edytuj zasady grupy**, aby uruchomić **lokalny edytor zasady grupy**.
    
       :::image type="content" source="images/gpedit-search.png" alt-text="Wynik wyszukiwania paska zadań GPEdit w panelu sterowania" lightbox="images/gpedit-search.png":::

2. W okienku po lewej stronie **edytora zasady grupy lokalnego** rozwiń drzewo do pozycji **Szablony** \> administracyjne **konfiguracji** \> komputera **Windows Składniki** \> **Program antywirusowy Microsoft Defender**.

3. Skonfiguruj ustawienie zasad usługi ochrony przed złośliwym kodem Program antywirusowy Microsoft Defender.

   W okienku **szczegółów Program antywirusowy Microsoft Defender** po prawej stronie kliknij dwukrotnie pozycję **Zezwalaj na uruchamianie usługi ochrony przed złośliwym kodem z normalnym priorytetem** i ustaw ją na **wartość Włączone**.

   Następnie wybierz przycisk **OK**.

4. Skonfiguruj Program antywirusowy Microsoft Defender ustawienia zasad ochrony w czasie rzeczywistym w następujący sposób:

    1. W okienku **szczegółów Program antywirusowy Microsoft Defender** kliknij dwukrotnie pozycję **Ochrona w czasie rzeczywistym**. Lub w drzewie **Program antywirusowy Microsoft Defender** w okienku po lewej stronie wybierz pozycję **Ochrona w czasie rzeczywistym**.

    2. W okienku Szczegóły **ochrony w czasie rzeczywistym** po prawej stronie kliknij dwukrotnie ustawienie zasad określone w [ustawieniach zasad ochrony w czasie rzeczywistym](#real-time-protection-policy-settings) (w dalszej części tego artykułu).

    3. Skonfiguruj odpowiednie ustawienie i wybierz przycisk **OK**.

    4. Powtórz poprzednie kroki dla każdego ustawienia w tabeli.

5. Skonfiguruj ustawienie zasad skanowania Program antywirusowy Microsoft Defender w następujący sposób:

    1. W drzewie **Program antywirusowy Microsoft Defender** w okienku po lewej stronie wybierz pozycję **Skanuj**.
    
   2. W okienku **Szczegóły skanowania** po prawej stronie kliknij dwukrotnie pozycję **Włącz heurystyczne** i ustaw ją na **wartość Włączone**. 

   3. Wybierz przycisk **OK**.

6. Zamknij **lokalny edytor zasady grupy**.

### <a name="real-time-protection-policy-settings"></a>Ustawienia zasad ochrony w czasie rzeczywistym

|Ustawienie|Ustawienie domyślne|
|---|---|
|Włączanie monitorowania zachowania <p> Aparat antywirusowy będzie monitorować procesy plików, zmiany plików i rejestru oraz inne zdarzenia w punktach końcowych pod kątem podejrzanych i znanych złośliwych działań.|Włączone|
|Skanuj wszystkie pobrane pliki i załączniki <p> Pobrane pliki i załączniki są automatycznie skanowane. To skanowanie działa oprócz filtru Windows Defender SmartScreen, który skanuje pliki przed i podczas pobierania.|Włączone|
|Monitorowanie aktywności plików i programów na komputerze <p> Aparat Program antywirusowy Microsoft Defender zwraca uwagę na wszelkie zmiany plików (zapisy plików, takie jak przenoszenie, kopie lub modyfikacje) oraz ogólne działania programu (programy, które są otwierane lub uruchomione i które powodują uruchamianie innych programów).|Włączone|
|Włączanie nieprzetworzonych powiadomień zapisu woluminu <p> Informacje o nieprzetworzonych zapisach woluminów zostaną przeanalizowane przez monitorowanie zachowania.|Włączone|
|Włączanie skanowania procesów za każdym razem, gdy włączono ochronę w czasie rzeczywistym <p> Możesz niezależnie włączyć aparat Program antywirusowy Microsoft Defender w celu skanowania uruchomionych procesów pod kątem podejrzanych modyfikacji lub zachowań. Jest to przydatne, jeśli tymczasowo wyłączono ochronę w czasie rzeczywistym i chcesz automatycznie skanować procesy, które rozpoczęły się, gdy zostały wyłączone.|Włączone|
|Definiowanie maksymalnego rozmiaru pobranych plików i załączników do skanowania <p> Rozmiar można zdefiniować w kilobajtach.|Włączone|
|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby włączania monitorowania zachowania <p> Skonfiguruj lokalne przesłonięcia dla konfiguracji monitorowania zachowania. To ustawienie można ustawić tylko przez zasady grupy. Jeśli to ustawienie zostanie włączone, lokalne ustawienie preferencji będzie mieć pierwszeństwo przed zasady grupy. Jeśli to ustawienie zostanie wyłączone lub nie zostanie skonfigurowane, zasady grupy będzie mieć pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby skanowania wszystkich pobranych plików i załączników <p> Skonfiguruj lokalne zastąpienie konfiguracji skanowania wszystkich pobranych plików i załączników. To ustawienie można ustawić tylko przez zasady grupy. Jeśli to ustawienie zostanie włączone, lokalne ustawienie preferencji będzie mieć pierwszeństwo przed zasady grupy. Jeśli to ustawienie zostanie wyłączone lub nie zostanie skonfigurowane, zasady grupy będzie mieć pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie zastąpienia ustawień lokalnych na potrzeby monitorowania działania plików i programów na komputerze <p> Skonfiguruj lokalne zastąpienie konfiguracji monitorowania działania plików i programów na komputerze. To ustawienie można ustawić tylko przez zasady grupy. Jeśli to ustawienie zostanie włączone, lokalne ustawienie preferencji będzie mieć pierwszeństwo przed zasady grupy. Jeśli to ustawienie zostanie wyłączone lub nie zostanie skonfigurowane, zasady grupy będzie mieć pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie przesłonięcia ustawień lokalnych w celu włączenia ochrony w czasie rzeczywistym <p> Skonfiguruj lokalne przesłonięcia dla konfiguracji, aby włączyć ochronę w czasie rzeczywistym. To ustawienie można ustawić tylko przez zasady grupy. Jeśli to ustawienie zostanie włączone, lokalne ustawienie preferencji będzie mieć pierwszeństwo przed zasady grupy. Jeśli to ustawienie zostanie wyłączone lub nie zostanie skonfigurowane, zasady grupy będzie mieć pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie przesłonięcia ustawień lokalnych na potrzeby monitorowania aktywności plików przychodzących i wychodzących <p> Skonfiguruj lokalne przesłonięcia dla konfiguracji monitorowania dla przychodzącego i wychodzącego działania plików. To ustawienie można ustawić tylko przez zasady grupy. Jeśli to ustawienie zostanie włączone, lokalne ustawienie preferencji będzie mieć pierwszeństwo przed zasady grupy. Jeśli to ustawienie zostanie wyłączone lub nie zostanie skonfigurowane, zasady grupy będzie mieć pierwszeństwo przed ustawieniem preferencji lokalnych.|Włączone|
|Konfigurowanie monitorowania dla działań przychodzących i wychodzących plików i programów <p> Określ, czy monitorowanie powinno odbywać się w kierunku przychodzącym, wychodzącym, obu lub żadnym z tych kierunków. Ta akcja jest istotna w przypadku instalacji serwera Windows, w których zdefiniowano określone serwery lub role serwera, które widzą duże ilości zmian plików tylko w jednym kierunku i chcesz zwiększyć wydajność sieci. W pełni zaktualizowane punkty końcowe (i serwery) w sieci będą miały niewielki wpływ na wydajność niezależnie od liczby lub kierunku zmian plików.|Włączone (w obu kierunkach)|

## <a name="disable-real-time-protection-in-group-policy"></a>Wyłączanie ochrony w czasie rzeczywistym w zasady grupy

> [!WARNING]
> Wyłączenie ochrony w czasie rzeczywistym znacząco zmniejsza ochronę punktów końcowych i nie jest zalecane.

Główna funkcja ochrony w czasie rzeczywistym jest domyślnie włączona, ale można ją wyłączyć przy użyciu **lokalnego edytora zasady grupy**.

### <a name="to-disable-real-time-protection-in-group-policy"></a>Aby wyłączyć ochronę w czasie rzeczywistym w zasadach grupy

1. Otwórz **edytor zasady grupy lokalnych**.

   1. W polu wyszukiwania Windows 10 lub Windows 11 paska zadań wpisz **gpedit**.
   2. W obszarze **Najlepsze dopasowanie** wybierz pozycję **Edytuj zasady grupy**, aby uruchomić **lokalny edytor zasady grupy**.

2. W okienku po lewej stronie **edytora zasady grupy lokalnego** rozwiń drzewo do pozycji **Konfiguracja** \> komputera **Szablony** \> administracyjne **Windows Składniki** \> **Program antywirusowy Microsoft Defender** \> **Ochrona w czasie rzeczywistym**.

3. W okienku Szczegóły **ochrony w czasie rzeczywistym** po prawej stronie kliknij dwukrotnie pozycję **Wyłącz ochronę w czasie rzeczywistym**.

4. W oknie **Wyłączanie ustawienia ochrony w czasie rzeczywistym** ustaw opcję **Włączone**.
   
5. wybierz przycisk **OK**.

6. Zamknij **lokalny edytor zasady grupy**.

> [!TIP]
> Jeśli szukasz informacji związanych z programem antywirusowym dla innych platform, zobacz:
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla Program antywirusowy Microsoft Defender dla Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustawianie preferencji dla Ochrona punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfigurowanie usługi Defender dla punktu końcowego w funkcjach systemu Android](android-configure.md)
> - [Konfigurowanie Ochrona punktu końcowego w usłudze Microsoft Defender funkcji systemu iOS](ios-configure-features.md)

## <a name="see-also"></a>Zobacz też

- [Konfiguruj ochronę behawioralną, heurystyczną i w czasie rzeczywistym](configure-protection-features-microsoft-defender-antivirus.md)
- [Program antywirusowy Microsoft Defender w Windows 10](microsoft-defender-antivirus-in-windows-10.md)
