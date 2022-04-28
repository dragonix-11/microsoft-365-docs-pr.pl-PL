---
title: Planowanie certyfikatów SSL innych firm dla Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Podsumowanie: opisuje certyfikaty SSL potrzebne do Exchange lokalnych i hybrydowych, logowania jednokrotnego przy użyciu usług AD FS, usług Exchange Online i usług Exchange Sieci Web.'
ms.openlocfilehash: 0cd7cce2cd5f0aba8baecab7048d86d629d30427
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100308"
---
# <a name="plan-for-third-party-ssl-certificates-for-microsoft-365"></a>Planowanie certyfikatów SSL innych firm dla Microsoft 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Aby szyfrować komunikację między klientami a środowiskiem Microsoft 365, na serwerach infrastruktury muszą być zainstalowane certyfikaty protokołu Secure Socket Layer (SSL) innych firm.

Ten artykuł jest częścią [planowania sieci i dostrajania wydajności dla Microsoft 365](./network-planning-and-performance.md).
   
Certyfikaty są wymagane dla następujących składników Microsoft 365:
  
- Exchange lokalnie
    
- Logowanie jednokrotne (SSO) (zarówno dla serwerów federacyjnych Active Directory Federation Services (AD FS), jak i serwerów proxy serwerów federacyjnych usług AD FS)
    
- usługi Exchange Online, takie jak wykrywanie automatyczne, Outlook Anywhere i usługi sieci Web Exchange
    
- serwer hybrydowy Exchange
    
## <a name="certificates-for-exchange-on-premises"></a>Certyfikaty dla Exchange lokalnie

Aby zapoznać się z omówieniem sposobu używania certyfikatów cyfrowych w celu zapewnienia bezpieczeństwa komunikacji między lokalną organizacją Exchange i Exchange Online bezpiecznym, zobacz artykuł TechNet [Understanding Certificate Requirements (Informacje o wymaganiach dotyczących certyfikatów](/previous-versions/exchange-server/exchange-141/gg476123(v=exchg.141))).
  
## <a name="certificates-for-single-sign-on"></a>Certyfikaty na potrzeby logowania jednokrotnego

Aby zapewnić użytkownikom uproszczone środowisko logowania jednokrotnego, które obejmuje niezawodne zabezpieczenia, certyfikaty wyświetlane w poniższej tabeli są wymagane na serwerach federacyjnych lub serwerach proxy serwera federacyjnego. Poniższa tabela koncentruje się na Active Directory Federation Services (AD FS), mamy również więcej informacji na temat [korzystania z dostawców tożsamości innych firm](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).
  
| Typ certyfikatu | Opis | Co należy wiedzieć przed wdrożeniem |
|:-----|:-----|:-----|
|**Certyfikat SSL (nazywany również certyfikatem uwierzytelniania serwera)** <br/> |Jest to standardowy certyfikat SSL, który służy do zabezpieczania komunikacji między serwerami federacyjnymi, klientami i komputerami proxy serwera federacyjnego.  <br/> |Usługi AD FS wymagają certyfikatu SSL. Domyślnie usługi AD FS używa certyfikatu SSL, który jest skonfigurowany dla domyślnej witryny internetowej w Internet Information Services (IIS).  <br/> Nazwa podmiotu tego certyfikatu SSL służy do określania nazwy usługi federacyjnej (FS) dla każdego wdrożonego wystąpienia usług AD FS. Rozważ wybranie nazwy podmiotu dla wszelkich nowych certyfikatów wystawionych przez urząd certyfikacji, które najlepiej reprezentują nazwę firmy lub organizacji do Microsoft 365. Ta nazwa musi być routingu internetowego.  <br/>**Ostrożność:** Usługi AD FS wymagają, aby ten certyfikat SSL nie miał nazwy podmiotu bez kropki (krótkiej nazwy).          <br/> **Zalecenie:** Ponieważ ten certyfikat musi być zaufany przez klientów usług AD FS, zalecamy użycie certyfikatu SSL wystawionego przez publiczny urząd certyfikacji (innej firmy) lub przez urząd certyfikacji podrzędny do publicznego zaufanego katalogu głównego; na przykład VeriSign lub Thawte.  <br/> |
|**Certyfikat podpisywania tokenu** <br/> |Jest to standardowy certyfikat X.509 używany do bezpiecznego podpisywania wszystkich tokenów wystawianych przez serwer federacyjny i który Microsoft 365 akceptuje i weryfikuje.  <br/> |Certyfikat podpisywania tokenu musi zawierać klucz prywatny, który jest łańcuchem do zaufanego katalogu głównego w usługach FS. Domyślnie usługi AD FS tworzy certyfikat z podpisem własnym. Jednak w zależności od potrzeb organizacji można zmienić ten certyfikat na certyfikat wystawiony przez urząd certyfikacji przy użyciu przystawki zarządzania usługami AD FS.  <br/>**Ostrożność:** Certyfikat podpisywania tokenu ma kluczowe znaczenie dla stabilności usług FS. Jeśli certyfikat zostanie zmieniony, Microsoft 365 musi zostać powiadomiony o zmianie. Jeśli powiadomienie nie zostanie dostarczone, użytkownicy nie będą mogli zalogować się do swoich ofert usług Microsoft 365.<br/>**Zalecenie:** Zalecamy użycie certyfikatu podpisywania tokenu z podpisem własnym, który jest generowany przez usługi AD FS. W ten sposób domyślnie zarządza tym certyfikatem. Na przykład gdy ten certyfikat wkrótce wygaśnie, usługi AD FS wygenerują nowy certyfikat z podpisem własnym.  <br/> |
   
