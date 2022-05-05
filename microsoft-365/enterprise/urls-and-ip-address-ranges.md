---
title: Adresy URL i zakresy adresów IP usługi Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 04/28/2022
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
description: 'Podsumowanie: usługa Office 365 wymaga łączności z Internetem. Poniższe punkty końcowe powinny być osiągalne dla klientów korzystających z planów usługi Office 365, w tym dla chmury Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: 80e4c14652303d1f04e697f73153b0f013b987cd
ms.sourcegitcommit: b3f5fe84a319741583954ef8ff2ec9ec6da69bcf
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2022
ms.locfileid: "65217337"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Adresy URL i zakresy adresów IP usługi Office 365

Usługa Office 365 wymaga łączności z Internetem. Poniższe punkty końcowe powinny być osiągalne dla klientów korzystających z planów usługi Office 365, w tym dla chmury Government Community Cloud (GCC).
  
*Usługa Office 365 na całym świecie (+GCC)* \| [Usługa Office 365 obsługiwana przez firmę 21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Usługa Office 365 dla Departamentu Obrony Rządu USA](microsoft-365-u-s-government-dod-endpoints.md) \| [Usługa Office 365 dla GCC High Rządu USA](microsoft-365-u-s-government-gcc-high-endpoints.md) \|

|Uwagi|Pobierz|Opcja, której należy użyć|
|---|---|---|
|**Ostatnia aktualizacja:** 28.04.2022 – ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Subskrypcja dziennika zmian](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Pobieranie:** lista w [formacie JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) zawierająca wszystkie wymagane i opcjonalne adresy docelowe.|**Użyj:** [plików PAC](managing-office-365-endpoints.md#pacfiles) naszych serwerów proxy|
|

Zacznij od pozycji [Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md), aby zrozumieć nasze zalecenia dotyczące zarządzania łącznością sieciową przy użyciu tych danych. Dane punktów końcowych są aktualizowane zgodnie z potrzebami na początku każdego miesiąca przy użyciu nowych adresów IP i adresów URL opublikowanych 30 dni przed uaktywnieniem. Dzięki temu klienci, którzy nie mają jeszcze automatycznych aktualizacji, mogą ukończyć swoje procesy zanim będzie wymagana nowa łączność. Punkty końcowe mogą być również aktualizowane w ciągu miesiąca, jeśli jest to konieczne w celu realizacji eskalacji pomocy technicznej, zdarzeń zabezpieczeń lub innych natychmiastowych wymagań operacyjnych. Wszystkie dane wyświetlane na poniższej stronie są generowane na podstawie usług internetowych opartych na protokole REST. Jeśli do uzyskiwania dostępu do tych danych używasz skryptu lub urządzenia sieciowego, przejdź bezpośrednio do pozycji [Usługa sieci Web](microsoft-365-ip-web-service.md).

Poniższe dane punktu końcowego zawierają wymagania dotyczące łączności z komputera użytkownika do usługi Office 365. Aby uzyskać szczegółowe informacje na temat adresów IP używanych na potrzeby połączeń sieciowych z firmy Microsoft do sieci klienta, czasami nazywanych hybrydowymi lub przychodzącymi połączeniami sieciowymi, zobacz [Dodatkowe punkty końcowe](additional-office365-ip-addresses-and-urls.md), aby uzyskać więcej informacji.

Punkty końcowe są pogrupowane w cztery obszary usług reprezentujące trzy podstawowe obciążenia i zestaw wspólnych zasobów. Grupy mogą być używane do kojarzenia przepływów ruchu z określoną aplikacją, jednak biorąc pod uwagę, że funkcje często używają punktów końcowych w wielu obciążeniach, nie można skutecznie używać tych grup do ograniczania dostępu.

Wyświetlane kolumny danych to:

- **ID**: numer identyfikatora wiersza, znany również jako zestaw punktów końcowych. Ten identyfikator jest taki sam jak zwracany przez usługę sieci Web dla zestawu punktów końcowych.

- **Kategoria**: pokazuje, czy zestaw punktów końcowych jest przydzielony do kategorii „Optymalizuj”, „Zezwalaj” lub „Domyślne”. O tych kategoriach i wskazówkach dotyczących zarządzania nimi można przeczytać w temacie [Nowe kategorie punktów końcowych usługi Office 365](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). Ta kolumna zawiera również listę zestawów punktów końcowych wymaganych do łączności sieciowej. W przypadku zestawów punktów końcowych, które nie muszą mieć łączności sieciowej, w tym polu udostępniamy uwagi wskazujące, jakich funkcji brakowałoby w przypadku zablokowania zestawu punktów końcowych. Jeśli wykluczasz cały obszar usługi, zestawy punktów końcowych wymienione jako wymagane nie wymagają łączności.

- **ER**: jest to **Tak**, jeśli zestaw punktów końcowych jest obsługiwany przez usługę Azure ExpressRoute z prefiksami tras usługi Office 365. Społeczność BGP zawierająca wyświetlane prefiksy tras jest zgodna z wymienionym obszarem usługi. Gdy wartość ER to **Nie**, oznacza to, że usługa ExpressRoute nie jest obsługiwana dla tego zestawu punktów końcowych. Nie należy jednak zakładać, że żadne trasy nie są anonsowane dla zestawu punktów końcowych, w którym ER ma wartość **Nie**.

- **Adresy**: wyświetla listę nazw FQDN lub nazw domen z symbolami wieloznacznymi i zakresów adresów IP dla zestawu punktów końcowych. Należy pamiętać, że zakres adresów IP jest w formacie CIDR i może zawierać wiele pojedynczych adresów IP w określonej sieci.

- **Porty**: wyświetla listę portów TCP lub UDP połączonych z adresami w celu utworzenia punktu końcowego sieci. Możesz zauważyć pewne duplikowanie zakresów adresów IP, gdzie znajdują się różne porty.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> Aby zapoznać się z zaleceniami dotyczącymi adresów IP i adresów URL usługi Yammer, zobacz [Używanie zakodowanych na stałe adresów IP dla usługi Yammer nie jest zalecane](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592) w blogu usługi Yammer.

## <a name="related-topics"></a>Tematy pokrewne

[Dodatkowe punkty końcowe nieuwzględnione w adresach IP usługi Office 365 i usługi sieci Web adresów URL](additional-office365-ip-addresses-and-urls.md)

[Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md)

[Ogólne punkty końcowe usługi Microsoft Stream](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Monitorowanie łączności platformy Microsoft 365](./monitor-connectivity.md)

[Pakiet głównego i pośredniego urzędu certyfikacji w systemie aplikacji innej firmy](../compliance/encryption-office-365-certificate-chains.md)
  
[Łączność z klientami](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Sieci dostarczania zawartości](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Zakresy adresów IP i tagi usług platformy Microsoft Azure — chmura publiczna](https://www.microsoft.com/download/details.aspx?id=56519)

[Zakresy adresów IP i tagi usług platformy Microsoft Azure — chmura rządu USA](https://www.microsoft.com/download/details.aspx?id=57063)

[Zakresy adresów IP i tagi usług platformy Microsoft Azure — chmura w Chinach](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Przestrzeń publicznych adresów IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

[Nazwa usługi i rejestr numerów portów protokołu transportowego](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
