---
title: Ponawianie próby przeszukiwania zawartości w celu rozwiązania problemu z lokalizacją zawartości
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: ''
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: W trakcie badania możesz użyć przycisku Ponów próbę w celu rozwiązania problemów z przeszukiwaniami zawartości, w których wystąpiły błędy lokalizacji zawartości.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3c433dfa6bf842f1d62350e3b518177d1bdca6d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984965"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>Ponawianie próby przeszukiwania zawartości w celu rozwiązania problemu z lokalizacją zawartości

Podczas wyszukiwania zawartości w Centrum zabezpieczeń i zgodności w celu przeszukania dużej liczby skrzynek pocztowych mogą zostać wystąpiły błędy wyszukiwania podobne do tego błędu:

```text
Error


The search on the following locations failed:

User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)

User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Te błędy (kody błędów CS001-002, CS003-002, CS008-009, CS012-002 i inne błędy formularza CS0XX-0XX) wskazują, że wyszukiwanie zawartości nie powiodło się do konkretnych lokalizacji zawartości. w tym przykładzie nie wyszukiwano dwóch skrzynek pocztowych. Te błędy są wyświetlane na wysuwanych informacjach o stanie na stronie przeszukiwania zawartości.

## <a name="cause-of-content-location-errors"></a>Przyczyna błędów lokalizacji zawartości

Podczas wyszukiwania w dużej liczbie skrzynek pocztowych wyszukiwanie jest rozłożone na tysiące serwerów w centrum danych firmy Microsoft. W dowolnym momencie określone serwery mogą być w stanie ponownego rozruchu lub w procesie uruchamiania w celu ponownego uruchomienia w nadmiarowych kopiach. W każdym z tych przypadków żądanie pobrania danych przez przeszukiwanie zawartości ułomie się. W poprzednim przykładzie błędy dotyczące skrzynek pocztowych, których wyszukiwanie zakończyło się niepowodzeniem, były wynikiem przechyłki wyszukiwania.

## <a name="resolving-content-location-errors"></a>Rozwiązywanie błędów dotyczących lokalizacji zawartości

Ponowne uruchomienie wyszukiwania często powoduje podobne błędy na różnych serwerach. Zamiast ponownie uruchamiać wyszukiwanie, **kliknij przycisk** Ponów próbę wyświetlany u góry strony wyników wyszukiwania.

![Kliknij przycisk Ponów próbę, aby usunąć błędy lokalizacji zawartości.](../media/retrycontentsearch3.png)

Spowoduje to ponowne przeszukanie tylko tych skrzynek pocztowych, których wyszukiwanie zakończyło się niepowodzeniem. Po ponowiniu próby wyszukiwania pozostałe wyniki, które zostały pomyślnie zwrócone, zostaną zachowane.

## <a name="tips-to-avoid-content-location-errors"></a>Wskazówki w celu uniknięcia błędów lokalizacji zawartości

Oto kilka dodatkowych przyczyn błędów lokalizacji zawartości i kilka porad pomocnych w ich uniknięciu podczas wyszukiwania w dużej liczbie skrzynek pocztowych.

- Przeszukiwana skrzynka pocztowa może być zajęta z powodu aktywności użytkowników. W takim przypadku usługa wyszukiwania może ograniczać się, aby zapobiec niedostępności skrzynki pocztowej. Aby tego uniknąć, spróbuj uruchamiać wyszukiwania w godzinach innych niż godziny pracy.

- Kwerenda wyszukiwania może pobierania zbyt dużej zawartości ze skrzynki pocztowej. Jeśli to możliwe, spróbuj zawęzić zakres wyszukiwania przy użyciu słów kluczowych, zakresów dat i warunków wyszukiwania.

- Zbyt wiele słów kluczowych lub fraz słów kluczowych podczas tworzenia zapytania wyszukiwania przy użyciu [listy słów kluczowych](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches). Po uruchomieniu zapytania wyszukiwania, które używa listy słów kluczowych, usługa zasadniczo uruchamia oddzielne wyszukiwanie dla każdego wiersza na liście słów kluczowych, aby można było generować statystyki. Jeśli używasz listy słów kluczowych w zapytaniach wyszukiwania, zminimalizuj liczbę wierszy na liście słów kluczowych lub podziel słowa kluczowe liczby na mniejsze listy i utwórz inne wyszukiwanie dla każdej listy słów kluczowych.

  > [!NOTE]
  > Teraz możesz ograniczyć liczbę problemów spowodowanych przez duże listy słów kluczowych do maksymalnie 20 wierszy na liście słów kluczowych zapytania wyszukiwania.

- Jednocześnie jest wykonywanych zbyt wiele wyszukiwań w tej samej skrzynce pocztowej. Jeśli to możliwe, spróbuj uruchomić jedno wyszukiwanie na raz w dowolnej skrzynce pocztowej.

- Wyszukiwanie zbyt wielu skrzynek pocztowych w ramach jednego wyszukiwania. Prawdopodobieństwo błędów lokalizacji zawartości zwiększa się podczas wyszukiwania w dużej liczbie skrzynek pocztowych. Jeśli to możliwe, spróbuj uruchomić wiele wyszukiwań, aby każde wyszukiwanie uwzględniało podzbiór skrzynek pocztowych w organizacji.

- W skrzynce pocztowej jest wykonywana wymagana konserwacja. Mimo że ta przyczyna prawdopodobnie występuje rzadko, poczekaj chwilę po otrzymaniu błędu lokalizacji zawartości i ponów próbę wyszukiwania.
