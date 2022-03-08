---
title: Krok nr 2. Rozwiązywanie pierwszego zdarzenia
description: Jak rozpocząć rozwiązywanie pierwszego zdarzenia w programie Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2837b6009c143ea724d8c13d2548eeeca80e431d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321323"
---
# <a name="step-2-remediate-your-first-incident"></a>Krok nr 2. Rozwiązywanie pierwszego zdarzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Microsoft 365 Defender oferuje nie tylko możliwości wykrywania i analizowania, ale także zawiera treści i treści złośliwego oprogramowania. Zawieranie zawiera kroki mające na celu ograniczenie wpływu ataków, podczas gdy przestępcy mają pewność, że wszystkie ślady aktywności atakującej zostaną usunięte z sieci. Microsoft 365 Defender oferuje kilka akcji naprawczych, które można skonfigurować w celu [automatycznego](m365d-autoir.md) korygowania w zależności od systemu operacyjnego urządzeń, których dotyczy problem, i typu ataków.

Microsoft 365 Defender udostępnia kilka akcji naprawczych, które analitycy mogą zainicjować ręcznie. Akcje są podzielone na dwie kategorie: Akcje na urządzeniach i akcje dotyczące plików. Niektóre akcje mogą służyć do natychmiastowego zatrzymania zagrożenia, natomiast inne mogą pomóc w dalszej analizie sądowej.

## <a name="actions-on-devices"></a>Akcje na urządzeniach

- **Odizoluj** urządzenie — ta aktywność natychmiast blokuje cały ruch sieciowy (internetowy i wewnętrzny), aby zminimalizować rozpowszechnianie złośliwego oprogramowania i umożliwić analitykom kontynuowanie analizy bez możliwości kontynuowania ataków przez złośliwego podmiotu. Jedyne dozwolone połączenie jest z chmurą usługi Microsoft Defender for Identity, więc usługa Microsoft Defender dla tożsamości może nadal monitorować urządzenie. 
- **Ogranicz uruchamianie aplikacji** — aby ograniczyć uruchamianie aplikacji, są stosowane zasady integralności kodu, które umożliwiają uruchamianie plików tylko wtedy, gdy są podpisane za pomocą certyfikatu wydanego przez firmę Microsoft. Ta metoda ograniczeń może pomóc zapobiec kontrolowaniu przez atakującego naruszonych urządzeń i wykonywaniu dalszych złośliwych działań.
- **Uruchom skanowanie antywirusowe** — skanowanie Program antywirusowy Microsoft Defender może być uruchamiane wraz z innymi rozwiązaniami antywirusowymi, niezależnie od tego, czy program antywirusowy Defender jest aktywnym rozwiązaniem antywirusowym. Jeśli głównym rozwiązaniem ochrony punktu końcowego jest inny produkt dostawcy oprogramowania antywirusowego, możesz uruchomić program antywirusowy Defender w trybie pasywnym.
- **Inicjowanie automatycznego badania** — możesz rozpocząć nowe zautomatyzowane badanie ogólnego przeznaczenia na urządzeniu. Gdy jest uruchomione badanie, wszelkie inne alerty wygenerowane z urządzenia będą dodawane do trwającego automatycznego badania do czasu jego ukończenia. Ponadto, jeśli to samo zagrożenie będzie widoczne na innych urządzeniach, zostaną one dodane do badania.
- **Inicjowanie odpowiedzi** na żywo — funkcja odpowiedzi na żywo umożliwia błyskawiczny dostęp do urządzenia przy użyciu połączenia powłoki zdalnej. Umożliwia to szczegółową pracę w ramach badania i natychmiastowe działanie w celu natychmiastowego reagowania na określone zagrożenia w czasie rzeczywistym. Odpowiedź na żywo ma na celu usprawnianie analiz przez umożliwienie zbierania danych forensycznych, uruchamiania skryptów, wysyłania podejrzanych jednostek do analizy, korygowania zagrożeń oraz aktywnego poszukiwania wyłaniających się zagrożeń.
- **Zbierz pakiet badania** — w ramach procesu badania lub odpowiedzi możesz zebrać pakiet badania z urządzenia. Zbierając pakiet badań, można określić bieżący stan urządzenia oraz lepiej zrozumieć narzędzia i techniki używane przez atakującego. 
- **Skonsultuj** się z ekspertem ds. zagrożeń (dostępnym zarówno w przypadku akcji na urządzeniach, jak i w plikach) — możesz skonsultować się z ekspertem ds. zagrożeń firmy Microsoft, aby uzyskać więcej informacji dotyczących potencjalnie naruszonych urządzeń lub urządzeń, które już zostały naruszone. Eksperci ds. zagrożeń firmy Microsoft mogą być zaangażowani bezpośrednio Microsoft 365 Defender w celu terminowej i dokładnej odpowiedzi. 

