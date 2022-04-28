---
title: Plan oprogramowania klienta i serwera dla Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 08/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-subscription-management
ms.custom: it-pro
description: Ten plan służy do konfigurowania oprogramowania klienckiego i serwera dla Microsoft 365.
ms.openlocfilehash: c42f02f20c9f16dd19f60d051c7f4a4aa5316bf2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090844"
---
# <a name="client-and-server-software-roadmap-for-microsoft-365"></a>Plan oprogramowania klienta i serwera dla Microsoft 365

Większość organizacji korporacyjnych ma heterogeniczne środowisko, które obejmuje wiele wersji systemów operacyjnych, oprogramowania klienckiego i oprogramowania serwera. Microsoft 365 dla Enterprise zawiera najbezpieczniejsze wersje kluczowych składników infrastruktury IT. Obejmuje ona również funkcje zwiększające produktywność, które są przeznaczone do korzystania z technologii w chmurze.

Aby zmaksymalizować wartość biznesową Microsoft 365 dla Enterprise zintegrowanego pakietu produktów, rozpocznij planowanie i implementowanie strategii migracji wydań:

- Klient Office zainstalowany na komputerach w celu Aplikacje Microsoft 365 dla przedsiębiorstw.
- Serwery Office zainstalowane na serwerach z ich równoważnymi usługami w Microsoft 365.
- Windows 7 i Windows 8.1 na urządzeniach do Windows 10 Enterprise.

>[!Note]
>Wsparcie dla Windows 7 zakończyło się *14 stycznia 2020 r*. Aby uzyskać więcej informacji, zobacz [szczegóły dotyczące zakończenia pomocy technicznej](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020).
>

