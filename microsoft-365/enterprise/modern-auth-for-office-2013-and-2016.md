---
title: Jak działa nowoczesne uwierzytelnianie dla aplikacji klienckich Office 2013 i Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Dowiedz się, jak Microsoft 365 nowoczesne funkcje uwierzytelniania działają inaczej w przypadku aplikacji klienckich Office 2013 i 2016.
ms.openlocfilehash: 9c4cdc384ceded4ce3bb78ae4e67e0f4c5a503de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093377"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Jak działa nowoczesne uwierzytelnianie dla aplikacji klienckich Office 2013, Office 2016 i Office 2019

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Przeczytaj ten artykuł, aby dowiedzieć się, jak aplikacje klienckie Office 2013, Office 2016 i Office 2019 korzystają z nowoczesnych funkcji uwierzytelniania opartych na konfiguracji uwierzytelniania w dzierżawie Microsoft 365 dla Exchange Online, SharePoint Online i Skype dla firm Online.

> [!NOTE]
> Starsze aplikacje klienckie, takie jak Office 2010 i Office dla komputerów Mac 2011, nie obsługują nowoczesnego uwierzytelniania i mogą być używane tylko z uwierzytelnianiem podstawowym.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Dostępność nowoczesnego uwierzytelniania dla usług Microsoft 365

W przypadku usług Microsoft 365 domyślnym stanem nowoczesnego uwierzytelniania jest:

- Domyślnie **włączono** dla Exchange Online. Zobacz [Włączanie lub wyłączanie nowoczesnego uwierzytelniania w Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662), aby je wyłączyć lub włączyć.

- Domyślnie **włączono** dla SharePoint Online.

- Domyślnie **włączono** dla Skype dla firm Online. Zobacz [Włączanie Skype dla firm Online na potrzeby nowoczesnego uwierzytelniania](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx), aby wyłączyć lub włączyć.

> [!NOTE]
> W przypadku dzierżaw utworzonych **przed** 1 sierpnia 2017 r. nowoczesne uwierzytelnianie jest domyślnie **wyłączone** dla Exchange Online i Skype dla firm Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>Zachowanie logowania Office aplikacji klienckich

