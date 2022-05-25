---
title: Zarządzanie zakupami samoobsługowymi (administratorzy)
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: prlachhw, pablom
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
description: Administratorzy mogą dowiedzieć się, jak zarządzać zakupami samoobsługowymi dokonanymi przez użytkowników w organizacji.
ms.date: 05/24/2022
ms.openlocfilehash: 50d782052839c099f3c64e45cc82a6f2ae5ba853
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663519"
---
# <a name="manage-self-service-purchases-admin"></a>Zarządzanie zakupami samoobsługowymi (Administracja)

Jako administrator możesz zobaczyć zakupy samoobsługowe dokonywane przez osoby w organizacji. Zobaczysz nazwę produktu, nazwę nabywcy, zakupione subskrypcje, datę wygaśnięcia, cenę zakupu i przypisanych użytkowników dla każdego zakupu samoobsługowego. Jeśli jest to wymagane przez organizację, możesz wyłączyć samoobsługowe zakupy dla każdego produktu za pośrednictwem programu PowerShell. Masz te same zasady zarządzania danymi i dostępu do produktów zakupionych w ramach samoobsługowego zakupu lub centralnie.

Możesz również kontrolować, czy użytkownicy w organizacji mogą dokonywać zakupów samoobsługowych. Aby uzyskać więcej informacji, zobacz [Use AllowSelfServicePurchase for the MSCommerce PowerShell module (Używanie elementu AllowSelfServicePurchase dla modułu MSCommerce programu PowerShell](allowselfservicepurchase-powershell.md)).

## <a name="view-self-service-subscriptions"></a>Wyświetlanie subskrypcji samoobsługowych

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Twoje produkty</a>.
::: moniker-end

2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Samoobsługowe**.
3. Aby wyświetlić więcej szczegółów dotyczących subskrypcji, wybierz jedną z listy.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Wyświetlanie, kto ma licencje na subskrypcję zakupu samoobsługowego

