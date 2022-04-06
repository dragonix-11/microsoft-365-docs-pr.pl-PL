---
title: Wykluczanie urządzeń w programie Microsoft Defender for Endpoint
description: Wykluczanie urządzeń z listy zasobów w spisie urządzeń
keywords: wykluczanie
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c17bea7b6a3decdb1cf20f21067c316366c2afed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705070"
---
# <a name="exclude-devices"></a>Wyklucz urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

## <a name="exclude-devices-from-threat-and-vulnerability-management"></a>Wykluczanie urządzeń z Zarządzanie zagrożeniami i lukami

Wykluczanie urządzeń, które są nieaktywne, zduplikowane lub znajdują się poza zakresem, umożliwia skoncentrowanie się na odnajdowanie zagrożeń i ustalanie ich priorytetów na aktywnych urządzeniach. To działanie może także pomóc odzwierciedlić bardziej dokładną Zarządzanie zagrożeniami i lukami wyników ekspozycji, ponieważ urządzenia wykluczone nie będą widoczne w Twoich Zarządzanie zagrożeniami i lukami raportach.

Po wykluczenia urządzeń nie będzie można wyświetlać zaktualizowanych ani odpowiednich informacji dotyczących luk i zainstalowanych na nich oprogramowania. Wpływa on na wszystkie Zarządzanie zagrożeniami i lukami, raporty i powiązane tabele podczas zaawansowanego wyszukiwania.

Mimo że funkcja wykluczenia urządzenia usuwa dane urządzenia ze stron zarządzanie lukami w zabezpieczeniach i raportów, urządzenia pozostają połączone z siecią i nadal mogą stanowić zagrożenie dla organizacji. W każdej chwili będzie można anulować wykluczenie urządzenia.

## <a name="how-to-exclude-a-device"></a>Jak wykluczyć urządzenie

Możesz wykluczyć jedno lub wiele urządzeń jednocześnie.

### <a name="exclude-a-single-device"></a>Wykluczanie jednego urządzenia

1. Przejdź na stronę **Spis urządzeń** i wybierz urządzenie, które chcesz wykluczyć.
2. Wybierz **pozycję** Wyklucz na pasku akcji na stronie spisu urządzeń lub z menu akcji w wysuwanych urządzeniach.

![Obraz opcji menu Wyklucz urządzenie.](images/exclude-devices-menu.png)

 3. Wybierz uzasadnienie:

    - Nieaktywne urządzenie
    - Duplikowanie urządzenia
    - Urządzenie nie istnieje
    - Poza zakresem  
    - Inne

4. Wpisz notatkę i wybierz pozycję **Wyklucz urządzenie**.

![Obraz wykluczającego urządzenia.](images/exclude-device.png)

Możesz również wykluczyć urządzenie z jego strony urządzenia.

> [!NOTE]
> Wykluczanie aktywnych urządzeń nie jest zalecane, ponieważ szczególnie ryzykowne jest nieoekronowanie ich informacji o luki w zabezpieczeniach. Jeśli urządzenie jest aktywne i spróbujesz je wykluczyć, zostanie wyświetlony komunikat ostrzegawczy i okno podręczne potwierdzenia z pytaniem, czy na pewno chcesz wykluczyć aktywne urządzenie.

Pełne wykluczenie urządzenia z zarządzanie lukami w zabezpieczeniach i danych może potrwać do 10 godzin.

Urządzenia wykluczonych są nadal widoczne na liście w spisie urządzeń. Do zarządzania widokiem urządzeń wykluczonych możesz użyć:

- Dodanie **kolumny Stan wykluczeń** do widoku spisu urządzeń.
- Wyświetlanie  **odpowiedniej listy urządzeń za pomocą filtru** województwoWysyłki .

![Obraz stanu wykluczenia.](images/exclusion-state.png)

### <a name="bulk-device-exclusion"></a>Zbiorcze wykluczenie urządzeń

Możesz także wykluczyć wiele urządzeń jednocześnie:

1. Przejdź do strony **Spis urządzeń** i wybierz urządzenia, które chcesz wykluczyć.

2. Na pasku akcji wybierz pozycję **Wyklucz**.

3. Wybierz uzasadnienie, a następnie wybierz **pozycję Wyklucz urządzenie**.

Jeśli wybierzesz wiele urządzeń na liście urządzeń z różnymi stanami wykluczeń, wysuw wybrane urządzenia zostaną wyświetlona informacja o tym, ile z wybranych urządzeń zostało już wykluczonych. Możesz ponownie wykluczyć urządzenia, ale uzasadnienie i notatki zostaną zastąpione.

![Obraz wykluczania zbiorczego](images/exclude-device-bulk.png)

Gdy urządzenie zostanie wykluczony, po dojściu do strony urządzenia wykluczonym urządzeniu nie będzie można wyświetlić danych dotyczących wykrytych luk w zabezpieczeniach, spisu oprogramowania ani zaleceń dotyczących zabezpieczeń. Dane nie będą też wyświetlane na stronach zarządzanie lukami w zabezpieczeniach, powiązanych zaawansowanych tabelach myśliwnych i raporcie urządzeń narażonych na zagrożenia.

## <a name="stop-excluding-a-device"></a>Zatrzymywanie wykluczania urządzenia

W każdej chwili możesz przestać wykluczać urządzenie. Gdy urządzenia nie zostaną już wykluczone, ich dane luk będą widoczne na zarządzanie lukami w zabezpieczeniach, raportach i w zaawansowanym szukaniu. Może upłynieć do 8 godzin, aż zmiany zajdą w życie.

1. Przejdź do spisu urządzeń, wybierz urządzenie wykluczonych, aby otworzyć wysuwne menu, a następnie wybierz pozycję **Szczegóły wykluczenia**
2. Wybierz pozycję **Zatrzymaj wykluczenie**

![Obraz szczegółów wykluczenia](images/exclusion-details.png)

## <a name="see-also"></a>Zobacz też

- [Spis urządzeń](machines-view-overview.md)
