---
title: Jak działa nowoczesne uwierzytelnianie w aplikacjach Office 2013 i Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Dowiedz się Microsoft 365 jak funkcje nowoczesnego uwierzytelniania działają inaczej w Office klientach pakietu Office 2013 i 2016.
ms.openlocfilehash: c3586029a3c1ea73dae30696c74011e3dd22400d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973657"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Jak działa nowoczesne uwierzytelnianie w aplikacjach Office 2013, Office 2016 i Office 2019

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Przeczytaj ten artykuł, aby dowiedzieć się, jak aplikacje klienckie programów Office 2013, Office 2016 i Office 2019 korzystają z funkcji nowoczesnego uwierzytelniania na podstawie konfiguracji uwierzytelniania w dzierżawie usług Microsoft 365 Exchange Online, SharePoint Online i Skype dla firm Online.

> [!NOTE]
> Starsze aplikacje klienckie, takie jak Office 2010 i Office dla komputerów Mac 2011, nie obsługują nowoczesnego uwierzytelniania i mogą być używane tylko w przypadku uwierzytelniania podstawowego.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Dostępność nowoczesnego uwierzytelniania dla Microsoft 365 usług

W przypadku Microsoft 365 domyślny stan nowoczesnego uwierzytelniania to:

- Domyślnie **włączone** dla Exchange Online. Zobacz [Włączanie lub wyłączanie nowoczesnego uwierzytelniania w Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662), aby wyłączyć lub włączyć tę funkcję.

- Domyślnie **włączone** dla usługi SharePoint Online.

- Domyślnie **włączone** dla Skype dla firm Online. Zobacz [Włączanie Skype dla firm Online dla nowoczesnego uwierzytelniania](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx), aby wyłączyć lub włączyć tę funkcję.

> [!NOTE]
> W przypadku dzierżaw utworzonych **przed** 1 sierpnia 2017 r. nowoczesne uwierzytelnianie jest domyślnie wyłączone  dla usług Exchange Online i Skype dla firm Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>Zachowanie logowania w Office klienckich

