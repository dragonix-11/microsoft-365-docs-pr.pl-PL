---
title: Automatyzacje ładunków na potrzeby trenowania symulacji ataków
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
description: Administratorzy mogą dowiedzieć się, jak używać automatyzacji ładunków (zbierania ładunków) do zbierania i uruchamiania zautomatyzowanych symulacji na potrzeby trenowania symulacji ataków w Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.openlocfilehash: bc7bba0d91e9b2ff1f9baddc52f717450660d070
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838918"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatyzacje ładunków na potrzeby trenowania symulacji ataków

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

W ramach trenowania symulacji ataków w Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2 automatyzacje ładunków (znane również jako _zbieranie ładunków_) zbierają informacje z rzeczywistych komunikatów o ataku wyłudzania informacji, które zostały zgłoszone przez użytkowników w organizacji. Chociaż liczba tych komunikatów jest prawdopodobnie niska w organizacji, możesz określić warunki, których należy szukać w przypadku ataków wyłudzania informacji (na przykład adresatów, techniki inżynierii społecznej, informacji o nadawcy itp.). Trenowanie symulacji ataków będzie następnie naśladować komunikaty i ładunki używane w ataku do automatycznego uruchamiania nieszkodliwych symulacji dla docelowych użytkowników.

Aby wyświetlić dostępne automatyzacje ładunków, otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>, przejdź do karty \> Automatyzacje **trenowania symulacji** \> **ataków** **& współpracy** \> pocztą e-mail, a następnie wybierz pozycję **Automatyzacje ładunku**. Aby przejść bezpośrednio do karty **Automatyzacje** , na której można wybrać pozycję **Automatyzacje ładunku**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=automations>.

Dla każdej automatyzacji ładunku są wyświetlane następujące informacje:

- **Nazwa automatyzacji**
- **Typ**: Wartość to **Payload**.
- **Zebrane elementy**
- **Ostatnia modyfikacja**
- **Stan**: Wartość to **Gotowe** lub **Wersja robocza**.

Po wybraniu automatyzacji ładunku z listy zostanie wyświetlony wysuwany szczegół z następującymi informacjami:

- **Karta Ogólne** : wyświetla podstawowe informacje o automatyzacji symulacji.
- Karta **Historia uruchamiania**: ta karta jest dostępna tylko dla automatyzacji ładunków z wartością **Stan** **Gotowy**.

## <a name="create-payload-automations"></a>Tworzenie automatyzacji ładunków

Aby utworzyć automatyzację ładunku, wykonaj następujące kroki:

1. W portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com/>przejdź do obszaru Email & collaboration Attack simulation training **Automations** tab \> **Payload automations (Automatyzacje ładunków** za pomocą **funkcji e-mail & współpracy** \> **w zakresie** \> symulacji ataków). Aby przejść bezpośrednio do karty **Automatyzacje** , na której można wybrać pozycję **Automatyzacje ładunku**, użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=automations>.

   Kliknij ikonę ![Utwórz automatyzację.](../../media/m365-cc-sc-create-icon.png) **Tworzenie automatyzacji**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Przycisk Utwórz symulację na karcie Automatyzacje ładunku w trenowaniu symulacji ataku w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

   > [!NOTE]
   > W dowolnym momencie kreatora tworzenia możesz kliknąć pozycję **Zapisz i zamknij** , aby zapisać postęp i kontynuować konfigurowanie automatyzacji ładunku później. Możesz wybrać miejsce, w którym zostało przerwane, wybierając automatyzację ładunku w **automatyzacjach ładunków**, a następnie klikając ikonę Edytuj automatyzację ![.](../../media/m365-cc-sc-edit-icon.png) **Edytuj automatyzację**. Częściowo ukończona automatyzacja ładunku będzie mieć wartość **Stan** **— wersja robocza**.

2. Na stronie **Nazwa usługi Automation** skonfiguruj następujące ustawienia:

   - **Nazwa**: wprowadź unikatową, opisową nazwę automatyzacji ładunku.
   - **Opis**: wprowadź opcjonalny szczegółowy opis automatyzacji ładunku.

   Po zakończeniu kliknij przycisk **Dalej**.

