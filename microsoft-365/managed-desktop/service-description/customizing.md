---
title: Wyjątki od planu serwisowego
description: Jak zażądać wyjątków od standardowego planu serwisowego
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 8069a899b9992a0e8b941b6ac53cd2f230a6174a
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014762"
---
# <a name="exceptions-to-the-service-plan"></a>Wyjątki od planu serwisowego

Microsoft Managed Desktop zawiera listę urządzeń, standardowe ustawienia [urządzeń, wymagania](device-policies.md) dotyczące aplikacji i niektóre konfigurowane ustawienia zaprojektowane [](../working-with-managed-desktop/config-setting-overview.md)w celu zapewnienia użytkownikom bezpiecznego, produktywnego i przyjemniejszego środowiska pracy.

Najlepiej jest zawsze pozostać przy dostępnej usłudze. Jednak zdajemy sobie sprawę, że niektóre szczegóły usługi mogą nie dopasować się dokładnie do potrzeb Twojej organizacji. Jeśli uważasz, że chcesz w jakiś sposób zmodyfikować usługę, postępuj zgodnie z poniższymi procesami, aby zażądać tych zmian.

## <a name="types-of-exceptions"></a>Typy wyjątków

Wyjątkiem są wszelkie dodawanie lub zmienianie Microsoft Managed Desktop konfiguracji podstawowej. Przykłady to konfiguracja portów USB do wdrażania nowego sterownika urządzenia. Grupuje się różne wyjątki w następujący sposób:

| Typy wyjątków | Opis |
| ----- | ----- |
| Oprogramowanie zwiększające produktywność | Oprogramowanie pierwszego planu wymagane przez użytkowników, ograniczone wymaganiami [aplikacji](mmd-app-requirements.md). |
| Agenci zabezpieczeń & sieci VPN | Oprogramowanie służące do zabezpieczania, monitorowania lub zmieniania zachowania urządzenia lub sieci. |
| Monitorowanie środowiska cyfrowego | Oprogramowanie używane do śledzenia danych na urządzeniu użytkownika w celu zgłoszenia go do IT. |
| Sterowniki sprzętu lub oprogramowania | Sterowniki urządzeń ograniczone wymaganiami [aplikacji](mmd-app-requirements.md). |
| Policies (zasady) | Windows 10 lub Aplikacje Microsoft 365 dla przedsiębiorstw na urządzeniu zarządzanym. |
| Urządzenia | Urządzenia, których nie ma na Microsoft Managed Desktop [urządzenia.](device-list.md) |
| Inne | Wszystko, co nie jest objęte innymi obszarami. |

## <a name="request-an-exception"></a>Żądanie wyjątku

Żądania można przesyłać za pośrednictwem Microsoft Managed Desktop administracyjnego przez utworzenie żądania zmiany. Pamiętaj, aby uwzględnić następujące informacje:

| Szczegóły żądania zmiany | Opis |
| ----- | ----- |
| Typ zwolnienia | Jakiego typu wyjątek istnieje? (zobacz [poprzednią tabelę](#types-of-exceptions)) |
| Wymaganie | Jakie jest konkretne wymaganie biznesowe dla wyjątku? |
| Propozycja | Które rozwiązanie jest żądaniem Twojej firmy? |
| Oś czasu | Jak długo ma trwać ten wyjątek? |

## <a name="how-we-assess-an-exception-request"></a>Jak oceniamy żądanie wyjątku

Przeglądając żądania wyjątków, oceniamy te czynniki w następującej kolejności:

1. Niektóre aplikacje i zasady, Microsoft Managed Desktop wdrażane na wszystkich urządzeniach nie mogą być ekwowalne. Twoje żądanie nie może mieć wpływu na te aplikacje ani zasady. Aby uzyskać więcej informacji, zobacz [Konfiguracja urządzenia](device-policies.md).
2. Ograniczone oprogramowanie zwiększające produktywność wymagane przez użytkownika do jego pracy prawdopodobnie zostanie zatwierdzone.
3. Jeśli możemy spełnić Twoje wymagania przy użyciu technologii firmy Microsoft, prawdopodobnie zatwierdzimy Twoje żądanie w przypadku okresu migracji wyjątku, który wynosi od trzech do 12 miesięcy. Okres migracji zależy od zakresu projektu.
4. Jeśli nie będziemy w stanie spełnić Twoich wymagań przy użyciu technologii firmy Microsoft, prawdopodobnie zatwierdzimy Twoje żądanie, chyba że narusza ono jeden z [warunków kluczowych](#key-conditions).  

Te zasady zapewniają, Microsoft Managed Desktop mogą zawsze spełniać Twoje potrzeby, śledząc odchylenia od naszego szablonu standardowego.

## <a name="key-conditions"></a>Najważniejsze warunki

Przeglądamy wyjątki, aby upewnić się, że nie naruszają one żadnego z tych warunków:

- Wyjątek nie może mieć negatywnego wpływu na bezpieczeństwo systemu.
- Utrzymywanie wyjątku nie musi wiązać się z istotnymi kosztami Microsoft Managed Desktop operacji lub pomocy technicznej.
- Wyjątkiem nie może być stabilność systemu, na przykład powoduje awarię lub zawieszanie się trybu kernela.
- Ta zmiana nie może nas ograniczać możliwości obsługi usługi ani być w konflikcie z podstawową Microsoft Managed Desktop technologii.
- Wyjątkiem nie może być personalizowanie interfejsu użytkownika, na przykład zmiana menu Start lub Pasek zadań.

Te warunki mogą się zmienić w przyszłości. Jeśli dokonamy takich zmian, otrzymasz powiadomienie 30 dni przed tymi warunkami, które zostaną wprowadzone.  Jeśli Microsoft Managed Desktop alternatywny sposób spełnienia zatwierdzonego wyjątku, Microsoft Managed Desktop powiadomi klienta o Microsoft Managed Desktop zmianie sposobu, w jaki ten wyjątek obsługuje.

## <a name="revoking-approval-for-an-exception"></a>Odwoływanie zatwierdzenia wyjątku

Po zatwierdzeniu i wdrożeniu żądanego wyjątku możemy wykryć problemy, które mogłyby naruszyć najważniejsze warunki, które nie mogły zostać dowiedzone po zatwierdzeniu zmiany w pierwszej kolejności. W takiej sytuacji może być konieczne cofnięcie zatwierdzenia dla wyjątku.

Jeśli cofniemy zatwierdzenie wyjątku, powiadomimy Cię za pośrednictwem Microsoft Managed Desktop administracyjnego. Od pierwszego powiadomienia użytkownik ma 90 dni na usunięcie wyjątku, zanim urządzenia z wyjątkiem nie będą już powiązane Microsoft Managed Desktop umowami poziomu usług.

Wyślemy Ci kilka powiadomień zgodnie z rygorystyczną osią czasu. Jednak poważne zdarzenie lub zagrożenie może wymagać od nas zmiany osi czasu decyzji dotyczących wyjątku. Nie usuniemy *wyjątku* bez Twojej zgody. Jednak każde urządzenie z cofniętym wyjątkiem nie będzie już powiązane umową na poziomie usługi. W poniższej tabeli przedstawiono oś czasu powiadomień, które będziemy Ci wysyłać:

| Typ powiadomienia | Opis |
| ----- | ----- |
| Pierwsze powiadomienie | W pierwszej informacji podano następujące informacje: <ul><li>Informacje o tym, dlaczego je odwołaliśmy.</li><li>Zaleca się działanie, które należy podjąć.</li><li>Termin wykonania tych działań.</li><Li>Kroki, które należy wykonać, jeśli chcesz odwołać się do decyzji.</li></ul> <br>To powiadomienie jest wcześniejsze 90 dni przed usunięciem wyjątku ze wszystkich urządzeń. |
| Drugie powiadomienie (30 dni później) | Dostarczamy drugie powiadomienie, z uwzględnieniem tych samych informacji podanych w pierwszym zawiadomieniu. |
| Trzecie powiadomienie (60 dni od pierwszego powiadomienia) | Dostarczamy trzecie powiadomienie z uwzględnieniem tych samych informacji podanych w pierwszej informacji. |
| Powiadomienie końcowe (tydzień przed upływem 90-dniowego terminu ostatecznego) | Dostarczamy czwarte powiadomienie z uwzględnieniem tych samych informacji podanych w pierwszym zawiadomieniu. |
| 90 dni od pierwszego powiadomienia| Microsoft Managed Desktop poziomu usług nie mają już zastosowania do żadnych urządzeń, dla których odwoływniętą wyjątek. W każdej chwili możesz podyskarć decyzję i podać dodatkowe informacje do rozważenia, w tym uaktualnianie, zmiany w konfiguracji lub zmiany oprogramowania. |
