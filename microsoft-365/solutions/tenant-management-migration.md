---
title: Krok nr 4. Migracja do dzierżawy Microsoft 365 przedsiębiorstwa
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Przemigruj Windows urządzenia, aplikacje Office klienckie i serwery Office dzierżaw Microsoft 365 dzierżaw.
ms.openlocfilehash: 1892ae3da900f1c940866a2b2a3c70c1d6cb5db3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63011278"
---
# <a name="step-4-migration-for-your-microsoft-365-for-enterprise-tenants"></a>Krok nr 4. Migracja do dzierżawy Microsoft 365 przedsiębiorstwa

Większość przedsiębiorstw ma niejednorodne środowisko, które zawiera wiele wersji systemów operacyjnych, oprogramowania klienckiego i oprogramowania serwera. Microsoft 365 dla przedsiębiorstw obejmują najbezpieczniejsze wersje kluczowych składników Twojej infrastruktury IT. Zawiera również funkcje zwiększające produktywność, które zostały zaprojektowane tak, aby korzystać z technologii chmury.

Aby zmaksymalizować wartość biznesową pakietu Microsoft 365 produktów zintegrowanych z przedsiębiorstwem, rozpocznij planowanie i implementowanie strategii migrowania tych wersji:

| Od | Do |
|:-------|:-----|
| Windows 7 i Windows 8.1 | System Windows10 dla firm |
| Office produktów klienckich zainstalowanych na urządzeniach pracowników | Aplikacje usługi Microsoft 365 dla przedsiębiorstw |
| Office serwerów zainstalowanych na serwerach lokalnych | Równoważne usługi chmurowe w programie Microsoft 365 |
|  |  |

## <a name="migrating-to-windows-10"></a>Migrowanie do Windows 10

Każdy Microsoft 365 dla przedsiębiorstwa zawiera licencję na usługę Windows 10 Enterprise. Aby przeprowadzić migrację urządzeń z systemem Windows 7 lub Windows 8.1, możesz przeprowadzić uaktualnienie w miejscu. 14 stycznia 2020 r. zakończono pomoc techniczną dla Windows 7 *stycznia 2020 r*. 

Aby uzyskać dodatkowe metody Windows 10 Enterprise uaktualniania w miejscu, zobacz Windows 10 [scenariuszy wdrażania](/windows/deployment/windows-10-deployment-scenarios). Możesz również [samodzielnie Windows 10](/windows/deployment/planning/) wdrożenie.

## <a name="migrating-to-microsoft-365-apps-for-enterprise"></a>Migrowanie do Aplikacje Microsoft 365 dla przedsiębiorstw

Microsoft 365 dla przedsiębiorstw obejmuje Aplikacje Microsoft 365 dla przedsiębiorstw, wersję produktów klienckich pakietu Office (Word, PowerPoint, Excel i Outlook), która jest instalowana i aktualizowana przez firmę Microsoft w chmurze. Aby uzyskać więcej informacji, zobacz [Informacje Aplikacje Microsoft 365 dla przedsiębiorstw](/deployoffice/about-microsoft-365-apps).

Zamiast dbać o aktualną wersję Office 2019 lub starszej wersji, zrób tak:

1. Uzyskaj i przypisz licencję Microsoft 365 użytkowników.
2. Odinstaluj Office 2013 lub Office 2016 na swoich komputerach.
3. Instalowanie Aplikacje Microsoft 365 dla przedsiębiorstw, indywidualnie lub podczas procesu procesu it. Aby uzyskać więcej informacji, zobacz [Przewodnik po wdrażaniu Aplikacje Microsoft 365](/deployoffice/deployment-guide-microsoft-365-apps).

Aplikacje Microsoft 365 dla przedsiębiorstw automatycznie instaluje zarówno aktualizacje zabezpieczeń, jak i nowe funkcje, i może korzystać z usług opartych na chmurze w programie Microsoft 365 w celu zwiększenia bezpieczeństwa i produktywności.

