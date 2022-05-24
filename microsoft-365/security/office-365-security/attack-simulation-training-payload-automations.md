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
ms.openlocfilehash: 5b008dc25ee3b705f212b1fac1bf3779f1de8bda
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647518"
---
# <a name="payload-automations-for-attack-simulation-training"></a>Automatyzacje ładunków na potrzeby trenowania symulacji ataków

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy** [planu Ochrona usługi Office 365 w usłudze Microsoft Defender 2](defender-for-office-365.md)

W ramach trenowania symulacji ataków w Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2 automatyzacje ładunków (nazywane również _zbieraniem ładunków_) zbierają informacje z rzeczywistych komunikatów wyłudzających informacje, które zostały zgłoszone przez użytkowników w organizacji. Chociaż liczba tych komunikatów jest prawdopodobnie niska w organizacji, możesz określić warunki, których należy szukać w przypadku ataków wyłudzania informacji (na przykład adresatów, techniki inżynierii społecznej, informacji o nadawcy itp.). Trenowanie symulacji ataków będzie następnie naśladować komunikaty i ładunki używane w ataku do automatycznego uruchamiania nieszkodliwych symulacji dla docelowych użytkowników.

Aby utworzyć automatyzację ładunku, wykonaj następujące kroki:

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/>przejdź do karty Email & collaboration **Attack simulation training** \> **Payload automations (Trenowanie automatyzacji ładunków** za pomocą **funkcji e-mail & symulacji** \> ataków).

   Aby przejść bezpośrednio do karty **Automatyzacje ładunku** , użyj polecenia <https://security.microsoft.com/attacksimulator?viewid=payloadautomation>.

2. Na **karcie Automatyzacje ładunku** wybierz pozycję Utwórz ikonę ![automatyzacji.](../../media/m365-cc-sc-create-icon.png) **Tworzenie automatyzacji**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Przycisk Utwórz symulację na karcie Automatyzacje ładunku w trenowaniu symulacji ataku w portalu Microsoft 365 Defender" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Zostanie otwarty kreator tworzenia. W pozostałej części tego artykułu opisano strony i ustawienia, które zawierają.

> [!NOTE]
> W dowolnym momencie kreatora tworzenia możesz kliknąć pozycję **Zapisz i zamknij** , aby zapisać postęp i kontynuować konfigurowanie automatyzacji ładunku później. Możesz wybrać miejsce, w którym zostało przerwane, wybierając automatyzację ładunku na **karcie Automatyzacje ładunku** , a następnie klikając ikonę Edytuj automatyzację ![.](../../media/m365-cc-sc-edit-icon.png) **Edytuj automatyzację**.

## <a name="automation-name"></a>Nazwa automatyzacji

Na stronie **Nazwa usługi Automation** skonfiguruj następujące ustawienia:

- **Nazwa**: wprowadź unikatową, opisową nazwę automatyzacji ładunku.
- **Opis**: wprowadź opcjonalny szczegółowy opis automatyzacji ładunku.

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="run-conditions"></a>Warunki uruchamiania

Na stronie **Warunki uruchamiania** wybierz warunki rzeczywistego ataku polegającego na wyłudzaniu informacji, który określa, kiedy zostanie uruchomiona automatyzacja.

Każdy warunek można użyć tylko raz. Wiele warunków używa logiki AND (\<Condition1\> i \<Condition2\>).

![Dodaj ikonę warunku.](../../media/m365-cc-sc-create-icon.png) **Dodaj warunek**.

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

Aby usunąć warunek po jego dodaniu, kliknij przycisk ![Usuń ikonę.](../../media/m365-cc-sc-delete-icon.png).

Po zakończeniu kliknij przycisk **Dalej**.

## <a name="review-automation"></a>Przegląd automatyzacji

Na stronie **Przegląd automatyzacji** możesz przejrzeć szczegóły automatyzacji ładunku.

W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

Po zakończeniu kliknij pozycję **Prześlij**.