> [!NOTE]
> Jako administrator nie możesz przypisywać ani anulować przypisywania licencji dla subskrypcji zakupu samoobsługowego zakupionej przez użytkownika w organizacji. Możesz [przejąć subskrypcję samoobsługowego zakupu](#take-over-a-self-service-purchase-subscription), a następnie przypisać lub cofnąć przypisanie licencji.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**>.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

 1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Wybierz ikonę filtru, a następnie wybierz pozycję **Samoobsługowe**.
3. Wybierz produkt, aby wyświetlić licencje przypisane do osób.
    > [!NOTE]
    > Jeśli istnieje wiele zakupów dla produktu, ten produkt jest wyświetlany tylko raz, a kolumna **Dostępna ilość** zawiera sumę wszystkich subskrypcji zakupionych dla tego produktu.
4. Lista **Użytkownicy** jest pogrupowana według nazw osób, które dokonały zakupów samoobsługowych.
5. Aby wyeksportować listę użytkowników z licencjami dla tych subskrypcji, wybierz subskrypcje, które chcesz wyeksportować, a następnie wybierz pozycję **Eksportuj użytkowników**.

## <a name="disable-or-enable-self-service-purchases"></a>Wyłączanie lub włączanie zakupów samoobsługowych

Możesz wyłączyć lub włączyć zakupy samoobsługowe dla użytkowników w organizacji. Moduł **MSCommerce** Programu PowerShell zawiera wartość parametru **PolicyID** dla **elementu AllowSelfServicePurchase** , która umożliwia kontrolowanie, czy użytkownicy w organizacji mogą dokonywać zakupów samoobsługowych i dla których produktów.

Moduł **MSCommerce** PowerShell umożliwia:

- Wyświetl domyślny stan wartości parametru **AllowSelfServicePurchase** — niezależnie od tego, czy jest ona włączona, czy wyłączona przez produkt
- Wyświetl listę odpowiednich produktów oraz informacje o tym, czy zakup samoobsługowy jest włączony, czy wyłączony
- Wyświetl lub zmodyfikuj bieżące ustawienie dla określonego produktu, aby je włączyć lub wyłączyć

> [!IMPORTANT]
> Użycie zasad **AllowSelfServicePurchase** powoduje włączenie lub wyłączenie zarówno zakupów samoobsługowych, jak i samoobsługowych wersji próbnych. Aby uzyskać listę produktów dostępnych do zakupu samoobsługowego, zobacz [Wyświetlanie listy produktów samoobsługowych i ich stanu](allowselfservicepurchase-powershell.md#view-a-list-of-self-service-purchase-products-and-their-status). Tylko Project i Visio są dostępne dla subskrypcji wersji próbnej.

Aby uzyskać więcej informacji, zobacz [Use AllowSelfServicePurchase for the MSCommerce PowerShell module (Używanie elementu AllowSelfServicePurchase dla modułu MSCommerce programu PowerShell](allowselfservicepurchase-powershell.md)).

## <a name="centralize-licenses-under-a-single-subscription"></a>Scentralizacja licencji w ramach jednej subskrypcji

Możesz przypisać istniejące licencje lub kupić dodatkowe subskrypcje za pośrednictwem istniejących umów dla użytkowników przypisanych do zakupów samoobsługowych. Po przypisaniu tych licencji zakupionych centralnie można zażądać, aby nabywcy anulowali istniejące subskrypcje.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Usługi zakupu</a> **rozliczeń**>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centrum administracyjnym</a> przejdź do strony **Usługi zakupu rozliczeń**  >.

::: moniker-end

2. Znajdź i wybierz produkt, który chcesz kupić, a następnie wybierz pozycję **Kup**.
3. Wykonaj pozostałe kroki, aby ukończyć zakup.
4. Wykonaj kroki opisane w [temacie Wyświetlanie, kto ma licencje na subskrypcję zakupioną przez samoobsługę](#view-who-has-licenses-for-a-self-service-purchase-subscription) , aby wyeksportować listę użytkowników do odwołania w następnym kroku.
5. Przypisz licencje wszystkim, którzy mają licencję w innej subskrypcji. Aby uzyskać pełne kroki, zobacz [Przypisywanie licencji użytkownikom](../../admin/manage/assign-licenses-to-users.md).
6. Skontaktuj się z osobą, która kupiła subskrypcję samoobsługowego zakupu i poproś ją o [jej anulowanie](manage-self-service-purchases-users.md#cancel-a-subscription).

## <a name="take-over-a-self-service-purchase-subscription"></a>Przejęcie subskrypcji zakupu samoobsługowego

Możesz przejąć subskrypcję samoobsługowego zakupu dokonaną przez użytkownika w organizacji. Po przejęeniu subskrypcji samoobsługowego zakupu dostępne są dwie opcje:

1. Przenieś użytkowników do innej subskrypcji i anuluj oryginalną subskrypcję.
2. Anuluj subskrypcję samoobsługowego zakupu i usuń licencje przypisanych użytkowników.

### <a name="move-users-to-a-different-subscription"></a>Przenoszenie użytkowników do innej subskrypcji

Po przeniesieniu użytkowników do innej subskrypcji stara subskrypcja zostanie automatycznie anulowana. Użytkownik, który pierwotnie kupił subskrypcję samoobsługowego zakupu, otrzymuje wiadomość e-mail z informacją, że subskrypcja została anulowana.

> [!NOTE]
> Musisz mieć dostępną licencję dla każdego użytkownika przenoszonego w subskrypcji, do której przenosisz użytkowników.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centrum administracyjnym</a> przejdź do strony **Rozliczenia** > **Twoje produkty** .

::: moniker-end

2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Samoobsługowe**.
3. Wybierz subskrypcję, którą chcesz przejąć.
4. Na stronie szczegółów subskrypcji w sekcji **Subskrypcje i ustawienia** wybierz pozycję **Przejmij kontrolę nad tą subskrypcją**.
5. W okienku po prawej stronie wybierz pozycję **Przenieś użytkowników**.
6. Wybierz produkt, do który chcesz przenieść użytkowników, a następnie wybierz pozycję **Przenieś użytkowników**.
7. W polu **Przenoszenie użytkowników** wybierz pozycję **Przenieś użytkowników**. Proces przenoszenia może potrwać kilka minut. Nie zamykaj przeglądarki podczas uruchamiania procesu.
8. Po zakończeniu procesu przenoszenia zamknij **okienko Przenieś ukończone**.
9. Na stronie szczegółów subskrypcji **stan subskrypcji** dla subskrypcji zakupionej samoobsługowej jest wyświetlany jako **Usunięty**.

### <a name="cancel-a-self-service-purchase-subscription"></a>Anulowanie subskrypcji samoobsługowego zakupu

Jeśli zdecydujesz się anulować subskrypcję samoobsługowego zakupu, użytkownicy z licencjami utracą dostęp do produktu. Użytkownik, który pierwotnie kupił subskrypcję samoobsługowego zakupu, otrzymuje wiadomość e-mail z informacją, że subskrypcja została anulowana.

::: moniker range="o365-worldwide"

1. W centrum administracyjnym przejdź do strony **Rozliczenia** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Twoje produkty</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centrum administracyjnym</a> przejdź do strony **Rozliczenia** > **Twoje produkty** .

::: moniker-end

2. Na karcie **Produkty** wybierz ikonę filtru, a następnie wybierz pozycję **Samoobsługowe**.
3. Wybierz subskrypcję, którą chcesz anulować.
4. Na stronie szczegółów subskrypcji w sekcji **Subskrypcje i ustawienia** wybierz pozycję **Przejmij kontrolę nad tą subskrypcją**.
5. W okienku po prawej stronie wybierz pozycję **Anuluj subskrypcję**.
6. Wybierz przyczynę anulowania z listy rozwijanej, a następnie wybierz pozycję **Anuluj subskrypcję**.
7. W polu **Czy na pewno chcesz anulować?** wybierz pozycję **Anuluj subskrypcję**.
8. Zamknij okienko po prawej stronie.
9. Na stronie szczegółów subskrypcji **stan Subskrypcja** jest wyświetlany jako **Usunięty**.

## <a name="need-help-contact-us"></a>Potrzebujesz pomocy? Skontaktuj się z nami.

Aby uzyskać typowe pytania dotyczące zakupów samoobsługowych, zobacz [Często zadawane pytania dotyczące zakupów samoobsługowych](self-service-purchase-faq.yml).

Jeśli masz pytania lub potrzebujesz pomocy dotyczącej zakupów samoobsługowych, [skontaktuj się z pomocą techniczną](../../admin/get-help-support.md).
