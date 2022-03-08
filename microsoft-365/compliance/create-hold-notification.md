---
title: Tworzenie informacji prawnych o wstrzymaniu ich od zesłania
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Za pomocą narzędzia do komunikacji w przypadku Advanced eDiscovery przypadku wysyłaj, zbieraj i śledź powiadomienia o obsłudze prawnych.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 5c0bda35ffe2547e1c30b4bbf0a6c7d0d0563b7b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315665"
---
# <a name="create-a-legal-hold-notice"></a>Tworzenie informacji prawnych o wstrzymaniu ich od zesłania

Przy Advanced eDiscovery informacji o użytkownikach organizacje mogą zarządzać swoim przepływem pracy, komunikując się z nimi. Za pośrednictwem narzędzia do komunikacji zespoły prawne mogą systemowo wysyłać, zbierać i śledzić powiadomienia o holdie prawnej. Elastyczny proces tworzenia umożliwia również zespołom dostosowywanie przepływu pracy powiadomień o wstrzymaniu i zawartości w powiadomieniach wysyłanych do osób przechwytczy.

![Strona komunikacji.](../media/CommunicationPage.PNG)

W tym artykule przedstawiono kroki przepływu pracy z powiadomieniem o wstrzymaniu.

## <a name="step-1-specify-communication-details"></a>Krok 1. Określanie szczegółów komunikacji

Pierwszym krokiem jest określenie odpowiednich danych do informacji prawnych i innych informacji o wstrzymaniu się od nich.

![Name Communication page.](../media/NameCommunication.PNG)

1. W Centrum zgodności platformy Microsoft 365 przejdź do tematu **Zbierania elektronicznych** materiałów dowodowych > Zaawansowane, aby wyświetlić listę spraw w organizacji.

2. Wybierz sprawę, kliknij **kartę Komunikacja** , a następnie kliknij pozycję **Nowa komunikacja**.

3. Na stronie **Nazwa komunikacji** określ następujące ustawienia komunikacji.

    - **Nazwa**: jest to nazwa komunikacji.

    - **Issuing officer**: Na liście rozwijanej są wyświetlani użytkownicy w Twojej organizacji, których można wybrać jako inspektora ds. wydania komunikacji. Każda komunikacja wysyłana do osób, które je zatrzymały, zostanie wysłana w imieniu wybranego inspektora wydania. Lista użytkowników na liście rozwijanej składa się z członków sprawy oraz członków służb wydających w całej organizacji. Ci inscytatorzy zbierania elektronicznych materiałów dowodowych są dodawana przez administratora zbierania elektronicznych materiałów dowodowych i są dostępni we wszystkich Advanced eDiscovery przypadkach w Twojej organizacji. Aby uzyskać więcej informacji, zobacz [Zarządzanie organami wydającym informacje](advanced-ediscovery-issuing-officers.md).

    - **Wybierz szablon komunikacji**: Na liście rozwijanej są wyświetlane szablony z biblioteki komunikacji na Advanced eDiscovery ustawień. Jeśli wybierzesz szablon, będzie on wyświetlany w witrynie Definiowanie  zawartości portalu jako punkt wyjścia dla tekstu powiadomienia, które tworzysz. Jeśli nie wybierzesz szablonu, musisz utworzyć powiadomienie samodzielnie od podstaw. Aby uzyskać więcej informacji na temat szablonów komunikacji, zobacz [Zarządzanie szablonami do komunikacji z użytkownikami](advanced-ediscovery-communications-library.md).

4. Kliknij **Dalej**.

## <a name="step-2-define-the-portal-content"></a>Krok 2. Definiowanie zawartości portalu

Następnie możesz utworzyć i dodać zawartość powiadomienia o wstrzymaniu. Na stronie **Definiowanie zawartości portalu** w kreatorze **tworzenia** komunikacji określ zawartość powiadomienia o wstrzymaniu. Ta zawartość zostanie automatycznie dołączona do zasad wydawania, ponownego wydawania, przypomnienia i eskalacji. Ponadto ta zawartość będzie wyświetlana w Portalu zgodności użytkownika- opiekuna. Jeśli wybrano szablon z biblioteki Komunikacji, będzie on wyświetlany i stanowi punkt wyjścia dla powiadomienia, które tworzysz.

