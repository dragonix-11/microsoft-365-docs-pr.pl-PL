---
title: Adresy URL i zakresy adresów IP usługi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Podsumowanie: Office 365 wymaga łączności z Internetem. Poniższe punkty końcowe powinny być osiągalne dla klientów korzystających z planów Office 365, w tym Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: 81f3f7ef203e9ed1e6d45e6139421b9a03057840
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "63009745"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Adresy URL i zakresy adresów IP usługi Office 365

Usługa Office 365 wymaga połączenia z Internetem. Poniższe punkty końcowe powinny być osiągalne dla klientów korzystających z planów Office 365, w tym Government Community Cloud (GCC).
  
*Office 365 Worldwide (+GCC)* \| [Office 365 obsługiwane przez firmę 21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) \|

|Uwagi|Pobierz|Opcja, której należy użyć|
|---|---|---|
|**Ostatnia aktualizacja:** 2022-01-28 — ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Subskrypcja dziennika zmian](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Pliki do pobrania:** wszystkie wymagane i opcjonalne miejsca docelowe na jednej liście [sformatowanych przy formacie JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) .|**Użyj: naszych** plików [PAC serwera proxy](managing-office-365-endpoints.md#pacfiles)|
|

Zacznij od [tematu Office 365 punktów końcowych,](managing-office-365-endpoints.md) aby zrozumieć nasze zalecenia dotyczące zarządzania łącznością sieciową przy użyciu tych danych. Na początku każdego miesiąca dane dotyczące punktów końcowych są aktualizowane przy użyciu nowych adresów IP i adresów URL opublikowanych 30 dni przed ich aktywnością. Dzięki temu klienci, którzy nie mają jeszcze automatycznych aktualizacji, mogą zakończyć swoje procesy, zanim będzie wymagana nowa łączność. W razie potrzeby punkty końcowe mogą być także aktualizowane w ciągu miesiąca, aby rozwiązać potrzeby dotyczące eskalacji pomocy technicznej, zdarzeń dotyczących zabezpieczeń lub innych natychmiastowych wymagań operacyjnych. Wszystkie dane pokazane na poniższej stronie są generowane z usług sieci Web opartych na u dołu. Jeśli uzyskujesz dostęp do tych danych za pomocą skryptu lub urządzenia sieciowego, przejdź [bezpośrednio do usługi](microsoft-365-ip-web-service.md) sieci Web.

Poniżej przedstawiono dane punktu końcowego z listą wymagań dotyczących łączności między komputerami Office 365. Aby uzyskać szczegółowe informacje na temat adresów IP używanych dla połączeń sieciowych firmy Microsoft do sieci klienta, nazywanych czasem hybrydowymi lub przychodzącymi połączeniami sieciowymi, zobacz Dodatkowe punkty końcowe, aby uzyskać więcej informacji.[](additional-office365-ip-addresses-and-urls.md)

Punkty końcowe są pogrupowane w cztery obszary usługi reprezentujące trzy podstawowe obciążenia pracą i zestaw zasobów wspólnych. Grup można używać do kojarzenia przepływów ruchu z określonej aplikacji, jednak jeśli funkcje często zużywają punkty końcowe w wielu obciążeniach pracą, nie można ich w praktyce używać do ograniczania dostępu.

Pokazane są kolumny danych:

- **Identyfikator**: Numer identyfikacyjny wiersza, nazywany również zestawem punktów końcowych. Ten identyfikator jest taki sam, jak jest zwracany przez usługę sieci Web dla zestawu punktów końcowych.

- **Kategoria**: Pokazuje, czy zestaw punktów końcowych jest kategoryzowany jako "Optymalizuj", "Zezwalaj" lub "Domyślny". Informacje na temat tych kategorii i wskazówek dotyczących zarządzania nimi można znaleźć w te Office 365 [kategorii punktów końcowych](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). W tej kolumnie wymieniono również zestawy punktów końcowych, które są wymagane do łączności sieciowej. W przypadku zestawów punktów końcowych, które nie są wymagane do łączności sieciowej, w tym polu są dostępne uwagi wskazujące, jakie funkcje byłyby brakujące w przypadku zablokowania zestawu punktów końcowych. Jeśli wykluczasz cały obszar usługi, zestawy punktów końcowych wymienione jako wymagane nie wymagają łączności.

- **ER**: Jest tak **, jeśli** zestaw punktów końcowych jest obsługiwany przez usługę Azure ExpressRoute Office 365 prefiksami tras. Społeczność BGP, która zawiera przedstawione prefiksy tras, jest wyrównana z wymienionym obszarem usługi. Gdy ER ma **wartość Nie**, oznacza to, że w tym zestawie punktów końcowych usługi ExpressRoute nie jest obsługiwana. Nie należy jednak zakładać, że żadne trasy nie są ogłaszane dla zestawu punktów końcowych, w którym ER ma wartość **Nie**.

- **Adresy**: Zawiera listę nazw FQDN lub nazw domen z symbolami wieloznacznych i zakresów adresów IP dla zestawu punktów końcowych. Zakres adresów IP jest w formacie CIDR i może zawierać wiele pojedynczych adresów IP w określonej sieci.

- **Porty**. Zawiera listę portów TCP lub UDP, które są połączone z adresami, aby stanowią punkt końcowy sieci. W zakresach adresów IP, w których znajdują się różne porty, możesz zauważyć pewne duplikaty.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> Aby uzyskać zalecenia Yammer adresów IP i adresów URL, zobacz Używanie kodów twardych adresów IP na Yammer [nie](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592) jest zalecane w blogu Yammer adresach IP.

## <a name="related-topics"></a>Tematy pokrewne

[Dodatkowe punkty końcowe, które nie są dostępne w usłudze Office 365 sieci Web adresów IP i adresów URL](additional-office365-ip-addresses-and-urls.md)

[Zarządzanie Office 365 punktami końcowymi](managing-office-365-endpoints.md)

[Ogólne punkty końcowe usługi Microsoft Stream](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Monitorowanie Microsoft 365 sieci](./monitor-connectivity.md)

[Główny urząd certyfikacji i pakiet pośredniczącego urzędu certyfikacji w systemie aplikacji innej firmy](../compliance/encryption-office-365-certificate-chains.md)
  
[Łączność z klientem](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Sieci dostarczania zawartości](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure zakresów adresów IP i tagów usług — chmura publiczna](https://www.microsoft.com/download/details.aspx?id=56519)

[Microsoft Azure zakresów adresów IP i tagów usług — US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063)

[Microsoft Azure zakresów adresów IP i tagów usług — chmura w Chinach](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Publiczny obszar adresów IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

[Rejestr numeru portu usługi i nazwy usługi (Transport Protocol Port Number)](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
