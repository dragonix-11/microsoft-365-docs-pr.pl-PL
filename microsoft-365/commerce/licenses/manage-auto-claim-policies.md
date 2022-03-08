---
title: Zarządzanie zasadami automatycznego żądania
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: yinggiy, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
description: Dowiedz się, jak tworzyć zasady automatycznego żądania i zarządzać nimi, które automatycznie przypiszą licencje użytkownikom określonych aplikacji.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: d6cb3d78de914e84e831947089aeadf277e72ddf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321099"
---
# <a name="manage-auto-claim-policies"></a>Zarządzanie zasadami automatycznego żądania

Zasady automatycznego żądania umożliwiają użytkownikom automatyczne żądanie licencji na produkt po pierwszym zalogowaniu się do aplikacji. Zazwyczaj jako administrator przypisujesz licencje użytkownikom ręcznie lub przy użyciu licencjonowania grupowego. Za pomocą zasad automatycznego żądania można zarządzać produktami, dla których użytkownicy mogą automatycznie żądać licencji. Możesz również kontrolować, z jakich produktów pochodzą te licencje.

> [!IMPORTANT]
> Zasady automatycznego żądania są obecnie dostępne tylko dla Microsoft Teams. W przyszłości będzie dostępnych więcej produktów.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby tworzyć zasady automatycznego żądania i zarządzać nimi, musisz być administratorem globalnym, użytkownikiem lub licencją. Aby uzyskać więcej informacji, zobacz [Informacje Microsoft 365 administratorów](../../admin/add-users/about-admin-roles.md).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Włączanie lub wyłączanie funkcji automatycznego żądania zasad

Domyślnie funkcja zasad automatycznego żądania jest wyłączona. Aby można było korzystać z tej funkcji, należy ją najpierw włączyć. Po włączeniu tej funkcji możesz utworzyć zasady automatycznego żądania.

### <a name="turn-on-auto-claim-policies"></a>Włączanie zasad automatycznego żądania

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Na środku strony wybierz przycisk **Włącz ustawienie** .

### <a name="turn-off-auto-claim-policies"></a>Wyłączanie zasad automatycznego żądania

Tylko administrator globalny może wyłączyć ustawienie zasad automatycznego żądania.

1. W centrum administracyjnym przejdź **do strony Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">ustawienia organizacji</a>.
2. U dołu tabeli wybierz pozycję Aplikacje i usługi **należące do użytkownika**.
3. W prawym okienku wyczyść pole wyboru Pozwalaj użytkownikom **na automatyczne żądanie licencji podczas pierwszego logowania**.

