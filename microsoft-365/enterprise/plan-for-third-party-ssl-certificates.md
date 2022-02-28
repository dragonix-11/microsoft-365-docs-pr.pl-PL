---
title: Planowanie certyfikatów SSL innych firm dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.date: 05/15/2019
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: b48cdf63-07e0-4cda-8c12-4871590f59ce
description: 'Podsumowanie: w tym artykule opisano certyfikaty SSL wymagane dla Exchange lokalnego i hybrydowego, logowania jednokrotnego przy użyciu usług AD FS, Exchange Online usług sieci Web Exchange sieci Web.'
ms.openlocfilehash: 8c0bf69090abb87e71f2d51b73405ccf4e54d4bb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988012"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>Planowanie certyfikatów SSL innych firm dla Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Aby szyfrowanie komunikacji między klientami i środowiskiem usługi Microsoft 365 było Microsoft 365, na serwerach infrastruktury muszą być zainstalowane certyfikaty SSL (Secure Socket Layer).

Ten artykuł jest częścią [planowania sieci i dostosowywania wydajności dla Microsoft 365](./network-planning-and-performance.md).
   
Certyfikaty są wymagane dla następujących Microsoft 365 składników:
  
- Exchange lokalnym
    
- Logowanie jednokrotne (SSO) zarówno dla serwerów federowych usług federnych Active Directory (AD FS), jak i federowych serwerów proxy usług AD FS
    
- Exchange Online usługi, takie jak autodiscover, Outlook Anywhere i Exchange Web Services
    
- Exchange hybrydowy
    
## <a name="certificates-for-exchange-on-premises"></a>Certyfikaty dla Exchange lokalnych

Aby uzyskać omówienie sposobu używania certyfikatów cyfrowych w celu zabezpieczenia komunikacji między lokalną organizacją Exchange a Exchange Online, zobacz artykuł w witrynie TechNet Opis [wymagań dotyczących certyfikatów](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141)).
  
## <a name="certificates-for-single-sign-on"></a>Certyfikaty na potrzeby logowania jednokrotnego

