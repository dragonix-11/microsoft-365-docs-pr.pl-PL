---
title: Inne punkty końcowe, które nie są zawarte w usłudze Office 365 adres IP i usługa sieci Web adresu URL
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
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
ms.openlocfilehash: 0453efbea7957c3cf859c59da7a2cff7db04b4f0
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2022
ms.locfileid: "63009774"
---
# <a name="other-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Inne punkty końcowe, które nie są zawarte w usłudze Office 365 adres IP i usługa sieci Web adresu URL

Niektóre punkty końcowe sieci zostały wcześniej opublikowane i nie zostały uwzględnione w usłudze [sieci Office 365 adres IP i usługa sieci Web adresu URL](microsoft-365-ip-web-service.md). Usługa sieci Web publikuje punkty końcowe sieci, które są wymagane do Office 365 sieci obwodowej przedsiębiorstwa. Obecnie ten zakres nie obejmuje:

1. Łączność sieciowa, która może być wymagana z centrum danych firmy Microsoft do sieci klienta (przychodzącego hybrydowego ruchu sieciowego serwera).
2. Łączność sieciowa z serwerów w sieci klienta na obwodzie przedsiębiorstwa (wychodzący ruch sieciowy serwerów).
3. Nietypowe scenariusze dla wymagań dotyczących łączności sieciowej ze strony użytkownika.
4. Wymaga łączności rozpoznawania nazw DNS (których nie wymieniono poniżej).
5. Internet Explorer lub Microsoft Edge zaufanych witryn.

Poza systemem DNS te wystąpienia są wszystkie opcjonalne dla większości klientów, chyba że jest potrzebny opisany scenariusz.

<br>

****

