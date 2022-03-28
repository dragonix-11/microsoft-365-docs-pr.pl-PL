---
title: Wprowadzenie do ochrony przed utratą danych w Power BI
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Przygotowywanie i wdrażanie zasad DLP w lokalizacjach usługi PowerBI.
ms.openlocfilehash: a1ea5321b77db1b4e7741f4d41cdd485adbd0b97
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2022
ms.locfileid: "63717327"
---
# <a name="get-started-with-data-loss-prevention-policies-for-power-bi-preview"></a>Wprowadzenie do zasad ochrony przed utratą danych dotyczących Power BI (wersja zapoznawcza)

Aby ułatwić organizacjom wykrywanie i ochronę ich poufnych danych, Microsoft 365 ochrony przed utratą danych [(DLP, Data Loss Prevention) obsługują](/microsoft-365/compliance/dlp-learn-about-dlp) Power BI. Gdy zestaw danych usługi PowerBI odpowiada kryteriom w zasadach DLP, może zostać wyzwolony alert wyjaśniacy charakter poufnej zawartości. Ten alert jest również zarejestrowany na karcie Alerty **ochrony przed utratą** danych w portalu zgodności firmy Microsoft w celu monitorowania i zarządzania przez administratorów. Ponadto alerty e-mail mogą być wysyłane do administratorów i określonych użytkowników.

## <a name="considerations-and-limitations"></a>Uwagi i ograniczenia