Office klienckie w wersji 2013 domyślnie obsługują starsze uwierzytelnianie. Oznacza to obsługę asystenta logowania w witrynie Microsoft Online Online Lub uwierzytelniania podstawowego. Aby te klienci korzystali z funkcji nowoczesnego uwierzytelniania, Windows musi mieć ustawione klucze rejestru. Aby uzyskać instrukcje, [zobacz Włączanie nowoczesnego uwierzytelniania Office 2013 na Windows urządzeniach](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Aby włączyć nowoczesne uwierzytelnianie na dowolnych urządzeniach z systemem Windows (na przykład komputerów przenośnych i tabletów), na których zainstalowano pakiet Microsoft Office 2013, musisz ustawić poniższe klucze rejestru. Klucze musisz ustawić na każdym urządzeniu, na którym chcesz włączyć nowoczesne uwierzytelnianie:

|**Klucz rejestru**|**Type**|**Wartość** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Przeczytaj [Jak używać nowoczesnego uwierzytelniania (ADAL, Modern Authentication) z Skype dla firm](./hybrid-modern-auth-overview.md), aby dowiedzieć się, jak ta metoda działa z Skype dla firm.

klienci Office 2016 i Office 2019 domyślnie obsługują nowoczesne uwierzytelnianie i nie trzeba nic więcej zrobić, aby klient używał tych nowych przepływów. Jednak w celu korzystania ze starszego uwierzytelniania wymagane jest jawne działanie.

Kliknij poniższe linki, aby dowiedzieć się, jak działa uwierzytelnianie klientów usług Office 2013, Office 2016 i Office 2019 z usługami Microsoft 365 w zależności od tego, czy jest włączone nowoczesne uwierzytelnianie.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype dla firm Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

W poniższej tabeli opisano zachowanie uwierzytelniania w przypadku aplikacji klienckich programów Office 2013, Office 2016 i Office 2019 podczas nawiązania przez nie połączenia z aplikacją Exchange Online z nowoczesnym uwierzytelnianiem lub bez niego.

|Office wersji aplikacji klienckiej****|Prezentuj klucz rejestru?****|Nowoczesne uwierzytelnianie w dniu?****|Zachowanie uwierzytelniania przy włączonym nowoczesnym uwierzytelnianiu dla dzierżawy (domyślne)****|Zachowanie uwierzytelniania przy wyłączonym nowoczesnym uwierzytelnianiu dla dzierżawy****|
|:-----|:-----|:-----|:-----|:-----|
|Pakiet Office 2019  <br/> |Nie, <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Tak  <br/> |Wymusza nowoczesne uwierzytelnianie na Outlook 2013, 2016 lub 2019. <br/> [Więcej informacji](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Wymusza nowoczesne uwierzytelnianie w Outlook klienta.<br/> |
|Pakiet Office 2019  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL=0  <br/> |Nie  <br/> |Uwierzytelnianie podstawowe  <br/> |Uwierzytelnianie podstawowe  <br/> |
|Office 2016  <br/> |Nie, <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Tak  <br/> |Wymusza nowoczesne uwierzytelnianie w dniu 2013, 2016 lub 2019. <br/> [Więcej informacji](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Wymusza nowoczesne uwierzytelnianie w Outlook klienta.<br/> |
|Office 2016  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL=0  <br/> |Nie  <br/> |Uwierzytelnianie podstawowe  <br/> |Uwierzytelnianie podstawowe  <br/> |
|Office 2013  <br/> |Nie  <br/> |Nie  <br/> |Uwierzytelnianie podstawowe  <br/> |Uwierzytelnianie podstawowe  <br/> |
|Office 2013  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

W poniższej tabeli opisano zachowanie uwierzytelniania dla aplikacji klienckich programów Office 2013, Office 2016 i Office 2019 podczas łączenia się z usługą SharePoint Online z nowoczesnym uwierzytelnianiem lub bez niego.

|Office wersji aplikacji klienckiej****|Prezentuj klucz rejestru?****|Nowoczesne uwierzytelnianie w dniu?****|Zachowanie uwierzytelniania przy włączonym nowoczesnym uwierzytelnianiu dla dzierżawy (domyślne)****|Zachowanie uwierzytelniania przy wyłączonym nowoczesnym uwierzytelnianiu dla dzierżawy****|
|:-----|:-----|:-----|:-----|:-----|
|Pakiet Office 2019  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Niepowodzenie połączenia.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Niepowodzenie połączenia.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |
|Office 2016  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Niepowodzenie połączenia.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Niepowodzenie połączenia.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |
|Office 2013  <br/> |Nie  <br/> |Nie  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |
|Office 2013  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Niepowodzenie połączenia.  <br/> |

### <a name="skype-for-business-online"></a>Skype dla firm Online
<a name="BK_SFBO"> </a>

W poniższej tabeli opisano zachowanie uwierzytelniania dla aplikacji klienckich programów Office 2013, Office 2016 i Office 2019 podczas łączenia się z usługą Skype dla firm Online z nowoczesnym uwierzytelnianiem lub bez niego.

|Office wersji aplikacji klienckiej****|Prezentuj klucz rejestru?****|Nowoczesne uwierzytelnianie w dniu?****|Zachowanie uwierzytelniania przy włączonym nowoczesnym uwierzytelnianiu dla dzierżawy****|Zachowanie uwierzytelniania przy wyłączonym nowoczesnym uwierzytelnianiu dla dzierżawy (domyślne)****|
|:-----|:-----|:-----|:-----|:-----|
|Pakiet Office 2019  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |
|Office 2016  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |
|Office 2013  <br/> |Nie  <br/> |Nie  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |
|Office 2013  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw jest podejmowana próba nowoczesnego uwierzytelniania. Jeśli serwer odmówi nawiązaniu połączenia przy użyciu nowoczesnego uwierzytelniania, zostanie użyty asystent logowania w witrynie Microsoft Online Sign-in Assistant. Serwer odmawia nowoczesnego uwierzytelniania, gdy funkcja Skype dla firm online nie jest włączona.  <br/> |Tylko Asystent logowania w witrynie Microsoft Online.  <br/> |

## <a name="see-also"></a>Zobacz też

[Włączanie nowoczesnego uwierzytelniania dla pakietu Office 2013 na urządzeniach z systemem Windows](../admin/security-and-compliance/enable-modern-authentication.md)

[Uwierzytelnianie wieloskładnikowe dla Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Logowanie się Microsoft 365 przy użyciu uwierzytelniania wieloskładnikowego](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)