---
title: Jak ustalać priorytety, zarządzać & reagować na zdarzenia w Microsoft 365 Defender
description: Kroki zarządzania alertami wyzwalane w Microsoft 365 Defender. Zautomatyzowane badanie i reagowanie (AIR) sprawdza w całej subskrypcji oraz określa wpływ i zakres zagrożenia oraz łączy informacje w jednym zdarzeniu.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: c1a6180aac7513b2c88904a4c8fb631ba6ffd542
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842521"
---
# <a name="prioritize-manage-investigate--respond-to-incidents-in-microsoft-365-defender"></a>Określanie priorytetów, zarządzanie & reagowanie na zdarzenia w Microsoft 365 Defender

Gdy alerty są wyzwalane w Microsoft 365 Defender, automatyczne badanie i reagowanie (AIR) spowoduje wyszukiwanie w subskrypcji organizacji, określanie wpływu i zakresu zagrożenia oraz sortowanie informacji w jednym zdarzeniu, aby administratorzy nie musieli zarządzać wieloma zdarzeniami.

## <a name="what-youll-need"></a>Co będzie potrzebne

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 lub nowszy
- Wystarczające uprawnienia (czytelnik zabezpieczeń, operacje zabezpieczeń lub administrator zabezpieczeń oraz rola [wyszukiwania i przeczyszczania](../permissions-microsoft-365-security-center.md) )

## <a name="prioritize--manage-incidents"></a>Określanie priorytetów & zarządzania zdarzeniami

Przejdź do strony https://security.microsoft.com/incidentsZdarzenia w portalu zabezpieczeń.

Po załadowaniu strony Zdarzenia można filtrować i określać priorytety, klikając kolumny w celu sortowania akcji lub naciskając przycisk Filtry, aby zastosować filtr, taki jak źródło danych, tagi lub stan.

Teraz masz priorytetową listę zdarzeń, z których możesz zmienić nazwę, przypisać, sklasyfikować, oznaczyć, zmienić stan lub dodać komentarze za pomocą przycisku Zarządzaj zdarzeniami.

Użyj filtrów, aby upewnić się, że usługa Microsoft Defender dla Office elementów jest uwzględniona.

Jeśli szukasz określonych alertów, użyj funkcji wyszukiwania zdarzeń (*Wyszukaj nazwę lub identyfikator*) lub rozważ użycie filtrowania kolejki alertów dla określonego alertu.

## <a name="investigate--respond-to-incidents"></a>Badanie & reagowania na zdarzenia

Po określeniu priorytetu kolejki zdarzeń kliknij pozycję Incydent, który chcesz zbadać, aby załadować stronę Przegląd zdarzeń. Będą dostępne przydatne informacje, takie jak obserwowane *techniki CK&MITRE ATT* i *oś czasu ataku*.

Karty w górnej części strony zdarzenia umożliwiają zapoznanie się z bardziej szczegółowymi informacjami, takimi jak użytkownicy, których dotyczy problem, skrzynki pocztowe, punkty końcowe i et cetera.

Karta *Dowody i odpowiedź* pokazuje elementy zidentyfikowane jako powiązane z oryginalnym alertem za pośrednictwem badania.

Wszystkie elementy wyświetlane jako *oczekujące akcje* w obszarze Dowody i odpowiedź oczekują na zatwierdzenie przez administratora.  Zaleca się sortowanie według kolumny stan korygowania w widoku *Wszystkie dowody* , a następnie kliknięcie jednostki lub klastra w celu załadowania menu wysuwanego, w którym można następnie zatwierdzić akcje w razie potrzeby.

Jeśli musisz dokładniej zrozumieć zaangażowane elementy, możesz użyć wykresu zdarzenia, aby zobaczyć wizualne powiązanie dowodów i zaangażowanych jednostek. Alternatywnie możesz przejrzeć podstawowe badania, które pokażą więcej jednostek i elementów biorących udział w zdarzeniu zabezpieczeń.

## <a name="next-steps"></a>Następne kroki

Możesz zacząć korzystać z *Centrum akcji* , aby działać na oczekujących elementach akcji ze wszystkich zdarzeń w organizacji, jeśli chcesz skupić się na elementach akcji, dla które środowisko AIR wymaga zatwierdzenia.  

## <a name="more-information"></a>Więcej informacji

[Zarządzanie zdarzeniami w Microsoft 365 Defender | Microsoft Docs](../../defender/manage-incidents.md)

[Jak działa zautomatyzowane badanie i reagowanie w Ochrona usługi Office 365 w usłudze Microsoft Defender](../automated-investigation-response-office.md)

[Akcje korygowania w Ochrona usługi Office 365 w usłudze Microsoft Defender](../air-remediation-actions.md)