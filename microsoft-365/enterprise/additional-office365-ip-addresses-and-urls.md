---
title: Inne punkty końcowe nie są uwzględnione w usłudze sieci Web Office 365 adresów IP i adresów URL
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
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
ms.assetid: ''
description: 'Podsumowanie: Nowa usługa sieci Web punktu końcowego nie zawiera kilku punktów końcowych dla określonych scenariuszy.'
hideEdit: true
ms.openlocfilehash: bebffa1cb03a85ffd5ab7519095f38b7ae5cf985
ms.sourcegitcommit: 60970cf8a2cb451011c423d797dfb77925394f89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2022
ms.locfileid: "65587353"
---
# <a name="other-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Inne punkty końcowe nie są uwzględnione w usłudze sieci Web Office 365 adresów IP i adresów URL

Niektóre punkty końcowe sieci zostały wcześniej opublikowane i nie zostały uwzględnione w [usłudze sieci Web Office 365 adresów IP i adresów URL](microsoft-365-ip-web-service.md). Usługa internetowa publikuje punkty końcowe sieci, które są wymagane do Office 365 łączności w sieci obwodowej przedsiębiorstwa. Ten zakres obecnie nie obejmuje:

1. Łączność sieciowa, która może być wymagana z centrum danych firmy Microsoft do sieci klienta (przychodzący ruch sieciowy serwera hybrydowego).
2. Łączność sieciowa z serwerów w sieci klienta na całym obwodzie przedsiębiorstwa (ruch sieciowy serwera wychodzącego).
3. Nietypowe scenariusze dotyczące wymagań dotyczących łączności sieciowej od użytkownika.
4. Wymagania dotyczące łączności rozpoznawania nazw DNS (nie wymieniono poniżej).
5. Internet Explorer lub Microsoft Edge zaufanych witryn.

Oprócz systemu DNS wszystkie te wystąpienia są opcjonalne dla większości klientów, chyba że potrzebujesz określonego scenariusza, który został opisany.

<br>

****

