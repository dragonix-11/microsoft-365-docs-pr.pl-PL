---
title: Niechciane oprogramowanie
ms.reviewer: ''
description: Dowiedz się, jak niechciane oprogramowanie zmienia domyślne ustawienia bez twojej zgody i co możesz zrobić, aby się chronić.
keywords: security, malware, protection, unwanted, software, alter, infect, unwanted software, software bundlers, browser modifiers, privacy, security, computing experience, prevent infection, solution, WDSI, MMPC, Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem , zagrożenia badań wirusów, złośliwe oprogramowanie badawcze, ochrona komputera, infekcja komputera, zakażenie wirusem, opisy, korygowanie, najnowsze zagrożenia
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 654730571de934552d983e1135f24a3299567741
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666685"
---
# <a name="unwanted-software"></a>Niechciane oprogramowanie

Niechciane oprogramowanie to programy, które zmieniają środowisko Windows bez twojej zgody lub kontroli. Może to mieć postać zmodyfikowanego środowiska przeglądania, braku kontroli nad pobieraniem i instalacją, wprowadzających w błąd komunikatów lub nieautoryzowanych zmian w ustawieniach Windows.

## <a name="how-unwanted-software-works"></a>Jak działa niechciane oprogramowanie

Niechciane oprogramowanie można wprowadzić, gdy użytkownik wyszukuje i pobiera aplikacje z Internetu. Niektóre aplikacje to pakiety oprogramowania, co oznacza, że są one pakowane w inne aplikacje. W związku z tym inne programy mogą zostać przypadkowo zainstalowane po pobraniu oryginalnej aplikacji.

Oto kilka wskazówek dotyczących niechcianego oprogramowania:

- Istnieją programy, których nie zainstalowano i które mogą być trudne do odinstalowania

- Funkcje lub ustawienia przeglądarki zostały zmienione i nie można ich wyświetlać ani modyfikować

- Występują nadmierne komunikaty o kondycji urządzenia lub o plikach i programach

- Istnieją reklamy, których nie można łatwo zamknąć

Niektóre wskaźniki są trudniejsze do rozpoznania, ponieważ są mniej destrukcyjne, ale nadal są niechciane. Na przykład niechciane oprogramowanie może modyfikować strony internetowe w celu wyświetlania określonych reklam, monitorowania działań przeglądania lub usuwania kontroli nad przeglądarką.

Firma Microsoft używa obszernych [kryteriów oceny](criteria.md) do identyfikowania niechcianego oprogramowania.

## <a name="how-to-protect-against-unwanted-software"></a>Jak chronić przed niepożądanym oprogramowaniem

Aby zapobiec niepożądanej infekcji oprogramowania, pobierz oprogramowanie tylko z oficjalnych witryn internetowych lub z Microsoft Store. Uważaj na pobieranie oprogramowania z witryn innych firm.

Używaj [Microsoft Edge](/microsoft-edge/deploy/index) podczas przeglądania Internetu. Microsoft Edge obejmuje dodatkowe zabezpieczenia, które skutecznie blokują modyfikatory przeglądarki, które mogą zmieniać ustawienia przeglądarki. Microsoft Edge blokuje również znane witryny internetowe hostujące niechciane oprogramowanie przy użyciu [Windows Defender SmartScreen](/microsoft-edge/deploy/index) (używanego również przez program Internet Explorer).

Włącz [Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-in-windows-10) w Windows 10. Zapewnia ona ochronę w czasie rzeczywistym przed zagrożeniami oraz wykrywa i usuwa znane niechciane oprogramowanie.

Pobierz [program Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201) na potrzeby ochrony w czasie rzeczywistym w Windows 7 lub Windows Vista.

Aby uzyskać bardziej ogólne porady, zobacz [Zapobieganie infekcji złośliwym oprogramowaniem](prevent-malware-infection.md).

### <a name="what-should-i-do-if-my-device-is-infected"></a>Co należy zrobić, jeśli moje urządzenie jest zainfekowane? 

Jeśli podejrzewasz, że masz niechciane oprogramowanie, możesz [przesłać pliki do analizy](https://www.microsoft.com/wdsi/filesubmission).

Niektóre niechciane oprogramowanie dodaje wpisy dezinstalacji, co oznacza, że można **je usunąć przy użyciu Ustawienia**.
1. Wybierz przycisk Start
2. Przejdź do **obszaru Ustawienia > Aplikacje > Aplikacje & funkcje**.
3. Wybierz aplikację, którą chcesz odinstalować, a następnie kliknij pozycję **Odinstaluj**.

Jeśli ostatnio zauważono objawy niechcianego oprogramowania, rozważ posortowanie aplikacji według daty instalacji, a następnie odinstaluj najnowsze aplikacje, które nie zostały zainstalowane.

Może być również konieczne **usunięcie dodatków przeglądarki** w przeglądarkach, takich jak Internet Explorer, Firefox lub Chrome.

W przypadku niepowodzenia usuwania zagrożeń przeczytaj o [rozwiązywaniu problemów z wykrywaniem i usuwaniem złośliwego oprogramowania](https://support.microsoft.com/help/4466982/windows-10-troubleshoot-problems-with-detecting-and-removing-malware).