![Strona Zawartość portalu.](../media/PortalContent.PNG)

Aby utworzyć zawartość portalu:

1. Wpisz (lub wytnij i wklej z innego dokumentu) powiadomienie o wstrzymaniu w polu tekstowym zawartości portalu. Jeśli na poprzedniej stronie kreatora wybrano szablon komunikacji, ten szablon jest wyświetlany. W razie potrzeby możesz edytować zawartość szablonu.

2. Wstaw zmienne korespondencji seryjnej do powiadomienia, aby dostosować powiadomienie i udostępnić Portal zgodności wt.

3. Kliknij **Dalej**.

  > [!TIP]
  > Aby dowiedzieć się więcej o dostosowywaniu zawartości i formatowania zawartości portalu, zobacz [Korzystanie z Edytora komunikacji](using-communications-editor.md).

## <a name="step-3-set-the-required-notifications"></a>Krok 3. Ustawianie wymaganych powiadomień

Po skonfigurowaniu zawartości powiadomienia o wstrzymaniu możesz skonfigurować przepływy pracy wokół wysyłania i zarządzania procesem powiadomień. Powiadomienia to wiadomości e-mail, które są wysyłane w celu powiadamiania i obserwowania osób, które odimówią. Każdy pochwała dodana do komunikacji otrzyma to samo powiadomienie.

Aby skonfigurować i wysłać powiadomienie o wstrzymaniu, należy dołączyć powiadomienia o wydaniu, wydaniu, ponownym wydaniu i wydaniu.

### <a name="issuance-notification"></a>Powiadomienie o wydaniu

Po utworzeniu komunikacji powiadomienie o **wydaniu** jest inicjowane przez określonego inspektora ds. wydania. Powiadomienie o wydaniu jest pierwszą wiadomością wysłaną do użytkownika, który go zawiera i informuje o zobowiązaniach do zachowania poufności.

Aby utworzyć powiadomienie o wydawaniu informacji:

1. Na **kafelku Wydawanie** kliknij pozycję **Edytuj**.

2. W razie potrzeby dodaj kolejnych członków sprawy lub pracowników do **pól DW** **i UDW** . Aby dodać wielu użytkowników do tych pól, oddziel adresy e-mail średnikami.

3. Określ **temat** powiadomienia (wymagane).

4. Określ zawartość lub dodatkowe instrukcje, które chcesz udostępnić opiekunowi (wymagane). Zawartość portalu zdefiniowana w kroku 2 zostanie dodana do końca powiadomienia o wydaniu.

5. Kliknij **Zapisz**.

### <a name="re-issuance-notification"></a>Re-Issuance powiadomienia

W związku z postępem tej sytuacji może być wymagane zachowanie dodatkowych lub mniejszej niezbędnej do tego danych, niż zostało to wcześniej instrukcje. Po zaktualizowaniu zawartości portalu zostanie wysłane powiadomienie o ponownej aktualizacji i alerty o wszelkich zmianach w ich zobowiązaniach do zachowania poufności.

Aby utworzyć powiadomienie o ponownej rezygnacji:

1. Na **kafelku Ponowne wyedytowanie** kliknij pozycję **Edytuj**.

2. W razie potrzeby dodaj kolejnych członków sprawy lub pracowników do **pól DW** **i UDW** . Aby dodać wielu użytkowników do tych pól, oddziel adresy e-mail średnikami.

3. Określ **temat** powiadomienia (wymagane).

4. Określ zawartość lub dodatkowe instrukcje, które chcesz udostępnić opiekunowi (wymagane). Zawartość portalu zdefiniowana w kroku 2 jest dodawana na końcu powiadomienia o ponownej rezygnacji.