Office 2013 aplikacje klienckie domyślnie obsługują starsze uwierzytelnianie. Starsza wersja oznacza, że obsługują one asystenta logowania online firmy Microsoft lub uwierzytelnianie podstawowe. Aby klienci mogli korzystać z nowoczesnych funkcji uwierzytelniania, klient Windows musi mieć ustawione klucze rejestru. Aby uzyskać instrukcje, zobacz [Włączanie nowoczesnego uwierzytelniania dla Office 2013 na urządzeniach Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Aby włączyć nowoczesne uwierzytelnianie na dowolnych urządzeniach z systemem Windows (na przykład komputerów przenośnych i tabletów), na których zainstalowano pakiet Microsoft Office 2013, musisz ustawić poniższe klucze rejestru. Klucze musisz ustawić na każdym urządzeniu, na którym chcesz włączyć nowoczesne uwierzytelnianie:

|**Klucz rejestru**|**Type**|**Wartość** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Przeczytaj [artykuł How to use Modern Authentication (ADAL) with Skype dla firm to learn about how it works with Skype dla firm (Jak korzystać z nowoczesnego uwierzytelniania (ADAL) z Skype dla firm](./hybrid-modern-auth-overview.md), aby dowiedzieć się, jak działa z Skype dla firm.

klienci Office 2016 i Office 2019 domyślnie obsługują nowoczesne uwierzytelnianie i klient nie musi wykonywać żadnych działań w celu korzystania z tych nowych przepływów. Jednak do używania starszego uwierzytelniania jest wymagana jawna akcja.

Kliknij poniższe linki, aby zobaczyć, jak uwierzytelnianie klienta Office 2013, Office 2016 i Office 2019 działa z usługami Microsoft 365 w zależności od tego, czy nowoczesne uwierzytelnianie jest włączone.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype dla firm Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

W poniższej tabeli opisano zachowanie uwierzytelniania dla aplikacji klienckich Office 2013, Office 2016 i Office 2019, gdy łączą się z Exchange Online przy użyciu nowoczesnego uwierzytelniania lub bez tego uwierzytelniania.

|Office wersji aplikacji klienckiej****|Obecny klucz rejestru?****|Nowoczesne uwierzytelnianie w środowisku?****|Zachowanie uwierzytelniania z włączonym nowoczesnym uwierzytelnianiem dla dzierżawy (domyślne)****|Zachowanie uwierzytelniania z nowoczesnym uwierzytelnianiem wyłączone dla dzierżawy****|
|:-----|:-----|:-----|:-----|:-----|
|Pakiet Office 2019  <br/> |Nr <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Tak  <br/> |Wymusza nowoczesne uwierzytelnianie na Outlook 2013, 2016 lub 2019. <br/> [Więcej informacji](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Wymusza nowoczesne uwierzytelnianie w kliencie Outlook.<br/> |
|Pakiet Office 2019  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL=0  <br/> |Nie  <br/> |Uwierzytelnianie podstawowe  <br/> |Uwierzytelnianie podstawowe  <br/> |
|Office 2016  <br/> |Nr <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Tak  <br/> |Wymusza nowoczesne uwierzytelnianie w wersji 2013, 2016 lub 2019. <br/> [Więcej informacji](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Wymusza nowoczesne uwierzytelnianie w kliencie Outlook.<br/> |
|Office 2016  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL=0  <br/> |Nie  <br/> |Uwierzytelnianie podstawowe  <br/> |Uwierzytelnianie podstawowe  <br/> |
|Office 2013  <br/> |Nie  <br/> |Nie  <br/> |Uwierzytelnianie podstawowe  <br/> |Uwierzytelnianie podstawowe  <br/> |
|Office 2013  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyte uwierzytelnianie podstawowe. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawa nie jest włączona.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

W poniższej tabeli opisano zachowanie uwierzytelniania dla aplikacji klienckich Office 2013, Office 2016 i Office 2019, gdy nawiązują połączenie z usługą SharePoint Online przy użyciu nowoczesnego uwierzytelniania lub bez tego uwierzytelniania.

|Office wersji aplikacji klienckiej****|Obecny klucz rejestru?****|Nowoczesne uwierzytelnianie w środowisku?****|Zachowanie uwierzytelniania z włączonym nowoczesnym uwierzytelnianiem dla dzierżawy (domyślne)****|Zachowanie uwierzytelniania z nowoczesnym uwierzytelnianiem wyłączone dla dzierżawy****|
|:-----|:-----|:-----|:-----|:-----|
|Pakiet Office 2019  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Nie można nawiązać połączenia.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Nie można nawiązać połączenia.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |
|Office 2016  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Nie można nawiązać połączenia.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Nie można nawiązać połączenia.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |
|Office 2013  <br/> |Nie  <br/> |Nie  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |
|Office 2013  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Tylko nowoczesne uwierzytelnianie.  <br/> |Nie można nawiązać połączenia.  <br/> |

### <a name="skype-for-business-online"></a>Skype dla firm Online
<a name="BK_SFBO"> </a>

W poniższej tabeli opisano zachowanie uwierzytelniania dla aplikacji klienckich Office 2013, Office 2016 i Office 2019, gdy nawiązują połączenie z usługą Skype dla firm Online przy użyciu nowoczesnego uwierzytelniania lub bez tego uwierzytelniania.

|Office wersji aplikacji klienckiej****|Obecny klucz rejestru?****|Nowoczesne uwierzytelnianie w środowisku?****|Zachowanie uwierzytelniania z włączonym nowoczesnym uwierzytelnianiem dla dzierżawy****|Zachowanie uwierzytelniania z nowoczesnym uwierzytelnianiem wyłączone dla dzierżawy (domyślne)****|
|:-----|:-----|:-----|:-----|:-----|
|Pakiet Office 2019  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |
|Pakiet Office 2019  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |
|Office 2016  <br/> |Nie lub EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |
|Office 2016  <br/> |Tak, EnableADAL = 0  <br/> |Nie  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |
|Office 2013  <br/> |Nie  <br/> |Nie  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |
|Office 2013  <br/> |Tak, EnableADAL = 1  <br/> |Tak  <br/> |Najpierw podjęto próbę nowoczesnego uwierzytelniania. Jeśli serwer odmówi nowoczesnego połączenia uwierzytelniania, zostanie użyty Asystent logowania online firmy Microsoft. Serwer odmawia nowoczesnego uwierzytelniania, gdy dzierżawy usługi Skype dla firm Online nie są włączone.  <br/> |Tylko Asystent logowania w usłudze Microsoft Online.  <br/> |

## <a name="see-also"></a>Zobacz też

[Włączanie nowoczesnego uwierzytelniania dla pakietu Office 2013 na urządzeniach z systemem Windows](../admin/security-and-compliance/enable-modern-authentication.md)

[Uwierzytelnianie wieloskładnikowe na platformie Microsoft365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Zaloguj się do Microsoft 365 przy użyciu uwierzytelniania wieloskładnikowego](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)