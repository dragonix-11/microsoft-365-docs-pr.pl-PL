---
title: Uaktualnianie z SharePoint 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: sharepoint-server-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Znajdź informacje i zasoby do uaktualnienia z programu SharePoint Server 2013 i SharePoint Foundation 2013. Obsługa obu tych dni kończy się 11 kwietnia 2023 r.
ms.openlocfilehash: 05f545b67d60d6bcc45587049e49a5f5c1f6d654
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2021
ms.locfileid: "62990525"
---
# <a name="upgrading-from-sharepoint-2013"></a>Uaktualnianie z SharePoint 2013

Wsparcie Microsoft SharePoint Server 11 kwietnia 2023 SharePoint 2013 r. w obu tych SharePoint i Foundation **2013**. Ten artykuł zawiera zasoby pomocne w migracji istniejących danych programu SharePoint Server do usługi SharePoint Online w programie Microsoft 365 lub uaktualnieniu lokalnego środowiska programu SharePoint 2013. W dalszej części tego artykułu użyjemy programu SharePoint 2013 do odwoływać się zarówno do programu SharePoint Server 2013, jak i SharePoint Foundation 2013.

## <a name="what-is-end-of-support"></a>Co oznacza *zakończenie wsparcia technicznego*?

Większość produktów firmy Microsoft ma cykl życia pomocy technicznej, w trakcie którego uzyskają nowe funkcje, poprawki, poprawki zabezpieczeń i tak dalej. Po zakończeniu wsparcia technicznego produkt nie przestanie działać, ale firma Microsoft już nie udostępnia:

- pomoc techniczną w zakresie mogącego wystąpić problemów;

- Poprawki błędów dotyczące problemów, które mogą mieć wpływ na stabilność i użyteczność serwera.

- Poprawki zabezpieczeń dotyczące luk, które mogą nabędać serwer na naruszenie bezpieczeństwa.

- Aktualizacje stref czasowych.

Oznacza to, że nie będą dostępne żadne dalsze aktualizacje, poprawki ani poprawki dla tego produktu (w tym poprawki zabezpieczeń/poprawki). Pomoc techniczna firmy Microsoft całkowicie przesunięła swoje działania na rzecz obsługi najnowszych wersji.

