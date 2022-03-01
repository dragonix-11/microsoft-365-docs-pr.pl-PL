---
title: Wdrażanie Microsoft Information Protection rozwiązania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-overview
- m365solution-mip
- m365initiative-compliance
description: Wskazówki preskrypcji dotyczące wdrażania Microsoft Information Protection (MIP) w organizacji.
ms.openlocfilehash: 92167530771992ee04713d69d1da75af7e468f24
ms.sourcegitcommit: 1627bbbdf2762845274edb6fbfad0b4a5d2f1deb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2021
ms.locfileid: "63018972"
---
# <a name="deploy-a-microsoft-information-protection-solution"></a>Wdrażanie Microsoft Information Protection rozwiązania

>*[Licencjonowanie w Microsoft 365 zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Twoja strategia ochrony informacji jest kierowana potrzebami Biznesowymi. Wiele organizacji musi przestrzegać przepisów prawa i praktyk biznesowych. Ponadto organizacje muszą chronić informacje zastrzeżone, takie jak dane dla konkretnych projektów.

Microsoft Information Protection (MIP) zapewnia ramę, proces i możliwości, których można użyć do zrealizowania określonych celów biznesowych. 

## <a name="microsoft-information-protection-framework"></a>Microsoft Information Protection struktury

Używaj Microsoft Information Protection, aby odnajdować, klasyfikować, chronić informacje poufne oraz zarządzać informacjami poufnymi niezależnie od miejsca życia lub podróży.

![Omówienie rozwiązania MIP](../media/mip-solution-overview-extended.png)

Obejrzyj następującą sesję Ignite, aby zobaczyć, jak te funkcje obsługują się i wybudowywają się wzajemnie: Poznaj swoje dane, chroń dane i zapobiegaj utracie danych dzięki [Microsoft Information Protection](https://myignite.microsoft.com/archives/IG20-OD273).

Aby uzyskać informacje dotyczące zarządzania danymi, zobacz [Zarządzanie informacjami firmy Microsoft w programie Microsoft 365](manage-Information-governance.md).

## <a name="licensing"></a>Licencjonowanie

Funkcje miP są zawarte w Microsoft 365 zgodności. Wymagania licencyjne mogą się różnić nawet w obrębie funkcji, w zależności od opcji konfiguracji. Aby określić wymagania i opcje licencjonowania, zobacz [Microsoft 365 na temat zabezpieczeń i & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="know-your-data"></a>Poznaj swoje dane

![Omówienie rozwiązań do migracji miP](../media/knowyourdata-mipsolution.png)

Znajomość miejsca, w którym znajdują się Twoje poufne dane, często stanowi największe wyzwanie dla wielu organizacji. Klasyfikacja danych w programie MIP ułatwia odnajdowanie i dokładne klasyfikowanie stale rosnących ilości danych owanych przez organizację. Graficzne reprezentacje pomagają uzyskać szczegółowe informacje na temat tych danych, dzięki czemu można skonfigurować i monitorować zasady ochrony danych i zarządzania nim.


|Krok|Opis|Więcej informacji|
|:---|:----------|:---------------|
|1| Opisz kategorie informacji poufnych, które chcesz chronić. <br /><br /> Wiesz już, jakie typy informacji są najcenniejsze dla Twojej organizacji, a jakie nie. Opisz te kategorie we współpracy z uczestnikami projektu, ponieważ są one punktem wyjścia. | [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md) <p> [Dowiedz się więcej o przeszkolnych klasyfikatorach](classifier-learn-about.md)|
|2| Odnajdowanie i klasyfikowanie poufnych danych. <br /><br /> Dane poufne w elementach można znaleźć, stosując wiele różnych metod, takich jak domyślne zasady DLP, ręczne oznaczanie etykiet przez użytkowników oraz automatyczne rozpoznawanie wzorców przy użyciu typów informacji poufnych lub uczenia maszynowego. | [Informacje o klasyfikacji danych](data-classification-overview.md) <p> [Klip wideo: klasyfikacja danych w centrum zgodności](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| Wyświetlanie elementów poufnych.  <br /><br /> Eksplorator zawartości i Eksplorator aktywności umożliwia bardziej dogłębną analizę poufnych elementów i akcji, które użytkownicy mogą stosować do tych elementów.| [Wprowadzenie do Eksploratora zawartości](data-classification-content-explorer.md) <p> [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)|

## <a name="protect-your-data"></a>Ochrona danych

![Omówienie ochrony danych w celu rozwiązania miP](../media/protect-mipsolution.png)

Używaj informacji, które nie wiedzą, gdzie znajdują się Twoje poufne dane, aby skuteczniej je chronić. Nie musisz jednak czekać — możesz natychmiast uruchomić ochronę danych za pomocą etykiet ręcznych, domyślnych i automatycznych. Następnie [potwierdź](data-classification-content-explorer.md) [etykiety](data-classification-activity-explorer.md) i sposób użycia etykiet w Eksploratorze zawartości i Eksploratorze aktywności z poprzedniej sekcji.

|Krok|Opis|Więcej informacji|
|:---|-----------|:---------------|
| 1|[Zdefiniuj etykiety](sensitivity-labels.md) wrażliwości i zasady, które będą chronić dane Twojej organizacji. <br /><br />Oprócz identyfikowania wrażliwości zawartości etykiety te mogą stosować akcje ochrony, takie jak nagłówki, stopki, znaki wodne i szyfrowanie. | [Wprowadzenie do etykiet wrażliwości](get-started-with-sensitivity-labels.md) <br /><br /> [Tworzenie i konfigurowanie etykiet wrażliwości oraz ich zasad](create-sensitivity-labels.md) <br /><br /> [Ograniczanie dostępu do zawartości przy użyciu etykiet wrażliwości w celu zastosowania szyfrowania](encryption-sensitivity-labels.md) |
| 2|Oznaczaj i chroń elementy Microsoft 365 i usług. <br /><br />Etykiety wrażliwości są obsługiwane Microsoft 365 witryn programu Word, Excel, PowerPoint, Outlook, kontenerów, które obejmują witryny sieci SharePoint i OneDrive oraz Microsoft 365 grupy. Użyj kombinacji metod etykiet, takich jak ręczne oznaczanie etykiet, etykiety automatyczne, etykiety domyślne i etykiety obowiązkowe.| [Zarządzanie etykietami poufności w aplikacjach Office](sensitivity-labels-office-apps.md) <br /><br /> [Włączanie etykiet wrażliwości dla Office w SharePoint i OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) <br /><br /> [Włączanie współtworowania plików zaszyfrowanych przy użyciu etykiet wrażliwości](sensitivity-labels-coauthoring.md) <br /><br /> [Automatyczne stosowanie etykiet wrażliwości do zawartości](apply-sensitivity-label-automatically.md) <br /><br /> [Używanie etykiet wrażliwości z Microsoft Teams, Microsoft 365 grupami i SharePoint sieci Web](sensitivity-labels-teams-groups-sites.md) <br /><br /> [Stosowanie etykiet wrażliwości do modelu w aplikacji Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [Etykiety wrażliwości w Power BI](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|Odnajdowanie, oznaczanie i chroninie poufnych elementów, które znajdują się w magazynach danych w chmurze, za pomocą programu [Microsoft Defender dla](/cloud-app-security/what-is-cloud-app-security) aplikacji w chmurze za pomocą etykiet wrażliwości.| [Odnajdowanie, klasyfikowanie, oznaczanie i ochrona danych chronionych zgodnie z regulacjami regulacyjną i poufnymi przechowywanymi w chmurze](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|Odnajdowanie, oznaczanie i ochrona poufnych elementów, które znajdują się w lokalnych magazynach danych, dzięki wdrożeniu ujednoliconego skanera etykiet usługi [Azure Information Protection](/azure/information-protection/deploy-aip-scanner) z etykietami wrażliwości.| [Konfigurowanie i instalowanie ujednoliconego skanera etykiet usługi Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|Rozszerzanie etykiet wrażliwości na platformę Azure przy użyciu usługi [Azure Purview](/azure/purview/overview) w celu odnajdowanie i oznaczanie elementów obiektów blob platformy Azure Storage, plików platformy Azure, usługi Azure Data Lake Storage Gen1 i usługi Azure Data Lake Storage Gen12. | [Oznaczanie etykietami w usłudze Azure Purview](/azure/purview/create-sensitivity-label)|

Jeśli jesteś deweloperem, który chce rozszerzyć etykiety wrażliwości na aplikacje firmowe lub aplikacje SaaS innej firmy, zobacz Konfiguracja i konfiguracja zestawu [SDK programu Microsoft Information Protection (MIP).](/information-protection/develop/setup-configure-mip) 

### <a name="additional-protection-capabilities"></a>Dodatkowe funkcje ochrony

Microsoft 365 dodatkowe funkcje ochrony danych. Nie każdy klient potrzebuje tych funkcji, a niektóre mogą zostać wyeksymowane przez najnowsze wersje.

Aby uzyskać [pełną Microsoft Information Protection ochrony, Microsoft 365](information-protection.md) stronie głównej witryny sieci Web.

## <a name="prevent-data-loss"></a>Zapobieganie utracie danych

![Zapobieganie utracie danych w przypadku rozwiązania miP — omówienie](../media/dlp-mipsolution.png)

Wdrażaj zasady ochrony przed utratą danych (DLP, data loss prevention) w celu zarządzania i zapobiegania nieodpowiednim udostępnianiu, przesyłaniu i używaniu poufnych danych w aplikacjach i usługach. Te zasady ułatwiają użytkownikom podejmowanie właściwych decyzji i podejmowanie odpowiednich działań, gdy są one wykorzystywane do przetwarzania poufnych danych.

|Krok|Opis|Więcej informacji|
|:---|:----------|:---------------|
|1|Dowiedz się więcej na temat zasad DLP. <br /><br /> Organizacje mają pod swoją kontrolą poufne informacje, takie jak dane finansowe, dane zastrzeżone, numery kart kredytowych, dokumentację opiekę zdrowotnej lub numery PESEL. Aby chronić te poufne dane i zmniejszyć ryzyko, potrzebują sposobu, aby uniemożliwić użytkownikom niewłaściwe udostępnianie tych danych osobom, które nie powinny ich udostępniać. Takie rozwiązanie nazywa się zapobieganiem utracie danych (DLP).| [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)|
|2|Zaplanuj implementację zasad DLP. <br /><br /> Każda organizacja będzie zaplanować i wdrożyć zapobieganie utracie danych (DLP) w inny sposób, ponieważ potrzeby biznesowe, cele, zasoby i sytuacje każdej organizacji są unikatowe. Istnieją jednak elementy wspólne dla wszystkich skutecznych implementacji DLP. | [Planowanie ochrony przed utratą danych](dlp-overview-plan-for-dlp.md)|
|3|Projektowanie i tworzenie zasad DLP. <br /><br /> Tworzenie zasad ochrony przed utratą danych (DLP, data loss prevention) jest szybkie i łatwe, ale uzyskanie zasad uzyskania zamierzonych wyników może być czasochłonne, jeśli trzeba dużo dostrajać. Poświęć czas na zaprojektowanie zasad przed ich wdrożeniem, aby uzyskać odpowiednie wyniki szybciej i z mniejszą liczbą niezamierzonych problemów, niż tylko dostosowywanie za pomocą samej wersji próbnej i błędów.| [Projektowanie zasad DLP](dlp-policy-design.md) <p> [Informacje dotyczące zasad DLP](dlp-policy-reference.md) <p>[Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)|
|4|Dostosowywanie zasad DLP. <br /><br /> Po wdrożeniu zasad DLP zobaczysz, jak dobrze spełniają one zamierzone cele. Skorzystaj z tych informacji, aby dostosować ustawienia zasad w celu lepszej wydajności. | [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)|


## <a name="training-resources"></a>Zasoby szkoleniowe

Edukacja dla konsultantów i administratorów:

- [Wprowadzenie do ochrony informacji i zarządzania zarządzaniem Microsoft 365](/learn/modules/m365-compliance-information-governance)
- [Klasyfikowanie danych w celu ochrony i zarządzania](/learn/modules/m365-compliance-information-classify-data)
- [Ochrona informacji w programie Microsoft 365](/learn/modules/m365-compliance-information-protect-information)
- [Zapobieganie utracie danych podczas Microsoft 365](/learn/modules/m365-compliance-information-prevent-data-loss)

Aby ułatwić użytkownikom stosowanie etykiet wrażliwości i korzystanie z nich, zobacz Dokumentację użytkownika [końcowego, aby uzyskać informacje na temat etykiet wrażliwości](get-started-with-sensitivity-labels.md#end-user-documentation-for-sensitivity-labels).

Po wdrożeniu zasad ochrony przed utratą danych w programie Teams poniższe wskazówki dla użytkowników końcowych mogą okazać się przydatne jako wprowadzenie do tej technologii wraz z potencjalnymi komunikatami, które mogą zostać do nich wysłane: wiadomości programu Teams dotyczące ochrony przed utratą danych [(DLP) ](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0)i zasad zgodności komunikacji.