3. Na stronie **Warunki uruchamiania** wybierz warunki rzeczywistego ataku polegającego na wyłudzaniu informacji, który określa, kiedy zostanie uruchomiona automatyzacja.

   Kliknij ikonę ![Dodaj warunek.](../../media/m365-cc-sc-create-icon.png) **Dodaj warunek** i wybierz jeden z następujących warunków:

   - **Nr. użytkowników objętych kampanią**: skonfiguruj następujące ustawienia:
     - **Równe**, **Mniejsze niż**, **Większe niż**, **Mniejsze lub równe** lub **Większe niż lub równe**.
     - **Wprowadź wartość**: liczba użytkowników objętych kampanią wyłudzania informacji.
   - **Kampanie z określoną techniką phish**: wybierz jedną z dostępnych wartości:
     - **Zbieranie poświadczeń**
     - **Załącznik złośliwego oprogramowania**
     - **Link w załączniku**
     - **Link do złośliwego oprogramowania**
     - **Drive-by URL**
   - **Określona domena nadawcy**: wprowadź wartość domeny wiadomości e-mail nadawcy (na przykład contoso.com).
   - **Określona nazwa nadawcy**: wprowadź wartość nazwy nadawcy.
   - **Adres e-mail określonego nadawcy**: wprowadź adres e-mail nadawcy.
   - **Określoni adresaci użytkowników i grup**: zacznij wpisywać nazwę lub adres e-mail użytkownika lub grupy. Gdy zostanie wyświetlony, wybierz go.

   Każdy warunek można użyć tylko raz. Wiele warunków używa logiki AND (\<Condition1\> i \<Condition2\>).

   Aby dodać inny warunek, kliknij ikonę ![Dodaj warunek.](../../media/m365-cc-sc-create-icon.png) **Dodaj warunek**.

   Aby usunąć warunek po jego dodaniu, kliknij przycisk ![Usuń ikonę.](../../media/m365-cc-sc-delete-icon.png).

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na stronie **Przegląd automatyzacji** możesz przejrzeć szczegóły automatyzacji ładunku.

   W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

5. Na utworzonej stronie **Nowa automatyzacja** możesz użyć linków, aby włączyć automatyzację lub przejść do strony **Symulacje** .

   Po zakończeniu kliknij pozycję **Gotowe**.

Po **powrocie do automatyzacji ładunku** w **usłudze Automations** zostanie wyświetlona utworzona strona logowania.

## <a name="turn-payload-automations-on-or-off"></a>Włączanie lub wyłączanie automatyzacji ładunków

Automatyzacje ładunków można włączać lub wyłączać tylko wtedy, gdy wartość **Stan** to **Gotowe**. Nie można włączać ani wyłączać niekompletnych automatyzacji ładunków, w których wartość **Stan** to **Wersja robocza**.

Aby włączyć automatyzację ładunku, wybierz ją z listy, klikając pole wyboru. Kliknij ikonę ![Włącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz** wyświetloną ikonę, a następnie kliknij przycisk **Potwierdź** w oknie dialogowym.

Aby wyłączyć automatyzację ładunku, wybierz ją z listy, klikając pole wyboru. Kliknij ikonę ![Wyłącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz** wyświetloną ikonę, a następnie kliknij przycisk **Potwierdź** w oknie dialogowym.

## <a name="modify-payload-automations"></a>Modyfikowanie automatyzacji ładunków

Aby zmodyfikować istniejącą automatyzację ładunku w **automatyzacjach ładunków**, wykonaj jedną z następujących czynności:

- Wybierz automatyzację ładunku z listy, klikając pole wyboru. Kliknij ikonę Edytuj ![automatyzację.](../../media/m365-cc-sc-edit-icon.png) **Edytuj** wyświetloną ikonę automatyzacji.
- Wybierz automatyzację ładunku z listy, klikając dowolne miejsce w wierszu z wyjątkiem pola wyboru. W wyświetlonym wysuwu szczegółów na karcie **Ogólne** kliknij pozycję **Edytuj** w sekcjach **Nazwa**, **Opis** lub **Warunki uruchamiania** .

Zostanie otwarty kreator automatyzacji ładunków z ustawieniami i wartościami wybranej automatyzacji ładunku. Kroki są takie same, jak opisano w sekcji [Tworzenie automatyzacji ładunku](#create-payload-automations) .

## <a name="remove-payload-automations"></a>Usuwanie automatyzacji ładunków

Aby usunąć automatyzację ładunku, wybierz automatyzację ładunku z listy, klikając pole wyboru. Kliknij ikonę ![Usuń.](../../media/m365-cc-sc-delete-icon.png) **Zostanie** wyświetlona ikona Usuń, a następnie kliknij przycisk **Potwierdź** w oknie dialogowym.

## <a name="related-links"></a>Linki pokrewne

[Wprowadzenie do szkolenia z symulacji ataku](attack-simulation-training-get-started.md)

[Automatyzacje symulacji na potrzeby trenowania symulacji ataków](attack-simulation-training-simulation-automations.md)

[Uzyskuj szczegółowe informacje dzięki szkoleniu związanemu z symulacją ataku](attack-simulation-training-insights.md)