W miarę jak te migracje są realizowane w miarę upływu czasu, twoja organizacja zbliża się do wizji [nowoczesnego miejsca pracy](https://www.microsoft.com/microsoft-365/blog/2018/04/27/making-it-simpler-with-a-modern-workplace/). To bezpieczne i zintegrowane środowisko może pomóc w odblokowaniu pracy zespołowej i kreatywności w organizacji. Microsoft 365 dla Enterprise umożliwia i zwiększa możliwości na całej drodze.

## <a name="migration-for-office-client-products"></a>Migracja produktów klienckich Office

Organizacje duże i małe często używają kombinacji starszych wersji Office produktów klienckich, takich jak Word, Excel i PowerPoint. Te starsze wersje:

- Można [je zaktualizować](https://support.office.com/article/install-office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5) przy użyciu najnowszych aktualizacji zabezpieczeń i poprawek pomocy technicznej. Proces ten jest jednak czasami ręczny i może nie być skalowany w całej organizacji.
- Nie są zoptymalizowane pod kątem korzystania z technologii w chmurze firmy Microsoft, które ułatwiają cyfrową transformację firmy.
- Nie udostępniaj najnowszych funkcji.

Microsoft 365 Enterprise obejmuje Aplikacje Microsoft 365 dla przedsiębiorstw. Ta wersja produktów klienckich Office jest dostępna z Microsoft 365 licencji Enterprise. Jest on instalowany i aktualizowany z chmury firmy Microsoft. Aplikacje Microsoft 365 dla przedsiębiorstw zawiera aktualizacje zabezpieczeń i najnowsze funkcje. Aby uzyskać więcej informacji, zobacz [Informacje o Aplikacje Microsoft 365 dla przedsiębiorstw](/deployoffice/about-microsoft-365-apps).

### <a name="office-2007"></a>Office 2007

W przypadku wersji Office w wersji Office 2007 koniec wsparcia już minął. Aby uzyskać więcej informacji, zobacz [plan zakończenia wsparcia Office 2007](/deployoffice/office-2007-end-support-roadmap) r.

Zamiast uaktualniać komputery z systemem Office 2007 r. do Office 2010 r., Office 2013 r. lub Office 2016 r., rozważ wykonanie następujących kroków:

1. Pobierz i przypisz licencję Microsoft 365 dla użytkowników.
2. Odinstaluj Office 2007 na swoich komputerach.
3. Zainstaluj Aplikacje Microsoft 365 dla przedsiębiorstw pojedynczo lub podczas wdrażania IT. Aby uzyskać więcej informacji, zobacz [Przewodnik wdrażania Aplikacje Microsoft 365](/deployoffice/deployment-guide-microsoft-365-apps).

Aplikacje Microsoft 365 dla przedsiębiorstw automatycznie instaluje aktualizacje. Może ona korzystać z usług opartych na chmurze w celu zwiększenia bezpieczeństwa i produktywności.

### <a name="office-2010"></a>Office 2010

W przypadku wersji Office w wersji Office 2010 pomoc *techniczna zakończyła się 13 października 2020 r*. Aby uzyskać więcej informacji, zobacz [plan zakończenia wsparcia technicznego Office 2010](/deployoffice/office-2010-end-support-roadmap) r.

Możesz rozważyć uaktualnienie komputerów z systemem Office 2010 do Office 2013 lub Office 2016. Jednak obie te wersje muszą zostać zaktualizowane ręcznie. Rozważ więc wykonanie następujących kroków:

1. Pobierz i przypisz licencję Microsoft 365 dla użytkowników.
2. Odinstaluj program Office 2010 na swoich komputerach.
3. Zainstaluj Aplikacje Microsoft 365 dla przedsiębiorstw pojedynczo lub podczas wdrażania IT. Aby uzyskać więcej informacji, zobacz [Przewodnik wdrażania Aplikacje Microsoft 365](/deployoffice/deployment-guide-microsoft-365-apps).

Aplikacje Microsoft 365 dla przedsiębiorstw automatycznie instaluje zarówno aktualizacje zabezpieczeń, jak i nowe aktualizacje funkcji. Może ona korzystać z usług opartych na chmurze w Microsoft 365 w celu zwiększenia bezpieczeństwa i produktywności.

### <a name="office-2013-and-office-2016"></a>Office 2013 r. i Office 2016 r.

Zobacz [plan zakończenia wsparcia dla Office 2013 roku](/lifecycle/products/microsoft-office-2013). Koniec wsparcia dla Office 2016 r. nie został jeszcze ustalony. W tych wersjach, takich jak Office 2010 r., nadal należy [zainstalować aktualizacje zabezpieczeń](https://support.office.com/article/install-office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5). To zadanie może nie być dobrze skalowane w zależności od rozmiaru organizacji.

Zamiast aktualizować komputery z najnowszymi aktualizacjami zabezpieczeń dla Office 2013 lub Office 2016 r. lub aktualizować komputery z Office 2013 r. do Office 2016 r., rozważ wykonanie następujących kroków:

1. Pobierz i przypisz licencję Microsoft 365 dla użytkowników.
2. Odinstaluj Office 2013 lub Office 2016 na swoich komputerach.
3. Zainstaluj Aplikacje Microsoft 365 dla przedsiębiorstw pojedynczo lub podczas wdrażania IT. Aby uzyskać więcej informacji, zobacz [Przewodnik wdrażania Aplikacje Microsoft 365](/deployoffice/deployment-guide-microsoft-365-apps).

Aplikacje Microsoft 365 dla przedsiębiorstw automatycznie instaluje aktualizacje zabezpieczeń i nowe aktualizacje funkcji. Może ona korzystać z usług opartych na chmurze w Microsoft 365 w celu zwiększenia bezpieczeństwa i produktywności.

## <a name="migration-for-office-server-products"></a>Migracja produktów serwera Office

Zarówno duże, jak i małe organizacje często używają kombinacji starszych wersji produktów serwera Office, takich jak Exchange Server i SharePoint Server. Te starsze wersje:

- Należy zaktualizować o najnowsze aktualizacje zabezpieczeń i poprawki pomocy technicznej. W niektórych przypadkach te aktualizacje są wydawane co miesiąc.
- Nie są zoptymalizowane pod kątem korzystania z technologii w chmurze firmy Microsoft, które ułatwiają cyfrową transformację firmy.
- Nie uwzględniaj nowych aplikacji zwiększających produktywność, takich jak Microsoft Teams.
- Nie uwzględniaj najnowszych funkcji zabezpieczeń, takich jak Exchange i Ochrona usługi Office 365 w usłudze Defender.

Microsoft 365 dla Enterprise obejmuje oparte na chmurze wersje usług serwera Office, które używają niektórych z tych samych narzędzi, co lokalne wersje oprogramowania serwera Office, takie jak przeglądarki internetowe i klient Outlook. Te usługi są automatycznie aktualizowane pod kątem zabezpieczeń. Dzięki temu pracownicy IT oszczędzają czas potrzebny na konserwację i aktualizowanie serwerów lokalnych. Te usługi oferują również nowe ulepszenia funkcji, które nie są obecne w oprogramowaniu serwera Office.

Skorzystaj z następujących zasobów, aby uzyskać informacje o migrowaniu użytkowników i danych dla określonych obciążeń Microsoft 365:

- [Przenoszenie skrzynek pocztowych z lokalnego Exchange Server do Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [Migrowanie danych SharePoint z serwera SharePoint do usługi SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)
- [Migrowanie Skype dla firm Online do Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

### <a name="office-2007-server-products"></a>produkty serwera Office 2007

W przypadku produktów serwera w wersji Office 2007 koniec wsparcia już minął. Aby uzyskać szczegółowe informacje, zobacz następujące artykuły:

- [Exchange 2007 r. plan zakończenia wsparcia](exchange-2007-end-of-support.md)
- [plan zakończenia wsparcia dla serwera SharePoint Server 2007](sharepoint-2007-end-of-support.md)
- [plan zakończenia wsparcia dla serwera Project Server 2007](project-server-2007-end-of-support.md)
- [plan zakończenia obsługi serwera Office Communications Server](/skypeforbusiness/plan-your-deployment/upgrade)
- [PerformancePoint Server 2007 r. plan zakończenia wsparcia](pps-2007-end-of-support.md)

Zamiast uaktualniać produkty serwera w wersji Office 2007 z produktami serwera w wersjach dla Office 2010 r., Office 2013 r. lub Office 2016 r., rozważ wykonanie następujących kroków:

1. Migrowanie danych na serwerach Office 2007 do Microsoft 365. Aby uzyskać więcej informacji lub pomocy, zatrudnij partnera firmy Microsoft.
2. Wprowadź nowe funkcje i procesy robocze dla użytkowników.
3. Jeśli nie potrzebujesz już serwerów lokalnych z uruchomionymi produktami serwera Office 2007, likwiduj je.

### <a name="office-2010-server-products"></a>produkty serwera Office 2010

Wsparcie dla [Exchange Server 2010](exchange-2010-end-of-support.md) r. zakończyło się *13 października 2020 r*.

Koniec wsparcia dla [SharePoint Server 2010](upgrade-from-sharepoint-2010.md) to *13 kwietnia 2021* r.

Zamiast uaktualniać te produkty serwera w wersji Office 2010 z produktami serwera w wersjach dla Office 2013 lub Office 2016, rozważ wykonanie następujących kroków:

1. Migrowanie danych na serwerach Office 2010 do Microsoft 365. Aby uzyskać więcej informacji, zobacz [FastTrack, aby uzyskać Microsoft 365](https://fasttrack.microsoft.com/microsoft365) lub zatrudnić partnera firmy Microsoft.
2. Wprowadź nowe funkcje i procesy robocze dla użytkowników.
3. Jeśli nie potrzebujesz już serwerów lokalnych z uruchomionymi Office produktów serwera 2010, likwiduj je.

### <a name="office-2013-server-products"></a>produkty serwera Office 2013

W przypadku produktów serwera w wersji Office 2013 nie określono końca pomocy technicznej. Zamiast uaktualniać produkty serwera w wersji Office 2013 z produktami serwera w wersji Office 2016, rozważ wykonanie następujących kroków:

1. Migrowanie danych na serwerach Office 2013 do Microsoft 365. Aby uzyskać więcej informacji, zobacz [FastTrack, aby uzyskać Microsoft 365](https://fasttrack.microsoft.com/microsoft365) lub zatrudnić partnera firmy Microsoft.
2. Wprowadź nowe funkcje i procesy robocze dla użytkowników.
3. Jeśli nie potrzebujesz już serwerów lokalnych z uruchomionymi produktami serwera Office 2013, likwiduj je.

### <a name="office-2016-server-products"></a>produkty serwera Office 2016

W przypadku produktów serwera w wersji Office 2016 nie określono końca pomocy technicznej. Aby skorzystać z usług opartych na chmurze i ulepszeń umożliwiających cyfrową transformację firmy, rozważ wykonanie następujących kroków:

1. Migrowanie danych na serwerach Office 2016 do Microsoft 365. Aby uzyskać więcej informacji, zobacz [FastTrack, aby uzyskać Microsoft 365](https://fasttrack.microsoft.com/microsoft365) lub zatrudnić partnera firmy Microsoft.
2. Wprowadź nowe funkcje i procesy robocze dla użytkowników.
3. Jeśli nie potrzebujesz już serwerów lokalnych z uruchomionymi Office produktów serwera 2016, likwiduj je.

## <a name="migration-for-windows-7-and-81"></a>Migracja dla Windows 7 i 8.1

Wsparcie dla Windows 7 zostało zakończone *14 stycznia 2020 r*. Aby przeprowadzić migrację urządzeń z systemem Windows 7 lub Windows 8.1, możesz przeprowadzić uaktualnienie w miejscu.

Aby uzyskać dodatkowe metody, zobacz [Windows 10 scenariusze wdrażania](/windows/deployment/windows-10-deployment-scenarios). Możesz również [samodzielnie zaplanować wdrożenie Windows 10](/windows/deployment/planning/).

## <a name="office-2010-clients-and-servers-and-windows-7"></a>Office 2010 klientów i serwerów oraz Windows 7

Oto wizualne podsumowanie opcji uaktualniania, migracji i przenoszenia do chmury dla klientów i serwerów Office 2010 r. oraz Windows 7:

[![Obraz przedstawiający opcje zakończenia obsługi dla klientów i serwerów Office 2010 oraz Windows 7.](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Ten jednostronicowy plakat to szybki sposób na zrozumienie ścieżek, które można podjąć, aby zarządzać zakończeniem obsługi produktów klienckich i serwerowych Office 2010 oraz Windows 7. Preferowane ścieżki są obsługiwane w Microsoft 365 dla Enterprise.

Możesz [pobrać ten plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) i wydrukować go w rozmiarze litery, rozmiarze prawnym lub rozmiarze tabloidu (11 x 17).

## <a name="transition-your-entire-organization"></a>Przenoszenie całej organizacji

Aby uzyskać lepszy obraz sposobu przenoszenia całej organizacji do produktów i usług w Microsoft 365 dla Enterprise, pobierz ten plakat przejściowy:

[![Obraz przedstawiający plakat Przejście do Microsoft 365.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

Ten dwustronicowy plakat to szybki sposób na inwentaryzację istniejącej infrastruktury. Użyj go, aby uzyskać wskazówki dotyczące przenoszenia do produktu lub usługi w Microsoft 365 dla Enterprise. Przedstawia produkty Windows i Office oraz inne elementy infrastruktury i zabezpieczeń, takie jak zarządzanie urządzeniami, ochrona przed tożsamościami i zagrożeniami oraz ochrona przed informacjami i zgodnością.

## <a name="how-microsoft-migrated-to-microsoft-365-for-enterprise"></a>Jak firma Microsoft zmigrowała Microsoft 365 dla Enterprise

Zobacz, jak eksperci IT w firmie Microsoft zmigrowali firmę do Microsoft 365 dla Enterprise:

- [Wdrażanie i aktualizowanie Aplikacje Microsoft 365 dla przedsiębiorstw](https://www.microsoft.com/itshowcase/Article/Content/757/Deploying-and-updating-Microsoft-Office-365-ProPlus)
- [Firma Microsoft migruje 150 000 skrzynek pocztowych do Exchange Online](https://www.microsoft.com/itshowcase/Article/Content/577/Microsoft-migrates-150000-mailboxes-to-Exchange-Online)
- [SharePoint do chmury: dowiedz się, jak firma Microsoft przeprowadziła własną migrację](https://www.microsoft.com/itshowcase/Article/Content/691/SharePoint-to-the-cloud-Learn-how-Microsoft-ran-its-own-migration)
- [Wdrażanie Windows 10 w firmie Microsoft jako uaktualnienie w miejscu](https://www.microsoft.com/itshowcase/Article/Content/668/Deploying-Windows-10-at-Microsoft-as-an-inplace-upgrade)
- [wdrożenie Windows 10: Wskazówki i wskazówki z działu IT firmy Microsoft](https://www.microsoft.com/itshowcase/Article/Content/951/Windows-10-deployment-tips-and-tricks-from-Microsoft-IT) (wideo)