- Zasady DLP dotyczą obszarów roboczych. Obsługiwane są tylko obszary robocze Premium 2 generacji.
- Obciążenia pracą oceny zestawów danych DLP wpływają na wydajność. Taryfowe obciążenia pracą przez proces oceny DLP nie są obsługiwane.
- Obsługiwane są zarówno obszary robocze środowiska klasycznego, jak i nowego, o ile są hostowane Premium 2. generacji.
- Musisz utworzyć niestandardowe zasady niestandardowe zasad DLP dla Power BI. Szablony DLP nie są obsługiwane.
- Zasady DLP stosowane do lokalizacji zasad DLP obsługują etykiety wrażliwości, a poufne typy informacji jako warunki. 
- Zasady DLP dotyczące Power BI nie są obsługiwane w przypadku przykładowych zestawów [danych, zestawów](/power-bi/connect-data/service-real-time-streaming) danych strumieniowych ani zestawów danych, które łączą się ze swoim źródłem danych za pośrednictwem usługi [DirectQuery](/power-bi/connect-data/desktop-use-directquery) lub połączenia [na żywo](/power-bi/connect-data/desktop-directquery-about#live-connections).
- Zasady DLP dla Power BI nie są obsługiwane w suwerennych chmurach.

## <a name="licensing-and-permissions"></a>Licencjonowanie i uprawnienia

### <a name="skusubscriptions-licensing"></a>Licencjonowanie subskrypcji/licencji na subskrypcje sKU

Przed rozpoczęciem pracy z zasadą DLP dla usługi Power BI potwierdź swoją Microsoft 365 [subskrypcję](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). Aby uzyskać pełne wskazówki dotyczące licencjonowania, [Microsoft 365 wskazówki dotyczące zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

### <a name="permissions"></a>Uprawnienia

Dane z zasad DLP Power BI można wyświetlać w [Eksploratorze aktywności](/microsoft-365/compliance/data-classification-activity-explorer). Istnieją cztery role, które przyznają uprawnienia eksploratorowi aktywności. konto, za pomocą których uzyskujesz dostęp do danych, musi być członkiem dowolnej z nich.

- Administrator globalny
- Administrator zgodności
- Administrator zabezpieczeń
- Administrator danych zgodności

## <a name="how-dlp-policies-for-power-bi-work"></a>Jak działają zasady DLP Power BI ochrony przed Power BI działania

Zasady DLP definiujesz w sekcji ochrony przed utratą danych w portalu zgodności. Zobacz Projektowanie [zasad ochrony przed utratą danych](dlp-policy-design.md#design-a-data-loss-prevention-policy). W zasadach określasz etykiety wrażliwości, które chcesz wykryć. Możesz także określić akcje, które będą się odbywać, gdy zasady wykryją zestaw danych, do których zastosowano określoną etykietę wrażliwości. Zasady DLP obsługują dwie akcje dla Power BI:

- Powiadomienie użytkownika za pośrednictwem porad dotyczących zasad.
- Alerty. Alerty mogą być wysyłane pocztą e-mail do administratorów i użytkowników. Ponadto administratorzy mogą monitorować alerty i zarządzać nimi na karcie **Alerty** w Centrum zgodności. 

Podczas oceny zestawu danych przez zasady DLP i dopasowania go do warunków określonych w zasadach DLP są stosowane akcje zdefiniowane w tych zasadach. Oceniany jest zestaw danych, gdy zestaw danych:

- Opublikuj
- Ponowne opublikować
- Odświeżanie na żądanie
- Zaplanowane odświeżanie

>[!NOTE]
> Ocena DLP zestawu danych nie występuje, jeśli cokolwiek z poniższych jest prawdziwe:
> - Inicjatorem wydarzenia jest podmiot zabezpieczeń usługi.
> - Właścicielem zestawu danych jest podmiot zabezpieczeń usługi lub użytkownik B2B.

### <a name="what-happens-when-a-dataset-matches-a-dlp-policy"></a>Co się stanie, gdy zestaw danych będzie odpowiadać zasadom DLP

Gdy zestaw danych jest pasuje do zasad DLP:

- Jeśli zasady mają skonfigurowane powiadomienie użytkownika, będą one oznaczone w usłudze Power BI ikoną tarczy, aby wskazać, że są one takie, jak zasady DLP.

    ![Zrzut ekranu przedstawiający znaczek porad dotyczących zasad na zestawie danych na listach.](../media/dlp-power-bi-policy-tip-on-dataset.png)

    Otwórz stronę szczegółów zestawu danych, aby wyświetlić poradę o zasadach z objaśnieniami dopasowania zasad i sposobu obsługi wykrytego typu informacji poufnych.

    ![Zrzut ekranu przedstawiający poradę o zasadach na stronie szczegółów zestawu danych.](../media/dlp-power-bi-policy-tip-in-dataset-details.png)

    >[!NOTE]
    > Ukrycie porady dotyczącej zasad nie spowoduje usunięcia jej. Pojawi się on przy następnym odwiedzinze strony.

- Jeśli w zasadach włączono alerty, alert zostanie zarejestrowany na karcie Alerty ochrony przed firmami w Centrum zgodności, a do administratorów i/lub określonych użytkowników zostanie wysłana wiadomość e-mail (jeśli została skonfigurowana). Na poniższej ilustracji przedstawiono **kartę Alerty** w sekcji ochrony przed utratą danych w Centrum zgodności.

    ![Zrzut ekranu przedstawiający kartę Alerty w centrum zgodności.](../media/dlp-power-bi-alerts-tab.png)

## <a name="configure-a-dlp-policy-for-power-bi"></a>Konfigurowanie zasad DLP dla Power BI

Postępuj zgodnie z [procedurami w teście Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) i używanie szablonu niestandardowego.

> [!IMPORTANT]
> Po wybraniu lokalizacji zasad DLP dla aplikacji usługi Power BI wybierz tylko lokalizację, Power BI lokalizacji. Nie wybieraj żadnych innych lokalizacji. Ta konfiguracja nie jest obsługiwana. 

<!--1. Log into the [Microsoft 365 compliance portal](https://compliance.microsoft.com).

1. Choose the **Data loss prevention** solution in the navigation pane, select the **Policies** tab, choose **Create policy**.

    ![Screenshot of D L P create policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create.png)

1. Choose the **Custom** category and then the **Custom policy** template.
    
    >[!NOTE]
    >No other categories or templates are currently supported.

    ![Screenshot of D L P choose custom policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-custom.png)
 
    When done, click **Next**.

1. Name the policy and provide a meaningful description.

    ![Screenshot of D L P policy name description section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-name-description.png)
 
    When done, click **Next**.

1. Enable Power BI as a location for the DLP policy. **Disable all other locations**. Currently, DLP policies for Power BI must specify Power BI as the sole location.

    ![Screenshot of D L P choose location page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-location.png)

    By default the policy will apply to all workspaces. Alternatively, you can specify particular workspaces to include in the policy as well as workspaces to exclude from the policy.
    >[!NOTE]
    > DLP actions are supported only for workspaces hosted in Premium Gen2 capacities.

    If you select **Choose workspaces** or **Exclude workspaces**, a dialog will allow you to create a list of included (or excluded) workspaces. You must specify workspaces by workspace object ID. Click the info icon for information about how to find workspace object IDs.

    ![Screenshot of D L P choose workspaces dialog.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-workspaces.png)
 
    After enabling Power BI as a DLP location for the policy and choosing which workspaces the policy will apply to, click **Next**.

1. The **Define policy settings** page appears. Choose **Create or customize advanced DLP rules** to begin defining your policy.

    ![Screenshot of D L P create advanced rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-advanced-rule.png)
 
    When done, click **Next**.

1. On the **Customize advanced DLP rules** page, you can either start creating a new rule or choose an existing rule to edit. Click **Create rule**.

    ![Screenshot of D L P create rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule.png)


1. The **Create rule** page appears. On the create rule page, provide a name and description for the rule, and then configure the other sections, which are described following the image below.

    ![Screenshot of D L P create rule form.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule-form.png)
 
### Conditions

In the condition section, you define the conditions under which the policy will apply to a dataset. Conditions are created in groups. Groups make it possible to construct complex conditions.

1. Open the conditions section, choose **Add condition** and then **Content contains**.

    ![Screenshot of D L P add conditions content contains section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions-content-contains.png)
 
    This opens the first group (named Default – you can change this).

1. Choose **Add**, and then **Sensitivity labels**.
        
    >[!NOTE]
    > Sensitive info types are currently not supported.
    
    ![Screenshot of D L P add conditions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions.png)
 
    When you choose **Sensitivity labels**, you will be able to choose a particular sensitivity label from a list that will appear.

    You can add additional sensitivity labels to the group. To the right of the group name, you can specify **Any of these** or **All of these**. This determines whether matches on all or any of the labels is required for the condition to hold. Make sure **Any of these** is selected, since datasets can’t have more than one label applied.

    The image below shows a group (Default) that contains two sensitivity label conditions. The logic Any of these means that a match on any one of the sensitivity labels in the group constitutes “true” for that group.

    ![Screenshot of D L P conditions group section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-condition-group.png) 
 
    You can create more than one group, and you can control the logic between the groups with **AND** or **OR** logic. 

    The image below shows a rule containing two groups, joined by **OR** logic.

    ![Screenshot of rule with two groups.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-content-contains.png) 
 
### Exceptions

If the sensitivity label of the dataset matches any of the defined exceptions, the rule won’t be applied to the dataset. 

Exceptions are configured in the same way as conditions, described above.
    
![Screenshot of D L P exceptions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-exceptions-section.png)
 
### Actions

Protection actions are currently unavailable for Power BI DLP policies.

![Screenshot of D L P policy actions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-actions-section.png)


### User notifications

The user notifications section is where you configure your policy tip. Turn on the toggle, select the **Notify users in Office 365 service with a policy tip** and **Policy tips** checkboxes, and write your policy tip in the text box.

![Screenshot of D L P user notification section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-notification.png)
 
### User overrides
 
User overrides are currently unavailable for Power BI DLP policies.

![Screenshot of D L P user overrides section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-overrides-section.png) 
 
### Incident reports

Assign a severity level that will be shown in alerts generated from this policy. Enable (default) or disable email notification to admins, specify users or groups for email notification, and configure the details about when notification will occur.

![Screenshot of D L P incident report section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-incidence-report.png)
   
### Additional options

![Screenshot of D L P additional options section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-additional-options.png)
 
## Monitor and manage policy alerts

Log into the Microsoft 365 compliance portal and navigate to **Data loss prevention > Alerts**.

![Screenshot of D L P Alerts tab.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-alerts-tab.png)

Click on an alert to start drilling down to its details and to see management options.
-->
## <a name="next-steps"></a>Następne kroki

- [Dowiedz się więcej o ochronie przed utratą danych](/microsoft-365/compliance/dlp-learn-about-dlp)
- [Etykiety wrażliwości w Power BI](/power-bi/enterprise/service-security-sensitivity-label-overview)
- [Schemat inspekcji etykiet wrażliwości w Power BI](/power-bi/enterprise/service-security-sensitivity-label-audit-schema)