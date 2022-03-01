---
title: Microsoft Secure Score
description: W tym artykule opisano pozycję Microsoft Secure Score Microsoft 365 Defender portalu sieciowego, jak ulepszyć zabezpieczenia oraz czego mogą oczekiwać administratorzy zabezpieczeń.
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
ms.openlocfilehash: d31fa35ddf84b63a115cf3128673794617fcc730
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014853"
---
# <a name="microsoft-secure-score"></a>Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Secure Score to miara stanu zabezpieczeń organizacji. Wyższa liczba oznacza więcej działań usprawnień. Można go znaleźć w https://security.microsoft.com/securescore portalu [Microsoft 365 Defender.](microsoft-365-defender.md#the-microsoft-365-defender-portal)

Zgodnie z zaleceniami w zakresie bezpiecznego wyniku można chronić organizację przed zagrożeniami. Za pomocą scentralizowanego pulpitu nawigacyjnego w portalu Microsoft 365 Defender organizacje mogą monitorować zabezpieczenia swoich Microsoft 365, aplikacji i urządzeń oraz pracować nad tym.

Bezpieczny wynik pomaga organizacjom:  

* Raportuje bieżący stan stanu stanu zabezpieczeń organizacji.
* Poprawiaj ich bezpieczeństwo dzięki możliwości odnajdowania, widoczności, wskazówek i kontroli.  
* Porównaj dane z punktami odniesienia i ustal kluczowe wskaźniki wydajności (KPI).

Obejrzyj ten klip wideo, aby szybko oomówić wynik bezpiecznego.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWUPrP]

Organizacje uzyskują dostęp do niezawodnych wizualizacji metryk i trendów, integracji z innymi produktami firmy Microsoft, porównywania wyników z podobnymi organizacjami i wielu innych. Wynik może także odzwierciedlać, kiedy rozwiązania innych firm zajęły się zalecanymi działaniami.

![Strona główna Secure Score.](../../media/secure-score/secure-score-home-page.png)

## <a name="how-it-works"></a>Jak to działa

Masz punkty za następujące działania:

- Konfigurowanie zalecanych funkcji zabezpieczeń
- Wykonywanie zadań związanych z zabezpieczeniami
- Adresowanie działania udoskonalania za pomocą aplikacji lub oprogramowania innej firmy albo alternatywnego zaradczego wpływu

Niektóre działania udoskonalania dają punkty tylko w przypadku ich pełnego ukończenia. Niektórzy mogą dać częściowe punkty, jeśli zostały ukończone dla niektórych urządzeń lub użytkowników. Jeśli nie możesz lub nie chcesz, aby szedł do działania udoskonalania, możesz zaakceptować to ryzyko lub je zaakceptować.

Jeśli masz licencję na jeden z obsługiwanych produktów firmy Microsoft, zobaczysz zalecenia dotyczące tych produktów. Pokazujemy pełny zestaw możliwych ulepszeń produktu, niezależnie od wersji licencji, subskrypcji lub planu. Dzięki temu można zrozumieć najlepsze rozwiązania dotyczące zabezpieczeń i poprawić swoje wyniki. Bezwzględna postawa zabezpieczeń, reprezentowana przez ocenę bezpiecznego, pozostaje bez względu na licencje posiadane przez Twoją organizację dla określonego produktu. Należy pamiętać, że zabezpieczenia powinny być zrównoważone pod względami użyteczności i nie wszystkie zalecenia mogą działać w Twoim środowisku.

Twój wynik jest aktualizowany w czasie rzeczywistym, aby odzwierciedlał informacje prezentowane w wizualizacjach i na stronach działań udoskonalania. Secure Score jest również codziennie synchronizowane w celu odbierania danych systemowych o osiąganych punktach za poszczególne działania.

### <a name="key-scenarios"></a>Kluczowe scenariusze