## <a name="actions-on-files"></a>Akcje dotyczące plików

- **Zatrzymaj i poddaj** plikowi kwarantanny — ta akcja obejmuje zatrzymywanie uruchomionych procesów, kwartylowanie plików oraz usuwanie trwałych danych, takich jak wszystkie klucze rejestru. Ta akcja  dotyczy urządzeń z systemem Windows 11 lub Windows 10, wersja 1703 lub nowsza, na których plik został obserwowany w ciągu ostatnich 30 dni. 
- **Dodaj wskaźniki, aby zablokować** lub zezwolić na plik — zapobiegaj dalszej propagacji ataków w organizacji, blokując potencjalnie złośliwe pliki lub podejrzewane złośliwe oprogramowanie. Ta operacja zapobiegnie odczytywaniu, zapisywaniu i wykonaniu pliku na urządzeniach w organizacji.
- **Pobierz lub zbierz plik —** ta akcja umożliwia analitykom pobranie pliku w chronionym hasłem pliku .zip do dalszej analizy przez organizację.
- **Analiza głębokości** — ta akcja wykonuje plik w bezpiecznym, w pełni o przyrządowym środowisku w chmurze. Wyniki dogłębnej analizy pokazują działania pliku, obserwowane zachowania i skojarzone artefakty, takie jak porzucone pliki, modyfikacje rejestru i komunikacja z adresami IP. 

Kontynuując przykład w [teście Wykrywanie, ocenianie i](first-incident-analyze.md#analyze-your-first-incident) analizowanie zdarzeń, analityk może rekultywować to zdarzenie za pomocą tych akcji:

1. Natychmiast zresetuj hasło do konta użytkownika
2. Wyizoluj urządzenie w Microsoft 365 Defender aż do zakończenia dogłębnej analizy
3. Upewnij się, że złośliwy plik został poddany kwarantannie z SharePoint
4. Sprawdzanie, na które punkty końcowe wpływało złośliwe oprogramowanie
5. Odbudowywanie systemów
6. Sprawdzanie, czy są podobne alerty programu Microsoft Defender dla aplikacji w chmurze dla innych użytkowników
7. Tworzenie niestandardowego wskaźnika w programie Microsoft Defender dla punktu końcowego w celu zablokowania adresu IP Tor
8. Utwórz akcję zarządzania w usłudze Microsoft Defender dla aplikacji w chmurze dla tego typu alertu, na przykład w przypadku alertów pokazanych na poniższej ilustracji:

   :::image type="content" source="../../media/first-incident-remediate/first-incident-mcas-governance.png" alt-text="Przykład działań dotyczących zarządzania w portalu usługi Microsoft Defender for Cloud Apps.":::

Większość działań naprawczych można stosować i śledzić w Microsoft 365 Defender.

## <a name="using-playbooks"></a>Korzystanie z podręczników

Ponadto przy użyciu podręczników można tworzyć automatyczne działania naprawcze. Obecnie firma Microsoft oferuje szablony [podręczników do GitHub](https://github.com/microsoft/Microsoft-Cloud-App-Security/tree/master/Playbooks), które zapewniają podręczniki dla następujących scenariuszy:

- Usuwanie poufnego udostępniania plików po żądaniu weryfikacji użytkownika
- Alerty dotyczące automatycznych trygorów w kraju, które rzadko się wyzwolą
- Żądanie działania kierownika przed wyłączeniem konta
- Wyłączanie złośliwych reguł skrzynki odbiorczej

Podręczniki używają Power Automate do tworzenia niestandardowych przepływów automatyzacji procesu procesu w celu zautomatyzowania określonych działań po wyzwoleniu określonych kryteriów. Organizacje mogą tworzyć podręczniki na podstawie istniejących szablonów lub od podstaw. 

Oto przykład.
 
:::image type="content" source="../../media/first-incident-remediate/first-incident-power-automate.png" alt-text="Przykład niestandardowego przepływu Power Automate automatyzacji procesu."::: 
 
Podręczniki można również tworzyć podczas przeglądu [po](first-incident-post.md) incydentach w celu tworzenia działań naprawczych na podstawie rozwiązanych zdarzeń. 

## <a name="next-step"></a>Następny krok

[![Krok 3. Dowiedz się, jak przeprowadzić przegląd zdarzenia po zdarzeniu.](../../media/first-incident-overview/first-incident-path-step3.png)](first-incident-post.md)

Dowiedz się, [jak przeprowadzić przegląd po zdarzeniu.](first-incident-post.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