Serwery proxy serwera federacyjnego wymagają certyfikatu opisanego w poniższej tabeli.
  
| Typ certyfikatu | Opis | Co należy wiedzieć przed wdrożeniem |
|:-----|:-----|:-----|
|Certyfikat SSL  <br/> |Jest to standardowy certyfikat SSL używany do zabezpieczania komunikacji między serwerem federacyjnym, serwerem proxy serwera federacyjnego i komputerami klienckimi w Internecie.  <br/> |Aby można było pomyślnie uruchomić kreatora konfiguracji serwera proxy usług AD FS, ten certyfikat SSL musi być powiązany z domyślną witryną sieci Web w usługach IIS.  <br/> Ten certyfikat musi mieć taką samą nazwę podmiotu jak certyfikat SSL, który został skonfigurowany na serwerze federacyjnym w sieci firmowej.  <br/> **Zalecenie:** Zalecamy użycie tego samego certyfikatu uwierzytelniania serwera skonfigurowanego na serwerze federacyjnym, z którym łączy się ten serwer proxy serwera federacyjnego.  <br/> |
   
## <a name="certificates-for-autodiscover-outlook-anywhere-and-active-directory-synchronization"></a>Certyfikaty do wykrywania automatycznego, Outlook Anywhere i synchronizacji usługi Active Directory

Zewnętrzne Exchange 2013 r., Exchange 2010 r., Exchange 2007 r. i Exchange 2003 serwery dostępu klienta (CAS) wymagają certyfikatu SSL innej firmy na potrzeby bezpiecznych połączeń dla usług automatycznego wykrywania, Outlook Anywhere i usług synchronizacji usługi Active Directory. Ten certyfikat może już być zainstalowany w środowisku lokalnym.
  
## <a name="certificate-for-an-exchange-hybrid-server"></a>Certyfikat dla serwera hybrydowego Exchange

Zewnętrzny serwer lub serwery hybrydowe Exchange wymagają certyfikatu SSL innej firmy w celu zapewnienia bezpiecznej łączności z usługą Exchange Online. Musisz pobrać ten certyfikat od innego dostawcy protokołu SSL.
  
## <a name="microsoft-365-certificate-chains"></a>łańcuchy certyfikatów Microsoft 365

W tym artykule opisano certyfikaty, które mogą być konieczne do zainstalowania w infrastrukturze. Aby uzyskać więcej informacji na temat certyfikatów zainstalowanych na naszych serwerach Microsoft 365, zobacz [Microsoft 365 Łańcuchy certyfikatów](https://support.office.com/article/0c03e6b3-e73f-4316-9e2b-bf4091ae96bb).
  
## <a name="see-also"></a>Zobacz też

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)