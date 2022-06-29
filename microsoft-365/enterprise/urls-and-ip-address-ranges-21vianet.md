---
title: Adresy URL i zakresy adresów IP dla Office 365 obsługiwanych przez firmę 21Vianet
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/01/2022
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
description: Ten artykuł zawiera listę adresów URL i zakresów adresów IP dla Office 365 obsługiwanych przez firmę 21Vianet w Chinach.
hideEdit: true
ms.openlocfilehash: e99a89e511faef069f0856e046ea1898e896b3c1
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489908"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>Adresy URL i zakresy adresów IP dla Office 365 obsługiwanych przez firmę 21Vianet

 *Dotyczy: Office 365 obsługiwany przez firmę 21Vianet — Small Business Administracja, Office 365 obsługiwany przez firmę 21Vianet - Administracja*

Podsumowanie: Następujące punkty końcowe (nazwy FQDN, porty, **adresy** URL, prefiksy IPv4 i IPv6) mają zastosowanie do Office 365 obsługiwanych przez sieć Vianet 21 i są przeznaczone do dostarczania usług produktywności organizacjom korzystającym tylko z tych planów.
  
 **Office 365 punkty końcowe:** [Na całym świecie (w tym GCC)](urls-and-ip-address-ranges.md)  | *Office 365 obsługiwane przez 21 Vianet* |  [Office 365 Us Government DoD](microsoft-365-u-s-government-dod-endpoints.md) |  [Office 365 Us Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |
  
**Ostatnia aktualizacja:** 01.06.2022 r. — ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Subskrypcja dziennika zmian](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

**Pobieranie:** lista w [formacie JSON](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) zawierająca wszystkie wymagane i opcjonalne adresy docelowe.

Zacznij od pozycji [Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md), aby zrozumieć nasze zalecenia dotyczące zarządzania łącznością sieciową przy użyciu tych danych. Dane punktów końcowych są aktualizowane zgodnie z potrzebami na początku każdego miesiąca przy użyciu nowych adresów IP i adresów URL opublikowanych 30 dni przed uaktywnieniem. Dzięki temu klienci, którzy nie mają jeszcze automatycznych aktualizacji, mogą ukończyć swoje procesy zanim będzie wymagana nowa łączność. Punkty końcowe mogą być również aktualizowane w ciągu miesiąca, jeśli jest to konieczne w celu realizacji eskalacji pomocy technicznej, zdarzeń zabezpieczeń lub innych natychmiastowych wymagań operacyjnych. Wszystkie dane wyświetlane na poniższej stronie są generowane na podstawie usług internetowych opartych na protokole REST. Jeśli do uzyskiwania dostępu do tych danych używasz skryptu lub urządzenia sieciowego, przejdź bezpośrednio do pozycji [Usługa sieci Web](microsoft-365-ip-web-service.md).

Poniżej wymieniono wymagania dotyczące łączności z maszyny użytkownika do Office 365. Nie obejmuje ona połączeń sieciowych firmy Microsoft z siecią klienta, czasami nazywanych połączeniami sieciowymi hybrydowymi lub przychodzącymi.

Punkty końcowe są pogrupowane w cztery obszary usług. Pierwsze trzy obszary usług można niezależnie wybrać na potrzeby łączności. Czwarty obszar usługi jest wspólną zależnością (o nazwie Microsoft 365 Common i Office) i musi zawsze mieć łączność sieciową.

Wyświetlane kolumny danych to:

- **ID**: numer identyfikatora wiersza, znany również jako zestaw punktów końcowych. Ten identyfikator jest taki sam jak zwracany przez usługę sieci Web dla zestawu punktów końcowych.

- **Kategoria**: pokazuje, czy zestaw punktów końcowych jest skategoryzowany jako "Optymalizuj", "Zezwalaj" lub "Domyślny". Informacje o tych kategoriach i wskazówki dotyczące zarządzania nimi można znaleźć na stronie [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Ta kolumna zawiera również listę zestawów punktów końcowych wymaganych do łączności sieciowej. W przypadku zestawów punktów końcowych, które nie muszą mieć łączności sieciowej, w tym polu udostępniamy uwagi wskazujące, jakich funkcji brakowałoby w przypadku zablokowania zestawu punktów końcowych. Jeśli wykluczasz cały obszar usługi, zestawy punktów końcowych wymienione jako wymagane nie wymagają łączności.

- **ER**: jest to **Tak**, jeśli zestaw punktów końcowych jest obsługiwany przez usługę Azure ExpressRoute z prefiksami tras usługi Office 365. Społeczność BGP zawierająca wyświetlane prefiksy tras jest zgodna z wymienionym obszarem usługi. Gdy wartość ER to **Nie**, oznacza to, że usługa ExpressRoute nie jest obsługiwana dla tego zestawu punktów końcowych. Nie należy jednak zakładać, że żadne trasy nie są anonsowane dla zestawu punktów końcowych, w którym ER ma wartość **Nie**.

- **Adresy**: wyświetla listę nazw FQDN lub nazw domen z symbolami wieloznacznymi i zakresów adresów IP dla zestawu punktów końcowych. Należy pamiętać, że zakres adresów IP jest w formacie CIDR i może zawierać wiele pojedynczych adresów IP w określonej sieci.
 
- **Porty**: wyświetla listę portów TCP lub UDP połączonych z adresami w celu utworzenia punktu końcowego sieci. Możesz zauważyć pewne duplikowanie zakresów adresów IP, gdzie znajdują się różne porty.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]