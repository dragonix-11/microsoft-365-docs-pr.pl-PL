---
title: Rekordy DNS dla Office 365 DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Podsumowanie: rekordy DNS dla Office 365 DoD'
hideEdit: true
ms.openlocfilehash: f3d7926b69de24786891406a7613c44ab5013dfa
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019351"
---
# <a name="dns-records-for-office-365-dod"></a>Rekordy DNS dla Office 365 DoD

*Ten artykuł dotyczy wszystkich Office 365 DoD i Microsoft 365 DoD*

W ramach dołączania do usługi Office 365 DoD należy dodać domeny SMTP i SIP do dzierżawy usług online.  Możesz to zrobić za pomocą polecenia cmdlet New-MsolDomain w programie PowerShell usługi Azure AD lub użyć portalu [Azure Government Portal](https://portal.azure.us) , aby rozpocząć proces dodawania domeny i udowodnienia własności.

Po dodaniu domen do dzierżawy i weryfikacji ich poprawności skorzystaj z poniższych wskazówek, aby dodać odpowiednie rekordy DNS dla usług poniżej.  Może być konieczne zmodyfikowanie poniższej tabeli zgodnie z potrzebami Twojej organizacji w odniesieniu do przychodzących rekordów MX i wszystkich istniejących Exchange rekordów wykrywania automatycznego.  Zdecydowanie zalecamy skoordynowanie tych rekordów DNS ze swoim zespołem ds. wiadomości w celu uniknięcia  usterek lub błędnego dostarczania poczty e-mail.

## <a name="exchange-online"></a>Exchange Online

| Type (Typ) | Priority (Priorytet) | Nazwa hosta | Wskazuje adres lub wartość | Czas wygaśnięcia |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant.mail.protection.office365.us* (zobacz poniżej, aby uzyskać więcej informacji) | Jedna godzina |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | Jedna godzina |
| CNAME | - | autodiscover | autodiscover-dod.office365.us | Jedna godzina |

### <a name="exchange-autodiscover-record"></a>Exchange rekordu wykrywania automatycznego

Jeśli masz program Exchange Server lokalnym, zalecamy pozostawienie istniejącego rekordu w miejscu podczas migracji do programu Exchange Online i zaktualizowanie tego rekordu po ukończeniu migracji.

### <a name="exchange-online-mx-record"></a>Exchange Online REKORD MX

Wartość rekordu MX dla zaakceptowanych domen jest zgodna ze standardowym formatem, jak opisano powyżej: *tenant.mail.protection.office365.us*, zastępując dzierżawę pierwszą częścią domyślnej nazwy dzierżawy.

Jeśli na przykład nazwa Twojej dzierżawy jest contoso.onmicrosoft.us, użyj wartości contoso.mail.protection.office365.us jako wartości rekordu  MX.

## <a name="skype-for-business-online"></a>Skype dla firm Online

### <a name="cname-records"></a>Rekordy CNAME

| Wpisać | Nazwa hosta | Wskazuje adres lub wartość | Czas wygaśnięcia |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.dod.skypeforbusiness.us | Jedna godzina |
| CNAME | lyncdiscover | webdir.online.dod.skypeforbusiness.us | Jedna godzina | 

### <a name="srv-records"></a>Rekordy SRV

| Wpisać | Usługa | Protocol (Protokół) | Port | Weight (Waga) | Priority (Priorytet) | Name (Nazwa) | Target (Element docelowy) | Czas wygaśnięcia |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1 | 100 | @ | sipdir.online.dod.skypeforbusiness.us | Jedna godzina |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.dod.skypeforbusiness.us | Jedna godzina |

## <a name="other-dns-records"></a>Inne rekordy DNS

> [!IMPORTANT]
> Jeśli w Twojej strefie DNS jest już istniejący rekord *CNAME msoid***, należy usunąć** ten rekord z systemu DNS.  Rekord msoid jest niezgodny z aplikacją Microsoft 365 Enterprise *Apps (dawniej Office 365 ProPlus)* i uniemożliwi aktywację.
