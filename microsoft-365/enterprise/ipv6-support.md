---
title: Obsługa protokołu IPv6 w Microsoft 365 usługach internetowych
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Podsumowanie: w tym artykule opisano obsługę protokołu IPv6 w Microsoft 365 i w Microsoft 365 dla instytucji rządowych.'
ms.openlocfilehash: a6a2e11ff2e312c02f10d152fe580bdead5fa7c9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996355"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>Obsługa protokołu IPv6 w Microsoft 365 usługach internetowych

Microsoft 365 obsługuje zarówno protokół IPv6, jak i IPv4, jednak nie wszystkie Microsoft 365 są w pełni włączone z obsługą protokołu IPv6. Oznacza to, że musisz używać zarówno protokołu IPv4, jak i IPv6, aby nawiązać połączenie z Microsoft 365. Jeśli filtrowany jest ruch wychodzący do usługi Microsoft 365, pełną listę adresów IPv6 obsługiwanych przez protokół Microsoft 365 można znaleźć w artykule Adresy URL i zakresy adresów [IP usługi Microsoft 365](urls-and-ip-address-ranges.md). Po skonfigurowaniu sieci i zbędeniu odpowiednich adresów IPv6 możesz pobrać plan testowania protokołu [IPv6 dla protokołu IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) Microsoft 365 z Centrum pobierania Microsoft.