|Wiersz|Cel|Destination (Miejsce docelowe)|Wpisać|
|---|---|---|---|
|1|**[Usługa importowania](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) plików PST i ingestion plików**|Aby uzyskać [więcej wymagań, zobacz](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) Usługa importowania.|Nietypowy scenariusz ruchu wychodzącego|
|2|**[Microsoft Asystent odzyskiwania i pomocy technicznej for Office 365](https://diagnostics.office.com/#/)**|<https://autodiscover.outlook.com> <br> <https://officecdn.microsoft.com> <br> <https://api.diagnostics.office.com> <br> <https://apibasic.diagnostics.office.com> <br> <https://autodiscover-s.outlook.com> <br> <https://cloudcheckenabler.azurewebsites.net> <br> <https://login.live.com> <br> <https://login.microsoftonline.com> <br> <https://login.windows.net> <br> <https://o365diagtelemetry.trafficmanager.net> <br> <https://odc.officeapps.live.com> <br> <https://offcatedge.azureedge.net> <br> <https://officeapps.live.com> <br> <https://outlook.office365.com> <br> <https://outlookdiagnostics.azureedge.net>|Wychodzący ruch na serwerze|
|3|**Narzędzie do Połączenie Azure AD (opcja logowania jednokrotnego)** <p> Zdalny program PowerShell & WinRM|Środowisko usług sts klienta (serwer usług AD FS i serwer proxy usług AD FS) \| porty TCP 80 & 443|Przychodzący ruch na serwerze|
|4|**Usługi STS** , takie jak serwery proxy usług AD FS (tylko w przypadku klientów federowanych)|Port TCP 443 lub port TCP 49443 klienta (na przykład serwer proxy usług AD FS) \| z protokołem TS klienta|Przychodzący ruch na serwerze|
|5|**[Exchange Online funkcji Unified Messaging/SBC](/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-session-border-controllers)**|Dwukierunkowy między lokalnym kontrolerem obramowania sesji \*a plikiem um.outlook.com|Wychodzący ruch tylko na serwerze|
|6|**Migracja skrzynek pocztowych**<p>Jeśli migracja skrzynek pocztowych zostanie zainicjowana z lokalnego środowiska [Exchange](/exchange/exchange-deployment-assistant) hybrydowego do programu Office 365, program Office 365 połączy się z opublikowanym serwerem usług sieci Web programu Exchange Web Services (EWS)/serwerem usług replikacji skrzynek pocztowych (MRS). Jeśli potrzebujesz adresów IP NAT używanych przez serwery Exchange Online w celu ograniczenia połączeń przychodzących z określonych zakresów źródłowych adresów IP, są one wymienione w zakresach adresów IP & adresu [URL usługi Office 365 &](urls-and-ip-address-ranges.md) w obszarze usługi "Exchange Online". <p> Przed ograniczeniem połączeń TCP 443 z określonych zakresów źródłowych adresów IP należy zadbać o to, aby nie miało to wpływu na dostęp do opublikowanych punktów końcowych EWS, takich jak OWA.|Lokalne serwery proxy EWS/MRS klienta <br> Port TCP 443|Przychodzący ruch na serwerze|
|7|**[Exchange hybrydowych](/exchange/exchange-deployment-assistant) funkcji współistnienia**, takich jak udostępnianie informacji o wolnym/zajętym.|Serwer Exchange klienta|Przychodzący ruch na serwerze|
|8|**[Exchange hybrydowe](/exchange/exchange-deployment-assistant) uwierzytelnianie serwera proxy**|Lokalna usługa STS klienta|Przychodzący ruch na serwerze|
|9|Służy do [konfigurowania Exchange hybrydowego](/exchange/exchange-deployment-assistant) za pomocą Kreatora **[Exchange konfiguracji hybrydowej](/exchange/hybrid-configuration-wizard)** <p> Uwaga: Te punkty końcowe są wymagane tylko do skonfigurowania Exchange hybrydowego|domains.live.com portach TCP o numerach 80 & 443, wymagany tylko dla kreatora konfiguracji hybrydowej programu Exchange SP3 dla programu Exchange 2010 z dodatkiem SP3 <p> GCC adresy IP dod: 40.118.209.192/32; 168.62.190.41/32 <p> Worldwide Commercial & GCC: \*.store.core.windows.net; asl.configure.office.com; tds.configure.office.com; mshybridservice.trafficmanager.net ; <br> aka.ms/hybridwizard; <br> \*shcwreleaseprod.blob.core.windows.net/shcw/;|Wychodzący ruch tylko na serwerze|
|10|Usługa **AutoDetect jest używana w scenariuszach** Exchange [hybrydowych](/exchange/exchange-deployment-assistant) z nowoczesnym uwierzytelnianiem hybrydowym z Outlook [dla systemów iOS i Android](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <p> `*.acompli.net` <br> `*.outlookmobile.com` <br> `*.outlookmobile.us` <br> `52.125.128.0/20` <br> `52.127.96.0/23`|Klient w środowisku lokalnym Exchange tcp 443|Przychodzący ruch na serwerze|
|11|**Exchange hybrydowe uwierzytelnianie usługi Azure AD**|*.msappproxy.net|Ruch wychodzący TCP tylko na serwer|
|12|Skype dla firm roku 2016 Office udostępnianie ekranu oparte na klipach **wideo, które** korzysta z portów UDP. Wcześniej Skype dla firm w wersji Office 2013 i wcześniejszych używali protokołu RDP przez port TCP 443.|Port TCP 443 jest otwierany do portu 52.112.0.0/14|Skype dla firm starszych wersji klienta w Office 2013 i starszych|
|13|**Skype dla firm hybrydowej lokalnej łączności serwera z** usługą Skype dla firm Online|13.107.64.0/18, 52.112.0.0/14 <br> Porty UDP 50 000–59 999 <br> porty TCP 50 000–59 999; 5061|Skype dla firm połączeń wychodzących na serwerze lokalnym|
|14|**Chmurowa sieć PSTN** z lokalną łącznością hybrydową wymaga połączenia sieciowego otwartego z hostami lokalnymi. Aby uzyskać więcej szczegółowych informacji na Skype dla firm hybrydowych usługi Online|Zobacz [Planowanie łączności hybrydowej między Skype dla firm Server i Office 365](/skypeforbusiness/hybrid/plan-hybrid-connectivity)|Skype dla firm ruchu przychodzącego hybrydowego lokalnego|
|15|**FQDN uwierzytelniania i tożsamości** <p> Aby witryna FQDN `secure.aadcdn.microsoftonline-p.com` działała, musi się znaleźć w strefie zaufanej witryny klienta programu Internet Explorer (Internet Explorer) lub Edge Trusted Sites.||Zaufane witryny|
|16|**Microsoft Teams FQDN** <p> Jeśli korzystasz z programu Internet Explorer Microsoft Edge, musisz włączyć pliki cookie tej firmy i innych firm oraz dodać te Teams do zaufanych witryn. Jest to dodatek do wymienionych w wierszu 14 sieci FQNS, sieci CDN i telemetrii dla całego pakietu. Zobacz [Znane problemy dotyczące Microsoft Teams](/microsoftteams/known-issues), aby uzyskać więcej informacji.||Zaufane witryny|
|17|**SharePoint online i OneDrive dla Firm FQDN** <p> Aby wszystkie sharepoint.com "\<tenant\>.sharepoint.com" z "" w tej domenie, muszą się znaleźć w strefie Zaufane witryny w programie Internet Internet Dla Klientów lub Edge. Oprócz wymienionych w wierszu 14 sieci FQNS, sieci CDN i telemetrii dla całego pakietu konieczne będzie również dodanie tych punktów końcowych.||Zaufane witryny|
|18|**Yammer**  <br> Yammer jest dostępna tylko w przeglądarce i wymaga uwierzytelnienia użytkownika za pośrednictwem serwera proxy. Wszystkie Yammer FQDN muszą zostać w strefie Zaufane witryny na komputerze klienckim (Internet Internet Internet), czyli w strefie Zaufane witryny przeglądarki Edge.||Zaufane witryny|
|19|Użyj **[narzędzia Azure AD Połączenie](/azure/active-directory/hybrid/)** do synchronizowania lokalnych kont użytkowników z usługą Azure AD.|Zobacz [Porty i protokoły wymagane dla](/azure/active-directory/hybrid/reference-connect-ports) tożsamości hybrydowej, Rozwiązywanie problemów z łącznością w usłudze [Azure AD](/azure/active-directory/hybrid/tshoot-connect-connectivity) i [Instalacja agenta Połączenie kondycji usługi Azure AD](/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints).|Wychodzący ruch tylko na serwerze|
|20|**[Usługa Azure AD Połączenie](/azure/active-directory/hybrid/)** 21 viaNet w Chinach w celu synchronizowania lokalnych kont użytkowników z usługą Azure AD.|\*digicert.com:80 <BR> \*entrust.net:80 <BR> \*chinacloudapi.cn:443 <br> secure.aadcdn.partner.microsoftonline-p.cn:443 <br> \*partner.microsoftonline.cn:443 <p> Zobacz też [Rozwiązywanie problemów z ruchami wychodzącymi z łącznością w usłudze Azure AD](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity).|Wychodzący ruch tylko na serwerze|
|21|**Microsoft Stream** (wymaga tokenu użytkownika usługi Azure AD). <br> Office 365 na całym świecie (w tym GCC)|\*cloudapp.net <br> \*api.microsoftstream.com <br> \*notification.api.microsoftstream.com <br> amp.azure.net <br> api.microsoftstream.com <br> az416426.vo.msecnd.net <br> s0.assets-yammer.com <br> vortex.data.microsoft.com <br> web.microsoftstream.com <br> Port TCP 443|Przychodzący ruch na serwerze|
|22|Serwer **uwierzytelniania wieloskładnikowego** umożliwia żądania uwierzytelniania wieloskładnikowego — obie nowe instalacje serwera są następnie Usługi domenowe w usłudze Active Directory (AD DS).|Zobacz [Wprowadzenie do serwera uwierzytelniania wieloskładnikowego usługi Azure AD](/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).|Wychodzący ruch tylko na serwerze|
|23|**Powiadomienia o Graph microsoft** <p> Deweloperzy mogą używać [powiadomień o zmianach do](/graph/webhooks?context=graph%2fapi%2f1.0&view=graph-rest-1.0) subskrybowania zdarzeń w sklepie Microsoft Graph.|Public Cloud: 52.159.23.209, 52.159.17.84, 52.147.213.251, 52.147.213.181, 13.85.192.59, 13.85.192.123, 13.89.108.233, 13.89.104.147, 20.96.21.67, 20.69.245.215, 137.135.11.161, 137.135.11.116, 52.159.107.50, 52.159.107.4, 52.229.38.131, 52.183.67.212, 52.142.114.29, 52.142.115.31, 51.124.75.43, 51.124.73.177, 20.44.210.83, 20.44.210.146, 40.80.232.177, 40.80.232.118, 20.48.12.75, 20.48.11.201, 104.215.13.23, 104.215.6.169, 52.148.24.136, 52.148.27.39, 40.76.162.99, 40.76.162.42 , 40.74.203.28, 40.74.203.27, 13.86.37.15, 52.154.246.238, 20.96.21.98, 20.96.21.115, 137.135.11.222, 137.135.11.250, 52.159.109.205, 52.159.102.72, 52.151.30.78, 52.191.173.85, 51.104.159.213, 51.104.159.181, 51.138.90.7, 51.138.90.52, 52.148.115.48, 52.148.114.238, 40.80.233.14, 40.80.239.196, 20.48.14.35, 20.48.15.147, 104.215.18.55, 104.215.12.254, 20.199.102.157, 20.199.102.73, 13.87.81.123, 13.87.81.35, 20.111.9.46, 20.111.9.77, 13.87.81.133, 13.87.81.141 <p> Microsoft Cloud for US Government: 52.244.33.45, 52.244.35.174, 52.243.157.104, 52.243.157.105, 52.182.25.254, 52.182.25.110, 52.181.25.67, 52.181.25.66, 52.244.111.156, 52.244.111.170, 52.243.147.249, 52.243.148.1 9, 52.182.32.51, 52.182.32.143, 52.181.24.199, 52.181.24.220 <p> Microsoft Cloud China obsługiwana przez firmę 21Vianet: 42.159.72.35, 42.159.72.47, 42.159.180.55, 42.159.180.56, 40.125.138.23, 40.125.136.69, 40.72.155.199, 40.72.155.216 <br> Port TCP 443 <p> Uwaga: Podczas tworzenia subskrypcji deweloperzy mogą określać różne porty.|Przychodzący ruch na serwerze|
|24|**Wskaźnik stanu połączenia sieciowego**<p>Używany przez Windows 10 i 11 w celu określenia, czy komputer jest połączony z Internetem (nie dotyczy klientów innych Windows). Gdy adres URL nie będzie dostępny, program Windows założy, że nie jest połączony z Internetem, Enterprise aplikacje M365 dla usługi Enterprise nie będą próbować weryfikować stanu aktywacji, co powoduje niepowodzenie połączeń z usługami Exchange i innymi usługami.|www.mstfconnecttest.com <br> 13.107.4.52<p>Zobacz też [Zarządzanie punktami końcowymi połączenia dla Windows 11 Enterprise](/windows/privacy/manage-windows-11-endpoints) zarządzanie punktami końcowymi połączenia dla programu [Windows 10 Enterprise wersja 21H2](/windows/privacy/manage-windows-21h2-endpoints).|Wychodzący ruch tylko na serwerze|
|

## <a name="related-topics"></a>Tematy pokrewne

[Zarządzanie Office 365 punktami końcowymi](managing-office-365-endpoints.md)
  
[Monitorowanie Microsoft 365 sieci](./monitor-connectivity.md)
  
[Łączność z klientem](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Sieci dostarczania zawartości](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Zakresy adresów IP i tagi usługi Azure — chmura publiczna](https://www.microsoft.com/download/details.aspx?id=56519)

[Zakresy adresów IP i tagi usług Azure — Us Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063)

[Zakresy adresów IP i tagi usługi Azure — chmura Germany](https://www.microsoft.com/download/details.aspx?id=57064)

[Zakresy adresów IP i tagi usług azure — chmura w Chinach](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Publiczny obszar adresów IP firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
