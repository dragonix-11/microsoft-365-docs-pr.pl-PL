---
title: Uzyskaj pomoc techniczną dla Microsoft Managed Desktop
description: Jak użytkownicy mogą uzyskać pomoc z usługą i urządzeniami
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 48be29f8db689ddd0911d7512b267ba50c85a469
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63013778"
---
# <a name="getting-help-for-users"></a>Uzyskiwanie pomocy dla użytkowników

Jeśli osiągnięto punkt przepływu pracy, w [](../service-description/user-support.md) którym należy zażądać podwyższonych uprawnień dostępu do urządzenia lub eskalacji do firmy Microsoft, wykonaj następujące czynności:

>[!NOTE]
>Te opcje pomocy technicznej nie są dostępne dla urządzeń w grupie Testowanie.

## <a name="elevation-requests"></a>Żądania podwyższenia

Zanim poprosisz o podwyższony poziom dostępu do urządzenia, najlepiej sprawdzić, które akcje są najoceńsze.

| Akcje | Przykłady |
| ------ | ------ |
| **Typowe akcje są** przeznaczone do procesu żądania podwyższenia. Jest on wykonywany rutynowo podczas rozwiązywania problemów z Microsoft Managed Desktop urządzeniami. | <ul><li>Wykonuj wbudowane narzędzia do rozwiązywania problemów z systemem, wiersz polecenia Windows PowerShell rozwiązywanie problemów z aplikacjami biznesowymi.</li><li>Za pomocą obejścia problemu można rozwiązać problem, który powinien działać zgodnie z projektem (na przykład aktywacja funkcji BitLocker lub czas systemowy nie jest aktualizowany).</li><li>Wykonuj czynności, takie jak aktualizowanie sterowników, odinstalowywanie urządzenia lub skanowanie w poszukiwaniu nowych zmian.</li></ul>
| **Akcje, które nie są zalecane** | <ul><li>Instalowanie oprogramowania lub przeglądarek.</li><li>Instalowanie sterowników poza Windows, w tym sterowników urządzeń peryferyjnych.</li><li>Instalowanie .msi lub .exe plików.</li><li>Instalowanie Windows funkcji.</li></ul>
| **Akcje, które nie są obsługiwane** | <ul><li>Instalowanie oprogramowania lub funkcji, które są w konflikcie Microsoft Managed Desktop zabezpieczeniami lub operacjami zarządzania.</li><li>Wyłączanie funkcji Windows, która jest wymagana w celu obsługi Microsoft Managed Desktop, takiej jak funkcja BitLocker.</li><li>Modyfikowanie ustawień zarządzanych przez organizację.</li><ul>

**Aby zażądać podwyższenia:**

1. Zaloguj się [w Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Urządzenia**.
1. W sekcji **Microsoft Managed Desktop** **wybierz pozycję Urządzenia**, która zawiera dwie karty: **kartę** Urządzenia i **kartę Żądania podwyższenia**.
1. Aby utworzyć nowe żądanie podwyższenia na **karcie** Urządzenie, wybierz jedno urządzenie, które ma zostać wyniesiane.
1. Z menu rozwijanego Akcje urządzenia wybierz polecenie **Zażądaj podwyższenia**. Zostanie wyświetlone nowe przylot żądania podwyższenia z wstępnie wypełnioną nazwą urządzenia w tym polu.
1. Aby zamiast tego utworzyć nowe żądanie **podwyższenia na karcie Żądania podwyższenia** , wybierz pozycję **+Nowe żądanie podwyższenia.**
1. Podaj następujące szczegóły:
    - **Identyfikator biletu pomocy technicznej**: jest to numer z Twojego własnego systemu biletowania pomocy technicznej.
    - **Nazwa urządzenia**: Jest to możliwe tylko podczas tworzenia żądania z karty **Żądania podwyższenia** . Wprowadź numer seryjny urządzenia, a następnie wybierz urządzenie z menu.
    - **Kategoria**: Wybierz kategorię, która najlepiej odpowiada problemowi. Jeśli żadna z opcji nie wydaje się blisko, wybierz pozycję **Inne**. Jeśli to możliwe, najlepiej jest wybrać kategorię.
    - **Tytuł**: podaj krótki opis problemu na urządzeniu.
    - **Plan działania**: Opisz kroki rozwiązywania problemów, które zamierzasz wykonać po przyznaniu podwyższenia.
1. Wybierz **pozycję Prześlij**.
1. Lista i szczegóły wszystkich aktywnych i zamkniętych żądań są widoczne na karcie **Żądania podwyższenia** .

## <a name="escalation-requests"></a>Żądania eskalacji

**Aby [eskalować](../service-description/user-support.md#escalation-portal) problem do firmy Microsoft:**

1. Zaloguj się [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) i przejdź do menu **Administracja dzierżawą**.
2. W sekcji Microsoft Managed Desktop wybierz pozycję **Żądania usługi**.
3. W sekcji **Żądania obsługi** wybierz pozycję **+ Nowy wniosek o pomoc techniczną**.
4. W polu Tytuł podaj **krótki** opis. Następnie ustaw dla ustawienia **Typ żądania** wartość **Zdarzenie**.
5. Wybierz **kategorię** i **podkategorie** , które najlepiej pasują do problemu. Następnie wybierz pozycję **Dalej**.
6. W **sekcji Szczegóły** podaj następujące informacje:
    - **Opis**: Dodaj wszelkie dodatkowe szczegóły, które mogą pomóc naszemu zespołowi zrozumieć problem. Jeśli chcesz dołączyć pliki, możesz to zrobić, wracając do żądania po jego przesłaniu.
    - **Podstawowe informacje kontaktowe**: Podaj informacje o tym, jak skontaktować się z główną osobą odpowiedzialną za współpracę z naszym zespołem.
7. Wybierz **poziom ważności** . Aby uzyskać więcej informacji, zobacz [Definicje ważności wniosku o pomoc techniczną](../working-with-managed-desktop/admin-support.md#support-request-severity-definitions).
8. Podaj jak najwięcej informacji na temat wniosku, aby ułatwić zespołowi szybkie odpowiadanie. W zależności od typu żądania może być wymagane podanie różnych szczegółów.
9. Sprawdź wszystkie podane informacje pod warunkiem dokładności.
10. Gdy wszystko będzie gotowe, wybierz pozycję **Utwórz**.
