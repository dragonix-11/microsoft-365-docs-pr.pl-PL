---
title: Planowanie Microsoft 365 multi-geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Dowiedz się więcej o Microsoft 365 Multi-Geo, sposobie działania wielu obszarów geograficznych i o tym, jakie lokalizacje geograficzne są dostępne dla magazynu danych.
ms.openlocfilehash: bda48f14b14840eed03d456ef66e7d86df890619
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822799"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Planowanie Microsoft 365 multi-geo

Niniejsze wskazówki są przeznaczone dla administratorów firm wielonarodowych, którzy przygotowują swoją dzierżawę Microsoft 365 do rozszerzenia ich na dodatkowe lokalizacje geograficzne zgodnie z obecnością firmy w celu spełnienia wymagań dotyczących przechowywania danych.

W konfiguracji z wieloma lokalizacjami geograficznymi dzierżawa Microsoft 365 składa się z centralnej lokalizacji i co najmniej jednej lokalizacji satelitarnej. Jest to pojedyncza dzierżawa obejmująca wiele lokalizacji geograficznych. Informacje o dzierżawie, w tym lokalizacje geograficzne, są opanowane w Azure Active Directory (Azure AD).

Poniżej przedstawiono kilka kluczowych terminów obejmujących wiele obszarów geograficznych, które ułatwiają zrozumienie podstawowych pojęć związanych z konfiguracją:

