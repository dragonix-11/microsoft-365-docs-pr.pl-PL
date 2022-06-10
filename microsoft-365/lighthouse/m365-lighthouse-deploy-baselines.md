---
title: Wdrażanie Microsoft 365 Lighthouse punktów odniesienia
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw, kywirpel
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
description: W przypadku dostawców usług zarządzanych korzystających z Microsoft 365 Lighthouse dowiedz się, jak wdrażać Microsoft 365 Lighthouse planach bazowych.
ms.openlocfilehash: 17eda86e80b928fb8b4f56b0e5c719574e4741f5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012599"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Wdrażanie Microsoft 365 Lighthouse punktów odniesienia

Microsoft 365 Lighthouse umożliwia wdrażanie standardowych konfiguracji dzierżawy zarządzanej w celu zabezpieczenia użytkowników, urządzeń i danych w dzierżawach klientów. Istnieje siedem [domyślnych konfiguracji punktu odniesienia](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) , które są standardowo wyposażone w usługę Lighthouse. Za pomocą funkcji planu wdrożenia usługi Lighthouse można wyświetlać, testować i wdrażać konfiguracje zabezpieczeń we wszystkich dzierżawach. Plan wdrożenia jest dostępny tylko dla aktywnych dzierżaw. Po dołączeniu dzierżawy można porównać bieżącą konfigurację klientów z domyślną konfiguracją punktu odniesienia i wykonać odpowiednie akcje.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Upewnij się, że Ty i Twoi dzierżawcy klienta spełniacie wymagania wymienione w [temacie Wymagania dotyczące Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="view-a-deployment-plan"></a>Wyświetlanie planu wdrożenia

1. W okienku nawigacji po lewej stronie w aplikacji Lighthouse wybierz pozycję **Dzierżawy**.

2. Z listy dzierżawy wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz kartę **Plan wdrożenia** .

    Karta Plan wdrożenia zawiera listę możliwych do przeszukiwania i eksportowania każdego kroku wdrożenia, która jest uwzględniona w planie wdrażania dzierżawy, która zawiera następujące informacje dotyczące każdego kroku wdrażania:

    | Kolumna            | Opis |
    |-----------------|-------------------------------------------------------------------------------------|
    | Krok wdrożenia | Opis kroku wdrożenia.                                                     |
    | Stan          | Stan kroku wdrożenia.                                                  |
    | Linii bazowej        | Punkt odniesienia, z którego pochodzi krok wdrożenia.                             |
    | Kategoria        | Czy krok wdrożenia jest skojarzony z zarządzaniem urządzeniami, tożsamością czy danymi. |
    | Ostatnia aktualizacja    | Data ostatniej aktualizacji kroku wdrożenia.                             |

4. Z listy wybierz krok wdrożenia, który chcesz przejrzeć.

    Strona Krok wdrożenia zawiera następujące informacje:

    | Kolumna            | Opis |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | Podsumowanie        | Podsumowanie przeznaczenia kroku wdrożenia.                                         |
    | Linii bazowej       | Punkt odniesienia, z którego pochodzi krok wdrożenia.                             |
    | Kategoria       | Czy krok wdrożenia jest skojarzony z zarządzaniem urządzeniami, tożsamością czy danymi. |
    | Wymagana jednostka SKU   | Jednostki SKU wymagane do ukończenia kroku wdrażania.                                      |
    | Wpływ na użytkownika    | Wpływ wdrożenia kroku dla użytkowników dzierżawy.                             |
    | Dla użytkowników | Linki do zasobów, które mogą okazać się przydatne dla użytkowników dzierżawy.                             |
    | Następne kroki     | Linki i wskazówki dotyczące wszelkich odpowiednich następnych kroków.                                |

    Kroki wdrażania obejmują co najmniej jeden proces, który należy ukończyć. Na stronie Krok wdrożenia znajduje się tabela zawierająca listę poszczególnych procesów uwzględnionych w kroku wdrażania i udostępnia następujące informacje:

    | Kolumna            | Opis |
    |-------------------|-------------------------------------------------------------|
    | Nazwa procesu      | Nazwa procesu, który po wybraniu spowoduje otwarcie odpowiedniej karty Proces.          |
    | Stan            | Wykryto stan tych konfiguracji ustawień uwzględnionych w procesie wdrażania.           |
    | Portal zarządzania | Portal, za pomocą którego zarządzane są ustawienia konfiguracji skojarzone z procesem. |

## <a name="deploy-a-deployment-step"></a>Wdrażanie kroku wdrażania

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawy**.

2. Z listy dzierżawy wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz kartę **Plan wdrożenia** .

4. Z listy Krok wdrożenia wybierz krok wdrożenia, który chcesz wdrożyć.

5. Wybierz pozycję **Przejrzyj i wdróż**.

6. W okienku **Potwierdź konfiguracje** wybierz pozycję **Wdróż**.

## <a name="test-a-deployment-step"></a>Testowanie kroku wdrażania

W przypadku kroków wdrażania wdrożonych za pomocą zasad dostępu warunkowego można porównać ustawienia konfiguracji w kroku wdrażania z ustawieniami w istniejących zasadach bez wdrażania ustawień w dzierżawie.

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawy**.

2. Z listy dzierżawy wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz kartę **Plan wdrożenia** .

4. Z listy Krok wdrożenia wybierz krok wdrożenia, który chcesz wdrożyć.

5. Wybierz pozycję **Przejrzyj i wdróż**.

6. W okienku **Potwierdź konfiguracje** wybierz pozycję **Przetestuj te ustawienia bez wdrożenia**.

7. Wybierz pozycję **Testuj**.

Okienko Potwierdź konfiguracje spowoduje zamknięcie i wyświetlenie porównania zasad. Wszystkie zasady w istniejącej dzierżawie zostaną wyświetlone w tabeli Wykryte ustawienia.

Tabela Wykryte ustawienia zawiera listę wszystkich istniejących zasad i zawiera podsumowanie liczby ustawień oraz w nawiasach liczbę użytkowników w jednym z następujących stanów:

| Stan         | Opis
|-------------|------------------------------------------------------------|
| Równe ustawienia       | Całkowita liczba ustawień konfiguracji w planie wdrożenia z równoważną wartością w dzierżawie.      |
| Brak ustawień     | Całkowita liczba ustawień konfiguracji w planie wdrożenia, w których brakuje wartości w dzierżawie.      |
| Ustawienia powodujące konflikt | Całkowita liczba ustawień konfiguracji w planie wdrożenia, które mają wartość powodującą konflikt w dzierżawie. |

Wykryte ustawienia można również wyświetlić w tabeli modułowej, która zawiera szczegóły ustawień konfiguracji dla poszczególnych zasad na poziomie ustawienia i użytkownika i może być posortowana według każdego z następujących stanów ustawień:

| Stan         | Opis
|-------------|------------------------------------------------------------|
| Ustawienia sumy       | Całkowita liczba ustawień konfiguracji uwzględnionych w procesie wdrażania.                        |
| Równe ustawienia       | Całkowita liczba ustawień konfiguracji w planie wdrożenia z równoważną wartością w dzierżawie.      |
| Brak ustawień     | Całkowita liczba ustawień konfiguracji w planie wdrożenia, w których brakuje wartości w dzierżawie.      |
| Ustawienia powodujące konflikt | Całkowita liczba ustawień konfiguracji w planie wdrożenia, które mają wartość powodującą konflikt w dzierżawie. |
| Dodatkowe ustawienia       | Całkowita liczba ustawień konfiguracji z wartością w dzierżawie, ale bez wartości w planie wdrożenia.     |

Po dokonaniu tego porównania usługa Lighthouse automatycznie zaktualizuje stan Wykryto, Stan wdrożenia i Stan kroku wdrożenia.

Jeśli nie ma istniejących zasad do porównania, wybierz pozycję Przejrzyj i wdróż, aby ponownie otworzyć okienko Potwierdź konfiguracje, a następnie wybierz pozycję Wdróż.

Jeśli istnieją zasady, z którymi należy się porównać, możesz wykonać jedną z następujących czynności:

- Edytuj ustawienia konfiguracji planu wdrożenia i przetestuj je ponownie względem istniejących zasad, wybierz pozycję **Przejrzyj i wdróż** , aby ponownie otworzyć okienko Potwierdź konfiguracje, dostosować żądane ustawienia konfiguracji, ponownie zaznaczyć pole wyboru, a następnie wybierz pozycję **Testuj** w dolnej części okienka.

- Edytuj istniejące zasady w odpowiednim portalu zarządzania, aby uzgodnić różnice między nimi:
  - Stosowanie brakujących ustawień
  - Edytowanie ustawień powodujących konflikt
  - Usuwanie istniejących zasad

Dla każdego procesu wdrażania, który można zautomatyzować za pośrednictwem usługi Lighthouse, występuje zarówno stan wdrożenia, jak i wykryty stan.

- Wykryty stan wskazuje, w jakim stopniu ustawienia w tym procesie są obecnie wdrażane.
- Stan wdrożenia to stan ostatniego wdrożenia w dzierżawie.

Kroki wdrażania można wdrożyć niezależnie od istniejących zasad, ale nie będą uznawane za ukończone, dopóki nie zostaną spełnione żadne ustawienia powodujące konflikt. Nie można rozwiązać tych ustawień powodujących konflikt może mieć wpływ na środowisko użytkownika. 

Wdrożenie kroku wdrożenia w wystąpieniach, gdy w dzierżawie istnieją równe ustawienia z istniejących zasad, spowoduje duplikowanie istniejących ustawień w dzierżawie, ale nie wpłynie na środowisko użytkownika. 

Dodatkowe ustawienia są dostępne dla Twojej świadomości, ale nie wymagają podjęcia działań.

Aby uzyskać więcej informacji na temat zarządzania konfliktami zasad, zobacz [Azure AD dokumentację dostępu warunkowego](/azure/active-directory/conditional-access/).

## <a name="update-deployment-step-status"></a>Stan kroku wdrażania aktualizacji

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawy**.

2. Z listy dzierżawy wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz kartę **Plan wdrożenia** .

4. Z listy kroków wdrażania wybierz krok wdrożenia, który chcesz zaktualizować.

5. Z listy rozwijanej **Adres do** wybierz stan akcji.

    | Stan akcji                        | Opis      |
    |---------------------------------------|----------------------------------------|
    | Adres                        | Domyślny stan wszystkich kroków wdrażania, które NIE obejmują wielu procesów kroków wdrażania.      |
    | Planowane                           | Krok wdrożenia został zaplanowany, ale nie został jeszcze ukończony.                                      |
    | Zaakceptowano ryzyko                     | Użytkownik zaakceptował ryzyko, które w przeciwnym razie zostałoby zażegnane przez zastosowanie kroku wdrożenia. |
    | Ryzyko rozwiązane za pośrednictwem innych firm | Ryzyko zostało rozwiązane przez implementację aplikacji lub oprogramowania innej firmy.             |
    | Rozwiązane za pomocą alternatywnych środków  | Ryzyko zostało rozwiązane za pomocą alternatywnych środków, takich jak implementacja narzędzia wewnętrznego.    |
    | Zastosowana konfiguracja ręczna      | Konfiguracja określona w planie wdrażania została zastosowana ręcznie.                         |

## <a name="share-deployment-step"></a>Krok wdrażania udostępniania

1. Na lewej stronie nawigacji wybierz pozycję **Dzierżawy**.

2. Z listy dzierżawy wybierz dzierżawę, którą chcesz wyświetlić.

3. Wybierz kartę **Plan wdrożenia** .

4. Z listy Krok wdrożenia wybierz krok wdrożenia, który chcesz udostępnić.

5. Z listy rozwijanej **Udostępnij** wybierz jedną z następujących opcji.

    | Opcja  | Opis |
    |-----------|-------------------------------------------------------------------------|
    | Kopii  | Kopiuje link do kroku wdrożenia do schowka.                                     |
    | Poczta e-mail | Otwiera nową wiadomość e-mail na komputerze lokalnym i wstawia link do kroku wdrażania. |

    Link umożliwi wszystkim osobom z uprawnieniami w organizacji wyświetlanie planu wdrożenia dzierżawy.


## <a name="related-content"></a>Zawartość pokrewna

[Omówienie wdrażania standardowych konfiguracji dzierżawy za pomocą Microsoft 365 Lighthouse planów bazowych](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artykuł)\
[Omówienie strony Windows 365 (komputery w chmurze) w Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md) (artykuł)\
[Microsoft 365 Lighthouse często zadawane pytania](m365-lighthouse-faq.yml) (artykuł)\
[Konfigurowanie zabezpieczeń portalu Microsoft 365 Lighthouse](m365-lighthouse-configure-portal-security.md) (artykuł) 