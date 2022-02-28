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
description: Zapoznaj się z ogólnym rozporządzeniem o ochronie danych (RODO) obowiązującymi w przypadku danych osobowych osób niepełnoletnich.
ms.openlocfilehash: 84a1ecc9eb5d29ae1c2e4597b8299430cc3de038
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985475"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Osoby niepełnoletnie i kupowanie dodatków ze Sklepu

Ogólne Rozporządzenie o Ochronie Danych (RODO) to rozporządzenie Unii Europejskiej, które wchodzi w życie 25 maja 2018 r. Zapewnia ono użytkownikom prawa do ich danych oraz ochronę tych danych. Jednym z aspektów rozporządzenia RODO jest to, że osoby niepełnoletnie nie mogą przesyłać swoich danych osobowych do podmiotów, które nie zostały zatwierdzone przez opiekuna lub rodzica. Wiek określający niepełnoletność zależy od regionu, w którym dana osoba przebywa.
  
Do regionów, w których obowiązują przepisy ustawowe dotyczące zgody rodzica, należą: Stany Zjednoczone, Korea Południowa, Zjednoczone Królestwo i Unia Europejska. W tych regionach osoba niepełnoletnia będzie mieć zablokowaną (za pośrednictwem usługi Azure Active Directory) możliwość uzyskiwania jakichkolwiek nowych dodatków do pakietu Office ze Sklepu i uruchamiania dodatków, które zostały nabyte wcześniej. W krajach, w których nie obowiązują przepisy ustawowe, nie będą obowiązywały ograniczenia pobierania.
  
Użytkownik jest określany jako osoba niepełnoletnia na podstawie danych wprowadzonych w usłudze Azure Active Directory. Administrator organizacji jest odpowiedzialny za zadeklarowanie grupy wieku prawnego i zgodę rodzicielską dla tego użytkownika.
  
Jeśli rodzic/opiekun wyraża zgodę, aby niepełnoletni użytkownik korzystał z określonego dodatku, administrator organizacji może użyć funkcji scentralizowanego wdrażania, aby wdrożyć dodatek dla wszystkich osób niepełnoletnich, którzy mają zgodę.
  
Aby zapewnić zgodność z rozporządzeniem RODO odnośnie osób niepełnoletnich, upewnij się, że jedna z następujących kompilacji pakietu Office jest wdrożona w Twojej szkole/organizacji.
 
 **Dla programów Word, Excel, PowerPoint i Project**: 

|**Platforma** <br/> |**Numer kompilacji** <br/> |
|:-----|:-----|
|Aplikacje Microsoft 365 dla przedsiębiorstw (bieżący kanał)  <br/> |9001.2138   <br/> |
|Aplikacje Microsoft 365 dla przedsiębiorstw (półroczny kanał Enterprise)  <br/> |8431.2159  <br/> |
|Office 2016 dla systemu Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 dla systemu Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 dla komputerów Mac  <br/> |16.11.18020200  <br/> |
|Pakiet Office dla sieci Web  <br/> |Nie dotyczy  <br/> |
   
 **Dla programu Outlook**: 
  
|**Platforma** <br/> |**Numer kompilacji** <br/> |
|:-----|:-----|
|Outlook 2016 dla systemu Windows (MSI)  <br/> |Numer kompilacji (do ustalenia)  <br/> |
|Outlook 2016 dla systemu Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 dla komputerów Mac  <br/> |16.0.9318.1000  <br/> |
|Aplikacja mobilna Outlook dla systemu iOS  <br/> |2.75.0  <br/> |
|Aplikacja mobilna Outlook dla systemu Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |Nie dotyczy  <br/> |

 **Wymagania dotyczące pakietu Office 2013**
  
Program Word, Excel i PowerPoint 2013 dla systemu Windows będą obsługiwać takie same testy dla osób niepełnoletnich, jeśli jest włączona biblioteka Active Directory Authentication Library (ADAL). Istnieją dwie opcje zapewniania zgodności, jak wyjaśniono poniżej.
  
- **Włącz opcję ADAL**. W tym artykule wyjaśniono, jak włączyć uwierzytelnianie ADAL dla programu Office 2013: Używanie [Microsoft 365 nowoczesnego uwierzytelniania z Office klientami](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>Musisz również skonfigurować klucze rejestru, aby włączyć bibliotekę ADAL, zgodnie z opisem w artykule [Włączanie nowoczesnego uwierzytelniania dla pakietu Office 2013 na urządzeniach z systemem Windows](../security-and-compliance/enable-modern-authentication.md).<br/>Ponadto musisz zainstalować następujące aktualizacje z kwietnia dla pakietu Office 2013:
    
  - [Opis aktualizacji zabezpieczeń dla pakietu Office 2013: 10 kwietnia 2018 r.](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [3 kwietnia 2018 r., aktualizacja dla pakietu Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **Nie włączaj funkcji ADAL**. Jeśli nie możesz włączyć galerii ADAL w programie Office 2013, zaleca się użycie usługi zasady grupy w celu wyłączenia Sklepu dla klientów Office klientów. Informacje dotyczące wyłączania aplikacji dla pakietu Office znajdują się [tutaj](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)).

## <a name="related-articles"></a>Artykuły pokrewne

[Wdrażanie dodatki w centrum administracyjnym](./manage-deployment-of-add-ins.md)

[Zarządzanie dodatki w centrum administracyjnym](./manage-addins-in-the-admin-center.md)
