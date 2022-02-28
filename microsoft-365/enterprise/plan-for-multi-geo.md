---
title: Planowanie pod Microsoft 365 wielolokalizacji
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
description: Dowiedz się Microsoft 365 wielu lokalizacji geograficznych, jak działa obsługa wielu lokalizacji geograficznych i jakie lokalizacje geograficzne są dostępne do przechowywania danych.
ms.openlocfilehash: 5c079d5cf5f093be2c942a53468494044913fbd7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984276"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Planowanie pod Microsoft 365 wielolokalizacji

Te wskazówki są przeznaczone dla administratorów wielonarodowych firm (MNCs), które przygotowujeją swoją dzierżawę usługi Microsoft 365, w celu rozszerzenia ich na dodatkowe lokalizacje geograficzne zgodnie z obecnością firmy w celu spełnienia wymagań dotyczących przechowywania danych.

W konfiguracji wielolokalizacji dzierżawa Microsoft 365 składa się z lokalizacji centralnej i co najmniej jednej lokalizacji satelitarnej. Jest to jedna dzierżawa rozciąga się na wiele lokalizacji geograficznych. Informacje o Dzierżawie, w tym lokalizacje geograficzne, są mastered w usłudze Azure Active Directory (Azure AD).

Poniżej podano kilka kluczowych terminów dla wielu lokalizacji geograficznych, które ułatwiają zrozumienie podstawowych pojęć związanych z konfiguracją:

