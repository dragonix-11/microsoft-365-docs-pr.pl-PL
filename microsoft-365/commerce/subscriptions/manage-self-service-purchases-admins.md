---
title: Zarządzanie zakupami samoobsługi (administratorzy)
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
description: Administratorzy mogą dowiedzieć się, jak zarządzać zakupami samoobsługi dokonanmi przez użytkowników w ich organizacji.
ms.date: 03/26/2021
ms.openlocfilehash: 19f276107de7b1dd1053e500d249950a8700ac41
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319731"
---
# <a name="manage-self-service-purchases-admin"></a>Zarządzanie zakupami samoobsługi (administrator)

Jako administrator możesz widzieć zakupy samoobsługowe dokonywane przez osoby w Twojej organizacji. Dla każdego zakupu samoobsługowego zobaczysz nazwę produktu, imię i nazwisko nabywcy, zakupione subskrypcje, datę wygaśnięcia, cenę zakupu i przypisano użytkowników. Jeśli jest to wymagane przez Twoją organizację, możesz wyłączyć samoobsługowe zakupy według produktów za pomocą programu PowerShell. Masz te same zasady zarządzania danymi i dostępu do produktów kupionych w ramach zakupu samoobsługowego lub centralnie.

Możesz także kontrolować, czy użytkownicy w organizacji mogą kupować samodzielnie. Aby uzyskać więcej informacji, [zobacz Korzystanie z usługi AllowSelfServicePurchase dla modułu MS Commerce PowerShell](allowselfservicepurchase-powershell.md).

## <a name="view-self-service-subscriptions"></a>Wyświetlanie subskrypcji samoobsługowych

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">z produktami</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">z produktami</a> .
::: moniker-end

2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Samoobsługowa**.
3. Aby wyświetlić więcej szczegółów dotyczących subskrypcji, wybierz jedną z listy.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Wyświetlanie, kto ma licencje na subskrypcję zakupu samoobsługowego

