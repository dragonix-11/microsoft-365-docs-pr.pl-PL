---
title: Microsoft 365 multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: W tym artykule dowiesz się, jak rozszerzyć swoją obecność Microsoft 365 do wielu regionów geograficznych dzięki Microsoft 365 wielu lokalizacji geograficznych.
ms.openlocfilehash: 5122979fc79ce9aebe542a80ed614e7dcad70d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986414"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 multi-Geo

Dzięki Microsoft 365 wielolokalizacji organizacja może rozszerzyć swoją obecność Microsoft 365 o wiele regionów geograficznych i/lub krajów w ramach istniejącej dzierżawy. Słaniej zespół konta Microsoft, aby zarejestrować swoją wielonarodową firmę Microsoft 365 Multi-Geo.
  
Za pomocą usługi Microsoft 365 Multi-Geo możesz zapewniać i przechowywać dane w spoczynku w lokalizacjach geograficznych wybranych do spełnienia wymagań dotyczących przechowywania danych, a jednocześnie odblokować twoje globalne udostępnianie nowoczesnego środowiska zwiększającego produktywność Twoim pracownikom.

Aby uzyskać klip wideo wprowadzający do Microsoft 365 multi-Geo, zobacz SharePoint Online i OneDrive Multi-Geo, aby kontrolować[, gdzie znajdują się Twoje dane](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>Architektura wielu lokalizacji geograficznych

W środowisku z wieloma lokalizacjami geograficznymi dzierżawa usługi Microsoft 365 składa się z lokalizacji centralnej (w której pierwotnie Microsoft 365 subskrypcję usługi Microsoft 365) i co najmniej jednej lokalizacji satelitarnej. W dzierżawie wielowymiarowej informacje o lokalizacjach geograficznych, grupach i informacjach o użytkownikach są mastered w usłudze Azure Active Directory (Azure AD). Informacje o dzierżawie są centralnie opanujone i synchronizowane z każdą lokalizacją geograficzną, dlatego udostępnianie i doświadczenia dotyczące wszystkich osób z Twojej firmy zawierają informacje globalne.

![Zrzut ekranu przedstawiający mapę wielowymiarową z SharePoint administracyjnego.](../media/multi-geo-world-map.png)

Pamiętaj, Microsoft 365 multi-Geo nie jest przeznaczona do optymalizacji wydajności, jest ona przeznaczona do spełnienia wymagań dotyczących przechowywania danych. Aby uzyskać informacje na temat optymalizacji wydajności dla Microsoft 365, zobacz Planowanie sieci i dostosowywanie wydajności dla sieci [Microsoft 365 lub skontaktuj](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) się z grupą pomocy technicznej.

## <a name="terminology"></a>Terminologia

Oto najważniejsze terminy używane w opisywania Microsoft 365 wielolokalizacji:

- **Lokalizacja centralna** — lokalizacja geograficzna, w której pierwotnie aprowizacji obsługi administracyjnej dzierżawy.
- **Administrator lokalizacji geograficznej** — administrator, który może administrować jedną lub większą ich lokalizacją satelitarną.
- **Kod geograficzny** — trzyliterowy kod dla danej lokalizacji geograficznej.
- **Lokalizacja geograficzna** — lokalizacja geograficzna, która może być używana w dzierżawie wielodostępowej do hostowania danych, w tym Exchange skrzynek pocztowych oraz skrzynek OneDrive i SharePoint witrynach.
- **Preferowana lokalizacja danych (PDL)** — właściwość użytkownika ustawiona przez administratora, wskazująca lokalizację geograficzną, w której użytkownicy Exchange skrzynkę pocztową i OneDrive mają być aprowizacji. Plik PDL określa również, SharePoint są aprowowane witryny utworzone przez użytkownika.
- **Lokalizacja satelitarna** — lokalizacje geograficzne, w których obciążenia Microsoft 365 geograficzne (SharePoint, OneDrive i Exchange) są włączone w dzierżawie wielodostępowej.
- **Dzierżawa** — reprezentacja organizacji w programie Microsoft 365 z którą zwykle jest skojarzona co najmniej jedna domena (na przykład contoso.com).

## <a name="licensing"></a>Licencjonowanie

Microsoft 365 Multi-Geo jest dostępna jako dodatek dla następujących planów subskrypcji usługi Enterprise Agreement Microsoft 365 dla klientów korzystających z co najmniej 250 Microsoft 365 stanowisk w ich dzierżawie i co najmniej 5% stanowisk z wieloma lokalizacjami geograficznymi. Licencje subskrypcji użytkowników muszą znajdować się w tym samym Enterprise Agreement co licencje multi-Geo Services. Aby uzyskać szczegółowe informacje, skontaktuj się ze swoim zespołem obsługi konta Microsoft.

- Microsoft 365 F1, F3, E3 lub E5
- Office 365 F3, E1, E3 lub E5
- Exchange Online Plan 1 lub Plan 2
- OneDrive dla Firm Plan 1 lub Plan 2
- SharePoint Online (plan 1) lub Plan 2

Jeśli licencja została przypisana do użytkownika, a później usunięta, Teams danych czatu użytkownika są w kolejce, aby przenieść je z powrotem do lokalizacji centralnej. SharePoint i Exchange nie są przenoszone.

## <a name="microsoft-365-multi-geo-availability"></a>Microsoft 365 dostępność dla wielu lokalizacji geograficznych

Microsoft 365 usługi Multi-Geo są obecnie oferowane w tych regionach i krajach:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Wprowadzenie

Aby rozpocząć pracę z wieloma lokalizacjami geograficznymi, wykonaj następujące czynności:

1. We współpracy z zespołem klienta dodaj funkcje _Multi-Geo Capabilities Microsoft 365_ plan usługi. Pomoże Ci dodać liczbę potrzebnych licencji. Funkcja multi-Geo jest dostępna dla klientów z ea o co najmniej 250 Microsoft 365 subskrypcji.

   Przed rozpoczęciem korzystania z usługi Microsoft 365 Multi-Geo firma Microsoft musi skonfigurować Exchange Online na potrzeby obsługi wielu lokalizacji geograficznych. Ten proces konfiguracji jest wyzwalany po zamówieniu funkcji *Multi-Geo Capabilities* w Microsoft 365 usług i licencji, które są wyświetlane w dzierżawie. Po ukończeniu procesu konfiguracji dzierżawcy dla każdego obciążenia pracą otrzymasz w centrum wiadomości usługi Microsoft 365 powiadomienia dotyczące obciążenia pracą, [Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) następnie możesz rozpocząć konfigurowanie i używanie funkcji multi-Geo. Czas wymagany do skonfigurowania dzierżawy do obsługi wielu lokalizacji geograficznych różni się w zależności od dzierżawy, ale większość dzierżaw kończy się w ciągu miesiąca po otrzymaniu licencji funkcji. Większe lub bardziej złożone dzierżawy mogą wymagać więcej czasu na ukończenie procesu konfiguracji. Aby uzyskać szczegółowe informacje na temat konkretnej dzierżawy, należy skontaktować się z zespołem klienta.

2. Przeczytaj [Planowanie środowiska wielowymiarowego](plan-for-multi-geo.md).

3. Dowiedz się [, jak administrować środowiskiem wielolokalowym](administering-a-multi-geo-environment.md) i [jak użytkownicy będą go doświadczać](multi-geo-user-experience.md).

4. Gdy wszystko będzie gotowe do skonfigurowania usługi Microsoft 365-wielu lokalizacji geograficznych, skonfiguruj dzierżawę [do korzystania z wielu lokalizacji geograficznych](multi-geo-tenant-configuration.md).

5. [Konfigurowanie wyszukiwania](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Zobacz też

[Multi-Geo in Exchange Online and OneDrive](https://Aka.ms/GoMultiGeo)

[Funkcje multi-Geo Capabilities OneDrive i SharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[Funkcje multi-Geo Capabilities w Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[Teams środowiska wielowymiarowego](/microsoftteams/teams-experience-o365odb-spo-multi-geo)