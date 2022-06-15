---
title: Tworzenie kopii zapasowych danych przed zmianą planów
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
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
description: Przed zmianą planów Microsoft 365 utwórz kopię zapasową zawartości Outlook, OneDrive, Yammer i SharePoint.
ms.date: 03/17/2021
ms.openlocfilehash: fd5239deb88fbf9b87df7e62d85a3d2cc18e1df7
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102509"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Tworzenie kopii zapasowych danych przed przełączeniem Microsoft 365 dla planów biznesowych

Jeśli użytkownik zostanie przełączony na inną subskrypcję, która ma mniej usług związanych z danymi lub użytkownik opuści organizację, kopię danych przechowywanych w Microsoft 365 można pobrać przed przełączeniem do nowej subskrypcji.

Jeśli przenosisz użytkownika do subskrypcji, która ma te same lub więcej usług, nie musisz tworzyć kopii zapasowych danych użytkownika. Zobacz [Przenoszenie użytkowników do innej subskrypcji](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>Zapisywanie kopii informacji Outlook

Jeśli użytkownicy mają Outlook, mogą [wyeksportować lub utworzyć kopię zapasową poczty e-mail, kontaktów i kalendarza do pliku pst Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) przed przełączeniem planu.
  
Po zakończeniu przełączania do nowego planu użytkownicy mogą [importować wiadomości e-mail, kontakty i kalendarz z pliku pst Outlook](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>Zapisywanie plików przechowywanych w OneDrive dla Firm

Przed przełączeniem do innej subskrypcji użytkownicy mogą [pobierać pliki i foldery z OneDrive lub SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) do innej lokalizacji, takiej jak folder na dysku twardym komputera lub udział plików w sieci organizacji.
  
## <a name="save-yammer-information"></a>Zapisywanie informacji Yammer

Administratorzy mogą eksportować wszystkie komunikaty, notatki, pliki, tematy, użytkowników i grupy do pliku .zip. Aby uzyskać więcej informacji, zobacz [Eksportowanie danych z Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). W tym celu deweloperzy mogą również korzystać z [interfejsu API Yammer](https://go.microsoft.com/fwlink/p/?linkid=842495).
  
## <a name="how-to-save-sharepoint-information"></a>Jak zapisać informacje SharePoint

Jeśli użytkownik zostanie przełączony z subskrypcji z SharePoint Online na subskrypcję, która jej nie ma, kafelek **SharePoint** nie będzie już wyświetlany w menu Microsoft 365.
  
Jednak jeśli nowa subskrypcja znajduje się w tej samej organizacji, z jakiej została przełączona, użytkownicy nadal będą mogli uzyskać dostęp do witryny zespołu SharePoint. Mogą wyświetlać i aktualizować notesy, dokumenty, zadania i kalendarze przy użyciu bezpośredniego adresu URL witryny zespołu.
  
> [!TIP]
> Zalecamy, aby użytkownicy przechodzili do witryny zespołu przed przełączeniem subskrypcji i zapisywali adres URL jako ulubiony lub zakładkę w przeglądarce.
  
Domyślnie adres URL witryny internetowej zespołu ma następującą postać:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

gdzie  _\<orgDomain\>_ jest adresem URL organizacji.
  
Jeśli na przykład domena organizacji jest contoso.onmicrosoft.com, bezpośredni adres URL witryny zespołu to `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Oczywiście użytkownicy mogą również pobierać dokumenty SharePoint Online z witryny zespołu SharePoint na komputer lokalny lub do innej lokalizacji w dowolnym momencie.
