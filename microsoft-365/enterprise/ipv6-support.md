---
title: Obsługa protokołu IPv6 w usługach Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/03/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Podsumowanie: Opisuje obsługę protokołu IPv6 w składnikach Microsoft 365 i w ofertach Microsoft 365 dla instytucji rządowych.'
ms.openlocfilehash: 6cd53b71c6e15346d4940c539eea4aff0e5a613e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096485"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Obsługa protokołu IPv6 w usługach Microsoft 365

Microsoft 365 obsługuje zarówno protokół IPv6, jak i IPv4. Jednak nie wszystkie funkcje Microsoft 365 są w pełni włączone w usłudze IPv6. Oznacza to, że do nawiązania połączenia z Microsoft 365 należy użyć zarówno protokołu IPv4, jak i protokołu IPv6. Jeśli filtrujesz ruch wychodzący do Microsoft 365, pełną listę adresów IPv6 obsługiwanych przez Microsoft 365 można znaleźć w artykule [Microsoft 365 adresów URL i zakresów adresów IP](urls-and-ip-address-ranges.md). Po skonfigurowaniu sieci i dozwolonych odpowiednich adresach IPv6 możesz pobrać [plan testów Microsoft 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) z Centrum pobierania Microsoft.

> [!NOTE]
> Umożliwienie klientom ekscesowania usług SaaS Microsoft 365 z dowolnej lokalizacji i dowolnego urządzenia jest priorytetem dla firmy Microsoft. Obejmuje to umożliwienie klientom nawiązywania połączeń i korzystania z Microsoft 365 z włączonych protokołu IPv6 i tylko klientów i systemów informacyjnych IPv6. Obejmuje to również umożliwienie klientom rządowym spełnienia zobowiązań IPv6 w ich sieciach przy jednoczesnym kontynuowaniu korzystania Microsoft 365 scenariuszy produktywności bez żadnych przerw.  
> Ten artykuł zawiera listę Microsoft 365 usług SaaS, które umożliwiają bezpośrednie połączenia IPv6 już dziś. Oczekuje się, że zakres usług umożliwiających bezpośrednią łączność IPv6 będzie nadal rozszerzany. Microsoft 365 usług, które nie są jawnie wymienione na potrzeby bezpośredniej obsługi protokołu IPv6 w celu uwzględnienia usług uwierzytelniania Azure Active Directory (AAD), należy uznać za wymagające połączenia DNS64/NAT64 tylko z klientów i środowisk protokołu IPv6.  Jest to zgodne z intencją opisaną obecnie w istniejącej dokumentacji NIST USGv6: Wymagania dotyczące możliwości mechanizmu przejścia w [specjalnej publikacji NIST 500-267A Poprawka 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 są akceptowalnymi technologiami do zastosowań.
> - Obsługa NAT64 dla mechanizmu przejścia NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Stanowy NAT64: Adres sieciowy i tłumaczenie protokołów z klientów IPv6 na serwery IPv4
> - Obsługa systemu DNS64 dla mechanizmu przejścia DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: Rozszerzenia DNS dla tłumaczenia adresów sieciowych z klientów IPv6 na serwer IPv4

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>Obsługa protokołu IPv6 w usłudze subskrypcji Microsoft 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online i IPv6

Jeśli program używany do nawiązywania połączenia z Exchange Online obsługuje protokół IPv6, domyślnie będzie używać protokołu IPv6 zarówno w sieciach przewodowych, jak i bezprzewodowych. Jeśli chcesz kontrolować komunikację w celu Exchange Online, użyj zakresów adresów IP w [Microsoft 365 adresach URL i zakresach adresów IP](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online i IPv6

 **Microsoft 365 Government G1/G3/G4/K1** Jeśli program używany do nawiązywania połączenia z usługą SharePoint Online obsługuje protokół IPv6, domyślnie spróbuje użyć protokołu IPv6.
  
 **Chmura z wieloma dzierżawami publicznymi** Firma Microsoft włącza SharePoint Online IPv6 na żądanie. Musisz podać adresy IP notowane cidr dla infrastruktury DNS organizacji. Należy pamiętać, że ta infrastruktura DNS nie może być współużytkowana przez inne organizacje w celu włączenia protokołu IPv6 dla dzierżawy. Po włączeniu protokołu IPv6, jeśli program używany do nawiązywania połączenia z usługą SharePoint Online obsługuje protokół IPv6, domyślnie używa protokołu IPv6.
  
Jeśli program używany do nawiązywania połączenia z usługą SharePoint Online obsługuje protokół IPv6, domyślnie będzie używać protokołu IPv6 zarówno w sieciach przewodowych, jak i bezprzewodowych. Jeśli chcesz kontrolować komunikację z usługą SharePoint Online, użyj zakresów adresów IP w [Microsoft 365 adresach URL i zakresach adresów IP](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype dla firm i IPv6

Pamiętaj, że protokół IPv6 nie jest obsługiwany w Skype dla firm i nie można go już włączyć.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams, SIP Gateway i IPV6

Microsoft Teams routing bezpośredni i brama SIP obsługują tylko protokół IPv4. Usługa Microsoft Teams i klient obsługują zarówno protokół IPv4, jak i IPv6. Jeśli chcesz kontrolować komunikację w celu Microsoft Teams, użyj zakresów adresów IP w [Microsoft 365 adresach URL i zakresach adresów IP](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection i IPv6

Exchange Online Protection (EOP) obsługuje protokół IPv6, jeśli transmisja odbywa się za pośrednictwem protokołu Transport Layer Security Protocol. W przypadku zakresu EOP użyj [Microsoft 365 adresów URL i zakresów adresów IP](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>Obsługa protokołu IPv6 dla ofert Microsoft 365 dla instytucji rządowych

Microsoft 365 wsparcie IPv6 dla ofert rządowych jest zgodne z protokołem Office zarządzania i budżetu (OMB) dla dyrektorów ds. informacji dyrektorów departamentów i agencji wykonawczych, a także z przyjęciem protokołu internetowego w wersji 6 (IPv6) przez rząd federalny. [Microsoft Microsoft 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) to wielodostępna usługa, która przechowuje dane instytucji rządowych USA w oddzielnej chmurze społeczności. Podobnie jak inne oferty Microsoft 365, oferuje usługi produktywności i współpracy, w tym Exchange Online, Skype dla firm, SharePoint Online i Aplikacje Microsoft 365 dla przedsiębiorstw. 

Oferty microsoft Microsoft 365 dla instytucji rządowych mają zastosowanie tylko w 2013 r. i nowszych wersjach. Aby uzyskać więcej informacji na temat ofert Microsoft 365 rządowych, zobacz [Announcing Microsoft 365 for Government: A US Government Community Cloud (Ogłoszenie Microsoft 365 dla rządu: Government Community Cloud USA](https://go.microsoft.com/fwlink/p/?LinkId=325414)). International Traffic in Arms Regulations (ITAR) to zbiór przepisów rządowych STANÓW Zjednoczonych, które kontrolują eksport i import artykułów i usług związanych z obronnością na [liście amunicji Stany Zjednoczone (USML).](https://go.microsoft.com/fwlink/p/?LinkId=325415) 

Firma Microsoft Microsoft 365 for Enterprises oferuje dedykowane usługi hostingowe dla rozwiązań firmy Microsoft zwiększających produktywność, które obsługują wymagania dotyczące zabezpieczeń, prywatności i zgodności z przepisami dla agencji federalnych USA wymagających certyfikacji i jednostek komercyjnych federal information security management (FISMA) podlegających itar.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>Kwestie, które należy wziąć pod uwagę podczas korzystania z protokołu IPv6 i Microsoft 365

Zalecamy, aby nie wyłączać protokołu IPv6. Aby uzyskać więcej informacji, zobacz ten [artykuł ze wskazówkami](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Aby określić, jakie wersje adresów IP są używane w sieci, należy wziąć pod uwagę następujące kwestie:
  
- Jeśli wyświetlanie polecenia **IPConfig** w wierszu polecenia zawiera wiersze o nazwie "Adres IPv6" lub "Tymczasowy adres IPv6", masz protokół IPv6 w środowisku.

- Jeśli wszystkie adresy IPv6 zaczynają się od "fe80" i odpowiadają wierszom o nazwie "Link-Local IPv6 Address", nie masz protokołu IPv6 w środowisku.

Te zagadnienia mogą dotyczyć twojej sieci:
  
- Usługa subskrypcji publicznej nie obsługuje zakupu za pomocą karty kredytowej za pośrednictwem protokołu IPv6. Nie dotyczy to Government Community Cloud (GCC), ponieważ instytucje rządowe mają licencje Enterprise Agreement (EA).

- Protokół IPv6 nie obsługuje niektórych scenariuszy usług Rights Management Services (RMS).

- Protokół IPv6 nie obsługuje serwera BlackBerry® Enterprise Server (BES), ponieważ aplikacja BlackBerry nie obsługuje protokołu IPv6.

- Jeśli używasz Active Directory Federation Services (AD FS) z Microsoft 365, anonsowanie punktu końcowego sieci usług AD FS do Microsoft 365 przy użyciu protokołu IPv6 nie jest obsługiwane. Nie należy dołączać rekordów AAAA do wpisu DNS usług AD FS podczas korzystania z Exchange Online. 

Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Zobacz też

[Plan Edukacja IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Przewodnik przetrwania IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