5. Kliknij **Zapisz**.

> [!NOTE]
> W przypadku zmodyfikowania zawartości portalu (na  stronie Definiowanie zawartości portalu w  kreatorze edytowania komunikacji) powiadomienie o ponownej wydaniu zostanie automatycznie wysłane do wszystkich osób przechowywczych przypisanych do tego powiadomienia. Po wysłaniu powiadomienia poproszono opiekunów o ponowne potwierdzenie tych powiadomień. Jeśli zostały ustawione jakiekolwiek przepływy pracy z przypomnieniem lub eskalacją, zostaną one również ponownie uruchomić. Aby uzyskać więcej informacji o tym, jakie inne zdarzenia zarządzania sprawą powodują wyzwolenie komunikacji, zobacz [Zdarzenia wyzwalane przez powiadomienia](#events-that-trigger-notifications).

### <a name="release-notification"></a>Powiadomienie o wersji

Po rozpoznaniu sprawy lub zachowaniu zawartości przez użytkownika, który nie zachowuje już zawartości, można go zwolnić ze sprawy. Jeśli dla włodarzy poprzednio opublikowano powiadomienie o wstrzymaniu, można użyć powiadomienia o wydaniu w celu alertów o zwolnieniu tych osób z zobowiązań.

Aby utworzyć powiadomienie o wersji:

1. Na **kafelku Wersja** kliknij pozycję **Edytuj**.

2. W razie potrzeby dodaj kolejnych członków sprawy lub pracowników do **pól DW** **i UDW** . Aby dodać wielu użytkowników do tych pól, oddziel adresy e-mail średnikami.

3. Określ **temat** powiadomienia (wymagane).

4. Określ zawartość lub dodatkowe instrukcje, które chcesz udostępnić opiekunowi (wymagane).

5. Kliknij **pozycję** Zapisz i przejdź do następnego kroku.

## <a name="optional-step-4-set-the-optional-notifications"></a>(Opcjonalnie) Krok 4. Ustawianie opcjonalnych powiadomień

Opcjonalnie możesz uprościć przepływ pracy, aby usprawnić pracę, tworząc i planując automatyczne powiadomienia o przypomnieniach i eskalacjich.

![Strona Przypomnienie/Eskalacja.](../media/ReminderEscalations.PNG)

### <a name="reminders"></a>Przypomnienia

Po wysłaniu powiadomienia o wstrzymaniu możesz utworzyć monit z mało odpowiedzialnymi użytkownikami, definiując przepływ pracy przypomnienia.

Aby zaplanować przypomnienia:

1. Na **kafelku Przypomnienie** kliknij pozycję **Edytuj**.

2. Włącz przepływ **pracy Przypomnienie** , włączając przełącznik **Stan** (wymagane).

3. Określ **interwał przypomnienia (w dniach)** (wymagany). Jest to liczba dni oczekiwania przed wysłaniem pierwszego powiadomienia z przypomnieniem i monitu. Jeśli na przykład ustawisz interwał przypomnienia na siedem dni, pierwsze przypomnienie zostanie wysłane siedem dni po początkowym wysłaniu powiadomienia o wstrzymaniu. Wszystkie kolejne przypomnienia będą również wysyłane co siedem dni.

4. Określ **liczbę przypomnień** (wymagany). To pole określa liczbę przypomnień o wysłaniu do osób, które nie odpowiadają na przypomnienia. Jeśli na przykład ustawisz liczbę przypomnień na 3, wówczas osoby, które nie otrzymają przypomnień, otrzymają maksymalnie trzy przypomnienia. Po otrzymaniu przez użytkownika potwierdzenia o wstrzymaniu przypomnienia nie będą już wysyłane do tego użytkownika.

5. Określ **temat** powiadomienia (wymagane).

6. Określ zawartość lub dodatkowe instrukcje, które chcesz udostępnić opiekunowi (wymagane). Zawartość portalu zdefiniowana w kroku 2 zostanie dodana na końcu powiadomienia o przypomnieniu.

7. Kliknij **pozycję** Zapisz i przejdź do następnego kroku.

### <a name="escalations"></a>Eskalacji

W niektórych sytuacjach mogą być potrzebne dodatkowe sposoby śledzenia osób, które nie odpowiadają na nie. Jeśli po otrzymaniu określonej liczby przypomnień nasz opiekun nie potwierdzi powiadomienia o wstrzymaniu, zespół prawny może określić przepływ pracy w celu automatycznego wysłania powiadomienia o eskalacji do wywłaszącego użytkownika i jego kierownika.

Aby zaplanować eskalacji:

1. Na **kafelku Eskalacji** kliknij pozycję **Edytuj**.

2. Włącz przepływ **pracy Eskalacja** , włączając **przełącznik Stan** .

3. Określ interwał **eskalacji (w dniach)** (wymagany).

4. Określ liczbę **eskalacji** (wymagany). To pole określa liczbę eskalacji do wysłania do osób, które nie odpowiadają. Jeśli na przykład ustawisz liczbę eskalacji na 3, do kierownika i kierownika zostanie wysłane powiadomienie o eskalacji maksymalnie trzy razy. Gdy opiekun potwierdzi powiadomienie o wstrzymaniu, eskalacja nie będzie już wysyłana.

5. Określ **temat** powiadomienia (wymagane).

6. Określ zawartość lub dodatkowe instrukcje, które chcesz udostępnić opiekunowi (wymagane). Zawartość portalu zdefiniowana w kroku 2 jest dodawana na końcu powiadomienia o eskalacji.

7. Kliknij **pozycję** Zapisz i przejdź do następnego kroku.

## <a name="step-5-assign-custodians-to-receive-notifications"></a>Krok 5. Przypisywanie osób, które się odimówią, aby otrzymywać powiadomienia

Po sfinalizowaniu zawartości powiadomień wybierz osób, do których chcesz wysłać powiadomienia.

![Wybierz stronę Pojedyńcze.](../media/SelectCustodians.PNG)

Aby dodać opiekunów:

1. Przypisz osoby do komunikacji, klikając pole wyboru obok ich nazwisk.

    Po utworzeniu komunikacji przepływ pracy powiadomień zostanie automatycznie zastosować do wybranych osób przechowywczych.

2. Kliknij **przycisk Dalej** , aby przejrzeć ustawienia i szczegóły komunikacji.

> [!NOTE]
> Można dodawać tylko osoby zatrzymane, które zostały dodane do sprawy i nie zostały wysłane kolejnego powiadomienia w ramach sprawy.

## <a name="step-6-review-settings"></a>Krok 6. Przeglądanie ustawień

Po przejrzeniu ustawień i kliknięciu przycisku **Wyślij** w celu zakończenia komunikacji system automatycznie uruchamia przepływ pracy do komunikacji, wysyłając powiadomienie o wydaniu.

## <a name="events-that-trigger-notifications"></a>Zdarzenia wyzwalane przez powiadomienia

W poniższej tabeli opisano zdarzenia w procesie zarządzania nimi, które powodują, że różne typy powiadomień są wysyłane do opiekunów.

|Typ komunikacji|Wyzwalacz |
|:---------|:---------|
|Powiadomienia o wydawaniu decyzji|Początkowe utworzenie powiadomienia. Możesz także ręcznie ponownie wysłać powiadomienie o wstrzymaniu. |
|Powiadomienia o ponownej rezygnacji|Aktualizowanie zawartości portalu na stronie **Definiowanie zawartości portalu** w **kreatorze edycji** komunikacji.|
|Informacje o wersji|W przypadku tego przypadku tylko jego pojedyńczy projekt jest zwalniany ze sprawy.|
|Przypomnienia|Interwał i liczba przypomnień skonfigurowanych dla przypomnienia.|
|Eskalacji|Interwał i liczba przypomnień skonfigurowanych dla eskalacji.|
|||