> [!NOTE]
> Cykl życia oprogramowania zazwyczaj trwa pięć lat wsparcia głównego od wersji początkowej i potencjalnie do dodatkowych 5 lat wsparcia dodatkowego. [Dostawcy rozwiązań firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) mogą pomóc w uaktualnieniu do następnej wersji oprogramowania lub migracji do programu Microsoft 365 (lub obu). Upewnij się, że wiesz, kiedy kończysz wsparcie techniczne dla krytycznych technologii, zwłaszcza w przypadku wersji programu Microsoft SQL Server, z SharePoint. Aby uzyskać więcej informacji, zobacz [Stałe zasady cyklu życia](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planowanie z wyprzedzeniem

Sprawdź daty zakończenia obsługi w witrynie cyklu życia produktu dla programu [SharePoint Server 2013](/lifecycle/products/sharepoint-server-2013) i [SharePoint Foundation 2013](/lifecycle/products/sharepoint-foundation-2013). Planuj uaktualnienia i migracje, pamiętasz o tych datach. Pamiętaj, że produkt *nie przestanie działać w* dniu na liście. Jednak ponieważ po tym dniu instalacja nie będzie już poprawiana, należy zaplanować płynne przejście do następnej wersji produktu. W poniższej tabeli wymieniono dostępne opcje.

|Zakończenie produktu pomocy technicznej|Dobra|Lepsze|Najlepsza|
|---|---|---|---|
|SharePoint Server 2013<BR>SharePoint Foundation 2013|Uaktualnianie do SharePoint Server 2016 lub 2019|Uaktualnianie do SharePoint Server Subscription Edition|Migrowanie do SharePoint w programie Microsoft 365

## <a name="whats-next"></a>Co dalej?

Zalecamy  migrowanie do SharePoint Microsoft 365 w celu skorzystania z najnowszych rozwiązań do współpracy, analizy i zabezpieczeń w Microsoft 365. Nowoczesne funkcje obsługi w aplikacji Microsoft 365 są atrakcyjne, elastyczne i performacyjnie.

Jeśli chcesz zachować lokalne wdrożenie programu SharePoint, zalecamy wdrożenie hybrydowe, które umożliwi migrowanie tak dużej SharePoint funkcji, jak to SharePoint w Microsoft 365. Zobacz [SharePoint hybrydowe,](/sharepoint/hybrid/hybrid) aby dowiedzieć się więcej o implementacji hybrydowej i zaplanować jej wdrożenie.

### <a name="migrate-to-sharepoint-in-microsoft-365"></a>Migrowanie do SharePoint w programie Microsoft 365

Za pomocą narzędzia do migracji SharePoint(SPMT) możesz migrować witryny i zawartość do SharePoint w programie Microsoft 365. Mamy obszerną bibliotekę zawartości, która może ułatwić Ci planowanie z wyprzedzeniem, przeprowadzenie migracji i rozwiązanie wszelkich mogącej wystąpić problemów. [Warto zacząć SharePoint](/sharepointmigration/introducing-the-sharepoint-migration-tool) narzędzia do migracji wiadomości.

### <a name="upgrade-to-sharepoint-server-subscription-edition"></a>Uaktualnianie do SharePoint Server Subscription Edition

Mimo że nie istnieje bezpośrednia ścieżka uaktualnienia z wersji SharePoint 2013 do wersji Subscription Edition, nadal jest to druga najlepsza opcja. Główną przyczyną jest wprowadzenie SharePoint Server Subscription Edition, który eliminuje konieczność wprowadzania nowych wersji głównych programu SharePoint Server.

Aby uaktualnić do wersji Subscription Edition, musisz mieć SharePoint Server 2016 lub 2019. Ponieważ również nie istnieje bezpośrednia ścieżka z programu SharePoint 2013 do wersji 2019, najlepszym rozwiązaniem jest uaktualnienie do wersji 2016, a następnie uaktualnienie do wersji Subscription Edition. Zobacz poniższe linki, aby dowiedzieć się więcej na temat i zaplanować uaktualnienie do wersji Subscription Edition:

- [Uaktualnianie do SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Uaktualnianie do SharePoint Server Subscription Edition](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-subscription-edition)

Nawet jeśli masz potrzebę utrzymania wdrożenia lokalnego programu SharePoint, zalecamy przeprowadzenie migracji części witryn lub zawartości do usługi Microsoft 365 za pomocą wdrożenia hybrydowego programu [SharePoint](/sharepoint/hybrid/hybrid), aby zacząć korzystać z nowoczesnych środowisk współpracy, funkcji zabezpieczeń i zgodności w p Microsoft 365.  

### <a name="upgrade-to-sharepoint-server-2016-or-2019"></a>Uaktualnianie do SharePoint Server 2016 lub 2019

Obie SharePoint Server 2016 i 2019 są obsługiwane platformy, jeśli planujesz zachować lokalne wdrożenie usługi SharePoint po zakończeniu obsługi w roku 2013. Jednak obie **wersje zakończą się 14 lipca 2026 r**. Oznacza to, że musisz zaplanować kolejne uaktualnienie w ciągu 3 lat od daty zakończenia pomocy technicznej dla roku 2013. Poniżej znajdują się strony cyklu życia pomocy technicznej dla obu produktów:

- [SharePoint cykl życia programu SharePoint Server 2016](/lifecycle/products/sharepoint-server-2016)
- [SharePoint Server 2019 dat cyklu życia pomocy technicznej](/lifecycle/products/sharepoint-server-2019)

Aby dowiedzieć się więcej i zaplanować uaktualnienie, zobacz następujące artykuły:

- [Uaktualnianie do SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [Uaktualnij do SharePoint Server 2019](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2019)

Nawet jeśli masz potrzebę utrzymania wdrożenia lokalnego programu SharePoint, zalecamy przeprowadzenie migracji części witryn lub zawartości do usługi Microsoft 365 za pomocą wdrożenia hybrydowego programu [SharePoint](/sharepoint/hybrid/hybrid), aby zacząć korzystać z nowoczesnych środowisk współpracy, funkcji zabezpieczeń i zgodności w p Microsoft 365.  
