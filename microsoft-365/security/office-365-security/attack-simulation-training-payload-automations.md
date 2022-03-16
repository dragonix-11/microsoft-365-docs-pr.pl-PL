---
title: Automatyzacja ładowania dla szkolenia symulacyjnego w zakresie ataków
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorzy mogą dowiedzieć się, jak korzystać z automatyzacji ładowania (zbierania zbiorów zbiorów danych) do zbierania i uruchamiania zautomatyzowanych symulacyjnych szkoleń symulacyjnych ataków w programie Microsoft Defender dla programu Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 3a0245acbb6d27353b4d4bd27011652c0a902975
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512385"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatyzacja ładowania dla szkolenia symulacyjnego w zakresie ataków

**Dotyczy programu** [Microsoft Defender dla Office 365 plan 2](defender-for-office-365.md)

W szkoleniach symulacyjnych ataków w programie Microsoft 365 E5 lub Microsoft Defender dla systemu Office 365 Plan 2 automatyzacje ładowania (nazywane także gromadzeniem _obciążenia)_ zbierają informacje z rzeczywistych wiadomości wyłudzających informacje, które zostały zgłoszone przez użytkowników w organizacji. Mimo że w organizacji liczba tych wiadomości jest prawdopodobnie niewielka, możesz określić warunki do wyszukiwania w przypadku ataków na wyłudzanie informacji (na przykład adresaci, technikę socjową, informacje o nadawcy itp.). Następnie szkolenie symulacyjne ataków ma na celu naśladowanie wiadomości i ładowań używanych w atakach w celu automatycznego uruchamiania nieszkodliwych symulacyjnych dla użytkowników docelowych.

Aby utworzyć automatyzację ładowania, wykonaj następujące czynności:

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com/>adresem przejdź do szkolenia **& e-mail** \> **i współpracy podczas ataków na** \> kartę Automatyzacje **ładowania.**

   Aby przejść bezpośrednio do karty **Automatyzacja ładowania** , użyj klawisza <https://security.microsoft.com/attacksimulator?viewid=payloadautomation>.

2. Na karcie **Automatyzacja ładowania** wybierz pozycję Utwórz ![ikonę automatyzacji.](../../media/m365-cc-sc-create-icon.png) **Tworzenie automatyzacji**.

   ![Przycisk utwórz automatyzację na karcie Automatyzacja ładowania w szkoleniu z symezyjną ataków w Microsoft 365 Defender sieci.](../../media/attack-sim-training-payload-automations-create.png)

3. Zostanie otwarty kreator tworzenia. W dalszej części tego artykułu opisano strony i ustawienia, które zawierają.

> [!NOTE]
> W dowolnym momencie w kreatorze tworzenia można kliknąć przycisk Zapisz  i zamknąć, aby zapisać postęp i kontynuować konfigurowanie automatyzacji ładowania później. Można podnieść lewą pozycję, zaznaczając automatyzację ładowania na karcie Automatyzacje  ładowania, a następnie klikając ikonę ![Edytuj automatyzację.](../../media/m365-cc-sc-edit-icon.png) **Edytowanie automatyzacji**.

## <a name="automation-name"></a>Nazwa automatyzacji

Na stronie **Nazwa automatyzacji** skonfiguruj następujące ustawienia:

- **Nazwa**: Wprowadź unikatową nazwę opisową automatyzacji ładowania.
- **Opis**: Wprowadź opcjonalny szczegółowy opis automatyzacji ładowania.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="run-conditions"></a>Warunki uruchomienia

Na stronie **Warunki uruchamiania** wybierz warunki rzeczywistego ataku służącego do wyłudzania informacji, który określa, kiedy zostanie uruchomione automatyzacja.

Każdy warunek można stosować tylko raz. Wiele warunków używa logiki AND (\<Condition1\> i \<Condition2\>).

![Ikona Dodaj warunek.](../../media/m365-cc-sc-create-icon.png) **Dodaj warunek**.

- **Nie. użytkowników ukierunkowanych w kampanii**: Skonfiguruj następujące ustawienia:
  - **Równe**, **Mniejsze niż**, **Większe niż**, **Mniejsze** lub równe lub **Większe niż lub równe**.
  - **Wprowadź wartość**: Liczba użytkowników, do których była kierowana kampania wyłudzająca informacje.
- **Kampanie z określoną techniką wyłudzynia informacji**: Wybierz jedną z dostępnych wartości:
  - **Zbiór poświadczeń**
  - **Załącznik z złośliwym oprogramowaniem**
  - **Łącze w załączniku**
  - **Link do złośliwego oprogramowania**
  - **Adres URL dla dysków**
- **Domena określonego nadawcy**: Wprowadź wartość domeny adresu e-mail nadawcy (na przykład contoso.com).
- **Nazwa określonego nadawcy**: wprowadź wartość nazwy nadawcy.
- **Adres e-mail określonego nadawcy**: Wprowadź adres e-mail nadawcy.
- **Określoną adresaci użytkowników i grup**: Zacznij wpisywać nazwę lub adres e-mail użytkownika lub grupy. Po jego zaznaczeniu.

Aby usunąć warunek po jego dodaniu, kliknij pozycję ![Ikona usuń.](../../media/m365-cc-sc-delete-icon.png).

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="review-automation"></a>Przeglądanie automatyzacji

Na **stronie Przeglądanie automatyzacji** możesz przejrzeć szczegóły automatyzacji ładowania.

Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

Po zakończeniu kliknij pozycję **Prześlij**.
