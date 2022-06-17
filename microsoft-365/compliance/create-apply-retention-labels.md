---
title: Publikowanie i stosowanie etykiet przechowywania
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Instrukcje publikowania etykiet przechowywania, dzięki czemu można je zastosować w aplikacjach, aby zachować to, czego potrzebujesz, i usunąć to, czego nie potrzebujesz.
ms.openlocfilehash: b96d5f3df440db58aff63bffca11523f7c09d8ee
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128926"
---
# <a name="publish-retention-labels-and-apply-them-in-apps"></a>Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Ten scenariusz jest obsługiwany dla wszystkich konfiguracji etykiet przechowywania, w tym [rekordów regulacyjnych](records-management.md#records).

Poniższe informacje ułatwiają [publikowanie etykiet przechowywania](retention.md), a następnie stosowanie ich do dokumentów i wiadomości e-mail.

Etykiety przechowywania pomagają zachować potrzebne elementy i usuwać elementy na poziomie elementu (dokument lub wiadomość e-mail). Są one również używane do deklarowania elementu jako rekordu w ramach rozwiązania [do zarządzania rekordami](records-management.md) dla danych Microsoft 365.

Udostępnianie etykiet przechowywania osobom w organizacji w celu klasyfikowania zawartości jest procesem dwuetapowym: 

1. Utwórz etykiety przechowywania.

2. Opublikuj etykiety przechowywania przy użyciu zasad etykiet przechowywania.
  
![Diagram ról i zadań dla etykiet.](../media/4082bc7d-c04c-4b9a-8a26-7f12565d3311.png)

