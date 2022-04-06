---
title: Niechciane oprogramowanie
ms.reviewer: ''
description: Dowiedz się, jak niechciane oprogramowanie zmienia ustawienia domyślne bez Twojej zgody i co możesz zrobić, aby się ochronić.
keywords: zabezpieczenia, złośliwe oprogramowanie, ochrona, niechciane, oprogramowanie, zmiana, zainfekowanie, niechciane oprogramowanie, pakiety oprogramowania, modyfikujące przeglądarki, prywatność, zabezpieczenia, środowisko obliczeniowe, zapobieganie zainfekowaniu, rozwiązaniu, WDSI, MMPC, Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem , zagrożenia związane z badaniami wirusów, złośliwe oprogramowanie, ochrona komputera, zainfekowanie komputera, zainfekowanie komputera, opisy, działania naprawcze, najnowsze zagrożenia
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
ms.openlocfilehash: 94b3bad5b5653420d91cd422d40a0ff7802e6442
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63706200"
---
# <a name="unwanted-software"></a>Niechciane oprogramowanie

Niechciane oprogramowanie to programy, które Windows zmiany bez Twojej zgody lub kontroli. Może to mieć postać zmodyfikowanego przeglądania, braku kontroli nad pobieraniem i instalowaniem, wprowadzających w błąd wiadomości lub nieautoryzowanych zmian ustawień Windows pobierania.

## <a name="how-unwanted-software-works"></a>Jak działa niechciane oprogramowanie

Niechciane oprogramowanie może zostać wprowadzone, gdy użytkownik wyszuka i pobierze aplikacje z Internetu. Niektóre aplikacje są pakietami oprogramowania, co oznacza, że są one spakowane z innymi aplikacjami. W wyniku tego inne programy mogą zostać przypadkowo zainstalowane po pobraniu oryginalnej aplikacji.

Poniżej podano pewne oznaczenia dotyczące niechcianego oprogramowania:

- Istnieją programy, które nie zostały zainstalowane i ich odinstalowanie może być trudne

- Funkcje lub ustawienia przeglądarki zostały zmienione i nie można ich wyświetlać ani modyfikować

- Za nadmiarowe wiadomości na temat kondycji urządzenia lub plików i programów

- Istnieją reklamy, których nie można łatwo zamknąć

Niektóre wskaźniki są trudniejsze do rozpoznania, ponieważ są mniej zakłócające, ale nadal są niechciane. Na przykład niechciane oprogramowanie może zmodyfikować strony internetowe, aby wyświetlać określone reklamy, monitorować aktywność przeglądania lub usunąć kontrolę nad przeglądarką.

Firma Microsoft używa [rozbudowanych kryteriów oceny do](criteria.md) identyfikowania niechcianego oprogramowania.

## <a name="how-to-protect-against-unwanted-software"></a>Jak chronić przed niechcianym oprogramowaniem

Aby zapobiec niechcianym powstawaniu oprogramowania, pobierz oprogramowanie tylko z oficjalnych witryn internetowych lub ze Microsoft Store. Nie należy pobierać oprogramowania z witryn innych firm.

Używaj [Microsoft Edge](/microsoft-edge/deploy/index) podczas przeglądania Internetu. Microsoft Edge dodatkowe zabezpieczenia, które w praktyce blokują modyfikatory przeglądarki, które mogą zmienić ustawienia przeglądarki. Microsoft Edge także blokuje znane witryny internetowe hostowanie niechcianego oprogramowania przy użyciu filtru [SmartScreen](/microsoft-edge/deploy/index) Windows Defender (używanego również w programie Internet Explorer).

Włącz [Program antywirusowy Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-in-windows-10) w Windows 10. Zapewnia on ochronę w czasie rzeczywistym przed zagrożeniami oraz wykrywa i usuwa znane niechciane oprogramowanie.

Pobierz [program Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201) do ochrony w czasie rzeczywistym w programie Windows 7 lub Windows Vista.

Aby uzyskać więcej ogólnych porad, zobacz Zapobieganie [zainfekowaniu złośliwym oprogramowaniem](prevent-malware-infection.md).

### <a name="what-should-i-do-if-my-device-is-infected"></a>Co zrobić, jeśli urządzenie zostało zainfekowane? 

Jeśli podejrzewasz, że masz niechciane oprogramowanie, możesz [przesłać pliki do analizy](https://www.microsoft.com/wdsi/filesubmission).

Niektóre niechciane oprogramowanie dodaje wpisy dezinstalacji, co oznacza, że można je usunąć **przy** użyciu Ustawienia.
1. Wybierz przycisk Start
2. Przejdź do **Ustawienia > Aplikacje > aplikacje & funkcje**.
3. Wybierz aplikację, którą chcesz odinstalować, a następnie kliknij pozycję **Odinstaluj**.

Jeśli tylko ostatnio zauważono symptomy niepożądanej rośliny związanej z oprogramowaniem, rozważ sortowanie aplikacji według daty instalacji, a następnie odinstaluj najnowsze aplikacje, które nie zostały zainstalowane.

Może być również konieczne usunięcie z przeglądarek dodatków **przeglądarki** , takich jak Internet Explorer, Firefox lub Chrome.

Jeśli usuwanie zagrożeń nie powiedzie się, przeczytaj o [rozwiązywaniu problemów z wykrywaniem złośliwego oprogramowania i ich usuwaniem](https://support.microsoft.com/help/4466982/windows-10-troubleshoot-problems-with-detecting-and-removing-malware).