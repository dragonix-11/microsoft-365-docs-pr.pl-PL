---
title: Administrowanie środowiskiem usługi Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Administratorzy mogą dowiedzieć się, jak administrować usługami SharePoint i OneDrive w środowisku obejmującym wiele obszarów geograficznych.
ms.openlocfilehash: 155eea030cfa700a009805fb66aeb74eaae617d3
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949084"
---
# <a name="administering-a-multi-geo-environment"></a>Administrowanie środowiskiem usługi Multi-Geo

Poniżej przedstawiono sposób działania usług Microsoft 365 w środowisku obejmującym wiele obszarów geograficznych.

## <a name="administrator-experience"></a>Środowisko administratora

Centrum administracyjne SharePoint ma <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">kartę **Lokalizacje geograficzne**</a> w lewym pasku nawigacyjnym z mapą lokalizacji geograficznych, na której można wyświetlać lokalizacje geograficzne i zarządzać nimi. Ta strona służy do dodawania lub usuwania lokalizacji geograficznych dla dzierżawy.

## <a name="audit-log-search"></a>Przeszukiwanie dzienników inspekcji

Ujednolicony [dziennik inspekcji](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) dla wszystkich lokalizacji satelitarnych jest dostępny na stronie wyszukiwania dzienników inspekcji Microsoft 365. Możesz wyświetlić wszystkie wpisy dziennika inspekcji z różnych lokalizacji geograficznych, na przykład NAM & działania użytkowników EUR będą wyświetlane w jednym widoku organizacji, a następnie można zastosować istniejące filtry, aby wyświetlić działania określonego użytkownika.

> [!NOTE]
> Exchange zdarzenia inspekcji administratora są dostępne tylko dla lokalizacji domyślnej.

## <a name="bcs-secure-store-apps"></a>BCS, Bezpieczny sklep, Aplikacje

Wszystkie usługi BCS, Secure Store i Aplikacje mają oddzielne wystąpienia w każdej lokalizacji satelitarnej, dlatego administrator usługi SharePoint Online powinien zarządzać tymi usługami i konfigurować je oddzielnie od każdej lokalizacji satelitarnej.

## <a name="compliance-admin-center"></a>Centrum administracyjne zgodności

