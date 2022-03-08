---
title: Przed zmianą planów należy wrócić do kopii zapasowej danych
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
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
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Tworzenie kopii zapasowej zawartości programów Outlook, OneDrive, Yammer i SharePoint przed zmianą planów platformy Microsoft 365.
ms.date: 03/17/2021
ms.openlocfilehash: 57f897b353cfe61d5c9cae56c1d367d5e57a29ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317937"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Przed przełączeniem planów platformy Microsoft 365 dla firm należy uzyskać kopię zapasową danych

Jeśli użytkownik zostanie przełączony do innej subskrypcji, która ma mniej usług związanych z danymi lub opuści organizację, można pobrać kopię danych przechowywanych na platformie Microsoft 365 przed przełączeniem do nowej subskrypcji.

Jeśli przenosisz użytkownika do subskrypcji, która ma te same lub więcej usług, nie musisz  kopii zapasowej danych użytkownika. Zobacz [Przenoszenie użytkowników do innej subskrypcji](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Zapisywanie kopii informacji programu Outlook

Jeśli użytkownicy mają program Outlook, mogą wyeksportować lub utworzyć kopię zapasową wiadomości e-mail, kontaktów i kalendarza do pliku [pst programu Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) przed przełączeniem planu.
  
Po zakończeniu przełączania do nowego planu użytkownicy mogą importować wiadomości e-mail, kontakty i [kalendarz z pliku pst programu Outlook](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Zapisywanie plików przechowywanych w usłudze OneDrive dla Firm

Przed przełączeniem do innej subskrypcji użytkownicy mogą pobierać pliki i foldery z usługi [OneDrive lub programu SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) do innej lokalizacji, takiej jak folder na dysku twardym komputera lub udział plików w sieci organizacji.
  
## <a name="save-yammer-information"></a>Zapisywanie Yammer danych

Administratorzy mogą wyeksportować wszystkie wiadomości, notatki, pliki, tematy, użytkowników i grupy do .zip pliku. Aby uzyskać więcej informacji, zobacz [Eksportowanie danych z usługi Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Deweloperzy mogą również [używać Yammer API](https://go.microsoft.com/fwlink/p/?linkid=842495) interfejsu API firmy.
  
## <a name="how-to-save-sharepoint-information"></a>Jak zapisywać informacje programu SharePoint

Jeśli użytkownik zostanie przełączony z subskrypcji usługi SharePoint Online na subskrypcję, która jej nie zawiera, kafelek **Programu SharePoint** nie będzie już wyświetlany w menu platformy Microsoft 365.
  
Jednak o ile nowa subskrypcja znajduje się w tej samej organizacji, z tej, z która została przekierowyowana, użytkownicy nadal będą mogli uzyskać dostęp do witryny zespołu programu SharePoint. Mogą oni wyświetlać i aktualizować notesy, dokumenty, zadania i kalendarze, używając bezpośredniego adresu URL witryny zespołu.
  
> [!TIP]
> Zalecamy, aby użytkownicy przeszli do witryny zespołu przed przełączeniem subskrypcji i zapisać adres URL jako ulubiony lub zakładkę w przeglądarce.
  
Domyślnie adres URL witryny internetowej zespołu znajduje się w tym formularzu:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

gdzie  _\<orgDomain\>_ znajduje się adres URL organizacji.
  
Jeśli na przykład domena organizacji jest contoso.onmicrosoft.com, bezpośredni adres URL witryny zespołu będzie mieć .`https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`
  
Oczywiście użytkownicy mogą w dowolnym momencie pobierać dokumenty usługi SharePoint Online z witryny zespołu programu SharePoint na komputer lokalny lub do innej lokalizacji.
