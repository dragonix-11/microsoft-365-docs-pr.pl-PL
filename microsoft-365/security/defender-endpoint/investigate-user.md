---
title: Badanie konta użytkownika w programie Microsoft Defender dla punktu końcowego
description: Badanie konta użytkownika pod uwagę w przypadku potencjalnego naruszenia poświadczeń lub przeskok na skojarzone konto użytkownika w trakcie badania.
keywords: badanie, konto, użytkownik, podmiot użytkownika, alert, usługa Microsoft Defender dla punktu końcowego
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
ms.openlocfilehash: feebff9361f1504e94069e82a3de87a2e1d95c0c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312675"
---
# <a name="investigate-a-user-account-in-microsoft-defender-for-endpoint"></a>Badanie konta użytkownika w programie Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatgeuser-abovefoldlink)

## <a name="investigate-user-account-entities"></a>Badanie jednostek konta użytkownika

Określ konta użytkowników z najbardziej aktywnymi alertami (wyświetlanymi na pulpicie nawigacyjnym jako "Potencjalni użytkownicy") i zbadaj potencjalne naruszone poświadczenia lub przestaw skojarzone konto użytkownika podczas badania alertu lub urządzenia w celu zidentyfikowania możliwego ruchu bocznego między urządzeniami z tym kontem użytkownika.

Informacje o koncie użytkownika można znaleźć w następujących widokach:

- Pulpit nawigacyjny
- Kolejka alertów
- Strona szczegółów urządzenia

W tych widokach jest dostępny link do konta użytkownika, który można kliknąć, co spowoduje, że zostaniesz na stronie szczegółów konta użytkownika, gdzie zostaną wyświetlone więcej szczegółowych informacji o koncie użytkownika.

Podczas badania jednostki konta użytkownika zobaczysz:

- Szczegóły konta użytkownika, alerty usługi Microsoft Defender dla tożsamości oraz zalogowane urządzenia, rola, typ logowania i inne szczegóły
- Omówienie zdarzeń i urządzeń użytkownika
- Alerty dotyczące tego użytkownika
- Obserwowane w organizacji (urządzenia zalogowane do)

![Obraz strony szczegółów encji konta użytkownika.](images/atp-user-details-view.png)

### <a name="user-details"></a>Szczegóły użytkownika

Okienko  szczegółów użytkownika po lewej stronie zawiera informacje o użytkowniku, takie jak pokrewne zdarzenia otwarte, aktywne alerty, nazwa SAM, identyfikator SID, alerty usługi Microsoft Defender dla tożsamości, liczba urządzeń, na których użytkownik jest zalogowany, oraz informacje o pierwszym i ostatnim widzieli, rolach i typach logowania. W zależności od włączonych funkcji integracji zobaczysz inne szczegóły. Jeśli na przykład włączysz integrację usługi Skype dla firm, będzie można skontaktować się z użytkownikiem z portalu. Sekcja **Azure ATP alerts** (Alerty ATP) platformy Azure zawiera link, który umożliwia dostęp do strony Microsoft Defender for Identity, jeśli włączono funkcję Microsoft Defender for Identity i istnieją alerty dotyczące użytkownika. Na stronie Microsoft Defender for Identity zostaną podane dodatkowe informacje o alertach.

> [!NOTE]
> Aby korzystać z tej funkcji, należy włączyć integrację zarówno z usługą Microsoft Defender for Identity, jak i Usługą Defender for Endpoint. W programie Defender for Endpoint możesz włączyć tę funkcję w zaawansowanych funkcjach. Aby uzyskać więcej informacji na temat włączania funkcji zaawansowanych, zobacz [Włączanie funkcji zaawansowanych](advanced-features.md).

Przegląd, Alerty i Obserwowane w organizacji to różne karty z różnymi atrybutami konta użytkownika.


>[!NOTE]
>W przypadku urządzeń z systemem Linux informacje o zalogowanych użytkownikach nie są wyświetlane.


### <a name="overview"></a>Omówienie

Karta **Przegląd** zawiera szczegóły zdarzeń oraz listę urządzeń, na których użytkownik zalogował się. Możesz je rozwinąć, aby wyświetlić szczegóły zdarzeń logowania dla każdego urządzenia.

### <a name="alerts"></a>Alerty

Karta **Alerty** zawiera listę alertów skojarzonych z kontem użytkownika. Ta lista zawiera przefiltrowany widok kolejki alertów oraz alerty, w których kontekście użytkownika jest wybrane konto użytkownika, data wykrycia ostatniego działania, krótki opis alertu, urządzenie skojarzone z alertem, ważność alertu, stan alertu w kolejce oraz osoba, do której został przypisany alert.[](alerts-queue.md)

### <a name="observed-in-organization"></a>Obserwowane w organizacji

Na **karcie** Obserwowane w organizacji można określić zakres dat, aby wyświetlić listę urządzeń, na których obserwowany był zalogowany ten użytkownik, najczęściej i najczęstszo zalogowanych użytkowników dla każdego z tych urządzeń oraz całkowitą liczbę obserwowanych użytkowników na każdym urządzeniu.

Wybranie elementu w tabeli Obserwowane w organizacji spowoduje rozwinięcie tego elementu, ujawniając więcej szczegółów dotyczących urządzenia. Bezpośrednie wybranie linku w obrębie elementu spowoduje wysłanie Cię do odpowiedniej strony.

## <a name="search-for-specific-user-accounts"></a>Wyszukiwanie konkretnych kont użytkowników

1. Wybierz **pozycję** Użytkownik z **menu rozwijanego** paska wyszukiwania.
2. Wprowadź konto użytkownika w **polu** Wyszukaj.
3. Kliknij ikonę wyszukiwania lub naciśnij klawisz **Enter**.

Zostanie wyświetlona lista użytkowników pasujących do tekstu zapytania. Gdy konto użytkownika zostało ostatnio widziane, zobaczysz nazwę i domenę tego konta oraz łączną liczbę urządzeń, na których było ono obserwowane w ciągu ostatnich 30 dni.

Można filtrować wyniki według następujących okresów:

- 1 dzień
- 3 dni
- 7 dni
- 30 dni
- 6 miesięcy

## <a name="related-topics"></a>Tematy pokrewne

- [Wyświetlanie i organizowanie kolejki alertów programu Microsoft Defender dla punktu końcowego](alerts-queue.md)
- [Zarządzanie alertami programu Microsoft Defender dla punktów końcowych](manage-alerts.md)
- [Badanie alertów programu Microsoft Defender dla punktów końcowych](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem programu Defender dla punktu końcowego](investigate-files.md)
- [Badanie urządzeń na liście Usługi Defender dla urządzeń końcowych](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem programu Defender dla punktu końcowego](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem programu Defender dla punktu końcowego](investigate-domain.md)