-   **Dzierżawa** — reprezentacja organizacji w programie Microsoft 365 z którą zwykle jest skojarzona co najmniej jedna domena (na przykład https://contoso.sharepoint.com). 

-   **Lokalizacje geograficzne —** lokalizacje geograficzne dostępne do hostować dane w Microsoft 365 dzierżawie.

-   **Lokalizacje satelitarne —** dodatkowe lokalizacje geograficzne skonfigurowane do hostować dane w Microsoft 365 dzierżawie. Dzierżawy wielowymiarowe obejmują więcej niż jedną lokalizację geograficzną, na przykład Ameryki Północnej i Europy.

-   **Preferowana lokalizacja danych (PDL)** — lokalizacja geograficzna, w której są przechowywane Exchange i OneDrive danych użytkownika. Może to zostać skonfigurowane przez administratora dowolnej lokalizacji geograficznej, która została skonfigurowana dla dzierżawy. Zwróć uwagę, że jeśli zmienisz plik PDL dla użytkownika, który już ma witrynę sieci OneDrive, jego dane OneDrive nie zostaną automatycznie przeniesione do nowej lokalizacji geograficznej. Zobacz [Przenoszenie biblioteki OneDrive lokalizacji geograficznej,](move-onedrive-between-geo-locations.md) aby uzyskać więcej informacji. Jeśli osoby te mają skrzynkę Exchange, zostanie ona automatycznie przeniesiona do nowej preferowanej lokalizacji danych.

Włączenie multi-Geo wymaga czterech kluczowych kroków:

1.  We współpracy z zespołem klienta dodaj funkcje _Multi-Geo Capabilities Microsoft 365_ plan usługi.

2.  Wybierz odpowiednie lokalizacje satelitarne i dodaj je do dzierżawy.

3.  Ustaw preferowaną lokalizację danych użytkowników na żądaną lokalizację satelitarną. Gdy dla użytkownika OneDrive skrzynka pocztowa zostanie Exchange lub nową witryną sieci Web, jest ona zapewniana dla jego pliku PDL.

4.  W razie potrzeby przemigruj istniejące witryny OneDrive z lokalizacji centralnej do preferowanej lokalizacji danych. (Exchange skrzynki pocztowe są migrowane automatycznie po skonfigurowaniu pliku PDL użytkownika.

Aby [uzyskać szczegółowe Microsoft 365 na temat poszczególnych kroków, zobacz Konfigurowanie usługi multi-Geo](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> Pamiętaj, Microsoft 365 multi-Geo nie jest przeznaczona do optymalizacji wydajności, jest ona przeznaczona do spełnienia wymagań dotyczących przechowywania danych. Aby uzyskać informacje na temat optymalizacji wydajności dla Microsoft 365, zobacz Planowanie sieci i dostosowywanie wydajności dla sieci [Microsoft 365 lub skontaktuj](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) się z grupą pomocy technicznej.

Dowolną z poniższych lokalizacji można skonfigurować jako lokalizacje satelitarne, w których można hostować witryny OneDrive i SharePoint pocztowe oraz skrzynki Exchange pocztowe. Podczas planowania dla wielu lokalizacji geograficznych listy lokalizacji, które chcesz dodać do swojej Microsoft 365 dzierżawy. Zalecamy, aby zaczynać od jednej lub dwóch lokalizacji satelitarnych, a następnie stopniowo rozszerzać się na więcej lokalizacji geograficznych, jeśli to konieczne.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Podczas konfigurowania wielu lokalizacji geograficznych rozważ możliwość skonsolidowania swojej infrastruktury lokalnej podczas migracji do Microsoft 365. Jeśli na przykład masz lokalne farmy w Singapurze i Malezji, możesz skonsolidować je z lokalizacją satelitarną APC, o ile pozwalają na to wymagania dotyczące przechowywania danych.

## <a name="best-practices"></a>Najważniejsze wskazówki

Zalecamy utworzenie użytkownika testowego w celu Microsoft 365 testów wstępnych. Z tym użytkownikiem przejdziemy przez pewne kroki testowania i weryfikacji, zanim przystąpisz do logowania użytkowników produkcyjnych do Microsoft 365 multi-Geo.

Po zakończeniu testowania u użytkownika testowego wybierz grupę pilotażową — na przykład ze swojego działu IT — aby jako pierwsza używać aplikacji OneDrive i Exchange w nowej lokalizacji geograficznej. W przypadku tej pierwszej grupy wybierz użytkowników, którzy nie mają jeszcze OneDrive. Zalecamy, aby nie było więcej niż pięć osób w tej grupie początkowej i stopniowo rozszerza się zgodnie z podejściem do etapowego rozsyłania.

Każdy użytkownik powinien mieć *ustawioną preferowaną lokalizację* danych (PDL), aby Microsoft 365 określić, w której lokalizacji geograficznej ma być aprowizacji OneDrive. Preferowana lokalizacja danych użytkownika musi być dopasowana do jednej z wybranych lokalizacji satelitarnych lub lokalizacji centralnej. Pole PDL nie jest obowiązkowe, jednak zalecamy ustawienie pliku PDL dla wszystkich użytkowników. Obciążenia pracą użytkownika bez pliku PDL będą aprowowane w lokalizacji centralnej.

Utwórz listę użytkowników i dołącz główną nazwę użytkownika (UPN) oraz kod lokalizacji odpowiedniej preferowanej lokalizacji danych. Na początek dołącz użytkownika testowego i początkową grupę pilotażową. Ta lista będzie potrzebna na potrzeby procedur konfiguracji.

Jeśli użytkownicy są synchronizowane z lokalnego systemu usługi Active Directory z usługą Azure Active Directory, należy ustawić preferowaną lokalizację danych jako atrybut usługi Active Directory i zsynchronizować ją przy użyciu usługi Azure Active Directory Połączenie. Za pomocą programu PowerShell usługi Azure AD nie można bezpośrednio skonfigurować preferowanej lokalizacji danych dla synchronizowanych użytkowników. Kroki konfigurowania pliku PDL [w usłudze](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation) Active Directory i synchronizowania go odano Azure Active Directory Połączenie synchronizacji: Konfigurowanie preferowanej lokalizacji danych dla Microsoft 365 zasobów.

Administrowanie dzierżawą wielolokacyjną może różnić się od dzierżawy wielodostępowej, ponieważ wiele SharePoint i OneDrive i usług jest wielowymiarowych. Przed rozpoczęciem konfiguracji zalecamy zapoznanie [](administering-a-multi-geo-environment.md) się ze środowiskiem administrowania środowiskiem wielowymiarowym.

Aby [uzyskać szczegółowe informacje o](multi-geo-user-experience.md) środowisku użytkowników końcowych w środowisku wielolokalowym, przeczytaj Środowisko użytkownika w środowisku z wieloma lokalizacjami geograficznymi.

Aby rozpocząć konfigurowanie usługi Microsoft 365 multi-Geo, zobacz Microsoft 365 [Multi-Geo](multi-geo-tenant-configuration.md).

Po ukończeniu konfiguracji pamiętaj, aby w razie potrzeby przeprowadzić migrację bibliotek OneDrive [użytkowników](move-onedrive-between-geo-locations.md), aby rozpocząć pracę z ich preferowanymi lokalizacjami danych.

## <a name="related-topics"></a>Tematy pokrewne

[Microsoft 365 multi-Geo eDiscovery configuration](./multi-geo-ediscovery-configuration.md)