Istnieje jedno centralne centrum zgodności dla dzierżawy z wieloma lokalizacjami geograficznymi: [centrum administracyjne usługi Microsoft Purview](https://compliance.microsoft.com/).

## <a name="ediscovery"></a>Zbierania elektronicznych materiałów dowodowych

Domyślnie menedżer zbierania elektronicznych materiałów dowodowych lub administrator dzierżawy z wieloma obszarami geograficznymi będzie mógł przeprowadzać zbierania elektronicznych materiałów dowodowych tylko w centralnej lokalizacji tej dzierżawy. Administrator globalny Office 365 musi przypisać uprawnienia menedżera zbierania elektronicznych materiałów dowodowych, aby umożliwić innym osobom wykonywanie zbierania elektronicznych materiałów dowodowych i przypisać parametr "Region" w odpowiednim filtrze zabezpieczeń zgodności w celu określenia regionu do przeprowadzania zbierania elektronicznych materiałów dowodowych jako lokalizacji satelitarnej, w przeciwnym razie nie zostanie przeprowadzone żadne zbierania elektronicznych materiałów dowodowych dla lokalizacji satelitarnej. Aby skonfigurować filtr zabezpieczeń zgodności dla regionu, zobacz [Configure Office 365 Multi-Geo eDiscovery (Konfigurowanie zbierania elektronicznych elektronicznych materiałów dowodowych dla wielu obszarów geograficznych](multi-geo-ediscovery-configuration.md)).

## <a name="exchange-mailboxes"></a>skrzynki pocztowe Exchange

Skrzynki pocztowe Exchange użytkowników są przenoszone automatycznie po zmianie biblioteki PDL. Po utworzeniu nowej skrzynki pocztowej jest ona aprowizowana do biblioteki PDL użytkownika lub do centralnej lokalizacji, jeśli nie ustawiono żadnej wartości dla biblioteki PDL użytkownika.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>zasady ochrony przed utratą danych (DLP) Information Protection (IP)

Zasady DLP adresów IP można ustawić dla OneDrive dla Firm, SharePoint i Exchange w Centrum zabezpieczeń i zgodności, określając zakres zasad zgodnie z potrzebami dla całej dzierżawy lub odpowiednich użytkowników. Na przykład: jeśli chcesz wybrać zasady dla użytkownika w lokalizacji satelitarnej, wybierz, aby zastosować zasady do określonego OneDrive i wprowadzić adres URL OneDrive użytkownika. Aby uzyskać ogólne wskazówki dotyczące tworzenia zasad DLP [, zobacz Omówienie zasad ochrony przed utratą danych](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) .

Zasady DLP są automatycznie synchronizowane na podstawie ich zastosowania do każdej lokalizacji geograficznej.

Implementowanie zasad Information Protection i Microsoft Purview Data Loss Prevention dla wszystkich użytkowników w lokalizacji geograficznej nie jest opcją dostępną w interfejsie użytkownika, zamiast tego należy wybrać odpowiednie konta dla zasad lub zastosować zasady globalnie do wszystkich kont.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

Power Apps utworzona dla lokalizacji satelitarnej użyje punktu końcowego znajdującego się w centralnej lokalizacji dzierżawy. Microsoft Power Apps nie jest usługą multi-geo. 

## <a name="power-automate"></a>Power Automate

Przepływy utworzone dla lokalizacji satelitarnej będą używać punktu końcowego znajdującego się w domyślnej lokalizacji geograficznej dzierżawy.  Power Automate nie jest usługą multi-geo. 

## <a name="sharepoint-storage-quota"></a>limit przydziału magazynu SharePoint

Domyślnie wszystkie lokalizacje geograficzne środowiska z wieloma lokalizacjami geograficznymi współdzielą dostępny limit przydziału magazynu dzierżawy.  Możesz również zarządzać limitem przydziału magazynu, przydzielając określony limit przydziału dla określonej lokalizacji geograficznej. Aby uzyskać więcej informacji, zobacz [SharePoint limity przydziału magazynu w środowiskach z wieloma lokalizacjami geograficznymi](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Udostępnianie

Administratorzy mogą ustawiać zasady udostępniania i zarządzać nimi dla każdej ze swoich lokalizacji. Lokacje OneDrive i SharePoint w każdej lokalizacji geograficznej będą uwzględniać tylko odpowiednie ustawienia udostępniania specyficzne dla danego obszaru geograficznego. (Na przykład można zezwolić na [udostępnianie zewnętrzne](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) dla centralnej lokalizacji, ale nie dla lokalizacji satelitarnej lub odwrotnie). Pamiętaj, że ustawienia udostępniania nie zezwalają na konfigurowanie ograniczeń udostępniania między lokalizacjami geograficznymi.

## <a name="stream"></a>Stream

Filmy wideo przekazane do usługi Stream w ramach czatu 1:1 są przechowywane w OneDrive osoby przesyłającej. Nagrania spotkań są przechowywane w OneDrive każdego uczestnika, który rejestruje spotkanie.

## <a name="taxonomy"></a>Taksonomii

Obsługujemy ujednoliconą [taksonomię](/sharepoint/managed-metadata) dla metadanych zarządzanych przez przedsiębiorstwo w lokalizacjach geograficznych, a serwer główny jest hostowany w centralnej lokalizacji twojej firmy. Zalecamy zarządzanie globalną taksonomią z centralnej lokalizacji i dodawanie tylko terminów specyficznych dla lokalizacji do taksonomii lokalizacji satelitarnej. Globalne terminy taksonomii będą synchronizowane z lokalizacjami satelitarnymi.

Aby uzyskać dodatkowe informacje i wskazówki dla deweloperów, zobacz [Zarządzanie metadanymi w dzierżawie z wieloma lokalizacjami geograficznymi](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) .

## <a name="user-profile-application"></a>Aplikacja profilu użytkownika

W każdej lokalizacji geograficznej istnieje [aplikacja profilu użytkownika](/sharepoint/manage-user-profiles) . Informacje o profilu każdego użytkownika są hostowane w lokalizacji geograficznej i dostępne dla administratora dla tej lokalizacji geograficznej.

Jeśli masz niestandardowe właściwości profilu, zalecamy użycie tego samego schematu profilu w lokalizacjach geograficznych i wypełnienie właściwości profilu niestandardowego we wszystkich lokalizacjach geograficznych lub w razie potrzeby. Aby uzyskać wskazówki dotyczące programowego wypełniania danych profilu użytkownika, zapoznaj się z [interfejsem API zbiorczej aktualizacji profilu użytkownika](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Aby uzyskać dodatkowe informacje i wskazówki dla [deweloperów, zobacz Praca z profilami użytkowników w dzierżawie z wieloma lokalizacjami geograficznymi](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) .

## <a name="yammer"></a>Yammer

Yammer nie jest obciążeniem obejmującym wiele obszarów geograficznych. Yammer wątki przechowywane w Yammer zostaną umieszczone w centralnej lokalizacji dzierżawy. Yammer wprowadza zmianę magazynu plików, która będzie przechowywać pliki Yammer w SharePoint. Yammer plików przechowywanych w SharePoint zostanie umieszczona witryna SharePoint skojarzona z grupą Yammer. SharePoint lokacje grup są oparte na logice PDL zgodnie z opisem w [SharePoint Lokacje i grupy](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
