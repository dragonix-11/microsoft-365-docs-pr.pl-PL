---
title: Powiadomienia użytkownika końcowego dotyczące szkolenia symulacyjnego w zakresie ataków
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się, jak tworzyć wiadomości e-mail z powiadomieniami użytkownika końcowego na temat szkolenia symulacyjnego z tematem ataków w programie Microsoft Defender Office 365 plan 2.
ms.technology: mdo
ms.openlocfilehash: 3aa46724ef3414c83a5ece0c5fa17b4f9342c81c
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526666"
---
# <a name="end-user-notifications-for-attack-simulation-training"></a>Powiadomienia użytkownika końcowego dotyczące szkolenia symulacyjnego w zakresie ataków

W szkoleniu symulacyjnych ataków w programie Microsoft 365 E5 lub Microsoft Defender dla programu Office 365 plan 2 powiadomienia użytkowników końcowych to wiadomości e-mail wysyłane do użytkowników Istnieją dwa podstawowe typy powiadomień:

- **Powiadomienia symulowane**: Te wiadomości są wysyłane po zarejestrowaniu użytkowników w szkoleniach i jako przypomnienia o wymaganych szkoleniach.
- **Dodatnie powiadomienia dodatnie**: Te wiadomości są wysyłane, gdy użytkownicy zgłaszają symulowaną wiadomość wyłudzającą informacje.

Aby wyświetlić dostępne powiadomienie dla użytkownika końcowego, otwórz portal <https://security.microsoft.com>Microsoft 365 Defender w witrynie , **a** \>  \> następnie przejdź do karty Szkolenia dotyczące symulacji ataków z & **e-mail** w zakresie współpracy. Aby przejść bezpośrednio do karty **powiadomienia użytkownika końcowego**, użyj klawisza <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>.

Karta **Powiadomienia dla użytkowników końcowych** zawiera dwie karty:

- **Powiadomienia globalne**: zawiera wbudowane powiadomienia, których nie można modyfikować.
- **Powiadomienia dzierżawy**: zawiera niestandardowe powiadomienia utworzone przez Ciebie.

Dla każdego powiadomienia wyświetlane są następujące informacje:

- **Powiadomienia**: nazwa powiadomienia.
- **Język**: Jeśli powiadomienie zawiera wiele tłumaczeń, dwa pierwsze języki są wyświetlane bezpośrednio. Aby wyświetlić pozostałe języki, umieść wskaźnik myszy na ikonie numerycznej (na przykład **+10**).
- **Typ**: Wartość to Powiadomienie **w czasie symulowania lub** **Powiadomienie o dodatnim powiadomieniech w wiadomości e-mail**.
- **Źródło**: W przypadku wbudowanych powiadomień wartość to **Global**. W przypadku powiadomień niestandardowych wartość to **Dzierżawa**.
- **Stan**
- **Połączone symulacje**
- **Utworzone przez**: W przypadku wbudowanych powiadomień wartością jest firma **Microsoft**. W przypadku powiadomień niestandardowych ta wartość to nazwa UPN użytkownika, który utworzył powiadomienie.
- **Godzina utworzenia**
- **Zmodyfikowane przez**
- **Godzina ostatniej modyfikacji**

Aby znaleźć powiadomienie na liście, użyj ikony ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) **Pole** wyszukiwania, aby znaleźć nazwę powiadomienia.

Aby pogrupować powiadomienia według typu, kliknij ikonę ![Grupy.](../../media/m365-cc-sc-group-icon.png) **Grupuj** , a następnie **wybierz pozycję Typ powiadomienia**. Aby rozgrupować powiadomienia, wybierz pozycję **Brak**.

Na karcie **Powiadomienia dzierżawy** kliknij ikonę ![Filtruj.](../../media/m365-cc-sc-filter-icon.png) , aby filtrować powiadomienia według jednego lub kilku języków.

Aby usunąć jedną lub więcej wyświetlanych kolumn, kliknij ikonę ![Dostosuj kolumny.](../../media/m365-cc-sc-customize-icon.png) **Dostosowywanie kolumn**.

Po wybraniu powiadomienia z listy zostanie wyświetlone wysuwne okno szczegółów z następującymi informacjami:

- **Karta** Podgląd: Wyświetlanie komunikat z powiadomieniem. Aby wyświetlić wiadomość w różnych językach, użyj **pola Wybierz** język.
- **Karta** Szczegóły: Wyświetl szczegóły powiadomienia:
  - **Opis powiadomienia**
  - **Źródło**: W przypadku wbudowanych powiadomień wartość to **Global**. W przypadku powiadomień niestandardowych wartość to **Dzierżawa**.
  - **Typ powiadomienia**
  - **Zmodyfikowane przez**
  - **Ostatnia modyfikacja**

## <a name="create-end-user-notifications"></a>Tworzenie powiadomień dla użytkowników końcowych

Na karcie **Powiadomienia o dzierżawie** możesz kliknąć pozycję ![Utwórz nową ikonę.](../../media/m365-cc-sc-create-icon.png) **Utwórz nowy** , aby uruchomić nowego kreatora powiadomień użytkownika końcowego.

1. Na stronie **Definiowanie szczegółów** **skonfiguruj następujące ustawienia:
   - **Wybierz typ powiadomienia**: **Powiadomienie o dodatnim pokłonie lub** **Powiadomienie nasypek** .
   - **Nazwa**: Wprowadź unikatową nazwę.
   - **Opis**. Wprowadź opcjonalny opis.

   Po zakończeniu kliknij przycisk **Dalej**.

