---
title: Badanie plików Ochrona punktu końcowego w usłudze Microsoft Defender
description: Użyj opcji badania, aby uzyskać szczegółowe informacje na temat plików skojarzonych z alertami, zachowaniami lub zdarzeniami.
keywords: badanie, badanie, plik, złośliwa aktywność, motywacja do ataku, analiza szczegółowa, raport analizy głębokiej
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: c1f6fa058715f831b1c8ba594bf1604ad92e9ed2
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669369"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Badanie pliku skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 1)](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Zbadaj szczegóły pliku skojarzonego z określonym alertem, zachowaniem lub zdarzeniem, aby ustalić, czy plik wykazuje złośliwe działania, zidentyfikować motywację do ataku i zrozumieć potencjalny zakres naruszenia.

Istnieje wiele sposobów uzyskiwania dostępu do szczegółowej strony profilu określonego pliku. Możesz na przykład użyć funkcji wyszukiwania, kliknąć link z **drzewa procesów alertów**, **wykresu zdarzenia**, **osi czasu artefaktu** lub wybrać zdarzenie wymienione na **osi czasu urządzenia**.

Po przejściu na szczegółową stronę profilu możesz przełączać się między nowymi i starymi układami strony, przełączając **nową stronę Plik**. W pozostałej części tego artykułu opisano nowszy układ strony.

Informacje z następujących sekcji można uzyskać w widoku pliku:

- Szczegóły pliku, wykrywanie złośliwego oprogramowania, częstość występowania plików
- File PE metadata (jeśli istnieje)
- Głęboka analiza
- Alerty
- Obserwowane w organizacji
- Głęboka analiza
- Nazwy plików

Możesz również wykonać akcję w pliku z tej strony.

## <a name="file-actions"></a>Akcje plików

W górnej części strony profilu nad kartami informacji o pliku. Akcje, które można wykonać w tym miejscu, obejmują:

- Zatrzymywanie i kwarantanna
- Wskaźnik dodawania/edytowania
- Pobieranie pliku
- Konsultuj się z ekspertem ds. zagrożeń
- Centrum akcji

Aby uzyskać więcej informacji na temat tych akcji, zobacz [Akcja wykonania odpowiedzi w pliku](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Szczegóły pliku, wykrywanie złośliwego oprogramowania i częstość występowania plików

Szczegóły pliku, zdarzenia, wykrywanie złośliwego oprogramowania i karty rozpowszechnienia plików zawierają różne atrybuty dotyczące pliku.

Zostaną wyświetlone szczegółowe informacje, takie jak md5 pliku, współczynnik całkowitego wykrywania wirusa i wykrywanie av w usłudze Microsoft Defender, jeśli jest dostępny, oraz częstość występowania pliku.

Karta rozpowszechnienia plików pokazuje, gdzie plik był widoczny na urządzeniach w organizacji i na całym świecie. Możesz łatwo przestawić się na pierwsze i ostatnie urządzenia, na których był widoczny plik, i kontynuować badanie na osi czasu urządzenia. 

> [!NOTE]
> Różni użytkownicy mogą widzieć różne wartości w sekcji *urządzenia w organizacji* karty częstości występowania plików. Dzieje się tak, ponieważ karta wyświetla informacje na podstawie zakresu RBAC, który ma użytkownik. Oznacza to, że jeśli użytkownikowi przyznano wgląd w określony zestaw urządzeń, na tych urządzeniach będzie widoczna tylko częstość występowania w organizacji plików.

:::image type="content" source="images/atp-file-information.png" alt-text="Informacje o pliku" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>Alerty

Karta **Alerty** zawiera listę alertów skojarzonych z plikiem, a także zdarzenie, z jakim jest połączony alert. Ta lista obejmuje wiele tych samych informacji co kolejka alertów, z wyjątkiem grupy urządzeń, do której należy, jeśli istnieje. Możesz wybrać, jakiego rodzaju informacje są wyświetlane, wybierając pozycję **Dostosuj kolumny** na pasku narzędzi powyżej nagłówków kolumn.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="Alerty związane z sekcją pliku" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>Obserwowane w organizacji

Karta **Obserwowane w organizacji** umożliwia określenie zakresu dat, aby zobaczyć, które urządzenia zostały zaobserwowane w pliku.

> [!NOTE]
> Na tej karcie zostanie wyświetlona maksymalna liczba 100 urządzeń. Aby wyświetlić _wszystkie_ urządzenia z plikiem, wyeksportuj kartę do pliku CSV, wybierając pozycję **Eksportuj** z menu akcji nad nagłówkami kolumn karty.

:::image type="content" source="images/atp-observed-machines.png" alt-text="Najnowsze zaobserwowane urządzenia z plikiem" lightbox="images/atp-observed-machines.png":::

Użyj suwaka lub selektora zakresu, aby szybko określić okres, który chcesz sprawdzić pod kątem zdarzeń dotyczących pliku. Możesz uzyskać pomoc przy wskazywaniu alertów w zakresie. Możesz określić przedział czasu tak mały, jak jeden dzień. Umożliwi to wyświetlanie tylko plików, które komunikowały się z tym adresem IP w tym czasie, co znacząco zmniejsza niepotrzebne przewijanie i wyszukiwanie.

## <a name="deep-analysis"></a>Głęboka analiza

Karta **Analiza szczegółowa** umożliwia [przesłanie pliku do szczegółowej analizy](respond-file-alerts.md#deep-analysis), aby uzyskać więcej szczegółów na temat zachowania pliku, a także wpływu, jaki ma on na organizacje. Po przesłaniu pliku raport analizy głębokiej zostanie wyświetlony na tej karcie po udostępnieniu wyników. Jeśli analiza szczegółowa nie znajdzie niczego, raport będzie pusty, a miejsce na wyniki pozostanie puste.

:::image type="content" source="images/submit-file.png" alt-text="Karta Analiza szczegółowa" lightbox="images/submit-file.png":::

## <a name="file-names"></a>Nazwy plików

Na karcie **Nazwy plików** są wyświetlane wszystkie nazwy, których plik był obserwowany w organizacji.

:::image type="content" source="images/atp-file-names.png" alt-text="Karta Nazwy plików" lightbox="images/atp-file-names.png":::

## <a name="action-center"></a>Centrum akcji

**Centrum akcji** wyświetla centrum akcji odfiltrowane w określonym pliku, dzięki czemu można zobaczyć oczekujące akcje i historię akcji wykonywanych w pliku.

## <a name="related-topics"></a>Tematy pokrewne

- [Wyświetlanie i organizowanie kolejki Ochrona punktu końcowego w usłudze Microsoft Defender](alerts-queue.md)
- [Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender](manage-alerts.md)
- [Badanie alertów Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-alerts.md)
- [Badanie urządzeń na liście urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-domain.md)
- [Badanie konta użytkownika w Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-user.md)
- [Wykonaj akcje odpowiedzi na pliku](respond-file-alerts.md)
