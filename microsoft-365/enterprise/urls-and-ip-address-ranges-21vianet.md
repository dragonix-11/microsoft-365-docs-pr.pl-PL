---
title: Adresy URL i zakresy adresów IP dla usług Office 365 obsługiwanej przez firmę 21Vianet
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
ms.custom: seo-marvel-apr2020
f1.keywords:
- NOCSH
description: Ten artykuł zawiera listę adresów URL i zakresów adresów IP dla usługi Office 365 obsługiwanej przez firmę 21Vianet w Chinach.
hideEdit: true
ms.openlocfilehash: 8250fcddbc9b23317a0a3760b59c5f7776b98378
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "63009754"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>Adresy URL i zakresy adresów IP dla usług Office 365 obsługiwanej przez firmę 21Vianet

 *Dotyczy: Office 365 obsługiwane przez firmę 21Vianet — Small Business Admin, Office 365 obsługiwane przez firmę 21Vianet — Administrator*

Podsumowanie **: Następujące** punkty końcowe (nazwy FQDN, porty, adresy URL, prefiksy IPv4 i IPv6) dotyczą usługi Office 365 obsługiwanej przez firmę 21 Vianet i są zaprojektowane tak, aby dostarczać usługi zwiększające wydajność organizacjom korzystającym tylko z tych planów.
  
 **Office 365** punkty końcowe: Na całym świecie (w tym [GCC)](urls-and-ip-address-ranges.md)  | Office 365 obsługiwane przez firmę *21 Vianet* |  [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) |  [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |
  
**Ostatnia aktualizacja:** 2021-09-28 — ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Subskrypcja dziennika zmian](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

**Pliki do pobrania:** wszystkie wymagane i opcjonalne miejsca docelowe na jednej liście [sformatowanych przy formacie JSON](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) .

Zacznij od [tematu Office 365 punktów końcowych,](managing-office-365-endpoints.md) aby zrozumieć nasze zalecenia dotyczące zarządzania łącznością sieciową przy użyciu tych danych. Na początku każdego miesiąca dane dotyczące punktów końcowych są aktualizowane przy użyciu nowych adresów IP i adresów URL opublikowanych 30 dni przed ich aktywnością. Dzięki temu klienci, którzy nie mają jeszcze automatycznych aktualizacji, mogą zakończyć swoje procesy, zanim będzie wymagana nowa łączność. W razie potrzeby punkty końcowe mogą być także aktualizowane w ciągu miesiąca, aby rozwiązać potrzeby dotyczące eskalacji pomocy technicznej, zdarzeń dotyczących zabezpieczeń lub innych natychmiastowych wymagań operacyjnych. Wszystkie dane pokazane na poniższej stronie są generowane z usług sieci Web opartych na u dołu. Jeśli uzyskujesz dostęp do tych danych za pomocą skryptu lub urządzenia sieciowego, przejdź [bezpośrednio do usługi](microsoft-365-ip-web-service.md) sieci Web.

Poniżej przedstawiono dane punktu końcowego z listą wymagań dotyczących łączności między komputerami Office 365. Nie obejmuje ona połączeń sieciowych firmy Microsoft do sieci klienta, czasami nazywanych hybrydowymi lub przychodzącymi połączeniami sieciowymi.

Punkty końcowe są pogrupowane w cztery obszary usługi. Pierwsze trzy obszary usługi można niezależnie wybrać dla łączności. Czwarty obszar usługi jest wspólną zależnością (o nazwie Microsoft 365 Common i Office) i musi zawsze mieć łączność sieciową.

Pokazane są kolumny danych:

- **Identyfikator**: Numer identyfikacyjny wiersza, nazywany również zestawem punktów końcowych. Ten identyfikator jest taki sam, jak jest zwracany przez usługę sieci Web dla zestawu punktów końcowych.

- **Kategoria**: Pokazuje, czy zestaw punktów końcowych jest kategoryzowany jako "Optymalizuj", "Zezwalaj" lub "Domyślny". Informacje na temat tych kategorii i wskazówek dotyczących zarządzania nimi można znaleźć na stronie [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). W tej kolumnie wymieniono również zestawy punktów końcowych, które są wymagane do łączności sieciowej. W przypadku zestawów punktów końcowych, które nie są wymagane do łączności sieciowej, w tym polu są dostępne uwagi wskazujące, jakie funkcje byłyby brakujące w przypadku zablokowania zestawu punktów końcowych. Jeśli wykluczasz cały obszar usługi, zestawy punktów końcowych wymienione jako wymagane nie wymagają łączności.

- **ER**: Jest tak **, jeśli** zestaw punktów końcowych jest obsługiwany przez usługę Azure ExpressRoute Office 365 prefiksami tras. Społeczność BGP, która zawiera przedstawione prefiksy tras, jest wyrównana z wymienionym obszarem usługi. Gdy ER ma **wartość Nie**, oznacza to, że w tym zestawie punktów końcowych usługi ExpressRoute nie jest obsługiwana. Nie należy jednak zakładać, że żadne trasy nie są ogłaszane dla zestawu punktów końcowych, w którym ER ma wartość **Nie**.

- **Adresy**: Zawiera listę nazw FQDN lub nazw domen z symbolami wieloznacznych i zakresów adresów IP dla zestawu punktów końcowych. Zakres adresów IP jest w formacie CIDR i może zawierać wiele pojedynczych adresów IP w określonej sieci.
 
- **Porty**. Zawiera listę portów TCP lub UDP, które są połączone z adresami, aby stanowią punkt końcowy sieci. W zakresach adresów IP, w których znajdują się różne porty, możesz zauważyć pewne duplikaty.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]