|Wiersza|Celu|Destination (Miejsce docelowe)|Wpisać|
|---|---|---|---|
|1|**[Importowanie usługi](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) na potrzeby pozyskiwania plików i PST**|Aby uzyskać więcej wymagań, zapoznaj się z [usługą importowania](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) .|Nietypowy scenariusz ruchu wychodzącego|
|2|**[pomoc techniczna firmy Microsoft i Asystent odzyskiwania dla Office 365](https://diagnostics.office.com/#/)**|<https://autodiscover.outlook.com> <br> <https://officecdn.microsoft.com> <br> <https://api.diagnostics.office.com> <br> <https://apibasic.diagnostics.office.com> <br> <https://autodiscover-s.outlook.com> <br> <https://cloudcheckenabler.azurewebsites.net> <br> <https://login.live.com> <br> <https://login.microsoftonline.com> <br> <https://login.windows.net> <br> <https://o365diagtelemetry.trafficmanager.net> <br> <https://odc.officeapps.live.com> <br> <https://offcatedge.azureedge.net> <br> <https://officeapps.live.com> <br> <https://outlook.office365.com> <br> <https://outlookdiagnostics.azureedge.net>|Ruch na serwerze wychodzącym|
|3|**Azure AD Połączenie (opcja W/SSO)** <p> WinRM & zdalnego programu PowerShell|Porty TCP środowiska sts klienta (serwer usług AD FS i serwer proxy usług AD FS) \| 80 & 443|Ruch przychodzący serwera|
|4|**Usługi STS** , takie jak serwery proxy usług AD FS (tylko dla klientów federacyjnych)|Porty TCP 443 lub TCP 49443 w/ClientTLS klienta usługi STS (np. serwer proxy usług AD FS) \||Ruch przychodzący serwera|
|5|**[integracja Exchange Online Unified Messaging/SBC](/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-session-border-controllers)**|Dwukierunkowy między lokalnym kontrolerem obramowania sesji i \*um.outlook.com|Ruch wychodzący tylko na serwerze|
|6|**Migracja skrzynki pocztowej**<p>Gdy migracja skrzynki pocztowej jest inicjowana z lokalnego [Exchange hybrydowego](/exchange/exchange-deployment-assistant) do Office 365, Office 365 połączy się z opublikowanym serwerem usług Exchange Web Services (EWS)/Usługi replikacji skrzynek pocztowych (MRS). Jeśli potrzebujesz adresów IP TRANSLATOR używanych przez serwery Exchange Online w celu ograniczenia połączeń przychodzących z określonych źródłowych zakresów adresów IP, są one wymienione w [Office 365 adresach URL & zakresach adresów IP](urls-and-ip-address-ranges.md) w obszarze usługi "Exchange Online". <p> Należy zadbać o to, aby dostęp do opublikowanych punktów końcowych EWS, takich jak OWA, nie miał wpływu na serwer proxy MRS rozpoznawany jako oddzielna nazwa FQDN i publiczny adres IP przed ograniczeniem połączeń TCP 443 z określonych zakresów źródłowych adresów IP.|Lokalny serwer proxy EWS/MRS klienta <br> Port TCP 443|Ruch przychodzący serwera|
|7|**Exchange funkcje współistnienia [hybrydowego](/exchange/exchange-deployment-assistant)**, takie jak udostępnianie bezpłatne/zajęte.|Lokalny serwer Exchange klienta|Ruch przychodzący serwera|
|8|**[Exchange uwierzytelnianie hybrydowego](/exchange/exchange-deployment-assistant) serwera proxy**|Lokalny sts klienta|Ruch przychodzący serwera|
|9|Służy do konfigurowania [Exchange hybrydowej](/exchange/exchange-deployment-assistant) przy użyciu **[Kreatora konfiguracji hybrydowej Exchange](/exchange/hybrid-configuration-wizard)** <p> Uwaga: te punkty końcowe są wymagane tylko do skonfigurowania Exchange hybrydowej|domains.live.com na portach TCP 80 & 443, wymagane tylko dla kreatora konfiguracji hybrydowej Exchange 2010 z dodatkiem SP3 <p> GCC adresy IP wysokiego identyfikatora DoD: 40.118.209.192/32; 168.62.190.41/32 <p> Światowe & GCC handlowe: \*.store.core.windows.net; asl.configure.office.com; tds.configure.office.com; mshybridservice.trafficmanager.net; <br> aka.ms/hybridwizard; <br> \*shcwreleaseprod.blob.core.windows.net/shcw/;|Ruch wychodzący tylko na serwerze|
|10|**Usługa AutoWykrywanie** jest używana w [scenariuszach hybrydowych Exchange](/exchange/exchange-deployment-assistant) z [nowoczesnym uwierzytelnianiem hybrydowym z Outlook dla iOS i Android](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <p> `<email_domain>.outlookmobile.com` <br> `<email_domain>.outlookmobile.us` <br> `52.125.128.0/20` <br> `52.127.96.0/23`|Lokalny serwer Exchange klienta na serwerze TCP 443|Ruch przychodzący serwera|
|11|**Exchange uwierzytelnianie hybrydowe Azure AD**|*.msappproxy.net|Ruch wychodzący protokołu TCP tylko na serwerze|
|12|Skype dla firm w Office 2016 r. obejmuje **udostępnianie ekranu opartego na wideo**, które korzysta z portów UDP. Poprzedni klienci Skype dla firm w Office 2013 r. i wcześniej używali protokołu RDP za pośrednictwem portu TCP 443.|Port TCP 443 otwiera się na 52.112.0.0/14|Skype dla firm starszych wersji klienta w Office 2013 r. i starszych wersjach|
|13|**Skype dla firm hybrydowa łączność serwera lokalnego** z usługą Skype dla firm Online|13.107.64.0/18, 52.112.0.0/14 <br> Porty UDP 50 000–59 999 <br> Porty TCP 50 000–59 999; 5061|Skype dla firm łączności wychodzącej serwera lokalnego|
|14|**Sieć PSTN w chmurze** z lokalną łącznością hybrydową wymaga połączenia sieciowego otwartego dla hostów lokalnych. Aby uzyskać więcej informacji na temat konfiguracji hybrydowych usługi Skype dla firm Online|Zobacz [Planowanie łączności hybrydowej między Skype dla firm Server a Office 365](/skypeforbusiness/hybrid/plan-hybrid-connectivity)|Skype dla firm przychodzących hybrydowych lokalnych|
|15|**Nazwy FQDN uwierzytelniania i tożsamości** <p> Nazwa FQDN `secure.aadcdn.microsoftonline-p.com` musi znajdować się w strefie zaufanych witryn programu Internet Explorer (IE) klienta lub przeglądarki Edge.||Zaufane witryny|
|16|**Microsoft Teams nazw FQDN** <p> Jeśli używasz programu Internet Explorer lub Microsoft Edge, musisz włączyć pliki cookie pierwszej i innej firmy i dodać nazwy FQDN dla Teams do zaufanych witryn. Jest to oprócz zestawu nazw FQDN, CDN i telemetrii wymienionych w wierszu 14. Aby uzyskać więcej informacji, zobacz [Znane problemy dotyczące Microsoft Teams](/microsoftteams/known-issues).||Zaufane witryny|
|17|**SharePoint Online i OneDrive dla Firm nazw FQDN** <p> Wszystkie nazwy FQDN ".sharepoint.com" z nazwą "\<tenant\>" w nazwach FQDN muszą znajdować się w strefie zaufanych witryn IE lub Edge klienta, aby działały. Oprócz nazw FQDN, sieci CDN i danych telemetrycznych wymienionych w wierszu 14 należy również dodać te punkty końcowe.||Zaufane witryny|
|18|**Yammer**  <br> Yammer jest dostępna tylko w przeglądarce i wymaga przekazania uwierzytelnionego użytkownika za pośrednictwem serwera proxy. Wszystkie Yammer nazw FQDN muszą znajdować się w strefie zaufanych witryn IE lub Edge klienta, aby działały.||Zaufane witryny|
|19|Użyj **[Azure AD Połączenie](/azure/active-directory/hybrid/)**, aby zsynchronizować konta użytkowników lokalnych z Azure AD.|Zobacz [Porty i protokoły wymagane do obsługi tożsamości hybrydowej](/azure/active-directory/hybrid/reference-connect-ports), [Rozwiązywanie problemów z łącznością Azure AD](/azure/active-directory/hybrid/tshoot-connect-connectivity) i [instalacja agenta Azure AD Połączenie Kondycja](/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints).|Ruch wychodzący tylko na serwerze|
|20|**[Azure AD Połączenie](/azure/active-directory/hybrid/)** z 21 siecią ViaNet w Chinach, aby zsynchronizować konta użytkowników lokalnych z Azure AD.|\*.digicert.com:80 <BR> \*.entrust.net:80 <BR> \*.chinacloudapi.cn:443 <br> secure.aadcdn.partner.microsoftonline-p.cn:443 <br> \*.partner.microsoftonline.cn:443 <p> Zobacz również [Rozwiązywanie problemów z ruchem przychodzącym z Azure AD problemów z łącznością](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity).|Ruch wychodzący tylko na serwerze|
|21|**Microsoft Stream** (wymaga tokenu użytkownika Azure AD). <br> Office 365 Worldwide (w tym GCC)|\*.cloudapp.net <br> \*.api.microsoftstream.com <br> \*.notification.api.microsoftstream.com <br> amp.azure.net <br> api.microsoftstream.com <br> az416426.vo.msecnd.net <br> s0.assets-yammer.com <br> vortex.data.microsoft.com <br> web.microsoftstream.com <br> Port TCP 443|Ruch przychodzący serwera|
|22|Użyj **serwera MFA** dla żądań uwierzytelniania wieloskładnikowego, zarówno nowych instalacji serwera, jak i konfigurowania go przy użyciu Active Directory Domain Services (AD DS).|Zobacz [Wprowadzenie do serwera uwierzytelniania wieloskładnikowego Azure AD](/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).|Ruch wychodzący tylko na serwerze|
|23|**Powiadomienia o zmianach Graph firmy Microsoft** <p> Deweloperzy mogą używać [powiadomień o zmianach](/graph/webhooks?context=graph%2fapi%2f1.0&view=graph-rest-1.0) do subskrybowania zdarzeń w Graph firmy Microsoft.|Public Cloud: 52.159.23.209, 52.159.17.84, 52.147.213.251, 52.147.213.181, 13.85.192.59, 13.85.192.123, 13.89.108.233, 13.89.104.147, 20.96.21.67, 20.69.245.215, 137.135.11.161, 137.135.11.116, 52.159.107.50, 52.159.107.4, 52.229.38.131, 52.183.67.212, 52.142.114.29, 52.142.115.31, 51.124.75.43, 51.124.73.177, 20.44.210.83, 20.44.210.146, 40.80.232.177, 40.80.232.118, 20.48.12.75, 20.48.11.201, 104.215.13.23, 104.215.6.169, 52.148.24.136, 52.148.27.39, 40.76.162.99, 40.76.162.42 , 40.74.203.28, 40.74.203.27, 13.86.37.15, 52.154.246.238, 20.96.21.98, 20.96.21.115, 137.135.11.222, 137.135.11.250, 52.159.109.205, 52.159.102.72, 52.151.30.78, 52.191.173.85, 51.104.159.213, 51.104.159.181, 51.138.90.7, 51.138.90.52, 52.148.115.48, 52.148.114.238, 40.80.233.14, 40.80.239.196, 20.48.14.35, 20.48.15.147, 104.215.18.55, 104.215.12.254, 20.199.102.157, 20.199.102.73, 13.87.81.123, 13.87.81.35, 20.111.9.46, 20.111.9.77, 13.87.81.133, 13.87.81.141 <p> Microsoft Cloud for US Government: 52.244.33.45, 52.244.35.174, 52.243.157.104, 52.243.157.105, 52.182.25.254, 52.182.25.110, 52.181.25.67, 52.181.25.66, 52.244.111.156, 52.244.111.170, 52.243.147.249, 52.243.148.19, 52.182.32.51, 52.182.32.143, 52.181.24.199, 52.181.24.220 <p> Microsoft Cloud China obsługiwany przez firmę 21Vianet: 42.159.72.35, 42.159.72.47, 42.159.180.55, 42.159.180.56, 40.125.138.23, 40.125.136.69, 40.72.155.199, 40.72.155.216 <br> Port TCP 443 <p> Uwaga: deweloperzy mogą określić różne porty podczas tworzenia subskrypcji.|Ruch przychodzący serwera|
|24|**Wskaźnik stanu połączenia sieciowego**<p>Używane przez Windows 10 i 11 do określenia, czy komputer jest połączony z Internetem (nie dotyczy klientów innych niż Windows). Jeśli ten adres URL nie zostanie osiągnięty, Windows zakłada, że nie jest połączony z Internetem, a aplikacja M365 dla Enterprise nie spróbuje zweryfikować stanu aktywacji, powodując niepowodzenie połączeń z Exchange i innymi usługami.|www.msftconnecttest.com <br> 13.107.4.52<p>Zobacz również [Zarządzanie punktami końcowymi połączeń dla Windows 11 Enterprise](/windows/privacy/manage-windows-11-endpoints) i [Zarządzanie punktami końcowymi połączeń dla Windows 10 Enterprise w wersji 21H2](/windows/privacy/manage-windows-21h2-endpoints).|Ruch wychodzący tylko na serwerze|
|

## <a name="related-topics"></a>Tematy pokrewne

[Zarządzanie punktami końcowymi usługi Office 365](managing-office-365-endpoints.md)
  
[Monitorowanie łączności platformy Microsoft 365](./monitor-connectivity.md)
  
[Łączność z klientami](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Sieci dostarczania zawartości](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Zakresy adresów IP platformy Azure i tagi usług — chmura publiczna](https://www.microsoft.com/download/details.aspx?id=56519)

[Zakresy adresów IP platformy Azure i tagi usług — chmura dla instytucji rządowych USA](https://www.microsoft.com/download/details.aspx?id=57063)

[Zakresy adresów IP platformy Azure i tagi usług — chmura w Niemczech](https://www.microsoft.com/download/details.aspx?id=57064)

[Zakresy adresów IP platformy Azure i tagi usług — Chmura w Chinach](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Przestrzeń publicznych adresów IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
