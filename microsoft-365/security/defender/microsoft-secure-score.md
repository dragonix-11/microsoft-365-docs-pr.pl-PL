---
title: Wskaźnik bezpieczeństwa Microsoft
description: Opisuje wskaźnik bezpieczeństwa firmy Microsoft w portalu Microsoft 365 Defender, jak poprawić stan zabezpieczeń i czego mogą oczekiwać administratorzy zabezpieczeń.
keywords: microsoft secure score, secure score, office 365 secure score, microsoft security score, Microsoft 365 Defender portal, improvement actions
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- Adm_TOC
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 33e4ae46c6ec75d615cf64efe93d7b5bd8a77905
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617033"
---
# <a name="microsoft-secure-score"></a>Wskaźnik bezpieczeństwa Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Wskaźnik bezpieczeństwa firmy Microsoft to miara stanu zabezpieczeń organizacji, z większą liczbą wskazującą na więcej podjętych działań ulepszeń. Można go znaleźć w https://security.microsoft.com/securescore [portalu Microsoft 365 Defender](microsoft-365-defender-portal.md).

Zgodnie z zaleceniami dotyczącymi wskaźnika bezpieczeństwa organizacja może chronić organizację przed zagrożeniami. Ze scentralizowanego pulpitu nawigacyjnego w portalu Microsoft 365 Defender organizacje mogą monitorować zabezpieczenia swoich tożsamości, aplikacji i urządzeń platformy Microsoft 365 oraz pracować nad nimi.

Wskaźnik bezpieczeństwa pomaga organizacjom:  

* Raport dotyczący bieżącego stanu stanu zabezpieczeń organizacji.
* Zwiększ ich stan bezpieczeństwa, zapewniając możliwość odnajdywania, widoczność, wskazówki i kontrolę.  
* Porównaj z testami porównawczymi i ustal kluczowe wskaźniki wydajności (KPI).

Obejrzyj to wideo, aby zapoznać się z szybkim omówieniem wskaźnika bezpieczeństwa.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWUPrP]

Organizacje uzyskują dostęp do niezawodnych wizualizacji metryk i trendów, integracji z innymi produktami firmy Microsoft, porównywania wyników z podobnymi organizacjami i wielu innych. Wynik może również odzwierciedlać, kiedy rozwiązania innych firm rozwiązały zalecane akcje.

:::image type="content" source="../../media/secure-score/secure-score-home-page.png" alt-text="Strona główna Bezpieczna ocena firmy Microsoft w portalu Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-home-page.png":::

## <a name="how-it-works"></a>Jak to działa

Otrzymujesz punkty dla następujących akcji:

- Konfigurowanie zalecanych funkcji zabezpieczeń
- Wykonywanie zadań związanych z zabezpieczeniami
- Rozwiązywanie problemów z działaniem ulepszeń za pomocą aplikacji lub oprogramowania innej firmy lub alternatywnym środkiem zaradczym

Niektóre akcje poprawy dają punkty tylko po pełnym ukończeniu. Niektóre dają częściowe punkty, jeśli zostały ukończone dla niektórych urządzeń lub użytkowników. Jeśli nie możesz lub nie chcesz wprowadzać jednej z akcji poprawy, możesz zaakceptować ryzyko lub pozostałe ryzyko.

Jeśli masz licencję na jeden z obsługiwanych produktów firmy Microsoft, zobaczysz zalecenia dotyczące tych produktów. Przedstawiamy pełny zestaw możliwych ulepszeń dla produktu, niezależnie od wersji licencji, subskrypcji lub planu. W ten sposób można zrozumieć najlepsze rozwiązania w zakresie zabezpieczeń i poprawić swój wynik. Twoja bezwzględna postawa zabezpieczeń reprezentowana przez wskaźnik bezpieczeństwa pozostaje taka sama niezależnie od licencji posiadanych przez organizację dla określonego produktu. Należy pamiętać, że zabezpieczenia powinny być zrównoważone z użytecznością, a nie każde zalecenie może działać w danym środowisku.

Wynik jest aktualizowany w czasie rzeczywistym w celu odzwierciedlenia informacji przedstawionych na stronach akcji wizualizacji i ulepszeń. Wskaźnik bezpieczeństwa synchronizuje się również codziennie, aby odbierać dane systemowe o uzyskanych punktach dla każdej akcji.

### <a name="key-scenarios"></a>Kluczowe scenariusze