Wykonaj poniższe instrukcje dla dwóch kroków administratora.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny organizacji ma pełne uprawnienia do tworzenia i edytowania etykiet przechowywania oraz ich zasad. Jeśli nie logujesz się jako administrator globalny, zobacz informacje o uprawnieniach do [zarządzania rekordami](get-started-with-records-management.md#permissions) lub [zarządzania cyklem życia danych](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels), w zależności od używanego rozwiązania.

Upewnij się, że [utworzono etykiety przechowywania](file-plan-manager.md#create-retention-labels) , które chcesz zastosować do elementów.

## <a name="how-to-publish-retention-labels"></a>Jak publikować etykiety przechowywania

Przed utworzeniem zasad etykiet przechowywania zdecyduj, czy będą **to zasady adaptacyjne** , czy **statyczne**. Aby uzyskać więcej informacji, zobacz [Adaptacyjne lub statyczne zakresy zasad przechowywania](retention.md#adaptive-or-static-policy-scopes-for-retention). Jeśli zdecydujesz się na korzystanie z zasad adaptacyjnych, musisz utworzyć co najmniej jeden zakres adaptacyjny przed utworzeniem zasad etykiet przechowywania, a następnie wybrać je podczas procesu tworzenia zasad etykiet przechowywania. Aby uzyskać instrukcje, zobacz [Informacje o konfiguracji dla zakresów adaptacyjnych](retention-settings.md#configuration-information-for-adaptive-scopes).

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a> przejdź do jednej z następujących lokalizacji:
    
    - Jeśli używasz zarządzania rekordami:
        - **Rozwiązania** >  **Karta Zasady zarządzania rekordami** > > **Etykiety** > **Publikowanie etykiet**
    
    - Jeśli używasz zarządzania cyklem życia danych:
        - **Rozwiązania** >  **Zarządzanie cyklem** >  życia danych **Karta Zasady etykiet** > **Publikowanie etykiet**
    
    Nie widzisz rozwiązania od razu w okienku nawigacji? Najpierw wybierz pozycję **Pokaż wszystko**. 

2. Postępuj zgodnie z monitami, aby utworzyć zasady etykiet przechowywania. Zachowaj ostrożność, jaką nazwę wybierzesz dla zasad, ponieważ nie można jej zmienić po zapisaniu zasad.

3. Użyj linku, aby wybrać etykiety przechowywania do opublikowania, a następnie wybierz pozycję **Dalej**.

4. Na stronie **Wybierz typ zasad przechowywania do utworzenia** wybierz pozycję **Adaptacyjne** lub **Statyczne**, w zależności od wyboru dokonanego z instrukcji [Przed rozpoczęciem](#before-you-begin) . Jeśli nie utworzono jeszcze zakresów adaptacyjnych, możesz wybrać opcję **Adaptive,ale** ponieważ nie będzie żadnych zakresów adaptacyjnych do wybrania, nie będzie można ukończyć pracy kreatora z tą opcją.

5. W zależności od wybranego zakresu:
    
    - Jeśli wybrano pozycję **Adaptacyjne**: na stronie **Wybieranie zakresów i lokalizacji zasad adaptacyjnych** wybierz pozycję **Dodaj zakresy** i wybierz co najmniej jeden utworzony zakres adaptacyjny. Następnie wybierz co najmniej jedną lokalizację. Lokalizacje, które można wybrać, zależą od [dodanych typów zakresów](retention-settings.md#configuration-information-for-adaptive-scopes) . Jeśli na przykład dodano tylko typ zakresu **Użytkownika**, będzie można wybrać **Exchange wiadomości e-mail**, ale nie **SharePoint witryn**. 
    
    - Jeśli **wybrano pozycję Statyczne**: na stronie **Wybieranie lokalizacji** włącz lub wyłącz dowolną lokalizację. Dla każdej lokalizacji można pozostawić ją domyślną, aby [zastosować zasady do całej lokalizacji](retention-settings.md#a-policy-that-applies-to-entire-locations) lub [określić opcje dołączania i wykluczania](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions)
    
    Aby uzyskać informacje o wyborze lokalizacji, zobacz [Lokalizacje](retention-settings.md#locations).

Aby edytować istniejące zasady etykiet przechowywania (typ zasad to **Publikuj**), wybierz je, a następnie wybierz opcję **Edytuj** , aby uruchomić konfigurację **zasad przechowywania edycji** .

## <a name="when-retention-labels-become-available-to-apply"></a>Gdy etykiety przechowywania staną się dostępne do zastosowania

Jeśli publikujesz etykiety przechowywania w SharePoint lub OneDrive, te etykiety są zwykle wyświetlane, aby użytkownicy wybierali je w ciągu jednego dnia. Jednak poczekaj do siedmiu dni. 

Jeśli publikujesz etykiety przechowywania w Exchange, wyświetlanie etykiet przechowywania dla użytkowników może potrwać do siedmiu dni. Podobnie jak w przypadku wszystkich ustawień przechowywania dla Exchange, skrzynka pocztowa musi zawierać co najmniej 10 MB danych.

![Diagram przedstawiający, kiedy opublikowane etykiety wchodzą w życie.](../media/retention-labels-published-timings.png)

Jeśli etykiety nie są wyświetlane po siedmiu dniach, sprawdź **stan** zasad etykiety, wybierając je na stronie **Zasady etykiet** w portal zgodności Microsoft Purview. Jeśli zobaczysz **(błąd)** uwzględniony w stanie i w szczegółach lokalizacji zobaczysz komunikat, że wdrożenie zasad trwa dłużej niż oczekiwano lub spróbuj ponownie wdrożyć zasady, spróbuj uruchomić polecenie [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/set-appretentioncompliancepolicy) lub [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) , aby ponowić próbę dystrybucji zasad:

1. [Połączenie do programu PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom jedno z następujących poleceń:
    
    - W przypadku lokalizacji zasad **Teams wiadomości kanału prywatnego** **Yammer komunikaty użytkowników** i **Yammer komunikaty społeczności**:
    
        ```PowerShell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
    
    - W przypadku wszystkich innych lokalizacji zasad, takich jak **Exchange poczty e-mail**, **witryn SharePoint**, **wiadomości kanałów Teams** itp.:
    
        ```PowerShell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

### <a name="how-to-check-on-the-status-of-retention-labels-published-to-exchange"></a>Jak sprawdzić stan etykiet przechowywania opublikowanych w Exchange

W Exchange Online etykiety przechowywania są udostępniane użytkownikom końcowym przez proces uruchamiany co siedem dni. Za pomocą programu PowerShell można zobaczyć, kiedy ten proces został ostatnio uruchomiony i w związku z tym określić, kiedy zostanie uruchomiony ponownie.
  
1. [Połączenie do Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Uruchom te polecenia.
    
   ```powershell
   $logProps = Export-MailboxDiagnosticLogs <user> -ExtendedProperties
   ```

   ```powershell
   $xmlprops = [xml]($logProps.MailboxLog)
   ```

   ```powershell
   $xmlprops.Properties.MailboxTable.Property | ? {$_.Name -like "ELC*"}

In the results, the `ELCLastSuccessTimeStamp` (UTC) property shows when the system last processed your mailbox. If it has not happened since the time you created the policy, the labels are not going to appear. To force processing, run  `Start-ManagedFolderAssistant -Identity <user>`.
    
If labels aren't appearing in Outlook on the web and you think they should be, make sure to clear the cache in your browser (CTRL+F5).
    

## How to apply published retention labels

Use the following sections to learn how published retention labels can be applied in apps:

- [Manually apply retention labels](#manually-apply-retention-labels)

- [Applying a default retention label to all content in a SharePoint library, folder, or document set](#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set)

- [Automatically applying a retention label to email by using rules](#automatically-applying-a-retention-label-to-email-by-using-rules)

In addition, when you use [SharePoint Syntex](../contentunderstanding/index.md) and publish retention labels to SharePoint locations, you can [apply a retention label to a document understanding model](../contentunderstanding/apply-a-retention-label-to-a-model.md) so that identified documents are automatically labeled.

After content is labeled, see the following information to understand when the applied label can be removed or changed: [Only one retention label at a time](retention.md#only-one-retention-label-at-a-time).

### Manually apply retention labels 

End users, as well as administrators, can manually apply retention labels from the following locations:  

- Outlook and Outlook on the web
    
- OneDrive
    
- SharePoint
    
- Microsoft 365 group site for Teams
    
Use the following sections to understand how to apply retention labels. 

#### Applying retention labels in Outlook

To label an item in the Outlook desktop client, select the item. On the **Home** tab on the ribbon, click **Assign Policy**, and then choose the retention label. 
  
![Assign Policy button.](../media/30684dea-dd73-4e4a-9185-8e29f403b6ca.png)
  
You can also right-click an item, click **Assign Policy** in the context menu, and then choose the retention label. When you select multiple items, you can use this method to assign the same retention label to multiple items at once.

After the retention label is applied, you can view that retention label and what action it takes at the top of the item. If an email has a retention label applied that has an associated retention period, you can see at a glance when the email expires.

##### Applying a default retention label to an Outlook folder

You can apply retention labels to Outlook folders as a default label that can be inherited by messages in that folder. Right-click the folder, select **Properties**, the **Policy** tab, and select the retention label you want to use as that folder's default retention label.

When you use a standard retention label as your default label for an Outlook folder:
  
- All unlabeled items in the folder have this retention label applied.

- The inheritance flows to any child folders and items inherit the label from their nearest folder.

- Items that are already labeled retain their retention label, unless it was applied by a different default label.

- If you change or remove the default retention label for the folder: Existing retention labels applied to items in that folder are also changed or removed only if those labels were applied by a default label.

- If you move an item with a default retention label from one folder to another folder with a different default retention label: The item gets the new default retention label.

- If you move an item with a default retention label from one folder to another folder with no default retention label: The old default retention label is removed.

When labels are applied that aren't standard retention labels but mark items as [records (or regulatory records)](records-management.md#records), these labels can only be manually changed or removed.

#### Applying retention labels in Outlook on the web

To label an item in Outlook on the web, right-click the item \> **Assign policy** \> choose the retention label. Unlike Outlook desktop, you can't use this method if you multi-select items.
  
![Assign policy menu in Outlook on the web.](../media/146a23cf-e478-4595-b2e8-f707fc4e6ea3.png)
  
After the retention label is applied, you can view that retention label and what action it takes at the top of the item. If an email is classified and has an associated retention period, you can know at a glance when the email will expire.
  
![Label assigned to email in Outlook on the web.](../media/16f6c91b-5eab-4574-9d13-6d12be00a783.png)
  
As with the desktop version of Outlook on the web, you can also apply retention labels to folders. Right-click the folder, select **Assign policy**, and change **Use parent folder policy** to the retention label you want to use as that folder's default retention label.

#### Applying retention labels in OneDrive and SharePoint

To label a document (including OneNote files) in OneDrive or SharePoint, select the item \> in the upper-right corner, choose **Open the details pane**![Information pane icon.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) \> **Apply retention label** \> choose the retention label. 
  
You can also apply a retention label to a folder or document set, and you can set a [default retention label for a document library](#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set).
  
![Apply label list for an item in SharePoint.](../media/151cc83c-da57-45b0-9cd1-fd2f28a31083.png)
  
After a retention label is applied to an item, you can view it in the details pane when that item's selected.
  
![Applied label shown in Details pane.](../media/d06e585e-29f7-4c8c-afef-629c97268b8e.png)

For SharePoint, but not OneDrive, you can create a view of the library that contains the **Labels** column or **Item is a Record** column. This view lets you see at a glance the retention labels assigned to all items and which items are records. Note, however, that you can't filter the view by the **Item is a Record** column. For instructions how to add columns, see [Show or hide columns in a list or library](https://support.microsoft.com/en-us/office/show-or-hide-columns-in-a-list-or-library-b820db0d-9e3e-4ff9-8b8b-0b2dbefa87e2).


#### Applying retention labels using Microsoft 365 groups

When you publish retention labels to the **Microsoft 365 Groups** location, the retention labels appear in the SharePoint teams site but aren't supported by any email client for group mailboxes. The experience of applying a retention label in the site is identical to that for documents in SharePoint.

### Applying a default retention label to all content in a SharePoint library, folder, or document set

This method requires retention labels to be published to a retention label policy.

In addition to letting people apply a retention label to individual documents, you can also apply a default retention label to a SharePoint library, folder, or document set. In this scenario, documents in that location can inherit your selected default retention label. Although the same label is applied, each document will be retained and deleted separately, according to the start of the retention period setting in the label. 
  
For a document library, the default label configuration is done on the **Library settings** page for a document library. When you choose the default retention label, you can also choose to apply it to existing items in the library.
  
For example, if you have a retention label for marketing materials, and you know a specific document library contains only that type of content, you can make the **Marketing Materials** retention label the default label for all documents in that library.
  
![Apply label option on library Settings page.](../media/0787d651-63dc-43b4-8768-716a5ecc64ec.png)

#### Label behavior when you use a default label for SharePoint

For standard retention labels that you apply as a default retention label to a library, folder, or document set:

- All new, unlabeled items in the container will have this retention label applied.

- For folders, the inheritance flows to any child folders and items inherit the label from their nearest folder.

- If you selected the option to apply the default label to existing items: Items that are already labeled retain their retention label, unless it was applied by a different default label.
    
- If you change the default retention label for the container: Existing retention labels applied to items in that container are changed only if you selected the option to apply the default label to existing items and those labels were applied by a default label.

- If you remove the default retention label for the container: Items retain their labels.
    
- If you move an item with a default retention label applied from one container to another container: The item keeps its existing default retention label, even if the new location has a different default retention label. Only if you then change the default label for this new location can the moved item inherit the default label from its current location.

When labels are applied that aren't standard retention labels but mark items as [records (or regulatory records)](records-management.md#records), these labels can only be manually changed or removed.

### Automatically applying a retention label to email by using rules

In Outlook, you can create rules to apply a retention label.
  
For example, you can create a rule that applies a specific retention label to all messages sent to or from a specific distribution group.
  
To create a rule, right-click an item \> **Rules** \> **Create Rule** \> **Advanced Options** \> **Rules Wizard** \> **apply retention policy**.
  
![Rules wizard with option to apply retention policies.](../media/eeb2407c-15b6-4224-99cf-e0a00034d8ea.png)

Although the UI refers to retention policies, it's your retention labels that display here and can be selected, not your retention policies.

## Updating retention labels and their policies

If you [edit a retention label](file-plan-manager.md#edit-retention-labels) or a retention label policy, and the retention label or policy is already applied to content, your updated settings will automatically be applied to this content in addition to content that's newly identified.

Some settings can't be changed after the label or policy is created and saved, which include:
- Names for retention labels and their policies, the scope type (adaptive or static), and the retention settings except the retention period. However, you can't change the retention period when the retention period is based on when items were labeled.
- The option to mark items as a record.

### Deleting retention labels

You can delete retention labels that aren't currently included in any retention label policies, that aren't configured for event-based retention, or mark items as regulatory records.

For retention labels that you can delete, if they have been applied to items, the deletion fails and you see a link to content explorer to identify the labeled items.

However, it can take up to two days for content explorer to show the items that are labeled. In this scenario, the retention label might be deleted without showing you the link to content explorer.

## Locking the policy to prevent changes

If you need to ensure that no one can turn off the policy, delete the policy, or make it less restrictive, see [Use Preservation Lock to restrict changes to retention policies and retention label policies](retention-preservation-lock.md).

## Next steps

To help you track the labels applied from your published retention labeling policies:

- [Monitoring retention labels](retention.md#monitoring-retention-labels)
- [Using Content Search to find all content with a specific retention label](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)
- [Auditing retention actions](retention.md#auditing-retention-actions)

Event-based retention is another supported scenario for retention labels. For more information, see [Start retention when an event occurs](event-driven-retention.md).
