---
title: Badanie domen programu Microsoft Defender dla punktów końcowych
description: Użyj opcji badania, aby sprawdzić, czy urządzenia i serwery komunikowały się ze złośliwymi domenami.
keywords: badanie domeny, domeny, złośliwej domeny, programu Microsoft Defender dla punktu końcowego, alertu, adresu URL
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
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: bc309c3215524b20ff93c6f1f9c16248fdfffac1
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2021
ms.locfileid: "62996809"
---
# <a name="investigate-a-domain-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Badanie domeny skojarzonej z alertem programu Microsoft Defender dla punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatedomain-abovefoldlink)

Zbadaj domenę, aby sprawdzić, czy urządzenia i serwery w sieci przedsiębiorstwa komunikują się ze znaną złośliwą domeną.

Domenę możesz zbadać za pomocą funkcji wyszukiwania lub klikając link domeny na osi **czasu urządzenia**.

W widoku adresu URL można wyświetlać informacje z następujących sekcji:

- Szczegóły adresu URL, kontakty, serwery nazw
- Alerty dotyczące tego adresu URL 
- Adres URL w organizacji
- Najnowsze obserwowane urządzenia z adresem URL

## <a name="url-worldwide"></a>Adres URL na całym świecie

W **sekcji Adres URL na** całym świecie jest wymieniony adres URL, link do szczegółowych informacji na stronie Whois, liczba powiązanych otwartych zdarzeń i liczba aktywnych alertów.

## <a name="incident"></a>Zdarzenie

Na **karcie Zdarzenie** jest wyświetlany wykres słupkowy wszystkich aktywnych alertów dotyczących zdarzeń z ostatnich 180 dni.

## <a name="prevalence"></a>Wytła dla

Karta  Więdło zawiera szczegółowe informacje o zbędnych adresach URL w organizacji w określonym czasie.

Chociaż domyślny okres to ostatnie 30 dni, zakres można dostosować, wybierając strzałkę w dół w rogu karty. Najmniejszy dostępny zakres należy do przedziału dat wcześniejszego dnia, natomiast najdłuższy zakres wynosi w ciągu ostatnich 6 miesięcy.

## <a name="alerts"></a>Alerty

Karta **Alerty** zawiera listę alertów skojarzonych z adresem URL. W poniższej tabeli przedstawiono przefiltrowane wersje alertów widoczne na ekranie kolejki alertów, wyświetlając tylko alerty skojarzone z domeną, ich ważność, stan, skojarzone zdarzenie, klasyfikację, stan badania i inne.

Kartę Alerty można dostosować, aby wyświetlić więcej lub mniej informacji, wybierając polecenie  Dostosuj kolumny w menu akcji powyżej nagłówków kolumn. Liczbę wyświetlanych elementów można również dostosować, wybierając **elementy na stronie** w tym samym menu.

## <a name="observed-in-organization"></a>Obserwowane w organizacji

Karta **Obserwowane w organizacji** udostępnia widok chronologiczny zdarzeń i skojarzonych z nimi alertów, które zostały obserwowane pod adresem URL. Ta karta zawiera oś czasu i tabelę z możliwością dostosowania, która zawiera szczegółowe informacje o zdarzeniu, takie jak godzina, urządzenie, oraz krótki opis tego, co się stało. 

Zdarzenia z różnych okresów czasu można wyświetlać, wprowadzając daty w polach tekstowych nad nagłówkami tabeli. Możesz także dostosować zakres czasu, wybierając różne obszary osi czasu.

**Badanie domeny:**

1. Wybierz **pozycję Adres URL** **z menu rozwijanego** paska wyszukiwania.
2. Wprowadź adres URL w **polu** Wyszukaj.
3. Kliknij ikonę wyszukiwania lub naciśnij klawisz **Enter**. Zostaną wyświetlone szczegółowe informacje o adresie URL. Uwaga: wyniki wyszukiwania będą zwracane tylko dla adresów URL obserwowanych w komunikacji z urządzeniami w organizacji.
4. Zdefiniuj kryteria wyszukiwania za pomocą filtrów wyszukiwania. Za pomocą pola wyszukiwania osi czasu możesz również filtrować wyświetlane wyniki wszystkich urządzeń obserwowanych w organizacji komunikjących się z adresem URL, pliku skojarzonego z komunikacją i ostatniej obserwowanej daty.
5. Kliknięcie dowolnej nazwy urządzenia spowoduje wyświetlenie widoku tego urządzenia, w którym możesz kontynuować badanie zgłoszonych alertów, zachowań i zdarzeń.

## <a name="related-topics"></a>Tematy pokrewne
- [Wyświetlanie i organizowanie kolejki alertów programu Microsoft Defender dla punktu końcowego](alerts-queue.md)
- [Zarządzanie alertami programu Microsoft Defender dla punktów końcowych](manage-alerts.md)
- [Badanie alertów programu Microsoft Defender dla punktów końcowych](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem programu Microsoft Defender dla punktu końcowego](investigate-files.md)
- [Badanie urządzeń na liście programu Microsoft Defender dla urządzeń końcowych](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem programu Microsoft Defender dla punktu końcowego](investigate-ip.md)
- [Badanie konta użytkownika w programie Microsoft Defender dla punktu końcowego](investigate-user.md)
