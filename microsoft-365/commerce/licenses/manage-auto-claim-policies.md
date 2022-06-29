---
title: Zarządzanie zasadami automatycznego oświadczenia
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
description: Dowiedz się, jak tworzyć zasady automatycznego oświadczeń i zarządzać nimi, które automatycznie przypisują licencje użytkownikom dla niektórych aplikacji.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: 76f2742dc97f880c8044def269e3e9517ea4605c
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493791"
---
# <a name="manage-microsoft-teams-auto-claim-policies"></a>Zarządzanie zasadami automatycznego oświadczeń w usłudze Microsoft Teams

Zasady automatycznego oświadczenia umożliwiają użytkownikom automatyczne ubieganie się o licencję na produkt przy pierwszym zalogowaniu się do aplikacji. Jako administrator zazwyczaj przypisujesz licencje użytkownikom ręcznie lub przy użyciu licencjonowania opartego na grupach. Za pomocą zasad automatycznego oświadczeń zarządzasz produktami, dla których użytkownicy mogą automatycznie ubiegać się o licencje. Możesz również kontrolować produkty, z których pochodzą te licencje.

> [!IMPORTANT]
> Zasady automatycznego oświadczenia są obecnie dostępne tylko dla usługi Microsoft Teams. Więcej produktów będzie dostępnych do użycia w przyszłości.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby tworzyć zasady automatycznego oświadczeń i zarządzać nimi, musisz być administratorem globalnym, użytkownikiem lub administratorem licencji. Aby uzyskać więcej informacji, zobacz [About Microsoft 365 admin roles (Informacje o rolach administratora platformy Microsoft 365](../../admin/add-users/about-admin-roles.md)).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Włączanie lub wyłączanie funkcji zasad automatycznego oświadczeń

Domyślnie funkcja zasad automatycznego oświadczenia jest wyłączona. Przed rozpoczęciem korzystania z tej funkcji należy ją najpierw włączyć. Po włączeniu funkcji można utworzyć zasady automatycznego oświadczenia.

### <a name="turn-on-auto-claim-policies"></a>Włączanie zasad automatycznego oświadczeń

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Na środku strony wybierz przycisk **Włącz ustawienie** .

### <a name="turn-off-auto-claim-policies"></a>Wyłączanie zasad automatycznego oświadczeń

Tylko administrator globalny może wyłączyć ustawienie zasad automatycznego oświadczenia.

1. W centrum administracyjnym przejdź do strony **Ustawienia** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">ustawień organizacji</a> .
2. W dolnej części tabeli wybierz pozycję **Aplikacje i usługi należące do użytkownika**.
3. W okienku po prawej stronie wyczyść pole **Zezwalaj użytkownikom na automatyczne uzyskiwanie licencji podczas pierwszego logowania**.