> [!NOTE]
> Jako administrator nie możesz przypisywać ani anulować przypisania licencji na subskrypcję zakupu samoobsługowego zakupową zakupioną przez użytkownika w Organizacji. Możesz [przejąć subskrypcję zakupu samoobsługowego, a](#take-over-a-self-service-purchase-subscription) następnie przypisać lub anulować przypisanie licencji.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź **do strony** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

::: moniker range="o365-21vianet"

 1. W centrum administracyjnym przejdź **do strony** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licencje rozliczeniowe</a> .

::: moniker-end

2. Wybierz ikonę filtru, a następnie wybierz **pozycję Samoobsługowa**.
3. Wybierz produkt, aby wyświetlić licencje przypisane do osób.
    > [!NOTE]
    > Jeśli dla danego produktu istnieje wiele zakupów, ten produkt jest wymieniony tylko raz, a kolumna Dostępna  ilość zawiera sumę wszystkich subskrypcji zakupionych dla tego produktu.
4. Lista **Użytkownicy** jest pogrupowana według nazwisk osób, które dokonały zakupów samoobsługowych.
5. Aby wyeksportować listę użytkowników z licencjami dla tych subskrypcji, wybierz subskrypcje, które chcesz wyeksportować, a następnie wybierz pozycję **Eksportuj użytkowników**.

## <a name="disable-or-enable-self-service-purchases"></a>Wyłączanie lub włączanie zakupów samoobsługowych

Możesz wyłączyć lub włączyć zakupy samoobsługowe dla użytkowników w organizacji. Moduł **MS Commerce** PowerShell zawiera wartość parametru **PolicyID** dla parametru **AllowSelfServicePurchase** , która pozwala kontrolować, czy użytkownicy w organizacji mogą kupować samodzielnie i dla jakich produktów.

Moduł **MS Commerce** PowerShell umożliwia:

- Wyświetlanie domyślnego stanu wartości parametru **AllowSelfServicePurchase** — włączonej lub wyłączonej przez produkt
- Wyświetlanie listy produktów, które mają zastosowanie, i tego, czy zakup samoobsługowy został włączony, czy wyłączony
- Wyświetlanie lub modyfikowanie bieżącego ustawienia konkretnego produktu w celu jego włączenia lub wyłączenia

Aby uzyskać więcej informacji, [zobacz Korzystanie z usługi AllowSelfServicePurchase dla modułu MS Commerce PowerShell](allowselfservicepurchase-powershell.md).

## <a name="centralize-licenses-under-a-single-subscription"></a>Scentralizowane licencje w ramach jednej subskrypcji

Użytkownik może przypisać istniejące licencje lub kupić dodatkowe subskrypcje w ramach istniejących umów dla użytkowników przypisanych do zakupów samoobsługowych. Po przypisaniu tych centralnie zakupionych licencji możesz zażądać, aby nabywcy anulowali swoje istniejące subskrypcje.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Zakup** > <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">usług rozliczeniowych</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">administracyjnym</a> przejdź **do strony** Zakup > **usług rozliczeniowych** .

::: moniker-end

2. Znajdź i wybierz produkt, który chcesz kupić, a następnie wybierz pozycję **Kup**.
3. Wykonaj pozostałe czynności, aby ukończyć zakup.
4. Aby wyeksportować listę użytkowników [do](#view-who-has-licenses-for-a-self-service-purchase-subscription) odwołania w następnym kroku, wykonaj czynności opisane w tece Wyświetlanie, kto ma licencje na kupioną subskrypcję samoobsługową.
5. Przypisz licencje do wszystkich osób, które mają licencje w drugiej subskrypcji. Aby uzyskać pełne instrukcje, [zobacz Przypisywanie licencji użytkownikom](../../admin/manage/assign-licenses-to-users.md).
6. Skontaktuj się z osobą, która kupiła subskrypcję zakupu samoobsługowego, i poproś ją o [jej anulowanie](manage-self-service-purchases-users.md#cancel-a-subscription).

## <a name="take-over-a-self-service-purchase-subscription"></a>Przejmij subskrypcję zakupu samoobsługowego

Możesz przejąć subskrypcję zakupu samoobsługowego dokonaną przez użytkownika w Twojej organizacji. Gdy przejmiesz subskrypcję zakupu samoobsługowego, masz dwie opcje:

1. Przenieś użytkowników do innej subskrypcji i anuluj pierwotną subskrypcję.
2. Anulowanie subskrypcji zakupu samoobsługowego i usuwanie licencji przypisanych użytkownikom.

### <a name="move-users-to-a-different-subscription"></a>Przenoszenie użytkowników do innej subskrypcji

Przeniesienie użytkowników do innej subskrypcji spowoduje automatyczne anulowanie starej subskrypcji. Użytkownik, który pierwotnie kupił subskrypcję zakupu samoobsługowego, otrzyma wiadomość e-mail z komunikatem o anulowaniu subskrypcji.

> [!NOTE]
> Musisz mieć dostępną licencję dla każdego użytkownika, do których przenosisz w ramach subskrypcji, do których przenosisz użytkowników.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">z produktami</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">administracyjnym</a> przejdź do strony **Rozliczenia** > **z produktami** .

::: moniker-end

2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Samoobsługowa**.
3. Wybierz subskrypcję, którą chcesz przejąć.
4. Na stronie szczegółów subskrypcji w sekcji **Subskrypcje i ustawienia** wybierz pozycję **Przejmij kontrolę nad tą subskrypcją**.
5. W prawym okienku wybierz pozycję **Przenieś użytkowników**.
6. Wybierz produkt, do którego chcesz przenieść użytkowników, a następnie wybierz pozycję **Przenieś użytkowników**.
7. W **polu Przenieś użytkowników do** wybierz pozycję **Przenieś użytkowników**. Proces przenoszenia może potrwać kilka minut. Nie zamykaj przeglądarki w trakcie tego procesu.
8. Po zakończeniu procesu przenoszenia zamknij **okienko Przenoszenie ukończone**.
9. Na stronie szczegółów subskrypcji stan **subskrypcji** dla subskrypcji kupionej samodzielnie jest przedstawiany jako **Usunięte**.

### <a name="cancel-a-self-service-purchase-subscription"></a>Anulowanie subskrypcji zakupu samoobsługowego

Po anulowaniu subskrypcji zakupu samoobsługowego użytkownicy z licencjami utracą dostęp do produktu. Użytkownik, który pierwotnie kupił subskrypcję zakupu samoobsługowego, otrzyma wiadomość e-mail z komunikatem o anulowaniu subskrypcji.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">z produktami</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">administracyjnym</a> przejdź do strony **Rozliczenia** > **z produktami** .

::: moniker-end

2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Samoobsługowa**.
3. Wybierz subskrypcję, którą chcesz anulować.
4. Na stronie szczegółów subskrypcji w sekcji **Subskrypcje i ustawienia** wybierz pozycję **Przejmij kontrolę nad tą subskrypcją**.
5. W prawym okienku wybierz pozycję **Anuluj subskrypcję**.
6. Wybierz przyczynę anulowania z listy rozwijanej, a następnie wybierz pozycję **Anuluj subskrypcję**.
7. W **polu Czy na pewno chcesz anulować?** wybierz pozycję **Anuluj subskrypcję**.
8. Zamykanie prawego okienka.
9. Na stronie szczegółów subskrypcji stan Subskrypcja **jest** przedstawiany jako **Usunięte**.

## <a name="need-help-contact-us"></a>Potrzebujesz pomocy? Skontaktuj się z nami.

Aby uzyskać często zadawane pytania na temat zakupów samoobsługowych, zobacz [Często zadawane pytania dotyczące zakupów samoobsługowych](self-service-purchase-faq.yml).

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej zakupów samoobsługowych, skontaktuj się [z pomocą techniczną](../../admin/get-help-support.md).
