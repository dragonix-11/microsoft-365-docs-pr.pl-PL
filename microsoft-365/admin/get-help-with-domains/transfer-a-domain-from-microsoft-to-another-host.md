---
title: Przenoszenie domeny z firmy Microsoft do innego hosta
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: 'W tym miejscu znajdziesz czynności, które należy wykonać, aby przenieść domenę z firmy Microsoft do innego rejestratora. '
ms.openlocfilehash: 192e9c1e14666f80fb670c5c8e268ae54ece0c64
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316775"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Przenoszenie domeny z firmy Microsoft do innego hosta

Nie można przenieść domeny Microsoft 365 do innego rejestratora przez 60 dni od zakupu domeny od firmy Microsoft.

> [!NOTE]
> Zapytanie _Whoisquery_  wyświetla rejestratora domen zakupionych przez firmę Microsoft jako wild west domains LLC. Jednak w związku z tym należy kontaktować się tylko z firmą Microsoft w Microsoft 365 zakupioną domeną.

Wykonaj poniższe czynności, aby uzyskać kod w witrynie Microsoft 365, a następnie przejdź do witryny internetowej innego rejestratora domen, aby skonfigurować przeniesienie nazwy domeny do nowego rejestratora.

## <a name="transfer-a-domain"></a>Przenoszenie domeny

1. W centrum administracyjnym przejdź do pozycji   **Ustawienia** >  **Domains**.

2. Na stronie **Domeny** wybierz domenę, Microsoft 365 chcesz przenieść do innego rejestratora domen, a następnie wybierz **pozycję Sprawdź kondycję**.

3. U góry strony wybierz pozycję **Przenieś domenę**.

4. Na **stronie Wybierz, gdzie chcesz przenieść domenę** wybierz **pozycję Inny rejestrator, a** następnie kliknij przycisk **Dalej**.

5. Na stronie **Odblokowywanie przenoszenia domeny** wybierz pozycję **Odblokuj transfer dla <_domeny_>**, a następnie wybierz przycisk **Dalej**.

6. Sprawdź informacje kontaktowe dotyczące przenoszenia domeny, a następnie wybierz pozycję **Dalej**.

7. Skopiuj kod autoryzacji i poczekaj około 30 minut na zmianę stanu przenoszenia domeny na Odblokowany w celu **przeniesienia** na karcie **Rejestracja** przed kontynuowaniem następnych kroków.

8. Przejdź do witryny internetowej rejestratora domen, którego nazwą domeny chcesz zarządzać w przyszłości. Postępuj zgodnie z instrukcjami przenoszenia domeny (wyszukaj pomoc w witrynie internetowej tej domeny). Zazwyczaj oznacza to opłaty za przeniesienie i przekazywanie kodu uwierzytelniania noweowi rejestratorowi, aby ten rejestrator może zainicjować przeniesienie. Firma Microsoft otrzyma wiadomość e-mail z potwierdzeniem otrzymania żądania przeniesienia, a domena zostanie przekierowyna w ciągu 5 dni.

    Kartę Autoryzacja **kodu można** znaleźć na stronie  **Domeny** w Microsoft 365.
    
    > [!TIP]
    > Domeny uk wymagają innej procedury. Skontaktuj się z pomocą techniczną firmy Microsoft i poproś o zmianę **tagu protokołu IPS** , aby dopasować rejestratora, który będzie zarządzał Twoją domeną w przyszłości. Po zmianie tagu domena zostanie natychmiast przekierowyna do nowego rejestratora. Następnie musisz współpracować z nowym rejestratorem, aby dokończyć transfer, prawdopodobnie naliczając opłaty za transfer i dodając przetransferowana domenę do swojego konta u nowego rejestratora.

9. Po zakończeniu przenoszenia Twoja domena zostanie odnowiona u nowego rejestratora domen.

10. Aby zakończyć ten proces, wróć na stronę **Domeny** w centrum administracyjnym, a następnie wybierz pozycję Zakończ   **przenoszenie domeny**. Spowoduje to oznaczenie domeny jako już nie kupowane od Microsoft 365 i wyłączenie subskrypcji domeny. Nie spowoduje to usunięcia domeny z dzierżawy i nie wpłynie na istniejących użytkowników i skrzynek pocztowych w tej domenie.

> [!NOTE]
> Microsoft 365 domen nie są uprawnione do zmiany serwera nazw ani do przenoszenia domeny między Microsoft 365 organizacjami. Jeśli którekolwiek z tych składników jest wymagane, rejestracja domeny musi zostać przeniesiona do innego rejestratora.