Jeśli masz już aktywne zasady, ale nie chcesz, aby więcej użytkowników ubiegało się o licencje, [wyłącz zasady](#turn-a-policy-on-or-off). Po wyłączeniu zasad automatycznego oświadczeń żaden użytkownik nie może od tego momentu ubiegać się o licencję. Użytkownicy, którzy już ubiegali się o licencję, nie tracą licencji.

## <a name="create-an-auto-claim-policy"></a>Tworzenie zasad automatycznego oświadczenia

Karta <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a> zawiera listę utworzonych zasad. Na tej karcie można zobaczyć: nazwę zasad, aplikację skojarzoną z zasadami, produkt przypisany do zasad, liczbę dostępnych licencji i stan zasad.

Podczas tworzenia zasad automatycznego oświadczenia możesz dodać do niego produkt kopii zapasowej. Jeśli produkt podstawowy nie ma licencji, produkt kopii zapasowej jest używany do przypisywania licencji do użytkowników. Możesz dodać maksymalnie cztery produkty do tworzenia kopii zapasowych i [zmienić kolejność ich użycia](#change-the-assigning-order-for-backup-products). Aby dowiedzieć się więcej, zobacz [Dodawanie lub usuwanie produktów kopii zapasowych](#add-or-remove-backup-products).

> [!NOTE]
> Obecnie można utworzyć tylko jedną zasadę automatycznego oświadczenia. Liczba zasad, które można utworzyć, wzrośnie, ponieważ więcej produktów będzie mogło korzystać z tej funkcji.

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz **pozycję Dodaj zasady**.
3. Na stronie **Nazwa tych zasad automatycznego oświadczenia** wprowadź nazwę zasad, a następnie wybierz pozycję **Dalej**.
4. Na stronie **Ustawianie aplikacji automatycznego oświadczenia i produktu** wybierz aplikację i subskrypcję, z których chcesz przypisać licencje.
5. Jeśli chcesz dodać produkt kopii zapasowej, wybierz **pozycję Dodaj produkt kopii zapasowej do tych zasad**, a następnie wybierz produkt z listy.
6. Wybierz pozycję **Dalej**.
7. Na stronie **Wybieranie aplikacji** wyczyść lub zaznacz pola dla aplikacji do wykluczenia lub uwzględnienia w licencji, a następnie wybierz pozycję **Dalej**.
8. Jeśli dodano co najmniej jeden produkt do tworzenia kopii zapasowych, powtórz krok 7 dla każdego produktu. W przeciwnym razie przejdź do kroku 9.
9. Na stronie **Przeglądanie i zakończenie** sprawdź nowe informacje o zasadach, wprowadź wszelkie niezbędne zmiany, a następnie wybierz pozycję **Utwórz zasady**.
10. Wybierz pozycję **Zamknij**.

## <a name="turn-a-policy-on-or-off"></a>Włączanie lub wyłączanie zasad

Po wyłączeniu zasad żaden użytkownik nie może ubiegać się o licencje w ramach tych zasad. Zmiana nie ma wpływu na użytkowników, którzy już ubiegali się o licencje w ramach tych zasad.

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów w obszarze **Włącz lub wyłącz te zasady** zaznacz lub wyczyść pole wyboru.
4. Wybierz pozycję **Zapisz** , aby zamknąć okienko szczegółów.

## <a name="edit-the-policy-friendly-name"></a>Edytowanie przyjaznej nazwy zasad

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów w sekcji **Nazwa zasad** wybierz pozycję **Edytuj**.
4. Wprowadź nową nazwę zasad, a następnie wybierz pozycję **Zapisz**.
5. Wybierz pozycję **Zapisz** , aby zamknąć okienko szczegółów.

## <a name="add-or-remove-backup-products"></a>Dodawanie lub usuwanie produktów kopii zapasowych

Podczas tworzenia zasad dodajesz do niego produkt. Licencje są następnie automatycznie przypisywane do użytkowników z tej puli licencji. Produkty dla zasad automatycznego oświadczenia można dodawać lub usuwać w dowolnym momencie. Jeśli masz już jeden produkt skojarzony z zasadami, wszystkie dodane produkty są uznawane za produkty kopii zapasowej. Gdy jest używana dostępna liczba licencji z pierwszego produktu, zasady używają następnego produktu kopii zapasowej na liście do przypisywania licencji. [Możesz zmienić kolejność listy produktów zgodnie z](#change-the-assigning-apps-and-services) tym, co chcesz.

Usunięcie produktu kopii zapasowej nie jest już używane do przypisywania licencji. Użytkownicy z istniejącą licencją nadal mają tę licencję, ale żaden nowy użytkownik nie może otrzymać licencji dla tego produktu.

> [!NOTE]
> Zasady automatycznego oświadczenia muszą zawierać co najmniej jeden produkt. Nie można usunąć wszystkich produktów z zasad. Jeśli nie chcesz już przypisywać licencji z określonych zasad automatycznego oświadczenia, [wyłącz zasady](#view-an-auto-claim-policy-report).

### <a name="add-a-backup-product"></a>Dodawanie produktu kopii zapasowej

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów u dołu wybierz pozycję **Dodaj produkt kopii zapasowej do tych zasad**.
    > [!NOTE]
    > Jeśli nie widzisz tego linku, jest to spowodowane tym, że z kontem jest skojarzony tylko jeden produkt.
4. W okienku **Dodawanie produktu** użyj listy rozwijanej, aby wybrać produkt do dodania do zasad, a następnie wybierz pozycję **Dodaj**.
5. Wybierz pozycję **Zapisz** , aby zamknąć okienko szczegółów.

### <a name="remove-a-backup-product"></a>Usuwanie produktu kopii zapasowej

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów u dołu wybierz pozycję **Usuń produkt**.
4. W okienku **Usuń produkt z zasad** zaznacz pole zasad, które chcesz usunąć, a następnie wybierz pozycję **Zapisz**.
5. Zamknij okienko szczegółów.

## <a name="change-the-assigning-apps-and-services"></a>Zmienianie przypisywania aplikacji i usług

Każdy produkt ma skojarzoną kolekcję aplikacji i usług. Dla każdego produktu w zasadach automatycznego oświadczenia możesz określić, które aplikacje i usługi mają zostać uwzględnione, gdy użytkownik zostanie automatycznie przypisany do tego produktu.

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz zasady, które chcesz edytować.
3. W okienku szczegółów w obszarze **Aplikacje i usługi** wybierz pozycję **Edytuj**.
4. W okienku **Aplikacje i usługi** z listy rozwijanej **Produkt** wybierz pojedynczy produkt lub wybierz pozycję **Wszystkie produkty**.
5. Zaznacz lub wyczyść pola dla aplikacji i usług, do których użytkownicy mają mieć dostęp lub do których nie mają dostępu.
6. Po zakończeniu wybierz pozycję **Zapisz**, a następnie zamknij okienko szczegółów.

## <a name="change-the-assigning-order-for-backup-products"></a>Zmienianie kolejności przypisywania produktów kopii zapasowych

Jeśli masz produkty kopii zapasowych przypisane do zasad, możesz zmienić kolejność, w jakiej są one używane do przypisywania licencji podczas logowania użytkowników do aplikacji.

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz zasady, które chcesz edytować.
3. W okienku **szczegółów w sekcji Licencje produktów** wybierz pole obok produktu, który chcesz przenieść, a następnie wybierz pozycję Przenieś w **górę** lub **Przenieś w dół**.
4. Powtórz krok 3 dla każdego produktu, który chcesz zmienić kolejność.
5. Po zakończeniu zmiany kolejności produktów wybierz pozycję **Zapisz** , aby zamknąć okienko szczegółów.

## <a name="view-an-auto-claim-policy-report"></a>Wyświetlanie raportu zasad automatycznego oświadczenia

1. W centrum administracyjnym przejdź do strony **Licencje rozliczeniowe**  \>, a następnie wybierz kartę <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Zasady automatycznego oświadczenia</a>.
2. Wybierz pozycję **Wyświetl raport**. Strona **raportów zasad automatycznego oświadczenia** zawiera listę wszystkich licencji przypisanych z poszczególnych zasad w ciągu ostatnich 90 dni. Domyślnie strona pokazuje ostatnie 90 dni.
3. Aby zmienić wyświetlany okres, wybierz listę rozwijaną **Ostatnie 30 dni** . Raporty z ostatnich 1, 7, 30 i 90 dni można wyświetlać.

## <a name="next-steps"></a>Następne kroki

Okresowo można wrócić do karty **Zasady automatycznego oświadczenia** , aby wyświetlić listę użytkowników, którzy ubiegali się o licencje w ramach utworzonych zasad.

## <a name="related-content"></a>Zawartość pokrewna

[Przypisywanie licencji do użytkowników](../../admin/manage/assign-licenses-to-users.md) (artykuł)\
[Kupowanie lub usuwanie licencji subskrypcji](buy-licenses.md) (artykuł)\
[Omówienie subskrypcji i licencji](subscriptions-and-licenses.md) (artykuł)