## <a name="migrating-on-premises-servers-and-data-to-microsoft-365"></a>Migrowanie lokalnych serwerów i danych do Microsoft 365

Microsoft 365 dla przedsiębiorstwa obejmują oparte na chmurze wersje usług serwera Office, które używają niektórych narzędzi tego samego narzędzia co lokalne wersje oprogramowania serwera Office, takie jak przeglądarki sieci Web i Outlook klienta. Te usługi w chmurze są automatycznie aktualizowane na podstawie zabezpieczeń i nowych funkcji. Po migracji twój dział IT może zaoszczędzić czas, który zajmuje konserwacja i aktualizowanie serwerów lokalnych.

Skorzystaj z następujących zasobów, aby uzyskać informacje na temat migrowania użytkowników i danych dla określonych Microsoft 365 obciążeniami pracą:

- [Przenoszenie skrzynek pocztowych z lokalnych Exchange Server do Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [Migrowanie SharePoint danych z programu SharePoint Server do usługi SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)
- [Migrowanie Skype dla firm Online do usługi Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

## <a name="transition-your-entire-organization"></a>Przejście na całą organizację

Aby lepiej obrazować sposób przenoszenia całej organizacji do produktów i usług w programie Microsoft 365 dla przedsiębiorstw, pobierz ten plakat przejścia:

[![Obraz przedstawiający plakat Przejście do Microsoft 365 pliku.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

Ten dwustronicowy plakat jest szybkim sposobem na inwentaryzację istniejącej infrastruktury. Skorzystaj z niego, aby uzyskać wskazówki dotyczące przechodzenia do produktu lub usługi w programie Microsoft 365 dla przedsiębiorstw. Przedstawiono w nim Windows i Office oraz inne elementy infrastruktury i zabezpieczeń, takie jak zarządzanie urządzeniami, ochrona tożsamości i zagrożeń oraz ochrona informacji i zgodność z przepisami.

## <a name="results-of-step-4"></a>Wyniki kroku 4

W przypadku migracji dla Microsoft 365 dzierżawy usługi ustalisz:

- Urządzenia z systemem Windows 7 lub Windows 8.1 oraz plan ich aktualizacji do Windows 10 Enterprise.
- Na jakich urządzeniach działa Office klienckie, oraz plan ich aktualizacji w celu Microsoft 365 dla przedsiębiorstw.
- Które lokalne usługi Office serwera powinny zostać zmigrowane do swoich odpowiedników Microsoft 365 oraz plan migracji ich i ich danych.

Oto przykład dzierżawy z ukończoną migracją serwerów lokalnych.

![Przykład dzierżawy z ukończoną migracją serwerów lokalnych.](../media/tenant-management-overview/tenant-management-tenant-build-step4.png)

Na poniższej ilustracji organizacja ma:

- Jego lokalne skrzynki pocztowe zostały Exchange Server do Exchange Online.
- Dane i witryny serwera SharePoint zostały zmigrowane do SharePoint w Microsoft 365.

## <a name="ongoing-maintenance-for-migration"></a>Bieżąca konserwacja migracji

Na bieżąco może być konieczne:

- W zależności od stanu migracji skrzynki Exchange, kontynuuj wycofywanie przejścia do Exchange Online do organizacji.
- W zależności od stanu migracji witryny lokalnej SharePoint kontynuuj wycofywanie przejścia do usługi SharePoint w Microsoft 365 do organizacji.

## <a name="next-step"></a>Następny krok

[![Krok 5. Wdrażanie zarządzania urządzeniami i aplikacjami.](../media/tenant-management-overview/tenant-management-step-grid-device-mgmt.png)](tenant-management-device-management.md)

Kontynuuj zarządzanie [urządzeniami i aplikacjami,](tenant-management-device-management.md) aby wdrożyć zarządzanie urządzeniami i aplikacjami.