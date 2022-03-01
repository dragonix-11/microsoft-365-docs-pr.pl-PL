---
title: Administrowanie środowiskiem wielolokalowym
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
description: Administratorzy mogą dowiedzieć się, jak administrować usługami SharePoint i OneDrive w środowisku wielolokalowym.
ms.openlocfilehash: 31d361b2936c3d7bceca7137499c659030717eba
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010602"
---
# <a name="administering-a-multi-geo-environment"></a>Administrowanie środowiskiem wielolokalowym

Poniżej opisano, jak działają Microsoft 365 w środowisku z wieloma lokalizacjami geograficznymi.

## <a name="administrator-experience"></a>Środowisko administratora

Centrum [administracyjne SharePoint](https://admin.microsoft.com/sharepoint) po lewej stronie zawiera kartę Lokalizacje geograficzne, która zawiera mapę lokalizacji geograficznych, na której można wyświetlać lokalizacje geograficzne i zarządzać nimi. Na tej stronie możesz dodawać lub usuwać lokalizacje geograficzne dzierżawcy.

## <a name="audit-log-search"></a>Przeszukiwanie dziennika inspekcji

Ujednolicony dziennik [inspekcji dla](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) wszystkich lokalizacji satelitarnych jest dostępny na Microsoft 365 przeszukiwania dziennika inspekcji. Możesz wyświetlić wszystkie wpisy dziennika inspekcji z różnych lokalizacji geograficznych, na przykład działania użytkowników usługi NAM & EUR będą wyświetlane w jednym widoku organizacji, a następnie możesz zastosować istniejące filtry, aby zobaczyć działania poszczególnych użytkowników.

> [!NOTE]
> Exchange inspekcji administratora są dostępne tylko dla lokalizacji domyślnej.

## <a name="bcs-secure-store-apps"></a>BCS, bezpieczny magazyn, aplikacje

Wszystkie usługi BCS, Secure Store i Aplikacje mają osobne wystąpienia w poszczególnych lokalizacjach satelitarnych, dlatego administrator usługi SharePoint Online powinien zarządzać tymi usługami i konfigurować je oddzielnie od poszczególnych lokalizacji satelitarnych.

## <a name="compliance-admin-center"></a>Centrum administracyjne zgodności

Istnieje jedno centralne centrum zgodności dla dzierżawy wielowymiarowej: centrum [administracyjne Microsoft 365 zgodności](https://compliance.microsoft.com/).

## <a name="ediscovery"></a>zbierania elektronicznych materiałów dowodowych

Domyślnie menedżer zbierania elektronicznych materiałów dowodowych lub administrator dzierżawy wielowymiarowej będzie mógł przeprowadzać zbierania elektronicznych materiałów dowodowych tylko w lokalizacji centralnej tej dzierżawy. Administrator globalny usługi Office 365 musi przypisać uprawnienia Menedżera zbierania elektronicznych materiałów dowodowych w celu umożliwienia innym osobom wykonywania zbierania elektronicznych materiałów dowodowych i przypisania parametru "Region" w obowiązującym filtrze zabezpieczeń zgodności w celu określenia regionu przeprowadzania zbierania elektronicznych materiałów dowodowych jako lokalizacji satelitarnej. W przeciwnym razie nie zostanie przeprowadzone zbierania elektronicznych materiałów dowodowych w lokalizacji satelitarnej. Aby skonfigurować filtr zabezpieczeń zgodności dla regionu, zobacz [Konfigurowanie zbierania elektronicznych Office 365 wielu lokalizacji geograficznych](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Exchange skrzynki pocztowe

Jeśli plik PDL Exchange jest automatycznie przenoszony, skrzynki pocztowe użytkowników są przenoszone automatycznie. Po utworzeniu nowej skrzynki pocztowej jest ona zapewniana do pliku PDL użytkownika lub do lokalizacji centralnej, jeśli dla pliku PDL użytkownika nie ustawiono żadnej wartości.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Zasady ochrony przed utratą danych (DLP, Information Protection)

Zasady ochrony przed zagrożeniami (DLP) adresów IP dla usług OneDrive dla Firm, SharePoint i Exchange można ustawić w centrum zabezpieczeń i zgodności, ustawiając zakres zasad w razie potrzeby dla całej dzierżawy lub dla odpowiednich użytkowników. Na przykład: Jeśli chcesz wybrać zasady dla użytkownika w lokalizacji satelitarnej, wybierz, aby zastosować zasady do określonego OneDrive i wprowadź adres URL OneDrive URL użytkownika. Zobacz [Omówienie zasad ochrony przed utratą danych,](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) aby uzyskać ogólne wskazówki dotyczące tworzenia zasad DLP.

Zasady DLP są automatycznie synchronizowane na podstawie ich stosowania do poszczególnych lokalizacji geograficznych.

Wdrażanie zasad ochrony informacji i ochrony przed utratą danych u wszystkich użytkowników w lokalizacji geograficznej nie jest opcją dostępną w interfejsie użytkownika. Zamiast tego należy wybrać odpowiednie konta dla tych zasad lub zastosować je globalnie do wszystkich kont.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

Power Apps utworzone dla lokalizacji satelitarnej będzie używać punktu końcowego znajdującego się w lokalizacji centralnej dzierżawy. Microsoft Power Apps nie jest usługą multi-geo. 

## <a name="power-automate"></a>Power Automate

Przepływy utworzone dla lokalizacji satelitarnej będą używać punktu końcowego znajdującego się w domyślnej lokalizacji geograficznej dzierżawy.  Power Automate nie jest usługą multilokalizacji. 

## <a name="sharepoint-storage-quota"></a>SharePoint przydziału miejsca do magazynowania

Domyślnie wszystkie lokalizacje geograficzne środowiska wielowymiarowego mają współużytowany przydział magazynowania dzierżawy.  Możesz także zarządzać przydziałem magazynowania, przydzielając określony przydział dla określonej lokalizacji geograficznej. Aby uzyskać więcej informacji, [SharePoint przydziały magazynowania w środowiskach wielolokalizacji](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Udostępnianie

Administratorzy mogą ustawiać zasady udostępniania i zarządzać nimi dla każdej ze swoich lokalizacji. Grupy OneDrive i SharePoint w poszczególnych lokalizacjach geograficznych będą honorować tylko odpowiednie ustawienia udostępniania specyficzne dla lokalizacji geograficznej. Możesz na przykład zezwolić na udostępnianie [zewnętrzne](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) dla twojej lokalizacji centralnej, ale nie na lokalizację satelitarną i na odwrót. Należy pamiętać, że ustawienia udostępniania nie umożliwiają konfigurowania ograniczeń udostępniania między lokalizacjami geograficznymi.

## <a name="stream"></a>Stream

Klipy wideo przekazane do streamowania w czacie 1:1 są przechowywane OneDrive stronie osoby, która je przekaże. Nagrania ze spotkań są przechowywane w OneDrive każdego uczestnika, który nagrywa spotkanie.

## <a name="taxonomy"></a>Taksonomia

Obsługujemy ujednoliconą [taksonomię](/sharepoint/managed-metadata) dla metadanych zarządzanych w przedsiębiorstwie w lokalizacjach geograficznych, a wzorzec jest hostowany w centralnej lokalizacji Twojej firmy. Zalecamy zarządzanie taksonomią globalną z lokalizacji centralnej i dodawanie do taksonomii lokalizacji satelitarnej tylko terminów specyficznych dla lokalizacji. Warunki taksonomii globalnej zostaną zsynchronizowane z lokalizacjami satelitarnmi.

Aby [uzyskać dodatkowe informacje i](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) wskazówki dla deweloperów, zobacz Zarządzanie metadanymi w dzierżawie wielodostępowej.

## <a name="user-profile-application"></a>Aplikacja profilu użytkownika

W każdej [lokalizacji geograficznej istnieje aplikacja](/sharepoint/manage-user-profiles) profilu użytkownika. Informacje o profilu każdego użytkownika są hostowane w jego lokalizacji geograficznej i dostępne dla administratora dla tej lokalizacji geograficznej.

Jeśli masz niestandardowe właściwości profilu, zalecamy używanie tego samego schematu profilu na obszarach geograficznych i wypełnianie niestandardowych właściwości profilu we wszystkich lokalizacjach geograficznych lub w razie potrzeby. Aby uzyskać wskazówki dotyczące programowego wypełniania danych profilu użytkownika, zobacz Interfejs API zbiorczej aktualizacji [profilu użytkownika](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Aby [uzyskać dodatkowe informacje i](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) wskazówki dla deweloperów, zobacz Praca z profilami użytkowników w dzierżawie wielodostępowej.

## <a name="yammer"></a>Yammer

Yammer nie jest obciążeniem wielowymiarowym. Yammer wątków przechowywanych Yammer będą umieszczane w centralnej lokalizacji dzierżawy. Yammer obecnie wprowadzana jest zmiana miejsca do magazynowania plików, która będzie przechowywać Yammer w SharePoint. Yammer przechowywanych w SharePoint zostaną umieszczone w witrynie SharePoint skojarzonej z tą Yammer grupy. SharePoint witryn grupy są oparte na logice PDL, jak opisano SharePoint [witryny i grupy](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
