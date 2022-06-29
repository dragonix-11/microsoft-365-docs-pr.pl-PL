---
title: Microsoft 365 Multi-Geo
ms.reviewer: anfra
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
description: W tym artykule dowiesz się, jak rozszerzyć swoją obecność na platformie Microsoft 365 do wielu regionów geograficznych za pomocą usługi Microsoft 365 Multi-Geo.
ms.openlocfilehash: 154082785b71be8fbba55e00e2df8a1a3eacb500
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490215"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo

Dzięki rozwiązaniu Microsoft 365 Multi-Geo Twoja organizacja może rozszerzyć swoją obecność na platformie Microsoft 365 do wielu regionów geograficznych i/lub krajów w ramach istniejącej dzierżawy. Skontaktuj się ze swoim zespołem ds. konta Microsoft, aby zarejestrować firmę wielonarodową dla usługi Microsoft 365 Multi-Geo.
  
Za pomocą rozwiązania Microsoft 365 Multi-Geo można aprowizować i przechowywać dane magazynowane w lokalizacjach geograficznych wybranych w celu spełnienia wymagań dotyczących przechowywania danych, a jednocześnie odblokować globalne wdrożenie nowoczesnych środowisk produktywności dla pracowników.

Aby zapoznać się z wprowadzeniem wideo do usługi Microsoft 365 Multi-Geo, zobacz [SharePoint Online i OneDrive Multi-Geo, aby kontrolować, gdzie znajdują się dane](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>Architektura z wieloma lokalizacjami geograficznymi

W środowisku z wieloma lokalizacjami geograficznymi dzierżawa platformy Microsoft 365 składa się z centralnej lokalizacji (w której pierwotnie aprowizowano subskrypcję platformy Microsoft 365) i co najmniej jednej lokalizacji satelitarnej. W dzierżawie z wieloma lokalizacjami geograficznymi informacje o lokalizacjach geograficznych, grupach i informacjach o użytkownikach są opanowane w usłudze Azure Active Directory (Azure AD). Ponieważ informacje o dzierżawie są opanowane centralnie i synchronizowane z każdą lokalizacją geograficzną, udostępnianie i środowiska z udziałem wszystkich osób z twojej firmy zawierają globalną świadomość.

![Zrzut ekranu przedstawiający mapę z wieloma lokalizacjami geograficznymi z centrum administracyjnego programu SharePoint.](../media/multi-geo-world-map.png)

Należy pamiętać, że usługa Microsoft 365 Multi-Geo nie jest przeznaczona do optymalizacji wydajności. Jest ona zaprojektowana tak, aby spełniała wymagania dotyczące przechowywania danych. Aby uzyskać informacje na temat optymalizacji wydajności dla platformy Microsoft 365, zobacz [Planowanie sieci i dostrajanie wydajności dla platformy Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) lub skontaktuj się z grupą pomocy technicznej.

## <a name="terminology"></a>Terminologii

Poniżej przedstawiono kluczowe terminy używane podczas opisywania rozwiązania Microsoft 365 Multi-Geo:

- **Lokalizacja centralna** — lokalizacja geograficzna, w której pierwotnie aprowizowano dzierżawę.
- **Administrator geograficzny** — administrator, który może administrować co najmniej jedną określoną lokalizacją satelitarną.
- **Kod geograficzny** — trzyliterowy kod dla danej lokalizacji geograficznej.
- **Lokalizacja geograficzna** — lokalizacja geograficzna, której można używać w dzierżawie z wieloma lokalizacjami geograficznymi do hostowania danych, w tym skrzynek pocztowych programu Exchange oraz witryn usługi OneDrive i programu SharePoint.
- **Preferowana lokalizacja danych (PDL)** — właściwość użytkownika ustawiona przez administratora, która wskazuje lokalizację geograficzną, w której należy aprowizować skrzynkę pocztową programu Exchange użytkowników i usługę OneDrive. Biblioteka PDL określa również, gdzie są aprowizowane witryny programu SharePoint tworzone przez użytkownika.
- **Lokalizacja satelitarna** — lokalizacje geograficzne, w których obciążenia platformy Microsoft 365 z obsługą geograficzną (SharePoint, OneDrive i Exchange) są włączone w dzierżawie z wieloma lokalizacjami geograficznymi.
- **Dzierżawa** — reprezentacja organizacji w usłudze Microsoft 365, która zwykle ma co najmniej jedną domenę skojarzoną z nią (na przykład contoso.com).

## <a name="licensing"></a>Licencjonowanie

Usługa Microsoft 365 Multi-Geo jest dostępna jako dodatek do następujących planów subskrypcji platformy Microsoft 365 dla klientów Enterprise Agreement z co najmniej 250 miejscami na platformie Microsoft 365 w dzierżawie i co najmniej 5% tych miejsc korzystających z wielu obszarów geograficznych. Licencje subskrypcji użytkowników muszą być na tej samej Enterprise Agreement co licencje usługi Multi-Geo Services. Aby uzyskać szczegółowe informacje, skontaktuj się z zespołem ds. konta Microsoft.

- Microsoft 365 F1, F3, E3 lub E5
- Office 365 F3, E1, E3 lub E5
- Exchange Online plan 1 lub plan 2
- OneDrive dla Firm plan 1 lub plan 2
- Plan 1 lub plan 2 usługi SharePoint Online

Jeśli licencja zostanie przypisana do użytkownika, a później usunięta, dane czatu użytkownika usługi Teams zostaną przeniesione z powrotem do centralnej lokalizacji. Dane programu SharePoint i programu Exchange nie są przenoszone.

## <a name="microsoft-365-multi-geo-availability"></a>Dostępność wielu obszarów geograficznych platformy Microsoft 365

Usługa Microsoft 365 Multi-Geo jest obecnie oferowana w następujących regionach i krajach:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Wprowadzenie

Wykonaj następujące kroki, aby rozpocząć pracę z wieloma obszarami geograficznymi:

1. Skontaktuj się z zespołem ds. konta, aby dodać _możliwości wielu obszarów geograficznych w planie usługi Microsoft 365_ . Przeprowadzą Cię przez proces dodawania wymaganej liczby licencji. Funkcja Multi-Geo jest dostępna dla klientów z umową EA z co najmniej 250 subskrypcjami platformy Microsoft 365.

   Przed rozpoczęciem korzystania z usługi Microsoft 365 Multi-Geo firma Microsoft musi skonfigurować dzierżawę Exchange Online pod kątem obsługi wielu obszarów geograficznych. Ten jednorazowy proces konfiguracji jest wyzwalany po zamówieniu *funkcji wielu obszarów geograficznych w planie usługi Microsoft 365* , a licencje są wyświetlane w dzierżawie. Powiadomienia specyficzne dla obciążenia będą otrzymywane w [centrum komunikatów platformy Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) po zakończeniu procesu konfiguracji poszczególnych obciążeń przez dzierżawcę, a następnie możesz rozpocząć konfigurowanie i korzystanie z możliwości usługi Microsoft 365 Multi-Geo. Czas wymagany do skonfigurowania dzierżawy dla obsługi wielu obszarów geograficznych różni się w zależności od dzierżawy, ale większość dzierżaw kończy się w ciągu miesiąca od otrzymania licencji funkcji. Większe lub bardziej złożone dzierżawy mogą wymagać więcej czasu na ukończenie procesu konfiguracji. Skontaktuj się z zespołem ds. konta, aby uzyskać szczegółowe informacje na temat określonej dzierżawy, jeśli jej potrzebujesz.

2. Przeczytaj [Artykuł Planowanie środowiska z wieloma obszarami geograficznymi](plan-for-multi-geo.md).

3. Dowiedz się więcej na temat [administrowania środowiskiem z wieloma lokalizacjami geograficznymi](administering-a-multi-geo-environment.md) i [sposobu, w jaki użytkownicy będą doświadczać środowiska](multi-geo-user-experience.md).

4. Gdy wszystko będzie gotowe do skonfigurowania usługi Microsoft 365 Multi-Geo, [skonfiguruj dzierżawę pod kątem wielu obszarów geograficznych](multi-geo-tenant-configuration.md).

5. [Skonfiguruj wyszukiwanie](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Zobacz też

[Multi-Geo w Exchange Online i OneDrive](https://Aka.ms/GoMultiGeo)

[Możliwości wielu obszarów geograficznych w usłudze OneDrive i usłudze SharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[Możliwości wielu obszarów geograficznych w Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[Doświadczenie zespołów w środowisku z wieloma lokalizacjami geograficznymi](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