- **Dzierżawa** — reprezentacja organizacji w Microsoft 365 która zwykle ma skojarzoną co najmniej jedną domenę (na przykład https://contoso.sharepoint.com).

- **Lokalizacje geograficzne** — lokalizacje geograficzne dostępne do hostowania danych w dzierżawie Microsoft 365.

- **Lokalizacje satelitarne** — dodatkowe lokalizacje geograficzne skonfigurowane do hostowania danych w dzierżawie Microsoft 365. Dzierżawy z wieloma lokalizacjami geograficznymi obejmują więcej niż jedną lokalizację geograficzną, na przykład Ameryka Północna i Europę.

- **Preferowana lokalizacja danych (PDL)** — lokalizacja geograficzna, w której są przechowywane dane Exchange i OneDrive poszczególnych użytkowników. Administrator może ustawić tę opcję na dowolną lokalizację geograficzną skonfigurowaną dla dzierżawy. Należy pamiętać, że jeśli zmienisz bibliotekę PDL dla użytkownika, który ma już witrynę OneDrive, jego dane OneDrive nie zostaną automatycznie przeniesione do nowej lokalizacji geograficznej. Aby uzyskać więcej informacji[, zobacz Przenoszenie biblioteki OneDrive do innej lokalizacji geograficznej](move-onedrive-between-geo-locations.md). Jeśli mają skrzynkę pocztową Exchange, skrzynka pocztowa zostanie automatycznie przeniesiona do nowej preferowanej lokalizacji danych.

Włączenie funkcji Multi-Geo wymaga czterech kluczowych kroków:

1. Skontaktuj się z zespołem ds. konta, aby dodać _możliwości wielu obszarów geograficznych w planie usługi Microsoft 365_.

2. Wybierz żądane lokalizacje satelitarne i dodaj je do dzierżawy.

3. Ustaw preferowaną lokalizację danych użytkowników na żądaną lokalizację satelitarną. Gdy nowa witryna OneDrive lub skrzynka pocztowa Exchange jest aprowizowana dla użytkownika, jest aprowizowana do jego biblioteki PDL.

4. W razie potrzeby zmigruj istniejące witryny OneDrive użytkowników z centralnej lokalizacji do preferowanej lokalizacji danych. (Exchange skrzynki pocztowe są migrowane automatycznie po ustawieniu biblioteki PDL użytkownika).

Aby uzyskać szczegółowe informacje na temat każdego z tych kroków, zobacz [Konfigurowanie Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> Należy pamiętać, że Microsoft 365 Multi-Geo nie jest przeznaczony do optymalizacji wydajności, jest przeznaczony do spełnienia wymagań dotyczących przechowywania danych. Aby uzyskać informacje na temat optymalizacji wydajności dla Microsoft 365, zobacz [Planowanie sieci i dostrajanie wydajności dla Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) lub skontaktuj się z grupą pomocy technicznej.

Możesz skonfigurować dowolną z następujących lokalizacji jako lokalizacje satelitarne, w których można hostować OneDrive i SharePoint lokacje oraz Exchange skrzynki pocztowe. Podczas planowania wielu obszarów geograficznych utwórz listę lokalizacji, które chcesz dodać do dzierżawy Microsoft 365. Zalecamy rozpoczęcie od jednej lub dwóch lokalizacji satelitarnych, a następnie stopniowe rozszerzanie do większej liczby lokalizacji geograficznych, w razie potrzeby.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Podczas konfigurowania wielu obszarów geograficznych rozważ skorzystanie z możliwości skonsolidowania infrastruktury lokalnej podczas migracji do Microsoft 365. Jeśli na przykład masz lokalne farmy w Singapurze i Malezji, możesz je skonsolidować w lokalizacji satelitarnej APC, pod warunkiem, że pozwalają na to wymagania dotyczące przechowywania danych.

## <a name="best-practices"></a>Najważniejsze wskazówki

Zalecamy utworzenie użytkownika testowego w Microsoft 365, aby wykonać wstępne testy. Przed przystąpieniem użytkowników produkcyjnych do Microsoft 365 Multi-Geo przeprowadzimy kroki testowania i weryfikacji tego użytkownika.

Po zakończeniu testowania z użytkownikiem testowym wybierz grupę pilotażową — być może z działu IT — jako pierwszą, która będzie używać OneDrive i Exchange w nowej lokalizacji geograficznej. Dla tej pierwszej grupy wybierz użytkowników, którzy nie mają jeszcze OneDrive. Zalecamy nie więcej niż pięć osób w tej początkowej grupie i stopniowo rozwijamy się zgodnie z podejściem do wdrażania wsadowego.

Każdy użytkownik powinien mieć *ustawioną preferowaną lokalizację danych* (PDL), aby Microsoft 365 mógł określić lokalizację geograficzną do aprowizacji OneDrive. Preferowana lokalizacja danych użytkownika musi być zgodna z jedną z wybranych lokalizacji satelitarnych lub centralną lokalizacją. Chociaż pole PDL nie jest obowiązkowe, zalecamy ustawienie biblioteki PDL dla wszystkich użytkowników. Obciążenia użytkownika bez biblioteki PDL będą aprowizowane w centralnej lokalizacji.

Utwórz listę użytkowników i dołącz ich główną nazwę użytkownika (UPN) i kod lokalizacji dla odpowiedniej preferowanej lokalizacji danych. Dołącz użytkownika testowego i początkową grupę pilotażową na początek. Ta lista będzie potrzebna dla procedur konfiguracji.

Jeśli użytkownicy są synchronizowane z systemu lokalna usługa Active Directory do Azure Active Directory, należy ustawić preferowaną lokalizację danych jako atrybut usługi Active Directory i zsynchronizować go przy użyciu Azure Active Directory Połączenie. Nie można bezpośrednio skonfigurować preferowanej lokalizacji danych dla synchronizowanych użytkowników przy użyciu programu PowerShell usługi Azure AD. Kroki konfigurowania biblioteki PDL w usłudze Active Directory i synchronizowania ich są omówione w [Azure Active Directory Połączenie synchronizacji: konfigurowanie preferowanej lokalizacji danych dla Microsoft 365 zasobów](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

Administrowanie dzierżawą obejmującą wiele obszarów geograficznych może się różnić od dzierżawy innej niż dzierżawa z wieloma lokalizacjami geograficznymi, ponieważ wiele ustawień i usług SharePoint i OneDrive jest obsługujących wiele obszarów geograficznych. Zalecamy [zapoznanie się z artykułem Administrowanie środowiskiem z wieloma lokalizacjami geograficznymi](administering-a-multi-geo-environment.md) przed kontynuowaniem konfiguracji.

Przeczytaj [środowisko użytkownika w środowisku z wieloma lokalizacjami geograficznymi](multi-geo-user-experience.md) , aby uzyskać szczegółowe informacje o środowisku użytkowników końcowych w środowisku z wieloma lokalizacjami geograficznymi.

Aby rozpocząć konfigurowanie Microsoft 365 multi-geo, zobacz [Konfigurowanie Microsoft 365 multi-geo](multi-geo-tenant-configuration.md).

Po zakończeniu konfiguracji pamiętaj o [migracji bibliotek OneDrive użytkowników](move-onedrive-between-geo-locations.md) zgodnie z potrzebami, aby użytkownicy mogli pracować z preferowanych lokalizacji danych.

## <a name="related-topics"></a>Tematy pokrewne

[Microsoft 365 konfiguracji zbierania elektronicznych materiałów dowodowych](./multi-geo-ediscovery-configuration.md)
