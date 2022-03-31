---
title: Zarządzanie opiniami firmy Microsoft dla Twojej organizacji
f1.keywords:
- NOCSH
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Zarządzaj opiniami, które użytkownicy mogą wysyłać do firmy Microsoft na temat produktów firmy Microsoft.
ms.openlocfilehash: 8cd20b1a6138f389ba996bdaee8cae8ae24d2974
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403572"
---
# <a name="manage-microsoft-feedback-for-your-organization"></a>Zarządzanie opiniami firmy Microsoft dla Twojej organizacji

Jako administrator organizacji Microsoft 365, istnieje teraz kilka zasad, które ułatwiają zarządzanie zbieraniem opinii i obsługą klientów użytkowników podczas korzystania z Microsoft 365 aplikacji. Dla każdej z tych zasad możesz tworzyć istniejące grupy usługi Azure Active Directory w organizacji i korzystać z nich. Zasady te mogą kontrolować, w jaki sposób różne działy w organizacji mogą wysyłać opinie do firmy Microsoft. Firma Microsoft przegląda wszystkie opinie przesłane przez klientów i używa tych opinii w celu ulepszenia produktu. Zachowanie włączonych funkcji **opinii pozwala zobaczyć** , co użytkownicy mówią o produktach firmy Microsoft, z których chcą korzystać. Opinie od Twoich użytkowników będą wkrótce dostępne w <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365.</a>

Aby dowiedzieć się więcej na temat typów opinii i sposobu, w jaki firma Microsoft korzysta z opinii użytkowników, zobacz Informacje na temat opinii [firmy Microsoft dla Twojej organizacji](../misc/feedback-user-control.md).

W poniższej tabeli przedstawiono aplikacje i usługi, które są obecnie połączone z zasadami opinii przedstawionymi w poniższej tabeli zasad opinii. Przykłady zrzutów ekranu znajdują się poniżej tabeli.

|**Aplikacje & Usługach internetowych**|**Opinie o produktach** <br> |**Ankiety dotyczące produktów** <br> |**Zbieranie metadanych** <br> |**Zaangażowanie klientów** <br> |
|:-----|:-----|:-----|:-----|:-----|
|**Dostęp**|Tak|Tak|Tak|Tak|
|**Excel**|Tak|Tak|Tak|Tak|
|**Office.com**|Wkrótce|Wkrótce|Wkrótce|Wkrótce|
|**OneNote**|Tak|Tak|Tak|Tak|
|**OneDrive**|[Niektóre ustawienia obecnie zarządzane przez inne kontrolki.](/onedrive/disable-contact-support-send-feedback)||||
|**Outlook**|Wkrótce|Wkrótce|Wkrótce|Wkrótce|
|**PowerPoint**|Tak|Tak|Tak|Tak|
|**Project**|Wkrótce|Wkrótce|Wkrótce|Wkrótce|
|**Publisher**|Tak|Tak|Tak|Tak|
|**SharePoint**|[Niektóre ustawienia obecnie zarządzane przez inne kontrolki.](/powershell/module/sharepoint-online/set-spotenant)||||
|**Teams**|[Niektóre ustawienia obecnie zarządzane przez inne kontrolki.](/microsoftteams/manage-feedback-policies-in-teams)||||
|**Word**|Tak|Tak|Tak|Tak|
|**Visio**|Tak|Tak|Tak|Tak|
|**Yammer**|Tak|Tak|Tak|Tak|

[W tym miejscu znajdziesz kilka przykładów ankiet i opinii na temat produktów.](/microsoft-365/admin/misc/feedback-user-control#in-product-surveys)

**Zbieranie metadanych**

:::image type="content" source="../../media/feedback-metadata2.png" alt-text="Zrzut ekranu: strona opinii z przykładami metadanych":::

**Zaangażowanie klientów**

:::image type="content" source="../../media/feedback-in-product-customer-engagement.png" alt-text="Zrzut ekranu: Przykład pytania w sprawie badań klientów w produkcie":::

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby można było korzystać z tych zasad, urządzenia muszą mieć minimalny numer kompilacji. Aby uzyskać więcej informacji, zobacz tabelę poniżej.

|**Kompilacja #**|**Win32**|**iOS**|**Android**|**Mac**|**Web**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Opinie o produktach|Co najmniej wersja 2010|Co najmniej 2,42|Co najmniej 16.0.13328|Co najmniej 16,42|Publicznie dostępne|
|Ankiety dotyczące produktów|Co najmniej wersja 2010|Co najmniej 2,42|Co najmniej 16.0.13426|Co najmniej 16,42|Oczekujące na rozłożenie|
|Zbieranie metadanych|Co najmniej wersja 2010|Co najmniej 2,42|Co najmniej 16.0.13328|Co najmniej 16,42|Publicznie dostępne|
|Zaangażowanie klientów|Co najmniej wersja 2010|Co najmniej 2,42|Co najmniej 16.0.13426|Co najmniej 16,42|Oczekujące na rozłożenie|

## <a name="specific-policies-you-can-configure"></a>Konkretne zasady, które można skonfigurować

### <a name="feedback-policies"></a>Zasady dotyczące opinii

|**Nazwa zasad**|**Stan domyślny**|**Podsumowanie formantu**|
|:-----|:-----|:-----|
|Zezwalaj użytkownikom na przesyłanie opinii do firmy Microsoft|Wł.|Sterowanie punktami wprowadzania opinii dla różnych aplikacji|
|Zezwalanie użytkownikom na odbieranie ankiet w produktach firmy Microsoft i odpowiadanie na nie|Wł.|Steruj monitami ankiety w obrębie produktu|
|Zezwalaj użytkownikom na dołączanie zrzutów ekranu i załączników podczas przesyłania opinii do firmy Microsoft|Wyłączone|Określa, jakie metadane użytkownik może przesłać za pomocą opinii/ankiety|
|Zezwalaj firmie Microsoft na działania w sprawie opinii przesłanych przez użytkowników|Wyłączone|Określa, czy użytkownik może udostępniać informacje kontaktowe za pomocą opinii/ankiety|
|Zezwalanie użytkownikom na dołączanie plików dziennika i przykładów zawartości podczas przesłania opinii do firmy Microsoft|Wyłączone|Określa metadane, które użytkownik może przesłać za pomocą opinii/ankiety|

## <a name="configure-policies"></a>Konfigurowanie zasad

Aby skonfigurować te ustawienia zasad, możesz użyć usługi Office zasad w chmurze. Aby uzyskać więcej informacji, zobacz [Omówienie usługi Office w chmurze](/deployoffice/overview-office-cloud-policy-service). Możesz wyszukać "opinię" lub "ankietę" w interfejsie użytkownika usługi Office w chmurze, aby znaleźć ustawienia zasad ich konfiguracji. 

Te ustawienia zasad są również dostępne, jeśli używasz programu zasady grupy. Aby użyć tych ustawień zasad, pobierz co najmniej wersję 5146.1000 z plików szablonów administracyjnych [(ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030) opublikowanych 22 marca 2021 r.

Te ustawienia zasad znajdują się w obszarze Konfiguracja użytkownika\Zasady\Szablony administracyjne\Microsoft Office 2016\Prywatność\Centrum zaufania.

> [!NOTE]
> Aktualizacja aplikacji klienckich zajmuje kilka godzin.