2. Na **stronie Definiowanie** zawartości jedynym dostępnym ustawieniem jest przycisk **Dodaj zawartość w języku biznesowym** . Po jego kliknięciu zostanie wyświetlone **wysuwne** menu Dodaj zawartość w języku domyślnym zawierające następujące ustawienia:
   - **Przed nazwą wyświetlaną**
   - **Z adresu e-mail**
   - **Wybierz język wiadomości e-mail**: Wybierz język z listy.
   - **Oznacz ten język jako domyślny**: ponieważ jest to pierwszy i jedyny język powiadomienia, ta wartość jest zaznaczona i nie można jej zmienić.
   - **Temat**: Wartość domyślna to **Dziękujemy za wyłudzy** informacji, ale można go zmienić.
   - **Importowanie wiadomości** e-mail: Możesz opcjonalnie kliknąć ten przycisk, a następnie kliknąć pozycję **Wybierz** plik, aby zaimportować istniejący plik wiadomości w formacie zwykłego tekstu.
   - Obszar zawartości wiadomości e-mail: Dostępne są dwie karty:
     - **Karta** Tekst: Dostępny jest edytor tekstów sformatowanych, który umożliwia utworzenie wiadomości e-mail z powiadomieniem. Oprócz typowych ustawień czcionki i formatowania dostępne są następujące ustawienia:
       - **Tag dynamiczny**: Wybierz z następujących tagów:
         - **Wstawianie imienia**
         - **Wstawianie nazwiska**
         - **Wstawianie upn**
         - **Wstawianie adresu e-mail**
         - **Wstawianie ładu**
     - **Karta** Kod: Możesz bezpośrednio wyświetlać i modyfikować kod HTML.

   Możesz wyświetlić podgląd wyników, klikając przycisk **Podgląd** wiadomości e-mail w górnej części strony.

   Po zakończeniu kliknij przycisk **Zapisz**.

   Powrócisz do strony Definiowanie **zawartości, na** której zostanie podsumowane właśnie utworzone powiadomienie z następującymi informacjami:

   - **Język**
   - **Temat**
   - **Kategoria**
   - **Akcje**: Dostępne są następujące ikony:
     - ![Ikona Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj**
     - ![Ikona Widok.](../../media/m365-cc-sc-view-icon.png) **Widok**
     - ![Ikona Usuń.](../../media/m365-cc-sc-delete-icon.png) **Usuń**: Jeśli powiadomienie jest tylko w wersji językowej, nie można go usunąć.

   Aby dodać wersję powiadomienia w innym języku, kliknij ikonę ![Dodaj tłumaczenie](../../media/m365-cc-sc-create-icon.png). W **wyświetlonym wysuwanych** czacie Dodaj tłumaczenie ustawienia dostępne są w menu wysuwam Dodaj zawartość w języku domyślnym opisanym wcześniej. Jedyna różnica polega na tym, że możesz wybrać **pozycję Oznacz ten język jako domyślny w** dodatkowych tłumaczeniach.

   Po zakończeniu kliknij przycisk **Zapisz.**

   Możesz powtarzać te kroki tyle razy, ile potrzeba, aby utworzyć przetłumaczone wersje powiadomienia w 12 obsługiwanych językach.

   Po zakończeniu kliknij przycisk **Dalej.**

3. Na **stronie Przeglądanie powiadomień** możesz przejrzeć szczegóły powiadomienia.

   Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

   Na stronie **Utworzone powiadomienie z nowej symulacyjnej** funkcji możesz użyć linków do utworzenia nowego powiadomienia, uruchomienia symulacyjnej lub wyświetlenia wszystkich powiadomień.

   Po zakończeniu kliknij pozycję **Gotowe**.

Na karcie **Powiadomienia dzierżawy** znajduje się teraz lista powiadomień, które utworzono.

Po wybraniu powiadomienia dostępne są następujące dodatkowe opcje:

Wracasz do strony powiadomień o  dodatnich wiadomościach, na której właśnie utworzone powiadomienie jest wyświetlane na liście powiadomień Wybierz dodatnią **przechowatą.**

- Aby zmodyfikować powiadomienie lub dodać dodatkowe tłumaczenia, zaznacz to powiadomienie, a następnie kliknij ikonę ![Edytuj.](../../media/m365-cc-sc-edit-icon.png) **Edytuj powiadomienie,** aby uruchomić kreatora powiadomień w sposób opisany wcześniej (gdy większość wartości jest już wypełniona). Jeśli powiadomienie zawiera już tłumaczenia dla 12 obsługiwanych języków, nie możesz dodać więcej tłumaczeń.

- Aby utworzyć kopię powiadomienia, zaznacz ją, a następnie kliknij przycisk ![Ikona Utwórz kopię.](../../media/m365-cc-sc-copy-icon.png).

- Aby usunąć powiadomienie, zaznacz je, a następnie kliknij przycisk ![Ikona Usuń.](../../media/m365-cc-sc-delete-icon.png).

## <a name="related-links"></a>Linki pokrewne

[Wprowadzenie do korzystania ze szkolenia symulacyjnego w zakresie ataków](attack-simulation-training-get-started.md)

[Tworzenie symulacyjnej próby wyłudzania informacji](attack-simulation-training.md)

[Automatyzacje symezyjne dla szkolenia z symezyjną ataków](attack-simulation-training-simulation-automations.md)
