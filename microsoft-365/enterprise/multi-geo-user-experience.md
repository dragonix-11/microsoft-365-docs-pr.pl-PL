---
title: Środowisko użytkownika w środowisku z wieloma lokalizacjami geograficznymi
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Poznaj ustawienia SharePoint, OneDrive i Exchange użytkownika w środowisku wielolokalowym dla Microsoft 365.
ms.openlocfilehash: 638aa7d65f9243bfd110eebac6473d641e1d0b61
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014667"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Środowisko użytkownika w środowisku z wieloma lokalizacjami geograficznymi

W konfiguracji sieci OneDrive Multi-Geo będą widzieć OneDrive Multi-Geo użytkowników:

## <a name="exchange-mailbox"></a>Exchange skrzynki pocztowej

Skrzynka pocztowa użytkownika Exchange jest zapewniana do preferowanej lokalizacji danych i jest automatycznie przenosowana w przypadku zmiany jego pliku PDL. Użytkownicy mogą używać Outlook i Outlook w sieci Web normalnie bez zmiany środowiska użytkownika w środowisku wielolokalowym.

## <a name="hub-sites"></a>Witryny centrum

SharePoint witryn Centrum wzbogać możliwości odnajdowania zawartości i zaangażowania jej pracowników, tworząc pełną i spójną reprezentację projektów, działów lub regionów. W środowisku wielolokalowym witryny z lokalizacji satelitarnych można łatwo skojarzyć z witryną centrum niezależnie od lokalizacji geograficznej witryny centrum. Użytkownicy mogą wyszukiwać i uzyskać wyniki w centrum za pośrednictwem pojedynczego wyszukiwania niezależnie od lokalizacji geograficznej witryn.

## <a name="microsoft-365-app-launcher"></a>Microsoft 365 Uruchamianie aplikacji

Obszar Uruchamianie aplikacji działa w wielu lokalizacjach geograficznych i przekieruje każdy kafelek do odpowiedniej lokalizacji geograficznej obciążenia pracą. Kafelki SharePoint i OneDrive wskazują lokalizację odpowiadającą lokalizacji geograficznej aprowizacji przez użytkownika. Oznacza to, że użytkownik ma witrynę OneDrive lokalizacji centralnej, kafelek użytkownika SharePoint wskaże stronę główna dodatku SP w lokalizacji centralnej, ale jego witryna grupy zostanie aprowowana w lokalizacji odpowiadającej jego plikowi PDL. 

## <a name="office-applications"></a>Aplikacje pakietu Office

Office, takie jak Word, Excel i PowerPoint, automatycznie wykryją właściwą lokalizację geograficzną OneDrive dla każdego użytkownika podczas logowania. Użytkownicy nie muszą wprowadzać adresu URL witryn internetowych, które są OneDrive lub SharePoint lokalizacji geograficznej.

## <a name="onedrive-sync-app"></a>synchronizacja usługi OneDrive aplikacji

Aplikacja synchronizacja usługi OneDrive (wersja 17.3.6943.0625 i nowsze) automatycznie wykryje właściwą lokalizację geograficzną OneDrive użytkownika. Obsługa aplikacji do synchronizacji obejmuje możliwość synchronizowania witryn opartych na grupach niezależnie od ich lokalizacji geograficznej. Klient Groove synchronizacji nie jest obsługiwany dla wielu lokalizacji geograficznych. 

## <a name="onedrive-location"></a>OneDrive lokalizacji

Użytkownicy będą mieli OneDrive w preferowanej lokalizacji danych. Jeśli użytkownik przechodzi do adresu URL usługi OneDrive, który zawiera nieprawidłową lokalizację geograficzną (taką jak zakładka z poprzedniej lokalizacji geograficznej), jest automatycznie przekierowywany do OneDrive w odpowiedniej lokalizacji geograficznej.

## <a name="onedrive-ios-and-android"></a>OneDrive iOS i Android 

Aplikacje OneDrive dla systemów iOS i Android będą wyświetlać Twoje pliki OneDrive i pliki udostępnione Ci niezależnie od ich lokalizacji geograficznej. Wyszukiwanie z OneDrive dla urządzeń przenośnych spowoduje wyświetlanie odpowiednich wyników ze wszystkich lokalizacji geograficznych. Pobierz najnowszą wersję tych aplikacji.