Jeśli masz już aktywne zasady, ale nie chcesz, aby więcej użytkowników żądało licencji, [wyłącz te zasady](#turn-a-policy-on-or-off). Gdy wyłączysz zasady automatycznego żądania, już od tego momentu nikt więcej użytkowników nie będzie już może żądać licencji. Użytkownicy, którzy już odechcili licencję, nie utracą swojej licencji.

## <a name="create-an-auto-claim-policy"></a>Tworzenie zasad automatycznego żądania

Karta <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> zawiera listę tworzyć zasady. Na tej karcie widać: nazwę zasad, aplikację skojarzoną z zasadami, produkt przypisany do zasad, liczbę dostępnych licencji i stan zasad.

Gdy tworzysz zasady automatycznego żądania, możesz dodać do niego produkt kopii zapasowej. Jeśli w produkcie podstawowym nie ma licencji, do przypisania licencji do użytkowników służy produkt kopii zapasowej. Możesz dodać maksymalnie cztery produkty do kopii zapasowej i zmienić [kolejność ich przechowywania](#change-the-assigning-order-for-backup-products). Aby dowiedzieć się więcej, zobacz [Dodawanie lub usuwanie produktów kopii zapasowej](#add-or-remove-backup-products).

> [!NOTE]
> Obecnie można utworzyć tylko jedną zasady automatycznego żądania. Liczba zasad, które można utworzyć, zwiększy się, gdy więcej produktów będzie mógło korzystać z tej funkcji.

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz **pozycję Dodaj zasady**.
3. Na **stronie Nadaj nazwę zasadom automatycznego żądania** wprowadź nazwę zasad, a następnie wybierz pozycję **Dalej**.
4. Na **stronie Ustawianie automatycznego żądania aplikacji** i produktu wybierz aplikację i subskrypcję, z których chcesz przypisać licencje.
5. Jeśli chcesz dodać produkt kopii zapasowej, wybierz pozycję Dodaj produkt kopii zapasowej do tych zasad, **a** następnie wybierz produkt z listy.
6. Wybierz pozycję **Dalej**.
7. Na stronie **Wybieranie aplikacji** wyczyść lub zaznacz pola wyboru aplikacji, które chcesz wykluczyć z licencji lub dołączyć do nich, a następnie wybierz pozycję **Dalej**.
8. Jeśli dodano co najmniej jeden produkt kopii zapasowej, powtórz krok 7 dla każdego produktu. W przeciwnym razie przejdź do kroku 9.
9. Na stronie **Przeglądanie i kończanie** sprawdź informacje o nowych zasadach, w razie potrzeby wprowadzić zmiany, a następnie wybierz pozycję **Utwórz zasady**.
10. Wybierz pozycję **Zamknij**.

## <a name="turn-a-policy-on-or-off"></a>Włączanie i wyłączanie zasad

Po wyłączenie zasad użytkownicy nie mogą żądać licencji w ramach tych zasad. Zmiana nie ma wpływu na użytkowników, którzy już odmówili licencji na podstawie tych zasad.

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów w obszarze **Włączanie lub** wyłączanie tych zasad zaznacz lub wyczyść to pole wyboru.
4. Wybierz **pozycję Zapisz** , aby zamknąć okienko szczegółów.

## <a name="edit-the-policy-friendly-name"></a>Edytowanie przyjaznej nazwy zasad

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów w sekcji **Nazwa zasad** wybierz pozycję **Edytuj**.
4. Wprowadź nazwę nowej zasady, a następnie wybierz pozycję **Zapisz**.
5. Wybierz **pozycję Zapisz** , aby zamknąć okienko szczegółów.

## <a name="add-or-remove-backup-products"></a>Dodawanie lub usuwanie produktów kopii zapasowych

Tworząc zasady, dodajesz do niego produkt. Licencje są następnie automatycznie przypisywane do użytkowników z tej puli licencji. W dowolnej chwili możesz dodawać lub usuwać produkty na zasadach automatycznego żądania. Jeśli z zasadami jest już skojarzony jeden produkt, wszelkie produkty, które dodasz, są traktowane jako produkty kopii zapasowej. Gdy zostanie użyta dostępna liczba licencji z pierwszego produktu, zasady użyją następnego produktu kopii zapasowej z listy, z którym zostaną przypisane licencje. [Kolejność produktów na liście można zmieniać](#change-the-assigning-apps-and-services).

Po usunięciu produktu kopii zapasowej nie będzie on już używany do przypisywania licencji. Użytkownicy, którzy mają istniejącą licencję, nadal mają te licencje, ale żaden nowy użytkownik nie może otrzymać licencji na ten produkt.

> [!NOTE]
> Zasady automatycznego żądania muszą zawierać co najmniej jeden produkt. Nie można usunąć wszystkich produktów z zasad. Jeśli nie chcesz już przypisywać licencji z określonych zasad automatycznego żądania, [wyłącz te zasady](#view-an-auto-claim-policy-report).

### <a name="add-a-backup-product"></a>Dodawanie produktu kopii zapasowej

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów u dołu wybierz pozycję Dodaj produkt kopii zapasowej **do tych zasad**.
    > [!NOTE]
    > Jeśli nie widzisz tego linku, oznacza to, że z Twoim kontem jest skojarzony tylko jeden produkt.
4. W **okienku Dodaj produkt** wybierz produkt do dodania do zasad za pomocą listy rozwijanej, a następnie wybierz pozycję **Dodaj**.
5. Wybierz **pozycję Zapisz** , aby zamknąć okienko szczegółów.

### <a name="remove-a-backup-product"></a>Usuwanie produktu kopii zapasowej

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz zasady, które chcesz edytować.
3. W dolnym okienku szczegółów wybierz pozycję **Usuń produkt**.
4. W **okienku Usuń produkt z** zasad zaznacz pole zasad, które chcesz usunąć, a następnie wybierz pozycję **Zapisz**.
5. Zamknij okienko szczegółów.

## <a name="change-the-assigning-apps-and-services"></a>Zmienianie przypisanych aplikacji i usług

Z każdym produktem jest skojarzona kolekcja aplikacji i usług. Dla każdego produktu w twoich zasadach automatycznego żądania możesz określić, które aplikacje i usługi mają być dołączane, gdy użytkownikowi zostanie automatycznie przypisana licencja do tego produktu.

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów w obszarze **Aplikacje i usługi** wybierz pozycję **Edytuj**.
4. W **okienku Aplikacje i** usługi z listy rozwijanej Produkt wybierz jeden produkt lub wybierz pozycję **Wszystkie produkty**.
5. Zaznacz lub wyczyść pola wyboru aplikacji i usług, do których użytkownicy mają mieć dostęp lub do których nie mają dostępu.
6. Po zakończeniu wybierz pozycję **Zapisz**, a następnie zamknij okienko szczegółów.

## <a name="change-the-assigning-order-for-backup-products"></a>Zmienianie kolejności przypisywania produktów do kopii zapasowej

Jeśli do zasad przypisano produkty kopii zapasowej, możesz zmienić kolejność, w jakiej są używane do przypisywania licencji, gdy użytkownicy logują się do aplikacji.

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów w sekcji **Licencje na** produkty zaznacz pole obok produktu, który chcesz przenieść, a następnie **wybierz pozycję Przenieś** w górę lub **Przenieś w dół**.
4. Powtórz krok 3 dla każdego produktu, którego zamówienie chcesz zmienić.
5. Po zakończeniu zmieniania kolejności produktów **wybierz pozycję Zapisz** , aby zamknąć okienko szczegółów.

## <a name="view-an-auto-claim-policy-report"></a>Wyświetlanie raportu zasad automatycznego żądania

1. W centrum administracyjnym przejdź **do strony** \> **Licencje rozliczeniowe** , a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego żądania</a> .
2. Wybierz **pozycję Wyświetl raport**. Strona **Raport zasad automatycznego żądania** zawiera listę wszystkich licencji przypisanych z poszczególnych zasad w ciągu ostatnich 90 dni. Domyślnie na stronie jest pokazanych ostatnich 90 dni.
3. Aby zmienić wyświetlany okres, wybierz listę rozwijaną Ostatnie **30** dni. Możesz wyświetlać raporty z ostatnich 1, 7, 30 i 90 dni.

## <a name="next-steps"></a>Następne kroki

Możesz okresowo wracać do karty **Zasady automatycznego** żądania, aby wyświetlić listę użytkowników, którzy odmówili licencji w ramach utworzonych przez Ciebie zasad.

## <a name="related-content"></a>Zawartość pokrewna

[Przypisywanie licencji użytkownikom](../../admin/manage/assign-licenses-to-users.md) (artykuł)\
[Kupowanie lub usuwanie licencji subskrypcji](buy-licenses.md) (artykuł)\
[Opis subskrypcji i licencji](subscriptions-and-licenses.md) (artykuł)
