---
title: Osoby niepełnoletnie i kupowanie dodatków ze Sklepu
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Dowiedz się więcej na temat ogólnych przepisów rozporządzenia o ochronie danych (RODO), które regulują dane osobowe małoletnich.
ms.openlocfilehash: 9b348ce47b5deef8f012428a402a4a83eaa6dcf1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094245"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Osoby niepełnoletnie i kupowanie dodatków ze Sklepu

Ogólne Rozporządzenie o Ochronie Danych (RODO) to rozporządzenie Unii Europejskiej, które wchodzi w życie 25 maja 2018 r. Zapewnia ono użytkownikom prawa do ich danych oraz ochronę tych danych. Jednym z aspektów rozporządzenia RODO jest to, że osoby niepełnoletnie nie mogą przesyłać swoich danych osobowych do podmiotów, które nie zostały zatwierdzone przez opiekuna lub rodzica. Wiek określający niepełnoletność zależy od regionu, w którym dana osoba przebywa.

Do regionów, w których obowiązują przepisy ustawowe dotyczące zgody rodzica, należą: Stany Zjednoczone, Korea Południowa, Zjednoczone Królestwo i Unia Europejska. W przypadku tych regionów dostęp do dodatków pomocniczych (za pośrednictwem Azure Active Directory) zostanie zablokowany w przypadku pobierania nowych dodatków Office ze Sklepu i uruchamiania wcześniej uzyskanych dodatków. W krajach, w których nie obowiązują przepisy ustawowe, nie będą obowiązywały ograniczenia pobierania.

Użytkownik jest określany jako osoba niepełnoletnia na podstawie danych wprowadzonych w usłudze Azure Active Directory. Administrator organizacji jest odpowiedzialny za deklarowanie prawnej grupy wiekowej i zgody rodziców dla tego użytkownika.

Jeśli rodzic/opiekun wyraża zgodę na osoby niepełnoletnie przy użyciu określonego dodatku, administrator organizacji może użyć scentralizowanego wdrożenia, aby wdrożyć ten dodatek dla wszystkich osób niepełnoletnich, które mają zgodę.

Aby zapewnić zgodność z rozporządzeniem RODO odnośnie osób niepełnoletnich, upewnij się, że jedna z następujących kompilacji pakietu Office jest wdrożona w Twojej szkole/organizacji.

 **Dla programów Word, Excel, PowerPoint i Project**:

|Platforma|Numer kompilacji|
|---|---|
|Aplikacje Microsoft 365 dla przedsiębiorstw (bieżący kanał)|9001.2138|
|Aplikacje Microsoft 365 dla przedsiębiorstw (półroczny kanał Enterprise)|8431.2159|
|Office 2016 dla systemu Windows|16.0.4672.1000|
|Office 2013 dla systemu Windows|15.0.5023.1000|
|Office 2016 dla komputerów Mac|16.11.18020200|
|Pakiet Office dla sieci Web|Nie dotyczy|

 **Dla programu Outlook**:

|Platforma|Numer kompilacji|
|---|---|
|Outlook 2016 dla systemu Windows (MSI)|Numer kompilacji (do ustalenia)|
|Outlook 2016 dla systemu Windows (C2R)|16.0.9323.1000|
|Office 2016 dla komputerów Mac|16.0.9318.1000|
|Aplikacja mobilna Outlook dla systemu iOS|2.75.0|
|Aplikacja mobilna Outlook dla systemu Android|2.2.145|
|Outlook.com|Nie dotyczy|

 **Wymagania dotyczące pakietu Office 2013**

Program Word, Excel i PowerPoint 2013 dla Windows będą obsługiwać te same testy pomocnicze, jeśli biblioteka uwierzytelniania usługi Active Directory (ADAL) jest włączona. Istnieją dwie opcje zapewniania zgodności, jak wyjaśniono poniżej.

- **Włącz bibliotekę ADAL**. W tym artykule wyjaśniono, jak włączyć bibliotekę ADAL dla Office 2013 r.: [Używanie Microsoft 365 nowoczesnego uwierzytelniania z klientami Office](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>Musisz również skonfigurować klucze rejestru, aby włączyć bibliotekę ADAL, zgodnie z opisem w artykule [Włączanie nowoczesnego uwierzytelniania dla pakietu Office 2013 na urządzeniach z systemem Windows](../security-and-compliance/enable-modern-authentication.md).<br/>Ponadto musisz zainstalować następujące aktualizacje z kwietnia dla pakietu Office 2013:

  - [Opis aktualizacji zabezpieczeń dla pakietu Office 2013: 10 kwietnia 2018 r.](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)

  - [3 kwietnia 2018 r., aktualizacja dla pakietu Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)

- **Nie włączaj biblioteki ADAL**. Jeśli nie możesz włączyć biblioteki ADAL w Office 2013 r., zalecamy wyłączenie magazynu dla klientów Office przy użyciu zasady grupy. Informacje dotyczące wyłączania aplikacji dla pakietu Office znajdują się [tutaj](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)).

## <a name="related-articles"></a>Artykuły pokrewne

[Wdrażanie dodatki w centrum administracyjnym](./manage-deployment-of-add-ins.md)

[Zarządzanie dodatkami w centrum administracyjnym](./manage-addins-in-the-admin-center.md)