Aby uzyskać więcej informacji, zobacz Używanie aplikacji [OneDrive w systemie iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) i [Używanie aplikacji OneDrive dla systemu Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36), aby uzyskać więcej informacji.

## <a name="onedrive-mobile-client"></a>OneDrive mobile 

Klient OneDrive mobile ma świadomość wielu lokalizacji geograficznych i wyświetla zawartość i wyniki z wszystkich lokalizacji geograficznych.

## <a name="search"></a>Wyszukiwanie

Każda lokalizacja geograficzna ma własny indeks wyszukiwania i Centrum wyszukiwania. Podczas wyszukiwania przez użytkownika zapytanie jest wysyłane do wszystkich lokalizacji geograficznych, a zwracane wyniki są scalane, a następnie klasyfikowane, dzięki czemu użytkownik otrzymuje ujednolicone wyniki. Użytkownicy mogą uzyskać wyniki ze wszystkich lokalizacji geograficznych niezależnie od ich lokalizacji geograficznej. Zobacz [Konfigurowanie wyszukiwania OneDrive Multi-Geo](configure-search-for-multi-geo.md), aby uzyskać szczegółowe informacje.

Obsługiwani są następujący klienci wyszukiwania:

-   OneDrive

-   Delve

-   SharePoint strona główna

-   Centrum wyszukiwania

-   Niestandardowe aplikacje wyszukiwania, które korzystają z SharePoint API wyszukiwania

## <a name="sharepoint-home"></a>SharePoint strona główna 

Na SharePoint Multi-Geo Twoja SharePoint jest hostowana w lokalizacji, w której użytkownik OneDrive lokalizacji. Na przykład: jeśli użytkownik ma swoją OneDrive w lokalizacji satelitarnej w Europie, jego strona SharePoint będzie renderowana z Europy. SharePoint głównej zawiera całą zawartość odpowiednią dla użytkownika niezależnie od jego lokalizacji geograficznej. 

**Obserwowane witryny, Wiadomości z witryn, Ostatnio odwiedzane witryny, Często odwiedzane witryny i Sugerowane witryny**

Wszystkie te składniki będą wyświetlane dla użytkownika niezależnie od lokalizacji geograficznej, w której jest hostowana zawartość, o ile użytkownik ma uprawnienia do tej zawartości. 

**Linki funkcji**

Administratorzy mogą konfigurować polecane linki w SharePoint głównej odpowiednio do każdej lokalizacji geograficznej. Umożliwia to administratorowi korzystanie ze strony głównej programu SP dla każdego regionu za pomocą linków odpowiednich dla użytkowników w regionie. 

## <a name="sharepoint-mobile-client"></a>SharePoint klienta mobilnego

Klient SharePoint mobile ma wiele lokalizacji geograficznych i wyświetla zawartość i wyniki z wszystkich lokalizacji geograficznych.

## <a name="sharing"></a>Udostępnianie

Środowisko s wyboru osób wyświetla wszystkich użytkowników bez względu na ich lokalizację geograficzną. Umożliwia to użytkownikowi udostępnianie innym użytkownikom w tym samym miejscu geograficznym lub w dowolnej innej lokalizacji geograficznej Twojej dzierżawy. Zawartość z różnych lokalizacji geograficznych pojawi się w widoku Udostępnione  dla mnie w usługach OneDrive, Word, Excel, PowerPoint i Office.com i będzie dostępna za pomocą widoku Sign-On użytkownika bez względu na lokalizację geograficzną, w której jest hostowana.

## <a name="teams-experience"></a>Teams środowisko użytkownika

Teams jest usługą wielolokacyjną. OneDrive i ostatnio wyświetlane pliki są wyświetlane niezależnie od lokalizacji geograficznej użytkownika. @wzmianki pracują z użytkownikami ze wszystkich lokalizacji geograficznych.

## <a name="user-profiles"></a>Profile użytkowników

Informacje z profilów użytkowników są wzorcowane w lokalizacji geograficznej użytkownika. Po wybraniu użytkownika zostaniesz przekierowywowany do odpowiedniej lokalizacji geograficznej dla tego użytkownika, gdzie zobaczysz jego pełne szczegóły profilu.

Jeśli Delve jest wyłączona, zobaczysz klasyczne środowisko profilu w programie SharePoint, które nie ma wielowymiarowej obsługi lokalizacji geograficznej.


