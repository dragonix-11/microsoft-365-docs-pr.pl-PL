---
title: Punkty końcowe usługi Office 365 U.S. Government GCC High
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 02/28/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: W tym artykule znajdziesz punkty końcowe dostępne dla klientów korzystających z planów Office 365 Us Government GCC High.
hideEdit: true
ms.openlocfilehash: a3bd1040ee264db5b389aea302c3a6acacbd4f1f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094709"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Punkty końcowe usługi Office 365 U.S. Government GCC High

*Dotyczy: Office 365 Admin*

Usługa Office 365 wymaga połączenia z Internetem. Poniższe punkty końcowe powinny być dostępne tylko dla klientów korzystających z planów Office 365 Us Government GCC High.
  
 **Office 365 punkty końcowe:** [Na całym świecie (w tym GCC)](urls-and-ip-address-ranges.md) \| [Office 365 obsługiwane przez 21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 Us Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| *Office 365 Us Government GCC High*

<br>

****

|Uwagi|Pobierz|
|---|---|
|**Ostatnia aktualizacja:** 28/02/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Subskrypcja dziennika zmian](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Pobierz:** pełna lista w [formacie JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

 Zacznij od pozycji [Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md), aby zrozumieć nasze zalecenia dotyczące zarządzania łącznością sieciową przy użyciu tych danych. Dane punktów końcowych są aktualizowane zgodnie z potrzebami na początku każdego miesiąca przy użyciu nowych adresów IP i adresów URL opublikowanych 30 dni przed uaktywnieniem. Dzięki temu klienci, którzy nie mają jeszcze automatycznych aktualizacji, mogą ukończyć swoje procesy, zanim będzie wymagana nowa łączność. Punkty końcowe mogą być również aktualizowane w ciągu miesiąca, jeśli jest to konieczne w celu realizacji eskalacji pomocy technicznej, zdarzeń zabezpieczeń lub innych natychmiastowych wymagań operacyjnych. Wszystkie dane wyświetlane na poniższej stronie są generowane na podstawie usług internetowych opartych na protokole REST. Jeśli do uzyskiwania dostępu do tych danych używasz skryptu lub urządzenia sieciowego, przejdź bezpośrednio do pozycji [Usługa sieci Web](microsoft-365-ip-web-service.md).

Poniżej wymieniono wymagania dotyczące łączności z maszyny użytkownika do Office 365. Nie obejmuje ona połączeń sieciowych firmy Microsoft z siecią klienta, czasami nazywanych połączeniami sieciowymi hybrydowymi lub przychodzącymi.

Punkty końcowe są pogrupowane w cztery obszary usług. Pierwsze trzy obszary usług można niezależnie wybrać na potrzeby łączności. Czwarty obszar usługi jest wspólną zależnością (nazywaną Microsoft 365 Common i Office) i musi zawsze mieć łączność sieciową.

Wyświetlane kolumny danych to:

- **ID**: numer identyfikatora wiersza, znany również jako zestaw punktów końcowych. Ten identyfikator jest taki sam jak zwracany przez usługę sieci Web dla zestawu punktów końcowych.

- **Kategoria**: pokazuje, czy zestaw punktów końcowych jest skategoryzowany jako "Optymalizuj", "Zezwalaj" lub "Domyślny". Informacje o tych kategoriach i wskazówki dotyczące zarządzania nimi można znaleźć na stronie [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Ta kolumna zawiera również listę zestawów punktów końcowych wymaganych do łączności sieciowej. W przypadku zestawów punktów końcowych, które nie muszą mieć łączności sieciowej, w tym polu udostępniamy uwagi wskazujące, jakich funkcji brakowałoby w przypadku zablokowania zestawu punktów końcowych. Jeśli wykluczasz cały obszar usługi, zestawy punktów końcowych wymienione jako wymagane nie wymagają łączności.

- **ER**: jest to **Tak**, jeśli zestaw punktów końcowych jest obsługiwany przez usługę Azure ExpressRoute z prefiksami tras usługi Office 365. Społeczność BGP zawierająca wyświetlane prefiksy tras jest zgodna z wymienionym obszarem usługi. Gdy wartość ER to **Nie**, oznacza to, że usługa ExpressRoute nie jest obsługiwana dla tego zestawu punktów końcowych. Nie należy jednak zakładać, że żadne trasy nie są anonsowane dla zestawu punktów końcowych, w którym ER ma wartość **Nie**. Jeśli planujesz używać usługi Azure AD Połączenie, przeczytaj [sekcję poświęconą zagadnieniom specjalnym](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government), aby upewnić się, że masz odpowiednią konfigurację Połączenie usługi Azure AD.

- **Adresy**: wyświetla listę nazw FQDN lub nazw domen z symbolami wieloznacznymi i zakresów adresów IP dla zestawu punktów końcowych. Należy pamiętać, że zakres adresów IP jest w formacie CIDR i może zawierać wiele pojedynczych adresów IP w określonej sieci.

- **Porty**: wyświetla listę portów TCP lub UDP połączonych z adresami w celu utworzenia punktu końcowego sieci. Możesz zauważyć pewne duplikowanie zakresów adresów IP, gdzie znajdują się różne porty.

[!INCLUDE [Office 365 U.S. Government GCC High endpoints](../includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Uwagi dotyczące tej tabeli:

- Centrum zabezpieczeń i zgodności (SCC) zapewnia obsługę usługi Azure ExpressRoute dla Office 365. To samo dotyczy wielu funkcji udostępnianych za pośrednictwem SCC, takich jak raportowanie, inspekcja, zbieranie elektronicznych materiałów dowodowych (Premium), unified DLP i zarządzanie danymi. Dwie konkretne funkcje, PST Import i eDiscovery Export, obecnie nie obsługują usługi Azure ExpressRoute tylko Office 365 filtrów tras ze względu na ich zależność od Azure Blob Storage. Aby korzystać z tych funkcji, potrzebujesz oddzielnej łączności z Azure Blob Storage przy użyciu dowolnych obsługiwanych opcji łączności platformy Azure, które obejmują łączność z Internetem lub usługę Azure ExpressRoute z filtrami tras publicznych platformy Azure. Należy ocenić ustanowienie takiej łączności dla obu tych funkcji. Zespół Office 365 Information Protection jest świadomy tego ograniczenia i aktywnie pracuje nad obsługą usługi Azure ExpressRoute dla Office 365 ograniczony do Office 365 filtrów tras dla obu tych funkcji.

- Istnieją dodatkowe opcjonalne punkty końcowe dla Aplikacje Microsoft 365 dla przedsiębiorstw, które nie są wymienione i nie są wymagane, aby użytkownicy uruchamiali Aplikacje Microsoft 365 dla przedsiębiorstw aplikacje i edytowali dokumenty. Opcjonalne punkty końcowe są hostowane w centrach danych firmy Microsoft i nie przetwarzają, nie przesyłają ani nie przechowują danych klientów. Zalecamy, aby połączenia użytkowników z tymi punktami końcowymi były kierowane do domyślnego obwodu ruchu wychodzącego z Internetu.