- [Sprawdzanie bieżącego wyniku](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Porównaj swój wynik z organizacjami takimi jak Twoja](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Wyświetlanie akcji ulepszania i podejmowanie decyzji o planie działania](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Inicjowanie przepływów pracy w celu zbadania lub zaimplementowania](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>Jak są oceniane akcje poprawy

Każda akcja poprawy jest warta 10 punktów lub mniej, a większość z nich jest oceniana w sposób binarny. Jeśli zaimplementujesz akcję poprawy, taką jak tworzenie nowych zasad lub włączanie określonego ustawienia, otrzymasz 100% punktów. W przypadku innych akcji poprawy punkty są podawane jako procent całkowitej konfiguracji.

Na przykład akcja poprawy wskazuje, że uzyskujesz 10 punktów, chroniąc wszystkich użytkowników za pomocą uwierzytelniania wieloskładnikowego. Masz tylko 50 z 100 użytkowników chronionych, więc otrzymasz częściowy wynik 5 punktów (50 chronionych / 100 łącznie * 10 max pts = 5 pkt).

### <a name="products-included-in-secure-score"></a>Produkty uwzględnione w wskaźniku bezpieczeństwa

Obecnie istnieją zalecenia dotyczące następujących produktów:

- Microsoft 365 (w tym Exchange Online)
- Azure Active Directory
- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft Defender for Identity
- Defender for Cloud Apps
- Microsoft Teams

Zalecenia dotyczące innych produktów zabezpieczających pojawią się wkrótce. Zalecenia nie obejmują wszystkich obszarów ataków skojarzonych z każdym produktem, ale są dobrym punktem odniesienia. Możesz również oznaczyć akcje poprawy jako objęte przez inną firmę lub alternatywne środki zaradcze.

### <a name="security-defaults"></a>Ustawienia domyślne zabezpieczeń

Wskaźnik bezpieczeństwa firmy Microsoft zaktualizował akcje poprawy w celu obsługi [domyślnych zabezpieczeń w usłudze Azure Active Directory](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), co ułatwia ochronę organizacji przy użyciu wstępnie skonfigurowanych ustawień zabezpieczeń typowych ataków.

Jeśli włączysz wartości domyślne zabezpieczeń, otrzymasz pełne punkty za następujące akcje poprawy:

- Upewnij się, że wszyscy użytkownicy mogą przeprowadzić uwierzytelnianie wieloskładnikowe w celu zapewnienia bezpiecznego dostępu (9 punktów)
- Wymagaj uwierzytelniania wieloskładnikowego dla ról administracyjnych (10 punktów)
- Włączanie zasad w celu blokowania starszego uwierzytelniania (7 punktów)

>[!IMPORTANT]
>Wartości domyślne zabezpieczeń obejmują funkcje zabezpieczeń, które zapewniają podobne zabezpieczenia do akcji poprawy "zasad ryzyka logowania" i "zasad ryzyka użytkownika". Zamiast konfigurować te zasady w oparciu o wartości domyślne zabezpieczeń, zalecamy zaktualizowanie ich stanu do wartości "Rozwiązano za pomocą alternatywnego ograniczenia ryzyka".

## <a name="required-permissions"></a>Wymagane uprawnienia

Aby mieć uprawnienia dostępu do usługi Microsoft Secure Score, musisz mieć przypisaną jedną z następujących ról w usłudze Azure Active Directory.

### <a name="read-and-write-roles"></a>Role odczytu i zapisu

Dzięki dostępowi do odczytu i zapisu można wprowadzać zmiany i bezpośrednio wchodzić w interakcje z bezpiecznym wynikiem. Dostęp tylko do odczytu można również przypisać innym użytkownikom.

* Administrator globalny
* Administrator zabezpieczeń
* Administrator programu Exchange
* Administrator usługi SharePoint

### <a name="read-only-roles"></a>Role tylko do odczytu

Dzięki dostępowi tylko do odczytu nie można edytować stanu ani notatek w celu wykonania akcji poprawy, edytowania stref wyników ani edytowania porównań niestandardowych.

* Administrator pomocy technicznej
* Administrator użytkowników
* Administrator pomocy technicznej usługi
* Czytelnik zabezpieczeń
* Operator zabezpieczeń
* Czytelnik globalny

## <a name="risk-awareness"></a>Świadomość ryzyka

Wskaźnik bezpieczeństwa firmy Microsoft to numeryczne podsumowanie stanu zabezpieczeń na podstawie konfiguracji systemu, zachowania użytkownika i innych pomiarów związanych z zabezpieczeniami. Nie jest to bezwzględna miara prawdopodobieństwo naruszenia systemu lub danych. Oznacza to raczej zakres, w jakim wdrożono mechanizmy kontroli zabezpieczeń w środowisku firmy Microsoft, co może pomóc zrównoważyć ryzyko naruszenia zabezpieczeń. Żadna usługa online nie jest odporna na naruszenia bezpieczeństwa, a wskaźnik bezpieczeństwa nie powinien być interpretowany jako gwarancja naruszenia bezpieczeństwa w żaden sposób.

## <a name="we-want-to-hear-from-you"></a>Chcemy usłyszeć od Ciebie

Jeśli masz jakiekolwiek problemy, daj nam znać, publikując wpis w społeczności [zabezpieczeń, ochrony prywatności & zgodności](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Monitorujemy społeczność i zapewniamy pomoc.

## <a name="related-resources"></a>Powiązane zasoby

- [Ocenianie postawy dotyczącej zabezpieczeń](microsoft-secure-score-improvement-actions.md)
- [Śledzenie historii bezpiecznego wyniku firmy Microsoft i osiąganie celów](microsoft-secure-score-history-metrics-trends.md)
- [Nadchodzące nowości](microsoft-secure-score-whats-coming.md)
- [Co nowego](microsoft-secure-score-whats-new.md)