Aby zapewnić użytkownikom uproszczone logowanie pojedyncze z niezawodnymi zabezpieczeniami, na serwerach federowanych lub federowanych serwerach proxy są wymagane certyfikaty przedstawione w poniższej tabeli. W poniższej tabeli skupiono się na usługach federowych Active Directory (AD FS), ale mamy również więcej informacji na temat korzystania z dostawców [tożsamości innych firm](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
| Typ certyfikatu | Opis | Co należy wiedzieć przed wdrożeniem |
|:-----|:-----|:-----|
|**Certyfikat SSL (nazywany również certyfikatem uwierzytelniania serwera)** <br/> |Jest to standardowy certyfikat SSL używany do zabezpieczania komunikacji między serwerami federacyjną, klientami i komputerami feder serwerowych serwerów proxy.  <br/> |Usługi AD FS wymagają certyfikatu SSL. Domyślnie usługi AD FS używa certyfikatu SSL, który jest skonfigurowany dla domyślnej witryny sieci Web w programie Internet Information Services (IIS).  <br/> Nazwa podmiotu tego certyfikatu SSL służy do określania nazwy usługi federowej (FS) dla każdego wystąpienia wdrażanej usługi AD FS. Rozważ wybranie nazwy podmiotu dla każdego nowego certyfikatu wydanego przez urząd certyfikacji (UC), która będzie najlepiej reprezentować nazwę Twojej firmy lub organizacji do Microsoft 365. Ta nazwa musi być lewalna przez Internet.  <br/>**Przestroga:** Usługi AD FS wymagają, aby ten certyfikat SSL nie miał nazwy podmiotu bez kropki (krótkiej nazwy).          <br/> **Zalecenie:** Ponieważ ten certyfikat musi być zaufany przez klientów usług AD FS, zalecamy używanie certyfikatu SSL wystawionego przez publiczny urząd certyfikacji (innej firmy) lub przez urząd certyfikacji, który jest podmiotem podrzędnym publicznie zaufanego katalogu głównego. Na przykład VeriSign lub Thawte.  <br/> |
|**Certyfikat podpisywania tokenu** <br/> |Jest to standardowy certyfikat X.509 używany do bezpiecznego podpisywania wszystkich tokenów, które wydaje serwer federujący, Microsoft 365 przyjmuje i sprawdza.  <br/> |Certyfikat podpisywania tokenu musi zawierać klucz prywatny, który jest łańcuchem do zaufanego katalogu głównego w ujmce w usługę serwisową. Domyślnie usługi AD FS tworzą certyfikat z podpisem własnym. Jednak w zależności od potrzeb organizacji możesz zmienić ten certyfikat na certyfikat wystawiony przez urząd certyfikacji przy użyciu przystawki zarządzania usługami AD FS.  <br/>**Przestroga:** Certyfikat podpisywania tokenu ma krytyczne znaczenie dla stabilności usługi fs. Jeśli certyfikat zostanie zmieniony, Microsoft 365 o tej zmianie musi zostać powiadomiony. Jeśli powiadomienie nie zostanie dostarczone, użytkownicy nie mogą zalogować się do swoich usług Microsoft 365 usług.<br/>**Zalecenie:** Zalecamy używanie certyfikatu podpisywania tokenu z podpisem własnym generowanego przez usługi AD FS. Ta opcja domyślnie zarządza tym certyfikatem. Gdy na przykład ten certyfikat ma nie upłynąć, usługi AD FS wygeneruje nowy certyfikat z podpisem własnym.  <br/> |
   
Federowe serwery proxy wymagają certyfikatu opisanego w poniższej tabeli.
  
| Typ certyfikatu | Opis | Co należy wiedzieć przed wdrożeniem |
|:-----|:-----|:-----|
|Certyfikat SSL  <br/> |Jest to standardowy certyfikat SSL używany do zabezpieczania komunikacji między serwerami federacyjną, federacyjną serwerem proxy i komputerami klienckimi internetowymi.  <br/> |Ten certyfikat SSL musi być powiązany z domyślną witryną sieci Web w programie IIS, aby można było pomyślnie uruchomić kreatora Konfiguracji federacyjnych serwerów proxy usług AD FS.  <br/> Ten certyfikat musi mieć taką samą nazwę podmiotu jak certyfikat SSL skonfigurowany na serwerze federacyjna w sieci firmowej.  <br/> **Zalecenie:** Zalecamy używanie tego samego certyfikatu uwierzytelniania serwera, który jest skonfigurowany na serwerze federowym, z którym jest połączony ten federowany serwer proxy.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certyfikaty do wykrywania automatycznego, Outlook anywhere i synchronizacji z usługą Active Directory

Skierowane do użytkowników zewnętrznych serwery dostępu klienta (CAS) Exchange 2013, Exchange 2010, Exchange 2007 i Exchange 2003 wymagają certyfikatu SSL od innej firmy do bezpiecznego połączenia z usługami wykrywania automatycznego, usługi Outlook Anywhere i synchronizacji usługi Active Directory. Ten certyfikat może już być zainstalowany w środowisku lokalnym.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certyfikat dla serwera hybrydowego Exchange

Skierowane do środowiska zewnętrznego Exchange lub serwery hybrydowe wymagają certyfikatu SSL od innego podmiotu na temat bezpiecznej łączności z Exchange Online poczty. Ten certyfikat należy uzyskać od zewnętrznego dostawcy protokołu SSL.
  
## <a name="microsoft-365-certificate-chains"></a>Microsoft 365 łańcuchów certyfikatów

W tym artykule opisano certyfikaty, które mogą być potrzebne do instalacji w Twojej infrastrukturze. Aby uzyskać więcej informacji na temat certyfikatów zainstalowanych na naszych Microsoft 365, zobacz Microsoft 365 [łańcuchy certyfikatów](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Zobacz też

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)