---
title: Wykluczanie urządzeń w Ochrona punktu końcowego w usłudze Microsoft Defender
description: Wykluczanie urządzeń z listy spisu urządzeń
keywords: Wykluczyć
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
ms.openlocfilehash: d97e8db205d066671b7c0d430e3dbf79f0dd6ebd
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368116"
---
# <a name="exclude-devices"></a>Wyklucz urządzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

## <a name="exclude-devices-from-vulnerability-management"></a>Wykluczanie urządzeń z zarządzanie lukami w zabezpieczeniach

Wyłączenie urządzeń, które są nieaktywne, zduplikowane lub poza zakresem, pozwala skupić się na odnajdyowaniu i określaniu priorytetów zagrożeń na aktywnych urządzeniach. Ta akcja może również pomóc odzwierciedlić dokładniejszy wynik zarządzanie lukami w zabezpieczeniach ekspozycji, ponieważ wykluczone urządzenia nie będą widoczne w raportach zarządzanie lukami w zabezpieczeniach.

Po wykluczeniu urządzeń nie będzie można wyświetlać zaktualizowanych ani istotnych informacji o lukach w zabezpieczeniach i zainstalowanym oprogramowaniu na tych urządzeniach. Ma wpływ na wszystkie zarządzanie lukami w zabezpieczeniach stron, raportów i powiązanych tabel w zaawansowanym polowaniu.

Mimo że funkcja wykluczania urządzenia usuwa dane urządzenia z zarządzanie lukami w zabezpieczeniach stron i raportów, urządzenia pozostają połączone z siecią i nadal mogą stanowić zagrożenie dla organizacji. Wykluczenie urządzenia będzie można anulować w dowolnym momencie.

## <a name="how-to-exclude-a-device"></a>Jak wykluczyć urządzenie

Jednocześnie można wykluczyć pojedyncze urządzenie lub wiele urządzeń.

### <a name="exclude-a-single-device"></a>Wykluczanie pojedynczego urządzenia

1. Przejdź do strony **Spis urządzeń** i wybierz urządzenie do wykluczenia.
2. Wybierz pozycję **Wyklucz** na pasku akcji na stronie spisu urządzeń lub z menu akcji w wysuwanym urządzeniu.

   ![Obraz przedstawiający opcję menu wykluczania urządzenia.](images/exclude-devices-menu.png)

3. Wybierz uzasadnienie:

    - Nieaktywne urządzenie
    - Zduplikowane urządzenie
    - Urządzenie nie istnieje
    - Poza zakresem
    - Inne

4. Wpisz notatkę i wybierz pozycję **Wyklucz urządzenie**.

![Obraz przedstawiający wykluczanie urządzenia.](images/exclude-device.png)

Można również wykluczyć urządzenie ze strony urządzenia.

> [!NOTE]
> Wykluczanie aktywnych urządzeń nie jest zalecane, ponieważ szczególnie ryzykowne jest brak wglądu w informacje o lukach w zabezpieczeniach. Jeśli urządzenie jest aktywne i próbujesz je wykluczyć, zostanie wyświetlony komunikat ostrzegawczy i wyskakujące okno dialogowe z potwierdzeniem z pytaniem, czy na pewno chcesz wykluczyć aktywne urządzenie.

Całkowite wykluczenie urządzenia z zarządzanie lukami w zabezpieczeniach widoków i danych może potrwać do 10 godzin.

Wykluczone urządzenia są nadal widoczne na liście Spis urządzeń. Widok wykluczonych urządzeń można zarządzać za pomocą:

- Dodawanie kolumny **Stan wykluczenia** do widoku spisu urządzeń.
- Użyj filtru **Stanu wykluczenia** , aby wyświetlić odpowiednią listę urządzeń.

![Obraz stanu wykluczenia.](images/exclusion-state.png)

### <a name="bulk-device-exclusion"></a>Zbiorcze wykluczenie urządzenia

Można również wykluczyć wiele urządzeń w tym samym czasie:

1. Przejdź do strony **Spis urządzeń** i wybierz urządzenia do wykluczenia.

2. Na pasku akcji wybierz pozycję **Wyklucz**.

3. Wybierz uzasadnienie i wybierz pozycję **Wyklucz urządzenie**.

Jeśli wybierzesz wiele urządzeń na liście urządzeń z różnymi stanami wykluczeń, wysuwane wykluczenie wybranych urządzeń będzie zawierać szczegółowe informacje na temat liczby wybranych urządzeń, które zostały już wykluczone. Można wykluczyć urządzenia ponownie, ale uzasadnienie i notatki zostaną zastąpione.

![Obraz wykluczania zbiorczego](images/exclude-device-bulk.png)

Po wykluczeniu urządzenia, jeśli przejdziesz do strony urządzenia wykluczonego urządzenia, nie będzie można wyświetlić danych dotyczących wykrytych luk w zabezpieczeniach, spisu oprogramowania ani zaleceń dotyczących zabezpieczeń. Dane nie będą również wyświetlane na stronach zarządzanie lukami w zabezpieczeniach, powiązanych zaawansowanych tabelach zagrożeń i raportach urządzeń narażonych na zagrożenia.

## <a name="stop-excluding-a-device"></a>Zatrzymywanie wykluczania urządzenia

W dowolnym momencie będzie można przestać wykluczać urządzenie. Gdy urządzenia nie zostaną już wykluczone, ich dane luk w zabezpieczeniach będą widoczne na zarządzanie lukami w zabezpieczeniach stronach, raportach i w zaawansowanym polowaniu. Wprowadzenie zmian może potrwać do 8 godzin.

1. Przejdź do spisu urządzeń, wybierz wykluczone urządzenie, aby otworzyć wysuwane urządzenie, a następnie wybierz pozycję **Szczegóły wykluczenia**
2. Wybierz pozycję **Zatrzymaj wykluczanie**

![Obraz przedstawiający szczegóły wykluczenia](images/exclusion-details.png)

## <a name="see-also"></a>Zobacz też

- [Spisz urządzeń](machines-view-overview.md)
