---
title: Wdrażanie Microsoft 365 Lighthouse bazowych
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: W przypadku dostawców usług zarządzanych (MSP) używających Microsoft 365 Lighthouse dowiedz się, jak wdrożyć Microsoft 365 Lighthouse bazowe.
ms.openlocfilehash: 0e19843ee6cfebaf9b37e10929884d0671608451
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504495"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Wdrażanie Microsoft 365 Lighthouse bazowych

Microsoft 365 Lighthouse umożliwia wdrażanie standardowych konfiguracji dzierżaw zarządzanych w celu zabezpieczania użytkowników, urządzeń i danych w dzierżawach klientów. Istnieje siedem [domyślnych konfiguracji planu bazowego](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) standardowo z usługą Lighthouse. Za pomocą funkcji planu wdrażania latarni morskiej możesz wyświetlać, testować i wdrażać konfiguracje zabezpieczeń we wszystkich dzierżawach. Plan wdrażania jest dostępny tylko dla aktywnych dzierżawców. Po dojechania dzierżawy możesz porównać bieżącą konfigurację swoich klientów z domyślną konfiguracją podstawową i podjąć odpowiednie działania.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Upewnij się, że Twoja dzierżawa Twoich klientów spełnia wymagania wymienione w te sposób[: Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="view-a-deployment-plan"></a>Wyświetlanie planu wdrażania

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawcy**.

2. Z listy dzierżaw wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz **kartę Plan wdrażania** .

    Karta Plan wdrażania zawiera listę z możliwość wyszukiwania i eksportu każdego etapu wdrożenia uwzględnionego w planie wdrażania dzierżawy, która zawiera następujące informacje dotyczące poszczególnych kroków wdrażania:

    | Kolumna            | Opis |
    |-----------------|-------------------------------------------------------------------------------------|
    | Krok wdrażania | Opis etapu wdrażania.                                                     |
    | Stan          | Stan kroku wdrażania.                                                  |
    | Plan bazowy        | Plan bazowy, na podstawie którego pochodzi etap wdrożenia.                             |
    | Kategoria        | Czy etap wdrażania jest skojarzony z zarządzaniem urządzeniami, tożsamością lub danymi. |
    | Ostatnia aktualizacja    | Data ostatniej aktualizacji kroku wdrażania.                             |

4. Z listy wybierz krok wdrożenia, który chcesz przejrzeć.

    Na stronie Krok wdrożenia są podane następujące informacje:

    | Kolumna            | Opis |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | Podsumowanie        | Podsumowanie przeznaczenia Kroku wdrażania.                                         |
    | Plan bazowy       | Plan bazowy, na podstawie którego pochodzi etap wdrożenia.                             |
    | Kategoria       | Czy etap wdrażania jest skojarzony z zarządzaniem urządzeniami, tożsamością lub danymi. |
    | Wymagana sku   | Jednostki SKU wymagane do ukończenia kroku wdrażania.                                      |
    | Wpływ na użytkowników    | Wpływ wdrożenia kroku u użytkowników dzierżawy.                             |
    | Dla użytkowników | Linki do zasobów, które mogą być pomocne dla użytkowników dzierżawy.                             |
    | Następne kroki     | Linki i wskazówki dotyczące kolejnych odpowiednich kroków.                                |

    Kroki wdrażania składa się z jednego lub większej liczby procesów, które muszą zostać ukończone, aby spełnić wymagania kroku wdrażania. Strona Krok wdrażania zawiera tabelę procesu, która zawiera listę poszczególnych procesów uwzględnionych w kroku wdrażania i zawiera następujące informacje:

    | Kolumna            | Opis |
    |-------------------|-------------------------------------------------------------|
    | Nazwa procesu      | Nazwa procesu, który, jeśli zostanie zaznaczony, otworzy kartę Proces, która ma zastosowanie.          |
    | Stan            | Stan wykryty tych konfiguracji ustawień uwzględnionych w procesie wdrażania.           |
    | Portal zarządzania | Portal, za pomocą którego są zarządzane ustawienia konfiguracji skojarzone z tym procesem. |

## <a name="deploy-a-deployment-step"></a>Wdrażanie kroku wdrażania

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawcy**.

2. Z listy dzierżaw wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz **kartę Plan wdrażania** .

4. Z listy Krok wdrożenia wybierz krok wdrożenia, który chcesz wdrożyć.

5. Wybierz **pozycję Przejrzyj i wdeksuj**.

6. W **okienku Potwierdzanie** konfiguracji wybierz pozycję **Wdeksuj**.

## <a name="test-a-deployment-step"></a>Testowanie kroku wdrażania

Aby uzyskać informacje o czynnościach wdrażania wdrożonych za pomocą zasad dostępu warunkowego, możesz porównać ustawienia konfiguracji w kroku wdrażania z ustawieniami w istniejących zasadach bez wdrażania ustawień w dzierżawie.

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawcy**.

2. Z listy dzierżaw wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz **kartę Plan wdrażania** .

4. Z listy Krok wdrożenia wybierz krok wdrożenia, który chcesz wdrożyć.

5. Wybierz **pozycję Przejrzyj i wdeksuj**.

6. W **okienku Potwierdzanie** konfiguracji wybierz **pozycję Testuj te ustawienia bez wdrażania**.

7. Wybierz **pozycję Test**.

Okienko Potwierdzanie konfiguracji zostanie zamknięte i wyświetli porównanie zasad. Każda zasada w istniejącej dzierżawie będzie wymieniona w tabeli Wykryte ustawienia.

Tabela Wykryte ustawienia zawiera listę wszystkich istniejących zasad i podsumowuje liczbę ustawień oraz w nawiasach liczbę użytkowników w jednym z następujących stanów:

| Stan         | Opis
|-------------|------------------------------------------------------------|
| Ustawienia równe       | Łączna liczba ustawień konfiguracji w planie wdrażania o równoważnej wartości w dzierżawie.      |
| Brakujące ustawienia     | Łączna liczba ustawień konfiguracji w planie wdrażania, dla których brakuje wartości w dzierżawie.      |
| Ustawienia powodujące konflikt | Łączna liczba ustawień konfiguracji w planie wdrażania, których wartość w dzierżawie jest sprzeczna. |

Wykryte ustawienia można również wyświetlać w modułowej tabeli, która zawiera szczegółowe informacje o ustawieniach konfiguracji dla poszczególnych zasad na poziomie ustawienia i użytkownika, a także sortować według każdego z następujących stanów ustawień:

| Stan         | Opis
|-------------|------------------------------------------------------------|
| Ustawienia sumy       | Łączna liczba ustawień konfiguracji uwzględnionych w procesie wdrażania.                        |
| Ustawienia równe       | Łączna liczba ustawień konfiguracji w planie wdrażania o równoważnej wartości w dzierżawie.      |
| Brakujące ustawienia     | Łączna liczba ustawień konfiguracji w planie wdrażania, dla których brakuje wartości w dzierżawie.      |
| Ustawienia powodujące konflikt | Łączna liczba ustawień konfiguracji w planie wdrażania, których wartość w dzierżawie jest sprzeczna. |
| Dodatkowe ustawienia       | Łączna liczba ustawień konfiguracji z wartością w dzierżawie, ale bez wartości w planie wdrażania.     |

Po zakończeniu tego porównania stan wykryty, stan wdrożenia i stan etapu wdrożenia zostaną automatycznie zaktualizowane przez latarnię morską.

Jeśli nie ma żadnych istniejących zasad do porównania, wybierz pozycję Przejrzyj i wd wdrożono, aby ponownie otworzyć okienko Potwierdzanie konfiguracji, a następnie wybierz pozycję Wdeksuj.

Jeśli istnieją zasady, z którymi należy się porównać, możesz:

- Edytuj ustawienia konfiguracji planu wdrażania i sprawdzaj je ponownie pod względem istniejących zasad, wybierz pozycję  Przejrzyj i wdaj, aby ponownie otworzyć okienko Potwierdzanie konfiguracji, dostosuj odpowiednie ustawienia konfiguracji, ponownie zaznacz pole wyboru i wybierz pozycję **Test** u dołu okienka.

- Edytuj istniejące zasady w ramach odpowiedniego portalu zarządzania, aby uzgadniać różnice przez:
  - Stosowanie brakujących ustawień
  - Edytowanie ustawień konfliktów
  - Usuwanie istniejących zasad

Dla każdego procesu wdrażania, który można zautomatyzować za pośrednictwem latarni morskiej, istnieje zarówno stan wdrożenia, jak i stan wykryty.

- Stan wykryty wskazuje, w jakim zakresie są obecnie wdrożone ustawienia w tym procesie.
- Stan wdrożenia to stan ostatniego wdrożenia u dzierżawy.

Kroki wdrażania można wdrożyć niezależnie od istniejących zasad, ale nie będą uznawane za ukończone, dopóki nie istnieją żadne ustawienia powodujące konflikt. Niepowodzenie rozwiązania tych ustawień powodującego konflikt może mieć wpływ na środowisko użytkownika. 

Wdrożenie kroku wdrażania w wystąpieniach, gdy w dzierżawie istnieją jednakowe ustawienia, z poziomu istniejących zasad spowoduje duplikowanie istniejących ustawień w dzierżawie, ale nie będzie mieć wpływu na środowisko użytkownika. 

Dodatkowe ustawienia są dostępne dla Twojej wiedzy, ale nie wymagają podjęcia działań.

Aby uzyskać więcej informacji na temat zarządzania konfliktami zasad, zobacz Dokumentacja dostępu warunkowego w [usłudze Azure AD](/azure/active-directory/conditional-access/).

## <a name="update-deployment-step-status"></a>Aktualizowanie stanu etapu wdrożenia

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawcy**.

2. Z listy dzierżaw wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz **kartę Plan wdrażania** .

4. Z listy kroków wdrożenia wybierz krok wdrożenia, który chcesz zaktualizować.

5. Z listy **rozwijanej** Adres do wybierz stan akcji.

    | Stan akcji                        | Opis      |
    |---------------------------------------|----------------------------------------|
    | Adres do                        | Domyślny stan wszystkich kroków wdrażania, które NIE obejmują wielu procesów wdrożeniowych.      |
    | Planowane                           | Etap wdrożenia został zaplanowany, ale jeszcze nie został ukończony.                                      |
    | Ryzyko zaakceptowane                     | Użytkownik zaakceptował to ryzyko, które w przeciwnym razie zostałoby odwrócone przez zastosowanie kroku wdrażania. |
    | Rozwiązanie problemu związanego z ryzykiem za pośrednictwem innej firmy | Problem został rozwiązany przez implementację aplikacji lub oprogramowania innej firmy.             |
    | Rozwiązanie za pomocą alternatywnych środków  | Problem został rozwiązany za pomocą alternatywnych środków, takich jak wdrożenie narzędzia wewnętrznego.    |
    | Zastosowana konfiguracja ręczna      | Konfiguracja  zalecana w planie wdrażania została zastosowana ręcznie.                         |

## <a name="share-deployment-step"></a>Udostępnianie kroku wdrażania

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawcy**.

2. Z listy dzierżaw wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz **kartę Plan wdrażania** .

4. Z listy Krok wdrożenia wybierz krok wdrożenia, który chcesz udostępnić.

5. Z **listy rozwijanej** Udostępnij wybierz jedną z następujących opcji.

    | Opcja  | Opis |
    |-----------|-------------------------------------------------------------------------|
    | Kopiuj  | Kopiuje link do kroku wdrażania do Schowka.                                     |
    | Poczta e-mail | Otwiera nową wiadomość e-mail na komputerze lokalnym i wstawia link do kroku wdrażania. |

    Link umożliwia wszystkim osobom z uprawnieniami w organizacji wyświetlanie planu wdrażania dzierżawy.


## <a name="related-content"></a>Zawartość pokrewna

[Omówienie wdrażania standardowych konfiguracji dzierżawy](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) przy użyciu planu bazowego (artykuł)\
[Omówienie Microsoft 365 dzierżaw w latarni morskiej](m365-lighthouse-tenants-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse faq](m365-lighthouse-faq.yml) (artykuł)\
[Konfigurowanie Microsoft 365 Lighthouse zabezpieczeń portalu](m365-lighthouse-configure-portal-security.md) (artykuł) 