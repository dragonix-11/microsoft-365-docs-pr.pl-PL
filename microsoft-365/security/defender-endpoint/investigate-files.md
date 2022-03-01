---
title: Badanie plików programu Microsoft Defender dla punktów końcowych
description: Za pomocą opcji badania możesz uzyskać szczegółowe informacje na temat plików skojarzonych z alertami, zachowaniami lub zdarzeniami.
keywords: badanie, analiza, plik, złośliwa aktywność, motywacja ataków, dogłębna analiza, raport dogłębnej analizy
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: b990c73f9cdb81d164bd57d1aff5b7ec61df714f
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011923"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Badanie pliku skojarzonego z alertem programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Badanie szczegółów pliku skojarzonego z określonym alertem, zachowaniem lub zdarzeniem w celu ustalenia, czy plik zawiera złośliwe działania, zidentyfikuje motywację ataków i zrozumienie potencjalnego zakresu naruszenia.

Istnieje wiele sposobów uzyskiwania dostępu do strony szczegółowego profilu określonego pliku. Możesz na przykład użyć funkcji wyszukiwania, kliknąć link w drzewie procesu **alertu****, wykres** **zdarzenia, oś** czasu Artefakt lub wybrać zdarzenie wymienione na osi **czasu urządzenia**.

Gdy znajdziesz się na stronie ze szczegółowymi informacjami o profilu, możesz przełączać się między nowym i starym układem strony, przełączać się między nową **stroną Plik**. W dalszej części tego artykułu opisano nowsze układy stron.

W widoku pliku można uzyskać informacje z następujących sekcji:

- Szczegóły pliku, Wykrywanie złośliwego oprogramowania, Ochrona plików
- Analiza głębokości
- Alerty
- Obserwowane w organizacji
- Analiza głębokości
- Nazwy plików

Na tej stronie możesz także podjąć działania na pliku.

## <a name="file-actions"></a>Akcje pliku

U góry strony profilu nad kartami z informacjami o plikach. Oto akcje, które można wykonać w tym miejscu:

- Zatrzymywanie i kwarantanna
- Wskaźnik dodawania/edytowania
- Pobierz plik
- Skonsultuj się z ekspertem ds. zagrożeń
- Centrum akcji

Aby uzyskać więcej informacji na temat tych akcji, zobacz [Akcje odpowiedzi dotyczące pliku](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Szczegóły pliku, wykrywanie złośliwego oprogramowania i ochrona pliku

Na kartach szczegółów pliku, zdarzeń, złośliwego oprogramowania i kart pamięci są wyświetlane różne atrybuty pliku.

Zobaczysz szczegółowe informacje, takie jak md5 pliku, współczynnik wykrywania liczby wirusów i wykrywanie audio/wideo programu Microsoft Defender, jeśli jest dostępny, oraz informacje na temat tego pliku.

Karta z wizytówką pliku pokazuje miejsce, w którym plik był widoczny na urządzeniach w organizacji i na całym świecie.

> [!NOTE]
> Różne użytkownicy mogą zobaczyć różne wartości na urządzeniach w sekcji organizacji  na karcie kart treści pliku. Wynika to z tego, że na karcie są wyświetlane informacje na podstawie zakresu RBAC posiadanych przez użytkownika. Oznacza to, że jeśli użytkownikowi udzielono widoczności na określonym zestawie urządzeń, zobaczy on tylko plik organizacji na tych urządzeniach.

![Obraz informacji o pliku.](images/atp-file-information.png)

## <a name="alerts"></a>Alerty

Karta **Alerty** zawiera listę alertów skojarzonych z plikiem. Na tej liście zasłania się wiele informacji dostępnych w kolejce alertów, z wyjątkiem grupy urządzeń, do której należy dane urządzenie (jeśli taka grupa jest). Możesz wybrać rodzaj informacji, które mają być wyświetlane, wybierając pozycję Dostosuj **kolumny** na pasku narzędzi powyżej nagłówków kolumn.

![Obraz alertów dotyczących sekcji pliku.](images/atp-alerts-related-to-file.png)

## <a name="observed-in-organization"></a>Obserwowane w organizacji

Karta **Obserwowane** w organizacji umożliwia określenie zakresu dat w celu określenia, które urządzenia zostały obserwowane w pliku.

> [!NOTE]
> Na tej karcie jest pokazywanych maksymalnie 100 urządzeń. Aby wyświetlić _wszystkie_ urządzenia z plikiem, wyeksportuj kartę do pliku  CSV, wybierając pozycję Eksportuj z menu akcji powyżej nagłówków kolumn na karcie.

![Obraz ostatnio obserwowanego urządzenia z plikiem.](images/atp-observed-machines.png)

Za pomocą suwaka lub selektora zakresów możesz szybko określić przedział czasu, w którym chcesz sprawdzić, czy zdarzenia związane z plikiem mają być sprawdzane. Możesz określić okres tak mały, jak jeden dzień. Umożliwi to wyświetlanie tylko plików, które wówczas komunikowały się z tym adresem IP, znacząco zmniejszając niepotrzebne przewijanie i wyszukiwanie.

## <a name="deep-analysis"></a>Analiza głębokości

Karta **Analiza głębokości** umożliwia przesłanie pliku do szczegółowej [analizy, odkrycie](respond-file-alerts.md#deep-analysis) szczegółowych informacji na temat zachowania pliku oraz jego wpływu na działanie tego pliku w organizacji. Po przesłaniu pliku po ich zaznaczeniu na tej karcie pojawi się raport z analizą głębokości. Jeśli podczas dogłębnej analizy nic nie znajdzie, raport będzie pusty, a obszar wyników pozostanie pusty.

![Obraz karty Analiza głębokości.](images/submit-file.png)

## <a name="file-names"></a>Nazwy plików

Karta **Nazwy plików** zawiera listę wszystkich nazw obserwowanych w celu użycia pliku w Twojej organizacji.

![Obraz karty Nazwy plików.](images/atp-file-names.png)

## <a name="related-topics"></a>Tematy pokrewne

- [Wyświetlanie i organizowanie kolejki programu Microsoft Defender dla punktu końcowego](alerts-queue.md)
- [Zarządzanie alertami programu Microsoft Defender dla punktów końcowych](manage-alerts.md)
- [Badanie alertów programu Microsoft Defender dla punktów końcowych](investigate-alerts.md)
- [Badanie urządzeń na liście programu Microsoft Defender dla urządzeń końcowych](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem programu Microsoft Defender dla punktu końcowego](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem programu Microsoft Defender dla punktu końcowego](investigate-domain.md)
- [Badanie konta użytkownika w programie Microsoft Defender dla punktu końcowego](investigate-user.md)
- [Akcje odpowiedzi dotyczące pliku](respond-file-alerts.md)
