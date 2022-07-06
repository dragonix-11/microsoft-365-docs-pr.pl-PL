---
title: Ponów próbę wyszukiwania zawartości, aby rozwiązać problem z błędem lokalizacji zawartości
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Podczas badania możesz użyć przycisku Ponów próbę, aby rozwiązać problemy z wyszukiwaniem zawartości z błędami lokalizacji zawartości.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c524be95ac72f44e58b03958694d26c52a401e40
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638174"
---
# <a name="retry-a-content-search-to-resolve-a-content-location-error"></a>Ponów próbę wyszukiwania zawartości, aby rozwiązać problem z błędem lokalizacji zawartości

W przypadku wyszukiwania zawartości w centrum zabezpieczeń i zgodności do wyszukiwania dużej liczby skrzynek pocztowych mogą wystąpić błędy wyszukiwania podobne do błędu:

```text
Error


The search on the following locations failed:

User1@contoso.com: Problem in processing the request. Please try again later. If you keep getting this error, contact your admin. (CS008-009)

User2@contoso.com: Application error occurred. Please try again later. (CS012-002)
```

Te błędy (z kodami błędów CS001-002, CS003-002, CS008-009, CS012-002 i innymi błędami formularza CS0XX-0XX) wskazują, że wyszukiwanie zawartości nie może przeszukiwać określonych lokalizacji zawartości; W tym przykładzie nie przeszukano dwóch skrzynek pocztowych. Te błędy są wyświetlane na stronie wysuwanej szczegółów stanu wyszukiwania zawartości.

## <a name="cause-of-content-location-errors"></a>Przyczyna błędów lokalizacji zawartości

Podczas przeszukiwania dużej liczby skrzynek pocztowych wyszukiwanie jest dystrybuowane między tysiącami serwerów w centrum danych firmy Microsoft. W dowolnym momencie określone serwery mogą być w stanie ponownego uruchomienia lub w trakcie przechodzenia w tryb failover do nadmiarowych kopii. W każdym z tych przypadków przekroczą limit czasu żądania wyszukiwania zawartości dotyczące pobierania danych. W poprzednim przykładzie błędy skrzynek pocztowych, które uległy awarii, były wynikiem przesunięć limitu czasu wyszukiwania.

## <a name="resolving-content-location-errors"></a>Rozwiązywanie błędów lokalizacji zawartości

Ponowne uruchomienie wyszukiwania często powoduje podobne błędy na różnych serwerach. Zamiast ponownie uruchamiać wyszukiwanie, kliknij przycisk **Ponów próbę** wyświetlany w górnej części strony wyników wyszukiwania.

![Kliknij przycisk Ponów próbę, aby rozwiązać problemy z błędami lokalizacji zawartości.](../media/retrycontentsearch3.png)

Spowoduje to ponowienie próby wyszukiwania tylko dla skrzynek pocztowych, które nie powiodły się. Po ponowieniu próby wyszukiwania pozostałe wyniki, które zostały pomyślnie zwrócone, zostaną zachowane.

## <a name="tips-to-avoid-content-location-errors"></a>Porady dotyczące unikania błędów lokalizacji zawartości

Poniżej przedstawiono dodatkowe przyczyny błędów lokalizacji zawartości i kilka wskazówek, które pomogą Ci uniknąć ich przeszukiwania dużej liczby skrzynek pocztowych.

- Przeszukiwana skrzynka pocztowa może być zajęta z powodu aktywności użytkownika. W takim przypadku usługa wyszukiwania może ograniczyć się, aby zapobiec niedostępności skrzynki pocztowej. Aby tego uniknąć, spróbuj uruchomić wyszukiwania w godzinach innych niż godziny pracy.

- Zapytanie wyszukiwania może pobierać zbyt dużo zawartości ze skrzynki pocztowej. Jeśli to możliwe, spróbuj zawęzić zakres wyszukiwania przy użyciu słów kluczowych, zakresów dat i warunków wyszukiwania.

- Zbyt wiele słów kluczowych lub fraz kluczowych podczas tworzenia zapytania wyszukiwania przy użyciu [listy słów kluczowych](view-keyword-statistics-for-content-search.md#get-keyword-statistics-for-searches). Po uruchomieniu zapytania wyszukiwania korzystającego z listy słów kluczowych usługa zasadniczo uruchamia oddzielne wyszukiwanie każdego wiersza na liście słów kluczowych, aby można było wygenerować statystyki. Jeśli używasz listy słów kluczowych w zapytaniach wyszukiwania, zminimalizuj liczbę wierszy na liście słów kluczowych lub podziel słowa kluczowe liczby na mniejsze listy i utwórz inne wyszukiwanie dla każdej listy słów kluczowych.

  > [!NOTE]
  > Aby zmniejszyć problemy spowodowane przez duże listy słów kluczowych, możesz teraz ograniczyć do maksymalnie 20 wierszy na liście słów kluczowych zapytania wyszukiwania.

- Zbyt wiele wyszukiwań jest wykonywanych w tej samej skrzynce pocztowej w tym samym czasie. Jeśli to możliwe, spróbuj uruchomić jedno wyszukiwanie jednocześnie w jednej skrzynce pocztowej.

- Wyszukiwanie zbyt wielu skrzynek pocztowych w jednym wyszukiwaniu. Prawdopodobieństwo błędów lokalizacji zawartości zwiększa się podczas przeszukiwania dużej liczby skrzynek pocztowych. Jeśli to możliwe, spróbuj uruchomić wiele wyszukiwań, aby każde wyszukiwanie zawierało podzbiór skrzynek pocztowych w organizacji.

- Wymagana konserwacja jest wykonywana w skrzynce pocztowej. Chociaż ta przyczyna prawdopodobnie występuje rzadko, poczekaj chwilę po otrzymaniu błędu lokalizacji zawartości, a następnie ponów próbę wyszukiwania.
