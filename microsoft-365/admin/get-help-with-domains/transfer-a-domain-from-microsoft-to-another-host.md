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
description: 'Poniżej przedstawiono kroki przenoszenia domeny z firmy Microsoft do innego rejestratora. '
ms.openlocfilehash: 18f2b6502268b757b651abe08585cc06b63d7129
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782484"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Przenoszenie domeny z firmy Microsoft do innego hosta

Nie można przenieść domeny Microsoft 365 do innego rejestratora przez 60 dni po zakupie domeny od firmy Microsoft.

> [!NOTE]
> Zapytanie _Whois_ pokazuje rejestratora domen zakupionych przez firmę Microsoft jako Wild West Domains LLC. Należy jednak skontaktować się tylko z firmą Microsoft w sprawie twojej Microsoft 365 zakupionej domeny.

Wykonaj następujące kroki, aby uzyskać kod w Microsoft 365, a następnie przejdź do innej witryny internetowej rejestratora domen, aby skonfigurować przenoszenie nazwy domeny do nowego rejestratora.

## <a name="transfer-a-domain"></a>Przenoszenie domeny

1. W centrum administracyjnym przejdź do **obszaru Ustawienia** \> **Domeny**.

2. Na stronie **Domeny** wybierz domenę Microsoft 365, którą chcesz przenieść do innego rejestratora domeny, a następnie wybierz pozycję **Sprawdź kondycję**.

3. W górnej części strony wybierz pozycję **Przenieś domenę**.

4. Na stronie **Wybierz miejsce przeniesienia domeny** wybierz pozycję **Inny rejestrator**, a następnie kliknij przycisk **Dalej**.

5. Na stronie **Odblokuj transfer domeny** wybierz pozycję **Odblokuj transfer dla <_swojej domeny_>**, a następnie wybierz pozycję **Dalej**.

6. Sprawdź informacje kontaktowe dotyczące transferu domeny, a następnie wybierz pozycję **Dalej**.

7. Skopiuj kod autoryzacji i poczekaj około 30 minut, aż stan transferu domeny zmieni się **na Odblokowano** w celu przeniesienia na karcie **Rejestracja** , zanim przejdziesz do następnych kroków.

8. Przejdź do witryny internetowej rejestratora domen, który chcesz zarządzać nazwą domeny w przyszłości. Postępuj zgodnie z instrukcjami dotyczącymi przenoszenia domeny (wyszukaj pomoc w witrynie internetowej). Zwykle oznacza to uiszczanie opłat za transfer i przekazanie Authcode nowemu rejestratorowi, aby mógł zainicjować przeniesienie. Firma Microsoft wyśle Ci wiadomość e-mail z potwierdzeniem, że otrzymaliśmy żądanie przeniesienia, a domena zostanie przesłana w ciągu 5 dni.

    Kartę **Rejestracja** kodu autoryzacji można znaleźć na stronie **Domeny** w Microsoft 365.

    > [!TIP]
    > Domeny .uk wymagają innej procedury. Skontaktuj się z pomoc techniczna firmy Microsoft i poproś o **zmianę tagu IPS**, aby dopasować rejestratora, który chcesz zarządzać domeną w przyszłości. Po zmianie tagu domena natychmiast przenosi się do nowego rejestratora. Następnie będziesz musiał współpracować z nowym rejestratorem, aby ukończyć transfer, prawdopodobnie uiszczając opłaty za transfer i dodając przeniesioną domenę do konta u nowego rejestratora.

9. Po zakończeniu przenoszenia Twoja domena zostanie odnowiona u nowego rejestratora domen.

10. Aby zakończyć proces, wróć do strony **Domeny** w centrum administracyjnym, a następnie wybierz pozycję **Zakończ transfer domeny**. Spowoduje to oznaczenie domeny jako niezakupionej od Microsoft 365 i spowoduje wyłączenie subskrypcji domeny. Nie usunie ona domeny z dzierżawy i nie wpłynie na istniejących użytkowników i skrzynki pocztowe w domenie.

> [!NOTE]
> Microsoft 365 zakupione domeny nie kwalifikują się do zmian w programie nameserver ani do przenoszenia domeny między Microsoft 365 organizacjami. Jeśli któryś z tych elementów jest wymagany, rejestracja domeny musi zostać przeniesiona do innego rejestratora.