> [!NOTE]
> Umożliwienie klientom możliwości Microsoft 365 usług SaaS z dowolnej lokalizacji i dowolnego urządzenia jest dla firmy Microsoft priorytetem. Obejmuje to zezwolenie klientom na łączenie się i Microsoft 365 z obsługą protokołu IPv6 oraz tylko klientów i systemów informacyjnych IPv6. Obejmuje to również umożliwienie klientom rządowym realizacji zobowiązań dotyczących protokołu IPv6 w ich sieciach, a jednocześnie nadal korzystać Microsoft 365 scenariuszy dotyczących produktywności bez zakłóceń.  
> Ten artykuł zawiera listę usług SaaS Microsoft 365, które umożliwiają bezpośrednią łączność IPv6. Należy oczekiwać, że zakres usług umożliwiający bezpośrednią łączność IPv6 będzie nadal rozszerzany. Microsoft 365 usług, które nie zostały wprost wymienione w celu obsługi bezpośredniej protokołu IPv6, w celu dołączyć usługi uwierzytelniania Azure Active Directory (AAD) należy uznać, że połączenie z usługą DNS64/NAT64 z obsługą protokołu IPv6 jest wymagane tylko dla klientów i środowisk.  Jest to dostosowanie do celu opisanego obecnie w istniejącej dokumentacji NIST USGv6: Wymagania dotyczące funkcji mechanizmu przejścia w publikacji specjalnej [NIST 500-267A Wersja 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 to akceptowalne technologie do uwierzytelniania.
> - Obsługa translatora NAT64 dla mechanizmu przejścia NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Stateful NAT64: Tłumaczenie adresów sieciowych i protokołu z klientów IPv6 na serwery IPv4
> - Obsługa systemu DNS64 dla mechanizmu przejścia DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: Rozszerzenia DNS do tłumaczenia adresów sieciowych z klientów IPv6 na serwer IPv4

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>Obsługa protokołu IPv6 w Microsoft 365 subskrypcji usługi

### <a name="exchange-online-and-ipv6"></a>Exchange Online i IPv6

Jeśli program, za pomocą których łączysz się z siecią Exchange Online obsługuje protokół IPv6, to będzie on domyślnie używać protokołu IPv6 w sieci przewodowej i bezprzewodowej. Jeśli chcesz kontrolować komunikację z Exchange Online, użyj zakresów adresów IP podanych w Microsoft 365 [URL i zakresach adresów IP](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online i IPv6

 **Microsoft 365 dla instytucji rządowych G1/G3/G4/K1** Jeśli program, za pomocą których łączysz się z usługą SharePoint Online, obsługuje protokół IPv6, to domyślnie będzie on próbował używać protokołu IPv6.
  
 **Publiczna chmura wielodostępna** Na Twoje żądanie firma Microsoft SharePoint protokół IPv6 online. Musisz podać adresy IP z notacji CIDR dla swojej infrastruktury DNS organizacji. Pamiętaj, że inne organizacje nie mogą udostępniać tej infrastruktury DNS dla protokołu IPv6 dla Twojej dzierżawy. Po włączeniu protokołu IPv6, jeśli program, za pomocą których łączysz się z usługą SharePoint Online, obsługuje protokół IPv6, to protokół IPv6 jest używany domyślnie.
  
Jeśli program, za pomocą których łączysz się z usługą SharePoint Online, obsługuje protokół IPv6, to będzie on domyślnie używać protokołu IPv6 w sieci przewodowej i bezprzewodowej. Jeśli chcesz kontrolować komunikację z usługą SharePoint Online, użyj zakresów adresów IP podanych w Microsoft 365 [URL i zakresach adresów IP](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype dla firm i IPv6

Należy pamiętać, że protokół IPv6 nie jest obsługiwany Skype dla firm i nie można już go włączyć.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams, brama SIP i protokół IPV6

Microsoft Teams routing bezpośredni i brama SIP obsługują protokół IPv4. Usługa Microsoft Teams i klient obsługują zarówno protokół IPv4, jak i protokół IPv6. Jeśli chcesz kontrolować komunikację z Microsoft Teams, użyj zakresów adresów IP podanych w Microsoft 365 [URL i zakresach adresów IP](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection i IPv6

Exchange Online Protection (EOP) obsługuje protokół IPv6, jeśli transmisja odbywa się za pośrednictwem protokołu Transport Layer Security. Dla zakresu usługi EOP użyj Microsoft 365 [URL i zakresów adresów IP](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>Obsługa protokołu IPv6 dla Microsoft 365 dla instytucji rządowych

Obsługa protokołu IPv6 dla instytucji rządowych jest zgodna z standardem Office of Management and Budget (OMB) dla dyrektorów ds. informacji w działach i agencjach rządowych, a także federantów IPv6 (Federal Government Adoption of Internet Protocol w wersji 6). Microsoft 365 [Microsoft Microsoft 365 dla instytucji rządowych to](https://go.microsoft.com/fwlink/p/?LinkId=325414) usługa wielodostępna, która przechowuje dane instytucji rządowych Stanów Zjednoczonych w oddzielonej chmurze społeczności. Podobnie jak Microsoft 365 oferuje usługi zwiększające produktywność i współpracę, w tym usługi Exchange Online, Skype dla firm, SharePoint online i Aplikacje Microsoft 365 dla przedsiębiorstw. 

Oferta firmy Microsoft Microsoft 365 dla instytucji rządowych dotyczy tylko roku 2013 i nowszych. Aby uzyskać więcej informacji na Microsoft 365 dla instytucji rządowych, zobacz Ogłaszanie Microsoft 365 dla instytucji rządowych[:](https://go.microsoft.com/fwlink/p/?LinkId=325414) amerykański Government Community Cloud. Międzynarodowy ruch bronią (ITAR, International Traffic in Arms Regulations) to zestaw przepisów rządowych Stanów Zjednoczonych, które kontrolują eksportowanie i importowanie artykułów i usług związanych z obroną na liście amerykańskiej ( [USML](https://go.microsoft.com/fwlink/p/?LinkId=325415)) związanych z obroną. 

Firma Microsoft Microsoft 365 dla przedsiębiorstw oferuje dedykowane usługi hostingowe dla rozwiązań biurowych firmy Microsoft, które obsługują wymagania dotyczące bezpieczeństwa, prywatności i zgodności z przepisami dla amerykańskich organów federalnych, które wymagają certyfikacji Federal Information Security Management (FISMA), oraz jednostek komercyjnych podlegających zasadom ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>Co należy wziąć pod uwagę podczas korzystania z protokołu IPv6 i Microsoft 365

Zalecamy, aby nie wyłączać protokołu IPv6. Aby uzyskać więcej informacji, zobacz ten [artykuł z wskazówkami](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Aby ustalić, jakie wersje protokołu IP są używane w Twojej sieci, rozważ następujące kwestie:
  
- Jeśli wyświetlanie polecenia **IPConfig** w wierszu polecenia zawiera wiersze o nazwie "Adres IPv6" lub "Tymczasowy adres IPv6", to oznacza to, że Twoje środowisko ma protokół IPv6.

- Jeśli wszystkie adresy IPv6 zaczynają się od "fe80" i odpowiadają wierszom o nazwach "Adres IPv6 połączenia lokalnego", to twoje środowisko nie ma protokołu IPv6.

W przypadku Twojej sieci mogą obowiązywać następujące zagadnienia:
  
- Usługa subskrypcji publicznej nie obsługuje zakupów przy pomocy karty kredytowej za pośrednictwem protokołu IPv6. Nie dotyczy to Government Community Cloud (GCC), ponieważ rządy mają Enterprise Agreement (EA).

- Protokół IPv6 nie obsługuje niektórych scenariuszy usług zarządzania prawami dostępu (RMS).

- Protokół IPv6 nie obsługuje protokołu BlackBerry® Enterprise Server (BES), ponieważ urządzenia BlackBerry nie obsługują protokołu IPv6.

- Jeśli używasz z usługami federacyjną Active Directory (AD FS) Microsoft 365, reklamowanie punktu końcowego sieci usług AD FS w celu Microsoft 365 używania protokołu IPv6 nie jest obsługiwane. Używając rekordów usługi AD FS, nie należy uwzględniać rekordów AAAA we wpisie usługi DNS usług AD FS Exchange Online. 

Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Zobacz też

[Przewodnik po protokółach IPv6 Edukacja iPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[Przewodnik po protokole IPv6 (pogotowa)](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
