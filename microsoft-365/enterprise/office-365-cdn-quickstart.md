---
title: Office 365 Content Delivery Network (CDN) Szybki start
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/13/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 Content Delivery Network (CDN) Szybki start
ms.openlocfilehash: b0684fdfd8583ae6780cb23d47dc697582ae133b
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2022
ms.locfileid: "63009730"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 Content Delivery Network (CDN) Szybki start

Za pomocą wbudowanego programu **Office 365 Content Delivery Network (CDN)** można hostować elementy statyczne (obrazy, język JavaScript, arkusze stylów, pliki WOFF), aby zapewnić lepszą wydajność stron SharePoint Online. Ten Office 365 CDN zwiększa wydajność, buforowanie statycznych zasobów bliżej przeglądarek żądających ich, co pomaga przyspieszyć pobieranie i zmniejszyć opóźnienie. Ponadto ta Office 365 CDN korzysta z protokołu HTTP/2 w celu ulepszonej kompresji i do wytykiania potoków HTTP. Usługa Office 365 CDN jest zawarta w ramach subskrypcji usługi SharePoint Online.

Aby uzyskać bardziej szczegółowe informacje, zobacz Używanie [Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md).

>[!NOTE]
>Ten Office 365 CDN jest dostępny tylko dla dzierżawców w chmurze produkcyjnej (na całym świecie). Dzierżawcy chmury rządów Stanów Zjednoczonych, Chin i Niemiec obecnie nie obsługują Office 365 CDN.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>Narzędzie Diagnostyka stron dla SharePoint umożliwia identyfikowanie elementów, których nie ma w CDN

Rozszerzenie przeglądarki **narzędzi SharePoint** narzędzia za pomocą narzędzia Diagnostyka stron umożliwia łatwe listą zasobów na stronach usługi SharePoint Online, które można dodawać do CDN pochodzenia.

Narzędzie **Diagnostyka stron dla programu SharePoint** to rozszerzenie przeglądarki dla nowych przeglądarek Microsoft Edge (<https://www.microsoft.com/edge>) i Chrome, które analizuje zarówno nowoczesne SharePoint Online, jak i klasyczne strony witryn publikowania. To narzędzie udostępnia raport dla każdej analizowanej strony pokazujący, jak ta strona działa w stosunku do zdefiniowanego zestawu kryteriów wydajności. Aby zainstalować narzędzie Diagnostyka stron dla SharePoint informacji, odwiedź stronę Używanie narzędzia Diagnostyka stron dla usługi [SharePoint Online](./page-diagnostics-for-spo.md).

Po uruchomieniu narzędzia Diagnostyka strony dla usługi SharePoint na stronie usługi SharePoint Online możesz kliknąć kartę Testy diagnostyczne, aby wyświetlić listę  zasobów, które nie są hostowane przez CDN. Te zasoby zostaną wyświetlone pod pozycją Content Delivery Network **(CDN) jak** pokazano na zrzucie ekranu poniżej.

![Diagnostyka strony.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>Narzędzie Diagnostyka stron działa tylko w SharePoint Online i nie można go używać na SharePoint stronie systemu.

## <a name="cdn-overview"></a>CDN— omówienie

Ten Office 365 CDN został zaprojektowany w celu zoptymalizowania wydajności użytkowników przez rozpowszechnianie często używanych obiektów, takich jak obrazy i pliki JavaScript, przez wysoką szybkość sieci globalnej, co skraca czas ładowania stron i zapewnia dostęp do hostowanych obiektów jak najbłędszego możliwego poziomu. Ta CDN pobiera zasoby z lokalizacji nazywanej _pochodzeniem_. Pochodzeniem może być witryna SharePoint, biblioteka dokumentów lub folder z ułatwieniami dostępu za pomocą adresu URL.

Podstawowe Office 365 CDN są podzielone na dwa podstawowe typy:

- **Publiczna CDN** jest przeznaczona do obsługi JS (JavaScript), CSS (StyleSheets), Pliku czcionki sieci Web (WOFF, WOFF2) i obrazów nie zastrzeżonych, takich jak logo firmy.
- **Prywatne CDN** do obrazów (PNG, JPG, JPEG itp.).

Możesz wybrać pochodzenie publiczne lub prywatne swojej organizacji. Większość organizacji zdecyduje się wdrożyć połączenie tych dwóch opcji. Zarówno opcje publiczne, jak i prywatne zapewniają podobny wzrost wydajności, ale każda z nich ma unikatowe atrybuty i zalety. Aby uzyskać więcej informacji o publicznym i prywatnym CDN, zobacz Wybieranie, czy każde pochodzenie ma [być publiczne, czy prywatne](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>Jak włączyć ustawienia publiczne i CDN z konfiguracją domyślną
Zanim dokonasz zmian w ustawieniach CDN dzierżawy, upewnij się, że spełnia ona zasady zgodności, zabezpieczeń i prywatności Twojej organizacji.

Aby uzyskać bardziej szczegółowe ustawienia konfiguracji lub jeśli masz już włączoną usługę CDN i chcesz dodać dodatkowe lokalizacje (pochodzenie), zobacz sekcję Konfigurowanie i konfigurowanie Office 365 CDN przy użyciu powłoki zarządzania usługi [SharePoint Online](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)

Połączenie dzierżawy przy użyciu powłoki zarządzania SharePoint online:

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

Aby umożliwić organizacji używanie zarówno pochodzenia publicznego, jak i prywatnego przy użyciu konfiguracji domyślnej, wpisz następujące polecenie:

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Wyniki tych polecenia cmdlet powinny wyglądać następująco:

![Dane wyjściowe set-SPOTenantCdnEnabled.](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>Zobacz też

[Korzystanie z narzędzia Diagnostyka stron dla usługi SharePoint Online](./page-diagnostics-for-spo.md)

[Używanie Office 365 Content Delivery Network (CDN) z usługą SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[Sieci dostarczania zawartości](./content-delivery-networks.md)

[Network planning and performance tuning for Office 365](./network-planning-and-performance.md)

[SharePoint wydajność — seria Office 365 CDN wideo](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