- [Sprawdzanie bieżącego wyniku](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Porównywanie wyników z organizacjami, które polubiły Twój wynik](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Wyświetlanie działań udoskonalania i decydowanie o planie działania](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Inicjowanie przepływów pracy w celu zbadania lub wdrożenia](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>Jak są poprawiane działania

Każde działanie udoskonalania jest warte co najmniej 10 punktów i większość jest poprawiana w postaci binarnej. Jeśli wdrożysz działanie udoskonalania, takie jak utworzenie nowych zasad lub włączenie określonego ustawienia, otrzymasz 100% punktów. W przypadku innych działań udoskonalania punkty są podawane jako procent całkowitej konfiguracji.

Na przykład w ramach akcji udoskonalania otrzymasz 10 punktów, chroniąc wszystkich użytkowników za pomocą uwierzytelniania wieloskładnikowego. Masz tylko 50 z 100 chronionych użytkowników, dlatego zyskasz częściowy wynik: 5 punktów (50 chronionych / 100 łącznie * 10 maksymalnych punktów = 5 pkt).

### <a name="products-included-in-secure-score"></a>Produkty uwzględnione w bezpiecznym wyniku

Obecnie dostępne są zalecenia dotyczące następujących produktów:

- Microsoft 365 (w tym Exchange Online)
- Azure Active Directory
- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft Defender for Identity
- Defender for Cloud Apps
- Microsoft Teams

Rekomendacje dla innych produktów zabezpieczających zostaną wkrótce wkrótce dostępne. Zalecenia nie obejmują wszystkich powierzchni ataków skojarzonych z każdym produktem, ale są dobrym planem bazowym. Możesz również oznaczyć działania udoskonalania jako objęte przez stronę trzecią lub alternatywny środki zaradcze.

### <a name="security-defaults"></a>Domyślne ustawienia zabezpieczeń

Witryna Microsoft Secure Score zaktualizowała działania ulepszeń w celu obsługi ustawień domyślnych zabezpieczeń w programie [Azure Active Directory](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), co ułatwia ochronę organizacji za pomocą wstępnie skonfigurowanych ustawień zabezpieczeń na rzecz typowych ataków.

Jeśli włączysz ustawienia domyślne zabezpieczeń, otrzymasz pełne punkty za następujące działania udoskonalania:

- Zapewnianie wszystkim użytkownikom uwierzytelniania wieloskładnikowego w celu zapewnienia bezpiecznego dostępu (9 punktów)
- Wymaganie uwierzytelniania wieloskładnikowego dla ról administracyjnych (10 punktów)
- Włączanie zasad w celu blokowania starszego uwierzytelniania (7 punktów)

>[!IMPORTANT]
>Wartości domyślne zabezpieczeń obejmują funkcje zabezpieczeń, które zapewniają zabezpieczenia podobne do działań udoskonalania "zasad ryzyka logowania" i "zasad ryzyka użytkownika". Zamiast konfigurowania tych zasad zamiast wartości domyślnych zabezpieczeń, zalecamy zaktualizowanie ich stanów do "Rozwiązano przez alternatywne środki zaradcze".

## <a name="required-permissions"></a>Wymagane uprawnienia

Aby mieć uprawnienia dostępu do programu Microsoft Secure Score, musisz mieć przypisaną jedną z następujących ról w programie Azure Active Directory.

### <a name="read-and-write-roles"></a>Role czytania i pisania

Dzięki dostępowi do odczytu i zapisu możesz wprowadzać zmiany i bezpośrednio korzystać z bezpiecznego wyniku. Innym użytkownikom możesz też przypisać dostęp tylko do odczytu.

* Administrator globalny
* Administrator zabezpieczeń
* Administrator programu Exchange
* Administrator usługi SharePoint

### <a name="read-only-roles"></a>Role tylko do odczytu

Dzięki dostępowi tylko do odczytu nie możesz edytować stanu ani notatek w celu działania ulepszeń, edytować stref wyników ani edytować niestandardowych porównań.

* Administrator pomocy technicznej
* Administrator użytkowników
* Administrator pomocy technicznej usługi
* Czytelnik zabezpieczeń
* Operator zabezpieczeń
* Czytelnik globalny

## <a name="risk-awareness"></a>Świadomość ryzyka

Microsoft Secure Score to numeryczne podsumowanie informacji dotyczących zabezpieczeń na podstawie konfiguracji systemu, zachowania użytkownika i innych miar związanych z zabezpieczeniami. Nie jest to bezwzględne miara tego, czy system lub dane zostaną naruszone. Odzwierciedla natomiast zakres przyjętej kontroli zabezpieczeń w środowisku firmy Microsoft, który może pomóc zrównoważyć ryzyko naruszenia zabezpieczeń. Usługi online nie są w związku z naruszeniem bezpieczeństwa, a bezpieczny wynik nie powinien być w jakikolwiek sposób interpretowany jako gwarancję ochrony przed naruszeniem zabezpieczeń.

## <a name="we-want-to-hear-from-you"></a>Chcemy usłyszeć Od Ciebie

Jeśli masz problemy, po daj nam o tym znać, publikując wpis w społeczności dotyczącej zabezpieczeń [, prywatności & zgodności](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Monitorujemy społeczność i udzielamy pomocy.

## <a name="related-resources"></a>Zasoby pokrewne

- [Ocenianie postawy dotyczącej zabezpieczeń](microsoft-secure-score-improvement-actions.md)
- [Śledzenie historii bezpiecznego wyniku firmy Microsoft i spełnienie celów](microsoft-secure-score-history-metrics-trends.md)
- [Co będzie wkrótce](microsoft-secure-score-whats-coming.md)
- [Co nowego](microsoft-secure-score-whats-new.md)
