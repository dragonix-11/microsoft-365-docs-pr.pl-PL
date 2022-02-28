---
title: Przed zmianą planów należy wrócić do kopii zapasowej danych
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Przed zmianą Outlook kopii zapasowej OneDrive, Yammer i SharePoint Microsoft 365 kopii zapasowej.
ms.date: 03/17/2021
ms.openlocfilehash: c65c0ce533739f5d39314dc575d407d8d1af9ca8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985650"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Kopii zapasowej danych przed przełączeniem Microsoft 365 dla firm

Jeśli użytkownik zostanie przełączony do innej subskrypcji, która ma mniej usług powiązanych z danymi lub opuści organizację, przed przełączeniem do nowej subskrypcji można pobrać kopię danych przechowywanych w u administratorach usługi Microsoft 365.

Jeśli przenosisz użytkownika do subskrypcji, która ma te same lub więcej usług, nie musisz  kopii zapasowej danych użytkownika. Zobacz [Przenoszenie użytkowników do innej subskrypcji](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Zapisywanie kopii Outlook danych

Jeśli użytkownicy mają Outlook, mogą wyeksportować lub utworzyć kopię zapasową wiadomości e-mail, kontaktów i kalendarza do pliku [pst programu Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91), zanim ich plan zostanie przełączony.
  
Po zakończeniu przełączania do nowego planu użytkownicy mogą importować pocztę e-mail, kontakty i kalendarz z [pliku Outlook pst](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Zapisywanie plików przechowywanych w OneDrive dla Firm

Przed przełączeniem do innej subskrypcji użytkownicy mogą pobierać pliki i foldery z usługi [OneDrive lub SharePoint do](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) innej lokalizacji, takiej jak folder na dysku twardym komputera albo udział plików w sieci organizacji.
  
## <a name="save-yammer-information"></a>Zapisywanie Yammer danych

Administratorzy mogą wyeksportować wszystkie wiadomości, notatki, pliki, tematy, użytkowników i grupy do .zip pliku. Aby uzyskać więcej informacji, zobacz [Eksportowanie danych z Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Deweloperzy mogą w [tym Yammer interfejs API](https://go.microsoft.com/fwlink/p/?linkid=842495) aplikacji.
  
## <a name="how-to-save-sharepoint-information"></a>Jak zapisywać SharePoint informacje

Jeśli użytkownik został przełączony z subskrypcji, która zawiera usługę SharePoint Online na subskrypcję, która go nie ma, kafelek SharePoint  nie będzie już wyświetlany w Microsoft 365 menu usługi.
  
Jeśli jednak nowa subskrypcja znajduje się w tej samej organizacji, z tej, z SharePoint zespołu, użytkownicy nadal będą mieli dostęp do tej witryny. Mogą oni wyświetlać i aktualizować notesy, dokumenty, zadania i kalendarze, używając bezpośredniego adresu URL witryny zespołu.
  
> [!TIP]
> Zalecamy, aby użytkownicy przeszli do witryny zespołu przed przełączeniem subskrypcji i zapisać adres URL jako ulubiony lub zakładkę w przeglądarce.
  
Domyślnie adres URL witryny internetowej zespołu znajduje się w tym formularzu:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

gdzie  _\<orgDomain\>_ znajduje się adres URL organizacji.
  
Jeśli na przykład domena organizacji jest contoso.onmicrosoft.com, bezpośredni adres URL witryny zespołu będzie mieć .`https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`
  
Oczywiście użytkownicy mogą również w dowolnej chwili pobierać dokumenty SharePoint Online z witryny zespołu SharePoint na komputer lokalny lub do innej lokalizacji.
